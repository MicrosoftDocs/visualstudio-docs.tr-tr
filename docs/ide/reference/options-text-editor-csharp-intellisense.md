---
title: Seçenekler, Metin Düzenleyici, C#, IntelliSense
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.CSharp.Intellisense
helpviewer_keywords:
- underlines, wavy
- IntelliSense [C#], options
- IntelliSense [C#], wavy underlines
- wavy underlines
- Text Editor Options dialog box, IntelliSense
ms.assetid: 3466dedb-e5f4-424c-8dd8-e4941b2f4fc2
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 041b3c5d0a67d590bc409c21dd53d5d162b0a0b9
ms.sourcegitcommit: dd839de3aa24ed7cd69f676293648c6c59c6560a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/27/2018
ms.locfileid: "52389269"
---
# <a name="options-text-editor-c-intellisense"></a>Seçenekler, Metin Düzenleyici, C#, IntelliSense

Kullanım **IntelliSense** için IntelliSense'in davranışını etkileyen ayarları değiştirmek için seçenekler sayfası C#. Bu seçenekler sayfası erişmek için kendi seçtikleri **Araçları** > **seçenekleri**ve ardından **metin düzenleyici**  >  **C#**  >  **IntelliSense**.

**IntelliSense** seçenekleri sayfasında aşağıdaki seçenekleri içerir:

## <a name="completion-lists"></a>Tamamlanma listeleri

- Bir karakter girildikten sonra Tamamlama listesini göster *

   Bu seçenek belirlendiğinde, yazmaya başladığınızda IntelliSense tamamlanma listesi otomatik olarak görüntüler. Bu seçenek seçilmezse, IntelliSense tamamlama hala kullanılabilir **IntelliSense** menü tuşuna basarak veya **Ctrl**+**alanı**.

- Bir karakter silindikten sonra Tamamlama listesini göster

- Tamamlanma listesi öğelerinin eşleşen bölümlerini vurgulama

- Tamamlanma öğesi filtrelerini göster

## <a name="snippets-behavior"></a>Kod parçacığı davranışı

- Hiç kod parçacıklarını dahil et

   Bu seçenek belirlendiğinde, IntelliSense için diğer adlar hiçbir zaman ekler C# kod parçacıkları için tamamlanma listesi.

- Her zaman kod parçacıklarını dahil et

   Bu seçenek belirlendiğinde, IntelliSense, C# kod parçacıkları için diğer adlar tamamlanma listesine ekler. Kod parçacığı diğer ad olduğu bir anahtar sözcüğü ile aynı örneğin, durumda [sınıfı](/dotnet/csharp/language-reference/keywords/class), anahtar sözcüğü kısayol tarafından değiştirilir. Daha fazla bilgi için [ C# kod parçacıkları](../../ide/visual-csharp-code-snippets.md).

- Kod parçacıkları dahil olduğunda?-bir tanımlayıcıdan sonra Tab yazılırsa

   Bu seçenek belirlendiğinde, IntelliSense için diğer adlar ekler C# kod parçacıkları için tamamlama listesinde **?** + **Sekmesini** bir tanımlayıcıdan sonra basıldığında

## <a name="enter-key-behavior"></a>Enter tuşu davranışı

- Hiçbir zaman yeni satır Ekle enter

   Yeni bir satır hiçbir zaman otomatik olarak tuşuna basarak ve tamamlanma listesine dâhil bir öğeyi seçtikten sonra eklendiğini belirtir **Enter**.

- Yalnızca yeni bir satır eklemek tam yazılmış kelimenin sonunda enter

   Tamamlama listesinde bir girişi tüm karakterler yazın ve ENTER tuşuna basın belirten **Enter**, yeni bir satır otomatik olarak eklenir ve imleç yeni satıra taşır.

   Örneğin, `else` ve tuşuna **Enter**, aşağıdaki Düzenleyicisi'nde belirir:

   `else`

   `|` (imleç konumu)

   Ancak, yalnızca yazarsanız `el` ve tuşuna **Enter**, aşağıdaki Düzenleyicisi'nde belirir:

   `else|` (imleç konumu)

- Her zaman yeni satır Ekle enter

   Yazarsanız belirten *herhangi* ENTER tuşuna basın ve tamamlanma listesini bir giriş için karakter **Enter**, yeni bir satır otomatik olarak eklenir ve imleç yeni satıra taşır.

## <a name="show-name-suggestions"></a>Adı önerileri göster

Otomatik nesne adı tamamlama, yakın zamanda seçtiğiniz üyeler için gerçekleştirir.

## <a name="see-also"></a>Ayrıca bkz.

- [Genel, Ortam, Seçenekler İletişim Kutusu](../../ide/reference/general-environment-options-dialog-box.md)
- [IntelliSense Kullanma](../../ide/using-intellisense.md)