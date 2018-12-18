---
title: Var bir açık tür değiştirmek için kod yeniden Düzenle
ms.date: 05/15/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 9d816921f3449edfcd28a2fa9f4e2af9b9d015f9
ms.sourcegitcommit: 209c2c068ff0975994ed892b62aa9b834a7f6077
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/17/2018
ms.locfileid: "34268925"
---
# <a name="refactoring-to-replace-var-with-an-explicit-type"></a>Var bir açık tür değiştirmek için yeniden düzenleme

Değiştirmek için bu yeniden düzenleme kullanmak [var](/dotnet/csharp/language-reference/keywords/var) açık türe sahip bir yerel değişken bildiriminde.

Bu yeniden düzenleme için geçerlidir:

- C#

## <a name="why-to-use-an-explicit-type"></a>Açık tür kullanmak neden

Bir açık türünde bir değişken bildirmek için bazı nedenler şunlardır:

- Kodun okunabilirliğini artırmak için.

- Ne zaman bildiriminde değişkeni başlatmak istemiyorsanız.

Ancak, [var](/dotnet/csharp/language-reference/keywords/var) bir değişkene sahip anonim bir tür başlatılır ve daha sonraki bir noktada nesnenin özelliklerini erişilen kullanılmalıdır. Daha fazla bilgi için bkz: [örtük olarak yazılan yerel değişkenler (C#)](/dotnet/csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables).

## <a name="how-to-use-it"></a>Nasıl kullanılacağını

1. Düzeltme işareti yerleştirin `var` anahtar sözcüğü.

1. Tuşuna **Ctrl**+**.** veya tornavida ![tornavida simgesi](../media/screwdriver-icon.png) kod dosyasının kenar boşluğunda simgesi.

   ![Açık tür hızlı Eylemler menüsünü kullanın](media/use-explicit-type.png)

1. Seçin **açık tür kullanmak**. Ya da seçin **Önizleme değişiklikleri** açmak için [Değişiklikleri Önizle](../../ide/preview-changes.md) iletişim ve ardından **Uygula**.

## <a name="see-also"></a>Ayrıca bkz.

- [Türü örtük olarak belirlenmiş değişkenleri (C#)](/dotnet/csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables)
- [Yeniden Düzenleme](../refactoring-in-visual-studio.md)
- [Değişiklikleri Önizleme](../../ide/preview-changes.md)