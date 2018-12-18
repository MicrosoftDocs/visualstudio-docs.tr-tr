---
title: Bir Node.js ve React uygulaması oluşturma
description: Bu öğreticide, Visual Studio için Node.js araçları kullanarak uygulama oluşturma
ms.custom: mvc
ms.date: 11/01/2018
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
ms.openlocfilehash: 9203b07767d38443dbad8cc619a40971ca09f2c6
ms.sourcegitcommit: 1df0ae74af03bcf0244129a29fd6bd605efc9f61
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/01/2018
ms.locfileid: "50750793"
---
# <a name="tutorial-create-a-nodejs-and-react-app-in-visual-studio"></a>Öğretici: Visual Studio'da Node.js ve React uygulaması oluşturma

Visual Studio, kolayca bir Node.js projesi oluşturma ve IntelliSense ve Node.js destekleyen diğer yerleşik özellikler deneyimi sağlar. Bu öğreticide Visual Studio için Visual Studio şablondan bir Node.js web uygulaması projesi oluşturun. Ardından, React kullanarak basit bir uygulama oluşturun.

Bu öğreticide, şunların nasıl yapılır:
> [!div class="checklist"]
> * Node.js projesi oluşturma
> * Npm paketleri ekleme
> * React kodu uygulamanıza ekleyin
> * JSX derleyin
> * Hata ayıklayıcının

## <a name="before-you-begin"></a>Başlamadan önce

İşte bazı temel kavramlara tanıtmak için hızlı bir SSS.

### <a name="what-is-nodejs"></a>Node.js nedir?

Node.js sunucu tarafı JavaScript yürüten bir sunucu tarafı JavaScript çalışma zamanı ortamıdır.

### <a name="what-is-npm"></a>Npm nedir?

npm Node.js için varsayılan paket yöneticisidir. Paket Yöneticisi yayımlamak ve Node.js kitaplıklarının kaynak kodu paylaşmak programcıları için kolaylaştırır ve yükleme, güncelleştirme ve kaldırma kitaplıklarının kolaylaştırmak için tasarlanmıştır.

### <a name="what-is-react"></a>React nedir?

React kullanıcı Arabirimi oluşturmak için ön uç bir çerçevedir.

### <a name="what-is-jsx"></a>JSX nedir?

JSX genellikle kullanıcı Arabirimi öğeleri tanımlamak için React ile kullanılan bir JavaScript söz dizimi bir uzantıdır. Bir tarayıcıda çalıştırmadan önce transpiled düz JavaScript için JSX kodu olmalıdır.

### <a name="what-is-webpack"></a>Web nedir?

Web paketleri JavaScript dosyaları, bir tarayıcıda çalıştırabilirsiniz. Ayrıca dönüştürün veya diğer kaynakları ve varlıklar paketi yükleyebilir. Genellikle, bir derleyici, TypeScript, ya da Fish gibi düz JavaScript'e derleyin JSX veya TypeScript kodu belirtmek için kullanılır.

## <a name="prerequisites"></a>Önkoşullar

* Visual Studio 2017 ve Node.js geliştirme iş yükü olması gerekir.

    Visual Studio henüz yüklemediyseniz, Git [Visual Studio indirmeleri](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) ücretsiz yüklemek için sayfa.

    Gerekirse iş yükünü yükleyin ancak zaten Visual Studio varsa, seçin **açık Visual Studio yükleyicisi** sol bölmesinde bağlantıyı **yeni proje** iletişim kutusu. Visual Studio Yükleyicisi'ni başlatır. Seçin **Node.js geliştirme** iş yükü, ardından **Değiştir**.

* Node.js çalışma zamanı yüklü olması gerekir.

    Bu öğreticide 8.11.2 sürümü ile test edilmiştir.

    LTS sürümünden yüklü yoksa, yükleme [Node.js](https://nodejs.org/en/download/) Web sitesi. Genel olarak, Visual Studio yüklü Node.js çalışma zamanı otomatik olarak algılar. Yüklü bir çalışma zamanı algılayan değil, projenizi yüklü çalışma zamanı özellikleri sayfasında başvurmak için yapılandırabilirsiniz (bir proje oluşturduğunuzda, proje düğümüne sağ tıklayın ve seçin **özellikleri**).

## <a name="create-a-project"></a>Proje oluşturma

İlk olarak bir Node.js web uygulaması projesi oluşturun.

1. Visual Studio 2017'yi açın.

1. Üstteki menü çubuğundan seçin **dosya** > **yeni** > **proje**.

1. İçinde **yeni proje** iletişim kutusunda, sol bölmede, **JavaScript**ve ardından **Node.js**. Orta bölmede seçin **boş Node.js Web uygulaması**, adı **NodejsWebAppBlank**ve ardından **Tamam**.

     Görmüyorsanız **boş Node.js Web uygulaması** proje şablonu, Node.js geliştirme iş yükü yüklemelisiniz.

    Visual Studio, yeni bir çözüm oluşturur ve projenize açar.

    ![Çözüm Gezgini'nde node.js projesi](../javascript/media/tutorial-nodejs-react-project-structure.png)

    (1) vurgulanmış **kalın** olduğunu size verdiği adını kullanarak projenize **yeni proje** iletişim kutusu. Dosya sisteminde, bu proje tarafından temsil edilen bir *.njsproj* proje klasörünüzdeki dosya. Özellikler ve projeye sağ tıklayıp seçerek projeyle ilişkili ortam değişkenlerini ayarlayabilirsiniz **özellikleri**. Proje dosyası Node.js projesi kaynağına özel değişiklikler yapmaz çünkü diğer geliştirme araçlarıyla gidiş dönüşü yapabilirsiniz.

    (2) en üst düzeyinde ve proje ile aynı ada sahip varsayılan bir çözümdür. Tarafından temsil edilen bir çözüm, bir *.sln* dosya diskte, bir veya daha fazla ilgili proje için bir kapsayıcıdır.

    (3) npm düğüm tüm yüklü npm paketlerini gösterir. Npm için arama yapın ve bir iletişim kutusu veya yükleme kullanarak npm paketlerini yükle ve güncelleştirme ayarlarını kullanarak paketleri düğüme sağ tıklayabilirsiniz *package.json* ve npm düğümünde Seçenekleri'ne sağ tıklayın.

    (4) *package.json* tarafından npm Paket bağımlılıklarını ve yerel olarak yüklü paketler için paket sürümlerini yönetmek için kullanılan bir dosya. Bu dosya hakkında daha fazla bilgi için bkz. [package.json yapılandırma](../javascript/configure-packages-with-package-json.md)

    (5) proje dosyaları gibi *server.js* proje düğümü altında gösterilir. *Server.js* proje başlangıç dosyasını ve diğer bir deyişle neden bunu görünür **kalın**. Başlangıç dosyası bir proje dosyasında sağ tıklatıp seçerek ayarlayabilirsiniz **Node.js başlangıç dosyası olarak ayarla**.

## <a name="add-npm-packages"></a>Npm paketleri ekleme

Bu uygulama düzgün şekilde çalışması için npm modüllerini sayısı gerektirir.

* react
* react-dom
* Express
* yol
* TS yükleyicisi
* typescript
* Web
* webpack-cli

1. Çözüm Gezgini'nde (sağ bölme), sağ **npm** proje düğümünü seçin **yükleme yeni npm paketleri**.

    İçinde **yükleme yeni npm paketleri** iletişim kutusu tercih edebilirsiniz en geçerli Paket sürümü yükleyin veya bir sürüm belirtin. Bu paketler geçerli sürümünü yüklemek, ancak beklenmeyen hatalarla karşılaşırsanız daha sonra çalıştırmak isterseniz, daha sonra Bu adımlarda açıklanan tam paket sürümlerini yüklemeniz gerekebilir.

1. İçinde **yükleme yeni npm paketleri** iletişim kutusunda react paketini arayın ve seçin **yükleme paketi** yükleyin.

    ![Npm paketlerini yükle](../javascript/media/tutorial-nodejs-react-install-packages.png)

    Seçin **çıkış** paket yükleme ilerleme durumunu görmek için penceresini (seçin **Npm** içinde **çıktıyı Göster** alan). Yüklendiğinde, paket altında görünür **npm** düğümü.

    Projenin *package.json* dosyasını, Paket sürümü dahil olmak üzere yeni paket bilgileriyle güncelleştirilir.

1. İçin arama yapın ve aynı anda paketleri bir geri kalanını eklemek için kullanıcı arabirimini kullanmak yerine, aşağıdaki kodu yapıştırın *package.json*. Bunu yapmak için bir `dependencies` bölümü bu kod ile:

    ```json
    "dependencies": {
      "express": "~4.16.4",
      "path": "~0.12.7",
      "react": "~16.6.0",
      "react-dom": "~16.6.0",
      "ts-loader": "~5.3.0",
      "typescript": "~3.1.5",
      "webpack": "~4.23.1",
      "webpack-cli": "~3.1.2"
    }
    ```

    Zaten varsa bir `dependencies` yalnızca boş şablonu sürümünüz bölümde yukarıdaki JSON kod ile değiştirin. Bu dosyayı kullanma hakkında daha fazla bilgi için bkz. [package.json yapılandırma](../javascript/configure-packages-with-package-json.md)

1. Sağ **npm** projenizdeki düğüm ve **güncelleştirme npm paketleri**.

    Alt bölmede seçin **çıkış** paketleri yükleme ilerleme durumunu görmek için penceresi. Yükleme birkaç dakika sürebilir ve sonuçları hemen göremeyebilirsiniz. Çıktıyı görmek için seçtiğinizden emin olun **Npm** içinde **çıktıyı Göster** alanındaki **çıkış** penceresi.

    Bunlar yüklendikten sonra Çözüm Gezgini içinde görülen npm modüllerini aşağıdadır.

    ![npm paketleri](../javascript/media/tutorial-nodejs-react-npm-modules.png)

    > [!NOTE]
    > Komut satırını kullanarak npm paketleri yüklemek isterseniz, proje düğümüne sağ tıklayın ve seçin **burada açık komut istemi**. Paketleri yüklemek için standart Node.js komutlarını kullanın.

## <a name="add-project-files"></a>Proje dosyası Ekle

Bu adımlarda, dört yeni dosyayı projenize ekleyin.

* *app.TSX*
* *webpack-config.js*
* *index.HTML*
* *tsconfig.json*

Bu basit bir uygulama için proje kök dizininde yeni proje dosyalarını ekleyin. (Çoğu uygulamalarında genellikle alt klasörlere dosyaları ekleyin ve göreli yol başvuruları uygun şekilde ayarlayın.)

1. Çözüm Gezgini'nde projeye sağ tıklayın **NodejsWebAppBlank** ve **Ekle** > **yeni öğe**.

1. İçinde **Yeni Öğe Ekle** iletişim kutusunda **TypeScript JSX dosyası**, adı *app.tsx*seçip **Tamam**.

1. Eklemek için bu adımları yineleyin *Web config.js*. Bir TypeScript JSX dosyası yerine seçin **JavaScript dosyası**.

1. Eklemek için aynı adımları yineleyin *index.html* projeye. Bir JavaScript dosyası yerine seçin **HTML dosyası**.

1. Eklemek için aynı adımları yineleyin *tsconfig.json* projeye. Bir JavaScript dosyası yerine seçin **TypeScript JSON yapılandırma dosyası**.

## <a name="add-app-code"></a>Uygulama kodu ekleyin

1. Açık *server.js* ve varolan kodu aşağıdaki kodla değiştirin:

    ```javascript
    'use strict';
    var path = require('path');
    var express = require('express');

    var app = express();

    var staticPath = path.join(__dirname, '/');
    app.use(express.static(staticPath));

    // Allows you to set port in the project properties.
    app.set('port', process.env.PORT || 3000);

    var server = app.listen(app.get('port'), function() {
        console.log('listening');
    });
    ```

   Yukarıdaki kod Express Node.js web uygulaması sunucunuz olarak başlatmak için kullanır. Bu kod, Proje Özellikleri'nde yapılandırılan bağlantı noktası numarası için bağlantı noktasını ayarlar. (varsayılan olarak, bağlantı noktası özelliklerinde 1337 yapılandırılır). Proje Özellikleri'ni açmak için Çözüm Gezgini'nde projeye sağ tıklayıp seçin **özellikleri**.

1. Açık *app.tsx* ve aşağıdaki kodu ekleyin:

    ```javascript
    declare var require: any

    var React = require('react');
    var ReactDOM = require('react-dom');

    export class Hello extends React.Component {
        render() {
            return (
                <h1>Welcome to React!!</h1>
            );
        }
    }

    ReactDOM.render(<Hello />, document.getElementById('root'));
    ```

    Yukarıdaki kod, JSX söz dizimi ve React basit bir ileti görüntülemek için kullanır.

1. Açık *index.html* değiştirin **gövdesi** bölümü aşağıdaki kod ile:

    ```html
    <body>
        <div id="root"></div>
        <!-- scripts -->
        <script src="./dist/app-bundle.js"></script>
    </body>
    ```

    Bu HTML sayfasını yükler *uygulama bundle.js*, düz bir JavaScript için JSX ve React kod transpiled içerir. Şu anda *uygulama bundle.js* boş bir dosyadır. Sonraki bölümde, kodu derleyin seçeneklerini yapılandırın.

## <a name="configure-webpack-and-typescript-compiler-options"></a>Web ve TypeScript derleyici seçeneklerini yapılandırın

Önceki adımda eklediğiniz *Web config.js* projeye. Ardından, Web yapılandırma kodu ekleyin. Giriş dosyası belirten bir basit Web yapılandırma ekleyeceksiniz (*app.tsx*) ve bir çıkış dosyası (*uygulama bundle.js*) paketleme ve transpiling JSX düz JavaScript. Transpiling için de bazı TypeScript derleyici seçeneklerini yapılandırın. Bu kod, Web ve TypeScript derleyicisi için giriş olarak yönelik temel bir yapılandırmadır.

1. Çözüm Gezgini'nde açın *Web config.js* ve aşağıdaki kodu ekleyin.

    ```json
    module.exports = {
        devtool: 'source-map',
        entry: "./app.tsx",
        mode: "development",
        output: {
            filename: "./app-bundle.js"
        },
        resolve: {
            extensions: ['.Webpack.js', '.web.js', '.ts', '.js', '.jsx', '.tsx']
        },
        module: {
            rules: [
                {
                    test: /\.tsx$/,
                    exclude: /(node_modules|bower_components)/,
                    use: {
                        loader: 'ts-loader'
                    }
                }
            ]
        }
    }
    ```

    Web yapılandırma kodu derleyin JSX TypeScript yükleyicisine kullanmak için Web bildirir.

1. Açık *tsconfig.json* varsayılan kodu TypeScript derleyici seçeneklerini belirtir. aşağıdaki kodla değiştirin:

    ```json
    {
      "compilerOptions": {
        "noImplicitAny": false,
        "module": "commonjs",
        "noEmitOnError": true,
        "removeComments": false,
        "sourceMap": true,
        "target": "es5",
        "jsx": "react"
      },
      "exclude": [
        "node_modules"
      ],
      "files": [
        "app.tsx"
      ]
    }
    ```

    *app.TSX* kaynak dosyası olarak belirtilir.

## <a name="transpile-the-jsx"></a>JSX derleyin

1. Çözüm Gezgini'nde proje düğümünü sağ tıklatın ve seçin **burada açık komut istemi**.

1. Komut isteminde aşağıdaki komutu yazın:

    `node_modules\.bin\webpack app.tsx --config webpack-config.js`

    Komut İstemi penceresini sonucu gösterir.

    ![Web çalıştırın](../javascript/media/tutorial-nodejs-react-run-webpack.png)

    Önceki çıkış yerine herhangi bir hata görürseniz, uygulamanızı çalışmadan önce çözmeniz gerekir. Npm Paket sürümü Bu öğreticide gösterilen sürümlerinden farklı ise, hataların bir kaynak olabilir. Hataları düzeltmek için bir önceki adımda gösterilen tam sürümünü kullanmaktır. Ayrıca, bir veya daha fazla bu paket sürümlerini kullanım dışıdır ve hata ile sonuçlanır, hataları düzeltmek için daha yeni bir sürümünü yüklemeniz gerekebilir. Kullanma hakkında bilgi için *package.json* npm paket sürümlerini denetlemek için bkz: [package.json yapılandırma](../javascript/configure-packages-with-package-json.md).

1. Çözüm Gezgini'nde proje düğümünü sağ tıklatın ve seçin **Ekle** > **var olan bir klasörü**, ardından *dist* klasörü seçin  **Klasör seçin**.

    Visual Studio ekler *dist* içeren proje klasörüne *uygulama bundle.js* ve *uygulama bundle.js.map*.

1. Açık *uygulama bundle.js* transpiled JavaScript kodu görmek için.

1. Dışarıdan değiştirilmiş dosyalar yeniden yükleme istenirse seçin **Tümüne Evet**.

    ![Değiştirilen dosyaları yükleme](../javascript/media/tutorial-nodejs-react-reload-files.png)

Her zaman yaptığınız değişiklikleri *app.tsx*, Web komutu çalıştırmanız gerekir.

## <a name="run-the-app"></a>Uygulamayı çalıştırma

1. Chrome, geçerli hata ayıklama hedefi seçin.

    ![Chrome hata ayıklama hedefi olarak seçin](../javascript/media/tutorial-nodejs-react-debug-target.png)

    Chrome makinenizde kullanılabilir, ancak bir seçenek olarak görünmez, seçin **şununla Gözat** hata ayıklama hedef açılır liste ve select Chrome varsayılan tarayıcı hedefi olarak (seçin **varsayılan olarak ayarla**).

1. Uygulamayı çalıştırmak için basın **F5** (**hata ayıklama** > **hata ayıklamayı Başlat**) veya yeşil ok düğmesi.

    Hata ayıklayıcı dinlediği bağlantı noktasını gösteren bir Node.js konsol penceresi açılır.

    Visual Studio, başlangıç dosyasını başlatarak uygulama başlatır *server.js*.

    ![React tarayıcısında çalıştırma](../javascript/media/tutorial-nodejs-react-running-react.png)

1. Tarayıcı penceresini kapatın.

1. Konsol penceresini kapatın.

## <a name="set-a-breakpoint-and-run-the-app"></a>Bir kesme noktası ayarlayın ve uygulamayı çalıştırın

1. İçinde *server.js*, sol tarafındaki cilt payını tıklayın `staticPath` bildirimi bir kesme noktası ayarlamak için:

    ![Bir kesme noktası ayarlayın](../javascript/media/tutorial-nodejs-react-set-breakpoint.png)

    Kesme noktaları güvenilir hata ayıklama en temel hem de temel özelliğidir. Bir kesme noktası değişkenlerin değerleri veya bellek davranışını göz olabilmesi için Visual Studio çalışan kodunuzu nereye askıya almanız ya da bir dal kod getting run olup olmadığını gösterir.

1. Uygulamayı çalıştırmak için basın **F5** (**hata ayıklama** > **hata ayıklamayı Başlat**).

    Hata ayıklayıcı, kesme noktasında duraklatır (sarı renkli geçerli deyim işaretlenmiştir) kümesi. Şimdi, uygulama durumunuzu şu anda, kapsamındaki değişkenlerin üzerine gelerek gibi hata ayıklayıcı penceresini kullanarak inceleyebilirsiniz **Yereller** ve **Watch** windows.

1. Tuşuna **F5** uygulamaya devam etmek için.

1. Chrome geliştirme araçları kullanmak istiyorsanız, basın **F12**. DOM inceleyin ve JavaScript Konsolu'nu kullanarak uygulama ile etkileşim kurmak için bu araçları kullanabilirsiniz.

1. Web tarayıcısı ve konsolu kapatın.

## <a name="set-and-hit-a-breakpoint-in-the-client-side-react-code"></a>Ayarlanmış ve istemci tarafı React kod içinde bir kesme noktasına isabet

Önceki bölümde sunucu tarafı Node.js kod için hata ayıklayıcı iliştirilmiş. Visual Studio'dan hata ayıklayıcının ve istemci tarafı React kodda kesme noktaları isabet, hata ayıklayıcı doğru işlemi tanımlamak için Yardım gerekiyor. Bunu yapmanın bir yolu aşağıda verilmiştir.

1. Tüm Chrome pencerelerini kapatın.

2. Açık **çalıştırma** Windows komutunu **Başlat** düğmesine (sağ tıklatın ve seçin **çalıştırma**) ve aşağıdaki komutu girin:

    `chrome.exe --remote-debugging-port=9222`

    Bu, Chrome etkin hata ayıklama ile başlatır.

3. Bir kesme noktası ayarlayın ve Visual Studio'ya *uygulama bundle.js* kod `render()` işlev aşağıdaki çizimde gösterildiği gibi:

    ![Bir kesme noktası ayarlayın](../javascript/media/tutorial-nodejs-react-set-breakpoint-client-code.png)

    Bulunacak `render()` işlevi *uygulama bundle.js*, kullanın **Ctrl**+**F** (**Düzenle**  >   **Bul ve Değiştir** > **Hızlı Bul**).

4. Visual Studio'da hata ayıklama hedefi olarak seçilen Chrome ile basın **Ctrl**+**F5** (**hata ayıklama** > **hata ayıklama olmadan Başlat** ) tarayıcı içinde uygulamayı çalıştırmak için.

    Uygulama yeni bir tarayıcı sekmesinde açılır.

5. Seçin **hata ayıklama** > **işleme**.

6. İçinde **iliştirme** iletişim kutusunda **Webkit kod** içinde **ekleme** alanına **chrome** filtrelemek için filtre kutusundaki arama sonucu.

7. Doğru konak Chrome işlemle (Bu örnekte 1337) bağlantı noktası seçin seçip **iliştirme**.

    ![İşleme](../javascript/media/tutorial-nodejs-react-attach-to-process.png)

    DOM Gezgini ve JavaScript Konsolu Visual Studio'da açtığınızda hata ayıklayıcı düzgün eklenmiş biliyor. Bu hata ayıklama araçları, Chrome geliştirme araçları ve Edge için F12 araçlarındaki benzerdir.

    > [!NOTE]
    > Hata ayıklayıcıyı iliştirmek değil "işleme yüklenemiyor. iletiyi görürseniz Bir işlem geçerli durumu geçerli değil. ", Görev Yöneticisi'ni kullanarak hata ayıklama modu Chrome başlatmadan önce Chrome tüm örneklerini kapatın. Chrome uzantıları çalıştıran ve tam hata ayıklama modu engelliyor.

8. Kesme noktası koduyla zaten yürütüldü olduğundan, kesme noktasına isabet için tarayıcı sayfanızı yenileyin.

    Hata ayıklayıcıda duraklatıldığı sırada değişkenlerin gelin ve hata ayıklayıcı penceresini kullanarak, uygulama durumunu inceleyebilirsiniz. Hata ayıklayıcı kod içerisinde ilerlemeye tarafından ilerletebilirsiniz (**F5**, **F10**, ve **F11**).

    Herhangi bir kesme noktası isabet *uygulama bundle.js* veya eşlenmiş konumunda *app.tsx*ortamı ve tarayıcı durumunuzu bağlı olarak. Her iki durumda da, kod içinde gezinebilmek ve değişkenleri inceleyin.

   * Kod içinde kesme gerekiyorsa *app.tsx* ve bunu, kullanmanız doğrulanamıyor **iliştirme** hata ayıklayıcıyı iliştirmek için önceki adımlarda açıklandığı gibi. Dinamik olarak üretilen açılacağını *app.tsx* açarak dosya Çözüm Gezgini'nden **betik belgelerini** > **app.tsx**, bir kesme noktası ayarlayın ve Yenile tarayıcınızda sayfa (kesme noktaları, gibi veren kod satırında kesme noktası ayarlamak `return` deyimi veya bir `var` bildirimi).

       Alternatif olarak, kod içinde kesme gerekiyorsa *app.tsx* ve bunu, kullanmayı deneyin `debugger;` deyiminde *app.tsx*, veya Chrome geliştirici araçları kesme noktaları ayarlayın.

   * Kod içinde kesme gerekiyorsa *uygulama bundle.js* ve bunu, kaynak eşleme dosyası Kaldır *uygulama bundle.js.map*.

     > [!TIP]
     > Aşağıdaki adımları izleyerek ilk kez eklediğiniz işleme sonra hızlı bir şekilde Visual Studio 2017'de aynı işlemi seçerek iliştirebilirsiniz **hata ayıklama** > **İliştir**.

## <a name="next-steps"></a>Sonraki adımlar

> [!div class="nextstepaction"]
> [Uygulamayı Linux App Service'e dağıtma](../javascript/publish-nodejs-app-azure.md)