---
title: Eski dil hizmetinde özel belge özellikleri | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- custom document properties, language services [managed package framework]
- document properties, custom
- language services [managed package framework], custom document properties
ms.assetid: cc714a67-b33e-4440-9203-3c90f648bd9c
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 473b3970fe8a7d7e65b8e569420b2be6455a3d14
ms.sourcegitcommit: 1c2ed640512ba613b3bbbc9ce348e28be6ca3e45
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/03/2018
ms.locfileid: "39499090"
---
# <a name="custom-document-properties-in-a-legacy-language-service"></a>Eski dil hizmetinde özel belge özellikleri
Belge özellikleri görüntülenebilir [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] **özellikleri** penceresi. Programlama dilleri, tek tek kaynak dosyalarıyla ilişkili özellikler genellikle gerekmez. Ancak, XML kodlama, şema ve stil sayfası etkileyen belge özelliklerini destekler.  
  
## <a name="discussion"></a>Tartışma  
 Dilinizi özel belge özellikleri gerekiyorsa bir sınıftan türetilmelidir <xref:Microsoft.VisualStudio.Package.DocumentProperties> sınıfı ve gerekli özellikleri türetilmiş sınıfınızın uygulayın.  
  
 Ayrıca, belge özellikleri genellikle kaynak dosyada depolanır. Bu özellik bilgilerini görüntülemek için kaynak dosyasından ayrıştırmak için dil hizmeti gerektirir **özellikleri** penceresi ve belge özelliklerinde bir değişiklik yapıldığında, kaynak dosyasını güncelleştirmek için  **Özellikleri** penceresi.  
  
## <a name="customize-the-documentproperties-class"></a>DocumentProperties sınıfı özelleştirme  
 Özel belge özellikleri desteklemek için öğesinden bir sınıf türetin <xref:Microsoft.VisualStudio.Package.DocumentProperties> sınıfı ve gerektiği gibi birçok özelliği ekleyebilirsiniz. Kullanıcı öznitelikleri, bunları düzenlemek için da sağlamanız **özellikleri** penceresini görüntüleme. Yalnızca bir özelliği varsa, bir `get` erişimci olarak salt okunur olarak gösterilen **özellikleri** penceresi. Bir özellik hem de varsa `get` ve `set` erişimcileri özelliği de güncelleştirilebilir içinde **özellikleri** penceresi.  
  
### <a name="example"></a>Örnek  
 İşte bir örnek sınıfından türetilen <xref:Microsoft.VisualStudio.Package.DocumentProperties>, iki özelliklerini gösteren `Filename` ve `Description`. Bir özelliği güncelleştirildiğinde, özel bir yöntem <xref:Microsoft.VisualStudio.Package.LanguageService> sınıf özelliği kaynak dosyaya yazmak için çağrılır.  
  
```csharp  
using System.ComponentModel;  
using Microsoft.VisualStudio.Package;  
  
namespace TestLanguagePackage  
{  
    class TestDocumentProperties : DocumentProperties  
    {  
        private string m_filename;  
        private string m_description;  
  
        public TestDocumentProperties(CodeWindowManager mgr)  
            : base(mgr)  
        {  
        }  
  
        // Helper function to initialize this property without  
        // going through the FileName property (which does a lot  
        // more than we need when the filename is set).  
        public void SetFileName(string filename)  
        {  
            m_filename = filename;  
        }  
  
        // Helper function to initialize this property without  
        // going through the Description property (which does a lot  
        // more than we need when the description is set).  
        public void SetDescription(string description)  
        {  
            m_description = description;  
        }  
  
        ////////////////////////////////////////////////////////////  
        // The document properties  
  
        [CategoryAttribute("General")]  
        [DescriptionAttribute("Name of the file")]  
        [DisplayNameAttribute("Filename")]  
        public string FileName  
        {  
            get { return m_filename; }  
            set  
            {  
               if (value != m_filename)  
               {  
                    m_filename = value;  
                    SetPropertyValue("Filename", m_filename);  
               }  
            }  
        }  
  
        [CategoryAttribute("General")]  
        [DescriptionAttribute("Description of the file")]  
        [DisplayNameAttribute("Description")]  
        public string Description  
        {  
            get { return m_description; }  
            set  
            {  
                if (value != m_description)  
                {  
                    m_description = value;  
                    SetPropertyValue("Description", m_description);  
                }  
            }  
        }  
  
        ///////////////////////////////////////////////////////////  
        // Private methods.  
  
        private void SetPropertyValue(string propertyName, string propertyValue)  
        {  
            Source src = this.GetSource();  
            if (src != null)  
            {  
                TestLanguageService service = src.LanguageService as TestLanguageService;  
                if (service != null)  
                {  
                    // Set the property in to the source file.  
                    service.SetPropertyValue(src, propertyName, propertyValue);  
                }  
            }  
        }  
    }  
}  
```  
  
## <a name="instantiate-the-custom-documentproperties-class"></a>Özel DocumentProperties sınıfının örneği  
 Özel belge özellikleri sınıfınıza örneklemek için geçersiz kılmanız gerekir <xref:Microsoft.VisualStudio.Package.LanguageService.CreateDocumentProperties%2A> sürümünüz yönteminde <xref:Microsoft.VisualStudio.Package.LanguageService> tek bir örneğini döndürülecek sınıfı, <xref:Microsoft.VisualStudio.Package.DocumentProperties> sınıfı.  
  
### <a name="example"></a>Örnek  
  
```csharp  
using System.ComponentModel;  
using Microsoft.VisualStudio.Package;  
  
namespace TestLanguagePackage  
{  
    class TestLanguageService : LanguageService  
    {  
        private TestDocumentProperties m_documentProperties;  
  
        public override DocumentProperties CreateDocumentProperties(CodeWindowManager mgr)  
        {  
            if (m_documentProperties == null)  
            {  
                m_documentProperties = new TestDocumentProperties(mgr);  
            }  
            return m_documentProperties;  
        }  
    }  
}  
```  
  
## <a name="properties-in-the-source-file"></a>Kaynak dosyasındaki özellikleri  
 Belge özellikleri için kaynak dosyası genellikle belirli olduğundan, değerleri kaynak dosyada depolanır. Bu dil ayrıştırıcı ya da bu özellikleri tanımlamak için tarayıcı desteği gerektirir. Örneğin, bir XML belgesi özelliklerini kök düğüm üzerinde depolanır. Kök düğümü değerlerine ne zaman değiştirildiği **özellikleri** pencere değerleri değiştirilir ve kök düğümü düzenleyicide güncelleştirilir.  
  
### <a name="example"></a>Örnek  
 Bu örnek özelliklerini depolayan `Filename` ve `Description` kaynak dosyasının ilk iki satır olarak bir özel açıklama üst bilgisinde katıştırılmış:  
  
```  
//!Filename = file.testext  
//!Description = A sample file  
```  
  
 Bu örnekte, almak ve kullanıcı kaynak dosyayı doğrudan değiştirirse özellikler güncelleştirilir nasıl kaynak dosyanın da ilk iki satırlarından belge özelliklerini ayarlamak için gereken iki yöntemi gösterilir. `SetPropertyValue` One yöntemi aynı işte gösterilen örnekte adlı `TestDocumentProperties` gösterildiği gibi sınıf *DocumentProperties sınıfı özelleştirme* bölümü.  
  
 Bu örnekte, ilk iki satırını belirteçlerinde türünü belirlemek için tarayıcı kullanır. Bu örnek yalnızca tanım amaçlıdır. Bu duruma yönelik daha tipik bir yaklaşım ne ayrıştırma ağacı burada her düğüm ağacı belirli bir belirteç hakkında bilgi içeren çağrılır kaynak dosyasını ayrıştırma sağlamaktır. Kök düğümü belge özelliklerini içerir.  
  
```csharp  
using System.ComponentModel;  
using Microsoft.VisualStudio.Package;  
  
namespace TestLanguagePackage  
{  
    // TokenType.Comment is the last item in that enumeration.  
    public enum TestTokenTypes  
    {  
        DocPropertyLine = TokenType.Comment + 1,  
        DocPropertyName,  
        DocPropertyAssign,  
        DocPropertyValue  
    }  
  
    class TestLanguageService : LanguageService  
    {  
        // Search this many lines from the beginning for properties.  
        private static int maxLinesToSearch = 2;  
  
        private TestDocumentProperties m_documentProperties;  
  
        // Called whenever a full parsing operation has completed.  
        public override void OnParseComplete(ParseRequest req)  
        {  
            if (m_documentProperties != null)  
            {  
                Source src = GetSource(req.View);  
                if (src != null)  
                {  
                    string value = GetPropertyValue(src, "Filename");  
                    m_documentProperties.SetFileName(value);  
  
                    value = GetPropertyValue(src, "Description");  
                    m_documentProperties.SetDescription(value);  
  
                    // Update the Properties Window.  
                    m_documentProperties.Refresh();  
                }  
            }  
        }  
  
        // Retrieves the specified property value from the given source.  
        public string GetPropertyValue(Source src, string propertyName)  
        {  
            string propertyValue = "";  
  
            if (src != null)  
            {  
                IVsTextColorState colorState = src.ColorState;  
                if (colorState != null)  
                {  
                    string      line;  
                    TokenInfo[] lineInfo = null;  
                    int         i;  
  
                    for (i = 0; i < maxLinesToSearch; i++)  
                    {  
                        line     = src.GetLine(i);  
                        lineInfo = src.GetColorizer().GetLineInfo(  
                                                        src.GetTextLines(),  
                                                        i,  
                                                        colorState);  
                        if (lineInfo == null)  
                        {  
                            continue;  
                        }  
                        if (lineInfo[0].Type != (TokenType)TestTokenTypes.DocPropertyLine)  
                        {  
                            // Not a property line.  
                            continue;  
                        }  
                        TokenInfo valueInfo = new TokenInfo();  
                        int tokenIndex = -1;  
                        for (tokenIndex = 0;  
                             tokenIndex < lineInfo.Length;  
                             tokenIndex++)  
                        {  
                            if (lineInfo[tokenIndex].Type == (TokenType)TestTokenTypes.DocPropertyName)  
                            {  
                                break;  
                            }  
                        }  
                        if (tokenIndex >= lineInfo.Length)  
                        {  
                            // No property name on the line.  
                            continue;  
                        }  
                        string name = src.GetText(i,  
                                                  lineInfo[tokenIndex].StartIndex,  
                                                  i,  
                                                  lineInfo[tokenIndex].EndIndex + 1);  
                        if (name != null)  
                        {  
                            if (String.Compare(name, propertyName, true) == 0)  
                            {  
                                for ( ;  
                                     tokenIndex < lineInfo.Length;  
                                     tokenIndex++)  
                                {  
                                    if (lineInfo[tokenIndex].Type == (TokenType)TestTokenTypes.DocPropertyValue)  
                                    {  
                                        break;  
                                    }  
                                }  
                                if (tokenIndex < lineInfo.Length)  
                                {  
                                    propertyValue = src.GetText(i,  
                                                          lineInfo[tokenIndex].StartIndex,  
                                                          i,  
                                                          lineInfo[tokenIndex].EndIndex + 1);  
                                }  
                                break;  
                            }  
                        }  
                    }  
                }  
            }  
            return propertyValue;  
        }  
  
        // Sets the specified property into the given source file.  
        // Called from the TestDocumentProperties class.  
        public void SetPropertyValue(Source src, string propertyName, string propertyValue)  
        {  
            string newLine;  
  
            if (propertyName == null || propertyName == "")  
            {  
                // No property name, so nothing to do  
                return;  
            }  
            if (propertyValue == null)  
            {  
                propertyValue = "";  
            }  
            // This is the line to be inserted.  
            newLine = String.Format("//!{0} = {1}", propertyName, propertyValue);  
  
            // First, find the line on which the property belongs.  
            // If line is found, replace it.  
            // Otherwise, insert the line at the beginning of the file.  
            if (src != null)  
            {  
                IVsTextColorState colorState = src.ColorState;  
                if (colorState != null)  
                {  
                    int         lineNumber = -1;  
                    string      line;  
                    TokenInfo[] lineInfo   = null;  
                    int         i;  
  
                    for (i = 0; i < maxLinesToSearch; i++)  
                    {  
                        line     = src.GetLine(i);  
                        lineInfo = src.GetColorizer().GetLineInfo(  
                                                        src.GetTextLines(),  
                                                        i,  
                                                        colorState);  
                        if (lineInfo == null)  
                        {  
                            continue;  
                        }  
                        if (lineInfo[0].Type != (TokenType)TestTokenTypes.DocPropertyLine)  
                        {  
                            // Not a property line  
                            continue;  
                        }  
                        TokenInfo valueInfo = new TokenInfo();  
                        int tokenIndex = -1;  
                        for (tokenIndex = 0;  
                             tokenIndex < lineInfo.Length;  
                             tokenIndex++)  
                        {  
                            if (lineInfo[tokenIndex].Type == (TokenType)TestTokenTypes.DocPropertyName)  
                            {  
                                break;  
                            }  
                        }  
                        if (tokenIndex >= lineInfo.Length)  
                        {  
                            // No property name on the line.  
                            continue;  
                        }  
                        string name = src.GetText(i,  
                                                  lineInfo[tokenIndex].StartIndex,  
                                                  i,  
                                                  lineInfo[tokenIndex].EndIndex + 1);  
                        if (name != null)  
                        {  
                            if (String.Compare(name, propertyName, true) == 0)  
                            {  
                                lineNumber = i;  
                                break;  
                            }  
                        }  
                    }  
  
                    // Set up an undo context that also handles the insert/replace.  
                    EditArray editArray = new EditArray(src,  
                                                        true,  
                                                        "Update Property");  
                    if (editArray != null)  
                    {  
                        TextSpan span = new TextSpan();  
                        if (lineNumber != -1)  
                        {  
                            // Replace line.  
                            int lineLength = 0;  
                            src.GetTextLines().GetLengthOfLine(lineNumber,  
                                                               out lineLength);  
                            span.iStartLine  = lineNumber;  
                            span.iStartIndex = 0;  
                            span.iEndLine    = lineNumber;  
                            span.iEndIndex   = lineLength;  
                        }  
                        else  
                        {  
                            // Insert new line.  
                            span.iStartLine  = 0;  
                            span.iStartIndex = 0;  
                            span.iEndLine    = 0;  
                            span.iEndIndex   = 0;  
                            newLine += "\n";  
                        }  
                        editArray.Add(new EditSpan(span, newLine));  
                        editArray.ApplyEdits();  
                    }  
                }  
            }  
        }  
    }  
}  
```  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Eski dil hizmeti özellikleri](../../extensibility/internals/legacy-language-service-features1.md)