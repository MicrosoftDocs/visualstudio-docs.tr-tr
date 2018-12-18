---
title: Eski dil hizmetinde otomatik değişkenler penceresi desteği | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- language services [managed package framework], Autos window
- Autos window, supporting in language services [managed package framework]
ms.assetid: 47d40aae-7a3c-41e1-a949-34989924aefb
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: a1a2627bd36e6047db00afaada231dc49cde2cc3
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31135828"
---
# <a name="support-for-the-autos-window-in-a-legacy-language-service"></a>Eski dil hizmetinde otomatik değişkenler penceresi desteği
**Otomobiller** penceresi değişkenleri ve ayıklanacak program (ya da bir kesme noktası veya bir özel durum nedeniyle) duraklatıldığında kapsamındaki parametreleri gibi ifadeleri görüntüler. İfadeler değişkenleri, yerel veya genel ve yerel kapsamda değiştirilmiş parametreleri içerebilir. **Otomobiller** penceresi örneklemesi bir sınıf, yapı veya başka bir türü de içerebilir. Bir ifade değerlendiricisi değerlendirebilir herhangi bir şey olası gösterilebileceği **otomobiller** penceresi.  
  
 Yönetilen paket framework (MPF) için doğrudan destek sağlamaz **otomobiller** penceresi. Ancak, geçersiz kılarsanız <xref:Microsoft.VisualStudio.Package.LanguageService.GetProximityExpressions%2A> yöntemi, bir liste olarak sunulan ifadelerin dönebilirsiniz **otomobiller** penceresi.  
  
## <a name="implementing-support-for-the-autos-window"></a>Otomatik değişkenler penceresi uygulama desteği  
 Tüm yapmanız gereken desteklemek için **otomobiller** penceredir uygulamak için <xref:Microsoft.VisualStudio.Package.LanguageService.GetProximityExpressions%2A> yönteminde <xref:Microsoft.VisualStudio.Package.LanguageService> sınıfı. Uygulamanızı ifadeleri görüntülenmelidir kaynak dosya konumu verilen karar vermelisiniz **otomobiller** penceresi. Yöntem her dize tek bir ifade temsil eden dizeleri listesini döndürür. Dönüş değeri <xref:Microsoft.VisualStudio.VSConstants.S_OK> listesi ifadeleri, içerdiğini gösterir ancak <xref:Microsoft.VisualStudio.VSConstants.S_FALSE> göstermek için hiçbir ifadeleri olduğunu gösterir.  
  
 Döndürülen gerçek ifadeler, değişkenlerin ya da kod bu konumda görünür parametreleri adlardır. Bu adları değerleri ve sonra görüntülenen türlerinin edinilir ifade değerlendiricisi geçirilecek **otomobiller** penceresi.  
  
### <a name="example"></a>Örnek  
 Aşağıdaki örnek uygulaması gösterir <xref:Microsoft.VisualStudio.Package.LanguageService.GetProximityExpressions%2A> gelen ifadeleri listesini alır yöntemi <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> ayrıştırma neden kullanarak yöntemini <xref:Microsoft.VisualStudio.Package.ParseReason>. Her bir ifade olarak paketlenir bir `TestVsEnumBSTR` uygulayan <xref:Microsoft.VisualStudio.TextManager.Interop.IVsEnumBSTR> arabirimi.  
  
 Unutmayın `GetAutoExpressionsCount` ve `GetAutoExpression` yöntemleri olan özel yöntemler `TestAuthoringSink` nesne ve bu örnek desteklemek için eklenmiştir. Eklenen hangi ifadelerde bir yolu temsil `TestAuthoringSink` ayrıştırıcı nesnesiyle (çağırarak <xref:Microsoft.VisualStudio.Package.AuthoringSink.AutoExpression%2A> yöntemi) ayrıştırıcının dışında erişilebilir.  
  
```csharp  
using Microsoft.VisualStudio;  
using Microsoft.VisualStudio.Package;  
using Microsoft.VisualStudio.TextManager.Interop;  
  
namespace TestLanguagePackage  
{  
    public class TestLanguageService : LanguageService  
    {  
        public override int GetProximityExpressions(IVsTextBuffer buffer,  
                                                    int line,  
                                                    int col,  
                                                    int cLines,  
                                                    out IVsEnumBSTR ppEnum)  
        {  
            int retval = VSConstants.E_NOTIMPL;  
            ppEnum = null;  
            if (buffer != null)  
            {  
                IVsTextLines textLines = buffer as IVsTextLines;  
                if (textLines != null)  
                {  
                    Source src = this.GetSource(textLines);  
                    if (src != null)  
                    {  
                        TokenInfo tokenInfo = new TokenInfo();  
                        string text = src.GetText();  
                        ParseRequest req = CreateParseRequest(src,  
                                                              line,  
                                                              col,  
                                                              tokenInfo,  
                                                              text,  
                                                              src.GetFilePath(),  
                                                              ParseReason.Autos,  
                                                              null);  
                        req.Scope = this.ParseSource(req);  
                        TestAuthoringSink sink = req.Sink as TestAuthoringSink;  
  
                        retval = VSConstants.S_FALSE;  
                        int spanCount = sink.GetAutoExpressionsCount();  
                        if (spanCount > 0) {  
                            TestVsEnumBSTR bstrList = new TestVsEnumBSTR();  
                            for (int i = 0; i < spanCount; i++)  
                            {  
                                TextSpan span;  
                                sink.GetAutoExpression(i, out span);  
                                string expression = src.GetText(span.iStartLine,  
                                                                span.iStartIndex,  
                                                                span.iEndLine,  
                                                                span.iEndIndex);  
                                bstrList.AddString(expression);  
                            }  
                            ppEnum = bstrList;  
                            retval = VSConstants.S_OK;  
                        }  
                    }  
                }  
            }  
            return retval;  
        }  
    }  
}  
```