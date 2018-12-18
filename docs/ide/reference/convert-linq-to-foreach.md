---
title: Foreach deyimi için bir LINQ Sorgu dönüştürmek için kodu yeniden düzenleyin
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
ms.openlocfilehash: e3e4e448931e028c53d62c534e2785e4f026a7ec
ms.sourcegitcommit: 209c2c068ff0975994ed892b62aa9b834a7f6077
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/17/2018
ms.locfileid: "34268922"
---
# <a name="refactoring-to-convert-linq-to-a-foreach-statement"></a>Foreach deyimi için LINQ dönüştürmek için yeniden düzenleme

Dönüştürmek için bu yeniden düzenleme kullanın [LINQ Sorgu sözdizimi](/dotnet/csharp/programming-guide/concepts/linq/query-syntax-and-method-syntax-in-linq) için bir [foreach](/dotnet/csharp/language-reference/keywords/foreach-in) deyimi.

Bu yeniden düzenleme için geçerlidir:

- C#

## <a name="how-to-use-it"></a>Nasıl kullanılacağını

1. Tüm LINQ Sorgu başlayarak seçin `from`.

   > [!NOTE]
   > Bu yeniden düzenleme yalnızca sorgu sözdizimi ve yöntem sözdizimi ile ifade LINQ sorgularını dönüştürmek için kullanılabilir.

1. Tuşuna **Ctrl**+**.** veya tornavida ![tornavida simgesi](../media/screwdriver-icon.png) kod dosyasının kenar boşluğunda simgesi.

   ![Foreach hızlı Eylemler menüsüne LINQ Dönüştür](media/convert-linq-to-foreach.png)

1. Seçin **'foreach' Dönüştür**. Ya da seçin **Önizleme değişiklikleri** açmak için [Değişiklikleri Önizle](../../ide/preview-changes.md) iletişim ve ardından **Uygula**.

> [!NOTE]
> C# ' ta açık bir tür bu yapan yeniden düzenlemeler tarafından oluşturulan kodu kullanır veya [var](/dotnet/csharp/language-reference/keywords/var) değişkeni için `foreach` döngü. Oluşturulan kod, doğrudan veya dolaylı türünde kapsamındaki kod stili ayarlarına bağlıdır. Bu belirli kod stilini ayarlar altında makine düzeyinde yapılandırılır **Araçları** > **seçenekleri** > **metin düzenleyici**  >  **C#** > **kod stili** > **genel** > **\'var' Tercihler**, ya da çözüm düzeyinde bir [EditorConfig](../../ide/editorconfig-code-style-settings-reference.md#implicit-and-explicit-types) dosya. Bir kod stili ayarı değiştirirseniz, **seçenekleri**, değişikliklerin etkili olması kod dosyası yeniden açın.

## <a name="see-also"></a>Ayrıca bkz.

- [LINQ](/dotnet/standard/using-linq)
- [Yeniden Düzenleme](../refactoring-in-visual-studio.md)
- [Değişiklikleri Önizleme](../../ide/preview-changes.md)