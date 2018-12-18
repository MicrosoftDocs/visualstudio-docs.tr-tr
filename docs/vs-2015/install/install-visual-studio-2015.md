---
title: Visual Studio 2015'i yükleyin | Microsoft Docs
titleSuffix: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-install
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- vs.about
helpviewer_keywords:
- Visual Studio, installing
- installing Visual Studio
- server installations [Visual Studio]
- Setup [Visual Studio]
- install Visual Studio
- visual studio installer
ms.assetid: da049020-cfda-40d7-8ff4-7492772b620f
caps.latest.revision: 183
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.openlocfilehash: 761264d80c04f0e2ce13a365071f56739d6961a2
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53055173"
---
# <a name="install-visual-studio-2015"></a>Visual Studio 2015'i yükleyin

[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu sayfa yükleme ile yardımcı olacak ayrıntılı bilgiler içerir **Visual Studio 2015**, geliştiriciler için üretkenlik aracından oluşan tümleşik paketimiz. Ayrıca, hızlı bir şekilde için hakkında bilgi almak için bağlantıları ekledik [özellikleri](https://www.visualstudio.com/news/vs2015-vs.aspx), [sürümleri](http://go.microsoft.com/fwlink/?LinkID=242142), [sistem gereksinimleri](https://www.visualstudio.com/products/visual-studio-2015-compatibility-vs), [indirir](http://go.microsoft.com/fwlink/?LinkId=517106), ve daha fazlası.

## <a name="quick-links"></a>Hızlı bağlantılar

Biz ayrıntılara inmek önce en sık istenen bizim bağlantıların bir listesi aşağıda verilmiştir.

|||
|------------------|----------------|
|![Visual Studio'yu indirin](../install/media/downloads.png "indirir") |**İndirmeler**: Visual Studio 2015'i yüklemek için bir ürün yürütülebilir dosyanın indirebilirsiniz [My.VisualStudio.com](https://my.visualstudio.com/downloads?q=visual%20studio%20enterprise%202015) sayfa (abonelik gereklidir) veya paketlenmiş ürün yükleme medyasından kullanın. [Visual Studio, geçerli veya önceki sürümlerini indirme hakkında daha fazla bilgi edinin](https://www.visualstudio.com/vs/older-downloads/).|
|![Özellikler hakkında daha fazla bilgi](../install/media/features.png "özellikleri") |**Özellikleri**: Visual Studio 2015 özellikleri hakkında daha fazla bilgi için yayın notlarına bakın [RTM](https://www.visualstudio.com/news/vs2015-vs), [güncelleştirme 1](https://www.visualstudio.com/news/vs2015-update1-vs), [güncelleştirme 2](https://www.visualstudio.com/news/vs2015-update2-vs), ve [ Güncelleştirme 3](https://www.visualstudio.com/news/releasenotes/vs2015-update3-vs).|
|![Her bir SKU'da ne olduğunu öğrenmek](../install/media/sku.png "SKU'ları") |**SKU'ları**: her iki Visual Studio 2015 sürümünde kullanılabilir olduğunu bulmak için bkz. bizim [Visual Studio tekliflerini karşılaştırın](http://go.microsoft.com/fwlink/?LinkID=242142) sayfası.|
|![Sistem gereksinimlerini görüntüleyin](../install/media/system-requirements.png "sistem gereksinimleri") |**Sistem gereksinimleri**: her iki Visual Studio 2015 sistem gereksinimlerini görmek için bkz: [Visual Studio 2015 uyumluluğu](https://www.visualstudio.com/products/visual-studio-2015-compatibility-vs) sayfası.|
|![Ürün anahtarınızı bulmak](../install/media/product-keys.png "ürün anahtarları") |**Ürün anahtarları**: Ürün anahtarınızı bulmak için bkz: [nasıl yapılır: Visual Studio ürün anahtarını bulmak](../install/how-to-locate-the-visual-studio-product-key.md) konu.|
|![Lisanslama hakkında bilgi edinin](../install/media/licensing.png "lisanslama") |**Lisanslama**: hem kişiler hem de kurumsal müşteriler için lisanslama hakkında bilgi almak için bkz: [Visual Studio ve MSDN Lisanslama](https://www.microsoft.com/download/details.aspx?id=13350) teknik incelemesi.|

##  <a name="custom"></a> Varsayılan vs. Özel Kurulum
 Visual Studio 2015'i yüklediğinizde dahil edebilir veya hariç, günlük olarak kullanacağınız bileşenleri. Bu varsayılan yükleme genellikle daha küçük bir özel yükleme daha hızlı yükleme anlamına gelir. Ayrıca, bu sürümde açıkça seçmelisiniz özel bileşenlerin önceki sürümlerinde varsayılan olarak artık yüklenmiş olan birçok bileşen olarak kabul edilir anlamına gelir.

 ![Visual Studio 2015 Kurulum iletişim](../ide/media/vs2015-setup-screen.png "VS2015_Setup_screen")

 Özel bileşenler dahil Visual C++, Visual F#, SQL Server veri araçları, platformlar arası mobil araçları ve SDK'ları ve üçüncü taraf SDK'ları ve uzantıları. İlk kurulum sırasında seçmezseniz, özel bileşenleri daha sonra yükleyebilirsiniz.

> [!NOTE]
>  Bir özel yükleme otomatik olarak varsayılan yüklemede olan bileşenleri içerir.

 Özel bileşenlerin tam listesi şu şekildedir:

|Özellik kümeleri|Bileşenler|
|------------------|----------------|
|**Güncelleştirmeler**|Visual Studio 2015 Güncelleştirme 3|
|**Programlama dilleri**|Visual C++<br />Visual F#<br />Visual Studio için Python Araçları|
|**Windows ve Web geliştirme**|ClickOnce yayımlama araçları<br />LightSwitch<br />Microsoft Office geliştirici araçları<br />Microsoft SQL Server veri araçları<br /> Microsoft Web geliştirici araçları<br />Visual Studio için PowerShell Araçları (3. taraf)<br />Silverlight Geliştirme Seti<br />Evrensel Windows uygulama geliştirme araçları<br />Windows 10 araçlarını ve Sdk'leri<br />Windows 8.1 ve Windows Phone 8.0/8.1 araçları<br />Windows 8.1 araçları ve SDK'lar|
|**Platformlar arası Mobil Geliştirme**|C# / .NET (Xamarin)<br />HTML/JavaScript (Apache Cordova)<br />Visual C++ Mobil Geliştirme için iOS / Android<br />Microsoft CodeGen ile Clang|
|**Ortak Araçlar ve yazılım geliştirme setleri**|Android yerel Geliştirme Seti (3. taraf)<br /> Android SDK'sı [3. taraf]<br />Android SDK Kurulumu API'leri (3. taraf)<br />Apache Ant (3. taraf)<br /> Java SE Geliştirme Seti (3. taraf)<br /> Joyent Node.js (3. taraf)|
|**Ortak Araçlar**|Windows için Git (3. taraf)<br />Visual Studio için GitHub uzantısı (3. taraf)<br /> Visual Studio genişletilebilirlik araçları|

##  <a name="installing"></a> Visual Studio'yu yükleme
 Visual Studio yükleme medyasını (DVD'ler) kullanarak Visual Studio aboneliği hizmetinizden kullanarak yükleyebileceğiniz [My.VisualStudio.com](https://my.visualstudio.com/downloads?q=visual%20studio%20enterprise%202015) web yükleyicisinden yükleyerek Web sitesi, [Visual Studio İndirmeler](http://go.microsoft.com/fwlink/?LinkId=517106) Web sitesi veya bir çevrimdışı yükleme düzenini oluşturarak (bkz [bir çevrimdışı Visual Studio yüklemesi oluşturma](../install/create-an-offline-installation-of-visual-studio.md) daha fazla ayrıntı için).

> [!IMPORTANT]
>  Yüklemek için yönetici kimlik bilgilerine ihtiyacınız [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Ancak, kullanılacak ihtiyacınız [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] yükledikten sonra.

 Yerel yönetici hesabınızın, etkin olan her şeyi Visual Studio'ya yüklemek için aşağıdaki ayrıcalıkları olmalıdır.

|Yerel ilke nesne görünen adı|Kullanıcı hakkı|
|--------------------------------------|----------------|
|Dosya ve dizinleri yedekle|SeBackupPrivilege|
|Program hata ayıklama|SeDebugPrivilege|
|Denetim ve güvenlik günlüğünü yönetme|SeSecurityPrivilege|

 Bu yerel yönetici hesabı gereksinimi hakkında daha fazla bilgi için bkz. Bilgi Bankası makalesi [Kurulum hesabı belirli kullanıcı haklarına sahip değilse SQL Server yüklemesi başarısız olur](https://support.microsoft.com/en-us/kb/2000257).

###  <a name="BKMK_Media"></a> Yükleme ortamını kullanarak
 Yüklenecek [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], kök dizininde [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] yükleme medyasında, istediğiniz sürümü için yükleme dosyasını çalıştırın:

|Sürüm|Yükleme dosyası|
|-------------|-----------------------|
|Visual Studio Enterprise|vs_enterprise.exe|
|Visual Studio Professional|vs_professional.exe|
|Visual Studio Community|vs_community.exe|

###  <a name="BKMK_Website"></a> Ürünün Web sitesinden indirme
 Ziyaret [Visual Studio indirmeleri](http://go.microsoft.com/fwlink/?LinkId=517106) sayfasında ve istediğiniz Visual Studio sürümünü seçin.

### <a name="downloading-from-your-subscription-service"></a>Abonelik hizmetinizden indiriliyor
 Ziyaret [My.VisualStudio.com](https://my.visualstudio.com/downloads?q=visual%20studio%20enterprise%202015) sayfasında ve istediğiniz Visual Studio sürümünü seçin.

###  <a name="BKMK_Offline"></a> Çevrimdışı yükleme düzen oluşturma
 Yoksa [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] yükleme medyasından veya Visual Studio aboneliği olmadığından veya yüklemek istemediğiniz [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] web Yükleyicisi'ni kullanarak, bir "bağlantısız" yükleme ne çevrimdışı bilinir oluşturarak gerçekleştirebilirsiniz yükleme düzeni. Daha fazla bilgi için [bir çevrimdışı Visual Studio yüklemesi oluşturma](../install/create-an-offline-installation-of-visual-studio.md) sayfası.

##  <a name="enterprise"></a> Visual Studio bir kuruluşta dağıtma
 Nasıl dağıtılacağı hakkında daha fazla bilgi için [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] bir ağ üzerinden bkz [Visual Studio Yönetici Kılavuzu](../install/visual-studio-administrator-guide.md).

###  <a name="BKMK_Virtualized"></a> Sanallaştırılmış bir ortamda Visual Studio'yu yükleme
 **Hyper-V ile video sorunları**

 Hyper-V ve hızlandırılmış grafik bağdaştırıcısının etkin olduğu Windows Server 2008 R2 çalıştırıyorsanız, sistemde yavaşlamalarla karşılaşabilirsiniz.

 Daha fazla bilgi için Microsoft Web sitesindeki şu sayfaya bakın: [Video performansı, Windows Server 2008, küçültebilir veya Windows Server 2008 R2 tabanlı bir bilgisayarda Hyper-V rolü etkinleştirilmişse ve hızlandırılmış görüntü bağdaştırıcısı yüklenmişse](http://go.microsoft.com/fwlink/?LinkID=231084).

 **Cihazlar ile Hyper-V öykünmesini yapma**

 Visual Studio 2015 gerçek donanım sanallaştırma olmaksızın yüklediğinizde, Windows ve Android cihazlarının Hyper-V kullanarak öykünme sağlayan özellikler seçebilirsiniz. Hyper-V yüklediğinizde, Windows veya Android cihazlarına benzetmek mümkün olmayacaktır. Öykünücüler kendilerini sanal makineler olduğundan ve şu anda bir sanal makine başka bir VM içinde barındıramaz budur. Geçici çözüm, gerçek Windows veya kendisine doğrudan dağıtabilir ve uygulamanızda hata ayıklamak Android cihazları sağlamaktır.

##  <a name="optionalComponents"></a> İsteğe bağlı bileşenler yükleniyor
 Özgün yükleme sırasında seçmiş olabilirsiniz bileşenleri yüklemek istiyorsanız, aşağıdaki yordamı kullanın.

#### <a name="to-install-optional-components"></a>İsteğe bağlı bileşenleri yüklemek için

1.  İçinde **Denetim Masası**, **programlar ve Özellikler** sayfasında, bir veya daha fazla bileşen eklemek ve ardından istediğiniz ürün sürümünü **değişiklik**.

2.  Kurulum sihirbazında **Değiştir**ve ardından yüklemek istediğiniz bileşenleri seçin.

3.  Seçin **sonraki**ve ardından kalan yönergeleri izleyin.

##  <a name="helpContent"></a> Çevrimdışı Yardım içeriğini yükleme
 Yükledikten sonra [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], çevrimdışı kullanılabilir olacaktır, böylece Ek Yardım içeriğini indirebilirsiniz.

#### <a name="to-install-or-uninstall-help-content"></a>Yardım içeriğini yüklemek veya kaldırmak için

1. Üzerinde [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] menü çubuğundan **yardımcı**, **kaldırmak Yardım içeriğini Ekle ve**.

2. Üzerinde **içeriği Yönet** sekmesinde **Microsoft Yardım Görüntüleyici**, Yardım içerik yükleme kaynağını seçin.

3. İçin belirli bir Yardım koleksiyonunu arıyorsanız, ad veya bir anahtar sözcük girin **arama** metin kutusuna yazıp ENTER tuşuna **Enter**.

4. Seçmek istediğiniz Yardım koleksiyonunun adının yanında, **Ekle** veya **Kaldır** bağlantı.

5. Tıklayın **güncelleştirme** düğmesi.

   Yükleme veya çevrimdışı Yardım dağıtma hakkında daha fazla bilgi için bkz. [Yardım Görüntüleyicisi Yönetici Kılavuzu'na](../ide/help-viewer-administrator-guide.md).

##  <a name="serviceReleases"></a> Hizmet sürümlerini ve ürün güncelleştirmelerini denetleme
 Tüm uzantıları uyumlu olduğu için önceki sürümlerinden yükselttiğinizde, Visual Studio uzantıları otomatik olarak yükseltmez. Uzantılar'dan yeniden yüklemeniz gerekir [Visual Studio Galerisi](http://go.microsoft.com/fwlink/?LinkId=178891) veya yazılım yayımcısı.

#### <a name="to-automatically-check-for-service-releases"></a>Hizmet sürümlerini otomatik olarak denetlemek için

1.  Menü çubuğunda, **Araçları**, **seçenekleri**.

2.  İçinde **seçenekleri** iletişim kutusunda **ortam**ve ardından **Uzantılar ve güncelleştirmeler**. Emin **güncelleştirmeleri otomatik olarak denetle** onay kutusunun seçili olduğundan ve ardından **Tamam**.

## <a name="registering-visual-studio"></a>Visual Studio'yu kayıt ettirme

1.  Menü çubuğunda, **yardımcı**, **hakkında**.

     **Hakkında** iletişim kutusunda ürün kimlik numarası (PID) gösterilir. Ürün kayıt ettirin PID ve Windows hesabı kimlik bilgilerini (örneğin, Hotmail veya Outlook.com e-posta adresi ve parola) gerekir.

2.  Menü çubuğunda, **yardımcı**, **ürünü kayıt ettir**.

##  <a name="repair"></a> Visual Studio'yu onarma

#### <a name="to-repair-visual-studio"></a>Visual Studio'yu onarmak için

1.  İçinde **Denetim Masası**, **programlar ve Özellikler** onarın ve ardından istediğiniz ürün sürümünü seçin **değişiklik**.

2.  Kurulum sihirbazında **onarım**, seçin **sonraki**ve ardından kalan yönergeleri izleyin.

#### <a name="to-repair-visual-studio-in-silent-or-passive-modes-that-is-to-repair-from-source"></a>Visual Studio'yu Sessiz ya da pasif modda onarmak için (diğer bir deyişle, kaynaktan onarım için)

1.  Visual Studio'nun yüklü olduğu bilgisayarda Windows komut istemini açın.

2.  Aşağıdaki parametreleri girin:

     *DVDRoot* \\< yükleme dosyası\> \</quiet&#124;/passive > [/ norestart] / onarın

##  <a name="troubleshooting"></a> Bir yükleme sorunlarını giderme
 Kurulum ve yükleme sorunları için Yardım almak için bu kaynakları kullanın:

-   [Visual Studio Kurulum ve yükleme](http://go.microsoft.com/fwlink/?LinkID=151190) Forumu. Visual Studio topluluğundaki diğer kişilerden gelen soruları ve yanıtları gözden geçirin. Aradığınızı bulamazsanız, kendi sorularınızı sorun.

-   [Visual Studio için Microsoft Support](http://go.microsoft.com/fwlink/?LinkID=251019) Web sitesi. Bilgi Bankası (BB) makalelerini okuyun ve Visual Studio yüklemesiyle ilgili sorunlar hakkında bilgi için Microsoft Destek birimi ile nasıl iletişim kurabileceğinizi öğrenin.

##  <a name="relatedTopics"></a> İlgili Konular

|Başlık|Açıklama|
|-----------|-----------------|
|[Visual Studio’nun Çevrimdışı Yüklemesini Oluşturma](../install/create-an-offline-installation-of-visual-studio.md)|Visual Studio, Internet'e bağlı olmadığınızda yüklemeyi açıklar.
|[Visual Studio Sürümlerini Yan Yana Yükleme](../install/install-visual-studio-versions-side-by-side.md)|Bir bilgisayara Visual Studio'nun birden fazla sürümünü yükleme hakkında bilgi sağlar.|
|[Komut Satırı Parametrelerini Kullanarak Visual Studio'yu Yükleme](/visualstudio/install/use-command-line-parameters-to-install-visual-studio)|Visual Studio Komut İstemi'nden yüklediğinizde kullanabileceğiniz komut satırı parametrelerini listeler.|
|[Visual Studio'yu kaldırma](../install/uninstall-visual-studio.md)|Visual Studio kaldırmayı açıklar.|
|[Visual Studio Yönetici Kılavuzu](../install/visual-studio-administrator-guide.md)|Visual Studio için dağıtım seçenekleri hakkında bilgi sağlar.|
|[Visual Studio Görüntü Kitaplığı](../designers/the-visual-studio-image-library.md)|Visual Studio uygulamalarında kullanabileceğiniz grafikleri yükleme hakkında bilgi sağlar.|
|[Visual Studio ile Geliştirmeye Başlama](../ide/get-started-developing-with-visual-studio.md)|Bilgi ve Visual Studio daha etkili bir şekilde kullanmanıza yardımcı olabilecek bağlantıları içerir.|

## <a name="see-also"></a>Ayrıca Bkz.

- [Visual Studio'da Oturum Açma](../ide/signing-in-to-visual-studio.md)