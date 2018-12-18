---
title: 'Iscriptnode:: CreateChildEntry | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IScriptNode. CreateChildEntry
apilocation:
- scrobj.dll
helpviewer_keywords:
- IScriptNode::CreateChildEntry
ms.assetid: b9682505-4457-40e9-8691-235843637506
caps.latest.revision: 17
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8fcc010efe8fcf30a8f467dd94befff54bc5fac5
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24795062"
---
# <a name="iscriptnode-createchildentry"></a>IScriptNode:: CreateChildEntry
Bir alt örneğini ekler `IScriptEntry`.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT CreateChildEntry(  
   ULONG              isn,  
   DWORD              dwCookie,  
   LPCOLESTR          pszDelimiter,  
   IScriptEntry       **ppse  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `isn`  
 [in] Üst alt dizini.  
  
 `dwCookie`  
 [in] Alt öğe girişi konak nesnesi ile ilişkilendirmek için kullanılan bir uygulama tanımlı bir değer.  
  
 `pszDelimiter`  
 [in] Son olarak betik bloğu ayırıcısı adresi. Ayrıştırma için konak betik bloğu sonuna algılamak için sınırlayıcı (örneğin, iki tek tırnak işareti), genellikle kullanır.  
  
 Sınırlayıcı ön işleme sağlamak için altyapısı yazma komut dosyası sağlar. Örneğin, altyapı, tek tırnak işareti ayırıcı olarak kullanmak için iki tek tırnak işareti ile değiştirebilirsiniz. Altyapısını sınırlayıcısı nasıl kullanıldığını belirler.  
  
 Bir sınırlayıcı betik bloğu sonuna işaretlemez ise NULL olarak ayarlayın.  
  
 `ppse`  
 [out] Bir işaretçi alan değişkenin adresini `IScriptEntry` alt örneğinin arabirimi.  
  
 İçin `IScriptNode` bir Web sayfasını temsil eden nesneler, bu parametre döndüren bir `IScriptEntry` bir betik bloğu belirtir örneği.  
  
 İçin `IScriptEntry` bir betik bloğu temsil eden nesneler, bu parametre döndüren bir `IScriptEntry` işlev nesnesi belirtir örneği.  
  
 İçin `IScriptEntry` bir işlevi temsil eden nesneler nesnesi, bu yöntem başarısız olur.  
  
 İçin `IScriptScriptlet` nesneler, bu yöntem başarısız olur.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Bir `HRESULT`. Olası değerler aşağıdaki tablodakileri içerir, ancak bunlarla da sınırlı değildir:  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`S_OK`|Yöntem başarılı oldu.|  
  
## <a name="remarks"></a>Açıklamalar  
 `IScriptNode` Arabirimi bir Web sayfası veya öğelerini temsil eder. `IScriptEntry` Arabirimi (türetilen `IScriptNode`) bir betik bloğu ya da bir işlev nesnesi temsil eder. `IScriptScriptlet` Arabirimi (türetilen `IScriptEntry`) bir olay işleyicisini temsil eder.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Iscriptnode arabirimi](../../winscript/reference/iscriptnode-interface.md)   
 [Iscriptentry arabirimi](../../winscript/reference/iscriptentry-interface.md)