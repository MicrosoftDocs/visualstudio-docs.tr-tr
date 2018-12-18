---
title: C#kod parçacıkları
ms.date: 06/05/2017
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- snippets [C#]
- code snippets [C#]
- Code Snippet Inserter [C#]
- C#, code snippets
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: feec485f752ac13b43310e4afd97bdfaac93ee51
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49849170"
---
# <a name="c-code-snippets"></a>C#kod parçacıkları

Kod parçacıkları, kullanıma hazır, kodunuza hızla ekleyebilirsiniz kod parçacıkları verilmiştir. Örneğin, `for` oluşturur boş bir kod parçacığı `for` döngü. Bazı kod parçacıklarına, kod satırları seçmek etkinleştirmeniz ve sonra seçilen kod satırlarını içeren bir kod parçacığı surround-with kod parçacıkları, verilmiştir. Örneğin, ne zaman isterseniz kod satırlarını seçip ardından etkinleştirmek `for` kod parçacığı, oluşturur bir `for` Bu döngü bloğu içinde kod satırlarını içeren döngü. Kod parçacıkları kod yazma programını daha hızlı, kolay ve daha güvenilir hale getirebilirsiniz.

 İmleç konumuna bir kod parçacığı Ekle ya da şu anda seçili olan kod etrafında surround-with kod parçacığını ekleyin. Kod parçacığı ekleyici aracılığıyla çağrılan **kod parçacığı Ekle** veya **Surround With** komutlarını **IntelliSense** menüsünden veya klavyekısayollarınıkullanarak **CTRL**+**K**,**X** veya **Ctrl**+**K**,**S** sırasıyla.

 **Kod parçacığı ekleyici** tüm kullanılabilir kod parçacıkları için kod parçacığı adını görüntüler. Kod parçacığı ekleyici kod parçacığı veya bir kod parçacığı adı kısmını adını girebileceğiniz bir giriş iletişim kutusu da içerir. Kod parçacığı ekleyici en yakın eşleşme için kod parçacığı adı vurgulanır. Tuşuna basarak **sekmesini** herhangi bir zamanda kod parçacığı ekleyici kapatmak ve şu anda seçili kod parçacığını ekleyin. Tuşuna basarak **Esc** veya Kod düzenleyicisinde fareyle tıklamak Kapat kod parçacığı ekleyici bir kod parçacığı eklemeden.

## <a name="default-code-snippets"></a>Varsayılan kod parçacıkları

Varsayılan olarak, aşağıdaki kod parçacıkları için Visual Studio'da bulunan C#.

|Adı (veya kısayol)|Açıklama|Kod parçacığını eklemek için geçerli konumları|
| - |-----------------| - |
|#if|Oluşturur bir [#if](/dotnet/csharp/language-reference/preprocessor-directives/preprocessor-if) yönergesi ve [#endif](/dotnet/csharp/language-reference/preprocessor-directives/preprocessor-endif) yönergesi.|Herhangi bir yerde.|
|#region|Oluşturur bir [#region](/dotnet/csharp/language-reference/preprocessor-directives/preprocessor-region) yönergesi ve [#endregion](/dotnet/csharp/language-reference/preprocessor-directives/preprocessor-endregion) yönergesi.|Herhangi bir yerde.|
|~|Oluşturur bir [Sonlandırıcı](/dotnet/csharp/programming-guide/classes-and-structs/destructors) (yok edici) içeren sınıf.|Bir sınıf içinde.|
|özniteliği|Türetilen bir sınıf için bir bildirim oluşturur <xref:System.Attribute>.|Bir ad alanı (genel ad alanı dahil), bir sınıf veya yapı içinde.|
|checked|Oluşturur bir [işaretli](/dotnet/csharp/language-reference/keywords/checked) blok.|Bir yöntemi, bir dizin oluşturucu, bir özellik erişimcisi veya bir olay erişimcisi içinde.|
|sınıf|Bir sınıf bildirimi oluşturur.|Bir ad alanı (genel ad alanı dahil), bir sınıf veya yapı içinde.|
|ctor|Kapsayan sınıfı için bir oluşturucu oluşturur.|Bir sınıf içinde.|
|cw|Bir çağrı oluşturur <xref:System.Console.WriteLine%2A>.|Bir yöntemi, bir dizin oluşturucu, bir özellik erişimcisi veya bir olay erişimcisi içinde.|
|do|Oluşturur bir [yapmak](/dotnet/csharp/language-reference/keywords/do) `while` döngü.|Bir yöntemi, bir dizin oluşturucu, bir özellik erişimcisi veya bir olay erişimcisi içinde.|
|else|Oluşturur bir [başka](/dotnet/csharp/language-reference/keywords/if-else) blok.|Bir yöntemi, bir dizin oluşturucu, bir özellik erişimcisi veya bir olay erişimcisi içinde.|
|enum|Oluşturur bir [enum](/dotnet/csharp/language-reference/keywords/enum) bildirimi.|Bir ad alanı (genel ad alanı dahil), bir sınıf veya yapı içinde.|
|eşittir|Geçersiz kılan bir yöntem bildiriminde oluşturur <xref:System.Object.Equals%2A> içinde tanımlanan yöntem <xref:System.Object> sınıfı.|Bir sınıf veya yapı içinde.|
|özel durum|Bir özel durumdan türetilen bir sınıf için bir bildirim oluşturur (<xref:System.Exception> varsayılan olarak).|Bir ad alanı (genel ad alanı dahil), bir sınıf veya yapı içinde.|
|for|Oluşturur bir [için](/dotnet/csharp/language-reference/keywords/for) döngü.|Bir yöntemi, bir dizin oluşturucu, bir özellik erişimcisi veya bir olay erişimcisi içinde.|
|foreach|Oluşturur bir [foreach](/dotnet/csharp/language-reference/keywords/foreach-in) döngü.|Bir yöntemi, bir dizin oluşturucu, bir özellik erişimcisi veya bir olay erişimcisi içinde.|
|forr|Oluşturur bir [için](/dotnet/csharp/language-reference/keywords/for) bu azaltır, her yinelemeden sonra Döngü değişkeninin döngü.|Bir yöntemi, bir dizin oluşturucu, bir özellik erişimcisi veya bir olay erişimcisi içinde.|
|if|Oluşturur bir [varsa](/dotnet/csharp/language-reference/keywords/if-else) blok.|Bir yöntemi, bir dizin oluşturucu, bir özellik erişimcisi veya bir olay erişimcisi içinde.|
|Dizin Oluşturucu|Bir dizin oluşturucu bildirimi oluşturur.|Bir sınıf veya yapı içinde.|
|arabirim|Oluşturur bir [arabirimi](/dotnet/csharp/language-reference/keywords/interface) bildirimi.|Bir ad alanı (genel ad alanı dahil), bir sınıf veya yapı içinde.|
|çağırma|Bir olay güvenli bir şekilde çağıran bir blok oluşturur.|Bir yöntemi, bir dizin oluşturucu, bir özellik erişimcisi veya bir olay erişimcisi içinde.|
|iterator|Bir yineleyici oluşturur.|Bir sınıf veya yapı içinde.|
|iterindex|İç içe geçmiş bir sınıf kullanarak "adlı" bir yineleyici ve dizin oluşturucu çifti oluşturur.|Bir sınıf veya yapı içinde.|
|lock|Oluşturur bir [kilit](/dotnet/csharp/language-reference/keywords/lock-statement) blok.|Bir yöntemi, bir dizin oluşturucu, bir özellik erişimcisi veya bir olay erişimcisi içinde.|
|mbox|Bir çağrı oluşturur <xref:System.Windows.Forms.MessageBox.Show%2A?displayProperty=fullName>. Bir başvuru eklemeniz gerekebilir *System.Windows.Forms.dll*.|Bir yöntemi, bir dizin oluşturucu, bir özellik erişimcisi veya bir olay erişimcisi içinde.|
|ad alanı|Oluşturur bir [ad alanı](/dotnet/csharp/language-reference/keywords/namespace) bildirimi.|(Genel ad alanı dahil) bir ad alanı içinde.|
|prop|Oluşturur bir [otomatik uygulanan özellik](/dotnet/csharp/programming-guide/classes-and-structs/auto-implemented-properties) bildirimi.|Bir sınıf veya yapı içinde.|
|propfull|Bir özellik bildirimi ile oluşturur `get` ve `set` erişimcileri.|Bir sınıf veya yapı içinde.|
|propg|Salt okunur oluşturur [otomatik uygulanan özellik](/dotnet/csharp/programming-guide/classes-and-structs/auto-implemented-properties) özel ile `set` erişimcisi.|Bir sınıf veya yapı içinde.|
|SIM|Oluşturur bir [statik](/dotnet/csharp/language-reference/keywords/static) [int](/dotnet/csharp/language-reference/keywords/int) ana yöntem bildirimi.|Bir sınıf veya yapı içinde.|
|struct |Oluşturur bir [yapı](/dotnet/csharp/language-reference/keywords/struct) bildirimi.|Bir ad alanı (genel ad alanı dahil), bir sınıf veya yapı içinde.|
|svm|Oluşturur bir [statik](/dotnet/csharp/language-reference/keywords/static) [void](/dotnet/csharp/language-reference/keywords/void) ana yöntem bildirimi.|Bir sınıf veya yapı içinde.|
|anahtarı|Oluşturur bir [geçiş](/dotnet/csharp/language-reference/keywords/switch) blok.|Bir yöntemi, bir dizin oluşturucu, bir özellik erişimcisi veya bir olay erişimcisi içinde.|
|deneyin|Oluşturur bir [try-catch](/dotnet/csharp/language-reference/keywords/try-catch) blok.|Bir yöntemi, bir dizin oluşturucu, bir özellik erişimcisi veya bir olay erişimcisi içinde.|
|tryf|Oluşturur bir [try-finally](/dotnet/csharp/language-reference/keywords/try-finally) blok.|Bir yöntemi, bir dizin oluşturucu, bir özellik erişimcisi veya bir olay erişimcisi içinde.|
|unchecked|Oluşturur bir [denetlenmeyen](/dotnet/csharp/language-reference/keywords/unchecked) blok.|Bir yöntemi, bir dizin oluşturucu, bir özellik erişimcisi veya bir olay erişimcisi içinde.|
|unsafe|Oluşturur bir [güvenli](/dotnet/csharp/language-reference/keywords/unsafe) blok.|Bir yöntemi, bir dizin oluşturucu, bir özellik erişimcisi veya bir olay erişimcisi içinde.|
|kullanma|Oluşturur bir [kullanarak](/dotnet/csharp/language-reference/keywords/using-directive) yönergesi.|(Genel ad alanı dahil) bir ad alanı içinde.|
|while|Oluşturur bir [sırada](/dotnet/csharp/language-reference/keywords/while) döngü.|Bir yöntemi, bir dizin oluşturucu, bir özellik erişimcisi veya bir olay erişimcisi içinde.|

## <a name="see-also"></a>Ayrıca bkz.

- [Kod parçacığı işlevleri](../ide/code-snippet-functions.md)
- [Kod parçacıkları](../ide/code-snippets.md)
- [Şablon parametreleri](../ide/template-parameters.md)
- [Nasıl yapılır: surround-with kod parçacıklarını kullanma](../ide/how-to-use-surround-with-code-snippets.md)