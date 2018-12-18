---
title: '&lt;İmza&gt; (JavaScript) | Microsoft Docs'
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
- <signature> JavaScript XML tag
- signature JavaScript XML tag
ms.assetid: 319138e7-cfbe-4b37-9643-2ddb7f9c63d4
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 0b3278087545a4d49d5f4f2f0d3f6942c4ec6d9a
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49293013"
---
# <a name="ltsignaturegt-javascript"></a>&lt;İmza&gt; (JavaScript)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bir işlev veya yöntem aşırı yüklenmiş işlevler için belgeleri sağlamak için ilgili öğeleri kümesini gruplar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
<signature externalid="id" externalFile="filename"  
    helpKeyword="keyword" locid="descriptionID">  
</signature>   
```  
  
#### <a name="parameters"></a>Parametreler  
 `externalid`  
 İsteğe bağlı. Varsa `format` özniteliğini [ \<loc >](../ide/loc-javascript.md) öğesi `vsdoc`, imza ile ilişkili XML kodunu bulmak için kullanılan bir üye bu öznitelik belirtir. Farklı `locid` özniteliği, bu öznitelik belirtir bu Koduna sahip üye içindeki tüm öğelerin yüklenmesi gerekir. XML kodu mevcut herhangi bir ilişkili açıklama bilgi de imzasında belirtilen öğeleri ile birleştirilir. Bu ek öğeler gibi belirtmenize olanak tanıyan `<capability>`, kaynak dosyada belirtmeden sepet dosyasında. `externalid` İsteğe bağlı bir özniteliktir.  
  
 `externalFile`  
 İsteğe bağlı. Bulmak dosya adını belirtir `externalid`. Bu öznitelik yoksa göz ardı edilir `externalid` mevcuttur. Bu isteğe bağlı bir özniteliğidir. Varsayılan değer, ancak .js yerine .xml dosya uzantısı ile geçerli dosyanın adıdır. Varsayılan olarak, yönetilen kaynak arama kurallarını yerelleştirme için dosyayı bulmak için kullanılır.  
  
 `helpKeyword`  
 İsteğe bağlı. F1 Yardım anahtar sözcüğü.  
  
 `locid`  
 İsteğe bağlı. Yerelleştirme alanı hakkında bilgi için tanımlayıcı. Tanımlayıcıdır ya da bir üye kimliği veya karşılık gelen `name` öznitelik değeri bir ileti paketteki OpenAjax meta verileri tarafından tanımlanır. Belirtilen biçim tanımlayıcı türü bağımlı [ \<loc >](../ide/loc-javascript.md) etiketi.  
  
## <a name="remarks"></a>Açıklamalar  
 Bir `<signature>` öğesini her .js dosyası veya bir işlev açıklama aşırı `<signature>` öğesi için belirtilen her dış üye kimliği.  
  
 `<signature>` Öğesi, herhangi bir deyim önce işlev gövdesindeki yerleştirilmelidir. Kullanırken [ \<Özet >](../ide/summary-javascript.md), [ \<param >](../ide/param-javascript.md), veya [ \<döndürür >](../ide/returns-javascript.md) öğelerle `<signature>` öğesi içindeki diğer öğeler yerleştirmeniz `<signature>` blok.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği kullanma işlemini gösterir `<signature>` öğesi.  
  
```javascript  
// Use of <signature> with externalid.  
// Requires use of the <loc> tag to identify the external functions.  
function illuminate(light) {  
    /// <signature externalid='M:Windows.Devices.Light.Illuminate()' />  
    /// <signature externalid='M:Windows.Devices.Light.Illuminate(System.Int32)'>  
    ///   <param name='light' type='Number' />  
    /// </signature>  
}  
  
// Use of <signature> for overloads implemented in JavaScript.  
function add(a, b) {  
    /// <signature>  
    /// <summary>function summary 1</summary>  
    /// <param name="a" type="Number">The first number</param>  
    /// <param name="b" type="Number">The second number</param>  
    /// <returns type="Number" />  
    /// </signature>  
    /// <signature>  
    /// <summary>function summary 2 – differ by number of params</summary>  
    /// <param name="a" type="Number">Only 1 parameter</param>  
    /// <returns type="Number" />  
    /// </signature>  
    /// <signature>  
    /// <summary>function summary 3 – differ by parameter type</summary>  
    /// <param name="a" type="Number">Number parameter</param>  
    /// <param name="b" type="String">String parameter</param>  
    /// <returns type="Number" />  
    /// </signature>  
    /// <signature>  
    /// <summary>function summary 4 – differ by return type</summary>  
    /// <param name="a" type="Number">The first number</param>  
    /// <param name="b" type="Number">The second number</param>  
    /// <returns type="String" />  
    /// </signature>  
  
    return a + b;  
}  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [XML Belge Açıklamaları](../ide/xml-documentation-comments-javascript.md)



