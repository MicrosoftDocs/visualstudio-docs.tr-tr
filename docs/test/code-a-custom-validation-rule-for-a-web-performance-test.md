---
title: Web performans testi için özel bir doğrulama kuralı kodlama
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- custom validation rules
- validation rules, creating
- web performance tests, creating custom validation rules
- rules, validation
- validation rules
ms.assetid: 989124bc-1a86-41f7-b37d-8f9e54dd4f0b
dev_langs:
- CSharp
- VB
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: 407c6e5b8beec118ce8f25edb35e66722990e8ca
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53047680"
---
# <a name="code-a-custom-validation-rule-for-a-web-performance-test"></a>Kodu bir web performans testi için özel doğrulama kuralı

Kendi doğrulama kuralları oluşturabilirsiniz. Bunu yapmak için kendi kural sınıfı bir doğrulama kuralı sınıfından türetilir. Doğrulama kuralları türetilen <xref:Microsoft.VisualStudio.TestTools.WebTesting.ValidationRule> temel sınıfı.

> [!NOTE]
> Özel ayıklama kuralları oluşturabilirsiniz. Daha fazla bilgi için [özel kod ve yük testleri için eklentiler oluşturma](../test/create-custom-code-and-plug-ins-for-load-tests.md).

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="to-create-custom-validation-rules"></a>Özel doğrulama kurallarını oluşturmak için

1.  Bir Test içeren bir web performans testi projesi açın.

2.  (İsteğe bağlı) Doğrulama kuralınızı depolanacağı ayrı bir sınıf kitaplığı projesi oluşturun.

    > [!IMPORTANT]
    > Sınıfı, testlerinizi bulunan aynı projede oluşturabilirsiniz. Ancak, kural yeniden kullanmak isterseniz, kural depolanacağı ayrı bir sınıf kitaplığı projesi oluşturun en iyisidir. Ayrı bir proje oluşturursanız, bu yordam isteğe bağlı adımları tamamlamanız gerekir.

3.  (İsteğe bağlı) Sınıf kitaplığı projesinde Microsoft.VisualStudio.QualityTools.WebTestFramework DLL'ye bir başvuru ekleyin.

4.  Türetilen bir sınıf oluşturmanız <xref:Microsoft.VisualStudio.TestTools.WebTesting.ValidationRule> sınıfı. Uygulama <xref:Microsoft.VisualStudio.TestTools.WebTesting.ValidationRule.Validate*> ve <xref:Microsoft.VisualStudio.TestTools.WebTesting.ValidationRule.RuleName*> üyeleri.

5.  (İsteğe bağlı) Yeni sınıf kitaplığı projesi oluşturun.

6.  (İsteğe bağlı) Test projesinde özel doğrulama kuralı içeren sınıf kitaplığı projesine bir başvuru ekleyin.

7.  Bir web performans testinde Test projesinde, açık **Web Performans Testi Düzenleyicisi**.

8.  Bir web performans testi isteği için özel doğrulama kuralı eklemek için bir istek ve select sağ **doğrulama kuralı Ekle**.

     **Doğrulama kuralı Ekle** iletişim kutusu görüntülenir. Özel doğrulama kuralınızı göreceğiniz **bir kural seçin** birlikte önceden tanımlanmış doğrulama kuralları listesi. Özel doğrulama kuralınızı seçin ve ardından **Tamam**.

9. Web performans testinizi çalıştırın.

## <a name="example"></a>Örnek

Aşağıdaki kod, özel doğrulama kuralı uygulanışı gösterilmektedir. Bu doğrulama kuralı önceden tanımlanmış etiketi gerekli doğrulama kuralı davranışını taklit eder. Bu örnekte, kendi özel doğrulama kuralları için bir başlangıç noktası olarak kullanın.

> [!WARNING]
> Özel Doğrulayıcı sağlayıcısı için kodunda genel özellikleri null değer olamaz.

```csharp
using System;
using System.Diagnostics;
using System.Globalization;
using Microsoft.VisualStudio.TestTools.WebTesting;

namespace SampleWebTestRules
{
    //-------------------------------------------------------------------------
    // This class creates a custom validation rule named "Custom Validate Tag"
    // The custom validation rule is used to check that an HTML tag with a
    // particular name is found one or more times in the HTML response.
    // The user of the rule can specify the HTML tag to look for, and the
    // number of times that it must appear in the response.
    //-------------------------------------------------------------------------
    public class CustomValidateTag : ValidationRule
    {
        /// Specify a name for use in the user interface.
        /// The user sees this name in the Add Validation dialog box.
        //---------------------------------------------------------------------
        public override string RuleName
        {
            get { return "Custom Validate Tag"; }
        }

        /// Specify a description for use in the user interface.
        /// The user sees this description in the Add Validation dialog box.
        //---------------------------------------------------------------------
        public override string RuleDescription
        {
            get { return "Validates that the specified tag exists on the page."; }
        }

        // The name of the required tag
        private string RequiredTagNameValue;
        public string RequiredTagName
        {
            get { return RequiredTagNameValue; }
            set { RequiredTagNameValue = value; }
        }

        // The minimum number of times the tag must appear in the response
        private int MinOccurrencesValue;
        public int MinOccurrences
        {
            get { return MinOccurrencesValue; }
            set { MinOccurrencesValue = value; }
        }

        // Validate is called with the test case Context and the request context.
        // These allow the rule to examine both the request and the response.
        //---------------------------------------------------------------------
        public override void Validate(object sender, ValidationEventArgs e)
        {
            bool validated = false;
            int numTagsFound = 0;

            foreach (HtmlTag tag in e.Response.HtmlDocument.GetFilteredHtmlTags(RequiredTagName))
            {
                Debug.Assert(string.Equals(tag.Name, RequiredTagName, StringComparison.InvariantCultureIgnoreCase));

                if (++numTagsFound >= MinOccurrences)
                {
                    validated = true;
                    break;
                }
            }

            e.IsValid = validated;

            // If the validation fails, set the error text that the user sees
            if (!validated)
            {
                if (numTagsFound > 0)
                {
                    e.Message = String.Format("Only found {0} occurrences of the tag", numTagsFound);
                }
                else
                {
                    e.Message = String.Format("Did not find any occurrences of tag '{0}'", RequiredTagName);
                }
            }
        }
    }
}
```

```vb
Imports System
Imports System.Diagnostics
Imports System.Globalization
Imports Microsoft.VisualStudio.TestTools.WebTesting

Namespace SampleWebTestRules

    '-------------------------------------------------------------------------
    ' This class creates a custom validation rule named "Custom Validate Tag"
    ' The custom validation rule is used to check that an HTML tag with a
    ' particular name is found one or more times in the HTML response.
    ' The user of the rule can specify the HTML tag to look for, and the
    ' number of times that it must appear in the response.
    '-------------------------------------------------------------------------
    Public Class CustomValidateTag
        Inherits Microsoft.VisualStudio.TestTools.WebTesting.ValidationRule

        ' Specify a name for use in the user interface.
        ' The user sees this name in the Add Validation dialog box.
        '---------------------------------------------------------------------
        Public Overrides ReadOnly Property RuleName() As String
            Get
                Return "Custom Validate Tag"
            End Get
        End Property

        ' Specify a description for use in the user interface.
        ' The user sees this description in the Add Validation dialog box.
        '---------------------------------------------------------------------
        Public Overrides ReadOnly Property RuleDescription() As String
            Get
                Return "Validates that the specified tag exists on the page."
            End Get
        End Property

        ' The name of the required tag
        Private RequiredTagNameValue As String
        Public Property RequiredTagName() As String
            Get
                Return RequiredTagNameValue
            End Get
            Set(ByVal value As String)
                RequiredTagNameValue = value
            End Set
        End Property

        ' The minimum number of times the tag must appear in the response
        Private MinOccurrencesValue As Integer
        Public Property MinOccurrences() As Integer
            Get
                Return MinOccurrencesValue
            End Get
            Set(ByVal value As Integer)
                MinOccurrencesValue = value
            End Set
        End Property

        ' Validate is called with the test case Context and the request context.
        ' These allow the rule to examine both the request and the response.
        '---------------------------------------------------------------------
        Public Overrides Sub Validate(ByVal sender As Object, ByVal e As ValidationEventArgs)

            Dim validated As Boolean = False
            Dim numTagsFound As Integer = 0

            For Each tag As HtmlTag In e.Response.HtmlDocument.GetFilteredHtmlTags(RequiredTagName)

                Debug.Assert(String.Equals(tag.Name, RequiredTagName, StringComparison.InvariantCultureIgnoreCase))

                numTagsFound += 1
                If numTagsFound >= MinOccurrences Then

                    validated = True
                    Exit For
                End If
            Next

            e.IsValid = validated

            ' If the validation fails, set the error text that the user sees
            If Not (validated) Then
                If numTagsFound > 0 Then
                    e.Message = String.Format("Only found {0} occurrences of the tag", numTagsFound)
                Else
                    e.Message = String.Format("Did not find any occurrences of tag '{0}'", RequiredTagName)
                End If
            End If
        End Sub
    End Class
End Namespace
```

## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualStudio.TestTools.WebTesting.ValidationRule>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting.Rules>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting.Rules.ValidateFormField>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting.Rules.ValidationRuleFindText>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting.Rules.ValidationRuleRequestTime>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting.Rules.ValidationRuleRequiredAttributeValue>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting.Rules.ValidationRuleRequiredTag>
- [Web performans testi için özel bir ayıklama kuralı kodlama](../test/code-a-custom-extraction-rule-for-a-web-performance-test.md)