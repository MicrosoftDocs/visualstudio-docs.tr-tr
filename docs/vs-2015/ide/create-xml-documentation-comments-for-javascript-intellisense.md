---
title: JavaScript IntelliSense için XML belge açıklamaları oluştur | Microsoft Docs
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
- code comments, JavaScript IntelliSense
- XML documentation comments, JavaScript IntelliSense
- documentation comments [JavaScript]
- IntelliSense [JavaScript], XML documentation comments
ms.assetid: a27f5b50-9807-436f-a0cf-6f3137ecbaf0
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: d15144a2cee70e5f6bdc496bf2c09eb8fb95c85d
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49220564"
---
# <a name="create-xml-documentation-comments-for-javascript-intellisense"></a>JavaScript IntelliSense için XML belge açıklamaları oluşturma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

*XML belgeleri yorumları* olan JavaScript yorumları işlevleri, alanları ve değişkenler gibi kod öğeleri hakkında bilgi sağlamak için bir komut ekleyin. Betik işlevi başvurduğunuzda, Visual Studio'da bu metin açıklamaları IntelliSense ile görüntülenir.  
  
 Bu konuda, XML belgeleri yorumları kullanma hakkında temel bir öğretici sağlar. Diğer öğeleri gibi kullanma hakkında bilgi için [ \<var >](../ide/var-javascript.md) ve [ \<değer >](../ide/value-javascript.md)ve ek kod örnekleri için bkz: [XML belge açıklamaları ](../ide/xml-documentation-comments-javascript.md). Zaman uyumsuz bir geri çağırma için IntelliSense bilgisi gibi sağlama hakkında bilgi için bir `Promise`, bkz: [ \<döndürür >](../ide/returns-javascript.md).  
  
> [!NOTE]
>  XML belgeleri yorumlarına yalnızca dosyalardan, derlemelerden ve hizmetlerden ulaşılabilir.  
  
### <a name="to-create-xml-documentation-comments-for-a-javascript-function"></a>Bir JavaScript işlevi için XML belge açıklamaları oluşturma  
  
-   İşlevinde [ \<Özet >](../ide/summary-javascript.md), [ \<param >](../ide/param-javascript.md), ve [ \<döndürür >](../ide/returns-javascript.md) öğeleri ve her bir öğeyle koyun üç (/ / /) işaretleri eğik çizgi.  
  
    > [!NOTE]
    >  Her öğe, tek bir satırda olmalıdır.  
  
     Aşağıdaki örnek, bir JavaScript işlevi gösterir.  
  
    ```javascript  
    function getArea(radius)  
    {  
        /// <summary>Determines the area of a circle that has the specified radius parameter.</summary>  
        /// <param name="radius" type="Number">The radius of the circle.</param>  
        /// <returns type="Number">The area.</returns>  
        var areaVal;  
        areaVal = Math.PI * radius * radius;  
        return areaVal;  
    }  
    ```  
  
-   XML belge açıklamaları görüntülemek için adı ve açma parantezi aşağıdaki örnekte olduğu gibi XML belgeleri yorumları ile işaretlenmiş bir işlevin yazın:  
  
    ```javascript  
    var areaVal = getArea(  
    ```  
  
     XML belge açıklamaları içeren işlev ait sol ayraçtan yazdığınızda, Kod Düzenleyicisi IntelliSense XML belgeleri yorumları içinde tanımlanan bilgileri görüntülemek için kullanır.  
  
### <a name="to-create-xml-documentation-comments-for-a-javascript-field"></a>Bir JavaScript alan için XML belge açıklamaları oluşturma  
  
-   Bir oluşturucu işlevin veya nesnenin tanımında ekleme bir [ \<alan >](../ide/field-javascript.md) öğesi öncesinde üç eğik çizgi işareti (/ / /).  
  
     Aşağıdaki örnek kullanımını gösterir `<field>` öğesinde bir oluşturucu işlevi. Diğer örnekler için [ \<alan >](../ide/field-javascript.md).  
  
    ```javascript  
    function Engine() {  
        /// <field name='HorsePower' type='Number'>The engine's horsepower.</field>  
        this.HorsePower = 150;  
    }  
    ```  
  
-   XML belge açıklamaları görüntülemek için aşağıdaki örnekteki gibi XML belgeleri yorumları olarak işaretlenmiş işlev oluşturucu kullanılarak bir nesne oluşturun.  
  
    ```javascript  
    var eng = new Engine();  
    ```  
  
-   Sonraki satırda nesne ve alan için IntelliSense bilgilerini göstermek için bir nokta adını yazın.  
  
    ```javascript  
    eng.  
    ```  
  
### <a name="to-create-xml-documentation-comments-for-an-overloaded-function"></a>XML belge açıklamaları için aşırı yüklenmiş bir işlev oluşturmak için  
  
1.  İşlevinde, bir [ \<imza >](../ide/signature-javascript.md) her aşırı yükleme için öğesi. Bu öğeler, gibi diğer öğeleri ekleyin `<summary>`, `<param>`, ve `<returns>`, önceki üç eğik çizgi işareti (/ / /) her bir öğe.  
  
     Aşağıdaki örnek, aşırı yüklenmiş bir JavaScript işlevi gösterir. Bu örnekte, aşırı parametre türüne göre farklılık gösterir.  
  
    ```javascript  
    function calc(a) {  
        /// <signature>  
        /// <summary>Function summary 1.</summary>  
        /// <param name="a" type="Number">A number.</param>  
        /// <returns type="Number" />  
        /// </signature>  
        /// <signature>  
        /// <summary>Function summary 2.</summary>  
        /// <param name="a" type="String">A string.</param>  
        /// <returns type="Number" />  
        /// </signature>  
        return a;  
    }  
    ```  
  
2.  XML belge açıklamaları görüntülemek için adı ve aşağıdaki örnekte olduğu gibi XML belgeleri yorumları ile işaretlenmiş işlevi ait sol ayraçtan yazın:  
  
    ```javascript  
    calc(  
    ```  
  
### <a name="to-create-localized-intellisense"></a>Yerelleştirilmiş IntelliSense oluşturmak için  
  
1.  Belge açıklamaları OpenAjax MessageBundle biçime sahip bir XML dosyası oluşturun.  
  
    > [!IMPORTANT]
    >  MessageBundle önerilen bir biçimidir. Bu biçim, Microsoft AJAX veya .winmd dosyalarında desteklenmiyor. Alternatif kullanma hakkında bilgi için `VSDoc` biçimlendirmek için bkz: [ \<loc >](../ide/loc-javascript.md).  
  
     Aşağıdaki örnek yerelleştirilmiş IntelliSense bilgilerini içeren bir sepet dosyasında içerik gösterir. Bu, JA gibi kültüre özgü bir klasörde bulunan bir XML dosyasıdır. Klasör içeren .js dosyası ile aynı konumda olmalıdır `<loc>` öğesi. XML dosyasının dosya adı eşleşmelidir `filename` belirtilen parametre `<loc>` öğesi.  
  
    ```  
    <messagebundle>  
      <msg name="1">A class that represents a rectangle</msg>  
      <msg name="2">The length of the rectangle</msg>  
      <msg name="3">The height of the rectangle</msg>  
    </messagebundle>  
  
    ```  
  
2.  .Js dosyanıza aşağıdaki kodu ekleyin. `<loc>` Öğesi herhangi bir betik önce bildirilmelidir ve olarak aynı kullanım kurallara `<reference>` öğesi. Daha fazla bilgi için [JavaScript IntelliSense](../ide/javascript-intellisense.md) ve [ \<loc >](../ide/loc-javascript.md).  
  
    ```javascript  
    /// <loc filename="messageFilename.xml" format="messagebundle"/>  
  
    ```  
  
3.  XML belgeleri öğelerini ve varsayılan açıklamaları .js dosyanıza ekleyin. Ayarlama `locid` öznitelik değerleri karşılık gelen eşleşecek şekilde `name` öznitelik değerlerini sepet dosyasından. Varsa, varsayılan açıklamaları yerelleştirilmiş IntelliSense bilgisi değiştirilecek.  
  
    ```javascript  
    function add(a,b)   
    {  
        /// <summary locid='1'>description</summary>  
        /// <param name='a' locid='2'>parameter a description</param>  
        /// <param name='b' locid='3'>parameter b description</param>  
    }  
  
    ```  
  
4.  XML belge açıklamaları görüntülemek için adını ve parantez işlev için aşağıdaki örnekte olduğu gibi yazın:  
  
    ```javascript  
    add(  
    ```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [JavaScript IntelliSense](../ide/javascript-intellisense.md)   
 [XML belge açıklamaları](../ide/xml-documentation-comments-javascript.md)   
 [NIB: İzlenecek yol: ASP.NET, JavaScript IntelliSense](http://msdn.microsoft.com/en-us/4f6e0cc2-7f48-4dbf-abb0-7fb743a2d05b)



