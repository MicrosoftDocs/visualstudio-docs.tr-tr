---
title: Kodlanmış UI testleriyle SharePoint uygulamaları test etme
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: conceptual
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 91d17857f1d20508041ad6c5daa90a962d6d30e6
ms.sourcegitcommit: ae46be4a2b2b63da7e7049e9ed67cd80897c8102
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/05/2018
ms.locfileid: "52895450"
---
# <a name="test-sharepoint-applications-with-coded-ui-tests"></a>Kodlanmış UI testleriyle SharePoint uygulamaları test etme

Kodlanmış UI testleri içindeki bir SharePoint uygulaması da dahil olmak üzere, kendi kullanıcı Arabirimi denetimleri de dahil olmak üzere tüm uygulamanın düzgün çalıştığını doğrulamak olanak tanır. Kodlanmış UI testleri, değerleri ve kullanıcı arabirimi mantığı da doğrulayabilirsiniz.

Kodlanmış UI testleri kullanmanın avantajları hakkında daha fazla bilgi için bkz: [kodunuzu test etmek için kullanım UI Otomasyonu](../test/use-ui-automation-to-test-your-code.md).

[!INCLUDE [coded-ui-test-deprecation](includes/coded-ui-test-deprecation.md)]

**Gereksinimler**

- Visual Studio Enterprise

## <a name="create-a-coded-ui-test-for-a-sharepoint-app"></a>Bir SharePoint uygulaması için kodlanmış UI testi oluşturma

[Kodlanmış UI testleri oluşturma](../test/use-ui-automation-to-test-your-code.md) SharePoint uygulamalarınız için diğer uygulama türleri için testleri oluşturma ile aynıdır. Kayıt ve kayıttan yürütme desteklenir tüm denetimler için **Web'den düzenlemeyi** arabirimi. Kategorileri ve web bölümleri seçme arabirimi, tüm standart web denetimler bulunur.

![SharePoint web bölümleri](../test/media/cuit_sharepoint.png)

> [!NOTE]
> Eylem kaydı yapıyorsanız, kod oluşturmadan önce eylemleri doğrulayın. Bazı davranışları fareyle üzerine gelindiğinde ile ilişkili olduğundan, varsayılan olarak açıktır. Yedekli eklenmemesi, kodlanmış UI testlerini kaldırmak dikkatli olun. Test için kod düzenleme veya kullanarak bunu yapabilirsiniz [kodlanmış UI Test Düzenleyicisi](../test/editing-coded-ui-tests-using-the-coded-ui-test-editor.md).

## <a name="test-office-controls-within-a-sharepoint-app"></a>Bir SharePoint uygulama içinde test Office denetimleri

Bazı office web bölümleri SharePoint uygulamanızda Otomasyon etkinleştirmek için bazı küçük bir kod değişikliği yapmanız gerekir.

> [!NOTE]
> Bir SharePoint uygulamasında Visio ve PowerPoint denetimleri test desteklenmiyor.

### <a name="excel-cell-controls"></a>Excel hücre denetimleri

Excel hücre denetimleri eklemek için kodlanmış UI test kodu bazı değişiklikler yapmanız gerekir.

> [!WARNING]
> Ok anahtar eylemi tarafından izlenen herhangi bir Excel hücreyi metin girme doğru kaydetmez. Hücreleri seçmek için fare kullanın.

Boş bir hücreye eylemleri kaydediyorsanız, double hücreyi tıklayarak ve ardından kümesi metin işlemi gerçekleştirme kodu değiştirmeniz gerekir. Tüm klavye eylemi tarafından izlenen hücre click etkinleştirir çünkü bu gerekli `textarea` hücresi içinde. Yalnızca kaydı bir `setvalue` boş hücreyi aramak `editbox` tıklanan hücre kadar mevcut değil. Örneğin:

```csharp
Mouse.DoubliClick(uiItemCell,new Point(31,14));
uiGridKeyboardInputEdit.Text=value;
```

Eylemler boş olmayan hücre kaydetmekte olduğunuz sonra çünkü kaydı biraz daha karmaşık alır bir hücre için metni ekleme şu anda yeni bir \<div > denetimi hücrenin alt olarak eklenir. Yeni \<div > girdiğiniz metin denetimi içerir. Kaydedici eylemleri yeni kaydetmek gereken \<div > denetimi; ancak, çünkü olamaz yeni \<div > Denetim yok kadar test girildikten sonra. Bu sorunu uyum sağlamak için aşağıdaki kod değişikliklerini el ile yapmalısınız.

1. Hücre başlatma için gidin ve olun `RowIndex` ve `ColumnIndex` birincil özellikleri:

    ```csharp
    this.mUIItemCell.SearchProperties[HtmlCell.PropertyNames. RowIndex] = "3";
    this.mUIItemCell.SearchProperties[HtmlCell.PropertyNames. ColumnIndex] = "3";
    ```

2. Bulma `HtmlDiv` alt hücrenin:

    ```csharp
    private UITestControl getControlToDoubleClick(HtmlCell cell)
    {
         if (String.IsNullOrEmpty(cell.InnerText)) return cell;
         HtmlDiv pane = new HtmlDiv(cell);
         pane.FilterProperties[HtmlDiv.PropertyNames.InnerText] = cell.InnerText;
         // Class is an important property in finding pane
         pane.FilterProperties[HtmlDiv.PropertyNames.Class] = "cv-nwr";
         UITestControlCollection panes = pane.FindMatchingControls();
         return panes[0];
    }
    ```

3. Kod bir fare çift tıklatın için eylem ekleme `HtmlDiv`:

    ```csharp
    Mouse.DoubleClick(uIItemPane, new Point(31, 14)); )
    ```

4. Metni ayarlamak için kod ekleme `TextArea`:

    ```csharp
    uIGridKeyboardInputEdit.Text = value; }
    ``

## See also

- [Use UI automation to test your code](../test/use-ui-automation-to-test-your-code.md)
- [Create SharePoint solutions](../sharepoint/create-sharepoint-solutions.md)
- [Verify and debug SharePoint code](../sharepoint/verifying-and-debugging-sharepoint-code.md)
- [Build and debug SharePoint solutions](../sharepoint/building-and-debugging-sharepoint-solutions.md)
- [Profile the performance of SharePoint applications](../sharepoint/profiling-the-performance-of-sharepoint-applications.md)
