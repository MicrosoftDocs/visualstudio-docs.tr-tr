---
title: Visual Studio'da JavaScript | Microsoft Docs
ms.custom: ''
ms.date: 04/10/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 74dca14c-5071-416f-a92b-d09f95e3dfb8
caps.latest.revision: 1
author: bowdenk7
ms.author: wilkelly
manager: ghogen
ms.openlocfilehash: 75c234b2a3b16d3bcbe05da9f0818c73be0412db
ms.sourcegitcommit: 71218ffc33da325cc1b886f69ff2ca50d44f5f33
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/09/2018
ms.locfileid: "48880805"
---
# <a name="javascript-in-visual-studio-2017"></a>Visual Studio 2017'de JavaScript

JavaScript, Visual Studio'da birinci sınıf bir dildir. Visual Studio IDE'de JavaScript kodu yazarken standart düzenleme yardımlarının (kod parçacıkları, IntelliSense, vb.) çoğunu veya tümünü kullanabilirsiniz. Birçok uygulama türleri ve hizmetler için JavaScript kodu yazabilirsiniz.

> [!NOTE]
> Biz olmak için topluluk çok emek harcadığımızı katılmış [MDN web docs](https://developer.mozilla.org/en-US/) tüm (500'den fazla sayfa) için kendi MDN getiriyor Microsoft'un JavaScript API başvuru yönlendirmek Web'in tek, üstün geliştirme kaynak ortaklarınıza. Ayrıntılar için bkz. Bu [duyuru](https://blogs.windows.com/msedgedev/2018/06/26/chakra-docs-mdn-web-docs/).

## <a name="ES6"></a> Destek ve daha fazlası için ECMAScript 2015 (ES6)

Visual Studio, sözdizimi artık ECMAScript 2015/2016 gibi ECMAScript dil güncelleştirmelerini destekler.

### <a name="what-is-ecmascript-2015"></a>ECMAScript 2015 nedir?

JavaScript bir programlama dili olarak hala gelişen ve [TC39](http://www.ecma-international.org/memento/TC39.htm) komitesi güncelleştirmeleri yapmaktan sorumludur.
ECMAScript 2015 yararlı yeni söz dizimi ve İşlevler getiren JavaScript dil bir güncelleştirmedir. ES6 özellikler hakkında derinlemesine bir bakış için kullanıma [bu](http://es6-features.org) başvuru sitesi.

ECMAScript 2015 desteği, ek olarak Visual Studio ayrıca ECMAScript 2016 destekler ve yayınlandıkça ECMAScript gelecek sürümleri için destek gerekir. TC39 ve en son değişikliklerin ECMAScript kalmasını sağlamak için işlerini takip edin [github](https://github.com/tc39).

### <a name="transpile-javascript"></a>JavaScript derleyin

Bir ortak JavaScript ile en son ES6 + dil özelliklerini daha üretken olmanıza yardımcı olur, ancak çalışma zamanı ortamlarınızın (genellikle tarayıcıları) henüz bu yeni özellikleri desteklemeyen için kullanmak istediğiniz bir sorundur. Bu, hangi tarayıcılar izlemek için sahip olmanız (Bu can sıkıcı olabilir) hangi özellikleri desteklemek veya ES6 + kodunuzu, hedef çalışma zamanları (genellikle ES5) anladığınızı sürümüne dönüştürmek için bir yönteme ihtiyaç duyarsınız anlamına gelir. Çalışma zamanı "transpiling" genellikle adlandırılır anlayan bir sürüme kodunuzu dönüştürülüyor.

Böylece en üretken yapan kod yazın, ancak yine de kodunuzu herhangi bir platform üzerinde çalıştırmasını TypeScript anahtar özelliklerini özelliği derleyin ES6 + kod ES5 veya ES3 biridir. Çünkü JavaScript'te [!include[vs_dev15](../../docs/misc/includes/vs_dev15_md.md)] kullandığı aynı dilde hizmet TypeScript, çok ES5 transpilation için ES6 + avantajlarından yararlanabilirsiniz.

Transpilation ayarlanabilir önce bazı yapılandırma seçenekleri anlayış gereklidir.
TypeScript ile yapılandırılmış bir `tsconfig.json` dosya.
Böyle bir dosya olmaması durumunda bazı varsayılan değerler kullanılır.
Bu varsayılan uyumluluk açısından farklı bir bağlamda yalnızca burada JavaScript dosyaları (ve isteğe bağlı olarak `.d.ts` dosyaları) yok.
JavaScript dosyalarını derlemek için bir `tsconfig.json` dosya eklenmelidir ve bu seçeneklerden bazısı açıkça ayarlanması gerekir.

Tsconfig dosya için gerekli ayarları aşağıdaki gibidir:

 - `allowJs`: Bu değer ayarlanmalıdır `true` tanınması JavaScript dosyaları için. Varsayılan değer `false`, çünkü TypeScript JavaScript derler ve derleyicinin yalnızca derlenmiş dosyalar içermemelidir.
 - `outDir`: Yayılan JavaScript dosyaları algılanmaz ve sonra projeye dahil edebilmesi projede yer almayan bir konum bu değer ayarlanmalıdır (bkz `exclude`).
 - `module`: Modüller kullanıyorsanız, bu ayar gösterilen kod kullanması gereken hangi modül biçimi derleyiciye (örneğin `commonjs` düğümüne veya paketleyicileri Browserify gibi).
 - `exclude`: Bu ayar, projede içermeyecek şekilde klasörleri belirtir.
 Proje-olmayan klasörler gibi yanı sıra çıkış konumunu `node_modules` veya `temp`, bu ayarı eklenmesi gerekir.
 - `enableAutoDiscovery`: Bu ayar, daha önce belirtildiği gibi otomatik algılama ve tanım dosyalarını indirilmesini sağlar.
 - `compileOnSave`: Bu ayar, Visual Studio'da herhangi bir kaynak dosyası kaydedildiğinde derlemeniz, derleyiciye bildirir.
 - `typeAcquisition`: Bu ayarları kümesi otomatik tür alımı davranışını denetleyen (daha ayrıntılı olarak açıklayın [Bu bölümde](/visualstudio/ide/javascript-intellisense#Auto))

CommonJS modüller için JavaScript dosyalarını dönüştürmek ve bunları yerleştirmek için bir `./out` klasöründe aşağıdaki kullanabileceğinizi `tsconfig.json` dosyası:

```json
{
  "compilerOptions": {
    "module": "commonjs",
    "allowJs": true,
    "outDir": "out"
  },
  "exclude": [
    "node_modules",
    "wwwroot",
    "out"
  ],
  "compileOnSave": true,
  "typeAcquisition": {
    "enable": true
  }
}
```

Yerinde bir kaynak dosyanın ayarlarıyla (`./app.js`) vardı ve birkaç ECMAScript 2015 dil özellikleri aşağıda yer alan:

```js
import {Subscription} from 'rxjs/Subscription';  // ES6 import

class Foo {  // ES6 Class
    sayHi(name) {
        return `Hi ${name}, welcome to Salsa!`;  // ES6 template string
    }
}

export let sqr = x => x * x;  //ES6 export, let, and arrow function
export default Subscription;  //ES6 default export
```

Bir dosya için derleyicisindeki sonra `./out/app.js` hedefleyen ECMAScript şunun gibi görünen 5 (varsayılan):

```js
"use strict";
var Subscription_1 = require('rxjs/Subscription');
var Foo = (function () {
    function Foo() {
    }
    Foo.prototype.sayHi = function (name) {
        return "Hi " + name + ", welcome to Salsa!";
    };
    return Foo;
}());
exports.sqr = function (x) { return x * x; };
Object.defineProperty(exports, "__esModule", { value: true });
exports.default = Subscription_1.Subscription;
```

## <a name="better-intellisense"></a>Daha iyi IntelliSense

JavaScript IntelliSense içinde [!include[vs_dev15](../../docs/misc/includes/vs_dev15_md.md)] şimdi görünen parametreleri ve üye listelerini çok daha fazla bilgi olacaktır. Bu yeni bilgi kodunuzu daha iyi anlamak için perde arkasında statik analiz kullanır TypeScript dil hizmeti tarafından sağlanır. Yeni bir IntelliSense deneyimi hakkında daha fazla bilgi ve nasıl çalıştığını okuyabilir [burada](/visualstudio/ide/javascript-intellisense/).

## <a name="JSX"></a> JSX söz dizimi desteğini

JavaScript'te [!include[vs_dev15](../../docs/misc/includes/vs_dev15_md.md)] JSX söz dizimi için zengin destek sunar. JSX JavaScript dosyaları içinde HTML etiketleri izin veren bir söz dizimi kümesidir.

Tanımlanan bir React bileşeni aşağıdaki çizimde `comps.tsx` TypeScript dosyası ve bu bileşen gelen kullanılan `app.jsx` tam IntelliSense tamamlamaları ve JSX ifadelerde belgeler için dosya.
TypeScript gerekmez. Burada, bu özel bir örnek yalnızca bazı TypeScript kodu de içerecek şekilde gerçekleşir.

<img src="./media/react.png" height="500" width="640"/>

> [!NOTE]
> İçin React JSX sözdizimini dönüştürmek için çağırdığı ayarı `"jsx": "react"` eklenmelidir `compilerOptions` içinde `tsconfig.json` dosya.

Oluşturulma JavaScript dosyası '. / out/app.js derleme sırasında kodu da içerebilir:

```js
"use strict";
var comps_1 = require('./comps');
var x = React.createElement(comps_1.RepoDisplay, {description: "test"});
```

## <a name="configure-your-javascript-project"></a>JavaScript projenizi yapılandırın

Dil hizmeti anlamına gelir, IntelliSense sonuçlar döndürebilir ve diğer düzenleme özellikleri sağlamak için gerçekten çalıştırmadan kaynak kodunuzu analiz statik analiz tarafından desteklenmektedir.
Bu nedenle, büyük dosyaların boyutunu ve Miktar Proje bağlamı, daha fazla bellek dahil ve CPU analiz sırasında kullanılır.
Bu nedenle, proje şekli hakkında yapılan birkaç varsayılan varsayımlar vardır:

- `package.json` ve `bower.json` varsayılan ve projeniz tarafından kullanılan liste bağımlılıkları otomatik tür edinme (ATA) dahil
- Üst düzey `node_modules` klasörü kitaplığı kaynak kodunu içerir ve içeriği varsayılan olarak proje bağlamdan dışlanmaz
- Tüm diğer `.js`, `.jsx`, `.ts`, ve `.tsx` dosya, büyük olasılıkla biridir *kendi* kaynak dosyaları ve proje bağlamında eklenmelidir

Çoğu durumda, yalnızca projenizi açın ve varsayılan proje yapılandırmasını kullanarak mükemmel bir deneyim yaşadığınızdan mümkün olacaktır. Ancak, büyük veya farklı bir klasör yapılarını projelerinde, daha iyi odaklanmak dil hizmeti yalnızca kendi kaynak dosyaları hakkında daha fazla yapılandırmak için istenen olabilir.

### <a name="override-defaults"></a>Varsayılanları geçersiz kılma

Ekleyerek varsayılan yapılandırmayı geçersiz kılabilir bir `tsconfig.json` proje kökünüze dosya.
A `tsconfig.json` proje Bağlamınızı değiştirebilirsiniz birkaç farklı seçenek vardır.
Birkaç tanesi Aşağıda, ancak mevcut tüm seçeneklerin tam bir dizi için listelenen [deposunun şeması bkz](http://json.schemastore.org/tsconfig).

## <a name="important-tsconfigjson-options"></a>Önemli `tsconfig.json` seçenekleri

```json
{
  "compilerOptions": {
    "allowJs": true,          // include .js and .jsx in project context (defaults to only .ts and .tsx)
    "noEmit": true            // turns off downlevel compiler
  },
  "files": [],                // list of explicit files to include in the project context. Highest priority.
  "include": [],              // list of folders or glob patterns to include in the project context.
  "exclude": [],              // list of folders or glob patterns to exclude. Overridden by files array.
  "typeAcquisition": {
    "enable": true,           // Defaulted to "false" with a tsconfig. Enables better IntelliSense in JS.
    "include": [ "jquery" ],  // Specific libs to fetch .d.ts files that weren't picked up by ATA
    "exclude": [ "node" ]     // Specific libs to not fetch .d.ts files for
  }
}
```

### <a name="example-project-configuration"></a>Örnek Proje yapılandırması

Aşağıdaki Kurulum projesiyle verilen:

- Projenin kaynak dosyaları `wwwroot/js`
- Projenin lib dosyaları `wwwroot/lib`
- `bootstrap`, `jquery`, `jquery-validation`, ve `jquery-validation-unobtrusive` listelenir `bower.json`
- `kendo-ui` lib klasörüne el ile eklendi

![klasör yapısı](./media/folderStructure.png)

Aşağıdaki kullanabileceğinizi `tsconfig.json` dil emin olmak için hizmet yalnızca kaynak dosyalarınızda çözümler `js` klasörü, ancak yine de getirir ve kullanır `.d.ts` kitaplıkları için dosyaları, `lib` klasör.

```json
{
  "compilerOptions": {
    "allowJs": true,
    "noEmit": true
  },
  "exclude": ["wwwroot/lib"],  //ignore lib folders, we will get IntelliSense via ATA
  "typeAcquisition": {
    "enable": true,
    "include": [ "kendo-ui" ]  //kendo-ui wasn't added via bower, so we need to list it here
  }
}
```
# <a name="troubleshooting-the-javascript-language-service-has-been-disabled-for-the-following-projects"></a>JavaScript dil hizmeti sorun giderme şu projeler için devre dışı bırakıldı
İçeriği çok büyük miktarda olan bir JavaScript projesini açtığınızda "JavaScript language service şu projeler için devre dışı bırakıldı" yazan bir ileti alabilirsiniz. Çok büyük miktarda JavaScript kaynak sahip olmak için en yaygın nedeni, 20 MB proje limiti aşan kaynak koduyla birlikte kitaplıkları dahil olmak üzere nedeniyle olmasıdır.

Projenizi en iyi duruma getirmek için basit bir yol eklemektir bir `tsconfig.json` hangi dosyaları yoksaymak güvenli olduğunu bildiğiniz dil hizmeti sağlamak için proje kökünüze dosyasında. Kitaplıkları depolandığı en yaygın dizinleri hariç tutmak için aşağıdaki örneği kullanın:

```json
{
  "compilerOptions": {
    "allowJs": true,
    "allowSyntheticDefaultImports": true,
    "maxNodeModuleJsDepth": 2,
    "noEmit": true,
    "skipLibCheck": true
  },
  "exclude": [
    "**/bin",
    "**/bower_components",
    "**/jspm_packages",
    "**/node_modules",
    "**/obj",
    "**/platforms"
  ]
}
```

Gördüğünüz gibi dizin ekleyin. Bazı diğer örnekleri, "Satıcı" veya "wwwroot/lib" dizinleri içerir. 

> [!NOTE]
> Derleyici özelliği `disableSizeLimit` 20 MB onay sınırını devre dışı bırakmak için de kullanılabilir. Dil hizmeti sınırını devre dışı bırakma çökebilir çünkü bu özelliği kullanırken özel önlemleri alın.

## <a name="notable-changes-from-visual-studio-2015"></a>Visual Studio 2015 önemli değişiklikler

Olarak [!include[vs_dev15](../../docs/misc/includes/vs_dev15_md.md)] tamamen yeni bir dil hizmeti özellikleri birkaç farklı davranışları vardır veya belirtilmemelidir önceki deneyiminden.
JSDoc, özel kaldırılmasını ile VSDoc yerine en önemli değişiklikler `.intellisense.js` uzantıları ve belirli kod desenleri için sınırlı IntelliSense.

### <a name="no-more-references-or-referencesjs"></a>Daha fazla `///<references/>` veya `_references.js`

Daha önce IntelliSense kapsamınızda dosyaları olan belirli bir anda anlamak oldukça karmaşıktır. Bazen tüm dosyalarınızı kapsamdaki ve bazen bölümdü etmesi ve el ile başvuru yönetim içeren karmaşık yapılandırmalar için bu neden. Artık başvuru yönetimi konusunda düşünmek gerekir ve zorunda kalmazsınız üç eğik çizgi açıklamaları başvurur. ileride veya `_references.js` dosyaları.

Bkz: [JavaScript IntelliSense](/visualstudio/ide/javascript-intellisense/) IntelliSense birlikte nasıl çalıştığı hakkında daha fazla bilgi için sayfa.

### <a name="vsdoc"></a>VSDoc

Bazen VSDocs adlandırılır, XML belge açıklamaları, daha önce kaynak kodunuzu IntelliSense sonuçlarını buff için kullanılacak ek verileriyle donatmak için de kullanılabilir.
Şunun için artık VSDoc desteklenmiyor [JSDoc](http://usejsdoc.org/about-getting-started.html) yazma ve JavaScript için kabul edilen standart kolay olduğu.

### <a name="intellisensejs-extensions"></a>`.intellisense.js` Uzantıları

Daha önce yazabilirsiniz [IntelliSense uzantıları](https://msdn.microsoft.com/library/hh874692.aspx) olduğu izin üçüncü taraf kitaplıklar için özel tamamlama sonuçlarını eklemek.
Bu uzantılar, yazma ve yükleme için oldukça zor ve yeni dil hizmetini ileride bu dosyaları desteklemeyeceği için bunlara başvuran hantal,.
Daha kolay bir alternatif olarak, eskisiyle aynı IntelliSense yararları sağlamak üzere bir TypeScript tanım dosyası yazabilirsiniz `.intellisense.js` uzantıları.
Bildirimi hakkında daha fazla bilgi (`.d.ts`) dosyası yazma [burada](http://www.typescriptlang.org/docs/handbook/declaration-files/introduction.html).

### <a name="unsupported-patterns"></a>Desteklenmeyen desenleri

Yeni dil hizmetini bir yürütme altyapısı yerine statik analiz tarafından desteklenen olduğundan (okuma [bu sorunu](https://github.com/Microsoft/TypeScript/issues/4789) bilgi farklar için), artık algılanabilir birkaç JavaScript desen vardır.
En yaygın desen, "expando" modelidir.
Şu anda dil hizmeti Yığılmış bildiriminden sonra özelliklere sahip nesne üzerinde IntelliSense sağlayamaz.
Örneğin:

```js
var obj = {};
obj.a = 10;
obj.b = "hello world";
obj. // IntelliSense won't show properties a or b
```

Bu sorunu, nesne oluşturma sırasında özelliklerini bildirerek alabilirsiniz:

```js
var obj = {
    "a": 10,
    "b": "hello world"
}
obj. // IntelliSense shows properties a and b
```

JSDoc açıklamasını şu şekilde ekleyebilirsiniz:

```js
/**
 * @type {{a: number, b: string}}
 */
var obj = {};
obj.a = 10;
obj.b = "hello world";
obj. // IntelliSense shows properties a and b
```
