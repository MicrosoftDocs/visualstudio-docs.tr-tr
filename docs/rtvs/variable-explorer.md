---
title: R için değişken Gezgini
description: Değişken Gezgini Visual Studio'da tüm değişkenleri belirli bir kapsamda geçerli R oturumda gösterir.
ms.date: 01/24/2018
ms.prod: visual-studio-dev15
ms.technology: vs-rtvs
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: douge
ms.workload:
- data-science
ms.openlocfilehash: fbd20c362c407148262d8e1e61e15d22d9cbcf2f
ms.sourcegitcommit: e5a382de633156b85b292f35e3d740f817715d47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/12/2018
ms.locfileid: "38978131"
---
# <a name="variable-explorer"></a>Değişken Gezgini

**Değişken Gezgini** kullanılarak açılır penceresinde **R Araçları** > **Windows** > **değişken Gezgini** (veya **Ctrl**+**8** kullandıysanız **R Araçları** > **veri bilimi ayarları**), tüm gösterir Geçerli R oturumdaki belirli bir kapsamda değişkenler. Örneğin, açarsanız **değişken Gezgini** aşağıdaki satırları girin [etkileşimli pencere](interactive-repl-for-r-in-visual-studio.md):

```R
x <- 42
y <- 43
n <- c(1,2,3,5,8,13)
```

**Değişken Gezgini** penceresi sonra şu şekilde görünür:

![Visual Studio'daki değişken Gezgini](media/variable-explorer-window.png)

Oturumda tanımlanan daha karmaşık bir R veri çerçevesine varsa, verileri gidebilirsiniz. Örneğin, çalıştırdıktan sonra `cars <- mtcars` farklı düğümlerde genişleterek veri kümesinde gezinebilirsiniz **değişken Gezgini**:

![Değişken Gezgini genişletilmiş görünümünü](media/variable-explorer-expanded-results.png)

Değişkenleri silmek için sağ tıklayıp **Sil**, ya da değişken seçip ENTER tuşuna **Sil** anahtarı.

Artımlı arama'yı kullanarak bir veri çerçevesinde gözlemi için arama da yapabilirsiniz. İlk olarak, arama yapmak istediğiniz veri çerçevesinde düğümleri genişletin ve ardından arama kutusuna arama terimlerini girin.

## <a name="details-table-view"></a>Ayrıntılar (tablo) görünümü

Veriler genellikle tablo olduğundan, herhangi bir karmaşık veri türü ayrı bir tabloda Büyüteç simgesini seçerek veya sağ tıklayarak ve görüntüleyebileceğiniz **ayrıntıları göster**.

![Değişken Gezgini Tablo görünümü](media/variable-explorer-table-view.png)

Üzerinde bir sütunun başlığına tıklayarak verileri (artan veya azalan arasında değişen) sütununa göre sıralar. Basılı **Shift** ve ek sütunlarda tıklayarak ekler sütunlar için de sıralama. Bir sütun olmadan tıklayarak **Shift** tek sütun sıralama için döndürür.

Sütun başlıkları tıkladığınız dizisi sıralama gerçekleştirildiği sırasını belirler. Örneğin, **Shift**+**tıklayın** **cyl** sütununda, ardından **Shift**+**tıklayın** **mpg** iki kez silindir sayısı artan ve azalan düzende galon başına mil için Listeyi sıralamak için sütun:

![İki sütuna göre sıralama verileri tablo görünümü.](media/variable-explorer-table-view-sorting.png)

Çünkü **değişken Gezgini** ve tablo görünümleri ayrı Visual Studio windows, yan yana çalışma istiyor ancak bunları düzenleyebilirsiniz. Bkz: [Visual Studio'da pencere düzenlerini özelleştirme](../ide/customizing-window-layouts-in-visual-studio.md) genel yönergeler için.

## <a name="open-in-excel-or-other-csv-capable-application"></a>Excel'de Aç (veya başka bir CSV özellikli uygulama)

Daha fazla işleme ve analiz için genellikle oturum değişkenleri CSV'ye dışarı aktarmak yararlıdır. Dışarı aktarma küçük bir Excel simgesi ile yapılır (![Excel Dışarı Aktar simgesine](media/variable-explorer-excel-icon.png)) içindeki her bir düğümün yanında **değişken Gezgini**, veya öğeyi sağ tıklatıp seçerek **CSV uygulamada Aç**. Simgesini seçerek Yazar verileri yeni bir CSV dosyasında *%userprofile%\Documents\RTVS_CSV_Exports* klasörünü ve ardından başlatır her uygulamada açılır bu dosya ile ilişkili *.csv*uzantısı.

## <a name="scopes"></a>Kapsamları

Varsayılan olarak **değişken Gezgini** genel kapsam için açar. Pencerenin üst kısmındaki açılır listeden bir paket seçerek, paket kapsamına geçiş yapabilirsiniz.

![Bir paket kapsam gösteren bir değişken Gezgini](media/variable-explorer-package-scopes.png)

Hata ayıklayıcı bir kesme noktasında durdurulduğunda bir işlev kapsamı için geçiş yapabilirsiniz (unutmayın **değişken Gezgini** ayıklanan kod için işlev kapsamı otomatik olarak geçiş yapılmaz):

![Hata ayıklama sırasında bir veri çerçevesi gösteren bir değişken Gezgini](media/variable-explorer-as-locals-window.png)

**Değişken Gezgini** yerel değişkenler bir işlevde gösteren gibi hata ayıklayıcı, kodda adım adım gibi değişiklikler kapsamı otomatik olarak işlev.

## <a name="import-data-into-variable-explorer"></a>Değişken Gezgini ile veri alma

İki komutları **değişken Gezgini** aracılığıyla da kullanılabilir olan araç çubuğu **R Araçları** > **veri** menüsünde, içeri aktarma dış CSV kümelerine R oturum: **Web URL'si oturumundan R alma kümesine** ve **R oturumu metin dosyasından içeri aktarma kümesine**.

İçeri aktarmak için CSV dosyası belirledikten sonra Visual Studio görüntüler bir **veri kümesini içeri aktarma** o veri dosyasını nasıl ayrıştırılır denetlemek için seçenekleri sahip iletişim (diğer bir deyişle, gelen alan ayırıcısı nedir ve nasıl işleneceğini tırnak işareti). Ayrıca, içeri aktarılan veri çerçevesi ile özgün veri dosyasının önizlemesini görebilirsiniz:

![Veri kümesi iletişim kutusu İçeri Aktar](media/variable-explorer-import-dataset-dialog.png)
