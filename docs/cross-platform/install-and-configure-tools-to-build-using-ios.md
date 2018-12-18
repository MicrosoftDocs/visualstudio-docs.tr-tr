---
title: İOS kullanarak derlemeye yönelik ve Yapılandırma Araçları'nı yükleme | Microsoft Docs
ms.custom: ''
ms.date: 05/21/2018
ms.technology: vs-ide-mobile
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: d0c311c9-9eb9-42c5-ba07-25604362cd28
author: corob-msft
ms.author: corob
manager: douge
ms.workload:
- xplat-cplusplus
ms.openlocfilehash: cbc9e2b0016fde990e2fbd6d79b083907ced5060
ms.sourcegitcommit: 71218ffc33da325cc1b886f69ff2ca50d44f5f33
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/09/2018
ms.locfileid: "48881091"
---
# <a name="install-and-configure-tools-to-build-using-ios"></a>Yükleme ve yapılandırma araçları kullanarak iOS oluşturmak için

Platformlar arası Mobil Geliştirme için Visual C++, düzenleme, hata ayıklama ve iOS Simulator'a veya bir iOS cihazının iOS kod dağıtmak için kullanabilirsiniz, ancak lisans kısıtlamaları nedeniyle, kodu oluşturulmuş ve gerekir uzaktan Mac'te çalışan Yapı ve Visual Studio kullanarak iOS uygulamaları çalıştırmak için kurma ve uzak aracı yapılandırma yapmanız [vcremote](https://go.microsoft.com/fwlink/p/?LinkId=534988), mac'inizde Uzak Aracı tutamaçları Visual Studio'dan derleme istekleri ve uygulama, Mac veya Mac üzerinde iOS Simülatörünün bağlı bir iOS cihazında çalışır

> [!NOTE]
> Bulutta barındırılan Mac Hizmetleri yerine bir Mac kullanarak hakkında daha fazla bilgi için bkz: [bulutunuza bağlanmak için Visual Studio'yu yapılandırma barındırılan Mac](/visualstudio/cross-platform/tools-for-cordova/tips-workarounds/host-a-mac-in-the-cloud?view=toolsforcordova-2017#configure-visual-studio-to-connect-to-your-cloud-hosted-mac). Apache Cordova için Visual Studio Araçları'nı kullanarak oluşturmak için yönergeleri verilmiştir. C++ kullanarak oluşturmak için yönergeleri kullanmak için için remotebuild, vcremote değiştirin.

İOS kullanarak geliştirmek için araçları yükledikten sonra yolları hızlı bir şekilde yapılandırın ve Visual Studio ve Mac üzerinde iOS geliştirme için Uzak aracısını güncelleştirmek bu konuya bakın

## <a name="prerequisites"></a>Önkoşullar

Yüklediğinizde ve uzak aracı iOS için kod geliştirme için önce şu önkoşulların olmalıdır:

- OS X Mavericks (sürüm 10.9) ya da üzerini çalıştıran bir Mac bilgisayar

- Bir [Apple kimliği](https://appleid.apple.com/)

- Etkin bir [iOS Developer Program](https://developer.apple.com/programs/ios/) Apple Hesapla

- [Xcode](https://developer.apple.com/xcode/downloads/) 6 veya sonraki bir sürümü.

   Xcode, App Store ' indirilebilir.

- Xcode komut satırı araçları

   Xcode komut satırı araçlarını yüklemek için Mac Terminal uygulamasını açın ve aşağıdaki komutu girin:

   `xcode-select --install`

- İmzalama kimliği Xcode içinde yapılandırılmış bir iOS

   İOS imzalama kimliğini edinme hakkında ayrıntılı bilgi için bkz: [imzalama kimlikleri ve sertifikaları](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppDistributionGuide/MaintainingCertificates/MaintainingCertificates.html) iOS Geliştirici Kitaplığı'nda. Xcode'da imzalama kimliğinizi ayarlayın veya görmek için açık **Xcode** menü ve **tercihleri**. Seçin **hesapları** ve Apple Kimliğinizi seçin ve ardından **ayrıntıları** düğmesi.

- Geliştirme için bir iOS cihazı kullanıyorsanız, bir sağlama profili Xcode'da cihazınız için yapılandırılmış.

   Sağlama profilleri oluşturma hakkında ayrıntılı bilgi için bkz: [sağlama profilleri üye Merkezi'ni kullanarak oluşturma](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppDistributionGuide/MaintainingProfiles/MaintainingProfiles.html#//apple_ref/doc/uid/TP40012582-CH30-SW24) iOS Geliştirici Kitaplığı'nda.

- [Node.js](https://nodejs.org/)

   En son uzun süreli destek (LTS) sürümünü yüklemek mac'inizde node.js 8.x Not diğer son yayın sürümleri vcremote içinde kullanılan bazı modüller desteklemeyebilir ve vcremote yüklemesinin başarısız olmasına neden olabilir.

- Npm güncelleştirilmiş bir sürümü

   Node.js ile birlikte gelen npm sürümünü vcremote yüklemek için güncel olmayabilir. Npm güncelleştirmek için Mac Terminal uygulamasını açın ve aşağıdaki komutu girin:

   `sudo npm install -g npm@latest`

##  <a name="Install"></a> İOS için Uzak aracı yükleme

Platformlar arası Mobil Geliştirme için Visual C++'ı yüklediğinizde Visual Studio ile iletişim kurabilir [vcremote](https://go.microsoft.com/fwlink/p/?LinkId=534988), dosya aktarımı, oluşturun ve iOS uygulamanızı çalıştırma Mac'inizde çalıştıran uzak bir aracı ve hata ayıklama komutları gönderme.

Uzak Aracı yüklemeden önce memnun emin [önkoşulları](#Prerequisites) yüklenip [platformlar arası Mobil Geliştirme için Visual C++](../cross-platform/install-visual-cpp-for-cross-platform-mobile-development.md#install-the-tools).

###  <a name="DownloadInstall"></a> Uzak aracısını indirme ve yükleme için

- Mac Terminal uygulamadan girin:

   `sudo npm install -g --unsafe-perm vcremote`

   Genel yükleme (**-g**) anahtar önerilir ancak gerekli değildir.

   Yükleme sırasında vcremote yüklü olduğundan ve Geliştirici modu Mac'inizde etkinleştirildi [Homebrew](https://brew.sh/) ve iki npm paketi, vcremote LIB ve vcremote-utils da yüklenir. Yükleme tamamlandığında, atlanan isteğe bağlı bağımlılıklar hakkında tüm uyarıları yoksaymak güvenlidir.

   > [!NOTE]
   > Homebrew yüklemek için sudo (Yönetici) erişiminiz olmalıdır. Sudo olmadan vcremote yüklemeniz gerekiyorsa, Homebrew usr/local konumda el ile yükleyin ve kendi bin klasörü yolunuza ekleyin. Daha fazla bilgi için [Homebrew belgeleri](https://github.com/Homebrew/homebrew/wiki/Installation). El ile geliştirici modunu etkinleştirmek için Terminal uygulamada şu komutu girin: `DevToolsSecurity -enable`

Visual Studio'nun yeni bir sürüme güncelleştirmek, uzak aracı de geçerli sürüme güncelleştirmeniz gerekir. Uzak Aracı güncelleştirmek için Uzak aracısını indirme ve yükleme adımları yineleyin.

##  <a name="Start"></a> Uzak Aracı Başlat

Derleme ve iOS kodunuzu çalıştırmak Visual Studio için Uzak Aracı'nın çalışıyor olması gerekir. Bu iletişim kurabilmesi, visual Studio uzak aracı ile eşleştirilmelidir. Varsayılan olarak, uzak aracı Visual Studio ile eşleştirme için PIN gerektiren güvenli bir bağlantı modunda çalışır.

###  <a name="RemoteAgentStartServer"></a> Uzak Aracı başlatmak için

- Mac Terminal uygulamadan girin:

   `vcremote`

   Bu varsayılan derleme dizini ile uzak aracı başlatır ~ / vcremote. Ek yapılandırma seçenekleri için bkz [Mac üzerinde Uzak Aracı yapılandırma](#ConfigureMac).

İlk kez Aracısı'nı başlatın ve dilediğiniz zaman yeni bir istemci sertifikası oluşturma aracı Visual Studio kullanarak ana bilgisayar adı, bağlantı noktası ve PIN dahil olmak üzere yapılandırmak için gerekli bilgiler ile sağlanır.

![Güvenli bir PIN oluşturmak için vcremote kullanın](../cross-platform/media/cppmdd_vcremote_generateclientcert.png "CPPMDD_vcremote_generateClientCert")

Uzak Aracı konak adını kullanarak Visual Studio'da yapılandırmak istiyorsanız, Mac bilgisayardan erişilebilir olduğunu doğrulamak için konak adını kullanarak Windows ping atın. Aksi takdirde, IP adresini kullanmanız gerekebilir.

Oluşturulmuş bir PIN, bir zaman kullanım içindir ve yalnızca sınırlı bir süre için geçerlidir. Süresi sona ermeden önce Visual Studio ile uzak aracı pair değil, yeni bir PIN oluşturmak ihtiyacınız olacak. Daha fazla bilgi için [yeni bir güvenlik PIN'i Oluştur](#GeneratePIN).

Güvenli olmayan modda, uzak aracı kullanabilirsiniz. Güvenli olmayan modda, PIN olmadan Visual Studio için Uzak Aracı eşleştirilmiş.

#### <a name="to-disable-secured-connection-mode"></a>Güvenli bağlantı modu devre dışı bırakmak için

- Vcremote güvenli bağlantı modunda devre dışı bırakmak için Mac'inizde Terminal uygulamada şu komutu girin:

   `vcremote --secure false`

#### <a name="to-enable-secured-connection-mode"></a>Güvenli bağlantı modunu etkinleştirmek için

- Güvenli bağlantı modunu etkinleştirmek için şu komutu girin:

   `vcremote --secure true`

Uzak Aracı başlattıktan sonra siz durduruncaya kadar bunu Visual Studio'dan kullanabilirsiniz.

#### <a name="to-stop-the-remote-agent"></a>Uzak Aracı durdurmak için

- Terminal penceresinde vcremote çalışıyor, girin **denetimi**+**C**.

##  <a name="ConfigureVS"></a> Visual Studio'da uzak aracı yapılandırma

Visual Studio'dan uzak aracıya bağlanmak için Visual Studio seçenekleri Uzaktan yapılandırma belirtmeniz gerekir.

#### <a name="to-configure-the-remote-agent-from-visual-studio"></a>Visual Studio'dan uzak aracı yapılandırma

1. Mac'inizde Aracısı zaten çalışmıyorsa adımları [uzak aracı Başlat](#Start). Mac bilgisayarınızda vcremote başarıyla eşleştirebilir, bağlanma ve projenizi Visual Studio için çalışıyor olması gerekir.

1. Konak adı veya IP adresini Mac Mac'inizde Al

   Kullanarak IP adresini alabilirsiniz **ifconfig** bir Terminal penceresinde komutu. Etkin ağ arabirimi altında listelenen INet adresini kullanın.

1. Visual Studio menü çubuğunda **Araçları**, **seçenekleri**.

1. İçinde **seçenekleri** iletişim kutusunda **Çoklu Platform**, **C++**, **iOS**.

1. İçinde **ana bilgisayar adı** ve **bağlantı noktası** alanları, başlatıldığında uzak aracı tarafından belirtilen değerleri girin. Ana bilgisayar adı, DNS adını veya IP adresini Mac olabilir. Varsayılan bağlantı noktası: 3030.

   > [!NOTE]
   > Ana bilgisayar adını kullanarak Mac ping yapılamıyor, IP adresini kullanmanız gerekebilir.

1. Uzak Aracı varsayılan güvenli bağlantı modunda kullanırsanız, kontrol **güvenli** onay kutusunu uzak aracısı tarafından belirtilen PIN değer enter **PIN** alan. Güvenli olmayan bir bağlantı modunda, uzak aracı kullanmanız durumunda Temizle **güvenli** onay kutusu bırakıp **PIN** alanını boş bırakın.

1. Seçin **çifti** eşleştirme etkinleştirmek için.

   ![İOS yapıları için vcremote bağlantısı yapılandırma](../cross-platform/media/cppmdd_options_ios.PNG "CPPMDD_Options_iOS")

   Konak adı veya bağlantı noktası değiştirene kadar eşleştirmeye devam ettirir. Ana bilgisayar adını değiştirin veya içinde bağlantı noktası **seçenekleri** Seç iletişim kutusu, bir değişikliği geri almak için **geri döndürme** önceki eşleştirmeye geri dönmek için düğme.

   Eşleştirmenin başarısız olursa, Uzak Aracı'ndaki adımları izleyerek çalıştığını doğrulayın [uzak aracı Başlat](#Start). Uzak Aracı PIN oluşturulmasının üzerinden çok uzun zaman geçtiyse, adımları [yeni bir güvenlik PIN'i Oluştur](#GeneratePIN) Mac ve yeniden deneyin. Ana bilgisayar adı Mac kullanıyorsanız, IP adresini kullanarak deneyin **ana bilgisayar adı** bunun yerine alan.

1. Klasör adı güncelleştirme **uzak kök** ev uzak aracısı tarafından kullanılan klasörü belirtmek için alanını (*~*) Mac'te dizin Varsayılan olarak /Users/ uzak aracı kullanır`username`/vcremote uzak kök olarak.

1. Seçin **Tamam** eşleştirme uzak bağlantı ayarları kaydetmek için.

Visual Studio Mac bilgisayarınızda uzak aracı her kullanışınızda bağlanmak için bilgilerin aynısını kullanır. Visual Studio ile eşleştirme uzak aracı ile yeniden Mac'inizde yeni bir güvenlik sertifikası oluşturmak ya da kendi ana bilgisayar adı veya IP adresi değişiklikleri sürece ihtiyacınız yoktur.

##  <a name="GeneratePIN"></a> Yeni bir güvenlik PIN'i oluştur

Oluşturulmuş bir PIN, uzak aracı ilk kez başlattığınızda, sınırlı bir süre için geçerlidir — varsayılan olarak, 10 dakika. Süresi sona ermeden önce Visual Studio için Uzak Aracı eşleştirilmemiş, yeni bir PIN oluşturmak ihtiyacınız olacak.

#### <a name="to-generate-a-new-pin"></a>Yeni bir PIN oluşturmak için

1. Aracısını durdurun veya Mac üzerinde ikinci bir Terminal uygulamasını penceresi açın ve bu komut girmek için kullanın.

1. Bu komut, Terminal uygulamada girin:

   `vcremote generateClientCert`

   Uzak Aracı yeni bir geçici PIN oluşturur. Yeni PIN kullanarak Visual Studio eşleşmesine izin adımlarını yineleyin [Visual Studio'da uzak aracı yapılandırma](#ConfigureVS).

##  <a name="GenerateCert"></a> Yeni bir sunucu sertifikası oluşturma

Güvenlik nedeniyle, sunucunun IP adresi veya ana bilgisayar adını, Mac için Visual Studio ile uzak aracı işletim sistemi bu çiftin sertifikaları Bu değerleri değiştirirseniz, yeni bir sunucu sertifikası oluşturma ve sonra Visual Studio yeni değerlerle yeniden yapılandırmanız gerekir.

#### <a name="to-generate-a-new-server-certificate"></a>Yeni bir sunucu sertifikası oluşturmak için

1. Vcremote aracısını durdurun.

1. Bu komut, Terminal uygulamada girin:

   `vcremote resetServerCert`

1. Onayınız istendiğinde girin `Y`.

1. Bu komut, Terminal uygulamada girin:

   `vcremote generateClientCert`

   Bu, yeni bir geçici PIN oluşturur.

1. Yeni PIN kullanarak Visual Studio eşleşmesine izin adımlarını yineleyin [Visual Studio'da uzak aracı yapılandırma](#ConfigureVS).

##  <a name="ConfigureMac"></a> Mac'te uzak aracı yapılandırma

Çeşitli komut satırı seçeneklerini kullanarak uzak aracı yapılandırabilirsiniz. Örneğin, dosya sisteminde korumak için derleme sayısının üst sınırı belirtin ve yapı isteklerini dinlemek için bağlantı noktası belirtebilirsiniz. Varsayılan olarak, 10 derlemeleri bir sınırdır. Uzak Aracı kapatma sırasında en yüksek süreyi aşmasına derlemeleri kaldırır.

#### <a name="to-configure-the-remote-agent"></a>Uzak Aracı yapılandırma

- Terminal uygulamasında, uzak aracı komutların tam listesi görmek için aşağıdakileri girin:

   `vcremote --help`

- Güvenli modu devre dışı bırakın ve basit HTTP tabanlı bağlantıları etkinleştirmek için şunu girin:

   `vcremote --secure false`

   Bu seçeneği kullandığınızda, Temizle **güvenli** onay kutusu bırakıp **PIN** aracı Visual Studio ile yapılandırırken alanını boş bırakın.

- Uzak Aracı dosyaları için bir konum belirtmek için şunu girin:

   `vcremote --serverDir directory_path`

   Burada *directory_path* günlük dosyaları, yapılar ve sunucu sertifikaları yerleştirmek için mac'inizde konumdur. Varsayılan olarak, bu konumudur */Users/\<kullanıcı adı > / vcremote*. Yapılar, bu konumda derleme numarasına göre düzenlenir.

- Bir arka plan işlemi kullanmak üzere `stdout` ve `stderr` server.log adlı bir dosyaya girin:

   `vcremote > server.log 2>&1 &`

   Server.log dosyanın derleme sorunları gidermenize yardımcı olur.

- Aracı bir yapılandırma dosyası yerine komut satırı parametreleri kullanarak çalıştırmak için şunu girin:

   `vcremote --config config_file_path`

   Burada *config_file_path* JSON biçiminde bir yapılandırma dosyası yolu. Başlangıç seçeneklerini ve değerlerini, kısa çizgi içermemelidir.

## <a name="see-also"></a>Ayrıca bkz.

- [Platformlar arası Mobil Geliştirme için Visual C++'ı yükleme](../cross-platform/install-visual-cpp-for-cross-platform-mobile-development.md)
