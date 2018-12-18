---
title: Araç kutusu yönetme | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Toolbox [Visual Studio SDK], automatic tab selection
- Toolbox [Visual Studio SDK], managing
ms.assetid: 3b052047-f6db-46dd-b3bf-da1c348ee410
caps.latest.revision: 33
manager: douge
ms.openlocfilehash: 227001e827057ffab4c851a985f7e36afaf0f351
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49873428"
---
# <a name="managing-the-toolbox"></a>Araç kutusu yönetme
[!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] Gibi bir düzenleyici veya tasarımcı, görünümünü ve üyeliğini yönetmek için bir VSPackage sağlayan **araç kutusu**.  
  
 Ayrıca, **araç kutusu** kendisini Otomasyon kullanılarak yönetilebilir. Otomasyon aracılığıyla bir araç kutusu yönetme ile ilgili daha fazla bilgi için bkz: [nasıl yapılır: araç kutusunu denetleme](http://msdn.microsoft.com/library/c9d8a18a-d2bc-43d4-a803-601bfc6a6599).  
  
## <a name="automatic-toolbox-tab-selection"></a>Otomatik araç kutusu sekme seçimi  
 Belirli bir **araç kutusu** sekme veya kategori otomatik olarak yapılabilir etkin hangi Düzenleyici veya tasarımcı şu anda etkin olan temel. Örneğin, bir form tasarımcısı etkinleştirilmişse, isteyebileceğiniz **tüm Windows Formları** sekmesi seçili.  
  
 Bu destek, düzenleyiciler ve tasarımcılar gerektiren sınırlıdır:  
  
1.  Düzenleyici veya tasarımcı örneği sağlamak için bir Fabrika nesnesine uygulamasıdır. Bir tasarımcı veya düzenleyici fabrikası nesneyi uygulama ile ilgili daha fazla bilgi için bkz: [Düzenleyici fabrikaları](../extensibility/editor-factories.md).  
  
2.  Düzenleyici veya tasarımcı varsa, otomatik olarak etkinleştirilir araç kutusu sekmeyi kaydı.  
  
## <a name="controlling-the-toolbox"></a>Araç kutusunu denetleme  
 Otomasyon desteği ekleme [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] VSPackages üzerinde nasıl daha fazla denetim sağlamak için aşağıdaki arabirimlerinden sağlar **araç kutusu** yönetilir.  
  
|Arabirim|Açıklama|  
|---------------|-----------------|  
|<xref:System.Drawing.Design.IToolboxService>|Uygulamalara yönetmek, ekleme ve kaldırma olanağı tanır <xref:System.Drawing.Design.ToolboxItem> nesnelerin **araç kutusu**. Ayrıca yapılandırma görünümünü sağlar ve **araç kutusu** kategorileri.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox2>|Etkin tabanlı uygulamalara yönetmek, ekleme ve kaldırma olanağı tanır **araç kutusu** yanı sıra yapılandırma denetimleri **araç kutusu** kategorileri ve görünüm.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox3>|İçindeki işlevle genişletir <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox2> Kalıcılık ve yerelleştirme için tam destek sağlayarak.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox4>||  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox5>||  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox6>||  
  
 Bu arabirimleri ile çalışırken göz önünde bulundurmanız birkaç önemli nokta vardır:  
  
- <xref:System.Drawing.Design.IToolboxService> yalnızca yönetilen paket çerçevesini tabanlı Vspackage'lar için kullanılabilir.  
  
- Denetim doğrudan eklenemez için **araç kutusu** kullanarak <xref:System.Drawing.Design.IToolboxService>.  
  
- VSPackage gerekir ya da kullanım <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox2> denetimleri eklemek veya öğesinden türetilen bir sarmalayıcı denetimi denetiminde barındırmak için <xref:System.Windows.Forms.AxHost>.  
  
   Visual Studio sağlar `Aximp.exe` türetilen bir ActiveX denetimi denetiminde kaydırma otomatikleştirme için aracı <xref:System.Windows.Forms.AxHost>. Daha fazla bilgi için [Aximp.exe (Windows Forms ActiveX denetim içeri Aktarıcı)](http://msdn.microsoft.com/library/482c0d83-7144-4497-b626-87d2351b78d0).  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox>, <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox2>, ve <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox3> COM tabanlı arabirimleri ile birlikte çalışma derlemelerini kullanılabilir.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox2> öğesinden türetilen <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox> ve tüm yöntemleri uygular.  
  
   Nesneler, yalnızca bir örneği elde <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox2>.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox3> türünden türemez <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox2> ve yöntemlerini uygulamaz.  
  
   Her iki arabirimde işlevselliği gerektiren nesneler iki arabirim örneklerini ortamdan edinmeniz gerekir.  
  
- İle çalışırken <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox2> ve <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox3>, kurallı (yerelleştirilmemiş) adları hakkında bilgi sekme tarafından işlenir <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox3.GetIDOfTab%2A> ve <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox3.SetIDOfTab%2A> yöntemleri.  
  
- Kullanırken <xref:System.Drawing.Design.IToolboxService>, kategori adları gibi yerelleştirilmiş bilgilerini yönetmek için uygulayan kadar olan.  
  
  Kaydedin açmasına etkinleştirmek için ayarlar mekanizmasının kullanılması **araç kutusu** kullanıcıları tarafından erişilen ayarları **içeri/dışarı aktarma ayarları** komutu, IDE'nin üzerinde bulunan **Araçları** menüsü. Ayarları nasıl kullanılacağı hakkında daha fazla bilgi için bkz. [genişletme kullanıcı ayarları ve seçenekleri](../extensibility/extending-user-settings-and-options.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Araç kutusu genişletme](../misc/extending-the-toolbox.md)