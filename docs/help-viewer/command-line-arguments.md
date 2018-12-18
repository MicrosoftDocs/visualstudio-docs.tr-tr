---
title: Komut satırı bağımsız değişkenleri için Yardım içeriği Yöneticisi
ms.date: 11/01/2017
ms.prod: visual-studio-dev15
ms.topic: reference
ms.assetid: 3aa9890a-1147-42ba-adea-17935d184038
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e25e213f168739f6fe98d60a6ffbf00237a970b6
ms.sourcegitcommit: 75e02ed88a1ace6e8265fd4e3a82a1bc78f3adca
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/13/2018
ms.locfileid: "53378124"
---
# <a name="command-line-arguments-for-the-help-content-manager"></a>Komut satırı bağımsız değişkenleri için Yardım içeriği Yöneticisi

Dağıtıp için Yardım içeriği Yöneticisi komut satırı bağımsız değişkenleri kullanarak yerel Yardım içeriğini yönetmek nasıl belirtebilirsiniz (*HlpCtntMgr.exe*). Bu komut satırı aracı için komut dosyalarını yönetici izinleriyle çalıştırmalısınız ve bu betikler, hizmet olarak çalıştıramazsınız. Bu aracı kullanarak aşağıdaki görevleri gerçekleştirebilirsiniz:

-   Ekleyin veya bir disk veya buluttan yerel Yardım içeriğini güncelleştirin.

-   Yerel Yardım içeriğini kaldırın.

-   Yerel Yardım içerik deposunu taşıyın.

-   Eklemek, güncelleştirmek, kaldırmak veya yerel Yardım içeriğini sessizce taşıyın.

Sözdizimi:

```cmd
HlpCtntmgr.exe /operation Value /catalogname CatalogName /locale Locale /sourceuri InstallationPoint
```

Örneğin:

```cmd
hlpctntmgr.exe /operation install /catalogname VisualStudio15 /locale en-us /sourceuri d:\productDocumentation\HelpContentSetup.msha
```

## <a name="switches-and-arguments"></a>Anahtarlar ve bağımsız değişkenler

Aşağıdaki tabloda, anahtarlar ve bağımsız değişkenler için Yardım içeriği Yöneticisi komut satırı aracı için kullanabileceğiniz tanımlar:

|Anahtar|Gerekli mi?|Arguments|
|------------|---------------|---------------|
|/operation|Evet|-   **Yükleme**--books belirtilen yükleme kaynağından yerel içerik deposuna ekler.<br />     Bu anahtar, / booklist bağımsız değişkeni, / sourceuri bağımsız değişkeni veya her ikisini de gerektirir. / Sourceurı bağımsız değişkenini belirtmezseniz, yükleme kaynağı olarak varsayılan Visual Studio URI'si kullanılır. / Booklist bağımsız değişkeni belirtmezseniz / sourceuri tüm kitaplar yüklenir.<br />-   **Kaldırma**--yerel içerik deposundan belirttiğiniz kitapları kaldırır.<br />     Bu anahtar / booklist bağımsız değişkeni veya/sourceurı bağımsız değişkenini gerektirir.  / Sourceurı bağımsız değişkenini belirtirseniz, tüm kitaplar kaldırılır ve/booklist bağımsız değişkeni yoksayılır.<br />-   **Taşıma**--yerel depo belirlediğiniz yola taşır. Varsayılan yerel depo yolu altında bir dizin olarak ayarlanmış olan *% ProgramData %*<br />     Bu anahtar, / locationpath ve/catalogname bağımsız değişkenler gerektirir. Geçerli olmayan bir yol belirtirseniz veya sürücü içeriği alacak kadar yeterli boş alan içermiyorsa hata iletileri olay günlüğüne kaydedilir.<br />-   **Yenileme**--güncelleştirmeleri yüklü veya en son güncellemeden beri değiştirilmiş konuları günceller.<br />     Bu anahtar, / sourceuri bağımsız değişkeni gerektirir.|
|/ catalogname|Evet|İçerik kataloğunun adını belirtir.|
|/ Locale|Hayır|Görüntüleme ve Yardım Görüntüleyici'nün geçerli örneğini içeriğini yönetmek için kullanılan ürün yerel ayarını belirtir. Örneğin, belirttiğiniz `EN-US` için belirtirsiniz.<br /><br /> Bir yerel ayar belirtmezseniz, işletim sistemi yerel ayarı kullanılır. Bu yerel ayar belirlenemiyorsa `EN-US` kullanılır.<br /><br /> Geçerli olmayan bir yerel ayar belirtirseniz, bir hata iletisi olay günlüğüne kaydedilir.|
|/e|Hayır|Geçerli kullanıcının yönetici kimlik bilgileri varsa Yardım içerik yöneticisini yönetimsel ayrıcalıklara yükseltir.|
|/ sourceurı|Hayır|İçeriğin kurulduğu URL'yi (API hizmeti) yüklü belirtir veya içerik yükleme dosyası yolu (*.msha*). URL, ürün grubuna (üst düzey düğümü) veya Visual Studio 2010 stil son içinde ürün kitaplarına (yaprak düzey düğüm) işaret edebilir. URL'nin sonunda bir eğik çizgi (/) eklemeniz gerekmez. Sonunda eğik çizgi eklerseniz, uygun şekilde işlenir.<br /><br /> Bir internet bağlantısı kullanılamıyor ya da içerik yönetilirken kesintiye günlük bulunmayan, bir dosya belirtirseniz, geçerli değil veya erişilebilir durumda değil durumunda veya bir hata iletisi kaydedilir.|
|Vendor|Hayır|Kaldırılacak ürün içeriği için satıcıyı belirtir (örneğin, `Microsoft`). Bu anahtar için varsayılan değişken Microsoft'tur.|
|/ ProductName|Hayır|Kaldırılacak kitapların ürün adını belirtir. Ürün adı tanımlanır *helpcontentsetup.msha* veya *books.html* içerik ile gönderilen dosyaları. Aynı anda yalnızca tek bir üründen kitap kaldırabilirsiniz. Kitapları birden çok üründen kaldırmak için birden çok yükleme gerçekleştirmeniz gerekir.|
|/ booklist|Hayır|Yönetilecek, boşluklarla ayrılmış kitap adlarını belirtir. Değerler, yükleme medyasında listelendiği gibi kitap adları eşleşmelidir.<br /><br /> Bu bağımsız değişkeni belirtmezseniz, / sourceurı içinde belirtilen ürün için önerilen tüm kitaplar yüklenir.<br /><br /> Bir kitap adını, bir veya daha fazla boşluk içeriyorsa, listenin uygun şekilde ayrılması çift tırnak (") içine alın.<br /><br /> Geçerli veya ulaşılabilir olmayan bir/sourceurı belirtirseniz, hata iletileri kaydedilir.|
|/ skuıd|Hayır|Stok birimini (STB) ürününü yükleme kaynağından tutma belirtir ve/sourceurı anahtarının tanıttığı kitaplara filtre uygular.|
|/Membership|Hayır|-   **En düşük**--üzerinde/skuıd anahtarını kullanarak belirttiğiniz SKU temelli Yardım içeriğinin minimum kümesini yükler. SKU ve İçerik kümesi arasındaki eşleme hizmet API'SİNDE gösterilir.<br />-   **Önerilen**— / skuıd bağımsız değişkenini kullanarak belirttiğiniz SKU için önerilen kitaplar kümesini yükler. Hizmet API'si yükleme kaynağı olan veya *. MSHA*.<br />-   **Tam**--/ skuıd bağımsız değişkenini kullanarak belirttiğiniz SKU için tüm kitaplar kümesini yükler. Hizmet API'si yükleme kaynağı olan veya *. MSHA*.|
|/ locationpath|Hayır|Yerel Yardım içeriğini için varsayılan klasörü belirtir. Yalnızca içeriği yüklemek veya taşımak için bu anahtarı kullanmanız gerekir. Bu anahtarı belirtirseniz, / silent de belirtmeniz gerekir geçin.|
|/silent|Hayır|Yükler veya olmadan kullanıcıya sormadan veya durum bildirim alanında simgesi dahil olmak üzere herhangi bir UI görüntülemeden Yardım içeriğini kaldırır. Çıkış bir dosyaya kaydedilir *% Temp %* dizin. **Önemli:**  İçeriği sessizce yüklemek için dijital olarak imzalanmış kullanmalısınız *.cab* dosyaları değil *.mshc* dosyaları.|
|/launchingApp|Hayır|Yardım Görüntüleyici ana uygulama olmadan başlatıldığında uygulama ve Katalog bağlamını tanımlar. Bu anahtar için bağımsız değişkenler *CompanyName*, *ProductName*, ve *VersionNumber* (örneğin, `/launchingApp Microsoft,VisualStudio,15.0`).<br /><br /> Bu/silent içeriği yüklemek için gerekli parametre.|
|/ wait *saniye*|Hayır|Duraklatır yükleme, kaldırma ve yenileme işlemlerini. Bir işlem zaten devam eden kataloğuna yönelik ise, işlem belirtilen sayıda devam etmek için saniye bekler. Süresiz beklemesi için 0 kullanın.|
|/?|Hayır|Anahtarları ve açıklamaları için Yardım içeriği Yöneticisi komut satırı aracı için listeler.|

### <a name="exit-codes"></a>Çıkış kodları

Komut satırı aracı için Yardım içeriği Yöneticisi sessiz modda çalıştırdığınızda, aşağıdaki çıkış kodlarını döndürür:

```
Success = 0,

FailureToElevate = 100
InvalidCmdArgs = 101,
FailOnFetchingOnlineContent = 110,
FailOnFetchingContentFromDisk = 120,
FailOnFetchingInstalledBooks = 130,
NoBooksToUninstall = 200,
NoBooksToInstall = 300,
FailOnUninstall = 400,
FailOnInstall = 500,
FailOnMove = 600,
FailOnUpdate = 700,
FailOnRefresh = 800,
Cancelled = 900,
Others = 999,
ContentManagementDisabled = 1200,
OnlineHelpPreferenceDisabled = 1201
UpdateAlreadyRunning = 1300 - (Signals that the update didn't run because another was in progress.)
```

## <a name="see-also"></a>Ayrıca bkz.

- [Yardım Görüntüleyicisi Yönetici Kılavuzu](../help-viewer/administrator-guide.md)
- [Yardım İçerik Yöneticisi geçersiz kılmaları](../help-viewer/behavior-overrides.md)
- [Microsoft Yardım Görüntüleyicisi](../help-viewer/overview.md)