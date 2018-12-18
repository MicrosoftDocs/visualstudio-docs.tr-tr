---
title: SccBackgroundGet işlevi | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- SccBackgroundGet
helpviewer_keywords:
- SccBackgroundGet function
ms.assetid: 69817e52-b9ac-4f4d-820b-2cc9c384f0dc
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 39550665c804aa971ba88ee76707bdd150f74ab0
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49811795"
---
# <a name="sccbackgroundget-function"></a>SccBackgroundGet işlevi
Bu işlev, kaynak denetiminden her belirtilen dosyalar, kullanıcı etkileşimi olmadan alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
SCCRTN SccBackgroundGet(  
   LPVOID  pContext,  
   LONG    nFiles,  
   LPCSTR* lpFileNames,  
   LONG    dwFlags,  
   LONG    dwBackgroundOperationID  
);  
```  
  
### <a name="parameters"></a>Parametreler  
 pContext  
 [in] Kaynak Denetimi Eklentisi bağlam işaretçisi.  
  
 nFiles  
 [in] Belirtilen dosya sayısı `lpFileNames` dizisi.  
  
 lpFileNames  
 [out içinde] Alınacak dosya adları dizisi.  
  
> [!NOTE]
>  Adlarının tam yerel dosya adları olması gerekir.  
  
 CertOpenStore  
 [in] Komut bayrakları (`SCC_GET_ALL`, `SCC_GET_RECURSIVE`).  
  
 dwBackgroundOperationID  
 [in] Bu işlemle ilişkili benzersiz bir değerdir.  
  
## <a name="return-value"></a>Dönüş değeri  
 Kaynak Denetimi Eklentisi uygulanması bu işlev, aşağıdaki değerlerden birini döndürmesi beklenir:  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|SCC_OK|İşlem başarıyla tamamlandı.|  
|SCC_E_BACKGROUNDGETINPROGRESS|Arka planda alma (yalnızca aynı anda toplu işlemleri desteklemiyorsa, kaynak denetimi eklentisi bu döndürmelidir) sürüyor.|  
|SCC_I_OPERATIONCANCELED|İşlem tamamlandı önce iptal edildi.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu işlev, her zaman kaynak denetimi eklentisi yüklenmiş olandan farklı bir iş parçacığı üzerinde çağrılır. Bu işlev, tamamlanana kadar geri dönmek için beklenmiyor; Ancak, birden çok kez dosyaları, tümü aynı anda birden çok listesi ile çağrılabilir.  
  
 Kullanımını `dwFlags` bağımsız değişkeni ile aynı olduğu [SccGet](../extensibility/sccget-function.md).  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Kaynak Denetimi Eklentisi API işlevleri](../extensibility/source-control-plug-in-api-functions.md)   
 [SccGet](../extensibility/sccget-function.md)