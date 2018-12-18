---
title: JavaScript IntelliSense | Microsoft Docs
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
- IntelliSense [JavaScript]
- <reference> JavaScript XML tag
- JavaScript Code Editor
- XML code comments, JavaScript IntelliSense
- reference JavaScript XML tag
- JavaScript, IntelliSense
- code comments, JavaScript IntelliSense
- JavaScript, reference groups
- JavaScript Editor
- reference directives [JavaScript]
- JavaScript, XML documentation comments
- reference groups [JavaScript]
- JavaScript, reference directives
- IntelliSense [JavaScript], about
- IntelliSense extensibility [JavaScript]
- XML documentation comments [JavaScript]
ms.assetid: af1a3171-c9d8-45a3-9c96-a763e3b163ef
caps.latest.revision: 67
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 215bebb071ce707e2997e934fd58901ec2d56b8b
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49816345"
---
# <a name="javascript-intellisense"></a>JavaScript IntelliSense
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

IntelliSense, kodu oluşturduğunuz sırada size bilgi sağlayarak daha hızlı ve daha az hatayla kod yazmanıza yardımcı olur. JavaScript Düzenleyicisi'nde istemci komut dosyasıyla çalıştığınız sırada, IntelliSense geçerli bağlamınızı temel alarak uygun nesneleri, işlevleri, özellikleri ve parametreleri listeler. IntelliSense'in sağladığı açılan listeden bir kodlama seçeneğini belirleyerek kodunuzu tamamlayabilirsiniz.  
  
 IntelliSense aşağıdaki görevleri tamamlamayı kolaylaştırır:  
  
- Üye bilgilerini bulun.  
  
- Dil öğelerini doğrudan kodunuza ekleyin.  
  
- Kod düzenleyicisinden çıkmak zorunda kalmadan bağlamınızı koruyun.  
  
- XML belgeleri yorumları ve JavaScript IntelliSense genişletilebilirlik özelliği ile özel IntelliSense'i destekleyin.  
  
  Bu konu aşağıdaki bölümleri içermektedir:  
  
- [IntelliSense bağlamını belirleme](#DeterminingIntelliSenseContext)  
  
- [IntelliSense bilgilerini işleme](#ProcessingIntelliSenseInformation)  
  
- [JavaScript IntelliSense özellikleri](#Features)  
  
- [JavaScript IntelliSense genişletilebilirliği](#Extensibility)  
  
- [JavaScript doğrulaması](#Validation)  
  
  IntelliSense işlevselliği hakkında daha fazla bilgi için [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)], bkz: [IntelliSense kullanarak](../ide/using-intellisense.md).  
  
##  <a name="DeterminingIntelliSenseContext"></a> IntelliSense bağlamını belirleme  
 JavaScript IntelliSense, geçerli komut dosyası bağlamınızla alakalı tüm komut dosyalarını temel alarak kodlama seçenekleri sağlar. Geçerli dosyadaki betik oluşturma öğeleri de buna dahildir. Ayrıca, komut dosyası başvuruları, derleme komut dosyası başvuruları, hizmet başvuruları ve sayfayla ilişkili başvurular gibi, komut dosyanızın doğrudan ya da dolaylı olarak başvurduğu her kodu içerir.  
  
 Geçerli komut dosyası bağlamınız aşağıdaki öğeler temel alınarak oluşturulur:  
  
-   Etkin belgedeki tüm komut dosyası bloklarında tanımlı işlevler. Dosya adı uzantısı .aspx., .ascx, .master, .html ve .htm olan dosyalarda satır içi komut dosyası blokları desteklenir.  
  
-   `script` öğelerle `src` başka bir komut dosyasına işaret öznitelikleri. Hedef komut dosyasının dosya adı uzantısı .js olmalıdır.  
  
-   Diğer JavaScript dosyalarına başvuruda JavaScript dosyaları bir `reference` yönergesi.  
  
-   Genel nesneler, IntelliSense uzantıları veya gecikmeli yüklenen komut dosyaları için başvuru grupları.  
  
-   XML Web hizmetlerine yapılan başvurular.  
  
-   <xref:System.Web.UI.ScriptManager> Ve <xref:System.Web.UI.ScriptManagerProxy> Web uygulaması AJAX etkinleştirilmiş ASP.NET uygulaması olup olmadığını denetler.  
  
-   [!INCLUDE[atlaslib_current_ext](../includes/atlaslib-current-ext-md.md)], Bir AJAX etkinleştirilmiş ASP.NET Web uygulamasında çalışıyor.  
  
    > [!NOTE]
    >  HTML öğelerinde olay işleyicisi öznitelikleri içinde olan veya içinde tanımlandığından, komut dosyası için IntelliSense desteklenmez `href` öznitelikleri.  
  
##  <a name="ProcessingIntelliSenseInformation"></a> IntelliSense bilgilerini işleme  
 JavaScript IntelliSense sağlamak için dil hizmeti aşağıdaki işlemleri gerçekleştirir:  
  
-   Etkin belgedeki başvuruları temel alan ve başvurulan dosyalardaki özyinelemeli inceleme komut dosyası başvurularını temel alan bağımlı JavaScript dosyalarının bir listesini oluşturur.  
  
-   Listeyi dikkatle inceler ve her bir dosyadan tür bilgilerini ve diğer ilgili verileri toplar.  
  
-   Verileri bir araya toplar ve JavaScript dil servisine aktarır; böylece tür bilgileri ve veriler IntelliSense'in kullanımına sunulur.  
  
-   Dosyaları, IntelliSense listesini etkileyebilecek değişiklikler açısından izler ve gerektiğinde listeyi güncelleştirir. Uzak depolardaki (HTTP kullanılarak başvurulan depolar gibi) komut dosyaları izlenmez.  
  
##  <a name="Features"></a> JavaScript IntelliSense özellikleri  
 JavaScript IntelliSense aşağıdaki nesneleri destekler:  
  
- [Belge nesne modeli (DOM) öğeleri](#HTMLDom)  
  
- [İç nesneler](#IntrinsicObjects)  
  
- [Kullanıcı tanımlı değişkenler, İşlevler ve nesneler](#UserDefined)  
  
- Gibi başvurular kullanarak dış dosyalarda tanımlanan nesneler [komut dosyası başvuruları](#Script), [başvuru yönergeleri](#ReferenceDirectives), ve [başvuru grupları](#ReferenceGroups).  
  
- Uzak dosyalarda tanımlı olup Visual Studio tarafından indirilen nesneler.  
  
- Belirtilen nesneler [XML belgeleri yorumları](#XMLDocComments), parametreler ve alanlar gibi.  
  
- Standart JavaScript açıklama etiketleri (//) kullanılarak açıklanan nesneler. Daha fazla bilgi için [JavaScript IntelliSense genişletme](../ide/extending-javascript-intellisense.md).  
  
- Kullanılarak desteklenen nesneler [JavaScript IntelliSense genişletilebilirlik](#Extensibility) mekanizması. Daha fazla bilgi için [JavaScript IntelliSense genişletme](../ide/extending-javascript-intellisense.md).  
  
- [ASP.NET AJAX nesneleri](#ASPNet)  
  
  IntelliSense bir nesnenin türünü belirleyemediğinde, etkin belgedeki tanımlayıcıları kullanarak deyim tamamlama seçenekleri sunar. Daha fazla bilgi için [tanımlayıcılar için ifade tamamlama](../ide/statement-completion-for-identifiers.md).  
  
###  <a name="HTMLDom"></a> HTML DOM öğeleri  
 JavaScript IntelliSense programlama başvuruları gibi dinamik HTML (DHTML) DOM öğeleri için sağlar `body`, `form`, ve `div`. IntelliSense yalnızca, geçerli belgede ve ana sayfada yer alan öğeleri görüntüler. JavaScript IntelliSense de destekler `window` ve `document` nesneleri ve üyeleri.  
  
###  <a name="IntrinsicObjects"></a> İç nesneler  
 JavaScript IntelliSense programlama başvuruları gibi iç nesneler için sağlar `Array`, `String`, `Math`, `Date`, ve `Number`. İç nesneler hakkında daha fazla bilgi için bkz: [iç nesneler](~/E:/Repos/visualstudio-docs-pr/scripting-docs/javascript/intrinsic-objects-javascript.md).  
  
###  <a name="UserDefined"></a> Kullanıcı tanımlı değişkenler, İşlevler ve nesneler  
 Bir JavaScript dosyasını değiştirdiğinizde [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] taramaların açık ve başvuruda bulunulan tüm uygun kod kaynaklarını belirlemek için belgeleri. Bu değişkenler, İşlevler ve oluşturduğunuz nesneleri içerir. Bu kaynaklar daha sonra JavaScript IntelliSense kullanımına sunulur.  
  
 Kullanıcı tanımlı değişkenler, İşlevler ve nesneler hakkında daha fazla bilgi için bkz: [kendi nesnelerinizi oluşturma](http://go.microsoft.com/fwlink/?LinkId=108671) MSDN Web sitesinde.  
  
###  <a name="External"></a> Harici dosya başvuruları  
 Kodunuzda IntelliSense desteği elde etmek için çeşitli türlerde harici dosya başvuruları ekleyebilirsiniz. Harici dosya başvuruları; komut dosyası başvuruları ve başvuru yönergeleri olabileceği gibi, başvuru grupları kullanılarak da belirtilebilir.  
  
####  <a name="Script"></a> Komut dosyası başvuruları  
 Tüm istemci komut dosyasını bir sayfaya yazmak yerine, komut dosyası kodu içeren harici dosyalara başvuruda bulunabilirsiniz. Böylece, kodu sayfalar arasında yeniden kullanmanız daha kolay olur ve istemci komut dosyasının tarayıcı tarafından önbelleğe alınmasına olanak sağlanır.  
  
 ASP.NET AJAX etkinleştirilmiş bir Web sayfasıyla çalışmıyorsanız kullanarak harici bir komut dosyasına başvurabilirsiniz `src` açılış etiketinde özniteliği bir `script` öğesi. `src` Özniteliği, kaynak kodu veya verileri içeren bir harici dosyanın URL'si belirtir.  
  
 Aşağıdaki örnekte kullanan bir biçimlendirme gösterilmektedir `src` özniteliğini bir <`script`> etiketi, bir komut dosyasına başvuruda bulunmak.  
  
```html  
<script type="text/javascript" src="~/Scripts/JavaScript.js">  
  
</script>  
```  
  
 ASP.NET AJAX etkinleştirilmiş bir Web sayfasıyla çalışıyorsanız, komut dosyaları kullanarak başvurabilirsiniz <xref:System.Web.UI.ScriptReference> nesnesinin <xref:System.Web.UI.ScriptManager> denetimi.  
  
 Kullanan bir biçimlendirme aşağıdaki örnekte bir <xref:System.Web.UI.ScriptReference> nesnesine bir <xref:System.Web.UI.ScriptManager> bir komut dosyasına başvuruda bulunmak denetimi.  
  
```html  
<asp:ScriptManager ID="ScriptManager1" runat="server">  
  <Scripts>  
    <asp:ScriptReference Path="~/Scripts/JavaScript.js" />  
  </Scripts>  
</asp:ScriptManager>  
```  
  
 IntelliSense, ASP.NET AJAX Web uygulamalarında bir derlemeye kaynak olarak eklenen komut dosyalarını da destekler. Ekli komut dosyası kaynakları hakkında daha fazla bilgi için bkz: [izlenecek yol: bir JavaScript dosyasını bir kaynak olarak bir derlemede katıştırmak](http://msdn.microsoft.com/library/d8cb78cd-95a9-4dc6-92df-391866817e89).  
  
####  <a name="ReferenceDirectives"></a> Başvuru yönergeleri  
 A `reference` yönergesi [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] düzenlemekte olduğunuz komut dosyası ve diğer betikleri arasında ilişki kurmak için. `reference` Yönergesi, geçerli komut dosyası komut bağlamında bir komut dosyası eklemenize olanak tanır. Böylece, kodunuzu yazarken IntelliSense'in harici olarak tanımlı işlevlere, türlere ve alanlara başvuruda bulunabilmesi sağlanır.  
  
 Oluşturduğunuz bir `reference` XML açıklaması biçiminde yönergesi. Bu yönerge, dosya içinde tüm diğer komut dosyalarından önce bildirilmelidir. A `reference` yönergesi, disk tabanlı komut dosyası başvurusu, derleme tabanlı komut dosyası başvurusu, hizmet tabanlı komut dosyası başvurusu veya sayfa tabanlı komut dosyası başvurusu içerebilir.  
  
 Aşağıdaki örnekte, disk tabanlı başvuru yönergelerinin kullanımına dair örnekler gösterilmektedir. İlk örnekte, dil servisi, proje dosyasını (örneğin, .jsproj) içeren aynı klasörde ilgili dosyayı da arar.  
  
 `/// <reference path="ScriptFile1.js" />`  
  
 `/// <reference path="Scripts/ScriptFile2.js" />`  
  
 `/// <reference path="../ScriptFile3.js" />`  
  
 `/// <reference path="~/Scripts/ScriptFile4.js" />`  
  
 Aşağıdaki örnekte, derleme tabanlı bir komut dosyası için nasıl başvuru oluşturulacağı gösterilmektedir.  
  
 `/// <reference name "Ajax.js" assembly="System.Web.Extensions, ..." />`  
  
 Aşağıdaki örnekte, hizmet tabanlı komut dosyasına nasıl başvurulacağı gösterilmektedir:  
  
 `/// <reference path="MyService.asmx" />`  
  
 `/// <reference path="Services/MyService.asmx" />`  
  
 `/// <reference path="../MyService.asmx" />`  
  
 `/// <reference path="~/Services/MyService.asmx" />`  
  
> [!NOTE]
>  Web Uygulama Projeleri'nde (WAP), Web hizmeti (.asmx) dosyaları içinde yer alan komut dosyası için JavaScript IntelliSense desteklenmez.  
  
 Aşağıdaki örnekte, sayfa tabanlı komut dosyasına nasıl başvurulacağı gösterilmektedir:  
  
 `/// <reference path="Default.aspx" />`  
  
 `/// <reference path="Admin/Default.aspx" />`  
  
 `/// <reference path="../Default.aspx" />`  
  
 `/// <reference path="~/Admin/Default.aspx" />`  
  
 Aşağıdaki kurallar için geçerli bir `reference` yönergesi.  
  
-   `reference` Önce herhangi bir komut XML açıklaması bildirilmelidir.  
  
-   XML açıklamaları sözdizimini üç eğik çizgi ile kullanmalısınız. Standart açıklamalar sözdizimi (iki eğik çizgi) kullanılarak yapılan başvurular yoksayılır.  
  
-   Yönerge başına yalnızca tek bir dosya veya kaynak belirtilebilir.  
  
-   Sayfa tabanlı komut dosyalarına yönelik birden fazla başvuruya izin verilmez.  
  
-   Bir sayfa başvurusu belirtiliyorsa, başka hiçbir türde başvuru yönergesine izin verilmez.  
  
-   Dosya adlarında göreli yollar kullanılır. Tilde işlecini kullanabilirsiniz (`~`) uygulama köküne göreli yollar yapmak için.  
  
-   Mutlak yollar yoksayılır.  
  
-   Başvurulan sayfalardaki başvuru yönergeleri işlenmez; yani başvuru yönergeleri sayfalar için özyinelemeli olarak çözümlenmez. Yalnızca sayfanın doğrudan başvurduğu komut dosyası dahil edilir.  
  
####  <a name="ReferenceGroups"></a> Başvuru grupları  
 Belirli IntelliSense .js dosyalarının farklı JavaScript projeleri için kapsamda olduğunu belirtmek için önceden tanımlı başvuru gruplarını kullanabilirsiniz. Aşağıdaki başvuru grubu türleri kullanılabilir:  
  
- Örtük (Windows) için [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] JavaScript kullanan uygulamalar. Bu grupta yer alan dosyalar, belirtilen türdeki proje için Kod Düzenleyicisi'nde açılan her .js dosyası için kapsama girer.  
  
- Örtük (Web); HTML5 projeleri için. Bu grupta yer alan dosyalar, bu proje türleri için Kod Düzenleyicisi'nde açılan her .js dosyası için kapsama girer.  
  
- Adanmış çalışan başvuru grupları; HTML5 Web Çalışanları için. Bu grupta belirtilen dosyalar, bir adanmış çalışan başvuru grubuna dair açık başvuru içeren .js dosyaları için kapsama girer.  
  
- Genel; diğer JavaScript proje türleri için.  
  
  Çoğu senaryoda başvuru gruplarını değiştirmeniz gerekmez. Ancak, değişiklikler yapmak istiyorsanız, başvuru gruplarında yer alan dosyaları belirtmek için JavaScript Kodu Düzenleyicisi'ne ilişkin yapılandırma seçeneklerini kullanabilirsiniz. Bu özelliğin kullanımı hakkında yönergeler için bkz: [seçenekler, metin düzenleyici, JavaScript, IntelliSense](../ide/reference/options-text-editor-javascript-intellisense.md).  
  
> [!TIP]
>  IntelliSense başvuruları normalde IntelliSense ve genel nesneler için IntelliSense desteği sağlamak için kullanılan [uzantıları](#Extensibility). Bu seçeneği ayrıca, komut dosyası yükleyici kullanılarak çalışma zamanında yüklenmesi gereken komut dosyaları için de kullanabilirsiniz.  
  
### <a name="remote-file-references"></a>Uzak Dosya Başvuruları  
 Uzak bir dosya veya kitaplık için IntelliSense desteği sağlamak amacıyla, Visual Studio'ya bir JavaScript dosyasında başvurulan uzak JavaScript dosyalarını indirme talimatı verebilirsiniz. Bu özelliği kullandığınızda, JavaScript dosyanıza bir başvuru olarak eklediğiniz dosyalar indirilir.  
  
> [!NOTE]
>  Web projeleri dışında, bu özelik yalnızca projenin bağlamı dışında açılan JavaScript dosyaları için çalışır. Web projeleri için, projenizde başvurulan uzak dosyalar varsayılan olarak indirilir.  
  
 Bu özelliğin kullanımı hakkında yönergeler için bkz: [seçenekler, metin düzenleyici, JavaScript, IntelliSense](../ide/reference/options-text-editor-javascript-intellisense.md).  
  
> [!WARNING]
>  Bu özelliği etkinleştirir ve Kod Düzenleyicisi'nde daha yavaş bir performans gözlemlerseniz, özelliği devre dışı bırakmanızı öneririz.  
  
###  <a name="XMLDocComments"></a> XML belge açıklamaları  
 XML belgeleri yorumları, komut dosyasına eklediğiniz kod öğelerinin metin açıklamalarıdır. Bu metin açıklamaları IntelliSense'te, yorumda bulunulan komut dosyasına başvurduğunuz zamanlarda görüntülenir. Örneğin, bir işlevin parametreleri ve dönüş değeri hakkında bilgi verebilirsiniz. XML belgeleri yorumlarına yalnızca dosyalardan, derlemelerden ve hizmetlerden ulaşılabilir. Daha fazla bilgi için [XML belgeleri yorumları](../ide/xml-documentation-comments-javascript.md) ve [XML belge açıklamaları oluşturma](../ide/create-xml-documentation-comments-for-javascript-intellisense.md).  
  
 IntelliSense XML belgeleri yorumlarını şu senaryolarda görüntüleyebilir:  
  
- Başka bir .js dosyasına başvuruda bulunan .js dosyası.  
  
- Bir .aspx dosyasına başvuruda bulunan .js dosyası.  
  
- Bir .js dosyasına başvuruda bulunan .aspx dosyası.  
  
  Bir .aspx dosyası başka bir .aspx dosyasına başvurduğunda IntelliSense kullanılamaz.  
  
###  <a name="ASPNet"></a> ASP.NET AJAX nesneleri  
 ASP.NET AJAX da JavaScript IntelliSense'i destekler. ASP.NET AJAX, ECMAScript (JavaScript) içinde kullanılabilen standart türlerin kapsamını genişleten bir istemci çerçevesi içerir. ASP.NET AJAX nesneleri hakkında daha fazla ayrıntı sağlamak JavaScript IntelliSense sağlamak için XML belge açıklamaları boyunca eklenen [!INCLUDE[atlaslib_current_ext](../includes/atlaslib-current-ext-md.md)]. ASP.NET AJAX Kitaplığı'nda yer alan türleri ve üyeleri kullandığınızda bu XML belgeleri yorumları görüntülenir.  
  
> [!NOTE]
>  Özel üyeler JavaScript IntelliSense tarafından görüntülenmez. Özel üyeler, ASP.NET AJAX içinde, bir alt çizgi (_) ile başlayan üyeler olarak belirtilir.  
  
##  <a name="Extensibility"></a> JavaScript IntelliSense genişletilebilirliği  
 JavaScript dil servisi, üçüncü taraf kitaplıkları kullanan geliştiriciler için IntelliSense deneyimini değiştirmenize olanak sağlayan nesneleri ve işlevleri sunar. Özellikle de varsayılan dil servisinin müşterilere vermek istediğiniz tüm bilgileri sağlayamadığı durumlarda bu özellikler yararlı olur. Daha fazla bilgi için [JavaScript IntelliSense genişletme](../ide/extending-javascript-intellisense.md).  
  
##  <a name="Validation"></a> JavaScript doğrulaması  
 JavaScript komut dosyası doğrulaması arka planda sürekli gerçekleşir. Zaman [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] sözdizimi hataları algıladığında JavaScript kodunda aşağıdaki yollarla geri bildirim sağlanır:  
  
-   Düzenleyicide altı çizili öğeler. Dalgalı kırmızı alt çizgiler hataları gösterir. Fare işaretçisini hatanın üzerinde tutarsanız, bir araç ipucu hata açıklamasını görüntüler.  
  
-   **Hata listesi** penceresi. **Hata listesi** penceresi hata açıklamasını, hatanın oluştuğu dosya, satır ve sütun numarasını ve projeyi görüntüler. Görüntülenecek **hata listesi** penceresi, **görünümü** menüsünde tıklatın **hata listesi**.  
  
-   Çıkış penceresi yüklenmemiş başvuruları gösterir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IntelliSense kullanma](../ide/using-intellisense.md)   
 [XML belge açıklamaları oluşturma](../ide/create-xml-documentation-comments-for-javascript-intellisense.md)   
 [JavaScript IntelliSense genişletme](../ide/extending-javascript-intellisense.md)   
 [Tanımlayıcılar için ifade tamamlama](../ide/statement-completion-for-identifiers.md)   
 [XML belge açıklamaları](../ide/xml-documentation-comments-javascript.md)   
 [DHTML nesne modeli](http://go.microsoft.com/fwlink/?LinkID=92344)   
 [Üyeleri Listele](http://msdn.microsoft.com/en-us/1b9cc469-9cd4-4d42-9999-1f9479635ff8)   
 [SRC özniteliğini &#124; src özelliği](http://go.microsoft.com/fwlink/?LinkId=92345)



