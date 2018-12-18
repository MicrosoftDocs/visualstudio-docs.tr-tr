---
title: IDebugProperty2::GetExtendedInfo | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugProperty2::GetExtendedInfo
helpviewer_keywords:
- IDebugProperty2::GetExtendedInfo
ms.assetid: 0c9c0b2b-7540-4424-adb5-fce7aa37a026
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 9f6fd711a70c050a6f490a27a56eb860c84de867
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51726959"
---
# <a name="idebugproperty2getextendedinfo"></a>IDebugProperty2::GetExtendedInfo
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Genişletilmiş özelliği bilgilerini.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp#  
HRESULT GetExtendedInfo (   
   REFGUID* guidExtendedInfo,  
   VARIANT* pExtendedInfo  
);  
```  
  
```csharp  
int GetExtendedInfo (   
   ref Guid guidExtendedInfo,  
   out object pExtendedInfo  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `guidExtendedInfo`  
 [in] Alınacak genişletilmiş bilgi türünü tanımlayan GUID. Açıklamalar, Ayrıntılar için bkz.  
  
 `pExtendedInfo`  
 [out] Döndürür bir `VARIANT` (C++) veya nesne (C#) genişletilmiş özellik bilgileri almak için kullanılabilir. Örneğin, bu parametre döndürebilir bir `IUnknown` için sorgulanabilir arabirimi bir [IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md) arabirimi. Açıklamalar, Ayrıntılar için bkz.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Başarılı olursa döndürür `S_OK`; Aksi halde hata kodu döndürür. Döndürür `S_GETEXTENDEDINFO_NO_EXTENDEDINFO` almak için genişletilmiş bilgileri yoksa.  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yöntem, kendisini çağırarak alınıyor için uygun olmayan bilgi almak amacıyla mevcut [GetPropertyInfo](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) yöntemi.  
  
 Aşağıdaki GUID, genellikle (herhangi bir derleme adı kullanılamadığından GUID değerler için C# belirtilir) Bu yöntem tarafından tanınır. Ek GUID'leri iç kullanım için oluşturulabilir.  
  
|Ad|GUID|Açıklama|  
|----------|----------|-----------------|  
|guidDocument|{3f98de84-fee9-11d0-b47f-00a0244a1dd2}|Döndürür bir `IUnknown` belge arabirimi. Genellikle, [IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md) arabirimi elde edilebilir buradan `IUnknown` arabirimi.|  
|guidCodeContext|{e2fc65e 56ce - 11d 1-b528-00aax004a8797}|Döndürür bir `IUnknown` arabirimi belge içeriği. Genellikle, [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) arabirimi elde edilebilir buradan `IUnknown` arabirimi.|  
|guidCustomViewerSupported|{d9c9da31-ffbe-4eeb-9186-23121e3c088c}|Genellikle bir ifade değerlendiricisi tarafından uygulanan özel bir görüntüleyicinin CLSID içeren bir dize döndürür.|  
|guidExtendedInfoSlot|{6df235ad-82c6-4292-9c97-7389770bc42f}|Bu özellik bir yönetilen kodun yerel adresi temsil ediyorsa, istenen Yuva sayısını temsil eden 32 bit bir sayı döndürür.|  
|guidExtendedInfoSignature|{b5fb6d46-f805-417f-96a3-8ba737073ffd}|İmza özelliği nesneyle ilişkili değişken içeren bir dize döndürür.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md)   
 [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)

