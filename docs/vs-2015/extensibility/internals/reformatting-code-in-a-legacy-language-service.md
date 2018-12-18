---
title: Eski dil hizmetinde kodu yeniden biçimlendirme | Microsoft Docs
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
- reformatting code, supporting in language services [managed package framework]
- language services [managed package framework], reformatting code
ms.assetid: 08bb3375-8fef-4f4e-9efa-0d7333bab0eb
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 95b878448904c194bd758d266e67599369502fe6
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51779274"
---
# <a name="reformatting-code-in-a-legacy-language-service"></a>Eski Dil Hizmetinde Kodu Yeniden Biçimlendirme
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

İçinde [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] kaynak kodu girintileri ve boşluk normalleştirme tarafından yeniden biçimlendirildi. Bu, ekleme veya boşluk veya sekme her satırın başında kaldırma, satırları arasına yeni satır ekleyerek veya sekme veya boşluk sekmeleri boşluk yerine içerebilir.  
  
> [!NOTE]
>  **Not** ekleme veya yeni satır karakterleri silme kesme noktalarını ve yer işaretleri gibi işaretçiler etkileyebilir, ancak ekleme veya boşluk veya sekme çıkarma işaretçileri etkilemez.  
  
 Kullanıcıların, seçerek reformatting işlemi başlatabilir **seçimi Biçimlendir** veya **belgeyi Biçimlendir** gelen **Gelişmiş** menüsünde **Düzenle**menüsü. Kod parçacığı veya belirli bir karakter eklendiğinde reformatting işlemi da tetiklenebilir. Bir kapanış ayracı C# dilinde yazdığınız zaman, örneğin, eşleşen bir açma ayracı ve kapatma ayracı arasında her şey için uygun düzeyde otomatik olarak girintilenir.  
  
 Zaman [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] gönderir **seçimi Biçimlendir** veya **belgeyi Biçimlendir** dil hizmeti komutunu <xref:Microsoft.VisualStudio.Package.ViewFilter> sınıf çağrıları <xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A> yönteminde <xref:Microsoft.VisualStudio.Package.Source> sınıfı. Geçersiz kılması gerekir biçimlendirmeyi desteklemek için <xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A> kendi biçimlendirme yöntemi ve tedarik kod.  
  
## <a name="enabling-support-for-reformatting"></a>Yeniden biçimlendirilmeye desteğini etkinleştirme  
 Biçimlendirmeyi desteklemek için `EnableFormatSelection` parametresinin <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> ayarlanmalıdır `true` , VSPackage'ı kaydettiğinizde. Bu ayarlar <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableFormatSelection%2A> özelliğini `true`. <xref:Microsoft.VisualStudio.Package.ViewFilter.CanReformat%2A> Yöntem bu özelliğin değerini döndürür. True döndürürse <xref:Microsoft.VisualStudio.Package.ViewFilter> sınıf çağrıları <xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A>.  
  
## <a name="implementing-reformatting"></a>Biçimlendirme uygulama  
 Biçimlendirme uygulamak için öğesinden bir sınıf türetin <xref:Microsoft.VisualStudio.Package.Source> sınıf ve geçersiz kılma <xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A> yöntemi. <xref:Microsoft.VisualStudio.TextManager.Interop.TextSpan> Nesneyi biçimlendirmek için aralık tanımlar ve <xref:Microsoft.VisualStudio.Package.EditArray> nesnesi üzerinde aralık yapılan düzenlemeleri tutar. Bu aralık tüm belgeyi olabileceğini unutmayın. Ancak, tüm değişiklikleri olduğundan yayılma yapılan birden çok değişiklik büyük olasılıkla, tek bir eylemle ters çevrilebilir olmalıdır. Bunu yapmak için tüm değişiklikleri kaydırma bir <xref:Microsoft.VisualStudio.Package.CompoundAction> nesne (Bu konudaki "CompoundAction sınıfını kullanma" bölümüne bakın).  
  
### <a name="example"></a>Örnek  
 Aşağıdaki örnek tek bir boşluk her virgülden sonra seçiminde virgül sekme tarafından izlenen veya satırın sonunda olup sürece yoktur sağlar. Sondaki boşlukları sonra satırdaki son virgülle silinir. Bu yöntem nasıl çağrılır görmek için bu konudaki "CompoundAction Class kullanma" bölümüne bakın <xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A> yöntemi.  
  
```csharp  
using Microsoft.VisualStudio.Package;  
using Microsoft VisualStudio.TextManager.Interop;  
  
namespace MyLanguagePackage  
{  
    class MySource : Source  
    {  
        private void DoFormatting(EditArray mgr, TextSpan span)  
        {  
            // Make sure there is one space after every comma unless followed  
            // by a tab or comma is at end of line.  
            IVsTextLines pBuffer = GetTextLines();  
            if (pBuffer != null)  
            {  
                int    startIndex = span.iStartIndex;  
                int    endIndex   = 0;  
                string line       = "";  
                // Loop over all lines in span  
                for (int i = span.iStartLine; i <= span.iEndLine; i++)  
                {  
                    if (i < span.iEndLine)  
                    {  
                        pBuffer.GetLengthOfLine(i, out endIndex);  
                    }  
                    else  
                    {  
                        endIndex = span.iEndIndex;  
                    }  
                    pBuffer.GetLineText(i, startIndex, i, endIndex, out line);  
  
                    if (line.Length > 0)  
                    {  
                        int index = 0;  
                        // Loop over all commas in line  
                        while ((index = line.IndexOf(',', index)) != -1)  
                        {  
                            int spaceIndex = index + 1;  
                            // Determine how many spaces after comma  
                            while (spaceIndex < line.Length && line[spaceIndex] == ' ')  
                            {  
                                ++spaceIndex;  
                            }  
  
                            int      spaceCount      = spaceIndex - (index + 1);  
                            string   replacementText = " ";  
                            bool     fDoEdit         = true;  
                            TextSpan editTextSpan    = new TextSpan();  
  
                            editTextSpan.iStartLine  = i;  
                            editTextSpan.iEndLine    = i;  
                            editTextSpan.iStartIndex = index + 1;  
  
                            if (spaceIndex == line.Length)  
                            {  
                                if (spaceCount > 0)  
                                {  
                                    // Delete spaces after a comma at end of line  
                                    editTextSpan.iEndIndex = spaceIndex;  
                                    replacementText = "";  
                                }  
                                else  
                                {  
                                    // Otherwise, do not add spaces if comma is  
                                    // at end of line.  
                                    fDoEdit = false;  
                                }  
                            }  
                            else if (spaceCount == 0)  
                            {  
                                if (spaceIndex < line.Length && line[spaceIndex] == '\t')  
                                {  
                                    // Do not insert space if a tab follows  
                                    // a comma.  
                                    fDoEdit = false;  
                                }  
                                else  
                                {  
                                    // No space after comma so add a space.  
                                    editTextSpan.iEndIndex = index + 1;  
                                }  
                            }  
                            else if (spaceCount > 1)  
                            {  
                                // More than one space after comma, replace  
                                // with a single space.  
                                editTextSpan.iEndIndex = spaceIndex;  
                            }  
                            else  
                            {  
                                // Single space after a comma and not at end  
                                // of the line, leave it alone.  
                                fDoEdit = false;  
                            }  
                            if (fDoEdit)  
                            {  
                                // Add edit operation  
                                mgr.Add(new EditSpan(editTextSpan, replacementText));  
                            }  
                            index = spaceIndex;  
                        }  
                    }  
                    startIndex = 0; // All subsequent lines start at 0  
                }  
                // Apply all edits  
                mgr.ApplyEdits();  
            }  
        }  
    }  
}  
```  
  
## <a name="using-the-compoundaction-class"></a>CompoundAction sınıfını kullanma  
 Tüm kodun bir bölümünü bitti yeniden biçimlendirme içinde tek bir eylem geri alınamaz olmalıdır. Bu kullanarak gerçekleştirilebilir bir <xref:Microsoft.VisualStudio.Package.CompoundAction> sınıfı. Bu sınıf, bir dizi metin arabelleğini düzenleme işlemleri tek düzen işleminde göz önünde sarmalar.  
  
### <a name="example"></a>Örnek  
 İşte nasıl kullanılacağına ilişkin bir örnek <xref:Microsoft.VisualStudio.Package.CompoundAction> sınıfı. "Uygulama desteği için biçimlendiriliyor" bölümünde örneği için bu konudaki örneğe bakın `DoFormatting` yöntemi.  
  
```csharp  
using Microsoft.VisualStudio.Package;  
using Microsoft VisualStudio.TextManager.Interop;  
  
namespace MyLanguagePackage  
{  
    class MySource : Source  
    {  
        public override void ReformatSpan(EditArray mgr, TextSpan span)  
        {  
            string description = "Reformat code";  
            CompoundAction ca = new CompoundAction(this, description);  
            using (ca)  
            {  
                ca.FlushEditActions();      // Flush any pending edits  
                DoFormatting(mgr, span);    // Format the span  
            }  
        }  
    }  
}  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Eski Dil Hizmeti Özellikleri](../../extensibility/internals/legacy-language-service-features1.md)

