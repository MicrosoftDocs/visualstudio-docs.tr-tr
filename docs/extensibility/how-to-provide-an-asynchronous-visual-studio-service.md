---
title: 'Nasıl yapılır: bir zaman uyumsuz Visual Studio hizmeti sağlama | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 0448274c-d3d2-4e12-9d11-8aca78a1f3f5
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: c022f1a039aacee3599dd680adfa92a9404b34b8
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49915678"
---
# <a name="how-to-provide-an-asynchronous-visual-studio-service"></a>Nasıl yapılır: zaman uyumsuz bir Visual Studio hizmeti sağlama
UI iş parçacığını engellemeden bir hizmet elde etmek istiyorsanız, zaman uyumsuz bir hizmet oluşturma ve arka plan iş parçacığında paketi gerekir. Bu amaçla kullanabileceğiniz bir <xref:Microsoft.VisualStudio.Shell.AsyncPackage> yerine <xref:Microsoft.VisualStudio.Shell.Package>ve hizmeti ile özel zaman uyumsuz yöntemler zaman uyumsuz paketin ekleyin.
  
 Zaman uyumlu Visual Studio hizmetleri sağlama hakkında daha fazla bilgi için bkz: [nasıl yapılır: bir hizmet sağlamak](../extensibility/how-to-provide-a-service.md).  
  
## <a name="implement-an-asynchronous-service"></a>Zaman uyumsuz bir hizmet ekleme  
  
1.  VSIX projesi oluşturun (**dosya** > **yeni** > **proje** > **Visual C#**  >  **Extensiblity** > **VSIX projesi**). Projeyi adlandırın **TestAsync**.  
  
2.  Bir VSPackage'ı projeye ekleyin. ' Nde proje düğümüne seçin **Çözüm Gezgini** tıklatıp **Ekle** > **yeni öğe** > **Visual C# öğeleri**  >  **Genişletilebilirlik** > **Visual Studio paket**. Bu dosya adı *TestAsyncPackage.cs*.  
  
3.  İçinde *TestAsyncPackage.cs*, devralınacak paketi değiştirmek `AsyncPackage` yerine `Package`:  
  
    ```csharp  
    public sealed class TestAsyncPackage : AsyncPackage  
    ```  
  
4.  Bir hizmeti uygulamak için üç tür oluşturmanız gerekir:  
  
    -   Bir arabirim hizmeti tanımlar. Bu arabirimlerin çoğu boştur, yalnızca hizmet sorgulama için kullanılması gibi diğer bir deyişle, yöntemlerin hiçbiri sahiptirler.
  
    -   Hizmet arabirimi açıklayan bir arabirim. Bu arabirim, uygulanacak yöntemleri içerir.  
  
    -   Hem hizmet hem de hizmet arabirimi uygulayan bir sınıf.  
  
5.  Aşağıdaki örnek, üç tür çok basit bir uygulamasını gösterir. Hizmet sınıfının oluşturucusu, hizmet sağlayıcısı ayarlamanız gerekir. Bu örnekte yalnızca hizmet paketi kod dosyasına ekleyeceğiz.  
  
6.  Aşağıdaki using deyimlerini için paket dosyası:  
  
    ```csharp  
    using System.Threading;  
    using System.Threading.Tasks;  
    using System.Runtime.CompilerServices;  
    using System.IO;
    using Microsoft.VisualStudio.Threading;
    using IAsyncServiceProvider = Microsoft.VisualStudio.Shell.IAsyncServiceProvider;
    using Task = System.Threading.Tasks.Task;
    ```  
  
7.  Zaman uyumsuz bir hizmet uygulaması aşağıda verilmiştir. Zaman uyumlu bir hizmet sağlayıcısı yerine zaman uyumsuz bir hizmet sağlayıcısı oluşturucuda ayarlanacak gerektiğini unutmayın:  
  
    ```csharp
    public class TextWriterService : STextWriterService, ITextWriterService  
    {  
        private IAsyncServiceProvider asyncServiceProvider;  
        
        public TextWriterService(IAsyncServiceProvider provider)  
        {
            // constructor should only be used for simple initialization
            // any usage of Visual Studio service, expensive background operations should happen in the
            // asynchronous InitializeAsync method for best performance
            asyncServiceProvider = provider;  
        }
        
        public async Task InitializeAsync(CancellationToken cancellationToken)
        {
            await TaskScheduler.Default;
            // do background operations that involve IO or other async methods

            await this.JoinableTaskFactory.SwitchToMainThreadAsync(cancellationToken);               
            // query Visual Studio services on main thread unless they are documented as free threaded explicitly.
            // The reason for this is the final cast to service interface (such as IVsShell) may involve COM operations to add/release references.

            IVsShell vsShell = this.asyncServiceProvider.GetServiceAsync(typeof(SVsShell)) as IVsShell;
            // use Visual Studio services to continue initialization
        }
        
        public async Task WriteLineAsync(string path, string line)  
        {  
            StreamWriter writer = new StreamWriter(path);  
            await writer.WriteLineAsync(line);  
            writer.Close();  
        }  
    }  

    public interface STextWriterService  
    {  
    }  
    
    public interface ITextWriterService   
    {  
        System.Threading.Tasks.Task WriteLineAsync(string path, string line);  
    }  
    ```  
  
## <a name="register-a-service"></a>Bir hizmeti kaydedin  
 Bir hizmeti kaydetmek için ekleme <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute> hizmeti sağlayan paket. Farklı bir zaman uyumlu bir hizmet kayıt için hem paket hem de hizmet yükleme zaman uyumsuz desteklediğinden emin olmanız için gerekenler:
  
- Eklemelisiniz **AllowsBackgroundLoading = true** alanı <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute> paket başlatılabilir zaman uyumsuz olarak PackageRegistrationAttribute hakkında daha fazla bilgi sağlamak için bkz: [kaydedin ve VSPackage kaydı](../extensibility/registering-and-unregistering-vspackages.md).  
  
- Eklemelisiniz **IsAsyncQueryable = true** alanı <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute> hizmet örneği zaman uyumsuz olarak başlatılabilir emin olmak için.

  İşte bir örnek bir `AsyncPackage` uyumsuz bir hizmet kaydı ile:
  
```csharp  
[ProvideService((typeof(STextWriterService)), IsAsyncQueryable = true)]  
[ProvideAutoLoad(UIContextGuids80.SolutionExists, PackageAutoLoadFlags.BackgroundLoad)]  
[PackageRegistration(UseManagedResourcesOnly = true, AllowsBackgroundLoading = true)]   
[Guid(TestAsyncPackage.PackageGuidString)]  
public sealed class TestAsyncPackage : AsyncPackage  
{. . . }  
```  
  
## <a name="add-a-service"></a>Hizmet ekleme  
  
1.  İçinde *TestAsyncPackage.cs*, kaldırma `Initialize()` yöntemi ve geçersiz kılma `InitializeAsync()` yöntemi. Hizmet Ekle ve hizmetleri oluşturmak için bir geri çağırma yöntemi ekleyin. Bir hizmeti eklemek, zaman uyumsuz Başlatıcı bir örneği aşağıda verilmiştir:  
  
    ```csharp
    protected override async Task InitializeAsync(CancellationToken cancellationToken, IProgress<ServiceProgressData> progress)  
    {  
        await base.InitializeAsync(cancellationToken, progress);  
        this.AddService(typeof(STextWriterService), CreateTextWriterService);
    }  
  
    ```  
  
2.  Bir başvuru ekleyin *Microsoft.VisualStudio.Shell.Interop.14.0.DesignTime.dll*.  
  
3.  Geri arama yöntemi oluşturur ve hizmet döndüren zaman uyumsuz bir yöntem uygulayın.  
  
    ```csharp  
    public async Task<object> CreateTextWriterService(IAsyncServiceContainer container, CancellationToken cancellationToken, Type serviceType)  
    {  
        TextWriterService service = new TextWriterService(this);  
        await service.InitializeAsync(cancellationToken);
        return service;
    }  
  
    ```  
  
## <a name="use-a-service"></a>Bir hizmet kullanın  
 Artık hizmet alma ve onun yöntemlerini kullanın.  
  
1.  Bu Başlatıcı göstereceğiz, ancak herhangi bir hizmet kullanmak istediğiniz hizmet alabilirsiniz.  
  
    ```csharp  
    protected override async System.Threading.Tasks.Task InitializeAsync(CancellationToken cancellationToken, IProgress<ServiceProgressData> progress)  
    {  
        await base.InitializeAsync(cancellationToken, progress);  
        this.AddService(typeof(STextWriterService), CreateTextWriterService);  
  
        ITextWriterService textService = await this.GetServiceAsync(typeof(STextWriterService)) as ITextWriterService;  
  
        await textService.WriteLineAsync(<userpath>), "this is a test");  
    }  
  
    ```  
  
     Değiştirmeyi unutmayın  *\<userpath >* makinenizde mantıklı yolu ve dosya adı!  
  
2.  Kodunu derleme ve çalıştırma. Visual Studio'nun deneysel örneğinde göründüğünde, bir çözüm açın. Bu neden `AsyncPackage` otomatik yükleme için. Başlatıcı çalıştırıldığında, belirtilen konumda bir dosya bulmanız gerekir.  
  
## <a name="use-an-asynchronous-service-in-a-command-handler"></a>Komut işleyicisinde uyumsuz bir hizmet kullanın  
 Bir menü komutunu uyumsuz bir hizmet kullanmaya ilişkin bir örnek aşağıda verilmiştir. Hizmetini zaman uyumsuz olmayan diğer yöntemleri kullanmayı burada gösterilen yordam kullanabilirsiniz.  
  
1.  Bir menü komutu projenize ekleyin. (İçinde **Çözüm Gezgini**, proje düğümünü sağ tıklatın ve seçin seçin **Ekle** > **yeni öğe**  >   **Genişletilebilirlik** > **özel komut**.) Komut dosyası adı *TestAsyncCommand.cs*.  
  
2.  Özel komut şablonu yeniden ekler `Initialize()` yönteme *TestAsyncPackage.cs* komutu başlatmak için dosya. İçinde `Initialize()` yöntemini başlatan komut satırı kopyalayın. Şu şekilde görünmelidir:  
  
    ```csharp
    TestAsyncCommand.Initialize(this);  
    ```  
  
     Bu satıra taşımak `InitializeAsync()` yönteminde *AsyncPackageForService.cs* dosya. Bu zaman uyumsuz bir başlatma olduğundan, komutu kullanarak başlatılmadan önce ana iş parçacığından geçmelidir <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.SwitchToMainThreadAsync%2A>. Bunu artık şöyle görünmelidir:  
  
    ```csharp  
  
    protected override async System.Threading.Tasks.Task InitializeAsync(CancellationToken cancellationToken, IProgress<ServiceProgressData> progress)  
    {  
        await base.InitializeAsync(cancellationToken, progress);  
        this.AddService(typeof(STextWriterService), CreateTextWriterService);  

        ITextWriterService textService =   
           await this.GetServiceAsync(typeof(STextWriterService)) as ITextWriterService;  
  
        await textService.WriteLineAsync((<userpath>, "this is a test");  
  
        await this.JoinableTaskFactory.SwitchToMainThreadAsync(cancellationToken);  
        TestAsyncCommand.Initialize(this);
    }  
  
    ```  
  
3.  Silme `Initialize()` yöntemi.  
  
4.  İçinde *TestAsyncCommand.cs* dosya, bulma `MenuItemCallback()` yöntemi. Yöntemin gövdesi silin.  
  
5.  Kullanarak bir ekleme deyimi:  
  
    ```csharp 
    using System.IO;  
    ```  
  
6.  Adlı bir zaman uyumsuz bir yöntem ekleyin `UseTextWriterAsync()`, hizmet alır ve kendi yöntemlerini kullanır:  
  
    ```csharp  
    private async System.Threading.Tasks.Task UseTextWriterAsync()  
    {  
        // Query text writer service asynchronously to avoid a blocking call.
        ITextWriterService textService =   
           await AsyncServiceProvider.GlobalProvider.GetServiceAsync(typeof(STextWriterService))  
              as ITextWriterService;  

        // don't forget to change <userpath> to a local path  
        await textService.WriteLineAsync((<userpath>),"this is a test");  
       }  
  
    ```  
  
7.  Bu yöntemi çağırın `MenuItemCallback()` yöntemi:  
  
    ```csharp
    private void MenuItemCallback(object sender, EventArgs e)  
    {  
        UseTextWriterAsync();  
    }  
  
    ```  
  
8.  Çözümü derleyin ve hata ayıklamaya başlayın. Visual Studio'nun deneysel örneğinde göründüğünde, Git **Araçları** menü ve Ara **çağırma TestAsyncCommand** menü öğesi. Düğmeyi tıklattığınızda TextWriterService, belirtilen dosyaya yazar. (Komutu çağırmadan ayrıca yüklemek paket neden olduğundan, bir çözümü açmak gerekmez.)  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Hizmetleri sağlamak ve kullanın](../extensibility/using-and-providing-services.md)
