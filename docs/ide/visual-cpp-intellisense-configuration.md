---
title: IntelliSense için bir C++ projesi yapılandırma
ms.date: 10/08/2018
ms.technology: vs-ide-general
ms.topic: conceptual
author: mblome
ms.author: mblome
manager: wpickett
ms.workload:
- cplusplus
ms.openlocfilehash: 3772c2c910188aacb675f267d20f5e0f16565001
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49836651"
---
# <a name="configure-a-c-project-for-intellisense"></a>IntelliSense için bir C++ projesi yapılandırma

Bazı durumlarda, IntelliSense düzgün çalışmasını almak için C++ projenize el ile yapılandırmanız gerekebilir. (.Vcxproj dosyaları bağlı olarak), MSBuild projeleri için Proje Özellikleri'nde ayarlarını yapabilirsiniz. MSBuild olmayan projeler için proje kök dizininde CppProperties.json dosyasındaki ayarları ayarlayın. Bazı durumlarda, IntelliSense makro tanımları anlamanıza yardımcı olacak bir ipucu dosyası oluşturmanız gerekebilir. Visual Studio IDE tanımlamak ve IntelliSense sorunlarını gidermenize yardımcı olur.



## <a name="single-file-intellisense"></a>Tek Dosyalı IntelliSense

Bir projede yer almayan bir dosyayı açtığınızda, Visual Studio bazı IntelliSense desteği sunar ancak varsayılan olarak, hiçbir hata ilişkilendirmelerini gösterilir. Varsa **gezinti çubuğu** diyor *çeşitli dosyalar*, ardından, büyük olasılıkla açıklar neden yanlış kod altında hata ilişkilendirmelerini görmediğinizden veya neden önişlemci makrosu tanımlanmadı.

## <a name="check-the-error-list"></a>Hata listesini gözden geçirin

Bir dosya, tek dosyalı modunda açık değil ve IntelliSense doğru çalışmıyorsa, kontrol etmek için ilk hata listesi penceresine yerdir. Geçerli kaynak dosyanın tüm bulunan üst bilgi dosyaları ile birlikte tüm IntelliSense hataları görmek için **derleme + IntelliSense** açılır:

![VC ++ hata Listesi'nde IntelliSense](media/vcpp-intellisense-error-list.png)

IntelliSense, en fazla 1000 hata üretir. Kaynak dosya tarafından eklenen üstbilgi dosyalarında 1000'den hatalar varsa, kaynak dosyası yalnızca bir tek hata dalgalı çok kaynak dosyasının başında gösterir.

## <a name="ensure-include-paths-are-correct"></a>Olun #include yolları doğru

### <a name="msbuild-projects"></a>MSBuild projeleri

Visual Studio IDE dışında yapılarınızı çalıştırma ve derlemelerinizi başarılı olmaktadır ancak IntelliSense yanlış ise komut satırınızda bir veya daha fazla yapılandırması proje ayarları ile eşitlenmemiş olduğunu mümkündür. ' Nde proje düğümüne sağ **Çözüm Gezgini** emin olun tüm **#include** yolları geçerli yapılandırma ve platform için doğru. Tüm yapılandırmalar ve platformlar yolları aynıysa seçebileceğiniz **yapılandırmalarında** ve **tüm platformlar** ve yollarının doğru olduğunu doğrulayın.

![VC ++ dizinleri](media/vcpp-intellisense-include-paths.png)

 Geçerli görmek için değerleri gibi derleme makroları **VC_IncludePath**ekleme dizinleri satırı seçin ve açılan sağ tıklayın. Ardından  **\<Düzenle >** tıklayın **makroları** düğmesi.

### <a name="makefile-projects"></a>Derleme görevleri dosyası projeleri

NMake proje şablonuna dayalı derleme görevleri dosyası projeleri için seçin **NMake** sol bölmede seçip **ekleme kodu arama yolunu** altında **IntelliSense** Kategori:

![Derleme görevleri dosyası projesi yolları içerir](media/vcpp-intellisense-makefile-include-paths.png)

Daha fazla bilgi için [nasıl yapılır: derleme görevleri dosyası projeleri için IntelliSense'i etkinleştirme](/cpp/ide/how-to-enable-intellisense-for-makefile-projects).

### <a name="open-folder-projects"></a>Proje klasörü aç

CMake projeleri için emin #include yolları belirtilen doğru CMakeLists.txt içindeki tüm yapılandırmalar için. Diğer proje türleri CppProperties.json dosyası gerektirebilir. Daha fazla bilgi için [yapılandırma IntelliSense ile CppProperties.json](/cpp/ide/non-msbuild-projects#cppproperties). Yolları dosyasında tanımlanan her bir yapılandırma için doğru olduğundan emin olun.

CppProperties.json dosyada bir sözdizimi hatası varsa, etkilenen dosyalarında IntelliSense hatalı olacaktır. Visual Studio çıktı penceresinde bir hata görüntüler.

## <a name="tag-parser-issues"></a>Etiket ayrıştırıcısı sorunları

Etiket ayrıştırıcısı göz atma ve gezinme için kullanılan bir "benzer öğe" C++ ayrıştırıcısıdır. Çok hızlıdır, ancak tamamen her kod yapısı kavrama çalışmaz.

Örneğin, Önişlemci makroları değerlendirmez ve bu nedenle yanlış ağır kullanımına zarar yapan kod ayrıştırmak. Etiket ayrıştırıcısı bir alışkın olmadığınız bir kod yapısı karşılaştığında, bu, tüm bölge kodu atlayabilirsiniz.

Visual Studio'da bu sorunu hangi bildirimleri iki genel yolu vardır:

1. En içteki bir makro gezinti çubuğunu gösterir, ardından geçerli işlev tanımı atlandı:

   ![Etiket ayrıştırıcısı işlev tanımı atlar.](media/vcpp-intellisense-tag-parser-macro.png)

1. Bir işlev tanımı zaten tanımlı bir işlev oluşturmak IDE sunar:

   ![Etiket ayrıştırıcısı sunar var olan bir fonksiyon tanımlayın](media/vcpp-intellisense-tag-parser-function.png)

Bu tür sorunları gidermek için adlı bir dosya ekleyin. **cpp.hint** kök çözüm dizininizin. Daha fazla bilgi için [ipucu dosyaları](/cpp/ide/hint-files).

**Visual Studio 2017 sürüm 15.7** etiket ayrıştırıcısı hatalarını Hata Listesi penceresinde görünür.

## <a name="validate-project-settings-with-diagnostic-logging"></a>Tanılama günlüğüne kaydetme ile proje ayarlarını doğrulama

IntelliSense derleyici INCLUDE Paths ve Önişlemci makroları dahil olmak üzere, doğru derleyici seçenekleri kullanılıp kullanılmadığını kontrol etmek için IntelliSense, tanılama günlüğü komut satırlarında açın **Araçlar > Seçenekler > Metin Düzenleyicisi > C/C++ > Gelişmiş > Tanılama günlüğünün**. Ayarlama **günlüğü etkinleştir** true olarak **günlük düzeyi** (en ayrıntılı), 5 ve **günlüğü filtresi** 8 (IntelliSense günlük kaydı).

Çıkış penceresi artık IntelliSense derleyici geçirilen komut satırları gösterir. Örnek çıktı aşağıdaki gibidir:

```output
 [IntelliSense] Configuration Name: Debug|Win32
 [IntelliSense] Toolset IntelliSense Identifier:
 [IntelliSense] command line options:
 /c
 /I.
 /IC:\Repo\Includes
 /DWIN32
 /DDEBUG
 /D_DEBUG
 /Zc:wchar_t-
 /Zc:forScope
 /Yustdafx.h
```

Bu bilgiler IntelliSense hatalı bilgilerin neden sağlama anlamanıza yardımcı olabilir. Örneğin, projenizin ekleme dizini içeriyorsa **$(MyVariable) \Include**ve tanılama günlüğü gösterir **/I\Include** bir INCLUDE yolu olarak anlamına **$(MyVariable)** değerlendirilir değildi ve en son kaldırıldı yolunu ekleyin.

## <a name="about-the-intellisense-build"></a>IntelliSense derleme hakkında

Visual Studio, oluşturmak ve veritabanı destek veren tüm IntelliSense özelliklerini güncelleştirmek için adanmış bir C++ derleyicisi kullanır. IntelliSense veritabanı kod ile eşitlenmiş tutmak için Visual Studio otomatik olarak yalnızca IntelliSense yapılar arka plan görevleri proje ayarları veya kaynak dosyalarda yapılan bazı değişikliklere yanıt olarak başlatılır.

Ancak, bazı durumlarda Visual Studio IntelliSense veritabanı zamanında güncelleştirilemeyebilir. Örneğin, çalıştırdığınızda bir **git çekme** veya **git checkout** komutu, Visual Studio alabilir için bir saat dosyalarında değişikliklerini algılamak için. ' Nde proje düğümüne sağ tıklayarak bir çözümdeki tüm dosyaları bir yeniden tarama zorlayabilirsiniz **Çözüm Gezgini** seçip **yeniden tarama çözüm**.

## <a name="troubleshooting-intellisense-build-failures"></a>IntelliSense derleme hatalarını giderme

Bir IntelliSense derleme ikili dosyaları oluşturmaz, ancak yine de başarısız olabilir. Hatanın olası nedenlerinden biri, özel .props veya .targets dosyaları olmasıdır. Visual Studio 2017 sürüm 15.6, çıkış penceresinde IntelliSense yalnızca derleme hataları günlüğe kaydedilir. Bunları görmek için ayarlanmış **çıktıyı Göster** için **çözüm**:

![Çözüm hataları için çıkış penceresine](media/vcpp-intellisense-output-window.png)

Hata iletisi, tasarım zamanı izlemeyi etkinleştirmek için bildirin:

```output
 error: Designtime build failed for project 'E:\src\MyProject\MyProject.vcxproj',
 configuration 'Debug|x64'. IntelliSense might be unavailable.
 Set environment variable TRACEDESIGNTIME=true and restart
 Visual Studio to investigate.
```

True ve Visual Studio'yu yeniden başlatmak için TRACEDESIGNTIME ortam değişkenini ayarladığınız derleme hatasını tanılamanıza yardımcı olabilecek % TEMP % dizininde bir günlük dosyası görürsünüz.

TRACEDESIGNTIME ortam değişkenini hakkında daha fazla bilgi için bkz: [Roslyn](https://github.com/dotnet/roslyn/wiki/Diagnosing-Project-System-Build-Errors) ve [ortak proje sistemi](https://github.com/dotnet/project-system/blob/master/docs/design-time-builds.md). Bilgiler Bu makaleler, C++ projeleri için geçerlidir.

## <a name="see-also"></a>Ayrıca Bkz.

- [Visual C++ IntelliSense](visual-cpp-intellisense.md)
