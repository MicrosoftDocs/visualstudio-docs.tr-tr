---
title: Sccınitialize işlevi | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- SccInitialize
helpviewer_keywords:
- SccInitialize function
ms.assetid: 5bc0d28b-2c68-4d43-9e51-541506a8f76e
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 136978a6d1dc19a414079ba424ebcd5d50f6840a
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49934580"
---
# <a name="sccinitialize-function"></a>SccInitialize İşlevi
Bu işlev, kaynak denetimi eklentisi başlatır ve özellikler ve sınırlamalar için tümleşik geliştirme ortamı (IDE) sağlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
SCCRTN SccInitialize (  
   LPVOID* ppvContext,  
   HWND    hWnd,  
   LPCSTR  lpCallerName,  
   LPSTR   lpSccName,  
   LPLONG  lpSccCaps,  
   LPSTR   lpAuxPathLabel,  
   LPLONG  pnCheckoutCommentLen,  
   LPLONG  pnCommentLen  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `ppvContext`  
 [in] Kaynak Denetimi Eklentisi bağlam yapısı işaretçisi buraya koyabilirsiniz.  
  
 `hWnd`  
 [in] Kaynak Denetimi Eklentisi sağladığı herhangi bir iletişim kutusu için bir üst öğe olarak kullanabileceğiniz IDE penceresi için bir tanıtıcı.  
  
 `lpCallerName`  
 [in] Kaynak Denetimi Eklentisi çağırma programının adı.  
  
 `lpSccName`  
 [out içinde] Burada, kaynak denetimi eklentisi koyar kendi adına arabellek (aşmayan `SCC_NAME_LEN`).  
  
 `lpSccCaps`  
 [out] Kaynak denetimi, özellik bayrakları, eklentinin döndürür.  
  
 `lpAuxPathLabel`  
 [out içinde] Burada, kaynak denetimi eklentisi koyar açıklayan bir dize arabellek `lpAuxProjPath` parametresi tarafından döndürülen [SccOpenProject](../extensibility/sccopenproject-function.md) ve [SccGetProjPath](../extensibility/sccgetprojpath-function.md) (aşmayan `SCC_AUXLABEL_LEN`).  
  
 `pnCheckoutCommentLen`  
 [out] Kullanıma alma açıklaması izin verilen maksimum uzunluğunu döndürür.  
  
 `pnCommentLen`  
 [out] Diğer açıklamaları izin verilen maksimum uzunluğunu döndürür.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Kaynak Denetimi Eklentisi uygulanması bu işlev, aşağıdaki değerlerden birini döndürmesi beklenir:  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|SCC_OK|Kaynak denetimi başlatma başarılı oldu.|  
|SCC_E_INITIALIZEFAILED|Sistem başlatılamadı.|  
|SCC_E_NOTAUTHORIZED|Kullanıcı, belirtilen işlemi gerçekleştirmek için izin verilmiyor.|  
|SCC_E_NONSPECFICERROR|Belirli olmayan hata; Kaynak denetim sistemi başlatılmadı.|  
  
## <a name="remarks"></a>Açıklamalar  
 Kaynak Denetimi Eklentisi ilk kez yüklediğinde IDE bu işlevi çağırır. Bu eklentiye arayanın adı gibi belirli bilgileri geçirmek IDE sağlar. IDE Ayrıca açıklamalar ve eklentinin özellikleri için izin verilen uzunluk sınırını gibi belirli bilgileri geri alır.  
  
 `ppvContext` İşaret eden bir `NULL` işaretçi. Kaynak Denetimi Eklentisi, bir yapının kendi kullanımı için ayırma ve bu yapısına bir işaretçi depolar `ppvContext`. IDE this işaretçisi, her diğer VSSCI API işlevi için genel depolama alanına başvurmadan bağlam bilgilere sahip ve birden fazla eklentinin desteklemek için eklenti izin vererek geçirin. Bu yapı ne zaman kaldırılmamalıdır [SccUninitialize](../extensibility/sccuninitialize-function.md) çağrılır.  
  
 `lpCallerName` Ve `lpSccName` parametreleri IDE ve kaynak denetimi eklentisi adları alışverişi olanak tanır. Bu adlar, yalnızca birden fazla örnek arasında ayrım yapmak için kullanılabilir veya bunlar gerçekten menüleri veya iletişim kutusu görünebilir.  
  
 `lpAuxPathLabel` Parametredir çözüm dosyasında depolanan ve kaynak denetimi eklentisi bir çağrıda geçirilen yardımcı proje yolunu tanımlamak için bir açıklama olarak kullanılan bir dize [SccOpenProject](../extensibility/sccopenproject-function.md). [!INCLUDE[vsvss](../extensibility/includes/vsvss_md.md)] dize kullanır "SourceSafe projesinin:"; Bu belirli dize kullanmadığınızdan diğer kaynak denetimi eklentileri.  
  
 `lpSccCaps` Parametre verir kaynak denetimi eklentisi eklentinin özelliklerini gösteren bit bayrakları depolamak için bir yer. (Özellik bit bayrakları tam bir listesi için bkz. [özellik bayrakları](../extensibility/capability-flags.md)). Örneğin, sonuçları çağıran tarafından sağlanan geri çağırma işlevi içinde eklenti ayarlama yeteneği yazmak için eklenti planları SCC_CAP_TEXTOUT bit varsa. Bu, sürüm denetimi sonuçları için bir pencere oluşturmak için IDE sinyal.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Kaynak Denetimi Eklentisi API işlevleri](../extensibility/source-control-plug-in-api-functions.md)   
 [SccUninitialize](../extensibility/sccuninitialize-function.md)   
 [SccOpenProject](../extensibility/sccopenproject-function.md)   
 [Özellik Bayrakları](../extensibility/capability-flags.md)