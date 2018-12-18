---
title: IDebugProgram2::WriteDump | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugProgram2::WriteDump
helpviewer_keywords:
- IDebugProgram2::WriteDump
ms.assetid: 375afb8c-882d-44db-bfa7-e2c9eb555122
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 3d2953b3f30a0d485b58afc04e8ce42158a7537e
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49905278"
---
# <a name="idebugprogram2writedump"></a>IDebugProgram2::WriteDump
Bir döküm bir dosyaya yazar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT WriteDump(   
   DUMPTYPE  DumpType,  
   LPCOLESTR pszDumpUrl  
);  
```  
  
```csharp  
int WriteDump(   
   enum_DUMPTYPE  DumpType,  
   string         pszDumpUrl  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `DumpType`  
 [in] Bir değer [DUMPTYPE](../../../extensibility/debugger/reference/dumptype.md) Örneğin, kısa döküm, türünü belirten sabit listesi veya uzun süre.  
  
 `pszDumpUrl`  
 [in] Döküm için yazma URL'si. Genellikle, bu biçimindedir `file://c:\path\filename.ext`, ancak geçerli bir URL olabilir.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Başarılı olursa döndürür `S_OK`; Aksi takdirde bir hata kodu döndürür.  
  
## <a name="remarks"></a>Açıklamalar  
 Bir program dökümü genellikle verilebilir geçerli yığın çerçevesi yığın, program ve program sahip büyük olasılıkla herhangi bir bellek çalışan iş parçacıkları listesi.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)