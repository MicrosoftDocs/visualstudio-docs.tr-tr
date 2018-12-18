---
title: '&lt;param&gt; (JavaScript) | Microsoft Docs'
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
- <param> JavaScript XML tag
- param JavaScript XML tag
ms.assetid: 2c4e0167-c1dd-4e54-83f1-c437856bddc1
caps.latest.revision: 22
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: b1178fc6ff2cb5b4664930eaa70fd3de5ebed0f5
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49949077"
---
# <a name="ltparamgt-javascript"></a>&lt;param&gt; (JavaScript)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Belgelendirme bilgilerini bir parametre için bir işlevi veya yöntemi belirtir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
<param name="parameterName" type="ParameterType"  
    integer="true|false" domElement="true|false"  
    mayBeNull="true|false" elementType="ArrayElementType"  
    elementInteger="true|false" elementDomElement="true|false"  
    elementMayBeNull="true|false" locid="descriptionID"  
    parameterArray="true|false" optional="true|false"  
    value="code">description  
</param>  
```  
  
#### <a name="parameters"></a>Parametreler  
 `name`  
 Gerekli. Parametrenin adı.  
  
 `type`  
 İsteğe bağlı. Parametrenin veri türü. Tür aşağıdakilerden biri olabilir:  
  
- ECMAScript dil yazın, ECMAScript 5 açıklamasında gibi `Number` ve `Object`.  
  
- Gibi bir DOM nesnesi `HTMLElement`, `Window`, ve `Document`.  
  
- Bir JavaScript oluşturucu işlevi.  
  
  `integer`  
  İsteğe bağlı. Varsa `type` olduğu `Number`, parametresinin bir tamsayı olup olmadığını belirtir. Kümesine `true` parametresi tamsayı; olduğunu belirtmek için Aksi takdirde, kümesine `false`. Bu öznitelik, IntelliSense bilgilerini sağlamak için Visual Studio tarafından kullanılmaz.  
  
  `domElement`  
  İsteğe bağlı. Bu öznitelik kullanım dışı; `type` özniteliği bu öznitelik göre önceliklidir. Bu öznitelik belgelenmiş parametresinin bir DOM öğesi olup olmadığını belirtir. Kümesine `true` parametresi bir DOM öğesi; olduğunu belirtmek için Aksi takdirde, kümesine `false`. Varsa `type` özniteliği ayarlanmamıştır ve `domElement` ayarlanır `true`, IntelliSense belgelenmiş parametre olarak değerlendirir bir `HTMLElement` deyim tamamlama gerçekleştirirken.  
  
  `mayBeNull`  
  İsteğe bağlı. Belgelenen parametresi ayarlayıp ayarlayamayacağını belirler null. Kümesine `true` parametresi ayarlanabilir, aksi takdirde çok belirtmek için ayarlanmış `false`. Varsayılan değer `false` şeklindedir. Bu öznitelik, IntelliSense bilgilerini sağlamak için Visual Studio tarafından kullanılmaz.  
  
  `elementType`  
  İsteğe bağlı. Varsa `type` olduğu `Array`, bu öznitelik, dizideki öğelerin türünü belirtir.  
  
  `elementInteger`  
  İsteğe bağlı. Varsa `type` olduğu `Array` ve `elementType` olduğu `Number`, bu öznitelik, dizideki öğelerin tamsayılar olup olmadığını belirtir. Kümesine `true` göstermek için dizideki öğelerin tamsayılardır; Aksi takdirde, kümesine `false`. Bu öznitelik, IntelliSense bilgilerini sağlamak için Visual Studio tarafından kullanılmaz.  
  
  `elementDomElement`  
  İsteğe bağlı. Bu öznitelik kullanım dışı; `elementType` özniteliği bu öznitelik göre önceliklidir. Varsa `type` olduğu `Array`, bu öznitelik, dizideki öğelerin DOM öğeleri olup olmadığını belirtir. Kümesine `true` belirtmek için öğeleri DOM öğeleri; Aksi takdirde, kümesine `false`. Varsa `elementType` özniteliği ayarlanmamıştır ve `elementDomElement` ayarlanır `true`, IntelliSense her öğe dizisi değerlendirir bir `HTMLElement` deyim tamamlama gerçekleştirirken.  
  
  `elementMayBeNull`  
  İsteğe bağlı. Varsa `type` olduğu `Array`, dizideki öğelerin ayarlayıp ayarlayamayacağını belirler null. Kümesine `true` dizideki öğelerin ayarlanabilir, aksi takdirde çok belirtmek için ayarlanmış `false`. Varsayılan değer `false` şeklindedir. Bu öznitelik, IntelliSense bilgilerini sağlamak için Visual Studio tarafından kullanılmaz.  
  
  `locid`  
  İsteğe bağlı. Parametresi ile ilgili bilgileri yerelleştirme tanımlayıcısı. Tanımlayıcıdır ya da bir üye kimliği veya karşılık gelen `name` öznitelik değeri bir ileti paketteki OpenAjax meta verileri tarafından tanımlanır. Belirtilen biçim tanımlayıcı türü bağımlı [ \<loc >](../ide/loc-javascript.md) öğesi.  
  
  `parameterArray`  
  İsteğe bağlı. Belgelenen parametresi desteklenen parametreler yinelenen benzer işlevi çağrısında yinelenen olup olmadığını belirtir `String.format` işlevi. Kümesine `true` parametre olabilir, aksi takdirde yinelenen belirtmek için ayarlanmış `false`. Bu öznitelik, IntelliSense bilgilerini sağlamak için Visual Studio tarafından kullanılmaz.  
  
  `optional`  
  İsteğe bağlı. Belgelenen parametrenin çağıran işlevin isteğe bağlı olup olmadığını belirtir. Kümesine `true` parametresi isteğe bağlı; Aksi durumda olduğunu belirtmek için ayarlanmış `false`.  
  
  `value`  
  İsteğe bağlı. İşlev kodunun kendisi yerine IntelliSense tarafından kullanılmak üzere değerlendirilmelidir kodu belirtir. Bu parametre türü tanımlanmamış olduğunda tür bilgisini sağlaması özniteliğidir. Örneğin, kullanabileceğiniz `value=’1’` parametre türü bir sayı olarak değerlendirilecek.  
  
  `description`  
  İsteğe bağlı. Parametre açıklaması.  
  
## <a name="remarks"></a>Açıklamalar  
 Yalnızca gerekli bir özniteliktir `name`. Diğer tüm öznitelikler isteğe bağlıdır.  
  
 İşlevler, aşağıdakiler gibi ek açıklama eklemek için kullanılan öğeleri [ \<Özet >](../ide/summary-javascript.md), [ \<param >](../ide/param-javascript.md), ve [ \<döndürür >](../ide/returns-javascript.md), yerleştirilmesi gerekir herhangi bir deyim önce işlev gövdesinde.  
  
 Varsa birden çok `<param>` aynı adı, biri olan öğeler `<param>` öğeleri kullanılır ve yedekli öğeleri yok sayılır. Hangi öğe kullanılan belirler davranışı tanımlı değil. Varsa `name` başvuruyor var olmayan bir parametre için öğe yoksayılır.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği kullanma işlemini gösterir `<param>` öğesi.  
  
```javascript  
function areaFunction(radiusParam)  
{  
    /// <summary>Determines the area of a circle when provided a radius parameter.</summary>  
    /// <param name="radiusParam" type="Number">The radius of the circle.</param>  
    /// <returns type="Number">The area.</returns>  
    var areaVal;  
    areaVal = Math.PI * radiusParam * radiusParam;  
    return areaVal;  
}  
  
// Uses of <param> with the value attribute.  
  
function calculate(a) {  
    /// <param name='a' value='1'/>  
    a.    // Completion list for a Number.  
}  
  
function calculate(a) {  
    /// <param name='a' value='{x:0,y:0}'/>  
    a.    // x and y appear in the completion list.  
}  
  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [XML Belge Açıklamaları](../ide/xml-documentation-comments-javascript.md)



