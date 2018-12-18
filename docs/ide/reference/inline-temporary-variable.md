---
title: Geçici bir değişken değeriyle değiştirin.
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
ms.openlocfilehash: a6fea50f3cceb907cb014d29bb46988ab07dad6c
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53066869"
---
# <a name="inline-a-temporary-variable-refactoring"></a>Satır içi bir geçici değişken yeniden düzenleme

Bu yeniden düzenleme için geçerlidir:

- C#

- Visual Basic

**Ne:** geçici değişken kaldırın ve bunun yerine değeriyle değiştirme olanak tanır.

**Ne zaman:** geçici değişken kullanımı kodu anlamak zorlaştırır.

**Neden:** geçici değişken kaldırılması duruma kodu daha kolay okunabilir.

## <a name="how-to"></a>Nasıl Yapılır Konuları

1. Vurgulama veya satır içine alınmayacak kadar geçici değişken metin imleci yerleştirin:

   - C# İÇİN:

       ![Vurgulanan kodu:C#](media/inline-highlight-cs.png)

   - Visual Basic:

       ![Vurgulanan kod - Visual Basic](media/inline-highlight-vb.png)

2. Ardından, aşağıdakilerden birini yapın:

   - **Klavye**
      - Tuşuna **Ctrl**+**.** Tetikleyici için **hızlı Eylemler ve yeniden düzenlemeler** menüsü.
   - **Fare**
      - Kod sağ tıklayıp **hızlı Eylemler ve yeniden düzenlemeler** menüsü.

3. Seçin **satır içi geçici değişken** gelen önizleme penceresi açılır.

   Değişken kaldırılır ve kendi kullanımları değişkenin değeriyle değiştirilir.

   - C# İÇİN:

      ![Satır içi sonucu-C#](media/inline-result-cs.png)

   - Visual Basic:

      ![Satır içi sonucu - Visual Basic](media/inline-result-vb.png)

## <a name="see-also"></a>Ayrıca bkz.

- [Yeniden Düzenleme](../refactoring-in-visual-studio.md)