---
title: 'Nasıl yapılır: zaman uyumsuz bir hizmet sağlamak | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0448274c-d3d2-4e12-9d11-8aca78a1f3f5
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 5e57de7ca683678441b4e0908110e8e651930b64
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53061620"
---
# <a name="how-to-provide-an-asynchronous-visual-studio-service"></a>Nasıl yapılır: bir zaman uyumsuz Visual Studio hizmeti sağlama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

UI iş parçacığını engellemeden bir hizmet elde etmek istiyorsanız, zaman uyumsuz bir hizmet oluşturma ve arka plan iş parçacığında paketi gerekir. Bu amaçla kullanabileceğiniz bir <xref:Microsoft.VisualStudio.Shell.AsyncPackage> yerine <xref:Microsoft.VisualStudio.Shell.Package>ve hizmeti ile özel zaman uyumsuz yöntemler zaman uyumsuz paketin ekleyin

 Zaman uyumlu Visual Studio hizmetleri sağlama hakkında daha fazla bilgi için bkz: [nasıl yapılır: bir hizmet sağlamak](../extensibility/how-to-provide-a-service.md).

## <a name="implementing-an-asynchronous-service"></a>Uyumsuz bir hizmet uygulama

1.  VSIX projesi oluşturun (**dosya / yeni / Project / Visual C# / Extensiblity / VSIX projesi**). Projeyi adlandırın **TestAsync**.

2.  Bir VSPackage'ı projeye ekleyin. ' Nde proje düğümüne seçin **Çözüm Gezgini** tıklatıp **Ekle / yeni öğe / Visual C# öğeleri / genişletilebilirlik / Visual Studio paket**. Bu dosya adı **TestAsyncPackage.cs**.

3.  Paket yerine AsyncPackage devralmak için paket TestAsyncPackage.cs değiştirin:

    ```csharp
    public sealed class TestAsyncPackage : AsyncPackage
    ```

4.  Bir hizmeti uygulamak için üç tür oluşturmanız gerekir:

    -   Hizmeti tanımlayan bir arabirim. Bu arabirimlerin çoğu boştur, diğer bir deyişle, bunlar hiçbir yöntemleri vardır.

    -   Hizmet arabirimi açıklayan bir arabirim. Bu arabirim, uygulanacak yöntemleri içerir.

    -   Hem hizmet hem de hizmet arabirimi uygulayan bir sınıf.

5.  Aşağıdaki örnek, üç tür çok basit bir uygulamasını gösterir. Hizmet sınıfının oluşturucusu, hizmet sağlayıcısı ayarlamanız gerekir. Bu örnekte yalnızca hizmet paketi kod dosyasına ekleyeceğiz.

6.  Aşağıdaki using deyimlerini için paket dosyası:

    ```csharp
    using System.Threading;
    using System.Threading.Tasks;
    using System.Runtime.CompilerServices;
    using System.IO;
    ```

7.  Zaman uyumsuz bir hizmet uygulaması aşağıda verilmiştir. Zaman uyumlu bir hizmet sağlayıcısı yerine zaman uyumsuz bir hizmet sağlayıcısı oluşturucuda ayarlanacak gerektiğini unutmayın:

    ```
    public class TextWriterService : STextWriterService, ITextWriterService
    {
        private Microsoft.VisualStudio.Shell.IAsyncServiceProvider serviceProvider;
        public TextWriterService(Microsoft.VisualStudio.Shell.IAsyncServiceProvider provider)
        {
            serviceProvider = provider;
        }
        public async System.Threading.Tasks.Task WriteLineAsync(string path, string line)
        {
            StreamWriter writer = new StreamWriter(path);
            await writer.WriteLineAsync(line);
            writer.Close();
        }
        public TaskAwaiter GetAwaiter()
        {
            return new TaskAwaiter();
        }
    }
    public interface STextWriterService
    {
    }
    public interface ITextWriterService
    {
        System.Threading.Tasks.Task WriteLineAsync(string path, string line);
        TaskAwaiter GetAwaiter();
    }
    ```

## <a name="registering-a-service"></a>Bir hizmeti kaydediliyor
 Bir hizmeti kaydetmek için ekleme <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute> hizmeti sağlayan paket. Zaman uyumlu bir hizmet kayıt gelen iki fark vardır:

- Autoloading varsa paket eklemelisiniz <xref:Microsoft.VisualStudio.Shell.PackageAutoLoadFlags> BackgroundLoad değer özniteliğine. Autoloading VSPackage'ları hakkında daha fazla bilgi için bkz: [VSPackage yükleme](../extensibility/loading-vspackages.md).

- Eklemelisiniz **AllowsBackgroundLoading = true** alanı <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute>. PackageRegistrationAttribute hakkında daha fazla bilgi için bkz: [kaydetme ve kaydını kaldırma VSPackages](../extensibility/registering-and-unregistering-vspackages.md).

  İşte bir örnek bir sınıfta bir zaman uyumsuz hizmet kaydı ile::

```csharp
[ProvideService((typeof(STextWriterService)), IsAsyncQueryable = true)]
[ProvideAutoLoad(UIContextGuids80.SolutionExists, PackageAutoLoadFlags.BackgroundLoad)]
[PackageRegistration(UseManagedResourcesOnly = true, AllowsBackgroundLoading = true)]
[Guid(TestAsyncPackage.PackageGuidString)]
public sealed class TestAsyncPackage : AsyncPackage
{. . . }
```

## <a name="adding-a-service"></a>Bir hizmet ekleme

1.  TestAsyncPackage.cs içinde kaldırmak `Initialize()` yöntemi ve geçersiz kılma `InitializeAsync()` yöntemi. Hizmet Ekle ve hizmetleri oluşturmak için bir geri çağırma yöntemi ekleyin. Bir hizmeti eklemek, zaman uyumsuz Başlatıcı bir örneği aşağıda verilmiştir:

    ```
    protected override async System.Threading.Tasks.Task InitializeAsync(CancellationToken cancellationToken, IProgress<ServiceProgressData> progress)
    {
        this.AddService(typeof(STextWriterService), CreateService);

        await base.InitializeAsync(cancellationToken, progress);
    }

    ```

2.  Microsoft.VisualStudio.Shell.Interop.14.0.DesignTime.dll bir başvuru ekleyin.

3.  Geri arama yöntemi oluşturur ve hizmet döndüren zaman uyumsuz bir yöntem uygulayın.

    ```csharp
    public async System.Threading.Tasks.Task<object> CreateService(IAsyncServiceContainer container, CancellationToken cancellationToken, Type serviceType)
    {
        STextWriterService service = null;
        await System.Threading.Tasks.Task.Run(() => {
                    service = new TextWriterService(this);
             });

        return service;
    }

    ```

## <a name="using-a-service"></a>Bir hizmet kullanma
 Artık hizmet alma ve onun yöntemlerini kullanın.

1.  Bu Başlatıcı göstereceğiz, ancak herhangi bir hizmet kullanmak istediğiniz hizmet alabilirsiniz.

    ```csharp
    protected override async System.Threading.Tasks.Task InitializeAsync(CancellationToken cancellationToken, IProgress<ServiceProgressData> progress)
    {
        this.AddService(typeof(STextWriterService), CreateService);

        ITextWriterService textService = await this.GetServiceAsync(typeof(STextWriterService)) as ITextWriterService;

        await writer.WriteLineAsync(<userpath>), "this is a test");

        await base.InitializeAsync(cancellationToken, progress);
    }

    ```

     Değiştirmeyi unutmayın  *\<userpath >* makinenizde mantıklı yolu ve dosya adı!

2.  Kodunu derleme ve çalıştırma. Visual Studio'nun deneysel örneğinde göründüğünde, bir çözüm açın. Bu otomatik yükleme için AsyncPackage neden olur. Başlatıcı çalıştırıldığında, belirtilen konumda bir dosya bulmanız gerekir.

## <a name="using-an-asynchronous-service-in-a-command-handler"></a>Komut işleyicisinde uyumsuz bir hizmet kullanma
 Bir menü komutunu uyumsuz bir hizmet kullanmaya ilişkin bir örnek aşağıda verilmiştir. Hizmetini zaman uyumsuz olmayan diğer yöntemleri kullanmayı burada gösterilen yordam kullanabilirsiniz.

1.  Bir menü komutu projenize ekleyin. (İçinde **Çözüm Gezgini**, proje düğümünü sağ tıklatın ve seçin seçin **Ekle / yeni öğe / genişletilebilirlik / özel komut**.) Komut dosyası adı **TestAsyncCommand.cs.**

2.  Özel komut şablonu yeniden ekler `Initialize()` TestAsyncPackage.cs dosyasına komutu başlatmak için yöntemi. Initialize() yöntemi başlatan komut satırı kopyalayın. Şu şekilde görünmelidir:

    ```
    TestAsyncCommand.Initialize(this);
    ```

     Bu satıra taşımak `InitializeAsync()` AsyncPackageForService.cs dosyasındaki yöntemi. Bu zaman uyumsuz bir başlatma olduğundan, komutu kullanarak başlatılmadan önce ana iş parçacığından geçmelidir <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.SwitchToMainThreadAsync%2A>. Bunu artık şöyle görünmelidir:

    ```csharp

    protected override async System.Threading.Tasks.Task InitializeAsync(CancellationToken cancellationToken, IProgress<ServiceProgressData> progress)
    {
        await ThreadHelper.JoinableTaskFactory.SwitchToMainThreadAsync();
        TestAsyncCommand.Initialize(this);

        this.AddService(typeof(STextWriterService), CreateService);

        ITextWriterService textService =
           await this.GetServiceAsync(typeof(STextWriterService)) as ITextWriterService;

        await writer.WriteLineAsync((<userpath>, "this is a test");

        await base.InitializeAsync(cancellationToken, progress);
    }

    ```

3.  Silme `Initialize()` yöntemi.

4.  TestAsyncCommand.cs dosyasında `MenuItemCallback()` yöntemi. Yöntemin gövdesi silin.

5.  Kullanarak bir ekleme deyimi:

    ```
    using System.IO;
    ```

6.  Adlı bir zaman uyumsuz bir yöntem ekleyin `GetAsyncService()`, hizmet alır ve kendi yöntemlerini kullanır:

    ```csharp
    private async System.Threading.Tasks.Task GetAsyncService()
    {
        ITextWriterService textService =
           this.ServiceProvider.GetService(typeof(STextWriterService))
              as ITextWriterService;
        // don’t forget to change <userpath> to a local path
        await writer.WriteLineAsync((<userpath>),"this is a test");
       }

    ```

7.  Bu yöntemi çağırın `MenuItemCallback()` yöntemi:

    ```
    private void MenuItemCallback(object sender, EventArgs e)
    {
        GetAsyncService();
    }

    ```

8.  Çözümü derleyin ve hata ayıklamaya başlayın. Visual Studio'nun deneysel örneğinde göründüğünde, Git **Araçları** menü ve Ara **çağırma TestAsyncCommand** menü öğesi. Düğmeyi tıklattığınızda TextWriterService, belirtilen dosyaya yazar. (Komutu çağırmadan ayrıca yüklemek paket neden olduğundan, bir çözümü açmak gerekmez.)

## <a name="see-also"></a>Ayrıca Bkz.
 [Hizmetleri Kullanma ve Sağlama](../extensibility/using-and-providing-services.md)
