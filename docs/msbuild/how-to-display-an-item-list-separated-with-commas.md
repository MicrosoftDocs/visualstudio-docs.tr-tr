---
title: 'Nasıl yapılır: virgülle ayrılmış bir öğe listesini görüntüleme | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, separating items with semicolons
- MSBuild, formatting item collections
ms.assetid: 3cae844c-7c6d-4144-82dc-efad10ba458f
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f1507a297c1baf7f410bde1c6d32e48b43a9cdc2
ms.sourcegitcommit: 71218ffc33da325cc1b886f69ff2ca50d44f5f33
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/09/2018
ms.locfileid: "48880241"
---
# <a name="how-to-display-an-item-list-separated-with-commas"></a>Nasıl yapılır: virgülle ayrılmış bir öğe listesini görüntüleme
Öğesi ile çalışırken listeleri [!INCLUDE[vstecmsbuildengine](../msbuild/includes/vstecmsbuildengine_md.md)] ([!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]), bu öğe listeleri içeriğini okumak kolay bir şekilde görüntülemek bazen kullanışlıdır. Veya özel ayırıcı dize ile ayrılmış olan öğelerin listesini alan bir görev olabilir. Her iki durumda, bir öğe listesi için bir ayırıcı dize belirtebilirsiniz.  
  
## <a name="separate-items-in-a-list-with-commas"></a>Virgül içeren bir liste içindeki ayrı öğeleri  
 Varsayılan olarak, [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] listedeki öğeleri ayırmak için noktalı virgül kullanır. Örneğin, bir `Message` şu değere sahip öğe:  
  
 `<Message Text="This is my list of TXT files: @(TXTFile)"/>`  
  
 Zaman `@(TXTFile)` öğe listesi öğeleri içeren *App1.txt*, *App2.txt*, ve *App3.txt*, ileti:  
  
 `This is my list of TXT files: App1.txt;App2.txt;App3.txt`  
  
 Varsayılan davranışı değiştirmek isterseniz, kendi ayırıcı belirtebilirsiniz. Bir öğe liste ayırıcı belirtmek için sözdizimi aşağıdaki gibidir:  
  
 `@(ItemListName, '<separator>')`  
  
 Ayırıcı, tek bir karakter veya bir dize olabilir ve tek tırnak içine alınmalıdır.  
  
#### <a name="to-insert-a-comma-and-a-space-between-items"></a>Bir virgül ve öğeleri arasına boşluk eklemek için  
  
-   Aşağıdakine benzer bir öğe gösterimini kullanın:  
  
     `@(TXTFile, ', ')`  
  
## <a name="example"></a>Örnek  
 Bu örnekte, [Exec](../msbuild/exec-task.md) görev çalıştırır dosyasında belirtilen metin dizeleri bulmak için findstr aracı *Phrases.txt*. Findstr komut içinde değişmez değer dizeleri tarafından belirtilen **-c:** geçiş, bunu öğesi ayırıcısı `-c:` bulunan öğeler arasındaki eklenen `@(Phrase)` öğe listesi.  
  
 Bu örnekte, eşdeğer komut satırı komutudur:  
  
 `findstr /i /c:hello /c:world /c:msbuild phrases.txt`  
  
```xml  
<Project DefaultTargets = "Find"  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003" >  
  
    <ItemGroup>  
        <Phrase Include="hello"/>  
        <Phrase Include="world"/>  
        <Phrase Include="msbuild"/>  
    </ItemGroup>  
  
    <Target Name = "Find">  
        <!-- Find some strings in a file -->  
        <Exec Command="findstr /i /c:@(Phrase, ' /c:') phrases.txt"/>  
    </Target>  
</Project>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [MSBuild başvurusu](../msbuild/msbuild-reference.md)   
 [Öğeler](../msbuild/msbuild-items.md)