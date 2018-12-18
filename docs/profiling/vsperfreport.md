---
title: VSPerfReport | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- command-line tools, VSPerfReporttool
- performance tools, VSPerfReport tool
- profiling tools,VSPerfReport
- VSPerfReport tool
- command line, tools
- instrumentation, VSPerfReporttool
ms.assetid: dbfd8d91-4430-4b82-81b9-97ac61412a6c
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1c679acf7ce6a767702da05bde6fb4a1e6f8a7df
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/01/2018
ms.locfileid: "34572221"
---
# <a name="vsperfreport"></a>VSPerfReport
VSPerfReport komut satırı aracını kullanarak raporlar oluşturmak için kullanılan [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] profil oluşturma veri dosyaları profil oluşturma araçları. Varsayılan rapor biçiminde olan bir. *csv* dosya.  
  
 VSPerfReport aşağıdaki söz dizimini kullanır:  
  
```cmd  
VSPerfReport [/U] vspfilename [/options]  
```  
  
 Unutmayın `filename` geçerli olması gerekir. *Vsp* veya. *vsps* dosya.  
  
 VSPerfReport komut satırı aracı karşılaştırmak için de kullanılır. *vsp* veya. *vsps* dosyaları. Fark ("fark") raporu oluşturmak için aşağıdaki sözdizimini kullanın:  
  
```cmd  
VSPerfReport [/U] /diff vspfilename1 vspfilename2 [/options]  
```  
  
 `vspfilename1 and vspfilename2` geçerli olmalıdır. *vsp* veya. *vsps* dosyaları.  
  
## <a name="symbol-files"></a>Simge dosyaları  
 İşlev adları ve satır numaralarını gibi sembol bilgilerini görüntülemek için VSPerfReport simgenin erişmesi (. PDB) dosyaları profili bileşenlerini ve Windows simge dosyaları. Daha fazla bilgi için bkz: [nasıl yapılır: simge dosyası konumlarını komut satırından belirtme](../profiling/how-to-specify-symbol-file-locations-from-the-command-line.md).  
  
## <a name="general-report-options"></a>Genel rapor seçenekleri  
 Aşağıdaki tablo genel raporun biçimlendirme seçenekleri ve bildirilecek verileri seçme seçenekleri açıklar.  
  
|Seçenekler|Açıklama|  
|-------------|-----------------|  
|**U**|Rapor çıktısı ve yeniden yönlendirilen konsol Çıkışı Unicode olarak yazılır. İlk seçeneği belirtilmelidir.|  
|**Özet:**[*türleri*]|Rapor bir veya daha fazla türleri oluşturur.<br /><br /> -   `All` -Tüm rapor türleri oluşturulur.<br />-   `CallerCallee` -işlevleri arasında üst/alt ilişkiler.<br />-   `Function` -işlevleri çağrılır.<br />-   `CallTree` -çağrılan işlevler hiyerarşisi.<br />-   `Counter` -tüm işaretleri birlikte Windows performans sayacı değerlerini.<br />-   `Ip` -profili yönergeler.<br />-   `Life` -(ayırma veri toplanan olduğunda kullanılabilir.) ayrılmış nesnelerin ömrü<br />-   `Line` Kaynak kodu satır profil verileri.<br />-   `Header` -Rapor dosyası üst bilgileri içerir.<br />-   `Mark` tüm işaretler.<br />-   `Module` -profili modüller.<br />-   `Process` -profili işlemler.<br />-   `Thread` -profili iş parçacığı sayısı.<br />-   `Type` -türleri ayrılmış.<br />-   `Contention` -Kaynak çekişmeleri.<br />-   `RuleWarnings` -Performans kuralı sorunları<br />-   `ETW` -tüm olay izleme için Windows (ETW) olayları toplanan profil çalıştırın. .Etl veri dosyası, özgün konumuna veya .vsp veya .vsps dosyasını içeren dizinde olması gerekir.|  
|**Xml**|Çıktı rapor XML biçiminde.|  
|**CallTrace**|İşlev girdisi ve çıkar, ETW olayları ve işaretleri listesini oluşturur.|  
|**ClearPackedSymbols**|Daha önce katıştırılmış simgeleri bir profil oluşturucu veri dosyasından kaldırır. Paket sembolleri ikinci çalıştırmadan önce bu komutu çalıştırmak zaman.|  
|**SymbolPath:** `path`|Bir veya daha fazla arama yolları veya de Profil Oluşturucu veri dosyası simgelerini içeren simge sunucuları belirtir.|  
|**DebugSymPath**|Simgeler ve olup bulunan Aranan konumları listeler. Bu seçenek, simge çözümleme sorunlarını gidermek kullanışlıdır.|  
|**Paket sembolleri**|Kaydeder simgeleri profil oluşturma veri (.vsp) dosyasına dolayısıyla bu simgeyi (. *pdb*) dosyalarını, çözümlemesi için gerekli değildir.|  
|**Çıkış:** *yolu*&#124;*dosya adı*|Oluşturulan rapora dosyaları için alternatif bir konum belirtir. Varsayılan olarak, raporları geçerli dizinde oluşturulur.|  
|**SummaryFile**|Analiz etmek ve .vsps Özet dosyasında çözümlenen bilgilerini kaydedin.|  
|**PrintMarks**|Adları ve damgaları tüm işaretleri için belirtilen rapor dosyasında gösterir.|  
|**?**|Kullanım bilgilerini görüntüler.|  
|**NoLogo**|Raporu çalıştırırken sürüm bilgilerini gizler.|  
|**UserRulesDirectory**|[Henüz uygulanmadı] dizin içeren kullanıcı tanımlı performans kurallarını belirtir.|  
  
## <a name="filter-options"></a>Filtre Seçenekleri  
 Aşağıdaki tabloda kullanılabilir verileri filtrelemek için seçenekleri açıklar.  
  
|Seçenekler|Açıklama|  
|-------------|-----------------|  
|**JustMyCode**[**:**[`caller`] [,`callee`]]|Yalnızca kullanıcı uygulama işlev çağrılarını gösterir; Sistem çağrıları gizleyin.<br /><br /> -Herhangi bir parametre - tüm sistem işlevleri gizleyin.<br />-   `caller` -Uygulama işlevlerini çağırma sistem işlevleri bir düzeyini gösterir.<br />-   `callee` -bir kullanıcı uygulama işlevleri tarafından çağrılan sistem işlevleri düzeyini gösterir.|  
|**StartTime:**[*değeri*]|Yalnızca değerden (milisaniye cinsinden.) toplanan verileri göster|  
|**EndTime:**[*değeri*]|Yalnızca değeri (milisaniye cinsinden.) önce toplanan verileri göster|  
|**FilterFile:** `VSPFFile`|Visual Studio performans raporu penceresinden oluşturulan bir filtre dosyasının konumunu belirtir.|  
|**MsFilter:**[*starttime, süre*]|Yalnızca verileri gösterir `starttime` uzunluğu kadar `duration` (milisaniye cinsinden.)|  
|**İşlem:**[*PID*]|Yalnızca belirtilen işlem verilerini gösterir.|  
|**İş parçacığı:**[*ThreadID*]|Yalnızca belirtilen iş parçacığı verileri gösterir.|  
|**İş parçacığı:**[*ThreadID, ProcessId*]|Yalnızca belirtilen iş parçacığı belirtilen işlemle ilişkili verileri gösterir.|  
  
## <a name="difference-report-options"></a>Fark rapor seçenekleri  
 Aşağıdaki tabloda rapor dosyalarını karşılaştırma için seçenekleri açıklar.  
  
|Seçenekler|Açıklama|  
|-------------|-----------------|  
|**fark**  `vspfile1 vspfile2`|İki rapor dosyalarını karşılaştırma (. *Vsp* veya. *vsps*) dosyaları. Özet Seçenekleri fark seçeneği kullanılarak yoksayılacak.|  
|**Fark:**[*değeri*]|Bu Eşik değerin altına iki değerler arasındaki farkın göz ardı edilir. Ayrıca, bu eşiğin altında değerlerle yeni veriler gösterilmez.|  
|**DiffTable:**[*tablename*]|Dosyaları karşılaştırmak için bu belirli tabloyu kullanın. İşlevler tablosuna varsayılandır.|  
|**DiffColumn:**[*columnname*]|Bu belirli sütun karşılaştırma değerlerini kullanın. Varsayılan özel örnekler yüzde sütundur.|  
|**QueryDiffTables**|Geçerli tablolar ve sütunlar sağlanan iki rapor dosyaların listesi.|  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Performans rapor görünümleri](../profiling/performance-report-views.md)