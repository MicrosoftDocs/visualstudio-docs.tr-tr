---
title: Öğe işlevleri | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- msbuild, Item functions
ms.assetid: 5e6df3cc-2db8-4cbd-8fdd-3ffd03ac0876
caps.latest.revision: 32
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 687d740a379bd3b04bd47d0d2e3111bb71e7934d
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49207928"
---
# <a name="item-functions"></a>Öğe İşlevleri
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
MSBuild 4.0 ile başlayarak, görevleri ve hedefleri kod projesinde öğeleri hakkında bilgi almak için öğe işlevleri çağırabilir. Bu işlevler, başlangıç Distinct() öğeleri basitleştirin ve öğeler arasında döngü daha hızlıdır.  
  
## <a name="string-item-functions"></a>Dize öğe işlevleri  
 Herhangi bir öğeyi değer üzerinde çalışması için .NET Framework dize yöntemlerini ve özelliklerini kullanabilirsiniz. İçin <xref:System.String> yöntemleri, yöntem adını belirtin. İçin <xref:System.String> özellikleri "get_ sonra" özellik adı belirtin.  
  
 Birden çok dizeyi sahip öğeleri için her bir dizenin dize yöntemi veya özelliği çalıştırır.  
  
 Aşağıdaki örnek bu dize öğesi işlevlerinin nasıl kullanılacağı gösterilmektedir.  
  
```  
<ItemGroup>  
    <theItem Include="andromeda;tadpole;cartwheel" />  
</ItemGroup>  
  
<Target Name = "go">  
    <Message Text="IndexOf  @(theItem->IndexOf('r'))" />  
    <Message Text="Replace  @(theItem->Replace('tadpole', 'pinwheel'))" />  
    <Message Text="Length   @(theItem->get_Length())" />  
    <Message Text="Chars    @(theItem->get_Chars(2))" />  
</Target>  
  
  <!--  
  Output:  
    IndexOf  3;-1;2  
    Replace  andromeda;pinwheel;cartwheel  
    Length   9;7;9  
    Chars    d;d;r  
  -->  
```  
  
## <a name="intrinsic-item-functions"></a>İç öğe işlevleri  
 Aşağıdaki tabloda, öğeler için kullanılabilen iç işlevleri listeler.  
  
|İşlev|Örnek|Açıklama|  
|--------------|-------------|-----------------|  
|`Count`|`@(MyItem->Count())`|Öğelerin sayısını döndürür.|  
|`DirectoryName`|`@(MyItem->DirectoryName())`|Eşdeğerini döndürür `Path.DirectoryName` her öğe için.|  
|`Distinct`|`@(MyItem->Distinct())`|Farklı bir sahip öğeleri döndürür `Include` değerleri. Meta veri göz ardı edilir. Karşılaştırma büyük/küçük harfe duyarlıdır.|  
|`DistinctWithCase`|`@(MyItem->DistinctWithCase())`|Farklı bir sahip öğeleri döndürür `itemspec` değerleri. Meta veri göz ardı edilir. Karşılaştırma büyük/küçük harfe duyarlıdır.|  
|`Reverse`|`@(MyItem->Reverse())`|Öğeleri ters sırada döndürür.|  
|`AnyHaveMetadataValue`|`@(MyItem->AnyHaveMetadataValue("MetadataName", "MetadataValue"))`|Döndürür bir `boolean` herhangi bir öğeyi belirtilen meta veriler ada ve değere sahip olup olmadığını belirtmek için. Karşılaştırma büyük/küçük harfe duyarlıdır.|  
|`ClearMetadata`|`@(MyItem->ClearMetadata())`|Temizlenmiş meta verilerine öğeleri döndürür. Yalnızca `itemspec` korunur.|  
|`HasMetadata`|`@(MyItem->HasMetadataValue("MetadataName")`|Belirtilen meta veri adı sahip öğeleri döndürür. Karşılaştırma büyük/küçük harfe duyarlıdır.|  
|`Metadata`|`@(MyItem->Metadata("MetadataName"))`|Meta veri adı olan meta verileri değerlerini döndürür.|  
|`WithMetadataValue`|`@(MyItem->WithMetadataValue("MetadataName", "MetadataValue")`|Belirtilen meta veri adı ve değeri sahip öğeleri döndürür. Karşılaştırma büyük/küçük harfe duyarlıdır.|  
  
 Aşağıdaki örnekte, iç öğe işlevleri kullanma işlemini gösterir.  
  
```  
<ItemGroup>  
    <TheItem Include="first">  
        <Plant>geranium</Plant>  
    </TheItem>  
    <TheItem Include="second">  
        <Plant>algae</Plant>  
    </TheItem>  
    <TheItem Include="third">  
        <Plant>geranium</Plant>  
    </TheItem>  
</ItemGroup>  
  
<Target Name="go">  
    <Message Text="MetaData:    @(TheItem->Metadata('Plant'))" />  
    <Message Text="HasMetadata: @(theItem->HasMetadata('Plant'))" />  
    <Message Text="WithMetadataValue: @(TheItem->WithMetadataValue('Plant', 'geranium'))" />  
    <Message Text=" " />  
    <Message Text="Count:   @(theItem->Count())" />  
    <Message Text="Reverse: @(theItem->Reverse())" />  
</Target>  
  
  <!--   
  Output:  
    MetaData:    geranium;algae;geranium  
    HasMetadata: first;second;third  
    WithMetadataValue: first;third  
  
    Count:   3  
    Reverse: third;second;first  
  -->  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Öğeler](../msbuild/msbuild-items.md)



