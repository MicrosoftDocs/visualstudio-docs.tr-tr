---
title: Node.js kullanarak bir Vue.js uygulaması oluşturma
description: Vue.js framework kullanarak Visual Studio'da Node.js uygulamaları oluşturun
ms.custom: seodec18
ms.date: 07/06/2018
ms.technology: vs-nodejs
ms.topic: conceptual
ms.devlang: javascript
author: mikejo5000
ms.author: mikejo
manager: douge
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: 03576347dc740f44a04ca38150abde458338ef14
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53066882"
---
# <a name="create-a-vuejs-application-using-nodejs-tools-for-visual-studio"></a>Visual Studio için node.js araçları kullanarak Vue.js uygulama oluşturma

Visual Studio 2017 için geliştirilmiş destek içerir [Vue.js](https://vuejs.org/) framework Vue.js, JavaScript ve TypeScript ile uygulama oluşturma geliştirme deneyimini geliştirir.

Aşağıdaki yeni özellikleri, Visual Studio'da Vue.js uygulama geliştirmeyi destekler:

* Betik, stil ve şablon bloklarında desteği *.vue* dosyaları
* Tanıma `lang` özniteliği *.vue* dosyaları
* VUE.js proje ve dosya şablonları

## <a name="prerequisites"></a>Önkoşullar

* Visual Studio 2017 sürüm 15,8 Preview 3 veya üzeri yüklü olmalıdır ve **Node.js geliştirme** iş yükü.

    > [!IMPORTANT]
    > Bu makalede, yalnızca mevcut Visual Studio 2017 sürümünde 15,8 Preview 3 başlatma özellikleri gerektirir.

    Visual Studio henüz yüklemediyseniz, Git [Visual Studio indirmeleri](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) ücretsiz yüklemek için sayfa.

    İş yükünü yükleyin, ancak Visual Studio'a tıklayın, zaten gerektiğinde **açık Visual Studio yükleyicisi** sol bölmesinde bağlantıyı **yeni proje** iletişim kutusu (seçin **dosya**  >  **Yeni** > **proje**). Visual Studio Yükleyicisi'ni başlatır. Seçin **Node.js geliştirme** iş yükü, ardından **Değiştir**.

* ASP.NET Core projesi oluşturmak için ASP.NET ve web geliştirme ve .NET Core çoklu platform geliştirme iş yükleri yüklü olması gerekir.

* Node.js çalışma zamanı yüklü olması gerekir.

    LTS sürümünden yüklü yoksa, yükleme [Node.js](https://nodejs.org/en/download/) Web sitesi. Genel olarak, Visual Studio yüklü Node.js çalışma zamanı otomatik olarak algılar. Yüklü bir çalışma zamanı algılamazsa, projenizi yüklü çalışma zamanı özellikleri sayfasında başvurmak için yapılandırabilirsiniz. (Bir proje oluşturduğunuzda, proje düğümüne sağ tıklayın ve seçin **özellikleri**).

## <a name="create-a-vuejs-project-using-a-template"></a>Bir şablon kullanarak Vue.js projesi oluşturma

Yeni bir proje oluşturmak için yeni Vue.js şablonları kullanabilirsiniz. Şablon kullanımı başlamanın en kolay yoludur. Ayrıntılı adımlar için bkz. [ilk Vue.js uygulamanızı oluşturmak için Visual Studio](../javascript/quickstart-vuejs-with-nodejs.md).

## <a name="create-a-vuejs-project-with-aspnet-core-and-the-vue-cli"></a>ASP.NET Core ve Vue CLI ile bir Vue.js projesi oluşturma

VUE.js hızla yapı iskelesi projeleri için resmi bir CLI sağlar. Uygulamanızı oluşturmak için CLI'yı kullanmak istiyorsanız, geliştirme ortamınızı ayarlamak için bu makaledeki adımları izleyin.

> [!IMPORTANT]
> Bu adımları biraz deneyim Vue.js framework ile zaten sahip olduğunuzu varsaymaktadır. Aksi takdirde, lütfen [Vue.js](https://vuejs.org/) altyapısı hakkında daha fazla bilgi edinmek için.

### <a name="create-a-new-aspnet-core-project"></a>Yeni bir ASP.NET Core projesi oluşturma

Bu örnekte, boş bir ASP.NET Core uygulaması (C#) kullanın. Ancak, çeşitli projeler ve programlama dilleri arasından seçebilirsiniz.

#### <a name="create-an-empty-project"></a>Boş bir proje oluşturun

1. Visual Studio açıp seçin **dosya** > **yeni** > **proje** ana menüden.

1. Altında **Visual C#** > **Web**, seçin **ASP.NET Core Web uygulaması**ve ardından **Tamam**.

    Görmüyorsanız **ASP.NET Core Web uygulaması** proje şablonu, yüklemelisiniz **ASP.NET ve web geliştirme** iş yükü ve. **NET Core** geliştirme iş yükü ilk. Workload(s) yüklemek için tıklayın **açık Visual Studio yükleyicisi** sol bölmesinde bağlantıyı **yeni proje** iletişim kutusu (seçin **dosya**  >  **Yeni** > **proje**). Visual Studio Yükleyicisi'ni başlatır. Gerekli iş yüklerini seçin.

1. Seçin **boş**ve ardından **Tamam**.

    Visual Studio Çözüm Gezgini'nde (sağ bölme) açar Proje oluşturur.

#### <a name="configure-the-project-startup-file"></a>Proje başlangıç dosyasını yapılandırın

* Dosyayı açmak *./Startup.cs*ve yapılandırma yöntemine aşağıdaki satırları ekleyin:

    ```csharp
    app.UseDefaultFiles(); // Enables default file mapping on the web root.
    app.UseStaticFiles(); // Marks files on the web root as servable.
    ```

### <a name="install-the-vue-cli"></a>' % S'vue CLI yükleme

CLI vue npm modülünü yüklemek için bir komut istemi açıp `npm install --g vue-cli` veya `npm install -g @vue/cli` (şu anda beta sürümündeki) sürüm 3.0 için.

### <a name="scaffold-a-new-client-application-using-the-vue-cli"></a>İskele vue CLI kullanarak yeni bir istemci uygulaması

1. Komut istemine gidin ve geçerli dizini, proje kök klasörüne değiştirin.

1. Tür `vue init webpack ClientApp` ve ek soruları yanıtlamak için istendiğinde adımları izleyin.

#### <a name="modify-the-webpack-configuration-to-output-the-built-files-to-wwwroot"></a>Web yapılandırmasını wwwroot oluşturulmuş dosyaları çıkış değiştirin

* Dosyayı açmak *./ClientApp/config/index.js*, değiştirip `build.index` ve `build.assetsRoot` wwwroot yolu:

    ```js
    // Template for index.html
    index: path.resolve(__dirname, '../../wwwroot/index.html'),

    // Paths
    assetsRoot: path.resolve(__dirname, '../../wwwroot'),
    ```

#### <a name="indicate-the-project-to-build-the-clientapp-each-time-that-a-build-is-triggered"></a>ClientApp oluşturmak için projeyi gösteren bir derlemenin tetiklenmesinin her zaman

1. Visual Studio'da Git **proje** > **özellikleri** > **Build Events**.

1. Üzerinde **derleme öncesi olay komut satırı**, türü `npm --prefix ./ClientApp run build`.

#### <a name="configure-webpacks-output-module-names"></a>Web'ın çıktı modül adlarını yapılandırın

* Dosyayı açmak *./ClientApp/build/webpack.base.conf.js*ve çıkış özelliğini aşağıdaki özellikleri ekleyin:

    ```js
    devtoolModuleFilenameTemplate: '[absolute-resource-path]',
    devtoolFallbackModuleFilenameTemplate: '[absolute-resource-path]?[hash]'
    ```

### <a name="add-typescript-support-with-the-vue-cli"></a>Vue CLI ile TypeScript desteği eklendi

Bu adımlar vue-şu anda beta sürümünde olan CLI 3.0 gerektirir.

1. Komut istemine gidin ve geçerli dizin proje kök klasörüyle değiştirin.

1. Tür `vue create ClientApp`ve ardından **özellikleri el ile seçin**.

1. Seçin **Typescript**ve ardından diğer istenen seçenekleri belirleyin.

1. Kalan adımları izleyin ve soruları yanıtlayın.

#### <a name="configure-a-vuejs-project-for-typescript"></a>TypeScript için Vue.js proje yapılandırma

1. Dosyayı açmak *./ClientApp/tsconfig.json* ve ekleme `noEmit:true` derleyici seçenekleri.

    Bu seçenek ayarlayarak, projenizi Visual Studio'da derleyin her zaman karmaşık hale getirmekten kaçının.

1. Ardından, oluşturun bir *vue.config.js* dosyası *./ClientApp/* ve aşağıdaki kodu ekleyin.

    ```js
    module.exports = {
        outputDir: '../wwwroot',

        configureWebpack: {
            output: {
                devtoolModuleFilenameTemplate: '[absolute-resource-path]',
                devtoolFallbackModuleFilenameTemplate: '[absolute-resource-path]?[hash]'
            }
        }
    };
    ```

    Yukarıdaki kod, Web yapılandırır ve wwwroot klasörü ayarlar.

#### <a name="build-with-vue-cli-30"></a>VUE-cli 3.0 ile derleme

Bilinmeyen bir sorun 3.0 vue-CLI ile oluşturma işlemini otomatikleştirmenin engeller. Wwwroot klasörü yenilemeye çalışın her zaman komutunu çalıştırmanız gerekir. `npm run build` ClientApp klasör.

## <a name="limitations"></a>Sınırlamalar

* `lang` öznitelik yalnızca, JavaScript ve TypeScript dilleri de destekler. Kabul edilen değerler şunlardır: js, jsx, ts ve tsx.
* `lang` öznitelik, şablon veya stil etiketler ile çalışmaz.
* Hata ayıklamayı engelleyen *.vue* dosyaları, önceden işlenmiş doğası nedeniyle desteklenmiyor.
* TypeScript tanımıyor *.vue* modülleri olarak dosyaları. TypeScript ne söylemek için aşağıdaki gibi bir kod içeren bir dosyayı duyduğunuz *.vue* dosyaları aramak gibi (vue-cli 3.0 şablonu bu dosya zaten içerir).

    ```js
    // ./ClientApp/vue-shims.d.ts
    declare module "*.vue" {
        import Vue from "vue";
        export default Vue;
    }
    ```

* Komutu çalıştırmadan `npm run build` proje özelliklerinde bir derleme öncesi olay vue-cli 3.0 kullanırken işe yaramazsa gibi.

## <a name="see-also"></a>Ayrıca bkz.
https://vuejs.org/v2/guide -Vue Başlarken Kılavuzu.  
https://github.com/vuejs/vue-cli -Vue CLI projesi.  
https://webpack.js.org/configuration/ -Web yapılandırma belgeleri.
