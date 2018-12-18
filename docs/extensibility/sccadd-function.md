---
title: SccAdd işlevi | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- SccAdd
helpviewer_keywords:
- SccAdd function
ms.assetid: 545268f3-8e83-446a-a398-1a9db9e866e8
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: defb9a682b7f382f414d7bedfe60509d73cea64b
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49840031"
---
# <a name="sccadd-function"></a>SccAdd işlevi
Bu işlev, yeni dosyaların kaynak denetim sistemine ekler.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
SCCRTN SccAdd(  
   LPVOID    pvContext,  
   HWND      hWnd,  
   LONG      nFiles,  
   LPCSTR*   lpFileNames,  
   LPCSTR    lpComment,  
   LONG*     pfOptions,  
   LPCMDOPTS pvOptions  
);  
```  
  
### <a name="parameters"></a>Parametreler  
 pvContext  
 [in] Kaynak Denetimi Eklentisi bağlam yapısı.  
  
 hWnd  
 [in] Kaynak Denetimi Eklentisi sağladığı herhangi bir iletişim kutusu için bir üst öğe olarak kullanabileceğiniz IDE penceresi için bir tanıtıcı.  
  
 nFiles  
 [in] Geçerli projeye, verilen eklenecek seçili dosya sayısı `lpFileNames` dizisi.  
  
 lpFileNames  
 [in] Eklenecek dosyaların tam yerel adları dizisi.  
  
 lpComment  
 [in] Eklenmekte olan dosyalar tümüne uygulanacak açıklama.  
  
 pfOptions  
 [in] Sağlanan dosya başına temelinde, komut bayrakları dizisi.  
  
 pvOptions  
 [in] Kaynak denetimi fişi özel seçenekleri.  
  
## <a name="return-value"></a>Dönüş değeri  
 Kaynak Denetimi Eklentisi uygulanması bu işlev, aşağıdaki değerlerden birini döndürmesi beklenir:  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|SCC_OK|Ekleme işlemi başarılı oldu.|  
|SCC_E_FILEALREADYEXISTS|Seçili dosya kaynak denetimi altında zaten var.|  
|SCC_E_TYPENOTSUPPORTED|Kaynak denetim sistemi tarafından (örneğin, ikili) dosya türü desteklenmiyor.|  
|SCC_E_OPNOTSUPPORTED|Kaynak denetim sistemi bu işlemi desteklemiyor.|  
|SCC_E_ACCESSFAILURE|Kaynak denetim sistemi, ağ veya çakışma sorunları nedeniyle muhtemelen erişilirken sorun oluştu. Bir yeniden deneme önerilir.|  
|SCC_E_NOTAUTHORIZED|Kullanıcı bu işlemi gerçekleştirmek için izin verilmiyor.|  
|SCC_E_NONSPECIFICERROR|Belirli olmayan hata; ekleme gerçekleştirilemiyor.|  
|SCC_I_OPERATIONCANCELED|İşlem tamamlanmadan önce iptal edildi.|  
|SCC_I_RELOADFILE|Bir dosya veya projenin yeniden yüklenmesi gerekiyor.|  
|SCC_E_FILENOTEXIST|Yerel dosya bulunamadı.|  
  
## <a name="remarks"></a>Açıklamalar  
 Normal `fOptions` burada bir dizi tarafından değiştirilir `pfOptions`, biriyle `LONG` seçeneği her dosya belirtimi. Dosya türü dosyası başka bir dosya değişebilir olmasıdır.  
  
> [!NOTE]
>  Her ikisini de belirtmek için geçersiz `SCC_FILETYPE_TEXT` ve `SCC_FILETYPE_BINARY` ne belirtmek için aynı dosyayı, ancak seçeneklerini geçerlidir. Hiçbiri ayardır ayarı ile aynı `SCC_FILETYPE_AUTO`, bu durumda, kaynak denetim eklentisi autodetects dosya türü.  
  
 Kullanılan bayrakların listesi aşağıdadır `pfOptions` dizisi:  
  
|Seçenek|Değer|Açıklama|  
|------------|-----------|-------------|  
|SCC_FILETYPE_AUTO|0x00|Kaynak Denetimi Eklentisi, dosya türü algılanmalıdır.|  
|SCC_FILETYPE_TEXT|0x01|Bir ASCII metin dosyası gösterir.|  
|SCC_FILETYPE_BINARY|0x02|ASCII metni başka bir dosya türünü belirtir.|  
|SCC_ADD_STORELATEST|0x04|Dosya hiçbir deltaları yalnızca en son kopyasını depolar.|  
|SCC_FILETYPE_TEXT_ANSI|0x08|Dosya ANSI metin olarak değerlendirir.|  
|SCC_FILETYPE_UTF8|0x10|UTF8 biçiminde bir Unicode metin olarak dosyanın değerlendirir.|  
|SCC_FILETYPE_UTF16LE|0x20|Küçük Endian biçiminde UTF16 Unicode metin olarak dosyanın değerlendirir.|  
|SCC_FILETYPE_UTF16BE|0x40|Davranır dosya UTF16 Big Endian Unicode metin olarak biçimlendirir.|  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Kaynak Denetimi Eklentisi API işlevleri](../extensibility/source-control-plug-in-api-functions.md)