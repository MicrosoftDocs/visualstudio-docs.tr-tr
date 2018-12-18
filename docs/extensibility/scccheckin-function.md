---
title: SccCheckin işlevi | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- SccCheckin
helpviewer_keywords:
- SccCheckin function
ms.assetid: e3f26ac2-6163-42e1-a764-22cfea5a3bc6
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 95e63c9d8875bb222bf0ab1c161b4437de7466dc
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49898284"
---
# <a name="scccheckin-function"></a>SccCheckin işlevi
Bu işlev, daha önce kullanıma dosyalardaki değişiklikleri depolamak ve yeni bir sürüm oluşturma kaynak denetim sistemine denetler. Bu işlev, bir sayı ve bir dizi adını dosyaların iade edilmesine çağrılır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
SCCRTN SccCheckin (  
   LPVOID    pvContext,  
   HWND      hWnd,  
   LONG      nFiles,  
   LPSTR*    lpFileNames,  
   LPCSTR    lpComment,  
   LONG      fOptions,  
   LPCMDOPTS pvOptions  
);  
```  
  
### <a name="parameters"></a>Parametreler  
 pvContext  
 [in] Kaynak Denetimi Eklentisi bağlam yapısı.  
  
 hWnd  
 [in] Eklenti SCC sağladığı herhangi bir iletişim kutusu için bir üst öğe olarak kullanabileceğiniz IDE penceresi için bir tanıtıcı.  
  
 nFiles  
 [in] İade edilmesi seçili dosya sayısı.  
  
 lpFileNames  
 [in] Dosyaların iade edilmesine tam yerel yol adları dizisi.  
  
 lpComment  
 [in] Seçili dosyaları iade edilen uygulanması için açıklama. Bu parametre `NULL` , kaynak denetimi eklentisi için bir açıklama isteyecektir.  
  
 fOptions  
 [in] Komut bayrakları, ya da 0 veya `SCC_KEEP_CHECKEDOUT`.  
  
 pvOptions  
 [in] SCC fişi özel seçenekleri.  
  
## <a name="return-value"></a>Dönüş değeri  
 Kaynak Denetimi Eklentisi uygulanması bu işlev, aşağıdaki değerlerden birini döndürmesi beklenir:  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|SCC_OK|Dosya başarıyla iade edildi.|  
|SCC_E_FILENOTCONTROLLED|Seçili dosya kaynak kodu denetimi altında değil.|  
|SCC_E_ACCESSFAILURE|Kaynak denetim sistemi, ağ veya çakışma sorunları nedeniyle muhtemelen erişilirken sorun oluştu. Bir yeniden deneme önerilir.|  
|SCC_E_NONSPECIFICERROR|Belirli olmayan hata oluştu. Dosya iade.|  
|SCC_E_NOTCHECKEDOUT|Kullanıcının dosyaya iade edilemiyor, kullanıma değil.|  
|SCC_E_CHECKINCONFLICT|İade etme nedeniyle gerçekleştirilemedi:<br /><br /> -Başka bir kullanıcı önceden iade ve `bAutoReconcile` yanlıştı.<br /><br /> veya<br /><br /> -(Örneğin, dosyaları ikili olduğunda) otomatik birleştirme işlemi gerçekleştirilemiyor.|  
|SCC_E_VERIFYMERGE|Dosya otomatik olarak birleştirilmiş olmuştur, ancak kullanıcı doğrulaması iade edilmedi.|  
|SCC_E_FIXMERGE|Dosya otomatik olarak birleştirilmiş olmuştur, ancak manüel olarak çözülmesi gereken bir birleştirme çakışması sebebiyle iade edilmedi.|  
|SCC_E_NOTAUTHORIZED|Kullanıcı bu işlemi gerçekleştirmek için izin verilmiyor.|  
|SCC_I_OPERATIONCANCELED|İşlem tamamlanmadan önce iptal edildi.|  
|SCC_I_RELOADFILE|Bir dosya veya projenin yeniden yüklenmesi gerekiyor.|  
|SCC_E_FILENOTEXIST|Yerel dosya bulunamadı.|  
  
## <a name="remarks"></a>Açıklamalar  
 Açıklama teslim edilen tüm dosyalar için geçerlidir. Açıklama bağımsız değişken olabilir bir `null` dize, kaynak denetimi eklentisi her dosya için bir açıklama dizesi kullanıcıdan bu durumda.  
  
 `fOptions` Bağımsız değişken değeri verilebilir `SCC_KEEP_CHECKEDOUT` dosyayı iade edin ve yeniden kullanıma kullanıcının amacını belirten bayrak.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Kaynak Denetimi Eklentisi API işlevleri](../extensibility/source-control-plug-in-api-functions.md)