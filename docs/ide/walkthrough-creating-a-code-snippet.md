---
title: 'İzlenecek Yol: Kod parçacığı oluşturma'
ms.date: 10/27/2017
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- code snippets, creating
- code snippets, shortcut
- code snippets, template
- code snippets, replacements
- code snippets, references
- code snippets, imports
ms.assetid: 0dcaae11-39cf-4463-9c90-2494321251c2
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- VB
ms.workload:
- multiple
ms.openlocfilehash: 517eb98e7ca5b32d07a4501823ca092c366e4639
ms.sourcegitcommit: 0cf1e63b6e0e6a0130668278489b21a6e5038084
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/02/2018
ms.locfileid: "39469158"
---
# <a name="walkthrough-create-a-code-snippet"></a>İzlenecek Yol: Kod parçacığı oluşturma
Yalnızca birkaç adımda bir kod parçacığı oluşturabilirsiniz. Tek yapmak için ihtiyacınız olan bir XML dosyası oluşturun, uygun öğeleri doldurmak ve kodunuzu ekleyin. Kodunuza başvurular ve değiştirme parametreleri de ekleyebilirsiniz. Kod parçacığını kullanarak Visual Studio yüklemenize ekleyebilirsiniz **alma** düğmesini **kod parçacıkları Yöneticisi** (**Araçları**  >   **Kod parçacıkları Yöneticisi**).

## <a name="snippet-template"></a>Parçacık şablonu
 Temel parçacık şablonu aşağıda verilmiştir:

```xml
<?xml version="1.0" encoding="utf-8"?>
<CodeSnippets xmlns="http://schemas.microsoft.com/VisualStudio/2005/CodeSnippet">
    <CodeSnippet Format="1.0.0">
        <Header>
            <Title></Title>
        </Header>
        <Snippet>
            <Code Language="">
                <![CDATA[]]>
            </Code>
        </Snippet>
    </CodeSnippet>
</CodeSnippets>
```

### <a name="create-a-code-snippet"></a>Kod parçacığı oluşturma

1.  Visual Studio'da yeni bir XML dosyası oluşturun ve yukarıda gösterilen şablonu ekleyin.

2.  Kod parçacığı başlığında örn doldurun "Hello World VB" içinde **başlık** öğesi.

3.  Kod parçacığında dilini doldurun **dil** özniteliği **kod** öğesi. Bu örnekte, "VB" kullanın.

4.  Bazı kodda **CDATA** bölümünü **kod** öğesi, örneğin:

    ```xml
    <Code Language="VB">
        <![CDATA[Console.WriteLine("Hello, World!")]]>
    </Code>
    ```

5.  Kod parçacığını olarak kaydedin *VBCodeSnippet.snippet*.

### <a name="add-a-code-snippet-to-visual-studio"></a>Visual Studio'ya bir kod parçacığını ekleyin

1.  Kod parçacıkları Yöneticisi'ni kullanarak, kendi parçacıklarınızı Visual Studio yüklemenize ekleyebilirsiniz. Açık **kod parçacıkları Yöneticisi** (**Araçları** > **kod parçacıkları Yöneticisi**).

2.  Tıklayın **alma** düğmesi.

3.  Önceki yordamda kod parçacığını kaydedildiği konuma seçin ve tıklayın Git **açık**.

4.  **Kod parçacığını içe aktar** iletişim kutusunu açar, sağ bölmedeki seçeneklerden parçacığın nereye isteyen. Seçeneklerden biri olmalıdır **kod Parçacıklarım**. Seçin ve **son**, ardından **Tamam**.

5.  Parçacık aşağıdaki konuma kopyalanır:

     *%USERPROFILE%\Documents\Visual studio 2017\Code Snippets\Visual Basic\My kod parçacıkları*

6.  Visual Basic projesi açarak ve kod bir dosyası açarak parçacığınızı test. Dosyayı seçin **parçacıkları** > **parçacık Ekle** bağlam menüsünden **kod Parçacıklarım**. Adlı bir parçacık görmelisiniz **My Visual Basic kod parçacığını**. Çift tıklatın.

    `Console.WriteLine("Hello, World!")` kod dosyasına eklenir.

### <a name="add-description-and-shortcut-fields"></a>Açıklama ve kısayol alanları ekleme

1.  Açıklama alanları, kod parçacıkları Yöneticisi'nde görüntülendiğinde, kod parçacığı hakkında daha fazla bilgi verin. Kısayol, kod parçacığını eklemek için kullanıcıların yazabileceği bir etikettir. Dosyasını açarak eklediğiniz parçacığı düzenleyin *%USERPROFILE%\Documents\Visual Studio 2017\Code Snippets\Visual Basic\My Code Snippet\VBCodeSnippet.snippet*.

2.  Ekleme **Yazar** ve **açıklama** öğelerine **üstbilgi** öğesi ve bunları doldurun.

3.  **Üstbilgi** öğesi şunun gibi görünmelidir:

    ```xml
    <Header>
        <Title>Hello World VB</Title>
        <Author>Myself</Author>
        <Description>Says Hello to the world.</Description>
    </Header>
    ```

4.  Açık **kod parçacıkları Yöneticisi** ve kod parçacığınızı seçin. Sağ bölmede, görmelisiniz **açıklama** ve **Yazar** alanlarını artık doldurulmuş.

5.  Bir kısayol eklemek için Ekle bir **kısayol** yanı sıra öğe **Yazar** ve **açıklama** öğesi:

    ```xml
    <Header>
        <Title>Hello World VB</Title>
        <Author>Myself</Author>
        <Description>Says Hello to the world.</Description>
        <Shortcut>hello</Shortcut>
    </Header>
    ```

6.  Kod parçacığı dosyasını yeniden kaydedin.

7.  Bir kısayolu sınamak için bir Visual Basic projesi açın ve bir kod dosyası açın. Tür `hello` dosya ve tuşuna **sekmesini** iki kez.

    Kod parçacığı eklenir.

### <a name="add-references-and-imports"></a>Başvurular ve içe aktarmalar eklemek

1.  Kullanarak bir projeye bir başvuru ekleyebilirsiniz **başvuruları** öğesini kullanarak bir almalar bildirimi ekleyin **içeri aktarmalar** öğesi. (Bu C# ' de çalışır.) Örneğin, değiştirirseniz `Console.WriteLine` için kod örneğinde `MessageBox.Show`, eklemeniz gerekebilir *System.Windows.Forms.dll* projeyi derlemeye.

2.  Kod parçacığınızı açın.

3.  Ekleme **başvuruları** öğesi altında **kod parçacığı** öğesi:

    ```xml
    <References>
        <Reference>
            <Assembly>System.Windows.Forms.dll</Assembly>
        </Reference>
    </References>
    ```

4.  Ekleme **içeri aktarmalar** öğesi altında **kod parçacığı** öğesi:

    ```xml
    <Imports>
        <Import>
           <Namespace>System.Windows.Forms</Namespace>
        </Import>
    </Imports>
    ```

5.  Değişiklik **CDATA** aşağıdaki bölüme:

    ```xml
    <![CDATA[MessageBox.Show("Hello, World!")]]>
    ```

6.  Kod parçacığını kaydedin.

7.  Visual Basic projesi açın ve parçacık ekleyin.

8.  Göreceğiniz bir `Imports` kod dosyasının üst deyimi:

    ```vb
    Imports System.Windows.Forms
    ```

9. Projenin özelliklerini arayın. **Başvuruları** sekmesini bir başvuru içerir *System.Windows.Forms.dll*.

### <a name="add-replacements"></a>Değişiklik ekleme

1.  Örneğin bir değişken ekleyip, kullanıcının değişkeni geçerli projedeki biriyle değiştirin istediğiniz kullanıcı tarafından değiştirilmesi, kod parçacıklarınız bölümlerini isteyebilirsiniz. İki tür değişiklik sağlayabilirsiniz: sabit değerler ve nesneler. Değişmez değerler, bazı türdeki (dize değişmez değerleri, değişken adları veya sayısal değerlerin dize halinde temsili) dizelerdir. Bazı tür örnekleridir bir dize örneği nesneleridir. Bu yordamda bir değişmez değer değişikliği ve bir nesne değişikliği bildirimini ve bu değişikliklere başvuruda bulunmak için kodu değiştirin.

2.  Kod parçacığınızı açın.

3.  Değiştirmeniz gerekir. Bu nedenle bu örnek, bir SQL bağlantı dizesi kullanır. **içeri aktarmalar** ve **başvuruları** uygun başvuruları eklemek için öğeleri:

    ```xml
    <References>
        <Reference>
            <Assembly>System.Data.dll</Assembly>
        </Reference>
        <Reference>
            <Assembly>System.Xml.dll</Assembly>
        </Reference>
    </References>
    <Imports>
        <Import>
            <Namespace>System.Data</Namespace>
        </Import>
        <Import>
            <Namespace>System.Data.SqlClient</Namespace>
        </Import>
    </Imports>
    ```

4.  SQL bağlantı dizesi için bir değişmez değer değişikliği bildirmek için ekleme bir **bildirimleri** öğesi altında **kod parçacığı** öğesi ve ekleyebilirsiniz bir **değişmez değer** öğeyle Kimliği, araç ipucu ve değiştirmeye yönelik varsayılan değer için alt öğeler:

    ```xml
    <Declarations>
        <Literal>
            <ID>SqlConnString</ID>
            <ToolTip>Replace with a SQL connection string.</ToolTip>
            <Default>"SQL connection string"</Default>
        </Literal>
    </Declarations>
    ```

5.  SQL bağlantısı için bir nesne değişikliği bildirmek için ekleme bir **nesne** öğe içinde **bildirimleri** öğesi ve alt öğeleri için kimliği, nesne, araç ipucu ve varsayılan türü ekleyin değer. Ortaya çıkan **bildirimleri** öğesi şu şekilde görünmelidir:

    ```xml
    <Declarations>
        <Literal>
            <ID>SqlConnString</ID>
            <ToolTip>Replace with a SQL connection string.</ToolTip>
            <Default>"SQL connection string"</Default>
        </Literal>
        <Object>
            <ID>SqlConnection</ID>
            <Type>System.Data.SqlClient.SqlConnection</Type>
            <ToolTip>Replace with a connection object in your application.</ToolTip>
            <Default>dcConnection</Default>
        </Object>
    </Declarations>
    ```

6.  Örneğin $ işaretleriyle çevreleyen ile değiştirmeler kod bölümünde, başvuru `$replacement$`:

    ```xml
    <Code Language="VB" Kind="method body">
        <![CDATA[Dim daCustomers As SqlDataAdapter
            Dim selectCommand As SqlCommand

            daCustomers = New SqlClient.SqlDataAdapter()
            selectCommand = new SqlClient.SqlCommand($SqlConnString$)
            daCustomers.SelectCommand = selectCommand
            daCustomers.SelectCommand.Connection = $SqlConnection$]]>
    </Code>
    ```

7.  Kod parçacığını kaydedin.

8.  Visual Basic projesi açın ve parçacık ekleyin.

9. Kod aşağıdaki gibi görünmelidir nerede değişiklik `SQL connection string` ve `dcConnection` açık turuncu vurgulanır. Seçin **sekmesini** birinden diğerine gitmek için.

    ```vb
    Dim daCustomers As SqlDataAdapter
    Dim selectCommand As SqlCommand

    daCustomers = New SqlClient.SqlDataAdapter()
    selectCommand = New SqlClient.SqlCommand("SQL connection string")
    daCustomers.SelectCommand = selectCommand
    daCustomers.SelectCommand.Connection = dcConnection
    ```

## <a name="see-also"></a>Ayrıca bkz.

- [Kod parçacıkları şema başvurusu](../ide/code-snippets-schema-reference.md)