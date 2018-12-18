---
title: Proje modeli çekirdek bileşenleri | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- project models, objects and interfaces
- project models, services
ms.assetid: b2f572d3-b26d-4846-92d1-84055fac141a
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 863aef532e90d749f5c9c93a9d16cb2daf7f6c0b
ms.sourcegitcommit: 9765b3fcf89375ca499afd9fc42cf4645b66a8a2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/20/2018
ms.locfileid: "46495992"
---
# <a name="project-model-core-components"></a>Proje Modeli Çekirdek Bileşenleri
Aşağıdaki tablolarda, proje modeli üzerinde genişletin. Tabloları kısa açıklamaları arabirimleri ve model ve arabirimleri ve belirli nesneleri ile ilişkili hizmetleri tanımlanan hizmetleri sunar. Ayrıca, proje oluşturma ve belirli proje türünüzü gereksinimlerine bağlı olarak bakım isteğe bağlı olan diğer arabirimleri tabloları ayrıntılarını gösterir.  
  
 Daha fazla bilgi için [destekleyen sembol tarama araçlarını](../../extensibility/internals/supporting-symbol-browsing-tools.md).  
  
### <a name="package-object"></a>Paket nesnesi  
  
|Arabirim|Açıklamalar|  
|---------------|--------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>|IDE'de bir VSPackage'ı başlatır ve hizmetlerinin IDE için kullanılabilir hale getirir.|  
  
### <a name="project-factory-object"></a>Proje fabrikası nesnesi  
  
|Arabirim|Açıklamalar|  
|---------------|--------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory>|Yeni proje oluşturma ve mevcut projeleri açma yönetir.|  
  
### <a name="project-objects"></a>Proje nesneleri  
  
|Arabirimler|Açıklamalar|  
|----------------|--------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3>|Her belge ad arasında eşleme tutar eklenmesini ve kaldırılmasını proje öğeleri yönetir ve düzenleyicileri açar ve `VSITEMID`. Devralınan `IVsProject` ve `IVsProject2`.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>|Gezinme ve görüntü özelliklerini yönetir ve olayları sağlar.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>|Komut yürütme benzer etkinleştirir `IOleCommandTarget` odağı Çözüm Gezgini içinde olduğunda yalnızca geçerli olan Kes ve yeniden adlandırma gibi komutları için.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|Bir proje hiyerarşisi birincil komut hedefi arabirimi olarak görev yapar. Komut durumu veya durumu ve çalıştırma komutları için nesneleri sorgulamak için standart arabirimidir. Proje penceresinde odaklı olmayan olduğunda kullanılabilir.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>|Proje durumu sürekliliği düzenler. Genellikle, proje durumu bir proje dosyası olarak depolanır, ancak dosya tabanlı olmayan depolama sistemleri için uyarlanabilir.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2>|Proje kalıcılığı, proje öğeleri için dosyaları diskte veya diğer depolama sistemlerinde nesneleri olarak tüm yönlerini yönetmek etkinleştirir. `IVsPersistHierarchyItem2` Arabirimini uygulamayan öğeleri için kullanılan <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> arabirimi.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>|Kaynak kodu denetimi ile etkileşimleri düzenler.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfgProvider>|Projeleri yapılandırma bilgilerini yönetmek etkinleştirir.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2>|Proje hata ayıklama/yayınlama yapılandırması gibi yapılandırma nesnelerini yönetir. Oluşturun, dağıtın ve hatalarını ayıklama işlemlerini proje yapılandırma nesneleri Eşgüdümlü.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyDeleteHandler>|Silme (yıkıcı) denetlemek veya hiyerarşi öğeleri (bozucu olmayan) seçeneklerini kaldırmak için hiyerarşi tarafından uygulanır. Sorgu arabirimi çağırmak `IVsHierarchyDeleteHandler` alanından arabirim `IVsHierarchy` arabirimi.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsGetCfgProvider>|Destekleyen bir nesne olan uygulama seçeneği sağlar `IVsCfgProvider2` arabirimi uygulayan proje nesne değerinden farklı bir COM kimlik `IVsHierarchy` arabirimi.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectStartupServices>|Projenizi Genişletilebilir olmak için diğer geliştiriciler tarafından uygulanan isteğe bağlı bir arabirim. `IVsProjectStartupServices` Arabirimi sağlayan proje dosyanıza kalıcı hale getirmek ve böylece her seferinde projenizi yükler, üçüncü taraf hizmetinin GUID çağrısı ve proje dosyası yüklediğiniz bir GUID kaydetmek üçüncü taraf VSPackage `QueryService` için GUID.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierWinClipboardHelperEvents>|Kaynak hiyerarşileri tarafından uygulanan bir `UIHierarchy` penceresinde kesme, kopyalama gibi Pano işlemleri koordine etmek ve yapıştırın. Kullanım `AdviseClipboardHelperEvents` Pano olaylarını kaydetmek için arabirim.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyDropDataSource2>|Bir UI hiyerarşi penceresinde bir Sürükle ve bırak işlemi sırasında veri kaynağına göre sürüklenen bir öğe hakkında bilgi sağlar. Çağrılabilir `IVsHierarchy` arabirimi.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyDropDataTarget>|Bir UI hiyerarşi penceresinde bir Sürükle ve bırak işlemi sırasında bırakma hedefine göre sürüklenen bir öğe hakkında bilgi sağlar. Çağrılabilir `IVsHierarchy` arabirimi.|  
  
### <a name="configuration-object"></a>Yapılandırma nesnesi  
  
|Arabirimler|Açıklamalar|  
|----------------|--------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg>|Bir yapılandırma hakkında bilgi sağlar.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2>|Projeleri yapılandırma bilgilerini yönetmek etkinleştirir.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg>|Hata ayıklayıcının denetiminin altında çalıştırılacak bir proje sağlar.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg>|Diğer projelerde dağıtım işlemleri dağıtım projeleri tarafından uygulanır.|  
  
### <a name="configuration-builder-object"></a>Yapılandırma Oluşturucu nesnesi  
  
|Arabirimler|Açıklamalar|  
|----------------|--------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg>|Bir proje yapılandırması oluşturma işlemi yönetir.|  
  
### <a name="additional-project-objects"></a>Ek proje nesneleri  
  
|Arabirimler|Açıklamalar|  
|----------------|--------------|  
|`IDispatch`<br /><br /> <xref:Microsoft.VisualStudio.OLE.Interop.ISpecifyPropertyPages>|Görüntüler öğe özelliklerinde **özellikleri** penceresi.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsOutput2><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumOutputs>|Çıkış dağıtımı için görüntüler.|  
  
 Aşağıdaki tabloda, kısa açıklamaları proje modelde tanımlanan hizmetleri sunar.  
  
### <a name="services"></a>Hizmetler  
  
|Hizmet|Açıklamalar|  
|-------------|--------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsRegisterProjectTypes>|Kendi proje fabrikası IDE ile var olduğunu kaydetmek için proje türleri uygulayan VSPackages tarafından kullanılır. VSPackage'ı çağırmanız gerekir `QueryService` bu hizmet ve kendi proje üreteci kaydettirir olduğunda `IVsPackage::SetSite` yöntemi çağrılır. Varsa `SetSite` yönteminin çağrılmaması, projenizi örneği değil.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>|IDE'nin yerleşik, iç kavramı projeleri listeleme, yeni projeler oluştur, proje değişiklikler alın ve benzeri olanağı gibi geçerli çözüm erişim sağlar.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager>|Kaynak denetiminde katılmak istediğiniz projeleri tarafından çağrılır.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsRunningDocumentTable>|Tabloya bir veya daha fazla proje öğelerinizi zaten açık olup olmadığını belirlemek için açık belgeleri saklar.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShellOpenDocument>|Aslında Standart Düzenleyici veya belirli bir düzenleyiciyi kullanarak proje öğesini açmak için çağrılan yöntemleri ve arabirimleri içerir.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments>|Bunlar eklemek, kaldırmak veya kendi öğeleri yeniden adlandırmak, tüm projeleri tarafından çağrılmak için gereklidir.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsFileChangeEx>|Bir dosya veya dizin değişiklikler yönetir ve seçili dosyaları diskte değiştirilmiş olduğunda istemciler bildirir.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave>|Öğeleri kirli veya kaydetmek için önce tüm projeler ve düzenleyiciler tarafından çağrılması gerekmez.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSolutionBuildManager>|Derleme ve dağıtım işlemleri için proje yapılandırmalarını sırasını yönetir.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsShellDebugger>|Çoğu hata ayıklama denetimler için kullanılan alt düzey hata ayıklayıcı hizmetlerine erişim sağlar.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection>|VSPackage erişimi geçerli seçimleri hakkında bilgi sağlar ve ile iletişimi sağlayan **özellikleri** penceresi.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>|Oluşturma ve araç pencerelerini veya belge pencereleri numaralandırma veya kullanıcıya hata raporlama özelliği gibi temel IDE kullanıcı Arabirimi ile ilgili işlevleri sağlar.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsStatusbar>|IDE'nin durum çubuğu erişim sağlar.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibility3>|Otomasyon modeli uygulamak için kullanılır. Proje modelinizde, döndüreceği sağlayan özellikleri nesnesi, nesne örneği oluşturur.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIHierWinClipboardHelper>|Pano olayları hiyerarşideki proje nesne üzerinde gerçekleştirmek için kullanılır. `SVsUIHierWinClipboardHelper` tanıtıcı kesme, kopyalama ve yapıştırma işlemlerine doğru olanak tanır.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>   
 [Denetim listesi: Yeni proje türleri oluşturma](../../extensibility/internals/checklist-creating-new-project-types.md)   
 [Derleme içinde değil: bir proje türü (C++) uygulamak için HierUtil7 proje sınıflarını kullanma](https://msdn.microsoft.com/library/a5c16a09-94a2-46ef-87b5-35b815e2f346)   
 [Sembol tarama araçlarını destekleme](../../extensibility/internals/supporting-symbol-browsing-tools.md)   
 [Proje Modeli Öğeleri](../../extensibility/internals/elements-of-a-project-model.md)