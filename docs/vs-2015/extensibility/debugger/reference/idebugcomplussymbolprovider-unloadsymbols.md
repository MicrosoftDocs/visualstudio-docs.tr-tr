---
title: 'IDebugComPlusSymbolProvider:: UnloadSymbols | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- UnloadSymbols
- IDebugComPlusSymbolProvider::UnloadSymbols
ms.assetid: 53e3ddc1-ab47-4097-8fef-b26e5504b37a
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ad78f1b569180a93b195f6a4076cc7396dcf8e53
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68176773"
---
# <a name="idebugcomplussymbolproviderunloadsymbols"></a>IDebugComPlusSymbolProvider::UnloadSymbols
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Belirtilen modülün hata ayıklama sembollerini bellekten kaldırır.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp#  
HRESULT UnloadSymbols(  
   ULONG32 ulAppDomainID,  
   GUID    guidModule  
);  
```  
  
```csharp  
int UnloadSymbols(  
   uint ulAppDomainID,  
   Guid guidModule  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `ulAppDomainID`  
 'ndaki Uygulama etki alanının tanımlayıcısı.  
  
 `guidModule`  
 'ndaki Modülün benzersiz tanıtıcısı.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, [IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md) arabirimini kullanıma sunan bir **CDebugSymbolProvider** nesnesi için bu yöntemin nasıl uygulanacağını gösterir.  
  
```cpp#  
HRESULT CDebugSymbolProvider::UnloadSymbols(  
    ULONG32 ulAppDomainID,  
    GUID guidModule  
)  
{  
    HRESULT hr = S_OK;  
    CComPtr<CModule> pmodule;  
    Module_ID idModule(ulAppDomainID, guidModule);  
  
    METHOD_ENTRY( CDebugSymbolProvider::UnloadSymbols );  
  
#if DEBUG  
  
    DebugVerifyModules();  
#endif  
  
    IfFailGo( GetModule( idModule, &pmodule ) );  
  
#if DEBUG  
  
    DebugVerifyModules();  
#endif  
  
    RemoveModule( pmodule );  
    pmodule->Cleanup();  
  
Error:  
#if DEBUG  
  
    DebugVerifyModules();  
#endif  
  
    METHOD_EXIT( CDebugSymbolProvider::UnloadSymbols, hr );  
  
    return hr;  
}  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md)
