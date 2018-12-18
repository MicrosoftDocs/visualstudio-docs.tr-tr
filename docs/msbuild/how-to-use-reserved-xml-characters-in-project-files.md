---
title: 'Nasıl yapılır: proje dosyalarında ayrılmış XML karakterlerini kullanma | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, using reserved XML characters
- MSBuild, reserved XML characters
ms.assetid: 1ae37275-96bf-4e6e-897b-6b048e5bbe93
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 647dba94840383410d06f6e5bf96ec3b0146c394
ms.sourcegitcommit: 8ee7efb70a1bfebcb6dd9855b926a4ff043ecf35
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/17/2018
ms.locfileid: "39077665"
---
# <a name="how-to-use-reserved-xml-characters-in-project-files"></a>Nasıl yapılır: proje dosyalarında ayrılmış XML karakterlerini kullanma
Proje dosyaları yazdığınızda, ayrılmış XML karakterleri, örneğin özellik değerlerini veya görev parametresi değerleri kullanmak gerekebilir. Ancak, proje dosyası ayrıştırıldığında, bazı ayrılmış karakterleri adlandırılmış varlık tarafından değiştirilmelidir.  
  
## <a name="use-reserved-characters"></a>Ayrılmış karakterleri kullanın  
 Aşağıdaki tabloda, ayrılmış XML karakterlerini karşılık gelen adlandırılmış varlık tarafından değiştirilmelidir ve böylece proje dosyası ayrıştırıldığında açıklanmaktadır.  
  
|Ayrılmış karakter|Adlandırılmış varlık|  
|------------------------|------------------|  
|\<|&amp;lt;|  
|>|&amp;gt;|  
|&|&amp;amp;|  
|"|&amp;quot;|  
|'|&amp;apos;|  
  
#### <a name="to-use-double-quotes-in-a-project-file"></a>Çift tırnak işareti bir proje dosyasında kullanmak için  
  
-   Adlandırılmış varlık, ilgili ile çift tırnak işaretleri yerine &amp;quot;. Örneğin, çift tırnak işaretlerini yerleştirmek için `EXEFile` öğe listesi, türü:  
  
    ```xml  
    <Message Text="The output file is &quot;@(EXEFile)&quot;."/>  
    ```  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneğinde proje dosyası tarafından çıkış iletisini dosya adında vurgulamak için çift tırnak işareti kullanılır.  
  
```xml  
<Project DefaultTargets="Compile"  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003" >  
    <!-- Set the application name as a property -->  
    <PropertyGroup>  
        <appname>"HelloWorldCS"</appname>  
    </PropertyGroup>  
    <!-- Specify the inputs -->  
    <ItemGroup>  
        <CSFile Include = "consolehwcs1.cs" />  
    </ItemGroup>  
    <Target Name = "Compile">  
        <!-- Run the Visual C# compilation using input  
        files of type CSFile -->  
        <Csc Sources = "@(CSFile)">  
            <!-- Set the OutputAssembly attribute of the CSC task  
            to the name of the executable file that is created -->  
            <Output  
                TaskParameter = "OutputAssembly"  
                ItemName = "EXEFile"/>  
        </Csc>  
        <!-- Log the file name of the output file -->  
        <Message Text="The output file is &quot;@(EXEFile)&quot;."/>  
    </Target>  
</Project>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [MSBuild başvurusu](../msbuild/msbuild-reference.md)    
 [MSBuild](../msbuild/msbuild.md)    
