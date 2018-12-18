---
title: Linux App Service'te bir Node.js uygulaması yayımlama
description: Node.js uygulamalarını azure'da bir Linux App Service için Visual Studio'da oluşturulan yayımlayabilirsiniz.
ms.custom: ''
ms.date: 11/1/2018
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
ms.openlocfilehash: 8af99919fe80f1f5e2776e381d24aa8d37bad36d
ms.sourcegitcommit: 1df0ae74af03bcf0244129a29fd6bd605efc9f61
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/01/2018
ms.locfileid: "50750777"
---
# <a name="publish-a-nodejs-application-to-azure-linux-app-service"></a>Bir Node.js uygulaması (App Service Linux) azure'a yayımlama

Bu öğretici, basit bir Node.js uygulaması oluşturma ve Azure'a yayımlama görevi size kılavuzluk eder.

Azure'a bir Node.js uygulaması yayımlama sırasında birkaç seçenek vardır. Bunlar, Azure App Service, seçtiğiniz, Azure Container Service (AKS) yönetim için Kubernetes, Docker ve daha fazlasını kullanarak bir kapsayıcı örneği ile bir işletim sistemini çalıştıran bir VM içerir. Bu seçeneklerin her biri hakkında daha fazla bilgi almak için bkz. [işlem](https://azure.microsoft.com/product-categories/compute/).

Bu öğreticide, uygulamayı dağıttığınız [Linux App Service](/azure/app-service/containers/app-service-linux-intro).
Linux App Service Node.js uygulaması (aksine, Windows uygulama Node.js uygulamalarını IIS arkasında Windows üzerinde çalışan hizmeti) çalıştırmak için Linux Docker kapsayıcısını dağıtır.

Bu öğreticide Visual Studio için Node.js araçları ile yüklenen bir şablon başlayarak bir Node.js uygulaması oluşturma, kod github'daki depoya itme ve gelen dağıtabilirsiniz, böylece bir Azure App Service Azure web portalı üzerinden sağlama işlemini gösterir. GitHub deposu. Azure uygulama hizmeti sağlama ve yerel bir Git deposundan kod göndermek için komut satırı kullanmak için bkz. [Node.js uygulaması oluşturma](/azure/app-service/containers/quickstart-nodejs).

Bu öğreticide, şunların nasıl yapılır:
> [!div class="checklist"]
> * Node.js projesi oluşturma
> * Kodunuz için bir GitHub deposu oluşturma
> * Azure'da bir Linux App Service oluşturma
> * Linux için dağıtma

## <a name="create-a-nodejs-project-to-run-in-azure"></a>Azure'da çalıştırmak için bir Node.js projesi oluşturma

1. Kullanarak yeni bir TypeScript Express uygulaması oluşturma **dosya** > **yeni proje** iletişim kutusu.

1. Altında **TypeScript** düğümünü **temel Node.js Express 4 uygulaması**.

    ![Yeni bir TypeScript Express uygulaması oluşturma](../javascript/media/azure-ts-express-app.png)

1. Tıklayın **Tamam** Visual Studio'da proje oluşturmaktır.

1. Tuşuna **F5** oluşturun ve uygulamayı çalıştırın ve her şeyin beklendiği gibi çalıştığından emin olun.

1. Seçin **dosya** > **kaynak denetimine Ekle** proje için yerel bir Git deposu oluşturmak için.

    Bu noktada, Node.js kullanarak bir uygulaması Express framework ile yazılmış TypeScript çalışıyor ve yerel kaynak denetimine iade edildi.

1. Projenin sonraki adımlara geçmeden önce istediğiniz gibi düzenleyin.

## <a name="push-code-from-visual-studio-to-github"></a>GitHub Visual Studio kodu

Visual Studio için GitHub'ı ayarlamak için:

1. Emin [Visual Studio için GitHub uzantısı](https://visualstudio.github.com/) yüklü ve etkin menü öğesini kullanarak **Araçları** > **Uzantılar ve güncelleştirmeler**.

2. Menüden **görünümü** > **diğer Windows** > **GitHub**.

    GitHub penceresi açılır.

3. Görmüyorsanız **Başlarken** GitHub penceresinde düğmesini tıklatın, **dosya** > **kaynak denetimine Ekle** ve güncelleştirmek kullanıcı Arabirimi için bekleyin.

    ![GitHub penceresini açın](../javascript/media/azure-github-get-started.png)

4. Tıklayın **başlama**.

    Github'a zaten bağlıysa, araç aşağıdaki çizime benzer görünür.

    ![GitHub depo ayarları](../javascript/media/azure-github-publish.png)

5. Yayımlayın ve ardından yeni bir havuz için alanları doldurun **Yayımla**.

    Birkaç dakika sonra "Depo başarıyla oluşturuldu" belirten bir başlık görüntülenir.

    Sonraki bölümde, bu depodan bir Linux üzerinde Azure App Service'e yayımlama konusunda bilgi edinin.

## <a name="create-a-linux-app-service-in-azure"></a>Azure'da bir Linux App Service oluşturma

1. Oturum [Azure portalında](https://portal.azure.com).

2. Seçin **uygulama hizmetleri** solda, hizmetler listesinden ve ardından **Ekle**.

3. Gerekirse, yeni uygulamayı barındırmak için yeni bir kaynak grubu ve App Service planı oluşturun.

4. Ayarladığınızdan emin olun **işletim sistemi** için **Linux**, ayarlayıp **çalışma zamanı yığını** çizimde gösterildiği gibi gerekli Node.js sürümü için.

    ![Bir Linux App Service oluştur](../javascript/media/azure-create-appservice-annotated.png)

5. Tıklayın **Oluştur** App Service oluşturma.

    Bunu dağıtılması birkaç dakika sürebilir.

6. Dağıtıldıktan sonra Git **uygulama ayarları** bölümünde ve adı ile bir ayar ekleyin `SCM_SCRIPT_GENERATOR_ARGS` değerini `--node`.

    ![Uygulama ayarları](../javascript/media/azure-script-generator-args.png)

    > [!WARNING]
    > App Service dağıtım işlemi, deneyin ve çalıştırmak için uygulama türünü belirlemek için buluşsal yöntem kümesi kullanır. Varsa bir. *sln* dosya dağıtılan içeriği algılandığında, dayalı MSBuild Projesi dağıtıldığı varsayar. Yukarıda eklediğiniz ayarı, bu mantık geçersiz kılar ve bir Node.js uygulaması olduğunu açıkça belirtir. Bu ayar olmadan alıyorsa, dağıtılacak Node.js uygulaması başarısız olur. *sln* dosya adlı App Service ile dağıtılan deponun bir parçasıdır.

7. Dağıtıldıktan sonra App Service'ı açın ve seçin **dağıtım seçenekleri**.

    ![Dağıtım seçenekleri](../javascript/media/azure-deployment-options.png)

8. Tıklayın **Kaynak Seç**ve ardından **GitHub**ve ardından gerekli izinlerin yapılandırın.

    ![GitHub izinleri](../javascript/media/azure-choose-source.png)

9. Depoyu seçin ve yayımlamak için dal ve ardından **Tamam**.

    ![Linux App Service’e yayımlama](../javascript/media/azure-repo-and-branch.png)

    **Dağıtım seçenekleri** sayfası eşitlenirken görüntülenir.

    ![Dağıtma ve GitHub ile eşitleniyor](../javascript/media/azure-deployment-options-sync.png)

    İşlem tamamlandığında eşitleme, bir onay işareti görünür.

    GitHub deposundan Node.js uygulaması çalıştıran artık site olduğunu ve Azure App Service için oluşturulan URL'sinde erişilebilir (varsayılan olarak Azure App Service'e verilen ad ve ardından ". azurewebsites.net").

## <a name="modify-your-app-and-push-changes"></a>Uygulama ve anında iletme değişikliklerinizi değiştirme

1. Burada gösterilen kod ekleme *app.ts* satırdan `app.use('/users', users);`. Bu URL'de bir REST API ekler */API'si*.

    ```typescript
    app.use('/api', (req, res, next) => {
        res.json({"result": "success"});
    });
    ```

2. Kod ve test, yerel olarak iade Github'a gönderme oluşturun.

    Azure portalında GitHub deposunda değişikliklerini algılamak için birkaç dakika sürer ve ardından dağıtım için yeni bir eşitleme başlatır. Bu, aşağıdaki çizime benzer.

    ![Değiştirme ve eşitleme](../javascript/media/azure-changes-detected.png)

3. Dağıtım tamamlandıktan sonra genel sitesine gidin ve ekleme */API'si* URL'si. JSON yanıtı döndürdü.

## <a name="troubleshooting"></a>Sorun giderme

* Node.exe işlemi bitmeden (diğer bir deyişle, işlenmeyen bir özel durum gerçekleşir), kapsayıcı yeniden başlatılır.
* Kapsayıcı başlatıldığında Node.js işlemini nasıl bağlayacağınızı çeşitli buluşsal yöntemler aracılığıyla çalıştırır. Uygulama ayrıntılarını en görülebilir [generateStartupCommand.js](https://github.com/Azure-App-Service/node/blob/master/8.9.4/startup/generateStartupCommand.js).
* Araştırmalar için çalışmakta olan kapsayıcıyı SSH aracılığıyla bağlanabilirsiniz. Bu bir kolayca gerçekleştirilir Azure portalını kullanarak. App Service'ı seçin ve araçları listesini kaydırın ulaşana kadar **SSH** altında **geliştirme araçları** bölümü.
* Giderilmesine yardımcı olmak için Git **tanılama günlükleri** App Service ve değişiklik ayarlarını **Docker kapsayıcı günlüğe kaydetme** ayarını **kapalı** için  **Dosya sistemi**. Günlükleri kapsayıcısı altında oluşturulur */home/LogFiles/*_docker.log*, SSH veya FTP (S) kullanarak kutusu üzerinde erişilebilir.
* Özel etki alanı bir siteye atanabilir yerine *. azurewebsites.net URL'SİYLE varsayılan olarak atanır. Daha fazla bilgi için Ek Yardım konusuna [harita özel etki alanı](/azure/app-service/app-service-web-tutorial-custom-domain).
* Üretime geçmeden önce daha fazla test için hazırlama sitesi dağıtımı iyi bir uygulamadır. Bu, yapılandırma hakkında ayrıntılı bilgi için bkz: [hazırlık ortamları oluşturma](/azure/app-service/web-sites-staged-publishing).
* Bkz: [App Service Linux SSS](/azure/app-service/containers/app-service-linux-faq) daha sık sorulan sorular için.

## <a name="next-steps"></a>Sonraki adımlar

Bu öğreticide şunları öğrendiniz nasıl bir Linux App Service oluştur ve hizmeti bir Node.js uygulaması dağıtın. Linux App Service hakkında daha fazla bilgi edinmek isteyebilirsiniz.

> [!div class="nextstepaction"]
> [Linux uygulama hizmeti](/azure/app-service/containers/app-service-linux-intro)
