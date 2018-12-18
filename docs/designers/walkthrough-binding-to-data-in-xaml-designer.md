---
title: XAML Tasarımcısı'nda verileri bağlama
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-designers
ms.topic: conceptual
f1_keywords:
- VS.XamlDesigner.DataBinding
dev_langs:
- CSharp
- VB
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- uwp
ms.openlocfilehash: f1effd15666839b6e48bcebf46120585c4cfc36c
ms.sourcegitcommit: 1ab675a872848c81a44d6b4bd3a49958fe673c56
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2018
ms.locfileid: "44282891"
---
# <a name="walkthrough-bind-to-data-in-xaml-designer"></a>İzlenecek yol: XAML Tasarımcısı’nda verilere bağlama

XAML Tasarımcısı'nda, çalışma yüzeyine ve Özellikler penceresini kullanarak veri bağlama özellikleri ayarlayabilirsiniz. Bu kılavuzda örnek veriyi denetime bağlama gösterilmektedir. Özellikle, gözden geçirme sahip basit bir alışveriş sepeti sınıfı oluşturma işlemini gösterir ve bir [DependencyProperty](/uwp/api/Windows.UI.Xaml.DependencyProperty) adlı `ItemCount`ve ardından `ItemCount` özelliğini **metin** özelliği bir [TextBlock](/uwp/api/Windows.UI.Xaml.Controls.TextBlock) denetimi.

## <a name="to-create-a-class-to-use-as-a-data-source"></a>Veri kaynağı olarak kullanılacak bir sınıf oluşturmak için

1. Üzerinde **dosya** menüsünde seçin **yeni** > **proje**.

1. İçinde **yeni proje** iletişim kutusunda, ya da **Visual C#** veya **Visual Basic** düğümünü genişletin **Windows Masaüstü** düğümünü ve ardından seçin **WPF uygulaması** şablonu.

1. Projeyi adlandırın **BindingTest**ve ardından **Tamam** düğmesi.

1. Açık **MainWindow.xaml.cs** (veya **MainWindow.xaml.vb**) dosya ve aşağıdaki kodu ekleyin. C# kodu ekleyin `BindingTest` ad alanı (önce dosyanın son kapatma parantezi). Visual Basic'te, yalnızca yeni bir sınıf ekleyin.

   ```csharp
   public class ShoppingCart : DependencyObject
   {
       public int ItemCount
       {
           get { return (int)GetValue(ItemCountProperty); }
           set { SetValue(ItemCountProperty, value); }
       }

       public static readonly DependencyProperty ItemCountProperty =
            DependencyProperty.Register("ItemCount", typeof(int),
            typeof(ShoppingCart), new PropertyMetadata(0));
   }
   ```

   ```vb
   Public Class ShoppingCart
       Inherits DependencyObject

       Public Shared ReadOnly ItemCountProperty As DependencyProperty = DependencyProperty.Register(
            "ItemCount", GetType(Integer), GetType(ShoppingCart), New PropertyMetadata(0))
       Public Property ItemCount As Integer
           Get
               ItemCount = CType(GetValue(ItemCountProperty), Integer)
           End Get
           Set(value As Integer)
               SetValue(ItemCountProperty, value)
           End Set
       End Property
   End Class
   ```

   Bu kod, kullanarak varsayılan öğe sayısı 0 değerini ayarlar [PropertyMetadata](/uwp/api/Windows.UI.Xaml.PropertyMetadata) nesne.

1. Üzerinde **dosya** menüsünde seçin **derleme** > **Çözümü Derle**.

## <a name="to-bind-the-itemcount-property-to-a-textblock-control"></a>Bir TextBlock denetimi ItemCount özelliği bağlamak için

1. Çözüm Gezgini içinde kısayol menüsünü açın **MainWindow.xaml** ve **Görünüm Tasarımcısı**.

1. Araç kutusunda seçin bir [kılavuz](/uwp/api/Windows.UI.Xaml.Controls.Grid) denetlemek ve forma ekleyin.

1. İle `Grid` seçiliyken, Özellikler penceresinde **yeni** düğmesinin yanındaki **DataContext** özelliği.

1. İçinde **Nesne Seç** iletişim kutusunda, emin **tüm derlemeleri Göster** onay kutusu işaretli değilse, seçin **ShoppingCart** altında **BindingTest** ad alanını seçip **Tamam** düğmesi.

     Aşağıdaki çizimde gösterildiği **Nesne Seç** iletişim kutusuyla **ShoppingCart** seçili.

     ![Nesne Seç](../designers/media/blendselectobject.png)

1. İçinde **araç kutusu**, seçin bir `TextBlock` eklemek için form denetimi.

1. İle `TextBlock` denetimi, Özellikler penceresinde, seçili özellik işaretçisi sağındaki seçin **metin** özelliği ve ardından **veri bağlama oluşturun**. (Özellik işaretçisi küçük bir kutu gibi görünüyor.)

1. İletişim kutusu, bağlama Oluştur Veri **yolu** kutusunda **ItemCount: (int32)** özelliği seçip **Tamam** düğmesi.

     Aşağıdaki çizimde gösterildiği **veri bağlama oluşturun** iletişim kutusuyla **ItemCount** seçili özellik.

     ![Oluştur iletişim kutusu veri bağlama](../designers/media/xaml_create_data_binding.png)

1. Tuşuna **F5** uygulamayı çalıştırmak için.

     `TextBlock` Denetim 0 varsayılan değerini metin olarak göstermelidir.

## <a name="see-also"></a>Ayrıca bkz.

- [XAML Tasarımcısı’nı kullanarak bir kullanıcı arabirimi oluşturma](../designers/creating-a-ui-by-using-xaml-designer-in-visual-studio.md)
- [Değer dönüştürücüsü iletişim kutusu Ekle](https://msdn.microsoft.com/library/c5f3d110-a541-4b55-8bca-928f77778af8)