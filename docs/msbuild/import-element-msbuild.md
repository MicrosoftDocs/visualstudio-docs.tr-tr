---
title: İçeri aktarma öğesi (MSBuild) | Microsoft Docs
ms.custom: ''
ms.date: 03/13/2017
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Import
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- Import element [MSBuild]
- <Import> element [MSBuild]
ms.assetid: 3bfecaf1-69fd-4008-b651-c9dafd4389d9
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 7dd5b0aa6f0ed56aaa3315c03aeef6ed1b77ad62
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49839615"
---
# <a name="import-element-msbuild"></a>İçeri aktarma öğesi (MSBuild)
Bir proje dosyasının içeriğini başka bir proje dosyasına aktarır.  

 \<Proje >  
 \<İçeri aktarma >  

## <a name="syntax"></a>Sözdizimi  

```xml  
<Import Project="ProjectPath"  
    Condition="'String A'=='String B'" />  
```  

## <a name="attributes-and-elements"></a>Öznitelikler ve öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  

### <a name="attributes"></a>Öznitelikler  

|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`Project`|Gerekli öznitelik.<br /><br /> İçeri aktarmak için proje dosyasının yolu. Yol, joker karakterler içerebilir. Eşleşen dosyaları sıralanmış olarak içeri aktarılır. Bu özelliği kullanarak, yalnızca bir dizine kod dosyasına ekleyerek bir proje için kod ekleyebilirsiniz.|  
|`Condition`|İsteğe bağlı öznitelik.<br /><br /> Değerlendirilecek olan koşul. Daha fazla bilgi için [koşullar](../msbuild/msbuild-conditions.md).|  

### <a name="child-elements"></a>Alt öğeleri  
 Yok.  

### <a name="parent-elements"></a>Üst öğeler  

| Öğe | Açıklama |
| - | - |
| [Project](../msbuild/project-element-msbuild.md) | Gerekli kök öğesi bir [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] proje dosyası. |
| [Importgroup](../msbuild/importgroup-element.md) | Bir koleksiyonunu içeren `Import` öğeleri isteğe bağlı bir koşul altında gruplandırılır. |

## <a name="remarks"></a>Açıklamalar  
 Kullanarak `Import` öğesi, birçok proje dosyaları için ortak olan kod yeniden. Paylaşılan koda yaptığınız tüm güncelleştirmeleri almak için tüm projeleri yayılan çünkü kod bakımını kolaylaştırır.  

 Kural gereği, paylaşılan içeri aktarılan proje dosyaları olarak kaydedilen *.targets* dosyaları, ancak bunlar standart [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] proje dosyaları. [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] farklı dosya adı uzantısına sahip olan bir projeyi içeri aktarma öğesinden önlemeniz değil, ancak kullanmanızı öneririz *.targets* tutarlılık için uzantısı.  

 İçeri aktarılan projeleri göreli yollar içeri aktarma proje dizinine göreli olarak yorumlanır. Bu nedenle, farklı konumlardaki bazı proje dosyaları içinde bir proje dosyası aldıysanız, içeri aktarılan proje dosyasındaki göreli yollar içeri aktarılan her proje için farklı kabul edilecektir.  

 Tüm [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] ayrılmış, proje dosyasına, örneğin, ilgili Özellikler `MSBuildProjectDirectory` ve `MSBuildProjectFile`, başvurulan içeri aktarılan bir projedeki alma proje dosyasını temel alarak değerler atanır.  

 İçeri aktarılan proje yoksa bir `DefaultTargets` özniteliği, içeri aktarılan projeleri içeri aktarılır ve bulunan değerin ilk sırada inceledi `DefaultTargets` özniteliği kullanılır. Örneğin ProjectA ProjectB ve ProjectC (bu sırayla) alır ve ProjectB alır, ProjectD [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] ilk arar `DefaultTargets` ProjectA, ardından ProjectB, ardından ProjectD ve ProjectC son belirtilen.  

 Şema içeri aktarılan bir proje, standart bir proje için aynıdır. Ancak [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] olabilir bir içeri aktarılan proje genellikle kümesi veya hedefleri çalıştırın sırayı hangi özellikleri hakkında bilgi içermiyor içeri aktarılan bir proje oluşturmak kullanabilirsiniz, olası olmasıdır. İçeri aktarılan proje içine bu bilgileri sağlamak için aktarılır projeye bağlıdır.  

> [!NOTE]
>  Koşullu içeri aktarma deyimlerini komut satırı MSBuilds içinde çalışırken, bunlar ile Msbuild'de çalışmaz [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] tümleşik geliştirme ortamı (IDE). Proje yüklendiğinde ayarlanır yapılandırma ve platform değerleri kullanarak koşullu içeri aktarmalar değerlendirilir. Daha sonra proje dosyasında koşullar'ın bir yeniden değerlendirme gerektiren değişiklikler, örneğin, platform değiştirme [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] özellikleri ve öğeleri, ancak içeri aktarmalar koşulları reevaluates. İçeri aktarma, içeri aktarma koşullu değerlendirilmez çünkü atlanır.  
> 
>  Bu sorunu çözmek için koşullu içeri aktarmalar koymak *.targets* dosyaları veya put kodu koşullu gibi engelleyecek bir [Seç öğesi (MSBuild)](../msbuild/choose-element-msbuild.md) blok.  

## <a name="wildcards"></a>Joker karakterler  
 .NET Framework 4'te MSBuild proje öznitelik joker karakterler sağlar. Joker karakterler olduğunda, tüm eşleşme bulundu (için yeniden üretilebilirliğini) sıralanır ve sırasını açıkça ayarlanmış olarak daha sonra bu sırayla aktarıldıkları.  

 Bu, başka birisi bir dosyayı içeri aktarma dosyası için dosya adı açıkça eklemeye gerek kalmadan içe aktarabilmesi genişletilebilirlik noktası olanağı sunmak istiyorsanız kullanışlıdır. Bu amaçla *Microsoft.Common.Targets* dosyasının en üstüne aşağıdaki satırı içerir.  

```xml  
<Import Project="$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\$(MSBuildThisFile)\ImportBefore\*" Condition="'$(ImportByWildcardBeforeMicrosoftCommonTargets)' == 'true' and exists('$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\$(MSBuildThisFile)\ImportBefore')"/>  
```  

## <a name="example"></a>Örnek  
 Aşağıdaki örnek, çeşitli öğeleri ve özellikleri ve genel proje dosyasını içe aktaran bir proje gösterir.  

```xml  
<Project DefaultTargets="Compile"  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  

    <PropertyGroup>  
        <resourcefile>Strings.resx</resourcefile>  

        <compiledresources>  
            $(O)\$(MSBuildProjectName).Strings.resources  
        </compiledresources>  
    </PropertyGroup>  

    <ItemGroup>  
        <CSFile Include="*.cs" />  

        <Reference Include="System" />  
        <Reference Include="System.Data" />  
    </ItemGroup>  

    <Import Project="$(CommonLocation)\General.targets" />  
</Project>  
```  

## <a name="see-also"></a>Ayrıca bkz.  
 [Proje dosyası şema başvurusu](../msbuild/msbuild-project-file-schema-reference.md)   
 [Nasıl yapılır: birden çok proje dosyasında aynı hedefi kullanma](../msbuild/how-to-use-the-same-target-in-multiple-project-files.md)
