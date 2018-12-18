---
title: SccQueryChanges işlevi | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- SccQueryChanges
helpviewer_keywords:
- SccQueryChanges function
ms.assetid: 4cd58eb3-6952-49b1-9620-8682e3eaa604
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: f7b3a9454daa0f2e3c5cf91a9dc483afe1f635a1
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49915717"
---
# <a name="sccquerychanges-function"></a>SccQueryChanges İşlevi
Bu işlev, dosyalar, bir geri çağırma işlevi aracılığıyla her dosya için ad değişiklikleri hakkında bilgi sağlayan belirli bir listesini numaralandırır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
SCCRTN SccQueryChanges(  
   LPVOID           pContext,  
   LONG             nFiles,  
   LPCSTR*          lpFileNames,  
   QUERYCHANGESFUNC pfnCallback,  
   LPVOID           pvCallerData  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 pContext  
 [in] Kaynak Denetimi Eklentisi bağlam işaretçisi.  
  
 nFiles  
 [in] Dosya sayısı `lpFileNames` dizisi.  
  
 lpFileNames  
 [in] Hakkında bilgi almak için dosya adları dizisi.  
  
 pfnCallback  
 [in] Listedeki her bir dosya adı için çağrılacak bir geri çağırma işlevi (bkz [QUERYCHANGESFUNC](../extensibility/querychangesfunc.md) Ayrıntılar için).  
  
 pvCallerData  
 [in] Geri çağırma işlevine geçirilen değer değişmedi.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Kaynak Denetimi Eklentisi uygulanması bu işlev, aşağıdaki değerlerden birini döndürmesi beklenir:  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|SCC_OK|Sorgu işlemi başarıyla tamamlandı.|  
|SCC_E_PROJNOTOPEN|Proje, kaynak denetiminde açılmadı.|  
|SCC_E_ACCESSFAILURE|Kaynak denetim sistemi, ağ veya çakışma sorunları nedeniyle muhtemelen erişilirken sorun oluştu.|  
|SCC_E_NONSPECIFICERROR|Belirtilmemiş veya genel bir hata oluştu.|  
  
## <a name="remarks"></a>Açıklamalar  
 İçin sorgulanan ad alanına değişiklikler: Bu özellikle, yeniden adlandırma, ekleme ve kaldırma bir dosya.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Kaynak Denetimi Eklentisi API işlevleri](../extensibility/source-control-plug-in-api-functions.md)   
 [QUERYCHANGESFUNC](../extensibility/querychangesfunc.md)   
 [Hata Kodları](../extensibility/error-codes.md)