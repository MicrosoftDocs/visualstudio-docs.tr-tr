---
title: R projeleri
description: Bir yönetici, özellikler, proje komutları ve şablonları dahil olmak üzere Visual Studio'da R projeleri oluşturma
ms.date: 06/29/2017
ms.prod: visual-studio-dev15
ms.technology: vs-rtvs
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: douge
ms.workload:
- data-science
ms.openlocfilehash: f91d105d1c7b5b60d74dae2f9669a18f8ec064c8
ms.sourcegitcommit: 20c0991d737c540750c613c380cd4cf5bb07de51
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/11/2018
ms.locfileid: "53248289"
---
# <a name="create-r-projects-in-visual-studio"></a>Visual Studio'da R projeleri oluşturma

Projekt R (bir *.rxproj* dosyası) kaynak ve projenizle ilişkili içerik dosyalarını tanımlar. Ayrıca her dosya için derleme bilgisi içeriyor, kaynak denetimi sistemleriyle tümleştirmeyi bilgilerini korur ve mantıksal bileşenler uygulamanıza düzenlemenize yardımcı olur. Çalışma alanı ile ilgili yüklü paketlerin listesi gibi bilgileri, ancak çalışma alanında ayrı olarak korunur.

Projeleri Visual Studio'da her zaman yönetilen *çözüm*, herhangi bir sayıda birbirlerine başvurabilir projeleri içerebilir. Bkz: [Visual Studio'da birden fazla proje türü kullanmak](#use-multiple-project-types-in-visual-studio).

## <a name="creating-a-new-r-project"></a>Yeni bir R projesi oluşturma

1. Visual Studio’yu çalıştırın.
1. Seçin **Dosya > Yeni > Proje...** (**Ctrl**+**Shift**+**N**)
1. "R" altındaki projenizi **şablonları > R**, projeye bir ad ve konum verin ve seçin **Tamam**:

    ![R (vs2017 RTVS) Visual Studio'da yeni proje iletişim kutusu](media/getting-started-01-new-project.png)

Bu komut, bir boş olan bir proje oluşturur *betiği. R* dosya düzenleyicide açık. Ayrıca fark **Çözüm Gezgini** projede iki dosya vardır:

![Şablondan oluşturulan bir R proje içeriği](media/projects-template-results.png)

*. Rhistory* içine girdiğiniz hangi komutları kaydeder [R etkileşimli](interactive-repl-for-r-in-visual-studio.md) penceresi. İle bir adanmış Geçmişi penceresini açabilirsiniz **R Araçları** > **Windows** > **geçmişi** komutu. Bu pencere geçmişini içeriğini temizlemek için bir araç çubuğu düğmesi ve bağlam menü öğelerini içerir.

*Rproject.rproj* dosyası tutar, aksi takdirde Visual Studio tarafından yönetilmeyen bazı R özel Proje ayarları:

| Özellik | Varsayılan | Açıklama |
| --- | --- | --- |
| Sürüm | 1.0 | Projeyi oluşturmak için kullanılan Visual Studio için R araçları sürümü. |
| RestoreWorkspace | Varsayılan | Önceki çalışma değişkenlerinden otomatik olarak yük `.RData` dosya proje dizininde. |
| SaveWorkspace | Varsayılan | Geçerli çalışma alanı değişkenlere kaydetmek `.RData` dosya proje dizininde bir projeyi kapatırken. |
| AlwaysSaveHistory | Varsayılan | Geçerli etkileşimli pencere geçmişine Kaydet `.RHistory` dosya proje dizininde bir projeyi kapatırken. |
| EnableCodeIndexing | Evet | Kod aramaları hızlandırmak için bir arka plan dizin oluşturma görevini çalıştırmak belirler. |
| UseSpacesForTab | Evet | Mi (Evet) alanları eklemek veya bir sekme karakteri belirler (yok) olduğunda **sekmesini** düzenleyicide tuşuna basıldığında. |
| NumSpacesForTab | 2 | UseSpacesForTab Evet ise eklemek için boşluk sayısı. |
| Encoding | UTF-8 | İçin varsayılan kodlamayı `.R` dosyaları. |
| RnwWeave | Sweave | Rnw dosya weaving kullanılacak paketi. |
| LaTeX | pdfLaTeX | RMarkdwon PDF'ye dönüştürme işleminde kullanılacak kitaplığı. |

### <a name="converting-a-folder-of-files-to-an-r-project"></a>Dosya bir klasörü bir R projesine dönüştürme

Mevcut bir klasörü varsa *. R* bir projede, yönetmek istediğiniz dosyaları aşağıdaki adımları uygulayın:

1. Yeni Proje Visual Studio'da, önceki bölümde gösterildiği gibi oluşturun.
1. Dosyalarınızı proje klasörüne kopyalayın.
1. Visual Studio Çözüm Gezgini'nde projeye sağ tıklayın, **Ekle** > **çıkmadan öğesi**, eklemek istediğiniz dosyaya göz atın. Bu dosyaları seçtikten sonra proje ağacında görünür **Tamam**.
1. Kod alt klasörler halinde düzenlemek için projeye sağ tıklayın, **Ekle** > **yeni klasör** ilk olarak, ardından dosyalarınızı bu klasöre kopyalayın ve 3. adımda bu varolan öğeleri ekleyin.

## <a name="project-properties"></a>Proje Özellikleri

Proje özellik sayfaları'ni açmak için projeye sağ **Çözüm Gezgini** seçip **özellikleri**, ya da seçin **Proje > (proje adı) özellikleri** menüsü öğe. Açılan pencerede, proje özellikleri görüntüler:


| Tab | Özellik | Açıklama | 
| --- | --- | --- | 
| Çalıştır | Başlangıç dosyası | İle çalıştırılan dosyasının adı **kaynak başlangıç dosyası** komutu **F5**, **hata ayıklama** > **hata ayıklamayı Başlat**, veya  **Hata ayıklama** > **ayıklamadan Başlat**. Proje dosyasına sağ tıklayıp **başlangıç R betiği ayarlamak** başlangıç dosyası olarak da ayarlar. | 
| | R çalıştırmada etkileşimli sıfırlama | Tüm değişkenler etkileşimli pencerenin çalışma alanından projeyi çalıştırırken temizler. Bunu garanti var, bunu hiçbir denetlerler çalıştırmalardan kalan çalışma içeriğidir. | 
| | Uzak proje yolu | Bir uzak çalışma alanı yolu. | 
| | Aktarım dosyalarda Çalıştır | Proje, filtrede tabi dosyalar olup olmadığını gösteren **dosyaları aktarmak için**, her çalıştırma ile uzak bir çalışma alanına kopyalanacak. | 
| | Dosyaları aktarmak için | Dosya adları ve joker karakterler, bir uzak çalışma alanına kopyalamak için belirli dosyaları belirten **aktarım çalışma dosyalarını** seçilir. | 
| Ayarlar | (Settings.R dosyası) | R proje ayarları geldiğini *Settings.R* veya **. Settings.R* projede bulunan dosyalar. Ayarlar dosyası yoksa, değişkenler, sayfa ve bir varsayılan kaydetme ekleyebilirsiniz *Settings.R* dosya sizin için oluşturulur. Projeye ayar dosyası ekleyebilirsiniz **dosya** > **Yeni Öğe Ekle** menü komutu. <br/> Ayarları R kodu olarak depolanır ve bu nedenle önceden tanımlı ayarlar ortamıyla önceden doldurma, diğer modüllerin çalıştırmadan önce dosya kaynağı. | 

## <a name="r-specific-project-commands"></a>R özel Proje komutları

Visual Studio projeleri sağ tıklama menüsü aracılığıyla genel komutları sayısını desteklemek ve **proje** menüsü. Bu genel özellikleri hakkında ayrıntılı bilgi için bkz. [Visual Studio'da projeler ve çözümler](../ide/solutions-and-projects-in-visual-studio.md). R araçları için Visual Studio (RTVS) kendi komutları birkaç R proje için sağ tıklama menüsü ekler ve ayrıca dosyaları unutmayın, Bununla birlikte ve proje klasörler unutmayın.

| Komut | Açıklama |
| --- | --- |
| Çalışma dizini buraya Ayarla | Bir proje içinde herhangi bir alt üzerinde de kullanılabilir proje klasörüne R etkileşimli pencerenin çalışma dizinini ayarlar. |
| İçeren klasörü aç | Seçilen dosya konumunda Windows Explorer'ı açar. |
| R betiği Ekle | Oluşturur ve yeni bir açılır *. R* varsayılan ada sahip bir dosya. Ayrıca **Ekle** > **yeni öğe** oluşturmak için komut *. R* birkaç diğer dosya türlerinin yanı sıra dosyaları. Bkz: [R özel öğe şablonları](#r-specific-item-templates). |
| R Markdown Ekle | Oluşturur ve açar Yeni *.rmd* varsayılan ada sahip bir belge. Ayrıca **Ekle** > **yeni öğe** oluşturmak için komut *.rmd* birkaç diğer dosya türlerinin yanı sıra dosyaları. Bkz: [R özel öğe şablonları](#r-specific-item-templates).  |
| Saklı yordamları Yayımla | R betiklerini yer alan tüm saklı yordamlar yayımlamak için bir işlem başlatır. Bkz: [çalışma ile SQL Server saklı yordamları](integrating-sql-server-with-r.md#work-with-sql-server-stored-procedures). | 

## <a name="r-specific-item-templates"></a>R özel öğe şablonları

RTVS belirli dosya türleri için şablonlar içerir. Projekt R sağ tıklatıp seçerek şablonları erişim **Ekle** > **yeni öğe**, seçerek **proje**  >   **Yeni Öğe Ekle**, kullanarak veya **dosya** > **yeni** > **dosya** seçerek **R** sekmesi. Yeni bir proje oluşturun ve her türdeki dosyaları eklemek için bir şablon keşfetmek için en iyi yolu var.

> [!Note]
> **Ekle** > **yeni öğe** komutları tabloda; listelenmemiş genel dosya türleri de görüntüler **dosya** > **yeni**   >  **Dosya** üzerinde bu türleri yerine içerdiği **genel** sekmesi.

| Dosya türü | Açıklama |
| --- | --- |
| R betiği | R komut satırına girilen aynı komutları içeren bir metin dosyası. |
| R Markdown | Bir dosya içeren bir [R Markdown](rmarkdown-with-r-in-visual-studio.md) belge. |
| R ayarları | R uygulama ayarlarını içeren bir dosya. | 
| Dokumentace R | Yalnızca ad, diğer ad ve başlık alanları içeren genel R belge dosyası. |
| Dokumentace R (Funkce) | Bir işlev tanımlamak için yorum içeren daha fazla alan içeren bir R belge dosyası. |
| Dokumentace R (veri kümesi) | Bir veri kümesini tanımlamak için yorum içeren daha fazla alan içeren bir R belge dosyası. |
| SQL sorgusu | Ve boş *.sql* dosya. Bkz: [iş SQL Server ve R ile](integrating-sql-server-with-r.md). |
| R ile saklı yordam | Bir R dosyasıyla SQL sorgu alt ve alt yordam şablon dosyası depolanır. Bkz: [iş SQL Server ve R ile](integrating-sql-server-with-r.md). |

## <a name="use-multiple-project-types-in-visual-studio"></a>Visual Studio'da birden fazla proje türleri kullanın

Visual Studio çözümleri toplayın ve ilgili projeler mantıksal tek bir yerde yönetmek için uygun bir yer sağlar. Çözüm, kodunuzu düzenli tutmak ve teams içinde işbirliği yapılmasını kolaylaştırır.

Aşağıdaki örnekte, bir R proje çözüm, R ve Azure Machine Learning, bir Python/scikit-öğrenme projesi, yoğun hesaplama işleri için modüller içeren bir C++ projesi, veri yönetimi için bir SQL projesi ve bir Python/Bottle kullanılarak oluşturulan bir modelle içeriyor. Proje sonucu yayımlayan web sitesi için:

![Visual Studio Çözüm Gezgini'nde bir çözümde birden çok ilgili proje gösteriliyor](media/projects-polyglot.png)

Kalın ile vurgulanmış "Başlangıç" projesi çözümü projedir; değiştirmek için farklı bir projeye sağ tıklayıp **başlangıç projesi olarak ayarla**.

> [!Note]
> Şu anda hiç açık tüm R C#/C++ dil yerinde tümleştirme söz konusu (Python için olduğundan, bkz. [Python için C++ uzantısı oluşturma](../python/working-with-c-cpp-python-in-visual-studio.md)).  Ancak vardır sağlayan kitaplıkları C# ve r için C++ köprüleri

Projeler ve çözümler genel yönetme ile ilgili daha fazla bilgi için bkz: [Visual Studio'da projeler ve çözümler](../ide/solutions-and-projects-in-visual-studio.md).
