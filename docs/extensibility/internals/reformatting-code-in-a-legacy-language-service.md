---
title: Eski dil hizmeti kodunda yeniden biçimlendirme | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- reformatting code, supporting in language services [managed package framework]
- language services [managed package framework], reformatting code
ms.assetid: 08bb3375-8fef-4f4e-9efa-0d7333bab0eb
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 392afbafc2ce15dbf7ee347efdf24ce1f7fe2301
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31133202"
---
# <a name="reformatting-code-in-a-legacy-language-service"></a>Eski dil hizmeti kodunda yeniden biçimlendirme

İçinde [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] kaynak kodu girintileri ve boşluk kullanımını normalleştirme tarafından yeniden biçimlendirilen. Bu, ekleme veya boşluk ya da her satırın başındaki sekme kaldırma, satırları arasındaki yeni satır ekleme veya sekme veya boşluk ile sekme alanları değiştirerek içerebilir.  
  
>**Not:** ekleme veya yeni satır karakterlerini silme kesme noktaları ve yer işaretleri gibi işaretçileri etkileyebilir, ancak ekleyerek veya kaldırarak alanları veya sekmeler işaretçileri etkilemez.  
  
Kullanıcılar, reformatting işlemi seçerek başlayabilir **Biçim Seçimi** veya **belgeyi Biçimlendir** gelen **Gelişmiş** menüsünde **Düzenle**menüsü. Kod parçacığı veya belirli bir karakterin takıldığında reformatting işlemi da tetiklenebilir. Bir kapanış ayracı C# ' ta yazdığınızda, örneğin, eşleşen açma ayracı kapatma parantezi arasındaki her şeyin doğru seviyesi otomatik olarak girintili olur.
  
Zaman [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] gönderir **Biçim Seçimi** veya **belgeyi Biçimlendir** dil hizmetine komutunu <xref:Microsoft.VisualStudio.Package.ViewFilter> sınıfı çağrıları <xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A> yönteminde <xref:Microsoft.VisualStudio.Package.Source> sınıfı. Geçersiz kılması gerekir biçimlendirme desteklemek için <xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A> yöntemi ve kaynağı kendi biçimlendirme kodu.  
  
## <a name="enabling-support-for-reformatting"></a>Biçimlendirme için desteğini etkinleştirme  

Biçimlendirme, desteklemek için `EnableFormatSelection` parametresinin <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> ayarlanmalıdır `true` , VSPackage kaydettiğinizde. Bu ayarlar <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableFormatSelection%2A> özelliğine `true`. <xref:Microsoft.VisualStudio.Package.ViewFilter.CanReformat%2A> Yöntem bu özelliğin değerini döndürür. True döndürürse <xref:Microsoft.VisualStudio.Package.ViewFilter> sınıfı çağrıları <xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A>.  
  
## <a name="implementing-reformatting"></a>Yeniden biçimlendirme uygulama

Yeniden biçimlendirme uygulamak için öğesinden bir sınıf türetin <xref:Microsoft.VisualStudio.Package.Source> sınıfı ve geçersiz kılma <xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A> yöntemi. <xref:Microsoft.VisualStudio.TextManager.Interop.TextSpan> Nesnesi biçimlendirmek için aralık açıklar ve <xref:Microsoft.VisualStudio.Package.EditArray> nesnesi üzerinde aralık yapılan düzenlemeler tutar. Bu aralık tüm belgeyi olabileceğini unutmayın. Ancak, tüm değişiklikler olduğundan yayılma birden çok değişikliklerinin büyük olasılıkla, tek bir eylemle ters çevrilebilir olmalıdır. Bunu yapmak için tüm değişiklikleri sarmalamak bir <xref:Microsoft.VisualStudio.Package.CompoundAction> nesne (Bu konudaki "CompoundAction sınıfını kullanma" bölümüne bakın).

### <a name="example"></a>Örnek  

Aşağıdaki örnek var. tek bir boşluk sonra her virgül seçimde virgülden sekmesini tarafından izlenen veya satırın sonuna kaldırılana kadar sağlar. Bir satırda son virgülle silinir sonra sonunda boşluk. Bu yöntem nasıl çağrılır görmek için bu konudaki "CompoundAction sınıf kullanma" bölümüne bakın <xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A> yöntemi.  

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
 
Tüm kod bir bölüm bitti yeniden biçimlendirme tek bir eylemle ters çevrilebilir olmalıdır. Bu kullanılarak gerçekleştirilebilir bir <xref:Microsoft.VisualStudio.Package.CompoundAction> sınıfı. Bu sınıf, bir metin arabelleği düzenleme işlemlerinin tek düzenleme işlemi içine sarmalar.  
  
### <a name="example"></a>Örnek

İşte nasıl kullanılacağına ilişkin bir örnek <xref:Microsoft.VisualStudio.Package.CompoundAction> sınıfı. Bir örneği için bu konudaki "Uygulama desteği için biçimlendirme" bölümündeki örnek `DoFormatting` yöntemi.  
  
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

[Eski dil hizmeti özellikleri](legacy-language-service-features1.md)