---
title: Kesme noktaları eski dil hizmetindeki doğrulanıyor | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- breakpoint validation
- language services [managed package framework], breakpoint validation
ms.assetid: a7e873cd-dfe1-474f-bda5-fd7532774b15
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 03bf1534789ba24e1bbf597874ea427057073b61
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31139383"
---
# <a name="validating-breakpoints-in-a-legacy-language-service"></a>Kesme noktaları eski dil hizmetindeki doğrulanıyor
Bir kesme noktası, bir hata ayıklayıcıda çalıştırılırken program yürütme belirli bir noktada durması gerektiğini belirtir. Düzenleyici bir kesme noktası için geçerli bir konum nelerin oluşturduğunu, hiçbir bilgiye sahip olduğundan kullanıcı kaynak dosyasında her satırda bir kesme noktası yerleştirebilirsiniz. Hata ayıklayıcı başlatıldığında, tüm (kesme noktaları olarak adlandırılır) işaretli kesme noktaları çalışan program uygun konuma bağlıdır. Kesme noktaları emin olmak için doğrulanır aynı anda bunlar geçerli kod konumlarını işaretler. Örneğin, kaynak kodu bu konumda hiçbir kod olduğundan bir yorum üzerinde bir kesme noktası geçerli değil. Hata ayıklayıcı geçersiz kesme noktaları devre dışı bırakır.  
  
 Dil hizmeti görüntülenmesini kaynak kodu hakkında bilir olduğundan, hata ayıklayıcı başlatılmadan önce kesme noktaları doğrulayabilirsiniz. Geçersiz kılabilirsiniz <xref:Microsoft.VisualStudio.Package.LanguageService.ValidateBreakpointLocation%2A> bir kesme noktası için geçerli bir konum belirten bir aralık döndürülecek yöntemi. Kesme noktası konumu hala hata ayıklayıcı başlatılır, ancak kullanıcı geçersiz kesme noktaları hata ayıklayıcı yük beklemeden bildirilir doğrulanır.  
  
## <a name="implementing-support-for-validating-breakpoints"></a>Kesme noktaları doğrulamak için destek uygulama  
  
-   <xref:Microsoft.VisualStudio.Package.LanguageService.ValidateBreakpointLocation%2A> Yöntemi olarak kesme konumunu verilir. Uygulamanızı konumun geçerli olduğundan ve bu kodu tanımlayan bir metin aralığını döndürerek kesme satır konumu ile ilişkili belirtmek olup olmadığına karar vermeniz gerekir.  
  
-   Dönüş <xref:Microsoft.VisualStudio.VSConstants.S_OK> konumu geçerliyse, veya <xref:Microsoft.VisualStudio.VSConstants.S_FALSE> geçerli değilse.  
  
-   Kesme noktası geçerliyse metin aralık birlikte kesme vurgulanır.  
  
-   Kesme noktası geçersizse, bir hata iletisi durum çubuğunda görünür.  
  
### <a name="example"></a>Örnek  
 Bu örnek uygulaması gösterir <xref:Microsoft.VisualStudio.Package.LanguageService.ValidateBreakpointLocation%2A> belirtilen konumda aralık kod (varsa) almak için ayrıştırıcı çağıran yöntemi.  
  
 Bu örnekte, eklediğiniz varsayılır bir `GetCodeSpan` yönteme <xref:Microsoft.VisualStudio.Package.AuthoringSink> döndürür ve metin aralık doğrulayan sınıfı `true` geçerli kesme noktası konumu ise.  
  
```csharp  
using Microsoft VisualStudio;  
using Microsoft.VisualStudio.Package;  
using Microsoft.VisualStudio.TextManager.Interop;  
  
namespace TestLanguagePackage  
{  
    class TestLanguageService : LanguageService  
    {  
        public override int ValidateBreakpointLocation(IVsTextBuffer buffer,  
                                                       int line,  
                                                       int col,  
                                                       TextSpan[] pCodeSpan)  
        {  
            int retval = VSConstants.S_FALSE;  
            if (pCodeSpan != null)  
            {  
                // Initialize span to current line by default.  
                pCodeSpan[0].iStartLine = line;  
                pCodeSpan[0].iStartIndex = col;  
                pCodeSpan[0].iEndLine = line;  
                pCodeSpan[0].iEndIndex = col;  
            }  
  
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
                                                              ParseReason.CodeSpan,  
                                                              null);  
                        req.Scope = this.ParseSource(req);  
                        TestAuthoringSink sink = req.Sink as TestAuthoringSink;  
  
                        TextSpan span = new TextSpan();  
                        if (sink.GetCodeSpan(out span))  
                        {  
                            pCodeSpan[0] = span;  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Eski dil hizmeti özellikleri](../../extensibility/internals/legacy-language-service-features1.md)