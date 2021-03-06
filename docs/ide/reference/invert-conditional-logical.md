---
title: Koşullu ifadeleri ve mantıksal işlemleri tersine çevirme
description: Koşullu bir ifadeyi veya koşullu ve/veya işlecini tersine çevirmek için hızlı eylemler ve yeniden düzenlemeler menüsünü nasıl kullanacağınızı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 02/19/2019
ms.topic: reference
author: kendrahavens
ms.author: kehavens
manager: jmartens
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 0bd75a40f52a6148a6c50b212183bb8dc7a52d56
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99852251"
---
# <a name="invert-conditional-expressions-and-conditional-andor-operators"></a>Koşullu ifadeleri ve koşullu ve/veya işleçleri ters çevir

Bu yeniden düzenleme için geçerlidir:

- C#
- Visual Basic

**Ne:** Koşullu bir ifadeyi veya bir koşullu ve/veya işlecini ters çevirmenizi sağlar.

**Ne zaman:** Ters çevrilsiyse daha iyi anlaşılabilecek koşullu bir ifade veya koşullu ve/veya operatörünüz vardır.

**Neden:** Bir ifadeyi veya koşullu ve/veya işleci el ile tersine çevirme çok daha uzun sürebilir ve muhtemelen hata verebilir. Bu kod çözümü, bu yeniden düzenlemeyi otomatik olarak yapmanıza yardımcı olur.

## <a name="invert-conditional-expressions-and-conditional-andor-operators-refactoring"></a>Koşullu ifadeleri ve koşullu ve/veya işleçleri yeniden düzenlemeyi ters çevir

1. İmlecinizi koşullu bir ifadeye veya koşullu ve/veya işleçte yerleştirin.
2. **CTRL** tuşuna basın + **.** **hızlı eylemleri ve yeniden düzenlemeler** menüsünü tetiklemek için.
3. **Koşullu çevir** ' i seçin veya ' **&& ' öğesini ' | | ' ile değiştirin**

    ![Ters çevir koşullu seçeneğinin ekran görüntüsü.](media/invert-conditional.png)

    ![Değiştirme && ekran görüntüsü | | seçeneği.](media/invert-logical-operator.png)

## <a name="see-also"></a>Ayrıca bkz.

- [Yeniden Düzenle](../refactoring-in-visual-studio.md)
- [.NET geliştiricileri için ipuçları](../csharp-developer-productivity.md)
