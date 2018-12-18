---
title: JavaScript IntelliSense
ms.date: 06/28/2017
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
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
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 666ce7d65269992af486e59c6b5ce11e94da736b
ms.sourcegitcommit: bc43970c000f07c9cc2051f1264a9742943a9755
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/09/2018
ms.locfileid: "51348139"
---
# <a name="javascript-intellisense"></a>JavaScript IntelliSense

[!include[vs_dev15](../misc/includes/vs_dev15_md.md)] düzenleme deneyimi elde edebilmesi güçlü bir JavaScript sağlar. Temel TypeScript dil hizmeti tarafından desteklenen, Visual Studio, daha zengin IntelliSense, modern JavaScript özellikleri için destek sunar ve verimliliğin yeniden düzenleme, Tanıma Git gibi özellikleri ve daha fazlası.

> [!NOTE]
> JavaScript dil hizmeti [!include[vs_dev15](../misc/includes/vs_dev15_md.md)] dil hizmeti (çağrılan "Salsa") için yeni bir altyapısını kullanır. Ayrıntılar bu konuda dahil edilir ve bu da okuyabilirsiniz [blog gönderisi](https://blogs.msdn.microsoft.com/visualstudio/2016/11/28/more-productive-javascript-in-visual-studio-2017-rc/). Yeni düzenleme deneyimi, çoğunlukla da Visual Studio Code için geçerlidir. Bkz: [VS Code belgelerindeki](https://code.visualstudio.com/docs/languages/javascript) daha fazla bilgi için.

Visual Studio genel IntelliSense işlevselliği hakkında daha fazla bilgi için bkz. [IntelliSense kullanarak](../ide/using-intellisense.md).

## <a name="whats-new-in-the-javascript-language-service-in-includevsdev15miscincludesvsdev15mdmd"></a>JavaScript dil hizmeti içindeki yenilikler nelerdir? [!include[vs_dev15](../misc/includes/vs_dev15_md.md)]

İtibariyle [!include[vs_dev15](../misc/includes/vs_dev15_md.md)], JavaScript IntelliSense, parametre ve üye listelerini çok daha fazla bilgi görüntüler.
Bu yeni bilgi kodunuzu daha iyi anlamak için perde arkasında statik analiz kullanır TypeScript dil hizmeti tarafından sağlanır.
TypeScript, bu bilgileri oluşturmak için çeşitli kaynaklardan kullanır:

- [Tür çıkarımı üzerinde temel IntelliSense](#TypeInference)
- [JSDoc üzerinde temel IntelliSense](#JsDoc)
- [TypeScript bildirim dosyalarını temel IntelliSense](#TsDeclFiles)
- [Tür tanımları otomatik edinme](#Auto)

<a name="TypeInference"></a>
### <a name="intellisense-based-on-type-inference"></a>Tür çıkarımı üzerinde temel IntelliSense

JavaScript'te, çoğu zaman kullanılabilir açık tür bilgisi yok. Neyse ki, genellikle bir türünün çevreleyen kod bağlamı verilen şekil yapmak oldukça kolaydır.
Bu işlem, tür çıkarımı çağrılır.

Bir değişken veya özellik için genellikle türü veya en son değer atama başlatmak için kullanılan değer türüdür.

```js
var nextItem = 10;
nextItem; // here we know nextItem is a number

nextItem = "box";
nextItem; // now we know nextItem is a string
```

Bir işlev için dönüş türünü dönüş deyimlerinden çıkarılan.

İşlev parametreleri için şu anda hiçbir çıkarımı olmakla birlikte, bu sorunu çözmek için yolla JSDoc veya TypeScript kullanarak *. d.ts* dosyaları (sonraki bölümlere bakın).

Ayrıca, aşağıdakiler için özel çıkarımı vardır:

- Bir oluşturucu işlevi ve prototip özelliğine atamaları kullanarak belirtilen "ES3-style" sınıflar.
- Özelliği atamaları belirtilen CommonJS stili modülü desenleri `exports` nesne veya atamalarını `module.exports` özelliği.

```js
function Foo(param1) {
    this.prop = param1;
}
Foo.prototype.getIt = function () { return this.prop; };
// Foo will appear as a class, and instances will have a 'prop' property and a 'getIt' method.

exports.Foo = Foo;
// This file will appear as an external module with a 'Foo' export.
// Note that assigning a value to "module.exports" is also supported.
```

<a name="JsDoc"></a>
### <a name="intellisense-based-on-jsdoc"></a>JSDoc üzerinde temel IntelliSense

Burada tür çıkarımı sağlamaz istenen tür bilgisi (veya belgeleri desteklemek için), tür bilgilerini sağlanmalı açıkça JSDoc ek açıklamaları.  Örneğin, belirli bir tür kısmen bildirilen bir nesnenin vermek için kullanabileceğiniz `@type` aşağıda gösterildiği gibi etiketleyin:

```js
/**
 * @type {{a: boolean, b: boolean, c: number}}
 */
var x = {a: true};
x.b = false;
x. // <- "x" is shown as having properties a, b, and c of the types specified
```

Belirtildiği gibi işlev parametrelerini hiçbir zaman algılanır. Ancak, JSDoc kullanılarak `@param` türleri de işlev parametreleri için etiket ekleyebilirsiniz.

```js
/**
 * @param {string} param1 - The first argument to this function
 */
function Foo(param1) {
    this.prop = param1; // "param1" (and thus "this.prop") are now of type "string".
}
```

Bkz: [JavaScript JSDoc desteği](https://github.com/Microsoft/TypeScript/wiki/JsDoc-support-in-JavaScript) JsDoc ek açıklamaları şu anda desteklenmiyor.

<a name="TsDeclFiles"></a>
### <a name="intellisense-based-on-typescript-declaration-files"></a>TypeScript bildirim dosyalarını temel IntelliSense

JavaScript ve TypeScript artık aynı language service'ı temel aldığından, daha zengin bir şekilde etkileşim kurabilirsiniz. JavaScript IntelliSense, bildirilen değerleri için örneğin sağlanabilir bir *. d.ts* dosyası (bkz [TypeScript belgeleri](https://www.typescriptlang.org/docs/handbook/declaration-files/introduction.html)), ve arabirimler ve sınıflar TypeScript içinde bildirilen gibi türler JsDoc yorumları türleri olarak kullanmak için kullanılabilir.

Aşağıda, basit bir örnek (aracılığıyla bir arabirimi) gibi tür bilgilerini sağlamaktan TypeScript tanım dosyasının bir JavaScript dosyasına aynı projede göstereceğiz (kullanarak bir `JsDoc` etiketi).

<img src="https://raw.githubusercontent.com/wiki/Microsoft/TypeScript/images/decl1.png" height="400" width="640" alt="TypeScript definition file" />

<a name="Auto"></a>
### <a name="automatic-acquisition-of-type-definitions"></a>Tür tanımları otomatik edinme

TypeScript dünyanın en popüler JavaScript kitaplıklarını tarafından açıklanan kendi API sahip *. d.ts* dosya ve tür tanımları için en yaygın depo açıktır [DefinitelyTyped](https://github.com/DefinitelyTyped/DefinitelyTyped).

Varsayılan olarak, hangi JavaScript kitaplıklarını kullanın ve otomatik olarak karşıdan yüklenir ve buna karşılık gelen başvuru olan algılama Salsa dil hizmeti çalışacaktır *. d.ts* daha zengin sağlamak için kitaplık açıklayan dosyası IntelliSense. Kullanıcı klasörünün altında yer önbelleğine indirilen dosyaları *%LOCALAPPDATA%\Microsoft\TypeScript*.

> [!NOTE]
> Bu özellik **devre dışı** kullanıyorsanız varsayılan olarak bir *tsconfig.json* yapılandırma dosyası, ancak anahatları belirlenmiş olarak daha fazla etkin olarak aşağıda ayarlanmış olabilir.

Şu anda npm'den indirilen bağımlılıklar için otomatik algılama çalışır (okuyarak *package.json* dosyası), Bower (okuyarak *bower.json* dosyası) ve bir listesiyle eşleşen gevşek projenize dosyalar için kabaca üst 400 en popüler JavaScript kitaplıklarını. Örneğin, *jquery 1.10.min.js* dosyayı projenize *jquery.d.ts* getirildi ve daha iyi düzenleme deneyimi sağlamak için yüklenir. Bu *. d.ts* dosya, projenizdeki herhangi bir etkisi olacaktır.

Otomatik edinme kullanmak istemiyorsanız, aşağıda belirtildiği gibi bir yapılandırma dosyasına ekleyerek devre dışı bırakın. Yine de kullanmak için tanım dosyalarını doğrudan projenize içinde el ile yerleştirebilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [IntelliSense Kullanma](../ide/using-intellisense.md)
- [JavaScript desteği (Mac için Visual Studio)](/visualstudio/mac/javascript)