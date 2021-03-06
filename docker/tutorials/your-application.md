---
title: 'Docker öğreticisi - 1. Bölüm: Todo list örnek uygulamasını derleme ve çalıştırma'
description: Uygulama içinde çalışan todo listesi örnek uygulamasına genel Node.js.
ms.date: 08/04/2020
author: nebuk89
ms.author: ghogen
manager: jmartens
ms.topic: conceptual
ms.workload:
- azure
ms.openlocfilehash: 9229c3717b686a3f08ef49e7912ac0515864d793
ms.sourcegitcommit: 8b75524dc544e34d09ef428c3ebbc9b09f14982d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/02/2021
ms.locfileid: "113222818"
---
# <a name="build-and-run-the-todo-sample-app"></a>Todo örnek uygulamasını derleme ve çalıştırma

Bu öğreticinin geri kalanında, bu öğreticide çalışan basit bir todo listesi yöneticisiyle Node.js. Bu konuda bilgi sahibi Node.js endişelenmeyin! Gerçek bir JavaScript deneyimi gerekmez!

Bu noktada geliştirme takımınız oldukça küçüktür ve MVP'nizi (en düşük uygun ürün) kanıtlamak için bir uygulama derlersiniz. Büyük bir ekip ve birden çok geliştirici için nasıl çalışabileceklerini düşünmek zorunda kalmadan nasıl çalıştığını ve neler yapabileceğini göstermek istiyor.

![Todo List Manager Ekran Görüntüsü](media/todo-list-sample.png)

## <a name="get-the-app"></a>Uygulamayı alın

Uygulamayı çalıştıramadan önce uygulama kaynak kodunu makinenize alasiniz. Gerçek projeler için genellikle repo klonlar. Ancak bu öğretici için uygulamayı içeren bir ZIP dosyası oluşturduk.

1. Yerel makinede Docker for Windows veya Docker Community Edition'ın yüklü olduğundan emin olun. Docker [for Windows belgelerine bakın.](https://docs.docker.com/docker-for-windows/install/) Yükleme işlemi, örneği içeren ZIP dosyasını localhost adreslerinde kullanılabilir yapar.

1. Docker repolarından [uygulamanın kaynağını](https://github.com/docker/getting-started) indirin. Repo için ZIP dosyasını indirebilirsiniz. ZIP dosyasını indirmek için yeşil Kod düğmesini kullanın ve **ZIP'i** **İndir'i seçin.** UYGULAMA klasöründen sabit sürücüdeki bir klasöre uygulamanın kaynağını ayıklamak için ZIP dosyasını *açın* ve Hepsini Ayıkla'ya tıklayın.

   ![Yeşil Kod düğmesini ve ZIP'i İndir seçeneğini gösteren ekran görüntüsü](media/download-zip.png)

1. Ayıklandıktan sonra projeyi açmak için sık kullanılan kod düzenleyicinizi kullanın. Bir düzenleyiciye ihtiyacınız varsa, bu düzenleyiciyi [Visual Studio Code.](https://code.visualstudio.com/) ve iki alt `package.json` dizinini ( ve ) `src` görüyor `spec` gerekir.

    ![Uygulama Visual Studio Code açık olan dosyanın ekran görüntüsü](media/ide-screenshot.png)

## <a name="building-the-apps-container-image"></a>Uygulamanın kapsayıcı görüntüsünü bina

Uygulamayı derlemek için bir kullan `Dockerfile` gerekir. Dockerfile, kapsayıcı görüntüsü oluşturmak için kullanılan metin tabanlı bir yönergeler betiğidir. Daha önce Dockerfile'lar oluşturduysanız aşağıdaki Dockerfile dosyasında birkaç kusur görebilirsiniz. Ama endişelenmeyin! Bunları daha sonra tekrarlaacağız.

1. Aşağıdaki içeriklere `Dockerfile` sahip dosyayla aynı klasörde `package.json` adlı bir dosya oluşturun.

    ```dockerfile
    FROM node:12-alpine
    WORKDIR /app
    COPY . .
    RUN yarn install --production
    CMD ["node", "/app/src/index.js"]
    ```

    Lütfen dosyanın gibi `Dockerfile` bir dosya uzantısına sahip olmadığını kontrol `.txt` edin. Bazı düzenleyiciler bu dosya uzantısını otomatik olarak ekler ve bu bir sonraki adımda hataya neden olur.

1. Henüz bunu yapmadıysanız bir terminal açın ve ile `app` dizinine `Dockerfile` gidin. Şimdi komutunu kullanarak kapsayıcı görüntüsünü `docker build` derleme.

    ```bash
    docker build -t getting-started .
    ```

    Alternatif olarak Dockerfile'a sağ tıklayarak Görüntü **Derleme...** seçeneğini de seçebilir ve ardından isteminde etiketini belirtebilirsiniz.

    Bu komut, yeni bir kapsayıcı görüntüsü oluşturmak için Dockerfile'ı kullandı. Çok sayıda "katmanın" indirilmiş olduğunu fark etmişsinizdir. Bunun nedeni oluşturucuya görüntüden başlamak istediğinin talimatını `node:12-alpine` vermişsinizdir. Ancak makinede bu görüntüye sahip olmadığınız için bu görüntünün indirilmiş olması gerekir.

    Görüntü indirildikten sonra, uygulamanıza kopyaladınız ve uygulama `yarn` bağımlılıklarınızı yüklemek için kullandınız. `CMD`yönergesi, bu görüntüden bir kapsayıcıyı başlatarak çalıştıracak varsayılan komutu belirtir.

    Son olarak, `-t` bayrağı görüntünizi etiketler. Bunu son görüntü için okunabilir bir ad olarak düşünebilirsiniz. Görüntüyü olarak adlandırılmış `getting-started` olduğunuz için kapsayıcıyı çalıştırarak bu görüntüye başvurabilirsiniz.

    `.`Komutun sonundaki `docker build` komutu Docker'ın geçerli dizinde `Dockerfile` için bakarak bak gerektiğini söyler.

## <a name="starting-an-app-container"></a>Uygulama kapsayıcısı başlatma

Artık bir görüntünüz olduğu için uygulamayı çalıştırın! Bunu yapmak için komutunu kullanın `docker run` (bunu daha önce hatırlayabilirsiniz?).

1. komutunu kullanarak `docker run` kapsayıcınızı başlatın ve yeni oluşturduğunuz görüntünün adını belirtin:

    ```bash
    docker run -dp 3000:3000 getting-started
    ```

    ve `-d` bayraklarını hatırlıyor `-p` musunuz? Yeni kapsayıcıyı "ayrılmış" modda (arka planda) çalıştırarak ana bilgisayar bağlantı noktası 3000 ile kapsayıcının 3000 bağlantı noktası arasında bir eşleme oluşturuyorsunuz. Bağlantı noktası eşlemesi olmadan uygulamaya erişesiniz.

1. Birkaç saniye sonra web tarayıcınızı 'de [http://localhost:3000](http://localhost:3000) açın.
    Uygulamayı görüyorsanız!

    ![Boş Todo Listesi](media/todo-list-empty.png)

1. Devam edin ve bir veya iki öğe ekleyin ve beklediğiniz gibi çalıştığını bakın. Öğeleri tamamlandı olarak işaretlerini kaldırabilir ve öğeleri kaldırabilirsiniz. Ön ucun öğeleri arka uçta başarıyla depolandı! Oldukça hızlı ve kolay, değil mi?

Bu noktada, birkaç öğeyle çalışan bir yapılacaklar listesi yöneticiniz olmalı ve hepsi sizin tarafından ekleyebilirsiniz! Şimdi birkaç değişiklik yapın ve kapsayıcılarınızı yönetme hakkında bilgi edinin.

VS Code uzantısına hızlıca göz atacak olursanız iki kapsayıcının (bu öğretici ve yeni başlatılan uygulama kapsayıcınız) çalışıyor olduğunu görüyor olun!

![Öğretici ve uygulama kapsayıcıları çalıştıran Docker Uzantısı](media/vs-two-containers.png)

## <a name="recap"></a>Özet

Bu kısa bölümde kapsayıcı görüntüsü oluşturmayla ilgili temel bilgileri öğrendin ve bunu yapmak için bir Dockerfile oluşturdunız. Bir görüntü 2009'da kapsayıcıyı başlattıktan sonra çalışan uygulamayı görmüş olduktan sonra!

Ardından uygulamada bir değişiklik yapacak ve çalışan uygulamayı yeni bir görüntüyle güncelleştirmeyi öğreneceksiniz. Bu arada, birkaç yararlı komut daha öğrenirsiniz.

## <a name="next-steps"></a>Sonraki adımlar

Öğreticiye devam edin!

> [!div class="nextstepaction"]
> [Uygulama güncelleştirme](update-your-app.md)
