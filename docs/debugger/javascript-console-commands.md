---
title: JavaScript Konsolu komutları | Microsoft Docs
ms.custom: seodec18
ms.date: 07/17/2017
ms.technology: vs-ide-debug
ms.topic: reference
helpviewer_keywords:
- JavaScript Console commands [UWP apps]
- JavaScript debugging, console [UWP apps]
- debugging JavaScript, console [UWP apps]
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- uwp
- cordova
ms.openlocfilehash: c546e3f1938a7dddc3dd48fa9d941b9f7d2e7048
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53052228"
---
# <a name="javascript-console-commands-in-visual-studio"></a>Visual Studio'da JavaScript Konsolu komutları
  
 İleti göndermek ve Visual Studio JavaScript konsol penceresinde diğer görevleri gerçekleştirmek için komutlarını kullanabilirsiniz. Bu pencere kullanmayı gösteren örnekler için bkz [hızlı başlangıç: JavaScript hata ayıklama](../debugger/quickstart-debug-javascript-using-the-console.md). Bu konu başlığı altındaki bilgiler, UWP uygulamaları ve Apache Cordova için Visual Studio Araçları kullanılarak oluşturulan uygulamalar için geçerlidir. Cordova uygulamalarında desteklenen Konsolu komutları hakkında daha fazla bilgi için bkz. [Debug Your App](https://taco.visualstudio.com/en-us/docs/debug-using-visual-studio/). Internet Explorer F12 araçlarındaki konsolunu kullanma hakkında daha fazla bilgi için bkz. [bu konuda](/previous-versions/windows/internet-explorer/ie-developer/samples/dn255006(v=vs.85)).  
  
 JavaScript Konsolu penceresi kapatıldığında, Visual Studio'da seçerek hata ayıklarken bunu açabilirsiniz **hata ayıklama** > **Windows** > **JavaScript Konsol**.  
  
> [!NOTE]
>  Penceresi bir hata ayıklama oturumu sırasında kullanılabilir durumda değilse, hata ayıklayıcı türü ayarlandığından emin olun **betik** proje için hata ayıklama özellikleri.  
  
## <a name="console-object-commands"></a>Konsol nesne komutları  
 Bu tablo için söz dizimi görülmektedir `console` nesne komutları JavaScript konsol penceresinde kullanabilirsiniz veya konsola kodunuzdan iletileri göndermek için kullanabilirsiniz. Böylece bilgi iletilerini ve hata iletileri ayırt etmek isterseniz, bu nesne forms sayısını sağlar.  
  
 Daha uzun komut formun kullanabileceğiniz `window.console.[command]` konsol adlı yerel nesneleriyle olası Karışıklığı önlemek gerekiyorsa.  
  
> [!TIP]
>  Visual Studio'nun eski sürümlerini komutların tam bir set desteklemez. IntelliSense konsol nesne üzerinde desteklenen komutlar hakkında hızlı bilgi almak için kullanın.  
  
|Komut|Açıklama|Örnek|  
|-------------|-----------------|-------------|  
|`assert(expression, message)`|Bir ileti gönderir `expression` değerlendiren **false**.|`console.assert((x == 1), "assert message: x != 1");`|  
|`clear()`|Betik hata iletileri de dahil olmak üzere konsol penceresinden iletileri temizler ve ayrıca konsol penceresinde görüntülenen betik temizler. Giriş konsolunu komut isteminden girdiğiniz betik temizlemez.|`console.clear();`|  
|`count(title)`|Sayımı komutunu çağrıldı sayısı konsol penceresine gönderir. Her çağrı sayısı benzersiz olarak isteğe bağlı olarak tanımlanan `title`.<br /><br /> Konsol penceresinde var olan girdiyi tarafından tanımlanan `title` parametre (varsa) ve sayısı komutu tarafından güncelleştirildi. Yeni bir giriş oluşturulmaz.|`console.count();`<br /><br /> `console.count("inner loop");`|  
|`debug(message)`|Gönderen `message` konsol penceresi.<br /><br /> Bu komut, console.log için aynıdır.<br /><br /> Komutu kullanılarak geçirilen nesneleri, bir dize değerine dönüştürülür.|`console.debug("logging message");`|  
|`dir(object)`|Belirtilen nesnenin konsol penceresine gönderir ve bir nesne görselleştiricisi içinde görüntüler. Görselleştirici, konsol penceresinde özellikleri incelemek için kullanabilirsiniz.|`console.dir(obj);`|  
|`dirxml(object)`|Belirtilen XML düğümün gönderdiği `object` konsol penceresi ve bir XML düğümü ağaç olarak görüntüler.|`console.dirxaml(xmlNode);`|  
|`error(message)`|Gönderen `message` konsol penceresi. İleti metni, kırmızı ve başında tarafından bir hata simgesi.<br /><br /> Komutu kullanılarak geçirilen nesneleri, bir dize değerine dönüştürülür.|`console.error("error message");`|  
|`group(title)`|Konsol penceresine gönderilen iletiler için bir gruplama başlar ve isteğe bağlı gönderen `title` Grup etiketi olarak. Grupları iç içe geçebilir ve ağaç görünümünde konsol penceresinde görünür.<br /><br /> Grup * komutları bir bileşen modeli kullanımda olduğunda bazı senaryolarda konsol penceresi çıkışını görüntülemek daha kolay yapabilirsiniz.|`console.group("Level 2 Header");` <br /> `console.log("Level 2");` <br /> `console.group();` <br /> `console.log("Level 3");` <br /> `console.warn("More of level 3");` <br /> `console.groupEnd();` <br /> `console.log("Back to level 2");` <br /> `console.groupEnd();` <br /> `console.debug("Back to the outer level");`|  
|`groupCollapsed(title)`|Konsol penceresine gönderilen iletiler için bir gruplama başlar ve isteğe bağlı gönderen `title` Grup etiketi olarak. Kullanılarak gönderilen grupları `groupCollapsed` varsayılan olarak daraltılmış görünümünde görünür. Grupları iç içe geçebilir ve ağaç görünümünde konsol penceresinde görünür.|Kullanım aynıdır `group` komutu.<br /><br /> Örneğin bakın `group` komutu.|  
|`groupEnd()`|Geçerli grubun sona erer.<br /><br /> Gereksinimler:<br /><br /> Visual Studio 2013|Örneğin bakın `group` komutu.|  
|`info(message)`|Gönderen `message` konsol penceresi. İleti bir bilgi simgesi başında vardır.|`console.info("info message");`<br /><br /> Daha fazla örnek için bkz. [console.log çıktı biçimlendirme](#ConsoleLog) bu konuda.|  
|`log(message)`|Gönderen `message` konsol penceresi.<br /><br /> Bir nesne geçirirseniz, bu komut söz konusu nesne konsol penceresine gönderir ve bir nesne görselleştiricisi içinde görüntüler. Görselleştirici, konsol penceresinde özellikleri incelemek için kullanabilirsiniz.|`console.log("logging message");`|  
|`msIsIndependentlyComposed(element)`|Web uygulamalarında kullanılır. JavaScript kullanarak UWP uygulamalarında desteklenmiyor.|Desteklenmez.|  
|`profile(reportName)`|Web uygulamalarında kullanılır. JavaScript kullanarak UWP uygulamalarında desteklenmiyor.|Desteklenmez.|  
|`profileEnd()`|Web uygulamalarında kullanılır. JavaScript kullanarak UWP uygulamalarında desteklenmiyor.|Desteklenmez.|  
|`select(element)`|Belirtilen HTML seçer `element` içinde [DOM Gezgini](../debugger/quickstart-debug-html-and-css.md).|Console.Select(element);|  
|`time (name)`|İsteğe bağlı olarak tanımlanan bir süreölçer başlatır `name` parametresi. İle kullanıldığında `console.timeEnd`, hesaplar arasında geçen süreyi `time` ve `timeEnd`ve konsolunu kullanarak (ms cinsinden ölçülür) sonucu gönderir `name` öneki olarak dize. Uygulama kodunun performansı ölçmek için izlemeyi etkinleştirmek için kullanılır.|`console.time("app start");  app.start();  console.timeEnd("app start");`|  
|`timeEnd(name)`|İsteğe bağlı olarak tanımlanan bir zamanlayıcı durur `name` parametresi. Bkz: `time` konsol komutu.|`console.time("app start"); app.start(); console.timeEnd("app start");`|  
|`trace()`|Bir yığın izlemesi konsol penceresine gönderir. İzleme, tam çağrı yığınını içerir ve dosya adı ve satır numarası sütunu numarası gibi bilgileri içerir.|`console.trace();`|  
|`warn(message)`|Gönderen `message` konsol penceresinde, bir uyarı simgesi ile başlar.<br /><br /> Komutu kullanılarak geçirilen nesneleri, bir dize değerine dönüştürülür.|`console.warn("warning message");`|  
  
## <a name="miscellaneous-commands"></a>Çeşitli komutlar  
 Bu komutlar da (koddan kullanılamaz) JavaScript konsol penceresinde kullanılabilir.  
  
|Komut|Açıklama|Örnek|  
|-------------|-----------------|-------------|  
|`$0`, `$1`, `$2`, `$3`, `$4`|Konsol penceresinde belirtilen öğeyi döndürür. `$0` DOM Gezgini'nde seçili öğeyi döndürür `$1` DOM Gezgini ve dördüncü daha önce seçilen öğenin kadar benzeri daha önce seçilen öğeyi döndürür.|$3|  
|`$(id)`|Kimliğe göre bir öğeyi döndürür Bunun için bir kısayol komut olduğunu `document.getElementById(id)`burada `id` öğesi kimliğini temsil eden bir dize|`$("contenthost")`|  
|`$$(selector)`|CSS Seçici söz dizimini kullanarak belirtilen Seçici eşleşen öğeleri dizisi döndürür. Bunun için bir kısayol komut olduğunu `document.querySelectorAll()`.|`$$(".itemlist")`|  
|`cd()`<br /><br /> `cd(window)`|İfade değerlendirme bağlamının sayfasını varsayılan düzey penceresinden belirtilen çerçeve penceresine değiştirmenize olanak tanır. Çağırma `cd()` en üst düzey penceresine bağlamı olmadan parametrelerini döndürür.|`cd();`<br /><br /> `cd(myframe);`|  
|`select(element)`|Belirtilen öğeyi seçer [DOM Gezgini](../debugger/quickstart-debug-html-and-css.md).|`select(document.getElementById("element"));`<br /><br /> `select($("element"));`<br /><br /> `select($1);`|  
|`dir(object)`|Belirtilen nesne için Görselleştirici döndürür. Görselleştirici, konsol penceresinde özellikleri incelemek için kullanabilirsiniz.|`dir(obj);`|  
  
## <a name="checking-whether-a-console-command-exists"></a>Konsolu komut olup olmadığı denetleniyor  
 Belirli bir komut bunu kullanmayı denemeden önce mevcut olup olmadığını kontrol edebilirsiniz. Bu örnek varlığını denetler `console.log` komutu. Varsa `console.log` var, kodu çağırır.  
  
```javascript  
if (console && console.log) {  
    console.log("msg");  
}  
  
```  
  
## <a name="examining-objects-in-the-javascript-console-window"></a>JavaScript Konsolu penceresi nesneleri İnceleme  
 JavaScript Konsolu penceresi kullandığınızda, kapsam içi herhangi bir nesne ile etkileşim kurabilir. Konsol penceresinde bir kapsam dışı nesne incelemek için kullanın `console.log` , `console.dir`, veya kodunuzun diğer komutlar. Kodunuzda bir kesme noktası ayarlayarak kapsamda olmakla birlikte alternatif olarak, konsol penceresinde nesneden etkileşim kurabilirsiniz (**kesme noktası** > **kesme noktası Ekle**).  
  
##  <a name="ConsoleLog"></a> Console.log çıktı biçimlendirme  
 Birden çok bağımsız değişkenler, `console.log`, konsol bağımsız değişken bir dizi olarak kabul et ve çıktıyı birleştirir.  
  
```javascript  
var user = new Object();  
user.first = "Fred";  
user.last = "Smith";  
  
console.log(user.first, user.last);  
// Output:  
// Fred Smith  
  
```  
  
 `console.log` Ayrıca, çıktıyı biçimlendirmek için "printf" değiştirme desenleri destekler. Değiştirme desenleri ilk bağımsız değişken olarak kullanırsanız, ek bağımsız değişkenler, belirli kalıplarla kullanıldıkları sırada değiştirmek için kullanılır.  
  
 Aşağıdaki değiştirme desenleri desteklenir:  
  
- %s - dize  
   %i - tamsayı  
   %d - tamsayı  
   %f - float  
   %o - nesne  
   %b - ikili  
   %x - onaltılık  
   %e - üs  
  
  Değiştirme desenlerinde kullanmanın bazı örnekler şunlardır `console.log`:  
  
```javascript  
var user = new Object();  
user.first = "Fred";  
user.last = "Smith";  
user.age = 10.01;  
console.log("Hi, %s %s!", user.first, user.last);  
console.log("%s is %i years old!", user.first, user.age);  
console.log("%s is %f years old!", user.first, user.age);  
  
// Output:  
// Hi, Fred Smith!  
// Fred is 10 years old!  
// Fred is 10.01 years old!  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Hızlı Başlangıç: JavaScript hata ayıklama](../debugger/quickstart-debug-javascript-using-the-console.md)   
 [Hızlı başlangıç: HTML ve CSS hatalarını ayıklama](../debugger/quickstart-debug-html-and-css.md)