---
title: Kod Parçacığı İşlevleri
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- code snippets [Visual Studio], functions
- snippets [Visual Studio], functions
- IntelliSense code snippets, functions
ms.assetid: c0a2bf21-8fa5-4457-9281-f599beb53e7d
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f3362bae41b540ee097e1109848680a11d37a272
ms.sourcegitcommit: 206e738fc45ff8ec4ddac2dd484e5be37192cfbd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/03/2018
ms.locfileid: "39512141"
---
# <a name="code-snippet-functions"></a>Kod parçacığı işlevleri

C# kod parçacıkları ile kullanılabilecek üç işlev vardır. İçinde belirtilen işlevi [işlevi](../ide/code-snippets-schema-reference.md#function-element) kod parçacığının öğesi. Kod parçacıkları oluşturma hakkında daha fazla bilgi için bkz. [kod parçacıkları](../ide/code-snippets.md).

## <a name="functions"></a>İşlevler

Aşağıdaki tablo ile kullanmak için kullanılabilir işlevler açıklar `Function` kod parçacıkları öğesinde.

|İşlev|Açıklama|Dil|
|--------------|-----------------|--------------|
|`GenerateSwitchCases(` `EnumerationLiteral` `)`|Tarafından belirtilen numaralandırma üyeleri için bir switch ifadesi ve bir dizi case deyimleri oluşturur `EnumerationLiteral` parametresi. `EnumerationLiteral` Parametresi bir numaralandırma sabit değeri başvurusu veya bir sabit listesi türü olmalıdır.|C#|
|`ClassName()`|Eklenen kod parçacığı içeren sınıf adını döndürür.|C#|
|`SimpleTypeName(` `TypeName` `)`|Azaltır *TypeName* en basit haliyle kod parçacığını çağrıldığı bağlam parametresi.|C#|

## <a name="example"></a>Örnek

Aşağıdaki örnek nasıl kullanılacağını gösterir `GenerateSwitchCases` işlevi. Ne zaman bu kod parçacığı eklenir ve bir numaralandırma girilir `$switch_on$` değişmez değeri `$cases$` değişmez değeri oluşturur bir `case` deyimi için listedeki her bir değer.

```xml
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

```xml
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
            <Code Language="csharp" Format="CData">
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

```xml
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

## <a name="see-also"></a>Ayrıca bkz.

- [Function öğesi](../ide/code-snippets-schema-reference.md#function-element)
- [Kod parçacıkları şema başvurusu](../ide/code-snippets-schema-reference.md)
