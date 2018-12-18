---
title: '&lt;döndürür&gt; (JavaScript) | Microsoft Docs'
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
- returns JavaScript XML tag
- <returns> JavaScript XML tag
ms.assetid: 10d97829-c0ae-40a5-b04c-d8b538cdefbc
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 5896c35c53feedb2f253bd86691f2fbf6793099e
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49875716"
---
# <a name="ltreturnsgt-javascript"></a>&lt;döndürür&gt; (JavaScript)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bir işlev veya metot çağrısının sonucuna belgeleri bilgilerini belirtir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
<returns type="ValueType" integer="true|false"  
    domElement="true|false" mayBeNull="true|false"  
    elementType="ArrayElementType" elementInteger="true|false"  
    elementDomElement="true|false" elementMayBeNull="true|false"  
    locid="descriptionID" value="code">description  
</returns>  
```  
  
#### <a name="parameters"></a>Parametreler  
 `type`  
 İsteğe bağlı. Dönüş değerinin veri türü. Tür aşağıdakilerden biri olabilir:  
  
- ECMAScript dil yazın, ECMAScript 5 açıklamasında gibi `Number` ve `Object`.  
  
- Gibi bir DOM nesnesi `HTMLElement`, `Window`, ve `Document`.  
  
- Bir JavaScript oluşturucu işlevi.  
  
  `integer`  
  İsteğe bağlı. Varsa `type` olduğu `Number`, dönüş değeri bir tamsayı olup olmadığını belirtir. Kümesine `true` dönüş değeri bir tamsayı; olduğunu belirtmek için Aksi takdirde, kümesine `false`. Bu öznitelik, IntelliSense bilgilerini sağlamak için Visual Studio tarafından kullanılmaz.  
  
  `domElement`  
  İsteğe bağlı. Bu öznitelik kullanım dışı; `type` özniteliği bu öznitelik göre önceliklidir. Bu öznitelik, belgelenmiş dönüş değeri bir DOM öğesi olup olmadığını belirtir. Kümesine `true` dönüş değeri bir DOM öğesi; olduğunu belirtmek için Aksi takdirde, kümesine `false`. Varsa `type` özniteliği ayarlanmamıştır ve `domElement` ayarlanır `true`, IntelliSense belgelenmiş dönüş değeri olarak değerlendirir bir `HTMLElement` deyim tamamlama gerçekleştirirken.  
  
  `mayBeNull`  
  İsteğe bağlı. Belge değer ayarlanabilir döndürüp döndürmeyeceğini belirtir null. Kümesine `true` dönüş değeri ayarlanabilir, aksi takdirde çok belirtmek için ayarlanmış `false`. Varsayılan değer `false` şeklindedir. Bu öznitelik, IntelliSense bilgilerini sağlamak için Visual Studio tarafından kullanılmaz.  
  
  `elementType`  
  İsteğe bağlı. Varsa `type` olduğu `Array`, bu öznitelik, dizideki öğelerin türünü belirtir.  
  
  `elementInteger`  
  İsteğe bağlı. Varsa `type` olduğu `Array` ve `elementType` olduğu `Number`, bu öznitelik, dizideki öğelerin tamsayılar olup olmadığını belirtir. Kümesine `true` göstermek için dizideki öğelerin tamsayılardır; Aksi takdirde, kümesine `false`. Bu öznitelik, IntelliSense bilgilerini sağlamak için Visual Studio tarafından kullanılmaz.  
  
  `elementDomElement`  
  İsteğe bağlı. Bu öznitelik kullanım dışı; `elementType` özniteliği bu öznitelik göre önceliklidir. Varsa `type` olduğu `Array`, bu öznitelik, dizideki öğelerin DOM öğeleri olup olmadığını belirtir. Kümesine `true` belirtmek için öğeleri DOM öğeleri; Aksi takdirde, kümesine `false`. Varsa `elementType` özniteliği ayarlanmamıştır ve `elementDomElement` ayarlanır `true`, IntelliSense her öğe dizisi değerlendirir bir `HTMLElement` deyim tamamlama gerçekleştirirken.  
  
  `elementMayBeNull`  
  İsteğe bağlı. Varsa `type` olduğu `Array`, dizideki öğelerin ayarlayıp ayarlayamayacağını belirler null. Kümesine `true` dizideki öğelerin ayarlanabilir, aksi takdirde çok belirtmek için ayarlanmış `false`. Varsayılan değer `false` şeklindedir. Bu öznitelik, IntelliSense bilgilerini sağlamak için Visual Studio tarafından kullanılmaz.  
  
  `locid`  
  İsteğe bağlı. Dönüş değeri hakkında yerelleştirme bilgisi tanımlayıcısı. Tanımlayıcıdır ya da bir üye kimliği veya karşılık gelen `name` öznitelik değeri bir ileti paketteki OpenAjax meta verileri tarafından tanımlanır. Belirtilen biçim tanımlayıcı türü bağımlı [ \<loc >](../ide/loc-javascript.md) etiketi.  
  
  `value`  
  İsteğe bağlı. İşlev kodunun kendisi yerine IntelliSense tarafından kullanılmak üzere değerlendirilmelidir kodu belirtir. Örneğin, IntelliSense gibi zaman uyumsuz geri çağırmalar için sağlamak için bu özniteliği kullanabilirsiniz bir `Promise`. Kullanarak `value` özniteliğini `<returns>` öğesi uzun kod yürütme atlayarak IntelliSense performansını geliştirebilir.  
  
  `description`  
  İsteğe bağlı. Dönüş değeri bir açıklaması.  
  
## <a name="remarks"></a>Açıklamalar  
 `<returns>` Öğesi, herhangi bir deyim önce işlev gövdesindeki yerleştirilmelidir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği kullanma işlemini gösterir `<returns>` öğesi.  
  
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
  
// The following examples use the <remarks> element with a value attribute.  
  
function getJson(complete) {   
    /// <returns value='complete("")' ></returns>  
    var r = new XMLHttpRequest();   
    // . . .   
}   
  
getJson(function (json) {   
    json.  // IntelliSense for a String object is   
           // available here.  
});  
  
function calculate(x) {  
    /// <returns value='1'/>  
}  
calculate().  // Completion list for a Number.  
  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [XML Belge Açıklamaları](../ide/xml-documentation-comments-javascript.md)



