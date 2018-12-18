---
title: Bir çözümde proje yüklemeyi yönetme | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- solutions, managing project loading
ms.assetid: 097c89d0-f76a-4aaf-ada9-9a778bd179a0
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 041c5ab52a7a0e8be89ef1abe6db4d1aed51ecfc
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51781770"
---
# <a name="managing-project-loading-in-a-solution"></a>Bir Çözümde Proje Yüklemeyi Yönetme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio çözümleri, çok sayıda proje içerebilir. Varsayılan Visual Studio çözüm açıldığında bir çözümdeki tüm projeleri yüklemek ve bunların tümünü yükleme işlemini tamamlayana kadar projelerinden herhangi birinin erişmek kullanıcı izin vermeyecek şekilde davranışıdır. Proje yükleme işlemi iki dakikadan fazla en son, yüklenen projelerin sayısını ve projeleri toplam sayısını gösteren bir ilerleme çubuğu görüntülenir. Bir çözümde birden çok proje ile çalışırken, kullanıcı projeleri kaldırma, ancak bu yordamı bazı dezavantajları vardır: bir çözümü yeniden derle komutunu bir parçası olarak yüklenmemiş projeler oluşturulmadı ve IntelliSense açıklamaları türleri ve üyeleri kapalı projeleri görüntülenmez.  
  
 Geliştiriciler, çözüm yükleme sürelerinizi azaltabilir ve Proje Yöneticisi bir çözüm yük oluşturarak yükleme davranışını yönetin. Çözüm yükü Yöneticisi öncelikleri belirli proje veya proje türleri için farklı proje ayarlayın, projeleri arka plan yapı başlatmadan önce yüklendiğinden emin olun, diğer arka plan görevleri tamamlanana kadar arka planda yükleniyor gecikme ve gerçekleştirme diğer proje yükleme yönetim görevleri.  
  
## <a name="project-loading-priorities"></a>Proje öncelikleri yükleniyor  
 Visual Studio dört farklı proje yükleme öncelikleri tanımlar:  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop._VSProjectLoadPriority> (varsayılan): bir çözümü açtığınızda projeleri zaman uyumsuz olarak yüklenir. Bu öncelik yüklenmemiş bir proje üzerinde ayarlanır, bu çözümü zaten açıldıktan sonra projeyi İleri boşta noktada yüklenir.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop._VSProjectLoadPriority>: bir çözümü açtığınızda projeleri kullanıcının yüklenen tüm projeler yüklendi beklemek zorunda kalmadan oldukları gibi projeler erişmesine izin vererek arka planda yüklenir.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop._VSProjectLoadPriority>: Bunlar erişildiğinde projeleri yüklenir. Kullanıcı, (Çözüm kullanıcı seçenekleri dosyası'nda kalıcı) açık belge listesinde olduğu için çözüm açıldığında projeye ait olan bir dosya açıldığında ya da Çözüm Gezgini'nde proje düğümünü genişletirken bir proje erişilir başka bir proje diğer bir deyişle proje üzerinde sahip bağımlılık yükleniyor. Bu tür bir proje, derleme işlemini başlatmadan önce otomatik olarak yüklenmez; Çözüm yükleme yöneticisi, gerekli tüm projeleri yüklenen sağlamaktan sorumludur. Ayrıca bu projeleri Çözümdeki tüm dosyalarda Bul/Değiştir başlatmadan önce yüklenmelidir.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop._VSProjectLoadPriority>: projeleri, kullanıcı formu açıkça istemedikçe yüklü olmaması. Projeleri açıkça yüklenmediği zaman bu durum geçerlidir.  
  
## <a name="creating-a-solution-load-manager"></a>Çözüm yükü Yöneticisi oluşturma  
 Geliştiriciler oluşturabileceğiniz bir çözüm yükü Yöneticisi uygulayarak <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadManager> ve Visual Studio çözüm yükleme yöneticisi etkin olduğunu bildiren.  
  
#### <a name="activating-a-solution-load-manager"></a>Bir çözüm yük Yöneticisi'ni etkinleştirme  
 Çözüm yükleme etkinleştirmek istediğiniz zaman Visual Studio bildirmek için visual Studio Yöneticisi belirli bir anda yalnızca bir çözüm yükleme yöneticisi sağlar. İkinci bir çözüm yükleme yöneticisi daha sonra etkinleştirilmişse, çözüm yükleme yöneticinize kesilir.  
  
 Edinmeniz gerekir <xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution> ayarlayın ve hizmet <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4> özelliği:  
  
```csharp  
IVsSolution pSolution = GetService(typeof(SVsSolution)) as IVsSolution;  
object objLoadMgr = this;   //the class that implements IVsSolutionManager  
pSolution.SetProperty((int)__VSPROPID4.VSPROPID_ActiveSolutionLoadManager, objLoadMgr);  
```  
  
#### <a name="implementing-ivssolutionloadmanager"></a>IVsSolutionLoadManager uygulama  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadManager.OnBeforeOpenProject%2A> Yöntemi çözümü açma işlemi sırasında çağrılır. Bu yöntem uygulamak için kullandığınız <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadManagerSupport> yönetmek istediğiniz projenin türünü yük önceliğini ayarlamak için hizmet. Örneğin, aşağıdaki kodu, arka planda yüklenecek C# projesi türleri ayarlar:  
  
```csharp  
Guid guidCSProjectType = new Guid("{FAE04EC0-301F-11d3-BF4B-00C04F79EFBC}");  
pSLMgrSupport.SetProjectLoadPriority(guidProjectID, (uint)_VSProjectLoadPriority.PLP_BackgroundLoad);  
```  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadManager.OnDisconnect%2A> Visual Studio kapatılıyor olduğunda veya farklı bir paket etkin çözüm yükü Yöneticisi çağırarak edildiğinde yöntemi çağrıldığında <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.SetProperty%2A> ile <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4> özelliği.  
  
#### <a name="strategies-for-different-kinds-of-solution-load-manager"></a>Çözüm yükleme yöneticisi çeşitli stratejileri  
 Çözüm yükü yöneticileri yönetmek için gereken çözümlerinin türlerine bağlı olarak, farklı şekillerde uygulayabilir.  
  
 Genel yükleme çözümü yönetmek için çözüm yükleme yöneticisi geliyorsa, VSPackage bir parçası olarak uygulanabilir. Paket ekleyerek otomatik yükleme için ayarlanmalıdır <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> değeriyle VSPackage'ı üzerinde <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionOpening_guid>. Çözüm yükü Yöneticisi'ni, sonra etkinleştirilebilir <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> yöntemi.  
  
> [!NOTE]
>  Autoloading paketler hakkında daha fazla bilgi için bkz. [VSPackage yükleme](../extensibility/loading-vspackages.md).  
  
 Visual Studio etkinleştirilmesi için yalnızca son çözüm yükleme yöneticisi algılar olduğundan, genel çözüm yük yöneticileri olup var olan bir yükleme yöneticisi kendilerini etkinleştirmeden önce her zaman algılanmalıdır. Çözüm Service'i GetProperty() çağırır <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4> döndürür `null`, hiçbir etkin çözüm yükü Yöneticisi yoktur. Null döndürmezse, nesnenin, çözüm yükleme yöneticisi ile aynı olup olmadığını denetleyin.  
  
 VSPackage'ı yalnızca birkaç çözüm türlerini yönetmek için çözüm yükleme yöneticisi geliyorsa, çözüm yükleme olaylarının abone olabilir (çağırarak <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.AdviseSolutionEvents%2A>) ve olay işleyicisi <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeOpenSolution%2A> çözüm yük Yöneticisi'ni etkinleştirmek için.  
  
 Yalnızca özel çözümler yönetmek için çözüm yükleme yöneticisi geliyorsa, etkinleştirme bilgilerini çözüm dosyasının bir parçası olarak kalıcı. Bunu yapmak için <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.WriteSolutionProps%2A> öncesi çözüm bölümü için.  
  
 Belirli bir çözüm yük yöneticileri devre dışı kendileri de <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents.OnAfterCloseSolution%2A> diğer çözüm yük yöneticileri ile çakışmaması sırayla olay işleyicisi.  
  
 Genel proje yükleme öncelikleri (örneğin, bir seçenekler sayfası üzerinde ayarlanan özellikleri) kalıcı hale getirmek için çözüm Yükleme Yöneticisi'nde etkinleştirebilirsiniz. yalnızca bir çözüm yükleme yöneticisi gerekiyorsa <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents2.OnAfterOpenProject%2A> olay işleyicisi, çözüm özellikleri ayarı daha sonra kalıcı olması Çözüm yükleme yöneticisi devre dışı bırakın.  
  
## <a name="handling-solution-load-events"></a>Çözüm yükleme olayları işleme  
 Çözüm yükü olaylarına abone olmak için çağrı <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.AdviseSolutionEvents%2A> çözüm Yükleme Yöneticisi'ni etkinleştirdiğinizde. Uygularsanız <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents>, öncelikleri yüklenirken farklı projesiyle ilgili olaylara yanıt verebilir.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeOpenSolution%2A>: Bir çözüm açılmadan önce bu harekete geçirilir. Öncelik Çözümdeki projeler için proje değiştirmek için kullanabilirsiniz.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeBackgroundSolutionLoadBegins%2A>: Bu çözüm tamamen yüklendikten, ancak önce arka plan proje yüklenirken yeniden başladıktan sonra tetiklenir. Örneğin, kullanıcı yükü önceliğini projesini LoadIfNeeded bir erişebilir veya bu projenin bir arka plan yük başlar BackgroundLoad çözüm yükleme yöneticisi proje yükü önceliğini değişmiş olabilir.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnAfterBackgroundSolutionLoadComplete%2A>: Bir çözüm tam olarak başlangıçta yüklendikten sonra var olup olmadığını bir çözüm yükleme yöneticisi bu harekete geçirilir. Ayrıca arka plan yük ya da isteğe bağlı yükledikten sonra çözüm tam yüklü durumuna geldiğinde tetiklenir. Aynı anda <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionExistsAndFullyLoaded_guid> yeniden etkinleştirilir.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnQueryBackgroundLoadProjectBatch%2A>: Bu proje (veya projeleri) yüklenmesini önce harekete geçirilir. Projeleri yüklenmeden önce diğer arka plan işlemleri tamamlandığından emin olmak için ayarlanmış `pfShouldDelayLoadToNextIdle` için **true**.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeLoadProjectBatch%2A>: Bu projelerin bir toplu iş yaklaşık olarak yüklenmesine olduğunda tetiklenir. Varsa `fIsBackgroundIdleBatch` projeler varsa arka planda; yüklenecek true ise `fIsBackgroundIdleBatch` projeleri, örneğin kullanıcı, beklemedeki bir proje Çözüm Gezgini'nde genişletir, zaman uyumlu olarak bir kullanıcı isteği sonucunda yüklenecek false olur. Aksi takdirde yapılması gereken pahalı iş yapmak için uygulayabileceğiniz <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenProject%2A>.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnAfterLoadProjectBatch%2A>: Bu projeleri toplu yüklendikten sonra tetiklenir.  
  
## <a name="detecting-and-managing-solution-and-project-loading"></a>Algılama ve çözüm ve proje yüklemeyi yönetme  
 Projeler ve çözümler yükleme durumunu saptamak amacıyla çağrı <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.GetProperty%2A> aşağıdaki değerlerle:  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4>: `var` döndürür `true` çözüm ve tüm projeleri, aksi takdirde yüklü olduğunda `false`.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4>: `var` döndürür `true` projelerin bir batch şu anda yüklenir, arka planda, aksi takdirde `false`.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4>: `var` döndürür `true` projelerin bir batch şu anda yüklenir, zaman uyumlu olarak kullanıcı komutu ya da diğer açık yük sonucunda aksi `false`.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID2>: `var` döndürür `true` çözümü şu anda, aksi takdirde kapatılıyorsa `false`.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID>: `var` döndürür `true` çözüm şu anda, aksi takdirde açıldığında `false`.  
  
  De (ne proje yükleme öncelikleri olursa olsun) projeler ve çözümler yüklenen aşağıdaki yöntemlerden birini çağırarak emin olabilirsiniz:  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution4.EnsureSolutionIsLoaded%2A>: Bu yöntemin çağrılması yöntemi döndürmeden önce yüklemek için bir çözüm içindeki projeleri zorlar.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution4.EnsureProjectIsLoaded%2A>: Bu yöntemi çağırmadan zorlayan projelerde `guidProject` yöntemi döndürmeden önce yüklenecek.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution4.EnsureProjectsAreLoaded%2A>: Bu yöntemi çağırmadan, projede zorlar `guidProjectID` yöntemi döndürmeden önce yüklenecek.  
  
> [!NOTE]
>  biçimindeki telefon numarasıdır. Varsayılan olarak yalnızca isteğe bağlı olan projelerin yüklenmesi ve arka plan yük öncelikleri yüklenir, ancak <xref:Microsoft.VisualStudio.Shell.Interop.__VSBSLFLAGS> bayrağı yönteme geçirilir, açıkça yüklemek için işaretlenmiş olanlar dışında tüm projeleri yüklenir.

