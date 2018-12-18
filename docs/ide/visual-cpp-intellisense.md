---
title: C++ IntelliSense
ms.date: 10/08/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
author: mikeblome
ms.author: mblome
manager: wpickett
ms.workload:
- cplusplus
ms.openlocfilehash: ab520f7cdf512ebbfd07770d63d2ed50caee7a55
ms.sourcegitcommit: 71218ffc33da325cc1b886f69ff2ca50d44f5f33
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/09/2018
ms.locfileid: "48879856"
---
# <a name="visual-c-intellisense-features"></a>Visual C++ IntelliSense özellikleri

IntelliSense, bir dizi özellikler, kodlamayı daha kullanışlı hale getirmek için verilen bir addır. C++ IntelliSense de tek başına dosyalar için C++ projesinin bir parçası olan dosyalar için kullanılabilir. Platformlar arası projelerinde bazı IntelliSense özellikleri kullanılabilir *.cpp* ve *.c* bir Android veya iOS bağlamında olsa bile paylaşılan kod projesinde dosyaları.

Bu makalede, Özellikler C++ IntelliSense genel bir bakış sağlar. Projeniz için IntelliSense ve sorunlarını gidermek nasıl nasıl yapılandırılacağı hakkında daha fazla bilgi için bkz: [bir C++ projesini yapılandırmak için IntelliSense](visual-cpp-intellisense-configuration.md).

## <a name="intellisense-features-in-c"></a>C++ IntelliSense özellikleri

IntelliSense, bir dizi özellikler, kodlamayı daha kullanışlı hale getirmek için verilen bir addır. Farklı kişilerin ne kullanışlı olduğu hakkında farklı fikirlerinizi görünmesi, neredeyse tüm IntelliSense özelliklerini etkinleştirilebilir veya devre dışı bırakılmış **seçenekleri** iletişim kutusunun **metin düzenleyici**  >  **C/C++** > **Gelişmiş**. **Seçenekleri** iletişim kutusu kullanılabilir **Araçları** menü çubuğundaki menü.

![Araç Seçenekleri iletişim kutusu](../ide/media/sintellisensecpptoolsoptions.PNG)

IntelliSense erişmek için menü öğeleri ve aşağıdaki görüntüde gösterilen klavye kısayollarını kullanabilirsiniz.

![IntelliSense menüsü](../ide/media/vs2015_cpp_intellisense_menu.png)

## <a name="statement-completion-and-member-list"></a>Deyim tamamlama ve üye listesi

Bir anahtar sözcüğü, türü, işlev, değişken adı veya derleyici tanıdığı başka bir program öğesi yazmaya başladığınızda, word tamamlanması Düzenleyicisi sunar.

Simgelerini ve anlamlarını listesi için bkz. [sınıf görünümü ve Nesne Tarayıcısı simgeleri](../ide/class-view-and-object-browser-icons.md).

![Visual C&#43; &#43; tam sözcük penceresi](../ide/media/vs2015_cpp_complete_word.png)

Üye listesi, çağırma ilk kez, yalnızca geçerli bağlam için erişilebilir olan üyeleri gösterir. Basarsanız **Ctrl**+**J** bundan sonra erişilebilirlik bağımsız olarak tüm üyeleri gösterir. Üçüncü kez çağırmak, program öğelerini çok daha geniş bir listesi gösterilir. Üye listesinde kapatabilirsiniz **seçenekleri** iletişim kutusunun **metin düzenleyici** > **C/C++** > **genel**  >  **Otomatik üyeleri Listele**.

![Visual C&#43; &#43; üye listesi](../ide/media/vs2015_cpp_list_members.png)

## <a name="parameter-help"></a>Parametre Yardımı

Bir sınıf şablonu değişken bildirimi bir açılış ayracı bir işlev çağrısı veya açılı ayraç yazdığınızda Düzenleyici küçük bir pencere için her bir işlevde veya Oluşturucu yüklemesini parametre türleri ile gösterir. "Geçerli" parametresi&mdash;İmleç konumuna göre&mdash;yazısı kalın. Parametre bilgileri kapatabilirsiniz **seçenekleri** iletişim kutusunun **metin düzenleyici** > **C/C++** > **genel**  >  **Parametre bilgileri**.

![Visual C&#43; &#43; parametre Yardımı](../ide/media/vs_2015_cpp_param_help.png)

## <a name="quick-info"></a>Hızlı Bilgi

Fare imlecini bir değişkenin geldiğinizde, küçük bir pencere tür bilgilerini gösteren bir satır içi ve türünün tanımlandığı üstbilgi görünür. İşlev imzası görmek için işlev çağrısı gelin. İçinde hızlı Bilgi'yi kapatabilirsiniz **seçenekleri** iletişim kutusunun **metin düzenleyici** > **C/C++** > **Gelişmiş**  >  **Otomatik hızlı bilgi**.

![Visual C&#43; &#43; Hızlıbilgi](../ide/media/vs2015_cpp_quickinfo.png)

## <a name="error-squiggles"></a>Hata ilişkilendirmelerini

Dalgalı çizgiler (değişken, anahtar sözcüğü, küme ayracı, tür adı vb.) bir program öğesinin altındaki kodda bir hata veya olası hata dikkat etmeniz çağırın. Yine de uygulama yazmak gerektiğini hatırlatan bir ileri dönük bildirimi yazdığınızda bir yeşil dalgalı çizgi görünür. Olduğunda bir mor dalgalı bir paylaşılan projede bir Android bağlamındaki hata olacaktır Windows bağlamda çalışıyoruz, ancak bir şey girin, örneğin şu anda etkin değil, kodda bir hata görüntülenir. Derleyici hatası veya uyarısı uğraşmanız gereken etkin kod kırmızı dalgalı gösterir.

![Visual C&#43; &#43; hata ilişkilendirmelerini](../ide/media/vs2015_cpp_error_quiggles.png)

### <a name="code-colorization-and-fonts"></a>Kod renklendirme ve yazı tipleri

Varsayılan renkleri ve yazı tipleri içinde değiştirilebilen **seçenekleri** iletişim kutusunun **ortam** > **yazı tipleri ve renkler**. Çok sayıda UI windows burada yalnızca Düzenleyici yazı tiplerini değiştirebilirsiniz. "C++ ile"; C++ için belirli ayarların başlayın diğer ayarlar, tüm diller için gösterir.

## <a name="cross-platform-intellisense"></a>Platformlar arası IntelliSense

Hatta Android bir bağlamda çalışırken bir paylaşılan kod projesinde dalgalı çizgiler gibi bazı IntelliSense özellikleri kullanılabilir. Etkin olmayan bir projede hata ortaya çıkabilecek bazı kodlar yazma, IntelliSense ilişkilendirmelerini görüntülenmeye devam eder, ancak farklı bir renkte dalgalı çizgiler hataları geçerli bağlamda yer.

Android ve iOS için oluşturulacak şekilde yapılandırılmış bir OpenGLES uygulaması göz önünde bulundurun. Çizimde düzenlenmekte olan paylaşılan kod gösterilmektedir. Bu görüntü, projesinin etkin olduğundan **iOS.StaticLibrary**:

![iOS, etkin bir proje seçilir.](../ide/media/intellisensecppcrossplatform2.png)

Aşağıdakilere dikkat edin:

- `#ifdef` Dal 6. satırda gri bir etkin olmayan bölge göstermek için çünkü `__ANDROID__` iOS projesi için tanımlı değil.

- 11. satırında Karşılama değişken tanımlayıcısıyla başlatılır `HELLO`, şimdi bir kırmızı dalgalı çizgi vardır. Bunun nedeni, hiçbir tanımlayıcısı `HELLO` etkin bir iOS projesi içinde tanımlanır.

- 12 satır tanımlayıcısı mor dalgalı sahip `BYE` bu tanımlayıcı (şu anda) etkin değil tanımlı olmaması nedeniyle **Android.NativeActivity** proje. İOS projesinin etkin olduğunda, bu satırı derler olsa da, Android projesinin etkin olduğunda derlenemeyecektir. Bu paylaşılan kod olduğundan, şu anda etkin yapılandırmada derler olsa bile, kodu düzeltmeniz gerekir.

Android için etkin proje değiştirirseniz dalgalı çizgiler değiştirin:

- `#else` 8. satır bir daldaki gri bir etkin olmayan bölge göstermek için çünkü `__ANDROID__` Android projesi için tanımlanmış.

- 11. satırında Karşılama değişken tanımlayıcısına sahip başlatılır `HELLO`, mor dalgalı sahiptir. Bunun nedeni, hiçbir tanımlayıcısı `HELLO` şu anda etkin olmayan iOS projesinde tanımlanır.

- Çizgi 12 bulunan kırmızı dalgalı tanımlayıcının `BYE` bu tanımlayıcıyı etkin projedeki tanımlanmadığından.

## <a name="intellisense-for-stand-alone-files"></a>Tek başına dosyalar için IntelliSense

Tek bir dosyayı dışında herhangi bir projeyi açtığınızda, IntelliSense almaya devam. Etkinleştirebilir veya belirli IntelliSense özelliklerini devre dışı **seçenekleri** iletişim kutusunun **metin düzenleyici** > **C/C++**  >  **Gelişmiş**. Bir projenin parçası olmayan tek dosyalar için IntelliSense yapılandırmak için Ara **IntelliSense ve gözatma proje dışı dosyalar için** bölümü.

![Visual C&#43; &#43; tek dosya IntelliSense](../ide/media/vs2015_cpp_single_file_intellisense.png)

Varsayılan olarak, tek dosyalı IntelliSense yalnızca kullanımlar standart üst bilgi dosyaları bulmak için dizinler. Ek dizinleri eklemek için kısayol menüsünü açın **çözüm** düğümünü ve dizininize eklemek **kaynak kodu hata ayıklama** listesinde, aşağıdaki çizimde gösterildiği gibi:

![Bir yol için bir üstbilgi dosyası ekleniyor.](../ide/media/intellisensedebugyourcode.jpg)

## <a name="enable-or-disable-features"></a>Etkinleştirmek veya özellikleri devre dışı bırak

Farklı kişilerin ne kullanışlı olduğu hakkında farklı fikirlerinizi görünmesi, neredeyse tüm IntelliSense özelliklerini etkinleştirilebilir veya devre dışı bırakılmış **seçenekleri** iletişim kutusunun **metin düzenleyici**  >  **C/C++** > **Gelişmiş**. **Seçenekleri** iletişim kutusu kullanılabilir **Araçları** menü çubuğundaki menü.

![Araç Seçenekleri iletişim kutusu](../ide/media/sintellisensecpptoolsoptions.PNG)

## <a name="see-also"></a>Ayrıca bkz.

- [IntelliSense Kullanma](../ide/using-intellisense.md)
- [IntelliSense için bir C++ projesi yapılandırma](visual-cpp-intellisense-configuration.md)
