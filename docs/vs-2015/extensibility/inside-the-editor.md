---
title: Düzenleyici içinde | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], new - architecture
ms.assetid: 822cbb8d-7ab4-40ee-bd12-44016ebcce81
caps.latest.revision: 32
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ddca5ab4b0d7dc6aa43f3db8c641ad5fc9e583b2
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51735180"
---
# <a name="inside-the-editor"></a>Düzenleyicinin İçinde
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Düzenleyici metin görünümünü ve kullanıcı arabirimi düzenleyici metin modeli ayrı tutmak için tasarlanmış farklı alt sistemler sayısı oluşur.  
  
 Bu bölümlerde, düzenleyici farklı yönlerini açıklanmıştır:  
  
- [Alt sistemler genel bakış](../extensibility/inside-the-editor.md#overview)  
  
- [Metin modeli](../extensibility/inside-the-editor.md#textmodel)  
  
- [Metin görünümü](../extensibility/inside-the-editor.md#textview)  
  
  Bu bölümlerde, düzenleyici özellikleri açıklanmaktadır:  
  
- [Etiketleri ve sınıflandırıcı](../extensibility/inside-the-editor.md#tagsandclassifiers)  
  
- [Kenarlıklar](../extensibility/inside-the-editor.md#adornments)  
  
- [Projeksiyon](../extensibility/inside-the-editor.md#projection)  
  
- [Anahat Oluşturma](../extensibility/inside-the-editor.md#outlining)  
  
- [Fare bağlamaları](../extensibility/inside-the-editor.md#mousebindings)  
  
- [Düzenleyici işlemleri](../extensibility/inside-the-editor.md#editoroperations)  
  
- [IntelliSense](../extensibility/inside-the-editor.md#intellisense)  
  
##  <a name="overview"></a> Alt sistemler genel bakış  
  
### <a name="text-model-subsystem"></a>Metin modeli alt sistemi  
 Metin modeli alt metin temsil eden ve kendi işleme etkinleştirme sorumludur. Metin modeli alt içeren <xref:Microsoft.VisualStudio.Text.ITextBuffer> düzenleyici tarafından görüntülenecek olan karakter dizisini tanımlayan arabirimi. Bu metin değiştirildi, izlenen ve aksi takdirde pek çok şekilde değiştirilebilir. Metin model türleri için aşağıdaki konuları da sağlar:  
  
- Metin dosyaları ile ilişkilendirir ve bunları dosya sistemindeki yazma ve okuma yöneten hizmet.  
  
- En az iki diziyi nesnelerin farklarını bulur bir fark kayıt hizmeti.  
  
- Diğer arabellekler metinde kümelerine açısından arabellekteki metni açıklayan bir sistemi.  
  
  Metin modeli alt sistemi, kullanıcı arabirimi (UI) kavramlarını ücretsizdir. Örneğin, metin biçimlendirme veya metin düzeni için sorumlu değildir ve metinle birlikte ilişkilendirilebilir görsel Kenarlıklar olanağıyla sahiptir.  
  
  Metin modeli alt ortak tür yalnızca .NET Framework temel sınıf kitaplığı ve Yönetilen Genişletilebilirlik Çerçevesi (MEF) bağlıdır Microsoft.VisualStudio.Text.Data.dll ve Microsoft.VisualStudio.CoreUtilitiy.dll, yer alır.  
  
### <a name="text-view-subsystem"></a>Metin görünümü alt sistemi  
 Metin görünümü alt sistemi, biçimlendirme ve metin görüntüleme için sorumludur. Bu alt türlerini olup türleri Windows Presentation Foundation (WPF) dayanır bağlı olarak iki katmanlara ayrılır. En önemli türleridir <xref:Microsoft.VisualStudio.Text.Editor.ITextView> ve <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextView>, görüntülenecek olan metin satırlarını kümesini ve da giriş işaretini seçimi ve WPF kullanıcı Arabirimi öğeleri kullanarak metin donatmak için özellikleri denetleme. Bu alt sistemi, ayrıca metin kenar boşluklarını görüntüleme alanı sağlar. Bu kenar boşluklarının uzatılabilir ve farklı türde içerik ve görsel efektler içerebilir. Satır numarası görüntüler ve kaydırma çubukları kenar boşlukları örnekleridir.  
  
 Genel metin görünümü alt türlerini Microsoft.VisualStudio.Text.UI.dll ve Microsoft.VisualStudio.Text.UI.Wpf.dll yer alır. Platformdan bağımsız öğeleri ilk derlemeyi içeren ve ikinci WPF'ye özgü öğeleri içerir.  
  
### <a name="classification-subsystem"></a>Sınıflandırma alt sistemi  
 Metin yazı tipi özelliklerini belirlemek için sınıflandırma alt sorumludur. Sınıflandırıcı, örneğin, "anahtar sözcüğü" veya "Açıklama" olmak üzere farklı sınıflara metni keser. Gerçek yazı tipi özellikleri için bu sınıflar sınıflandırma biçim eşlemesine Örneğin, ilişkili "mavi Consolas 10 pt". Bu bilgiler biçimlendirir ve metin işler metin görünüm tarafından kullanılır. Etiketleme, bu konunun ilerleyen bölümlerinde daha ayrıntılı anlatılan sağlar metin yayılma ile ilişkilendirilecek veri.  
  
 Genel türler sınıflandırma alt sisteminin Microsoft.VisualStudio.Text.Logic.dll içinde bulunan ve Microsoft.VisualStudio.Text.UI.Wpf.dll içinde bulunan sınıflandırma görsel yönlerini etkileşim.  
  
### <a name="operations-subsystem"></a>İşlem alt sistemi  
 İşlem alt sistemi Düzenleyicisi davranışını tanımlar. Bu, Visual Studio Düzenleyicisi komutları için uygulama ve geri alma sistemi sağlar.  
  
## <a name="a-closer-look-at-the-text-model-and-the-text-view"></a>Metin modeli ve metin görünümünü daha yakından bakın  
  
###  <a name="textmodel"></a> Metin modeli  
 Metin modeli alt metin türleri farklı gruplandırmalarını oluşur. Bunlar, metin arabelleği, metin anlık görüntü ve metin alanları içerir.  
  
#### <a name="text-buffers-and-text-snapshots"></a>Metin arabelleği ve metin anlık görüntüleri  
 <xref:Microsoft.VisualStudio.Text.ITextBuffer> Arabirimi temsil eder, tarafından kullanılan kodlama olan UTF-16 kullanılarak kodlanmış bir Unicode karakter dizisi `String` .NET Framework türü. Bir dosya sistemi belgesi olarak bir metin arabelleği kalıcı olmasını, ancak bu zorunlu değildir.  
  
 <xref:Microsoft.VisualStudio.Text.ITextBufferFactoryService> Boş metin arabelleği veya bir dize ya da başlatılmış olan bir metin arabelleği oluşturmak için kullanılan <xref:System.IO.TextReader>. Metin arabelleği için dosya sistemi olarak kalıcı bir <xref:Microsoft.VisualStudio.Text.ITextDocument>.  
  
 Metin arabelleği çağırarak bir iş parçacığı sahipliğini metin arabelleğini alır kadar herhangi bir iş parçacığı tarafından düzenlenebilir <xref:Microsoft.VisualStudio.Text.ITextBuffer.TakeThreadOwnership%2A>. Bundan sonra yalnızca o iş parçacığı düzenlemeleri gerçekleştirebilirsiniz.  
  
 Bir metin arabelleği yaşam süresi boyunca birçok sürümü gidebilirsiniz. Yeni bir sürümü oluşturulan arabellek düzenlendiğinde ve sabit bir <xref:Microsoft.VisualStudio.Text.ITextSnapshot> arabellek bu sürümünün içeriğini temsil eder. Metin anlık sabit olduğundan, bile temsil ettiği metin arabelleği değişikliği devam eder, kısıtlama olmadan tüm iş parçacığı üzerinde metin anlık görüntü erişebilirsiniz.  
  
#### <a name="text-snapshots-and-text-snapshot-lines"></a>Metin anlık görüntüler ve metin anlık görüntü satırları  
 Bir karakter dizisi veya bir dizi satır olarak bir metin anlık görüntü içeriğini görüntüleyebilirsiniz. Karakterler ve satırlar hem de sıfırdan başlayarak dizine görünüyor. Bir boş metin anlık görüntü, sıfır karakter ve bir boş satır içerir. Bir satır başında ve sonunda arabellek veya herhangi bir geçerli Unicode satır sonu karakter dizisi sınırlandırılmıştır. Satır sonu karakterleri metin anlık açıkça gösterilir ve satır sonları metin anlık görüntüsündeki tüm aynı olması gerekmez.  
  
> [!NOTE]
>  Visual Studio Düzenleyicisi'nde satır sonu karakterleri hakkında daha fazla bilgi için bkz: [Kodlamalar ve satır sonlarını](../ide/encodings-and-line-breaks.md).  
  
 Bir metin satırı tarafından temsil edilen bir <xref:Microsoft.VisualStudio.Text.ITextSnapshotLine> belirli karakter konumu veya belirli bir satıra için metin anlık görüntüden alınan nesnesidir.  
  
#### <a name="snapshotpoints-snapshotspans-and-normalizedsnapshotspancollections"></a>SnapshotPoints, SnapshotSpans ve NormalizedSnapshotSpanCollections  
 A <xref:Microsoft.VisualStudio.Text.SnapshotPoint> bir anlık görüntü içinde bir karakterin konumu temsil eder. Konumu sıfır ve anlık görüntü uzunluğu arasında garanti edilir. A <xref:Microsoft.VisualStudio.Text.SnapshotSpan> bir anlık görüntü metni temsil eder. Bitiş konumu sıfır ve anlık görüntü uzunluğu arasında garanti edilir. <xref:Microsoft.VisualStudio.Text.NormalizedSnapshotSpanCollection> Kümesinden oluşan <xref:Microsoft.VisualStudio.Text.SnapshotSpan> aynı anlık görüntüden nesneleri.  
  
#### <a name="spans-and-normalizedspancollections"></a>Yayılımları ve NormalizedSpanCollections  
 A <xref:Microsoft.VisualStudio.Text.Span> metin anlık görüntüdeki metnin uygulanabilir bir aralığı temsil eder. Anlık görüntü konumları sıfır tabanlı, olduğundan yayılma sıfır dahil olmak üzere herhangi bir konumda başlayabilirsiniz. `End` Bir aralık özelliği için toplamına eşit olduğu kendi `Start` özelliği ve kendi `Length` özelliği. A `Span` tarafından dizine karakteri içermez `End` özelliği. Örneğin, bir başlangıç aralık = 5 ve uzunluğu = 3 olan son = 8, 5, 6 ve 7 konumlarda karakterleri içerir. Bu aralığa gösterim 5..8 şeklindedir).  
  
 Tüm pozisyonlar genel olarak, bitiş konumu dahil olmak üzere oluşturulduysa iki yayılma kesişen. Bu nedenle, kesişim [3, 5) ve [2, 7) olan [3, 5) ve kesişimi [3, 5) ve [5, 7) olduğundan [5, 5). (Dikkat [5, 5) boş bir aralığı.)  
  
 Konumlar bitiş konumu dışında ortak oluşturulduysa iki yayılma çakışıyor. Boş bir aralık hiçbir zaman başka bir yayılma çakışıyor ve iki yayılma çakışmasını hiçbir zaman boş değildir.  
  
 A <xref:Microsoft.VisualStudio.Text.NormalizedSpanCollection> yayılma yayılma başlangıç özelliklerini sırasına göre listesi verilmiştir. Listede, çakışan veya bitişik yayılma birleştirilir. Örneğin, yayılma kümesini verilen [5..9), [0..1), [3..6), ve [9..10), normalleştirilmiş yayılma listesidir [0..1), [3..10).  
  
#### <a name="itextedit-textversion-and-text-change-notifications"></a>ITextEdit TextVersion ve metin değişikliği bildirimleri  
 Bir metin arabelleği içeriğini kullanarak değiştirilebilir bir <xref:Microsoft.VisualStudio.Text.ITextEdit> nesne. Böyle bir nesne oluşturma (birini kullanarak `CreateEdit()` yöntemlerinin <xref:Microsoft.VisualStudio.Text.ITextBuffer>) metin düzenlemeleri oluşan bir metin hareket başlatır. Her Düzen bazı aralığını bir dizesini arabellekteki metni'nın yerini almıştır. İşlem başlatıldığında arabellek anlık görüntü göreli koordinatları ve her Düzen içeriğini cinsinden ifade edilir. <xref:Microsoft.VisualStudio.Text.ITextEdit> Nesnesi aynı işlemde başka düzenlemeler etkilenen düzenlemeleri koordinatlarını ayarlar.  
  
 Örneğin, bu dizeyi içeren bir metin arabelleği göz önünde bulundurun:  
  
```  
abcdefghij  
```  
  
 İki düzenlemeler, yayılma, yerini alan bir düzen içeren bir işlem uygulama [2..4) karakter kullanarak `X` ve aralık, yerini alan ikinci bir düzenleme [6..9) karakter kullanarak `Y`. Bu arabellek oluşur:  
  
```  
abXefYj  
```  
  
 İlk düzenleme uygulanmadan önce koordinatları ikinci düzenleme için işlemin başında arabellek içeriği göre hesaplanan.  
  
 Arabellek değişikliklerin zaman <xref:Microsoft.VisualStudio.Text.ITextEdit> nesne kabul edilen çağırarak kendi `Apply()` yöntemi. En az bir boş olmayan Düzen ise yeni bir <xref:Microsoft.VisualStudio.Text.ITextVersion> , yeni bir oluşturulan <xref:Microsoft.VisualStudio.Text.ITextSnapshot> oluşturulur ve bir `Changed` olayı oluşturulur. Her metin farklı bir sürümde metin anlık görüntü. Metin anlık bir düzenleme işlemi sonra tam metin arabelleğini durumunu temsil eder, ancak yalnızca bir anlık görüntüsünden sonraki değişiklikler metin sürümünü açıklar. Genel olarak, metin anlık görüntüleri için bir kez kullanılması amaçlanmıştır ve atılan, metin sürümleri için biraz zaman canlı kalmasını gerekir.  
  
 Bir metin sürümünü içeren bir <xref:Microsoft.VisualStudio.Text.INormalizedTextChangeCollection>. Bu koleksiyon değişiklikleri açıklar, anlık görüntüye uygulandığında, sonraki anlık görüntü oluşturur. Her <xref:Microsoft.VisualStudio.Text.ITextChange> koleksiyonda karakter konumunu değiştirme, değiştirilen dizeye ve değiştirme dizesi içerir. Değiştirilen temel bir ekleme için boş bir dizedir ve değiştirme dizesi bir temel silme işlemi için boştur. Normalleştirilmiş her zaman koleksiyondur `null` metin arabelleğini en son sürümü için.  
  
 Yalnızca bir <xref:Microsoft.VisualStudio.Text.ITextEdit> nesne oluşturulabilir için bir metin arabelleği dilediğiniz zaman ve tüm metin düzenlemeleri (sahipliği istenmişti varsa) metin arabelleğini sahip olan iş parçacığında gerçekleştirilmesi gerekir. Metin düzenleme çağırarak durdurulmuş, `Cancel` yöntemi veya kendi `Dispose` yöntemi.  
  
 <xref:Microsoft.VisualStudio.Text.ITextBuffer> Ayrıca sağlar `Insert()`, `Delete()`, ve `Replace()` olanlar benzer yöntemler sonucuna <xref:Microsoft.VisualStudio.Text.ITextEdit> arabirimi. Bu çağırma oluşturma aynı etkiye sahip bir <xref:Microsoft.VisualStudio.Text.ITextEdit> nesne, benzer çağrıyı yapan ve ardından düzenleme uygulanıyor.  
  
#### <a name="tracking-points-and-tracking-spans"></a>İzleme noktaları ve izleme alanları  
 Bir <xref:Microsoft.VisualStudio.Text.ITrackingPoint> bir karakter konumunu bir metin arabelleği temsil eder. İzleme noktası ile arabellek kaydırılacak karakterin konumu neden olan bir şekilde düzenlendiğinde, çekirdek yapılandırmasına geçer. Örneğin, bir arabellek konumunu 10 izleme noktasını belirtir ve arabellek başında eklenen beş karakterler, izleme noktası sonra 15 konuma başvuruyor. Tam olarak izleme noktası tarafından belirtilen konumda bir ekleme olursa davranışını tarafından belirlenir, <xref:Microsoft.VisualStudio.Text.PointTrackingMode>, olabilen ya da `Positive` veya `Negative`. İzleme modunu pozitif ise, izleme noktası ekleme sonunda sunulmuştur aynı karakterle başvuruyor; İzleme noktası izleme modunu negatif ise, özgün konumunda eklenen ilk karakteri başvurur. İzleme noktası tarafından temsil edilen konumunda bulunan karakteri silinirse, silinen aralığı izleyen ilk karaktere İzleme noktası kaydırır. Örneğin, bir izleme noktasına 5 konumunda bulunan karakteri ifade eder ve 3'ten 6 konumlarda karakterler silinir, izleme noktası 3 konumunda bulunan karakteri ifade eder.  
  
 Bir <xref:Microsoft.VisualStudio.Text.ITrackingSpan> bir dizi karakter yerine yalnızca bir konumu temsil eder. Davranışını tarafından belirlenen kendi <xref:Microsoft.VisualStudio.Text.SpanTrackingMode>. Aralık izleme modunu ise <xref:Microsoft.VisualStudio.Text.SpanTrackingMode>, aralık izleme modunu ise kenarlarını; eklenen metin birleştirmek için izleme aralığı büyüdükçe <xref:Microsoft.VisualStudio.Text.SpanTrackingMode>, izleme aralığı kenarlarını eklenen metin birleşmez. Ancak aralık izleme modunu ise <xref:Microsoft.VisualStudio.Text.SpanTrackingMode>, ekleme geçerli konumun doğru başlangıç, gönderim ve aralık izleme modunu <xref:Microsoft.VisualStudio.Text.SpanTrackingMode>, sonuna doğru geçerli konum bir ekleme iter.  
  
 İzleme noktası konumunu veya bir izleme aralığı aralık için metin arabelleği ait oldukları herhangi bir anlık görüntüyü alabilirsiniz. İzleme noktaları ve izleme yayılma, herhangi bir iş parçacığından güvenli bir şekilde başvurulabilir.  
  
#### <a name="content-types"></a>İçerik türleri  
 İçerik türleri, farklı içerik türleri tanımlamak için bir mekanizması mevcuttur. Bir içerik türü "metin", "code" veya "ikili" gibi bir dosya türü veya "xml", "vb" veya "c#" gibi bir teknoloji türü olabilir. Örneğin, word "kullanarak" hem C# ve Visual Basic'te, ancak diğer programlama dillerinin bir anahtar sözcüktür. Bu nedenle, bu anahtar sözcüğünün tanımını "c#" ve "vb" içerik türleri için sınırlı olacaktır.  
  
 İçerik türleri, kenarlıklar ve diğer öğeleri Düzenleyicisi için filtre olarak kullanılır. Birçok Düzenleyicisi özellikleri ve uzantı noktaları içerik türü tanımlanır; Örneğin, metin renklendirmesi düz metin dosyaları, XML dosyalarını ve Visual Basic kaynak kodu dosyaları için farklıdır. Metin arabelleği, genellikle bunlar oluşturulur ve bir metin arabelleği içerik türü değiştirilebilir bir içerik türü atanır.  
  
 İçerik türleri birden çok-içerik diğer türlerden devralabilir. <xref:Microsoft.VisualStudio.Utilities.ContentTypeDefinition> Üst öğelerinin belirli bir içerik türü birden çok temel tür belirtmenize olanak tanır.  
  
 Geliştiriciler kendi içerik türlerini tanımlayın ve bunları kullanarak kaydetme <xref:Microsoft.VisualStudio.Utilities.IContentTypeRegistryService>. Birçok düzenleyici özellikleri kullanarak belirli bir içerik türüne göre tanımlanabilir <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>. Bunlar belirli içerik türlerini görüntülemek düzenleyiciler için geçerli olacak şekilde, örneğin, düzenleyici kenar boşlukları ve Kenarlıklar fare işleyicileri tanımlanabilir.  
  
###  <a name="textview"></a> Metin görünümü  
 Model görünüm denetleyicisi (MVC) deseni görünümü parçası biçimlendirme görünüm, kaydırma çubuğu ve giriş işaretini gibi grafik öğeleri metin görünümünü tanımlar. Visual Studio Düzenleyicisi tüm sunum öğelerini, WPF, temel alır.  
  
#### <a name="text-views"></a>Metin görünümleri  
 <xref:Microsoft.VisualStudio.Text.Editor.ITextView> Metni görünümü platformdan bağımsız gösterimini arabirimidir. Öncelikli olarak metin belgeleri bir pencerede görüntülemek için kullanılır, ancak bu aynı zamanda başka bir amaçla Örneğin, bir araç ipucunda kullanılabilir.  
  
 Metin arabelleği farklı türde metin görünümünü başvuruyor. <xref:Microsoft.VisualStudio.Text.Editor.ITextView.TextViewModel%2A> Özelliği başvurduğu bir <xref:Microsoft.VisualStudio.Text.Editor.ITextViewModel> için bu üç farklı metin arabelleği işaret eden bir nesne: üst veri düzeyi arabellek düzenlemenin gerçekleşir ve, arabellek visual arabellek düzenleme arabelleği veri arabelleği Metin Görünümü'nde görüntülenir.  
  
 Metin için temel alınan metin arabelleğini bağlı sınıflandırıcılar göre biçimlendirilir ve metin görünümünü kendisine bağlı kenarlığı sağlayıcılarını kullanarak donatılmış.  
  
#### <a name="the-text-view-coordinate-system"></a>Metin görünümü koordinat sistemi  
 Metin görünümünü konumda metin görünümü koordinat sistemini belirtir. Bu koordinat sistemini x değeri 0,0 görüntülenen metnin sol kenarına karşılık gelir ve y değeri 0,0 görüntülenen metin üst kenarına karşılık gelir. X koordinatı soldan sağa artırır ve y koordinatı üstten alta artırır.  
  
 Dikey olarak kaydırılan gibi bir Görünüm penceresi (metin penceresinde görünen metin parçası) aynı şekilde yatay olarak kaydırılan olamaz. Bir görünüm penceresinin sol alt koordinat çizim yüzeyi göre hareket değiştirerek yatay olarak kaydırılan. Ancak, bir görünüm penceresinin dikey olarak yalnızca neden olur işlenen metni değiştirerek kaydırılabileceğini bir <xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged> olay oluşturulur.  
  
 Uzaklıkları koordinat sisteminde mantıksal piksele karşılık gelir. Metin işleme yüzeyi ölçekleme dönüşümü gösterilirse, ardından metin işleme koordinat sisteminde bir birimi bir piksel ekranındaki karşılık gelir.  
  
#### <a name="margins"></a>Kenar boşlukları  
 <xref:Microsoft.VisualStudio.Text.Editor.ITextViewMargin> Arabirimi kenar boşluğu temsil eder ve kenar boşluğu bırakma ve boyutunu görünürlüğünü denetimini etkinleştirir. Üst, alt, sol veya sağ kenarı bir görünümünün eklenir ve "Üst", "Sol", "Sağ" ve "Alt" adlı dört önceden tanımlanmış kenar vardır. Bu kenar boşlukları başka kenar boşlukları yerleştirilebilir kapsayıcılardır. Kenar boşluğu boyutu ve kenar boşluğu görünürlüğünü döndüren yöntemler arabirimi tanımlar. Kenar boşlukları, bağlı metin görünümünü hakkında ek bilgiler sağlayan visual öğeleridir. Örneğin, satır numarası kenar boşluğunu metin görünümünü için satır numaralarını görüntüler. Simge kenar boşluğu kullanıcı Arabirimi öğeleri görüntüler.  
  
 <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewMarginProvider> Arabirimi oluşturulmasını ve kenar boşlukları yerleşimini işler. Kenar boşlukları başka kenar boşlukları göre sıralanabilir. Daha yüksek öncelikli kenar boşlukları için metin görünümünü bir yakın olarak yer alır. Örneğin, iki sol kenar, kenar boşluğuna ve kenar boşluğu B vardır ve kenar boşluğu B kenar boşluğuna daha düşük önceliğe sahiptir, sol kenar boşluğu A. B kenar boşluğu görünür  
  
#### <a name="the-text-view-host"></a>Metin görünümü ana bilgisayarı  
 <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewHost> Metni görünümü ve görünüm, örneğin, kaydırma çubukları eşlik eden herhangi bir bitişik süslemeleri arabirimi içerir. Metin görünümü ana görünümün kenarlık bağlı kenar boşlukları da içerir.  
  
#### <a name="formatted-text"></a>Biçimlendirilmiş metin  
 Bir metin görünümünde görüntülenen metni oluşan <xref:Microsoft.VisualStudio.Text.Formatting.ITextViewLine> nesneleri. Her metin görünümünü satır tek satırlık bir metin görünümünde metin karşılık gelir. Temel alınan metin arabelleğinde uzun satırları kısmen (sözcük kaydırma etkin değilse) engellediği veya birden çok metin görünümünü satırlara ayrılmış. <xref:Microsoft.VisualStudio.Text.Formatting.ITextViewLine> Yöntemleri ve özellikleri satırla ilişkili Kenarlıklar ve koordinatları karakterleri arasında eşleme için arabirimi içerir.  
  
 <xref:Microsoft.VisualStudio.Text.Formatting.ITextViewLine> nesneleri kullanılarak oluşturulan bir <xref:Microsoft.VisualStudio.Text.Formatting.IFormattedLineSource> arabirimi. Yalnızca şu anda görünümünde görüntülenen metin hakkında endişe biçimlendirme kaynak yoksayabilirsiniz. Olmayan metin biçiminde ilgileniyorsanız (örneğin destekleyen bir zengin metin Kes ve Yapıştır,), görünümünde görüntülenen kullanabileceğiniz <xref:Microsoft.VisualStudio.Text.Formatting.IFormattedLineSource> biçim metni metin arabelleği.  
  
 Bir metin görünümünü biçimleri <xref:Microsoft.VisualStudio.Text.ITextSnapshotLine> birer güncelleştirir.  
  
## <a name="editor-features"></a>Düzenleyici Özellikleri  
 Düzenleyici özelliklerini özellik tanımı, uygulamadan ayrı şekilde tasarlanmıştır. Düzenleyici, şu özellikleri içerir:  
  
-   Etiketleri ve sınıflandırıcı  
  
-   Kenarlıklar  
  
-   Projeksiyon  
  
-   Anahat Oluşturma  
  
-   Fare ve anahtar bağlamaları  
  
-   İşlemler ve temelleri  
  
-   IntelliSense  
  
###  <a name="tagsandclassifiers"></a> Etiketleri ve sınıflandırıcı  
 Etiketler, metin aralığı ile ilişkili olan işaretleyicileri şunlardır. Bunlar farklı yollarla, örneğin, metin renklendirme, alt çizgiler, grafik veya açılır pencereleri kullanarak sunulabilir. Etiketi bir tür sınıflandırıcıdır.  
  
 Etiketleri diğer türde <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag> Metin vurgulama için <xref:Microsoft.VisualStudio.Text.Tagging.OutliningRegionTag> anahat oluşturma için ve <xref:Microsoft.VisualStudio.Text.Tagging.ErrorTag> derleme hataları.  
  
#### <a name="classification-types"></a>Sınıflandırma türleri  
 Bir <xref:Microsoft.VisualStudio.Text.Classification.IClassificationType> arabirimi soyut bir kategori metnin bir denklik sınıfı temsil eder. Sınıflandırma türleri birden çok-diğer sınıflandırma türlerden devralabilir. Örneğin, programlama dili sınıflandırmalar "anahtar sözcüğü", "Açıklama" ve "tanımlayıcı", "code" devralan tüm hangi içerebilir. "Ad", "eylem" ve "sıfat", "doğal dili" devralan tüm, doğal dil sınıflandırma türleri içerebilir.  
  
#### <a name="classifications"></a>Sınıflandırmalar  
 Bir sınıflandırma belirli bir sınıflandırma türü, genellikle metnin bir aralığı örneğidir. A <xref:Microsoft.VisualStudio.Text.Classification.ClassificationSpan> bir sınıflandırma temsil etmek için kullanılır. Sınıflandırma yayılma, belirli bir metin aralığını kapsar ve bu aralığa metnin belirli bir sınıflandırma türü olan bir sisteme söyler etiket olarak düşünülebilir.  
  
#### <a name="classifiers"></a>Sınıflandırıcı  
 Bir <xref:Microsoft.VisualStudio.Text.Classification.IClassifier> sınıflandırmaları kümesine metni keser mekanizmadır. Sınıflandırıcı belirli içerik türleri için tanımlanan ve örneği için belirli bir metin arabelleği. İstemciler uygulanmalı <xref:Microsoft.VisualStudio.Text.Classification.IClassifier> metin sınıflandırma katılmak için.  
  
#### <a name="classifier-aggregators"></a>Sınıflandırıcı toplayıcılardan verileri  
 Bir sınıflandırıcı toplayıcısı sınıflandırmaları tek kümesine bir metin arabelleği için tüm sınıflandırıcılar birleştiren bir mekanizmadır. Örneğin, hem C# sınıflandırıcı hem de İngilizce sınıflandırıcı C# dosyasında bir yorum üzerinden sınıflandırmaları oluşturabilirsiniz. Bu açıklamayı göz önünde bulundurun:  
  
```  
// This method produces a classifier  
```  
  
 C# sınıflandırıcı yorum olarak tüm aralık etiketi ve İngilizce sınıflandırıcı "oluşturan" bir "eylem" ve "ad" olarak "yöntemi" olarak sınıflandırmak. Toplayıcı sınıflandırmaları çakışmayan bir dizi oluşturur ve küme türünü tüm katkılar dayanır.  
  
 Sınıflandırmaları kümesine metin bozacağı sınıflandırıcı toplayıcısı ayrıca bir sınıflandırıcıdır. Sınıflandırıcı toplayıcısı ayrıca hiçbir çakışan sınıflandırmaları vardır ve sınıflandırmaları sıralanır sağlar. Tek tek sınıflandırıcılar, herhangi bir sırada Sınıflandırmalar, herhangi bir dizi döndürmek ücretsiz ve herhangi bir şekilde çakışan.  
  
#### <a name="classification-formatting-and-text-coloring"></a>Sınıflandırma biçimlendirme ve metin renklendirmesi  
 Metin biçimlendirme bir metin sınıflandırmasına yerleşik bir özellik örneğidir. Metin görünümü katmanı tarafından bir uygulamada metin görünümünü belirlemek için kullanılır. WPF, metin biçimlendirme alanına bağlıdır, ancak sınıflandırmalar mantıksal tanımı değil.  
  
 Belirli bir sınıflandırma türünün özellikleri biçimlendirme kümesi bir sınıflandırma biçimidir. Bu biçimler üst sınıflandırma türünün biçiminden devralır.  
  
 Bir <xref:Microsoft.VisualStudio.Text.Classification.IClassificationFormatMap> metin özellikleri biçimlendirme kümesi için bir sınıflandırma türünden bir eşlemesi. Sınıflandırma biçimlerinin dışarı aktarmaları uygulaması Düzenleyicisi'nde biçim eşlemesi işler.  
  
###  <a name="adornments"></a> Kenarlıklar  
 Kenarlıklar doğrudan metin görünümünü karakterleri rengini ve yazı tipi için ilgili olmayan grafik efektleri ' dir. Örneğin, çok sayıda programlama dilinde kod derlerken işaretlemek için kullanılan bir kırmızı dalgalı çizgi katıştırılmış bir kenarlığı olan ve açılır Kenarlıklar araç ipuçları şunlardır. Kenarlıklar türetilir <xref:System.Windows.UIElement> ve uygulama <xref:Microsoft.VisualStudio.Text.Tagging.ITag>. İki özel türler kenarlığı etiketinin <xref:Microsoft.VisualStudio.Text.Tagging.SpaceNegotiatingAdornmentTag>, metni bir görünüm olarak aynı alanı kaplayan kenarlıkları için ve <xref:Microsoft.VisualStudio.Text.Tagging.ErrorTag>, dalgalı çizgi için.  
  
 Katıştırılmış Kenarlıklar biçimlendirilmiş metin görünümünü parçasını grafiklerdir. Bunlar farklı Z düzenini katmanlarında düzenlenir. Üç yerleşik Katmanlar vardır: metin, giriş işaretini ve seçimi. Ancak, geliştiricilerin daha fazla katman tanımlayabilir ve bunları birbirine göre sırayla yerleştirebilirsiniz. (Metin silindiğinde, çalıştırdığınız ve metin hareket ettiğinde taşıma silinir) metin göreli Kenarlıklar ve (hangi görünümün metin olmayan bölümleriyle yapmak zorunda) görünümü-göreli Kenarlıklar sahibi tarafından denetlenen Kenarlıklar (embedded Kenarlıklar üç tür olan Geliştirici oluşuturun yönetmeniz gerekir).  
  
 Açılır Kenarlıklar metin görünümü, örneğin, araç ipuçları yukarıda küçük bir pencerede görünen grafiklerdir.  
  
###  <a name="projection"></a> Projeksiyon  
 Projeksiyon, gerçekte metin depolamaz, ancak bunun yerine diğer metin arabelleği metinleri birleştiren metin arabelleğini farklı bir tür oluşturmak için kullanılan bir tekniktir. Örneğin, bir projeksiyon arabellek diğer arabellekler iki metinden birleştirmek ve tek bir arabellek grubundaymış gibi sonucu sunmak için veya bir arabellek metin parçalarını gizlemek için kullanılabilir. Bir projeksiyon arabellek başka bir projeksiyon arabelleğe kaynak arabelleği üstlenebilir. Bir projeksiyon ile ilgili arabelleklerinin metin birçok farklı şekilde yeniden düzenlemek için oluşturulabilir. (Böyle bir küme olarak da bilinen olduğu bir *arabellek grafik*.) Daraltılmış metin gizlemek için bir yansıtma arabelleği kullanarak Visual Studio metin anahat oluşturma özelliğini uygulanır ve ASP.NET sayfaları için Visual Studio Düzenleyicisi, Visual Basic ve C# gibi katıştırılmış dilleri desteklemek için yansıtma kullanır.  
  
 Bir <xref:Microsoft.VisualStudio.Text.Projection.IProjectionBuffer> kullanılarak oluşturulan <xref:Microsoft.VisualStudio.Text.Projection.IProjectionBufferFactoryService>. Bir projeksiyon arabellek sıralı bir dizi tarafından temsil edilen <xref:Microsoft.VisualStudio.Text.ITrackingSpan> olarak bilinen nesneleri *kaynak yayılmaları*. Bu alanı, içeriğini, bir karakter dizisi sunulur. İçinden kaynak yayılmaları çizilmiştir metin arabelleği adlı *kaynak arabelleği*. İstemciler bir projeksiyon arabellek bir normal metin arabelleğinden farklı haberdar olmanız gerekmez.  
  
 Projeksiyon arabellek kaynak arabelleklerini metin değişikliği olaylarını dinler. Bir kaynak metin span değiştiğinde, projeksiyon arabellek değiştirilen metin koordinatları kendi koordinatlarına eşler ve uygun metin değişikliği olaylarını oluşturur. Örneğin, bu içeriğe sahip olan kaynak arabelleklerini A ve B göz önünde bulundurun:  
  
```  
A: ABCDE  
B: vwxyz  
```  
  
 İki metin yayılma bir arabellek bir ve tüm içeren diğer tüm B, arabelleğin sahip projeksiyon arabellek P biçimlendirilmiş, P aşağıdaki içeriğe sahip:  
  
```  
P: ABCDEvwxyz  
```  
  
 Varsa alt dizeyi `xy` arabellek B, P arabellek karakterleri 7 ve 8 konumlarda silindiğini belirtir bir olay oluşturur silinir.  
  
 Projeksiyon arabellek de doğrudan düzenlenebilir. Bu, uygun kaynak arabelleklerini düzenlemeleri yayar. Örneğin, bir dize arabelleğine P 6 ("v" karakteriyle özgün konum) konumunda eklediyseniz, 1 konumunda B arabelleğine ekleme yayılır.  
  
 Bir projeksiyon arabelleğe katkıda kaynak yayılmaları kısıtlamalar vardır. Kaynak yayılmaları çakışmaması; bir projeksiyon arabellek konumu birden fazla konumda herhangi bir kaynak arabelleği eşlenemez ve kaynak arabelleği bir konumda bir projeksiyon arabellek birden fazla konumda eşlenemez. Kaynak arabelleği ilişkide hiçbir circularities izin verilir.  
  
 Bir projeksiyon arabellek değişikliklerin ve kaynak kümesi değişiklikleri yayıldığında kaynak kümesini arabelleği olaylar oluşturulur.  
  
 Eleme arabellek projeksiyon arabellek özel türüdür. Öncelikle, anahat oluşturma ve genişletme ve daraltma metin bloklarını işlemleri için kullanılır. Yalnızca bir kaynak arabelleği eleme arabellek temel alır ve kaynak arabellekteki göre sıralı olarak eleme arabellekteki yayılma aynı sıralanmış olmaları gerekmektedir.  
  
##### <a name="the-buffer-graph"></a>Arabellek grafiği  
 <xref:Microsoft.VisualStudio.Text.Projection.IBufferGraph> Arabirimi projeksiyon arabellek bir grafik arasında eşleme sağlar. Tüm projeksiyon arabellekleri ve metin arabelleği çok bir dil derleyicisi tarafından üretilen soyut sözdizimi ağacını gibi yönlendirilmiş Çevrimsiz grafik toplanır. Graf, herhangi bir metin arabelleği olabilecek en üst arabellek tarafından tanımlanır. Arabellek grafı kaynak arabelleği bir noktaya en üst arabellek nokta veya bir dizi yayılma kaynak arabellekteki en üst arabellek yayılımda eşleyebilirsiniz. Benzer şekilde, eşleme bir noktası veya kaynak arabelleğinden bir noktaya en üst arabellek span yükleyebilir. Arabellek grafikleri kullanılarak oluşturulan <xref:Microsoft.VisualStudio.Text.Projection.IBufferGraphFactoryService>.  
  
##### <a name="events-and-projection-buffers"></a>Olayları ve projeksiyon arabellekler  
 Bir projeksiyon arabellek değiştirildiğinde, değişikliklerin bağımlı arabellekler projeksiyon arabelleğinden gönderilir. Tüm arabellekler değiştirildikten sonra en derin arabellek ile başlayan arabelleği değişikliği olaylar oluşturulur.  
  
###  <a name="outlining"></a> Anahat oluşturma  
 Anahat oluşturma genişletmek veya daraltmak için farklı bir metin görünümündeki metin bloklarını yeteneğidir. Anahat oluşturma türü olarak tanımlanmış, <xref:Microsoft.VisualStudio.Text.Tagging.ITag>, aynı şekilde kenarlıkları tanımlanmış gibi. A <xref:Microsoft.VisualStudio.Text.Tagging.OutliningRegionTag> genişletilmiş veya daraltılmış bir metin bölge tanımlayan bir etikettir. Anahat oluşturma kullanmak için aktarmalısınız <xref:Microsoft.VisualStudio.Text.Outlining.IOutliningManagerService> almak için bir <xref:Microsoft.VisualStudio.Text.Outlining.IOutliningManager>. Anahat oluşturma manager sıralar, daraltır ve olarak temsil edilen farklı bloklarını genişletir <xref:Microsoft.VisualStudio.Text.Outlining.ICollapsible> nesneleri ve olayları buna uygun olarak oluşturur.  
  
###  <a name="mousebindings"></a> Fare bağlamaları  
 Fare bağlamaları için farklı komutlar fare hareketlerini bağlayın. Fare bağlamalar tanımlandı kullanarak bir <xref:Microsoft.VisualStudio.Text.Editor.IMouseProcessorProvider>, ve tuş bağlamaları kullanılarak tanımlanmış bir <xref:Microsoft.VisualStudio.Text.Editor.IKeyProcessorProvider>. <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewHost> Otomatik olarak tüm bağlantıları başlatır ve fare olayları görünümünde bağlanır.  
  
 <xref:Microsoft.VisualStudio.Text.Editor.IMouseProcessor> Arabirimi farklı fare olayları için önceden işleme ve işlem sonrası olay işleyicilerini içerir. Bazı yöntemleri geçersiz olaylardan biri için tanıtıcı <xref:Microsoft.VisualStudio.Text.Editor.MouseProcessorBase>.  
  
###  <a name="editoroperations"></a> Düzenleyici işlemleri  
 Komut Dosyası Düzenleyicisi veya başka amaçlarla etkileşim otomatik hale getirmek için düzenleyici işlemleri kullanılabilir. İçeri aktarabilirsiniz <xref:Microsoft.VisualStudio.Text.Operations.IEditorOperationsFactoryService> erişim işlemleri için bir verilen <xref:Microsoft.VisualStudio.Text.Editor.ITextView>. Ardından bu nesneleri giriş işaretini görünümün farklı bölümlerine Taşı, görünümü kaydırarak ya da seçimi değiştirmek için de kullanabilirsiniz.  
  
###  <a name="intellisense"></a> IntelliSense  
 IntelliSense deyim tamamlama, imza Yardımı (parametre bilgisi olarak da bilinir), hızlı bilgi ve ampuller destekler.  
  
 Deyim tamamlama açılır listesi yöntem adları, XML ve diğer biçimlendirme kodlama veya öğeler için olası tamamlamaları sağlar. Genel olarak, bir kullanıcı hareketi tamamlama oturumu çağırır. Oturum olası listesini görüntüler ve kullanıcının birini seçebilmesi veya listeyi kapatın. <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionBroker> Oluşturma ve tetikleme sorumlu <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSession>. <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource> Hesaplar <xref:Microsoft.VisualStudio.Language.Intellisense.CompletionSet> oturumu için tamamlanma öğesi.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Dil hizmeti ve düzenleyici uzantı noktaları](../extensibility/language-service-and-editor-extension-points.md)   
 [Düzenleyici İçeri Aktarımları](../extensibility/editor-imports.md)

