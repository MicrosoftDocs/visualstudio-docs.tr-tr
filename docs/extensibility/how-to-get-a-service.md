---
title: 'Nasıl yapılır: hizmet alma | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- services, consuming
ms.assetid: 1f000020-8fb7-4e39-8e1e-2e38c7fec3d4
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b7b28f018ba92ad2ab8a266311ac2e71fd910440
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49951385"
---
# <a name="how-to-get-a-service"></a>Nasıl yapılır: hizmet alma
Genellikle farklı özelliklere erişmek için Visual Studio Hizmetleri almanız gerekir. Genel olarak, Visual Studio hizmeti, kullanabileceğiniz bir veya daha fazla arabirimleri sağlar. VSPackage çoğu Hizmetleri elde edebilirsiniz.  
  
 Öğesinden türetilen herhangi bir VSPackage <xref:Microsoft.VisualStudio.Shell.Package> ve, doğru tarihli için herhangi bir genel hizmeti isteyebilir. Çünkü `Package` sınıfının Implements <xref:System.IServiceProvider>, türetilen herhangi bir VSPackage `Package` de bir hizmet sağlayıcısıdır.  
  
 Visual Studio yüklediğinde bir <xref:Microsoft.VisualStudio.Shell.Package>, arabimini bir <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> nesnesini <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> başlatma sırasında yöntemi. Bu adlandırılır *siting* VSPackage'ı. `Package` Sınıfı bu hizmet sağlayıcısı sarmalar ve sağlayan <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> Hizmetleri alma yöntemi.  
  
## <a name="getting-a-service-from-an-initialized-vspackage"></a>Başlatılmış bir VSPackage bir hizmet alma  
  
1. Her Visual Studio uzantısı, uzantı varlıkları içeren bir VSIX dağıtım projesi ile başlar. Oluşturma bir [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] adlı VSIX projesi `GetServiceExtension`. VSIX proje şablonunda bulabilirsiniz **yeni proje** iletişim altında **Visual C#** > **genişletilebilirlik**.  
  
2. Şimdi adlı bir özel komut öğe şablonu ekleyin **GetServiceCommand**. İçinde **Yeni Öğe Ekle** iletişim kutusunda, Git **Visual C#** > **genişletilebilirlik** seçip **özel komut**. İçinde **adı** alan penceresinin en altında komut dosyası adı için değiştirme *GetServiceCommand.cs*. Özel bir komut oluşturma hakkında daha fazla bilgi için [bir menü komutuyla uzantı oluşturma](../extensibility/creating-an-extension-with-a-menu-command.md)  
  
3. İçinde *GetServiceCommand.cs*, gövdesi kaldırın `MenuItemCommand` yöntemi ve aşağıdaki kodu ekleyin:  
  
   ```csharp  
   IVsActivityLog activityLog = ServiceProvider.GetService(typeof(SVsActivityLog)) as IVsActivityLog;  
   if (activityLog == null) return;  
   System.Windows.Forms.MessageBox.Show("Found the activity log service.");  
  
   ```  
  
    Bu kod bir SVsActivityLog hizmeti alır ve kendisine bıraktığı bir <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog> etkinlik günlüğüne yazmak için kullanılan arabirim. Bir örnek için bkz. [nasıl yapılır: etkinlik günlüğü'nün](../extensibility/how-to-use-the-activity-log.md).  
  
4. Projeyi oluşturmak ve hata ayıklamaya başlayın. Deneysel örneği açılır.  
  
5. Üzerinde **Araçları** Deneysel örneğinin menü Bul **çağırma GetServiceCommand** düğmesi. Bu düğmeye tıkladığınızda, bildiren bir ileti kutusu görmeniz gerekir **etkinlik günlüğü hizmeti bulunamadı.**  
  
## <a name="getting-a-service-from-a-tool-window-or-control-container"></a>Bir araç penceresi ya da Denetim kapsayıcısından hizmet alma  
 Bazen bir araç penceresinden bir hizmet almaya veya değil tarihli, aksi takdirde, istediğiniz hizmeti hakkında bilgi sahibi değildir bir hizmet sağlayıcısı ile tarihli kapsayıcı denetimi gerekebilir. Örneğin, etkinlik günlüğünde denetimdeki yazmak isteyebilirsiniz.  
  
 Statik <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> sınıfından türetilen herhangi VSPackage'ı ilk kez başlatılan bir önbelleğe alınan hizmet sağlayıcısı dayanır yöntemi <xref:Microsoft.VisualStudio.Shell.Package> tarihli.  
  
 VSPackage Oluşturucusu VSPackage tarihli önce çağrıldığından, küresel hizmetler VSPackage oluşturucu içinde genellikle gelen kullanılamaz. Bkz: [nasıl yapılır: hizmetlerde sorun giderme](../extensibility/how-to-troubleshoot-services.md) geçici bir çözüm için.  
  
 Bir hizmet bir araç penceresi ya da diğer VSPackage olmayan öğe yolu bir örneği aşağıda verilmiştir.  
  
```csharp  
IVsActivityLog log = Package.GetGlobalService(typeof(SVsActivityLog)) as IVsActivityLog;  
if (log == null) return;  
```  
  
## <a name="getting-a-service-from-the-dte-object"></a>DTE nesneden bir hizmet alma  
 Ayrıca Hizmetleri'nden alabilir <xref:EnvDTE.DTEClass> nesne. Ancak, bir VSPackage'ı veya statik çağırarak bir hizmet olarak DTE nesnesi almalısınız <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> yöntemi.  
  
 DTE nesnesi uygulayan <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>, kullanabileceğiniz sorgulamak için bir hizmet kullanarak <xref:Microsoft.VisualStudio.Shell.ServiceProvider.GetService%2A>.  
  
 Hizmet DTE nesnesini Al açıklanmıştır.  
  
```csharp  
// Start with the DTE object, for example:   
// using EnvDTE;  
// DTE dte = (DTE)GetService(typeof(DTE));  
  
ServiceProvider sp = new ServiceProvider((Microsoft.VisualStudio.OLE.Interop.IServiceProvider)dte);  
if (sp != null)  
{  
    IVsActivityLog log = sp.GetService(typeof(SVsActivityLog)) as IVsActivityLog;  
    if (log != null)  
    {   
        System.Windows.Forms.MessageBox.Show("Found the activity log service.");  
    }  
}  
```  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Nasıl yapılır: bir hizmeti sağlama](../extensibility/how-to-provide-a-service.md)   
 [Hizmetleri sağlamak ve kullanın](../extensibility/using-and-providing-services.md)   
 [Hizmet temel bileşenleri](../extensibility/internals/service-essentials.md)