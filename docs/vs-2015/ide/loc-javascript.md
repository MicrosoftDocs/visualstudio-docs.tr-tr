---
title: '&lt;loc&gt; (JavaScript) | Microsoft Docs'
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
- <loc> JavaScript XML tag
- loc JavaScript XML tag
ms.assetid: 0d3349b6-4bdd-418f-bc11-73665305baae
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 9314453b5e75e31f98d6989efa274278706bc5a4
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49244016"
---
# <a name="ltlocgt-javascript"></a>&lt;loc&gt; (JavaScript)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Yerelleştirilmiş IntelliSense bilgisi sağlayan sepet dosya türünü ve konumunu belirtir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
<loc filename="filename"  
    format="vsdoc|messagebundle" />  
```  
  
#### <a name="parameters"></a>Parametreler  
 `filename`  
 İsteğe bağlı. Bağımsız kültür için yerelleştirme bilgisi içeren sepet dosyasının kök adı. Visual Studio için yerelleştirme bilgisi aradığında, bu dosyanın bir kültüre özgü sürümünü bulmayı dener. Örneğin, varsa `filename` jquery.xml, Visual Studio arar (JA gibi) doğru kültüre özgü klasörü içeren .js dosyası ile aynı konumda olan `<loc>` öğesi. Kültüre özgü bir klasörde bulur, jquery.xml dosyası içinde var olup olmadığını denetler. Doğru dosya bulamıyorsanız, bunun yerine yönetilen kaynak konumu kuralları kullanır. İçin varsayılan değer `filename` geçerli dosyanın ancak .js yerine .xml uzantılı bir addır.  
  
 `format`  
 İsteğe bağlı. Yerelleştirme için kullanılan sepet dosya türü. Kullanma `messagebundle` açık Ajax meta verileri tarafından tanımlanan ileti paketlerin kullanımını belirlemek için. `messagebundle` Önerilen biçimidir. Ancak, bu biçim, Microsoft AJAX veya .winmd dosyalarında desteklenmiyor. Kullanım `vsdoc` Microsoft Ajax ve Windows çalışma zamanı tarafından kullanılan standart .NET Framework yerelleştirme biçimini belirtmek için. Bu öznitelik isteğe bağlıdır. `vsdoc` Varsayılan biçimidir.  
  
## <a name="remarks"></a>Açıklamalar  
 `<loc>` Aynı bölüme dosyasının üst öğesi görünmelidir `<reference>` öğesi. Kullanım kuralları için `<loc>` öğesi aynıdır `<reference>` öğesi. "Başvuru yönergeleri" bölümünde daha fazla bilgi için bkz. [JavaScript IntelliSense](../ide/javascript-intellisense.md).  
  
 Visual Studio, tek bir işleme `<loc>` her .js dosyası için öğesi. Birden çok `<loc>` öğeler varsa, tek bir `<loc>` öğe kullanılır. Hangi belirlemek için davranış `<loc>` kullanılacak öğesi tanımlı değil.  
  
 İleti paket biçimi, kullanırken `locid` XML belgeleri yorumları belirtmek için özniteliği `name` öznitelik değeri.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek nasıl kullanılacağını gösterir `<loc>` messagebundle biçimi olan öğe. Aşağıdaki XML messageFilename.xml adlı bir dosya ekleyin ve dosyayı açıklamasını belirtildiği gibi doğru kültüre özgü klasörüne yerleştirin `filename` parametresi.  
  
```  
<?xml version="1.0" encoding="utf-8" ?>  
<messagebundle>  
  <msg name="1">A class that represents a rectangle</msg>  
  <msg name="2">The height of a rectangle</msg>  
  <msg name="3">The width of a rectangle</msg>  
</messagebundle>  
  
```  
  
 Messagebundle örnek için projenizde bir JavaScript dosyasına aşağıdaki kodu ekleyin. `<loc>` Öğesi JavaScript dosyanın ilk satırı olarak görünmesi gerekir. Bu kod açıklamaları varsa yerelleştirilmiş açıklamaları tarafından değiştirilir.  
  
```javascript  
/// <loc filename="messageFilename.xml" format="messagebundle"/>  
  
function doSomething(a,b)   
{  
    /// <summary locid='1'>description</summary>  
    /// <param name='a' locid='2'>parameter a description</param>  
    /// <param name='b' locid='3'>parameter b description</param>  
}  
  
```  
  
 Aşağıdaki örnek VSDoc biçimini kullanır. Aşağıdaki XML scriptFilename.xml adlı bir dosya ekleyin ve dosyayı doğru kültüre özgü klasöre yerleştirin.  
  
```  
<?xml version="1.0" encoding="utf-8" ?>  
<doc>  
  <assembly>  
    <name>Lights</name>  
  </assembly>  
  <members>  
    <member name="M:illuminate">  
      <summary>Activates a light. </summary>  
      <param name='a'>The light to activate. </param>  
    </member>  
  </members>  
</doc>  
  
```  
  
 VSDoc örnek için projenizde bir JavaScript dosyasına aşağıdaki kodu ekleyin. Bu kod açıklamaları varsa yerelleştirilmiş açıklamaları tarafından değiştirilir.  
  
```javascript  
/// <loc filename="scriptFilename.xml" format="vsdoc" />  
  
function illuminate(a)   
{  
    /// <summary locid='M:illuminate'>description</summary>  
    /// <param name='a' type='Number'>parameter a description</param>  
}  
  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [XML Belge Açıklamaları](../ide/xml-documentation-comments-javascript.md)



