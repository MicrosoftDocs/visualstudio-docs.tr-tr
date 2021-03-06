---
title: Switch deyimini switch ifadesine dönüştürme
description: Bir switch deyimini C# 8,0 anahtar ifadesine dönüştürmek için hızlı eylemler ve yeniden düzenlemeler menüsünü nasıl kullanacağınızı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 06/19/2019
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jmartens
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 56a1b20854cdd2c1821490bb4972d67bbe912056
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99919667"
---
# <a name="convert-switch-statement-to-switch-expression"></a>Switch deyimini switch ifadesine dönüştürme

Bu yeniden düzenleme için geçerlidir:

- C#

**Ne:** [Switch deyimini](/dotnet/csharp/language-reference/keywords/switch) C# 8,0 [anahtar ifadesine](/dotnet/csharp/whats-new/csharp-8#switch-expressions)Dönüştür.

**Ne zaman:** Bir deyimi ifadeye dönüştürmek istiyorsunuz, `switch` `switch` tersi de geçerlidir. 

**Neden:** Yalnızca ifadeler kullanıyorsanız, bu yeniden düzenleme geleneksel deyimlerden kolay bir geçişe izin vermez `switch` .

## <a name="how-to"></a>Nasıl yapılır

1. Proje dosyanızda, ifadeler yeni bir C# 8,0 özelliği olduğundan, [dil sürümünü önizleme olarak ayarlayın](/dotnet/csharp/language-reference/configure-language-version#edit-the-project-file) `switch` .
2. İmlecinizi `switch` anahtar sözcüğe yerleştirip **CTRL** tuşuna basın + **.** **hızlı eylemleri ve yeniden düzenlemeler** menüsünü tetiklemek için.
3. **Switch deyimini Ifadeye Dönüştür**' ü seçin.

   ![Switch deyimini switch ifadesine dönüştürme](media/convert-switch-statement-to-switch-expression.png) 

## <a name="see-also"></a>Ayrıca bkz.

- [Yeniden Düzenle](../refactoring-in-visual-studio.md)
