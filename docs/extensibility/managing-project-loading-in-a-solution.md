---
title: Bir çözümde proje yüklemeyi yönetme | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- solutions, managing project loading
ms.assetid: 097c89d0-f76a-4aaf-ada9-9a778bd179a0
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 2ead4834f1d29baff099eedbf464c1ba6344ca6c
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49950205"
---
# <a name="manage-project-loading-in-a-solution"></a>Bir çözümde proje yüklemeyi yönetme
Visual Studio çözümleri, çok sayıda proje içerebilir. Varsayılan Visual Studio çözüm açıldığında bir çözümdeki tüm projeleri yüklemek ve bunların tümünü yükleme işlemini tamamlayana kadar projelerinden herhangi birinin erişmek kullanıcı izin vermeyecek şekilde davranışıdır. Proje yükleme işlemi iki dakikadan fazla en son, yüklenen projelerin sayısını ve projeleri toplam sayısını gösteren bir ilerleme çubuğu görüntülenir. Bir çözümde birden çok proje ile çalışırken, kullanıcı projeleri kaldırma, ancak bu yordamı bazı dezavantajları vardır: bir çözümü yeniden derle komutunu bir parçası olarak yüklenmemiş projeler oluşturulmadı ve IntelliSense açıklamaları türleri ve üyeleri kapalı projeleri görüntülenmez.  
  
 Geliştiriciler, çözüm yükleme sürelerinizi azaltabilir ve Proje Yöneticisi bir çözüm yük oluşturarak yükleme davranışını yönetin. Çözüm yükleme yöneticisi projeleri arka plan yapı başlatmadan önce yüklendiğinden emin olun, diğer arka plan görevleri tamamlanana kadar arka planda yükleniyor gecikme ve diğer proje yükü yönetim görevlerini gerçekleştirebilirsiniz.  
  
## <a name="create-a-solution-load-manager"></a>Çözüm yükü Yöneticisi oluşturma  
 Geliştiriciler oluşturabileceğiniz bir çözüm yükü Yöneticisi uygulayarak <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadManager> ve Visual Studio çözüm yükleme yöneticisi etkin olduğunu bildiren.  
  
### <a name="activate-a-solution-load-manager"></a>Bir çözüm Yükleme Yöneticisi'ni etkinleştir  
 Çözüm yükleme etkinleştirmek istediğiniz zaman Visual Studio bildirmek için visual Studio Yöneticisi belirli bir anda yalnızca bir çözüm yükleme yöneticisi sağlar. İkinci bir çözüm yükleme yöneticisi daha sonra etkinleştirilmişse, çözüm yükleme yöneticinize kesilir.  
  
 Edinmeniz gerekir <xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution> ayarlayın ve hizmet <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4> özelliği:  
  
```csharp  
IVsSolution pSolution = GetService(typeof(SVsSolution)) as IVsSolution;  
object objLoadMgr = this;   //the class that implements IVsSolutionManager  
pSolution.SetProperty((int)__VSPROPID4.VSPROPID_ActiveSolutionLoadManager, objLoadMgr);  
```  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadManager.OnDisconnect%2A> Visual Studio kapatılıyor olduğunda veya farklı bir paket etkin çözüm yükü Yöneticisi çağırarak edildiğinde yöntemi çağrıldığında <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.SetProperty%2A> ile <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4> özelliği.  
  
#### <a name="strategies-for-different-kinds-of-solution-load-manager"></a>Çözüm yükleme yöneticisi çeşitli stratejileri  
 Çözüm yükü yöneticileri yönetmek için gereken çözümlerinin türlerine bağlı olarak, farklı şekillerde uygulayabilir.  
  
 Genel yükleme çözümü yönetmek için çözüm yükleme yöneticisi geliyorsa, VSPackage bir parçası olarak uygulanabilir. Paket ekleyerek otomatik yükleme için ayarlanmalıdır <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> değeriyle VSPackage'ı üzerinde <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionOpening_guid>. Çözüm yükü Yöneticisi'ni, sonra etkinleştirilebilir <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> yöntemi.  
  
> [!NOTE]
>  Autoloading paketler hakkında daha fazla bilgi için bkz. [VSPackage yükleme](../extensibility/loading-vspackages.md).  
  
 Visual Studio etkinleştirilmesi için yalnızca son çözüm yükleme yöneticisi algılar olduğundan, genel çözüm yük yöneticileri olup var olan bir yükleme yöneticisi kendilerini etkinleştirmeden önce her zaman algılanmalıdır. Çağırma varsa `GetProperty()` çözüm Service'i <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4> döndürür `null`, hiçbir etkin çözüm yükü Yöneticisi yoktur. Null döndürmezse, nesnenin, çözüm yükleme yöneticisi ile aynı olup olmadığını denetleyin.  
  
 VSPackage'ı yalnızca birkaç çözüm türlerini yönetmek için çözüm yükleme yöneticisi geliyorsa, çözüm yükleme olaylarının abone olabilir (çağırarak <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.AdviseSolutionEvents%2A>) ve olay işleyicisi <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeOpenSolution%2A> çözüm yük Yöneticisi'ni etkinleştirmek için.  
  
 Yalnızca özel çözümler yönetmek için çözüm yükleme yöneticisi geliyorsa, etkinleştirme bilgilerini çözüm dosyasının bir parçası olarak çağırarak kalıcı yapılabilecek <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.WriteSolutionProps%2A> öncesi çözüm bölümü için.  
  
 Belirli bir çözüm yük yöneticileri devre dışı kendileri de <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents.OnAfterCloseSolution%2A> diğer çözüm yük yöneticileri ile çakışmaması sırayla olay işleyicisi.  
  
 Genel proje yükü özellikleri (örneğin, bir seçenekler sayfası üzerinde ayarlanan özellikleri) kalıcı hale getirmek için çözüm Yükleme Yöneticisi'nde etkinleştirebilirsiniz. yalnızca bir çözüm yükleme yöneticisi gerekiyorsa <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenProject%2A> olay işleyicisi, çözüm özellikleri ayarı daha sonra kalıcı olması Çözüm yükleme yöneticisi devre dışı bırakın.  
  
## <a name="handle-solution-load-events"></a>Çözüm yükleme olaylarını işleme  
 Çözüm yükü olaylarına abone olmak için çağrı <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.AdviseSolutionEvents%2A> çözüm Yükleme Yöneticisi'ni etkinleştirdiğinizde. Uygularsanız <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents>, özellikleri yükleniyor farklı projesiyle ilgili olaylara yanıt verebilir.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeOpenSolution%2A>: Bir çözüm açılmadan önce bu olay harekete geçirilir.
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeBackgroundSolutionLoadBegins%2A>: Çözüm tamamen yüklendikten, ancak önce arka plan proje yüklenirken yeniden başladıktan sonra bu bu olay tetiklenir.
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnAfterBackgroundSolutionLoadComplete%2A>: Bir çözüm tam olarak başlangıçta yüklendikten sonra var olup olmadığını bir çözüm yükleme yöneticisi bu olay harekete geçirilir. Ayrıca arka plan yük ya da isteğe bağlı yükledikten sonra çözüm tam yüklü durumuna geldiğinde tetiklenir. Aynı anda <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionExistsAndFullyLoaded_guid> yeniden etkinleştirilir.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnQueryBackgroundLoadProjectBatch%2A>: Bir proje (veya projeleri) yüklenmesini önce bu olay harekete geçirilir. Projeleri yüklenmeden önce diğer arka plan işlemleri tamamlandığından emin olmak için ayarlanmış `pfShouldDelayLoadToNextIdle` için **true**.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeLoadProjectBatch%2A>: Projelerin bir toplu iş yaklaşık olarak yüklenmesine olduğunda bu olay harekete geçirilir. Varsa `fIsBackgroundIdleBatch` projeler varsa arka planda; yüklenecek true ise `fIsBackgroundIdleBatch` projeleri, örneğin kullanıcı, beklemedeki bir proje Çözüm Gezgini'nde genişletir, zaman uyumlu olarak bir kullanıcı isteği sonucunda yüklenecek false olur. Aksi takdirde yapılması gereken pahalı işlerini gerçekleştirmek için bu olay işleyebilir <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenProject%2A>.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnAfterLoadProjectBatch%2A>: Projeleri toplu yüklendikten sonra bu olay harekete geçirilir.  
  
## <a name="detect-and-manage-solution-and-project-loading"></a>Algılama ve çözüm ve proje yüklemeyi yönetme  
 Projeler ve çözümler yükleme durumunu saptamak amacıyla çağrı <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.GetProperty%2A> aşağıdaki değerlerle:  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4>: `var` döndürür `true` çözüm ve tüm projeleri, aksi takdirde yüklü olduğunda `false`.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4>: `var` döndürür `true` projelerin bir batch şu anda arka planda, aksi takdirde yüklenirken, `false`.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4>: `var` döndürür `true` projelerin bir batch şu anda zaman uyumlu olarak kullanıcı komutu ya da diğer açık yük sonucunda Aksi takdirde yüklenirken, `false`.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID2>: `var` döndürür `true` çözümü şu anda, aksi takdirde kapatılıyorsa `false`.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID>: `var` döndürür `true` çözüm şu anda, aksi takdirde açıldığında `false`.  
  
  Ayrıca projeler ve çözümler aşağıdaki yöntemlerden birini çağırarak yüklendiğinden emin olun:  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution4.EnsureSolutionIsLoaded%2A>: Bu yöntemin çağrılması yöntemi döndürmeden önce yüklemek için bir çözüm içindeki projeleri zorlar.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution4.EnsureProjectIsLoaded%2A>: Bu yöntemi çağırmadan zorlayan projelerde `guidProject` yöntemi döndürmeden önce yüklenecek.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution4.EnsureProjectsAreLoaded%2A>: Bu yöntemi çağırmadan, projede zorlar `guidProjectID` yöntemi döndürmeden önce yüklenecek.  
