---
title: Eski dil hizmetinde anahat oluşturma | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- outlining
- language services [managed package framework], outlining
- outlining, supporting in language services [managed package framework]
ms.assetid: 7b5578b4-a20a-4b94-ad4c-98687ac133b9
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b899f53ba6b2a0b58997cc51a83a0d9ca8480e63
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31135659"
---
# <a name="outlining-in-a-legacy-language-service"></a>Eski dil hizmetinde anahat oluşturma
Anahat oluşturma, karmaşık bir program bir genel bakış veya anahat daraltmak mümkün kılar. Örneğin, C# ' ta tüm yöntemleri yalnızca yöntem imzası gösteren tek bir satır için daraltılabilir. Ayrıca, yapılar ve sınıflar yalnızca yapılar ve sınıflar adlarını göstermek için daraltılabilir. İçinde tek bir yöntemi, yalnızca ilk satır deyimlerinin göstererek genel akış göstermek için karmaşık mantık daraltılabilen `foreach`, `if`, ve `while`.  
  
 Eski dil hizmetler bir VSPackage bir parçası olarak uygulanır, ancak dil hizmet özellikleri uygulamak için daha yeni MEF uzantıları kullanmak için bir yoludur. Daha fazla bilgi bulmak için bkz: [izlenecek yol: anahat oluşturma](../../extensibility/walkthrough-outlining.md).  
  
> [!NOTE]
>  Yeni Düzenleyicisi API mümkün olan en kısa sürede kullanmaya başlamanızı öneriyoruz. Bu dil hizmetinizin performansını ve yeni Düzenleyicisi özelliklerden yararlanmak sağlar.  
  
## <a name="enabling-support-for-outlining"></a>Anahat oluşturma için desteğini etkinleştirme  
 `AutoOutlining` Kayıt defteri girdisini otomatik anahat oluşturma etkinleştirmek için 1 olarak ayarlanır. Bir dosya yüklenen ya da gizli bölgeleri tanımlamak ve anahat karakterlerin göstermek için değiştirilen otomatik anahat oluşturma tüm kaynak ayrıştırma ayarlar. Anahat oluşturma da el ile kullanıcı tarafından denetlenebilir.  
  
 Değeri `AutoOutlining` kayıt defteri girdisi aracılığıyla elde edilebilir <xref:Microsoft.VisualStudio.Package.LanguagePreferences.AutoOutlining%2A> özellikte <xref:Microsoft.VisualStudio.Package.LanguagePreferences> sınıfı. `AutoOutlining` Kayıt defteri girişi, adlandırılmış bir parametre ile başlatılabilir <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> özniteliği (bkz [eski dil hizmeti kaydetme](../../extensibility/internals/registering-a-legacy-language-service1.md) Ayrıntılar için).  
  
## <a name="the-hidden-region"></a>Gizli bölge  
 Anahat oluşturma sağlamak için dil hizmetinizi gizli bölgeler desteklemesi gerekir. Genişletilmiş veya daraltılmış metin yayılma bunlar. Gizli bölgeler, süslü ayraçlar gibi standart dil simgeler veya özel sembolleri tarafından sınırlandırılabilir. Örneğin, C# sahip bir `#region` / `#endregion` gizli bir bölge sınırlandıran çifti.  
  
 Gizli bölgeleri olarak sunulan bir gizli bölge yöneticisi tarafından yönetilen <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> arabirimi.  
  
 Anahat oluşturma kullanan gizli bölgeleri <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenRegion> arabirim ve gizli bölge, geçerli görünür durumu ve ne zaman aralığı daraltılmış gösterilecek başlık aralık içermelidir.  
  
 Dil hizmeti ayrıştırıcı kullanan <xref:Microsoft.VisualStudio.Package.AuthoringSink.AddHiddenRegion%2A> gizli bölgeler için varsayılan davranışa sahip yeni bir gizli bölgesi ekleme yöntemi sırada <xref:Microsoft.VisualStudio.Package.AuthoringSink.AddHiddenRegion%2A> yöntemi görünümünü ve davranışını hattın özelleştirmenizi sağlar. Gizli bölgeler gizli bölge oturumuna verilen sonra [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] dil hizmeti için gizli bölgeler yönetir.  
  
 Gizli bölge oturum bozulduğunda belirlemeniz gerekiyorsa, gizli bir bölge değiştirilir veya belirli bir gizli bölge görünür olduğundan emin olmanız gerekir; öğesinden bir sınıf türetin <xref:Microsoft.VisualStudio.Package.Source> sınıfı ve uygun yöntemleri geçersiz kılma <xref:Microsoft.VisualStudio.Package.Source.OnBeforeSessionEnd%2A>, <xref:Microsoft.VisualStudio.Package.Source.OnHiddenRegionChange%2A>, ve <xref:Microsoft.VisualStudio.Package.Source.MakeBaseSpanVisible%2A>sırasıyla.  
  
### <a name="example"></a>Örnek  
 Burada, süslü ayraçlar tüm çiftleri için gizli bölgeleri oluşturma basitleştirilmiş bir örnek verilmiştir. Dil Ayraç eşleştirme sağlar ve eşleştirilmesi için ayraç en az süslü ayraçlar dahil varsayılır ({ve}). Bu yaklaşım yalnızca tanım amaçlıdır. Tam bir uygulamaya durumlarda tam işlenmesini olurdu <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>. Bu örnek ayrıca nasıl ayarlanacağını gösterir <xref:Microsoft.VisualStudio.Package.LanguagePreferences.AutoOutlining%2A> tercih `true` geçici olarak. Alternatif belirtmektir `AutoOutlining` parametresinde belirtilen `ProvideLanguageServiceAttribute` özniteliği dil paketi.  
  
 Bu örnek, açıklamalar, dizeleri ve değişmez değerleri için C# kuralları varsayar.  
  
```csharp  
using Microsoft.VisualStudio.Package;  
using Microsoft.VisualStudio.TextManager.Interop;  
  
namespace MyLanguagePackage  
{  
  
    public class MyLanguageService : LanguageService  
    {  
        private LanguagePreferences m_preferences;  
  
        public override LanguagePreferences  GetLanguagePreferences()  
        {  
            if (m_preferences == null)  
            {  
                m_preferences = new LanguagePreferences(this.Site,  
                                                        typeof(MyLanguageService).GUID,  
                                                        Name);  
                m_preferences.Init();  
                // Temporarily enabled auto-outlining  
                m_preferences.AutoOutlining = true;  
            }  
            return m_preferences;  
        }  
  
        public override AuthoringScope  ParseSource(ParseRequest req)  
        {  
            Source source = (Source) this.GetSource(req.FileName);  
            switch (req.Reason)  
            {  
               case ParseReason.HighlightBraces:  
               case ParseReason.MatchBraces:  
               case ParseReason.MemberSelectAndHighlightBraces:  
                  if (source.Braces != null)  
                  {  
                      foreach (TextSpan[] brace in source.Braces)  
                      {  
                         if (brace.Length == 2)  
                         {  
                             if (req.Sink.HiddenRegions == true   
                                   && source.GetText(brace[0]).Equals("{")   
                                   && source.GetText(brace[1]).Equals("}"))  
                             {  
                                //construct a TextSpan of everything between the braces  
                                TextSpan hideSpan = new TextSpan();  
                                hideSpan.iStartIndex = brace[0].iStartIndex;  
                                hideSpan.iStartLine = brace[0].iStartLine;  
                                hideSpan.iEndIndex = brace[1].iEndIndex;  
                                hideSpan.iEndLine = brace[1].iEndLine;  
                                req.Sink.ProcessHiddenRegions = true;  
                                req.Sink.AddHiddenRegion(hideSpan);  
                             }  
                             req.Sink.MatchPair(brace[0], brace[1], 1);  
                         }  
                         else if (brace.Length >= 3)  
                             req.Sink.MatchTriple(brace[0], brace[1], brace[2], 1);  
                  }  
        }  
                   break;  
               default:  
                   break;  
      }  
            // Must always return a valid AuthoringScope object.  
            return new MyAuthoringScope();  
        }  
    }  
}  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Eski dil hizmeti özellikleri](../../extensibility/internals/legacy-language-service-features1.md)   
 [Eski dil hizmeti kaydetme](../../extensibility/internals/registering-a-legacy-language-service1.md)