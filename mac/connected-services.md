---
title: Bağlı Hizmetler
description: Visual Studio mobile apps için Azure veri depolama, kimlik doğrulaması ve anında iletme bildirimleri için Mac Ekle
ms.assetid: 41CB62FF-0F39-4CE8-8917-6A77F058719F
author: conceptdev
ms.author: crdun
ms.date: 11/06/2018
ms.openlocfilehash: ada47aa3d0cb0d9917404efc2775b843223c6e86
ms.sourcegitcommit: 54c65f81a138fc1e8ff1826f7bd9dcec710618cc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/19/2018
ms.locfileid: "51948952"
---
# <a name="connected-services-walkthrough"></a>Bağlı Hizmetleri gözden geçirme

Hizmet eklemek için projenizin bırakmak zorunda kalmamak için bağlı hizmetler iş akışı, Mac için Visual Studio'ya Azure portal iş akışı getirir.

Bu izlenecek yol, bulut veri depolama, kimlik doğrulama ve platformlar arası Xamarin.Forms taşınabilir sınıf kitaplığı (PCL) uygulamasına anında iletme bildirimleri bir Azure arka uç hizmetini nasıl ekleyeceğiniz gösterilir.

1. Başlangıç çift tıklayarak **bağlı hizmetler** getirir çözüm düğümünde **Hizmetleri galeri**.
  Uygulama türü için tüm kullanılabilir hizmetlerin listesini budur. Bir hizmet seçin (gibi **Azure App Service ile mobil arka uç**) üzerine tıklayarak.

    [![Mac için Visual Studio bağlı Hizmetleri düğümünde](media/connected-services-image001-sml.png "Mac için Visual Studio bağlı hizmetler düğümü")](media/connected-services-image001.png#lightbox)

2. Hizmet Ayrıntıları sayfası açıklamasını hizmet ve yüklenecek bağımlılıklarını sahiptir.
  Tıklayın **Ekle** bağımlılıkları uygulamaya eklemek için:

    [![Azure ile mobil arka uç](media/connected-services-image002-sml.png "Azure ile mobil arka uç")](media/connected-services-image002.png#lightbox)

3. Bağımlılıkları PCL hem platforma özel projeler için çalışmaya eklenmesi gerekir.
  (Doğrudan veya dolaylı olarak) Bakacağınız her projeye hizmet eklemek için onay kutularını seçin:

    [![Hizmet başvurması gereken tüm projeleri denetleyin](media/connected-services-image003-sml.png "hizmet başvurması gereken tüm projeleri denetleyin")](media/connected-services-image003.png#lightbox)

4. Seçin **kabul** üzerinde **lisans kabulü** iletişim kutuları için NuGet paketlerini.
  Kabul etmek için MobileClient ve bağımlılıklar için diğeri SQLiteStore için çevrimdışı veri eşitleme için gerekli olan iki iletişim kutuları olabilir:

    [![Lisans sözleşmelerini kabul](media/connected-services-image004-sml.png "lisans sözleşmelerini kabul edin")](media/connected-services-image004.png#lightbox)

    ![Lisans kabulü penceresini](media/connected-services-image005.png "lisans kabulü penceresi")

5. Bağımlılıkları eklendikten sonra Azure ile iletişim kurması için kullanmak istediğiniz hesabı oturum açması istenir.
  Oturum a Microsoft ID henüz oturum açmadıysanız, Mac için Visual Studio Azure Abonelikleriniz ve bunlarla ilişkili tüm uygulama hizmetleri getirme girişiminde bulunur. Herhangi bir aboneliğiniz yoksa, ücretsiz deneme için kaydolma veya Azure portalında bir abonelik planı satın ekleyebilirsiniz.

6. Bir app service, listeden seçin. Bu şablon kodunu doldurur `MobileServiceClient` nesne üzerinde Azure app Service'in karşılık gelen URL ile:

    [![App service, listeden](media/connected-services-image006-sml.png "listeden app service'ı seçin")](media/connected-services-image006.png#lightbox)

    Listelenen hizmet varsa, tıklayın **yeni** düğmesine (bkz. 9. adım.)

7. Şablon kodunu kopyalayın `MobileServiceClient` PCL içine. Yalnızca bir örneğini var olduğu sürece, dosya konumu önemli değil.
  Oluşturmak için önerilen yaklaşımdır bir `AzureService` kullanır ve tüm Azure etkileşimleri işleme sınıf `MobileServiceClient`:

    ![Config kodu ap kopyalayın](media/connected-services-image007.png "config kodu uygulamaya kopyalayın")

8. Belgelerde izleyin **sonraki adımlar** veri, çevrimdışı eşitleme, kimlik doğrulaması ekleyin ve uygulamanıza anında iletme bildirimleri için:

    [![Sonraki adımları yönergeleri gözden geçirin](media/connected-services-image008-sml.png "sonraki adımları yönergeleri gözden geçirin")](media/connected-services-image008.png#lightbox)

9. Mevcut tüm uygulama hizmetleri yoksa, Mac için Visual Studio içinden ait yeni hizmetler oluşturabilirsiniz.
  Tıklayın **yeni** açmak için hizmetler listesinden pencerenin sol düğmesine **yeni App Service** iletişim:

    [![Mac için Visual Studio'da yeni bir app service oluşturma](media/connected-services-image009-sml.png "Mac için Visual Studio'da yeni bir app service oluşturma")](media/connected-services-image009.png#lightbox)

Yeni bir hizmet için aşağıdaki parametreler gereklidir:

-   **Uygulama hizmeti adı** -planı için benzersiz ad/kimliği
-   **Abonelik** – hizmet için ödeme için kullanmak istediğiniz abonelik
-   **Kaynak grubu** – bir yol veya bir proje için tüm Azure kaynaklarını düzenleme. Var olanı kullan veya yeni bir tane oluşturmak için seçeneği. Bu ilk Azure hizmetinizi ise, yeni bir tane oluşturun.
-   **Hizmet planı** – konum ve onu kullanan tüm kaynakların maliyetini belirler. Var olanı kullan veya yeni bir tane oluşturmak için seçeneği. Bu ilk Azure hizmetinizi ise, varsayılan kullanın veya ücretsiz katmanda (F1) yeni bir tane oluşturun.

Ziyaret [Mobile apps belgeleri](/azure/app-service-mobile/) daha fazla bilgi için.

## <a name="see-also"></a>Ayrıca bkz.

- [Bağlı hizmetler (Windows için Visual Studio)](/visualstudio/azure/vs-azure-tools-connected-services-storage)