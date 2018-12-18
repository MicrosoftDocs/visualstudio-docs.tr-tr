---
title: Özellikler penceresine genel bakış | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Properties window
ms.assetid: 289ed4f2-02ac-4899-855e-42dfe57ee05f
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 42048c22498915cfc2d73e691ed49d5790193854
ms.sourcegitcommit: 206e738fc45ff8ec4ddac2dd484e5be37192cfbd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/03/2018
ms.locfileid: "39510789"
---
# <a name="properties-window-overview"></a>Özellikler Penceresine Genel Bakış
**Özellikleri** windows bulunan iki ana tür seçili nesnelerin özelliklerini görüntülemek için kullanılan pencere [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] tümleşik geliştirme ortamı (IDE). Bu iki windows türleri şunlardır:  
  
-   Çözüm Gezgini, sınıf görünümü ve nesne tarayıcısı gibi araç pencereleri  
  
-   Bu tür düzenleyiciler ve tasarımcılar Form Tasarımcısı, XML Düzenleyicisi'ni ve HTML düzenleyicisi içeren belge pencereleri  
  
## <a name="using-the-properties-window"></a>Özellikler penceresini kullanma  
 **Özellikleri** penceresi tek veya birden çok Seçili öğelerin özelliklerini görüntüler. Birden çok öğe seçili değilse, seçilen tüm nesneler için tüm özellikleri kesişimi görüntülenir.  
  
 Bir form Tasarım penceresinde veya COM + meta verileri kullanarak HTML düzenleyicisi içinde seçili bir nesne için ilgili olayları görüntülenir **özellikleri** penceresi. Örneğin, bir düğmeyi seçin ve onun ilişkili olayları görüntüleyen bir `OnClick` olayı için bu düğmeyi bağlanabilir.  
  
 Görüntülenen olayları **özellikleri** penceresi öncelikle koda bağlı olan nesneleri ile kullanılır. Kod ile yapmak için hiçbir şey yüklü olmayan bir dosya biçimi düzenliyorsanız, meydana gelen olayları için yapmayacağınız. Olayları yalnızca görüntülenir **özellikleri** arasında kod ve belirli nesneleri ile ilişkili belirli olaylar çalışan bir bağlama olduğunda penceresi. Buna örnek olarak, bu nesne etkinleştirildiğinde yürüten seçili nesnenin arka plan kod olacaktır.  
  
 Aşağıdaki tabloda tarafından kullanılan birincil arabirimi **özellikleri** penceresi.  
  
|Arabirim adı|Açıklama|  
|--------------------|-----------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties>|Kategoriler bir listesini sağlar **özellikleri** penceresi ve her bir özellik için bir kategori eşler.|  
|[IDispatch arabirimi](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch)|Bir nesnenin yöntemleri ve programlama Araçlar ve Otomasyon destekleyen diğer uygulamalar için özellikler sunar.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IProvidePropertyBuilder>|Olarak adlandırılan üç nokta (...) düğmeleri sağlar *oluşturucular* nesne tarafından uygulanan kalıcı iletişim kutusu windows açın. Değer bir kolayca metin alanında kullanıcı tarafından değil yazıldığında kullanılır. Örneğin, sizin için RGB değeri belirleyen bir renk seçiciyi açmak için kullanılabilir.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>|Görüntülenen bilgileri güncelleştirmek için kullanılan nesneleri erişim sağlayan **özellikleri** penceresi. <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> VSPackage'ları tarafından görüntülenecek ilgili özellikleri ile seçilebilir nesneleri içeren her bir pencere için uygulanır.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.ITypeInfo>|Bir arabirim ve alanların bir yapının yöntemleri gibi bir nesne türü hakkında bilgi sağlar.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection>|VSPackage seçimi olayları bildirim alacak ve geçerli proje hiyerarşisi, öğe, öğe değeri ve komut UI bağlamı hakkında bilgi almak için etkinleştirir.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsMultiItemSelect>|Birden çok seçimin erişimi olan bir ortam sağlar.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing>|Bazı özellikler görüntülenen yerelleştirilmiş adlar sağlamak için kullanılan **özellikleri** penceresi.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSelectionEvents>|Geçerli seçimi, öğe değeri ya da komut UI bağlamı değişikliklerinin kayıtlı VSPackages bildirir.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx>|Ortam geçerli seçim içindeki bir değişikliği bildirir ve yeni seçime ilgili hiyerarşi ve öğe bilgilerine erişim sağlar.|  
  
 Daha fazla bilgi için `IDispatch`, MSDN Kitaplığı'na bakın.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Özellikleri genişletme](../../extensibility/internals/extending-properties.md)   
 [Özellikler Penceresi Alanları ve Arabirimleri](../../extensibility/internals/properties-window-fields-and-interfaces.md)