---
title: Codeındex komutu | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- command-line tools [Team Foundation Server]
- TFSConfig
- CodeIndex command [Team Foundation Server]
ms.assetid: b79568d4-6a64-4ca9-a1ee-3e57f92a9c5c
caps.latest.revision: 22
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 9586348a1862820540613a5f191132c49fa6a74d
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49282366"
---
# <a name="codeindex-command"></a>CodeIndex Komutu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Kullanım **Codeındex** Team Foundation Server'ınızdaki kod dizin oluşturmanın yönetmek için komutu. Örneğin, CodeLens bilgilerini düzeltmek veya sunucu performans sorunlarını araştırmak üzere dizin oluşturmayı kapatmak için dizini sıfırlamak isteyebilirsiniz.  
  
 **Gerekli izinler**  
  
 Kullanılacak **Codeındex** komutunu bir üyesi olmanız gerekir **Team Foundation Yöneticileri** güvenlik grubu. Bkz: [Team Foundation Server için izin başvurusu](http://msdn.microsoft.com/library/39997de5-b7fb-4777-b779-07de0543abe6).  
  
> [!NOTE]
>  Yönetici kimlik bilgileriyle oturum açmış olsanız bile, bu komutu çalıştırmak için yükseltilmiş bir komut istemi penceresi açmanız gerekir. Ayrıca Team Foundation Uygulama katmanından bu komutunu da çalıştırmanız gerekir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
TFSConfig CodeIndex /indexingStatus | /setIndexing:[ on | off | keepupOnly ] | /ignoreList:[ add | remove | removeAll | view ] ServerPath | /listLargeFiles [/fileCount:FileCount] [/minSize:MinSize] | /reindexAll | /destroyCodeIndex [/noPrompt] | /temporaryDataSizeLimit:[ view | <SizeInGBs> | disable ] | /indexHistoryPeriod:[ view | all | <NumberOfMonths> ] [/collectionName:CollectionName | /collectionId:CollectionId]  
```  
  
#### <a name="parameters"></a>Parametreler  
  
|**Bağımsız değişken**|**Açıklama**|  
|------------------|---------------------|  
|`CollectionName`|Takım projesi koleksiyonunun adını belirtir. Ad boşluk içeriyorsa, tırnak işaretleri, örneğin, "Fabrikam Web sitesi" adıyla alın.|  
|`CollectionId`|Takım projesi koleksiyonunun kimlik numarasını belirtir.|  
|`ServerPath`|Bir kod dosyası yolunu belirtir.|  
  
|**Seçeneği**|**Açıklama**|  
|----------------|---------------------|  
|**/indexingStatus**|Kod dizin oluşturma hizmeti yapılandırmasını ve durumunu gösterir.|  
|**/ setındexing:**[üzerinde &#124; kapalı &#124; keepuponly seçeneğinin belirtilmesini]|-   **üzerinde**: tüm değişiklik kümelerini dizine almayı Başlat.<br />-   **Kapalı**: tüm değişiklik kümelerini dizine almayı sonlandır.<br />-   **keepuponly seçeneğinin belirtilmesini**: daha önce oluşturulan değişiklik kümelerinin dizinini oluşturmayı durdurmak ve yalnızca yeni değişiklik kümelerini dizine almayı Başlat.|  
|**/ ignorelist:**[ekleme &#124; Kaldır &#124; removeAll &#124; görünümü] `ServerPath`<br /><br /> Başlangıç, bitiş veya her iki ucunda da sunucu yolu joker karakter (*) kullanabilirsiniz.|Kod dosyaları ve dizinli istemediğiniz yollarının listesini belirtir.<br /><br /> -   **ekleme**: istemediğiniz dosya dizini yok sayılan dosya listesine ekleyin.<br />-   **kaldırma**: dizinli yoksayılan dosyalar listesinden istediğiniz dosya kaldırma.<br />-   **removeAll**: yoksayılan dosya listesini temizleyin ve tüm dosyaları dizine almaya başlayın.<br />-   **Görünüm**: dizine alınmamış tüm dosyalarına bakın.|  
|**/listLargeFiles [/ fileCount:** `FileCount` **/minSize:** `MinSize`]|KB olarak belirtilen boyutu aşan dosyaları belirtilen sayısını gösterir. Ardından **/ignorelist** bu dosyaları dizine elmadan hariç tutmak için seçeneği.|  
|**/reindexAll**|Önceden dizinlenmiş verileri silmek ve dizinlemeye yeniden başlayın.|  
|**/destroyCodeIndex [/noPrompt]**|Kod dizinini silin ve dizinlenen tüm veriyi kaldırın. Kullanırsanız, onay gerektirmez **/noprompt** seçeneği.|  
|**/temporaryDataSizeLimit**: [görünümü &#124; <`SizeInGBs`> &#124; devre dışı]|Değişiklik kümesi işleme CodeLens oluşturur ne kadar geçici veri denetimi. Varsayılan sınırı 2 GB'dir.<br /><br /> -   **Görünüm**: Geçerli boyut sınırını gösterir.<br />-   `SizeInGBs`: Boyut sınırını değiştirin.<br />-   **devre dışı**: boyut sınırını kaldırın.<br /><br /> Yeni bir değişiklik kümesi CodeLens işlemeden önce bu sınırı denetlenir. Geçici verileri bu sınırı aşarsa, CodeLens değil yenilerini değişiklik işleme duraklatılır. CodeLens, veriler temizlenir ve bu sınırın altına düştüğünde sonra işleme yeniden başlar. Temizleme, günde bir kez otomatik olarak çalıştırır. Başka bir deyişle, geçici verileri temizleme çalışan başlatana kadar bu sınırı aşan.|  
|**/indexHistoryPeriod**: [görünümü &#124; tüm &#124; <`NumberOfMonths`>]|Denetim, değişiklik geçmişini dizin ne kadar. Bu, ne kadar geçmiş CodeLens gösterir etkiler. 12 ay varsayılan sınırlıdır. Bu, yalnızca son 12 aya ait değişiklik geçmişinizi CodeLens gösterir anlamına gelir.<br /><br /> -   **Görünüm**: geçerli ay sayısını gösterir.<br />-   **tüm**: tüm değişiklik geçmişini dizin.<br />-   `NumberOfMonths`: Dizin değişiklik geçmişi için kullanılan ay sayısını değiştirin.|  
|**/ CollectionName:** `CollectionName`|Çalıştırılacağı takım projesi koleksiyonunun adını belirtir **Codeındex** komutu. Kullanmadığınızda gerekli **/CollectionId**.|  
|**/ CollectionId:** `CollectionId`|Çalıştırılacağı takım projesi koleksiyonunun kimlik numarasını belirtir **Codeındex** komutu. Kullanmadığınızda gerekli **CollectionName**.|  
  
## <a name="examples"></a>Örnekler  
  
> [!NOTE]
>  Burada adı geçen örnek şirketler, kuruluşlar, ürünler, etki alanı adları, e-posta adresleri, logolar, kişiler, yerler ve olaylar hayal ürünüdür.  Gerçek şirket, kuruluş, ürün, etki alanı adı, e-posta adresi, logo, kişi, yer veya olayları ile hiçbir ilişki amaçlanmamıştır veya çıkarılmamalıdır.  
  
 Durumunu ve yapılandırmasını dizin kodu görmek için:  
  
```  
TFSConfig CodeIndex /indexingStatus /collectionName:"Fabrikam Web Site"  
```  
  
 Tüm değişiklik kümelerini dizine almayı başlatmak için:  
  
```  
TFSConfig CodeIndex /setIndexing:on /collectionName:"Fabrikam Web Site"  
```  
  
 Daha önce oluşturulan değişiklik kümelerinin dizinini oluşturmayı durdurmak ve yalnızca yeni değişiklik kümelerini dizine almayı başlatmak için:  
  
```  
TFSConfig CodeIndex /setIndexing:keepupOnly /collectionName:"Fabrikam Web Site"  
```  
  
 10 KB'den büyük olan en fazla 50 dosyaları bulmak için:  
  
```  
TFSConfig CodeIndex /listLargeFiles /fileCount:50 /minSize:10 /collectionName:"Fabrikam Web Site"  
```  
  
 Belirli bir dosyayı dizine elmadan hariç tutmak ve yoksayılan dosya listesine eklemek için:  
  
```  
TFSConfig CodeIndex /ignoreList:add "$/Fabrikam Web Site/Catalog.cs" /collectionName:"Fabrikam Web Site"  
```  
  
 Dizine alınmamış tüm dosyaları görmek için:  
  
```  
TFSConfig CodeIndex /ignoreList:view  
```  
  
 Önceden dizinlenmiş verileri silmek ve dizinlemeye yeniden başlamak için:  
  
```  
TFSConfig CodeIndex /reindexAll /collectionName:"Fabrikam Web Site"  
```  
  
 Tüm değişiklik geçmişini kaydetmek için:  
  
```  
TFSConfig CodeIndex /indexHistoryPeriod:all /collectionName:"Fabrikam Web Site"  
```  
  
 CodeLens geçici veri boyutu sınırı kaldırın ve geçici veri boyutundan bağımsız olarak dizin oluşturmaya devam etmek için:  
  
```  
TFSConfig CodeIndex /temporaryDataSizeLimit:disable /collectionName:"Fabrikam Web Site"  
```  
  
 Kod dizinini Onayla silmek için:  
  
```  
TFSConfig CodeIndex /destroyCodeIndex /collectionName:"Fabrikam Web Site"  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [TFSConfig ile sunucu yapılandırmasını yönetme](http://msdn.microsoft.com/en-us/94424190-3b6b-4f33-a6b6-5807f4225b62)   
 [TFS için komut satırı araçları](http://msdn.microsoft.com/en-us/be8c997a-b97b-4e59-97f5-04db0a601a6c)



