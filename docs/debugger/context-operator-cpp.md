---
title: Bağlam işleci (C++) hata ayıklayıcısı | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.operators
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- expressions [C++], native debugger
- evaluation
- format specifiers, expressions
- context operator, in expressions
- debugging [C++], expressions
- native expression evaluator
ms.assetid: 73cc9afe-f4a4-474e-bb89-5a33fb5e570c
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- cplusplus
ms.openlocfilehash: e520b40e5a2f4bf6bb7c3a7b6c2ab50930773578
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49862404"
---
# <a name="context-operator-in-the-visual-studio-debugger-c"></a>Bağlam işleci Visual Studio hata ayıklayıcısında (C++)
Bir kesme noktası konumu, değişken adı veya ifade nitelemek için C++'da şu içerik işlecini kullanabilirsiniz. Bağlam işleci, aksi takdirde yerel bir ad tarafından gizlenen bir dış kapsam adı belirtmek için kullanışlıdır.  
  
##  <a name="BKMK_Using_context_operators_to_specify_a_symbol"></a> Söz dizimi  
 Bağlam belirtmenin iki yolu vardır:  
  
1.  {, [*Modülü*]} *ifadesi*  
  
     Küme ayraçları iki virgül ve modül içermelidir (yürütülebilir veya DLL) adını veya tam yolu.  
  
     Örneğin, bir kesme noktasında ayarlanacak `SomeFunction` EXAMPLE.dll işlevi:  
  
    ```C++  
    {,,EXAMPLE.dll}SomeFunction  
    ```  
  
2.  *Modül*! *ifade*  
  
    ```C++  
    EXAMPLE.dll!SomeFunction  
    ```  
  
- *Modül* bir modül adı. Aynı ada sahip modüller arasında ayırt etmek için bir tam yol kullanabilirsiniz.  
  
   Varsa *Modülü* yolu, virgül, katıştırılmış bir boşluk veya bir küme ayracı içerir, bağlam ayrıştırıcının dizesi düzgün tanıyabilmesi, yolu tırnak kullanmanız gerekir. Tek tırnak işaretleri çift tırnak işareti kullanmalısınız bir Windows dosya adının parçası olarak kabul edilir. Örneğin,  
  
  ```C++  
  {,,"a long, long, library name.dll"} g_Var  
  ```  
  
- *ifade* işlev adı, değişken adı veya işaretçi adresi gibi geçerli bir hedef çözümler herhangi geçerli bir C++ ifadesi *Modülü*.  
  
  İfade değerlendirici bir ifadede bir sembol karşılaştığında sembolünün şu sırayla arar:  
  
1.  Sözcük kapsamı geçerli blok küme ayraçları içine alındığına ve dışa doğru kapsayan bir blok ile devam bir deyimler serisini başlayarak dışa doğru. Geçerli blok yönerge işaretçisi adresi geçerli konumu içeren kodudur.  
  
2.  İşlev kapsamı. Geçerli işlev.  
  
3.  C++ üye işlevinin içerisinde geçerli konumu ise sınıf kapsamı. Sınıf kapsamı, tüm temel sınıflar içerir. İfade değerlendirici, normal baskınlık kurallarını kullanır.  
  
4.  Genel semboller geçerli modül içinde.  
  
5.  Ortak semboller geçerli programı.