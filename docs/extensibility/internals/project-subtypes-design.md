---
title: Proje alt türleri tasarımı | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- project subtypes, design
ms.assetid: 405488bb-1362-40ed-b0f1-04a57fc98c56
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b9032da4a8884c940973865016bf0bbec955ebb5
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49876600"
---
# <a name="project-subtypes-design"></a>Proje Alt Türleri Tasarımı
Proje alt türleri kılan Microsoft Build Engine (MSBuild) üzerinde temel projeleri VSPackages olanak tanır. Toplama kullanımı sayesinde uygulanan yönetilen çekirdek proje sisteminin toplu yeniden [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ancak yine de belirli bir senaryo davranışını özelleştirebilirsiniz.  
  
 Aşağıdaki konular temel tasarım ve uygulama proje alt türlerinin başlatılma vermektedir:  
  
-   Proje alt türü tasarım.  
  
-   Çok düzeyli toplama.  
  
-   Arabirimleri destekleme.  
  
## <a name="project-subtype-design"></a>Proje alt tasarımı  
 Bir proje alt başlatma ana toplayarak sağlanır <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> ve <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject> nesneleri. Bu toplama geçersiz kılabilir veya en temel projenin yeteneklerini geliştirmek bir proje alt sağlar. Proje alt türleri alma özelliklerini kullanarak işlemek için ilk şans <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>, komutları kullanarak <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> ve <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>ve proje öğesi Yönetimi'ni kullanarak <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3>. Proje alt türleri de genişletebilirsiniz:  
  
- Proje yapılandırma nesneleri.  
  
- Yapılandırma bağımlı nesneler.  
  
- Bağımsız yapılandırma Gözat nesneleri.  
  
- Proje Otomasyon nesneleri.  
  
- Proje Otomasyon özellik koleksiyonları.  
  
  Proje alt türleri tarafından genişletilebilirlik hakkında daha fazla bilgi için bkz. [özellikleri ve yöntemleri genişletilmiş proje alt türleri tarafından](../../extensibility/internals/properties-and-methods-extended-by-project-subtypes.md).  
  
##### <a name="policy-files"></a>İlke dosyaları  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Ortamı ile bir proje alt ilke dosyaları uygulamaya temel proje sistemini genişletme örneği sağlar. Bir ilke dosyası, şekillendirme sağlar [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Solution Explorer dahil özelliklerini yönetme tarafından ortam **Proje Ekle** iletişim kutusu, **Yeni Öğe Ekle** iletişim kutusu ve  **Özellikleri** iletişim kutusu. İlke alt geçersiz kılar ve bu özellikleri aracılığıyla geliştirir <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg>, `IOleCommandTarget` ve <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> uygulamaları.  
  
##### <a name="aggregation-mechanism"></a>Toplama mekanizması  
 Ortamın proje alt toplama mekanizması birden çok toplama, bu nedenle daha fazla flavored proje flavoring uygulanması gereken gelişmiş bir alt tür izin düzeylerini destekler. Ayrıca, bir projenin destekleyici nesneleri, gibi alt tür <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfg>, birden çok katman düzeyini sağlamak amacıyla tasarlanmıştır. COM ve COM kısıtlamaları mantığıyla toplama kuralları, proje alt türleri ve temel projeleri iç alt veya temel Proje düzgün bir şekilde yöntem çağrıları için temsilci seçme ve başvuru sayısı yönetme katılacak şekilde etkinleştirmek için işbirliği ile programlanmak gerekir . Diğer bir deyişle, proje hakkında toplanacak toplama desteklemek için programlanmış gerekir.  
  
 Aşağıdaki çizimde, çok düzeyli proje alt toplama şematik bir temsilini gösterir.  
  
 ![Visual Studio çok düzeyli projectflavor grafiği](../../extensibility/internals/media/vs_multilevelprojectflavor.gif "VS_MultilevelProjectFlavor")  
Çok düzeyli proje alt türü  
  
 Çok düzeyli proje alt toplama üç düzeyi, bir proje alt tarafından toplanan sonra başka bir düzey proje alt türü tarafından toplanan bir temel proje oluşur. Şekil bir parçası olarak sağlanan destek arabirimlerin bazıları odaklanır [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] proje alt mimarisi.  
  
##### <a name="deployment-mechanisms"></a>Dağıtım mekanizması  
 Birçok temel proje sistemi arasında bir proje alt tarafından gelişmiş işlevler dağıtım mekanizmasıdır. Proje alt yapılandırma arabirimlerini uygulayarak dağıtım mekanizması etkiler (gibi <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg> ve <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg>) üzerinde QueryInterface çağırarak alınır <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfgProvider>. Temel projenin nerede hem proje alt düzey proje alt ekleyip farklı yapılandırma uygulamaları bir senaryoda, çağıran `QueryInterface` Gelişmiş proje alt'ın üzerinde `IUnknown`. Gelişmiş proje alt türü iç proje alt türü temel proje için soran yapılandırma uygulaması içeriyorsa, iç proje alt türü tarafından sağlanan uygulama devreder. Bir toplama düzeyinde bir durumdan diğerine kalıcı hale getirmek için bir mekanizma proje alt türleri tüm düzeyleri uygulayan <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> derleme olmayan kalıcı hale getirmek için proje dosyalarına ilgili XML verileri. Daha fazla bilgi için [MSBuild proje dosyasında verileri kalıcı hale](../../extensibility/internals/persisting-data-in-the-msbuild-project-file.md). <xref:EnvDTE80.IInternalExtenderProvider> Otomasyon genişleticilerine proje alt türleri ' almak için bir mekanizma olarak uygulanır.  
  
 Aşağıdaki çizimde, Otomasyon extender uygulaması, proje yapılandırması Gözat nesnesi özellikle, temel proje sistemini genişletmek için proje alt türleri tarafından kullanılan odaklanır.  
  
 ![VS proje Flavor otomatik genişletici grafiği](../../extensibility/internals/media/vs_projectflavorautoextender.gif "VS_ProjectFlavorAutoExtender")  
Proje alt Otomasyon Extender'ı seçin.  
  
 Proje alt türleri, Otomasyon nesne modeli genişleterek temel proje sistemi daha da genişletebilirsiniz. Bunlar DTE Otomasyon nesnesi bir parçası olarak tanımlanır ve proje nesneyi genişletmek için kullanılan `ProjectItem` nesne ve `Configuration` nesne. Daha fazla bilgi edinmek, [temel projenin nesne modelini genişletme](../../extensibility/internals/extending-the-object-model-of-the-base-project.md).  
  
## <a name="multi-level-aggregation"></a>Çok düzeyli toplama  
 Alt düzey proje alt türü sarmalayan bir proje alt uygulama düzgün şekilde çalışabilmesi iç proje alt izin vermek için işbirliği ile programlanmak gerekir. Sorumlulukları programlama bir liste aşağıdakileri içerir:  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> İç alt sarmalama proje alt uygulaması için temsilci seçme gerekir <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> iç proje alt uygulaması hem de <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment.Load%2A> ve <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment.Save%2A> yöntemleri.  
  
-   <xref:EnvDTE80.IInternalExtenderProvider> Sarmalayıcı proje alt uygulaması, kendi iç proje alt temsilci gerekir. Özellikle, uygulanması <xref:EnvDTE80.IInternalExtenderProvider.GetExtenderNames%2A> iç proje alt türü adları dizisi alın ve ardından istediği Genişleticileri eklemek için dizeleri birleştirmek gerekir.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfgProvider> Gereken bir sarmalayıcı proje alt uygulama örneğini <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfg> kendi iç nesne alt proje ve temel projenin proje yapılandırması nesnesi doğrudan olduğunu bilir yalnızca özel bir temsilci beri tutun sarmalayıcı Proje alt yapılandırma nesnesi yok. Dış Proje alt başlangıçta istediği doğrudan işlemek için yapılandırma arabirimleri seçin ve ardından kalan iç proje alt 's uygulaması için temsilci <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfg.get_CfgType%2A>.  
  
## <a name="supporting-interfaces"></a>Arabirimleri destekleme  
 Temel projenin uygulanması çeşitli yönlerini genişletmek için bir proje alt tarafından eklenen arabirimleri destekleme çağrıları atar. Bu proje yapılandırma nesneleri ve çeşitli özellik tarayıcısı nesneleri içerir. Bu arabirimler çağırarak alınır `QueryInterface` üzerinde `punkOuter` (bir işaretçiye `IUnknown`), en dıştaki proje alt toplayıcısı.  
  
|Arabirim|Proje alt türü|  
|---------------|---------------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfg>|Proje alt türü için izin verir:<br /><br /> -Bir uygulamasını sağlamak <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg>.<br />-Denetim hata ayıklayıcı başlatma kendi uygulamasını sağlamak üzere proje alt vererek <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg>.<br />-Tasarım zamanı ifade değerlendirmesi uygun şekilde işleyerek devre dışı `DBGLAUNCH_DesignTimeExprEval` uygulaması örneğini <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg.QueryDebugLaunch%2A>.|  
|<xref:EnvDTE80.IInternalExtenderProvider>|Proje alt türü için izin verir:<br /><br /> -Genişletme <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID> ekleme veya kaldırma bağımsız yapılandırma özellikleri projenin proje.<br />-Proje Otomasyon nesnesi genişletin (<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID>) projenin.<br /><br /> Yukarıdaki özellik değerlerini verilerinden alınır <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> sabit listesi.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject>|Yeniden eşlemek proje alt sağlayan <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg> proje yapılandırması Gözat nesnesi verilen nesne.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsBrowseObject>|Yeniden eşlemek proje alt sağlayan <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> veya `VSITEMID` nesne, belirtilen proje yapılandırması Gözat nesnesi.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment>|Proje dosyası (.vbproj veya .csproj) için rastgele yapılandırılmış XML verileri kalıcı hale getirmek proje alt türü sağlar. Bu veriler, MSBuild için görünür değil.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage>|Proje alt türü için izin verir:<br /><br /> -Kalıcı için yeni MSBuild özellikleri ekleyin.<br />-Gereksiz özellikleri MSBuild'den kaldırın.<br />-Sorgu için bir MSBuild özelliğinin geçerli değeri.<br />-Geçerli bir MSBuild özellik değerini değiştirin.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID>   
 <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID2>