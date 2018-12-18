---
title: VSPerfReport | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- command-line tools, VSPerfReporttool
- performance tools, VSPerfReport tool
- profiling tools,VSPerfReport
- VSPerfReport tool
- command line, tools
- instrumentation, VSPerfReporttool
ms.assetid: dbfd8d91-4430-4b82-81b9-97ac61412a6c
caps.latest.revision: 37
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 12b76923a0687125643f95228397d3051cb08c5b
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51806834"
---
# <a name="vsperfreport"></a>VSPerfReport
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

VSPerfReport komut satırı aracını kullanarak raporları oluşturmak için kullanılan [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] profil oluşturma veri dosyaları profil oluşturma araçları. Varsayılan rapor biçimini .csv dosyasıdır.  
  
 VSPerfReport aşağıdaki sözdizimini kullanır:  
  
```  
VSPerfReport [/U] vspfilename [/options]  
```  
  
 Unutmayın `filename` geçerli .vsp veya .vsps dosyası olmalıdır.  
  
 VSPerfReport komut satırı aracını da .vsp veya .vsps dosyayı karşılaştırmak için kullanılır. Fark ("fark") rapor oluşturmak için aşağıdaki sözdizimini kullanın:  
  
```  
VSPerfReport [/U] /diff vspfilename1 vspfilename2 [/options]  
```  
  
 `vspfilename1 and vspfilename2` Geçerli .vsp veya .vsps dosyası olmalıdır.  
  
## <a name="symbol-files"></a>Simge dosyaları  
 İşlev adları ve satır numaraları gibi sembol bilgilerini görüntülemek için VSPerfReport sembol erişim gerektirir (. Profili oluşturulan bileşenleri ve Windows sembol dosyalarını PDB) dosyaları. Daha fazla bilgi için [nasıl yapılır: komut satırından sembol dosyası konumu belirtin](../profiling/how-to-specify-symbol-file-locations-from-the-command-line.md).  
  
## <a name="general-report-options"></a>Genel rapor seçenekleri  
 Aşağıdaki tabloda genel raporun biçimlendirme seçenekleri ve raporlanacak verileri seçme seçeneklerini açıklar.  
  
|Seçenekler|Açıklama|  
|-------------|-----------------|  
|**U**|Rapor çıktısı ve yeniden yönlendirilmiş konsol Çıkışı Unicode olarak yazılır. İlk seçenek belirtilmelidir.|  
|**Özet:**[*türleri*]|Bir veya daha fazla rapor türlerini oluşturur.<br /><br /> -   `All` -Tüm rapor türleri oluşturuldu.<br />-   `CallerCallee` -İşlevler arası üst/alt ilişkilerini.<br />-   `Function` -çağrılan işlevlerin.<br />-   `CallTree` -çağrılan işlevlerin hiyerarşisini.<br />-   `Counter` -tüm işaretleri birlikte Windows performans sayacı değerlerini.<br />-   `Ip` -profili yönergeleri.<br />-   `Life` -(ayırma verilerinin toplandığını olduğunda kullanılabilir.) ayrılmış nesnelerin ömrü<br />-   `Line` Kaynak kod satırı profil verileri.<br />-   `Header` -rapor dosyasının başlık bilgilerini içerir.<br />-   `Mark` tüm işaretleri.<br />-   `Module` -profili modüller.<br />-   `Process` -profili işlemler.<br />-   `Thread` -iş parçacığı profili.<br />-   `Type` -türler ayrılmış.<br />-   `Contention` -Kaynak çakışmaları.<br />-   `RuleWarnings` -Performans kural sorunlarını<br />-   `ETW` -tüm olay izleme için Windows (ETW) olayları, profil oluşturma çalışmasında toplanan. .Etl veri dosyası özgün konumuna veya .vsp veya .vsps dosyasını içeren dizini olmalıdır.|  
|**Xml**|XML formatında çıkış rapor.|  
|**CallTrace**|İşlev girişi ve çıkış yapar ve ETW olayları işaretleri listesini oluşturur.|  
|**ClearPackedSymbols**|Daha önce katıştırılmış sembolleri bir profil oluşturucu veri dosyasından kaldırır. İkinci PackSymbols çalıştırmadan önce şu komutu çalıştırın. zaman.|  
|**SymbolPath:** `path`|Bir veya daha fazla arama yollarını ya da profil oluşturucu veri dosyası için sembolleri içeren sembol sunucuları belirtir.|  
|**DebugSymPath**|Simgeler ve bulunan olup olmadığı için Aranan konumları listeler. Bu seçenek, sembol çözümleme sorunlarını gidermek kullanışlıdır.|  
|**PackSymbols**|Sembolleri sembol (.pdb) dosyalarını analiz için gerekli olmayan profil oluşturma veri (.vsp) dosyasına kaydeder.|  
|**Çıkış:** *yolu*&#124;*dosya adı*|Oluşturulan rapor dosyaları için alternatif bir konum belirtir. Varsayılan olarak, raporlar, geçerli dizinde oluşturulur.|  
|**SummaryFile**|Analiz edin ve analiz edilmiş bilgileri bir .vsps Özet dosyasına kaydet.|  
|**PrintMarks**|Adları ve tüm zaman damgaları içinde belirtilen rapor dosyasını görüntüleyin.|  
|**?**|Kullanım bilgilerini görüntüler.|  
|**NoLogo**|Rapor çalıştırırken sürüm bilgileri gizler.|  
|**UserRulesDirectory**|[Henüz uygulanmadı] directory içeren kullanıcı tanımlı performans kuralları belirtir.|  
  
## <a name="filter-options"></a>Filtre Seçenekleri  
 Aşağıdaki tabloda kullanılabilir verileri filtrelemek için seçenekleri açıklar.  
  
|Seçenekler|Açıklama|  
|-------------|-----------------|  
|**JustMyCode**[**:**[`caller`] [,`callee`]]|Yalnızca kullanıcı uygulama işlev çağrılarını Göster; Sistem çağrıları gizleyin.<br /><br /> -Parametre - tüm sistem işlevlerini gizleyin.<br />-   `caller` -Uygulama işlevlerini çağıran sistem fonksiyonların bir seviyesini göster.<br />-   `callee` -Kullanıcı uygulama işlevleri tarafından çağrılan sistem fonksiyonların bir seviyesini göster.|  
|**StartTime:**[*değer*]|Yalnızca (milisaniye cinsinden.) değerden sonra toplanan verileri göster|  
|**EndTime:**[*değer*]|Yalnızca (milisaniye cinsinden.) değerden önce toplanan verileri göster|  
|**FilterFile:** `VSPFFile`|Visual Studio performans raporu penceresinden oluşturulan bir filtre dosyasının konumunu belirtir.|  
|**MsFilter:**[*starttime, süresi*]|Yalnızca verileri göstermek `starttime` uzunluğuna kadar `duration` (milisaniye cinsinden.)|  
|**İşlem:**[*PID*]|Yalnızca belirtilen işlemden verileri göster.|  
|**İş parçacığı:**[*ThreadID*]|Yalnızca belirtilen iş parçacığından verileri göster.|  
|**İş parçacığı:**[*ThreadID, ProcessId*]|Yalnızca belirtilen işlemle ilişkili belirtilen iş parçacığından verileri göster.|  
  
## <a name="difference-report-options"></a>Fark rapor seçenekleri  
 Aşağıdaki tabloda, rapor dosyalarını karşılaştırma seçeneklerini açıklar.  
  
|Seçenekler|Açıklama|  
|-------------|-----------------|  
|**Fark**  `vspfile1 vspfile2`|İki rapor dosyalarını (.vsp veya .vsps) dosyası karşılaştırın. Özet Seçenekleri fark seçeneğini kullanarak göz ardı edilir.|  
|**Fark:**[*değer*]|Bu eşik değerinin iki değer arasındaki farkı göz ardı edilir. Ayrıca bu eşiğin altında yeni veriler gösterilmeyecek.|  
|**DiffTable:**[*tablename*]|Dosyayı karşılaştırmak için belirli tabloyu kullanın. İşlevler tablosu varsayılandır.|  
|**DiffColumn:**[*columnname*]|Bu özel sütun karşılaştırma değerleri kullanın. Özel örnekler Yüzde sütunu varsayılandır.|  
|**QueryDiffTables**|Geçerli tablolar ve sütunlar için sağlanan iki rapor dosyaları listeler.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Performans Raporu Görünümleri](../profiling/performance-report-views.md)



