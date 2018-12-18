---
title: 'Nasıl yapılır: bağlam sağlamak için düzenleyicileri | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - provide context
ms.assetid: 12df4d06-df6b-4eaf-a7bf-c83655a0c683
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 848778506bdea1b7bf61b6a94a1fb14908a7b930
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49908964"
---
# <a name="how-to-provide-context-for-editors"></a>Nasıl yapılır: bağlam sağlamak için düzenleyicileri açma
Yalnızca Düzenleyici odaklı veya araç penceresine odak hemen taşınmadan önce odağa sahip için bir düzenleyici, bağlamı etkin değil. Aşağıdaki görevleri gerçekleştirerek, içerik için bir düzenleyici sağlayabilirsiniz:  
  
1. Bir içerik paketi oluşturun.  
  
2. İçerik Paketi seçimi öğe tanımlayıcısı (SEID) yayımlayın.  
  
3. Paket bağlamı korur.  
  
   Bu görevleri, aşağıdaki yordamları tarafından ele alınmaktadır. Bağlam sağlama hakkında daha fazla bilgi için bkz. **güçlü programlama** bu makalenin ilerleyen bölümlerinde.  
  
## <a name="to-create-a-context-bag-for-an-editor-or-a-designer"></a>Bir düzenleyici veya tasarımcı için bir içerik paketi oluşturmak için  
  
1.  Çağrı `QueryService` üzerinde <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> için arabirim <xref:Microsoft.VisualStudio.Shell.Interop.SVsMonitorUserContext> hizmeti.  
  
     Bir işaretçi <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorUserContext> arabirimi döndürülür.  
  
2.  Çağrı <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorUserContext.CreateEmptyContext%2A> yeni bir bağlam veya alt bağlam paketi oluşturmak için yöntemi.  
  
     Bir işaretçi <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext> arabirimi döndürülür.  
  
3.  Çağrı <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AddAttribute%2A> öznitelikler, arama anahtar sözcükleri, yöntemi veya **F1** bağlamı veya üzere paket anahtar sözcükleri.  
  
4.  Üzere paket oluşturuyorsanız, çağrı <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AddSubcontext%2A> üzere paket için ana içerik paketi bağlamak için yöntemi.  
  
5.  Çağrı <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AdviseUpdate%2A> bildirim almak için zaman **dinamik Yardım** güncelleştirmek üzere penceredir.  
  
     Sahip **dinamik Yardım** çağrı düzenleyici penceresi güncelleştirmek hazır olduğunda gecikme güncelleştirme gerçekleşene kadar bağlamını değiştirme olanağı sağlar. Sistem boşta kalma süresi kullanılabilir hale gelene kadar zaman algoritmaları çalıştıran gecikme izin verdiğinden, bunun yapılması performansı geliştirebilir.  
  
## <a name="to-publish-the-context-bag-to-the-seid"></a>İçerik Paketi için SEID yayımlamak için  
  
1.  Çağrı `QueryService` üzerinde <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackSelectionEx> işaretçisi döndürecek şekilde <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx> arabirimi.  
  
2.  Çağrı <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx.OnElementValueChange%2A>, bir öğe tanımlayıcı belirtme (`elementid` parametresi) için genel düzeyde bağlamı geçirme belirtmek için SEID_UserContext değeri.  
  
3.  Düzenleyici veya tasarımcı etkin olduğunda, değerleri kendi <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx> nesne genel seçimi yayılır. Yalnızca her oturumda bu işlemi tamamlamak ve sonra çağrıldığında oluşturulan genel bağlamda işaretçisi depolamak gereken <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx.OnElementValueChange%2A>.  
  
## <a name="to-maintain-the-context-bag"></a>İçerik Paketi korumak için  
  
1.  Uygulama <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext> emin olmak için **dinamik Yardım** penceresi, düzenleyici veya tasarımcı güncelleştirdiği önce çağırır.  
  
     Çağırdı her içerik paketi için <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AdviseUpdate%2A> içerik paketi oluşturulur ve gerçekleştirdiğini sonra <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate>, IDE çağrıları <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate.UpdateUserContext%2A> içerik paketi güncelleştirilir bağlam sağlayıcısına bildirir. Bu çağrı öznitelikleri ve anahtar sözcükleri İçerik Paketi ve tüm alt bağlam paketleri önce değiştirmek için kullanabileceğiniz **dinamik Yardım** penceresi güncelleştirme gerçekleşir.  
  
2.  Çağrı <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.SetDirty%2A> Düzenleyici veya tasarımcı yeni bağlam olduğunu belirtmek için içerik paketi üzerinde.  
  
     Zaman **dinamik Yardım** penceresi çağrıları <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate.UpdateUserContext%2A> , güncelleştirme, düzenleyici veya tasarımcı bağlamı uygun şekilde üst içerik paketi hem de tüm üzere paketleri için o anda güncelleştirebilirsiniz belirtmek için.  
  
    > [!NOTE]
    >  `SetDirty` Bayrağı otomatik olarak ayarlandığında `true` her içerik eklendiğinde veya içerik paketinden kaldırıldı. **Dinamik Yardım** penceresi yalnızca çağıran <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate.UpdateUserContext%2A> üzerinde içerik paketi, `SetDirty` bayrağı ayarlandığında `true`. İçin sıfırlama `false` güncelleştirme sonrası.  
  
3.  Çağrı <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AddAttribute%2A> bağlam etkin bağlam koleksiyona eklenecek veya <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.RemoveAttribute%2A> bağlamı kaldırmak için.  
  
## <a name="robust-programming"></a>Güçlü programlama  
 Kendi düzenleyicinizi yazıyorsanız üçü için düzenleyici bağlam sağlamak için bu makaleyi yordamları tamamlamanız gerekir.  
  
> [!NOTE]
>  Düzgün bir düzenleyici veya tasarımcı penceresini etkinleştir ve komut yönlendirme düzgün bir şekilde güncelleştirildiğinden emin olmak için çağırmalıdır <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A> bileşende odaklama penceresine olun.  
  
 SEID seçim temel alınarak değiştiren özellikler koleksiyonudur. SEID bilgi genel seçimi kullanılabilir. Genel seçimi tarafından tetiklenen olayları kablolu <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx> arabirimi ve bir liste her şeyin (geçerli Düzenleyici, geçerli araç penceresi, geçerli hiyerarşi vb.) seçti.  
  
 Düzenleyiciler ve tasarımcılar için hangi bağlamda herhangi bir zamanda değiştirebilir miyim işaretçiyi taşır bir sözcük içinde sürekli olarak içerik paketi güncelleştirmeye verimsizdir. Düzenleyici veya tasarımcı penceresini içinde taşıma imleç algılamak istediğiniz zaman daha verimli güncelleştirme yapmanız gereken, çağırabilirsiniz <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.SetDirty%2A>. Bunun yapılması, sağlar, boşta kalma süresi yoktur ve IDE'nin bağlam hizmet bildirimi Düzenleyici veya tasarımcı gönderen kadar bağlam değişikliklerinizi tutmak **dinamik Yardım** penceresi güncelleştiriyor. Bu yaklaşım kullanılır **içerik paketi korumak için** bu makaledeki yordamı.  
  
 Düzenleyici veya tasarımcı içindeki etkinlikler için bağlam girdikten sonra belirli bir sağlamalıdır **F1** Düzenleyici veya tasarımcı kendisini Yardım almak kullanıcılara izin vermek için anahtar sözcüğü.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx.OnElementValueChange%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AddAttribute%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AdviseUpdate%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.RemoveAttribute%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.SetDirty%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate.UpdateUserContext%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackSelectionEx>