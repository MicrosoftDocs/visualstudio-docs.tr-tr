---
title: 'Nasıl Yapılır: Oluşturma ve çalıştırma LinqToXmlDataBinding örneği'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-designers
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 67d8bc9ece20867e96f0ae0ee6d6ceb9ad2e3952
ms.sourcegitcommit: 0cdd8e8a53fb4fd5e869f07c35204419fa12783d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53159782"
---
# <a name="how-to-build-and-run-the-linqtoxmldatabinding-example"></a>Nasıl Yapılır: LinqToXmlDataBinding oluşturma ve çalıştırma örneği

Bu konu nasıl oluşturulup LinqToXmlDataBinding Visual Studio projeyi oluşturun ve elde edilen LinqToXmlDataBinding Windows Presentation Foundation (WPF) örnek program çalıştırma gösterir.

Visual Studio hakkında daha fazla bilgi için bkz. [Visual Studio IDE'ye genel bakış](../get-started/visual-studio-ide.md).

## <a name="create-and-populate-the-project"></a>Oluşturma ve proje doldurma

### <a name="to-create-the-starting-project"></a>Başlangıç projesi oluşturmak için

1. Visual Studio'yu başlatın ve LinqToXmlDataBinding adlı bir C# WPF uygulaması oluşturun. Proje .NET Framework 3.5 (veya sonraki sürümler) kullanmanız gerekir.

1. Aksi halde aşağıdaki .NET derlemeleri için zaten mevcut proje başvurularını ekleyin:

    - System.Data

    - System.Data.DataSetExtensions

    - System.Xml

    - System.Xml.Linq

1. Basarak çözümü oluşturun **Ctrl**+**Shift**+**B**, çalıştırın tuşlarına basarak **F5**. Projenin hatasız derleyip genel WPF uygulaması çalıştırın.

### <a name="to-add-custom-code-to-the-project"></a>Özel kod projesine eklemek için

1. Çözüm Gezgini içinde kaynak dosyayı yeniden adlandırın **gt;Window1.XAML** için **L2XDBForm.xaml**. Bağımlı kaynak dosyası **Window1.xaml.cs** için otomatik olarak adlandırılmamalıdır **L2XDBForm.xaml.cs**.

1. Kaynak kodu dosyasında bulunan Değiştir **L2XDBForm.xaml** konusunun kod ile [L2DBForm.xaml kaynak kodu](../designers/l2dbform-xaml-source-code.md). Bu dosyayla çalışmak için XAML kaynak görünümünü kullanın.

1. Benzer şekilde, kaynak değiştirin **L2XDBForm.xaml.cs** bulunan kodla [L2DBForm.xaml.cs kaynak kodu](../designers/l2dbform-xaml-cs-source-code.md).

1. Dosyasındaki **App.xaml**, dizenin tüm oluşumları değiştirmek `Window1.xaml` ile `L2XDBForm.xaml`.

1. **Ctrl**+**Shift**+**B** tuşlarına basarak çözümü oluşturun.

## <a name="run-the-program"></a>Programı çalıştırma

LinqToXmlDataBinding program görüntülemek ve gömülü bir XML öğesi olarak depolanan kitap listesi işlemek kullanıcının sağlar.

### <a name="to-run-the-program-and-view-the-book-list"></a>Programı çalıştırın ve kitap listesi görüntülemek için

- LinqToXmlDataBinding basarak çalıştırın **F5** (**hata ayıklamayı Başlat**) veya **Ctrl**+**F5** (**Başlat Hata ayıklama olmadan**).

   Başlık program penceresiyle **LINQ to XML kullanarak WPF verilerini bağlama** görünür.

- Dosyanın üst kısmında ham görüntüler UI fark **XML** temsil eden kitap listesi. WPF kullanarak görüntülenir <xref:System.Windows.Controls.TextBlock> denetimi, klavye ve fare aracılığıyla etkileşim etkinleştirmez.

- Etiketli ikinci dikey bölümde **kitap listesi**, görüntüler books düz metin olarak sıralı listesi. Bunu kullanan bir <xref:System.Windows.Controls.ListBox> klavye ve fare seçimi ancak etkinleştiren denetimi.

### <a name="to-add-and-delete-books-from-the-list"></a>Ekleme ve Kitaplar listeden silme

- Yeni bir kitap listeye eklemek için değerlerini girin. **kimliği** ve **değeri** <xref:System.Windows.Controls.TextBox> son bölümüne denetimler **yeni kitabı ekleme**,'a tıklayın **Ekle Kitap** düğmesi. Not Defteri kitap ve XML listelerini listesine eklenir. Bu program, giriş değerleri doğrulamaz.

- Mevcut bir kitap listeden silmek için onu seçip **kitap listesi** bölümünde'a tıklayın **seçili kitap kaldırmak** düğmesi. Kitap hem ham XML kaynak listelerini defteri girdisi kaldırıldı dikkat edin.

### <a name="to-edit-an-existing-book-entry"></a>Bir kitap girişi düzenlemek için

1. İkinci defteri girdisini seçin **kitap listesi** bölümü. Geçerli değerleri üçüncü bölümünde görüntülenip **seçili kitap Düzenle**.

1. Klavyeyi kullanarak değerleri düzenleyin. Kapanmaz <xref:System.Windows.Controls.TextBox> denetim odağı kaybettiğinde, değişiklikleri otomatik olarak XML kaynak ve kitap listelerini yayılır.

## <a name="see-also"></a>Ayrıca bkz.

- [LINQ, XML örneği kullanarak WPF verilerini bağlama](../designers/wpf-data-binding-using-linq-to-xml-example.md)
- [İzlenecek yol: LinqToXmlDataBinding örneği](../designers/walkthrough-linqtoxmldatabinding-example.md)
- [Visual Studio IDE'ye genel bakış](../get-started/visual-studio-ide.md)