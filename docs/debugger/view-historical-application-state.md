---
title: IntelliTrace kullanarak görünüm önceki uygulama durumu
description: Anlık görüntülerini alabilir ve anlık görüntülerle IntelliTrace geri adım görüntüleme hakkında bilgi edinin
ms.custom: seodec18
ms.date: 09/19/2018
ms.technology: vs-ide-debug
ms.topic: tutorial
ms.assetid: 7c60d929-d993-49dc-9db3-43b30be9912b
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ba1ab23fead36cfabc8b2754535e8b10de981987
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53060151"
---
# <a name="inspect-previous-app-states-using-intellitrace-step-back-in-visual-studio"></a>Visual Studio'da IntelliTrace geri adım atmayı kullanarak önceki uygulama durumlarını İnceleme

IntelliTrace geri adım, otomatik olarak adım olay, her bir kesme noktası ve hata ayıklayıcı uygulamanızın anlık görüntüsünü alır. Kaydedilen anlık görüntü, önceki kesme noktaları veya adımlara geri dönün ve daha önce olduğu gibi uygulama durumunu görüntülemek etkinleştirin. IntelliTrace geri adım atma önceki uygulama durumu görmek istiyorsanız ancak hata ayıklamayı yeniden başlatın veya istenen uygulama durumu yeniden istemediğiniz durumlarda size zaman kazandırabilir.

Visual Studio Enterprise 2017 sürüm 15.5 ve daha yüksek başlangıç IntelliTrace geri adım bulunur ve Windows 10 Yıldönümü güncelleştirmesi gerektirir veya üzeri. Bu özellik şu anda ASP.NET, WinForms, WPF, yönetilen konsol uygulamaları ve yönetilen sınıf kitaplıklarında hata ayıklama için desteklenir. Visual Studio 2017 Enterprise sürüm 15.7 başlayarak, ASP.NET Core ve .NET Core için de özellik desteklenir. Visual Studio 2017 Enterprise sürümü 15.9 başlangıç Önizleme 2, bu özellik Windows hedefleyen yerel uygulamalar için desteklenir. UWP uygulamalarında hata ayıklama şu anda desteklenmiyor.

Bu öğreticide şunları yapacaksınız:

> [!div class="checklist"]
> * IntelliTrace olayları ve anlık görüntüleri etkinleştir
> * Geri adım atma ve adım ileri komutlarını kullanarak olayları gidin
> * Olay anlık görüntüleri Göster
  
## <a name="enable-intellitrace-events-and-snapshots-mode"></a>IntelliTrace olayları ve anlık görüntüleri modunu etkinleştir 

1. Visual Studio Enterprise'da projenizi açın.

1. Açık **Araçları** > **seçenekleri** > **IntelliTrace** Ayarları ' nı seçip seçeneği **IntelliTrace olayları ve anlık görüntüleri** . 

    Visual Studio 2017 Enterprise sürümü 15.9 başlangıcıdır Önizleme 2, bu seçenek **IntelliTrace anlık görüntülerini (yönetilen ve yerel)**. 

    ![IntelliTrace olayları ve anlık görüntüler modu etkinleştirme](../debugger/media/intellitrace-enable-snapshots.png "etkinleştirme IntelliTrace olayları ve anlık görüntüler modu")

1. Özel durumları görüntüleme anlık görüntüler için seçenekleri yapılandırmak istiyorsanız, seçin **IntelliTrace** > **Gelişmiş** gelen **seçenekleri** iletişim kutusu.

    Bu seçenekler, Visual Studio 2017 Enterprise sürüm 15.7 başlangıç kullanılabilir.

    ![Özel durumlarda anlık görüntüler için davranışı yapılandırma](../debugger/media/intellitrace-enable-snapshots-on-exceptions.png)

    Ayrıca, olayları ve anlık görüntüleri etkinleştirdiğinizde, özel durumlarda anlık görüntülerini almadan varsayılan olarak etkindir. Kaldırarak özel durumlarda anlık görüntüler devre dışı bırakabilirsiniz **özel durum olaylarında anlık görüntüleri toplamak**. Bu özellik etkinleştirildiğinde, İşlenmeyen özel durumlar için anlık görüntü alınır. İşlenen özel durumlar için anlık görüntüler yalnızca özel durum oluşturulursa ve daha önce oluşturulan özel durumu yeniden harekete değilse alınır. Aşağı açılan listeden bir değer seçerek, Maksimum sayıda anlık görüntü üzerinde özel durumlar ayarlayabilirsiniz. Uygulamanız (örneğin, uygulamanız bir kesme noktasına denk gelir) Kesme moduna girdiğinde her zaman için üst sınırı uygulanır.

    > [!NOTE]
    > Anlık görüntüler yalnızca özel durum olayları için IntelliTrace kayıt alınır. Yönetilen kod için hangi Intellitrace'in kaydettiği olayları seçerek belirtebilirsiniz **Araçları** > **seçenekleri** > **IntelliTrace olayları**.

1. Projenizde, bir veya daha fazla kesme noktaları ayarlayın ve hata ayıklamayı Başlat (basın **F5**), veya, kod içerisinde ilerlemeye tarafından hata ayıklamayı Başlat (**F10** veya **F11**).

    IntelliTrace, uygulamanın işlemi her bir hata ayıklayıcı adım, kesme olayının ve işlenmeyen özel durum olayı anlık görüntüsünü alır. Bu olaylar kaydedilir **olayları** sekmesinde **tanılama araçları** diğer IntelliTrace olayları ile birlikte bir pencere. Bu pencereyi açmak için seçin **hata ayıklama** > **Windows** > **tanılama araçlarını Göster**.

    Kamera simgesini anlık görüntüleri kullanılabilir olaylar yanında görünür. 

    ![Olayları anlık görüntüleri ile sekmesindeki](../debugger/media/intellitrace-events-tab-with-snapshots.png "kesme noktaları ve adımları anlık görüntülerle olaylar sekmesi")

    Performansla ilgili nedenlerden dolayı anlık görüntülerinin alınma hızlıca dolaştığınızda değil. Herhangi bir kamera simge adımın yanında görünüyorsa, daha yavaş Adımlama deneyin.

## <a name="navigate-and-view-snapshots"></a>Gidin ve anlık görüntüleri görüntüleme

1. Kullanarak olaylar arasında gezinmek **geri adım (Alt + [)** ve **İleri (Alt +])** hata ayıklama araç çubuğu düğmeleri.

    Bu düğmeler görünen olaylar gidin **olayları** sekmesinde **tanılama araçları penceresi**. Geriye veya ileriye doğru bir olay için otomatik olarak Adımlama etkinleştirir [geçmiş hata ayıklama](../debugger/historical-debugging.md) seçilen olayla ilgili.

    ![Geri adım ve İleri düğmelerini](../debugger/media/intellitrace-step-back-icons-description.png "adım geri ve İleri düğmeleri")

    Adım geri veya İleri adım atın, Visual Studio Geçmiş hata ayıklama moduna girer. Bu modda, hata ayıklayıcı'nın içeriği ne zaman seçili olayın kaydedildiği zamana geçer. Visual Studio işaretçiyi kaynak penceresinde kod ilgili satırını da taşır. 

    Bu görünümde, değerler inceleyebilirsiniz **çağrı yığını**, **Yereller**, **Otolar**, ve **Watch** windows. Ayrıca değişkenleri veri ipuçlarını görüntülemek ve ifade değerlendirmesinde gerçekleştirmek için üzerine gelerek **hemen** penceresi. Gördüğünüz geçen süre içinde bu noktada uygulamanın işlemi anlık görüntüden verilerdir.

    Böylece, örneğin, bir kesme noktası isabet ve bir adım geçen (**F10**), **adım geriye dönük** düğmesi, kesme noktasına karşılık gelen kod satırının geçmiş modda Visual Studio koyar. 

    ![Anlık görüntü ile bir olay geçmiş modu etkinleştirme](../debugger/media/intellitrace-historical-mode-with-snapshot.png "bir anlık görüntü ile bir olay geçmiş modunu etkinleştirme")

2. Canlı yürütme için döndürülecek seçin **devam et (F5)** veya **Canlı hata ayıklamaya dönün** Bilgi Çubuğu'nda bağlantı. 

3. Ayrıca, bir anlık görüntüden görüntüleyebilirsiniz **olayları** sekmesi. Bunu yapmak için bir anlık görüntü ile bir olay seçin ve **etkinleştirmek geçmiş hata ayıklama**.

    ![Geçmiş hata ayıklamayı etkinleştir olaya](../debugger/media/intellitrace-activate-historical-debugging.png "etkinleştirmek geçmiş hata ayıklama olay")

    Farklı **sonraki deyimi Ayarla** görüntüleme bir anlık görüntü komutu, kodunuzu yeniden değil; Bu, statik bir görünüm durumu uygulamanın bir noktada geçmişte gerçekleşen zaman sağlar.

    ![IntelliTrace geri adım bakış](../debugger/media/intellitrace-step-back-overview.png "genel bakış, IntelliTrace geri adım atma")

    Visual Studio'da değişkenleri İnceleme hakkında daha fazla bilgi için bkz: [hata ayıklayıcısı özellik turu](../debugger/debugger-feature-tour.md)  

## <a name="frequently-asked-questions"></a>Sıkça Sorulan Sorular

#### <a name="how-is-intellitrace-step-back-different-from-intellitrace-events-only-mode"></a>IntelliTrace geri adım IntelliTrace olayları yalnızca modundan farklı mı?

Olayları yalnızca modunda IntelliTrace geçmiş hata ayıklama adımlarında ve kesme noktaları hata ayıklamayı etkinleştir izin vermez. Ancak, IntelliTrace verileri yalnızca yakalar **Yereller** ve **Otolar** windows açık olan ve yalnızca genişletilmiş verileri yakalar, windows ve görüntüleme. Olayları yalnızca modunda genellikle karmaşık nesneler ve değişkenler eksiksiz bir görünümünü erişiminiz yok. Ayrıca, ifade değerlendirme ve izleme verilerini **Watch** penceresi desteklenmiyor. 

Modunda, olayları ve anlık görüntüleri, IntelliTrace uygulamanın işlemi, karmaşık nesneler de dahil olmak üzere tüm anlık görüntüsünü yakalar. Bir kod satırına bir kesme noktasında durdurulan (ve bu bilgileri daha önce genişletilen olup olmaması önemli değil varsa gibi) aynı bilgileri görebilirsiniz. İfade değerlendirme, bir anlık görüntü görüntülerken da desteklenir.  

#### <a name="what-is-the-performance-impact-of-this-feature"></a>Bu özelliğin performans etkisi nedir? 

Genel Adımlama performansı üzerindeki etkisini, uygulamaya bağlıdır. Bir anlık görüntü alma yükü, yaklaşık 30 ms olur. Bir anlık görüntü alınırken, uygulamanın işlem çatallanmış ve çatalı oluşturulan kopya askıya alındı. Visual Studio, bir anlık görüntü görüntülediğinizde, işlem çatalı kopyasına iliştiriyor. Visual Studio, her anlık görüntü için yalnızca sayfa tablosu kopyalar ve sayfalarını kopyalama yazarken için ayarlar. Yığındaki nesneleri ile ilişkili anlık görüntü hata ayıklayıcısı adımlar arasında değiştirirseniz, ilgili sayfa tablosu sonra en az bellek maliyet kaynaklanan kopyalanır. Visual Studio anlık görüntüsünü almak için yeterli bellek yok algılarsa bir almaz.
 
## <a name="known-issues"></a>Bilinen Sorunlar  
* Windows 10 Fall Creators Update (RS3) eski Windows sürümlerinde IntelliTrace olayları ve anlık görüntüler modu kullanıyorsanız ve uygulamayı hata ayıklama platformu hedefi için x86 ayarlanırsa IntelliTrace anlık görüntüler almaz.

    Geçici çözümler:
  * Windows 10 Yıldönümü Güncelleştirmesi (RS1) ve 10.0.14393.2273, önceki bir sürümü kullanıyorsanız [KB4103720 yükleme](https://support.microsoft.com/help/4103720/windows-10-update-kb4103720). 
  * Windows 10 Creators Update (RS2) ve 10.0.15063.1112, önceki bir sürümü kullanıyorsanız [KB4103722 yükleme](https://support.microsoft.com/help/4103722/windows-10-update-4103722).
  * Yükleme veya Windows 10 Fall Creators Update (RS3) yükseltin. 
  * Alternatif olarak: 
    1. Visual Studio yükleyicisinden masaüstü için VC++ 2015.3 v140 araç seti (x86, x64) bileşenini yükleyin.
    2. Hedef uygulamayı derleyin.
    3. Komut satırından, editbin aracını ayarlamak için kullanın. `Largeaddressaware` hedef yürütülebilir için bayrak. Örneğin, (yol güncelleştirdikten sonra) Bu komutu kullanabilirsiniz: "C:\Program Files (x86) \Microsoft Visual Studio\Preview\Enterprise\VC\Tools\MSVC\14.12.25718\bin\Hostx86\x86\editbin.exe" / largeaddressaware "C:\Path\To\Application\app.exe".
    4. Hata ayıklamayı başlatmak için basın **F5**. Artık, hata ayıklama adımlarında ve kesme noktalarında anlık görüntü alınır.

       > [!Note]
       > `Largeaddressaware` Yürütülebilirin değişikliklerle yeniden derlendiği her zaman bayrağı ayarlanmalıdır.

* Uygulamanın işlem anlık görüntüsünü kullanan bir kalıcı bellek işlemeli dosya bir uygulama alındığında anlık görüntü ile işlem (hatta üst işleme kilidin piyasaya sonra) özel bir kilit üzerinde bellekle eşlenen dosya tutar. Diğer işlemlerin okunan ancak, bellekle eşlenen dosyasına yazmayacak koruyabilmeyi.

    Geçici çözüm:
    * Tüm anlık görüntüleri, hata ayıklama oturumunu sona erdirme tarafından temizleyin. 

* Çok sayıda DLL'leri yükleyen bir uygulama gibi benzersiz bellek bölümlerinin yüksek sayıda olan işlem sahip bir uygulamada hata ayıklaması yaparken, performans etkin anlık görüntülerle Adımlama etkilenebilir. Bu sorun gelecekteki bir Windows sürümünde ele alınacaktır. Bu sorunu yaşıyorsanız adresinden bize ulaşın stepback@microsoft.com. 

* Bir dosyayı kaydederken **hata ayıklama > IntelliTrace > Kaydet IntelliTrace oturumu** modunda, olayları ve anlık görüntüler, anlık görüntülerden yakalanan ek verilerini .itrace dosyasına kullanılamıyor. Kesme noktası ve adım olaylarında IntelliTrace olaylarını yalnızca modunda dosyayı kaydettiğiniz gibi aynı bilgileri görürsünüz. 

## <a name="next-steps"></a>Sonraki adımlar

Bu öğreticide, IntelliTrace geri adım kullanmayı öğrendiniz. Diğer IntelliTrace özellikleri hakkında daha fazla bilgi edinmek isteyebilirsiniz.

> [!div class="nextstepaction"]
> [IntelliTrace özellikleri](../debugger/intellitrace-features.md)
