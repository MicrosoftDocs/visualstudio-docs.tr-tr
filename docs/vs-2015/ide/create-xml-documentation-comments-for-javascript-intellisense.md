---
title: JavaScript IntelliSense için XML belge açıklamaları oluşturma | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- code comments, JavaScript IntelliSense
- XML documentation comments, JavaScript IntelliSense
- documentation comments [JavaScript]
- IntelliSense [JavaScript], XML documentation comments
ms.assetid: a27f5b50-9807-436f-a0cf-6f3137ecbaf0
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 21fdc15b161b7d1cef30effe82e518a174bc9666
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72619541"
---
# <a name="create-xml-documentation-comments-for-javascript-intellisense"></a>JavaScript IntelliSense için XML belge açıklamaları oluşturma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

*XML belge açıklamaları* , işlevler, alanlar ve değişkenler gibi kod öğeleri hakkında bilgi sağlamak için bir betiğe eklediğiniz JavaScript açıklamalardır. Visual Studio 'da, komut dosyası işlevine başvurduğunuzda IntelliSense ile bu metin açıklamaları görüntülenir.

 Bu konu, XML belge açıklamalarını kullanmaya ilişkin temel bir öğretici sağlar. Ve gibi diğer öğeleri kullanma hakkında daha fazla bilgi için, [\<var>](../ide/var-javascript.md) [\<value>](../ide/value-javascript.md) bkz. [XML belge açıklamaları](../ide/xml-documentation-comments-javascript.md). Gibi zaman uyumsuz geri çağırma için IntelliSense bilgilerini sağlama hakkında bilgi için `Promise` , bkz [\<returns>](../ide/returns-javascript.md) ..

> [!NOTE]
> XML belgeleri yorumlarına yalnızca dosyalardan, derlemelerden ve hizmetlerden ulaşılabilir.

### <a name="to-create-xml-documentation-comments-for-a-javascript-function"></a>JavaScript işlevi için XML belge açıklamaları oluşturmak için

- İşlevinde,, [\<summary>](../ide/summary-javascript.md) [\<param>](../ide/param-javascript.md) ve [\<returns>](../ide/returns-javascript.md) öğelerini ekleyin ve her öğeden önce üç eğik çizgi işareti (///) ile önce gelmeli.

    > [!NOTE]
    > Her öğe tek bir satırda olmalıdır.

     Aşağıdaki örnekte bir JavaScript işlevi gösterilmektedir.

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

- XML belge açıklamalarını görüntülemek için, aşağıdaki örnekte olduğu gibi XML belge açıklamalarıyla işaretlenmiş bir işlevin adını ve açılış ayracını yazın:

    ```javascript
    var areaVal = getArea(
    ```

     XML belge açıklamalarını içeren işlevin açılış ayracını yazdığınızda, kod Düzenleyicisi, XML belge açıklamalarında tanımlanan bilgileri göstermek için IntelliSense kullanır.

### <a name="to-create-xml-documentation-comments-for-a-javascript-field"></a>JavaScript alanı için XML belge açıklamaları oluşturmak için

- Bir Oluşturucu işlevinde veya nesne tanımında, [\<field>](../ide/field-javascript.md) önünde üç eğik çizgi (///) işaretinden önce bir öğe ekleyin.

     Aşağıdaki örnek, `<field>` bir Oluşturucu işlevindeki öğesinin kullanımını gösterir. Daha fazla örnek için bkz [\<field>](../ide/field-javascript.md) ..

    ```javascript
    function Engine() {
        /// <field name='HorsePower' type='Number'>The engine's horsepower.</field>
        this.HorsePower = 150;
    }
    ```

- XML belge açıklamalarını görüntülemek için, aşağıdaki örnekte olduğu gibi XML belge açıklamalarıyla işaretlenen işlev oluşturucusunu kullanarak bir nesne oluşturun.

    ```javascript
    var eng = new Engine();
    ```

- Bir sonraki satırda, alan için IntelliSense bilgilerini göstermek üzere nesnenin adını ve bir dönemi yazın.

    ```javascript
    eng.
    ```

### <a name="to-create-xml-documentation-comments-for-an-overloaded-function"></a>Aşırı yüklenmiş bir işlev için XML belge açıklamaları oluşturmak için

1. İşlevinde, [\<signature>](../ide/signature-javascript.md) her aşırı yükleme için bir öğe ekleyin. Bu öğelerde,, ve gibi diğer öğeleri `<summary>` `<param>` `<returns>` üç eğik çizgi işareti (///) ile önce ekleyin.

     Aşağıdaki örnekte, aşırı yüklenmiş bir JavaScript işlevi gösterilmektedir. Bu örnekte, aşırı yüklemeler parametre türüne göre farklılık gösterir.

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

2. XML belge açıklamalarını görüntülemek için, aşağıdaki örnekte gösterildiği gibi, XML belge açıklamalarıyla işaretlenmiş işlevin adını ve açılış ayracını yazın:

    ```javascript
    calc(
    ```

### <a name="to-create-localized-intellisense"></a>Yerelleştirilmiş IntelliSense oluşturmak için

1. OpenAjax Messagedemeti biçiminde belge açıklamalarını içeren bir XML dosyası oluşturun.

    > [!IMPORTANT]
    > Messagedemeti önerilen biçimdir. Bu biçim Microsoft Ajax veya. winmd dosyalarında desteklenmez. Alternatif biçimi kullanma hakkında daha fazla bilgi için `VSDoc` bkz [\<loc>](../ide/loc-javascript.md) ..

     Aşağıdaki örnek, yerelleştirilmiş IntelliSense bilgilerini içeren bir sepet dosyasındaki içeriği gösterir. Bu, JA gibi kültüre özgü bir klasörde bulunan bir XML dosyasıdır. Klasör, öğesini içeren. js dosyası ile aynı konumda olmalıdır `<loc>` . XML dosyasının dosya adı `filename` , öğesinde belirtilen parametreyle aynı olmalıdır `<loc>` .

    ```
    <messagebundle>
      <msg name="1">A class that represents a rectangle</msg>
      <msg name="2">The length of the rectangle</msg>
      <msg name="3">The height of the rectangle</msg>
    </messagebundle>

    ```

2. . Js dosyanıza aşağıdaki kodu ekleyin. `<loc>`Öğe herhangi bir betikten önce bildirilmelidir ve öğesiyle aynı kullanım kurallarını takip etmelidir `<reference>` . Daha fazla bilgi için bkz. [JavaScript IntelliSense](../ide/javascript-intellisense.md) ve [\<loc>](../ide/loc-javascript.md) .

    ```javascript
    /// <loc filename="messageFilename.xml" format="messagebundle"/>

    ```

3. . Js dosyanızda XML belge öğelerini ve varsayılan açıklamaları ekleyin. `locid`Öznitelik değerlerini, `name` sepet dosyasındaki karşılık gelen öznitelik değerleriyle eşleşecek şekilde ayarlayın. Varsayılan açıklamalar, varsa yerelleştirilmiş IntelliSense bilgileri ile değiştirilirler.

    ```javascript
    function add(a,b)
    {
        /// <summary locid='1'>description</summary>
        /// <param name='a' locid='2'>parameter a description</param>
        /// <param name='b' locid='3'>parameter b description</param>
    }

    ```

4. XML belge açıklamalarını görüntülemek için, aşağıdaki örnekte olduğu gibi işlevin adını ve açılış ayracını yazın:

    ```javascript
    add(
    ```

## <a name="see-also"></a>Ayrıca Bkz.
 [JavaScript IntelliSense](../ide/javascript-intellisense.md) [XML belge açıklamaları](../ide/xml-documentation-comments-javascript.md) [nib: Izlenecek yol: ASP.NET içinde JavaScript IntelliSense](https://msdn.microsoft.com/4f6e0cc2-7f48-4dbf-abb0-7fb743a2d05b)
