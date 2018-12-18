---
title: Hedef öğe (MSBuild) | Microsoft Docs
ms.custom: ''
ms.date: 03/13/2017
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Target
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- Target element [MSBuild]
- <Target> element [MSBuild]
ms.assetid: 350f6fc2-86b3-45f2-a31e-ece0e6bd4dca
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9085861418f11ed63f76a6493a6927c63530759b
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49918798"
---
# <a name="target-element-msbuild"></a>Hedef öğe (MSBuild)
İçin görevler kümesini içeren [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] ardışık olarak yürütmek için.  

 \<Proje >  
 \<Hedef >  

## <a name="syntax"></a>Sözdizimi  

```xml  
<Target Name="Target Name"  
        Inputs="Inputs"  
        Outputs="Outputs"  
        Returns="Returns"  
        KeepDuplicateOutputs="true/false"  
        BeforeTargets="Targets"  
        AfterTargets="Targets"  
        DependsOnTargets="DependentTarget"  
        Condition="'String A' == 'String B'">  
        Label="Label">  
    <Task>... </Task>  
    <PropertyGroup>... </PropertyGroup>  
    <ItemGroup>... </ItemGroup>  
    <OnError... />  
</Target>  
```  

## <a name="attributes-and-elements"></a>Öznitelikler ve öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  

### <a name="attributes"></a>Öznitelikler  

|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`Name`|Gerekli öznitelik.<br /><br /> Hedefin adı.|  
|`Condition`|İsteğe bağlı öznitelik.<br /><br /> Değerlendirilecek koşul. İçin değerlendirilen koşul yoksa `false`, hedef hedefi ya da ayarlanmış olan tüm aracıların gövdesini yürütmez `DependsOnTargets` özniteliği. Koşullar hakkında daha fazla bilgi için bkz. [koşullar](../msbuild/msbuild-conditions.md).|  
|`Inputs`|İsteğe bağlı öznitelik.<br /><br /> Bu hedefin giriş oluşturan dosyalar. Birden çok dosya noktalı virgül ile ayrılır. Damgaları Çıkıştaki dosyaların zaman damgaları Çıkıştaki dosyaların zaman ile karşılaştırıldığında `Outputs` belirlemek için olup olmadığını `Target` güncel. Daha fazla bilgi için [artımlı derlemeleri](../msbuild/incremental-builds.md), [nasıl yapılır: artımlı olarak derleme](../msbuild/how-to-build-incrementally.md), ve [dönüştüren](../msbuild/msbuild-transforms.md).|  
|`Outputs`|İsteğe bağlı öznitelik.<br /><br /> Form bu hedefe çıkarır dosyalar. Birden çok dosya noktalı virgül ile ayrılır. Damgaları Çıkıştaki dosyaların zaman damgaları Çıkıştaki dosyaların zaman ile karşılaştırıldığında `Inputs` belirlemek için olup olmadığını `Target` güncel. Daha fazla bilgi için [artımlı derlemeleri](../msbuild/incremental-builds.md), [nasıl yapılır: artımlı olarak derleme](../msbuild/how-to-build-incrementally.md), ve [dönüştüren](../msbuild/msbuild-transforms.md).|  
|`Returns`|İsteğe bağlı öznitelik.<br /><br /> Bu hedef, örneğin, MSBuild görevleri çağıran görevler için kullanılabilir hale getirilir öğeleri kümesi. Birden çok hedefe, noktalı virgül ile ayrılır. Hedef dosya yoksa `Returns` öznitelikler yerine bu amaç için kullanılan çıkış öznitelikleri.|  
|`KeepDuplicateOutputs`|İsteğe bağlı Boolean özniteliği.<br /><br /> Varsa `true`, birden fazla başvuru aynı öğe hedef olarak kaydedilir.  Varsayılan olarak, bu özniteliktir `false`.|  
|`BeforeTargets`|İsteğe bağlı öznitelik.<br /><br /> Hedef adları noktalı virgülle ayrılmış listesi.  Bu seçenek belirtildiğinde, bu hedefe belirtilen hedef veya hedefleri önce çalışması gerektiğini belirtir. Bu, doğrudan değiştirmeden hedefleri var olan bir dizi genişletme proje yazarı olanak tanır. Daha fazla bilgi için [hedef derleme sırası](../msbuild/target-build-order.md).|  
|`AfterTargets`|İsteğe bağlı öznitelik.<br /><br /> Hedef adları noktalı virgülle ayrılmış listesi. Bu seçenek belirtildiğinde, bu hedefe belirtilen hedef veya hedefleri sonra çalışması gerektiğini belirtir. Bu, doğrudan değiştirmeden hedefleri var olan bir dizi genişletme proje yazarı olanak tanır. Daha fazla bilgi için [hedef derleme sırası](../msbuild/target-build-order.md).|  
|`DependsOnTargets`|İsteğe bağlı öznitelik.<br /><br /> Bu hedef yürütülebilmesi yürütülmelidir hedefleri veya üst düzey bağımlılık analizi ortaya çıkabilir. Birden çok hedefe, noktalı virgül ile ayrılır.|  
|`Label`|İsteğe bağlı öznitelik.<br /><br /> Kimliğinizi belirlemek veya sistem ve kullanıcı öğelerini siparişi tanımlayıcısı.|  

### <a name="child-elements"></a>Alt öğeleri  

| Öğe | Açıklama |
| - | - |
| [Görev](../msbuild/task-element-msbuild.md) | Oluşturur ve yürütür örneği bir [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] görev. Bir hedef olarak sıfır veya daha fazla görev olabilir. |
| [PropertyGroup](../msbuild/propertygroup-element-msbuild.md) | Kullanıcı tanımlı bir dizi içeren `Property` öğeleri. .NET Framework 3.5 başlayan bir `Target` öğesi içerebilir `PropertyGroup` öğeleri. |
| [ItemGroup](../msbuild/itemgroup-element-msbuild.md) | Kullanıcı tanımlı bir dizi içeren `Item` öğeleri. .NET Framework 3.5 başlayan bir `Target` öğesi içerebilir `ItemGroup` öğeleri. Daha fazla bilgi için [öğeleri](../msbuild/msbuild-items.md). |
| [OnError](../msbuild/onerror-element-msbuild.md) | Neden olursa yürütülmek üzere bir veya daha fazla hedef `ContinueOnError` özniteliktir ErrorAndStop (veya `false`) için başarısız bir görev. Sıfır veya daha fazla olabilir `OnError` hedef öğelerinde. Varsa `OnError` öğeler, bunlar içerisinde son öğe olmalıdır `Target` öğesi.<br /><br /> Hakkında bilgi için `ContinueOnError` özniteliği için bkz: [görev öğesi (MSBuild)](../msbuild/task-element-msbuild.md). |

### <a name="parent-elements"></a>Üst öğeler  

| Öğe | Açıklama |
| - | - |
| [Project](../msbuild/project-element-msbuild.md) | Gerekli kök öğesi bir [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] proje dosyası. |

## <a name="remarks"></a>Açıklamalar  
 İlk hedef yürütmek için çalışma zamanında belirtilir. Hedefleri diğer hedefler üzerinde bağımlılıkları olabilir. Örneğin, dağıtım için hedef derleme hedefi bağlıdır. [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] Altyapısı bağımlılıkları göründükleri içinde sırayla yürütür `DependsOnTargets` soldan sağa doğru öznitelik. Daha fazla bilgi için [hedefleri](../msbuild/msbuild-targets.md).  

 Birden fazla hedef üzerinde bağımlılık sahip olsa bile, bir hedef yalnızca bir derleme sırasında bir kez yürütülür.  

 Bir hedef çünkü atladıysanız, `Condition` özniteliği değerlendirilen `false`, yapı içinde çağrılması durumunda hala yürütülebilecek ve kendi `Condition` özniteliğine hesaplar için `true` o zaman.  

 MSBuild 4 önce `Target` belirtilen tüm öğeler döndürülen `Outputs` özniteliği.  Bunu yapmak için derleme görevleri daha sonra bunları istenen durumlarda bu öğeleri kaydetmek MSBuild vardı. Çağıranlar gerektirecek çıkışları hedefleri olan belirtmek mümkün olduğundan tüm öğeleri tüm MSBuild birikmiş `Outputs` tüm çağrılan `Target`s. Bu sorunları çok sayıda olan derlemeler için ölçeklendirme adayı öğelerini çıktı.  

 Kullanıcı belirtiyorsa bir `Returns` herhangi `Target` öğesinde bir proje, ardından yalnızca `Target`sahip s bir `Returns` özniteliği öğelerden kaydedin.  

 A `Target` her ikisi de içerebilir bir `Outputs` özniteliği ve `Returns` özniteliği.  `Outputs` ile kullanılan `Inputs` hedefin güncel olup olmadığını belirlemek için. `Returns`, varsa, değerini geçersiz kılar `Outputs` hangi öğelerin arayanlara döndürülen belirlemek için.  Varsa `Returns` ardından yoksa `Outputs` daha önce açıklanan durumda arayanlara dışında kullanılabilir hale getirilir.  

 MSBuild 4 önce herhangi bir zamanda bir `Target` aynı öğede birden fazla başvuru dahil, `Outputs`, yinelenen öğeleri kaydedilmesi. Çok büyük sayıda çıktıları ve birçok proje bağımlılıkları olan oluşturur, bu çok miktarda bellek yinelenen öğeleri herhangi bir kullanımı olmadığı için boşa için neden olur. Zaman `KeepDuplicateOutputs` özniteliği `true`, bu yinelemeler kaydedilir.  

## <a name="example"></a>Örnek  
 Aşağıdaki kod örnekte gösterildiği bir `Target` yürüten öğesi `Csc` görev.  

```xml  
<Target Name="Compile" DependsOnTargets="Resources" Returns="$(TargetPath)">  
    <Csc Sources="@(CSFile)"  
          TargetType="library"  
          Resources="@(CompiledResources)"  
          EmitDebugInformation="$(includeDebugInformation)"  
          References="@(Reference)"  
          DebugType="$(debuggingType)" >  
        <Output TaskParameter="OutputAssembly"  
                  ItemName="FinalAssemblyName" />  
    </Csc>  
</Target>  
```  

## <a name="see-also"></a>Ayrıca bkz.  
 [Hedefleri](../msbuild/msbuild-targets.md)   
 [Proje dosyası şema başvurusu](../msbuild/msbuild-project-file-schema-reference.md)
