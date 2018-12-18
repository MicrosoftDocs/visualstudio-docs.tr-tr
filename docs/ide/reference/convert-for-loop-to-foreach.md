---
title: Dönüştürülecek kodu yeniden bir döngünün foreach deyimi
ms.date: 05/10/2018
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
ms.openlocfilehash: 6a200874cec92fada17c13eb45e226ce26119a60
ms.sourcegitcommit: 209c2c068ff0975994ed892b62aa9b834a7f6077
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/17/2018
ms.locfileid: "34267679"
---
# <a name="refactoring-to-convert-between-a-for-loop-and-a-foreach-statement"></a>Yeniden düzenleme arasında dönüştürme için bir döngü için ve foreach deyimi

Bu makalede iki döngü yapıları arasında dönüştürme hızlı Eylemler yapan yeniden düzenlemeler. Neden isteyebilirsiniz arasında geçiş yapmak için bazı nedenler içeren bir [için](/dotnet/csharp/language-reference/keywords/for) döngü ve [foreach](/dotnet/csharp/language-reference/keywords/foreach-in) deyimi kodunuza.

## <a name="convert-a-for-loop-to-a-foreach-statement"></a>Dönüştürme bir döngünün foreach deyimi

Varsa bir [için](/dotnet/csharp/language-reference/keywords/for) döngü kodunuzda bu yeniden düzenleme için dönüştürmek için kullanabileceğiniz bir [foreach](/dotnet/csharp/language-reference/keywords/foreach-in) deyimi.

Bu yeniden düzenleme için geçerlidir:

- C#

> [!NOTE]
> **İçin foreach Dönüştür** hızlı eylem yeniden düzenleme yüklenebilir yalnızca [için](/dotnet/csharp/language-reference/keywords/for) tüm üç bölümden içeren döngüler: Başlatıcı, koşul ve yineleyici.

### <a name="why-convert"></a>Neden Dönüştür

Dönüştürme isteyebileceğiniz neden bir [için](/dotnet/csharp/language-reference/keywords/for) döngüsü bir [foreach](/dotnet/csharp/language-reference/keywords/foreach-in) deyimi içerir:

- Öğesine erişmek için bir dizin olarak döngü dışında içindeki yerel döngü değişkeni kullanmayın.

- Kodunuzu basitleştiren ve Başlatıcı, koşul ve yineleyici bölümlerindeki mantık hataları olasılığını azaltmak istiyor.

### <a name="how-to-use-it"></a>Nasıl kullanılacağını

1. İçinde düzeltme işareti koyun `for` anahtar sözcüğü.

1. Tuşuna **Ctrl**+**.** veya tornavida ![tornavida simgesi](../media/screwdriver-icon.png) kod dosyasının kenar boşluğunda simgesi.

   ![Foreach menüye dönüştürme](media/convert-to-foreach.png)

1. Seçin **'foreach' Dönüştür**. Ya da seçin **Önizleme değişiklikleri** açmak için [Değişiklikleri Önizle](../../ide/preview-changes.md) iletişim ve ardından **Uygula**.

## <a name="convert-a-foreach-statement-to-a-for-loop"></a>Foreach deyimi için dönüştürme bir döngü için

Varsa bir [foreach (C#)](/dotnet/csharp/language-reference/keywords/foreach-in) veya [For Each... Next (Visual Basic)](/dotnet/visual-basic/language-reference/statements/for-each-next-statement) kodunuzu deyiminde, bu yeniden düzenleme dönüştürebilir için kullanabileceğiniz bir [için](/dotnet/csharp/language-reference/keywords/for) döngü.

Bu yeniden düzenleme için geçerlidir:

- C#

- Visual Basic

### <a name="why-convert"></a>Neden Dönüştür

Dönüştürme isteyebileceğiniz neden bir [foreach](/dotnet/csharp/language-reference/keywords/foreach-in) ifadesine bir [için](/dotnet/csharp/language-reference/keywords/for) döngü içerir:

- Daha fazlasını öğesi erişmek için yerel döngü değişkeni döngü içinde kullanmak istediğiniz.

- Olduğunuz [çok boyutlu bir dizi yineleme](/dotnet/csharp/programming-guide/arrays/using-foreach-with-arrays) ve dizi öğeleri hakkında daha fazla denetime istiyor.

### <a name="how-to-use-it"></a>Nasıl kullanılacağını

1. İçinde düzeltme işareti koyun `foreach` veya `For Each` anahtar sözcüğü.

1. Tuşuna **Ctrl**+**.** veya tornavida ![tornavida simgesi](../media/screwdriver-icon.png) kod dosyasının kenar boşluğunda simgesi.

   ![Menü için Dönüştür](media/convert-to-for.png)

1. Seçin **'için' Dönüştür**. Ya da seçin **Önizleme değişiklikleri** açmak için [Değişiklikleri Önizle](../../ide/preview-changes.md) iletişim ve ardından **Uygula**.

1. Yeniden düzenleme yeni bir yineleme sayısı değişkeni oluşturduğundan **yeniden adlandırma** Kutusu Düzenleyicisi'ni sağ üst köşesinde görüntülenir. Değişkeni için farklı bir ad seçmek istiyorsanız, yazın ve sonra basın **Enter** veya seçin **Uygula** içinde **yeniden adlandırma** kutusu. Yeni bir ad seçin istemiyorsanız basın **Esc** veya seçin **Uygula** kapatmak için **yeniden adlandırma** kutusu.

> [!NOTE]
> C# ' ta açık bir tür bu yapan yeniden düzenlemeler tarafından oluşturulan kodu kullanır veya [var](/dotnet/csharp/language-reference/keywords/var) koleksiyondaki öğelerin türü. Oluşturulan kod, doğrudan veya dolaylı türünde kapsamındaki kod stili ayarlarına bağlıdır. Bu belirli kod stilini ayarlar altında makine düzeyinde yapılandırılır **Araçları** > **seçenekleri** > **metin düzenleyici**  >  **C#** > **kod stili** > **genel** > **\'var' Tercihler**, ya da çözüm düzeyinde bir [EditorConfig](../../ide/editorconfig-code-style-settings-reference.md#implicit-and-explicit-types) dosya. Bir kod stili ayarı değiştirirseniz, **seçenekleri**, değişikliklerin etkili olması kod dosyası yeniden açın.

## <a name="see-also"></a>Ayrıca bkz.

- [Yeniden Düzenleme](../refactoring-in-visual-studio.md)
- [Değişiklikleri Önizleme](../../ide/preview-changes.md)