---
title: DebuggerTypeProxy özniteliğini kullanma | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- attributes [C#], debugger
- DebuggerTypeProxyAttribute class
- DebuggerTypeProxy attribute
ms.assetid: 943f3bb1-993e-4800-a47e-0af78b063014
caps.latest.revision: 27
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 14e42546245aad8e5e5071a843da87f23a038149
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51754333"
---
# <a name="using-debuggertypeproxy-attribute"></a>DebuggerTypeProxy Özniteliğini Kullanma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

DebuggerTypeProxyAttribute] (assetId:///T:System.Diagnostics.DebuggerTypeProxyAttribute?qualifyHint=False & autoUpgrade = True) bir proxy belirtir ya da stand-in, bir tür ve değişiklikleri yol türü için hata ayıklayıcı pencerelerinde görüntülenir. Bir proxy sahip bir değişken görüntülediğinizde, proxy özgün türü için anlamına gelir **görüntüleme**. Proxy türü yalnızca genel üyeleri hata ayıklayıcı değişken penceresinde görüntüler. Özel üyeler görüntülenmez.  
  
 Bu öznitelik için uygulanabilir:  
  
- Yapılar  
  
- Sınıflar  
  
- Derlemeleri  
  
  Proxy yerini alacak türünde bir bağımsız değişken alan bir oluşturucu türü proxy sınıfı olmalıdır. Hedef türünde bir değişken görüntülemek ihtiyaç duyduğu her seferinde hata ayıklayıcı türü proxy sınıfının yeni bir örneğini oluşturur. Bu performans etkileri olabilir. Sonuç olarak, tüm kıyasla daha fazla oluşturucuda kesin olarak gerekmedikçe yapmamanız gerekir.  
  
  Türü kullanıcı tıklayarak genişletilir sürece performans cezaları en aza indirmek için ifade değerlendirici türündeki görüntü proxy özniteliklerinde incelemez + simgesi hata ayıklayıcı penceresinde veya kullanımını <xref:System.Diagnostics.DebuggerBrowsableAttribute>. Bu nedenle, öznitelikler görünen türün kendisine girmemelisiniz. Öznitelikleri olabilir ve görünen yöntemin gövdesinde kullanılmalıdır.  
  
  Özel bir iç içe geçmiş sınıf sınıf içinde olacak şekilde proxy türü için iyi bir fikir olduğunu, öznitelik hedefleri. Bu durum iç üyeleri bir kolayca erişmenizi sağlar.  
  
  Varsa <xref:System.Diagnostics.DebuggerTypeProxyAttribute> derleme düzeyinde kullanılan `Target` parametresi proxy değiştirilecek olan türünü belirtir.  
  
  Bu öznitelik ile birlikte kullanma örneği için <xref:System.Diagnostics.DebuggerDisplayAttribute> ve <xref:System.Diagnostics.DebuggerTypeProxyAttribute>, bkz:[DebuggerDisplay özniteliğini kullanma](../debugger/using-the-debuggerdisplay-attribute.md).  
  
## <a name="using-generics-with-debuggertypeproxy"></a>DebuggerTypeProxy ile Genellemeleri kullanma  
 Genel türler için destek sınırlıdır. C# ' ta, `DebuggerTypeProxy` yalnızca açık türlerini destekler. Unconstructed bir tür olarak da bilinir, açık bir tür bağımsız değişkenleri için tür parametrelerinden biri ile oluşturulmadı genel bir türdür. Oluşturulan türler olarak da bilinir, kapalı türleri desteklenmez.  
  
 Açık bir tür için söz dizimi şu şekilde görünür:  
  
 `Namespace.TypeName<,>`  
  
 Bir hedef olarak bir genel tür kullanıyorsanız `DebuggerTypeProxy`, bu sözdizimini kullanmanız gerekir. `DebuggerTypeProxy` Mekanizması, tür parametreleri algılar.  
  
 C# açık ve kapalı türleri hakkında daha fazla bilgi için bkz. [C# dil belirtimi](http://msdn.microsoft.com/library/e5d5a5cc-636b-4bff-b9c8-a8edc6207c22), 20.5.2 bölümünü açın ve türleri.  
  
 Visual Basic açık tür sözdizimi olmadığından, Visual Basic'te de aynı bunu yapamazsınız. Bunun yerine açık tür adı bir dize gösterimini kullanmanız gerekir.  
  
 `"Namespace.TypeName'2"`  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [DebuggerDisplay özniteliğini kullanma](../debugger/using-the-debuggerdisplay-attribute.md)   
  [Hata Ayıklayıcı Görüntü Öznitelikleriyle Hata Ayıklamayı Geliştirme](http://msdn.microsoft.com/library/72bb7aa9-459b-42c4-9163-9312fab4c410)



