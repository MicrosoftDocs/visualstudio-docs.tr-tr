---
title: Bir Git deposu ayarlama
description: Git, Subversion Mac için Visual Studio kullanarak
author: conceptdev
ms.author: crdun
ms.date: 05/06/2018
ms.assetid: E992FA1D-B2AD-4A28-ADC6-47E4FC471060
ms.openlocfilehash: c8d1cec438c0d942290997a6d51c4c0f2252bf8e
ms.sourcegitcommit: 0a8ac5f2a685270d9ca79bb39d26fd90099bfa29
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/09/2018
ms.locfileid: "51296222"
---
# <a name="set-up-a-git-repository"></a>Bir Git deposu ayarlama

Git takımlar aynı belgelerde aynı anda çalışmasına izin veren bir dağıtılmış sürüm denetim sistemidir. Bu, tüm dosyaları içeren tek bir sunucu yoktur, ancak bu kaynaktan bir depo kullanıma her deponun tamamı makinenizde yerel olarak kopyalanmış olan anlamına gelir.

GitHub ancak yaygın bir ana bilgisayardır sürüm denetimi için Git ile çalışmanıza olanak tanıyan çok uzak ana vardır. Aşağıdaki örnek, bir GitHub konak kullanır, ancak Mac için Visual Studio'da sürüm denetimi için herhangi bir Git ana kullanabilirsiniz

GitHub kullanmak istiyorsanız, bir hesap oluşturulur ve bu makaledeki adımları izlemeden önce yapılandırılmış olduğundan emin olun.

## <a name="creating-a-remote-repo-on-github"></a>GitHub üzerinde uzak bir depo oluşturma

Aşağıdaki örnek, bir GitHub konak kullanır, ancak Mac için Visual Studio'da sürüm denetimi için herhangi bir Git ana kullanabilirsiniz

Bir Git deposu ayarlama için aşağıdaki adımları uygulayın:

1. Github.com yeni Git deposu oluşturun:

    ![Yeni git deposu oluşturma](media/version-control-git1-sml.png)

2. Depo adı, açıklama ve gizlilik ayarlayın. Yapmak **değil** depo başlatın. .Gitignore ve lisans hiçbiri olarak ayarlayın:

    ![Git deposunun kümesi ayrıntıları](media/version-control-git2.png)

3. Sonraki sayfada görüntülemek ve HTTPS ya da SSH adresi oluşturduğunuz depoyu kopyalamak için bir seçenek sunar:

    ![görüntüleme ve kopyalama adresi](media/version-control-git3.png)

   Mac için bu depoya noktası Visual Studio için HTTPS adresi gerekir.

## <a name="publishing-an-existing-project"></a>Mevcut bir projeyi yayımlama

Mevcut bir proje varsa _değil_ zaten sürüm denetiminde Git'te ayarlamak için aşağıdaki adımları kullanın:

1.  Mac için Visual Studio'da Çözüm bölmesi çözüm adı seçin

2. Menü çubuğunda **sürüm denetimi > sürüm denetiminde Yayımla** görüntülenecek **depo seçin** iletişim:

    ![Mac için Visual Studio'da kullanıma almayı başlatma](media/version-control-git4-sml.png)

    Bu menü öğesi menüde gri renkte görünür, çözüm adı seçtiğinizden emin olun.

3. Seçin **kayıtlı depoları** sekmesi ve ENTER tuşuna **Ekle** düğmesi:

    ![](media/version-control-git5.png)

4. Yerel olarak görüntülemek ve #3. adımdaki URL'yi yapıştırın istediğiniz deponun adını girin. Depo yapılandırması iletişim aşağıdakine benzer görünmelidir. Tamam'a basın:

    ![Git Ayrıntıları iletişim girin](media/version-control-git6.png)

    Git'e bağlanmak için SSH kullanmak da mümkündür.

5. Uygulama için Git yayımlamayı denerse için depoyu seçin ve emin her ikisi de **modül adı** ve **ileti** metin alanları tamamlanır:

    ![Proje için git yayımlamayı denerse](media/version-control-git7.png)

6. Tıklayın **Tamam**, ardından **Yayımla** uyarı iletişim.

7. Git kimlik bilgilerinizi Visual Studio'da Mac tercihleri için girdiğiniz değil, şimdi girin. İlk olarak, bir erişim bir parola yerine kullanılan belirteç, oluşturmanız gerekir. Bir erişim belirteci oluşturmadıysanız, Git adımları [erişim belirteci](https://help.github.com/articles/creating-an-access-token-for-command-line-use/) belgeleri.

8. Kullanıcı adı ve kişisel erişim belirteci, girin ve basın **Tamam**:

    ![Git için kullanıcı adı ve parola girin](media/version-control-git9-sml.png)

9. Birkaç saniye sonra çözümü ile ilk alt işleme yayımlanması gerekir. Pek çok seçenek ile doldurulmuş artık sürüm denetimi menü öğesi göz atarak yayımlandı onaylayın:

    ![Sürüm denetimi menüsü](media/version-control-git10.png)

10. Ek değişiklikler yapmak başlattıktan sonra seçin **değişiklikleri gönderdikten** değişiklikleri göndermek için **uzak** depo. Bu, üzerinde github.com görüntülemek uygun tüm kullanıcılara izin verir:

    ![Değişiklikleri uzak depoya gönderin](media/version-control-git11.png)

## <a name="publishing-a-new-project"></a>Yeni bir proje yayımlama

Yeni Proje iletişim kutusu, git kullanarak yeni bir proje yayımlamak için kullanılabilir. Bunu etkinleştirmek için işaretleyin **sürüm denetimi için Git'i kullanabilirsiniz.** Aşağıdaki ekran görüntüsünde gösterildiği gibi onay kutusu. Deponuzu başlatmak ve isteğe bağlı bir .gitignore dosyası ekleyin:

![Değişiklikleri uzak depoya gönderin](media/version-control-git12.png)

## <a name="check-out-an-existing-repository"></a>Mevcut bir havuzuna göz atın

Yerel makinenizde olmayan uzak yalnızca var olan bir GitHub deposu ile çalışmak zorunda kalırsınız olasıdır. Mac için Visual Studio Bu deponun hızla kullanıma olanak sağlar. Makinenize kopyalamak için aşağıdaki adımları izleyin:

1. Menü çubuğunda **sürüm denetimi > kullanıma alma**:

2. Bu görüntüler **depo Bağlan** sekmesinde:

    ![Girilen ayrıntılarla depo sekmesinde bağlanma](media/version-control-git13.png)

3. Uzak deponun GitHub sayfasında basın **Kopyala veya indir** düğmesi ve sağlanan URL'yi kopyalayın:

    ![Görüntülenen github URL'si](media/version-control-git14.png)

4. Tüm metni değiştirin **URL** giriş alanına **depo Bağlan** sekmesi. Bu en diğer alanları bu sekme, #2. adımdaki resimde gösterildiği gibi doldurur.

5. Depoyu kopyalamak ve basın istediğiniz dizini girin **kullanıma alma**.

> [!NOTE]
> Depo 4 GB boyutunda ise sorunlarla karşılaşabilirsiniz.

## <a name="troubleshooting"></a>Sorun giderme

Boş bir uzak depo projenizle başlatma sorunları varsa, aşağıdaki adımları deneyebilirsiniz:

1. Çözüm klasörünüze gidin.
1. Tuşuna **Command + üst karakter +.** Gizli dosya ve klasörleri göstermek için.
1. Varsa bir **.git** klasörünü silin.
1. Varsa bir **da gitignore** dosya, silin.
1. Tuşuna **Command + üst karakter +.** Dosya ve klasörleri gizlemek için.
1. Mac için VS çözümünüzü açın
1. Çözüm paneli üzerinde çözüm düğümü seçin.
1. Sürüm denetimi menüsüne göz atıp seçin **sürüm denetiminde Yayımla**.
1. Adım 6 ' itibaren yukarıdaki öğreticideki adımları izleyin.

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio'da sürüm denetimi (Windows üzerinde)](/visualstudio/version-control/)