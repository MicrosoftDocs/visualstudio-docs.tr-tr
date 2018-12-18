---
title: İçeri aktarma öğesi (MSBuild) | Microsoft Docs
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
caps.latest.revision: 32
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 575fd2e83abd309b67e6e1684fd38b8d5c9953ac
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49248475"
---
# <a name="import-element-msbuild"></a>İçeri Aktarma Öğesi (MSBuild)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Bir proje dosyasının içeriğini başka bir proje dosyasına aktarır.  
  
 \<Proje >  
 \<İçeri aktarma >  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
<Import Project="ProjectPath"  
    Condition="'String A'=='String B'" />  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`Project`|Gerekli öznitelik.<br /><br /> İçeri aktarmak için proje dosyasının yolu. Yol, joker karakterler içerebilir. Eşleşen dosyaları sıralanmış olarak içeri aktarılır. Bu özelliği kullanarak, yalnızca bir dizine kod dosyasına ekleyerek bir proje için kod ekleyebilirsiniz.|  
|`Condition`|İsteğe bağlı öznitelik.<br /><br /> Değerlendirilecek olan koşul. Daha fazla bilgi için [koşullar](../msbuild/msbuild-conditions.md).|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[Project](../msbuild/project-element-msbuild.md)|Gerekli kök öğesi bir [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] proje dosyası.|  
|[Importgroup](../msbuild/importgroup-element.md)|Bir koleksiyonunu içeren `Import` öğeleri isteğe bağlı bir koşul altında gruplandırılır.|  
  
## <a name="remarks"></a>Açıklamalar  
 Kullanarak `Import` öğesi, birçok proje dosyaları için ortak olan kod yeniden. Paylaşılan koda yaptığınız tüm güncelleştirmeleri almak için tüm projeleri yayılan çünkü kod bakımını kolaylaştırır.  
  
 Kural gereği, içeri aktarılan paylaşılan proje dosyaları .targets dosyaları kaydedilir, ancak bunlar standart [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] proje dosyaları. [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] farklı dosya adı uzantısına sahip olan bir projeyi içeri aktarma öğesinden önlemeniz değil, ancak tutarlılık açısından .targets uzantıyı kullanmanızı öneririz.  
  
 İçeri aktarılan projeleri göreli yollar içeri aktarma proje dizinine göreli olarak yorumlanır. Bu nedenle, farklı konumlardaki bazı proje dosyaları içinde bir proje dosyası aldıysanız, içeri aktarılan proje dosyasındaki göreli yollar içeri aktarılan her proje için farklı kabul edilecektir.  
  
 Tüm [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] ayrılmış, proje dosyasına, örneğin, ilgili Özellikler `MSBuildProjectDirectory` ve `MSBuildProjectFile`, başvurulan içeri aktarılan bir projedeki alma proje dosyasını temel alarak değerler atanır.  
  
 İçeri aktarılan proje yoksa bir `DefaultTargets` özniteliği, içeri aktarılan projeleri içeri aktarılır ve bulunan değerin ilk sırada inceledi `DefaultTargets` özniteliği kullanılır. Örneğin ProjectA ProjectB ve ProjectC (bu sırayla) alır ve ProjectB alır, ProjectD [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] ilk arar `DefaultTargets` ProjectA, ardından ProjectB, ardından ProjectD ve ProjectC son belirtilen.  
  
 Şema içeri aktarılan bir proje, standart bir proje için aynıdır. Ancak [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] olabilir bir içeri aktarılan proje genellikle kümesi veya hedefleri çalıştırın sırayı hangi özellikleri hakkında bilgi içermiyor içeri aktarılan bir proje oluşturmak kullanabilirsiniz, olası olmasıdır. İçeri aktarılan proje içine bu bilgileri sağlamak için aktarılır projeye bağlıdır.  
  
> [!NOTE]
>  Koşullu içeri aktarma deyimlerini komut satırı MSBuilds içinde çalışırken, bunlar ile Msbuild'de çalışmaz [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] tümleşik geliştirme ortamı (IDE). Proje yüklendiğinde ayarlanır yapılandırma ve platform değerleri kullanarak koşullu içeri aktarmalar değerlendirilir. Daha sonra proje dosyasında koşullar'ın bir yeniden değerlendirme gerektiren değişiklikler, örneğin, platform değiştirme [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] özellikleri ve öğeleri, ancak içeri aktarmalar koşulları reevaluates. İçeri aktarma, içeri aktarma koşullu değerlendirilmez çünkü atlanır.  
>   
>  Bu sorunu çözmek için koşullu içeri aktarmalar .targets dosyalarında put veya kodu gibi bir koşullu blok içinde koyun bir [Seç öğesi (MSBuild)](../msbuild/choose-element-msbuild.md) blok.  
  
## <a name="wildcards"></a>Joker karakterler  
 .NET Framework 4'te MSBuild proje öznitelik joker karakterler sağlar. Joker karakterler olduğunda, tüm eşleşme bulundu (için yeniden üretilebilirliğini) sıralanır ve sırasını açıkça ayarlanmış olarak daha sonra bu sırayla aktarıldıkları.  
  
 Bu, başka birisi bir dosyayı içeri aktarma dosyası için dosya adı açıkça eklemeye gerek kalmadan içe aktarabilmesi genişletilebilirlik noktası olanağı sunmak istiyorsanız kullanışlıdır. Bu amaç için Microsoft.common.targets'ı dosyasının en üstüne aşağıdaki satırı içerir.  
  
```  
<Import Project="$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\$(MSBuildThisFile)\ImportBefore\*" Condition="'$(ImportByWildcardBeforeMicrosoftCommonTargets)' == 'true' and exists('$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\$(MSBuildThisFile)\ImportBefore')"/>  
```  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, çeşitli öğeleri ve özellikleri ve genel proje dosyasını içe aktaran bir proje gösterir.  
  
```  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Proje dosyası şema başvurusu](../msbuild/msbuild-project-file-schema-reference.md)   
 [Nasıl Yapılır: Birden Çok Proje Dosyasında Aynı Hedefi Kullanma](../msbuild/how-to-use-the-same-target-in-multiple-project-files.md)



