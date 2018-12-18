---
title: SccAddFilesFromSCC işlevi | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- SccAddFilesFromSCC
helpviewer_keywords:
- SccAddFilesFromSCC function
ms.assetid: f21a3500-ade8-4dd8-8647-10e2179be9c1
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b827e1f7e26fb98e9d49de4e9fe2388e46ee07cb
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49831178"
---
# <a name="sccaddfilesfromscc-function"></a>SccAddFilesFromSCC işlevi
Bu işlev, kaynak denetiminden dosyaların listesini açık projeye ekler.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
SCCRTN SccAddFilesFromSCC(  
   LPVOID  pContext,  
   HWND    hWnd,  
   LPSTR   lpUser,  
   LPSTR   lpAuxProjPath,  
   LONG    cFiles,  
   LPCSTR* lpFilePaths,  
   LPCSTR  lpDestination,  
   LPCSTR  lpComment,  
   LPBOOL  pbResults  
);  
```  
  
### <a name="parameters"></a>Parametreler  
 pContext  
 [in] Kaynak Denetimi Eklentisi bağlam işaretçisi.  
  
 hWnd  
 [in] Kaynak Denetimi Eklentisi sağladığı herhangi bir iletişim kutusu için bir üst öğe olarak kullanabileceğiniz IDE penceresi için bir tanıtıcı.  
  
 lpUser  
 [out içinde] Kullanıcı adı (en fazla SCC_USER_SIZE, null sonlandırıcıyı da dahil olmak üzere).  
  
 lpAuxProjPath  
 [out içinde] Proje tanımlayan yardımcı dize (en fazla `SCC_PRJPATH_`BOYUTU, null sonlandırıcıyı da dahil olmak üzere).  
  
 cFiles  
 [in] Tarafından verilen dosya sayısı `lpFilePaths`.  
  
 lpFilePaths  
 [out içinde] Geçerli projeye eklemek için dosya adları dizisi.  
  
 lpDestination  
 [in] Yazılacak dosyalar nerede hedef yolu.  
  
 lpComment  
 [in] Eklenmekte olan dosyalar her öğesine uygulanması için açıklama.  
  
 pbResults  
 [out içinde] Başarılı (sıfır olmayan veya TRUE) olduğunu belirtmek için set ya da hata bayrakları dizisi (sıfır ya da FALSE) her dosya için (dizinin boyutu en az olmalıdır `cFiles` uzun).  
  
## <a name="return-value"></a>Dönüş değeri  
 Kaynak Denetimi Eklentisi uygulanması bu işlev, aşağıdaki değerlerden birini döndürmesi beklenir:  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|SCC_E_PROJNOTOPEN|Proje açık değil.|  
|SCC_E_OPNOTPERFORMED|Bağlantı tarafından belirtildiği gibi aynı projeye değil `lpAuxProjPath.`|  
|SCC_E_NOTAUTHORIZED|Veritabanını güncellemek için kullanıcı yetkili değil.|  
|SCC_E_NONSPECIFICERROR|Bilinmeyen hata.|  
|SCC_I_RELOADFILE|Bir dosya veya projenin yeniden yüklenmesi gerekiyor.|  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Kaynak Denetimi Eklentisi API işlevleri](../extensibility/source-control-plug-in-api-functions.md)