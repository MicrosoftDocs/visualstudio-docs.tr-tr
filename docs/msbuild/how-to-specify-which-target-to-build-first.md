---
title: 'Nasıl yapılır: önce hangi hedefin oluşturulacağını belirtme | Microsoft Docs'
description: İlk hedefleri veya varsayılan hedefleri MSBuild proje dosyalarında derlemek için belirleme hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- DefaultTargets attribute [MSBuild]
- MSBuild, specifying the defalut target
- MSBuild, DefaultTargets attribute
ms.assetid: a580ba5b-2919-42d2-ae38-1af991e0205a
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: f41c9fec5b5ce9b6e4716c83edf9cd9f43e0eb94
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99914207"
---
# <a name="how-to-specify-which-target-to-build-first"></a>Nasıl yapılır: önce hangi hedefin oluşturulacağını belirtme

Proje dosyası, projenin nasıl oluşturulduğunu tanımlayan bir veya daha fazla `Target` öğe içerebilir. Microsoft Build Engine (MSBuild) altyapısı, bulduğu ilk hedefi ve tüm bağımlılıkları oluşturur; proje dosyası bir `DefaultTargets` öznitelik, bir `InitialTargets` öznitelik veya hedef, komut satırında **-target** anahtarı kullanılarak belirtilir.
## <a name="use-the-initialtargets-attribute"></a>InitialTargets özniteliğini kullanma

`InitialTargets`Öğesinin özniteliği, `Project` hedefler komut satırında veya özniteliğinde belirtilmiş olsa bile, ilk olarak çalıştırılacak hedefi belirtir `DefaultTargets` .

#### <a name="to-specify-one-initial-target"></a>Bir başlangıç hedefi belirtmek için

- Öğesinin özniteliğinde varsayılan hedefi belirtin `InitialTargets` `Project` . Örneğin:

   `<Project InitialTargets="Clean">`

  `InitialTargets`Hedefleri sırayla listeleyerek ve her hedefi ayırmak için noktalı virgül kullanarak öznitelikte birden fazla başlangıç hedefi belirtebilirsiniz. Listedeki hedefler sırayla çalıştırılır.

#### <a name="to-specify-more-than-one-initial-target"></a>Birden fazla ilk hedef belirtmek için

- Öğe özniteliğinde noktalı virgülle ayırarak ilk hedefleri listeleyin `InitialTargets` `Project` . Örneğin, `Clean` hedefi ve sonra hedefi çalıştırmak için `Compile` şunu yazın:

     `<Project InitialTargets="Clean;Compile">`

## <a name="use-the-defaulttargets-attribute"></a>DefaultTargets özniteliğini kullanma

 `DefaultTargets`Öğesinin özniteliği, `Project` bir hedef açık olarak komut satırında belirtilmemişse, hangi hedefin veya hedeflerin derlenmediğini belirtir. Hedefler hem `InitialTargets` hem de `DefaultTargets` özniteliklerde belirtilirse ve komut satırında hiçbir hedef belirtilmemişse, MSBuild özniteliğinde belirtilen hedefleri, `InitialTargets` ardından özniteliğinde belirtilen hedefleri çalıştırır `DefaultTargets` .

#### <a name="to-specify-one-default-target"></a>Bir varsayılan hedef belirtmek için

- Öğesinin özniteliğinde varsayılan hedefi belirtin `DefaultTargets` `Project` . Örneğin:

   `<Project DefaultTargets="Compile">`

  `DefaultTargets`Hedefleri sırasıyla listeleyerek ve her hedefi ayırmak için noktalı virgül kullanarak öznitelikte birden fazla varsayılan hedef belirtebilirsiniz. Listedeki hedefler sırayla çalıştırılır.

#### <a name="to-specify-more-than-one-default-target"></a>Birden fazla varsayılan hedef belirtmek için

- Öğesinin özniteliğinde, varsayılan hedefleri noktalı virgülle ayırarak listeleyin `DefaultTargets` `Project` . Örneğin, `Clean` hedefi ve sonra hedefi çalıştırmak için `Compile` şunu yazın:

     `<Project DefaultTargets="Clean;Compile">`

## <a name="use-the--target-switch"></a>-Target anahtarını kullanma

 Proje dosyasında varsayılan bir hedef tanımlanmamışsa veya bu varsayılan hedefi kullanmak istemiyorsanız, farklı bir hedef belirtmek için anahtar **-hedef** komut satırını kullanabilirsiniz. **-Target** anahtarıyla belirtilen hedef veya hedefler, özniteliği tarafından belirtilen hedefler yerine çalıştırılır `DefaultTargets` . Öznitelikte belirtilen hedefler `InitialTargets` her zaman önce çalıştırılır.

#### <a name="to-use-a-target-other-than-the-default-target-first"></a>Önce varsayılan hedeften farklı bir hedef kullanmak için

- Hedefi, **-target** komut satırı anahtarını kullanarak ilk hedef olarak belirtin. Örneğin:

     `msbuild file.proj -target:Clean`

#### <a name="to-use-several-targets-other-than-the-default-targets-first"></a>Önce varsayılan hedefleri dışında birkaç hedefi kullanmak için

- Hedefleri, **-target** komut satırı anahtarını kullanarak noktalı virgül veya virgülle ayırarak listeleyin. Örneğin:

     `msbuild <file name>.proj -t:Clean;Compile`

## <a name="see-also"></a>Ayrıca bkz.

- [MSBuild](../msbuild/msbuild.md)
- [Targets](../msbuild/msbuild-targets.md)
- [Nasıl yapılır: derlemeyi Temizleme](../msbuild/how-to-clean-a-build.md)
