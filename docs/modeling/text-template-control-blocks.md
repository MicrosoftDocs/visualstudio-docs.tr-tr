---
title: Metin Şablonu Denetim Blokları
description: Metin şablonu denetim blokları ve denetim bloklarının çıktıyı değiştirmek için metin şablonunuza kod yazmanıza nasıl izin vereceğinizi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, template code
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 11cc289f668a674707c584396998ea7abb9e7ea9
ms.sourcegitcommit: 4d394866b7817689411afee98e85da1653ec42f2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/12/2020
ms.locfileid: "97363594"
---
# <a name="text-template-control-blocks"></a>Metin Şablonu Denetim Blokları
Denetim blokları çıktıyı değiştirmek için metin şablonunuza kod yazmanızı sağlar. Sol köşeli ayraçlarına göre ayırt edilen üç tür denetim bloğu vardır:

- `<# Standard control blocks #>` deyimleri içerebilir.

- `<#= Expression control blocks #>` ifade içerebilir.

- `<#+ Class feature control blocks #>` Yöntemler, alanlar ve özellikler içerebilir.

## <a name="standard-control-block"></a>Standart denetim bloğu
 Standart denetim blokları deyimler içerir. Örneğin, aşağıdaki standart blok XML belgesindeki tüm özniteliklerin adlarını alır:

```
<#@ assembly name="System.Xml.dll" #>
<#@ import namespace="System.Xml" #>

<#
    List<string> allAttributes = new List<string>();
    XmlDocument xDoc = new XmlDocument();
    xDoc.Load(@"E:\CSharp\Overview.xml");
    XmlAttributeCollection attributes = xDoc.Attributes;
    if (attributes.Count > 0)
    {
       foreach (XmlAttribute attr in attributes)
       {
           allAtributes.Add(attr.Name);
       }
     }
#>
```

 Düz metni, veya gibi bir bileşik deyimin içine ekleyebilirsiniz `if` `for` . Örneğin, bu parça her döngü yinelemesinde bir çıkış satırı üretir:

```
<#
       foreach (XmlAttribute attr in attributes)
       {
#>
Found another one!
<#
           allAtributes.Add(attr.Name);
       }
#>
```

> [!WARNING]
> Her zaman {...} kullanın gömülü düz metin içeren iç içe geçmiş deyimlerini sınırlamak için. Aşağıdaki örnek düzgün çalışmayabilir:
>
> `<# if (ShouldPrint) #> Some text. -- WRONG`
>
> Bunun yerine, şu şekilde {parantezlerin} eklemeniz gerekir:

```

<#
 if (ShouldPrint)
 {   //  "{" REQUIRED
#>
Some text.
<#
 }
#>
```

## <a name="expression-control-block"></a>İfade denetim bloğu
 İfade denetim blokları, çıkış dosyasına yazılacak dizeler sağlayan kod için kullanılır. Örneğin, yukarıdaki örnekte, kod bloğunu aşağıdaki gibi değiştirerek, özniteliklerin adlarını çıkış dosyasına yazdırabilirsiniz:

```
<#
    XmlDocument xDoc = new XmlDocument();
    xDoc.Load(@"E:\CSharp\Overview.xml");
    XmlAttributeCollection attributes = xDoc.Attributes;
    if (attributes != null)
    {
       foreach (XmlAttribute attr in attributes)
       {
#><#= attr.Name #><#
       }
    }
#>
```

## <a name="class-feature-control-block"></a>Sınıf özelliği denetim bloğu
 Metin şablonunuza Yöntemler, özellikler, alanlar, hatta iç içe geçmiş sınıflar eklemek için sınıf özelliği denetim bloklarını kullanabilirsiniz. Sınıf özelliği bloklarının en yaygın kullanımı, metin şablonunun diğer bölümlerinde kod için yardımcı işlevler sağlamaktır. Örneğin, aşağıdaki sınıf özelliği bloğu, öznitelik adının ilk harfini büyük harfe dönüştürür (veya ad boşluk içeriyorsa, her sözcüğün ilk harfini büyük harfe dönüştürür):

```
<#@ import namespace="System.Globalization" #>
```

```
<#+
    private string FixAttributeName(string name)
    {
        return CultureInfo.CurrentCulture.TextInfo.ToTitleCase(name);
    }
#>
```

> [!NOTE]
> Sınıf özelliği denetim bloğunun, aynı şablon dosyasındaki standart denetim blokları ile izlenmemelidir. Ancak, bu kısıtlama kullanım yönergelerinin sonucu için de geçerlidir `<#@include#>` . Dahil edilen her dosyanın standart blokları ve ardından sınıf özelliği blokları olabilir.

 Bir sınıf özelliği denetim bloğu içinde metin ve ifade blokları gömerek çıkış üreten bir işlev oluşturabilirsiniz. Örneğin:

```
<#+
    private void OutputFixedAttributeName(string name)
    {
#>
 Attribute:  <#= CultureInfo.CurrentCulture.TextInfo.ToTitleCase(name) #>
<#+  // <<< Notice that this is also a class feature block.
    }
#>
```

 Bu işlevi standart bir bloktan veya başka bir sınıf özelliği bloğundan çağırabilirsiniz:

```
<# foreach (Attribute attribute in item.Attributes)
{
  OutputFixedAttributeName(attribute.Name);
}
#>
```

## <a name="how-to-use-control-blocks"></a>Denetim bloklarını kullanma
 Tek bir şablonda tüm standart ve ifade denetim bloklardaki tüm kod (dahil edilen şablonlarda bulunan tüm kodlar dahil) `TransformText()` oluşturulan kodun yöntemini oluşturmak için birleştirilir. (Yönergeyle diğer metin şablonlarını ekleme hakkında daha fazla bilgi için `include` bkz. [T4 metin şablonu yönergeleri](../modeling/t4-text-template-directives.md).)

 Denetim bloklarını kullanırken aşağıdaki noktaları göz önünde bulundurmanız gerekir:

- **Dildir.** Bir metin şablonunda C# veya Visual Basic kodunu kullanabilirsiniz. Varsayılan dil C# ' dir, ancak Visual Basic `language` yönerge parametresiyle belirtebilirsiniz `template` . (Yönergesi hakkında daha fazla bilgi için `template` bkz. [T4 metin şablonu yönergeleri](../modeling/t4-text-template-directives.md).)

     Denetim bloklarından kullandığınız dilin bir metin şablonunda oluşturduğunuz dilin veya biçimdeki herhangi bir şey yoktur. Visual Basic kodu kullanarak C# oluşturabilirsiniz veya tam tersi de geçerlidir.

     Belirli bir metin şablonunda, yönergeyle birlikte dahil ettiğiniz tüm metin şablonları dahil olmak üzere yalnızca bir dili kullanabilirsiniz `include` .

- **Yerel değişkenler.** Bir metin şablonundaki standart ve ifade denetim bloklarının tüm kodları tek bir yöntem olarak oluşturulduğundan, yerel değişkenlerin adlarıyla hiçbir çakışma olmadığından emin olmanız gerekir. Diğer metin şablonlarını dahil ediyorsanız, değişken adlarının dahil edilen tüm şablonlar genelinde benzersiz olduğundan emin olmanız gerekir. Bunu sağlamanın bir yolu, bildirildiği metin şablonunu tanımlayan her yerel değişken adına bir dize eklemektir.

     Ayrıca, özellikle birden çok metin şablonu dahil ettiğinizde, bunları bildirdiğinizde, yerel değişkenlerinizi hazır değerlere başlatmak iyi bir fikirdir.

- **Denetim blokları iç içe geçme.** Denetim blokları birbirlerinin içinde iç içe olamaz. Başka bir denetim bloğunu açmadan önce her zaman belirli bir denetim bloğunu sonlandırabilirsiniz. Örneğin, aşağıda standart denetim bloğunun bir parçası olarak bir ifade bloğunda bazı metinlerin nasıl yazdırılacağı gösterilmektedir.

    ```
    <#
    int x = 10;
    while (x-- > 0)
    {
    #>
    <#= x #>
    <# } #>
    ```

- **Yeniden.** Metin Şablonlarınızın kısa ve kolay anlaşılır olmasını sağlamak için, yeniden kullanılabilir kodu sınıf özellik bloklarından yardımcı işlevlere düzenleme veya Microsoft. VisualStudio. Textþablonı. TextTransformation sınıfından devralan kendi metin şablonu sınıfınızı oluşturarak yinelenen koddan kaçınmanız önemle tavsiye edilir.
