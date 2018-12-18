---
title: Proje öğesi (MSBuild) | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Project
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- ToolsVersion attribute [MSBuild]
- <Project> element [MSBuild]
- Project element [MSBuild]
ms.assetid: d1cda56a-dbef-4109-9201-39e962e3f653
caps.latest.revision: 34
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 923cfa4a32362e28705e9f7fddfa3461979f84e4
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49820038"
---
# <a name="project-element-msbuild"></a>Proje Öğesi (MSBuild)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Gerekli kök öğesi bir [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] proje dosyası.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
<Project InitialTargets="TargetA;TargetB"  
         DefaultTargets="TargetC;TargetD"  
         TreatAsLocalProperty="PropertyA;PropertyB"  
         ToolsVersion=<version number>  
         xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <Choose>... </Choose>  
    <PropertyGroup>... </PropertyGroup>  
    <ItemGroup>... </ItemGroup>  
    <Target>... </Target>  
    <UsingTask.../>  
    <ProjectExtensions>... </ProjectExtensions>  
    <Import... />  
</Project>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|       Öznitelik        |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              Açıklama                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
|------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|    `DefaultTargets`    |                                                                                                                                                                                                                                                                                                 İsteğe bağlı öznitelik.<br /><br /> Varsayılan hedef veya hedefleri hiçbir hedef belirtilmemişse, derlemenin giriş noktası olacak. Noktalı virgülle (;) birden çok hedefi olan ayrılmış.<br /><br /> Varsayılan hedef ya da belirtilirse `DefaultTargets` özniteliği veya [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] komut satırı altyapısı yürütür ilk hedef sonra proje dosyasında [alma](../msbuild/import-element-msbuild.md) öğeler değerlendirilir.                                                                                                                                                                                                                                                                                                  |
|    `InitialTargets`    |                                                                                                                                                                                                                                                                                                                                                                                                                                             İsteğe bağlı öznitelik.<br /><br /> İlk hedef veya hedefleri önce belirtilen hedefleri çalıştırılacak `DefaultTargets` özniteliği veya komut satırında. Noktalı virgülle (;) birden çok hedefi olan ayrılmış.                                                                                                                                                                                                                                                                                                                                                                                                                                              |
|     `ToolsVersion`     |                                                                                                                                                                                                                                                                                                                                                                                                                                                                             İsteğe bağlı öznitelik.<br /><br /> MSBuild araç takımı sürümünü $(MSBuildBinPath) ve $(MSBuildToolsPath) için değerleri belirlemek için kullanır.                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| `TreatAsLocalProperty` | İsteğe bağlı öznitelik.<br /><br /> Genel olarak kabul olmaz özellik adları. Bu öznitelik, bir proje veya hedefler dosyasının ve sonraki tüm içe aktarmaları ayarlanan özellik değerlerini geçersiz kılmasını belirli komut satırı özelliklerini engeller. Noktalı virgülle (;) birden çok özelliklerdir ayrılmış.<br /><br /> Normalde, genel özellikler, proje veya hedefler dosyasında ayarlanan özellik değerlerini geçersiz kılar. Özelliği içinde listelenmişse `TreatAsLocalProperty` , genel özellik değerini değil geçersiz kılma değeri'nda bu dosya ve sonraki tüm içeri aktarmaları ayarlanan özellik değerleri. Daha fazla bilgi için [nasıl yapılır: farklı seçeneklerle aynı kaynak dosyaları derleme](../msbuild/how-to-build-the-same-source-files-with-different-options.md). **Not:** genel özellikleri kullanarak bir komut isteminde ayarlama **/Property** (veya **/p**) geçin. Ayrıca ayarlamak veya birden çok proje derleme alt projeler için genel özelliklerini kullanarak değiştirmek `Properties` MSBuild görevinin özniteliği. Daha fazla bilgi için [MSBuild görevi](../msbuild/msbuild-task.md). |
|        `Xmlns`         |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 Gerekli öznitelik.<br /><br /> `xmlns` Öznitelik değerini olmalıdır "<http://schemas.microsoft.com/developer/msbuild/2003>".                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[Seçin](../msbuild/choose-element-msbuild.md)|İsteğe bağlı öğe.<br /><br /> Bir grubu seçmek için alt öğeleri değerlendirir `ItemGroup` öğelerin ve/veya `PropertyGroup` değerlendirmek için öğeleri.|  
|[İçeri Aktar](../msbuild/import-element-msbuild.md)|İsteğe bağlı öğe.<br /><br /> Başka bir proje dosyasını içeri aktarmak bir proje dosyası sağlar. Sıfır veya daha fazla olabilir `Import` proje öğeleri.|  
|[ItemGroup](../msbuild/itemgroup-element-msbuild.md)|İsteğe bağlı öğe.<br /><br /> Bireysel öğeleri için gruplandırma öğesi. Öğeleri kullanılarak belirtilir [öğesi](../msbuild/item-element-msbuild.md) öğesi. Sıfır veya daha fazla olabilir `ItemGroup` proje öğeleri.|  
|[ProjectExtensions](../msbuild/projectextensions-element-msbuild.md)|İsteğe bağlı öğe.<br /><br /> Kalıcı olmayan bir şekilde sağlar[!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] bilgileri bir [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] proje dosyası. Sıfır veya bir olabilir `ProjectExtensions` proje öğeleri.|  
|[PropertyGroup](../msbuild/propertygroup-element-msbuild.md)|İsteğe bağlı öğe.<br /><br /> Tek tek özellikler için gruplandırma öğesi. Özellikleri kullanarak belirtilen [özelliği](../msbuild/property-element-msbuild.md) öğesi. Sıfır veya daha fazla olabilir `PropertyGroup` proje öğeleri.|  
|[Hedef](../msbuild/target-element-msbuild.md)|İsteğe bağlı öğe.<br /><br /> İçin görevler kümesini içeren [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] ardışık olarak yürütmek için. Görevleri kullanarak belirtilen [görev](../msbuild/task-element-msbuild.md) öğesi. Sıfır veya daha fazla olabilir `Target` proje öğeleri.|  
|[UsingTask](../msbuild/usingtask-element-msbuild.md)|İsteğe bağlı öğe.<br /><br /> Görevleri kaydetmek için bir yol sağlar [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)]. Sıfır veya daha fazla olabilir `UsingTask` proje öğeleri.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
 Yok.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Nasıl yapılır: hangi için önce hedefin derleneceğini belirtme](../msbuild/how-to-specify-which-target-to-build-first.md)   
 [Komut satırı başvurusu](../msbuild/msbuild-command-line-reference.md)   
 [Proje dosyası şema başvurusu](../msbuild/msbuild-project-file-schema-reference.md)   
 [MSBuild](msbuild.md)


