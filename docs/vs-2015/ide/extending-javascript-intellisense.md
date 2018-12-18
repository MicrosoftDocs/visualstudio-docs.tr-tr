---
title: JavaScript IntelliSense genişletme | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- JavaScript, intellisense object
- extending JavaScript IntelliSense
- customizing JavaScript IntelliSense
- JavaScript, extending IntelliSense
- IntelliSense [JavaScript], extending
ms.assetid: 004e1ab6-bd7a-4327-9e01-89b9be96ba2f
caps.latest.revision: 43
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 239416a1638940207a8dcb78b395ed1915e8a93a
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49867084"
---
# <a name="extending-javascript-intellisense"></a>JavaScript IntelliSense Genişletme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

JavaScript IntelliSense genişletilebilirlik özelliği, üçüncü taraf kitaplıklar için JavaScript Düzenleyicisi IntelliSense sonuçlarında özelleştirmenizi sağlar. Bu, bu kitaplıkları kullanan geliştiriciler deneyimini geliştirebilir.  
  
 JavaScript dil servisi, bir projeye eklenen üçüncü taraf JavaScript kitaplıkları için IntelliSense özellikleri sağlar. Çoğu kitaplık için deyim tamamlama dil hizmeti tarafından otomatik olarak sağlanır. Deyim tamamlama örneği aşağıda gösterilmiştir:  
  
 ![Deyim tamamlama örneği](../ide/media/js-intellisense-completion.png "js_intellisense_completion")  
  
 Kitaplığınızı standart JavaScript açıklama etiketleri açıklamalarını değişkenler, İşlevler ve nesneler içeriyorsa (/ /), size otomatik olarak, varsayılan olarak açılan kutusuna açıklayıcı bilgiler sağlayan IntelliSense genişletilebilirlik özelliği yararlanın Tamamlanma listesi veya bir işlev çağrısı parantez yazdığında öğeleri sağında görünür. Açılır kutu açıklamalarda, üye açıklamasını içerir. Aşağıdaki örnek, tamamlanma listesi açılır kutusunu gösterir.  
  
 ![Hızlı bilgi pop örneği&#45;kutusunu](../ide/media/js-intellisense-quickinfo.png "js_intellisense_quickinfo")  
  
 Daha fazla Geliştirici deneyimini iyileştirmek için açılır kutusunda geliştiriciler tür bilgileri sağlamak isteyebilirsiniz. JavaScript kullanarak tür bilgilerini sağlayabilir [XML belgeleri yorumları](../ide/xml-documentation-comments-javascript.md) standart yorum etiketleri yerine. XML belgeleri yorumları, üç eğik çizgi açıklama etiketleri (/ / /) ve bir dizi tanımlanmış XML öğeleri kullanılarak ekleyin.  
  
 Alternatif olarak, JavaScript IntelliSense genişletilebilirliği kullanarak tür bilgilerini sağlayabilir. Bu özellik, JavaScript uzantıları oluşturma ve bunları komut dosyası bağlamınızla ekleyerek IntelliSense sonuçları özelleştirmenize olanak sağlar. Tarafından kullanıma sunulan olaylara abone olan bir JavaScript dosyası uzantısında `intellisense` dil hizmetinin nesne. JavaScript IntelliSense genişletilebilirlik tercih edilen kitaplıkları için bir davranış desen Kitaplığı'nda JavaScript dil servisi IntelliSense desteği düzeyinde vermesini engeller ve alternatif, bildirim temelli XML çözümüdür Belge açıklamaları da gerekir. IntelliSense sonuçları özelleştirerek dil hizmet varsayılan özelliklerine kısıtlayabilir tüm davranış kalıplarını bağımsız olarak birinci sınıf bir IntelliSense deneyimi oluşturabilirsiniz. Daha fazla bilgi için [tanımlayıcılar için ifade tamamlama](../ide/statement-completion-for-identifiers.md).  
  
## <a name="adding-an-extension-to-the-script-context"></a>Betik bağlamı için bir uzantı ekleme  
 IntelliSense uzantı yürütülecek, geçerli komut dosyası bağlamınızla eklenmesi gerekir. Uzantı otomatik olarak komut dosyası bağlamınızla tarafından otomatik bulma mekanizmasından eklenebilir veya uzantı komut dosyası bağlamınızla el ile başvuru grupları veya başvuru yönergesi'nı kullanarak ekleyebilirsiniz.  
  
 Otomatik bulma mekanizmasından dosya adlandırma kuralını uyguladığınızdan uzantıları otomatik olarak bulmak dil hizmeti sağlayan *libraryname*. intellisense.js ve kitaplığa ile aynı dizinde bulunur Uzantı geçerli. Örneğin, jQuery kitaplığı için geçerli bir uzantı jQuery.intellisense.js olacaktır. Daha kısıtlayıcı jQuery uzantıları için jQuery-1.7.1.intellisense.js (sürüm özgü bir uzantı) veya jQuery.ui.intellisense.js (kapsamlı jQuery kitaplığı için bir uzantı) gibi dosya adlarını kullanabilirsiniz. Belirli bir kitaplık için birden fazla uzantı bulunursa uzantısının en kısıtlayıcı sürümü kullanılır.  
  
 Uzantı için tüm JavaScript proje dosyalarını kullanmak istiyorsanız, bunun yerine uzantısı için başvuru grubu eklemek seçebilirsiniz. Başvuru grupları; ya da örtük bir başvuru içeren ve adanmış çalışan başvuru içeren birkaç türü vardır. Bir uzantı eklemek için genellikle bir örtük bir başvuru grubu ya da dosya ekleme ihtiyacınız **örtük (Windows)**, **örtük (Web)**. Örtük başvuruda Kod Düzenleyicisi'nde açılan her .js dosyası için kapsamına dahildir. Bu yöntemi kullandığınızda, uzantısı ve uzantı ekleme dosyası eklemeniz gerekir.  
  
 Kullanım **IntelliSense** sayfasının **seçenekleri** uzantı başvuru grubu eklemek için iletişim kutusu. Erişebildiğiniz **IntelliSense** seçerek sayfası **Araçları**, **seçenekleri** menü çubuğu ve açıp **metin düzenleyici**, **JavaScript**, **IntelliSense**, **başvuruları**. Başvuru grupları hakkında daha fazla bilgi için bkz. [JavaScript IntelliSense](../ide/javascript-intellisense.md) ve [seçenekler, metin düzenleyici, JavaScript, IntelliSense](../ide/reference/options-text-editor-javascript-intellisense.md).  
  
 Belirli bir dosya kümesi için uzantıyı kullanmak istiyorsanız, bir başvuru yönergesini kullanın. Bu yöntemi kullandığınızda, hem genişletme hem de dosyanın uzantısı ekleme başvurmanız gerekir. Başvuru yönergesi kullanma hakkında daha fazla bilgi için bkz: [JavaScript IntelliSense](../ide/javascript-intellisense.md).  
  
## <a name="handling-intellisense-events"></a>IntelliSense olaylarını işleme  
 Genişletilebilirlik özelliği gibi olaylara abone olarak IntelliSense sonuçları özelleştirmenize olanak tanıyan `statementcompletion` olay dil hizmetinin `intellisense` nesne. Aşağıdaki örnek, deyim tamamlama gelen bir alt çizgi ile başlayan üyeler gizlemek için dil hizmeti tarafından kullanılan basit bir uzantıyı gösterir. Bu kod underscorefilter.js içinde yer alır ve içinde \\ \\ *Visual Studio yükleme yolu*\JavaScript\References klasör.  
  
```javascript  
intellisense.addEventListener('statementcompletion', function (event) {  
    if (event.targetName === "this") return;  
  
    var filterRegex;  
  
    if (event.target === undefined || event.target === window)  
        filterRegex = /^_.*\d{2,}/;  
    else  
        filterRegex = /^_.*/;  
  
    event.items = event.items.filter(function (item) {  
        return !filterRegex.test(item.name);  
    });  
});  
```  
  
 Önceki kodda; uzantısını denetler [targetName özelliği](#TargetName) ve [özelliği hedef](#Target) özelliklerini `statementcompletion` nesneleri gibi hariç tutmak için olay nesnesinin `this` ve `window`ve geçerli deyim tamamlanma listesi tanımlanabilir olmasını sağlamak için. Tamamlanma listesi tanımlanabilir, deyim tamamlama uzantı güncelleştirmeleri [özelliği](#Items) bir alt çizgiyle başlayan üyeleri kullanıma filtreleyerek koleksiyonu.  
  
 Diğer örnekler için konum \\ \\ *Visual Studio yükleme yolu*\JavaScript\References klasör. Standart JavaScript açıklama etiketleri için varsayılan IntelliSense desteği sağlamak amacıyla diğer olayları kullanarak örnekler showPlainComments.js dosyayı bu klasöre sağlar (/ /). Underscorefilter.js gibi showPlainComments.js zaten çalışma uzantısı olarak kullanılabilir ve değişkenler, İşlevler ve nesneler için kodunuza açıklama etiketleri kullanırken, IntelliSense bilgilerine görebilirsiniz. Diğer örnekler için [kod örnekleri](#CodeExamples).  
  
> [!WARNING]
>  Visual Studio'ya dahil edildi uzantılarını değiştirirseniz, JavaScript IntelliSense veya uzantı tarafından desteklenen özelliğini devre dışı bırakabilir.  
  
 Uzantı kodunuzu kullanarak aşağıdaki olay türleri için işleyiciler oluşturabilirsiniz `addEventListener`:  
  
- `statementcompletion`, bir deyim tamamlama olayı işleyicisi ekler. Deyim tamamlama bir nokta (.) gibi özel bir karakter yazın sonra görüntülenen belirli bir tür için üye listesi veya yazarken veya CTRL + J. tuşuna bastığınızda görüntülenen tanımlayıcıları listesini sağlar. Bir olay nesne türünde işleyici alır `CompletionEvent`, aşağıdaki üyeleri destekler: [özelliği](#Items), [özelliği hedef](#Target), [targetName özelliği](#TargetName), ve [özelliği kapsam](#Scope).  
  
- `signaturehelp`, IntelliSense parametre bilgisi için bir işleyici ekler. Parametre bilgisi sayısı, adları ve bir işlev için gerekli parametre türleri hakkında bilgi sağlar. Bir olay nesne türünde işleyici alır `SignatureHelpEvent`, aşağıdaki üyeleri destekler: [özelliği hedef](#Target), [parentObject özelliği](#ParentObject), [functionCommentsözelliği](#FunctionComments), [functionHelp özelliği](#FunctionHelp).  
  
- `statementcompletionhint`, IntelliSense hızlı bilgi için bir işleyici ekler. Hızlı bilgi açılır kutunun tam bir bildirim tanımlayıcıları için kodunuzda gösterir. Bir olay nesne türünde işleyici alır `CompletionHintEvent`, aşağıdaki üyeleri destekler: [completionItem özelliği](#CompletionItem), ve [symbolHelp özelliği](#SymbolHelp).  
  
  Deyim tamamlama, parametre bilgileri ve hızlı bilgi gibi IntelliSense özelliklerini gösteren örnekler için bkz [IntelliSense kullanarak](../ide/using-intellisense.md).  
  
> [!NOTE]
>  JavaScript'te hızlı bilgi tamamlanma listesi sağında görünen açılır kutusunda ifade eder. Hızlı Bilgi'yi el ile çağrılamaz.  
  
##  <a name="intellisenseObject"></a> IntelliSense nesnesi  
 Aşağıdaki tablo, kullanılabilen işlevler gösterir `intellisense` nesne. `intellisense` Nesne yalnızca tasarım zamanında kullanılabilir.  
  
|İşlev|Açıklama|  
|--------------|-----------------|  
|`addEventListener(type, handler);`|Bir IntelliSense olay için bir olay işleyicisi ekler.<br /><br /> `type` bir dize değeridir. Geçerli değerler `statementcompletion`, `signaturehelp`, ve `statementcompletionhint`.<br /><br /> `handler` şu türlerden birinde bir olay nesnesi alan bir olay işleyici işlevi şöyledir:<br /><br /> -   `CompletionEvent`, kullanılan `statementcompletion` olay.<br />-   `SignatureHelpEvent`, kullanılan `signaturehelp` olay.<br />-   `CompletionHintEvent`, kullanılan `statementcompletionhint` olay.<br /><br /> Bu işlev kullanan örnekler için bkz [kod örnekleri](#CodeExamples).|  
|`annotate(obj, doc);`|Belge yorumlarını bir nesneden kopyalayarak başka bir nesneye bir nesne için belgeleri belirtir.<br /><br /> `obj` belgeleri kopyalanacağı nesneyi belirtir.<br /><br /> `doc` belgeleri kopyalanacak nesnesini belirtir.<br /><br /> Bu işlevin nasıl kullanılacağını gösteren bir örnek için bkz: [IntelliSense ek açıklamaları ekleme](#Annotations).|  
|`getFunctionComments(func);`|Belirtilen işlev için açıklamalar döndürür.<br /><br /> `func` Açıklamalar döndürülen işlevi belirtir.<br /><br /> Ayarlayabileceğiniz `func` kullanarak parametre `completionItem.value`.<br /><br /> Döndürülen `functionComments` nesne aşağıdaki üyeleri içerir: `above`, `inside`, ve `paramComment`. Daha fazla bilgi için [functionComments özelliği](#FunctionComments) özelliği.<br /><br /> `getFunctionComments` yalnızca biri tarafından kaydedilen olay işleyicileri içinde çağrılabilir `addEventListener`.<br /><br /> Bu işlevin nasıl kullanılacağını gösteren bir örnek için bkz: \\ \\ *Visual Studio yükleme yolu*\JavaScript\References\showPlainComments.js.|  
|`logMessage(msg);`|Tanılama iletilerini çıkış penceresine gönderir.<br /><br /> `msg` iletisini içeren bir dizedir.<br /><br /> Bu işlevin nasıl kullanılacağını gösteren bir örnek için bkz: [gönderme iletilerini çıkış penceresine](#Logging).|  
|`nullWithCompletionsOf(value);`|Kendisi için tamamlanma listesi tarafından belirlenir geçirilen nesne özel bir null değeri döndürür `value` parametresi.<br /><br /> `value` döndürülen değer için tamamlanma listesini belirler. `value` herhangi bir tür olabilir.<br /><br /> Null dönüş değeri tasarım zamanında null olarak kabul edilir, ancak dönüş değeri için tamamlanma listesi için tamamlanma listesini aynıdır `value` parametresi.<br /><br /> Bu işlev bir kullanım içindir dönüş türü, çalışma zamanında tahmin edilebilir, ancak dönüş değeri, dönüş değeri için IntelliSense sağlamak üzere `null` tasarım zamanında.|  
|`redirectDefinition(func, definition);`|IntelliSense için belirtilen tanım işlevi parametre Yardımı özgün func işlevi yerine kullanacağınız bildirir veya **tanıma** istenir.<br /><br /> `func` Hedef işlevi belirtir.<br /><br /> `definition` işlevi için parametre bilgileri hedef işlevi yerine kullanılacak belirtir ve **tanıma**.|  
|`setCallContext(func, thisArg);`|Arama bağlamı veya belirtilen işlev için bir kapsam belirler.<br /><br /> `func` kapsamını ayarlamak istediğiniz işlevi belirtir.<br /><br /> `thisArg` bir nesne sabit değeri olan `this` anahtar sözcüğünün başvurabileceği için yeni üye kapsamını belirtir. Örneğin bu parametrede geçirilecek bağımsız değişkenleri içerebilir, `intellisense.setCallContext(func, { thisArg: "", args: [23,2] });`<br /><br /> `setCallContext` benzer şekilde davranış sağlar `Function.prototype.bind`dışında yalnızca tasarım zamanı IntelliSense desteği için kullanılır. Kullanabileceğiniz `setCallContext` işlev çağırdığınızda, aksi takdirde ulaşılabilir değil, kod için bir arama benzetimi gerçekleştirmesi gerekiyorsa işlevi kapsamını ayarlamak için işlev çağrısının bağımsız değişkenleri ve kapsamının doğru içerecektir.|  
|`undefinedWithCompletionsOf(value);`|Kendisi için tamamlanma listesi tarafından belirlenir geçirilen nesne özel tanımlanmamış bir değer döndürür `value` parametresi.<br /><br /> `value` döndürülen değer için tamamlanma listesini belirler. `value` herhangi bir tür olabilir.<br /><br /> Tanımsız dönüş değeri kabul edilir olarak tanımlanmamış, tasarım zamanı ancak tamamlama listesi için dönüş değeri için tamamlanma listesini aynıdır `value` parametresi.<br /><br /> İçin dönüş değeri, dönüş türü, çalışma zamanında tahmin edilebilir, ancak tasarım zamanında dönüş değeri tanımsızdır IntelliSense sağlamak için bu işlevi bir kullanım içindir.|  
|`version()`|Visual Studio sürümünü döndürür.|  
  
## <a name="event-members"></a>Olay üyesi  
 Aşağıdaki olaylar için olay nesnesi sunulan üyeleri aşağıdaki bölümlerde açıklanmıştır: `statementcompletion`, `signaturehelp`, ve `statementcompletionhint`.  
  
###  <a name="CompletionItem"></a> completionItem özelliği  
 Hızlı bilgi açılır kutu istendiği tamamlanma öğesi olarak bilinen bir tanımlayıcı döndürür. Bu özellik kullanılabilir `statementcompletionhint` olay nesnesi ve [özelliği](#Items) özelliği `statementcompletion` olay nesnesi.  
  
 Dönüş değeri: `completionItem` nesnesi  
  
 Aşağıdaki üyeleri olan `completionItem` nesnesi:  
  
-   `name`. Okuma/yazma kullanıldığında `items` koleksiyonu; Aksi takdirde, salt okunur. Tamamlanma öğesi tanımlayan bir dize döndürür.  
  
-   `kind`. Okuma/yazma kullanıldığında `items` koleksiyonu; Aksi takdirde, salt okunur. Tamamlanma öğesi türünü temsil eden bir dize döndürür. Olası değerler yöntemi, alan, özelliği, parametre, değişken ve ayrılmış.  
  
-   `glyph`. Okuma/yazma kullanıldığında `items` koleksiyonu; Aksi takdirde, salt okunur. Tamamlama listesinde görüntülenecek bir simge temsil eden bir dize döndürür. Olası değerler için `glyph` aşağıdaki biçimi kullanın: vs:*glyphType*burada *glyphType* dilden bağımsız üyeleri karşılık gelen <xref:Microsoft.VisualStudio.Language.Intellisense.StandardGlyphGroup> sabit listesi. Örneğin, `vs:GlyphGroupMethod` için bir olası değer `glyph`. Zaman `glyph` ayarlı değil, `kind` özelliği varsayılan simgeyi belirtir.  
  
-   `parentObject`. Salt okunur. Üst nesne döndürür.  
  
-   `value`. Salt okunur. Tamamlama öğesinin değeri temsil eden bir nesne döndürür.  
  
-   `comments`. Salt okunur. Alan veya değişken üzerindeki açıklamalar içeren bir dize döndürür.  
  
-   `scope`. Salt okunur. Tamamlanma öğesi kapsamını döndürür. Olası değerler şunlardır: Genel, yerel, parametre ve üye.  
  
###  <a name="Items"></a> Öğe özelliği  
 Alır veya bir dizi deyim tamamlama öğeleri ayarlar. Dizideki her öğe bir [completionItem özelliği](#CompletionItem) nesne. `items` Özelliği kullanılabilir `statementcompletion` olay nesnesi.  
  
 Dönüş değeri: dizi  
  
###  <a name="FunctionComments"></a> functionComments özelliği  
 İşlev için açıklamalar döndürür. Bu özellik kullanılabilir `signaturehelp` olay nesnesi.  
  
 Dönüş değeri: `comments` nesnesi  
  
 Aşağıdaki üyeleri olan `comments` nesnesi:  
  
-   `above`. Açıklamalar işlevin üstünde döndürür.  
  
-   `inside`. İşlevin içindeki açıklamalar genellikle VSDoc biçiminde döndürür.  
  
-   `paramComments`. Her bir parametreye işlev açıklamaları temsil eden bir dizi döndürür. Dizi üyeleri Ekle:  
  
    -   `name`. Parametre adını temsil eden bir dize döndürür.  
  
    -   `comment`. Parametre açıklama içeren bir dize döndürür.  
  
###  <a name="FunctionHelp"></a> functionHelp özelliği  
 İşlev için Yardım'ı döndürür. Bu özellik kullanılabilir `signaturehelp` olay nesnesi.  
  
 Dönüş değeri: `functionHelp` nesnesi  
  
 Aşağıdaki üyeleri olan `functionHelp` nesnesi:  
  
-   `functionName`. Okuma/yazma. İşlev adı içeren bir dize döndürür.  
  
-   `signatures`. Okuma/yazma. Alır veya ayarlar işlev imzası dizisi. Dizideki her öğe bir `signature` nesne. Bazı `signature` özellikleri gibi `locid`, karşılık gelen ortak [XML belgeleri yorumları](../ide/xml-documentation-comments-javascript.md) öznitelikleri.  
  
     Üyeleri `signature` nesne içerir:  
  
    -   `description`. Okuma/yazma. İşlevi tanımlayan bir dize döndürür.  
  
    -   `locid`. Okuma/yazma. Yerelleştirme işlevi hakkında bilgi içeren bir dize tanımlayıcı döndürür.  
  
    -   `helpKeyword`. Okuma/yazma. Yardım anahtar sözcüğü içeren bir dize döndürür.  
  
    -   `externalFile`. Okuma/yazma. Üye kimliği içeren dosyayı temsil eden bir dize döndürür  
  
    -   `externalid`. Okuma/yazma. İşlevin üye kimliği temsil eden bir dize döndürür.  
  
    -   `params`. Okuma/yazma. Alır veya işlevi için parametreler dizisi ayarlar. Parametreler dizideki her öğe bir `parameter` aşağıdaki özniteliklerine karşılık gelen özelliklerle nesnesi [ \<param >](../ide/param-javascript.md) öğesi:  
  
        -   `name`. Okuma/yazma. Parametre adını temsil eden bir dize döndürür.  
  
        -   `type`. Okuma/yazma. Parametre türünü temsil eden bir dize döndürür.  
  
        -   `elementType`. Okuma/yazma. Tür ise `Array`, dizideki öğelerin türünü temsil eden bir dize döndürür.  
  
        -   `description`. Okuma/yazma. Parametreyi açıklayan bir dize döndürür.  
  
        -   `locid`. Okuma/yazma. Yerelleştirme işlevi hakkında bilgi içeren bir dize tanımlayıcı döndürür.  
  
        -   `optional`. Okuma/yazma. Parametre isteğe bağlı olup olmadığını gösteren bir dize döndürür. `true` parametre isteğe bağlı olduğunu gösterir; `false` bunu olmadığını gösterir.  
  
    -   `returnValue`. Okuma/yazma. Nesneyi alır veya bir dönüş değeri karşılık gelen özelliklerle birlikte aşağıdaki öznitelikleri ayarlar [ \<döndürür >](../ide/returns-javascript.md) öğesi:  
  
        -   `type`. Okuma/yazma. Dönüş türünü temsil eden bir dize döndürür.  
  
        -   `elementType`. Okuma/yazma. Tür ise `Array`, dizideki öğelerin türünü temsil eden bir dize döndürür.  
  
        -   `description`. Okuma/yazma. Dönüş değeri tanımlayan bir dize döndürür.  
  
        -   `locid`. Okuma/yazma. Yerelleştirme işlevi hakkında bilgi içeren bir dize tanımlayıcı döndürür.  
  
        -   `helpKeyword`. Okuma/yazma. Yardım anahtar sözcüğü içeren bir dize döndürür.  
  
        -   `externalFile`. Okuma/yazma. Üye kimliği içeren dosyayı temsil eden bir dize döndürür  
  
        -   `externalid`. Okuma/yazma. İşlevin üye kimliği temsil eden bir dize döndürür.  
  
###  <a name="ParentObject"></a> parentObject özelliği  
 Bir üye işlevinin üst nesnesini döndürür. Örneğin, `document.getElementByID`, `parentObject` döndürür `document` nesne. Bu özellik kullanılabilir `signaturehelp` olay nesnesi.  
  
 Dönüş değeri: nesne  
  
###  <a name="Target"></a> hedef özelliği  
 Öğe sol tarafında bir nokta (.) olan bir tetikleyici karakteri temsil eden bir nesne döndürür. İşlevler için `target` parametre bilgisi talep edilen işlevi döndürür. Bu özellik kullanılabilir `statementcompletion` ve `signaturehelp` olay nesneleri.  
  
 Dönüş değeri: nesne  
  
###  <a name="TargetName"></a> targetName özelliği  
 Hedef temsil eden bir dize döndürür. Örneğin, "this.", `targetName` "this" döndürür. "(İmleç"B"olduğunda) A.B" için `targetName` "B" döndürür. Bu özellik kullanılabilir `statementcompletion` olay nesnesi.  
  
 Dönüş değeri: dize  
  
###  <a name="SymbolHelp"></a> symbolHelp özelliği  
 Hızlı bilgi açılır kutu istendiği tamamlanma öğesi döndürür. Bu özellik kullanılabilir `statementcompletionhint` olay nesnesi.  
  
 Dönüş değeri: `symbolHelp` nesne.  
  
 Bazı özellikleri `symbolHelp` gibi nesne `locid`, karşılık gelen ortak [XML belgeleri yorumları](../ide/xml-documentation-comments-javascript.md) öznitelikleri.  
  
 Aşağıdaki üyeleri olan `symbolHelp` nesnesi:  
  
-   `name`. Okuma/yazma. Tanımlayıcı adı içeren bir dize döndürür.  
  
-   `symbolType`. Okuma/yazma. Simge türü temsil eden bir dize döndürür. Olası değerler şunlardır: Bilinmeyen, Boolean, sayı, dize, nesne, işlevi, dizi, tarih ve normal ifade.  
  
-   `symbolDisplayType`. Okuma/yazma. Görüntülenecek tür adı içeren bir dize döndürür. Varsa `symbolDisplayType` ayarlanmamışsa, `symbolType` kullanılır.  
  
-   `elementType`. Okuma/yazma. Varsa `symbolType` olduğu `Array`, dizideki öğelerin türünü temsil eden bir dize döndürür.  
  
-   `scope`. Okuma/yazma. Simgenin kapsamı temsil eden bir dize döndürür. Olası değerler, küresel ve yerel, parametre ve üye içerir.  
  
-   `description`. Okuma/yazma. Simgenin bir açıklama içeren bir dize döndürür.  
  
-   `locid`. Okuma/yazma. Yerelleştirme sembol bilgilerini içeren bir dize tanımlayıcı döndürür.  
  
-   `helpKeyword`. Okuma/yazma. Yardım anahtar sözcüğü içeren bir dize döndürür.  
  
-   `externalFile`. Okuma/yazma. Üye kimliği içeren dosyayı temsil eden bir dize döndürür  
  
-   `externalid`. Okuma/yazma. Simgenin üye kimliği temsil eden bir dize döndürür.  
  
-   `functionHelp`. Okuma/yazma. Döndürür bir [functionHelp özelliği](#FunctionHelp), bilgiler içerebilir, zaman `symbolType` işlevdir.  
  
###  <a name="Scope"></a> Kapsam özelliği  
 Etkinliğin tamamlanma kapsamını döndürür. Tamamlama için olası değerler, genel olan ve üye kapsamı. Bu özellik kullanılabilir `statementcompletion` olay nesnesi.  
  
 Dönüş değeri: dize  
  
## <a name="debugging-intellisense-extensions"></a>IntelliSense uzantıların hatalarını ayıklama  
 Uzantıları hata ayıklama, ancak kullanabileceğiniz [IntelliSense nesne](#intellisenseObject) Visual Studio çıkış penceresinde bilgi göndermek için işlevi. Bu işlevin nasıl kullanılacağını gösteren bir örnek için bkz: [gönderme iletilerini çıkış penceresine](#Logging) bu konuda. İçin `logMessage` çözmek için en az bir olay işleyicisi uzantısı'nda kayıtlı olması gerekir.  
  
##  <a name="CodeExamples"></a> Kod örnekleri  
 Bu bölüm, IntelliSense genişletilebilirlik API'leri kullanmayı gösteren kod örnekleri içerir. Bu API'leri kullanan başka yolları da vardır. Aşağıdaki dosyalarda ek örnekler için bkz. \\ \\ *Visual Studio yükleme yolu*\JavaScript\References klasör. Bu örnekler JavaScript dil hizmeti tarafından kullanılan çalışıyoruz.  
  
-   underscoreFilter.js. Bu kod, IntelliSense özel üyeleri gizler. Olay işleyicilerini içerir `statementcompletion` olay.  
  
-   showPlainComments.js. Bu kod, standart açıklamalar için IntelliSense desteği sunar. Olay işleyicilerini içerir `signaturehelp` ve `statementcompletionhint` olayları.  
  
###  <a name="Annotations"></a> IntelliSense ek açıklamaları ekleme  
 Aşağıdaki yordam, kitaplık doğrudan değişiklik yapmadan bir üçüncü taraf kitaplık için IntelliSense belgeleri desteğini sağlamak nasıl gösterir. Bunu yapmak için kullanabileceğiniz `intellisense.annotate` bir uzantı.  
  
 Bu örneğin çalışması, aşağıdaki JavaScript dosyaları projenize gerekir:  
  
-   bir üçüncü taraf kitaplığı temsil eden bir proje dosyası demoLib.js.  
  
-   demoLib.intellisense.js IntelliSense uzantısıdır. Bu dosya projeye dahil gerekmez, ancak exampleLib.js aynı klasörde olması gerekir.  
  
-   appCode.js uygulama kodunu temsil eden bir proje dosyası.  
  
##### <a name="to-add-an-intellisense-annotation"></a>Bir IntelliSense ek açıklama eklemek için  
  
1.  DemoLib.js için aşağıdaki kodu ekleyin.  
  
    ```javascript  
    function someFunc(a) { };  
    var rectangle;  
  
    ```  
  
2.  DemoLib.intellisense.js için aşağıdaki kodu ekleyin.  
  
    ```javascript  
    intellisense.annotate(someFunc, function (a) {  
        /// <signature>  
        /// <summary>Description of someFunc</summary>  
        /// <param name="a">Param a</param>  
        /// </signature>  
    });  
  
    intellisense.annotate(window, {  
        // This is a comment on a global variable named rectangle.  
        rectangle: undefined  
    });  
    ```  
  
3.  Aşağıdaki başvuru yönergesi appCode.js ilk satırı olarak ekleyin. Burada kullanılan yolu JavaScript dosyaları aynı klasörde gösterir.  
  
    ```javascript  
    /// <reference path="demoLib.js" />  
  
    ```  
  
4.  AppCode.js içinde aşağıdaki kodu yazın. XML belge açıklamaları IntelliSense parametre bilgisi olarak görüntülenen uzantısında görürsünüz.  
  
     ![İntellisense.annotate kullanımını gösteren örnek](../ide/media/js-intellisense-annotate-paraminfo.png "js_intellisense_annotate_paraminfo")  
  
5.  AppCode.js içinde aşağıdaki kodu yazın. Siz yazarken, standart yorumları hızlı bilgi IntelliSense görüntülenen uzantısında görürsünüz.  
  
     ![İntellisense.annotate kullanımını gösteren örnek](../ide/media/js-intellisense-annotations.png "js_intellisense_annotations")  
  
###  <a name="Logging"></a> Çıkış penceresinde ileti gönderme  
 Aşağıdaki yordam için çıkış penceresine ileti göndermek nasıl gösterir. Hata ayıklama IntelliSense uzantıları yardımcı olmak için iletileri gönderebilir.  
  
 Bu örneğin çalışması, aşağıdaki JavaScript dosyaları projenize gerekir:  
  
-   bir üçüncü taraf kitaplığı temsil eden bir proje dosyası exampleLib.js.  
  
-   exampleLib.intellisense.js IntelliSense uzantısıdır. Bu dosya projeye dahil gerekmez, ancak exampleLib.js aynı klasörde olması gerekir.  
  
-   appCode.js uygulama kodunu temsil eden bir proje dosyası.  
  
##### <a name="to-send-a-message-to-the-output-window"></a>Çıkış penceresinde bir ileti göndermek için  
  
1.  ExampleLib.js için aşağıdaki kodu ekleyin.  
  
    ```javascript  
    var someVar = {  
        a: 1,  
        b: 'hello'  
    };  
    ```  
  
2.  ExampleLib.intellisense.js için aşağıdaki kodu ekleyin.  
  
    ```javascript  
    intellisense.addEventListener('statementcompletion', function (e) {  
        // Prints out statement completion info: Either (1) the member   
        // list, if the trigger character was typed, or (2) the   
        // statement completion identifiers.  
        // e.target represents the object left of the trigger character.  
        intellisense.logMessage(  
            e.target ? 'member list requested, target: ' + e.targetName : 'statement completion for current scope requested');  
  
        // Prints out all statement completion items.  
        e.items.forEach(function (item) {  
            intellisense.logMessage('[completion item] ' + item.name + ', kind:' + item.kind + ', scope:' + item.scope + ', value:' + item.value);  
        });  
    });  
    ```  
  
3.  Aşağıdaki başvuru yönergesi appCode.js ilk satırı olarak ekleyin. Burada kullanılan yolu JavaScript dosyaları aynı klasörde gösterir.  
  
    ```javascript  
    /// <reference path="exampleLib.js" />  
  
    ```  
  
4.  Çıkış penceresinde **JavaScript dil hizmeti** içinde **çıktıyı Göster** listesi. (Çıktı penceresini görüntülemek için seçin **çıkış** Görünüm menüsünden.)  
  
5.  AppCode.js içinde aşağıdaki kodu yazın. Siz yazarken, çıkış penceresine dil hizmetinden gelen iletileri gösterir. Deyim tamamlama geçerli kapsam için istenen çıkış penceresine ilk iletiyi gösterir.  
  
    ```javascript  
    some  
    ```  
  
     Aşağıdaki çıktıyı görmelisiniz kısmi bir görünümüdür.  
  
    ```scr  
    03:16:14.3113: statement completion for current scope requested  
    03:16:14.3113: [completion item] break, kind:reserved, scope:undefined, value:undefined  
    03:16:14.3113: [completion item] case, kind:reserved, scope:undefined, value:undefined  
    03:16:14.3113: [completion item] catch, kind:reserved, scope:undefined, value:undefined  
  
    …  
    ```  
  
6.  Seçin **Tümünü Temizle** çıktı penceresinde düğmesi.  
  
7.  Aşağıdaki kodu yazın. Üye listesi istenen çıkış penceresine ilk iletiyi gösterir.  
  
    ```javascript  
    someVar.  
    ```  
  
     Aşağıdaki çıktıyı görmelisiniz kısmi bir görünümü şu şekildedir:  
  
    ```scr  
    03:17:43.4032: member list requested, target: someVar  
    03:17:43.4032: [completion item] a, kind:field, scope:member, value:1  
    03:17:43.4032: [completion item] b, kind:field, scope:member, value:hello  
    03:17:43.4032: [completion item] constructor, kind:method, scope:member, value:  
  
    …  
    ```  
  
###  <a name="Icons"></a> IntelliSense simgeleri değiştirme  
 Aşağıdaki yordam, IntelliSense tarafından varsayılan olarak görüntülenen simgeler değiştirme gösterir. Ad alanları, sınıflar, arayüzler ve numaralandırma gibi kitaplık özgü kavramları IntelliSense bilgilerini sağladığınızda bu yararlı olabilir.  
  
 Kullanılabilir simge değerlerinin <xref:Microsoft.VisualStudio.Language.Intellisense.StandardGlyphGroup>.  
  
 Bu örneğin çalışması, aşağıdaki JavaScript dosyaları projenize gerekir:  
  
-   bir proje olan exampleLib.js bu represens üçüncü taraf kitaplık dosyası.  
  
-   exampleLib.intellisense.js IntelliSense uzantısıdır. Bu dosya projeye dahil gerekmez, ancak exampleLib.js aynı klasörde olması gerekir.  
  
-   appCode.js uygulama kodunu temsil eden bir proje dosyası.  
  
##### <a name="to-change-the-icons"></a>Simgeleri değiştirmek için  
  
1.  ExampleLib.js için aşağıdaki kodu ekleyin.  
  
    ```javascript  
    function Namespace(name) {  
        this._isNamespace = true;  
        window[name] = this;  
    };  
  
    function Enum(values) {  
        var e = Object.create(values);  
        e._isEnum = true;  
        return e;  
    };  
  
    var SomeNamespace = new Namespace('SomeNamespace');  
    // A constructor function is considered a class.  
    SomeNamespace.SomeClass1 = function () { }  
    SomeNamespace.Enum1 = new Enum({ VALUE1: 0, VALUE2: 1 });  
    ```  
  
2.  ExampleLib.intellisense.js için aşağıdaki kodu ekleyin.  
  
    ```javascript  
    intellisense.addEventListener('statementcompletion', function (e) {  
        e.items.forEach(function (item) {  
            // Detect a namespace by using the _isNamespace flag.  
            if (item.value && item.value._isNamespace) {  
                item.glyph = 'vs:GlyphGroupNamespace';  
                }  
  
            if (item.parentObject && item.parentObject._isNamespace) {  
                // The item is a member of a namespace.   
  
                // All constructor functions that are part of a namespace   
                // are considered classes.   
                // A constructor function starts with  
                // an uppercase letter by convention.    
                if (typeof item.value == 'function' && (item.name[0].toUpperCase()   
                    == item.name[0])) {  
                    item.glyph = 'vs:GlyphGroupClass';  
                }  
  
                // Detect an enumeration by using the _isEnum flag.  
                if (item.value && item.value._isEnum) {  
                    item.glyph = 'vs:GlyphGroupEnum';  
                }  
            }  
        });  
    });  
  
    intellisense.addEventListener('statementcompletionhint', function (e) {  
        if (e.completionItem.value) {  
            if (e.completionItem.value._isNamespace) {  
                e.symbolHelp.symbolDisplayType = 'Namespace';  
            }  
            if (e.completionItem.value._isEnum) {  
                e.symbolHelp.symbolDisplayType = 'Enum';  
            }  
        }  
    });  
    ```  
  
3.  Aşağıdaki başvuru yönergesi appCode.js ilk satırı olarak ekleyin. Burada kullanılan yolu JavaScript dosyaları aynı klasörde gösterir.  
  
    ```javascript  
    /// <reference path="exampleLib.js" />  
  
    ```  
  
4.  AppCode.js içinde aşağıdaki kodu yazın. Siz yazarken, ad alanı simgesi değiştiğini görürsünüz "{}", C# dilinde kullanılır.  
  
     ![Glif özelliğinin kullanımını gösteren örnek](../ide/media/js-intellisense-glyph-namespace.png "js_intellisense_glyph_namespace")  
  
5.  AppCode.js içinde aşağıdaki kodu yazın. Siz yazarken Enum1 üyesi için yeni bir sabit listesi simgesi ve SomeClass1 üyesi için yeni bir sınıf simgesi görürsünüz.  
  
     ![Glif özelliğinin kullanımını gösteren örnek](../ide/media/js-intellisense-glyph-class-enum.png "js_intellisense_glyph_class_enum")  
  
###  <a name="Overriding"></a> Çalışma zamanı IntelliSense sonuçları etkileri kaçınma  
 JavaScript dil servisi, dinamik olarak IntelliSense bilgilerini sağlamak üzere kod çalıştırır. Sonuç olarak, çalışma zamanı davranışını bazen istenen sonuçları engelleyebilir. Aşağıdaki yordam, çalışma zamanı davranışını yanlış Intellisense'te sonuçlandığında IntelliSense sonuçları geçersiz kılmak gösterilmektedir.  
  
 Bu örneğin çalışması, aşağıdaki JavaScript dosyaları projenize gerekir:  
  
-   bir üçüncü taraf kitaplığı temsil eden bir proje dosyası exampleLib.js.  
  
-   exampleLib.intellisense.js IntelliSense uzantısıdır. Bu dosya projeye dahil gerekmez, ancak exampleLib.js aynı klasörde olması gerekir.  
  
-   appCode.js uygulama kodunu temsil eden bir proje dosyası.  
  
##### <a name="to-avoid-run-time-effects-on-intellisense-results"></a>Çalışma zamanı IntelliSense sonuçları etkileri önlemek için  
  
1.  ExampleLib.js için aşağıdaki kodu ekleyin.  
  
    ```javascript  
    function after(count, func) {  
        return function () {  
            if (--times < 1) {  
                return func.apply(this, arguments);  
            }  
        };  
    };  
    ```  
  
     Önceki kodda; değerine göre ilk çağrı, sarmalanmış işlev yoksayar `count`ve sonuçlar döndürmüyor.  
  
2.  Aşağıdaki başvuru yönergesi appCode.js ilk satırı olarak ekleyin. Burada kullanılan yolu JavaScript dosyaları aynı klasörde gösterir.  
  
    ```javascript  
    /// <reference path="exampleLib.js" />  
  
    ```  
  
3.  AppCode.js içinde aşağıdaki kodu yazın. Tanımlayıcı listesi, IntelliSense yerine görünür, sarmalanmış işlev hiçbir zaman anlamına çağrılır çünkü `throttled` işlevi herhangi bir sonuç döndürmez.  
  
     ![IntelliSense sonuçları geçersiz kılma örnek](../ide/media/js-intellisense-override.png "js_intellisense_override")  
  
4.  ExampleLib.intellisense.js için aşağıdaki kodu ekleyin. Sarmalanan işlevi için IntelliSense gösterilir böylece bu tasarım zamanı davranışını beklendiği gibi değiştirir.  
  
    ```javascript  
    window.after = function (count, func) {  
        // Just return func.   
        return func;  
    };  
    ```  
  
5.  AppCode.js içinde daha önce yazdığınız kod yazarak test sonuçları. Bu kez, IntelliSense, istenen bilgileri sağlar.  
  
     ![IntelliSense sonuçları geçersiz kılma örnek](../ide/media/js-intellisense-override-fixed.png "js_intellisense_override_fixed")  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [JavaScript IntelliSense](../ide/javascript-intellisense.md)   
 [Tanımlayıcılar İçin İfade Tamamlama](../ide/statement-completion-for-identifiers.md)



