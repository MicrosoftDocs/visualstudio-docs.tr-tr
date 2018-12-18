---
title: '&lt;Varyasyon&gt; (JavaScript) | Microsoft Docs'
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
- <var> JavaScript XML tag
- var JavaScript XML tag
ms.assetid: 34ff9023-c81c-46d1-85b6-0022f0962e66
caps.latest.revision: 14
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 04f592bab7679ed3e8fe8791872ce2280d05359a
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49881982"
---
# <a name="ltvargt-javascript"></a>&lt;Varyasyon&gt; (JavaScript)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Belgelendirme bilgilerini bir değişken için belirtir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
<var type="ValueType" integer="true|false"  
    domElement="true|false" mayBeNull="true|false"  
    elementType="ArrayElementType" elementInteger="true|false"  
    elementDomElement="true|false" elementMayBeNull="true|false"  
    helpKeyword="keyword" locid="descriptionID">description  
</var>   
```  
  
#### <a name="parameters"></a>Parametreler  
 `type`  
 İsteğe bağlı. Değişken veri türü. Tür aşağıdakilerden biri olabilir:  
  
- Olduğu gibi ECMAScript 5 açıklamasında bir ECMAScript dil türü `Number` ve `Object`.  
  
- Gibi bir DOM nesnesi `HTMLElement`, `Window`, ve `Document`.  
  
- Bir JavaScript oluşturucu işlevi.  
  
  `integer`  
  İsteğe bağlı. Varsa `type` olduğu `Number`, değişkeni bir tam sayı olup olmadığını belirtir. Kümesine `true` ; tamsayı değişkeni olduğunu göstermek için Aksi takdirde, kümesine `false`. Bu öznitelik, IntelliSense bilgilerini sağlamak için Visual Studio tarafından kullanılmaz.  
  
  `domElement`  
  İsteğe bağlı. Bu öznitelik kullanım dışı; `type` özniteliği bu öznitelik göre önceliklidir. Bu öznitelik, belgelenmiş değişkeni DOM öğesi olup olmadığını belirtir. Kümesine `true` değişkeni bir DOM öğesi; olduğunu belirtmek için Aksi takdirde, kümesine `false`. Varsa `type` özniteliği ayarlanmamıştır ve `domElement` ayarlanır `true`, IntelliSense belgelenmiş değişken olarak değerlendirir bir `HTMLElement` deyim tamamlama gerçekleştirirken.  
  
  `mayBeNull`  
  İsteğe bağlı. Belgelenen değişkeni ayarlayıp ayarlayamayacağını belirler null. Kümesine `true` değişken ayarlanabilir, aksi takdirde çok belirtmek için ayarlanmış `false`. Varsayılan değer `false` şeklindedir. Bu öznitelik, IntelliSense bilgilerini sağlamak için Visual Studio tarafından kullanılmaz.  
  
  `elementType`  
  İsteğe bağlı. Varsa `type` olduğu `Array`, bu öznitelik, dizideki öğelerin türünü belirtir.  
  
  `elementInteger`  
  İsteğe bağlı. Varsa `type` olduğu `Array` ve `elementType` olduğu `Number`, bu öznitelik, dizideki öğelerin tamsayılar olup olmadığını belirtir. Kümesine `true` göstermek için dizideki öğelerin tamsayılardır; Aksi takdirde, kümesine `false`. Bu öznitelik, IntelliSense bilgilerini sağlamak için Visual Studio tarafından kullanılmaz.  
  
  `elementDomElement`  
  İsteğe bağlı. Bu öznitelik kullanım dışı; `elementType` özniteliği bu öznitelik göre önceliklidir. Varsa `type` olduğu `Array`, bu öznitelik, dizideki öğelerin DOM öğeleri olup olmadığını belirtir. Kümesine `true` belirtmek için öğeleri DOM öğeleri; Aksi takdirde, kümesine `false`. Varsa `elementType` özniteliği ayarlanmamıştır ve `elementDomElement` ayarlanır `true`, IntelliSense her öğe dizisi değerlendirir bir `HTMLElement` deyim tamamlama gerçekleştirirken.  
  
  `elementMayBeNull`  
  İsteğe bağlı. Varsa `type` olduğu `Array`, dizideki öğelerin ayarlayıp ayarlayamayacağını belirler null. Kümesine `true` dizideki öğelerin ayarlanabilir, aksi takdirde çok belirtmek için ayarlanmış `false`. Varsayılan değer `false` şeklindedir. Bu öznitelik, IntelliSense bilgilerini sağlamak için Visual Studio tarafından kullanılmaz.  
  
  `helpKeyword`  
  İsteğe bağlı. F1 Yardım anahtar sözcüğü.  
  
  `locid`  
  İsteğe bağlı. Yerelleştirme değişken hakkında bilgi için tanımlayıcı. Tanımlayıcıdır ya da bir üye kimliği veya karşılık gelen `name` öznitelik değeri bir ileti paketteki OpenAjax meta verileri tarafından tanımlanır. Belirtilen biçim tanımlayıcı türü bağımlı [ \<loc >](../ide/loc-javascript.md) etiketi.  
  
  `description`  
  İsteğe bağlı. Değişken açıklaması.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği kullanma işlemini gösterir `<var>` öğesi.  
  
```javascript  
/// <var>A rectangle that has a width of 5.</var>  
var Rectangle = {  
    /// <field type = 'Number'>The width of the rectangle.</field>  
    wid: 5,  
    /// <field type = 'Number'>The length of the rectangle.</field>  
    len: 0,  
    /// <field type='Number'>Returns the area of the rectangle.</field>  
    getArea: function (wid, len) {  
        return len * wid;  
    }  
}  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [XML Belge Açıklamaları](../ide/xml-documentation-comments-javascript.md)



