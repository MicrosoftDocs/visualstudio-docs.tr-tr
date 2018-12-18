---
title: IActiveScriptAuthor::GetLanguageFlags | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptAuthor.GetLanguageFlags
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptAuthor::GetLanguageFlags
ms.assetid: eb244452-62f7-4a73-b48f-1aa05cbcc32d
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6137f1cd77d2f305a9ff9d51ac49c214e4c4237b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24793256"
---
# <a name="iactivescriptauthorgetlanguageflags"></a>IActiveScriptAuthor::GetLanguageFlags
Dil bilgileri döndürür.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetLanguageFlags(  
   DWORD              *pgrfasa  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pgrfasa`  
 [out] Dil bilgileri içeren bayraklar. Aşağıdaki değerlerden bir bileşimi olabilir:  
  
|Sabit|Değer|Açıklama|  
|--------------|-----------|-----------------|  
|fasaPreferInternalHandler|0X0001|Dil komut dosyası olay işleyicisi oluşturma engine uygulaması yerine yazma komut dosyası tarafından tercih eder.|  
|fasaSupportInternalHandler|0X0002|Dil komut dosyası olay işleyicileri altyapısı yazma komut dosyası tarafından oluşturulan destekler.|  
|fasaCaseSensitive|0X0004|Komut dosyası dili büyük küçük harfe duyarlıdır.|  
  
## <a name="return-value"></a>Dönüş Değeri  
 Bir `HRESULT`. Olası değerler aşağıdaki tablodakileri içerir, ancak bunlarla da sınırlı değildir:  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`S_OK`|Yöntem başarılı oldu.|  
  
## <a name="remarks"></a>Açıklamalar  
 Komut dosyası altyapısı yazma olay işleyicileri yönetiliyorsa, uygulamanızın çağırmalıdır `CreateChildHandler` gelen bir `IScriptEntry` nesnesi. Bu oluşturur bir `IScriptScriptlet` olay işleyicisine karşılık gelen nesne. Altyapısı olay işleyici komut dosyası girişine de ekler. Olay işleyicisi belirtilen imza bilgilerini içeren boş bir işlevdir.  
  
 Uygulamanızı olay işleyicileri yönetiliyorsa, çağırmalıdır `CreateChildHandler` gelen bir `IScriptNode` bir olay işleyicisi kod parçacığını temsil eden nesne. Bu oluşturur bir `IScriptScriptlet` olay işleyici kod parçacığı ile ilişkili nesne. Uygulama, bir olay boş bir işlev eklemek de sahip mevcut veya yeni bir işleyici `IScriptEntry` nesnesi.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Iactivescriptauthor arabirimi](../../winscript/reference/iactivescriptauthor-interface.md)