---
title: CodeIndex komutu
description: Kod dizinlemeyi Azure DevOps Server (eski adıyla Team Foundation Server) yönetmek için CodeIndex komutunu nasıl kullanacağınızı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- command-line tools [Team Foundation Server]
- TFSConfig
- CodeIndex command [Team Foundation Server]
ms.assetid: b79568d4-6a64-4ca9-a1ee-3e57f92a9c5c
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 47875bcece910433a1d20ad66867acd7fdbee8d8
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99841932"
---
# <a name="codeindex-command"></a>CodeIndex komutu

Team Foundation Server kod dizinlemeyi yönetmek için **CodeIndex** komutunu kullanın. Örneğin, CodeLens bilgilerini onarmak için dizini sıfırlamak veya sunucu performans sorunlarını araştırmak için dizin oluşturmayı devre dışı bırakmak isteyebilirsiniz.

## <a name="required-permissions"></a>Gerekli izinler

**CodeIndex** komutunu kullanmak Için, **Team Foundation yöneticileri** güvenlik grubunun bir üyesi olmanız gerekir. [Azure DevOps Services ve TFS için tanımlanan izinler ve gruplar](/azure/devops/organizations/security/permissions?view=vsts&preserve-view=true)bölümüne bakın.

> [!NOTE]
> Yönetici kimlik bilgileriyle oturum açmış olsanız bile, bu komutu çalıştırmak için yükseltilmiş bir komut Istemi penceresi açmalısınız. Ayrıca, bu komutu Team Foundation uygulama katmanından çalıştırmanız gerekir.

## <a name="syntax"></a>Sözdizimi

```cmd
TFSConfig CodeIndex /indexingStatus | /setIndexing:[ on | off | keepupOnly ] | /ignoreList:[ add | remove | removeAll | view ] ServerPath | /listLargeFiles [/fileCount:FileCount] [/minSize:MinSize] | /reindexAll | /destroyCodeIndex [/noPrompt] | /temporaryDataSizeLimit:[ view | <SizeInGBs> | disable ] | /indexHistoryPeriod:[ view | all | <NumberOfMonths> ] [/collectionName:CollectionName | /collectionId:CollectionId]
```

### <a name="parameters"></a>Parametreler

|**Değişkendir**|**Açıklama**|
|------------------| - |
|`CollectionName`|Proje koleksiyonunun adını belirtir. Adda boşluk varsa, adı tırnak işaretleri (örneğin, "Fabrikam Web sitesi") arasına alın.|
|`CollectionId`|Proje koleksiyonunun kimlik numarasını belirtir.|
|`ServerPath`|Bir kod dosyasının yolunu belirtir.|

|**Seçenek**|**Açıklama**|
|----------------| - |
|**/IndexingStatus**|Kod dizin oluşturma hizmetinin durumunu ve yapılandırmasını görüntüleyin.|
|**/setIndexing:**[&#124; kapalı &#124; yalnızca keepupOnly]|-   **Açık**: tüm değişiklik kümelerini dizine almayı Başlat.<br />-   **kapalı**: tüm değişiklik kümelerini dizinlemeyi durdur.<br />-   **keepupOnly**: önceden oluşturulmuş değişiklik kümelerinin dizinini oluşturmayı Durdur ve yalnızca yeni değişiklik kümelerini dizine almayı Başlat.|
|**/IgnoreList:**[Ekle &#124; kaldır &#124; removeall &#124; görünümü] `ServerPath`<br /><br /> Sunucu yolunun başlangıcında, sonunda veya her iki ucunda joker karakteri (*) kullanabilirsiniz.|Dizinlenmesini istemediğiniz kod dosyalarının ve yollarının listesini belirtir.<br /><br /> -   **Ekle**: dizinlenmesini istemediğiniz dosyayı, yoksayılan dosya listesine ekleyin.<br />-   **Kaldır**: dizine alınmasını istediğiniz dosyayı yoksayılan dosya listesinden kaldırın.<br />-   **RemoveAll**: yoksayılan dosya listesini temizleyin ve tüm dosyaları dizine almayı başlatın.<br />-   **görüntüle**: dizinlenmemiş tüm dosyaları görüntüleyin.|
|**/listlargefiles [/FileCount:** `FileCount` **/MinSize:** `MinSize` ]|KB cinsinden belirtilen boyutu aşan belirtilen dosya sayısını gösterir. Daha sonra bu dosyaları dizin oluşturma işleminden dışlamak için **/IgnoreList** seçeneğini kullanabilirsiniz.|
|**/Reındexall**|Önceden dizinli verileri temizleyin ve Dizin oluşturmayı yeniden başlatın.|
|**/Destroyıcodeındex [/noPrompt]**|Kod dizinini silin ve tüm dizinli verileri kaldırın. **/Noprompt** seçeneğini kullanırsanız onay gerektirmez.|
|**/temporaryDataSizeLimit**: [görünüm &#124; <`SizeInGBs`> &#124; devre dışı]|Değişiklik kümelerini işlerken CodeLens 'in ne kadar geçici veri oluşturduğunu denetleyin. Varsayılan sınır 2 GB 'dir.<br /><br /> -   **görüntüle**: geçerli boyut sınırını göster.<br />-   `SizeInGBs`: Boyut sınırını değiştirin.<br />-   **devre dışı bırak**: boyut sınırını kaldır.<br /><br /> Bu sınır, CodeLens yeni bir değişiklik kümesini işleyerek denetlenir. Geçici veriler bu sınırı aşarsa, CodeLens, yenilerini değil, geçmiş değişiklik kümelerini işlemeyi duraklatacaktır. CodeLens, veriler temizlendikten ve bu sınırın altına düştüğünde işlemeyi yeniden başlatacak. Temizleme, günde bir kez otomatik olarak çalıştırılır. Bu, temizleme çalışmaya başlamadan geçici verilerin bu sınırı aşabileceği anlamına gelir.|
|**/ındexgeçmişini**: [&#124; tüm &#124; <> görüntüleme `NumberOfMonths` ]|Değişiklik geçmişinizin ne kadar süreyle dizine alınacağını denetleyin. Bu, ne kadar geçmiş CodeLens 'in size gösterdiği geçmişi etkiler. Varsayılan sınır 12 aydır. Bu, CodeLens 'in yalnızca son 12 aydan değişiklik geçmişinizi gösterdiği anlamına gelir.<br /><br /> -   **görüntüle**: geçerli ay sayısını göster.<br />-   **All**: tüm değişiklik geçmişinin dizinini oluştur.<br />-   `NumberOfMonths`: Değişiklik geçmişine dizin eklemek için kullanılan ayların sayısını değiştirin.|
|**/CollectionName:**`CollectionName`|**CodeIndex** komutunun çalıştırılacağı proje koleksiyonunun adını belirtir. **/CollectionId** kullanmıyorsanız gereklidir.|
|**/CollectionId:**`CollectionId`|**CodeIndex** komutunun çalıştırılacağı proje koleksiyonunun kimlik numarasını belirtir. **/CollectionName** kullanmıyorsanız gereklidir.|

## <a name="examples"></a>Örnekler

> [!NOTE]
> Burada adı geçen örnek şirketler, kuruluşlar, ürünler, etki alanı adları, e-posta adresleri, logolar, kişiler, yerler ve olaylar hayal ürünüdür.  Herhangi bir gerçek şirket, kuruluş, ürün, etki alanı adı, e-posta adresi, logo, kişi, yer veya olay ile ilişki amaçlanmamıştır.

Kod dizini oluşturma durumunu ve yapılandırmasını görmek için:

```cmd
TFSConfig CodeIndex /indexingStatus /collectionName:"Fabrikam Website"
```

Tüm değişiklik kümelerini dizine almayı başlatmak için:

```cmd
TFSConfig CodeIndex /setIndexing:on /collectionName:"Fabrikam Website"
```

Önceden oluşturulmuş değişiklik kümelerinin dizinini oluşturmayı durdurmak ve yalnızca yeni değişiklik kümelerini dizine almayı başlatmak için:

```cmd
TFSConfig CodeIndex /setIndexing:keepupOnly /collectionName:"Fabrikam Website"
```

10 KB 'den büyük 50 dosya bulmak için:

```cmd
TFSConfig CodeIndex /listLargeFiles /fileCount:50 /minSize:10 /collectionName:"Fabrikam Website"
```

Dizin oluşturma işleminden belirli bir dosyayı dışlamak ve yoksayılan dosya listesine eklemek için:

```cmd
TFSConfig CodeIndex /ignoreList:add "$/Fabrikam Website/Catalog.cs" /collectionName:"Fabrikam Website"
```

Dizini oluşturulmamış tüm dosyaları görmek için:

```cmd
TFSConfig CodeIndex /ignoreList:view
```

Önceden dizinli verileri temizlemek ve Dizin oluşturmayı yeniden başlatmak için:

```cmd
TFSConfig CodeIndex /reindexAll /collectionName:"Fabrikam Website"
```

Tüm değişiklik kümesi geçmişini kaydetmek için:

```cmd
TFSConfig CodeIndex /indexHistoryPeriod:all /collectionName:"Fabrikam Website"
```

CodeLens geçici verilerinde boyut sınırını kaldırmak ve geçici veri boyutundan bağımsız olarak dizin oluşturmaya devam etmek için:

```cmd
TFSConfig CodeIndex /temporaryDataSizeLimit:disable /collectionName:"Fabrikam Website"
```

Kod dizinini onaylama ile silmek için:

```cmd
TFSConfig CodeIndex /destroyCodeIndex /collectionName:"Fabrikam Website"
```

## <a name="see-also"></a>Ayrıca bkz.

- [CodeLens ile kod değişikliklerini ve diğer geçmişi bulma](../ide/find-code-changes-and-other-history-with-codelens.md)
- [TFSConfig ile sunucu yapılandırmasını yönetme](/azure/devops/server/command-line/tfsconfig-cmd)
