---
title: Azure işlevleri'ne giriş
description: Mac için Visual Studio'daki Azure işlevleri'ni kullanarak
author: conceptdev
ms.author: crdun
ms.date: 05/06/2018
ms.topic: article
ms.technology: vs-ide-install
ms.assetid: 25CD47A4-5B32-4734-8EF3-E24A02AABF29
ms.openlocfilehash: eaf6f82cdc40b174dcd1ca8deb12c412fe675d70
ms.sourcegitcommit: 0a8ac5f2a685270d9ca79bb39d26fd90099bfa29
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/09/2018
ms.locfileid: "51295949"
---
# <a name="introduction-to-azure-functions"></a>Azure işlevleri'ne giriş

Azure işlevleri, bir şekilde oluşturun ve – – işlevleri – – kod parçacıkları olay temelli açıkça sağlamak veya altyapıyı yönetmek zorunda kalmadan bulutta çalıştırın. Azure işlevleri hakkında daha fazla bilgi için bkz. [Azure işlevleri belgelerinde](/azure/azure-functions/).

## <a name="requirements"></a>Gereksinimler

Azure işlev araçları dahil edilecek **7.5 Mac için Visual Studio**.

Oluşturma ve işlevleri dağıtmak için de kullanılabilir ücretsiz bir Azure aboneliğine ihtiyaç [ https://azure.com/free ](https://azure.com/free).

## <a name="creating-your-first-azure-functions-project"></a>İlk Azure işlevleri projenizi oluşturma

1. Mac için Visual Studio'da **Dosya > Yeni Çözüm**.
2. Yeni Proje iletişim kutusundan altında Azure işlevleri şablonu **bulut > Genel** tıklatıp **sonraki**:

    ![Azure işlevleri seçeneğini gösteren yeni proje iletişim kutusu](media/azure-functions-image1.png)

3. Kullanmak, işlev adınızı girin ve istediğiniz ilk Azure işlevleri şablonu **sonraki**.

    ![Azure işlevleri şablonları gösteren yeni proje iletişim kutusu](media/azure-functions-image2.png)

    Seçtiğiniz işlev türüne bağlı olarak, aşağıdaki görüntüde gösterildiği gibi bir sonraki sayfada, erişim hakları gibi ayrıntılarını girin ister:

    ![Ek seçeneğini gösteren yeni proje iletişim kutusu](media/azure-functions-image3.png)

    Azure işlevleri şablonları ve her şablonu yapılandırmak için gereken bağlama özellikleri farklı türleri hakkında daha fazla bilgi için bkz. [kullanılabilir işlev şablonları](#available-function-templates) bölümü. Bu örnekte, erişim haklarını anonim olarak Ayarla ile bir Http tetikleyici kullanıyoruz.

4. Parametreleri ayarladıktan sonra proje için konum seçin ve tıklayın **Oluştur**.

Mac için Visual Studio .NET Standard projesine dahil olan bir varsayılan işlev oluşturur. Ayrıca çeşitli NuGet başvurularını içerir **AzureWebJobs** paketleri yanı sıra **Newtonsoft.Json** paket.

![Visual Studio Mac Düzenleyicisi şablondan yeni bir azure işlevi görüntülemek için](media/azure-functions-newproj.png)

Yeni Proje aşağıdaki dosyaları içerir:

* **işlev name.cs bilgisayarınızı** – Bu sınıf, ortak kod için seçtiğiniz işlevi içerir. İçerdiği bir **FunctionName** özniteliği işlev adı ile ve ne tetikler (örn. işlevi belirten bir tetikleyici özniteliği bir HTTP isteği). İşlev yöntemi hakkında daha fazla bilgi için başvurmak [Azure işlevleri C# Geliştirici Başvurusu](/azure/azure-functions/functions-dotnet-class-library) makalesi.
* **Host.JSON** – bu dosya işlevleri konak genel yapılandırma seçeneklerini açıklar. Bir örnek dosyası ve bu dosya için kullanılabilir ayarlar hakkında bilgi için bkz: [Azure işlevleri için host.json başvurusu](/azure/azure-functions/functions-host-json).
* **Local.Settings.JSON** – işlevleri yerel olarak çalıştırmak için bu dosya tüm ayarları içerir. Bu ayarlar, Azure işlevleri çekirdek araçları tarafından kullanılır. Daha fazla bilgi için [yerel ayarları dosyası](/azure/azure-functions/functions-run-local#local-settings-file) Azure işlevleri çekirdek araçları makaledeki.

Mac için Visual Studio'da yeni bir Azure işlevleri projesi oluşturdunuz, yerel makinenizden varsayılan HTTP ile tetiklenen işlevi test edebilirsiniz.

## <a name="testing-the-function-locally"></a>İşlevi yerel olarak test etme

Mac için Visual Studio'da Azure işlevleri desteği ile test edin ve işleviniz yerel geliştirme bilgisayarınızda hata ayıklama.

1. İşleviniz yerel olarak test etmek için basın **çalıştırma** Mac için Visual Studio'da düğmesi:

    ![Düğme mac için visual Studio'da hata ayıklamayı Başlat](media/azure-functions-run.png)

1. Proje çalışan Azure işlev hata ayıklama yerel başlatır ve yeni bir Terminal penceresinde, aşağıdaki görüntüde gösterildiği gibi açılır:

    ![Terminal penceresini gösteren işlev çıkışı](media/azure-functions-terminal.png)

    URL çıktıdan kopyalayın.

3. HTTP isteğinin URL'sini tarayıcınızın adres çubuğuna yapıştırın. Sorgu dizesi eklemenize `?name=<yourname>` URL'nin sonuna ekleyip isteği yürütün. İşlevin döndürdüğü yerel GET isteğine tarayıcıda verilen yanıt aşağıda gösterilmiştir:

    ![tarayıcıda HTTP isteği](media/azure-functions-httpreq.png)

## <a name="adding-another-function-to-your-project"></a>Başka bir işleve projenize ekleme

İşlev Şablonları, en sık kullanılan tetikleyicileri ve şablonları kullanarak yeni işlevleri hızlıca oluşturmanızı sağlar. Başka türde bir işlev oluşturmak için aşağıdakileri yapın:

1. Yeni bir işlev eklemek için proje adını sağ tıklatın ve seçin **Ekle > işlev Ekle...** :

    ![Yeni işlev ekleme bağlamı eylemi](media/azure-functions-addnew.png)

2. Gelen **yeni Azure işlevi** iletişim kutusunda, ihtiyaç duyduğunuz işlevi seçin:

    ![Yeni azure işlevini iletişim kutusu](media/azure-functions-image4.png)

    Azure işlev şablonlarının bir listesi verilmiştir [kullanılabilir işlev şablonları](#available-function-templates) bölümü.

Daha fazla işlev, işlev uygulaması projenizi eklemek için yukarıdaki yordamı kullanabilirsiniz. Projedeki her işlevin farklı bir tetikleyici olabilir ancak bir işlev tam olarak bir tetikleyici olmalıdır. Daha fazla bilgi için [Azure işlevleri Tetikleyicileri ve bağlamaları kavramları](/azure/azure-functions/functions-triggers-bindings).

## <a name="publish-to-azure"></a>Azure'a Yayımlama

1. Proje adına sağ tıklayıp **Yayımla > Azure'da Yayımla**: ![azure menü seçeneği Yayımla](media/azure-functions-image5.png)
2. Önceden bağlandıysanız Azure hesabı için Visual Studio Mac için kullanılabilir uygulama hizmetleri görüntülenen bir listesi. Oturum açmadıysanız, sizden bunu yapmak için istenir.
3. Gelen **Azure App Service'e yayımlama** iletişim kutusunda, var olan bir app service'ı seçebilir veya tıklayarak yeni bir tane oluşturun **yeni**.
4. İçinde **yeni App Service Oluştur** iletişim kutusu, ayarlarınızı girin: ![azure menü seçeneği Yayımla](media/azure-functions-image7.png)

    |Ayar  |Açıklama  |
    |---------|---------|
    |**App Service adı**|Yeni işlev uygulamanızı tanımlayan genel olarak benzersiz bir ad.|
    |**Abonelik**|Kullanılacak Azure aboneliği.|
    |**[Kaynak grubu](/azure/azure-resource-manager/resource-group-overview)**|İşlev uygulamanızın oluşturulacağı kaynak grubunun adı. Seçin **+** yeni bir kaynak grubu oluşturmak için.|
    |**[Hizmet planı](/azure/azure-functions/functions-scale)**|Mevcut bir planı seçebilir veya özel bir plan oluşturun. İşlevleri erişiminizi erişeceği diğer hizmetlere ya da size yakın bir bölgede bir konum seçin.|

    > [!CAUTION]
    > Bir hata olduğunu 7.6 yayımlama bir özel hizmet planı oluşturmaya çalışırsanız, bir sağlama hatası ile başarısız olmasına neden olan Mac için Visual Studio sürümünde **fiyatlandırma** kümesine **tüketim**. Bu, sonraki hizmet sürümde düzeltilecektir.

5. Tıklayın **sonraki** bir depolama hesabı oluşturmak için. İşlevler çalışma zamanı tarafından bir Azure depolama hesabı gereklidir. Tıklayın **özel** bir genel amaçlı depolama hesabı oluşturun veya var olanı kullanın:

    ![Azure menü seçeneğine yayımlama](media/azure-functions-image8.png)

6. Tıklayın **Oluştur** bir işlev uygulaması ve ilgili kaynakları şu ayarlarla oluşturacak ve işlev proje kodunuzu dağıtmak için.

7. Yayımlama sırasında "Güncelleştirme işlevleri sürüm üzerinde Azure'a" bildiren bir iletişim kutusu ile istenebilir. Tıklayın **Evet**:

    ![Azure menü seçeneğine yayımlama](media/azure-functions-image12.png)

> [!CAUTION]
> Mac için Visual Studio 7.6 sürümünde bir hata varsa burada `FUNCTIONS_EXTENSION_VERSION` "işlevinizi çalışmayabilir anlamı beta için" doğru şekilde ayarlanmadı. Bu sorunu gidermek için Git, [işlev uygulaması ayarları](#function-app-settings) ayarlayıp `FUNCTIONS_EXTENSION_VERSION` "beta" için "-1".

## <a name="function-app-settings"></a>İşlev uygulaması ayarları

Azure işlev uygulaması da local.settings.json içinde eklenen herhangi bir ayarı eklenmesi gerekir. Proje yayımladığınızda, bu ayarlar otomatik olarak karşıya yüklenmemiş.

Adresinden azure portalında app ayarlarınız erişmek için Git [ https://ms.portal.azure.com/ ](https://ms.portal.azure.com/). Altında **işlev uygulamaları**seçin **işlev uygulamaları** ve değişken vurgulayabilirsiniz:

![Azure işlevleri menüsü](media/azure-functions-image9.png)

Gelen **genel bakış** sekmesinde **uygulama ayarları** altında **özellikler yapılandırıldı**:

![Azure işlevinin bir sekmenin üzerine](media/azure-functions-image10.png)

Buradan, yeni uygulama ayarlarını ekleyin veya var olanları düzenleyin işlev uygulaması için uygulama ayarlarını ayarlayabilirsiniz:

![azure portal'ın uygulama ayarları alanı](media/azure-functions-image11.png)

Ayarlanacak ihtiyacınız bir önemli ayar `FUNCTIONS_EXTENSION_VERSION`. Mac için Visual Studio'dan yayımlama sırasında bu değer ayarlanmalıdır **beta**.

## <a name="available-function-templates"></a>Kullanılabilir işlev şablonları

- **GitHub tetikleyicisi** -GitHub depolarınızda gerçekleşen olaylara yanıt. Daha fazla bilgi için [Azure işlevleri makalede GitHub üzerindeki](/azure/azure-functions/functions-create-github-webhook-triggered-function)
    - Bir sorun veya çekme isteği için bir GitHub Web kancası aldığında ve yorum ekleyen Github'da yorum yapan – bu işlevi çalıştırılır.
    - GitHub Web kancası aldığında, GitHub Web kancası – bu işlevi çalıştırılır.

- **HTTP** – bir HTTP isteği kullanarak kodunuzun yürütülmesini tetikler. Açık şablonları için aşağıdaki HTTP Tetikleyicileri vardır:
    - HTTP tetikleyicisi
    - HTTP GET CRUD
    - HTTP POST CRUD
    - Parametrelerle HTTP tetikleyicisi


- **Zamanlayıcı** – önceden tanımlanmış bir zamanlamaya göre temizleme veya diğer toplu işlem görevlerini yürütün. Bu şablon iki alanlarını alır: bir ad ve bir zamanlama altı alanı CRON ifadesidir. Daha fazla bilgi için [Azure işlevleri zamanında makalesi](/azure/azure-functions/functions-create-scheduled-function)


- **Kuyruk tetikleyicisi** – bunlar Azure Storage kuyruğuna geldiklerinde iletilere yanıt vereceğini bir işlev budur. İşlev adının yanı sıra bu şablon götüren bir **yolu** (ileti okuması Kuyruğun adı) ve depolama hesabı **bağlantı** (depolama alanınızı içeren uygulama ayarının adı hesabı bağlantı dizesi). Daha fazla bilgi için [Azure işlevleri kuyruk depolama üzerinde makale](/azure/azure-functions/functions-create-storage-queue-triggered-function).

- **BLOB tetikleyicisi** – Azure Storage bloblarını bir kapsayıcıya eklendiğinde. İşlev adının yanı sıra bu şablonu ayrıca bir yol ve bağlantı özelliğini alır. Path özelliği depolama hesabınızda Tetikleyicinin izleyeceği yoludur. Bağlantı hesabı depolama hesabı bağlantı dizenizi içeren uygulama ayarının adıdır. Daha fazla bilgi için [Azure işlevleri Blob Depolama makale](/azure/azure-functions/functions-create-storage-blob-triggered-function).

- **Genel Web kancası** – bu Web kancalarını destekleyen herhangi bir hizmeti isteği aldığında çalıştırılacak, basit bir işlevdir. Daha fazla bilgi için [Azure işlevleri üzerinde genel Web kancaları makale](/azure/azure-functions/functions-create-generic-webhook-triggered-function).

- **Dayanıklı işlevler düzenleme** – dayanıklı İşlevler, durum bilgisi olan işlevleri, sunucusuz bir ortamda yazmanıza olanak tanır. Uzantı durumu ve kontrol noktaları yeniden sizin yerinize yönetir. Daha fazla bilgi için Azure işlevleri kılavuzlarına bakın [dayanıklı işlevler](/azure/azure-functions/durable-functions-overview).

- **Görüntü Boyutlandırıcı** – bir kapsayıcıya bir blob eklendiğinde yeniden boyutlandırılmış görüntüler bu işlevi oluşturur. Şablon tetikleyicisi, küçük resmi çıkış ve orta görüntü çıkış yolu ve bağlantı dizesini alır.

- **SAS belirteci** – bu işlev, belirtilen Azure depolama kapsayıcısı ve blob adı için SAS belirteci oluşturur. İşlev adının yanı sıra bu şablonu ayrıca bir yol ve bağlantı özelliğini alır. Path özelliği depolama hesabınızda Tetikleyicinin izleyeceği yoludur. Bağlantı hesabı depolama hesabı bağlantı dizenizi içeren uygulama ayarının adıdır. **Erişim hakları** de ayarlamanız gerekir. Yetkilendirme düzeyi, işlevin bir API anahtarı gerektirip ve kullanmak için hangi anahtarı denetler; İşlevi, bir işlev anahtarı kullanır; Yönetici ana anahtarınızı kullanır. Daha fazla bilgi için [C# SAS belirteçleri oluşturmak için Azure işlevi](https://azure.microsoft.com/resources/samples/functions-dotnet-sas-token/) örnek.