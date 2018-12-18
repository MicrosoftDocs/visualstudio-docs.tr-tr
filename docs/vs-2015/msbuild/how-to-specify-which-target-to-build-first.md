---
title: 'Nasıl yapılır: hangi için önce hedefin derleneceğini belirtme | Microsoft Docs'
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
- DefaultTargets attribute [MSBuild]
- MSBuild, specifying the defalut target
- MSBuild, DefaultTargets attribute
ms.assetid: a580ba5b-2919-42d2-ae38-1af991e0205a
caps.latest.revision: 20
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f4ea97ed3650e74a10bfc5e49657f0ed3dce60ba
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49840707"
---
# <a name="how-to-specify-which-target-to-build-first"></a>Nasıl Yapılır: Önce Hangi Hedefin Derleneceğini Belirtme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Bir veya daha fazla proje dosyasını içerebilir `Target` projenin nasıl oluşturulduğunu tanımlayan öğeler. [!INCLUDE[vstecmsbuildengine](../includes/vstecmsbuildengine-md.md)] ([!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)]) Altyapısı yapılar ilk proje dosyası içermedikçe bulur ve tüm bağımlılıkları, proje bir `DefaultTargets` öznitelik, bir `InitialTargets` özniteliği veya bir hedef belirtilen komut satırını kullanarak **/ Hedef** geçin.  
  
## <a name="using-the-initialtargets-attribute"></a>InitialTargets özniteliğini kullanma  
 `InitialTargets` Özniteliği `Project` öğesi belirtir önce çalıştırılacak bir hedef hedefleri komut satırında veya belirtilmese bile `DefaultTargets` özniteliği.  
  
#### <a name="to-specify-one-initial-target"></a>Bir ilk hedef belirtmek için  
  
- Varsayılan hedef belirtin `InitialTargets` özniteliği `Project` öğesi. Örneğin:  
  
   `<Project InitialTargets="Clean">`  
  
  Birden fazla ilk hedef belirtebilirsiniz `InitialTargets` sırayla hedefleri listeleyen ve her hedef ayırmak için noktalı virgül kullanarak özniteliği. Hedefleri listesinde sırayla çalıştırılır.  
  
#### <a name="to-specify-more-than-one-initial-target"></a>Birden fazla ilk hedef belirtmek için  
  
-   İçinde noktalı virgülle ayrılmış başlangıç hedefleri listesinde `InitialTargets` özniteliği `Project` öğesi. Örneğin, çalıştırılacak `Clean` hedef ve ardından `Compile` hedef, yazın:  
  
     `<Project InitialTargets="Clean;Compile">`  
  
## <a name="using-the-defaulttargets-attribute"></a>DefaultTargets özniteliği kullanma  
 `DefaultTargets` Özniteliği `Project` öğesi belirtir hangi hedef veya hedefleri yerleşik bir hedef komut satırında açıkça belirtilmediği takdirde. Hedefleri her ikisi de belirtilirse `InitialTargets` ve `DefaultTargets` öznitelikleri ve hiçbir hedef komut satırında belirtilen [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] belirtilen hedefleri çalıştıran `InitialTargets` öznitelik belirtilen hedef ve ardından `DefaultTargets` özniteliği.  
  
#### <a name="to-specify-one-default-target"></a>Bir varsayılan hedef belirtmek için  
  
- Varsayılan hedef belirtin `DefaultTargets` özniteliği `Project` öğesi. Örneğin:  
  
   `<Project DefaultTargets="Compile">`  
  
  Birden fazla varsayılan hedef belirtebilirsiniz `DefaultTargets` sırayla hedefleri listeleyen ve her hedef ayırmak için noktalı virgül kullanarak özniteliği. Hedefleri listesinde sırayla çalıştırılır.  
  
#### <a name="to-specify-more-than-one-default-target"></a>Birden fazla varsayılan hedef belirtmek için  
  
-   Varsayılan hedefler olarak noktalı virgülle ayrılmış liste `DefaultTargets` özniteliği `Project` öğesi. Örneğin, çalıştırılacak `Clean` hedef ve ardından `Compile` hedef, yazın:  
  
     `<Project DefaultTargets="Clean;Compile">`  
  
## <a name="using-the-target-switch"></a>/ Target anahtarı kullanma  
 Varsayılan hedef proje dosyasında tanımlı değil ya da varsayılan hedefleyen kullanmak istemiyorsanız, komut satırı anahtarı kullanabileceğiniz **/target** farklı bir hedef belirtmek için. Hedef veya hedefleri ile belirtilen **/target** tarafından belirtilen hedefleri yerine run anahtarı `DefaultTargets` özniteliği. Belirtilen hedef `InitialTargets` öznitelik her zaman ilk önce çalışır.  
  
#### <a name="to-use-a-target-other-than-the-default-target-first"></a>Varsayılan hedef dışında bir hedef ilk kullanmak için  
  
-   Hedef olarak ilk kullanarak hedef belirtin **/target** komut satırı anahtarı. Örneğin:  
  
     `msbuild file.proj /target:Clean`  
  
#### <a name="to-use-several-targets-other-than-the-default-targets-first"></a>Varsayılan hedefler dışında çeşitli hedeflere ilk kullanmak için  
  
-   Noktalı virgül veya kullanarak, virgülle ayrılmış hedefleri listesinde **/target** komut satırı anahtarı. Örneğin:  
  
     `msbuild <file name>.proj /t:Clean;Compile`  
  
## <a name="see-also"></a>Ayrıca Bkz.
  [MSBuild](msbuild.md)  
 [Hedefleri](../msbuild/msbuild-targets.md)   
 [Nasıl Yapılır: Derlemeyi Temizleme](../msbuild/how-to-clean-a-build.md)


