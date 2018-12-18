---
title: .NET geliştirme üretkenliğinizi artırın
description: Gezinti, Kod Analizi genel bir bakış, daha hızlı .NET kod yazmanıza yardımcı olmak için birim testi ve diğer özellikleri daha iyi.
author: kuhlenh
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.date: 06/14/2018
ms.topic: conceptual
helpviewer_keywords:
- editor
ms.workload:
- dotnet
ms.openlocfilehash: 5a2158663defe02dc51e91e888d47f325db7226a
ms.sourcegitcommit: 20d1b9a5bf041bb28453501eb63bc0537a8e4f54
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/14/2018
ms.locfileid: "51645152"
---
# <a name="visual-studio-2017-c-productivity-guide"></a>Visual Studio 2017 C# üretkenlik Kılavuzu

Bilgi nasıl [Visual Studio 2017](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) geliştiricileri her zamankinden daha üretken hale getirir. Yazdığınız sırada bir hiyerarşi görünümüne bizim performans ve üretkenlik geliştirmeleri gezinme gibi kaynak koda dönüştürülmüş derlemeler için değişken adı önerileri yararlanmak **Test Gezgini**, tümüne Git (**Ctrl** + **T**) için dosya/türü/üyeye/sembole bildirimleri, akıllı gitmek için **özel durum Yardımcısı**, kod stili yapılandırması ve zorlaması ve satır ve kod düzeltmeleri.

## <a name="im-used-to-my-keyboard-shortcuts-from-a-different-extensioneditoride"></a>Benim için klavye kısayolları farklı bir uzantı/Düzenleyicisi/IDE kullandım yaşıyorum

**Yeni Visual Studio 2017 sürüm 15,8** kodlama, klavye düzeninizi değiştirebilirsiniz ya da başka bir IDE'den kullanıma sunulacak *Visual Studio Code* veya *ReSharper (Visual Studio)*:

![Visual Studio'da klavye düzenleri](../ide/media/VS2017Guide-Keyboard.png)

Bazı uzantılar da klavye düzenleri:

- [Visual Studio (ReSharper/Intellij) için kısayol tuşları](https://marketplace.visualstudio.com/items?itemName=JustinClareburtMSFT.HotKeys)
- [Emacs benzetimi](https://marketplace.visualstudio.com/items?itemName=JustinClareburtMSFT.EmacsEmulation)
- [VSVim](https://marketplace.visualstudio.com/items?itemName=JaredParMSFT.VsVim)

Popüler Visual Studio kısayolları şunlardır:

| Kısayol (tüm profilleri) | Komut | Açıklama |
|-|-|-|
| **CTRL**+**T** | Tümüne Git | Tüm dosya/türü/üyeye/sembole bildirimine gidin |
| **F12** (Ayrıca **Ctrl**+**tıklayın**) | Tanıma Git | Bir simgenin tanımlandığı gidin |
| **CTRL**+**F12** | Uygulamaya Git | Bir temel tür veya üye, çeşitli uygulamalar için gidin |
| **Shift**+**F12** | Tüm Başvuruları Bul | Tüm sembol veya değişmez değer başvuruları bakın |
| **Ctrl**+**.** (Ayrıca **Alt**+**girin** profilindeki C#) | Hızlı Eylemler ve Yeniden Düzenlemeler | Hangi kod düzeltmeleri görmek için İmleç konumuna veya kod seçim sırasında kod oluşturma işlemleri, yeniden düzenlemeler veya diğer hızlı Eylemler kullanılabilir |
| **Ctrl**+**D** | Satırı Yinele | İmlecin bulunduğu kod satırının çoğaltır (kullanılabilir **Visual Studio 2017 sürüm 15.6** ve üzeri) |
| **Shift**+**Alt**+**+**/**-** | Seçimi Genişlet/Sözleşmesi | Genişletir ya da geçerli seçimi Düzenleyicisi'nde sözleşmeler (kullanılabilir **Visual Studio 2017 sürüm 15.5** ve üzeri) |
| **Shift** + **Alt** + **.** | Eşleşen bir sonraki giriş işareti Ekle | Seçim ve giriş işaretini geçerli seçimi ile eşleşen bir sonraki konumda ekler (kullanılabilir **Visual Studio 2017 sürüm 15,8** ve üzeri) |
| **CTRL**+**Q** | Hızlı Başlat | Tüm Visual Studio ayarları arama |
| **F5** | Hata Ayıklamayı Başlat | Uygulamanızı hata ayıklamayı Başlat |
| **CTRL**+**F5** | Hata ayıklama Çalıştır | Uygulamanızı yerel olarak hata ayıklama olmadan çalıştırma |
| **CTRL**+**K**,**D** (varsayılan profili) veya **Ctrl**+**E**,**D**  (C# profili) | [Belgeyi Biçimlendir](code-styles-and-quick-actions.md#format-document-command) | Yeni satır, aralık ve girintileme ayarlarını göre dosyanızdaki ihlalleri biçimlendirme temizler |
| **CTRL**+**\\**,**Ctrl**+**E** (varsayılan profili) veya **Ctrl** + **W**,**E** (C# profili) | Hata Listesi görünümü | Belge, proje veya çözüm tüm hataları görmek |
| **Alt** + **PgUp/PgDn** | Sonraki/önceki soruna gidin | Bağlantı Uyarısı, öneri, belgedeki önceki/sonraki hata için (kullanılabilir **Visual Studio 2017 sürüm 15,8** ve üzeri) |

> [!NOTE]
> Bazı uzantılar, varsayılan Visual Studio tuş bağlamalarını bağlamayı Kaldır. Yukarıdaki komutları kullanmak için tuş bağlamaları Visual Studio'nun ayarlarına giderek geri yüklemek **Araçları** > **içeri ve dışarı aktarma ayarları** > **tüm ayarları sıfırla**  veya **Araçları** > **seçenekleri** > **klavye** > **sıfırlama**.

Klavye kısayolları ve Visual Studio'da komutlar daha fazla bilgi [Belgelerimizi](../ide/tips-and-tricks-for-visual-studio.md).

## <a name="i-need-a-way-to-quickly-navigate-to-files-or-types"></a>Dosya veya türler için hızlıca gezinmek için bir yola ihtiyacım

Visual Studio 2017 adlı bir özellik olan **tümüne Git** (**Ctrl**+**T**). **Tümüne Git** herhangi dosya, tür, üye veya sembol bildirimi hızla atlamak sağlar.

- Bu arama çubuğunun konumu değiştirebilir veya 'Canlı Gezinti önizlemeyi' ile Kapat **dişli** simgesi.
- Bizim sorgu söz dizimi (örneğin, "t mytype") kullanarak sonuçları filtreleyin. Ayrıca, yalnızca geçerli belgede arama kapsamını belirleyebilirsiniz.
- camelCase eşleşen destekleniyor!

![Visual Studio tüm Git](../ide/media/VS2017Guide-go-to-all.png)

## <a name="my-team-enforces-code-style-rules-on-our-codebase"></a>Kod stili kurallarından bizim kod temeli üzerinde takımım zorlar

Kullanabileceğiniz bir *.editorconfig* kodlama kurallarını kod oluşturma ve bunları kaynağınızla seyahat dosya.

- Yükleyebileceğiniz [EditorConfig dil Hizmetleri Uzantısı](https://aka.ms/editorconfig), kolaylaştıran ekleme ve düzenleme bir *.editorconfig* dosyasını Visual Studio'da.
- Denemenin [için Visual Studio Intellicode uzantısı](/visualstudio/intellicode/intellicode-visual-studio). Bu Deneysel uzantı mevcut koddan, kod stilleri algılar ve ardından boş olmayan oluşturur *.editorconfig* dosya ile kod stili tercihlerinizden zaten tanımlanmış.
- Kullanıma [.NET kodlama kuralı seçeneklerini](https://aka.ms/editorconfigDocs) belgeleri.
- Bkz: [bu gist](https://gist.github.com/kuhlenh/5471666a7a2c57fea427e81cf0a41da8) örneği *.editorconfig* dosya.

![Visual Studio'da kod stil uygulama](../ide/media/VSGuide_CodeStyle.png)

## <a name="i-need-more-refactorings-and-code-fixes"></a>Daha fazla sayıda yeniden düzenleme ve kod düzeltmeleri gerekiyor

Visual Studio 2017 ile çok sayıda yeniden düzenleme, kod oluşturma eylemleri ve kod düzeltmeleri gelir. Kırmızı dalgalı çizgiler hataları temsil eden yeşil dalgalı çizgiler uyarıları temsil eder ve gri üç noktaya kod önerileri temsil eder. Ampul/tornavida simgesine tıklayarak veya basarak erişim kod düzeltmeleri yapabilirsiniz **Ctrl**+**.** veya **Alt**+**girin**. Her düzeltme, düzeltme nasıl çalıştığına ilişkin bir Canlı kod fark gösteren bir önizleme penceresi ile birlikte gelir.

- Popüler hızlı düzeltmeler ve yeniden düzenlemeler içerir:
  - *Yeniden Adlandır*
  - *Ayıklama Yöntemi*
  - *Metot İmzasını Değiştirme*
  - *Oluşturucu Oluşturma*
  - *Üretme Metodu*
  - *Türü dosyaya Taşı*
  - *Null denetimi Ekle*
  - *Parametre Ekle*
  - *Gereksiz kullanımları Kaldır*
  - Daha fazla bilgi Bkz bizim [belgeleri](https://aka.ms/refactorings)
- Kendi yeniden düzenleme ya da kod düzeltme yazma [Roslyn Çözümleyicileri](https://github.com/dotnet/roslyn/wiki/Getting-Started-Writing-a-Custom-Analyzer-&-Code-Fix).
- Çeşitli topluluk üyeleri, ek kod incelemeleri ekleyen ücretsiz uzantıya yazmış:
  - [FXCop Çözümleyicileri](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/)
  - [Roslynator](https://marketplace.visualstudio.com/items?itemName=josefpihrt.Roslynator2017)
  - [Visual Studio için SonarLint](https://marketplace.visualstudio.com/items?itemName=SonarSource.SonarLintforVisualStudio2017)
  - [StyleCopAnalyzers](https://www.nuget.org/packages/stylecop.analyzers/)

![Visual Studio'da yeniden düzenlemeler](../ide/media/VSGuide_CodeAnalysis.png)

## <a name="i-need-find-usages-go-to-implementation-navigate-to-decompiled-assemblies"></a>Bulma kullanımları, uygulamaya Git, kaynak koda dönüştürülmüş derlemeleri gidin almam gerekiyor

Visual Studio 2017'yi arayın ve kod temelinizde gidin yardımcı olmak üzere birçok özelliğe sahiptir. Daha fazla bilgi edinin [kod gezintisi özelliklerinde](../ide/navigating-code.md)

| Özellik | Kısayol | Ayrıntılar/geliştirmeleri |
|- | - | -|
| Tüm Başvuruları Bul | **Shift**+**F12**| Sonuçları renklendirilmiş ve gruplandırılabilir proje, tanımı, vs. Ayrıca 'sonuçları kilitleyebilir'. |
| Uygulamaya Git | **CTRL**+**F12** | Tanıma Git kullanabileceğiniz `override` için geçersiz kılınan üyesiyle gitmek için anahtar sözcüğü |
| Tanıma Git | **F12** veya **Ctrl**+**tıklayın**| Basılı tutabilirsiniz **Ctrl** navgiate tanımına için tıklatırken |
| Tanıma göz at | **Alt**+**F12** | Satır içi görünüm tanımı |
| Yapı Görselleştirici | Gri, noktalı satırları ayraçlar arasındaki | Üzerine gelindiğinde, kod yapısını görmek için |
| Kaynak koda dönüştürülmüş derlemeleri gitme | **F12** veya **Ctrl**+**tıklayın** | Özelliğini etkinleştirerek (ile yetenek decompiled) bir dış kaynağa gidin: **Araçları** > **seçenekleri** > **metin düzenleyici**  >  **C#** > **Gelişmiş** > **kaynak koda dönüştürülmüş kaynaklara gezintiyi etkinleştir**. |

![Tümüne Git ve tüm başvuruları Bul](../ide/media/VSIDE_Productivity_Navigation.png)

## <a name="i-want-to-run-and-see-my-unit-tests"></a>Çalıştırın ve birim testlerimi görmek istiyorum

Visual Studio 2017'de çok fazla test deneyimde yapılan geliştirmeler yaptık. Kullanın ya da test etme deneyimlerine MSTest v1, MSTest v2, NUnit veya XUnit ile bizim birim test çerçeveleri.

- **Test Gezgini** test bulma işleminin hızlı sürüm 15.6 (için en iyi sonuçları, test bağdaştırıcınızın en son sürüme yükseltme) içinde.
- Test Gezgini'nde yeni ile testleri düzenlemek *hiyerarşik sıralama* 15.6 sürümünde.
- [Live unit Testing](../test/live-unit-testing.md) sürekli olarak kod değişikliklerinizden etkilenen testleri çalıştırır ve testlerinizi durumunu bildirmek için satır içi Düzenleyicisi simgeleri güncelleştirir. Dahil veya hariç belirli testleri test projelerinden, *Canlı Test kümesi*.

![Visual Studio'da metin Gezgini hiyerarşi görünümü](../ide/media/VSGuide_Testing.png)

## <a name="i-want-to-debug-my-code"></a>Kodumda Hata Ayıkla istiyorum

Visual Studio 2017'de bir sürü yeni hata ayıklama özellikleri ekledik:

- *Çalıştır'ı tıklatın* bir kod satırının yanındaki gelin sağlar görüntülenen yeşil 'Yürüt' simge ulaşmak ve bu satırı ulaşana kadar programınızı çalıştırın.
- Yeni **özel durum Yardımcısı** hangi değişkeni gibi en önemli bilgileri üst düzey iletişim kutusunda bir NullReferenceException ' null' geçirir.
- [Geri adım](../debugger/how-to-use-intellitrace-step-back.md) hata ayıklama, önceki kesme noktaları veya adımlara geri dönün ve daha önce olduğu gibi uygulama durumunu görüntüleme olanak tanır.
- [Anlık görüntü hata ayıklama](/azure/application-insights/app-insights-snapshot-debugger) bir canlı web uygulaması bir özel durum oluşturuldu anda durumunu araştırmanıza olanak tanır (Azure'da olmalıdır).

![Visual Studio 2017'de yeni bir özel durum Yardımcısı](../ide/media/VSGuide_Debugging.png)

## <a name="i-want-to-use-version-control-with-my-projects"></a>Sürüm denetimi ile Projelerim kullanmak istiyorum

Git veya TFVC, depolama ve Visual Studio'da kodunuzu güncelleştirmek için kullanabilirsiniz.

- Değişikliklerinizi yerel düzenleme **Takım Gezgini** ve durum çubuğunda işlemeler ve değişiklikleri izlemek için kullanabilirsiniz.
- Sürekli tümleştirme ve teslim ile Visual Studio içinde projeleriniz için ayarlama bizim [Visual Studio için sürekli teslim Araçları](https://marketplace.visualstudio.com/items?itemName=VSIDEDevOpsMSFT.ContinuousDeliveryToolsforVisualStudio) uzantısı ve Çevik Geliştirici iş akışını benimseyin.

![Visual Studio kaynak denetimi](../ide/media/VSIDE_Productivity_SourceControl.png)

## <a name="what-other-features-do-i-need-to-know-about"></a>Başka hangi özellikler hakkında bilgi edinmek ihtiyacım var?

Kod yazma daha verimli hale getirmek için düzenleyici ve üretkenlik özelliklerin bir listesi aşağıda verilmiştir. Bazı özellikler, çünkü bunlar devre dışı (bunlar makinenizde şeyler dizin, tartışmalı veya şu anda Deneysel) varsayılan olarak etkinleştirilmesi gerekebilir.

| Özellik | Ayrıntılar | Etkinleştirme |
|-|-|-|
| Çözüm Gezgini'nde dosyayı bulun | Etkin dosyada vurgular **Çözüm Gezgini** | **Araçlar** > **seçenekleri** > **projeler ve çözümler** > **Çözüm Gezgini'nde etkin öğe izleme** |
| Başvuru bütünleştirilmiş kodları ve NuGet paketleri içinde türler için using ekleme | Bir ampul başvurulmayan bir türü için bir NuGet paketini yüklemek için bir kod düzeltme gösterir | **Araçlar** > **seçenekleri** > **metin düzenleyici** > **C#** > **Gelişmiş**   >  **Reference bütünleştirilmiş kodlarında türler için using Öner** ve **NuGet paketlerinde türler için using Öner** |
| Tam çözüm analizini etkinleştirme | Çözümünüzdeki tüm hataları görmek **hata listesi** | **Araçlar** > **seçenekleri** > **metin düzenleyici** > **C#** > **Gelişmiş**   >  **Tam çözüm analizini etkinleştirme** |
| Kaynak koda dönüştürülmüş kaynaklara gezintiyi etkinleştir | Tür/üye dış kaynaklardan tanıma ver ve metot gövdeleri gösterilecek yetenek kaynak koda dönüştürücü kullanma | **Araçlar** > **seçenekleri** > **metin düzenleyici** > **C#** > **Gelişmiş**   >  **Kaynak koda dönüştürülmüş kaynaklara gezintiyi etkinleştir** |
| Tamamlanma/öneri modu | IntelliSense--Intellij arka planlar geliştiricilere tamamlama davranışı eğilimli ayarını değiştirmek için değişiklikleri buraya varsayılan | **Menü** > **Düzenle** > **IntelliSense** > **tamamlama modunu Değiştir** |
| [CodeLens](../ide/find-code-changes-and-other-history-with-codelens.md) | Başvuru bilgileri kod ve değişiklik geçmişi Düzenleyicisi'nde görüntüler | **Araçlar** > **seçenekleri** > **metin düzenleyici** > **tüm diller**  >   **CodeLens** |
| [Kod parçacıkları](../ide/visual-csharp-code-snippets.md) | Ortak Demirbaş saplama Yardım | Bir kod parçacığı adı yazıp basın **sekmesini** iki kez. |

## <a name="missing-a-feature-that-makes-you-productive-or-experiencing-poor-performance"></a>Üretken veya yaşayan kötü performans sağlayan bir özellik eksik?

Bize geri bildirim bırakmak için birkaç yolu vardır:

- .NET özellik istekleri üzerinde dosyalandı bizim [GitHub deposunu](https://github.com/dotnet/roslyn/issues).
- Visual Studio özellik isteklerini, hataları ve performans sorunları Dosyalanan kullanarak **geri bildirim gönder** Visual Studio pencerenizin sağ üst simge.
