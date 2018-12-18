---
title: Özet tanımı kullanma
ms.date: 01/10/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 518256c550f56832c6711ab6d2ca2dae4eb0aa2c
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53059658"
---
# <a name="how-to-view-and-edit-code-by-using-peek-definition-altf12"></a>Nasıl yapılır: Özet tanım (Alt + F12) kullanarak kodu görüntüleme ve düzenleme

Kullanabileceğiniz **Özet tanım** görüntülemek ve kod yazdığınız uzaklaşmadan kod tanımlarını düzenlemek için komutu. **Özet tanım** ve **tanıma** aynı bilgileri gösterir ancak **Özet tanım** bir açılır pencerede gösterir ve **tanıma** gösterir ayrı bir kod penceresinde kodu. **Tanıma Git** tanım kodu penceresine geçilmesine, bağlamınızın (yani, etkin kod penceresi, geçerli satır ve imleç konumu) neden olur. Kullanarak **Özet tanım**, görüntüleyebilir ve tanımını düzenleyin ve orijinal kod dosyasında yerinizi tutarken tanım dosyası içinde gezinebilirsiniz.

Kullanabileceğiniz **Özet tanım** C#, Visual Basic ve C++ koduna sahip. Visual Basic'te **Özet tanım** bir bağlantısı gösterir **Nesne Tarayıcısı** tanım meta verileri (yerleşik olarak bulunan Örneğin, .NET Framework türleri) olmayan simgeler için.

## <a name="working-with-peek-definition"></a>Özet Tanım ile Çalışma

### <a name="to-open-a-peek-definition-window"></a>Bir Özet Tanım penceresi açmak için

1. Seçerek bir tanıma göz atma **Özet tanımı** için keşfetmek istediğiniz bir türü veya bağlam menüsünden. Seçeneği etkinleştirilirse, Visual Studio 2017 sürüm 15.4 ve üzeri, ayrıca fare tuşuna basarak kullanarak bir Özet tanım **Ctrl** (veya başka bir değiştirici) ve üye adına tıklayarak. Veya, klavyeden basın **Alt**+**F12**.

     Bu resimde **Özet tanım** adlı bir yöntem için pencere `Print()`:

     ![Penceresinde göz at](../ide/media/peekwindow.png)

     Tanım penceresinin altında görünür `printer.Print("Hello World!")` özgün dosyadaki bir satır. Pencerede, özgün dosyanızdaki kodlardan hiçbiri gizlenmez. Gelen satırlar `printer.Print("Hello World!")` tanım penceresinin altında görünür.

1. İmleç, Özet tanımı penceresinde farklı konumlara taşıyabilirsiniz. Özgün kod penceresinde yine de taşıyabilirsiniz.

1. Dizeyi tanım penceresinden kopyalayıp özgün koda yapıştırabilirsiniz. Dizeyi tanım penceresinden sürükleyip özgün koda da bırakabilirsiniz (tanım penceresinden silinmeden).

1. Seçerek tanım penceresini kapatabilirsiniz **Esc** anahtarı veya **kapatmak** tanım penceresi sekmesindeki düğmesi.

### <a name="open-a-peek-definition-window-from-within-a-peek-definition-window"></a>Bir Özet tanım penceresinin içinden Özet tanım penceresini açın

Zaten bir **Özet tanım** pencereniz açıksa çağırabilirsiniz **Özet tanım** Bu penceredeki kod üzerinde yeniden. Başka bir tanım penceresi açılır. Tanım penceresi sekmesinin yanında, tanım pencereleri arasında gezinmek için kullanabileceğiniz bir dizi içerik haritası noktası görünür. Her bir noktadaki araç ipucu, noktanın temsil ettiği tanım dosyasının dosya adını ve yolunu gösterir.

   ![Pencere bir Özet penceresi içinde Ara](../ide/media/peekwithinpeek.png)

### <a name="peek-definition-with-multiple-results"></a>Özet tanım ile birden çok sonuç

Kullanırsanız **Özet tanım** (örneğin, kısmi bir sınıf) birden fazla tanıma sahip kod üzerinde kod tanımı görünümünün sağında bir sonuç listesi görünür. Listede istediğiniz sonucu seçerek tanımını görüntüleyebilirsiniz.

   ![Birden çok sonuç penceresinde göz at](../ide/media/peekmultiple.png)

### <a name="edit-inside-the-peek-definition-window"></a>Özet tanım penceresinin içinde düzenlemek

İçinde düzenleme yapmaya başladığınızda bir **Özet tanım** penceresinde otomatik olarak değişiklik yaptığınız dosya olarak Kod Düzenleyicisi içinde ayrı bir sekmede açılır ve yapmış olduğunuz değişiklikleri yansıtır. Yapabilir, Geri Al ve kaydetmeye devam edebilirsiniz **Özet tanım** penceresi ve sekme bu değişiklikleri yansıtacak şekilde sürdürür. Siz kapatana bile **Özet tanım** penceresinde, değişikliklerinizi kaydetmeden, yapın, geri alma ve daha fazla değişiklik sekmesinde, tam olarak kaldığınız yerden yukarı çekme kaydedin **Özet tanım** penceresi.

   ![Bir Özet penceresi içinde düzenleme](../ide/media/peekedit.png)

### <a name="to-change-options-for-peek-definition"></a>Özet tanım seçeneklerini değiştirmek için

1. Git **Araçları** > **seçenekleri** > **metin düzenleyici** > **genel**.

1. Seçeneğini **tanımı Özet Görünümü'nde açın**.

1. Tıklayın **Tamam** kapatmak için **seçenekleri** iletişim kutusu.

   ![Fare tıklatın gözlem tanım seçeneği ayarlama](../ide/media/editor_options_peek_view.png)

### <a name="keyboard-shortcuts-for-peek-definition"></a>Özet tanım klavye kısayolları

Bu klavye kısayollarını kullanabilirsiniz **Özet tanım** penceresi:

|İşlevi|Klavye kısayolu|
|-------------------|:-----------------------:|
|Tanım penceresini açma|**Alt**+**F12**|
|Tanım penceresini kapatma|**ESC**|
|Tanım penceresini bir normal belge sekmesine yükseltme|**Shift**+**Alt**+**giriş**|
|Tanım pencereleri arasında gezinme|**CTRL**+**Alt** + **-** ve **Ctrl**+**Alt**+**=**|
|Birden fazla sonuç arasında gezinme|**F8** ve **Shift**+**F8**|
|Kod düzenleyicisi penceresi ile tanım penceresi arasında geçiş yapma|**Shift**+**Esc**|

> [!NOTE]
> Kodu düzenleme için aynı klavye kısayollarını kullanabilirsiniz bir **Özet tanım** aynı pencereyi kullanırsınız başka bir yerde Visual Studio'da.

## <a name="see-also"></a>Ayrıca bkz.

- [Kod gidin](../ide/navigating-code.md)
- [Tanıma ve Özet Tanıma Gitme](../ide/go-to-and-peek-definition.md)
- [Üretkenlik ipuçları](../ide/productivity-tips-for-visual-studio.md)