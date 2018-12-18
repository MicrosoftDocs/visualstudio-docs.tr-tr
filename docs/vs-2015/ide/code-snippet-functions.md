---
title: Kod parçacığı işlevleri | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- code snippets [Visual Studio], functions
- snippets [Visual Studio], functions
- IntelliSense code snippets, functions
ms.assetid: c0a2bf21-8fa5-4457-9281-f599beb53e7d
caps.latest.revision: 15
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 3874b162719deb02813ceb7eae09b373e208f458
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49270887"
---
# <a name="code-snippet-functions"></a>Kod Parçacığı İşlevleri
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

İle kullanılabilecek üç işlev vardır [!INCLUDE[csprcs](../includes/csprcs-md.md)] kod parçacıkları. İçinde belirtilen işlevi [işlevi](http://msdn.microsoft.com/en-us/572c5549-5821-4e15-8ecd-0fa86c1c65df) kod parçacığının öğesi. Kod parçacıkları oluşturma hakkında daha fazla bilgi için bkz. [kod parçacıkları](../ide/code-snippets.md).  
  
## <a name="functions"></a>İşlevler  
 Aşağıdaki tablo ile kullanmak için kullanılabilir işlevler açıklar `Function` kod parçacıkları öğesinde.  
  
|İşlev|Açıklama|Dil|  
|--------------|-----------------|--------------|  
|`GenerateSwitchCases(` `EnumerationLiteral` `)`|Tarafından belirtilen numaralandırma üyeleri için bir switch ifadesi ve bir dizi case deyimleri oluşturur `EnumerationLiteral` parametresi. `EnumerationLiteral` Parametresi bir numaralandırma sabit değeri başvurusu veya bir sabit listesi türü olmalıdır.|[!INCLUDE[csprcs](../includes/csprcs-md.md)]|  
|`ClassName()`|Eklenen kod parçacığı içeren sınıf adını döndürür.|[!INCLUDE[csprcs](../includes/csprcs-md.md)]|  
|`SimpleTypeName(` `TypeName` `)`|Azaltır *TypeName* en basit haliyle kod parçacığını çağrıldığı bağlam parametresi.|[!INCLUDE[csprcs](../includes/csprcs-md.md)]|  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek nasıl kullanılacağını gösterir `GenerateSwitchCases` işlevi. Ne zaman bu kod parçacığı eklenir ve bir numaralandırma girilir `$switch_on$` değişmez değeri `$cases$` değişmez değeri oluşturur bir `case` deyimi için listedeki her bir değer.  
  
```  
<CodeSnippets xmlns="http://schemas.microsoft.com/VisualStudio/2005/CodeSnippet">  
    <CodeSnippet Format="1.0.0">  
        <Header>  
            <Title>switch</Title>   
            <Shortcut>switch</Shortcut>   
            <Description>Code snippet for switch statement</Description>   
            <Author>Microsoft Corporation</Author>   
            <SnippetTypes>  
                <SnippetType>Expansion</SnippetType>   
            </SnippetTypes>  
        </Header>  
        <Snippet>  
            <Declarations>  
                <Literal>  
                    <ID>expression</ID>   
                    <ToolTip>Expression to switch on</ToolTip>   
                    <Default>switch_on</Default>   
                </Literal>  
                <Literal Editable="false">  
                    <ID>cases</ID>   
                    <Function>GenerateSwitchCases($expression$)</Function>   
                    <Default>default:</Default>   
                </Literal>  
            </Declarations>  
            <Code Language="csharp">  
                <![CDATA[  
                    switch ($expression$)  
                    {  
                        $cases$  
                    }  
                ]]>  
            </Code>  
        </Snippet>  
    </CodeSnippet>  
</CodeSnippets>  
```  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek nasıl kullanılacağını gösterir `ClassName` işlevi. Bu kod parçacığı eklendiğinde `$classname$` değişmez değeri, kod dosyanın bu konumda kapsayan sınıfın adı ile değiştirilir.  
  
```  
<CodeSnippets xmlns="http://schemas.microsoft.com/VisualStudio/2005/CodeSnippet">  
    <CodeSnippet Format="1.0.0">  
        <Header>  
            <Title>Common constructor pattern</Title>   
            <Shortcut>ctor</Shortcut>   
            <Description>Code Snippet for a constructor</Description>  
            <Author>Microsoft Corporation</Author>   
            <SnippetTypes>  
                <SnippetType>Expansion</SnippetType>  
            </SnippetTypes>  
        </Header>  
        <Snippet>  
            <Declarations>  
                <Literal>  
                    <ID>type</ID>   
                    <Default>int</Default>   
                </Literal>  
                <Literal>  
                    <ID>name</ID>   
                    <Default>field</Default>   
                </Literal>  
                <Literal default="true" Editable="false">  
                    <ID>classname</ID>   
                    <ToolTip>Class name</ToolTip>   
                    <Function>ClassName()</Function>   
                    <Default>ClassNamePlaceholder</Default>   
                </Literal>  
            </Declarations>  
            <Code Language="vjsharp" Format="CData">  
                <![CDATA[   
                    public $classname$ ($type$ $name$)  
                    {  
                        this._$name$ = $name$;  
                    }  
                    private $type$ _$name$;  
                ]]>  
            </Code>  
        </Snippet>  
    </CodeSnippet>  
</CodeSnippets>  
```  
  
## <a name="example"></a>Örnek  
 Bu örnek nasıl kullanılacağını gösterir `SimpleTypeName` işlevi. Bu kod parçacığı bir kod dosyası yerleştirildiğinde `$SystemConsole$` değişmez değeri, en basit biçimi ile değiştirilecek <xref:System.Console> kod parçacığını çağrıldığı bağlamda türü.  
  
```  
<CodeSnippets xmlns="http://schemas.microsoft.com/VisualStudio/2005/CodeSnippet">  
    <CodeSnippet Format="1.0.0">  
        <Header>  
            <Title>Console_WriteLine</Title>   
            <Shortcut>cw</Shortcut>   
            <Description>Code snippet for Console.WriteLine</Description>   
            <Author>Microsoft Corporation</Author>   
            <SnippetTypes>  
                <SnippetType>Expansion</SnippetType>   
            </SnippetTypes>  
        </Header>  
        <Snippet>  
            <Declarations>  
                <Literal Editable="false">  
                    <ID>SystemConsole</ID>   
                    <Function>SimpleTypeName(global::System.Console)</Function>   
                </Literal>  
            </Declarations>  
            <Code Language="csharp">  
                <![CDATA[   
                    $SystemConsole$.WriteLine();  
                ]]>  
            </Code>  
        </Snippet>  
    </CodeSnippet>  
</CodeSnippets>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Function öğesi (IntelliSense kod parçacıkları)](http://msdn.microsoft.com/en-us/572c5549-5821-4e15-8ecd-0fa86c1c65df)   
 [Kod Parçacıkları Şema Başvurusu](../ide/code-snippets-schema-reference.md)



