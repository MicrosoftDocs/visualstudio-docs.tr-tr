---
title: Visual C++ IntelliSense | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9d7c6414-4e6c-4889-a74c-a6033795eccc
caps.latest.revision: 11
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: ced999c20678cc64dc5f96e86070b5f39d5ca2c7
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49881683"
---
# <a name="visual-c-intellisense"></a>Visual C++ IntelliSense
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio 2015'te IntelliSense de tek bir kod dosyaları için proje dosyalarında olduğu gibi kullanılabilir. Bir Android veya iOS bağlamında olsa bile platformlar arası projelerinde bazı IntelliSense özellikleri, .cpp ve .c dosyaları paylaşılan kod projesinde kullanılabilir.  
  
## <a name="intellisense-features-in-c"></a>C++ IntelliSense özellikleri  
 IntelliSense, bir dizi özellikler, kodlamayı daha kullanışlı hale getirmek için verilen bir addır. Farklı kişilerin ne kullanışlı olduğu hakkında farklı fikirlerinizi görünmesi, neredeyse tüm IntelliSense özelliklerini etkinleştirilebilir veya devre dışı bırakılmış **metin düzenleyici, C/C++, Gelişmiş** özellik sayfası.  
  
 ![Araçlar, Seçenekler, metin düzenleyici, C&#47;C&#43;&#43;, Gelişmiş](../ide/media/sintellisensecpptoolsoptions.PNG "sIntelliSenseCppToolsOptions")  
  
 IntelliSense erişmek için menü öğeleri ve aşağıdaki görüntüde gösterilen klavye kısayollarını kullanabilirsiniz.  
  
 ![Visual C&#43; &#43; IntelliSense menü](../ide/media/vs2015-cpp-intellisense-menu.png "vs2015_cpp_intellisense_menu")  
  
### <a name="statement-completion-and-member-list"></a>Deyim tamamlama ve üye listesi  
 Word tamamlamanız bir anahtar sözcüğü, türü, işlev, değişken adı veya derleyici tanıdığı başka bir program öğesi yazmaya başladığınızda, düzenleyici sunar  
  
 Simgelerini ve anlamlarını listesi için bkz. [sınıf görünümü ve Nesne Tarayıcısı simgeleri](../ide/class-view-and-object-browser-icons.md).  
  
 ![Visual C&#43; &#43; tam sözcük penceresi](../ide/media/vs2015-cpp-complete-word.png "vs2015_cpp_complete_word")  
  
 Üye listesi çağrılan ilk kez, yalnızca geçerli bağlam için erişilebilir olan üyeleri gösterir. Kullanırsanız **Ctrl + J** bundan sonra erişilebilirlik bağımsız olarak tüm üyeleri gösterir. Üçüncü kez çağırmak, program öğelerini çok daha geniş bir listesi gösterilir. Deyim tamamlama devre dışı bırakabilirsiniz **C/C++ genel seçenekleri** sayfası.  
  
 ![Visual C&#43; &#43; üye listesi](../ide/media/vs2015-cpp-list-members.png "vs2015_cpp_list_members")  
  
### <a name="parameter-help"></a>Parametre Yardımı  
 Bir sınıf şablonu değişken bildirimi bir açılış ayracı bir işlev çağrısı veya açılı ayraç yazdığınızda Düzenleyici küçük bir pencere için her bir işlevde veya Oluşturucu yüklemesini parametre türleri ile gösterir. İmleç konumuna bağlı--"geçerli"--kalın parametredir. Deyim tamamlama devre dışı bırakabilirsiniz **C/C++ genel seçenekleri** sayfası.  
  
 ![Visual C&#43; &#43; parametre Yardımı](../ide/media/vs-2015-cpp-param-help.png "vs_2015_cpp_param_help")  
  
### <a name="quick-info"></a>Hızlı Bilgi  
 Fare imlecini bir değişkenin geldiğinizde, küçük bir pencere tür bilgilerini gösteren bir satır içi ve türünün tanımlandığı üstbilgi görünür. İşlev imzası görmek için işlev çağrısı gelin. İçinde hızlı Bilgi'yi kapatabilirsiniz **metin düzenleyici, C/C++, Gelişmiş** sayfası.  
  
 ![Visual C&#43; &#43; Hızlıbilgi](../ide/media/vs2015-cpp-quickinfo.png "vs2015_cpp_quickInfo")  
  
## <a name="error-squiggles"></a>Hata ilişkilendirmelerini  
 Dalgalı çizgiler (değişken, anahtar sözcüğü, küme ayracı, tür adı vb.) bir program öğesinin altındaki kodda bir hata veya olası hata dikkat etmeniz çağırın. Yine de uygulama yazmak gerektiğini hatırlatan bir ileri dönük bildirimi yazdığınızda bir yeşil dalgalı çizgi görünür. Olduğunda bir mor dalgalı bir paylaşılan projede bir Android bağlamındaki hata olacaktır Windows bağlamda çalışıyoruz, ancak bir şey girin, örneğin şu anda etkin değil, kodda bir hata görüntülenir. Derleyici hatası veya uyarısı uğraşmanız gereken etkin kod kırmızı dalgalı gösterir.  
  
 ![Visual C&#43; &#43; hata ilişkilendirmelerini](../ide/media/vs2015-cpp-error-quiggles.png "vs2015_cpp_error_quiggles")  
  
## <a name="code-colorization-and-fonts"></a>Kod renklendirme ve yazı tipleri  
 Varsayılan renkleri ve yazı tiplerini kullanarak değiştirilebilir **ortamı, yazı tipleri ve renkler** özellik sayfası. Çok sayıda UI windows burada yalnızca Düzenleyici yazı tiplerini değiştirebilirsiniz. "C++ ile"; C++ için belirli ayarların başlayın diğer ayarlar, tüm diller için gösterir.  
  
## <a name="cross-platform-intellisense"></a>Platformlar arası IntelliSense  
 Hatta Android bir bağlamda çalışırken bir paylaşılan kod projesinde dalgalı çizgiler gibi bazı IntelliSense özellikleri kullanılabilir. Etkin olmayan bir projede hata ortaya çıkabilecek bazı kodlar yazma, IntelliSense ilişkilendirmelerini görüntülenmeye devam eder, ancak farklı bir renkte dalgalı çizgiler hataları geçerli bağlamda yer.  
  
 Android ve iOS için oluşturulacak şekilde yapılandırılmış bir OpenGLES uygulaması aşağıda verilmiştir. Çizimde düzenlenmekte olan paylaşılan kod gösterilmektedir. İlk görüntüde Android projesinin etkin olduğundan:  
  
 ![Etkin proje Android projesidir. ](../ide/media/intellisensecppcrossplatform.png "IntelliSenseCppCrossPlatform")  
  
 Aşağıdakilere dikkat edin:  
  
- #Else dal 8. satırda gri etkin olmayan bölge göstermek için çünkü `__ANDROID__` Android projesi için tanımlanmış.  
  
- 11. satırında Karşılama değişkeni mor dalgalı olan HELLO tanımlayıcısı ile başlatılır. Hiçbir tanımlayıcı HELLO şu anda etkin olmayan iOS projesinde tanımlanıp tanımlanmadığına olmasıdır. İOS, Android projesi satırı 11 derlenir, ancak böyle olmaz. Bu, bir şeyin paylaşılan kod olduğundan şu anda etkin yapılandırmada derler olsa da değiştirmeniz gerekir.  
  
- Satırı 12 kırmızı dalgalı BYE tanımlayıcısı içeriyor; Bu tanımlayıcı, şu anda seçili etkin projedeki tanımlanmadı.  
  
  Şimdi, etkin proje için iOS.StaticLibrary değiştirin ve dalgalı çizgiler nasıl değiştiğine dikkat edin.  
  
  ![iOS, etkin bir proje seçilir. ](../ide/media/intellisensecppcrossplatform2.png "IntelliSenseCppCrossPlatform2")  
  
  Aşağıdakilere dikkat edin:  
  
- 6. satırda #ifdef dal etkin olmayan bölge göstermek için çünkü gri renkli *_ANDROID\\*  \_ iOS projesi için tanımlı değil.  
  
- 11. satırında Karşılama değişkeni artık kırmızı dalgalı sahip HELLO, tanımlayıcı ile başlatılır. Hiçbir tanımlayıcı HELLO etkin iOS projesinde tanımlanıp tanımlanmadığına olmasıdır.  
  
- Satırı 12 mor dalgalı BYE tanımlayıcısı içeriyor; Bu tanımlayıcı, şu anda etkin olmayan Android.NativeActivity projesinde tanımlanmadı.  
  
## <a name="single-file-intellisense"></a>Tek dosya IntelliSense  
 Tek bir dosyayı dışında herhangi bir projeyi açtığınızda, IntelliSense almaya devam. Etkinleştirebilir veya giderek belirli özellikleri devre dışı bırak **metin düzenleyici, C/C++, Gelişmiş** etkinleştirmek veya IntelliSense özelliklerini devre dışı bırakmak için. Bir projenin parçası olmayan tek dosyalar için IntelliSense yapılandırmak için Ara **IntelliSense ve gözatma proje dışı dosyalar için** içinde **Gelişmiş** bölümü. Bkz: [Visual C++ Kılavuzlu Tur](http://msdn.microsoft.com/en-us/499cb66f-7df1-45d6-8b6b-33d94fd1f17c).  
  
 ![Visual C&#43; &#43; tek dosya IntelliSense](../ide/media/vs2015-cpp-single-file-intellisense.png "vs2015_cpp_single_file_intellisense")  
  
 Varsayılan olarak, tek dosyalı IntelliSense yalnızca kullanımlar standart üst bilgi dosyaları bulmak için dizinler. Ek dizinler eklemek için çözüm düğümüne kısayol menüsünü açın ve dizininize eklemek **kaynak kodu hata ayıklama** listesinde, aşağıdaki çizimde gösterildiği gibi:  
  
 ![Bir yol için bir üstbilgi dosyası ekleniyor. ](../ide/media/intellisensedebugyourcode.jpg "IntelliSenseDebugYourCode")  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IntelliSense Kullanma](../ide/using-intellisense.md)



