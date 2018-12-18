---
title: Türü eşleşen dosya yeniden düzenleme için Taşı
ms.date: 01/26/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 997cf31d14acd65abd003bcb00cce4a9797b394a
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53059645"
---
# <a name="move-a-type-to-a-matching-file-refactoring"></a>Bir eşleşen dosya yeniden düzenleme için bir tür Taşı

Bu yeniden düzenleme için geçerlidir:

- C#

- Visual Basic

**Ne:** Seçili türde aynı ada sahip ayrı bir dosyaya geçiş yapmanıza izin veren.

**Ne zaman:** ayırmak istediğiniz aynı dosyaya birden fazla sınıflar, yapılar, arabirimler, vb. vardır.

**Neden:** aynı dosyaya birden fazla yerleştirme yapabilirsiniz, bu tür bulmak zordur. Aynı ada sahip dosyaları türleri taşıyarak, kod daha okunabilir ve giderek daha kolay hale gelir.

## <a name="how-to"></a>Nasıl Yapılır Konuları

1. Burada tanımlanan türünün adı imleci yerleştirin. Örneğin:

   ```csharp
   class Person
   ```

   ```vb
   Class Person
   ```

2. Ardından, aşağıdakilerden birini yapın:

   - Tuşuna **Ctrl**+**.**
   - Tür adına sağ tıklayıp **hızlı Eylemler ve yeniden düzenlemeler**

1. Seçin **türüne taşımak için *TypeName*.cs** menüsünden, burada *TypeName* seçtiğiniz türünün adı.

   Yeni bir dosya türü ile aynı ada sahip bir proje türü taşınır.

   - C# İÇİN:

      ![Satır içi sonucu-C#](media/movetype-result-cs.png)

   - Visual Basic:

      ![Satır içi sonucu - Visual Basic](media/movetype-result-vb.png)

## <a name="see-also"></a>Ayrıca bkz.

- [Yeniden Düzenleme](../refactoring-in-visual-studio.md)
