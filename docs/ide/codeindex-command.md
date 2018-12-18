---
title: Codeındex komutu
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- command-line tools [Team Foundation Server]
- TFSConfig
- CodeIndex command [Team Foundation Server]
ms.assetid: b79568d4-6a64-4ca9-a1ee-3e57f92a9c5c
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3f1169ff5bc9487fc062ab7cbc6e2adb01151a19
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49926156"
---
# <a name="codeindex-command"></a>Codeındex komutu

Kullanım **Codeındex** Team Foundation Server'ınızdaki kod dizin oluşturmanın yönetmek için komutu. Örneğin, CodeLens bilgilerini düzeltmek veya sunucu performans sorunlarını araştırmak üzere dizin oluşturmayı kapatmak için dizini sıfırlamak isteyebilirsiniz.

## <a name="required-permissions"></a>Gerekli izinler

Kullanılacak **Codeındex** komutunu bir üyesi olmanız gerekir **Team Foundation Yöneticileri** güvenlik grubu. Bkz: [izinleri ve grupları Azure DevOps Hizmetleri ve TFS için tanımlanan](/azure/devops/organizations/security/permissions?view=vsts).

> [!NOTE]
> Yönetici kimlik bilgileriyle oturum açmış olsanız bile, bu komutu çalıştırmak için yükseltilmiş bir komut istemi penceresi açmanız gerekir. Ayrıca Team Foundation Uygulama katmanından bu komutunu da çalıştırmanız gerekir.

## <a name="syntax"></a>Sözdizimi

```cmd
TFSConfig CodeIndex /indexingStatus | /setIndexing:[ on | off | keepupOnly ] | /ignoreList:[ add | remove | removeAll | view ] ServerPath | /listLargeFiles [/fileCount:FileCount] [/minSize:MinSize] | /reindexAll | /destroyCodeIndex [/noPrompt] | /temporaryDataSizeLimit:[ view | <SizeInGBs> | disable ] | /indexHistoryPeriod:[ view | all | <NumberOfMonths> ] [/collectionName:CollectionName | /collectionId:CollectionId]
```

### <a name="parameters"></a>Parametreler

|**Bağımsız değişken**|**Açıklama**|
|------------------| - |
|`CollectionName`|Proje koleksiyonunun adını belirtir. Ad boşluk içeriyorsa, tırnak işaretleri, örneğin, "Fabrikam Web sitesi" adıyla alın.|
|`CollectionId`|Proje koleksiyonunun kimlik numarasını belirtir.|
|`ServerPath`|Bir kod dosyası yolunu belirtir.|

|**Seçeneği**|**Açıklama**|
|----------------| - |
|**/indexingStatus**|Kod dizin oluşturma hizmeti yapılandırmasını ve durumunu gösterir.|
|**/ setındexing:**[üzerinde &#124; kapalı &#124; keepuponly seçeneğinin belirtilmesini]|-   **üzerinde**: tüm değişiklik kümelerini dizine almayı Başlat.<br />-   **Kapalı**: tüm değişiklik kümelerini dizine almayı sonlandır.<br />-   **keepuponly seçeneğinin belirtilmesini**: daha önce oluşturulan değişiklik kümelerinin dizinini oluşturmayı durdurmak ve yalnızca yeni değişiklik kümelerini dizine almayı Başlat.|
|**/ ignorelist:**[ekleme &#124; Kaldır &#124; removeAll &#124; görünümü] `ServerPath`<br /><br /> Başlangıç, bitiş veya her iki ucunda da sunucu yolu joker karakter (*) kullanabilirsiniz.|Kod dosyaları ve dizinli istemediğiniz yollarının listesini belirtir.<br /><br /> -   **ekleme**: istemediğiniz dosya dizini yok sayılan dosya listesine ekleyin.<br />-   **kaldırma**: dizinli yoksayılan dosyalar listesinden istediğiniz dosya kaldırma.<br />-   **removeAll**: yoksayılan dosya listesini temizleyin ve tüm dosyaları dizine almaya başlayın.<br />-   **Görünüm**: dizine alınmamış tüm dosyalarına bakın.|
|**/listLargeFiles [/ fileCount:** `FileCount` **/minSize:** `MinSize`]|KB olarak belirtilen boyutu aşan dosyaları belirtilen sayısını gösterir. Ardından **/ignorelist** bu dosyaları dizine elmadan hariç tutmak için seçeneği.|
|**/reindexAll**|Önceden dizinlenmiş verileri silmek ve dizinlemeye yeniden başlayın.|
|**/destroyCodeIndex [/noPrompt]**|Kod dizinini silin ve dizinlenen tüm veriyi kaldırın. Kullanırsanız, onay gerektirmez **/noprompt** seçeneği.|
|**/temporaryDataSizeLimit**: [görünümü &#124; <`SizeInGBs`> &#124; devre dışı]|Değişiklik kümesi işleme CodeLens oluşturur ne kadar geçici veri denetimi. Varsayılan sınırı 2 GB'dir.<br /><br /> -   **Görünüm**: Geçerli boyut sınırını gösterir.<br />-   `SizeInGBs`: Boyut sınırını değiştirin.<br />-   **devre dışı**: boyut sınırını kaldırın.<br /><br /> Yeni bir değişiklik kümesi CodeLens işlemeden önce bu sınırı denetlenir. Geçici verileri bu sınırı aşarsa, CodeLens değil yenilerini değişiklik işleme duraklatılır. CodeLens, veriler temizlenir ve bu sınırın altına düştüğünde sonra işleme yeniden başlar. Temizleme, günde bir kez otomatik olarak çalıştırır. Başka bir deyişle, geçici verileri temizleme çalışan başlatana kadar bu sınırı aşan.|
|**/indexHistoryPeriod**: [görünümü &#124; tüm &#124; <`NumberOfMonths`>]|Denetim, değişiklik geçmişini dizin ne kadar. Bu, ne kadar geçmiş CodeLens gösterir etkiler. 12 ay varsayılan sınırlıdır. Bu, yalnızca son 12 aya ait değişiklik geçmişinizi CodeLens gösterir anlamına gelir.<br /><br /> -   **Görünüm**: geçerli ay sayısını gösterir.<br />-   **tüm**: tüm değişiklik geçmişini dizin.<br />-   `NumberOfMonths`: Dizin değişiklik geçmişi için kullanılan ay sayısını değiştirin.|
|**/ CollectionName:** `CollectionName`|Çalıştırılacağı proje koleksiyonunun adını belirtir **Codeındex** komutu. Kullanmadığınızda gerekli **/CollectionId**.|
|**/ CollectionId:** `CollectionId`|Çalıştırılacağı projesi koleksiyonunun kimlik numarasını belirtir **Codeındex** komutu. Kullanmadığınızda gerekli **CollectionName**.|

## <a name="examples"></a>Örnekler

> [!NOTE]
> Burada adı geçen örnek şirketler, kuruluşlar, ürünler, etki alanı adları, e-posta adresleri, logolar, kişiler, yerler ve olaylar hayal ürünüdür.  Gerçek şirket, kuruluş, ürün, etki alanı adı, e-posta adresi, logo, kişi, yer veya olayları ile hiçbir ilişki amaçlanmamıştır veya çıkarılmamalıdır.

 Durumunu ve yapılandırmasını dizin kodu görmek için:

```cmd
TFSConfig CodeIndex /indexingStatus /collectionName:"Fabrikam Website"
```

 Tüm değişiklik kümelerini dizine almayı başlatmak için:

```cmd
TFSConfig CodeIndex /setIndexing:on /collectionName:"Fabrikam Website"
```

 Daha önce oluşturulan değişiklik kümelerinin dizinini oluşturmayı durdurmak ve yalnızca yeni değişiklik kümelerini dizine almayı başlatmak için:

```cmd
TFSConfig CodeIndex /setIndexing:keepupOnly /collectionName:"Fabrikam Website"
```

 10 KB'den büyük olan en fazla 50 dosyaları bulmak için:

```cmd
TFSConfig CodeIndex /listLargeFiles /fileCount:50 /minSize:10 /collectionName:"Fabrikam Website"
```

 Belirli bir dosyayı dizine elmadan hariç tutmak ve yoksayılan dosya listesine eklemek için:

```cmd
TFSConfig CodeIndex /ignoreList:add "$/Fabrikam Website/Catalog.cs" /collectionName:"Fabrikam Website"
```

 Dizine alınmamış tüm dosyaları görmek için:

```cmd
TFSConfig CodeIndex /ignoreList:view
```

 Önceden dizinlenmiş verileri silmek ve dizinlemeye yeniden başlamak için:

```cmd
TFSConfig CodeIndex /reindexAll /collectionName:"Fabrikam Website"
```

 Tüm değişiklik geçmişini kaydetmek için:

```cmd
TFSConfig CodeIndex /indexHistoryPeriod:all /collectionName:"Fabrikam Website"
```

 CodeLens geçici veri boyutu sınırı kaldırın ve geçici veri boyutundan bağımsız olarak dizin oluşturmaya devam etmek için:

```cmd
TFSConfig CodeIndex /temporaryDataSizeLimit:disable /collectionName:"Fabrikam Website"
```

 Kod dizinini Onayla silmek için:

```cmd
TFSConfig CodeIndex /destroyCodeIndex /collectionName:"Fabrikam Website"
```

## <a name="see-also"></a>Ayrıca bkz.

- [CodeLens ile kod değişikliklerini ve diğer geçmişi bulma](../ide/find-code-changes-and-other-history-with-codelens.md)
- [TFSConfig ile sunucu yapılandırmasını yönetme](/tfs/server/ref/command-line/tfsconfig-cmd)