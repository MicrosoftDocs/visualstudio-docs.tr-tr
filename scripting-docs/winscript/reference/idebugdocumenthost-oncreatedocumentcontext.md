---
title: IDebugDocumentHost::OnCreateDocumentContext | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentHost.OnCreateDocumentContext
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDebugDocumentHost::OnCreateDocumentContext
ms.assetid: 080c8604-cfd7-484e-a337-15040870e683
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 55598a4191d421d3aea01d27cc7991b70bd6a019
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24794171"
---
# <a name="idebugdocumenthostoncreatedocumentcontext"></a>IDebugDocumentHost::OnCreateDocumentContext
Ana bilgisayar yeni bir belge bağlam oluşturuldu ve isteğe bağlı olarak yeni bağlam için bilinmeyen denetleme dönmek ana bilgisayar tanır bildirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT OnCreateDocumentContext(  
   IUnknown**  ppunkOuter  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `ppunkOuter`  
 [out] Yeni bağlam denetleyen bir nesne.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntem bir `HRESULT`. Olası değerler aşağıdaki tablodakileri içerir, ancak bunlarla da sınırlı değildir:  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`S_OK`|Yöntem başarılı oldu.|  
|`E_NOTIMPL`|Ana bilgisayar kontrol eden bir nesne sağlamaz.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yöntem için sağlanan yardımcı belge bağlamları yeni işlevler eklemek ana bilgisayar sağlar. Bu yöntem döndürebilir **E_NOTIMPL** veya servis talebi çağıran olduğu bağlam oluşturmaktan sorumlu null dış bir nesne.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Idebugdocumenthost arabirimi](../../winscript/reference/idebugdocumenthost-interface.md)