---
title: IProvideExpressionContexts::EnumExpressionContexts | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IProvideExpressionContexts.EnumExpressionContexts
apilocation:
- jscript.dll
helpviewer_keywords:
- IProvideExpressionContexts::EnumExpressionContexts
ms.assetid: ec5f0065-00df-41e6-b480-4c04ba464872
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c47619fface892e7e0d80141d7d4be53398a356e
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24794981"
---
# <a name="iprovideexpressioncontextsenumexpressioncontexts"></a>IProvideExpressionContexts::EnumExpressionContexts
Bu bileşen tarafından bilinen ifade bağlamlarının bir numaralandırıcı döndürür.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT EnumExpressionContexts(  
   IEnumDebugExpressionContexts**  ppedec  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `ppedec`  
 [out] Bu bileşen tarafından bilinen ifade bağlamları numaralandırması.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntem bir `HRESULT`. Olası değerler aşağıdaki tablodakileri içerir, ancak bunlarla da sınırlı değildir:  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`S_OK`|Yöntem başarılı oldu.|  
  
## <a name="remarks"></a>Açıklamalar  
 İşlem Hata Ayıklama Yöneticisi'ni, belirli bir iş parçacığı ile ilişkili tüm genel ifade bağlamları bulmak için bu yöntemi kullanır.  
  
> [!NOTE]
>  Bu yöntem ilgi iş parçacığı içinde çağrılır. Geçerli iş parçacığının tanımlamak ve uygun bir numaralandırıcı dönmek için uygulayan kadar olur.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Iprovideexpressioncontexts arabirimi](../../winscript/reference/iprovideexpressioncontexts-interface.md)