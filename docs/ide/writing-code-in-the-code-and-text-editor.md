---
title: Kod Düzenleyicisi özellikleri
ms.date: 02/23/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- code, editing [Visual Studio]
- code editor [Visual Studio]
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ca203b0c27906d1f861689953ca55280f73fa894
ms.sourcegitcommit: 0cdd8e8a53fb4fd5e869f07c35204419fa12783d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53160120"
---
# <a name="features-of-the-code-editor"></a>Kod Düzenleyicisi özellikleri

Visual Studio Düzenleyicisi, yazma ve kod ve metin yönetmek için kolaylaştıran birçok özellik sağlar. Genişletebilir ve Anahat oluşturmayı kullanarak farklı kod bloklarından birini daraltabilirsiniz. IntelliSense, kullanarak kod hakkında daha fazla bilgi edinebilirsiniz **Nesne Tarayıcısı**ve arama hiyerarşisi. Gibi özellikleri kullanarak kod bulabilirsiniz **Git**, **tanıma**, ve **tüm başvuruları Bul**. Kod parçacıklarıyla kod blokları ekleyebilirsiniz ve kod gibi özellikleri kullanarak oluşturabileceğiniz **kullanımından Oluştur**. Visual Studio Düzenleyicisi önce hiç kullanmadıysanız, [kodunuzu düzenleyin](https://visualstudio.microsoft.com/vs/features/ide/) hızlı bir genel bakış.

> [!NOTE]
> Bu konu, Windows üzerinde Visual Studio için geçerlidir. Mac için Visual Studio için bkz: [Kaynak Düzenleyicisi (Mac için Visual Studio)](/visualstudio/mac/source-editor).

Kodunuzu bir dizi farklı yolla görüntüleyebilirsiniz. Varsayılan olarak, **Çözüm Gezgini** dosyalar tarafından düzenlenir kodunuzu gösterir. Tıklayabilirsiniz **sınıf görünümü** pencerenin kodunu görüntülemek için sekmesinde sınıfları tarafından düzenlenir.

Arama ve tek veya birden çok dosyalardaki metni değiştirin. Daha fazla bilgi için [metin bulma ve değiştirme](../ide/finding-and-replacing-text.md). Metin bulma ve değiştirme için normal ifadeler kullanabilirsiniz. Daha fazla bilgi için [Visual Studio'da normal ifadeler kullanma](../ide/using-regular-expressions-in-visual-studio.md).

Farklı Visual Studio dilleri farklı özellik kümeleri sunar ve bazı durumlarda özellikler farklı dillerde farklı davranır. Bu farklılıkların birçoğu özelliklerin açıklamasında belirtilmiştir, ancak daha fazla bilgi için belirli Visual Studio dillerindeki bölümlere görebilirsiniz.

## <a name="editor-features"></a>Düzenleyici Özellikleri

|||
|-|-|
|Söz dizimi renklendirmesi|Bazı sözdizimi öğeleri kodu ve biçimlendirme dosyaları bunları ayırt etmek için farklı renklendirilmiştir. Örneğin, anahtar sözcükleri (gibi `using` C# ve `Imports` Visual Basic'te) bir renk, ancak türleri (gibi `Console` ve `Uri`) başka bir renktir. Diğer sözdizimi öğeleri de, dize sabit değerleri ve açıklamaları gibi renklendirilmiştir. C++ türler, numaralandırmaları ve makroları, diğer belirteçler arasında arasında ayırt etmek için renk kullanır.<br /><br /> Her tür için varsayılan rengi görebilir ve herhangi bir özel sözdizimi öğenin rengini değiştirebilirsiniz [yazı tipleri ve renkler, ortam, Seçenekler iletişim kutusu](../ide/reference/fonts-and-colors-environment-options-dialog-box.md), hangi açabileceğiniz **Araçları** menüsü.|
|Hata ve uyarı işaretleri|Kod eklediğinizde ve çözümünüzü gibi (a) farklı renkte dalgalı çizgiler (dalgalı çizgiler olarak da bilinir) veya (b) kodunuzda görünen ampuller görebilirsiniz. Kırmızı dalgalı çizgiler söz dizimi hataları belirtmek, mavi derleyici hataları gösterir, yeşil uyarılarını gösterir ve diğer hata türleri mor gösterir. [Hızlı Eylemler](../ide/quick-actions.md) sorunlara yönelik düzeltmeler önerir ve düzeltmeyi uygulamaya kolaylaştırır.<br /><br /> Her hata ve uyarı dalgalı oku için varsayılan rengi görebilirsiniz **Araçları** > **seçenekleri** > **ortam**  >   **Yazı tipleri ve renkler** iletişim kutusu. Aranacak **söz dizimi hatası**, **derleyici hatası**, **uyarı**, ve **diğer hata**.|
|Ayraç eşleştirme|Ekleme noktasını, kod dosyasındaki açık bir ayraç yerleştirildiğinde, hem hem de kapanış ayracı vurgulanır. Bu özellik eksik veya yanlış yerleştirilmiş ayraçlarla küme ayraçları anında geri bildirim sağlar. Açıp eşleşen ayracı kapatabilirsiniz **otomatik sınırlandırıcı vurgulaması** ayarı (**Araçları** > **seçenekleri**  >   **Metin düzenleyici**). Vurgu rengini değiştirebilirsiniz **yazı tipleri ve renkler** ayarı (**Araçları** > **seçenekleri** > **ortamı**). Aranacak **Ayraç eşleştirme (vurgula)** veya **Ayraç eşleştirme (dikdörtgen)**.|
|Yapı Görselleştirici|Noktalı çizgiler açılış ve kapanış küme ayracı çiftleri görmeyi kolaylaştıracak eşleşen küme ayraçlarını kodu dosyalarında bağlanın. Bu kodda bulmanıza yardımcı olabilir, daha hızlı kod tabanı. Bu satırlar üzerinde veya ile kapatabilirsiniz **yapısı Kılavuzları Göster** içinde **görünen** bölümünü **Araçları** > **seçenekleri**  >  **Metin düzenleyici** > **genel** sayfası.|
|Satır numaraları|Satır numaraları kod penceresinin sol kenar boşluğu içinde görüntülenebilir. Varsayılan olarak görüntülenmez. Bu seçenek de etkinleştirebilirsiniz **metin düzenleyici tüm diller** ayarları (**Araçları** > **seçenekleri** > **MetinDüzenleyicisi**  >  **Tüm diller**). Bu diller için ayarları değiştirerek alan bireysel programlama dilleri için satır numaralarını görüntüleyebilirsiniz (**Araçları** > **seçenekleri** > **metin düzenleyicisi**   >   **\<dil >**). Yazdırılacak satır numaraları için seçmelisiniz **satır numaralarını dahil etme** içinde **yazdırma** iletişim kutusu.|
|Değişiklik İzleme|Sol kenar boşluğunun rengi bir dosyada yaptığınız değişiklikleri izlemenize olanak sağlar. Dosya açıldı ancak kaydedilmedi yaptığınız değişiklikler sol kenar boşluğu (Seçim kenar boşluğu olarak bilinir) bulunan sarı çubuk ile belirtilir. Değişiklikleri kaydettikten sonra (ancak dosyayı kapatmadan önce), çubuğun rengi yeşile döner. Dosyayı kaydettikten sonra bir değişikliği geri alırsanız çubuk turuncu olur. Bu özelliği kapatıp açmak için değiştirmek **Değişiklikleri İzle** seçeneğini **metin düzenleyici** ayarları (**Araçları** > **seçenekleri**  >  **Metin düzenleyici**).|
|Kod ve metin seçme|Metni standart sürekli akış modunda veya bir dizi satır yerine metnin dikdörtgen bir bölümünü seçtiğiniz kutu modunda seçebilirsiniz. Kutu modunda bir seçim yapmak için basın **Alt** fareyi seçimin üzerine sürüklerken (veya basın **Alt**+**Shift** +  **\<ok tuşu >**). Seçim ilk ve son karakter tarafından tanımlanan dikdörtgen içindeki karakterlerin tümünü içerir. Yazılan veya yapıştırılan seçilen alana her satırın aynı noktasına eklenir.|
|Yakınlaştır|Size yakınlaştırma veya uzaklaştırma herhangi kod penceresinde tuşuna basarak ve bulunduran **Ctrl** anahtar ve kaydırma tekerleğini hareket ettirerek (veya **Ctrl**+**Shift** +**.** artırma ve **Ctrl**+**Shift**+**,** azaltmak için). Ayrıca **yakınlaştırma** belirli bir yakınlaştırma yüzdesi ayarlamak için kod penceresinin sol alt köşesinde kutusu. Yakınlaştırma özelliği araç pencerelerinde çalışmaz.|
|Sanal alan|Varsayılan olarak, Visual Studio düzenleyicileri bitimine son karakterden sonra satırları. böylece **sağ ok** anahtarı bir satırın sonunda imleci sonraki satırın başlangıcına taşır. Diğer bazı düzenleyicilerde bir satır son karakterden sonra bitmez ve imleci satır üzerinde herhangi bir yere yerleştirebilirsiniz. Düzenleyicide sanal alanı etkinleştirebilirsiniz **Araçları** > **seçenekleri** > **metin düzenleyici** > **tüm Diller** ayarları. Ya da etkileştiremeyeceğinizi unutmayın **sanal adres alanı** veya **sözcük kaydırma**, ikisini birden belirtmeyin.|
|Yazdırma|Kullanabileceğiniz seçenekler **yazdırma** dosya yazdırırken satır numaralarını dahil etme veya gizlemek için iletişim kutusu daraltılmış bölgeleri. İçinde **sayfa yapısı** iletişim kutusunda da tercih edebilirsiniz tam yolunu ve dosya adını seçerek yazdırma **sayfa üstbilgisi**.<br /><br /> Renkli yazdırma seçeneklerini belirleyebileceğiniz **Araçları** > **seçenekleri** > **ortam** > **yazı tipleri ve Renkleri** iletişim kutusu. Seçin **yazıcı** içinde **ayarlarını göster** renkli baskıyı özelleştirmek için. Bir dosyayı düzenlemek için çok yazdırmak için farklı renkler belirtebilirsiniz.|
|Genel Geri Al ve Yinele|**Son genel eylemi geri** ve **son genel eylemi yinele** komutlarını **Düzenle** menü geri alma veya birden çok dosyayı etkileyen genel eylemi yinele. Genel eylemler bir sınıf veya ad alanı, bir veritabanı veya birden çok dosyayı değiştiren başka herhangi bir eylemi yeniden düzenleme, bir çözüm çapında Bul ve Değiştir işlemi yeniden adlandırma içerir. Genel geri alma uygulayabilirsiniz ve bile, hangi eylemin uygulandığı çözüm kapatıldıktan sonra geçerli Visual Studio oturumunda komutları eylemlerine Yinele.|

## <a name="advanced-editing-features"></a>Gelişmiş düzenleme özellikleri

Gelişmiş Özellikler bulabilirsiniz **Düzenle** > **Gelişmiş** araç çubuğundaki menü. Bu özelliklerin tümünü kod dosyaların tüm türleri için kullanılabilir.

|||
|-|-|
|[Belgeyi Biçimlendir](code-styles-and-quick-actions.md#format-document-command)|Kod satırlarının uygun girintisini ayarlar ve belgedeki satırları ayırmak için çengelli ayraç taşır.|
|Seçimi Biçimlendir|Kod satırlarının uygun girintisini ayarlar ve seçimdeki satırları ayırmak için çengelli ayraç taşır.|
|Seçili satırları sekmeye Dönüştür|Uygun yerlerde sekmeleri öndeki boşlukları değiştirir.|
|Seçili satırları sekmeye dönüştürme|Değişiklikleri sekmeleri boşluklarla değiştirin. Dosyanızdaki tüm boşlukları sekme (veya tüm sekmeleri boşluklara) dönüştürmek isterseniz, kullanabileceğiniz `Edit.ConvertSpacesToTabs` ve `Edit.ConvertTabsToSpaces` komutları. Bu komutlar Visual Studio menülerinde görünmez, ancak bunları çağırabilirsiniz **hızlı erişim** penceresinden veya komut penceresinden.|
|Büyük Harf Yap|Büyük harfe Seçimdeki tüm karakterleri veya seçim yok ise büyük harfe ekleme noktasındaki karakteri değiştirir.|
|Küçük harfe Dönüştür|Küçük harf, seçimdeki tüm karakterleri veya herhangi bir seçim yoksa ekleme noktasındaki karakteri küçük harfe değiştirir.|
|Seçili satırları Yukarı Taşı|Seçili satır bir satır yukarı taşır. Kısayol: **Alt**+**yukarı ok**.|
|Seçili satırları Aşağı Taşı|Seçili satır bir satır aşağı taşır. Kısayol: **Alt**+**aşağı ok**.|
|Yatay boşluğu Sil|Sekme veya boşluk geçerli satırın sonunda siler.|
|Boşluğu görüntüle|Boşlukları Kabarık noktalar olarak, sekmeleri oklar olarak görüntüler. Bir dosyanın sonu dikdörtgen bir simge olarak görüntülenir. Varsa **Araçları** > **seçenekleri** > **metin düzenleyici** > **tüm diller**  >  **Sözcük kaydırma** > **Show görünür glyph'leri sözcük kaydırma için** olduğu belirlenirse, o glyph de gösterilir.|
|Sözcük kaydırma|Tüm satırların kod penceresinde görünür olmasını belgeye neden olur. Sözcük kaydırma ve buna kapatabilirsiniz **metin düzenleyici tüm diller** ayarları (**Araçları** > **seçenekleri** > **metin düzenleyicisi**   >  **Tüm diller**).|
|Seçimi açıklama satırı yap|Seçime veya geçerli satıra yorum karakterleri ekler.|
|Seçimi işletilir satıra Çevir|Seçimden veya geçerli satıra yorum karakterleri kaldırır.|
|Satır Girintisini Artır|Bir sekme (veya eşdeğer boşluk) seçilen satırlardan veya geçerli satırı ekler.|
|Satır girintisini Azalt|Bir sekme (veya eşdeğer boşluk) seçilen satırlardan veya geçerli satırı kaldırır.|
|Etiket Seç|Etiket (örneğin, XML veya HTML) içeren bir belgede etiket seçilir.|
|Etiket içeriğini Seç|Etiket (örneğin, XML veya HTML) içeren bir belgede içerik seçilir.|

## <a name="navigate-and-find-code"></a>Gidin ve kodu bulma

Kod Düzenleyicisi'nde çeşitli geriye doğru gezinmek gibi farklı yolları ve ileten önceki ekleme noktaları için tür veya üyenin tanımı görüntüleme ve gezinti çubuğunu kullanarak belirli bir yönteme atlama taşıyabilirsiniz. Daha fazla bilgi için [koda gitmek](navigating-code.md).

## <a name="find-references-in-your-code-base"></a>Kod tabanınızın başvuruları Bul

Belirli kod öğelerinin tabanınızın Burada başvurulan bulmak için kullanabileceğiniz **tüm başvuruları Bul** komutu. Ayrıca, tıkladığınızda bir tür veya üye, **başvuru vurgulama** özelliği, bu türe veya üyeye tüm başvurularını otomatik olarak vurgular. Daha fazla bilgi için [kodunuzdaki başvuruları bulma](finding-references.md).

## <a name="customize-the-editor"></a>Düzenleyiciyi özelleştirme

Başka bir Visual Studio ayarlarınızı paylaşabilir, ayarlarınızı standarda ya da kullanarak Visual Studio varsayılan ayarlarına geri döndürmeye **içeri ve dışarı aktarma ayarları Sihirbazı** komutunu  **Araçlar** menüsü. İçinde **içeri ve dışarı aktarma ayarları Sihirbazı**, seçilen genel ayarları veya dili ve projeye özgü ayarları değiştirebilirsiniz.

Yeni kısayol tuşlarını tanımlayabilir veya var olan bir kısayol tuşlarını yeniden tanımlamak için Git **Araçları** > **seçenekleri** > **ortam**  >  **Klavye**. Kısayol tuşları hakkında daha fazla bilgi için bkz. [varsayılan klavye kısayolları](../ide/default-keyboard-shortcuts-in-visual-studio.md).

Düzenleyiciyi özelleştirme hakkında daha fazla bilgi için bkz. [düzenleyiciyi özelleştirme](../ide/customizing-the-editor.md). JavaScript özel düzenleyici seçenekleri için bkz. [JavaScript Düzenleyici Seçenekleri](../ide/reference/options-text-editor-javascript-formatting.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Kaynak Düzenleyicisi (Mac için Visual Studio)](/visualstudio/mac/source-editor)
- [Visual Studio IDE](../get-started/visual-studio-ide.md)
- [Visual Studio'da C++ kullanmaya başlama](../ide/getting-started-with-cpp-in-visual-studio.md)
- [C# ve Visual Studio'da ASP.NET kullanmaya başlama](../ide/tutorial-csharp-aspnet-core.md)
- [Visual Studio'da Python ile çalışmaya başlama](../ide/quickstart-python.md)