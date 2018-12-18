---
title: Özellik sayfaları | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- configuration options, changing properties
- property pages
- property pages, changing configuration options
ms.assetid: b9b3e6e8-1e30-4c89-9862-330265dcf38c
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: a547f5d3b075f5489caca2567ca1f1679f145073
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49878888"
---
# <a name="property-pages"></a>Özellik Sayfaları
Kullanıcılar, görüntüleyin ve özellik sayfalarını kullanma proje yapılandırma bağımlı ve - bağımsız özelliklerini değiştirin. A **özellik sayfaları** düğmesi etkin **özellikleri** penceresi veya bir özellik sayfası görünümü seçili nesnenin sağlayan nesneleri için Çözüm Gezgini araç çubuğu. Özellik sayfaları ortamı tarafından oluşturulur ve çözümler ve projeler için kullanılabilir. Ancak, aynı zamanda olabilirler oluşturan Proje öğeleri yapılandırmaya bağlı özelliklerinin kullanımı için kullanılabilir. Dosyaları bir proje içinde düzgün bir şekilde oluşturmak farklı bir derleyici anahtarı ayarları gerektirdiğinde bu özellik kullanılabilir.  
  
## <a name="using-property-pages"></a>Özellik sayfalarını kullanma  
 Özellik sayfası zaten görüntüleniyor ve (örneğin, bir çözümden bir proje için) Seçimi değiştirir bilgileri yeni seçime özelliklerini görüntülemek için değişiklikleri sayfalarında görüntülenir. Özellik sayfaları destekleyen hiçbir nesne özellikleri varsa, özellik sayfası boş olur.  
  
 Birden fazla nesne seçili değilse, tüm seçili öğe özelliklerini kesişimi özellik sayfasını görüntüler. Seçilen öğeyi yapılandırma bağımlı özellikler içermiyorsa ve **özellik sayfaları** Çözüm Gezgini araç çubuğundaki düğmesine tıklandığında, odak değiştikçe ve Özellikler penceresinde. Özellikler penceresinde ve seçimi ile ilgili daha fazla bilgi için bkz. [genişletme özellikleri](../../extensibility/internals/extending-properties.md).  
  
 Birden çok nesne için özellikleri görüntülenir ve özellik sayfasında bir değer değiştirirseniz tüm nesneler için değerleri, başlangıçta farklı ve bağımsız bir nesnenin özelliklerinde görüntülendiğinde sayfası boş olsa bile yeni değere ayarlanır.  
  
 İki genel tür vardır **ProjectProperty sayfaları** iletişim kutuları bulunan [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Visual Basic projeleri için ilk olarak, örneğin, özellik sayfaları bir alan biçimini kullanarak aşağıdaki ekran görüntüsünde gösterildiği gibi görüntülenir. İkinci, daha sonra bu bölümde, özellik sayfası ana özellikler Kılavuzu benzer şekilde, Özellikler penceresinde bulunan gösterilir.  
  
 ![Visual Basic özellik sayfaları](../../extensibility/internals/media/vsvbproppages.gif "vsVBPropPages")  
Alan biçimi ve ağaç yapısı ile proje özellik sayfaları iletişim kutusu  
  
 Özellik sayfaları iletişim kutusunda ağaç yapısını kullanarak yerleşik olmayan <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>. Ortam tarafından geçirilen düzeyi adı temel <xref:Microsoft.VisualStudio.OLE.Interop.ISpecifyPropertyPages> ve <xref:Microsoft.VisualStudio.Shell.Interop.IVsPropertyPage> arabirimleri, onu oluşturur.  
  
 Yalnızca iki en üst düzey kategorilerini kullanılabilir [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] özellik sayfaları:  
  
- Ortak özellikler, seçili nesne veya nesneler bağımsız yapılandırma bilgilerini görüntüler. Ortak Özellikler alt kategorilerinin birini seçili olduğunda, sonuç olarak, yapılandırma, Platform ve Configuration Manager Seçenekler iletişim kutusunun üst kısmındaki kullanılabilir değil.  
  
- Yapılandırma özellikleri, hata ayıklama, iyileştirme ve derleme parametreleri çözüm veya proje için ilgili yapılandırma bağımlı bilgileri içeren.  
  
  Herhangi bir ek en üst düzey kategorilerini oluşturamazsınız ancak birini uygulamanızda göstermek seçebileceğiniz `IVsPropertyPage`. Örneğin, herhangi bir bağımsız yapılandırma özelliği için bir nesneyi görüntülemek için erişiminiz yok, ortak özellikler kategori görüntülemeyecek şekilde seçebilirsiniz. Ortak özellikler, görüntü `ISpecifyPropertyPages` öğenin Gözat nesne ve yapılandırma özellikleri, uyguladığınızda uygulanan `ISpecifyPropertyPages` yapılandırma nesnesinde (nesneyi uygulama `IVsCfg`, `IVsProjectCfg`ve ilgili arabirimleri).  
  
  Bir üst düzey kategori altında görüntülenen her kategoriyi ayrı özellik sayfasını temsil eder. Kategori ve alt kategori girdileri kullanılabilir iletişim kutusunda, uygulamanız tarafından belirlenir `ISpecifyPropertyPages` ve `IVsPropertyPage`.  
  
  `IDispatch` özellik sayfaları uygulama üzerinde görüntülenecek özelliklerine sahip seçimi kapsayıcı öğeleri için nesnelerini `ISpecifyPropertyPages` sınıfı kimliklerinin listesini numaralandırılamadı. Sınıf kimliği için değişkenleri olarak geçirilir `ISpecifyPropertyPages` ve özellik sayfaları oluşturmak için kullanılır. Sınıf kimlikleri listesini de geçirilir `IVsPropertyPage` iletişim kutusunun sol tarafında ağaç yapısı oluşturmak için. Özellik sayfaları sonra geçişi bilgi tekrar `IDispatch` uygulayan nesne `ISpecifyPropertyPages` ve her sayfası bilgilerini girer.  
  
  Göz atma nesnenin özelliklerini kullanarak alınır `IDispatch` seçimi kapsayıcıdaki her nesne için.  
  
  Uygulama `Help::DisplayTopicFromF1Keyword` içinde VSPackage'ı için Yardım düğmesini işlevlerini sağlar.  
  
  Daha fazla bilgi için bkz: `IDispatch` ve `ISpecifyPropertyPages`MSDN Kitaplığı'nda.  
  
  Özellik sayfaları ikinci türü örnekleri ana bilgisayarları aşağıdaki ekran görüntüsünde gösterildiği gibi özellikler Kılavuzu, bir form görüntülenir.  
  
  ![VC özellik sayfaları](../../extensibility/internals/media/vsvcproppages.gif "vsVCPropPages")  
  Özellik sayfaları iletişim kutusu özellikleri Kılavuzu  
  
  Arabirimler `IVSMDPropertyBrowser` ve `IVSMDPropertyGrid` (vsmanaged.h içinde bildirilen) oluşturun ve bir iletişim kutusu veya penceresi içinde özellik Kılavuzu doldurmak için kullanılır.  
  
  Projeleri mimarisi, geçmiş sürümlerinden önemli ölçüde değişti [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Özellikle, proje kavramı etkin olduğu değişti. İçinde [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], etkin bir proje kavramı yoktur. Önceki geliştirme ortamlarında, derleme ve dağıtma komutları proje bağlamı bağımsız olarak varsayılan etkin proje oluştu. Şimdi, çözüm denetler ve derleme ve dağıtma komutları istemlerde hangi projeler için geçerlidir.  
  
  Daha önce etkin bir proje neydi artık üç farklı şekilde kapsanır.  
  
- Başlangıç projesi  
  
   Bir projede veya projelerde kullanıcı F5 tuşuna bastığında veya derle menüsünde Çalıştır'ı seçer, başlatılacak çözümün özellik sayfasından belirtebilirsiniz. Bu, eski etkin proje adı kalın yazı tipiyle Çözüm Gezgini'nde gösterilen anlamında benzer şekilde çalışır.  
  
   Çağırarak Otomasyon modelinde bir özellik olarak başlangıç projesi alabilirsiniz `DTE.Solution.SolutionBuild.StartupProjects`. VSPackage içinde çağırırsınız <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionBuildManager2.get_StartupProject%2A> veya <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionBuildManager2.get_StartupProject%2A> yöntemleri. `IVsSolutionBuildManager` bir hizmet tarafından sağlanan `QueryService` SID_SVsSolutionBuildManager üzerinde. Daha fazla bilgi için [proje yapılandırması nesnesi](../../extensibility/internals/project-configuration-object.md) ve [çözüm yapılandırması](../../extensibility/internals/solution-configuration.md).  
  
- Etkin çözüm yapı yapılandırması  
  
   [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] uygulama tarafından Otomasyon modelinde kullanılabilir bir etkin çözüm yapılandırmasına sahip `DTE.Solution.SolutionBuild.ActiveConfiguration`. Bir çözüm yapılandırması (her proje birden çok yapılandırmada farklı adlara sahip birden çok platformda olabilir) çözümde her proje için bir proje yapılandırması içeren bir koleksiyondur. Çözümün özellik sayfalarına ilişkin daha fazla bilgi için bkz. [çözüm yapılandırması](../../extensibility/internals/solution-configuration.md).  
  
- Şu anda seçili proje  
  
   Uygulama <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.GetCurrentSelection%2A> proje hiyerarşisi ve proje öğesi veya seçilen öğeleri almak için yöntemi. DTE, kullanacağınız `SelectedItems.SelectedItem.Project` ve `SelectedItems.SelectedItem.ProjectItem` yöntemleri. Örnek kod bu başlıklar temel altında [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] belgeleri.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPropertyPage>   
 [Yapılandırma seçeneklerini yönetme](../../extensibility/internals/managing-configuration-options.md)   
 [Proje yapılandırması nesnesi](../../extensibility/internals/project-configuration-object.md)   
 [Çözüm Yapılandırması](../../extensibility/internals/solution-configuration.md)