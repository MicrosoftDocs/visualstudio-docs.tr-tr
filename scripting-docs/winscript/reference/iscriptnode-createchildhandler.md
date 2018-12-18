---
title: IScriptNode::CreateChildHandler | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IScriptNode.CreateChildHandler
apilocation:
- scrobj.dll
helpviewer_keywords:
- IScriptNode::CreateChildHandler
ms.assetid: 4ce5eb10-1a3f-43b0-a4b7-599a397ed3a2
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ff2ba40d1570e23f0256bd34ca8aff0f8d77ce5c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24795023"
---
# <a name="iscriptnodecreatechildhandler"></a>IScriptNode::CreateChildHandler
Bir kod parçacığı bir alt örneğini ekler bir `IScriptNode`.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT CreateChildHandler(  
   LPCOLESTR          pszDefaultName,  
   LPCOLESTR          *prgpszNames,  
   ULONG              cpszNames,  
   LPCOLESTR          pszEvent,  
   LPCOLESTR          pszDelimiter,  
   ITypeInfo*         ptiSignature,  
   ULONG              iMethodSignature,  
   ULONG              isn,  
   DWORD              dwCookie,  
   IScriptEntry       **ppse  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pszDefaultName`  
 [in] Kod parçacığı ile ilişkilendirmek için varsayılan adı adresidir.  
  
 `prgpszNames`  
 [içinde size_is (`cpszNames`)] tam adı ana bilgisayardaki tanımlayıcılardan listesi.  
  
 `cpszNames`  
 [in] Tanımlayıcıları sayısı `prgpszNames` parametresi.  
  
 `pszEvent`  
 [in] Kod parçacığı ile ilişkili olay adı tanımlayan arabellek adresi.  
  
 `pszDelimiter`  
 [in] Son olarak betik bloğu ayırıcısı adresi. Ayrıştırma için konak betik bloğu sonuna algılamak için sınırlayıcı (örneğin, iki tek tırnak işareti), genellikle kullanır.  
  
 Sınırlayıcı altyapısı yazma komut dosyası tarafından ön işleme sağlar. Örneğin, altyapı, tek tırnak işareti ayırıcı olarak kullanmak için iki tek tırnak işareti ile değiştirebilirsiniz. Altyapısını sınırlayıcısı nasıl kullanıldığını belirler.  
  
 Komut dosyası bloğunun sonunu tanımlamak için sınırlayıcı kullandıysanız NULL olarak ayarlayın.  
  
 `ptiSignature`  
 [in] İşlev nesnesi tür bilgileri.  
  
 `iMethodSignature`  
 [in] İşlev dizinini `ITypeInfo``ptiSignature` parametresi.  
  
 `isn`  
 [in] Üst alt dizini.  
  
 `dwCookie`  
 [in] Giriş konak nesnesi ile ilişkilendirmek için kullanılan bir uygulama tanımlı bir değer.  
  
 `ppse`  
 [out] Bir işaretçi alan değişkenin adresini `IScriptEntry` alt örneğinin arabirimi.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Bir `HRESULT`. Olası değerler aşağıdaki tablodakileri içerir, ancak bunlarla da sınırlı değildir:  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`S_OK`|Yöntem başarılı oldu.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bir kod parçacığını bir olay işleyicisi belirtir. Bu yöntem çağrılırsa bir kod parçacığı oluşturur bir `IScriptNode` bir Web sayfasını temsil eden nesne. Diğer arabirimleri tarafından çağrıldıklarında bu yöntem başarılı olmaz.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Iscriptnode arabirimi](../../winscript/reference/iscriptnode-interface.md)   
 [Iscriptentry arabirimi](../../winscript/reference/iscriptentry-interface.md)