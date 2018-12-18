---
title: SccSetOption işlevi | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- SccSetOption
helpviewer_keywords:
- SccSetOption function
ms.assetid: 4b5e6666-c24c-438a-a9df-9c52f58f8175
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 4da2906ad0881ef93f0bddf171a43f3229c3f0c0
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49813845"
---
# <a name="sccsetoption-function"></a>SccSetOption İşlevi
Bu işlev, kaynak denetimi eklentisi davranışını denetleyen seçenekler ayarlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
SCCRTN SccSetOption(  
   LPVOID pvContext,  
   LONG   nOption,  
   LONG   dwVal  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 pvContext  
 [in] Kaynak Denetimi Eklentisi bağlam yapısı.  
  
 nOption  
 [in] Ayarlanan seçeneği.  
  
 dwVal  
 [in] Seçenek için ayarlar.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Kaynak Denetimi Eklentisi uygulanması bu işlev, aşağıdaki değerlerden birini döndürmesi beklenir:  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|SCC_OK|Seçenek başarıyla ayarlandı.|  
|SCC_I_SHARESUBPROJOK|Döndürülen if `nOption` olan `SCC_OPT_SHARESUBPROJ` ve kaynak denetimi eklentisi hedef klasörü ayarlanmış bir IDE sağlar.|  
|SCC_E_OPNOTSUPPORTED|Seçenek ayarlanmadı ve üzerinde kullanılmamalıdır.|  
  
## <a name="remarks"></a>Açıklamalar  
 IDE, kaynak denetimi eklentisi davranışını denetlemek için bu işlevi çağırır. İlk parametre `nOption`, ikinci ayarlanan değer gösterir `dwVal`, söz konusu değerle yapmanız gerekenler gösterir. Eklentisi ile ilgili bu bilgileri depolayan bir `pvContext``,` çağırdıktan sonra bu işlevi çağırmanız gerekir IDE şekilde [Sccınitialize](../extensibility/sccinitialize-function.md) (ancak mutlaka sonra yapılan her çağrı [SccOpenProject](../extensibility/sccopenproject-function.md)).  
  
 Seçenekleri ve bunların değerlerini özeti:  
  
|`nOption`|`dwValue`|Açıklama|  
|---------------|---------------|-----------------|  
|`SCC_OPT_EVENTQUEUE`|`SCC_OPT_EQ_DISABLE`<br /><br /> `SCC_OPT_EQ_ENABLE`|Etkinleştirir/devre dışı bırakır, olay sıraya alma arka plan.|  
|`SCC_OPT_USERDATA`|Rastgele değer|Geçirilecek bir kullanıcı değeri belirtir [OPTNAMECHANGEPFN](../extensibility/optnamechangepfn.md) geri çağırma işlevi.|  
|`SCC_OPT_HASCANCELMODE`|`SCC_OPT_HCM_NO`<br /><br /> `SCC_OPT_HCM_YES`|IDE şu anda bir işlem iptal ediliyor destekleyip desteklemediğini belirtir.|  
|`SCC_OPT_NAMECHANGEPFN`|İşaretçi [OPTNAMECHANGEPFN](../extensibility/optnamechangepfn.md) geri çağırma işlevi|Bir ad değişikliği geri çağırma işlevine bir işaretçi ayarlar.|  
|`SCC_OPT_SCCCHECKOUTONLY`|`SCC_OPT_SCO_NO`<br /><br /> `SCC_OPT_SCO_YES`|Dosyaları el ile (kaynak denetimi kullanıcı arabirimi aracılığıyla) dışında denetleme veya yoksa bunlar yalnızca kaynak denetimi eklentisi kullanıma alınması gerekir IDE izin verip vermediğini belirtir.|  
|`SCC_OPT_SHARESUBPROJ`|Yok|Kaynak Denetimi Eklentisi yerel proje klasörü belirtmek IDE izin veriyorsa, eklenti döndürür `SCC_I_SHARESUBPROJOK`.|  
  
## <a name="sccopteventqueue"></a>SCC_OPT_EVENTQUEUE  
 Varsa `nOption` olduğu `SCC_OPT_EVENTQUEUE`, IDE devre dışı bırakma (yeniden etkinleştirerek veya) arka plan işlemesi. Örneğin, bir derleme sırasında kaynak denetimi eklentisi-boşta işleme herhangi bir türde durdurmak için IDE taramasını sağlayabilirsiniz. Derlemeden sonra eklentinin olay sırası güncel tutmak için arka plan işlemesi yeniden etkinleştirmeniz. Karşılık gelen `SCC_OPT_EVENTQUEUE` değerini `nOption`, olası iki değeri vardır `dwVal`, yani `SCC_OPT_EQ_ENABLE` ve `SCC_OPT_EQ_DISABLE`.  
  
## <a name="sccopthascancelmode"></a>SCC_OPT_HASCANCELMODE  
 Varsa değerini `nOption` olduğu `SCC_OPT_HASCANCELMODE`, uzun işlemleri iptal etmek kullanıcıların bir IDE sağlar. Ayarı `dwVal` için `SCC_OPT_HCM_NO` (varsayılan), IDE yok iptal modu sahip olduğunu gösterir. Kaynak Denetimi Eklentisi, iptal etmek kullanıcı istiyorsa, kendi iptal düğmesi sağlaması gerekir. `SCC_OPT_HCM_YES` IDE eklenti SCC kendi iptal düğmesi görüntülenecek gerek kalmayacak şekilde, bir işlem iptal etme yeteneğini sağladığını gösterir. IDE ayarlarsa `dwVal` için `SCC_OPT_HCM_YES`, yanıt vermek için hazırlanmış `SCC_MSG_STATUS` ve `DOCANCEL` gönderilen iletileri `lpTextOutProc` geri çağırma işlevi (bkz [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)). IDE, bu değişken ayarlı değil, eklenti bu iki iletiyle göndermemelidir.  
  
## <a name="sccoptnamechangepfn"></a>SCC_OPT_NAMECHANGEPFN  
 NOption ayarlanırsa `SCC_OPT_NAMECHANGEPFN`ve kaynak denetimi eklentisi ve IDE vermek, eklenti gerçekten yeniden adlandırabilir veya kaynak denetimi işlemi sırasında dosya taşıma. `dwVal` Bir işlev işaretçisi türü için ayarlanacak [OPTNAMECHANGEPFN](../extensibility/optnamechangepfn.md). Kaynak denetimi işlemi sırasında eklenti üç parametre geçirerek, bu işlevi çağırabilirsiniz. Bu, eski adıyla (tam yolu) bir dosyanın yeni adıyla (tam nitelenmiş bir yol), dosya ve IDE ile ilgisi olan bilgi işaretçisi vardır. IDE üzerinde son this işaretçisi çağırarak gönderir `SccSetOption` ile `nOption` kümesine `SCC_OPT_USERDATA`, ile `dwVal` verilere işaret eden. Bu işlev için destek, isteğe bağlıdır. VSSCI Tak-kullanır bu özelliği, işlev işaretçisi ve kullanıcı verisi değişkenleri başlatmalıdır `NULL`, ve onu bir verildi sürece Yeniden Adlandır işlevi çağırmamalıdır. Yanıt için yeni bir çağrı olarak değiştirmek için ya da verilen değerini tutmak için de hazırlanmalı `SccSetOption`. Bu ortasında bir kaynak denetimi komutu işlemi yapılmaz, ancak komut arasında gerçekleşebilir.  
  
## <a name="sccoptscccheckoutonly"></a>SCC_OPT_SCCCHECKOUTONLY  
 NOption ayarlanırsa `SCC_OPT_SCCCHECKOUTONLY`, açık olan proje dosyaları hiçbir zaman el ile kaynak denetimi sisteminizin kullanıcı arabirimi aracılığıyla kullanıma alınmasını IDE belirten. Bunun yerine, dosyaları yalnızca kaynak denetimi eklentisi IDE denetiminde aracılığıyla kullanıma alınması. Varsa `dwValue` ayarlanır `SCC_OPT_SCO_NO`, dosyaları normalde eklenti tarafından değerlendirilip ve kaynak denetimi kullanıcı Arabirimi kullanıma alınabildiğinden anlamına gelir. Varsa `dwValue` ayarlanır `SCC_OPT_SCO_YES`, ardından yalnızca eklenti dosyaları kullanıma izin verilmez ve kaynak denetimi sisteminizin UI olmayan çağrılmalıdır. Bu, "yalnızca IDE kullanıma mantıklı sözde files" IDE burada olabilir durumlarda içindir.  
  
## <a name="sccoptsharesubproj"></a>SCC_OPT_SHARESUBPROJ  
 Varsa`nOption` ayarlanır `SCC_OPT_SHARESUBPROJ`, kaynak denetimi eklentisi belirtilen yerel bir klasöre dosyalar kaynak denetiminden eklerken kullanıp kullanamayacağını IDE test ediyor. Değerini `dwVal` parametresi önemli değildir, bu durumda. Eklenti dosyaları ekleneceği kaynağından yerel hedef klasörü belirtmek IDE izin veriyorsa denetimi [SccAddFromScc](../extensibility/sccaddfromscc-function.md) çağrılır, ardından eklentiyi döndürmelidir `SCC_I_SHARESUBPROJOK` olduğunda `SccSetOption` işlevi çağrılır. IDE ardından kullanır `lplpFileNames` parametresinin `SccAddFromScc` işlevi hedef klasörde geçirilecek. Eklenti kaynak denetiminden eklenen dosyaları yerleştirmek için hedef klasör kullanır. Eklenti oluşmazsa `SCC_I_SHARESUBPROJOK` olduğunda `SCC_OPT_SHARESUBPROJ` seçeneği ayarlanır, IDE eklenti yalnızca geçerli yerel klasör içinde dosyalar eklemeniz mümkün olduğunu varsayar.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Kaynak Denetimi Eklentisi API işlevleri](../extensibility/source-control-plug-in-api-functions.md)   
 [Sccınitialize](../extensibility/sccinitialize-function.md)   
 [SccOpenProject](../extensibility/sccopenproject-function.md)   
 [SccAddFromScc](../extensibility/sccaddfromscc-function.md)   
 [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)   
 [OPTNAMECHANGEPFN](../extensibility/optnamechangepfn.md)