---
title: IDebugProperty3::GetStringCharLength | Microsoft Docs
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
- IDebugProperty3::GetStringCharLength
helpviewer_keywords:
- IDebugProperty3::GetStringCharLength
ms.assetid: 89a8676b-6da9-4358-91c2-039bf33f99e4
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 71fb9bb6a390c4b9f44cce3f06f1fb8c9c82460d
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51792274"
---
# <a name="idebugproperty3getstringcharlength"></a>IDebugProperty3::GetStringCharLength
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

İlişkili özelliğin dizesindeki karakterlerin sayısını döndürür.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetStringCharLength(  
   ULONG *pLen  
);  
```  
  
```csharp  
int GetStringCharLength(  
   out uint pLen  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
  
|Parametre|Açıklama|  
|---------------|-----------------|  
|`pLen`|[out] Özelliğin dizesindeki karakterlerin sayısını döndürür.|  
  
## <a name="return-value"></a>Dönüş Değeri  
 Başarılı olursa döndürür `S_OK`; Aksi halde hata kodu döndürür.  
  
## <a name="remarks"></a>Açıklamalar  
 Genellikle, bu yöntem çağrısı için bir arabellek ayırma için bir tanıtımlar olarak kullanılan [GetStringChars](../../../extensibility/debugger/reference/idebugproperty3-getstringchars.md) yöntemi.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek için bu yöntemi uygulaması gösterilmiştir bir **CProperty** gösteren nesne [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) arabirimi.  
  
```cpp#  
STDMETHODIMP CProperty::GetStringCharLength(ULONG *pLen)  
{  
    HRESULT hr = E_INVALIDARG;  
  
    EVALFLAGS oldEVALFLAGS = m_EVALFLAGS;  
  
    m_EVALFLAGS &= ~EVAL_NOFUNCEVAL;  
  
    if (pLen)  
    {  
        DEBUG_PROPERTY_INFO dpInfo;  
        dpInfo.bstrValue = NULL;  
        ULONG ulen = 0;  
        hr = GetPropertyInfo(DEBUGPROP_INFO_VALUE,10,DEFAULT_TIMEOUT,NULL,0,&dpInfo);  
        if (hr == S_OK && dpInfo.bstrValue)  
        {  
            if (wcscmp(dpInfo.bstrValue,L"Nothing") == 0)  
            {  
                ulen = 0;   //VSWhidbey#64815  
            }  
            else  
            {  
                ulen = ::SysStringLen(dpInfo.bstrValue);  
                if( ulen > 2 &&  
                    dpInfo.bstrValue[0] == L'"' &&  
                    dpInfo.bstrValue[ulen-1] == L'"')  
                {                      
                    ulen = ulen > 2 ? ulen - 2 : ulen;  //remove two double quotes  
                }  
            }  
        }  
        ::SysFreeString(dpInfo.bstrValue);  
        *pLen = ulen;  
    }  
    m_EVALFLAGS = oldEVALFLAGS;  
    return hr;  
}  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [GetStringChars](../../../extensibility/debugger/reference/idebugproperty3-getstringchars.md)   
 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)

