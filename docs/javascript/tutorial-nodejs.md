---
title: Node.js ve Express uygulaması oluşturma
description: Bu öğreticide, Visual Studio için Node.js araçları kullanarak uygulama oluşturma
ms.custom: ''
ms.date: 09/24/2018
ms.technology: vs-nodejs
ms.topic: tutorial
ms.devlang: javascript
author: mikejo5000
ms.author: mikejo
manager: douge
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: 8e7a1d04b83ffef2f7ec6efc786af6f5bc6e992e
ms.sourcegitcommit: 000cdd1e95dd02e99a7c7c1a34c2f8fba6a632af
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/25/2018
ms.locfileid: "47168350"
---
# <a name="tutorial-create-a-nodejs-and-express-app-in-visual-studio"></a>Öğretici: Visual Studio'da Node.js ve Express uygulaması oluşturma
Bu öğreticide Node.js ve Express kullanarak Visual Studio geliştirme için basit bir Node.js web uygulaması oluşturma, kod ekleyin, bazı IDE özelliklerini ve uygulamayı çalıştırın. Visual Studio henüz yüklemediyseniz, ücretsiz yükleme [burada](http://visualstudio.microsoft.com).

Bu öğreticide, şunların nasıl yapılır:
> [!div class="checklist"]
> * Node.js projesi oluşturma
> * Kod ekleyin
> * Kodu düzenleme için IntelliSense'i kullanın
> * Uygulamayı çalıştırma
> * Hata ayıklayıcı bir kesme noktasına isabet

## <a name="before-you-begin"></a>Başlamadan önce

İşte bazı temel kavramlara tanıtmak için hızlı bir SSS.

### <a name="what-is-nodejs"></a>Node.js nedir?

Node.js sunucu tarafı JavaScript yürüten bir sunucu tarafı JavaScript çalışma zamanı ortamıdır.

### <a name="what-is-npm"></a>Npm nedir?

npm Node.js için varsayılan paket yöneticisidir. Paket Yöneticisi yayımlamak ve Node.js kitaplıklarının kaynak kodu paylaşmak programcıları için kolaylaştırır ve yükleme, güncelleştirme ve kaldırma kitaplıklarının kolaylaştırmak için tasarlanmıştır.

### <a name="what-is-express"></a>Express nedir?

Express web uygulamaları oluşturmak için Node.js için bir sunucu çerçevesi olarak kullanılan bir web Uygulama Çerçevesi ' dir. Express kullanmanızı sağlar (eski adıyla. Jade) Pug gibi bir kullanıcı Arabirimi oluşturmak için farklı bir ön uç çerçevelerini seçin. Pug Bu öğreticide kullanılır.

## <a name="prerequisites"></a>Önkoşullar

* Visual Studio 2017 ve Node.js geliştirme iş yükü olması gerekir.

    Visual Studio henüz yüklemediyseniz, Git [Visual Studio indirmeleri](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) ücretsiz yüklemek için sayfa.

    İş yükünü yükleyin, ancak Visual Studio'a tıklayın, zaten gerektiğinde **açık Visual Studio yükleyicisi** sol bölmesinde bağlantıyı **yeni proje** iletişim kutusu (seçin **dosya**  >  **Yeni** > **proje**). Visual Studio Yükleyicisi'ni başlatır. Seçin **Node.js geliştirme** iş yükü, ardından **Değiştir**.

* Node.js çalışma zamanı yüklü olması gerekir.

    LTS sürümünden yüklü yoksa, yükleme [Node.js](https://nodejs.org/en/download/) Web sitesi. Genel olarak, Visual Studio yüklü Node.js çalışma zamanı otomatik olarak algılar. Yüklü bir çalışma zamanı algılayan değil, projenizi yüklü çalışma zamanı özellikleri sayfasında başvurmak için yapılandırabilirsiniz (bir proje oluşturduğunuzda, proje düğümüne sağ tıklayın ve seçin **özellikleri**).

    Bu öğreticide, Node.js 8.10.0 ile test edilmiştir.

## <a name="create-a-new-nodejs-project"></a>Yeni bir Node.js projesi oluşturma

Visual Studio için tek bir uygulama içinde dosyaları yöneten bir *proje*. Proje, kaynak kodu, kaynakları ve yapılandırma dosyalarını içerir.

Bu öğreticide, Node.js ve express uygulaması için kod içeren basit bir proje ile başlar.

1. Visual Studio 2017'yi açın.

1. Üstteki menü çubuğundan seçin **dosya** > **yeni** > **proje**.

1. İçinde **yeni proje** iletişim kutusunda, sol bölmede, **JavaScript**ve ardından **Node.js**. Orta bölmede seçin **temel Azure Node.js Express 4 uygulaması** seçip **Tamam**.

     Görmüyorsanız **temel Azure Node.js Express 4 uygulaması** proje şablonu, yüklemelisiniz **Node.js geliştirme** iş yükü ilk (yönergeler önkoşullara bakın).

    Visual Studio, yeni bir çözüm oluşturur ve projenize sağ bölmede açılır. *App.js* proje dosyası (sol bölmede) düzenleyicide açılır.

    ![Proje yapısı](../javascript/media/tutorial-project-structure.png)

    (1) vurgulanmış **kalın** olduğunu size verdiği adını kullanarak projenize **yeni proje** iletişim kutusu. Dosya sisteminde, bu proje tarafından temsil edilen bir *.njsproj* proje klasörünüzdeki dosya. Özellikler ve projeye sağ tıklayıp seçerek projeyle ilişkili ortam değişkenlerini ayarlayabilirsiniz **özellikleri**. Proje dosyası Node.js projesi kaynağına özel değişiklikler yapmaz çünkü diğer geliştirme araçlarıyla gidiş dönüşü yapabilirsiniz.

    (2) en üst düzeyinde ve proje ile aynı ada sahip varsayılan bir çözümdür. Tarafından temsil edilen bir çözüm, bir *.sln* dosya diskte, bir veya daha fazla ilgili proje için bir kapsayıcıdır.

    (3) npm düğüm tüm yüklü npm paketlerini gösterir. Npm için arama yapın ve bir iletişim kutusu veya yükleme kullanarak npm paketlerini yükle ve güncelleştirme ayarlarını kullanarak paketleri düğüme sağ tıklayabilirsiniz *package.json* ve npm düğümünde Seçenekleri'ne sağ tıklayın.

    (4) *package.json* tarafından npm Paket bağımlılıklarını ve yerel olarak yüklü paketler için paket sürümlerini yönetmek için kullanılan bir dosya. Bu dosya hakkında daha fazla bilgi için bkz. [package.json yapılandırma](../javascript/configure-packages-with-package-json.md)

    (5) proje dosyaları gibi *app.js* proje düğümü altında gösterilir. *app.js* proje başlangıç dosyasını ve diğer bir deyişle neden bunu görünür **kalın**. Başlangıç dosyası bir proje dosyasında sağ tıklatıp seçerek ayarlayabilirsiniz **Node.js başlangıç dosyası olarak ayarla**.

1. Açık **npm** düğümü ve tüm gerekli npm paketlerini mevcut olduğundan emin olun.

    Tüm paketler (ünlem simgesi) eksikse, sağ tıklayabilirsiniz **npm** düğümünü seçip **eksik npm paketlerini yükle**.

## <a name="add-some-code"></a>Kod ekleyin

Uygulama için ön uç JavaScript çerçevesini Pug kullanır. Pug HTML derler basit biçimlendirme kodu kullanır. (Pug görüntüleme altyapısı olarak ayarlandığında *app.js*. Görünüm altyapısı ayarlar kod *app.js* olduğu `app.set('view engine', 'pug');`.)

1. Çözüm Gezgini'nde (sağ bölme), görünüm klasörü açın ve ardından *index.pug*.

1. İçerik, aşağıdaki biçimlendirme ile değiştirin.

    ```js
    extends layout

    block content
      h1= title
      p Welcome to #{title}
      script.
        var f1 = function() { document.getElementById('myImage').src='#{data.item1}' }
      script.
        var f2 = function() { document.getElementById('myImage').src='#{data.item2}' }
      script.
        var f3 = function() { document.getElementById('myImage').src='#{data.item3}' }

      button(onclick='f1()') One!
      button(onclick='f2()') Two!
      button(onclick='f3()') Three!
      p
      a: img(id='myImage' height='200' width='200' src='')
    ```

    Yukarıdaki kod, dinamik olarak bir başlık ve Hoş Geldiniz iletisi içeren bir HTML sayfası oluşturmak için kullanılır. Sayfa aynı zamanda her bir düğmeye basarak değiştiren bir resmi görüntülemek için kod içerir.

1. Yollar klasöründe açın *index.js*.

1. Çağırmadan önce aşağıdaki kodu ekleyin `router.get`:

    ```js
    var getData = function () {
        var data = {
            'item1': 'http://public-domain-photos.com/free-stock-photos-1/flowers/cactus-76.jpg',
            'item2': 'http://public-domain-photos.com/free-stock-photos-1/flowers/cactus-77.jpg',
            'item3': 'http://public-domain-photos.com/free-stock-photos-1/flowers/cactus-78.jpg'
        }
        return data;
    }
    ````

    Bu kod dinamik olarak üretilen bir HTML sayfasına geçirdiğiniz bir veri nesnesi oluşturur.

1. Değiştirin `router.get` işlev çağrısı aşağıdaki kod ile:

    ```js
    router.get('/', function (req, res) {
        res.render('index', { title: 'Express', "data" });
    });
    ```

    Yukarıdaki kod Express yönlendirici nesnesini kullanarak geçerli sayfayı ayarlar ve sayfaya başlık ve veri nesnesi geçirme sayfasını işler. *İndex.pug* dosya belirtilen ne zaman yükleneceğini sayfası olarak burada *index.js* çalıştırır. *index.js* içinde varsayılan yol olarak yapılandırılmış *app.js* kod (gösterilmemiştir).

    Visual Studio'nin birtakım özelliklerini göstermek için yoktur bilinçli bir hata kodu içeren satırda `res.render`. Uygulama, sonraki bölümde bunu çalıştırmadan önce bu hatayı düzeltmek gerekir.

## <a name="use-intellisense"></a>IntelliSense kullanma

IntelliSense kod yazarken, size yardımcı olur. Visual Studio bir araçtır.

1. İçinde *index.js*içeren kod satırına gidin `res.render`.

1. İmlecinizi sonra put `data` dize, tip `: get` ve IntelliSense gösterilir `getData` kod içinde tanımlanan işlevi. Seçin `getData`.

    ![IntelliSense kullanma](../javascript/media/tutorial-nodejs-intellisense.png)

1. Virgül Kaldır (`,`) önce `"data"` ve ifade yeşil söz dizimi vurgulama görürsünüz. Söz dizimi vurgulama üzerine gelin.

    ![Görünüm söz dizimi hatası](../javascript/media/tutorial-nodejs-syntax-checking.png)

    Bu ileti son satırının JavaScript yorumlayıcı virgül bekleniyor bildirir (`,`).

1. Alt bölmede **hata listesi** sekmesi.

    Dosya adı ve satır sayısının yanı sıra açıklaması ve uyarı görürsünüz.

    ![Hata Listesi görünümü](../javascript/media/tutorial-nodejs-error-list.png)

1. Virgül ekleyerek kod düzeltmesi (`,`) önce `"data"`.

    Düzeltildi, kod satırının şu şekilde görünmelidir: `res.render('index', { title: 'Express', "data": getData() });`

## <a name="set-a-breakpoint"></a>Bir kesme noktası ayarlayın

Visual Studio hata ayıklayıcısı ekli uygulamayı çalıştırmak için sonraki yedekleyeceksiniz. Bunu yapmadan önce bir kesme noktasını ayarlamanız gerekir.

1. İçinde *index.js*, önce aşağıdaki bir kesme noktası ayarlamak için kod satırının sol kanaldaki tıklayın:

    `res.render('index', { title: 'Express', "data": getData() });`

    Kesme noktaları güvenilir hata ayıklama en temel hem de temel özelliğidir. Bir kesme noktası değişkenlerin değerleri veya bellek davranışını göz olabilmesi için Visual Studio çalışan kodunuzu nereye askıya almanız ya da bir dal kod getting run olup olmadığını gösterir.

    ![Bir kesme noktası ayarlayın](../javascript/media/tutorial-nodejs-set-breakpoint.png)

## <a name="run-the-application"></a>Uygulamayı çalıştırın

1. Edge veya Chrome'da gibi hata ayıklama araç çubuğundaki hata ayıklama hedefi seçin.

    ![Hata ayıklama hedefi seçin](../javascript/media/tutorial-nodejs-deploy-target.png)

    Chrome makinenizde kullanılabilir, ancak bir seçenek olarak görünmez, seçin **şununla Gözat** hata ayıklama hedef açılır liste ve select Chrome varsayılan tarayıcı hedefi olarak (seçin **varsayılan olarak ayarla**).

1. Tuşuna **F5** (**hata ayıklama** > **hata ayıklamayı Başlat**) uygulamayı çalıştırın.

    Hata ayıklayıcı, ayarladığınız kesme noktasında duraklatır. Şimdi, uygulama durumunu inceleyebilirsiniz.

1. Üzerine `getData` bir DataTip içinde özelliklerini görmek için

    ![Değişkenleri inceleme](../javascript/media/tutorial-nodejs-inspect-variables.png)

1. Tuşuna **F5** (**hata ayıklama** > **devam**) devam etmek için.

    Uygulama bir tarayıcıda açılır.

    Tarayıcı penceresinde görürsünüz "Başlık"Hoş Geldiniz Express"ilk paragrafa Express ve".

1. Düğmeleri farklı resimleri görüntülemek için tıklayın.

    ![Tarayıcıda çalışan uygulama](../javascript/media/tutorial-nodejs-running-in-browser.png)

1. Web tarayıcısını kapatın.

## <a name="optional-publish-to-azure-app-service"></a>(İsteğe bağlı) Azure App Service'e yayımlama

1. Çözüm Gezgini'nde projeye sağ tıklayıp seçin **Yayımla**.

   ![Azure App Service’e yayımlama](../javascript/media/tutorial-nodejs-publish-to-azure.png)

1. Seçin **Microsoft Azure App Service'te**.

    İçinde **App Service** iletişim kutusunda, Azure hesabınızda oturum açın ve mevcut Azure aboneliklerine bağlanma.

1. Bir abonelik seçin, seçin veya bir kaynak grubu oluşturun, seçin veya bir app service düzlemi oluşturmak üzere kalan adımları izleyin ve ardından Azure'da yayımlamak için istendiğinde adımları izleyin. Daha ayrıntılı yönergeler için bkz. [Yayımla web kullanarak Azure Web sitesine dağıtma](https://github.com/Microsoft/nodejstools/wiki/Publish-to-Azure-Website-using-Web-Deploy).

1. **Çıkış** Azure'a dağıtmaya penceresi ilerleme durumunu gösterir.

    Üzerinde başarılı dağıtımdan, uygulamanız Azure App Service'te çalışan bir tarayıcıda açılır. Bir resmi görüntülemek için bir düğmeye tıklayın.

   ![Azure App Service'te çalışan uygulama](../javascript/media/tutorial-nodejs-running-in-azure.png)

Bu öğreticiyi tamamlamak Tebrikler!

## <a name="next-steps"></a>Sonraki adımlar

> [!div class="nextstepaction"]
> [Uygulamayı Linux App Service'e dağıtma](../javascript/publish-nodejs-app-azure.md)