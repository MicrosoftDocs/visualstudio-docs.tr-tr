---
title: Kod ve metin düzenleyici içinde kod yazma | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.texteditor
dev_langs:
- JScript
- VB
- CSharp
helpviewer_keywords:
- code editor, word wrap
- outlining
- code, editing
- squiggles
- code editor, outlining
- code editor, error and warning markers
- word wrap
- code editor, syntax coloring
- code editor, go to definition
- diff
- code editor [Visual Studio]
- code editor, diff
- error and warning markers
- code editor, navigation bar
- code editor, customizing
- comment selection
- code editor, tabify
- brace matching
- code editor, line numbers
- printing
- code editor, brace matching
- code editor, squiggles
- code editor, features
- line numbers
- go to definition
- syntax coloring
- code editor, navigate to
- code editor, comparing files
- code editor, zoom
- code editor
- code files
- go to line
- tabify
- zoom
- navigate to
- line break characters
- code editor, virtual space
- code editor, change tracking
- code editor, comment selection
- code editor, printing
- virtual space
- code editor, line break characters
- code editor, go to line
- code
ms.assetid: cb53ab9a-5b76-4759-b9e8-7bf32298ecbe
caps.latest.revision: 46
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: bd12cfee50db7dd085fee6c0591dfff3f579e640
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49838692"
---
# <a name="writing-code-in-the-code-and-text-editor"></a>Kod ve Metin Düzenleyici'de Kod Yazma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]
Visual Studio Düzenleyicisi, yazmak ve kodunuzu yönetmenizi kolaylaştıran birçok özellik sağlar. Genişletebilir ve Anahat oluşturmayı kullanarak farklı kod bloklarından birini daraltabilirsiniz. IntelliSense, kullanarak kullandığınız kod hakkında daha fazla bilgi **Nesne Tarayıcısı**ve arama hiyerarşisi. Gibi özellikleri kullanarak kodunuzda gezebilirsiniz gidebilirsiniz **gitmek için**, **tanıma**, ve **tüm başvuruları Bul**. Kod parçacıklarıyla kod blokları ekleyebilirsiniz ve kod gibi özellikleri kullanarak oluşturabileceğiniz **kullanımından Oluştur**. Visual Studio 2015 Düzenleyicisi önce hiç kullanmadıysanız, [kodunuzu düzenleme](https://www.visualstudio.com/features/ide-vs) hızlı bir genel bakış.  

 Kodunuzu bir dizi farklı yolla görüntüleyebilirsiniz. Çözümünüzü sınıf görünümü görmek için açabilirsiniz **sınıf görünümü** penceresi veya ait düğümleri genişletebilirsiniz **Çözüm Gezgini** sınıf dosyaları altındaki.  

 Arama ve tek veya birden çok dosya için metni değiştirin. Daha fazla bilgi için [bulma ve değiştirme metnini](../ide/finding-and-replacing-text.md). Normal ifadeler kullanırsanız, Bul ve Değiştir Not artık kullanın .NET normal ifadeler. Daha fazla bilgi için [Visual Studio'da normal ifadeler kullanarak](../ide/using-regular-expressions-in-visual-studio.md).  

 Farklı Visual Studio dilleri farklı özellik kümeleri sunar ve bazı durumlarda özellikler farklı dillerde farklı davranır. Bu farklılıkların birçoğu özelliklerin açıklamasında belirtilmiştir, ancak daha fazla bilgi için belirli Visual Studio dillerindeki bölümlere görebilirsiniz.  

> [!IMPORTANT]
>  Visual Studio sürümü ve kullandığınız ayarlar IDE içindeki özellikleri etkileyebilir. Bunlar, bu konuda açıklanan olanlardan farklı olabilir.  

## <a name="editor-features"></a>Düzenleyici Özellikleri  

|||  
|-|-|  
|Söz dizimi renklendirmesi|Bazı sözdizimi öğeleri kodu ve biçimlendirme dosyaları bunları ayırt etmek için farklı renklendirilmiştir. Örneğin, anahtar sözcükleri (gibi `using` C# ve `Imports` Visual Basic'te) bir renk, ancak türleri (gibi `Console` ve `Uri`) başka bir renktir. Diğer sözdizimi öğeleri de, dize sabit değerleri ve açıklamaları gibi renklendirilmiştir. C++ türler, numaralandırmaları ve makroları, diğer belirteçler arasında arasında ayırt etmek için renk kullanır.<br /><br /> Her tür için varsayılan rengi görebilir ve herhangi bir özel sözdizimi öğenin rengini değiştirebilirsiniz [yazı tipleri ve renkler, ortam, Seçenekler iletişim kutusu](../ide/reference/fonts-and-colors-environment-options-dialog-box.md), hangi açabileceğiniz **Araçları** menüsü.|  
|Hata ve uyarı işaretleri|Kod eklediğinizde ve çözümünüzü gibi (a) farklı renkte dalgalı çizgiler (dalgalı çizgiler olarak da bilinir) veya (b) kodunuzda görünen ampuller görebilirsiniz. Kırmızı dalgalı çizgiler söz dizimi hataları belirtmek, mavi derleyici hataları gösterir, yeşil uyarılarını gösterir ve diğer hata türleri mor gösterir. [Ampuller](../ide/perform-quick-actions-with-light-bulbs.md) sorunlara yönelik düzeltmeler önerir ve düzeltmeyi uygulamaya kolaylaştırır.<br /><br /> Her hata ve uyarı dalgalı oku için varsayılan rengi görebilirsiniz **Araçlar/Seçenekler/ortam/yazı tipi ve renkler** iletişim kutusu. Aranacak **söz dizimi hatası**, **derleyici hatası**, **uyarı**, ve **diğer hata**.|  
|Ayraç eşleştirme|Ekleme noktasını, kod dosyasındaki açık bir ayraç yerleştirildiğinde, hem hem de kapanış ayracı vurgulanır. Bu özellik eksik veya yanlış yerleştirilmiş ayraçlarla küme ayraçları anında geri bildirim sağlar. Açıp eşleşen ayracı kapatabilirsiniz **otomatik sınırlandırıcı vurgulaması** ayarı (**Araçlar/Seçenekler/metin düzenleyici**). Vurgu rengini değiştirebilirsiniz **yazı tipleri ve renkler** ayarı (**Araçlar/Seçenekler/ortam**). Aranacak **Ayraç eşleştirme (vurgula)** veya **Ayraç eşleştirme (dikdörtgen)**.|  
|Satır numaraları|Satır numaraları kod penceresinin sol kenar boşluğu içinde görüntülenebilir. Varsayılan olarak görüntülenmez. Bu seçenek de etkinleştirebilirsiniz **metin düzenleyici tüm diller** ayarları (**Araçlar/Seçenekler/metin düzenleyici diller**). Bu diller için ayarları değiştirerek alan bireysel programlama dilleri için satır numaralarını görüntüleyebilirsiniz (**Araçlar / Seçenekler / metin düzenleyici /\<dil >**). Yazdırılacak satır numaraları için dahil etme satır numaralarını seçmelisiniz **yazdırma** iletişim kutusu.|  
|Değişiklik İzleme|Sol kenar boşluğunun rengi bir dosyada yaptığınız değişiklikleri izlemenize olanak sağlar. Dosya açıldı ancak kaydedilmedi yaptığınız değişiklikler sol kenar boşluğu (Seçim kenar boşluğu olarak bilinir) bulunan sarı çubuk ile belirtilir. Değişiklikleri kaydettikten sonra (ancak dosyayı kapatmadan önce), çubuğun rengi yeşile döner. Dosyayı kaydettikten sonra bir değişikliği geri alırsanız çubuk turuncu olur. Bu özelliği kapatıp açmak için değiştirmek **Değişiklikleri İzle** seçeneğini **metin düzenleyici** ayarları (**Araçlar/Seçenekler/metin düzenleyici**).|  
|Kod ve metin seçme|Metni standart sürekli akış modunda veya bir dizi satır yerine metnin dikdörtgen bir bölümünü seçtiğiniz kutu modunda seçebilirsiniz. Kutu modunda bir seçim yapmak için fareyi seçimin üzerine sürüklerken ALT tuşuna (veya ALT + SHIFT tuşlarına basın + \<ok tuşu >). Seçim ilk ve son karakter tarafından tanımlanan dikdörtgen içindeki karakterlerin tümünü içerir. Yazılan veya yapıştırılan seçilen alana her satırın aynı noktasına eklenir.|  
|Yakınlaştır|Size yakınlaştırma veya uzaklaştırma herhangi kod penceresinde tuşuna basarak ve CTRL tuşunu basılı tutarak ve kaydırma tekerleğini hareket ettirerek (veya CTRL + SHIFT +. artırma ve CTRL + SHIFT +, azaltmak için). Ayrıca, belirli bir yakınlaştırma yüzdesi ayarlamak için kod penceresinin sol alt köşedeki Yakınlaştır kutusunu da kullanabilirsiniz. Yakınlaştırma özelliği araç pencerelerinde çalışmaz.|  
|Sanal alan|Varsayılan olarak, Visual Studio Düzenleyicisi satırları son karakterden sonra sona bir satırın sonunda sağ ok tuşu imleci sonraki satırın başlangıcına taşır. Diğer bazı düzenleyicilerde bir satır son karakterden sonra bitmez ve imleci satır üzerinde herhangi bir yere yerleştirebilirsiniz. Düzenleyicide sanal alanı etkinleştirebilirsiniz **Araçlar/Seçenekler/metin düzenleyici diller** ayarları. Ya da etkileştiremeyeceğinizi unutmayın **sanal adres alanı** veya **sözcük kaydırma**, ikisini birden belirtmeyin.|  
|Yazdırma|Kullanabileceğiniz seçenekler **yazdırma** dosya yazdırırken satır numaralarını dahil etme veya gizlemek için iletişim kutusu daraltılmış bölgeleri. İçinde **sayfa yapısı** iletişim kutusunda da tercih edebilirsiniz tam yolunu ve dosya adını seçerek yazdırma **sayfa üstbilgisi**.<br /><br /> Renkli yazdırma seçeneklerini belirleyebileceğiniz **Araçlar/Seçenekler/ortam/yazı tipi ve renkler** iletişim kutusu. Seçin **yazıcı** içinde **ayarlarını göster** renkli baskıyı özelleştirmek için. Bir dosyayı düzenlemek için çok yazdırmak için farklı renkler belirtebilirsiniz.|  
|Genel Geri Al ve Yinele|**Son genel eylemi geri** ve **son genel eylemi yinele** komutlarını **Düzenle** menü geri alma veya birden çok dosyayı etkileyen genel eylemi yinele. Genel eylemler bir sınıf veya ad alanı, bir veritabanı veya birden çok dosyayı değiştiren başka herhangi bir eylemi yeniden düzenleme, bir çözüm çapında Bul ve Değiştir işlemi yeniden adlandırma içerir. Genel geri alma uygulayabilirsiniz ve bile, hangi eylemin uygulandığı çözüm kapatıldıktan sonra geçerli Visual Studio oturumunda komutları eylemlerine Yinele.|  

## <a name="advanced-editing-features"></a>Gelişmiş Düzenleme özelliklerinden  
 Gelişmiş Özellikler bulabilirsiniz **Düzenle/Gelişmiş** alt. Bu özelliklerin hepsi kod dosyaların tüm türleri için kullanılabilir.  

|||  
|-|-|  
|Belgeyi Biçimlendir|Kod satırlarının uygun girintisini ayarlar ve belgedeki satırları ayırmak için çengelli ayraç taşır.|  
|Seçimi Biçimlendir|Kod satırlarının uygun girintisini ayarlar ve seçimdeki satırları ayırmak için çengelli ayraç taşır.|  
|Seçili satırları sekmeye Dönüştür|Uygun yerlerde sekmeleri öndeki boşlukları değiştirir.|  
|Seçili satırları sekmeye dönüştürme|Değişiklikleri sekmeleri boşluklarla değiştirin. Dosyanızdaki tüm boşlukları sekme (veya tüm sekmeleri boşluklara) dönüştürmek isterseniz, kullanabileceğiniz `Edit.ConvertSpacesToTabs` ve `Edit.ConvertTabsToSpaces` komutları. Bu komutlar Visual Studio menülerinde görünmez, ancak bunları hızlı erişim penceresinden veya komut penceresinden çağırabilirsiniz.|  
|Büyük Harf Yap|Büyük harfe Seçimdeki tüm karakterleri veya seçim yok ise büyük harfe ekleme noktasındaki karakteri değiştirir.|  
|Küçük harfe Dönüştür|Küçük harf, seçimdeki tüm karakterleri veya herhangi bir seçim yoksa ekleme noktasındaki karakteri küçük harfe değiştirir.|  
|Belgeyi doğrula|JScript kod dosyalarını doğrular.|  
|Yatay boşluğu Sil|Sekme veya boşluk geçerli satırın sonunda siler.|  
|Boşluğu görüntüle|Boşlukları Kabarık noktalar olarak, sekmeleri oklar olarak görüntüler. Bir dosyanın sonu dikdörtgen bir simge olarak görüntülenir. Varsa **sözcük kaydırma için Araçlar/Seçenekler/metin düzenleyici Languages/Word Wrap/Show görünür glyph'leri** olduğu belirlenirse, o glyph de gösterilir.|  
|Sözcük kaydırma|Tüm satırların kod penceresinde görünür olmasını belgeye neden olur. Sözcük kaydırmayı metin düzenleyici tüm diller ayarlarında kapatıp açabilirsiniz (**Araçlar/Seçenekler/metin düzenleyici dilleri**).|  
|Seçimi işletilir satıra Çevir|Seçime veya geçerli satıra yorum karakterleri ekler.|  
|Seçimi açıklama satırı yap|Seçimden veya geçerli satıra yorum karakterleri kaldırır.|  
|Satır Girintisini Artır|Bir sekme (veya eşdeğer boşluk) seçilen satırlardan veya geçerli satırı ekler.|  
|Satır girintisini Azalt|Bir sekme (veya eşdeğer boşluk) seçilen satırlardan veya geçerli satırı kaldırır.|  
|Etiket Seç|Etiket (örneğin, XML veya HTML) içeren bir belgede etiket seçilir.|  
|Etiket içeriğini Seç|Etiket (örneğin, XML veya HTML) içeren bir belgede içerik seçilir.|  

## <a name="navigate-in-the-code-window"></a>Kod penceresinde gezinme  
 Bir belge içinde birkaç farklı şekilde dolaşabilirsiniz. Standart işlemlere ek olarak kullanabileceğiniz **Navigate Backward** (veya CTRL + eksi) ve **Navigate Forward** (CTRL + SHIFT + eksi) ekleme için araç çubuğundaki düğmeler önceki noktası konumları veya etkin belgede daha fazla güncel konuma dönmek. Bu düğmeler, ekleme noktasının son 20 konumunu korur.  

 ![İleri ve geri gezinti düğmeleri](../ide/media/vs2015-nav-buttons.png "VS2015_Nav_buttons")  

 Kodunuzun kuş bakışı görünümünü almak için bir kod penceresinde Gelişmiş kaydırma çubuğunu da kullanabilirsiniz. Harita modunda kod önizlemeler imleç Yukarı Taşı ve aşağı kaydırma çubuğunun, daha fazla bilgi için bkz, bkz: [nasıl yapılır: izleme kaydırma çubuğunu özelleştirerek kodunuzu](../ide/how-to-track-your-code-by-customizing-the-scrollbar.md).  

 Aşağıdaki komutlar, koda özgü Gezinti yöntemleridir:  

|||  
|-|-|  
|Git \<satır numarası >|(**Düzenle/Git** ya da CTRL + G): Etkin belgede belirli bir satıra taşıyın.|  
|Gidin|(**Düzenle/Git** ya da CTRL +,): etkin bir çözümde sembol veya dosya bulur. Eşleşen sorgu sonuçlarından düzgün bir küme seçmenize yardımcı olur. Sembolü anahtar sözcüklere bölmek için camel casing ve alt çizgi karakterleri kullanarak bir sembol içinde bulunan anahtar sözcükleri arayabilirsiniz.|  
|Tüm Başvuruları Bul|(bağlam menüsü): çözümde seçilen öğenin tüm başvurularını bulur.|  
|Tanıma Git|(bağlam menüsü veya F12): seçilen öğenin açıklamasını bulur.|  
|Tanıma göz at|(bağlam menüsü veya Alt + F12): seçilen öğenin açıklamasını bulur ve açılır pencerede görüntüler. Daha fazla bilgi için [nasıl yapılır: görünümü ve düzenleme kodu kullanarak Özet tanım (Alt + F12) tarafından](../ide/how-to-view-and-edit-code-by-using-peek-definition-alt-plus-f12.md).|  
|Sonraki yöntem, önceki yöntem|(**Düzenle/sonraki yöntem, önceki yöntem**) Visual Basic kod dosyaları, bu komutlar ekleme noktasını farklı yöntemlere kullanın.|  
|Başvuru vurgulama|Kaynak koddaki bir simge tıkladığınızda, o simgenin tüm örnekleri belgede vurgulanır. Vurgulanan simgeler bildirimleri ve başvurular içerebilir ve diğer pek çok simgeyi **tüm başvuruları Bul** döndürür. Bu sınıf, nesneler, değişkenler, yöntemleri ve özellik adlarını içerir. Visual Basic kodu içinde birçok denetim yapıları için anahtar sözcükler ayrıca vurgulanır. Sonraki veya önceki vurgulanan simgeye gitmek için CTRL + SHIFT + Aşağı Ok veya CTRL + SHIFT + Yukarı Ok tuşuna basın. Vurgulama rengini değiştirebilirsiniz **Araçlar/Seçenekler/ortam/yazı tipi ve renk/vurgulanan başvuru.**|  
|Kodla ilgili bilgiyi bulun|Değişiklikleri ve bu değişiklikler, başvurular, hatalar, iş öğeleri, kod incelemeleri ve birim test durumu, Kod Düzenleyicisi'nde CodeLens kullandığınızda kimin yaptığını gibi belirli kod hakkında bilgi bulabilirsiniz. Team Foundation Server ile Visual Studio Enterprise kullandığınızda CodeLens ekran gibi çalışır. Bkz: [kod değişikliklerini ve diğer geçmişi bulma](../ide/find-code-changes-and-other-history-with-codelens.md).|  

 Ayrıca **gezinti çubuğu**, diğer bir deyişle, görüntülenen bir kod dosyasına gitmek için kod penceresinin üstünde iki açılır liste kutusu. Bu çubuk doğrudan belirli bir tür veya bir tür içindeki üyelerden birine gitmenizi sağlar. Visual Basic, C# ve C++ kod dosyaları ile gezinti çubuğu görünür.  

 Gezinti çubuğunu gizlemek için değiştirin **gezinti çubuğu** seçeneği metin düzenleyici tüm diller ayarlarında (**Araçlar/Seçenekler/metin düzenleyici diller**, veya kişi için ayarları değiştirebilirsiniz diller için). Açılır liste kutularında aşağıdaki gibi gezinebilirsiniz:  

- Odağı kod penceresinden Gezinti çubuğuna geçirmek için CTRL + F2 kısayol tuş bileşimine basın.  

- Odağı gezinti çubuğundan kod penceresine dönmek için ESC tuşuna basın.  

- Odağı gezinti çubuğunda öğeden öğeye kaydırmak için TAB tuşuna basın.  

- IDE'ye dönün ve odaktaysa gezinti çubuğu öğesini seçmek için ENTER tuşuna basın.  

- Bir sınıf veya türe gitmek için soldaki aşağı açılır menüde adını tıklayın.  

- Bir sınıftaki bir yordama doğrudan gitmek için sağdaki aşağı açılır menüde bir prosedürü tıklayın.  

  Kısmi class içinde geçerli kod dosyası dışında tanımlanan üyeler gri renkte.  

## <a name="find-code-using-navigate-to"></a>Gezinmek için kullanarak kod bulma
Visual Studio'nun "Gitmek için" komut belirtilen öğeleri, kod dosyaları, dosya yolları ve kod sembolleri hızlı bir şekilde bulmanıza yardımcı olmak için kodunuzun odaklanmış bir arama yapar. Aramaları gibi bulun veya dosyalarda Bul diğer metin, gezinmek için arama, dosyalar, formlar ve kod modülleri gibi gerçek kod burada bulunduğu alanlara sınırlar. Örneğin, araması yaparsanız bir ASP.NET web uygulamasını kullanarak bir dize bulun veya dosyaları bulma içinde tüm çözümde kod açıklamalarını, dizenin örnekleri dahil olmak üzere çeşitli isabet alabilirsiniz. Gezinmek için kullanarak, ancak, yalnızca tek bir işlev kodu açıklamalar dizesinde'nın tüm örneklerini yok sayılıyor alabilirsiniz.

### <a name="navigate-code-using-navigate-to"></a>Git kullanarak kod gidin

1. Visual Studio'da bir çözüm ya da klasörü açın.
1. Ana menüsünde **Düzenle**, **gitmek için**, veya basın **CTRL +,**.

    Kod Düzenleyicisi üst köşede küçük bir metin kutusu görünür.
1. Metin kutusuna bulmak istediğiniz kod öğe adı girin.

    ![Gezinmek için pencere](../ide/media/vside-navigatetowindow.png "gitmek için penceresi")

    Siz yazarken, sonuçları bir açılan listedeki metin kutusunun altında görüntülenir.
1. Bir öğeye gitmek için listeden seçin.


### <a name="filter-your-search"></a>Aramanızı filtreleyin

Yalnızca Simgeler kodu için arama sınırlamak için gitmek için sorgu ile yazdığınızdan bir "@" karakteri. Örneğin, arama `@application`, gezinmek için görüntüler, örneğin, yalnızca "uygulama" sözcüğünü içeren sınıflar.

Kodunuzda camel casing kullanır, yalnızca büyük harf kod öğe adı girerek kod öğeleri daha hızlı bir şekilde bulabilirsiniz. Örneğin, kodunuzu adlı bir bileşen varsa `ViewSwitcher`, yalnızca büyük harf adı girerek bulabilirsiniz (`"VS"`) giderek penceresinde.

![Pencere gitmek için büyük harf ile arama -](../ide/media/vside-capitalsearch.png "penceresi gitmek için büyük harf ile arama -")

Bu özellik, uzun adları kodunuz varsa, özellikle yararlı olur.

## <a name="customize-the-editor"></a>Düzenleyiciyi özelleştirme  
 **İçeri ve dışarı aktarma ayarları**: başka bir paylaşım ayarlarını, ayarlarınızı standarda ya da kullanarak Visual Studio varsayılan ayarlarına geri döndürmeye **içeri ve dışarı aktarma ayarları Sihirbazı** üzerinde **Araçları** menüsü. Genel ayarları veya dili ve projeye özgü ayarları değiştirebilirsiniz.  

 **Klavye eşleme**: Yeni kısayol tuşlarını tanımlayabilir veya varolanları Araçlar/Seçenekler/ortam/klavye ayarları yeniden tanımlama. Kısayol tuşları hakkında daha fazla bilgi için bkz. [varsayılan klavye kısayolları](../ide/default-keyboard-shortcuts-in-visual-studio.md).  

 Dile özgü Düzenleyici seçenekleri hakkında daha fazla bilgi için aşağıdakilere bakın:  

-   [Visual Basic ayarları](http://msdn.microsoft.com/library/2712b3b1-18f2-430c-ae91-28468bbf5f32)  

-   [C# için Visual Studio Geliştirme Ortamını Kullanma](../csharp-ide/using-the-visual-studio-development-environment-for-csharp.md)  

-   [Seçenekler, Metin Düzenleyici, JavaScript, Biçimlendirme](../ide/reference/options-text-editor-javascript-formatting.md)  

## <a name="in-this-section"></a>Bu bölümde  

-   [Metin Bulma ve Değiştirme](../ide/finding-and-replacing-text.md)  

-   [Kodlamalar ve Satır Sonları](../ide/encodings-and-line-breaks.md)  

-   [Anahat Oluşturma](../ide/outlining.md)  

-   [Yeniden Düzenleme](../ide/refactoring-in-visual-studio.md)  

-   [Üretkenlik İpuçları](../ide/productivity-tips-for-visual-studio.md)  

-   [IntelliSense Kullanma](../ide/using-intellisense.md)  

-   [Düzenleyiciyi Özelleştirme](../ide/customizing-the-editor.md)  

-   [Nasıl Yapılır: Kaydırma Çubuğunu Özelleştirerek Kodunuzu İzleme](../ide/how-to-track-your-code-by-customizing-the-scrollbar.md)  

-   [Nasıl yapılır: Özet Tanımı'nı Kullanarak Kodu Görüntüleme ve Düzenleme (Alt+F12)](../ide/how-to-view-and-edit-code-by-using-peek-definition-alt-plus-f12.md)  

-   [Ampullerle hızlı eylemler gerçekleştirme](../ide/perform-quick-actions-with-light-bulbs.md)  

-   [Kod Parçacıkları](../ide/code-snippets.md)  

-   [Araç Kutusunu Kullanma](../ide/using-the-toolbox.md)  

-   [Kod Yapısını Görüntüleme](../ide/viewing-the-structure-of-code.md)  

-   [Kodda Yer İşaretleri Ayarlama](../ide/setting-bookmarks-in-code.md)  

-   [Görev Listesini Kullanma](../ide/using-the-task-list.md)  

-   [Kod değişikliklerini ve diğer geçmişi bulma](../ide/find-code-changes-and-other-history-with-codelens.md)  

## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual Studio IDE](../ide/visual-studio-ide.md)


