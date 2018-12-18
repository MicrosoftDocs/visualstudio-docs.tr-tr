---
title: '&lt;alan&gt; (JavaScript) | Microsoft Docs'
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
- <field> JavaScript XML tag
- field JavaScript XML tag
ms.assetid: c494bae0-3095-42a3-aa0a-4c415188c65c
caps.latest.revision: 23
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: a57f84901f2ac6bc691c50fa6d1e3c8b94db6c50
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49939912"
---
# <a name="ltfieldgt-javascript"></a>&lt;alan&gt; (JavaScript)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bir alan veya bir nesne üzerinde tanımlanan üyesi için bir açıklama da dahil olmak üzere, belgelendirme bilgilerini belirtir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
<field name="fieldName" static="true|false"  
    type="FieldType" integer="true|false"  
    domElement="true|false" mayBeNull="true|false"  
    elementType="ArrayElementType" elementInteger="true|false"  
    elementDomElement="true|false" elementMayBeNull="true|false"  
    helpKeyword="keyword" locid="descriptionID"  
    value="code">description  
</field>  
```  
  
#### <a name="parameters"></a>Parametreler  
 `name`  
 Alan veya üye adı. Zaman `<field>` öğe bir oluşturucu işlevi içinde kullanılan `name` gereklidir ve etiketin uygulandığı üye tanımlar. Zaman `<field>` öğesi bir alan doğrudan yorumlama, bu öznitelik yoksayılır ve Visual Studio tarafından kullanılan adı kaynak kodundaki gerçek alan adıdır.  
  
 `static`  
 İsteğe bağlı. Alan oluşturucu işlevi bir üyesidir veya nesnenin bir üyesi Oluşturucu işlevin döndürdüğü belirtir. Kümesine `true` alan oluşturucu işlevi bir üyesi olarak değerlendirilecek. Kümesine `false` alan bir oluşturucu işlevi tarafından döndürülen nesne üyesi olarak değerlendirilecek.  
  
 `type`  
 İsteğe bağlı. Alanın veri türü. Tür aşağıdakilerden biri olabilir:  
  
- ECMAScript dil yazın, ECMAScript 5 açıklamasında gibi `Number` ve `Object`.  
  
- Gibi bir DOM nesnesi `HTMLElement`, `Window`, ve `Document`.  
  
- Bir JavaScript oluşturucu işlevi.  
  
  `integer`  
  İsteğe bağlı. Varsa `type` olduğu `Number`, alanı bir tamsayı olup olmadığını belirtir. Kümesine `true` alanı bir tamsayı; olduğunu belirtmek için Aksi takdirde, kümesine `false`. Bu öznitelik, IntelliSense bilgilerini sağlamak için Visual Studio tarafından kullanılmaz.  
  
  `domElement`  
  İsteğe bağlı. Bu öznitelik kullanım dışı; `type` özniteliği bu öznitelik göre önceliklidir. Bu öznitelik, belgelenmiş alanın bir DOM öğesi olup olmadığını belirtir. Kümesine `true` alan bir DOM öğesi; olduğunu belirtmek için Aksi takdirde, kümesine `false`. Varsa `type` özniteliği ayarlanmamıştır ve `domElement` ayarlanır `true`, IntelliSense belgelenmiş alan olarak değerlendirir bir `HTMLElement` deyim tamamlama gerçekleştirirken.  
  
  `mayBeNull`  
  İsteğe bağlı. Belgelenen alanın ayarlayıp ayarlayamayacağını belirler null. Kümesine `true` alan ayarlanabilir, aksi takdirde çok belirtmek için ayarlanmış `false`. Varsayılan değer `false` şeklindedir. Bu öznitelik, IntelliSense bilgilerini sağlamak için Visual Studio tarafından kullanılmaz.  
  
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
  İsteğe bağlı. Yerelleştirme alanı hakkında bilgi için tanımlayıcı. Tanımlayıcıdır ya da bir üye kimliği veya karşılık gelen `name` öznitelik değeri bir ileti paketteki OpenAjax meta verileri tarafından tanımlanır. Belirtilen biçim tanımlayıcı türü bağımlı [ \<loc >](../ide/loc-javascript.md) etiketi.  
  
  `value`  
  İsteğe bağlı. İşlev kodunun kendisi yerine IntelliSense tarafından kullanılmak üzere değerlendirilmelidir kodu belirtir. İçin `<field>`, bu öznitelik, oluşturucu işlevleri için desteklenir, ancak nesne sabit değeri için desteklenmiyor. Bu alan türü tanımlanmamış olduğunda tür bilgisini sağlaması özniteliktir. Örneğin, kullanabileceğiniz `value=’1’` alan türünün sayı olarak değerlendirilecek.  
  
  `description`  
  İsteğe bağlı. Alan için bir açıklama.  
  
## <a name="remarks"></a>Açıklamalar  
 `name` Özniteliği, bir oluşturucu işlevi bir alanda belgeleme durumlarda gereklidir. Diğer tüm senaryolar için tüm öznitelikler için `<field>` öğe isteğe bağlıdır.  
  
 Bir oluşturucu işlevi belgeleme zaman `<field>` öğesi alanı bildiriminden hemen önce görünmelidir. `name` Özniteliği, kaynak kodunda kullanılan alanın adıyla eşleşmelidir. Nesne üyeleri için `name` varsa, öznitelik atlanabilir `<field>` öğesi hemen önce nesne üyesi bildirimi görünür.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği kullanma işlemini gösterir `<field>` öğesi.  
  
```javascript  
// Use of <field> in an object definition.  
var Rectangle = {  
    /// <field type='Number'>The width of the rectangle.</field>  
    wid: 5,  
    /// <field type='Number'>The length of the rectangle.</field>  
    len: 0,  
    /// <field type='Number'>Returns the area of the rectangle.</field>  
    getArea: function (wid, len) {  
        return len * wid;  
    }  
}  
  
// Use of <field> in a constructor function.  
// The name attribute is required.  
function Engine() {  
    /// <field name='HorsePower' type='Number'>The engine's horsepower.</field>  
    this.HorsePower = 150;  
}  
```  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek nasıl kullanılacağını gösterir `<field>` öğeyle `static` özniteliğini `true`.  
  
```javascript  
function Engine() {  
    /// <field name='HorsePower' static='true' type='Number'>static field desc.</field>  
}  
  
Engine.HorsePower = 140;  
// IntelliSense on the field is available here.  
Engine.  
  
```  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek nasıl kullanılacağını gösterir `<field>` öğeyle `static` özniteliğini `false`.  
  
```javascript  
function Engine() {  
    /// <field name='HorsePower' static='false' type='Number'>Non-static field desc.</field>  
}  
  
Engine.HorsePower = 140;  
var eng = new Engine();  
// IntelliSense on the field is available here.  
eng.  
  
```  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek nasıl kullanılacağını gösterir `<field>` öğeyle `value` özniteliği.  
  
```javascript  
function calculator(a) {  
    /// <field name='f' value='1'/>  
}  
new calculator().f.   // Completion list for a Number.  
  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [XML Belge Açıklamaları](../ide/xml-documentation-comments-javascript.md)



