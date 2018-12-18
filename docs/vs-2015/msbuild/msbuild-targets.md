---
title: MSBuild hedefleri | Microsoft Docs
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
- MSBuild, targets
ms.assetid: 8060b4d2-e4a9-48cf-a437-852649ceb417
caps.latest.revision: 29
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: af666f40dec018e2dfde330cfc5727159b8b1dc7
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49925741"
---
# <a name="msbuild-targets"></a>MSBuild Hedefleri
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Hedefler görevleri belirli bir sıraya göre gruplandırabilir ve daha küçük birimlere factored için derleme işlemindeki izin. Örneğin, bir hedef başka bir proje için girişler derler ve bunları boş dizine yerleştirir, derleme için hazırlamak için çıkış dizinindeki tüm dosyaları silebilirsiniz. Görevler hakkında daha fazla bilgi için bkz. [görevleri](../msbuild/msbuild-tasks.md).  
  
## <a name="declaring-targets-in-the-project-file"></a>Hedefler proje dosyasında bildirme  
 Hedefleri, bir proje dosyasında bildirilir [hedef](../msbuild/target-element-msbuild.md) öğesi. Örneğin, aşağıdaki XML Csc görevi derleme öğe türüne sahip'ı çağırır ve yapı adında bir hedef oluşturur.  
  
```  
<Target Name="Construct">  
    <Csc Sources="@(Compile)" />  
</Target>  
```  
  
 MSBuild özellikleri gibi hedefleri tanımlanabilir. Örneğin,  
  
```  
<Target Name="AfterBuild" >  
    <Message Text="First occurrence" />  
</Target>  
<Target Name="AfterBuild" >  
    <Message Text="Second occurrence" />  
</Target>  
```  
  
 AfterBuild yürütülürse, yalnızca "ikinci oluşum" görüntüler.  
  
## <a name="target-build-order"></a>Hedef Derleme Sırası  
 Başka bir hedef üzerinde çıkışını bir hedef girişi bağlıysa hedefleri sıralanmış olmaları gerekmektedir. Hangi hedeflerin çalıştırma sırasını belirlemek için çeşitli yollar vardır.  
  
- Başlangıç hedefleri  
  
- Varsayılan hedefler  
  
- İlk hedef  
  
- Hedef bağımlılıklar  
  
- `BeforeTargets` ve `AfterTargets` (MSBuild 4.0)  
  
  Bir sonraki hedef yapı ona bağlı olsa bile bir hedef iki kez tek bir yapı sırasında hiçbir zaman çalışır. Bir hedef çalıştırıldıktan sonra derleme katkısı tamamlanmıştır.  
  
  Derleme sırası ayrıntılarını ve hedef hakkında daha fazla bilgi için bkz: [hedef derleme sırası](../msbuild/target-build-order.md).  
  
## <a name="target-batching"></a>Toplu hedef işlemede  
 Hedef öğe olabilir bir `Outputs` meta verileri form % (meta veriler) belirten özniteliği. Bu durumda, MSBuild gruplandırma veya "Bu meta veri değeri içeren öğelerinin toplu işleme" hedefi için her bir benzersiz meta veri değeri için bir kez çalışır. Örneğin,  
  
```  
<ItemGroup>  
    <Reference Include="System.Core">  
      <RequiredTargetFramework>3.5</RequiredTargetFramework>  
    </Reference>  
    <Reference Include="System.Xml.Linq">  
      <RequiredTargetFramework>3.5</RequiredTargetFramework>  
    </Reference>  
    <Reference Include="Microsoft.CSharp">  
      <RequiredTargetFramework>4.0</RequiredTargetFramework>  
    </Reference>  
</ItemGroup>  
<Target Name="AfterBuild"  
    Outputs="%(Reference.RequiredTargetFramework)">  
    <Message Text="Reference:  
      @(Reference->'%(RequiredTargetFramework)')" />  
</Target>  
```  
  
 Başvuru öğelerini RequiredTargetFramework meta verilerine göre toplu olarak işler. Hedefin çıktı şuna benzer:  
  
```  
Reference: 3.5;3.5  
Reference: 4.0  
```  
  
 Toplu hedef işlemede gerçek yapılarında nadiren kullanılır. Toplu Görev işlemede daha yaygındır. Daha fazla bilgi için [toplu işleme](../msbuild/msbuild-batching.md).  
  
## <a name="incremental-builds"></a>Artımlı Derlemeler  
 Artımlı derlemeleri en iyi duruma getirilir ve böylece hedefleri ile ilgili giriş dosyaları ile ilgili güncel Çıkış dosyalarını yürütülmez derlemeleri ' dir. Hedef öğe olabilir `Inputs` ve `Outputs` öznitelikler, hangi hedef öğeler belirten giriş olarak bekliyor ve hangi, çıktı olarak üretir öğeler.  
  
 Tüm çıkış öğeleri güncel olduğundan, MSBuild derleme hızını önemli ölçüde geliştiren hedef atlar. Bu, artımlı derleme hedefi olarak adlandırılır. Bazı dosyalar güncel olduğundan, yalnızca MSBuild hedefi güncel öğeler olmadan yürütür. Bu, kısmi bir artımlı derleme hedefi olarak adlandırılır. Daha fazla bilgi için [artımlı derlemeler](../msbuild/incremental-builds.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [MSBuild kavramları](../msbuild/msbuild-concepts.md)   
 [Nasıl Yapılır: Birden Çok Proje Dosyasında Aynı Hedefi Kullanma](../msbuild/how-to-use-the-same-target-in-multiple-project-files.md)



