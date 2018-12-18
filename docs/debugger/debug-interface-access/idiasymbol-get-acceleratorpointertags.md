---
title: IDiaSymbol::get_acceleratorPointerTags | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 30e13cee-e511-49ec-affd-99b0097071b2
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 24db7164335a8deffbac7cb4f62207a974f6efb9
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2018
ms.locfileid: "31460677"
---
# <a name="idiasymbolgetacceleratorpointertags"></a>IDiaSymbol::get_acceleratorPointerTags
Karşılık gelen tüm Hızlandırıcı işaretçi etiket değerleri bir C++ AMP Hızlandırıcı saplama işlevi döndürür.  
  
## <a name="syntax"></a>Sözdizimi  
  
```C++  
HRESULT get_acceleratorPointerTags(   
   DWORD          cnt,  
   DWORD*         pcnt,  
   DWORD*         pPointerTags);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `cnt`  
 [in] Çıkış dizisi boyutunu `pPointerTags`.  
  
 `pcnt`  
 [out] Hızlandırıcı işaretçi C++ AMP Hızlandırıcı saplama işlevi etiketlerinde sayısı.  
  
 `pPointerTags`  
 [out] A `DWORD` C++ AMP Hızlandırıcı saplama işlevi Hızlandırıcı işaretçi etiketi değerler ile doldurulan bir dizi işaretçi.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Başarılı olursa, döndürür `S_OK`; Aksi halde döndürür `S_FALSE` veya bir hata kodu.  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yöntem üzerinde çağrılır bir `IDiaSymbol` C++ AMP Hızlandırıcı saplama işleve karşılık gelen arabirim.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)