---
title: 'IDebugSettingsCallback2:: GetEEMetricDword | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- IDebugSettingsCallback2::GetEEMetricDword
ms.assetid: c5f8f417-0ef0-4fd0-a779-b0a8ead4effe
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 461371efdb6152fc8507f081a6d20ccece932d09
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68155233"
---
# <a name="idebugsettingscallback2geteemetricdword"></a>IDebugSettingsCallback2::GetEEMetricDword
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

İfade değerlendiricisi 'nin belirtilen ölçüsüne karşılık gelen bir değer alır.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp#  
HRESULT GetEEMetricDword(  
   REFGUID guidLang,  
   REFGUID guidVendor,  
   LPCWSTR pszMetric,  
   DWORD*  pdwValue  
);  
```  
  
```csharp  
private int GetEEMetricDword(  
   ref Guid guidLang,  
   ref Guid guidVendor,  
   string   pszMetric,  
   out uint pdwValue  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `guidLang`  
 'ndaki Programlama dilinin benzersiz tanıtıcısı.  
  
 `guidVendor`  
 'ndaki Satıcının benzersiz tanıtıcısı.  
  
 `pszMetric`  
 'ndaki Ölçümün adı.  
  
 `pdwValue`  
 dışı Ölçüm dizesine karşılık gelen değeri döndürür.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IDebugSettingsCallback2](../../../extensibility/debugger/reference/idebugsettingscallback2.md)
