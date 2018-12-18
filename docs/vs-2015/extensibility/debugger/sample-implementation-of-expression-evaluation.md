---
title: Örnek İfade değerlendirme uygulaması | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- expression evaluators
- debugging [Debugging SDK], expression evaluators
- expression evaluation, examples
ms.assetid: 2a5f04b8-6c65-4232-bddd-9093653a22c4
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: a79f61351363ba14b9993181c77e1a9be88515d9
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51735176"
---
# <a name="sample-implementation-of-expression-evaluation"></a>Örnek İfade Değerlendirme Uygulaması
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

> [!IMPORTANT]
>  Visual Studio 2015'te, bu şekilde ifade değerlendiricisi uygulama kullanım dışı bırakılmıştır. CLR ifade değerlendiricisi uygulama hakkında daha fazla bilgi için lütfen bkz [CLR ifade Değerlendiricilerini](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) ve [yönetilen ifade değerlendiricisi örnek](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 İçin bir **Watch** penceresi ifadesini, Visual Studio çağrıları [ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) üretmek için bir [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) nesne. `IDebugExpressionContext2::ParseText` ifade değerlendiricisi (EE) ve çağrı başlatır [ayrıştırma](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) almak için bir [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md) nesne.  
  
 Bu uygulaması `IDebugExpressionEvaluator::Parse` aşağıdaki görevleri gerçekleştirir:  
  
1.  [Yalnızca C++] Hataları aramak için ifade ayrıştırır.  
  
2.  Bir sınıf oluşturur (adlı `CParsedExpression` Bu örnekte) uygulayan `IDebugParsedExpression` arabirim ve ayrıştırılacak ifade sınıfında depolar.  
  
3.  Döndürür `IDebugParsedExpression` alanından arabirim `CParsedExpression` nesne.  
  
> [!NOTE]
>  Aşağıdaki örneklerde ve MyCEE örnek ifade değerlendiricisi değerlendirmesinden gelen ayrıştırma ayrı değil.  
  
## <a name="managed-code"></a>Yönetilen kod  
 Bu uygulamasıdır `IDebugExpressionEvaluator::Parse` yönetilen kod. Yöntemi bu sürümü için ayrıştırma erteler Not [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) ayrıştırma kodunu da aynı anda değerlendirirken (bkz [bir Gözcü ifadesini değerlendirme](../../extensibility/debugger/evaluating-a-watch-expression.md)).  
  
```csharp  
namespace EEMC  
{  
    public class CParsedExpression : IDebugParsedExpression  
    {  
        public HRESULT Parse(  
                string                 expression,   
                uint                   parseFlags,  
                uint                   radix,  
            out string                 errorMessage,   
            out uint                   errorPosition,   
            out IDebugParsedExpression parsedExpression)  
        {   
            errorMessage = "";  
            errorPosition = 0;  
  
            parsedExpression =  
                new CParsedExpression(parseFlags, radix, expression);  
            return COM.S_OK;  
        }  
    }  
}  
```  
  
## <a name="unmanaged-code"></a>Yönetilmeyen Kod  
 Bu uygulamasıdır `IDebugExpressionEvaluator::Parse` yönetilmeyen kod. Bu yöntem bir yardımcı işlevini çağırır `Parse`hataları denetleyin ve ifade ayrıştırma, ancak bu yöntem sonuç değerini yoksayar. Biçimsel Değerlendirme için ertelenmiş [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) nerede ifade ayrıştırılır, değerlendirilmeden sırada (bkz [bir Gözcü ifadesini değerlendirme](../../extensibility/debugger/evaluating-a-watch-expression.md)).  
  
```cpp#  
STDMETHODIMP CExpressionEvaluator::Parse(  
        in    LPCOLESTR                 pszExpression,  
        in    PARSEFLAGS                flags,  
        in    UINT                      radix,  
        out   BSTR                     *pbstrErrorMessages,  
        inout UINT                     *perrorCount,  
        out   IDebugParsedExpression  **ppparsedExpression  
    )  
{  
    if (pbstrErrorMessages == NULL)  
        return E_INVALIDARG;  
    else  
        *pbstrErrormessages = 0;  
  
    if (pparsedExpression == NULL)  
        return E_INVALIDARG;  
    else  
        *pparsedExpression = 0;  
  
    if (perrorCount == NULL)  
        return E_INVALIDARG;  
  
    HRESULT hr;  
    // Look for errors in the expression but ignore results  
    hr = ::Parse( pszExpression, pbstrErrorMessages );  
    if (hr != S_OK)  
        return hr;  
  
    CParsedExpression* pparsedExpr = new CParsedExpression( radix, flags, pszExpression );  
    if (!pparsedExpr)  
        return E_OUTOFMEMORY;  
  
    hr = pparsedExpr->QueryInterface( IID_IDebugParsedExpression,  
                                      reinterpret_cast<void**>(ppparsedExpression) );  
    pparsedExpr->Release();  
  
    return hr;  
}  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Bir Gözcü penceresi ifadesini değerlendirme](../../extensibility/debugger/evaluating-a-watch-window-expression.md)   
 [Bir Gözcü İfadesini Değerlendirme](../../extensibility/debugger/evaluating-a-watch-expression.md)

