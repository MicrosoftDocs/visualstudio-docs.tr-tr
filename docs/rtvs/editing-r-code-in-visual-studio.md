---
title: R kodunu Düzenle
description: Visual Studio, tüm özellikleri ve uzantıları kullanabilme korurken, R için özel olarak uyarlanmış bir düzenleme deneyimi sağlar.
ms.date: 11/05/2018
ms.prod: visual-studio-dev15
ms.technology: vs-rtvs
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: douge
ms.workload:
- data-science
ms.openlocfilehash: c1d44e6d316db2ddce799784169a11a06578fe7f
ms.sourcegitcommit: bccb05b5b4e435f3c1f7c36ba342e7d4031eb398
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/06/2018
ms.locfileid: "51220885"
---
# <a name="edit-r-code-in-visual-studio"></a>Visual Studio'da R kodunu Düzenle

R araçları için Visual Studio (RTVS) Visual Studio düzenleme özellikleri ve uzantıları kullanabilme korurken deneyimi R için özel olarak belirlenmek. (VIM tuş bağlamaları tercih ederseniz, örneğin, ücretsiz yükleyebileceğiniz [VsVim uzantısı](https://marketplace.visualstudio.com/items?itemName=JaredParMSFT.VsVim) Visual Studio Market'ten.)

Bu makalede özelliklerin yanı sıra, ayrıca bkz: [IntelliSense](r-intellisense.md), [linting](linting-r-code.md), [kod parçacıkları](code-snippets-for-r.md), ve [R Markdown](rmarkdown-with-r-in-visual-studio.md).

## <a name="syntax-highlighting"></a>Söz dizimi vurgulama

Kodunuzu dizeleri, açıklamalar ve anahtar sözcükler gibi farklı kısımlarını renklendirme yanı sıra RTVS ayrıca vurgular ve açıklamalarındaki bağlantılar sağlar:

![Sözdizimi renklendirme için R kodu](media/editing-syntax-colors.png)

Yazı tipleri ve belirli vurgu renkleri özelleştirmek için işaretleyin **Araçları** > **seçenekleri** komutu, gitmek **ortam**  >  **Yazı tipleri ve renkler**, ardından R ile ilgili öğeleri ayarlarını değiştirme **görüntü öğeleri** kutusunda:

![Yazı tipi ve renk seçeneklerini R kodu](media/editing-syntax-colors-options.png)

Visual Studio Düzenleyicisi söz dizimi hataları da çizmeyeceğini:

![R kodu vurgulama söz dizimi hatası](media/editing-syntax-error.png)

Bu davranışı değiştirmek için bkz: **Gelişmiş** > **sözdizimi denetimi** bölümündeki [Düzenleyici Seçenekleri](#editor-options).

## <a name="edit-and-organize-code"></a>Düzenleme ve kod düzenleme

Kod yazarken RTVS otomatik tamamlama üzerinde açıklandığı şekilde sağlar [IntelliSense](r-intellisense.md) sayfası. Ayrıca, otomatik biçimlendirme küme ayraçları ve ayraç tamamlama gibi yapar: 

![Satır içi biçimlendirme animasyon](media/editing-inline-formatting.gif)

Aktardığınızda genellikle çok sayıda parametreye sahip işlevler çağrıları yazarken, kodun okunmasını kolaylaştırmak için parametreleri satır istiyorsunuz. RTVS girinti parametreleri kümenize hatırlar ve otomatik olarak bu girintileme sonraki satırlar için geçerlidir:

![Otomatik girintili yazma animasyonu](media/editing-auto-indentation.gif)

Bu davranışı değiştirmek için bkz: [Düzenleyici Seçenekleri](#editor-options) için **sekmeleri** grubu.

Daraltılabilir kod bölgeleri, Kod Düzenleyicisi'nde parçası geçici olarak gizleyebilirsiniz sağlar. Visual Studio oluşturur çeşitli bölgelere sizin için otomatik olarak, çok satırlı ifadeleri sunamıyoruz sürece **Gelişmiş** > **anahat** > **anahat oluşturma kodu**  seçeneği Off olarak ayarlanır.

İle biten yorumlarla istediğiniz kodu kendi saran bir bölge oluşturmak için `---`. Küçük kod solundaki denetimleri +/-ardından genişletip daraltabilirsiniz bölgeleri sağlar:

![Yorumlarla daraltılabilir bir bölge oluşturma](media/editing-collapsible-regions.gif)

Tuşuna bastığınızda varsayılan olarak, Visual Studio boşluk ekler. **sekmesini** anahtarı. Üzerinde açıklandığı şekilde yeniden bu davranışı değiştirebilirsiniz [seçenekler, metin düzenleyici sekmelerini](../ide/reference/options-text-editor-all-languages.md).

## <a name="code-navigation"></a>Kod Gezintisi

Kod Gezintisi, R programınızı kitaplıklarını ve kaynak koduna hızlı erişim sağlar. Bu özellikleri el ile kodunuzu arama yapmak zorunda yerine iş akışında tutun.

**Tanıma Git** hızla atlayan bir işlev tanımı ya da bir kitaplığı işlevin kaynak kodunu okumak için bir satır içi kısa bir Düzenleyicisi açılır. Yalnızca işlevi faiz ve seçin, sağ **tanıma**, veya işlev ve ENTER tuşuna imleci **F12**.

Bu komut, işlevin kaynak kodunu içeren yeni bir düzenleyici penceresi açılır. İmleç rahatça işlev tanımının başında yer alır.

**Özet tanım**, çağrılan sağ tıklatma menüsünden veya **Alt**+**F12**, aşağıdaki işlevin kaynak kodunu içeren bir salt okunur, kaydırılabilir bölge ekler işlev çağrısı:

![Animasyon için Özet tanımı](media/editing-peek-definition.gif)

## <a name="send-code-to-the-interactive-window"></a>Kod etkileşimli pencereye Gönder

Birçok geliştiricinin düzenleyicide kod yazma ve daha sonra bu kodu göndermek ister [etkileşimli pencere](interactive-repl-for-r-in-visual-studio.md) hemen testi (okuma-değerlendirme-Print-Loop veya REPL olarak da bilinir). Tuşuna basarak **Ctrl**+**Enter** R Düzenleyicisi kod geçerli satırı etkileşimli pencereye gönderir ve ardından imleci sonraki satırda yerleştirir. İle **Ctrl**+**Enter**, daha sonra etkili bir şekilde kodunuzda düzenleyiciden geçebilirsiniz.

Kod ve ENTER tuşuna de seçebilirsiniz **Ctrl**+**Enter** tüm bu seçim uygulamak için. Alternatif olarak, seçime sağ tıklayın ve **etkileşimli içinde Yürüt**.

## <a name="format-code"></a>Kodu biçimlendirme

Visual Studio'nun otomatik biçimlendirme, kod yanı sıra kodu tercihlerinize göre kümesi olarak biçimlendirilmiş düzenleyicisine yapıştırın, Yaz tutar. Ayrıca, seçim yapabileceğiniz sağ tıklatın ve seçin **seçimi Biçimlendir** (**Ctrl**+**K**,**F**) bu uygulamak için tercihleri. Örneğin, bir işlev tanımı tümü tek bir satıra tablonuz varsa:

```R
f<-function  (a){  return(a + 1) }
```

Biçimlendirme uygulamak, olacak şekilde temizler:

```R
f <- function(a) { return(a + 1) }
```

Bütün kod dosyasını yeniden biçimlendirmek için işaretleyin **Düzenle** > **Gelişmiş** > **belgeyi Biçimlendir** (**Ctrl** + **E**,**D**).

Otomatik biçimlendirme Al. geri alınabilecek ayrı bir işlemdir. Örneğin, Kod Düzenleyicisi ve biçimlendirme, geçerli yapıştırırsanız, seçerek **Düzenle** > **geri** ya basarak **Ctrl** + **Z** biçimlendirme; bir kez tersine ikinci **geri** Yapıştır tersine çevirir.

Biçimlendirme seçenekleri (biçimlendirmeyi devre dışı bırakma dahil) aracılığıyla ayarlanır **Araçları** > **seçenekleri** üzerinde **metin düzenleyici**  >  **R** > **Gelişmiş** sekmesi. Doğrudan herhangi birini kullanarak bu sayfasına gidebilirsiniz **R Araçları** > **Düzenleyici Seçenekleri** komutu veya göre Düzenleyicisi'nde sağ tıklayıp **biçimlendirme seçenekleri**. Bkz: [Düzenleyici Seçenekleri](#editor-options) ayrıntıları bölümü.

## <a name="inserting-roxygen-comments"></a>Roxygen açıklamaları ekleme

RTVS oluşturmak için bir kısayol sağlar [Roxygen](http://roxygen.org/) bir işlevin parametre adları kullanarak yorumlar. Yazmanız yeterlidir `###` işlev tanımı üzerinde boş bir satıra:

![Animasyon Roxygen açıklama ekleme](media/editing-roxygen-comments.gif)

## <a name="editor-options"></a>Düzenleyici Seçenekleri

Düzenleyici özgü seçenekleri aracılığıyla ayarlanır **Araçları** > **seçenekleri** giderek komutu **metin düzenleyici** > **R**, kısayol komutunu kullanmadan veya **R Araçları** > **Düzenleyici Seçenekleri**.

Seçeneklerinden **genel**, **kaydırma çubukları**, ve **sekmeleri** sekmeleri R özel değildir, ancak bunun yerine genel Visual Studio ayarları tüm diller için kullanılabilir, ancak üzerinde uygulanan bir Dil başına temel. Ayrıntılar için aşağıdaki makalelere bakın:

- [Seçenekler, Metin Düzenleyici, Tüm Diller](../ide/reference/options-text-editor-all-languages.md)
- [Kaydırma çubuğunu özelleştirerek, kodunuzu izleme](../ide/how-to-track-your-code-by-customizing-the-scrollbar.md)
- [Seçenekler, metin düzenleyici, sekmeler](../ide/reference/options-text-editor-all-languages-tabs.md)

Seçeneklerinden **R** > **Gelişmiş** RTVS için sekmesinde özeldir:

| Grup | Seçenek | Varsayılan | Açıklama |
| --- | --- | --- | --- |
| Biçimlendirme | Otomatik biçimlendirme | Açık | Yazarken kodu yeniden biçimlendirir. Etkilemez **seçimi Biçimlendir** veya **belgeyi Biçimlendir** komutları. |
| | Genişletilmiş küme ayraçları | Kapalı | {Yeni bir satıra. açık yerleştirir |
| | Yapıştırma sırasında Biçimlendir | Açık | Yapıştırırken biçimlendirmeyi uygular. |
| | Biçim kapsamına} | Açık | Kapanış yazdıktan sonra biçimleri} kapsamı. |
| | Virgülden sonra boşluk | Açık | Virgüllerden sonra boşluk yerleştirir. |
| | Anahtar sözcüğü sonra boşluk | Açık | Anahtar sözcükler ister sonra bir boşluk yerleştirir `if`, `while`, ve `repeat`. |
| | {Önce boşluk | Açık | Önce bir boşluk yerleştirir ve açma {. |
| | Alanları kolem znaku = | Açık | Eşittir işareti etrafındaki boşlukları yerleştirir. |
| IntelliSense | ' ENTER tuşuna işleme | Kapalı | Otomatik Tamamlama seçimi tamamlar olduğunda **Enter** basıldığında. |
| | Anahtar alanı tamamlama | Kapalı | Otomatik Tamamlama seçimi tamamlar olduğunda **alanı** basıldığında.|
| | Tamamlama listesinde ilk karakteri | Açık | Tamamlanma listesi üzerinde ilk karakter türleri gösterir. Kapalı olduğunda içeren tamamlanma listesi görüntülenir **Düzenle** > **IntelliSense** > **üyeleri Listele** (**Ctrl** + **J**). |
| | Tamamlama listesinde **sekmesini** anahtarı | Kapalı | Bir veya daha fazla karakter yazarak ve basarak tamamlanma listesi çağırır **sekmesini**. |
| | Eşleşen bağımsız değişken adları kısmen türleri | Kapalı | Bir işlev çağrısında bağımsız değişken adlarını yazarak, imza Yardımı en iyi eşleşme olan bağımsız değişken için bir açıklama gösterir. |
| Etkileşimli pencere | Kontrola syntaxe v Konzole R | Kapalı | Söz dizimi etkileşimli pencerede denetimi için geçerlidir. Söz dizimi denetimini, çok satırlı ifadeleri ile doğru şekilde çalışmayabilir. | 
| Anahat Oluşturma | Anahat oluşturma kodu | Açık | Çok satırlı ifadeleri gibi alanlar için daraltılabilir bölgeleri otomatik olarak oluşturur. |
| Sözdizimi denetimi | Zobrazovat chyby syntaxe | Açık | Otomatik söz dizimi kod denetimi sağlar. |
