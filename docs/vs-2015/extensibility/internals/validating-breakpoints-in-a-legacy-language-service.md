---
title: Eski dil hizmetinde kesme noktalarını doğrulama | Microsoft Docs
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
- breakpoint validation
- language services [managed package framework], breakpoint validation
ms.assetid: a7e873cd-dfe1-474f-bda5-fd7532774b15
caps.latest.revision: 15
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 0868e516720fd32a445f60f05f345936d24d6d7a
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51734975"
---
# <a name="validating-breakpoints-in-a-legacy-language-service"></a>Eski Dil Hizmetinde Kesme Noktalarını Doğrulama
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Bir kesme noktası programın yürütülmesi belirli bir noktada bir hata ayıklayıcıda çalıştırılırken durması gerektiğini belirtir. Düzenleyicisi bir kesme noktası için geçerli bir konum nelerden, hiçbir bilgiye sahip olduğundan kullanıcı kaynak dosya her satırda bir kesme noktası yerleştirebilirsiniz. Hata ayıklayıcı başlatıldığında, tüm işaretli kesme noktaları (kesme noktaları olarak adlandırılır) çalışan bir program içindeki uygun konumuna bağlıdır. Kesme noktaları doğrulandığından emin olmak için aynı anda bunlar geçerli kod konumlarını işaretler. Örneğin, kaynak kodunda bu konumda hiçbir kod olduğundan açıklama üzerinde bir kesme noktası geçerli değil. Hata ayıklayıcı geçersiz kesme noktalarını devre dışı bırakır.  
  
 Dil hizmeti görüntülenmesini kaynak kodu hakkında bilmesi olduğundan, hata ayıklayıcı başlatılmadan önce kesme noktaları doğrulayabilirsiniz. Geçersiz kılabilirsiniz <xref:Microsoft.VisualStudio.Package.LanguageService.ValidateBreakpointLocation%2A> bir kesme noktası için geçerli bir konum belirten bir yayılma döndürmek için yöntemi. Kesme noktası konumu, hata ayıklayıcı tarafından başlatılan, ancak kullanıcı hata ayıklayıcının için beklemenize gerek kalmadan geçersiz kesme bilgilendirilir hala doğrulanır.  
  
## <a name="implementing-support-for-validating-breakpoints"></a>Kesme noktaları doğrulamak için desteği sağlama  
  
-   <xref:Microsoft.VisualStudio.Package.LanguageService.ValidateBreakpointLocation%2A> Yöntemi, bir kesme noktası konumu verilir. Uygulamanız konumun geçerli olduğunu ve bu kodu tanımlayan bir metin aralığını döndürerek kesme noktası satır konumu ile ilişkili belirtmek olup olmadığına karar vermeniz gerekir.  
  
-   Dönüş <xref:Microsoft.VisualStudio.VSConstants.S_OK> konumu geçerliyse, veya <xref:Microsoft.VisualStudio.VSConstants.S_FALSE> geçerli değilse.  
  
-   Kesme noktası geçerli ise metin aralığı birlikte kesme noktası vurgulanır.  
  
-   Kesme noktası geçersizse, bir hata iletisi durum çubuğunda görünür.  
  
### <a name="example"></a>Örnek  
 Bu örnekte uygulanışı gösterilmektedir <xref:Microsoft.VisualStudio.Package.LanguageService.ValidateBreakpointLocation%2A> belirtilen konumda kod kapsamı (varsa) almak için ayrıştırıcı çağıran yöntemi.  
  
 Bu örnek, eklediğinizi varsayar bir `GetCodeSpan` yönteme <xref:Microsoft.VisualStudio.Package.AuthoringSink> döndürür ve metin aralığı doğrulayan sınıfı `true` geçerli kesme noktası konumu ise.  
  
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
 [Eski Dil Hizmeti Özellikleri](../../extensibility/internals/legacy-language-service-features1.md)

