---
title: Bir Gözcü ifadesini değerlendirme | Microsoft Docs
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
- expression evaluation, watch expressions
- watch expressions
ms.assetid: 8317cd52-6fea-4e8f-a739-774dc06bd44b
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 89cc466ee06cd0b4834a03495088c2efdc749e5a
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51780301"
---
# <a name="evaluating-a-watch-expression"></a>Bir Gözcü İfadesini Değerlendirme
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

> [!IMPORTANT]
>  Visual Studio 2015'te, bu şekilde ifade değerlendiricisi uygulama kullanım dışı bırakılmıştır. CLR ifade değerlendiricisi uygulama hakkında daha fazla bilgi için lütfen bkz [CLR ifade Değerlendiricilerini](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) ve [yönetilen ifade değerlendiricisi örnek](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Visual Studio bir Gözcü ifadesini değerini görüntülemek hazır olduğunda, çağrı [EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) sırayla çağıran [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md). Bu üreten bir [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) ifadenin türü ve değeri içeren nesne.  
  
 Bu uygulamada `IDebugParsedExpression::EvaluateSync`, ifade ayrıştırılır ve aynı anda değerlendirilir. Bu uygulama, aşağıdaki görevleri gerçekleştirir:  
  
1.  Ayrıştırır ve değer ve türünü tutan genel bir nesne oluşturmak için ifadeyi değerlendirir. C# ' ta bu olarak temsil edilen bir `object` C++'da bu olarak gösterilir ancak bir `VARIANT`.  
  
2.  Bir sınıf oluşturur (adlı `CValueProperty` Bu örnekte) uygulayan `IDebugProperty2` arabirim ve sınıfında döndürülecek değeri depolar.  
  
3.  Döndürür `IDebugProperty2` alanından arabirim `CValueProperty` nesne.  
  
## <a name="managed-code"></a>Yönetilen kod  
 Bu uygulamasıdır `IDebugParsedExpression::EvaluateSync` yönetilen kod. Yardımcı yöntemi `Tokenize` ayrıştırma ağacı ifadesine ayrıştırır. Yardımcı işlevini `EvalToken` belirteç değerine dönüştürür. Yardımcı işlevini `FindTerm` yinelemeli olarak erişir ayrıştırma ağacı çağırma `EvalToken` bir değeri temsil eden ve herhangi bir işlemi (ekleme veya çıkarma) ifade uygulayarak her düğüm için.  
  
```csharp  
namespace EEMC  
{  
    public class CParsedExpression : IDebugParsedExpression  
    {  
        public HRESULT EvaluateSync(  
            uint evalFlags,  
            uint timeout,  
            IDebugSymbolProvider provider,  
            IDebugAddress address,  
            IDebugBinder binder,  
            string resultType,  
            out IDebugProperty2 result)  
        {  
            HRESULT retval = COM.S_OK;  
            this.evalFlags = evalFlags;  
            this.timeout = timeout;  
            this.provider = provider;  
            this.address = address;  
            this.binder = binder;  
            this.resultType = resultType;  
  
            try  
            {  
                IDebugField field = null;  
                // Tokenize, then parse.  
                tokens = Tokenize(expression);  
                result = new CValueProperty(  
                             expression,  
                             (int) FindTerm(EvalToken(tokens[0], out field),1),  
                             field,  
                             binder);  
            }  
            catch (ParseException)  
            {  
                result = new CValueProperty(expression, "Huh?");  
                retval = COM.E_INVALIDARG;  
            }  
            return retval;  
        }  
    }  
}  
```  
  
## <a name="unmanaged-code"></a>Yönetilmeyen Kod  
 Bu uygulamasıdır `IDebugParsedExpression::EvaluateSync` yönetilmeyen kod. Yardımcı işlevini `Evaluate` ayrıştırır ve döndüren bir ifadeyi değerlendirir bir `VARIANT` sonuç değerini tutan. Yardımcı işlevini `VariantValueToProperty` paketleri `VARIANT` içine bir `CValueProperty` nesne.  
  
```  
[C++]  
STDMETHODIMP CParsedExpression::EvaluateSync(   
    in  DWORD                 evalFlags,  
    in  DWORD                 dwTimeout,  
    in  IDebugSymbolProvider* pprovider,  
    in  IDebugAddress*        paddress,  
    in  IDebugBinder*         pbinder,  
    in  BSTR                  bstrResultType,  
    out IDebugProperty2**     ppproperty )  
{  
    // dwTimeout parameter is ignored in this implementation.  
    if (pprovider == NULL)  
        return E_INVALIDARG;  
  
    if (paddress == NULL)  
        return E_INVALIDARG;  
  
    if (pbinder == NULL)  
        return E_INVALIDARG;  
  
    if (ppproperty == NULL)  
        return E_INVALIDARG;  
    else  
        *ppproperty = 0;  
  
    HRESULT hr;  
    VARIANT value;  
    BSTR    bstrErrorMessage = NULL;  
    hr = ::Evaluate( pprovider,  
                     paddress,  
                     pbinder,  
                     m_expr,  
                     &bstrErrorMessage,  
                     &value );  
    if (hr != S_OK)  
    {  
        if (bstrErrorMessage == NULL)  
            return hr;  
  
        //we can display better messages ourselves.  
        HRESULT hrLocal = S_OK;  
        VARIANT varType;  
        VARIANT varErrorMessage;  
  
        VariantInit( &varType );  
        VariantInit( &varErrorMessage );  
        varErrorMessage.vt      = VT_BSTR;  
        varErrorMessage.bstrVal = bstrErrorMessage;  
  
        CValueProperty* valueProperty = new CValueProperty();  
        if (valueProperty != NULL)  
        {  
            hrLocal = valueProperty->Init(m_expr, varType, varErrorMessage);  
            if (SUCCEEDED(hrLocal))   
            {  
                hrLocal = valueProperty->QueryInterface( IID_IDebugProperty2,  
                        reinterpret_cast<void**>(ppproperty) );  
            }  
        }  
  
        VariantClear(&varType);  
        VariantClear(&varErrorMessage); //frees BSTR  
        if (!valueProperty)  
            return hr;  
        valueProperty->Release();  
        if (FAILED(hrLocal))  
            return hr;  
    }  
    else  
    {  
        if (bstrErrorMessage != NULL)  
            SysFreeString(bstrErrorMessage);  
  
        hr = VariantValueToProperty( pprovider,  
                                     paddress,  
                                     pbinder,  
                                     m_radix,  
                                     m_expr,  
                                     value,  
                                     ppproperty );  
        VariantClear(&value);  
        if (FAILED(hr))  
            return hr;  
    }  
  
    return S_OK;  
}  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Bir Gözcü penceresi ifadesini değerlendirme](../../extensibility/debugger/evaluating-a-watch-window-expression.md)   
 [Örnek İfade Değerlendirme Uygulaması](../../extensibility/debugger/sample-implementation-of-expression-evaluation.md)

