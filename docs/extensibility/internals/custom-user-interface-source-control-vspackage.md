---
title: Özel kullanıcı arabirimi (kaynak denetimi VSPackage'ı) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- user interface, source control packages
- source control packages, user interface
ms.assetid: f35ddb24-53bf-461e-b34f-7414f657c082
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: bc8158325d975aec4bd522fddad2375001d2f72e
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49919357"
---
# <a name="custom-user-interface-source-control-vspackage"></a>Özel kullanıcı arabirimi (kaynak denetimi VSPackage'ı)
Alt menü öğelerini ve varsayılan durumlarına Visual Studio komut tablosu aracılığıyla VSPackage bildirir (*.vsct*) dosyası. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Tümleşik geliştirme ortamı (IDE) VSPackage yüklenene kadar bu menü öğeleri varsayılan durumlarını görüntüler. Sonuç olarak, <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> etkinleştirmek ya da menü öğelerini devre dışı yöntemi çağrılır.  
  
 VSPackage VSPackage bağlı olarak bir komut kullanıcı arabirimi (UI) bağlamı otomatik olarak yüklenebilmesi için kayıt defteri anahtarını ayarlayabilirsiniz, ancak genellikle bir kaynak denetimi VSPackage'ı yalnızca belirli bir kullanıcı Arabirimi bağlamına geçiş yerine isteğe bağlı yüklenecektir. Hakkında daha fazla bilgi için **AutoLoadPackages** kayıt defteri anahtarı, bkz: [yönetme VSPackages](../../extensibility/managing-vspackages.md).  
  
## <a name="vspackage-ui"></a>VSPackage kullanıcı Arabirimi  
 Paket kaynak denetimi VSPackage uygulanır ve herhangi bir UI kullanmaz [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Her kaynak denetimi VSPackage'ı seçenekler belirli kaynak denetimi VSPackage'ı ayarlamak için menü öğeleri, menü grupları, araç pencerelerini, araç çubukları ve gerekli herhangi bir UI gibi kendi kullanıcı Arabirimi öğeleri belirtmeniz gerekir. Bu kullanıcı Arabirimi öğeleri, statik veya dinamik olarak etkinleştirilebilir. Statik kullanıcı Arabirimi öğeleri tanımlanmış bir *.vsct* dosya ve VSPackage'ı veya yüklü olup olmadığını görüntülenir. Dinamik kullanıcı Arabirimi öğeleri olabilir görünür bir komuta UI bağlama bağlı olarak gibi <xref:EnvDTE.Constants.vsContextNoSolution>, veya yapılan bir çağrının sonucu olarak <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> yöntemi. Dinamik kullanıcı Arabirimi öğeleri görünürlüğünü VSPackages Gecikmeli yüklemeyi stratejisini ile uyumludur.  
  
## <a name="ui-constraints-on-source-control-vspackages"></a>Kaynak denetimi VSPackage'ları kısıtlamalar kullanıcı Arabirimi  
 Yüklendikten sonra IDE'den kaynak denetimi VSPackage'ı kaldırılamaz çünkü VSPackage etkin olmayan bir duruma girmeniz mümkün olması gerekir. VSPackage artık etkin olduğunu bildirimi aldığında, VSPackage kullanıcı arabirimini devre dışı bırakır ve dış IDE etkileşimi yok sayar. VSPackage'nın uygulaması <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> yöntemi VSPackage etkin değilken komutları gizle.  
  
 Her kaynak denetimi VSPackage'ı uygulanmalı `IVsSccProvider` arabirimi. İki yöntem arabirimde <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider.SetActive%2A> ve <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider.SetInactive%2A>, VSPackage'ı tarafından uygulanmalıdır.  
  
 Kaynak denetimi VSPackage'ı abone olduğunuz tarafından uygulanan çeşitli IDE olaylarına <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3>, <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>ve benzeri. Ayrıca, VSPackage kayıt defteri etkin geri çağırma arabirimleri olarak uygulanan <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence>. Bu arabirimlerin tüm etkin olmadığında yoksayılmalıdır.  
  
 Aşağıdaki listede, bir kaynak denetimi VSPackage'ı etkin durumunu tarafından etkilenen arabirimler gösterilir:  
  
- Proje belgelerini olayları izleyin.  
  
- Çözüm olayları.  
  
- Çözüm Kalıcılık arabirimleri. Etkin olmadığında, paketleri yazma değil *.sln* ve *.suo* dosyaları.  
  
- Özellik Genişleticileri.  
  
  Gerekli <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2> ve <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>, ve ayrıca kaynak denetimiyle ilişkili herhangi bir isteğe bağlı arabirimi değil çağrılır kaynak denetimi VSPackage'ı devre dışı olduğunda.  
  
  Zaman [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE başlatıldığında [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] komut UI bağlamı için geçerli varsayılan kaynak denetimi VSPackage'ı kimliği Kimliğini ayarlar Bu, statik UI etkin kaynak denetimi VSPackage'ı yüklemeden IDE'de görünmesini VSPackage'ı neden olur. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] VSPackage'ı kaydetmek için duraklatır [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] aracılığıyla <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterScciProvider> önce VSPackage yapılan her çağrı yapar.  
  
  Aşağıdaki tabloda belirli ayrıntıları hakkında nasıl açıklar [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE farklı kullanıcı Arabirimi öğeleri gizler.  
  
| Kullanıcı Arabirimi öğesi | Açıklama |
| - | - |
| Menüleri ve araç çubukları | Kaynak Denetim paketi kaynak denetimi paket Kimliğini ilk menü ve araç çubuğu görünürlük durumlarını ayarlamalısınız [VisibilityConstraints](../../extensibility/visibilityconstraints-element.md) bölümünü *.vsct* dosya. Böylece [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] VSPackage'ı yükleme ve uygulaması çağırma menü öğelerinin durumunu uygun şekilde ayarlamak için IDE <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> yöntemi. |
| Araç pencereleri | Kaynak denetimi VSPackage'ı devre dışı yapıldığında sahip olduğu tüm araç pencereleri gizler. |
| Kaynak denetimi VSPackage'ı özgü seçenekler sayfaları | Kayıt defteri anahtarı **HKLM\SOFTWARE\Microsoft\VisualStudio\X.Y\ToolsOptionsPages\VisibilityCmdUIContexts** sağlar bir VSPackage'ı ayarlama bağlamları içinde görüntülenecek seçenekler sayfalarını gerektiriyor. Bu anahtar altındaki bir kayıt defteri girişi, hizmet kimliği (SID), kaynak denetimi hizmetini kullanarak ve DWORD değerini 1 atama oluşturulması gerekir. Her bir kullanıcı Arabirimi olay kaynak denetimi VSPackage'ı ile kayıtlı bir bağlamda gerçekleştiğinde VSPackage etkin olursa çağrılır. |
  
## <a name="see-also"></a>Ayrıca bkz.  
 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterScciProvider>   
 <xref:EnvDTE.Constants.vsContextNoSolution>   
 [VSPackage'ları yönetme](../../extensibility/managing-vspackages.md)