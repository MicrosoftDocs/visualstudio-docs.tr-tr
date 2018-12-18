---
title: 'Nasıl yapılır: derlemede ortam değişkenlerini kullanma | Microsoft Docs'
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
- environment variables, referencing
- projects [.NET Framework], environment variables
- MSBuild, environment variables
ms.assetid: 7f9e4469-8865-4b59-aab3-3ff26bd36e77
caps.latest.revision: 21
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 463acc185a73b9a483bf74c98d4bde1cf0f42494
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49877510"
---
# <a name="how-to-use-environment-variables-in-a-build"></a>Nasıl Yapılır: Derlemede Ortam Değişkenlerini Kullanma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Projeler derlerken genellikle proje dosyası veya proje oluşturan dosyaların değil bilgileri kullanarak yapı seçeneklerini ayarlamak gereklidir. Bu bilgiler genellikle ortam değişkenleri olarak depolanır.  
  
## <a name="referencing-environment-variables"></a>Başvuruda bulunan ortam değişkenleri  
 Tüm ortam değişkenleri kullanılabilir [!INCLUDE[vstecmsbuildengine](../includes/vstecmsbuildengine-md.md)] ([!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)]) özellikleri olarak proje dosyası.  
  
> [!NOTE]
>  Proje dosyası açık bir ortam değişkeni ile aynı ada sahip bir özellik tanımı içeriyorsa, proje dosyasındaki özellik ortam değişkeninin değerini geçersiz kılar.  
  
#### <a name="to-use-an-environment-variable-in-an-msbuild-project"></a>İçinde bir MSBuild Projesi bir ortam değişkenini kullanmak için  
  
- Ortam değişkeni, proje dosyasında bildirilen bir değişken olduğu gibi başvuru. Örneğin, aşağıdaki kodu BIN_PATH ortam değişkeni başvuruyor:  
  
   `<FinalOutput>$(BIN_PATH)\MyAssembly.dll</FinalOutput>`  
  
  Kullanabileceğiniz bir `Condition` ortam değişkeni ayarlanmamış olması halinde bir özellik için varsayılan bir değer sağlamak için özniteliği.  
  
#### <a name="to-provide-a-default-value-for-a-property"></a>Bir özellik için varsayılan bir değer sağlamak için  
  
-   Kullanım bir `Condition` özellik değeri yalnızca şu durumlarda ayarlamak için bir özellik özniteliğini değere sahip değil. Örneğin, aşağıdaki ayarlar kod `ToolsPath` c:\tools yalnızca şu durumlarda özelliğini `ToolsPath` ortam değişkeninin ayarlı değil:  
  
     `<ToolsPath Condition="'$(TOOLSPATH)' == ''">c:\tools</ToolsPath>`  
  
    > [!NOTE]
    >  Özellik adlarını büyük küçük harfe duyarlı olmayan şekilde hem `$(ToolsPath)` ve `$(TOOLSPATH)` aynı özellik veya ortam değişkeni başvurusu.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki proje dosyası, dizin konumunu belirtmek için ortam değişkenlerini kullanır.  
  
```  
<Project DefaultTargets="FakeBuild">  
    <PropertyGroup>  
        <FinalOutput>$(BIN_PATH)\myassembly.dll</FinalOutput>  
        <ToolsPath Condition=" '$(ToolsPath)' == '' ">  
            C:\Tools  
        </ToolsPath>  
    </PropertyGroup>  
    <Target Name="FakeBuild">  
        <Message Text="Building $(FinalOutput) using the tools at $(ToolsPath)..."/>  
    </Target>  
</Project>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  

[MSBuild](msbuild.md)

[MSBuild Özellikleri](../msbuild/msbuild-properties1.md)

[Nasıl Yapılır: Farklı Seçeneklerle Aynı Kaynak Dosyaları Derleme](../msbuild/how-to-build-the-same-source-files-with-different-options.md)


