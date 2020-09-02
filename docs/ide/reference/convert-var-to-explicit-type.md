---
title: Var olan bir açık türle değiştirmek için kodu yeniden düzenleme
ms.date: 05/15/2018
ms.topic: reference
author: TerryGLee
ms.author: tglee
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 4ec388564e1851402f085f6bbaefba08dbea212c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75595780"
---
# <a name="refactoring-to-replace-var-with-an-explicit-type"></a>Var olan öğesini açık bir türle değiştirecek şekilde yeniden düzenleme

Yerel bir değişken bildiriminde [var](/dotnet/csharp/language-reference/keywords/var) olan bir açık tür ile değiştirmek için bu yeniden düzenlemeyi kullanın.

Bu yeniden düzenleme için geçerlidir:

- C#

## <a name="why-to-use-an-explicit-type"></a>Neden açık bir tür kullanılmalıdır

Aşağıda açık türde bir değişken bildirmek için bazı nedenler verilmiştir:

- Kodun okunabilirliğini geliştirmek için.

- Bildiriminde değişkeni başlatmak istemediğinizde.

Ancak, bir değişken anonim bir türle başlatıldığında ve nesnenin özelliklerine sonraki bir noktada erişildiğinde, [var](/dotnet/csharp/language-reference/keywords/var) kullanılması gerekir. Daha fazla bilgi için bkz. [örtülü olarak yazılan yerel değişkenler (C#)](/dotnet/csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables).

## <a name="how-to-use-it"></a>Nasıl kullanılır?

1. Giriş işaretini `var` anahtar sözcüğe yerleştirin.

1. **CTRL**tuşuna basın + **.** ya da ![ kod dosyasının kenar boşluğundaki screwdriver screwdriver simge ](../media/screwdriver-icon.png) simgesine tıklayın.

   ![Açık tür hızlı eylemler menüsünü kullan](media/use-explicit-type.png)

1. **Açık türü kullan**' ı seçin. Ya [da Değişiklikleri Önizle iletişim kutusunu](../../ide/preview-changes.md) açmak Için **Değişiklikleri Önizle** ' yi seçin ve ardından **Uygula**' yı seçin.

## <a name="see-also"></a>Ayrıca bkz.

- [Örtük olarak yazılan değişkenler (C#)](/dotnet/csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables)
- [Yeniden Düzenle](../refactoring-in-visual-studio.md)
- [Değişiklikleri Önizleme](../../ide/preview-changes.md)
