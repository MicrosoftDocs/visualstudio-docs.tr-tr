---
title: Öğe tanımları | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- msbuild, item definitions
ms.assetid: 8e3dc223-f9e5-4974-aa0e-5dc7967419cb
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0c267c8a0d76fdda08112e428c0fc7403daa1f30
ms.sourcegitcommit: 5b767247b3d819a99deb0dbce729a0562b9654ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/20/2018
ms.locfileid: "39178568"
---
# <a name="item-definitions"></a>Öğe tanımları
[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 2.0 kullanarak proje dosyalarındaki öğeleri statik bildirimi sağlayan [ItemGroup](../msbuild/itemgroup-element-msbuild.md) öğesi. Ancak, meta veriler için tüm öğeleri aynı olsa bile, yalnızca öğe düzeyinde meta veri eklenebilir. İtibariyle [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 3.5, adlı bir proje öğesi [Itemdefinitiongroup](../msbuild/itemdefinitiongroup-element-msbuild.md) bu sınırlamayı kaldırır. *Itemdefinitiongroup* adlandırılmış öğe türü içindeki tüm öğeler için varsayılan meta veri değerlerini ekleyen öğesi tanımları kümesini tanımlamanızı sağlar.  
  
 *Itemdefinitiongroup* öğesi görünür hemen sonra [proje](../msbuild/project-element-msbuild.md) proje dosyasının öğesi. Öğe tanımları aşağıdaki işlevleri sağlar:  
  
-   Öğeleri dışında bir hedef için genel varsayılan meta verileri tanımlayabilirsiniz. Diğer bir deyişle, aynı meta verileri belirtilen türdeki tüm öğeler için geçerlidir.  
  
-   Öğesi türleri, birden çok tanımına sahip olabilir. Ek meta veri belirtimleri türüne eklenir, son belirtimi önceliklidir. \(Meta veri özelliklerini izleyin aynı alma sırada izler.\)  
  
-   Meta veri olabilir eklenebilir. Örneğin, CDefines değerleri koşullu olarak ayarlanan özellikler bağlı olarak toplanır. Örneğin, `MT;STD_CALL;DEBUG;UNICODE`.  
  
-   Meta veri kaldırılabilir.  
  
-   Koşullar, eklenmesi, meta verileri denetlemek için kullanılabilir.  
  
## <a name="item-metadata-default-values"></a>Öğe meta verileri varsayılan değerler  
 Bir Itemdefinitiongroup içinde tanımlanan öğe meta verileri yalnızca bir varsayılan meta veri bildirimidir. Meta veri değerleri içeren bir ItemGroup kullanan bir öğeyi tanımlamak sürece meta veriler geçerli değildir.  
  
> [!NOTE]
>  Çoğu bu konudaki örnekler, Itemdefinitiongroup öğesi gösterilir ancak karşılık gelen ItemGroup tanımına açıklık için atlanır.  
  
 Bir ItemGroup içinde açıkça tanımlanmış meta verileri Itemdefinitiongroup meta verilerinde daha önceliklidir. Itemdefinitiongroup meta veriler, yalnızca bir ItemGroup meta verilerinde tanımsız için uygulanır. Örneğin:  
  
```xml  
<ItemDefinitionGroup>  
    <i>  
        <m>m1</m>  
        <n>n1</n>  
    </i>        
</ItemDefinitionGroup>  
<ItemGroup>  
    <i Include="a">  
        <o>o1</o>  
        <n>n2</n>  
    </i>  
</ItemGroup>  
```  
  
 "M" meta veri öğesi "i" tarafından açıkça tanımlanmadığından Bu örnekte, "m" varsayılan meta veri "i" öğesine uygulanır. Ancak, varsayılan meta veri "n", "n" meta veri öğesi "i" tarafından zaten tanımlı olduğundan, "i" öğesine uygulanmaz.  
  
> [!NOTE]
>  XML öğesi ve parametre adları olan çalışması\-hassas. Öğe meta verileri ve öğe\/özellik adları büyük/küçük harf olmayan\-hassas. Bu nedenle, yalnızca büyük küçük harfle farklı adlara sahip Itemdefinitiongroup öğeleri aynı ItemGroup değerlendirilmelidir.  
  
## <a name="value-sources"></a>Değer kaynakları  
 Bir Itemdefinitiongroup içinde tanımlanmış meta verileri değerlerini gibi birçok farklı kaynaklardan gelebilir:  
  
-   PropertyGroup özelliği  
  
-   Bir Itemdefinitiongroup öğesi  
  
-   Itemdefinitiongroup öğesi üzerinde öğesi dönüştürme  
  
-   ortam değişkeni  
  
-   Global özelliği (gelen *MSBuild.exe* komut satırı)  
  
-   Ayrılmış bir özellik  
  
-   Bir Itemdefinitiongroup bir öğe üzerinde iyi bilinen meta veriler  
  
-   CDATA bölümü \< \! \[CDATA\[burada bir şey ayrıştırılmaz\]\]\>  
  
> [!NOTE]
>  Itemdefinitiongroup öğeler ItemGroup öğelerini önce işlendiğinden bir ItemGroup öğesi meta verilerini bir Itemdefinitiongroup meta veri bildiriminde faydalı değil.  
  
## <a name="additive-and-multiple-definitions"></a>Eklenebilir ve birden çok tanım  
 Tanımları ekleme veya birden çok ItemDefinitionGroups kullandığınızda aşağıdakileri unutmayın:  
  
-   Ek meta veri belirtimine türüne eklenir.  
  
-   Son belirtimi önceliklidir.  
  
Birden çok ItemDefinitionGroups varsa, sonraki her belirtimi için önceki tanım meta verileri ekler. Örneğin:  
  
```xml  
<ItemDefinitionGroup>  
    <i>  
        <m>m1</m>  
        <n>n1</n>  
    </i>  
</ItemDefinitionGroup>  
<ItemDefinitionGroup>  
    <i>  
        <o>o1</o>  
    </i>  
</ItemDefinitionGroup>  
```  
  
Bu örnekte, "m" ve "n" için "o" meta veriler eklenir.  
  
Ayrıca, önceden tanımlanmış meta verileri değerlerini de eklenebilir. Örneğin:  
  
```xml  
<ItemDefinitionGroup>  
    <i>  
        <m>m1</m>  
    </i>  
</ItemDefinitionGroup>  
<ItemDefinitionGroup>  
    <i>  
        <m>%(m);m2</m>  
    </i>  
</ItemDefinitionGroup>    
```  
  
Bu örnekte, "m" meta veriler için önceden tanımlanmış değer \(m1\) yeni değere eklenen \(m2\), böylece son değeri "m1; m2".  
  
> [!NOTE]
>  Bu ayrıca aynı Itemdefinitiongroup ortaya çıkabilir.  
  
Önceden tanımlanmış meta verileri geçersiz kılma son belirtimi önceliklidir. Aşağıdaki örnekte, "m" meta veri son değerini "m1" "m1a için" gider.  
  
```xml  
<ItemDefinitionGroup>  
    <i>  
        <m>m1</m>  
    </i>  
</ItemDefinitionGroup>  
<ItemDefinitionGroup>  
    <i>  
        <m>m1a</m>  
    </i>  
</ItemDefinitionGroup>    
```  
  
## <a name="use-conditions-in-an-itemdefinitiongroup"></a>Bir Itemdefinitiongroup kullanım koşulları  
 Meta verilerin eklenmesi denetlemek için bir Itemdefinitiongroup koşulları kullanabilirsiniz. Örneğin:  
  
```xml  
<ItemDefinitionGroup Condition="'$(Configuration)'=='Debug'">  
    <i>  
        <m>m1</m>  
    </i>  
</ItemDefinitionGroup>  
```  
  
Bu durumda, yalnızca "Yapılandırma" özelliğinin değeri "Debug" ise "m1" öğesinde "i" varsayılan meta dahil edilir.  
  
> [!NOTE]
>  Yalnızca yerel meta veri başvurularının koşullarda desteklenir.  
  
Öğesi, tanım grubu içinde önceki bir Itemdefinitiongroup tanımlı meta veri başvurularını yereldir. Diğer bir deyişle, başvuruları kapsamını özel öğesi. Örneğin:  
  
```xml  
<ItemDefinitionGroup>  
    <test>  
        <yes>1</yes>  
    </test>  
    <i> 
        <m>m0</m>
        <m Condition="'%(test.yes)'=='1'">m1</m>  
    </i>  
</ItemDefinitionGroup>  
  
```  
  
Yukarıdaki örnekte, "i" "test" öğesi kendi koşulunda öğesi başvuruyor. Hiçbir zaman MSBuild bir Itemdefinitiongroup boş dize olarak başka bir öğenin meta verilerinde başvuru yorumlar bu koşul true olur. "M", "m0" Bu nedenle, ayarlanır
 
```xml 
  <ItemDefinitionGroup>
    <i>
      <m>m0</m>
      <yes>1</yes>
      <m Condition="'%(i.yes)'=='1'">m1</m>
    </i>
  </ItemDefinitionGroup>

```

Koşul başvuruları "i" öğesi olarak yukarıdaki örnekte, "m" "m1" değerine ayarlanır 's "yes" öğesi için meta veri değeri 
  
## <a name="override-and-delete-metadata"></a>Geçersiz kılma ve meta verilerini silme  
 Bir Itemdefinitiongroup öğesinde tanımlanan meta verileri, meta veri değeri için boş olarak ayarlayarak, bir sonraki Itemdefinitiongroup öğesi içinde kılınabilir. Bir meta veri öğesi boş bir değere ayarlayarak da verimli bir şekilde silebilirsiniz. Örneğin:  
  
```xml  
<ItemDefinitionGroup>  
    <i>  
        <m>m1</m>  
    </i>  
</ItemDefinitionGroup>  
<ItemDefinitionGroup>  
    <i>  
        <m></m>  
    </i>  
</ItemDefinitionGroup>  
```  
  
"İ" öğe meta verileri "m" hala içeriyor, ancak değeri artık boştur.  
  
## <a name="scope-of-metadata"></a>Meta verilerin kapsam  
 Tanımlanmış olan her yerde ItemDefinitionGroups tanımlı ve genel özellikleri genel kapsam vardır. Varsayılan meta veri tanımlarının bir Itemdefinitiongroup kendine başvuran olabilir. Örneğin, aşağıdaki basit bir meta veri başvurusu kullanır:  
  
```xml  
<ItemDefinitionGroup>  
    <i>  
        <m>m1</m>  
        <m>%(m);m2</m>  
    </i>  
</ItemDefinitionGroup>  
```  
  
Bir tam meta veri başvurusu de kullanılabilir:  
  
```xml  
<ItemDefinitionGroup>  
    <i>  
      <m>m1</m>  
      <m>%(i.m);m2</m>  
    </i>  
</ItemDefinitionGroup>  
```  
  
Ancak, aşağıdaki geçerli değil:  
  
```xml  
<ItemDefinitionGroup>  
    <i>  
        <m>m1</m>  
        <m>@(x)</m>  
    </i>  
</ItemDefinitionGroup>  
```  
  
Başlayarak [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 3.5, Itemgroups'un de olabilir kendine başvuran. Örneğin:  
  
```xml  
<ItemGroup>  
    <item Include="a">  
        <m>m1</m>  
        <m>%(m);m2</m>  
    </item>  
</ItemGroup>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Toplu işleme](../msbuild/msbuild-batching.md)
