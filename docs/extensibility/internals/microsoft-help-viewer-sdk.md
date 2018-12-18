---
title: Microsoft Yardım Görüntüleyicisi SDK'sı | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: 620d7dcd-d462-475e-a449-fbfa06ff12c5
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: af324b141815813aec9eaadfcd9982689fdeb467
ms.sourcegitcommit: e481d0055c0724d20003509000fd5f72fe9d1340
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/05/2018
ms.locfileid: "51000353"
---
# <a name="microsoft-help-viewer-sdk"></a>Microsoft Yardım Görüntüleyicisi SDK’sı

Bu makale, Visual Studio Yardım Görüntüleyicisi Tümleştiriciler için aşağıdaki görevleri içerir:

-   Bir konu (F1 desteği) oluşturma

-   Yardım Görüntüleyici içeriği marka paket oluşturma

-   Makale bir kümesi dağıtma

-   Visual Studio Kabuğu (tümleşik veya yalıtılmış) için ekleme Yardımı

-   Ek Kaynaklar

### <a name="creating-a-topic-f1-support"></a>Bir konu (F1 desteği) oluşturma
Bu bölümde sunulan bir konu, konunun gereksinimleri, işlenmiş sonucuyla (F1 destek gereksinimleri dahil) konu ve son olarak, bir örnek konusu oluşturma için kısa bir açıklama Bileşenleri'ne genel bakış sağlar.

**Yardım Görüntüleyici konusuna genel bakış**

İşleme için bir konu çağrıldığında, Yardım Görüntüleyicisi'ni yükleme veya XHTML, konu yanı sıra son güncelleştirme zaman konu ile ilişkili olan marka paket öğeleri alır ve sunulan içerik Görünümü'nde neden iki birleştirir (veri marka + Konu veri).  Marka paket, logolar, içerik davranışları ve marka metni (telif hakkı, vs.) için destek içerir.  "Markası paket oluşturma" marka paket öğeleri hakkında daha fazla bilgi için aşağıya bakın.  Yoktur olay konu ile ilgili hiçbir marka paket, Yardım Görüntüleyici Yardım Görüntüleyicisi'ni uygulama (US.mshc Branding_en) kökünde geri dönüş marka paketi kullanır.

**Yardım Görüntüleyicisi konu gereksinimleri**

Yardım Görüntüleyici içinde doğru işlenmek üzere ham konu içeriği W3C temel 1.1 XHTML olması gerekir.

Bir konu genellikle iki bölüm içerir:

-   Meta veri (içerik meta veri başvurusu bakın): konu, örneğin, konu benzersiz kimliği, anahtar değeri, içindekiler tablosu kimliği, konu hakkında daha fazla veri üst düğüm kimliği, vs.

-   Gövde içeriği: uyumlu W3C temel 1.1 XHTML ile içeren içerik davranışları (daraltılabilir alan, kod parçacığı, vb. desteklenen Tam bir listesi aşağıda gösterilmiştir).

Visual Studio markalama paket denetimleri desteklenir:

-   Bağlantılar

-   CodeSnippet

-   CollapsibleArea

-   Devralınan üye

-   LanguageSpecificText

Desteklenen dil dizeleri (büyük/küçük harfe duyarlı değil):

-   JavaScript

-   CSharp veya c#

-   cplusplus visualc ++ ya da c ++

-   JScript

-   VisualBasic veya vb

-   f # veya fsharp veya fs

-   diğer - dil adını temsil eden bir dize

**Yardım Görüntüleyicisi'konusu oluşturuluyor**

ContosoTopic4.htm adlı yeni bir XHTML belge oluşturun ve başlık etiketi (aşağıda) içerir.

```html
<html>
<head>
<title>Contoso Topic 4</title>
</head>

<body>

</body>
</html>

```

Ardından, nasıl konu (kendi veya markalı), sunulacak nasıl tanımlamak için veri ekleme F1, Kimliğini (için diğer konulara bağlantı başvuruyla) TOC içinde konunun mevcut olduğu için bu konuda başvurmak için vs.  Desteklenen meta verileri tam listesi için aşağıdaki "İçerik meta verileri" tabloya bakın.

-   Bu durumda, kendi marka paket, Visual Studio Yardım Görüntüleyicisi markalama paketinin bir değişken kullanacağız.

-   F1 meta adı ve değeri ekleyin ("Microsoft.Help.F1" içerik "ContosoTopic4" =) IDE özellik paketinde sağlanan F1 değer eşleşir.  (Daha fazla bilgi için F1 destek bölümüne bakın.)   Bu için F1'e eşleşen değerdir IDE'de F1 seçildiğinde, bu konuda görüntülemek için IDE içinde arama öğesinden.

-   Konu kimliği Ekle Diğer konular tarafından bu konuya bağlanmak için kullanılan dize budur.  Bu konuda Yardım Görüntüleyici kimliği var.

-   TOC için bu konuda İçindekiler düğümü nerede görüneceğini tanımlamak için bu konunun üst düğüm ekleyin.

-   TOC için bu konunun düğüm sırası ekleyin. N alt düğüm sayısı üst düğüme sahip olduğunda, alt düğümleri sırasına göre bu konunun konumunu tanımlayın. For example, bu konu başlığı altında 4 4 alt konuları sayısıdır.)

Örnek meta veriler bölümü:

```html
<html>
<head>
<title>Contoso Topic 4</title>

<meta name="SelfBranded" content="false" />
    <meta http-equiv="Content-Type" content="text/html; charset=UTF-8" />
    <meta name="Microsoft.Help.Id" content="ContosoTopic4" />
<meta name="Microsoft.Help.F1" content=" ContosoTopic4" />
    <meta name="Language" content="en-us" />
<meta name="Microsoft.Help.TocParent" content="ContosoTopic0" />
<meta name="Microsoft.Help.TocOrder" content="4" />

</head>

<body>

</body>
</html>

```

**Konu gövdesi**

Konu gövdesi (üstbilgi ve altbilgi dahil değil) sayfa bağlantılarının, Not bölümü, daraltılabilir bir alan, bir kod parçacığı ve dile özgü metnin bir bölümünü içerir.  Bu alanların hakkında bilgi sunulan konunun marka bölümüne bakın.

1.  Bir konu başlığı etiketi ekleyin:  `<div class="title">Contoso Topic 4</div>`

2.  Bir not bölümüne ekleyin: `<div class="alert"> add your table tag and text </div>`

3.  Daraltılabilir bir alan ekleyin:  `<CollapsibleArea Expanded="1" Title="Collapsible Area Test Heading"> add text  </CollapsibleArea>`

4.  Bir kod parçacığını ekleyin:  `<CodeSnippet EnableCopyCode="true" Language="CSharp" ContainsMarkup="false" DisplayLanguage="C#" > a block of code </CodeSnippet>`

5.  Dile özgü metin kodu ekleyin: `<LanguageSpecificText devLangcs="CS" devLangvb="VB" devLangcpp="C++" devLangnu="F#" />` unutmayın `devLangnu=` diğer diller girmenizi sağlar. Örneğin, `devLangnu="Fortran"` Fortran görüntüler, kod parçacığı DisplayLanguage Fortran =

6.  Sayfa bağlantılarının ekleyin: `<a href="ms-xhelp://?Id=ContosoTopic1">Main Topic</a>`

> [!NOTE]
>  Not: için desteklenmeyen yeni "Görüntüleme dilini" (örneğin, F#, Cobol, Fortran) kod parçacığında kod renklendirme, tek renkli olacaktır.

**Yardım Görüntüleyicisi konuya örnek** kod meta verileri, bir kod parçacığı, daraltılabilir alan ve dile özgü metin nasıl tanımlanacağını göstermektedir.

```html
<?xml version="1.0" encoding="utf-8"?>
<html>
<head>
<title>Contoso Topic 4</title>

    <meta http-equiv="Content-Type" content="text/html; charset=UTF-8" />
    <meta name="Microsoft.Help.Id" content="ContosoTopic4" />
<meta name="Microsoft.Help.F1" content=" ContosoTopic4" />
    <meta name="Language" content="en-us" />
<meta name="Microsoft.Help.TocParent" content="ContosoTopic0" />
<meta name="Microsoft.Help.TocOrder" content="4" />
<meta name="SelfBranded" content="false" />
</head>

<body>
<div class="title">Contoso Topic 4</div>

  <div id="header">
<table id="bottomTable" cellpadding="0" cellspacing="0"  width="100%">
        <tr id="headerTableRow2"><td align="left">
            <span id="nsrTitle">Contoso Topic 1</span>
          </td>
<td align="right">
</td></tr>
<tr id="headerTableRow1"><td align="left">
            <span id="runningHeaderText">Contoso Widgets & Sprockets</span>
          </td></tr>
      </table>
</div>

<h2>Table of Contents</h2>

<ul class="toc">
<li class="tocline1"><a href="#introduction" target="_self">1.0 Introduction</a></li>
<li class="tocline1"><a href="#seealso" target="_self">See Also</a></li>
</ul>

<div class="topic">

<div id="mainSection">
<div id="mainBody">

<a name="introduction"></a>
<h2>1.0 Introduction</h2>
<p>[This documentation is for sample purposes only.]</p>

<p>Contoso Topic 1 contains examples of:
<ul>
<li>Collapsible Area</li>
<li>Bookmark ("See also")</li>
<li>Code Snippets from Branding Package</li>
</ul>
 </p>
<div class="alert"><table><tr><th>
<strong>Note </strong></th></tr>
<tr><td>
<p>This is an example of a <span class="label">Note </span>section.
Call out important items for your reader in this <span class="label">Note </span>box.
</p></td></tr>
</table>
</div>
</div>

<CollapsibleArea Expanded="1" Title="Collapsible Area Test Heading">

            <a id="sectionToggle0"><!----></a>

<div>
Example of Collapsible Area
<br/>
Lorem ipsum dolor sit amet...
</div>
</CollapsibleArea>

<div id="snippetGroup" >
<CodeSnippet EnableCopyCode="true" Language="VisualBasic" ContainsMarkup="false" DisplayLanguage="Visual Basic" >
Private Sub ToolStripRenderer1_RenderGrip(sender as Object, e as ToolStripGripRenderEventArgs) _ Handles ToolStripRenderer1.RenderGrip
Dim messageBoxVB as New System.Text.StringBuilder()
    messageBoxVB.AppendFormat("{0} = {1}", "GripBounds", e.GripBounds)
    messageBoxVB.AppendLine()
 ...
    MessageBox.Show(messageBoxVB.ToString(),"RenderGrip Event")
End Sub
</CodeSnippet>

<CodeSnippet EnableCopyCode="true" Language="CSharp" ContainsMarkup="false" DisplayLanguage="C#" >
private void ToolStripRenderer1_RenderGrip(Object sender, ToolStripGripRenderEventArgs e)
{
System.Text.StringBuilder messageBoxCS = new System.Text.StringBuilder();
messageBoxCS.AppendFormat("{0} = {1}", "GripBounds", e.GripBounds );
messageBoxCS.AppendLine();
...
MessageBox.Show(messageBoxCS.ToString(), "RenderGrip Event" );
}
</CodeSnippet>

<CodeSnippet EnableCopyCode="true" Language="fsharp" ContainsMarkup="false" DisplayLanguage="F#" >
some F# code
</CodeSnippet>
</div>

<h4 class="subHeading">Example of code specific text</h4>Language = <LanguageSpecificText devLangcs="CS" devLangvb="VB" devLangcpp="C++" devLangnu="F#" />

<a name="seealso"></a>
<h1 class="heading">See Also</h1>

    <div id="seeAlsoSection" class="section">
    <div class="seeAlsoStyle">
        <a href="ms-xhelp://?Id=ContosoTopic1">Main Topic</a>
    </div>
 </div>
</div>
</div>
</body>
</html>
```

**F1 desteği**

Visual Studio'da F1 imleci IDE içinden yerleşimini gelen sağlanan değerler oluşturmaktadır seçip "(İmleç konumuna göre. bir özellik paketi" sağlanan değerlerle doldurur Özellik x imleci x özellik üzerinde olduğunda, etkin/odağını ve özellik paketi değerlerle doldurur.  F1 seçildiğinde özellik paketi doldurulur ve Visual Studio F1 kod görünür müşteriler varsayılan Yardım kaynak yerel veya çevrimiçi olup olmadığını görmek için (çevrimiçi varsayılandır), ardından ayarı kullanıcı temelli uygun bir dize oluşturur (varsayılan çevrimiçi) - Kabuğu Yürüt (bkz. Yardım yönetici başlatma parametreleri kılavuzu için exe) için yerel Yardım Görüntüleyici + yerel Yardım varsayılan veya parametre listesinde anahtar sözcüğü ile MSDN URL'si ise özellik paketi dan fazlasının parametrelere sahip.

Birden çok değerli dize olarak, ilk terimi, arama için isabet, yararlanmak için üç dizeleri için F1'e döndürdüyse denir ve bulunan hazırız, Aksi halde, sonraki dize taşıyın.  Sırası önemlidir. Birden çok değerli anahtar sözcükleri sunumu kısa dize için en uzun dize olmalıdır.  Bu durumda birden çok değerli anahtar sözcükler için doğrulamak için seçilen anahtar sözcüğü içeren çevrimiçi F1 URL dizesinin arayın.

Böylece kullanıcının ayarı için çevrimiçi olduysa, ardından biz yalnızca F1 isteği doğrudan çevrimiçi sorgu hizmetimiz MSDN Kitaplığı Yardım Aracısı yönlendirme yerine geçirilen Visual Studio 2012'de isteyerek daha güçlü bir bölme çevrimiçi ve çevrimdışı olarak arasında yaptık. Visual Studio 2010'da vardı. Biz ardından kullanan bir durumunu "yüklü satıcı içeriği = true" Bu bağlamda farklı bir şey belirlemek için. TRUE ise, ardından, müşterileriniz için desteklemek istediğiniz bağlı olarak bu ayrıştırma ve yönlendirme mantığı gerçekleştiririz. False ise, ardından şu MSDN olarak gitmeniz yeterlidir. Kullanıcının yerel ayardır, tüm çağrıları yerel Yardım Altyapısı'na gidin.

F1 Akış Diyagramı:

![F1 akış](../../extensibility/internals/media/f1flow.png "F1flow")

Ne zaman çevrimiçi (tarayıcıda başlatılacak) Yardım Görüntüleyicisi varsayılan Yardım içerik kaynağını ayarlayın:

-   Visual Studio iş ortağı (VSP) özellikleri yayma F1 özellik paketi (özellik paketi prefix.keyword ve çevrimiçi URL ön eki kayıt defterinde bulundu) bir değer: F1 gönderen bir VSP URL + parametreleri tarayıcıya.

-   Visual Studio özellikleri (dil Düzenleyicisi, Visual Studio özel menü öğeleri, vb.): F1 tarayıcıya bir Visual Studio URL gönderir.

Ne zaman yerel Yardım'a (tanıtım Yardım Görüntüleyici'de) Yardım Görüntüleyicisi varsayılan Yardım içerik kaynağını ayarlayın:

-   F1 özellik paketi arasında yerel depolama dizini anahtar sözcüğü eşleştiği VSP özellikler (yani, özellik paketi prefix.keyword = yerel depolama dizinde bulunan değeri): F1 Yardım Görüntüleyici konusundaki işler.

-   Visual Studio özellikleri (Visual Studio özelliklerinden yayılan özellik paketi geçersiz kılmak VSP seçeneği): F1 Yardım Görüntüleyicisi'nde bir Visual Studio konu işler.

F1'e geri dönüş için satıcı Yardım içeriğini etkinleştirmek için aşağıdaki kayıt defteri değerlerini ayarlayın. F1'e geri dönüş, Yardım Görüntüleyici F1 Yardımı için içerik aramak için çevrimiçi ayarlanır ve satıcı içeriği yerel olarak kullanıcıların sabit diske yüklenecek anlamına gelir. Varsayılan ayar için çevrimiçi yardıma olsa bile Yardım Görüntüleyici yerel Yardım içerik için bakmak.

1. Ayarlama **VendorContent** altındaki Yardım 2.3 kayıt defteri anahtarı değeri:

   -   32 bit işletim sistemleri için:

        HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Help\v2.3\Catalogs\VisualStudio15

        "VendorContent" = dword: 00000001

   -   64-bit işletim sistemleri için:

        HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Help\v2.3\Catalogs\VisualStudio15

        "VendorContent" = dword: 00000001

2. Ortak ad alanı için Yardım 2.3 kayıt defteri anahtarı altında kaydedin:

   - 32 bit işletim sistemleri için:

      HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Help\v2.3\Partner<em>\\< ad alanı\></em>

      "Konum"Çevrimdışı =""

   - 64-bit işletim sistemleri için:

      HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Help\v2.3\Partner<em>\\< ad alanı\></em>

      "Konum"Çevrimdışı =""

**Temel yerel Namespace ayrıştırma**

Kayıt defterinde temel yerel ad alanını ayrıştırma üzerinde etkinleştirmek için adını yazarak yeni bir DWORD değeri ekleyin: BaseNativeNamespaces ve 1 (altında desteklemek istediğiniz katalog anahtarı) değerini ayarlayın.  Örneğin, Visual Studio kataloğu kullanmak istiyorsanız, yolu anahtarı ekleyebilirsiniz:

HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Help\v2.3\Catalogs\VisualStudio15

F1 anahtar zaman üstbilgi/YÖNTEM karşılaşılanaa Biçim '/' karakteri, aşağıdaki yapısı içinde elde edilen ayrıştırılır:

-   Başlık: kayıt defterine kaydetmek için kullanılan ad olacaktır.

-   YÖNTEM: Bu aracılığıyla iletilir anahtar sözcüğü olur.

Örneğin, verilen CustomLibrary adlı özel bir kitaplık ve istek içinde gelen bir F1 olarak biçimlendirilmiş MyTestMethod, adında bir yöntem `CustomLibrary/MyTestMethod`.

Bir kullanıcı daha sonra iş ortakları hive altında bir ad alanı olarak CustomLibrary kaydetmek ve istenen hangi konuma anahtarı sağlayın ve sorguya aktarılan anahtar sözcüğü MyTestMethod olacaktır.

**Hata ayıklama aracı IDE içindeki Yardım'ı etkinleştir**

Aşağıdaki kayıt defteri anahtarı ve değeri ekleyin:

Yardım anahtar HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\15.0\Dynamic: görünen hata ayıklama çıktı perakende değer: Evet

Yardım menü öğesi altında IDE içindeki "Yardım bağlamı hata ayıklama" seçin.

**İçerik meta verileri**

Aşağıdaki tabloda, köşeli ayraç görünen herhangi bir dize tarafından tanınan bir değer değiştirilmesi gereken bir yer tutucudur. Örneğin, \<meta name="Microsoft.Help.Locale" içerik = "[dil kodu]" / >, "[dil kodu]" gerekir yerine değere göre gibi "en-us".


| Özellik (HTML gösterim) | Açıklama |
| - | - |
| \< İçerik meta name="Microsoft.Help.Locale" = "[kodu dil]" / > | Bu konu için bir yerel ayar ayarlar. Bu etiket, bir konu başlığında kullanılıyorsa, yalnızca bir kez kullanılmalıdır ve diğer tüm Microsoft Help etiketleri eklenmelidir. Bu etiket kullanılmıyorsa konunun gövde metni belirtilmişse, ürün yerel ayar ile ilişkili bir sözcük ayırıcı kullanılarak dizinlenir; Aksi takdirde, en-us Sözcük bölücü kullanıldı. Bu etiket ISOC RFC 4646 için uygundur. Microsoft Help düzgün çalıştığından emin olmak için genel dil özniteliği yerine bu özelliği kullanın. |
| \< İçerik meta name="Microsoft.Help.TopicLocale" = "[kodu dil]" / > | Bu konu için bir yerel ayar başka yerel ayarlara de kullanıldığında ayarlar. Bu etiket bir konuda kullanılıyorsa yalnızca bir kez kullanılmalıdır. Katalog içeriği birden fazla dilde içerdiğinde, bu etiketi kullanın. Birden çok konu katalogdaki aynı Kimliğe sahip olabilir, ancak her bir benzersiz TopicLocale belirtmeniz gerekir. Yerel katalog eşleşen bir TopicLocale belirten konu içindekiler tablosunda gösterilen konudur. Ancak, konu tüm dil sürümlerini arama sonuçları listesinde görüntülenir. |
| \< title > [Title] \< /title > | Bu konu başlığını belirtir. Bu etiket gereklidir ve yalnızca bir kez kullanılan bir konudaki. Konu gövdesi bir başlık içermiyorsa \<div > bölümüne ve içindekiler bölümünde, bu konu başlığı görüntülenir. |
| \< Meta name = "Microsoft.Help.Keywords" içerik = "[aKeywordPhrase]" / > | Yardım Görüntüleyici'nin dizin bölmesinde görüntülenen bağlantı metnini belirtir. Konu bağlantısına tıklandığında görüntülenir. Bir konu için birden fazla dizin anahtar belirtebilir veya dizininde görünmesi için bu konunun bağlantılarını istemiyorsanız bu etiketini atlayabilirsiniz. Bu özellik için "K" Yardım'ın önceki sürümlerini sözcüklerden dönüştürülebilir. |
| \< İçerik meta name="Microsoft.Help.Id" = "[Topicıd]" / > | Bu konu tanımlayıcısı ayarlar. Bu etiket gereklidir ve yalnızca bir kez kullanılan bir konudaki. Kimliği kataloğunda aynı yerel ayara sahip konular arasında benzersiz olmalıdır. Başka bir konu başlığında, bu kimliği kullanılarak bu konuya bir bağlantı oluşturabilirsiniz |
| \< Meta name="Microsoft.Help.F1" content="[System.Windows.Controls.Primitives.IRecyclingItemContainerGenerator]"/ > | Bu konuda F1 anahtar sözcük belirtir. Bir konu için birden çok F1 anahtar sözcük belirtebilir veya bu konuda, uygulama kullanıcısı F1 tuşuna bastığında görüntülenmesini istemiyorsanız bu etiketini atlayabilirsiniz. Genellikle, yalnızca bir F1 anahtar sözcüğü, bir konu için belirtilir. Bu özellik için Yardım'ın önceki sürümlerini "F" sözcüklerden dönüştürülebilir. |
| \< Meta name = "Description" content = "[konu description]" / > | Bu konudaki içeriğin kısa bir özetini sağlar. Bu etiket bir konuda kullanılıyorsa yalnızca bir kez kullanılmalıdır. Bu özellik sorgu kitaplığı tarafından doğrudan erişilir; Dizin dosyası içinde depolanmaz. |
| İçerik meta name="Microsoft.Help.TocParent" = "[parent_Id]" / > | Bu konunun üst konusu içindekiler tablosunun belirtir. Bu etiket gereklidir ve yalnızca bir kez kullanılan bir konudaki. Üst Microsoft.Help.Id değerdir. Bir konu içeriği tabloda yalnızca tek bir konumda olabilir. "-1" TOC Kök konu kimliği olarak kabul edilir. İçinde [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)], Yardım Görüntüleyicisi giriş sayfası, sayfasıdır. Özellikle TocParent =-1, üst düzeyi gösterilmediğini emin olmak için bazı konular eklediğimiz aynı nedeni budur. Yardım Görüntüleyicisi giriş sayfası bir sistem sayfası olduğu ve bu nedenle olmayan tarafından değiştirilebilir. -1 Kimliğine sahip bir sayfa eklemek bir VSP çalışırsa, içerik kümesine nasıl ekleneceğinizi, ancak Yardım Görüntüleyici Yardım Görüntüleyicisi giriş sayfası - sistem sayfası her zaman kullanır |
| \< İçerik meta name="Microsoft.Help.TocOrder" = "[pozitif tamsayı]" / > | İçindekiler tablosunda, eş konuları göre bu konuda göründüğü belirtir. Bu etiket gereklidir ve yalnızca bir kez kullanılan bir konudaki. Bir tamsayı değerdir. Düşük değerli tamsayı belirten bir konu daha yüksek bir değer tamsayı belirten bir konu görünür. |
| \< İçerik meta name="Microsoft.Help.Product" = "[ürün kodu]" / > | Bu konuda açıklanan ürün belirtir. Bu etiket bir konuda kullanılıyorsa yalnızca bir kez kullanılmalıdır. Bu bilgiler, ayrıca Yardım dizin oluşturucu için geçirilen parametre olarak sağlanabilir. |
| \< İçerik meta name="Microsoft.Help.ProductVersion" = "[sürüm number]" / > | Bu konuda açıklanan ürün sürümünü belirtir. Bu etiket bir konuda kullanılıyorsa yalnızca bir kez kullanılmalıdır. Bu bilgiler, ayrıca Yardım dizin oluşturucu için geçirilen parametre olarak sağlanabilir. |
| \< İçerik meta name="Microsoft.Help.Category" = "[string]" / > | Ürünleri tarafından içerik bölümlerini tanımlamak için kullanılır. Bir konu için birden çok alt bölümlere belirleyebilir veya tüm alt bölümlere tanımlamak için bağlantılar istemiyorsanız bu etiket atlayabilirsiniz. Bu etiket, bir konuda Yardım'ın önceki bir sürümden dönüştürüldüğünde, hedef işletim sistemi ve TargetFrameworkMoniker öznitelikleri depolamak için kullanılır. İçerik AttributeName:AttributeValue biçimidir. |
| \< Meta name="Microsoft.Help.TopicVersion içeriği ="[konu sürüm number]"/ > | Birden çok sürümünün bir katalogda mevcut olduğunda, bu konunun sürümü belirtir. Microsoft.Help.Id benzersiz olması garanti edilmez olduğundan, birden fazla sürümü bir konu bir katalogda Örneğin, bir katalog bir konu için bir konu başlığı ve .NET Framework 3.5 için .NET Framework 4 içerir ve her ikisi de aynı Micro var. Bu etiketi gereklidir yazılım. Help.Id. |
| \< Meta adı "SelfBranded" content = "[TRUE veya false değerini]" = / > | Bu konuda Yardım Kitaplığı Yöneticisi başlatma marka paketini veya konuya özgü marka paketini kullanıp kullanmayacağını belirtir. Bu etiket ya da TRUE olması gerekir ya da yanlış. Konu diğer içerik işleme farklı olsa bile beklendiği gibi işlenir böylece Yardım Kitaplığı Yöneticisi başlatıldığında ayarlanır marka paketi marka paketi ilişkili konu için geçersiz kılar, TRUE olarak ayarlanırsa. FALSE ise, geçerli konuda Yardım Kitaplığı Yöneticisi yeniden başlatıldığında ayarlanır marka paketi göre işlenir. Varsayılan olarak, Yardım Kitaplığı Yöneticisi SelfBranded değişkeni TRUE olarak bildirildiği sürece false olarak kendi kendine marka varsayar; Bu nedenle, bildirmeniz gerekmez \<meta name = "SelfBranded" content = "FALSE" / >. |

### <a name="creating-a-branding-package"></a>Marka paket oluşturma
Visual Studio sürüm, Visual Studio iş ortakları için yalıtılmış ve tümleşik Kabuk gibi farklı Visual Studio ürün sayısı kapsar.  Her bu ürünlerin belirli bir ölçüde konu tabanlı Yardım içeriği desteği, ürüne özgü marka gerektirir.  ISO Kabuk sarmalar, SQL Studio'yu kendi benzersiz Yardım içerik için her konuda marka gerektirirken, Visual Studio konuları tutarlı marka sunuyu olması gerekir.  Tümleşik Kabuk iş ortağı, Yardım konuları, kendi konu marka sağlamanın yanı sıra Visual Studio ürün Yardım içeriğini üst öğe içinde olmasını isteyebilirsiniz.

Marka paketleri Yardım Görüntüleyicisi'ni içeren ürün tarafından yüklenir.  Visual Studio ürünleri için:

-   Bir geri dönüş marka paket (Branding_\<yerel ayar > .mshc) Yardım Görüntüleyicisi 2.3 uygulama kök dizininde yüklü (örnek: C:\Program Files (x86) \Microsoft Help Viewer\v2.3) Yardım Görüntüleyicisi dil paketi tarafından.  Bu paket marka ürün yüklü olmayan durumlar için kullanılır (içerik yüklendi) veya yüklü paketleri şu marka burada bozuk.  Uygulama kök geri dönüş marka paketi kullanıldığında, Visual Studio öğelerini (logosu ve geri bildirim) göz ardı edilir.

-   Visual Studio içeriği içerik paket hizmetini yüklendiğinde bir marka paket de (ilk zaman içerik yükleme senaryosu için) yüklenir.  Marka paketine bir güncelleştirme varsa, güncelleştirmeyi içerik İleri güncelleştirmeyi veya ek paket yükleme eylemi olduğunda yüklenir.

Microsoft Yardım Görüntüleyici, konu meta verileri temel alarak konuları marka destekler.

-   Burada konu meta verilerini kendi kendine markalı tanımlar = true, olduğu gibi konu oluşturma, (sunulan ürünün kendinde markalama) hiçbir şey yapma.

-   Burada konu meta verilerini kendi kendine markalı tanımlar = false, TopicVendor meta verileri değeriyle ilişkili marka paketi kullanın.

-   Burada name="Microsoft.Help.TopicVendor konu meta verileri tanımlayan" içerik =\< satıcı MSHA marka paket adı >, içerik değeri tanımlanan marka paketi kullanın.

-   Visual Studio katalog içinde bir öncelik uygulama paketlerinin marka yoktur.  İlk Visual Studio varsayılan marka uygulanır ve sonra konu meta verilerde tanımlanan ve desteklenen ilişkili markalama paketini (yükleme msha içinde tanımlandığı şekilde), satıcı tanımlı marka bir geçersiz kılma uygulanır.

Marka öğeleri genellikle üç ana kategoriye ayrılır:

-   Üstbilgi öğeleri (örnekler geri bildirim bağlantısı, koşullu sorumluluk reddi metnini, logosu)

-   (Örnekler Genişlet/Daralt denetim metin öğelerini içerir ve kod parçacığı öğeleri) davranışlarını içerik

-   Alt öğeleri (örneğin telif hakkı)

Markalı öğeleri olarak dikkate öğeler (Bu belirtim ayrıntılı):

-   Katalog/ürün logo (örneğin, Visual Studio)

-   Geri bildirim bağlantısı ve e-posta öğeleri

-   Vazgeçme

-   Telif Hakkı metin

Visual Studio Yardım Görüntüleyicisi marka paketindeki destek dosyalarını içerir:

-   Grafik (logolar, simgeler, vb.)

-   Branding.js - destekleyici içerik davranışları betik dosyaları

-   Branding.xml - içerik arasında tutarlı bir şekilde kullanılan dizelerin katalog.  Not: Visual Studio yerelleştirme branding.xml metin öğeleri eklemek için _locID = "\<benzersiz değer >"

-   Branding.CSS - stil tanımları için sunu tutarlılık

-   Printing.css - tutarlı yazdırılan sunum için Stil tanımları

Yukarıda belirtildiği gibi marka paketleri konu ile ilişkilidir:

-   Zaman SelfBranded = false meta verilerde tanımlanan, konu paket marka Kataloğu devralır

-   Veya SelfBranded = false ve var. benzersiz bir marka paketi MSHA ve kullanılabilir içeriği yüklendiğinde tanımlanır

VSPs özel marka paketleri uygulamak için (VSP içerik SelfBranded = True), devam etmek için bir yoludur (Yardım Görüntüleyici ile yüklü) geri dönüş marka paket başlayın ve uygun olarak dosyanın adını değiştirmek için.  Branding_\<yerel ayar > .mshc dosyasıdır .mshc için değiştirilen dosya uzantısına sahip bir zip dosyası, bu nedenle yalnızca uzantısı .mshc .zip olarak değiştirin ve içeriğini ayıklayın.  Marka paket öğeleri için aşağıya bakın ve uygun şekilde değiştirin (örneğin, VSP logosu ve başvuru Branding.xml dosya logo logosunu değiştirmek, Branding.xml güncelleştirme VSP özellikleri, vb.).

Tüm değişiklikler yaptığınızda, istenen marka öğeleri içeren bir zip dosyası oluşturun ve uzantısını .mshc için değiştirin.

Özel marka paketi ilişkilendirmek için (konular içeren) içerik mshc birlikte marka mshc dosyaya başvuru içeren MSHA oluşturun.  "MSHA" temel MSHA oluşturmak için aşağıya bakın.

Bir konu içerdiğinde, tutarlı bir şekilde belirli bir konu öğelerinde çizmek için kullanılan öğeler listesi Branding.xml dosyayı içeren \<meta name="Microsoft.Help.SelfBranded" içerik = "false" / >.  Visual Studio Branding.xml dosyasındaki öğeleri listesi aşağıda verilmiştir.  Bu liste, ISO Kabuk Benimseyenler, nerede bunlar kendi ürün markasını karşılamak için bu öğeleri (örneğin logosu, geri bildirim ve telif hakkı) değiştirmek için bir şablon gerektiğinde kullanılması amaçlanmıştır.

Not: "{n}" tarafından belirtilen değişkenlerin kod bağımlılıklarını sahip - hataları ve büyük olasılıkla uygulama kilitlenme bu değerlerin değiştirilmesi veya kaldırılması neden olur. Yerelleştirme tanımlayıcıları (örneğin _locID="codesnippet.n"), Visual Studio markalama pakette dahil edilir.

**Branding.XML**


| | |
| - | - |
| Özelliği: | **CollapsibleArea** |
| Kullanım: | Daraltır içerik denetimi metni Genişlet |
| **Öğe** | **Değer** |
| ExpandText | Genişletin |
| CollapseText | Daralt |
| Özelliği: | **CodeSnippet** |
| Kullanım: | Kod parçacığı denetim metin.  Not: Alanı için kod parçacığı içerik "Bölünemez" alanı ile değiştirilir. |
| **Öğe** | **Değer** |
| CopyToClipboard | Panoya kopyala |
| ViewColorizedText | Renkli görüntüle |
| CombinedVBTabDisplayLanguage | Visual Basic (örnek) |
| VBDeclaration | Bildirim |
| VBUsage | Kullanım |
| Özelliği: | **Geri bildirim, altbilgi ve logosu** |
| Kullanım: | Müşteri e-posta yoluyla geçerli konu hakkında geri bildirim sağlamak için bir geri bildirim denetimi sağlar.  Telif Hakkı metin içeriği.  Logo tanımı. |
| **Öğe** | **Değer (Bu dizeler içerik benimseyen gereksinime uygun şekilde değiştirilebilir.)** |
| Telif Hakkı | © 2013 Microsoft Corporation. Tüm hakları saklıdır. |
| SendFeedback | \<bir href = "{0}" {1}> geri bildirim gönder\</a > Bu konuda Microsoft'a. |
| FeedbackLink | |
| LogoTitle | [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] |
| LogoFileName | vs_logo_bk.gif |
| LogoFileNameHC | vs_logo_wh.gif |
| Özelliği: | **Sorumluluk reddi** |
| Kullanım: | Özel durum bildirimleri makine için bir dizi içerik çevrilebilir. |
| **Öğe** | **Değer** |
| MT_Editable | Bu makale makine çevirisi oldu. Internet bağlantısı varsa, "Bu sayfayı düzenlenebilir modda orijinal İngilizce içerikle aynı anda görüntülemek için bu konuyu çevrimiçi gör"'i seçin. |
| MT_NonEditable | Bu makale makine çevirisi oldu. Internet bağlantısı varsa, "Bu sayfayı düzenlenebilir modda orijinal İngilizce içerikle aynı anda görüntülemek için bu konuyu çevrimiçi gör"'i seçin. |
| MT_QualityEditable | Bu makalede el ile çevrilmiştir. Internet bağlantısı varsa, "Bu sayfayı düzenlenebilir modda orijinal İngilizce içerikle aynı anda görüntülemek için bu konuyu çevrimiçi gör"'i seçin. |
| MT_QualityNonEditable | Bu makalede el ile çevrilmiştir. Internet bağlantısı varsa, "Bu sayfayı düzenlenebilir modda orijinal İngilizce içerikle aynı anda görüntülemek için bu konuyu çevrimiçi gör"'i seçin. |
| MT_BetaContents | Bu makale makine çevirisi bir ön sürüm için oldu. Internet bağlantısı varsa, "Bu sayfayı düzenlenebilir modda orijinal İngilizce içerikle aynı anda görüntülemek için bu konuyu çevrimiçi gör"'i seçin. |
| MT_BetaRecycledContents | Bu makalede, bir ön sürüm için el ile çevrilmiştir. Internet bağlantısı varsa, "Bu sayfayı düzenlenebilir modda orijinal İngilizce içerikle aynı anda görüntülemek için bu konuyu çevrimiçi gör"'i seçin. |
| Özelliği: | **LinkTable** |
| Kullanım: | Çevrimiçi konusuna bağlantılar için destek |
| **Öğe** | **Değer** |
| LinkTableTitle | Bağlantı tablosu |
| TopicEnuLinkText | İngilizce sürümünü görüntülemek\</a > bilgisayarınızda mevcut olan bu konu başlığının. |
| TopicOnlineLinkText | Bu konuda görüntülemek \<bir href = "{0}" {1}> Çevrimiçi\</a > |
| OnlineText | Çevrimiçi |
| Özelliği: | **Video ses denetimi** |
| Kullanım: | Öğeleri ve video içeriği için metin görüntüleme |
| **Öğe** | **Değer** |
| MultiMediaNotSupported | Internet Explorer 9 veya üstü yüklü olmalıdır destekleyecek şekilde {0} içeriği. |
| VideoText | video görüntüleme |
| AudioText | ses akışı |
| OnlineVideoLinkText | \<p > Bu konu ile ilgili videoyu görüntülemek için tıklayın {0} \<bir href = "{1}" >{2}burada\</a >.\< /p > |
| OnlineAudioLinkText | \<p > Bu konu ile ilgili sesi dinlemek için tıklatın {0} \<bir href = "{1}" >{2}burada\</a >.\< /p > |
| Özelliği: | **İçerik denetimi yüklü değil** |
| Kullanım: | Contentnotinstalled.htm işlemek için kullanılan metin öğelerini (dize) |
| **Öğe** | **Değer** |
| ContentNotInstalledTitle | Bilgisayarınızda hiçbir içerik bulunamadı. |
| ContentNotInstalledDownloadContentText | \<p > içeriği bilgisayarınıza indirmek için \<bir href = "{0}" {1}> Yönet sekmesini tıklatın\</a >.\< /p > |
| ContentNotInstalledText | \<p > bilgisayarınızda hiçbir içerik yüklenir. Yerel Yardım içerik yükleme için yöneticinize başvurun. \</p > |
| Özelliği: | **Konu denetim bulunamadı** |
| Kullanım: | Topicnotfound.htm işlemek için kullanılan metin öğelerini (dize) |
| **Öğe** | **Değer** |
| TopicNotFoundTitle | İstenen konu bilgisayarınızda bulunamıyor. |
| TopicNotFoundViewOnlineText | \<p > istediğiniz konu bilgisayarınızda bulunamadı, ancak yapabilecekleriniz \<bir href = "{0}" {1}> konuyu çevrimiçi gör\</a >.\< /p > |
| TopicNotFoundDownloadContentText | \<p > benzer konular için Gezinti bölmesine bakın veya \<bir href = "{0}" {1}> Yönet sekmesini tıklatın\</a > bilgisayarınıza içerik indirilemedi.\< /p > |
| TopicNotFoundText | \<p > istediğiniz konu bilgisayarınızda bulunamadı. \</p > |
| Özelliği: | **Konu bozuk denetimi** |
| Kullanım: | Topiccorrupted.htm işlemek için kullanılan metin öğelerini (dize) |
| **Öğe** | **Değer** |
| TopicCorruptedTitle | İstenen konu görüntülenemiyor. |
| TopicCorruptedViewOnlineText | \<p > Yardım Görüntüleyiciyi istenen konuyu görüntüleyemiyor. Konunun içeriğinde veya temel bir sistem bağımlılık bir hata olabilir. \</p > |
| Özelliği: | **Giriş sayfası denetimi** |
| Kullanım: | Yardım Görüntüleyicisi üst düzey düğüm içerik görünümü destekleyen metin. |
| **Öğe** | **Değer** |
| HomePageTitle | Yardım Görüntüleyicisi giriş sayfası |
| HomePageIntroduction | \<p > Microsoft Yardım Görüntüleyici, temel bir kaynağı olan Microsoft araçları, ürünleri, teknolojileri ve hizmetleri kullanan herkes için daha fazla bilgi için Hoş Geldiniz. Nasıl yapılır ve başvuru bilgileri, örnek kod, teknik makaleler ve daha fazla bilgi için Yardım Görüntüleyici erişmenizi sağlar. İçindekilere göz atın, ihtiyacınız olan içeriği bulmak için tam metin araması kullanın veya içerikte anahtar kelime dizinini kullanarak gezinin. \</p > |
| HomePageContentInstallText | \<p >\<br / > kullanım \<bir href = "{0}" {1}> İçeriği Yönet\</a > sekmesini aşağıdakileri yapmak için:\<ul >\<li > bilgisayarınıza içerik ekleyin.\< /li >\<li > yerel içerik güncelleştirmelerini denetleyin.\< /li >\<li > bilgisayarınızdan içerik kaldırın.\< /li >\</ul >\</p > |
| HomePageInstalledBooks | Yüklü kitaplar |
| HomePageNoBooksInstalled | Bilgisayarınızda hiçbir içerik bulunamadı. |
| HomePageHelpSettings | Yardım içeriği ayarları |
| HomePageHelpSettingsText | \<p > geçerli ayarınız yerel yardım eder. Yardım Görüntüleyici, bilgisayarınızda yüklü olan içeriğini görüntüler. \<br / > Visual Studio menü çubuğunda, Yardım içeriği kaynağını değiştirmek için seçin \<span style = "{0}" > Yardım, Yardım tercihini Ayarla\</span >.\< br / >\</p > |
| Megabayt | MB |

**Branding.js**

Visual Studio Yardım Görüntüleyicisi marka öğeleri tarafından kullanılan JavaScript branding.js dosya içerir.  Marka öğelerini destekleyen bir JavaScript işlevi ve bir listesi aşağıda verilmiştir.  Bu dosya için yerelleştirilecek tüm dizeleri, bu dosyayı üst kısmındaki "Yerelleştirilebilir dize" bölümünde tanımlanır.  Loc dizeleri branding.js dosyası içinde ICL dosyası oluşturuldu.

||||
|-|-|-|
|**Marka özelliği**|**JavaScript işlevi**|**Açıklama**|
|Var...||Değişkenleri tanımlama|
|Kullanıcı kod dilini Al|setUserPreferenceLang|bir dizini eşleyen # kod dili|
|Ayarlama ve tanımlama bilgisi değerleri alma|getCookie, setCookie||
|Devralınan üye|changeMembersLabel|Devralınan üye Genişlet/Daralt|
|Zaman SelfBranded = False|Yüklendiğinde|Bir yazdırma isteği olup olmadığını denetlemek için sorgu dizesini okuyun.  Kullanıcı tercih edilen sekmesi odaklanmak codesnippets ayarlayın.  Bir yazdırma isteği olup olmadığını isPrinterFriendly true olarak ayarlayın. Yüksek Karşıtlık modunu kullanmak için kontrol edin.|
|Kod parçacığı|addSpecificTextLanguageTagSet||
||getIndexFromDevLang||
||ChangeTab||
||setCodesnippetLang||
||setCurrentLang||
||CopyToClipboard||
|CollapsibleArea|addToCollapsibleControlSet|Tüm daraltılabilir denetim nesnesi listeye yazın.|
||CA_Click|Daraltılabilir alanının durumunu temel alan, hangi görüntü ve metin sunmak için tanımlar|
|Logo Karşıtlık desteği|isBlackBackground()|Siyah arka plan olup olmadığını belirlemek için çağrılır.  Yalnızca doğru olduğunda yüksek karşıtlık modunda.|
||isHighContrast()|Yüksek Karşıtlık modunu kullanmak algılamak için renkli bir yayılma kullanın|
||onHighContrast(black)|Yüksek Karşıtlık tespit edildiğinde çağırılır|
|LST işlevi|||
||addToLanSpecTextIdSet(id)||
||updateLST(currentLang)||
||getDevLangFromCodeSnippet(lang)||
|Multimedya işlevi|Başlık (başlar, end, metin stili)||
||findAllMediaControls(normalizedId)||
||getActivePlayer(normalizedId)||
||captionsOnOff(id)||
||toSeconds(t)||
||getAllComments(node)||
||(stil adı, styleValue) styleRectify||
||showCC(id)||
||subtitle(id)||

**HTM DOSYALARI**

Bir dizi anahtar bilgileri açıklayan hangi içerik kümelerini yüklü bir bölüm ve konuları bağlanamazken seçmesini söyleyen sayfaları içeren örnek bir giriş sayfası Yardım içerik kullanıcılara iletişim kurmak için senaryoları desteklemek HTM dosyasını marka pakette Yerel konuları kümesinde bulunamadı. Bu HTM dosyalar ürün değiştirilebilir.  ISO Kabuk satıcıları varsayılan marka paketi alıp davranışını ve bu sayfaların içeriğini kendi ihtiyacına paketine değiştirme olanağına sahip olursunuz.  Bu dosyalar branding.xml dosyasındaki ilgili içerik almak marka etiketleri için sırayla ilgili kendi marka paket bakın.

||||
|-|-|-|
|**Dosya**|**Kullanın**|**Görüntülenen içerik kaynağı**|
|homepage.htm|Şu anda yüklü içeriği ve içeriklerini hakkında kullanıcıya göstermek uygun başka iletisi görüntüleyen bir sayfa budur.  Bu dosya ek meta veri özniteliği "Microsoft.Help.Id" içeriğe sahip olan yerel içerik TOC üst kısmında bu içerik yerleştirir "-" 1 =.||
||&LT; META_HOME_PAGE_TITLE_ADD / &GT;|Branding.XML, etiket \<HomePageTitle >|
||&LT; HOME_PAGE_INTRODUCTION_SECTION_ADD / &GT;|Branding.XML, etiket \<HomePageIntroduction >|
||&LT; HOME_PAGE_CONTENT_INSTALL_SECTION_ADD / &GT;|Branding.XML, etiket \<HomePageContentInstallText >|
||&LT; HOME_PAGE_BOOKS_INSTALLED_SECTION_ADD / &GT;|Bölüm Branding.xml etiketi başlık\<HomePageInstalledBooks >, uygulamasından oluşturulan veriler \<HomePageNoBooksInstalled > hiçbir books yüklü olduğunda.|
||&LT; HOME_PAGE_SETTINGS_SECTION_ADD / &GT;|Bölüm Branding.xml etiketi başlık \<HomePageHelpSettings >, bölümünde metin \<HomePageHelpSettingsText >.|
|topiccorrupted.htm|Yerel kümede bir konu varsa, ancak herhangi bir nedenle görüntülenemiyor (bozuk içeriği).||
||&LT; META_TOPIC_CORRUPTED_TITLE_ADD / &GT;|Branding.XML, etiket \<TopicCorruptedTitle >|
||&LT; TOPIC_CORRUPTED_SECTION_ADD / &GT;|Branding.XML, etiket \<TopicCorruptedViewOnlineText >|
|topicnotfound.htm|Ne zaman bir konu yerel içeriği çevrimiçi ayarlayın ya da kullanılabilir bulunamadı||
||&LT; META_TOPIC_NOT_FOUND_TITLE_ADD / &GT;|Branding.XML, etiket \<TopicNotFoundTitle >|
||&LT; META_TOPIC_NOT_FOUND_ID_ADD / &GT;|Branding.XML, etiket \<TopicNotFoundViewOnlineText > + \<TopicNotFoundDownloadContentText >|
||&LT; TOPIC_NOT_FOUND_SECTION_ADD / &GT;|Branding.XML, etiket \<TopicNotFoundText >|
|contentnotinstalled.htm|Ürün için yüklenmiş yerel içerik olmadığında.||
||&LT; META_CONTENT_NOT_INSTALLED_TITLE_ADD / &GT;|Branding.XML, etiket \<ContentNotInstalledTitle >|
||&LT; META_CONTENT_NOT_INSTALLED_ID_ADD / &GT;|Branding.XML, etiket \<ContentNotInstalledDownloadContentText >|
||&LT; CONTENT_NOT_INSTALLED_SECTION_ADD / &GT;|Branding.XML, etiket \<ContentNotInstalledText >|

**CSS dosyaları**

Visual Studio Yardım Görüntüleyicisi marka paketi, Visual Studio Yardım tutarlı içerik sunum desteklemek için iki css dosyaları içerir:

-   Branding.css - where işlemeye css öğeleri içeren SelfBranded = false

-   Printer.css - where işlemeye css öğeleri içeren SelfBranded = false

Branding.css dosyaları, Visual Studio konu sunu için tanımları içerir (uyarı olduğu branding.css Branding_ içinde yer alan\<yerel ayar > paket hizmetinden .mshc değişebilir).

**Grafik dosyaları**

Visual Studio İçerik, Visual Studio logosu ve bunun yanı sıra diğer grafik görüntüler.  Visual Studio Yardım Görüntüleyicisi marka paketinde grafik dosyaların tam listesini aşağıda gösterilmiştir.

||||
|-|-|-|
|**Dosya**|**Kullanın**|**Örnekler**|
|Clear.gif|Daraltılabilir alan işlemek için kullanılan||
|footer_slice.gif|Altbilgi sunu||
|info_icon.gif|Bilgileri görüntülerken, kullanılan|Sorumluluk reddi|
|online_icon.gif|Bu çevrimiçi bağlantıları ile ilişkilendirilecek simgedir||
|tabLeftBD.gif|Kod parçacığı kapsayıcısı oluşturmak için kullanılır||
|tabRightBD.gif|Kod parçacığı kapsayıcısı oluşturmak için kullanılır||
|vs_logo_bk.gif|Branding.xml etiketinde tanımlanan normal Karşıtlık logosu başvurular için kullanılan \<LogoFileName >.  Visual Studio ürünleri için logo vs_logo_bk.gif adıdır.||
|vs_logo_wh.gif|Branding.xml etiketinde tanımlanan normal yüksek logosu başvurular için kullanılan \<LogoFileNameHC >.  Visual Studio ürünleri için logo vs_logo_wh.gif adıdır.||
|ccOff.png|Grafik resim yazısı||
|ccOn.png|Grafik resim yazısı||
|ImageSprite.png|Daraltılabilir alan işlemek için kullanılan|Genişletilmiş veya grafiği Daralt|

### <a name="deploying-a-set-of-topics"></a>Konuları kümesi dağıtma
MSHA dosyası ve kabinler veya konuları içeren MSHCs kümesinden oluşan bir Yardım Görüntüleyici içerik dağıtımı kümesi oluşturmak için basit ve hızlı bir öğretici budur. MSHA kabinler kümesini tanımlayan bir XML dosyasına veya MSHC dosyalar var. Yardım Görüntüleyicisi'ni (. içerik listesini almak için MSHA okuyabilirsiniz CAB veya. MSHC dosyaları) yerel yükleme için kullanılabilir.

Yalnızca çok basit bir XML şeması için Yardım Görüntüleyicisi MSHA açıklayan bir öncü budur.  Bu kısa genel bakış ve örnek HelpContentSetup.msha aşağıda bir örnek uygulama yok.

MSHA amaçları doğrultusunda bu temel bilgiler (dosya adı uzantısına sahip hiçbir şey olabilir. HelpContentSetup.msha adıdır MSHA). (Aşağıdaki örnek) HelpContentSetup.msha MSHCs kullanılabilir ve kabinler listesini içermelidir.  Dosya türü (MSHA ve CAB dosya türleri bileşimi desteklemez) MSHA içinde tutarlı olması gerekir. Her CAB veya MSHC için olmalıdır bir \<div class = "paketini" >...  \< /div > (aşağıdaki örneğe bakın).

Not: uygulaması aşağıdaki örnekte, marka paketini ekledik. Bu içerik davranışları ve gerekli öğe Visual Studio İçerik işleme almak için eklemek önemlidir.

Örnek HelpContentSetup.msha dosyası: ("İçerik kümesi adı 1" değiştirin ve "İçerik kümesi adı 2" vb. kullanarak dosya adlarıyla.)

```html
<html>
<head />
<body class="vendor-book">
<div class="details">
<span class="vendor">Your Company</span>
<span class="locale">en-us</span>
<span class="product">Your Company Help Content</span>
<span class="name">Your Company Help Content</span>
</div>
<div class="package-list">
<div class="package">
<span class="name">Your_Company _Content_Set_1</span>
<span class="deployed">True</span>
<a class="current-link" href="Your_Company _Content_Set_1.mshc">Your_Company _Content_Set_1.mshc </a>
</div>
<div class="package">
<span class="name">Your_Company _Content_Set_2</span>
<span class="deployed">True</span>
<a class="current-link"href=" Your_Company _Content_Set_2.mshc "> Your_Company _Content_Set_2.mshc </a>
</div>.
```

1.  "C:\SampleContent" gibi yerel bir klasör oluşturun

2.  Bu örnekte, konuları içerecek şekilde MSHC dosyaları kullanacağız.  Bir MSHC zip .zip olarak değiştirildi dosya uzantısına sahip olur. MSHC.

3.  Oluşturma bir metin dosyası olarak HelpContentSetup.msha aşağıda (Not Defteri dosyası oluşturmak için kullanılan) ve yukarıda belirtilenler klasörüne kaydedin (1. adıma bakın).

"Markalama" var ve benzersiz sınıfı. Marka mshc marka yüklü içeriği sahiptir ve marka pakette yer alan uygun destek öğeleri MSHCs içinde bulunan içerik davranışları olur böylece bu temel bilgiler dahil edilir. Sistem (yüklü) kopyalanan parçası olmayan destek öğeleri için içerik göründüğünde bu olmadan hatalara neden olabilecek.

Visual Studio Paket marka elde etmek için C:\Program Files (x86) \Microsoft Help Viewer\v2.3\ Branding_en US.mshc dosyasını çalışma klasörünüze kopyalayın.

```html
<html>
<head />
<body class="vendor-book">
<div class="details">
<span class="vendor">Your Company</span>
<span class="locale">en-us</span>
<span class="product">Your Company Help Content</span>
<span class="name">Your Company Help Content</span>
</div>
<div class="package-list">
<div class="package">
<span class="name">Your_Company _Content_Set_1</span>
<span class="deployed">True</span>
<a class="current-link" href="Your_Company _Content_Set_1.mshc">Your_Company _Content_Set_1.mshc </a>
</div>
<div class="package">
<span class="name">Your_Company _Content_Set_2</span>
<span class="deployed">True</span>
<a class="current-link"href=" Your_Company _Content_Set_2.mshc "> Your_Company _Content_Set_2.mshc </a>
</div>
<div class="package">
<span class="packageType">branding</span>
<span class="name">Branding_en-US</span>
<span class="deployed">True</span>
<a class="current-link" href="Branding_en-US.mshc">Branding_en-US.mshc</a>
</div>
</div>
</body>
</html>

```

**Özet**

Visual Studio Yardım Görüntüleyicisi için kendi içerik kümesi dağıtmak VSPs kullanarak ve yukarıdaki adımları genişletme etkinleştirir.

### <a name="adding-help-to-the-visual-studio-shell-integrated-and-isolated"></a>Visual Studio Kabuğu (tümleşik ve yalıtılmış) Yardım ekleme
**Giriş**

Bu izlenecek yol, Yardım içeriğini bir Visual Studio Shell uygulamaya eklemenizi ve dağıttıktan sonra gösterilmektedir.

**Gereksinimler**

1.  [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)]

2.  [Visual Studio 2013 Shell yeniden dağıtılabilir yalıtılmış](http://www.microsoft.com/visualstudio/11/downloads#vs-shell)

**Genel bakış**

[!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] Kabuktur sürümü [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] IDE üzerinde sizin temel bir uygulama. Bu tür uygulamalar, yalıtılmış Kabuk oluşturduğunuz uzantıları ile birlikte içerir. Dahil edilen yalıtılmış Kabuk proje şablonlarını kullanma [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] uzantılar oluşturmak için SDK'sı.

Yalıtılmış kabuk tabanlı bir uygulama ve onun Yardım oluşturmaya yönelik temel adımlar:

1. Elde [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] ISO Shell yeniden dağıtılabilir (Microsoft İndirme).

2. Visual Studio'da, yalıtılmış Kabuk, örneğin dayanan bir Yardım uzantısı, bu anlatımın ilerleyen kısımlarında açıklanan Contoso Yardım uzantısı oluşturun.

3. Uzantı ve dağıtım MSI (Uygulama Kurulumu) yeniden dağıtılabilir ISO Kabuk kaydır. Bu izlenecek yol, bir kurulum adımı içermez.

Visual Studio İçerik depolama alanı oluşturun. Tümleşik Kabuk senaryo için görsel Studio12 ürün kataloğu adına gibi değiştirin:

-   Klasör C:\ProgramData\Microsoft\HelpLibrary2\Catalogs\VisualStudio15 oluşturun.

-   CatalogType.xml adlı bir dosya oluşturun ve klasöre ekleyin. Dosya, aşağıdaki kod satırlarını içermesi gerekir:

    ```xml
    <?xml version="1.0" encoding="UTF-8"?>
    <catalogType>UserManaged</catalogType>
    ```

İçerik deposu kayıt defterinde tanımlayın. Tümleşik Kabuk için VisualStudio15 ürün kataloğu adla değiştirin:

- HKLM\SOFTWARE\Wow6432Node\Microsoft\Help\v2.3\Catalogs\VisualStudio15

   Anahtar: LocationPath dize değeri: C:\ProgramData\Microsoft\HelpLibrary2\Catalogs\VisualStudio15\

- HKLM\SOFTWARE\Wow6432Node\Microsoft\Help\v2.3\Catalogs\VisualStudio15\en-us

   Anahtar: Katalog adı dize değeri: [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] belgeleri

**Projeyi Oluşturma**

Yalıtılmış kabuk uzantısını oluşturmak için:

1.  Visual Studio'da altında **dosya**, seçin **yeni proje**altında **diğer proje türleri** seçin **genişletilebilirlik**, seçin **Visual Studio Kabuğu yalıtılmış**. Projeyi adlandırın `ContosoHelpShell`) Visual Studio yalıtılmış Kabuğu şablonu temel alan bir genişletilebilirlik projesi oluşturmak için.

2.  Çözüm Gezgini'nde ApplicationCommands.vsct ContosoHelpShellUI projesinde, kaynak dosyalar klasöründe açın. Bu satırı ("No_Help" aratın) kılınmıştır emin olun: `<!-- <define name="No_HelpMenuCommands"/> -->`

3.  Derlemek ve çalıştırmak için F5 tuşuna basın **hata ayıklama**. Yalıtılmış Kabuk IDE Deneysel örneğini seçin **yardımcı** menüsü. Emin olun **Yardımı Görüntüle**, **kaldırmak Yardım içeriğini Ekle ve**, ve **Yardım tercihini Ayarla** komut belirir.

4.  Çözüm Gezgini'nde ContosoHelpShell.pkgdef ContosHelpShell projede Kabuğu özelleştirme klasörü açın. Contoso Yardım kataloğu tanımlamak için aşağıdaki satırları ekleyin:

    ```
     [$RootKey$\Help]
    "Product"="Contoso"
    "Catalog"="Contoso"
    "Version"="100"
    "BrandingPackage"="ContosoBrandingPackage.mshc"
    ```

5.  Çözüm Gezgini'nde ContosoHelpShell.Application.pkgdef ContosHelpShell projede Kabuğu özelleştirme klasörü açın. F1 Yardımı'nı etkinleştirmek için aşağıdaki satırları ekleyin:

    ```
    // F1 Help Provider

    [$RootKey$\HelpProviders\{C99BDC23-FF29-46bf-9658-ADD634CCAED8}]
    "Name"="13407"
    "Package"="{DA9FB551-C724-11d0-AE1F-00A0C90FFFC3}"
    @="Help3 Provider"
    [$RootKey$\HelpProviders]
    @="{C99BDC23-FF29-46bf-9658-ADD634CCAED8}"
    [$RootKey$\Services\{C99BDC23-FF29-46bf-9658-ADD634CCAED8}]
    "Name"="Help3 Provider"
    @="{4A791146-19E4-11D3-B86B-00C04F79F802}"
    ```

6.  Çözüm Gezgini'nde ContosoHelpShell çözümün bağlam menüsünü seçin **özellikleri** menü öğesi. Altında **yapılandırma özellikleri**seçin **Configuration Manager**. İçinde **yapılandırma** sütun, "Sürüm" için "Debug" her bir değeri değiştirin.

7.  Çözümü oluşturun. Sonraki bölümde kullanılacak olan bir yayın klasördeki bir dosya kümesini oluşturur.

Dağıtılmışsa, bunu test etmek için:

1. Contoso indirilen ISO Kabuğu (yukarıdaki) yüklemek için makinede dağıttığınız.

2. Bir klasörde oluşturmak \\\Program dosyaları (x86)\\ve adlandırın `Contoso`.

3. ContosoHelpShell yayın klasörün içeriğini kopyalayın \\\Program Files (x86) \Contoso\ klasörü.

4. Kayıt Defteri Düzenleyicisi'ni seçerek başlayın **çalıştırma** içinde **Başlat** menü ve girerek `Regedit`. Kayıt Defteri Düzenleyicisi'nde seçin **dosya**, ardından **alma**. ContosoHelpShell proje klasörüne göz atın. ContosoHelpShell alt klasöründe ContosoHelpShell.reg seçin.

5. İçerik deposu oluşturun:

    Contoso içerik deposuna C:\ProgramData\Microsoft\HelpLibrary2\Catalogs\ContosoDev12 için ISO Shell - oluşturma

    İçin [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] tümleşik Kabuk C:\ProgramData\Microsoft\HelpLibrary2\Catalogs\VisualStudio15 klasör oluştur

6. CatalogType.xml oluşturun ve içerik deposu (önceki adımda) içeren ekleyin:

   ```
   <?xml version="1.0" encoding="UTF-8"?>
   <catalogType>UserManaged</catalogType>
   ```

7. Aşağıdaki kayıt defteri anahtarlarını ekleyin:

    HKLM\SOFTWARE\Wow6432Node\Microsoft\Help\v2.3\Catalogs\VisualStudio15Key: LocationPath dize değeri:

    ISO kabuğu için:

    C:ProgramDataMicrosoftHelpLibrary2CatalogsVisualStudio15

    [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] Tümleşik Kabuk:

    C:ProgramDataMicrosoftHelpLibrary2CatalogsVisualStudio15en-ABD

    Anahtar: Katalog adı dize değeri: [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] belgeleri. ISO Shell için bu kataloğunuzu adıdır.

8. İçeriğinizi (cab veya MSHC ve MSHA) yerel bir klasöre kopyalayın.

9. Örnek tümleşik Kabuk içerik deposuna test etmek için komutu. ISO kabuğu için katalog ve launchingApp değerleri ürün eşleştirmek uygun şekilde değiştirin.

     "C:\Program dosyaları (x86) \Microsoft Help Viewer\v2.3\HlpViewer.exe" / catalogname VisualStudio15 /helpQuery yöntemi = "sayfası & kimliği ContosoTopic0 =" /launchingApp Microsoft VisualStudio, 12.0

10. Contoso uygulaması (kökünden Contoso uygulaması) başlatın. ISO Kabuk içinde seçin **yardımcı** menü öğesi ile değişiklik **Yardım tercihini Ayarla** için **kullanımı yerel yardımcı**.

11. Kabuk içinde seçin **yardımcı** menü öğesi, ardından **Yardımı Görüntüle**. Yerel Yardım Görüntüleyicisi'ni başlatın. Seçin **içeriği Yönet** sekmesi. Altında **yükleme kaynağı**, seçin **Disk** seçenek düğmesini. Seçin **...**  düğmesi ve Contoso içeriği (Yukarıdaki adımda yerel klasöre kopyalandı) içeren yerel klasöre göz atın. HelpContentSetup.msha'ı seçin. Contoso artık bir kitap kitap seçimleri olarak gösterilmesi gerekir. Seçin **Ekle**ve ardından **güncelleştirme** düğmesine (sağ alt köşesindeki).

12. Contoso IDE F1 işlevselliğini test etmek için F1 tuşuna basın.

### <a name="additional-resources"></a>Ek kaynaklar

Çalışma zamanı API için bkz: [Windows Yardımı API](/previous-versions/windows/desktop/helpapi/helpapi-portal).

Nasıl yararlanacağınızı Yardımı API hakkında daha fazla bilgi için bkz. [Yardım Görüntüleyici kod örnekleri](https://marketplace.visualstudio.com/items?itemName=RobChandlerHelpMVP.HelpViewer20CodeExamples).

Özellik önerileri üzerinde gönderebilirsiniz [Geliştirici topluluğu](https://developercommunity.visualstudio.com/content/idea/post.html?space=8).