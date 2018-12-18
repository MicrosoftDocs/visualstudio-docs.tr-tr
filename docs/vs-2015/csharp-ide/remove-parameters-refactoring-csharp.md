---
title: Parametreleri Kaldır yeniden düzenlemesi (C#) | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.csharp.refactoring.remove
dev_langs:
- CSharp
helpviewer_keywords:
- parameters [C#], removing
- refactoring [C#], Remove Parameters
- Remove Parameters refactoring [C#]
ms.assetid: f4fc3265-0ef8-4398-a691-c338178697a6
caps.latest.revision: 24
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: c9559deda5c5cdc60adc10246196fb66646cfee5
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49284394"
---
# <a name="remove-parameters-refactoring-c"></a>Parametreleri Kaldır Yeniden Düzenlemesi (C#)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

`Remove Parameters` parametreleri yöntemlerden, dizin oluşturucular ya da temsilcilerden kaldırmak için kolay bir yol sağlayan bir yeniden düzenleme işlemi var. Parametreleri değişiklikleri bildirimini kaldırın; Burada üyesi çağrılır, her bir konumda yeni bildirimi yansıtacak şekilde parametresi kaldırıldı.  
  
 Parametreleri Kaldır işlemi, ilk yöntem, dizin oluşturucu veya temsilci imleci konumlandırma gerçekleştirin. İmleç konumu Kaldır çağrılacak alanındayken `Parameters` işlemi tıklayın **yeniden düzenleme** menüsünde, klavye kısayol tuşlarına basın veya komutu kısayol menüsünden seçin.  
  
> [!NOTE]
>  Genişletme yönteminin ilk parametresi kaldırılamıyor.  
  
### <a name="to-remove-parameters"></a>Parametreleri kaldırmak için  
  
1.  Adlı bir konsol uygulaması oluşturun `RemoveParameters`ve ardından `Program` aşağıdaki kod ile.  
  
    ```csharp  
    class A  
    {  
        // Invoke on 'A'.  
        public A(string s, int i) { }  
    }  
  
    class B  
    {  
        void C()  
        {  
            // Invoke on 'A'.  
            A a = new A("a", 2);  
        }  
    }  
    ```  
  
2.  İmleci metodunda `A`, yöntem bildiriminde veya yöntem çağrısı.  
  
3.  Gelen **yeniden düzenleme** menüsünde **parametreleri Kaldır** görüntülenecek **parametreleri Kaldır** iletişim kutusu.  
  
     Ayrıca CTRL + R, görüntülenecek V klavye kısayolunu yazın **parametreleri Kaldır** iletişim kutusu.  
  
     Ayrıca, imleç sağ işaret **yeniden düzenleyin**ve ardından **parametreleri Kaldır** görüntülenecek **parametreleri Kaldır** iletişim kutusu.  
  
4.  Kullanarak **parametreleri** alan, imleci getirin `int i`ve ardından **Kaldır**.  
  
5.  **Tamam**'ı tıklatın.  
  
6.  İçinde **Değişiklikleri Önizle — Parametreleri Kaldır** iletişim kutusu, tıklayın **Uygula**.  
  
## <a name="remarks"></a>Açıklamalar  
 Yöntem bildiriminde veya yöntem çağrısı parametreleri kaldırabilirsiniz. Yöntem bildiriminde ya da temsilci adı imleci yerleştirin ve parametreleri Kaldır çağırın.  
  
> [!CAUTION]
>  Parametreleri etkinleştirir, başvurulmayan parametre üyesi, ancak gövdesinde kaldırmak için bu parametre başvuruları yöntemin gövdesinde kaldırmaz kaldırın. Bu, kodunuzda yapı hatalara neden olabilir. Ancak, kullanabileceğiniz **Değişiklikleri Önizle** iletişim kutusunu yeniden düzenleme işlemi çalıştırmadan önce kodunuzu gözden geçirin.  
  
 Kaldırılmakta olan bir parametreyi, bir yöntem çağrısı sırasında değiştirilirse, parametre kaldırılmasını değişikliği de kaldırılır. Bir yöntem çağırırsanız, değiştirilirse  
  
```csharp  
MyMethod(param1++, param2);  
```  
  
 to  
  
```csharp  
MyMethod(param2);  
```  
  
 yeniden düzenleme işlemi tarafından `param1` artmaz.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Yeniden Düzenleme (C#)](../csharp-ide/refactoring-csharp.md)