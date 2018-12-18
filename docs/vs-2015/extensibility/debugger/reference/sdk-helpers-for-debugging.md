---
title: Hata ayıklama için SDK Yardımcıları | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- dbgmetric.lib
- registry, Debugging SDK
- Debugging SDK, registry locations
- dbgmetric.h
- metrics [Debugging SDK]
ms.assetid: 80a52e93-4a04-4ab2-8adc-a7847c2dc20b
caps.latest.revision: 29
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 904ac14433bf6b7b839a4fe634175a7f583e27ab
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51772189"
---
# <a name="sdk-helpers-for-debugging"></a>Hata Ayıklama için SDK Yardımcıları
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Bu işlevler ve bildirimleri C++'da uygulama, hata ayıklama altyapısı, ifade değerlendiricilerini ve sembol sağlayıcıları için genel yardımcı işlevlerdir.  
  
> [!NOTE]
>  Şu anda bu işlevler ve bildirimleri'hiçbir yönetilen sürümü vardır.  
  
## <a name="overview"></a>Genel Bakış  
 Visual Studio tarafından kullanılacak sırayla hata ayıklama altyapısı, ifade değerlendiricilerini ve sembol sağlayıcıları için kayıtlı olmaları gerekir. Bu kayıt defteri alt anahtarları ve girişleri, aksi takdirde "ölçümleri ayarlama". bilinen ayarlayarak yapılır Aşağıdaki genel işlevleri, bu ölçümleri güncelleştirme işlemini kolaylaştırmak için tasarlanmıştır. Bu işlevler tarafından güncelleştirilir her bir kayıt defteri alt anahtarı düzenini öğrenmek için kayıt defteri konumlarının bölümüne bakın.  
  
## <a name="general-metric-functions"></a>Genel ölçüm işlevleri  
 Hata ayıklama motoru tarafından kullanılan genel işlevleri şunlardır. İşlevler için ifade değerlendiricilerini özel olarak tasarlanan ve sembol sağlayıcıları daha sonra ayrıntıları verilecek.  
  
### <a name="getmetric-method"></a>GetMetric yöntemi  
 Ölçüm değeri kayıt defterinden alır.  
  
```cpp#  
HRESULT GetMetric(  
   LPCWSTR pszMachine,  
   LPCWSTR pszType,  
   REFGUID guidSection,  
   LPCWSTR pszMetric,  
   DWORD * pdwValue,  
   LPCWSTR pszAltRoot  
);  
```  
  
|Parametre|Açıklama|  
|---------------|-----------------|  
|pszMachine|[in] Bir kayıt yazılır büyük olasılıkla uzak makine adını (`NULL` yerel makine anlamına gelir).|  
|pszType|[in] Ölçüm türlerinden biri.|  
|guidSection|[in] Belirli altyapısını, değerlendirici, özel durum, vb. GUİD'si. Bu, belirli bir öğe için bir ölçüm türü altında bir alt belirtir.|  
|pszMetric|[in] Alınacağı ölçümü. Bu, belirli bir değerin adına karşılık gelir.|  
|pdwValue|[in] Ölçüm değeri depolama konumu. DWORD (Bu örnekteki), bir BSTR, bir GUID veya GUID'leri dizisini döndürebilen GetMetric birkaç türü vardır.|  
|pszAltRoot|[in] Kullanmak için bir alternatif kayıt defteri kökü. Kümesine `NULL` varsayılan kullanmak için.|  
  
### <a name="setmetric-method"></a>SetMetric yöntemi  
 Kayıt defterinde belirtilen ölçüm değeri ayarlar.  
  
```cpp#  
HRESULT SetMetric(  
         LPCWSTR pszType,  
         REFGUID guidSection,  
         LPCWSTR pszMetric,  
   const DWORD   dwValue,  
         bool    fUserSpecific,  
         LPCWSTR pszAltRoot  
);  
```  
  
|Parametre|Açıklama|  
|---------------|-----------------|  
|pszType|[in] Ölçüm türlerinden biri.|  
|guidSection|[in] Belirli altyapısını, değerlendirici, özel durum, vb. GUİD'si. Bu, belirli bir öğe için bir ölçüm türü altında bir alt belirtir.|  
|pszMetric|[in] Alınacağı ölçümü. Bu, belirli bir değerin adına karşılık gelir.|  
|dwValue|[in] Ölçüm değeri depolama konumu. DWORD (Bu örnekte), bir BSTR, bir GUID veya bir dizi GUID'leri depolayabilirsiniz SetMetric birkaç türü vardır.|  
|fUserSpecific|[in] Ölçüm kullanıcıya özgü ise ve yerel makine hive yerine kullanıcının hive yazılmalıdır TRUE.|  
|pszAltRoot|[in] Kullanmak için bir alternatif kayıt defteri kökü. Kümesine `NULL` varsayılan kullanmak için.|  
  
### <a name="removemetric-method"></a>RemoveMetric yöntemi  
 Belirtilen Ölçüm kayıt defterinden kaldırır.  
  
```cpp#  
HRESULT RemoveMetric(  
   LPCWSTR pszType,  
   REFGUID guidSection,  
   LPCWSTR pszMetric,  
   LPCWSTR pszAltRoot  
);  
```  
  
|Parametre|Açıklama|  
|---------------|-----------------|  
|pszType|[in] Ölçüm türlerinden biri.|  
|guidSection|[in] Belirli altyapısını, değerlendirici, özel durum, vb. GUİD'si. Bu, belirli bir öğe için bir ölçüm türü altında bir alt belirtir.|  
|pszMetric|[in] Kaldırılacak ölçümü. Bu, belirli bir değerin adına karşılık gelir.|  
|pszAltRoot|[in] Kullanmak için bir alternatif kayıt defteri kökü. Kümesine `NULL` varsayılan kullanmak için.|  
  
### <a name="enummetricsections-method"></a>EnumMetricSections yöntemi  
 Kayıt defteri çeşitli ölçüm bölümlerde numaralandırır.  
  
```cpp#  
HRESULT EnumMetricSections(  
   LPCWSTR pszMachine,  
   LPCWSTR pszType,  
   GUID *  rgguidSections,  
   DWORD * pdwSize,  
   LPCWSTR pszAltRoot  
);  
```  
  
|Parametre|Açıklama|  
|---------------|-----------------|  
|pszMachine|[in] Bir kayıt yazılır büyük olasılıkla uzak makine adını (`NULL` yerel makine anlamına gelir).|  
|pszType|[in] Ölçüm türlerinden biri.|  
|rgguidSections|[out içinde] Doldurulacak GUID'leri ön tahsis dizisi.|  
|pdwSize|[in] Depolanabilir GUID'leri sayısı `rgguidSections` dizisi.|  
|pszAltRoot|[in] Kullanmak için bir alternatif kayıt defteri kökü. Kümesine `NULL` varsayılan kullanmak için.|  
  
## <a name="expression-evaluator-functions"></a>İfade değerlendirici işlevleri  
  
|İşlev|Açıklama|  
|--------------|-----------------|  
|GetEEMetric|Ölçüm değeri kayıt defterinden alır.|  
|SetEEMetric|Kayıt defterinde belirtilen ölçüm değeri ayarlar.|  
|RemoveEEMetric|Belirtilen Ölçüm kayıt defterinden kaldırır.|  
|GetEEMetricFile|Bir dosya adı belirtilen ölçüm alır ve bir dize olarak dosyanın içeriği döndüren yükler.|  
  
## <a name="exception-functions"></a>Özel durum işlevleri  
  
|İşlev|Açıklama|  
|--------------|-----------------|  
|GetExceptionMetric|Ölçüm değeri kayıt defterinden alır.|  
|SetExceptionMetric|Kayıt defterinde belirtilen ölçüm değeri ayarlar.|  
|RemoveExceptionMetric|Belirtilen Ölçüm kayıt defterinden kaldırır.|  
|RemoveAllExceptionMetrics|Tüm özel durum ölçümleri kayıt defterinden kaldırır.|  
  
## <a name="symbol-provider-functions"></a>Sembol sağlayıcısı işlevleri  
  
|İşlev|Açıklama|  
|--------------|-----------------|  
|GetSPMetric|Ölçüm değeri kayıt defterinden alır.|  
|SetSPMetric|Kayıt defterinde belirtilen ölçüm değeri ayarlar.|  
|RemoveSPMetric|Belirtilen Ölçüm kayıt defterinden kaldırır.|  
  
## <a name="enumeration-functions"></a>Numaralandırma işlevleri  
  
|İşlev|Açıklama|  
|--------------|-----------------|  
|EnumMetricSections|Belirtilen bir ölçüm türü için tüm ölçümleri numaralandırır.|  
|EnumDebugEngine|Kaydedilen hata ayıklama motorlarını numaralandırır.|  
|EnumEEs|Kayıtlı ifade değerlendiricilerini numaralandırır.|  
|EnumExceptionMetrics|Tüm özel durum ölçümleri numaralandırır.|  
  
## <a name="metric-definitions"></a>Ölçüm tanımları  
 Bu tanımları için önceden tanımlanmış ölçüm adları kullanılabilir. Çeşitli kayıt defteri anahtarları ve değer adlarını ve geniş karakter dizesi olarak tanımlanmış olan tüm adlar karşılık gelir: Örneğin, `extern LPCWSTR metrictypeEngine`.  
  
|Önceden tanımlanmış bir metrik türleri|Açıklama: Temel anahtar için...|  
|-----------------------------|---------------------------------------|  
|metrictypeEngine|Tüm altyapısı ölçümleri hata ayıklayın.|  
|metrictypePortSupplier|Tüm bağlantı noktası tedarikçi ölçümleri.|  
|metrictypeException|Tüm özel durum ölçümleri.|  
|metricttypeEEExtension|Tüm ifade değerlendirici uzantıları.|  
  
|Hata ayıklama altyapısı özellikleri|Açıklama|  
|-----------------------------|-----------------|  
|metricAddressBP|Adres kesme noktaları için destek belirtmek için sıfır olarak ayarlayın.|  
|metricAlwaysLoadLocal|Her zaman yerel olarak hata ayıklama altyapısı yüklemek için sıfır olarak ayarlayın.|  
|metricLoadInDebuggeeSession|KULLANILMIYOR|  
|metricLoadedByDebuggee|Hata ayıklama altyapısı her zaman hata ayıklanan programa veya ile yükleneceğini belirten belirtmek için sıfır olarak ayarlayın.|  
|metricAttach|Mevcut programlara ek için destek belirtmek için sıfır olarak ayarlayın.|  
|metricCallStackBP|Çağrı yığını kesme noktalarını desteği belirtmek için sıfır olarak ayarlayın.|  
|metricConditionalBP|Koşullu kesme noktaları ayarı için destek belirtmek için sıfır olarak ayarlayın.|  
|metricDataBP|Verilerde yapılan değişiklikler üzerinde kesme noktaları ayarı için destek belirtmek için sıfır olarak ayarlayın.|  
|metricDisassembly|Ayrıştırılmış kodu listesini üretimi için destek belirtmek için sıfır olarak ayarlayın.|  
|metricDumpWriting|Döküm (bir çıktı cihazına bellek dökümü alma) yazma desteği belirtmek için sıfır olarak ayarlayın.|  
|metricENC|Düzenle ve devam et desteğini belirtmek için sıfır olarak ayarlayın. **Not:** bir özel hata ayıklama altyapısı hiçbir zaman bu ayarlamanız gerekir ya da her zaman 0 olarak ayarlamanız gerekir.|  
|metricExceptions|Özel durumlar için destek belirtmek için sıfır olarak ayarlayın.|  
|metricFunctionBP|Adlı kesme (belirli bir işlev adı çağrıldığında kesebileceğiniz kesme noktaları) için destek belirtmek için sıfır olarak ayarlayın.|  
|metricHitCountBP|Kesme noktaları (yalnızca belirli sayıda bir kez isabet olan sonra tetiklenen kesme noktaları) "nokta isabet" ayarı için destek belirtmek için sıfır olarak ayarlayın.|  
|metricJITDebug|(Çalışan bir işlem olarak bir özel durum oluştuğunda hata ayıklayıcının başlatılır) just-ın-time hata ayıklama desteği belirtmek için sıfır olarak ayarlayın.|  
|metricMemory|KULLANILMIYOR|  
|metricPortSupplier|Biri uygulanmışsa, bağlantı noktası sağlayıcısı CLSID değeri için bunu ayarlayın.|  
|metricRegisters|KULLANILMIYOR|  
|metricSetNextStatement|(Hangi Ara deyimler yürütme atlar) sonraki deyimi ayarlamak için destek belirtmek için sıfır olarak ayarlayın.|  
|metricSuspendThread|İş parçacığı yürütmesi askıya almak için destek belirtmek için sıfır olarak ayarlayın.|  
|metricWarnIfNoSymbols|Sembol varsa kullanıcı bilgilendirilmemeli belirtmek için sıfır olarak ayarlayın.|  
|metricProgramProvider|Bu program sağlayıcısı CLSID'sini ayarlayın.|  
|metricAlwaysLoadProgramProviderLocal|Bu program sağlayıcı her zaman yerel olarak yüklenmiş olması gerektiğini belirtmek için sıfır olmayan bir ayarlayın.|  
|metricEngineCanWatchProcess|Bu program sağlayıcı yerine olayları işlemek için hata ayıklama altyapısı izleyecek belirtmek için sıfır olarak ayarlayın.|  
|metricRemoteDebugging|Bu uzaktan hata ayıklama desteği belirtmek için sıfır olarak ayarlayın.|  
|metricEncUseNativeBuilder|Düzenle ve devam Yöneticisi hata ayıklama altyapısının encbuild.dll Düzenle ve devam et için oluşturulacak kullanması gerektiğini belirtmek için için sıfır olmayan bir ayarlayın. **Not:** bir özel hata ayıklama altyapısı hiçbir zaman bu ayarlamanız gerekir ya da her zaman 0 olarak ayarlamanız gerekir.|  
|metricLoadUnderWOW64|Sıfır dışında hata ayıklama altyapısı WOW altında hata ayıklanan işlem içindeki bir 64-bit işlem hata ayıklama sırasında yükleneceğini göstermek için bunu; Aksi takdirde, Visual Studio işlemindeki (Bu WOW64 altında çalışan) hata ayıklama altyapısı yüklenir.|  
|metricLoadProgramProviderUnderWOW64|Bu program sağlayıcısı WOW altında 64 bitlik bir işlem hata ayıklama sırasında hata ayıklanan işlemin yüklenmesi gerektiğini belirtmek için sıfır olmayan ayarlayın; Aksi takdirde Visual Studio işleminde yüklenir.|  
|metricStopOnExceptionCrossingManagedBoundary|Bu işlem, yönetilen ve yönetilmeyen kod sınırları arasında işlenmeyen bir özel durum oluşturulursa durması gerektiğini belirtmek için sıfır olarak ayarlayın.|  
|metricAutoSelectPriority|Otomatik Seçim hata ayıklama altyapısı (yüksek değerler eşittir daha yüksek öncelik) için bir öncelik için bunu ayarlayın.|  
|metricAutoSelectIncompatibleList|Yok sayılacak hata ayıklama motorlarını GUID'leri otomatik seçiminde belirtin girişlerini içeren kayıt defteri anahtarı. Bu girişler bir sayı (0, 1, 2 vb.) içeren bir dize olarak ifade edilen bir GUID.|  
|metricIncompatibleList|Bu hata ayıklama altyapısı ile uyumsuz hata ayıklama motorlarını GUID'leri belirtme girişlerini içeren kayıt defteri anahtarı.|  
|metricDisableJITOptimization|Bu tam zamanında iyileştirmeler (için yönetilen kod) hata ayıklama sırasında devre dışı bırakılmalıdır olduğunu belirtmek için sıfır olarak ayarlayın.|  
  
|İfade değerlendirici özellikleri|Açıklama|  
|-------------------------------------|-----------------|  
|metricEngine|Bu, belirtilen ifade değerlendiricisi destekleyen hata ayıklama altyapısı sayısını tutar.|  
|metricPreloadModules|Bu ifade değerlendiricisi karşı bir programı başlatıldığında modülleri yüklenmiş olduğunu belirtmek için sıfır olarak ayarlayın.|  
|metricThisObjectName|Bu, "Bu" nesnesinin adına ayarlayın.|  
  
|İfade değerlendirici uzantı özellikleri|Açıklama|  
|-----------------------------------------------|-----------------|  
|metricExtensionDll|Bu uzantının desteklediği DLL'in adı.|  
|metricExtensionRegistersSupported|Desteklenen kayıtları listesi.|  
|metricExtensionRegistersEntryPoint|Yazmaçları erişmek için giriş noktası'nı tıklatın.|  
|metricExtensionTypesSupported|Desteklenen türleri listesi.|  
|metricExtensionTypesEntryPoint|Türleri erişmek için giriş noktası'nı tıklatın.|  
  
|Bağlantı noktası sağlayıcısı özellikleri|Açıklama|  
|------------------------------|-----------------|  
|metricPortPickerCLSID|(Bir iletişim kutusu kullanıcının bağlantı noktalarını seçin ve hata ayıklama için kullanılacak bağlantı noktası eklemek için kullanabilirsiniz) bağlantı noktası Seçici CLSID değeri.|  
|metricDisallowUserEnteredPorts|Kullanıcı tarafından girilen bağlantı noktaları için bağlantı noktası sağlayıcısı eklediyseniz sıfır olmayan (Bu bağlantı noktası Seçici iletişim kutusu temelde salt okunur yapar).|  
|metricPidBase|İşlem kimliklerini tahsis ederken bağlantı sağlayıcı tarafından kullanılan temel işlem kimliği.|  
  
|Önceden tanımlanmış SP Store türleri|Açıklama|  
|-------------------------------|-----------------|  
|storetypeFile|Sembolleri ayrı bir dosyada depolanır.|  
|storetypeMetadata|Simgeleri bir derlemede meta veri olarak depolanır.|  
  
|Çeşitli özellikler|Açıklama|  
|------------------------------|-----------------|  
|metricShowNonUserCode|Bu nonuser kod göstermek için sıfır olarak ayarlayın.|  
|metricJustMyCodeStepping|Bu atlama yalnızca kullanıcı kodunda oluşabilir belirtmek için sıfır olarak ayarlayın.|  
|metricCLSID|Bir nesne belirli bir ölçüm türün CLSID değeri.|  
|MetricName|Ölçüm belirli bir türdeki bir nesne için kolay ad.|  
|metricLanguage|Dil adı.|  
  
## <a name="registry-locations"></a>Kayıt defteri konumları  
 Ölçümleri okuma ve kayıt defterinde, özellikle de yazılmış `VisualStudio` alt.  
  
> [!NOTE]
>  Çoğu zaman, HKEY_LOCAL_MACHINE anahtarı ölçümleri yazılır. Ancak, bazen HKEY_CURRENT_USER hedef anahtar olacaktır. Her iki anahtarı Dbgmetric.lib işler. Bir ölçüm alırken HKEY_CURRENT_USER arar. ilk ve HKEY_LOCAL_MACHINE. Bunu bir ölçüm ayarlanırken, bir parametre kullanmak için hangi üst düzey anahtar belirtir.  
  
 *[kayıt defteri anahtarı]*\  
  
 `Software`\  
  
 `Microsoft`\  
  
 `VisualStudio`\  
  
 *[sürüm kök]*\  
  
 *[ölçüm kök]*\  
  
 *[ölçüm türü]*\  
  
 *[ölçü] = [ölçüm değeri]*  
  
 *[ölçü] = [ölçüm değeri]*  
  
 *[ölçü] = [ölçüm değeri]*  
  
|Yer tutucu|Açıklama|  
|-----------------|-----------------|  
|*[kayıt defteri anahtarı]*|`HKEY_CURRENT_USER` veya `HKEY_LOCAL_MACHINE`.|  
|*[sürüm kök]*|Visual Studio sürümü (örneğin, `7.0`, `7.1`, veya `8.0`). Ancak, bu kök ayrıca kullanılarak değiştirilebilir **/rootsuffix** geçin **devenv.exe**. VSIP için bu genellikle bir değiştiricidir **Exp**, sürüm kök, örneğin, 8.0Exp olacaktır.|  
|*[ölçüm kök]*|Bu `AD7Metrics` veya `AD7Metrics(Debug)`dbgmetric.lib hata ayıklama sürümünü kullanılıp kullanılmadığını bağlı olarak. **Not:** dbgmetric.lib kullanılır olup olmadığına, hata ayıklama ve yayın arasındaki farklar varsa bu adlandırma kuralı için bağlı kayıt defterinde yansıtılan sürümleri.|  
|*[ölçüm türü]*|Yazılacak ölçüm türü: `Engine`, `ExpressionEvaluator`, `SymbolProvider`vb. Bunlar tüm dbgmetric.h olduğu gibi tanımlanır `metricTypeXXXX`burada `XXXX` belirli tür adıdır.|  
|*[ölçü]*|Ölçüm ayarlamak için bir değer atanması için bir giriş adı. Ölçüm gerçek kuruluş Ölçüm türüne bağlıdır.|  
|*[ölçüm değeri]*|Ölçüm için atanan değer. Değeri (dize, sayı, vb.) olmamalıdır türüne ölçüme göre değişir.|  
  
> [!NOTE]
>  Tüm GUID biçiminde depolanır `{GUID}`. Örneğin: `{123D150B-FA18-461C-B218-45B3E4589F9B}`  
  
### <a name="debug-engines"></a>Hata ayıklama altyapıları  
 Aşağıdaki kayıt defteri hata ayıklama altyapıları ölçümlerinin kuruluştur. `Engine` hata ayıklama altyapısı için ölçüm türü adıdır ve karşılık gelen *[ölçüm türü]* yukarıdaki kayıt defteri alt ağacı içinde.  
  
 `Engine`\  
  
 *[altyapısı GUID]*\  
  
 `CLSID` = *[sınıf GUID]*  
  
 *[ölçü] = [ölçüm değeri]*  
  
 *[ölçü] = [ölçüm değeri]*  
  
 *[ölçü] = [ölçüm değeri]*  
  
 `PortSupplier`\  
  
 `0` = *[bağlantı noktası sağlayıcısı GUID]*  
  
 `1` = *[bağlantı noktası sağlayıcısı GUID]*  
  
|Yer tutucu|Açıklama|  
|-----------------|-----------------|  
|*[altyapısı GUID]*|Hata ayıklama altyapısı GUİD'si.|  
|*[sınıf GUID]*|Bu hata ayıklama altyapısı uygulayan sınıf GUID.|  
|*[bağlantı noktası sağlayıcısı GUID]*|Varsa, bağlantı noktası sağlayıcısı GUID. Birçok hata ayıklama altyapısı, varsayılan bağlantı noktası sağlayıcısı kullanın ve kendi tedarikçi belirtmeyin. Bu durumda, alt `PortSupplier` eksik olacaktır.|  
  
### <a name="port-suppliers"></a>Bağlantı Noktası Sağlayıcıları  
 Aşağıdaki kayıt defteri bağlantı noktası tedarikçi ölçümlerinin kuruluştur. `PortSupplier` Ölçüm türü için bağlantı noktası sağlayıcısı adıdır ve karşılık gelen *[ölçüm türü]*.  
  
 `PortSupplier`\  
  
 *[bağlantı noktası sağlayıcısı GUID]*\  
  
 `CLSID` = *[sınıf GUID]*  
  
 *[ölçü] = [ölçüm değeri]*  
  
 *[ölçü] = [ölçüm değeri]*  
  
|Yer tutucu|Açıklama|  
|-----------------|-----------------|  
|*[bağlantı noktası sağlayıcısı GUID]*|Bağlantı noktası sağlayıcısı GUID|  
|*[sınıf GUID]*|Bu bağlantı noktası sağlayıcısı uygulayan sınıf GUID|  
  
### <a name="symbol-providers"></a>Sembol sağlayıcıları  
 Aşağıdaki kayıt defteri sembol tedarikçi ölçümlerinin kuruluştur. `SymbolProvider` Sembol sağlayıcısı için ölçüm türü adıdır ve karşılık gelen *[ölçüm türü]*.  
  
 `SymbolProvider`\  
  
 *[sembol sağlayıcısı GUID]*\  
  
 `file`\  
  
 `CLSID` = *[sınıf GUID]*  
  
 *[ölçü] = [ölçüm değeri]*  
  
 *[ölçü] = [ölçüm değeri]*  
  
 `metadata`\  
  
 `CLSID` = *[sınıf GUID]*  
  
 *[ölçü] = [ölçüm değeri]*  
  
 *[ölçü] = [ölçüm değeri]*  
  
|Yer tutucu|Açıklama|  
|-----------------|-----------------|  
|*[sembol sağlayıcısı GUID]*|Sembol sağlayıcısı GUID|  
|*[sınıf GUID]*|Bu sembol sağlayıcısı uygulayan sınıf GUID|  
  
### <a name="expression-evaluators"></a>İfade değerlendiricisi  
 İfade değerlendirici ölçümleri kayıt defterinde organizasyonu verilmiştir. `ExpressionEvaluator` ifade değerlendirici ölçüm türü adı ve karşılık gelen *[ölçüm türü]*.  
  
> [!NOTE]
>  Ölçüm türü için `ExpressionEvaluator` tüm ölçüm değişiklikler ifade değerlendiricilerini için uygun bir ifade değerlendirici ölçüm işlevleri aracılığıyla geçer varsayılır gibi dbgmetric.h içinde tanımlı değil (düzenini `ExpressionEvaluator` alt biraz anahtarıdır Ayrıntılar içinde dbgmetric.lib gizlenir şekilde, karmaşık).  
  
 `ExpressionEvaluator`\  
  
 *[dil guid]*\  
  
 *[satıcı GUID]*\  
  
 `CLSID` = *[sınıf GUID]*  
  
 *[ölçü] = [ölçüm değeri]*  
  
 *[ölçü] = [ölçüm değeri]*  
  
 `Engine`\  
  
 `0` = *[hata ayıklama altyapısı GUID]*  
  
 `1` = *[hata ayıklama altyapısı GUID]*  
  
|Yer tutucu|Açıklama|  
|-----------------|-----------------|  
|*[dil guid]*|Bir dil GUİD'si|  
|*[satıcı GUID]*|Bir satıcı GUİD'si|  
|*[sınıf GUID]*|Bu ifade değerlendiricisi uygulayan sınıf GUID|  
|*[hata ayıklama altyapısı GUID]*|Bu ifade değerlendiricisi çalışır bir hata ayıklama altyapısı GUİD'si|  
  
### <a name="expression-evaluator-extensions"></a>İfade değerlendirici uzantıları  
 İfade değerlendirici uzantısı ölçümleri kayıt defterinde organizasyonu verilmiştir. `EEExtensions` Ölçüm türü için ifade değerlendirici uzantıları adıdır ve karşılık gelen *[ölçüm türü]*.  
  
 `EEExtensions`\  
  
 *[uzantısı GUID]*\  
  
 *[ölçü] = [ölçüm değeri]*  
  
 *[ölçü] = [ölçüm değeri]*  
  
|Yer tutucu|Açıklama|  
|-----------------|-----------------|  
|*[uzantısı GUID]*|İfade değerlendirici uzantı GUİD'si|  
  
### <a name="exceptions"></a>Özel Durumlar  
 Kayıt defterinde özel durumları ölçümleri organizasyonu verilmiştir. `Exception` özel durumlar için ölçüm türü adıdır ve karşılık gelen *[ölçüm türü]*.  
  
 `Exception`\  
  
 *[hata ayıklama altyapısı GUID]*\  
  
 *[özel durum türleri]*\  
  
 *[özel]*\  
  
 *[ölçü] = [ölçüm değeri]*  
  
 *[ölçü] = [ölçüm değeri]*  
  
 *[özel]*\  
  
 *[ölçü] = [ölçüm değeri]*  
  
 *[ölçü] = [ölçüm değeri]*  
  
|Yer tutucu|Açıklama|  
|-----------------|-----------------|  
|*[hata ayıklama altyapısı GUID]*|Özel durumlar destekleyen bir hata ayıklama altyapısı GUİD'si.|  
|*[özel durum türleri]*|Genel bir başlık alt işlenebilir özel durum sınıfı tanımlayan. Tipik adları **C++ özel durumlarını**, **Win32 özel durumları**, **ortak dil çalışma zamanı özel durumları**, ve **yerel çalışma zamanı denetimleri**. Bu adlar, ayrıca özel durumu kullanıcıya, belirli bir sınıf tanımlamak için kullanılır.|  
|*[özel]*|Bir özel durum için bir ad: Örneğin, **_com_error** veya **Control-Break**. Bu adlar da kullanıcıya belirli bir özel durumu tanımlamak için kullanılır.|  
  
## <a name="requirements"></a>Gereksinimler  
 Bu dosyalar bulunur [!INCLUDE[vs_dev10_ext](../../../includes/vs-dev10-ext-md.md)] SDK yükleme dizini (varsayılan olarak, *[sürücü]* \Program Visual Studio 2010 SDK\\).  
  
 Üstbilgi: includes\dbgmetric.h  
  
 Kitaplığı: libs\ad2de.lib, libs\dbgmetric.lib  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [API Başvurusu](../../../extensibility/debugger/reference/api-reference-visual-studio-debugging.md)

