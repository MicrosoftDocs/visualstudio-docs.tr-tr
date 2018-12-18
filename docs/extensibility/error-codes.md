---
title: Hata kodları | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- error codes, source control plug-ins
- source control plug-ins, error codes
- errors [Visual Studio SDK]
ms.assetid: d9cbd1c4-719b-467a-8100-333c1e146d3b
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 53287b85c74fae205874dce7fdd0ebf274bfda96
ms.sourcegitcommit: 06db1892fff22572f0b0a11994dc547c2b7e2a48
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/08/2018
ms.locfileid: "39636859"
---
# <a name="error-codes"></a>Hata kodları
Bir kaynak denetimi eklentisi API işlevi bir hata geri döndüğünde, aşağıdaki hata kodları biri olması beklenir. Tüm hataları uyarı veya bilgilendirme hatası kodları pozitif, negatif ve başarı 0'dır.  
  
|Hata Kodu|Değer|Açıklama|  
|----------------|-----------|-----------------|  
|`SCC_I_SHARESUBPROJOK`|7|İki adımda kaynak denetiminden dosyalar ekleniyor. eklentisini destekler. Daha fazla bilgi için [SccSetOption](../extensibility/sccsetoption-function.md).|  
|`SCC_I_FILEDIFFERS`|6|Yerel dosya, kaynak denetim veritabanındaki dosyanın farklıdır (örneğin, [SccDiff](../extensibility/sccdiff-function.md) bu değer döndürebilir).|  
|`SCC_I_RELOADFILE`|5|Yerel dosya kaynak denetimi işlemi sırasında değiştirildi; IDE mümkün olduğunda dosya yeniden yüklemelisiniz.|  
|`SCC_I_FILENOTAFFECTED`|4|Dosya etkilenmez.|  
|`SCC_I_PROJECTCREATED`|3|Proje kaynak denetimi işlemi sırasında oluşturulan (örneğin, bir çağrı sırasında [SccOpenProject](../extensibility/sccopenproject-function.md) olduğunda `SCC_OP_CREATEIFNEW` bayrağı belirtildi).|  
|`SCC_I_OPERATIONCANCELED`|2|İşlem iptal edildi.|  
|`SCC_I_ADV_SUPPORT`|1.|Gelişmiş seçenekleri belirtilen komut için eklentiyi destekler. Daha fazla bilgi için [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md).|  
|`SCC_OK`|0|Başarılı.|  
|`SCC_E_INITIALIZEFAILED`|-1|Hata: başlatma başarısız oldu.|  
|`SCC_E_UNKNOWNPROJECT`|-2|Hata: Proje bilinmiyor.|  
|`SCC_E_COULDNOTCREATEPROJECT`|-3|Hata: Proje oluşturulamadı.|  
|`SCC_E_NOTCHECKEDOUT`|-4|Hata: dosya kullanıma alınmadı.|  
|`SCC_E_ALREADYCHECKEDOUT`|-5|Hata: dosya kullanıma alınmış durumda.|  
|`SCC_E_FILEISLOCKED`|-6|Hata: dosya kilitlidir.|  
|`SCC_E_FILEOUTEXCLUSIVE`|-7|Hata: dosya özel olarak kullanıma alındı.|  
|`SCC_E_ACCESSFAILURE`|-8|Kaynak denetim sistemi, ağ veya çakışma sorunları nedeniyle muhtemelen erişilirken sorun oluştu. Bir yeniden deneme önerilir.|  
|`SCC_E_CHECKINCONFLICT`|-9|Hata: İade sırasında çakışma oluştu.|  
|`SCC_E_FILEALREADYEXISTS`|-10|Hata: dosya zaten var.|  
|`SCC_E_FILENOTCONTROLLED`|-11|Hata: dosya kaynak denetimi altında değil.|  
|`SCC_E_FILEISCHECKEDOUT`|-12|Hata: dosya kullanıma alındı.|  
|`SCC_E_NOSPECIFIEDVERSION`|-13|Hata: belirtilen sürümü yoktur.|  
|`SCC_E_OPNOTSUPPORTED`|-14|Hata: işlem desteklenmiyor.|  
|`SCC_E_NONSPECIFICERROR`|-15|Belirli olmayan bir hata oluştu.|  
|`SCC_E_OPNOTPERFORMED`|-16|Hata, işlem gerçekleştirilmedi.|  
|`SCC_E_TYPENOTSUPPORTED`|-17|Hata: dosya türü, örneğin, ikili, kaynak kodu denetim sistemi tarafından desteklenmiyor.|  
|`SCC_E_VERIFYMERGE`|-18|Dosya otomatik olarak birleştirilmiş olmuştur, ancak bekleyen kullanıcı doğrulama olduğu için iade edilmiş değil.|  
|`SCC_E_FIXMERGE`|-19|Dosya otomatik olarak birleştirilmiş olmuştur, ancak manüel olarak çözülmesi gereken bir birleştirme çakışması sebebiyle iade edilmedi.|  
|`SCC_E_SHELLFAILURE`|-20|Bir kabuk hatası nedeniyle hata oluştu.|  
|`SCC_E_INVALIDUSER`|-21|Hata: Kullanıcı geçersiz.|  
|`SCC_E_PROJECTALREADYOPEN`|-22|Hata: Proje zaten açıktır.|  
|`SCC_E_PROJSYNTAXERR`|-23|Proje söz dizimi hatası.|  
|`SCC_E_INVALIDFILEPATH`|-24|Hata: dosya yolu geçersiz.|  
|`SCC_E_PROJNOTOPEN`|-25|Hata: Proje açık değil.|  
|`SCC_E_NOTAUTHORIZED`|-26|Hata: kullanıcı bu işlemi gerçekleştirmek için yetkili değil.|  
|`SCC_E_FILESYNTAXERR`|-27|Dosya söz dizimi hatası.|  
|`SCC_E_FILENOTEXIST`|-28|Hata, yerel dosya yok.|  
|`SCC_E_CONNECTIONFAILURE`|-29|Hata: bir bağlantı hatası oluştu.|  
|`SCC_E_UNKNOWNERROR`|-30|Bilinmeyen hata.|  
|`SCC_E_BACKGROUNDGETINPROGRESS`|-31|Şu anda arka plan alma işlemi devam ediyor.|  
  
## <a name="macros-provided-for-quick-checking"></a>Hızlı denetlemek için sağlanan makroları  
  
```cpp  
IS_SCC_ERROR(rtn) (((rtn) < 0) ? TRUE : FALSE)  
IS_SCC_SUCCESS(rtn) (((rtn) == SCC_OK) ? TRUE : FALSE)  
IS_SCC_WARNING(rtn) (((rtn) > 0) ? TRUE : FALSE)  
```  
  
## <a name="remarks"></a>Açıklamalar  
 Tüm kaynak denetimi eklentisi API işlevleri (dışında [SccAdd](../extensibility/sccadd-function.md), [SccCheckin](../extensibility/scccheckin-function.md), ve [SccDiff](../extensibility/sccdiff-function.md)) bağımsız değişken olarak geçirilen yerel dosyaları yaptığınızda başarılı olması için bekleniyor çalışma klasörü içinde mevcut değil. Örneğin, IDE bir çağrı gönderemezsiniz [SccCheckout](../extensibility/scccheckout-function.md) veya [SccUncheckout](../extensibility/sccuncheckout-function.md) çalışma klasöründe yok, ancak kaynak denetimi Sistemi'nde bir dosya çubuğunda. Bu çağrı başarılı olabilir. Yalnızca çalışma klasöründe veya kaynak denetim sistemi dosya olduğunda işlevi başarısız olması bekleniyor.  
  
 Gibi belirli işlevleri `SccAdd` ve `SccCheckin`, özellikle döndürmelidir `SCC_E_FILENOTEXIST` zaman çalışma klasöründeki dosya mevcut değil. Diğer işlevleri, İşlevler üzerinde geçerli bir dosya adı kaynak denetim sistemi çalışmazsa çalışma dosyası yok, başarılı olması beklenir.  
  
 Eklenti dosyası bazı işlemi sırasında salt okunur olsa bile kaynak denetimi eklentisi çalışma klasöründe bir dosya çubuğunda ilgili hiçbir varsayım olmanız gerekir. Çalışma klasöründeki bir dosyayı taşınmış, silinmiş ve eklentinin denetimi dışında değiştirildi.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Kaynak denetimi eklentileri](../extensibility/source-control-plug-ins.md)