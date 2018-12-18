---
title: Kod parçacıkları
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.ExpansionManagerImport
- vs.codesnippetmanager
helpviewer_keywords:
- surround with
- code snippets
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CSharp
- VB
- CPP
ms.workload:
- multiple
ms.openlocfilehash: 8ed3f2f8e588aa908827516fee44c1a38ad6a008
ms.sourcegitcommit: bc43970c000f07c9cc2051f1264a9742943a9755
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/09/2018
ms.locfileid: "51348493"
---
# <a name="code-snippets"></a>Kod parçacıkları

Küçük bir bağlam menüsü komutu veya bir birleşimini bir kısayol tuşlarını kullanarak bir kod dosyasında eklenebilen yeniden kullanılabilir kod bloklarını kod parçacıkları verilmiştir. Genellikle gibi yaygın olarak kullanılan kod blokları içerdikleri `try-finally` veya `if-else` blokları, ancak tüm sınıfları veya yöntemleri eklemek için kullanılabilir.

> [!NOTE]
> Bu konu, Windows üzerinde Visual Studio için geçerlidir. Mac için Visual Studio için bkz: [kod parçacıkları (Mac için Visual Studio)](/visualstudio/mac/snippets).

Kod parçacıkları gibi diller için çok sayıda kullanılabilir C#, C++, Visual Basic, XML ve T-SQL, birkaçıdır. Tüm kullanılabilir yüklü kod parçacıklarının bir dil için görmek için **kod parçacıkları Yöneticisi** gelen **Araçları** Visual Studio'da, menü ve üstteki açılan menüden dili seçin.

![Kod parçacıkları Yöneticisi iletişim kutusu](media/code-snippets-manager.png)

Kod parçacıkları, aşağıdaki genel yöntemlerle erişilebilir:

- Menü çubuğunda, **Düzenle** > **IntelliSense** > **kod parçacığı Ekle**

- Kod Düzenleyicisi'nde sağ tıklayın veya bağlam menüsünden seçin **kod parçacığı** > **kod parçacığı Ekle**

- Klavyeden basın **Ctrl**+**K**+**X**

## <a name="expansion-snippets-and-surround-with-snippets"></a>Genişletme kod parçacıkları ve surround-with kod parçacıkları

Visual Studio'da kod parçacığı, iki tür vardır: Belirtilen ekleme noktasına eklenir ve bir kod parçacığı kısayol değiştirebilir, genişletme kod parçacıkları ve seçilen bir kod bloğu içine eklenen surround-with kod parçacıkları (C# ve C++ yalnızca).

Bir genişletme kod parçacığı örneği: içinde C# kısayol tryf bir try-finally bloğu eklemek için kullanılır:

```csharp
try
{

}
finally
{

}
```

Tıklayarak, bu kod parçacığı ekleyebilirsiniz **parçacık Ekle** kod penceresinin bağlam menüsünde **Visual C#** , yazın `tryf`ve tuşuna **sekmesini**. Ya da yazabilirsiniz `tryf` basın **sekmesini** iki kez.

Surround-with kod parçacığı örneği: c++ kısayol `if` ekleme parçacığı veya bir surround-with kod parçacığı olarak kullanılabilir. Bir kod satırı seçerseniz (örneğin `return FALSE;`) ve ardından **Surround With** > **varsa**, kod parçacığı çizgiyi genişletilir:

```cpp
if (true)
{
    return FALSE;
}
```

## <a name="snippet-replacement-parameters"></a>Kod parçacığı değiştirme parametreleri

Kod parçacıkları, yazmakta olduğunuz kesin kod uyacak şekilde değiştirmeniz gereken yer tutucular olan değiştirme parametreleri içerebilir. Önceki örnekte `true` uygun koşulu ile değiştirirsiniz değiştirme parametresi. Yaptığınız değişiklik, kod parçacığında aynı değiştirme parametresinin her örneği için tekrarlanır.

Örneğin, Visual Basic'te bir özellik ekleyen bir kod parçacığı yoktur. Kod parçacığını eklemek için seçin **kod parçacığı** > **parçacık Ekle** sağ tıklayın veya bağlam menüsünde bulunan bir Visual Basic kod dosyası. Ardından, **kod desenleri** > **özellikler, yordamlar, olaylar** > **bir özellik tanımlayın**.

![Tanımla bir özellik için kod parçacığı menüsü](media/code-snippets-vb-property.png)

Aşağıdaki kodu eklenir:

```vb
Private newPropertyValue As String
Public Property NewProperty() As String
    Get
        Return newPropertyValue
    End Get
    Set(ByVal value As String)
        newPropertyValue = value
    End Set
End Property
```

Değiştirirseniz `newPropertyValue` için `m_property`, ardından her örneğini `newPropertyValue` değiştirilir. Değiştirirseniz `String` için `Int` özellik bildiriminde sonra küme yöntemini değeri de değiştirilecek `Int`.

## <a name="see-also"></a>Ayrıca bkz.

- [İzlenecek yol: kod parçacığı oluşturma](../ide/walkthrough-creating-a-code-snippet.md)
- [Nasıl yapılır: kod parçacıklarını dağıtma](../ide/how-to-distribute-code-snippets.md)
- [Kod parçacıkları için en iyi uygulamalar](../ide/best-practices-for-using-code-snippets.md)
- [Kod parçacıklarının sorunlarını giderme](../ide/troubleshooting-snippets.md)
- [C#kod parçacıkları](../ide/visual-csharp-code-snippets.md)
- [Visual C++ kod parçacıkları](../ide/visual-cpp-code-snippets.md)
- [Kod parçacıkları şema başvurusu](../ide/code-snippets-schema-reference.md)
- [Kod parçacıkları (Mac için Visual Studio)](/visualstudio/mac/snippets)