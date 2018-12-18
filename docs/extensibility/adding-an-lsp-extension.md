---
title: Dil sunucusu Protokolü uzantısı ekleme | Microsoft Docs
ms.custom: ''
ms.date: 11/14/2017
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: 52f12785-1c51-4c2c-8228-c8e10316cd83
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 7f2710693c7dae7c4238f9f31fbe8065d6864a19
ms.sourcegitcommit: be938c7ecd756a11c9de3e6019a490d0e52b4190
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50672970"
---
# <a name="add-a-language-server-protocol-extension"></a>Dil sunucusu Protokolü uzantısı ekleme

Dil sunucusu Protokolü (LSP) bir ortak dil çeşitli kod düzenleyicilerinden hizmet özellikler sağlamak için kullanılan, JSON RPC v2.0 biçiminde kuralıdır. Geliştiriciler protokolünü kullanarak, bir tek dil sunucu dil IntelliSense, hata tanılamaya gibi hizmet özellikleri sağlamak için tüm başvuruları, LSP destekleyen çeşitli kod düzenleyicilerinden vs. bulmak yazabilirsiniz. Geleneksel olarak, Visual Studio'da dil Hizmetleri ya da eklenebilir eksiksiz bir Visual Studio genişletilebilirlik API'leri kullanarak özel dil Hizmetleri yazarak veya söz dizimi vurgulama gibi temel işlevler sağlamak için TextMate dil bilgisi dosyaları kullanarak için daha zengin veriler sağlar. LSP üçüncü bir seçenek sunar. Şimdi desteği.

![Dil sunucusu Protokolü Hizmeti Visual Studio](media/lsp-service-in-VS.png)

## <a name="language-server-protocol"></a>Dil Sunucusu Protokolü

![Dil sunucusu Protokolü uygulaması](media/lsp-implementation.png)

Bu makalede, bir dil LSP tabanlı sunucusunun kullandığı Visual Studio uzantısı oluşturmayı açıklar. Bu, zaten bir LSP tabanlı dil sunucusu geliştirdik ve yalnızca Visual Studio ile tümleştirmek istediğiniz varsayılır.

Visual Studio içinde daha fazla destek için dil sunucular herhangi bir temel akış iletim mekanizma aracılığıyla istemci (Visual Studio) örneğin iletişim kurabilir:

* Standart giriş/çıkış akışları
* Adlandırılmış Kanallar
* Yuvalar (yalnızca TCP)

Visual Studio ürününün bir parçası olmayan yerleşik dil Hizmetleri desteği, Visual Studio'da ve LSP hedeftir. Visual Studio'da mevcut dil Hizmetleri (gibi C# ' ta) genişletmek için tasarlanmamıştır. Mevcut diller genişletmek için dil hizmetin genişletilebilirlik kılavuzuna başvurun. (örneğin, [.NET derleyici platformu "Roslyn"](../extensibility/dotnet-compiler-platform-roslyn-extensibility.md)).

Protokolü hakkında daha fazla bilgi için belgelere bakın [burada](https://github.com/Microsoft/language-server-protocol).

Nasıl oluşturulacağı hakkında daha fazla bilgi için örnek dil server veya Visual Studio Code içinde var olan dil sunucusu tümleştirme belgelerine bakın [burada](https://code.visualstudio.com/docs/extensions/example-language-server).

## <a name="language-server-protocol-features-supported"></a>Desteklenen dil sunucusu protokolü özellikleri

Aşağıdaki LSP özellikleri Visual Studio'da şimdiye desteklenir:

İleti | Visual Studio'da desteğine sahiptir
--- | ---
başlatma | Evet
başlatıldı | Evet
kapatma | Evet
Çıkış | Evet
$/ cancelRequest | Evet
Pencere/showMessage | Evet
Pencere/showMessageRequest | Evet
Pencere/logMessage | Evet
telemetri/olayı |
İstemci/registerCapability |
İstemci/unregisterCapability |
Çalışma alanı/didChangeConfiguration | Evet
workspace/didChangeWatchedFiles | Evet
Çalışma alanı/sembol | Evet
workspace/executeCommand | Evet
Çalışma alanı/applyEdit | Evet
textDocument/publishDiagnostics | Evet
textDocument/didOpen | Evet
textDocument/didChange | Evet
textDocument/willSave |
textDocument/willSaveWaitUntil |
textDocument/didSave | Evet
textDocument/didClose | Evet
textDocument/tamamlama | Evet
Tamamlanma/çözümleyin | Evet
textDocument/üzerine gelme | Evet
textDocument/signatureHelp | Evet
textDocument/başvuruları | Evet
textDocument/documentHighlight | Evet
textDocument/documentSymbol | Evet
textDocument ve biçimlendirme | Evet
textDocument/rangeFormatting | Evet
textDocument/onTypeFormatting |
textDocument/tanımı | Evet
textDocument/codeAction | Evet
textDocument/codeLens |
codeLens/çözümleyin |
textDocument/documentLink |
documentLink/çözümleyin |
textDocument/yeniden adlandırma | Evet

## <a name="getting-started"></a>Başlarken

> [!NOTE]
> Visual Studio 15,8 Preview 3, ortak dil sunucusu protokolü için desteği ile başlayarak, Visual Studio'da yerleşiktir.  LSP uzantıları önizlememiz kullanarak derlediyseniz, [dil sunucusu istemci VSIX](https://marketplace.visualstudio.com/items?itemName=vsext.LanguageServerClientPreview) sürümü, bunlar için 15,8 Preview 3 veya daha yüksek yükselttikten sonra çalışmayı durdurur.  Yeniden çalışma LSP uzantılarınızı almak için aşağıdakileri yapmanız gerekir:
>
> 1. Microsoft Visual Studio dil sunucusu protokolü Önizleme VSIX kaldırın.  15,8 Preview 4 ile başlayarak, Visual Studio'da bir yükseltme gerçekleştirmek için her seferinde sizi otomatik olarak algılar ve önizleme VSIX için yükseltme işlemi sırasında kaldırın.
>
> 2. En yeni önizleme olmayan sürümüne yönelik Nuget başvurunuz güncelleştirme [LSP paketleri](https://www.nuget.org/packages/Microsoft.VisualStudio.LanguageServer.Client).
>
> 3. Microsoft Visual Studio dil sunucusu protokolü Önizleme VSIX bağımlılığı VSIX bildiriminizi kaldırın.
>
> 4. Yükleme hedefi için alt sınır olarak Visual Studio 15,8 Preview 3, VSIX belirttiğinden emin olun.
>
> 5. Yeniden oluşturun ve yeniden dağıtın.

### <a name="create-a-vsix-project"></a>VSIX projesi oluşturun

Bir dil hizmeti uzantısı bir LSP tabanlı dil sunucusu kullanarak oluşturmak için ilk olarak sahip olduğunuzdan emin olun **Visual Studio uzantısı geliştirme** iş yükü VS Örneğiniz için yüklenmiş.

İleri giderek yeni bir boş VSIXProject oluşturma **dosya** > **yeni proje** > **Visual C#**  >   **Genişletilebilirlik** > **VSIX projesi**:

![VSIX projesi oluşturun](media/lsp-vsix-project.png)

### <a name="language-server-and-runtime-installation"></a>Dil sunucusu ve çalışma zamanı yükleme

Varsayılan olarak, Visual Studio'da LSP tabanlı dil sunucularını desteklemek için oluşturulan uzantıları dil sunucuları veya bunları yürütmek amacıyla gereken çalışma zamanlarını içermez. Uzantı geliştiricileri, dil sunucuları ve gerekli çalışma zamanları dağıtmaktan sorumludur. Bunu yapmak için birkaç yol vardır:

* Dil sunucuları içerik dosyaları içinde VSIX içine eklenebilir.
* Dil sunucusu yüklemek için MSI oluşturun ve/veya çalışma zamanları gerekli.
* Yönergeler, çalışma zamanları ve dil sunucularını almak nasıl Market bildiren kullanıcıları sağlar.

### <a name="textmate-grammar-files"></a>TextMate dil bilgisi dosyaları

LSP diller için metin renklendirmesi nasıl belirtimi içermez. Uzantı geliştiricileri, Visual Studio dillerinde özel renklendirme sağlamak için TextMate dil bilgisi dosyası kullanabilirsiniz. Özel TextMate dil bilgisi veya tema dosyaları eklemek için aşağıdaki adımları izleyin:

1. Uzantınız içinde "Dil" adlı bir klasör oluşturun (veya seçtiğiniz herhangi bir ad olabilir).

2. İçinde *Dilbilgisi* klasörü, herhangi bir dosyayı eklemek  *\*.tmlanguage*,  *\*.plist*,  *\*.tmtheme*, veya  *\*.json* özel renklendirme sağlayan istediğiniz dosyaları.

3. Sağ tıklatın ve dosyaları **özellikleri**. Değişiklik **derleme** eyleme **içerik** ve **VSIX Ekle** özelliği true.

4. Oluşturma bir *.pkgdef* dosya ve şuna benzer bir satır ekleyin:

   ```xml
   [$RootKey$\TextMate\Repositories]
   "MyLang"="$PackageFolder$\Grammars"
   ```

5. Sağ tıklatın ve dosyaları **özellikleri**. Değişiklik **derleme** eyleme **içerik** ve **VSIX Ekle** özelliği true.

Önceki adımları tamamladıktan sonra bir *Dilbilgisi* paket yüklemek için klasör eklenir dizini depo kaynağı olarak adlandırılan 'MyLang' ('MyLang' Kesinleştirme için yalnızca bir ad ve benzersiz bir dize olabilir). Tüm dil bilgisi (*.tmlanguage* dosyaları) ve tema dosyası (*.tmtheme* dosyaları) bu dizin toplanmış potentials ve TextMate ile sağlanan yerleşik dilbilgisi geçersiz kılar. Bildirilen uzantıları dilbilgisi dosyanın açılmasını dosya uzantısını eşleşirse, TextMate adım.

## <a name="create-a-simple-language-client"></a>Bir basit dil istemcisi oluşturma

### <a name="main-interface---ilanguageclientdotnetapimicrosoftvisualstudiolanguageserverclientilanguageclientviewvisualstudiosdk-2017"></a>Temel arabirim - [ILanguageClient](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient?view=visualstudiosdk-2017)

VSIX projeniz oluşturulduktan sonra aşağıdaki NuGet paketleri projeye ekleyin:

* [Microsoft.VisualStudio.LanguageServer.Client](https://www.nuget.org/packages/Microsoft.VisualStudio.LanguageServer.Client)

> [!NOTE]
> Önceki adımları tamamladıktan sonra NuGet paketi bir bağımlılık duruma getirdiğinizde, aynı zamanda Newtonsoft.Json ve StreamJsonRpc paketleri, projenize eklenir. **Bu yeni sürümleri Visual Studio sürümünde yüklü olmadığı sürece bu paketleri güncelleştirmez, uzantı hedeflerinizi**. Derlemeleri dahil edilmez VSIX'İNİZE--bunun yerine, Visual Studio Kurulum dizininden seçilir. Uzantınızı bir kullanıcının makine üzerinde yüklü değerinden daha yeni bir sürümü derlemelerine başvuran, *çalışmaz*.

Daha sonra uygulayan yeni bir sınıf oluşturabilirsiniz [ILanguageClient](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient?view=visualstudiosdk-2017) arabirimi, bir dil LSP tabanlı sunucuya bağlanan dil istemciler için gereken ana arabirimidir.

Bir örnek verilmiştir:

```csharp
namespace MockLanguageExtension
{
    [ContentType("bar")]
    [Export(typeof(ILanguageClient))]
    public class BarLanguageClient : ILanguageClient
    {
        public string Name => "Bar Language Extension";

        public IEnumerable<string> ConfigurationSections => null;

        public object InitializationOptions => null;

        public IEnumerable<string> FilesToWatch => null;

        public event AsyncEventHandler<EventArgs> StartAsync;
        public event AsyncEventHandler<EventArgs> StopAsync;

        public async Task<Connection> ActivateAsync(CancellationToken token)
        {
            await Task.Yield();

            ProcessStartInfo info = new ProcessStartInfo();
            info.FileName = Path.Combine(Path.GetDirectoryName(Assembly.GetExecutingAssembly().Location), "Server", @"MockLanguageServer.exe");
            info.Arguments = "bar";
            info.RedirectStandardInput = true;
            info.RedirectStandardOutput = true;
            info.UseShellExecute = false;
            info.CreateNoWindow = true;

            Process process = new Process();
            process.StartInfo = info;

            if (process.Start())
            {
                return new Connection(process.StandardOutput.BaseStream, process.StandardInput.BaseStream);
            }

            return null;
        }

        public async Task OnLoadedAsync()
        {
            await StartAsync.InvokeAsync(this, EventArgs.Empty);
        }

        public async Task OnServerInitializeFailedAsync(Exception e)
        {
            return Task.CompletedTask;
        }

        public async Task OnServerInitializedAsync()
        {
            return Task.CompletedTask;
        }
    }
}
```

Uygulanması gereken ana yöntemler şunlardır [OnLoadedAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.onloadedasync?view=visualstudiosdk-2017) ve [ActivateAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.activateasync?view=visualstudiosdk-2017). [OnLoadedAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.onloadedasync?view=visualstudiosdk-2017) Visual Studio, uzantı yüklemiş ve dil sunucunuzun başlatılması hazır olduğunda çağrılır. Bu yöntemde çağırabilirsiniz [StartAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.startasync?view=visualstudiosdk-2017) hemen dil sunucunun başlatılması, veya ek mantık yapın ve çağırma göstermek için temsilci [StartAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.startasync?view=visualstudiosdk-2017) daha sonra. **Dil sunucunuzu etkinleştirmek için belirli bir noktada StartAsync çağırmanız gerekir.**

[ActivateAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.activateasync?view=visualstudiosdk-2017) sonunda çağırarak çağrılan yöntem [StartAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.startasync?view=visualstudiosdk-2017) temsilci; dil sunucuyu başlatın ve bağlantı kurmak için mantığı içerir. Sunucuya yazma ve okuma sunucudan akışları içeren bir bağlantı nesnesi iade edilmesi gerekir. Burada oluşturulan özel durumlar yakalandı ve kullanıcı Visual Studio'da bir bilgi çubuğu mesaj yoluyla görüntülenir.

### <a name="activation"></a>Etkinleştirme

Dil istemci sınıfınız uygulandıktan sonra iki öznitelik nasıl bu Visual Studio'ya yüklenen ve etkinleştirilen tanımlamak de tanımlamanız gerekir:

```csharp
  [Export(typeof(ILanguageClient))]
  [ContentType("bar")]
```

### <a name="mef"></a>MEF

Visual Studio kullanan [MEF](https://github.com/Microsoft/vs-mef/blob/master/doc/index.md) (Extensibility Framework, genişletilebilirlik noktaları yönetmek için yönetilen). [Dışarı](/dotnet/api/system.componentmodel.composition.exportattribute) özniteliği için Visual Studio bu sınıf verilecek bir uzantı noktası olarak toplanmış ve uygun zamanda yüklü olduğunu gösterir.

MEF kullanmak için VSIX bildirimi bir varlığı olarak MEF tanımlamalısınız.

Kendi VSIX bildirim Tasarımcısı'nı açın ve gidin **varlıklar** sekmesinde:

![MEF varlık Ekle](media/lsp-add-asset.png)

Yeni bir varlık oluşturmak için Yeni'yi tıklatın:

![MEF varlık tanımlayın](media/lsp-define-asset.png)

* **Tür**: Microsoft.VisualStudio.MefComponent
* **Kaynak**: Geçerli çözümde bir proje
* **Proje**: [project]

### <a name="content-type-definition"></a>İçerik türü tanımı

Şu anda dil LSP tabanlı sunucu uzantınızı yüklemenin yalnızca dosya içerik türüne göre yoludur. Diğer bir deyişle, dil istemci sınıfınız tanımlarken (uygulayan [ILanguageClient](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient?view=visualstudiosdk-2017)), türlerini tanımlamak gerekir, dosyaları açıldı, uzantınızı yüklemeye neden olur. Ardından, tanımlanmış bir içerik türüyle eşleşen hiçbir dosya açıksa, uzantınızı yüklenmez.

Bu, bir veya daha fazla ContentTypeDefinition sınıfları tanımlama üzerinden gerçekleştirilir:

```csharp
namespace MockLanguageExtension
{
    public class BarContentDefinition
    {
        [Export]
        [Name("bar")]
        [BaseDefinition(CodeRemoteContentDefinition.CodeRemoteContentTypeName)]
        internal static ContentTypeDefinition BarContentTypeDefinition;


        [Export]
        [FileExtension(".bar")]
        [ContentType("bar")]
        internal static FileExtensionToContentTypeDefinition BarFileExtensionDefinition;
    }
}
```

Önceki örnekte, bir içerik türü tanımı biten dosyaları için oluşturulan *.bar* dosya uzantısı. İçerik türü tanımı "çubuğu" adı verilir ve **gerekir** öğesinden türetilen [CodeRemoteContentTypeName](/dotnet/api/microsoft.visualstudio.languageserver.client.coderemotecontentdefinition.coderemotecontenttypename?view=visualstudiosdk-2017).

Bir içerik türü tanımı ekledikten sonra daha sonra dil istemci sınıfı dil İstemci uzantı yükleme zamanı tanımlayabilirsiniz:

```csharp
    [ContentType("bar")]
    [Export(typeof(ILanguageClient))]
    public class BarLanguageClient : ILanguageClient
    {
    }
```

LSP dil Server'lar için desteği eklemek için Visual Studio içinde kendi proje sistemi uygulamak gerektirmez. Müşteriler, tek bir dosyayı veya klasörü, dil hizmeti kullanmaya başlamak için Visual Studio'da açabilirsiniz. Aslında, LSP dil sunucuları tasarlanmıştır için açık klasör/dosya senaryolarında çalışmaya destekler. Özel proje sistemi uygulanmışsa (ayarlar gibi) bazı özellikler çalışmaz.

## <a name="advanced-features"></a>Gelişmiş özellikler

### <a name="settings"></a>Ayarlar

Özel dil Server'a özgü ayarları için destek mevcuttur, ancak yine de geliştirilen sürecinde olduğundan. Hangi dil sunucunun destekler ve genellikle dil sunucunun verileri nasıl yayar denetlemek için ayarları özgüdür. Örneğin, bir dil sunucusu için rapor edilen hata sayısı bir ayar olabilir. Uzantı yazarları, belirli projeleri için kullanıcılar tarafından değiştirilebilir bir varsayılan değer tanımlamanız gerekir.

LSP dil hizmeti uzantınızı ayarları için destek eklemek için aşağıdaki adımları izleyin:

1. Bir JSON dosyası ekleyin (örneğin, *MockLanguageExtensionSettings.json*) projenizdeki ayarları ve kendi varsayılan değerlerini içerir. Örneğin:

   ```json
   {
    "foo.maxNumberOfProblems": -1
   }
   ```
2. JSON dosya sağ tıklayıp **özellikleri**. Değişiklik **derleme** eylem "İçerik" ve "VSIX Ekle ' özelliğini true.

3. Uygulama ConfigurationSections ve JSON dosyasında tanımlanan ayarlara yönelik önekleri listesini döndürür (Visual Studio kodu, bu eşleme Package.json'da yapılandırma bölümü adı):

   ```csharp
   public IEnumerable<string> ConfigurationSections
   {
      get
      {
          yield return "foo";
      }
   }
   ```
4. .Pkgdef dosyası projeye ekleyin (yeni metin dosyası ekleyin ve .pkgdef için dosya uzantısı değiştirme). Pkgdef bu dosya, bu bilgileri içermelidir:

   ```xml
    [$RootKey$\OpenFolder\Settings\VSWorkspaceSettings\[settings-name]]
    @="$PackageFolder$\[settings-file-name].json"
   ```

5. .pkgdef dosyasını sağ tıklatın ve seçin **özellikleri**. Değişiklik **derleme** eyleme **içerik** ve **VSIX Ekle** özelliği true.

6. Açık yukarı *source.extension.vsixmanifest* dosyası ve bir varlığı ekleyin **varlık** sekmesinde:

   ![VSPackage varlığı Düzenle](media/lsp-add-vspackage-asset.png)

   * **Tür**: Microsoft.VisualStudio.VsPackage
   * **Kaynak**: FileSystem'daki
   * **Yol**: [yolu, *.pkgdef* dosyası]

### <a name="user-editing-of-settings-for-a-workspace"></a>Kullanıcı, bir çalışma alanı ayarlarını düzenleme

1. Kullanıcı, sunucunun sahip olduğu dosyalar içeren bir çalışma alanı açılır.
2. Kullanıcı bir dosyayı ekler *.vs* adlı bir klasör *VSWorkspaceSettings.json*.
3. Kullanıcı için bir satır ekler *VSWorkspaceSettings.json* dosyası için bir ayar sunucu sağlar. Örneğin:

   ```json
   {
    "foo.maxNumberOfProblems": 10
   }
   ```
   ### <a name="enabling-diagnostics-tracing"></a>Tanılama izlemeyi etkinleştirme
   Tanılama izleme, sorunları hata ayıklama sırasında yararlı olabilecek sunucu ve istemci arasındaki tüm iletiler çıkarmasını etkinleştirilebilir.  Tanılama izlemesini etkinleştirmek için aşağıdakileri yapın:

4. Çalışma ayarları dosyasını oluşturun veya açın *VSWorkspaceSettings.json* ("Kullanıcı, bir çalışma alanı ayarlarını düzenleme" bakın).
5. Ayarları json dosyasında aşağıdaki satırı ekleyin:

```json
{
    "foo.trace.server": "Off"
}
```

İzleme ayrıntı düzeyi için üç olası değer vardır:
* "Kapalı": tamamen devre dışı izleme
* "İleti": izleme açık ancak tek yöntem adı ve yanıt kimliği izlenen.
* "Ayrıntılı": açık; izleme Tüm rpc message izlenen.

İzleme içeriği ne zaman etkin bir dosyaya yazılır *%temp%\VisualStudio\LSP* dizin.  Günlük aşağıdaki adlandırma biçimine *[LanguageClientName]-[Datetime damga] .log*.  Şu anda yalnızca izleme klasörünü aç senaryoları için etkinleştirilebilir.  Bir dil Sunucusu'nu etkinleştirmek için tek bir dosyayı açma Tanılama izleme desteği yok.

### <a name="custom-messages"></a>Özel iletiler

İleti geçirme ve standart dil sunucusu protokolü bir parçası olmayan alıcı dil sunucudaki iletileri kolaylaştırmak için API yerinde vardır. Özel iletileri işlemek için uygulama [ILanguageClientCustomMessage](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage?view=visualstudiosdk-2017) dil istemci sınıfınız arabirimi. [VS StreamJsonRpc](https://github.com/Microsoft/vs-streamjsonrpc/blob/master/doc/index.md) kitaplığı dil istemci ve sunucu dil arasında özel ileti iletmek için kullanılır. LSP dil istemci uzantınızı yalnızca herhangi diğer Visual Studio uzantısı gibi olduğundan, (LSP tarafından desteklenmez) ek özellikleri ekleyin (diğer Visual Studio API kullanarak) Visual Studio, uzantı özel iletiler aracılığıyla karar verebilirsiniz.

#### <a name="receiving-custom-messages"></a>Özel ileti alma

Özel ileti dil sunucudan almak için uygulama [CustomMessageTarget](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage.custommessagetarget?view=visualstudiosdk-2017) özelliği [ILanguageClientCustomMessage](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage?view=visualstudiosdk-2017) ve özel iletilerinizi yapılacağını bilmediği bir nesne döndürür . Aşağıdaki örnekte:

```csharp
internal class MockCustomLanguageClient : MockLanguageClient, ILanguageClientCustomMessage
{
    private JsonRpc customMessageRpc;

    public MockCustomLanguageClient() : base()
    {
        CustomMessageTarget = new CustomTarget();
    }

    public object CustomMessageTarget
    {
        get;
        set;
    }

    public class CustomTarget
    {
        public void OnCustomNotification(JToken arg)
        {
            // Provide logic on what happens OnCustomNotification is called from the language server
        }

        public string OnCustomRequest(string test)
        {
            // Provide logic on what happens OnCustomRequest is called from the language server
        }
    }
}
```

#### <a name="sending-custom-messages"></a>Özel ileti gönderme

Dil sunucuya özel ileti göndermek için uygulama [AttachForCustomMessageAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage.attachforcustommessageasync?view=visualstudiosdk-2017) metodunda [ILanguageClientCustomMessage](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage?view=visualstudiosdk-2017). Dil sunucunuz başlatılan ve iletileri almaya hazır olduğunda, bu yöntem çağrılır. A [JsonRpc](https://github.com/Microsoft/vs-streamjsonrpc/blob/master/src/StreamJsonRpc/JsonRpc.cs) dili kullanarak sunucuya ileti göndermek için daha sonra koruyabilirsiniz bir parametre olarak geçirilen nesne [VS StreamJsonRpc](https://github.com/Microsoft/vs-streamjsonrpc/blob/master/doc/index.md) API'leri. Aşağıdaki örnekte:

```csharp
internal class MockCustomLanguageClient : MockLanguageClient, ILanguageClientCustomMessage
{
    private JsonRpc customMessageRpc;

    public MockCustomLanguageClient() : base()
    {
        CustomMessageTarget = new CustomTarget();
    }

    public async Task AttachForCustomMessageAsync(JsonRpc rpc)
    {
        await Task.Yield();

        this.customMessageRpc = rpc;
    }

    public async Task SendServerCustomNotification(object arg)
    {    
        await this.customMessageRpc.NotifyWithParameterObjectAsync("OnCustomNotification", arg);
    }

    public async Task<string> SendServerCustomMessage(string test)
    {
        return await this.customMessageRpc.InvokeAsync<string>("OnCustomRequest", test);
    }
}
```

### <a name="middle-layer"></a>Orta katman

Bazen bir uzantı Geliştirici gönderilen ve dil sunucudan alınan LSP iletileri ıntercept isteyebilirsiniz. Örneğin, bir uzantı Geliştirici belirli bir LSP iletiyi gönderilen ileti parametreyi değiştirmek istiyorsanız veya bir LSP özelliği (örneğin, tamamlamalar) için dil sunucudan döndürülen sonuçlar değiştirin. Gerekli olduğunda, uzantı geliştiricileri, LSP iletileri izlemesine MiddleLayer API'yi kullanabilirsiniz.

Her bir LSP ileti durdurma için kendi orta katman arabirimi vardır. Belirli bir iletiyi komutlarını kesiştirmek için o ileti için orta katman arabirimi uygulayan bir sınıf oluşturun. Ardından, uygulama [ILanguageClientCustomMessage](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage?view=visualstudiosdk-2017) dil istemci Sınıfınız içinde arabirim ve içinde bir nesnenin örneğine dönüş [MiddleLayer](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage.middlelayer?view=visualstudiosdk-2017) özelliği. Aşağıdaki örnekte:

```csharp
public class MockLanguageClient: ILanguageClient, ILanguageClientCustomMessage
{
    public object MiddleLayer => MiddleLayerProvider.Instance;

    private class MiddleLayerProvider : ILanguageClientWorkspaceSymbolProvider
    {
        internal readonly static MiddleLayerProvider Instance = new MiddleLayerProvider();

        private MiddleLayerProvider()
        {
        }

        public async Task<SymbolInformation[]> RequestWorkspaceSymbols(WorkspaceSymbolParams param, Func<WorkspaceSymbolParams, Task<SymbolInformation[]>> sendRequest)
        {
            // Send along the request as given
            SymbolInformation[] symbols = await sendRequest(param);

            // Only return symbols that are "files"
            return symbols.Where(sym => string.Equals(new Uri(sym.Location.Uri).Scheme, "file", StringComparison.OrdinalIgnoreCase)).ToArray();
        }
    }
}
```

Orta katman özellik hala geliştirme aşamasındaki ve henüz kapsamlı değildir.

## <a name="sample-lsp-language-server-extension"></a>Örnek LSP dil server uzantısı

Visual Studio'da LSP istemcisi API'sini kullanarak bir örnek uzantısı kaynak kodunu görmek için VSSDK genişletilebilirlik örnekleri görmek [LSP örnek](https://github.com/Microsoft/VSSDK-Extensibility-Samples/tree/master/LanguageServerProtocol).

## <a name="faq"></a>SSS

**Visual Studio'da daha zengin bir özellik desteği sağlamak için LSP dil sunucumu desteklemek için özel Proje sistemi oluşturmak istiyorum nasıl ederim, bunu?**

Visual Studio'da dil LSP tabanlı sunucular için destek dayanır [Klasör Aç özelliği](https://blogs.msdn.microsoft.com/visualstudio/2016/04/12/open-any-folder-with-visual-studio-15-preview/) ve özel Proje sistemi gerektirmeyecek şekilde özel olarak tasarlanmıştır. Yönergeleri izleyerek kendi özel Proje sistemi oluşturabileceğinizi [burada](https://github.com/Microsoft/VSProjectSystem), ancak ayarları gibi bazı özellikler çalışmayabilir. Varsayılan başlatma mantığı LSP dil sunucuları için özel Proje sistemi kullanıyorsanız, dil server kullanabilirsiniz emin olmak için başlatma sırasında özel mantığı sağlayabilirsiniz gerekebilir için şu anda açılan klasörünün kök klasör konumunu geçirmektir düzgün bir şekilde başlatın.

**Hata ayıklayıcı desteği nasıl ekleyebilirim?**

Biz desteği sağladığını [ortak protokol hata ayıklama](https://code.visualstudio.com/docs/extensionAPI/api-debugging) gelecek sürümlerden birinde.

**Yüklü bir VS desteklenen dil hizmeti (örneğin, JavaScript) zaten varsa (linting gibi) ek özellikler sunan bir LSP dil server uzantısı hala yükleyebilirim?**

Evet, ancak tüm özellikler düzgün çalışır. Nihai amacıyla LSP dil sunucusu uzantıları için Visual Studio tarafından desteklen dil Hizmetleri etkinleştirmektir. Ek destek LSP dil sunucuları kullanarak uzantıları oluşturabilirsiniz ancak bazı özellikler (örneğin, IntelliSense) sorunsuz bir deneyim olmaz. Genel olarak, LSP dil sunucu uzantıları var olanları genişletme değil, yeni dil deneyimleri sağlamak için kullanılması önerilir.

**Tamamlanan LSP dil sunucumu VSIX burada yayımlansın mı?**

Market yönergelere bakın [burada](walkthrough-publishing-a-visual-studio-extension.md).
