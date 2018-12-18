---
title: Yer işareti denetimi
ms.date: 02/02/2017
ms.technology: office-development
ms.prod: visual-studio-dev15
ms.topic: conceptual
f1_keywords:
- VST.Toolbox.Bookmark
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- bookmarks, controlling
- Bookmark control, data binding
- Bookmark control, events
- Bookmark control
author: John-Hart
ms.author: johnhart
manager: douge
ms.workload:
- office
ms.openlocfilehash: 242a4692bc75715e661244dc8f513d30cc9480ed
ms.sourcegitcommit: 20c0991d737c540750c613c380cd4cf5bb07de51
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/11/2018
ms.locfileid: "53248198"
---
# <a name="bookmark-control"></a>Yer işareti denetimi
  <xref:Microsoft.Office.Tools.Word.Bookmark> Verilere bağlı benzersiz bir ada sahip ve olayları ortaya koyan bir yer işareti bir denetimdir. Yer işareti, bir öğe veya Microsoft Office Word belgesindeki bir konumu işaretlemek için yer tutucu olarak kullanılabilir. <xref:Microsoft.Office.Tools.Word.Bookmark> Denetimi bir birleşimi olan bir <xref:Microsoft.Office.Interop.Word.Bookmark> nesnesi ve bir <xref:Microsoft.Office.Interop.Word.Range> nesne.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

 Belge düzeyinde projelerde eklediğiniz <xref:Microsoft.Office.Tools.Word.Bookmark> belgenize tasarım zamanında veya çalışma zamanında denetimler. Projelerinde, VSTO eklentisi, eklediğiniz <xref:Microsoft.Office.Tools.Word.Bookmark> herhangi bir açık belgeye çalışma zamanında denetimler. Daha fazla bilgi için [nasıl yapılır: Word belgelerine yer işareti denetimi ekleme](../vsto/how-to-add-bookmark-controls-to-word-documents.md).

## <a name="bind-data-to-the-control"></a>Veriyi denetime bağlama
 A <xref:Microsoft.Office.Tools.Word.Bookmark> basit veri bağlama denetimi destekler. Yer işareti kullanarak bir veri kaynağına bağlanması gereken <xref:System.Windows.Forms.IBindableComponent.DataBindings%2A> özelliği. Varsayılan veri bağlama özelliği yer işaretinin <xref:Microsoft.Office.Tools.Word.Bookmark.Text%2A> özelliği.

 İlişkili veri kümesindeki veriler güncelleştirilirse <xref:Microsoft.Office.Tools.Word.Bookmark> denetimi değişiklikleri gösterir.

 Belge düzeyinde projelerde Ayrıca verileri yer işaretlerine kullanarak bağlayabilirsiniz **veri kaynakları** penceresi. Daha fazla bilgi için [nasıl yapılır: Belgeleri nesne verileriyle doldurma](../vsto/how-to-populate-documents-with-data-from-objects.md).

## <a name="formatting"></a>Biçimlendirme
 Uygulanabilir biçimlendirme bir <xref:Microsoft.Office.Interop.Word.Bookmark> uygulanabilir bir <xref:Microsoft.Office.Tools.Word.Bookmark> denetimi. Bu biçimlendirme yazı tipi, girintileri, boşluk, numaralandırma ve stilleri içerir.

## <a name="assign-text-to-the-bookmark"></a>Metin ve yer işaretine atayın
 Ek bir farkı bir <xref:Microsoft.Office.Interop.Word.Bookmark?displayProperty=nameWithType> nesnesi ve bir <xref:Microsoft.Office.Tools.Word.Bookmark?displayProperty=nameWithType> denetimdir ve yer işaretine metin atandığında nasıl davrandığını. Sıfır uzunluklu metin atarsanız <xref:Microsoft.Office.Interop.Word.Bookmark?displayProperty=nameWithType>, metnin sağ tarafında yer işareti eklenir ve sıfır uzunluklu yer işareti kalır. Ancak, sıfır uzunlukta metin atarsanız <xref:Microsoft.Office.Tools.Word.Bookmark?displayProperty=nameWithType>yer işaretine eklenen metin ve toplam eklenen karakter sayısı için işaretinin uzunluğunu genişletir.

 <xref:Microsoft.Office.Tools.Word.Bookmark?displayProperty=nameWithType> Denetimi de sahip <xref:Microsoft.Office.Tools.Word.Bookmark.Text?displayProperty=nameWithType> özelliği. Bu özellik farklıdır <xref:Microsoft.Office.Interop.Word.Range.Text?displayProperty=nameWithType> kullanılabilir özellik <xref:Microsoft.Office.Tools.Word.Bookmark.Range?displayProperty=nameWithType> özelliği bir <xref:Microsoft.Office.Tools.Word.Bookmark?displayProperty=nameWithType> denetimi veya <xref:Microsoft.Office.Interop.Word.Bookmark.Range?displayProperty=nameWithType> özelliği bir <xref:Microsoft.Office.Interop.Word.Bookmark?displayProperty=nameWithType> nesne.

|Metin özelliği|Açıklama|
|-------------------|-----------------|
|<xref:Microsoft.Office.Tools.Word.Bookmark.Text?displayProperty=nameWithType>|Yer işareti içinde metin görüntülemek ve belge üzerinde yer bırakmak için bu özelliği kullanın. Metin ve yer işaretine atama yer işareti aralığı genişletir ve yer işareti silmez.<br /><br /> Örneğin, `Bookmark1.Text = "Hello world"` yer işaretine metin ekler ve yer işareti dokunmaz.|
|<xref:Microsoft.Office.Interop.Word.Range.Text?displayProperty=nameWithType>|Yer işareti konumda metin görüntülemek ve otomatik olarak yer işareti silmek için bu özelliği kullanın. Örneğin, `Bookmark1.Range.Text = "Hello world"` yer işaretine metin ekler ve yer işareti siler.|

## <a name="rename-the-control-at-design-time"></a>Tasarım zamanında denetimi yeniden adlandırma
 Belge düzeyinde projelerde sürüklediğinizde bir <xref:Microsoft.Office.Tools.Word.Bookmark> denetimi **araç kutusu** belgeniz için Visual Studio denetim için bir ad otomatik olarak oluşturur. Denetimin adını değiştirebilirsiniz **özellikleri** penceresi.

## <a name="overlapping-controls"></a>Örtüşen Denetimler
 Yer işareti denetimlerini birbirleriyle çakışmamalıdır. Aynı metni birden fazla yer işareti tarafından paylaşılabilir. Yeni metin örtüşen yer işaretlerinden birine atadığınızda, yalnızca yeni metin içeriyor ve yer işaretleri artık çakışıyor. Diğer yer işareti artık yalnızca özgün çakışan yer işaretleri arasında paylaşılan değildi metni içerir.

 Aşağıdaki tabloda nasıl cümlenin "Örnek metin sağlıyor." iki örtüşen yer işareti tarafından paylaşılan:

|Yer işareti|Metin|
|--------------|----------|
|Çakışan yer işaretleri|[{örnek olduğundan] metin.}|
|Bookmark1|Örnek budur.|
|Bookmark2|örnek metin.|

 Yeni metin atarsanız "Yerini almaktadır." Bookmark1 için yer işaretlerini çakışmadığından ve başlangıçta Bookmark1 parçası olmayan metin Bookmark2 korur.

|Yer işareti|Metin|
|--------------|----------|
|İki ayrı yer işaretleri|[yerini almaktadır] {metin.}|
|Bookmark1|Bu değişiklik|
|Bookmark2|Metin.|

Başka bir yer işareti içeren bir yer işareti metnini değiştirirseniz, iç yer silinmez. Ancak, iç yer işareti, boş bir yer işaretine dönüşür ve dış işaretinin sonuna taşır.

Aşağıdaki tabloda nasıl cümlenin "Örnek metin sağlıyor." başka bir yer işareti bulunan bir yer işareti tarafından paylaşılır:

|Yer işareti|Metin|
|--------------|----------|
|Çakışan yer işaretleri|[{örnek} metin budur.]|
|Bookmark1|Bu örnek metindir.|
|Bookmark2|örnek|

 Yeni metin atarsanız "Yerini almaktadır." Bookmark1, yer işaretleri bundan böyle çakışan ve Bookmark2 Bookmark1 sonunda bulunan boş bir yer işaretine dönüşür.

|Yer işareti|Metin|
|--------------|----------|
|İki ayrı yer işaretleri|[yerini almaktadır.]{}|
|Bookmark1|Bu, yerini almaktadır.|
|Bookmark2|*\<Boş >*|

## <a name="events"></a>Olaylar

Aşağıdakiler için kullanılabilir <xref:Microsoft.Office.Tools.Word.Bookmark> denetimi:

-   <xref:Microsoft.Office.Tools.Word.Bookmark.BeforeDoubleClick>

-   <xref:Microsoft.Office.Tools.Word.Bookmark.BeforeRightClick>

-   <xref:Microsoft.Office.Tools.Word.Bookmark.BindingContextChanged>

-   <xref:Microsoft.Office.Tools.Word.Bookmark.Deselected>

-   <xref:System.ComponentModel.IComponent.Disposed>

-   <xref:Microsoft.Office.Tools.Word.Bookmark.Selected>

-   <xref:Microsoft.Office.Tools.Word.Bookmark.SelectionChange>

## <a name="see-also"></a>Ayrıca bkz.

- [Genişletilmiş nesneleri kullanarak Word'ü otomatikleştirirken](../vsto/automating-word-by-using-extended-objects.md)
- [Nasıl yapılır: Word belgelerine yer işareti denetimi ekleme](../vsto/how-to-add-bookmark-controls-to-word-documents.md)
- [İzlenecek yol: Yer işaretleri için kısayol menüleri oluşturma](../vsto/walkthrough-creating-shortcut-menus-for-bookmarks.md)
- [Office çözümlerinde denetimlere veri bağlama](../vsto/binding-data-to-controls-in-office-solutions.md)
- [Konak denetimlerinin ve konak öğelerinin programlama sınırlamaları](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)