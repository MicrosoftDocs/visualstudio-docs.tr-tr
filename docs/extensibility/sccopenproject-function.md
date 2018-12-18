---
title: SccOpenProject işlevi | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- SccOpenProject
helpviewer_keywords:
- SccOpenProject function
ms.assetid: d609510b-660a-46d7-b93d-2406df20434d
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 928c1d63451dc49fabf01503e8cb7f6789b98998
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49837015"
---
# <a name="sccopenproject-function"></a>SccOpenProject İşlevi
Bu işlev, kaynak denetimi varolan projeyi açar veya yeni bir tane oluşturur.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
SCCRTN SccOpenProject (  
   LPVOID        pvContext,  
   HWND          hWnd,  
   LPSTR         lpUser,  
   LPCSTR        lpProjName,  
   LPCSTR        lpLocalProjPath,  
   LPSTR         lpAuxProjPath,  
   LPCSTR        lpComment,  
   LPTEXTOUTPROC lpTextOutProc,  
   LONG          dwFlags  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 pvContext  
 [in] Kaynak Denetimi Eklentisi bağlam yapısı.  
  
 hWnd  
 [in] Kaynak Denetimi Eklentisi sağladığı herhangi bir iletişim kutusu için bir üst öğe olarak kullanabileceğiniz IDE penceresi için bir tanıtıcı.  
  
 lpUser  
 [out içinde] (Not NULL Sonlandırıcı dahil olmak üzere, SCC_USER_SIZE aşmayı) kullanıcı adı.  
  
 lpProjName  
 [in] Proje adını tanımlayan dize.  
  
 lpLocalProjPath  
 [in] Proje için çalışma klasörü yolu.  
  
 lpAuxProjPath  
 [out içinde] ' % S'projesi (SCC_AUXPATH_SIZE, NULL sonlandırıcıyı da dahil olmak üzere aşmayı değil) tanımlayan bir isteğe bağlı yardımcı dize.  
  
 lpComment  
 [in] Oluşturulmakta olan yeni bir proje için açıklama.  
  
 lpTextOutProc  
 [in] Kaynak Denetimi Eklentisi çıkış metni görüntülemek için bir isteğe bağlı geri çağırma işlevi.  
  
 CertOpenStore  
 [in] Yeni bir proje, proje için kaynak bilinmeyen ise oluşturulması gerekip gerekmediğini sinyalleri eklenti denetler. Değeri bir birleşimi olabilir `SCC_OP_CREATEIFNEW` ve `SCC_OP_SILENTOPEN.`  
  
## <a name="return-value"></a>Dönüş Değeri  
 Kaynak Denetimi Eklentisi uygulanması bu işlev, aşağıdaki değerlerden birini döndürmesi beklenir:  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|SCC_OK|Projeyi açarken başarılı.|  
|SCC_E_INITIALIZEFAILED|Proje başlatılamadı.|  
|SCC_E_INVALIDUSER|Kullanıcı için kaynak denetim sistemi oturum açılamadı.|  
|SCC_E_COULDNOTCREATEPROJECT|Proje çağrıdan önce yok;  `SCC_OPT_CREATEIFNEW` bayrağı ayarlı, ancak proje oluşturulamadı.|  
|SCC_E_PROJSYNTAXERR|Geçersiz proje söz dizimi.|  
|SCC_E_UNKNOWNPROJECT|Kaynak Denetimi Eklentisi, bilinmeyen bir projedir ve `SCC_OPT_CREATEIFNEW` bayrağı ayarlanmamış.|  
|SCC_E_INVALIDFILEPATH|Dosya geçersiz veya kullanılamaz durumda yolu.|  
|SCC_E_NOTAUTHORIZED|Kullanıcı bu işlemi gerçekleştirmek için izin verilmiyor.|  
|SCC_E_ACCESSFAILURE|Kaynak denetim sistemi, ağ veya çakışma sorunları nedeniyle muhtemelen erişilirken sorun oluştu. Bir yeniden deneme önerilir.|  
|SCC_E_NONSPECFICERROR|Belirli olmayan bir hata; Kaynak denetim sistemi başlatılmadı.|  
  
## <a name="remarks"></a>Açıklamalar  
 IDE bir kullanıcı adı olarak oldfashionedgoat (`lpUser`), veya yalnızca boş bir dizeye bir işaretçi iletebilir. Bir kullanıcı adı varsa, kaynak denetimi eklentisi, varsayılan olarak kullanmanız gerekir. Ancak, adsız aktarılırsa veya verilen ada sahip bir oturum açma başarısız olursa, eklenti kullanıcıdan oturum açmak için ve geçerli adı döndürür `lpUser` geçerli bir oturum açma aldığında`.` kullanıcı adı dizesi eklenti değişebilir olduğundan , IDE her zaman bir arabellek boyutunu tahsis (`SCC_USER_LEN`+ 1 ya da null sonlandırıcıyı ortasının içeren SCC_USER_SIZE).  
  
> [!NOTE]
>  İlk eylemi gerçekleştirmek için IDE gerekebilir bir çağrı olabilir `SccOpenProject` işlevi veya [SccGetProjPath](../extensibility/sccgetprojpath-function.md). Bu nedenle, her ikisi de aynı sahip `lpUser` parametresi.  
  
 `lpAuxProjPath` ve`lpProjName` çözüm dosyasından okumak veya çağrısından döndürülen `SccGetProjPath` işlevi. Bu parametreler, kaynak denetimi eklentisi projesi ile ilişkilendiren dizeleri içeren ve yalnızca eklenti için anlamlı olan. Bu tür bir dize içinde çözüm dosyası ve kullanıcı göz atmak için çalışandan değil (bir dize içinde dönmek, `SccGetProjPath` işlevi), IDE boş dizeler için her ikisi de geçirir `lpAuxProjPath` ve `lpProjName`ve bu değerleri güncelleştirilmesi bekleniyor Bu işlev tarafından eklenti olduğunda döndürür.  
  
 `lpTextOutProc` Kaynak denetimi eklentisi komut sonuç çıktısı görüntüleme amacıyla IDE tarafından sağlanan bir geri çağırma işlevi için bir işaretçidir. Bu geri çağırma işlevi, ayrıntılı olarak açıklanan [LPTEXTOUTPROC](../extensibility/lptextoutproc.md).  
  
> [!NOTE]
>  Kaynak Denetimi Eklentisi bu yararlanmak planlıyorsa, ayarlamış olmanız gerekir `SCC_CAP_TEXTOUT` bayrağını [Sccınitialize](../extensibility/sccinitialize-function.md). Bu bayrağı ayarlı değil veya bu özellik, IDE desteklemiyorsa `lpTextOutProc` olacaktır `NULL`.  
  
 `dwFlags` Parametre açılmasını proje zaten var olmadığından olay, sonucu denetler. İki bit bayrakları oluşur `SCC_OP_CREATEIFNEW` ve `SCC_OP_SILENTOPEN`. Zaten açık proje yoksa işlev yalnızca projeyi açar ve döndürür `SCC_OK`. Proje yoksa ve `SCC_OP_CREATEIFNEW` bayrağı açıktır, kaynak denetimi eklentisi proje kaynak denetimi sisteminizden oluşturabilir, açın ve dönüş `SCC_OK`. Proje yoksa ve `SCC_OP_CREATEIFNEW` bayrağı kapalıdır, eklenti ardından için denetlemelisiniz `SCC_OP_SILENTOPEN` bayrağı. Bu bayrağı açık değilse, eklentinin kullanıcı için bir proje adı isteyebilir. Bu bayrak üzerindeyse, eklenti yalnızca döndürmelidir `SCC_E_UNKNOWNPROJECT`.  
  
## <a name="calling-order"></a>Arama sırası  
 Olaylar, normal seyrinde [Sccınitialize](../extensibility/sccinitialize-function.md) bir kaynak denetim oturumu açmak için önce çağrılır. Bir oturum yapılan bir çağrının oluşabilir `SccOpenProject`tarafından diğer kaynak denetimi eklentisi API işlev çağrılarını izleyen ve bir çağrıyla sonlandırılır [SccCloseProject](../extensibility/scccloseproject-function.md). Bu tür oturumları birkaç kez önce yinelenebilir [SccUninitialize](../extensibility/sccuninitialize-function.md) çağrılır.  
  
 Kaynak Denetimi Eklentisi kümeleri `SCC_CAP_REENTRANT` içindeki bit `SccInitialize`, sonra da yukarıdaki oturum sırası paralel olarak birçok defa yinelenebilir. Farklı `pvContext` yapıları her farklı oturumları izlemek `pvContext` aynı anda bir Proje Aç ile ilişkilidir. Temel`pvContext` parametresi, eklentinin proje belirli herhangi bir çağrıda başvuruluyor belirleyebilirsiniz. Özellik bit varsa `SCC_CAP_REENTRANT` , nonreentrant ayarlı değil kaynak denetimi eklentileri birden çok projeleriyle çalışmak için kendi yeteneği sınırlıdır.  
  
> [!NOTE]
>  `SCC_CAP_REENTRANT` Bit, kaynak denetimi eklentisi API 1.1 sürümünde tanıtılmıştır. Ayarlı değil veya sürüm 1.0 göz ardı edilir ve tüm sürüm 1.0 kaynak denetimi eklentileri nonreentrant olduğu varsayılır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Kaynak Denetimi Eklentisi API işlevleri](../extensibility/source-control-plug-in-api-functions.md)   
 [SccCloseProject](../extensibility/scccloseproject-function.md)   
 [SccGetProjPath](../extensibility/sccgetprojpath-function.md)   
 [Sccınitialize](../extensibility/sccinitialize-function.md)   
 [SccUninitialize](../extensibility/sccuninitialize-function.md)   
 [Dize uzunluğu kısıtlamaları](../extensibility/restrictions-on-string-lengths.md)   
 [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)