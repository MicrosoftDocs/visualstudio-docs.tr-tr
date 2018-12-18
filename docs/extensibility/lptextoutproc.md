---
title: LPTEXTOUTPROC | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- LPTEXTOUTPROC
helpviewer_keywords:
- SccMsgDataOnMessage structure
- SccMsgDataOnBeforeGetFile structure
- SccMsgDataIsCancelled structure
- LPTEXTOUTPROC callback function
- SccMsgDataOnAfterGetFile structure
ms.assetid: 2025c969-e3c7-4cf4-a5c5-099d342895ea
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 2d8439d706dbe8c84d807fb445eda272b96ad589
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49822884"
---
# <a name="lptextoutproc"></a>LPTEXTOUTPROC
Kullanıcı bir kaynak denetim işleminde tümleşik geliştirme ortamı (IDE) içinde yürütüldüğünde, kaynak denetimi eklentisi işlemi ile ilgili durum veya hata iletilerini iletmek isteyebilirsiniz. Eklenti kendi ileti kutularını bu amaçla görüntüleyebilirsiniz. Ancak, daha fazla sorunsuz tümleştirme için eklenti dizeler ardından bunları durum bilgisini görüntüleme, kendi yerel biçiminde görüntüler IDE geçirebilirsiniz. Bu mekanizma `LPTEXTOUTPROC` işlev işaretçisi. IDE hata ve durum görüntüleme (Aşağıda daha ayrıntılı olarak açıklanmıştır) Bu işlev uygular.  
  
 IDE için kaynak denetimi eklentisi bu işlev, işlev işaretçisi olarak geçirir `lpTextOutProc` çağırırken parametre [SccOpenProject](../extensibility/sccopenproject-function.md). Örneğin, bir çağrı ortasında bir SCC işlemi sırasında [SccGet](../extensibility/sccget-function.md) çok sayıda dosya içeren, eklenti çağırabilirsiniz `LPTEXTOUTPROC` işlevi, düzenli aralıklarla görüntülemek için dizeleri geçirme. IDE bu dizeler durum çubuğunda, çıktı penceresinde ya da ayrı ileti kutusunda uygun şekilde görüntülenebilir. İsteğe bağlı olarak, IDE ile belirli iletileri görüntülemeyi mümkün olabilir bir **iptal** düğmesi. Bu işlemi iptal etmek kullanıcının sağlar ve bu bilgileri tekrar eklenti geçirme özelliği IDE sağlar.  
  
## <a name="signature"></a>İmza  
 IDE işlevi aşağıdaki imzası olan çıktı:  
  
```cpp  
typedef LONG (*LPTEXTOUTPROC) (  
   LPSTR display_string,  
   LONG mesg_type  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 display_string  
 Görüntülenecek bir metin dizesi. Bu dize bir satır başı dönüş veya satır besleme ile sonlandırılmalıdır değil.  
  
 mesg_type  
 İleti türü. Bu parametre için desteklenen değerler aşağıdaki tabloda listelenmektedir.  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`SCC_MSG_INFO, SCC_MSG_WARNING, SCC_MSG_ERROR`|İletinin bilgi, uyarı veya hata olarak kabul edilir.|  
|`SCC_MSG_STATUS`|İleti durumu gösterir ve durum çubuğunda görüntülenir.|  
|`SCC_MSG_DOCANCEL`|İleti dize ile gönderilir.|  
|`SCC_MSG_STARTCANCEL`|Görüntüleme başlangıcı bir **iptal** düğmesi.|  
|`SCC_MSG_STOPCANCEL`|Görüntüleme durdurur bir **iptal** düğmesi.|  
|`SCC_MSG_BACKGROUND_IS_CANCELLED`|Arka plan işlemi iptal edilip edilmeyeceğini IDE ister: IDE döndürür `SCC_MSG_RTN_CANCEL` işlem iptal edildi; Aksi halde döndürür `SCC_MSG_RTN_OK`. `display_string` Parametresi olarak atandığında bir [SccMsgDataIsCancelled](#LinkSccMsgDataIsCancelled) yapısı, kaynak denetimi eklentisi tarafından sağlanır.|  
|`SCC_MSG_BACKGROUND_ON_BEFORE_GET_FILE`|Sürüm denetiminden alınmadan önce bir dosya hakkında IDE söyler. `display_string` Parametresi olarak atandığında bir [SccMsgDataOnBeforeGetFile](#LinkSccMsgDataOnBeforeGetFile) yapısı, kaynak denetimi eklentisi tarafından sağlanır.|  
|`SCC_MSG_BACKGROUND_ON_AFTER_GET_FILE`|Sürüm denetiminden aldıktan sonra IDE bir dosya hakkında söyler. `display_string` Parametresi olarak atandığında bir [SccMsgDataOnAfterGetFile](#LinkSccMsgDataOnAfterGetFile) yapısı, kaynak denetimi eklentisi tarafından sağlanır.|  
|`SCC_MSG_BACKGROUND_ON_MESSAGE`|Arka plan işlemi şu andaki durumu IDE'yi söyler. `display_string` Parametresi olarak atandığında bir [SccMsgDataOnMessage](#LinkSccMsgDataOnMessage) yapısı, kaynak denetimi eklentisi tarafından sağlanır.|  
  
## <a name="return-value"></a>Dönüş değeri  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|SCC_MSG_RTN_OK|Dize zobrazilo veya işlemi başarıyla tamamlandı.|  
|SCC_MSG_RTN_CANCEL|Kullanıcı işlemi iptal etmek istiyor.|  
  
## <a name="example"></a>Örnek  
 IDE çağrıları varsayalım [SccGet](../extensibility/sccget-function.md) yirmi dosya adlarına sahip. Kaynak Denetimi Eklentisi, ortasında bir dosya alma işlemi iptal ediliyor önlemek istiyor. Her dosyayı edindikten sonra onu çağıran `lpTextOutProc`, her dosya durum bilgilerini geçirme ve gönderen bir `SCC_MSG_DOCANCEL` raporlanacak durum yok varsa, ileti. Herhangi bir zamanda eklenti dönüş değerini alıp almadığına `SCC_MSG_RTN_CANCEL` böylece daha fazla dosya alınır IDE üzerinden, alma işlemi hemen iptal eder.  
  
## <a name="structures"></a>Yapılar  
  
###  <a name="LinkSccMsgDataIsCancelled"></a> SccMsgDataIsCancelled  
  
```cpp  
typedef struct {  
   DWORD dwBackgroundOperationID;  
} SccMsgDataIsCancelled;  
```  
  
 Bu yapı ile gönderilen `SCC_MSG_BACKGROUND_IS_CANCELLED` ileti. İptal edildi arka plan işlemi kimliği iletişim kurmak için kullanılır.  
  
###  <a name="LinkSccMsgDataOnBeforeGetFile"></a> SccMsgDataOnBeforeGetFile  
  
```cpp  
typedef struct {  
   DWORD dwBackgroundOperationID;  
   PCSTR szFile;  
} SccMsgDataOnBeforeGetFile;  
```  
  
 Bu yapı ile gönderilen `SCC_MSG_BACKGROUND_ON_BEFORE_GET_FILE` ileti. Yaklaşık Alınacak dosya adını ve Kimliğini alma yapıyor arka plan işlemi iletişim kurmak için kullanılır.  
  
###  <a name="LinkSccMsgDataOnAfterGetFile"></a> SccMsgDataOnAfterGetFile  
  
```cpp  
typedef struct {  
   DWORD dwBackgroundOperationID;  
   PCSTR szFile;  
   SCCRTN sResult;  
} SccMsgDataOnAfterGetFile;  
```  
  
 Bu yapı ile gönderilen `SCC_MSG_BACKGROUND_ON_AFTER_GET_FILE` ileti. Belirtilen dosya ve bunun yanı sıra alınırken yapmış arka plandaki işlem kimliği alınıyor sonucunu iletişim kurmak için kullanılır. Dönüş değerlerinin [SccGet](../extensibility/sccget-function.md) için ne sonuç olarak verilebilir.  
  
###  <a name="LinkSccMsgDataOnMessage"></a> SccMsgDataOnMessage  
 [C++]  
  
```cpp  
typedef struct {  
   DWORD dwBackgroundOperationID;  
   PCSTR szMessage;  
   BOOL bIsError;  
} SccMsgDataOnMessage;  
```  
  
 Bu yapı ile gönderilen `SCC_MSG_BACKGROUND_ON_MESSAGE` ileti. Arka plan işlemi şu andaki durumu iletişim kurmak için kullanılır. Durum IDE tarafından görüntülenecek dize olarak ifade edilir ve `bIsError` iletinin önemini gösterir (`TRUE` bir hata iletisi için; `FALSE` bir uyarı ya da bir bilgi iletisidir). Gönderme durumu arka plan işlemi Kimliğini de verilir.  
  
## <a name="code-example"></a>Kod örneği  
 Kısa bir arama örnek `LPTEXTOUTPROC` göndermek için `SCC_MSG_BACKGROUND_ON_MESSAGE` yapısı çağrı için tür dönüştürme gösteren bir ileti.  
  
```cpp  
LONG SendStatusMessage(  
    LPTEXTOUTPROC pTextOutProc,  
    DWORD         dwBackgroundID,  
    LPCTSTR       pStatusMsg,  
    BOOL          bIsError)  
{  
    SccMsgDataOnMessage msgData = { 0 };  
    LONG                result  = 0;  
  
    msgData.dwBackgroundOperationID = dwBackgroundID;  
    msgData.szMessage               = pStatusMsg;  
    msgData.bIsError                = bIsError;  
  
    result = pTextOutProc(reinterpret_cast<LPCTSTR>(&msgData), SCC_MSG_BACKGROUND_ON_MESSAGE);  
    return result;  
}  
```  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [IDE tarafından uygulanan geri çağırma işlevleri](../extensibility/callback-functions-implemented-by-the-ide.md)   
 [Kaynak denetimi eklentileri](../extensibility/source-control-plug-ins.md)