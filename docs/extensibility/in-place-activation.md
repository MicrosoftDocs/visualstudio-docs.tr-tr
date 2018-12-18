---
title: Yerinde etkinleştirme | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - in-place view activation
ms.assetid: 7d316945-06e0-4d8e-ba3a-0ef96fc75399
manager: douge
ms.openlocfilehash: 72e6829533b1b314853b8836b8576d0165a87d03
ms.sourcegitcommit: 1c2ed640512ba613b3bbbc9ce348e28be6ca3e45
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/03/2018
ms.locfileid: "39500351"
---
# <a name="in-place-activation"></a>Yerinde etkinleştirme
Düzenleyici görünümü ActiveX veya diğer etkin denetimleri barındırıyorsa, bir ActiveX denetimi veya yerinde etkinleştirme modeli kullanarak etkin belgeyi veri nesnesi olarak Düzenleyicisi görünümünüzü uygulamalıdır.  
  
## <a name="support-for-menus-toolbars-and-commands"></a>Menüleri, araç çubukları ve komutları için destek  
 Visual Studio IDE'nin araç çubukları ve menüler kullanmak, düzenleyici görünümü sağlar. Bu uzantıları olarak ifade edilir *OLE yerinde bileşenler*. Daha fazla bilgi için <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponent> ve <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager>.  
  
 ActiveX denetimi uygularsanız, katıştırılmış diğer nesneleri barındırabilir. Bir belge veri nesnesi uygularsanız, pencere çerçevesi ActiveX denetimlerini kullanma yeteneğinizi kısıtlar.  
  
> [!NOTE]
>  <xref:Microsoft.VisualStudio.OLE.Interop.IOleDocument> Ve <xref:Microsoft.VisualStudio.OLE.Interop.IOleDocumentView> arabirimleri izin vermek için veri görünümü ve bir ayrım. Ancak, Visual Studio bu işlevselliği desteklemiyor ve bu arabirimler yalnızca belge view nesnesinin temsil etmek için kullanılır.  
  
 Kullanan düzenleyicileri <xref:Microsoft.VisualStudio.Shell.Interop.SOleComponentUIManager> hizmet sağlayabilir menü ve araç çubuğu komut tümleştirme yöntemleri çağırarak <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager> arabirim uygulandığında tarafından <xref:Microsoft.VisualStudio.Shell.Interop.SOleComponentUIManager> hizmeti. Ayrıca düzenleyicileri izleme seçimi gibi diğer Visual Studio işlevselliği sunar ve yönetim geri. Daha fazla bilgi için [özel düzenleyiciler ve tasarımcılar oluşturma](../extensibility/creating-custom-editors-and-designers.md).  
  
## <a name="objects-and-interfaces-used"></a>Nesneleri ve kullanılan arabirimleri  
 Yerinde etkinleştirme oluşturmak için kullanılan nesneleri aşağıdaki çizimde gösterilmektedir.  
  
 ![İçinde&#45;etkinleştirme Düzenleyicisi yerleştirin](../extensibility/media/vsinplaceactivationeditor.gif "vsInPlaceActivationEditor")  
Yerinde etkinleştirme Düzenleyicisi  
  
> [!NOTE]
>  Bu, yalnızca çizim nesneleri `CYourEditorFactory` nesnesi, standart bir düzenleyici oluşturmak için gereklidir. Özel bir düzenleyici oluşturuyorsanız, uygulama gerekmez <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> düzenleyiciniz büyük olasılıkla kendi özel Kalıcılık mekanizması olduğundan. Daha fazla bilgi için [özel düzenleyiciler ve tasarımcılar oluşturma](../extensibility/creating-custom-editors-and-designers.md).  
  
 Tek bir yerinde etkinleştirme düzenleyici oluşturmak için uygulanan tüm arabirimler gösterilir `CYourEditorDocument` nesne, ancak bu yapılandırma yalnızca belge verilerini tek bir görünüm destekler. Belge verilerinizi birden çok görünüm destekleme hakkında daha fazla bilgi için bkz. [birden çok belge görünümünü desteklemek](../extensibility/supporting-multiple-document-views.md).  
  
|Arabirim|Nesne türü|Bir yönetim grubuna bağlanmak veya bağlı bir yönetim grubunun özelliklerini düzenlemek için Yönetim çalışma alanında|  
|---------------|--------------------|---------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponent>|Görüntüle|Yerinde VSPackage nesneler kullanarak IDE, tamamen tümleşik bileşenleri olarak çalışılacak sağlayan <xref:Microsoft.VisualStudio.Shell.Interop.SOleComponentUIManager> hizmeti. Bu hizmet, menüleri, araç çubukları ve nesnenin komutları IDE'ye tümleştirilir ve durum değişikliği bildirimleri verir.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleObject>|Görüntüle|Katıştırılmış nesne kapsayıcısı için temel işlevleri sağlar ve bununla iletişim kurar, asıl anlamına gelir.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleInPlaceActiveObject>|Görüntüle|Etkinleştirme ve devre dışı bırakma yerinde nesnelerin yönetir ve yerinde nesne ne kadarının görünür olacağını belirler.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleInPlaceObject>|Görüntüle|Yerinde nesneyi, ilişkili uygulamanın en dıştaki çerçeve penceresi ve katıştırılmış nesne içeren uygulamayı belge penceresinde arasındaki iletişimin doğrudan bir kanal sağlar.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleDocument>|Görüntüle|Bir ActiveX nesnesinden uygular. Unutmayın yöntemlerinin <xref:Microsoft.VisualStudio.OLE.Interop.IOleDocument> ve <xref:Microsoft.VisualStudio.OLE.Interop.IOleDocumentView> ayrı bir belge verileri ve görünümü IDE içinde kullanılmaz.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|Verileri görüntüle|Belge veri nesnesi veya belge view nesnesinin ya da hem komut işlemede katılmasını sağlar.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser>|Görüntüle|Durum çubuğu güncelleştirmeleri sağlar.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxUser>|Görüntüle|Öğe araç kutusuna ekleme etkinleştirir.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsFileChangeEvents>|Veri|Değişiklik bildirimi, düzenlenen dosyayı gönderir. (Bu arabirim, isteğe bağlıdır.)|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>|Veri|Bir dosya türü için Farklı Kaydet özelliğini etkinleştirmek için kullanılır.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData>|Veri|Belge için kalıcılığını etkinleştirir. Salt okunur dosyalar için çağrı <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.SetDocDataReadOnly%2A> salt okunur dosyaları belirten "Kilitle" simge sağlamak için.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsDocDataFileChangeControl>|Veri|Belge verilerini değişiklikler yok sayılıp sayılmayacağını belirler.|