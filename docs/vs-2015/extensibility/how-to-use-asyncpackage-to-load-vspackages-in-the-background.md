---
title: 'Nasıl yapılır: AsyncPackage planda VSPackage sayfanızdaki | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: dedf0173-197e-4258-ae5a-807eb3abc952
caps.latest.revision: 9
ms.author: gregvanl
ms.openlocfilehash: d5bc0c22ff0a29984e59c30db6dc2b391bf007e0
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51778793"
---
# <a name="how-to-use-asyncpackage-to-load-vspackages-in-the-background"></a>Nasıl yapılır: AsyncPackage planda VSPackage'ı yüklemek için kullanın
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Yükleme ve VS paket başlatma disk g/ç neden olabilir. Böyle g/ç UI iş parçacığı üzerinde olursa bu yanıt hızını sorunlarına yol açabilir. Bunu ele almak için Visual Studio 2015 kullanıma sunulan <xref:Microsoft.VisualStudio.Shell.AsyncPackage> paketi yükleme arka plan iş parçacığında sağlayan sınıf.  
  
## <a name="creating-an-asyncpackage"></a>Bir sınıfta oluşturma  
 Bir VSIX projesi oluşturarak başlayın (**dosya / yeni / Project / Visual C# / genişletilebilirlik / VSIX projesi**) ve bir VSPackage'ı projeye ekleniyor (projeye sağ tıklayın ve **Ekle/yeni öğe / C# öğesi/genişletilebilirlik/Visual Studio Paketi**). Ardından, hizmetlerinizi oluşturup bu hizmetler, pakete ekleyin.  
  
1. Paketten türetilen <xref:Microsoft.VisualStudio.Shell.AsyncPackage>.  
  
2. Hizmetleri sorgulamak, yüklemek, paket neden olabilir sağlıyorsanız:  
  
    Visual Studio için paketinizi arka planda yükleme için güvenli olduğunu belirtmek için ve bu davranışı geri çevirmek için <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute> ayarlamalısınız **AllowsBackgroundLoading** özelliği true olarak öznitelik Oluşturucusu.  
  
   ```csharp  
   [PackageRegistration(UseManagedResourcesOnly = true, AllowsBackgroundLoading = true)]  
  
   ```  
  
    Visual Studio için hizmetinizde bir arka plan iş parçacığı oluşturmak güvenli olduğunu belirtmek için ayarlamalısınız <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttributeBase.IsAsyncQueryable%2A> özelliği true olarak <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute> Oluşturucusu.  
  
   ```csharp  
   [ProvideService(typeof(SMyTestService), IsAsyncQueryable = true)]  
  
   ```  
  
3. UI bağlamı yüklenen sonra belirtmeniz gerekir **PackageAutoLoadFlags.BackgroundLoad** için <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> bayrak değeri (0x2) paketinizin otomatik yükle giriş değeri olarak yazılamaz veya okunamaz.  
  
   ```csharp  
   [ProvideAutoLoad(UIContextGuid, PackageAutoLoadFlags.BackgroundLoad)]  
  
   ```  
  
4. Zaman uyumsuz başlatma iş yapmak için varsa, geçersiz kılmalıdır <xref:Microsoft.VisualStudio.Shell.AsyncPackage.InitializeAsync%2A>. Kaldırma **Initialize()** VSIX şablonuyla sağlanan yöntemi. ( **Initialize()** yönteminde **AsyncPackage** korumalı). Herhangi birini kullanabilmeniz için <xref:Microsoft.VisualStudio.Shell.AsyncPackage.AddService%2A> paketiniz için zaman uyumsuz bir hizmet eklemek için yöntemleri.  
  
    Not: çağrılacak **temel. InitializeAsync()**, kaynak kodunuzu değiştirebilirsiniz:  
  
   ```csharp  
   await base.InitializeAsync(cancellationToken, progress);  
   ```  
  
5. RPC (yordam çağrısı kaldırmak) yapmamak için zaman uyumsuz başlatma kodunuzdan ilgileniriz gerekir (içinde **InitializeAsync**). Çağırdığınızda bu oluşabilir <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> doğrudan veya dolaylı olarak.  Eşitleme yükleri gerekli olduğunda, UI iş parçacığı kullanan engeller <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory>. Varsayılan engelleme modelini RPC devre dışı bırakır. Bu, zaman uyumsuz görevleri bir RPC kullanmayı denerseniz, kullanıcı Arabirimi iş parçacığı kendisi, paketi yüklemek bekleyen ise, kilitlenme, anlamına gelir. Kodunuzu UI iş parçacığına benzer bir şey kullanarak gerekirse sıralamakta genel alternatiftir **birleştirilebilir görev fabrikasını**'s <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.SwitchToMainThreadAsync%2A> veya bir RPC kullanmaz başka bir mekanizma.  Kullanmayın **ThreadHelper.Generic.Invoke** veya genellikle UI iş parçacığına almak için bekliyor çağıran iş parçacığını engeller.  
  
    Not: Kullanmaktan kaçınmalısınız **GetService** veya **QueryService** içinde **InitializeAsync** yöntemi. Bu kullanmanız gerekiyorsa, kullanıcı Arabirimi iş parçacığına geçmeniz gerekir. Alternatif kullanmaktır <xref:Microsoft.VisualStudio.Shell.AsyncServiceProvider.GetServiceAsync%2A> gelen, **AsyncPackage** (için atama tarafından <xref:Microsoft.VisualStudio.Shell.Interop.IAsyncServiceProvider>.)  
  
   C# ' ta: bir AsyncPackage oluşturun:  
  
```csharp  
[PackageRegistration(UseManagedResourcesOnly = true, AllowsBackgroundLoading = true)]       
[ProvideService(typeof(SMyTestService), IsAsyncQueryable = true)]   
public sealed class TestPackage : AsyncPackage   
{   
    protected override Task InitializeAsync(System.Threading.CancellationToken cancellationToken, IProgress<ServiceProgressData> progress)   
    {               
        this.AddService(typeof(SMyTestService), CreateService, true);   
        return Task.FromResult<object>(null);   
    }   
}  
```  
  
## <a name="convert-an-existing-vspackage-to-asyncpackage"></a>Mevcut bir VSPackage AsyncPackage için Dönüştür  
 İşin çoğunu yeni oluşturma aynıdır **AsyncPackage**. 1 ile 5 yukarıdaki adımları izlemeniz gerekir. Aşağıdakilere çok dikkatli olması gerekir:  
  
1.  Kaldırmayı unutmayın **başlatmak** geçersiz kılma paketinizdeki vardı.  
  
2.  Kilitlenmeleri önlemek: olabilir, kodunuzda artık bir arka plan iş parçacığında gerçekleştirilmesi RPC gizli. Bir RPC yapıyorsanız emin olmanız gerekir (örneğin **GetService**), ana iş parçacığı (1) ya da geç yapmanız veya var (2) zaman uyumsuz bir API sürümünü kullanın (örneğin **Asyncpackage'dan**).  
  
3.  Çok sık iş parçacıkları arasında geçiş. Arka plan iş parçacığında oluşabilir iş yerelleştirmek deneyin. Bu yükleme süresini azaltır.  
  
## <a name="querying-services-from-asyncpackage"></a>AsyncPackage hizmetlerinden sorgulama  
 Bir **AsyncPackage** olabilir veya zaman uyumsuz olarak bağlı olarak çağıran yüklenmeyebilir. Örneğin,  
  
- Çağıranın çağrılırsa **GetService** veya **QueryService** (hem zaman uyumlu API) veya  
  
- Çağıranın çağrılırsa **IVsShell::LoadPackage** (veya **IVsShell5::LoadPackageWithContext**) veya  
  
- Yükleme kullanıcı Arabirimi bağlam tarafından tetiklenir, ancak UI bağlamı mekanizması, zaman uyumsuz olarak yükleyebilirsiniz belirtmedi  
  
  Ardından, paket zaman uyumlu olarak yüklenir.  
  
  UI iş parçacığı için söz konusu iş tamamlama engellenecek olsa paketinizi hala bir fırsat (zaman uyumsuz başlangıç aşamasında) UI iş parçacığından, çalışmaya olduğuna dikkat edin. Çağıranın kullanıyorsa **IAsyncServiceProvider** hizmetiniz için zaman uyumsuz olarak sorgu için sonra yükleme ve başlatma zaman uyumsuz olarak bunlar yok hemen engelleme elde edilen görev nesnesinde varsayılarak yapılır.  
  
  C# ' ta: hizmet zaman uyumsuz olarak sorgulayıp nasıl:  
  
```csharp  
using Microsoft.VisualStudio.Shell;   
using Microsoft.VisualStudio.Shell.Interop;   
  
IAsyncServiceProvider asyncServiceProvider = Package.GetService(typeof(SAsyncServiceProvider)) as IAsyncServiceProvider;   
IMyTestService testService = await ayncServiceProvider.GetServiceAsync(typeof(SMyTestService)) as IMyTestService;  
```

