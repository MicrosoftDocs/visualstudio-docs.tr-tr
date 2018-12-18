---
title: Web performans testi için özel bir ayıklama kuralı kodlama
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- extraction rules
- Web performance tests, creating custom extraction rules
- extraction rules, creating custom
ms.assetid: 6bcc5712-6cc6-4f59-8933-6e8078318c45
dev_langs:
- CSharp
- VB
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: 41e9a025db4ec9c8425e0de6ba4ecad25f775d50
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53066684"
---
# <a name="code-a-custom-extraction-rule-for-a-web-performance-test"></a>Kodu bir web performans testi için özel bir ayıklama kuralı

Kendi ayıklama kuralları oluşturabilirsiniz. Bunu yapmak için kendi kurallarınızı bir ayıklama kuralı sınıfından türetilir. Ayıklama kuralları türetilen <xref:Microsoft.VisualStudio.TestTools.WebTesting.ExtractionRule> temel sınıfı.

> [!NOTE]
> Ayrıca özel doğrulama kuralları oluşturabilirsiniz. Daha fazla bilgi için [özel kod ve yük testleri için eklentiler oluşturma](../test/create-custom-code-and-plug-ins-for-load-tests.md).

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="to-create-a-custom-extraction-rule"></a>Özel bir ayıklama kuralı oluşturmak için

1.  Bir web performans testi içeren bir Test projesi açın.

2.  (İsteğe bağlı) Ayıklama kuralı depolanacağı ayrı bir sınıf kitaplığı projesi oluşturun.

    > [!IMPORTANT]
    > Sınıfı, testlerinizi bulunan aynı projede oluşturabilirsiniz. Ancak, kural yeniden kullanmak isterseniz, kural depolanacağı ayrı bir sınıf kitaplığı projesi oluşturun en iyisidir. Ayrı bir proje oluşturursanız, bu yordam isteğe bağlı adımları tamamlamanız gerekir.

3.  (İsteğe bağlı) Sınıf kitaplığı projesinde Microsoft.VisualStudio.QualityTools.WebTestFramework DLL'ye bir başvuru ekleyin.

4.  Türetilen bir sınıf oluşturmanız <xref:Microsoft.VisualStudio.TestTools.WebTesting.ExtractionRule> sınıfı. Uygulama <xref:Microsoft.VisualStudio.TestTools.WebTesting.ExtractionRule.Extract*> ve <xref:Microsoft.VisualStudio.TestTools.WebTesting.ExtractionRule.RuleName*> üyeleri.

5.  (İsteğe bağlı) Yeni sınıf kitaplığı projesi oluşturun.

6.  (İsteğe bağlı) Test projesinde özel bir ayıklama kuralı içeren sınıf kitaplığı projesine bir başvuru ekleyin.

7.  Bir web performans testinde Test projesinde açık **Web Performans Testi Düzenleyicisi**.

8.  Özel ayıklama kuralı eklemek için bir web performans testi isteği seçin sağ tıklayın ve **Ayıklama Kuralı Ekle**.

     **Ayıklama Kuralı Ekle** iletişim kutusu görüntülenir. Özel doğrulama kuralınızı göreceğiniz **bir kural seçin** birlikte önceden tanımlanmış doğrulama kuralları listesi. Özel ayıklama kuralınızı seçin ve sonra **Tamam**.

9. Web performans testinizi çalıştırın.

## <a name="example"></a>Örnek

Aşağıdaki kod, özel bir ayıklama kuralı uygulanışı gösterilmektedir. Bu ayıklama kuralı, belirtilen bir giriş alan değeri ayıklar. Bu örnekte, kendi özel ayıklama kuralları için bir başlangıç noktası olarak kullanın.

```csharp
using System;
using System.Collections.Generic;
using Microsoft.VisualStudio.TestTools.WebTesting;
using System.Globalization;

namespace ClassLibrary2
{
    //-------------------------------------------------------------------------
    // This class creates a custom extraction rule named "Custom Extract Input"
    // The user of the rule specifies the name of an input field, and the
    // rule attempts to extract the value of that input field.
    //-------------------------------------------------------------------------
    public class CustomExtractInput : ExtractionRule
    {
        /// Specify a name for use in the user interface.
        /// The user sees this name in the Add Extraction dialog box.
        //---------------------------------------------------------------------
        public override string RuleName
        {
            get { return "Custom Extract Input"; }
        }

        /// Specify a description for use in the user interface.
        /// The user sees this description in the Add Extraction dialog box.
        //---------------------------------------------------------------------
        public override string RuleDescription
        {
            get { return "Extracts the value from a specified input field"; }
        }

        // The name of the desired input field
        private string NameValue;
        public string Name
        {
            get { return NameValue; }
            set { NameValue = value; }
        }

        // The Extract method.  The parameter e contains the web performance test context.
        //---------------------------------------------------------------------
        public override void Extract(object sender, ExtractionEventArgs e)
        {
            if (e.Response.HtmlDocument != null)
            {
                foreach (HtmlTag tag in e.Response.HtmlDocument.GetFilteredHtmlTags(new string[] { "input" }))
                {
                    if (String.Equals(tag.GetAttributeValueAsString("name"), Name, StringComparison.InvariantCultureIgnoreCase))
                    {
                        string formFieldValue = tag.GetAttributeValueAsString("value");
                        if (formFieldValue == null)
                        {
                            formFieldValue = String.Empty;
                        }

                        // add the extracted value to the web performance test context
                        e.WebTest.Context.Add(this.ContextParameterName, formFieldValue);
                        e.Success = true;
                        return;
                    }
                }
            }
            // If the extraction fails, set the error text that the user sees
            e.Success = false;
            e.Message = String.Format(CultureInfo.CurrentCulture, "Not Found: {0}", Name);
        }
    }
}
```

```vb
Imports System
Imports System.Collections.Generic
Imports Microsoft.VisualStudio.TestTools.WebTesting
Imports System.Globalization

Namespace ClassLibrary2

    '-------------------------------------------------------------------------
    ' This class creates a custom extraction rule named "Custom Extract Input"
    ' The user of the rule specifies the name of an input field, and the
    ' rule attempts to extract the value of that input field.
    '-------------------------------------------------------------------------
    Public Class CustomExtractInput
        Inherits ExtractionRule

        ' Specify a name for use in the user interface.
        ' The user sees this name in the Add Extraction dialog box.
        '---------------------------------------------------------------------
        Public Overrides ReadOnly Property RuleName() As String
            Get
                Return "Custom Extract Input"
            End Get
        End Property

        ' Specify a description for use in the user interface.
        ' The user sees this description in the Add Extraction dialog box.
        '---------------------------------------------------------------------
        Public Overrides ReadOnly Property RuleDescription() As String
            Get
                Return "Extracts the value from a specified input field"
            End Get
        End Property

        ' The name of the desired input field
        Private NameValue As String
        Public Property Name() As String
            Get
                Return NameValue
            End Get
            Set(ByVal value As String)
                NameValue = value
            End Set
        End Property

        ' The Extract method.  The parameter e contains the web performance test context.
        '---------------------------------------------------------------------
        Public Overrides Sub Extract(ByVal sender As Object, ByVal e As ExtractionEventArgs)

            If Not e.Response.HtmlDocument Is Nothing Then

                For Each tag As HtmlTag In e.Response.HtmlDocument.GetFilteredHtmlTags(New String() {"input"})

                    If String.Equals(tag.GetAttributeValueAsString("name"), Name, StringComparison.InvariantCultureIgnoreCase) Then

                        Dim formFieldValue As String = tag.GetAttributeValueAsString("value")
                        If formFieldValue Is Nothing Then

                            formFieldValue = String.Empty
                        End If

                        ' add the extracted value to the web performance test context
                        e.WebTest.Context.Add(Me.ContextParameterName, formFieldValue)
                        e.Success = True
                        Return
                    End If
                Next
            End If
            ' If the extraction fails, set the error text that the user sees
            e.Success = False
            e.Message = String.Format(CultureInfo.CurrentCulture, "Not Found: {0}", Name)
        End Sub
    End Class
End Namespace
```

<xref:Microsoft.VisualStudio.TestTools.WebTesting.ExtractionRule.Extract*> Yöntemi ayıklama kuralı temel işlevlerini içerir. <xref:Microsoft.VisualStudio.TestTools.WebTesting.ExtractionRule.Extract*> Önceki örnekte yöntemi alır bir <xref:Microsoft.VisualStudio.TestTools.WebTesting.ExtractionEventArgs> bu ayıklama kuralı kapsar istek tarafından oluşturulan yanıt sağlar. Yanıt içeren bir <xref:Microsoft.VisualStudio.TestTools.WebTesting.HtmlDocument> yanıtındaki tüm etiketleri içerir. Giriş etiketleri filtrelenerek <xref:Microsoft.VisualStudio.TestTools.WebTesting.HtmlDocument>. Her bir girdi etiketi olarak adlandırılan bir öznitelik için incelenir `name` değerini sağlanan kullanıcı değeri eşittir `Name` özelliği. Bu eşleşen özniteliğine sahip bir etiket bulunursa, bir tarafından bulunan bir değeri ayıklamak için girişimde `value` öznitelik değeri öznitelik zaten varsa. Varsa, ad ve değer etiketinin ayıklanır ve web performans testi bağlamına eklendi. Ayıklama kuralı geçirir.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualStudio.TestTools.WebTesting.ExtractionRule>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting.Rules>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting.Rules.ExtractAttributeValue>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting.Rules.ExtractFormField>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting.Rules.ExtractHttpHeader>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting.Rules.ExtractRegularExpression>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting.Rules.ExtractText>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting.Rules.ExtractHiddenFields>
- [Web performans testi için özel doğrulama kuralı kodlama](../test/code-a-custom-validation-rule-for-a-web-performance-test.md)