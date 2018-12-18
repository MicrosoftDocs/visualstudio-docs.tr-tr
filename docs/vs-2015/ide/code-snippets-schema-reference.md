---
title: Kod parçacıkları şema başvurusu | Microsoft Docs
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
- schema reference [Visual Studio]
- snippets [Visual Studio], schema reference
- code snippets [Visual Studio], schema reference
- IntelliSense Code Snippets, XML Schema
ms.assetid: 58a60621-725f-4763-93b7-62ea5424ef88
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 19a14972d36bcb7070e0604b47caab55f41d0126
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49188147"
---
# <a name="code-snippets-schema-reference"></a>Kod Parçacıkları Şema Başvurusu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

IntelliSense kod parçacıkları, ile uygulamanıza eklenmeye hazır önceden yazılmış kod parçalarıdır [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Yinelenen kodları yazmak veya örnekleri aramak için harcanan süreyi kısaltan kod parçacıkları sağlayarak üretkenliği artırabilirsiniz. Kendi kod parçacıklarınızı oluşturmak ve bunları Kod parçacıklarına eklemek için IntelliSense kod parçacığı XML şemasını kullanabilirsiniz, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] zaten içerir.  
  
## <a name="intellisense-code-snippets-schema-elements"></a>IntelliSense Kod Parçacıkları Şeması Öğeleri  
  
||||  
|-|-|-|  
|[Assembly öğesi](../ide/code-snippets-schema-reference.md#assembly)|[HelpUrl öğesi](../ide/code-snippets-schema-reference.md#helpurl)|[References öğesi](../ide/code-snippets-schema-reference.md#references)|  
|[Author öğesi](../ide/code-snippets-schema-reference.md#author)|[ID öğesi](../ide/code-snippets-schema-reference.md#id)|[Shortcut öğesi](../ide/code-snippets-schema-reference.md#shortcut)|  
|[Kod öğesi](../ide/code-snippets-schema-reference.md#code)|[İçeri aktarma öğesi](../ide/code-snippets-schema-reference.md#import)|[Snippet öğesi](../ide/code-snippets-schema-reference.md#snippet)|  
|[CodeSnippet öğesi](../ide/code-snippets-schema-reference.md#codesnippet)|[Imports öğesi](../ide/code-snippets-schema-reference.md#imports)|[SnippetType öğesi](../ide/code-snippets-schema-reference.md#snippettype)|  
|[CodeSnippets öğesi](../ide/code-snippets-schema-reference.md#codesnippets)|[Keyword öğesi](../ide/code-snippets-schema-reference.md#keyword)|[SnippetTypes öğesi](../ide/code-snippets-schema-reference.md#snippettypes)|  
|[Declarations öğesi](../ide/code-snippets-schema-reference.md#declarations)|[Keywords öğesi](../ide/code-snippets-schema-reference.md#keywords)|[Title öğesi](../ide/code-snippets-schema-reference.md#title)|  
|[Default öğesi](../ide/code-snippets-schema-reference.md#default)|[Literal öğesi](../ide/code-snippets-schema-reference.md#literal)|[ToolTip öğesi](../ide/code-snippets-schema-reference.md#tooltip)|  
|[Description öğesi](../ide/code-snippets-schema-reference.md#description)|[Namespace öğesi](../ide/code-snippets-schema-reference.md#namespace)|[Type öğesi](../ide/code-snippets-schema-reference.md#type)|  
|[Function öğesi](../ide/code-snippets-schema-reference.md#function)|[Object öğesi](../ide/code-snippets-schema-reference.md#object)|[URL öğesi](../ide/code-snippets-schema-reference.md#url)|  
|[Header öğesi](../ide/code-snippets-schema-reference.md#header)|[Reference öğesi](../ide/code-snippets-schema-reference.md#reference)||  
  
##  <a name="assembly"></a> Assembly öğesi  
 Kod parçacığının başvurduğu derlemenin adını belirtir.  
  
> [!NOTE]
>  `Assembly` Öğesi yalnızca Visual Basic kod parçacıkları tarafından desteklenir.  
  
 Metin değeri **derleme** öğedir derlemenin kolay adı gibi `System.dll`, ya da tanımlayıcı gibi ad `System,Version=1.0.0.1,Culture=neutral,PublicKeyToken=9b35aa323c18d4fb1`.  
  
```xml  
<Assembly>  
    AssemblyName  
</Assembly>  
```  
  
|Üst Öğe|Açıklama|  
|--------------------|-----------------|  
|[Reference öğesi](../ide/code-snippets-schema-reference.md#reference)|Kod parçacığının gerek duyduğu derleme başvuruları hakkındaki bilgileri içerir.|  
  
 Bir metin değeri gereklidir. Bu metin, kod parçacığının başvurduğu derlemeyi belirtir.  
  
##  <a name="author"></a> Author öğesi  
 Kod parçacığı yazarının adını belirtir. **Kod parçacıkları Yöneticisi** öğesinde depolanan adı görüntüler `Author` kod parçacığının öğesi.  
  
```xml  
<Author>  
   Code Snippet Author  
</Author>  
  
```  
  
|Üst Öğe|Açıklama|  
|--------------------|-----------------|  
|[Header öğesi](../ide/code-snippets-schema-reference.md#header)|Kod parçacığı hakkında genel bilgiler içerir.|  
  
 Bir metin değeri gereklidir. Bu metin kod parçacığının yazarını belirtir.  
  
##  <a name="code"></a> Kod öğesi  
 Kısa kod blokları için bir kapsayıcı sağlar.  
  
 Metninde kullanılabilecek iki ayrılmış sözcük `Code` öğesi: `$end$` ve `$selected$`. `$end$` kod parçacığı eklendikten sonra imlecin yerleştirileceği konumu işaretler. `$selected$` çağrıldığında kod parçacığına eklenecek olan belgedeki seçili metni temsil eder. Örneğin, içeren bir kod parçacığı verilen:  
  
```xml  
$selected$ is a great color.  
```  
  
 Kullanıcı şablonu çağırdığında "Mavi" sözcüğü seçtiyseniz oluşur:  
  
```xml  
Blue is a great color.  
```  
  
 Ya da kullanamazsınız `$end$` veya `$selected$` birden fazla kez bir kod parçacığında. Bunu yaparsanız, yalnızca ikinci örneğini tanınır. İçeren bir kod parçacığı verilen:  
  
```  
$selected$ is a great color. I love $selected$.  
```  
  
 "Mavi" sözcüğü seçtiyseniz oluşur:  
  
```  
is a great color. I love Blue.  
```  
  
 Arasında boşluk olmadığından ilk alanı görünür `$selected$` ve `is`.  
  
 Diğer tüm `$` anahtar sözcükleri tanımlanmış dinamik olarak `<Literal>` ve `<Object>` etiketler.  
  
```xml  
<Code Language="Language"  
    Kind="method body/method decl/type decl/page/file/any"  
    Delimiter="Delimiter">  
    Code to insert  
</Code>  
```  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`Delimiter`|İsteğe bağlı öznitelik. Kod içindeki değişmez değerleri ve nesneleri açıklamak için kullanılan sınırlayıcıyı belirtir. Varsayılan olarak sınırlayıcı olduğu `$`.|  
|`Kind`|İsteğe bağlı öznitelik. Kod parçacığının içerdiği kod türünü ve kod parçacığının derlenmesi için bir kod parçacığının araya eklenmesi gereken konumu belirtir. Kullanılabilir değerler `method body`, `method decl`, `type decl`, `file`, ve `any`.|  
|`Language`|Gerekli öznitelik. Kod parçacığının dilini belirtir.|  
  
|Tür Öznitelik Değeri|Açıklama|  
|--------------------------|-----------------|  
|`method body`|Kod parçacığının bir yöntem gövdesi olduğunu ve bu nedenle, bir yöntem bildiriminin içine eklenmesi gerektiğini belirtir.|  
|`method decl`|Kod parçacığının bir yöntem olduğunu ve bu nedenle, bir sınıf veya modül içine eklenmesi gerektiğini belirtir.|  
|`type decl`|Kod parçacığının bir tür olduğunu ve bu nedenle, bir sınıf, modül veya ad alanı içine eklenmesi gerektiğini belirtir.|  
|`file`|Kod parçacığının eksiksiz bir kod dosyası olduğunu belirtir. Bu kod parçacıkları tek başına bir kod dosyasının içine veya bir ad alanının içine eklenebilir.|  
|`any`|Kod parçacığının istenen yere eklenebileceğini belirtir. Bu etiket, açıklamalar gibi içeriğe bağımlı kod parçacıkları için kullanılır.|  
  
|Dil Özniteliği Değeri|Açıklama|  
|------------------------------|-----------------|  
|`VB`|Bir Visual Basic kod parçacığını tanımlar.|  
|`CSharp`|Bir C# kod parçacığını tanımlar.|  
|`CPP`|Bir C++ kod parçacığını tanımlar.|  
|`XML`|Bir XML kod parçacığını tanımlar.|  
|`JavaScript`|Bir JavaScript kod parçacığını tanımlar.|  
|`SQL`|Bir SQL kod parçacığını tanımlar.|  
|`HTML`|Bir HTML kod parçacığını tanımlar.|  
  
|Üst Öğe|Açıklama|  
|--------------------|-----------------|  
|[Snippet öğesi](../ide/code-snippets-schema-reference.md#snippet)|Kod parçacığı için başvuruları, içeri aktarımları, bildirimleri ve kodu içerir.|  
  
 Bir metin değeri gereklidir. Bu metin, bu kod parçacığı bir projeye eklendiğinde kullanabileceğiniz değişmez değerler ve nesnelerle birlikte kodu belirtir.  
  
##  <a name="codesnippet"></a> CodeSnippet öğesi  
 Visual Studio kod dosyalarına ekleyebileceğiniz bir başlık ve birden fazla IntelliSense Kod Parçacığı belirtmenizi sağlar.  
  
```xml  
<CodeSnippet Format="x.x.x">  
    <Header>... </Header>  
    <Snippet>... </Snippet>  
</CodeSnippet>  
  
```  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`Format`|Gerekli öznitelik. Kod parçacığının şema sürümünü belirtir. Format özniteliği, her "x"in sürüm numarasına ait sayısal bir değeri temsil ettiği x.x.x sözdiziminde bir dize olmalıdır. Visual Studio ile kod parçacıkları yoksayar `Format` anlamadığı öznitelikleri.|  
  
|Alt Öğe|Açıklama|  
|-------------------|-----------------|  
|[Header öğesi](../ide/code-snippets-schema-reference.md#header)|Gerekli öğe. Kod parçacığı hakkında genel bilgiler içerir. Olmalıdır tam olarak bir `Header` öğesinde bir kod parçacığı.|  
|[Snippet öğesi](../ide/code-snippets-schema-reference.md#snippet)|Gerekli öğe. Visual Studio tarafından eklenecek kodu içerir. Olmalıdır tam olarak bir `Snippet` öğesinde bir kod parçacığı.|  
  
|Üst Öğe|Açıklama|  
|--------------------|-----------------|  
|[CodeSnippets öğesi](../ide/code-snippets-schema-reference.md#codesnippets)|Kod parçacığı XML şemasının kök öğesi.|  
  
##  <a name="codesnippets"></a> CodeSnippets öğesi  
 Grupları [CodeSnippet öğesi](../ide/code-snippets-schema-reference.md#codesnippet)öğeleri. `CodeSnippets` Öğesi kod parçacığı XML şemasının kök öğesidir.  
  
```xml  
<CodeSnippets>  
    <CodeSnippet>... </CodeSnippet>  
</CodeSnippets>  
  
```  
  
|Alt Öğe|Açıklama|  
|-------------------|-----------------|  
|[CodeSnippet öğesi](../ide/code-snippets-schema-reference.md#codesnippet)|İsteğe bağlı öğe. Tüm kod parçacığı verisi için üst öğe. Sıfır veya daha fazla olabilir `CodeSnippet` öğelerinde bir `CodeSnippets` öğesi.|  
  
##  <a name="declarations"></a> Declarations öğesi  
 Bir kod parçacığının düzenleyebileceğiniz bölümlerini oluşturan değişmez değerleri ve nesneleri belirtir.  
  
```xml  
<Declarations>  
    <Literal>... </Literal>  
    <Object>... </Object>  
</Declarations>  
  
```  
  
|Alt Öğe|Açıklama|  
|-------------------|-----------------|  
|[Literal öğesi](../ide/code-snippets-schema-reference.md#literal)|İsteğe bağlı öğe. Kod parçacığının düzenleme yapabileceğiniz değişmez değerlerini tanımlar. Sıfır veya daha fazla olabilir `Literal` öğelerinde bir `Declarations` öğesi.|  
|[Object öğesi](../ide/code-snippets-schema-reference.md#object)|İsteğe bağlı öğe. Kod parçacığının düzenleme yapabileceğiniz nesnelerini tanımlar. Sıfır veya daha fazla olabilir `Object` öğelerinde bir `Declarations` öğesi.|  
  
|Üst Öğe|Açıklama|  
|--------------------|-----------------|  
|[Snippet öğesi](../ide/code-snippets-schema-reference.md#snippet)|Kod parçacığı için başvuruları, içeri aktarımları, bildirimleri ve kodu içerir.|  
  
##  <a name="default"></a> Default öğesi  
 Bir IntelliSense Kod Parçacığı için değişmez değerin veya nesnenin varsayılan değerini belirtir.  
  
```xml  
<Default>  
    Default value  
</Default>  
  
```  
  
|Üst Öğe|Açıklama|  
|--------------------|-----------------|  
|[Literal öğesi](../ide/code-snippets-schema-reference.md#literal)|Kod parçacığının düzenleme yapabileceğiniz değişmez değer alanlarını tanımlar.|  
|[Object öğesi](../ide/code-snippets-schema-reference.md#object)|Kod parçacığının düzenleme yapabileceğiniz nesne alanlarını tanımlar.|  
  
 Bir metin değeri gereklidir. Bu metin, düzenleyebileceğiniz kod parçacığı alanlarını dolduran değişmez değerin veya nesnenin varsayılan değerini belirtir.  
  
##  <a name="description"></a> Description öğesi  
 Bir IntelliSense Kod Parçacığı'nın içeriği hakkında açıklayıcı bilgileri belirtir.  
  
```xml  
<Description>  
    Code Snippet Description  
</Description>  
```  
  
|Üst Öğe|Açıklama|  
|--------------------|-----------------|  
|[Header öğesi](../ide/code-snippets-schema-reference.md#header)|Kod parçacığı hakkında genel bilgiler içerir.|  
  
 Bir metin değeri gereklidir. Bu metin kod parçacığını tanımlar.  
  
##  <a name="function"></a> Function öğesi  
 Değişmez değer veya nesne Visual Studio'da odağa geldiğinde yürütülecek bir işlevi belirtir.  
  
> [!NOTE]
>  `Function` Öğesi yalnızca Visual C# kod parçacıkları desteklenir.  
  
```xml  
<Function>  
    FunctionName  
</Function>  
```  
  
|Üst Öğe|Açıklama|  
|--------------------|-----------------|  
|[Literal öğesi](../ide/code-snippets-schema-reference.md#literal)|Kod parçacığının düzenleme yapabileceğiniz değişmez değer alanlarını tanımlar.|  
|[Object öğesi](../ide/code-snippets-schema-reference.md#object)|Kod parçacığının düzenleme yapabileceğiniz nesne alanlarını tanımlar.|  
  
 Bir metin değeri gereklidir. Bu metin, değişmez değer veya nesne alanı Visual Studio'da odağa geldiğinde yürütülecek bir işlevi belirtir.  
  
##  <a name="header"></a> Header öğesi  
 IntelliSense Kod Parçacığı hakkında genel bilgileri belirtir.  
  
```xml  
<Header>  
    <Title>... </Title>  
    <Author>... </Author>  
    <Description>... </Description>  
    <HelpUrl>... </HelpUrl>  
    <SnippetTypes>... </SnippetTypes>  
    <Keywords>... </Keywords>  
    <Shortcut>... </Shortcut>  
</Header>  
  
```  
  
|Alt Öğe|Açıklama|  
|-------------------|-----------------|  
|[Author öğesi](../ide/code-snippets-schema-reference.md#author)|İsteğe bağlı öğe. Kod parçacığını yazan kişinin veya şirketin adı. Sıfır veya bir olabilir `Author` öğelerinde bir `Header` öğesi.|  
|[Description öğesi](../ide/code-snippets-schema-reference.md#description)|İsteğe bağlı öğe. Kod parçacığının açıklaması. Sıfır veya bir olabilir `Description` öğelerinde bir `Header` öğesi.|  
|[HelpUrl öğesi](../ide/code-snippets-schema-reference.md#helpurl)|İsteğe bağlı öğe. Kod parçacığı hakkında daha fazla bilgi içeren URL. Sıfır veya bir olabilir `HelpURL` bir Header öğesinde öğeleri. **Not:** Visual Studio kullanmayan `HelpUrl` öğesi. Öğe, IntelliSense Kod Parçacığı XML şemasının bir parçasıdır ve öğeyi içeren her kod parçacığı doğrulanacaktır, ancak öğenin değeri hiçbir zaman kullanılmaz.|  
|[Keywords öğesi](../ide/code-snippets-schema-reference.md#keywords)|İsteğe bağlı öğe. Grupları `Keyword` öğeleri. Sıfır veya bir olabilir `Keywords` öğelerinde bir `Header` öğesi.|  
|[Shortcut öğesi](../ide/code-snippets-schema-reference.md#shortcut)|İsteğe bağlı öğe. Kod parçacığını eklemek için kullanılabilecek kısayol metnini belirtir. Sıfır veya bir olabilir `Shortcut` öğelerinde bir `Header` öğesi.|  
|[SnippetTypes öğesi](../ide/code-snippets-schema-reference.md#snippettypes)|İsteğe bağlı öğe. Grupları `SnippetType` öğeleri. Sıfır veya bir olabilir `SnippetTypes` öğelerinde bir `Header` öğesi. Varsa hiçbir `SnippetTypes` öğeleri, kod parçacığı her zaman geçerli.|  
|[Title öğesi](../ide/code-snippets-schema-reference.md#title)|Gerekli öğe. Kod parçacığının kolay adı. Olmalıdır tam olarak bir `Title` öğesinde bir `Header` öğesi.|  
  
|Üst Öğe|Açıklama|  
|--------------------|-----------------|  
|[CodeSnippet öğesi](../ide/code-snippets-schema-reference.md#codesnippet)|Tüm kod parçacığı verisi için üst öğe.|  
  
##  <a name="helpurl"></a> HelpUrl öğesi  
 Bir kod parçacığı hakkında daha fazla bilgi sağlayan URL'yi belirtir.  
  
> [!NOTE]
>  Visual Studio kullanmayan `HelpUrl` öğesi. Öğe, IntelliSense Kod Parçacığı XML şemasının bir parçasıdır ve öğeyi içeren her kod parçacığı doğrulanacaktır, ancak öğenin değeri hiçbir zaman kullanılmaz.  
  
```xml  
<HelpUrl>  
    www.microsoft.com  
</HelpUrl>  
  
```  
  
|Üst Öğe|Açıklama|  
|--------------------|-----------------|  
|[Header öğesi](../ide/code-snippets-schema-reference.md#header)|Kod parçacığı hakkında genel bilgiler içerir.|  
  
 Metin değeri isteğe bağlıdır. Bu metin, kod parçacığı hakkında daha fazla bilgi için ziyaret edilmesi gereken URL'yi belirtir.  
  
##  <a name="id"></a> ID öğesi  
 İçin benzersiz bir tanımlayıcı belirtir bir `Literal` veya `Object` öğesi. Aynı değeri hiçbir iki değişmez değerler veya nesneler aynı kod parçacığında olabilir kendi `ID` öğeleri. Değişmez değerler ve nesneler içeremez bir `ID` bitiş değerini içeren öğe. Değer `$end$` ayrılmıştır ve kod parçacığı eklendikten sonra imlecin yerleştirileceği konumu işaretlemek için kullanılır.  
  
```xml  
<ID>  
    Unique Identifier  
</ID>  
  
```  
  
|Üst Öğe|Açıklama|  
|--------------------|-----------------|  
|[Literal öğesi](../ide/code-snippets-schema-reference.md#literal)|Kod parçacığının düzenleme yapabileceğiniz değişmez değer alanlarını tanımlar.|  
|[Object öğesi](../ide/code-snippets-schema-reference.md#object)|Kod parçacığının düzenleme yapabileceğiniz nesne alanlarını tanımlar.|  
  
 Bir metin değeri gereklidir. Bu metin, nesne veya değişmez değer için benzersiz tanımlayıcıyı belirtir.  
  
##  <a name="import"></a> İçeri aktarma öğesi  
 Bir IntelliSense Kod Parçacığı tarafından kullanılan içeri aktarılan ad alanlarını belirtir.  
  
> [!NOTE]
>  `Import` Öğesi yalnızca Visual Basic projeleri için desteklenir.  
  
```xml  
<Import>  
    <Namespace>... </Namespace>  
</Import>  
  
```  
  
|Alt Öğe|Açıklama|  
|-------------------|-----------------|  
|[Namespace öğesi](../ide/code-snippets-schema-reference.md#namespace)|Gerekli öğe. Kod parçacığı tarafından kullanılan ad alanını belirtir. Olmalıdır tam olarak bir `Namespace` öğesinde bir `Import` öğesi.|  
  
|Üst Öğe|Açıklama|  
|--------------------|-----------------|  
|[Imports öğesi](../ide/code-snippets-schema-reference.md#imports)|İçin gruplandırma öğesi **alma** öğeleri.|  
  
##  <a name="imports"></a> Imports öğesi  
 Grupları tek tek `Import` öğeleri.  
  
> [!NOTE]
>  `Imports` Öğesi yalnızca Visual Basic projeleri için desteklenir.  
  
```xml  
<Imports>  
    <Import>... </Import>  
<Imports>  
```  
  
|Alt Öğe|Açıklama|  
|-------------------|-----------------|  
|[İçeri aktarma öğesi](../ide/code-snippets-schema-reference.md#import)|İsteğe bağlı öğe. Kod parçacığı için içeri aktarılan ad alanlarını içerir. Sıfır veya daha fazla olabilir **alma** öğelerinde bir `Imports` öğesi.|  
  
|Üst Öğe|Açıklama|  
|--------------------|-----------------|  
|[Snippet öğesi](../ide/code-snippets-schema-reference.md#snippet)|Kod parçacığı için başvuruları, içeri aktarımları, bildirimleri ve kodu içerir.|  
  
##  <a name="keyword"></a> Keyword öğesi  
 Kod parçacığı için özel bir anahtar sözcük belirtir. Kod parçacığı anahtar sözcükleri Visual Studio tarafından kullanılır ve çevrimiçi içerik sağlayıcılarının aramaya veya kategorilere ayırmaya yönelik özel anahtar sözcükler eklemek için kullandıkları standart bir yöntemi temsil eder.  
  
```xml  
<Keyword>  
    Code Snippet Keyword  
</Keyword>  
```  
  
|Üst Öğe|Açıklama|  
|--------------------|-----------------|  
|[Keywords öğesi](../ide/code-snippets-schema-reference.md#keywords)|Grupları tek tek `Keyword` öğeleri.|  
  
 Bir metin değeri gereklidir. Kod parçacığı için anahtar sözcük.  
  
##  <a name="keywords"></a> Keywords öğesi  
 Grupları tek tek `Keyword` öğeleri. Kod parçacığı anahtar sözcükleri Visual Studio tarafından kullanılır ve çevrimiçi içerik sağlayıcılarının aramaya veya kategorilere ayırmaya yönelik özel anahtar sözcükler eklemek için kullandıkları standart bir yöntemi temsil eder  
  
```xml  
<Keywords>  
    <Keyword>... </Keyword>  
    <Keyword>... </Keyword>  
<Keywords>  
```  
  
|Alt Öğe|Açıklama|  
|-------------------|-----------------|  
|[Keyword öğesi](../ide/code-snippets-schema-reference.md#keyword)|İsteğe bağlı öğe. Kod parçacığı için tek tek anahtar sözcükleri içerir. Sıfır veya daha fazla olabilir `Keyword` öğelerinde bir `Keywords` öğesi.|  
  
|Üst Öğe|Açıklama|  
|--------------------|-----------------|  
|[Header öğesi](../ide/code-snippets-schema-reference.md#header)|Kod parçacığı hakkında genel bilgiler içerir.|  
  
##  <a name="literal"></a> Literal öğesi  
 Kod parçacığının düzenleme yapabileceğiniz değişmez değerlerini tanımlar. `Literal` Öğesi tamamen kod parçacığı, ancak büyük olasılıkla olacak içinde yer alan kod parçasını koda eklendikten sonra özelleştirilmesi yerine tanımlamak için kullanılır. Örneğin, değişmez değer dizeleri, sayısal değerler ve bazı değişken adları değişmez değer olarak bildirilmelidir.  
  
 Değişmez değerler ve nesneler içeremez bir **kimliği** öğe değerini selected veya end. Değer `$selected$` , çağrıldığında kod parçacığına eklenecek olan belgedeki seçili metni temsil eder. `$end$` kod parçacığı eklendikten sonra imlecin yerleştirileceği konumu işaretler.  
  
```xml  
<Literal Editable="true/false">  
   <ID>... </ID>  
   <ToolTip>... </ToolTip>  
   <Default>... </Default>  
   <Function>... </Function>  
</Literal>  
```  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`Editable`|İsteğe bağlı `Boolean` özniteliği. Kod parçacığı eklendikten sonra değişmez değerde düzenleme yapıp yapamayacağınızı belirtir. Bu öznitelik varsayılan değeri `true`.|  
  
|Alt Öğe|Açıklama|  
|-------------------|-----------------|  
|[Default öğesi](../ide/code-snippets-schema-reference.md#default)|Gerekli öğe. Kod parçacığını eklediğinizde değişmez değerin alacağı varsayılan değeri belirtir. Olmalıdır tam olarak bir `Default` öğesinde bir `Literal` öğesi.|  
|[Function öğesi](../ide/code-snippets-schema-reference.md#function)|İsteğe bağlı öğe. Değişmez değer Visual Studio'da odağa geldiğinde yürütülecek bir işlevi belirtir. Sıfır veya bir olabilir `Function` öğelerinde bir `Literal` öğesi.|  
|[ID öğesi](../ide/code-snippets-schema-reference.md#id)|Gerekli öğe. Değişmez değer için benzersiz bir tanımlayıcı belirtir. Olmalıdır tam olarak bir `ID` öğesinde bir `Literal` öğesi.|  
|[ToolTip öğesi](../ide/code-snippets-schema-reference.md#tooltip)|İsteğe bağlı öğe. Değişmez değerin beklenen değerini ve kullanımını açıklar. Sıfır veya bir olabilir **araç ipucu** öğelerinde bir `Literal` öğesi.|  
  
|Üst Öğe|Açıklama|  
|--------------------|-----------------|  
|[Declarations öğesi](../ide/code-snippets-schema-reference.md#declarations)|Kod parçacığının düzenleme yapabileceğiniz değişmez değerlerini ve nesnelerini içerir.|  
  
##  <a name="namespace"></a> Namespace öğesi  
 Kod parçacığının derlenip çalışması için içeri aktarılması gereken ad alanını belirtir. Belirtilen ad alanı `Namespace` öğesi eklenen otomatik olarak bir `Imports` zaten yoksa, kod deyimi başında.  
  
> [!NOTE]
>  `Namespace` Öğesi yalnızca Visual Basic projeleri için desteklenir.  
  
```xml  
<Namespace>  
    Namespace  
</Namespace>  
```  
  
|Üst Öğe|Açıklama|  
|--------------------|-----------------|  
|[İçeri aktarma öğesi](../ide/code-snippets-schema-reference.md#import)|Belirtilen ad alanını içeri aktarır.|  
  
 Bir metin değeri gereklidir. Bu metin, kod parçacığının içeri aktarıldığını varsaydığı bir ad alanını belirtir.  
  
##  <a name="object"></a> Object öğesi  
 Kod parçacığının düzenleme yapabileceğiniz nesnelerini tanımlar. `Object` Öğesi, kod parçacığının gerek duyduğu, ancak büyük olasılıkla kod parçacığının kendisi dışında tanımlanacak bir öğeyi tanımlamak için kullanılır. Örneğin, Windows Forms denetimleri, ASP.NET denetimleri, nesne örnekleri ve tür örnekleri nesne olarak bildirilmelidir. Nesne bildirimi bir tür belirtilmesini gerektirir yapılır `Type` öğesi.  
  
```xml  
<Object Editable="true/false">  
    <ID>... </ID>  
    <Type>... </Type>  
    <ToolTip>... </ToolTip>  
    <Default>... </Default>  
    <Function>... </Function>  
</Object>  
```  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`Editable`|İsteğe bağlı `Boolean` özniteliği. Kod parçacığı eklendikten sonra değişmez değerde düzenleme yapıp yapamayacağınızı belirtir. Bu öznitelik varsayılan değeri `true`.|  
  
|Alt Öğe|Açıklama|  
|-------------------|-----------------|  
|[Default öğesi](../ide/code-snippets-schema-reference.md#default)|Gerekli öğe. Kod parçacığını eklediğinizde değişmez değerin alacağı varsayılan değeri belirtir. Olmalıdır tam olarak bir `Default` öğesinde bir `Literal` öğesi.|  
|[Function öğesi](../ide/code-snippets-schema-reference.md#function)|İsteğe bağlı öğe. Değişmez değer Visual Studio'da odağa geldiğinde yürütülecek bir işlevi belirtir. Sıfır veya bir olabilir `Function` öğelerinde bir `Literal` öğesi.|  
|[ID öğesi](../ide/code-snippets-schema-reference.md#id)|Gerekli öğe. Değişmez değer için benzersiz bir tanımlayıcı belirtir. Olmalıdır tam olarak bir `ID` öğesinde bir `Literal` öğesi.|  
|[ToolTip öğesi](../ide/code-snippets-schema-reference.md#tooltip)|İsteğe bağlı öğe. Değişmez değerin beklenen değerini ve kullanımını açıklar. Sıfır veya bir olabilir **araç ipucu** öğelerinde bir `Literal` öğesi.|  
|[Type öğesi](../ide/code-snippets-schema-reference.md#type)|Gerekli öğe. Nesnenin türünü belirtir. Olmalıdır tam olarak bir `Type` öğesinde bir `Object` öğesi.|  
  
|Üst Öğe|Açıklama|  
|--------------------|-----------------|  
|[Declarations öğesi](../ide/code-snippets-schema-reference.md#declarations)|Kod parçacığının düzenleme yapabileceğiniz değişmez değerlerini ve nesnelerini içerir.|  
  
##  <a name="reference"></a> Reference öğesi  
 Kod parçacığının gerek duyduğu derleme başvuruları hakkındaki bilgileri belirtir.  
  
> [!NOTE]
>  `Reference` Öğesi yalnızca Visual Basic projeleri için desteklenir.  
  
```xml  
<Reference>  
    <Assembly>... </Assembly>  
    <Url>... </Url>  
</Reference>  
```  
  
|Alt Öğe|Açıklama|  
|-------------------|-----------------|  
|[Assembly öğesi](../ide/code-snippets-schema-reference.md#assembly)|Gerekli öğe. Kod parçacığının başvurduğu derlemenin adını içerir. Olmalıdır tam olarak bir `Assembly` öğesinde bir `Reference` öğesi.|  
|[URL öğesi](../ide/code-snippets-schema-reference.md#url)|İsteğe bağlı öğe. Başvurulan derleme hakkında daha fazla bilgi sağlayan bir URL içerir. Sıfır veya bir olabilir `Url` öğelerinde bir `Reference` öğesi.|  
  
|Üst Öğe|Açıklama|  
|--------------------|-----------------|  
|[References öğesi](../ide/code-snippets-schema-reference.md#references)|İçin gruplandırma öğesi `Reference` öğeleri.|  
  
##  <a name="references"></a> References öğesi  
 Grupları tek tek `Reference` öğeleri.  
  
> [!NOTE]
>  `References` Öğesi yalnızca Visual Basic projeleri için desteklenir.  
  
```xml  
<References>  
    <Reference>... </Reference>  
</References>  
```  
  
|Alt Öğe|Açıklama|  
|-------------------|-----------------|  
|[Reference öğesi](../ide/code-snippets-schema-reference.md#reference)|İsteğe bağlı öğe. Kod parçacığı için derleme başvuruları hakkındaki bilgileri içerir. Sıfır veya daha fazla olabilir `Reference` öğelerinde bir `References` öğesi.|  
  
|Üst Öğe|Açıklama|  
|--------------------|-----------------|  
|[Snippet öğesi](../ide/code-snippets-schema-reference.md#snippet)|Kod parçacığı için başvuruları, içeri aktarımları, bildirimleri ve kodu içerir.|  
  
##  <a name="shortcut"></a> Shortcut öğesi  
 Kod parçacığını eklemek için kullanılan kısayol metnini belirtir. Metin değerini bir `Shortcut` öğesi yalnızca alfasayısal karakterler içerebilir tire (-) ve alt çizgi (_).  
  
> [!CAUTION]
>  _ ve – C++ kod parçacığı kısayollarında desteklenmeyen karakterlerdir.  
  
```xml  
<Shortcut>  
    Shortcut Text  
</Shortcut>  
```  
  
|Üst Öğe|Açıklama|  
|--------------------|-----------------|  
|[Header öğesi](../ide/code-snippets-schema-reference.md#header)|Kod parçacığı hakkında genel bilgiler içerir.|  
  
 Metin değeri isteğe bağlıdır. Bu metin, kod parçacığını eklemek için bir kısayol olarak kullanılır.  
  
##  <a name="snippet"></a> Snippet öğesi  
 Kod parçacığı için başvuruları, içeri aktarımları, bildirimleri ve kodu belirtir.  
  
```xml  
<Snippet>  
    <References>... </References>  
    <Imports>... </Imports>  
    <Declarations>... </Declarations>  
    <Code>... </Code>  
</Snippet>  
  
```  
  
|Alt Öğe|Açıklama|  
|-------------------|-----------------|  
|[Kod öğesi](../ide/code-snippets-schema-reference.md#code)|Gerekli öğe. Bir belge dosyasına eklemek istediğiniz kodu belirtir. Olmalıdır tam olarak bir `Code` öğesinde bir `Snippet` öğesi.|  
|[Declarations öğesi](../ide/code-snippets-schema-reference.md#declarations)|İsteğe bağlı öğe. Bir kod parçacığının düzenleyebileceğiniz bölümlerini oluşturan değişmez değerleri ve nesneleri belirtir. Sıfır veya bir olabilir `Declarations` öğelerinde bir `Snippet` öğesi.|  
|[Imports öğesi](../ide/code-snippets-schema-reference.md#imports)|İsteğe bağlı öğe. Grupları tek tek `Import` öğeleri. Sıfır veya bir olabilir `Imports` öğelerinde bir `Snippet` öğesi.|  
||İsteğe bağlı öğe. Grupları tek tek `Reference` öğeleri. Sıfır veya bir olabilir `References` öğelerinde bir `Snippet` öğesi.|  
  
|Üst Öğe|Açıklama|  
|--------------------|-----------------|  
|[CodeSnippet öğesi](../ide/code-snippets-schema-reference.md#codesnippet)|Visual Studio kod dosyalarına ekleyebileceğiniz bir başlık ve birden fazla IntelliSense Kod Parçacığı belirtmenizi sağlar.|  
  
##  <a name="snippettype"></a> SnippetType öğesi  
 Visual Studio'nun kod parçacığını nasıl eklediğini belirtir.  
  
```xml  
<SnippetType>  
    SurroundsWith/Expansion  
<SnippetType>  
```  
  
|Üst Öğe|Açıklama|  
|--------------------|-----------------|  
|[SnippetTypes öğesi](../ide/code-snippets-schema-reference.md#snippettypes)|Grupları `SnippetType` öğeleri.|  
  
 Metin değeri şu değerlerden biri olmalıdır:  
  
-   `SurroundsWith`: kod parçacığının, seçilen bir kod parçasının etrafına yerleştirilmesini sağlar.  
  
-   `Expansion`: kod parçacığının imlece eklenmesini sağlar.  
  
-   `Refactoring`: kod parçacığının Visual C# yeniden düzenlemesi sırasında kullanıldığını belirtir. `Refactoring` özel kod parçacıklarında kullanılamaz.  
  
##  <a name="snippettypes"></a> SnippetTypes öğesi  
 Grupları tek tek `SnippetType` öğeleri. Varsa `SnippetTypes` öğesi yoksa, kod içinde kod parçacığının istenen yere eklenebileceğini.  
  
```xml  
<SnippetTypes>  
    <SnippetType>... </SnippetType>  
    <SnippetType>... </SnippetType>  
<SnippetTypes>  
```  
  
|Alt Öğe|Açıklama|  
|-------------------|-----------------|  
|[SnippetType öğesi](../ide/code-snippets-schema-reference.md#snippettype)|İsteğe bağlı öğe. Visual Studio'nun kod parçacığını kodun içine nasıl eklediğini belirtir. Sıfır veya daha fazla olabilir `SnippetType` öğelerinde bir `SnippetTypes` öğesi.|  
  
|Üst Öğe|Açıklama|  
|--------------------|-----------------|  
|[Header öğesi](../ide/code-snippets-schema-reference.md#header)|Kod parçacığı hakkında genel bilgiler belirtir.|  
  
##  <a name="title"></a> Title öğesi  
 Kod parçacığı için başlığı belirtir. Saklanan `Title` kod parçacığının öğesi görünür **kod parçacığı Seçici** ve kod parçacığının açıklamasında **kod parçacıkları Yöneticisi**.  
  
```xml  
<Title>  
    Code Snippet Title  
<Title>  
```  
  
|Üst Öğe|Açıklama|  
|--------------------|-----------------|  
|[Header öğesi](../ide/code-snippets-schema-reference.md#header)|Kod parçacığı hakkında genel bilgiler belirtir.|  
  
 Bir metin değeri gereklidir. Bu metin kod parçacığının başlığını belirtir.  
  
##  <a name="tooltip"></a> ToolTip öğesi  
 Kod parçacığındaki bir değişmez değerin veya nesnenin beklenen değerini ve kullanımını açıklar; Visual Studio, kod parçacığını bir projeye eklerken ToolTip öğesinde bunu görüntüler. ToolTip metni, kod parçacığı eklendikten sonra değişmez değerin veya nesnenin üzerine fare geldiğinde görüntülenir.  
  
```xml  
<ToolTip>  
    ToolTip description  
</ToolTip>  
```  
  
|Üst Öğe|Açıklama|  
|--------------------|-----------------|  
|[Literal öğesi](../ide/code-snippets-schema-reference.md#literal)|Kod parçacığının düzenleme yapabileceğiniz değişmez değer alanlarını tanımlar.|  
|[Object öğesi](../ide/code-snippets-schema-reference.md#object)|Kod parçacığının düzenleme yapabileceğiniz nesne alanlarını tanımlar.|  
  
 Bir metin değeri gereklidir. Bu metin, kod parçacığındaki nesne veya değişmez değer ile ilişkilendirilecek ToolTip açıklamasını belirtir.  
  
##  <a name="type"></a> Type öğesi  
 Nesnenin türünü belirtir. `Object` Öğesi, kod parçacığının gerek duyduğu, ancak büyük olasılıkla kod parçacığının kendisi dışında tanımlanacak bir öğeyi tanımlamak için kullanılır. Örneğin, Windows Forms denetimleri, ASP.NET denetimleri, nesne örnekleri ve tür örnekleri nesne olarak bildirilmelidir. Nesne bildirimi bir tür belirtilmesini gerektirir yapılır `Type` öğesi.  
  
```xml  
<Type>  
    Type  
</Type>  
```  
  
|Üst Öğe|Açıklama|  
|--------------------|-----------------|  
|[Object öğesi](../ide/code-snippets-schema-reference.md#object)|Kod parçacığının düzenleme yapabileceğiniz nesne alanlarını tanımlar.|  
  
 Bir metin değeri gereklidir. Bu metin nesnenin türünü belirtir.  
  
##  <a name="url"></a> URL öğesi  
 Başvurulan derleme hakkında daha fazla bilgi sağlayan bir URL'yi belirtir.  
  
> [!NOTE]
>  `Url` Öğesi yalnızca Visual Basic projeleri için desteklenir.  
  
```xml  
<Url>  
    www.microsoft.com  
</Url>  
```  
  
|Üst Öğe|Açıklama|  
|--------------------|-----------------|  
|[Reference öğesi](../ide/code-snippets-schema-reference.md#reference)|Kod parçacığının gerek duyduğu derleme başvurularını belirtir.|  
  
 Bir metin değeri gereklidir. Bu metin, başvurulan derleme hakkında daha fazla bilgi içeren bir URL'yi belirtir. Bu URL, başvuru projeye eklenemediğinde görüntülenir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Kod parçacıkları](../ide/code-snippets.md)   
 [İzlenecek Yol: Kod Parçacığı Oluşturma](../ide/walkthrough-creating-a-code-snippet.md)



