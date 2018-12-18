---
title: 'Öğretici: Azure işlevleri'
description: Mac için Visual Studio'daki Azure işlevleri'ni kullanarak
author: conceptdev
ms.author: crdun
ms.date: 05/06/2018
ms.topic: article
ms.technology: vs-ide-install
ms.assetid: 38FD2070-5151-482E-B0A9-993715128736
ms.openlocfilehash: d6a0683405340d479fb3289540ffde2c5e7a4f78
ms.sourcegitcommit: 0a8ac5f2a685270d9ca79bb39d26fd90099bfa29
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/09/2018
ms.locfileid: "51296443"
---
# <a name="tutorial-getting-started-with-azure-functions"></a>Öğretici: Azure işlevleri ile çalışmaya başlama

Bu laboratuvarda, Mac için Visual Studio kullanarak Azure işlevleri geliştirmeye başlamak nasıl öğreneceksiniz. Bağlamalar ve tetikleyiciler kullanılabilir birçok türde birini temsil eden Azure işlevleri geliştiricileri için Azure depolama tabloları ile tümleştirmeyi.

## <a name="objectives"></a>Amaçlar

> [!div class="checklist"]
> * Oluşturma ve yerel Azure işlevleri hata ayıklama
> * Web ve Azure storage kaynakları ile tümleştirme
> * Birden çok Azure işlevleri içeren bir iş akışını düzenleyin

## <a name="requirements"></a>Gereksinimler

- Visual Studio Mac 7.5 veya üzeri.
- Bir Azure aboneliği (kullanılabilir boş [ https://azure.com/free ](https://azure.com/free)).

## <a name="exercise-1-creating-an-azure-functions-project"></a>Alıştırma 1: bir Azure işlevleri projesi oluşturma

1. Başlatma **Mac için Visual Studio**.

2. Seçin **Dosya > Yeni Çözüm**.

3. Gelen **bulut > Genel** kategorisi, select **Azure işlevleri** şablonu. Azure işlevleri'ı barındıran bir .NET sınıf kitaplığı oluşturmak için C# kullanır. **İleri**'ye tıklayın.

    ![Azure işlevleri şablonu seçimi](media/azure-functions-lab-image1.png)

4. Ayarlama **proje adı** için **"AzureFunctionsLab"** tıklatıp **Oluştur**.

    ![adlandırma ve, azure işlev projesi oluşturma](media/azure-functions-lab-image2.png)

5. Ait düğümleri genişletebilirsiniz **çözüm bölmesi**. Varsayılan proje şablonu ve Newtonsoft.Json paketini yanı sıra Azure WebJobs paketleri çeşitli NuGet başvurular içerir.

     Ayrıca üç dosya vardır:- **host.json** genel tanımlamak için - konak yapılandırma seçenekleri **local.settings.json** hizmet ayarlarını yapılandırmak için.
        - Proje şablonu ayrıca bir varsayılan HttpTrigger oluşturur. Bu Laboratuvar için silmeniz gerekir **HttpTrigger.cs** proje dosyası.

    Açık **local.settings.json**. İki boş bir bağlantı dizesi ayarlarını sahip olmak için varsayılan olarak ayarlanır.

    ![Çözüm panelini görüntüleme local.settings.json dosyasında](media/azure-functions-lab-image3.png)

## <a name="exercise-2-creating-an-azure-storage-account"></a>Alıştırma 2: bir Azure depolama hesabı oluşturma

1. Adresindeki Azure hesabınızda oturum [ https://portal.azure.com ](https://portal.azure.com).

1. Altında **Sık Kullanılanlar** seçin ekranın sol tarafında bulunan, bölümünde **depolama hesapları**:

    ![Sık kullanılanları bölümü gösterildiği Azure portalının depolama hesapları öğesi](media/azure-functions-lab-image4.png)

1. Seçin **Ekle** yeni bir depolama hesabı oluşturmak için:

    ![Yeni depolama hesabı eklemek için](media/azure-functions-lab-image5.png)

1. Genel olarak benzersiz bir ad girin **adı** ve için yeniden **kaynak grubu**. Varsayılan olarak tüm diğer öğeleri tutabilirsiniz.

    ![Yeni depolama hesabı ayrıntıları](media/azure-functions-lab-image6.png)

1. **Oluştur**'u tıklatın. İşlem, depolama hesabı oluşturmak için birkaç dakika sürebilir. Başarıyla oluşturulduktan sonra bir bildirim alırsınız.

    ![Dağıtım başarılı bildirimi](media/azure-functions-lab-image7.png)

1. Seçin **kaynağa Git** bildirim düğmesinden.

1. Seçin **erişim anahtarları** sekmesi.

    ![erişim anahtarı ayarı](media/azure-functions-lab-image8.png)

1. İlk kopyalama **bağlantı dizesi**. Bu dize, Azure depolama, daha sonra Azure işlevleri ile tümleştirmek için kullanılır.

    ![Anahtar 1 için bilgi](media/azure-functions-lab-image9.png)

1. Geri dönüp **Mac için Visual Studio** ve olarak tam bağlantı dizesini yapıştırabilir **AzureWebJobsStorage** ayarı **local.settings.json**. Artık özniteliklerindeki ayarının adı kendi kaynaklara erişmesi gereken işlevler için başvurabilirsiniz.

    ![yerel ayar dosyasıyla girilen bağlantı anahtarı](media/azure-functions-lab-image10.png)

## <a name="example-3-creating-and-debugging-an-azure-function"></a>Örnek 3: Oluşturma ve bir Azure işlevi hata ayıklama

1. Artık kod eklemeye başlamak hazırsınız. .NET sınıf kitaplığı ile çalışırken, Azure işlevleri statik yöntemler olarak eklenir. Gelen **çözüm bölmesi**, sağ **Azureişlevleri** proje düğümünü seçip alt **Ekle > işlev Ekle**:

    ![İşlev seçeneği Ekle](media/azure-functions-lab-image11.png)

1. Yeni Azure işlevleri iletişim kutusunda, genel Web kancası şablonu seçin. Ayarlama **adı** için **Ekle** tıklatıp **Tamam** işlevinizi oluşturmak için:

    ![Yeni azure işlevleri iletişim kutusu](media/azure-functions-lab-image12.png)

1. Yeni dosyanın en üstüne ekleyin **kullanarak** aşağıdaki yönergeleri:

    ```csharp
    using Microsoft.Azure.WebJobs.Extensions.Http;
    using System.Web;
    using Microsoft.WindowsAzure.Storage.Table;
    ```
1. Varolan kaldırmak `Run` yöntemi ve Azure işlevinizi olarak sınıfına aşağıdaki yöntemi ekleyin:

    ```csharp
    [FunctionName("Add")]
    public static int Run(
    [HttpTrigger(AuthorizationLevel.Function, "get", Route = null)]
    HttpRequestMessage req,
    TraceWriter log)
    {
        int x = 1;
        int y = 2;

        return x + y;
    }
    ```
1. Parça parça yöntemi tanımıyla atalım.

    İlk şey göreceksiniz **FunctionName** özniteliği, bu yöntem bir Azure işlevi olarak işaretler. Öznitelik Genel işlevin adını belirtir. Öznitelik adı gerçek yöntemi adıyla eşleşmesi gerekmez.

    ![Vurgulanan FunctionName özniteliği ile yeni çalışma yöntemi](media/azure-functions-lab-image13.png)

1. Ardından, yöntem olarak işaretlenmiş bir **genel statik** yöntemi gerekli değildir. Dönüş değeri olduğunu da fark edeceksiniz bir **int**. Yöntem öznitelikleri kullanarak aksi belirtilmediği sürece, bir Azure işlevi bir void olmayan dönüş değerini metin olarak istemciye döndürülür. Varsayılan olarak döndürülür **XML**, ancak değiştirilebilir **JSON**, laboratuvarda bunu daha sonra.

    ![Vurgulanan yöntemi başlatma ile yeni çalışma yöntemi](media/azure-functions-lab-image14.png)

1. İlk parametre ile işaretlenmiş **HttpTrigger** özniteliği, bu yöntemi bir HTTP isteği tarafından çağrılan gösterir. Öznitelik de yöntemin yanı sıra desteklediği fiilleri yetkilendirme düzeyini belirtir (yalnızca **"GET"** bu durumda). Ayrıca isteğe bağlı olarak tanımlayabilir bir **rota** yöntemi yolu geçersiz kılar ve değişkenleri yolundan otomatik olarak ayıklamak için bir yol sunar. Bu yana **rota** burada bu yöntem yolu varsayılan NULL **/api/Add**.

    ![Vurgulanan parametresiyle yeni çalışma yöntemi](media/azure-functions-lab-image15.png)

1. Yöntem son parametresi bir **TraceWriter** tanılama ve hata iletilerini günlüğe kaydetmek için kullanılabilir.

    ![Vurgulanan TraceWriter ile yeni çalışma yöntemi](media/azure-functions-lab-image16.png)

1. Bir kesme noktası ayarlamak **dönüş** satırının kenar boşluğunu tıklayarak yönteminin satır:

    ![Dönüş satırında kesme](media/azure-functions-lab-image17.png)

1. Derleme ve basarak projenin hata ayıklama oturumunda çalıştırmak **F5** veya seçerek **çalıştırın > hata ayıklamayı Başlat**. Alternatif olarak tıklayabilirsiniz **çalıştırma** düğmesi. Bu seçeneklerin tümü aynı görevi gerçekleştirir. Bu Laboratuvarın geri kalanı başvuran **F5**, ancak en rahat bulma yöntemini kullanabilirsiniz.

    ![Derleme ve proje çalıştırma](media/azure-functions-lab-image18.png)

1. Proje çalıştıran Terminal uygulamasına otomatik olarak açılır.

1. Yöntem öznitelikleri ve bu makalenin sonraki bölümlerinde ele bir dosya kuralına göre Azure işlevleri Algılama işlemi proje geçer. Bu durumda, tek bir Azure işlevi algılar ve "1 iş işlevi oluşturur".

    ![Terminalde Azure işlevinin çıkış](media/azure-functions-lab-image19.png)

1. Bir başlangıç iletisini alt kısmında, Azure işlevleri konak herhangi bir HTTP tetikleyicisi API'leri URL'lerini yazdırır. Yalnızca bulunmamalıdır biri. Bu URL'yi kopyalayıp yeni bir tarayıcı sekmesinde yapıştırın.

    ![Azure işlev API URL'si](media/azure-functions-lab-image20.png)

1. Kesme noktası hemen tetiklemesi gereken. Web isteği işleve yönlendirilir ve artık ayıklanabilir. Fare üzerindeyken **x** değerini görmek için değişkeni.

    ![Tetiklenen kesme noktası](media/azure-functions-lab-image21.png)

1. Daha önce eklemek için kullanılan yöntemin aynısını kullanarak kesme noktasını Kaldır (kenar boşluğu tıklayın veya basın ve satır seçin **F9**).

1. Tuşuna **F5** çalışmaya devam edebilmesi için.

1. Metodu XML sonucu tarayıcıda oluşturulur. Beklendiği gibi sabit kodlanmış toplama işlemi yatkýn toplam üretir. Unutmayın, yalnızca "3", Safari, Git için görürseniz **Safari > Tercihler > Gelişmiş** ve işaretleyerek "**Göster geliştirme menüsünü menü çubuğunda**" onay kutusunu ve sayfayı yeniden yükleyin.

1. İçinde **Mac için Visual Studio**, tıklayın **Durdur** hata ayıklama oturumunu sona erdirmek için düğme. Yeni değişiklikler seçilir emin olmak için (durdurmak ve ardından Çalıştır) hata ayıklama oturumunu yeniden başlatmayı unutmayın.

    ![Seçeneği hata ayıklamayı Durdur](media/azure-functions-lab-image22.png)

1. İçinde **çalıştırmak** yöntemi Değiştir **x** ve **y** aşağıdaki kod ile tanımları. Toplama işlemi dinamik olarak bağlı olarak sağlanan parametreler gerçekleştirilebilir. böylece bu kod, URL'nin Sorgu dizesinden değerlerini ayıklar.

    ```csharp
    var query = HttpUtility.ParseQueryString(req.RequestUri.Query);

    int x = int.Parse(query["x"]);

    int y = int.Parse(query["y"]);

    return x + y;
    ```
1. Uygulamayı çalıştırın.

1. Tarayıcı penceresine dönün ve dizesini `/?x=2&y=3` URL'si. URL'nin tamamı artık olmalıdır `http://localhost:7071/api/Add?x=2&y=3`. Yeni URL'ye gidin.

1. Bu süre sonucu yeni parametreler yansıtmalıdır. Projeyi farklı değerlerle çalıştırmak çekinmeyin. Geçersiz veya eksik parametreler bir hata atar. Bu nedenle denetimi, herhangi bir hata olmadığını unutmayın.

1. Hata ayıklama oturumunu durdurun.


## <a name="exercise-4-working-with-functionjson"></a>Alıştırma 4: function.json ile çalışma

1.  Bir önceki alıştırmada, Mac için Visual Studio "bir işlevi kitaplıkta tanımlanan Azure işlevi için üretilen" bahsedilen. Azure işlevleri yöntem öznitelikleri çalışma zamanında gerçekten kullanmaz, ancak bunun yerine nerede yapılandırmak için bir derleme zamanı dosya sistemi kuralını kullanır ve Azure işlevleri kullanıma sunulan nasıl budur. Gelen **çözüm bölmesi**, proje düğümünüze sağ tıklayıp **Finder'da Göster**.

     ![Bulucu menü seçeneğini göster](media/azure-functions-lab-image23.png)

1. Ulaşana kadar dosya sisteminde gezinmek **bin/Debug/netstandard2.0**. Adlı bir klasör olmalıdır **Ekle**. Bu klasör, C# kodu işlevi ad özniteliği ile karşılık olarak oluşturuldu. Tek bir açığa çıkarmak için Ekle klasörü genişletin **function.json** dosya. Bu dosya, barındırmanıza ve yönetmenize Azure işlevi için çalışma zamanı tarafından kullanılır. Derleme zamanı desteği (örneğin, C# betiği veya JavaScript gibi) olmayan diğer dil modelleri için bu klasörleri el ile oluşturulan ve bakımı yapılması gereken. C# geliştiricileri için bunlar otomatik olarak derleme sırasında öznitelik meta verilerden oluşturulur. Sağ **function.json** ve Visual Studio'da açmak için seçin.

    ![dosya dizininde Function.JSON](media/azure-functions-lab-image24.png)

1. Bu öğreticinin önceki adımları göz önünde bulundurulduğunda, C# özniteliklerini temel bir anlayışa sahip olmalıdır. Bu hesaba katılarak, bu JSON tanıdık gelecektir. Ancak, önceki alıştırmalarda kapsamında olmayan birkaç öğe yok. Örneğin, her **bağlama** olmalıdır, **yönü** ayarlayın. Çıkarsayabilir gibi **"içinde"** parametre girişi gelirken demektir **"çıkış"** parametresi bir dönüş değeri olduğunu gösterir (aracılığıyla **$return**) veya bir **kullanıma** yönteme parametre. Belirtmeniz gerekir **KomutDosyası** (göre bu son konum) ve **entryPoint** derlemedeki yöntemi (genel ve statik). Sonraki adımlarda bu modeli kullanarak bir özel işlev yolu ekleyeceksiniz. Bu nedenle bu dosyanın içeriğini panoya kopyala.

    ![mac için visual Studio'da Aç Function.JSON dosyası](media/azure-functions-lab-image25.png)

1. İçinde **çözüm bölmesi**, sağ **AzureFunctionsLab** proje düğümünü seçip alt **Ekle > Yeni klasör**. Yeni klasör adı **ekleyici**. Varsayılan kural olarak, bu klasörün adını yolunu API'sine gibi tanımlayacak **API/ekleyici**.

    ![Yeni klasör seçeneği](media/azure-functions-lab-image26.png)

1. Sağ **ekleyici** klasörü ve select **Ekle > yeni dosya**.

    ![Yeni dosya seçeneği](media/azure-functions-lab-image27.png)

1. Seçin **Web** kategorisi ve **boş JSON dosyası** şablonu. Ayarlama **adı** için **işlevi** tıklatıp **yeni**.

    ![Boş bir json dosyası seçeneği](media/azure-functions-lab-image28.png)

1. Diğer içeriğini yapıştırın **function.json** (dan 3. adım) yeni oluşturulan dosyasının varsayılan içeriklerini değiştirmek için.

1. Json dosyasının en üstüne aşağıdaki satırları kaldırın:

    ```json
    "configurationSource":"attributes",
    "generatedBy":"Microsoft.NET.Sdk.Functions-1.0.13",
    ```

1. İlk bağlama sonunda (sonra **"name": "istek"** satır), aşağıdaki özellikleri ekleyin. Önceki satıra bir virgül eklemeyi unutmayın. Bu özellik artık ayıklayacaktır şekilde varsayılan kök geçersiz kılar **int** yolundan parametreleri adlandırılan yöntem parametreleri yerleştirebilirsiniz **x** ve **y**.

    ```json
    "direction": "in",
    "route": "Adder/{x:int?}/{y:int?}"
    ```

1. Başka bir bağlama ilk altına ekleyin. Bu bağlama, dönüş değeri işlevin işler. Önceki satıra bir virgül eklemeyi unutmayın:

    ```json
    {
    "name": "$return",
    "type": "http",
    "direction": "out"
    }
    ```

1. Ayrıca güncelleştirme **entryPoint** adlı bir yöntem kullanılacak dosyanın sonuna özelliği **"Add2"** aşağıda gösterildiği gibi. Bu, göstermek için olan yolun **API/ekleyici...**  herhangi bir ad ile uygun bir yöntemi eşleyebilirsiniz (**Add2** burada).

    ```json
    "entryPoint": "<project-name>.<function-class-name>.Add2"
    ```

1. Son **function.json** dosya, aşağıdaki json gibi görünmelidir:

    ```json
    {
    "bindings": [
        {
        "type": "httpTrigger",
        "methods": [
            "get"
        ],
        "authLevel": "function",
        "direction": "in",
        "name": "req",
        "route": "Adder/{x:int?}/{y:int?}"
        },
        {
        "name": "$return",
        "type": "http",
        "direction": "out"
        }
    ],
    "disabled": false,
    "scriptFile": "../bin/AzureFunctionsProject.dll",
    "entryPoint": "AzureFunctionsProject.Add.Add2"
    }
    ```

1. Bir son adım Bunu yapmak için gereken tüm iş her değiştiğinde bu dosyayı çıkış dizinine aynı göreli yolda kopyalamak Mac için Visual Studio yüklemelerini sağlamaktır. Seçtiğiniz dosya ile Özellikler sekmesinde sağ çubuğu ve için seçebileceğiniz **çıkış dizinine Kopyala** seçin **yeniyse Kopyala**:

    ![Json dosyası için özellikleri seçenekleri](media/azure-functions-lab-image30.png)

1. İçinde **Add.cs**, değiştirin `Run` yöntemini beklenen işlevi yerine getirmek için aşağıdaki yöntemle (öznitelik dahil). Çok benzer `Run`dışında bu özniteliklere kullanır ve açık parametrelerini **x** ve **y**.

    ```csharp
    public static int Add2(
        HttpRequestMessage req,
        int x,
        int y,
        TraceWriter log)
    {
        return x + y;
    }
    ```
1. Tuşuna **F5** oluşturup projeyi çalıştırın.

1. Derleme tamamlandığında ve platform sanal makineleri çalıştırır gibi Şimdi ikinci rota yeni eklenen yöntemiyle eşleşen bir istek için kullanılabilir olduğunu gösterir:

    ![İşlevleri Http URL'si](media/azure-functions-lab-image31.png)

1. Tarayıcı penceresine dönün ve gidin **http://localhost:7071/api/Adder/3/5**.

1. Bu süre yöntem parametreleri yolundan çekme ve toplam üreten bir kez daha, çalışır.

1. Geri dönüp **Mac için Visual Studio** ve hata ayıklama oturumunu sona erdirme.

## <a name="exercise-5-working-with-azure-storage-tables"></a>Alıştırma 5: Azure depolama tablolarla çalışma

Genellikle, oluşturduğunuz hizmet ne biz şu ana kadar oluşturulmuş ve önemli miktarda zaman ve/veya yürütülecek altyapı gerektiren daha çok daha karmaşık olabilir. O durumda, bu kaynaklar kullanılabilir olduğunda işlenmek üzere kuyruğa alınan isteklerini kabul etmek etkili bulabilirsiniz, hangi Azure işlevleri için destek sağlar. Diğer durumlarda, veri merkezi olarak depolamak isteyebilirsiniz. Azure depolama tabloları, hızlı bir şekilde gerçekleştirmenize olanak tanır.

1. Aşağıda sınıfa eklemek **Add.cs**. Ad alanı içinde ancak varolan bir sınıf dışında gitmeniz gerekir.

    ```csharp
    public class TableRow : TableEntity
    {
        public int X { get; set; }
        public int Y { get; set; }
        public int Sum { get; set; }
    }
    ```
1. İçinde **Ekle** sınıfı, başka bir işlevi tanıtmak için aşağıdaki kodu ekleyin. Bir HTTP yanıtı içermeyen, bu kadar benzersiz olduğunu unutmayın. Yeni bir son satırı döndürür **TableRow'a** daha sonra almak kolay hale getirecek bazı temel bilgilerle doldurulur (**PartitionKey** ve **RowKey**), yanı sıra kendi parametreleri ve topla. Ayrıca metodu içindeki kod kullanan **TraceWriter** işlevi çalıştırıldığında bilmek daha kolay hale getirmek için.

    ```csharp
    [FunctionName("Process")]
    [return: Table("Results")]
    public static TableRow Process(
        [HttpTrigger(AuthorizationLevel.Function, "get",
            Route = "Process/{x:int}/{y:int}")]
        HttpRequestMessage req,
        int x,
        int y,
        TraceWriter log)
    {
        log.Info($"Processing {x} + {y}");

        return new TableRow()
        {
            PartitionKey = "sums",
            RowKey = $"{x}_{y}",
            X = x,
            Y = y,
            Sum = x + y
        };
    }
    ```
1. Tuşuna **F5** oluşturup projeyi çalıştırın.

1. Tarayıcı sekmesinde gidin **http://localhost:7071/api/Process/4/6**. Bu başka bir ileti kuyruğuna sonunda başka bir satır tabloya eklenmekte sonuçlanmalıdır koyacaktır.

1. Geri dönüp **Terminal** ve izlemek için gelen isteğin **4 + 6**.

    ![Terminal çıkış gösteren toplama isteği](media/azure-functions-lab-image32.png)

1. Aynı URL'ye isteği yenilemek için tarayıcıya dönün. Bu süre bir hata görürsünüz **işlem** yöntemi. Zaten var olan bir bölüm ve satır tuş bileşimini kullanarak Azure tablo depolama tablosuna satır eklemek kod çalışıyor olmasıdır.

    ```
    System.Private.CoreLib: Exception while executing function: Process. Microsoft.Azure.WebJobs.Host: Error while handling parameter $return after function returned:. Microsoft.Azure.WebJobs.Host: The specified entity already exists.
    ```

1. Hata ayıklama oturumunu sonlandırın.

1. Hatayı gidermek için aşağıdaki parametreyi yöntem tanımını hemen önüne ekleyin **TraceWriter** parametresi. Bu parametre alma denemesi için Azure işlevleri platformu sağlar. bir **TableRow'a** gelen **sonuçları** üzerinde tablo **PartitionKey** biz depolamak için kullanmakta olduğunuz Sonuç. Ancak, bazı gerçek Sihirli gelen oyuna olduğunu fark edersiniz, **RowKey** dinamik olarak oluşturulan diğer alan **x** ve **y** parametrelerini çok aynı yöntem. Bu satır, ardından zaten varsa **TableRow'a** olacaktır, yöntem ile geliştirici tarafından hiçbir ek iş başladığında. Ardından satır yoksa, onu yalnızca null olacaktır. Bu tür bir verimlilik, geliştiricilerin önemli iş mantığı ve altyapı üzerinde odaklanmanıza olanak tanır.

    ```csharp
    [Table("Results", "sums", "{x}_{y}")]
    TableRow tableRow,
    ```
1. Yönteminin başına aşağıdaki kodu ekleyin. Varsa **TableRow'a** biz zaten istenen işlemi için sonuçları varsa ve hemen dönebilirsiniz null değil. Aksi halde, işlev önceki gibi devam eder. Bu verileri döndürmek için en güçlü şekilde olmayabilir ancak çok az kod ile birden çok ölçeklenebilir katman arasında son derece karmaşık işlemleri düzenleyebilirsiniz noktası gösterilmektedir.

    ```csharp
    if (tableRow != null)
    {
        log.Info($"{x} + {y} already exists");
        return null;
    }
    ```
1. Tuşuna **F5** oluşturup projeyi çalıştırın.

1. Tarayıcı sekmesinde URL'SİNDE Yenile **http://localhost:7071/api/Process/4/6**. Bu kaydın tabloda satır mevcut olmadığından, hemen ve hatasız döndürmelidir. HTTP çıktı olduğundan, Terminal çıktıda görebilirsiniz.

    ![Tablo satırı zaten gösteren terminal çıkış var.](media/azure-functions-lab-image33.png)

1. Bir birleşim yansıtmıyor URL'sini henüz test, gibi güncelleştirme **http://localhost:7071/api/Process/5/7**. Tablo satırı (beklendiği gibi) bulunamadığını belirten bir Terminal ileti unutmayın.

    ![Terminal çıkış gösteren yeni işlem](media/azure-functions-lab-image34.png)

1. Geri dönüp **Mac için Visual Studio** ve hata ayıklama oturumunu sona erdirme.

<!--
1. Finally, let's take a look at what it's like to work with multiple input records. Rather than specify a specific **TableRow**, you can request an **IQueryable<TableRow>** using the same attributes, and the runtime will fill it with the appropriate resource you need. Add the code below to create a **List** function that lists all items that currently exist in the Azure table we've been working with. Also note that we're specifying that the MIME type of the response is **application/json**, so the runtime will automatically render as JSON.

    ```csharp
    [FunctionName("List")]
    public static HttpResponseMessage List(
        [HttpTrigger(AuthorizationLevel.Function, "get", Route = null)]
        HttpRequestMessage req,
        [Table("Results", "sums")]
        IQueryable<TableRow> table,
        TraceWriter log)
    {
        return req.CreateResponse(HttpStatusCode.OK, table, "application/json");
    }
    ```
1. Press **F5** to build and run the project.

1. In the browser tab, navigate to **http://localhost:7071/api/List**. This should pull down the list of all items in the Azure table and render it as JSON.

    ![](https://user-images.githubusercontent.com/3944468/29033725-be9d5a5e-7b4a-11e7-8b55-df0a200b6320.png)
-->

## <a name="summary"></a>Özet

Bu laboratuvarda, Mac için Visual Studio ile Azure işlevleri geliştirmeye başlamak nasıl öğrendiniz.

