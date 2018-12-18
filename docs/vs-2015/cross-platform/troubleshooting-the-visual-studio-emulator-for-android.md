---
title: Android için öykünücüsü sorunlarını giderme | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- tgt-pltfrm-cross-plat
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f3fb5df4-3aae-40e4-9450-bbe15b0c5af5
caps.latest.revision: 25
ms.author: crdun
manager: crdun
ms.openlocfilehash: c1d8310cb2585dfd2041ce25fd4301b557521911
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53068237"
---
# <a name="troubleshooting-the-visual-studio-emulator-for-android"></a>Android için Visual Studio Öykünücüsü’nde Sorun Giderme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]


Bu konuda, Android için Visual Studio öykünücüsü'nü kullanırken karşılaşabileceğiniz sorunları çözmenize yardımcı olacak bilgiler içerir.

> [!WARNING]
>  Öykünücü yüklendikten sonra Kurulum programı yazılımı çalıştıran önkoşulları denetler. Önkoşulları mevcut değildir, ancak bunları yükleme için gerekli olmadığı uyarıları görüntüler.

 Bu konuda aşağıdaki bölümleri içerir.

-   [Başlamadan önce](#BeforeYouStart)

-   [Öykünücüsü yüklenemez](#NoInstall)

-   [Bir etki alanı ya da kurumsal ağ üzerindeki Ağ Hedefe bağlanamıyor](#DomainNetwork)

-   [Ağ ayarlarını el ile yapılandırma gerektirdiğinde Ağ Hedefe bağlanamıyor](#ManualNetworkConfig)

-   [Öykünücü yavaş, zaman aşımı nedeniyle başlatmak için başarısız başlatılır veya uygulama dağıtımı başarısız oluyor](#SlowStart)

-   [Öykünücüsü başlatılamıyor](#NoStart2)

-   [Öykünücü (ilk kullanımda) başlatılamıyor.](#NoStart)

-   [Öykünücü yüklendikten sonra önyükleme bilgisayar başarısız](#NoBoot)

-   [Visual Studio öykünücüsü için uygulama dağıtılmaya çalışılırken takılı veya öykünücü diğer IDE içinde hata ayıklama hedefi olarak görünmüyor](#ADB)

-   [UDP bağlantı noktası ' ayarlanamadı çünkü öykünücü yanıt vermemeye başlıyor](#XamarinPlayer)

-   [Bir Xamarin projesi için hata ayıklayıcı eklenemiyor](#Skylake)

-   [Google Play hizmetleri kullanan bir uygulamayı çalıştırmak öykünücü başarısız](#GooglePlay)

-   [Sürükle ve bırak bir dosya, APK veya açılıp dosyasının çalışmıyor](#DragAndDrop)

-   [Ekran çözünürlüğü yanlış](#Resolution)

-   [OpenGL içeriğini işlemek öykünücü başarısız](#OpenGL)

-   [Öykünücü, çok noktalı dokunma hareketlerini için yanıt vermiyor](#Multitouch)

-   [Destek kaynakları](#Support)

##  <a name="BeforeYouStart"></a> Başlamadan önce
 Sorun gidermeye başlamadan önce aşağıdaki konuları gözden geçirmeniz faydalı olabilir:

-   [Android için Visual Studio Öykünücüsü Sistem Gereksinimleri](../cross-platform/system-requirements-for-the-visual-studio-emulator-for-android.md)

##  <a name="NoInstall"></a> Öykünücüsü yüklenemez
 Hyper-V yüklü yoksa öykünücü yüklemeye çalıştığınızda şu iletiyi görürsünüz. HyperV destekleyen bir makine olmalıdır ve etkinleştirilmesi gerekir.

 ![Android&#95;AB&#95;yükleme&#95;sorunu](../cross-platform/media/android-emu-install-issue.png "Android_Emu_Install_Issue")

> [!NOTE]
>  Bu ileti, hem Visual Studio öykünücüsü Android ve Windows Phone öykünücüsü için geçerlidir. Öykünücü, Windows 8.1 ve Windows 10'u destekler.

 Bu iletiyi görürseniz denetleyin [Android için Visual Studio öykünücüsü sistem gereksinimleri](../cross-platform/system-requirements-for-the-visual-studio-emulator-for-android.md) öykünücüyü çalıştırmak olup olmadığını görmek için.

##  <a name="DomainNetwork"></a> Bir etki alanı ya da kurumsal ağ üzerindeki Ağ Hedefe bağlanamıyor
 Android için Visual Studio öykünücüsü ağ üzerinde kendi IP adresine sahip ayrı bir cihaz olarak görünür. Bir Windows etki alanına katılmamışsa ve ana bilgisayar ile etki alanı veya çalışma grubu kimlik bilgileri paylaşmaz.

 Ağınızın temel ağ ve Internet bağlantısı için etki alanı veya çalışma grubu yetkilendirme gerektiriyorsa, özel durum için BT yöneticinize başvurun. Bu özel durumun geliştirme bilgisayarınıza bir sınır makine olarak görev yapacak ve öykünücü gibi ağ etki alanı ile birleşik olmayan cihazlardan gelen bağlantıları kabul etmek üzere sağlar.

 Android için Visual Studio öykünücüsü, ayrıca kendi MAC adresleri kümesini kullanır. Öykünücüsünden ağ veya Internet kaynaklarına erişim sağlayamazsanız öykünücü'nın MAC adresleri ağınızda yetkilendirilmiş emin olmak için BT yöneticinize danışın.

#### <a name="to-view-the-emulators-mac-addresses"></a>Adreslerini öykünücü'nın MAC görüntülemek için

1.  Öykünücüyü başlatın.

2.  Öykünücü araç çubuğunda köşeli çift ayraç düğmesini (>>) ek araçları penceresini açın.

3.  Ek araçlar penceresine, ağ sekmesini tıklatın.

4.  Ağ sayfasında, fiziksel adres girdilerini bulun.

##  <a name="ManualNetworkConfig"></a> Ağ ayarlarını el ile yapılandırma gerektirdiğinde Ağ Hedefe bağlanamıyor
 Öykünücüsünden ağ hedeflerine bağlamak için ağınıza aşağıdaki gereksinimleri karşılaması gerekir:

- DHCP. Kendi IP adresini ağ üzerinde ayrı bir cihaz olarak kendisini yapılandırır için öykünücü DHCP gerektirir.

- Otomatik olarak yapılandırılan DNS ve ağ geçidi ayarları. Öykünücü için el ile DNS ve ağ geçidi ayarlarını yapılandırmak mümkün değildir.

  Ağınız el ile yapılandırılan ayarların gerektiriyorsa ve öykünücüsü için ağ bağlantısını nasıl olanak sağlayabileceğiniz belirlemek için BT yöneticinize danışın.

##  <a name="SlowStart"></a> Öykünücü yavaş, zaman aşımı nedeniyle başlatmak için başarısız başlatılır veya uygulama dağıtımı başarısız oluyor
 Belirli koşullar altında öykünücü başlatmak için birkaç dakika sürer veya bir zaman aşımı nedeniyle başlatılamıyor. Öykünücü başlatmak başarısız olduğunda, aşağıdaki iletiyi görürsünüz: `App deployment failed. Please try again`. Aşağıdaki koşullar Bu hataya neden.

-   Visual Studio öykünücüsü Android için önyüklenebilir bir VHD'den çalıştırılıyor. Bu yapılandırma desteklenmez.

-   Hatalı sabit sürücü. Chkdsk programı çalıştırmayı göz önünde bulundurun.

-   Bir sabit sürücü birleştirilmesi gerekir. Sürücü birleştirmeyi göz önünde bulundurun.

-   Bir sabit sürücü dolmak üzere. Sürücüde kullanılabilir alan kontrol edin.

-   Yetersiz bellek nedeniyle çalışan diğer uygulamaları kullanılabilir. Bellek miktarını artırın veya bellek kullanan uygulamaların sayısını azaltın.

-   Genellikle, sistemdeki zayıf performansa katkıda bulunan tüm faktörü. En düşük alt Denetim Masası'nın performans bilgi ve araçları sayfasında bulabilirsiniz Windows Deneyimi Dizini olan bileşeni ile sorun giderme başlar.

##  <a name="NoStart2"></a> Öykünücüsü başlatılamıyor
 Öykünücü daha önce çalışıyor olsa da artık çalışmaz, aşağıdaki görevleri gidin. Öykünücü ilk kez kullanıyorsanız bkz [öykünücü başarısız (ilk kullanımda) başlatmak](#NoStart) önce aşağıdaki adımları deneyin.

-   Öykünücü diğer Hyper-V örneklerini kaldırın.

    1.  Visual Studio’yu kapatın.

    2.  Hyper-V Yöneticisi'ni açın ve herhangi bir Hyper-V örneği zaten çalışıyor öykünücüsü (sanal makineler) ve muhtemelen bozuk bir durumda durdurun.

    3.  Hyper-V Yöneticisi'nde, diğer bir öykünücü tüm sanal makineleri silin.

    4.  Makinenizi yeniden başlatın.

-   En az 4 GB sistem belleği ve bunu diğer yoğun kaynak programlar ve işlemler (örneğin, tüm tarayıcı pencerelerini kapatmayı deneyin) tarafından Tüketilmekte olan değil, sahip olduğunuzdan emin olun.

-   Sanal Anahtar Yöneticisi ve denetim, iki ağ anahtarları olduğunu görmek için Hyper-V Yöneticisi'nde açın; ilk iç anahtar ve ikinci dış olduğundan emin olun.

     ![Android&#95;AB&#95;V&#95;anahtar&#95;Man](../cross-platform/media/android-emu-v-switch-man.png "Android_Emu_V_Switch_Man")

     Kuruluma yanlış ise ve Windows 10 kullanıyorsanız, deneyebilir [netcfg – d komutu kullanarak ağ aygıtlarını yeniden](http://windows.microsoft.com/windows-10/fix-network-connection-issues) (Bölüm 6).

-   Bu adımlar sorunu çözmezse bkz [öykünücü başarısız (ilk kullanımda) başlatmak](#NoStart) öykünücü ile engellemesini 3 taraf yazılım hakkında bilgi için.

##  <a name="NoStart"></a> Öykünücü (ilk kullanımda) başlatılamıyor.
 Öykünücü başlatılmazsa belirlemek ve sorunu gidermek için aşağıdaki görevleri gidin.

- En düşük donanım gereksinimleri karşılandıktan ve BIOS ayarları doğru olduğundan emin olun.

   Öykünücü ve Windows 8 Hyper-V, ikinci düzey adres çevirisi (SLAT) ile 64-bit işlemci gerektirir. Intel, temelde çekirdek ı3 i5 veya i7 işlemci (ya da birçok Xeon birini) gerekir. AMD yongaları listesi kullanılabilir [burada](http://support.amd.com/en-us).

  1. Bilgisayar karşıladığından emin olun [sistem gereksinimleri](../cross-platform/system-requirements-for-the-visual-studio-emulator-for-android.md).

  2. Doğrulayın [SLAT aracı](https://slatstatuscheck.codeplex.com/) bilgisayarınızı SLAT özellikli olduğunu bildirir.

  3. Bilgisayarınızın BIOS ayarları içinde tüm sanallaştırma teknolojisini etkin olduğundan emin olun. Tam BIOS açıklamaları için her bir donanım üreticisinin farklılık gösterebilir. Genel olarak, ilgili özellikleri sağlar:

     -   SLAT (ikinci düzey adres çevirisi)

     -   (Genişletilmiş sayfa tabloları) kabul et (Intel)

     -   NPT (iç içe sayfa tabloları) (AMD)

     -   (Hızlı sanallaştırma dizini) RVI (AMD)

     -   VMX (bir Intel harflendirme belirten donanım Yardımlı sanallaştırma desteği)

     -   SVM (donanım Yardımlı sanallaştırma desteği belirten bir AMD kısaltması)

     -   XD (yürütmeyi devre dışı bırak) (Intel); Bu etkinleştirilmelidir

     -   NX (Execute)(AMD) yok; Bu etkinleştirilmesi gerekir.

  4. Aşağıdaki seçenekler BIOS'ta varsa, bunları devre dışı bırakın.

     - Intel VT-d devre dışı bırak

     - Güvenilir yürütme devre dışı bırak

       Bu makalede daha fazla bilgi için bkz: Technet: Hyper-V: nasıl düzeltme BIOS hataları etkinleştirme Hyper-V'ye

  5. En az 4 GB sistem belleği ve bunu diğer yoğun kaynak programlar ve süreçler tarafından Tüketilmekte olan değil, sahip olduğunuzdan emin olun.

  6. Daha iyi veya Windows 8 Professional çalıştırdığınızdan emin olun (Windows Server 2008 desteklenmez). Windows Server 2012 desteklenir, ancak masaüstü deneyimi etkinleştirmeniz gerekir.

     Hiper yönetici hataları olup olmadığını görmek için Olay Görüntüleyicisi'ni inceleyebilirsiniz. Bunu yapmak için Olay Görüntüleyicisini açın (Başlat tuşu + R, ardından yazın `eventvwr`) ve ardından **Windows Günlükleri**, **sistem**. Daha sonra kaynak ayarını günlük, olay kaynağına göre filtre **Hyper-V-hiper yönetici**. Kök nedeni belirlemenize yardımcı olması hata olup olmadığını denetleyin.

     En düşük gereksinimler ancak hiper yönetici hala başarısız, işlemci karşıladığını gerçekleştiriliyorsa, bulma olmadığını öğrenmek için bilgisayarınızın BIOS yükseltme yok. Varsa, yükseltme, üreticinin tüm önlemler (örneğin, BIOS üretici yazılımı yükseltme BIOS kalıcı olarak bozabilir ve güç kaybı tarafından engellenmez sağlamaktan) BIOS yükseltirken gözlemlemek mutlaka seçin.

- En az 4 GB sistem belleği ve bunu diğer yoğun kaynak programlar ve süreçler tarafından Tüketilmekte olan değil, sahip olduğunuzdan emin olun.

- Kaldır/devre dışı bırak üçüncü taraf sürücüler veya yazılımlar ile sanal ağ iletişimi engelliyor olabilir.

   Ağ sürücüleri/Hyper-V ağ yığınını ile tam olarak uyumlu olmayan protokolleri gibi Windows 8'altında yüklü 3 bazı taraf ürünler ile ilgili bazı bilinen sorunlar vardır.

   Genel olarak, geliştiricilerin bu ürün Windows 8 ve Hyper-V ile uyumlu olacak şekilde, yazılım güncelleştirme kadar olacaktır.

   Aşağıdaki ürünler için Windows 8 Uyumluluk yükseltme gerektirebilir: VirtualBox, sanal bilgisayar 7, VMWare, bazı VPN istemcileri yazılım güvenlik duvarları, Cisco VPN istemcileri ve diğer sanallaştırma sistemlerinin bazı sürümlerinde. Windows 8 ve Hyper-V ile uyumlu hale getirmek için yazılım yükseltmelerini teşvik etmek için sorgulanabilir sanallaştırma yazılımı geliştiricisi çalışın.

   Olarak bir **geçici çözüm**, tüm üçüncü taraf sürücüler ve Visual Studio ile iletişim kurmak için öykünücüsü tarafından kullanılan sanal ağ ile engelliyor uygulamalar devre dışı bırakabilirsiniz. Bu uygulamalar şunları içerebilir:

  - (Ağ yığınına kanca) virüsten koruma uygulamaları

  - Ağ izleme araçları

  - Ağ günlük araçları

  - Diğer sistem izleme yazılımı

    Heyecan verici ürünlerle ilgilenmeleri kaldırma kısıtlıysa, başka bir olası çözüm soru (ve güncelleştirilmiş bir sürümünü yayımlamayı ürün Geliştirici isteyen), aşağıdaki adımları sağlamaktır.

  1. Ağ bağlantıları Yöneticisi'ni başlatın (başlangıç ekranından yazın `View Network Connections` ve ağ bağlantılarını görüntülemek için bu seçeneği belirleyin.)

  2. VEthernet (dahili Ethernet bağlantı noktası Windows Phone öykünücüsü iç anahtar) bağdaştırıcısı için seçim yapın **özellikleri** bağlam menüsünden.

      ![Sanal bağdaştırıcı Hyper tarafından kullanılan&#45;V](../cross-platform/media/android-emu-virtual-adapter.png "Android_Emu_Virtual_Adapter")

      Bağdaştırıcı özellikleri burada gösterilir.

      ![Sanal bağdaştırıcı özellikleri](../cross-platform/media/android-emu-virtual-adapter-properties.png "Android_Emu_Virtual_Adapter_Properties")

  3. Bu bağdaştırıcı, altında seçilmelidir yalnızca öğeler için **Bu bağlantı aşağıdaki öğeleri kullanır** aşağıdaki gibi olmalıdır:

     -   Microsoft Ağları için istemci

     -   QoS Paket Zamanlayıcısı

     -   Dosya ve yazıcı paylaşımı Microsoft Ağları için

     -   Microsoft LLDP protokol sürücüsüne

     -   Bağlantı-katman Topoloji Bulma Eşleyicisi g/ç sürücüsü

     -   Bağlantı-katman Topoloji Bulma Yanıtlayıcı

     -   Internet Protokolü sürüm 6 (TCP/IPv6)

     -   Internet Protokolü sürüm 4 (TCP/IPv4)

  4. Diğer öğeleri kaldırın.

     İçin bu teknik kullanılarak dezavantajı, dilediğiniz zaman yeni bir 3. taraf ürün desteklenmeyen sürücüleri yükler veya öykünücü yüklendikten, dilediğiniz zaman bu adımları yinelenmesi gerekir ' dir.

     Üçüncü taraf ürünleri kaldırıldıktan sonra Windows Phone öykünücüsü iç anahtar geri yüklemek gerekebilir. Bunu yapmak için:

  - Hyper V açın ve sanal Anahtar Yöneticisi'ne gidin. "Windows Phone öykünücüsü iç geçiş" adlı bir sanal anahtar oluşturma ve bağlantı türünü ayarlamak **iç ağ**.

     ![Sanal Anahtar Yöneticisi](../cross-platform/media/android-emu-virtual-switch-manager.png "Android_Emu_Virtual_Switch_Manager")

    Artık öykünücüyü başlatın. Çalışmalıdır.

##  <a name="NoBoot"></a> Öykünücü yüklendikten sonra önyükleme bilgisayar başarısız
 Aşağıdaki koşullar doğru olduğunda bu sorun oluşabilir:

- Bilgisayarınızda bir gigabayt anakart vardır.

- USB3 anakart üzerinde etkindir.

  Bu sorunu çözmek için USB3 anakart BIOS ayarları devre dışı bırakın ve bilgisayarı yeniden başlatın. Daha sonra gigabayt, anakart ait BIOS için bir güncelleştirme yayımladı olup olmadığını denetleyin.

  Daha fazla bilgi için aşağıdaki Bilgi Bankası makalesine bakın: [önyükleme hatası sonra gigabayt sistemlerinde Hyper-V rolünün yüklenmesi](https://support.microsoft.com/en-us/kb/2693144).

##  <a name="ADB"></a> Visual Studio öykünücüsü için uygulama dağıtılmaya çalışılırken takılı veya öykünücü diğer IDE içinde hata ayıklama hedefi olarak görünmüyor
 Öykünücünün çalıştığından, ancak ADB (Android hata ayıklama köprüsü) bağlanması görünmez ya da (örneğin, Android Studio veya Eclipse) ADB kullanan Android araçları görünmüyor öykünücü için ADB nerede arar ayarlamak gerekebilir. Öykünücü, Android SDK'nızı temel konumunu tanımlamak için bir kayıt defteri anahtarını kullanır ve bu dizin altında \platform-tools\adb.exe dosyasını arar. Öykünücüsü tarafından kullanılan Android SDK yolu değiştirmek için:

- Kayıt Defteri Düzenleyicisi'ni seçerek açın **çalıştırma** başlangıç düğmeleri bağlam menüsünden yazarak `regedit` iletişim kutusunda seçip **Tamam**.

- Sol taraftaki klasör ağacında HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Android SDK Tools için gidin.

- Değiştirme **yolu** Android SDK'nızı yolunu eşleştirmek için kayıt defteri değişkeni.

  Öykünücü yeniden başlatın ve artık öykünücü ADB bağlı ve Android araçları ilişkili görüyor olmanız gerekir.

##  <a name="XamarinPlayer"></a> UDP bağlantı noktası ' ayarlanamadı çünkü öykünücü yanıt vermemeye başlıyor
 Xamarin Player ile uyumsuzluğu nedeniyle bu sorunla karşılaşabilirsiniz. Öykünücü askıda görünüyorsa ya da bu hata iletisini görürseniz, "öykünücü cihazın işletim sisteminde bağlanamıyor: UDP bağlantı noktası ' ayarlanamadı.  Bazı işlevler devre dışı bırakılabilir", bu sorunu yaşıyor olabilirsiniz. Aşağıdaki adımları uygulayın.

1.  Xamarin Player kaldırın.

2.  Kaldırılan (Xamarin Player çalıştırması sanal kutusunun üstünde) olan sanal kutunun doğrulayın.

3.  Cihaz Yöneticisi'ne gidin, gizli aygıtları göster seçeneğini belirleyin ve ardından fiziksel ağ kartları dışında her şeyi silin.

4.  Kaldırma/Hyper-V olmayan fiziksel ağ bağdaştırıcısı kaldırdıktan sonra yeniden yüklemeyi deneyebilirsiniz.

##  <a name="Skylake"></a> Bir Xamarin projesi için hata ayıklayıcı eklenemiyor
 Intel Skylake işlemcilere sahip Windows 10 çalıştırıyorsanız, Xamarin uygulamaları öykünücüde çalıştırma başarısız olabilir veya Visual Studio için hata ayıklayıcının değil. Hyper-V ve Skylake işlemciler ile ilgili bir sorun nedeniyle budur. Geçici bir çözüm olarak aşağıdaki adımları uygulayın.

1.  Hyper-V Yöneticisi'ni açın ve öykünücü profil için VM'yi seçin olduğunuz kullanarak.

2.  Seçin **silme kaydedilmiş durum** (sağ alt köşede).

3.  Seçin **ayarları...**

4.  İşlemci düğümünü genişletin ve seçin **Uyumluluk**.

5.  Etkinleştirme **farklı bir işlemci sürümü olan fiziksel bir bilgisayara geçirme**.

6.  Hizmeti yeniden başlatın (altında **eylemleri**) ve yeniden deneyin.

##  <a name="GooglePlay"></a> Google Play hizmetleri kullanan bir uygulamayı çalıştırmak öykünücü başarısız
 Öykünücü, Google Play Hizmetleri'ni kitaplıklarıyla gelmez. Ancak öykünücü sürükle ve bırak açılıp dosyaların yüklenmesini destekler.

##  <a name="DragAndDrop"></a> Sürükle ve bırak bir dosya, APK veya açılıp dosyasının çalışmıyor
 Öykünücü ADB.exe ekrana bir dosya sürükleyip zaman dosya aktarımı kolaylaştırmak için kullanır. Bir dosya sürükleyip denediğinizde bir hatayla karşılaşırsanız, bu büyük olasılıkla öykünücü ADB.exe için bağlı olmadığını gösterir. Gidermek için adımları izleyin. [Visual Studio öykünücüsü için uygulama dağıtılmaya çalışılırken takılı veya öykünücü diğer IDE içinde hata ayıklama hedefi olarak görünmüyor](#ADB).

##  <a name="Resolution"></a> Ekran çözünürlüğü yanlış
 Ekran sekmesindeki kullanarak bir ekran görüntüsünü almak, **ek araçlar** penceresi ve elde edilen görüntü beklenmeyen bir boyuta, ekranı yakınlaştırma düzeyi seçmeden önce ayarlamanız gerekebilir **Yakalama**. Öykünücü ekran görüntüleri, ana bilgisayar İzleyicisi ekranın çözünürlükte alır.

##  <a name="OpenGL"></a> OpenGL içeriğini işlemek öykünücü başarısız
 Öykünücü, konak makinenin GPU kullanan OpenGL içeriği işler ve DirectX gelen ve bu çağrıları dönüştürülecek AÇI proje kullanır. Bir cihazda, ancak yanlış öykünücü uygulamanızın doğru şekilde işlediğinden, cihaz yanlış bir OpenGL çağrı (örneğin, eşleşmeyen gölgelendirici değişkenleri kullanarak) için Azaltıcı olasıdır.

##  <a name="Multitouch"></a> Öykünücü, çok noktalı dokunma hareketlerini için yanıt vermiyor
 Bazı durumlarda, öykünücüyü başlatın ve çok noktalı dokunma için ya da ile doğrudan etkileşim-dokunmatik ekran veya öykünücü araç çubuğunda çok noktalı dokunma aracını kullanarak yanıt değil. Bu durumda, seçin **Döndür** düğmesini öykünücü araç ve çok noktalı dokunma tekrar kullanılmaya çalışıldı. Sorun devam ederse, okuma [öykünücü başarısız OpenGL içeriğini işlemek](#OpenGL) sorun.

##  <a name="Support"></a> Destek kaynakları
 Ana bilgisayarınızın sistem gereksinimlerini karşıladığından ve bu sorun giderme Kılavuzu'nda ele alınmayan bir sorunla karşılaşırsanız varsa:

-   StackOverflow kullanma hakkında bir soru sorun [android öykünücüsü](http://stackoverflow.com/questions/tagged/android-emulator) ve visual studio etiketler.

-   Visual Studio'da veya öykünücü Yöneticisi'nde gönderme gülümseme aracını kullanarak bir sorun bildirin.
