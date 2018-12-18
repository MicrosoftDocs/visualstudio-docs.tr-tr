---
title: 'İzlenecek yol: kod parçacığı oluşturma | Microsoft Docs'
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
- code snippets, creating
- code snippets, shortcut
- code snippets, template
- code snippets, replacements
- code snippets, references
- code snippets, imports
ms.assetid: 0dcaae11-39cf-4463-9c90-2494321251c2
caps.latest.revision: 25
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 038635db92d08837cc6519670053c9619ebe3c9b
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49267754"
---
# <a name="walkthrough-creating-a-code-snippet"></a>İzlenecek Yol: Kod Parçacığı Oluşturma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Yalnızca birkaç adımda bir kod parçacığı oluşturabilirsiniz. Tek yapmak için ihtiyacınız olan bir XML dosyası oluşturun, uygun öğeleri doldurmak ve kodunuzu ekleyin. Kodunuza başvurular ve değiştirme parametreleri de ekleyebilirsiniz. Kod parçacığını kod parçacıkları yöneticisindeki İçe Aktar düğmesini kullanarak Visual Studio yüklemenize ekleyebilirsiniz (**Araçlar/kod parçacıkları Yöneticisi**).  
  
> [!TIP]
>  Kod parçacıkları daha kolayca yazılacağı hakkında daha fazla bilgi için aşağıdaki gibi topluluk araçları için CodePlex Web sitesinde arama [parçacık Düzenleyicisi](http://go.microsoft.com/fwlink/?LinkId=251033).  
  
## <a name="snippet-template"></a>Parçacık şablonu  
 Temel parçacık şablonu aşağıda verilmiştir:  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
<CodeSnippets  
    xmlns="http://schemas.microsoft.com/VisualStudio/2005/CodeSnippet">  
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
  
### <a name="to-create-a-code-snippet"></a>Kod parçacığı oluşturmak için  
  
1.  Visual Studio'da yeni bir XML dosyası oluşturun ve yukarıda gösterilen şablonu ekleyin.  
  
2.  Kod parçacığı başlığında örn doldurun "VB, başlık öğesinde Merhaba Dünya".  
  
3.  Kod öğesinin diller özniteliğinde parçacığın dilini doldurun. Bu örnekte, "VB" kullanın.  
  
4.  Bazı kod örneğin kod öğesinin içindeki CDATA bölümüne kod ekleyin:  
  
    ```  
    <Code Language="VB">  
        <![CDATA[Console.WriteLine("Hello, World!")]]>  
    </Code>  
  
    ```  
  
5.  Kod parçacığını VBCodeSnippet.snippet olarak kaydedin.  
  
### <a name="to-add-a-code-snippet-to-visual-studio"></a>Visual Studio'ya bir kod parçacığı eklemek için  
  
1.  Kod parçacıkları Yöneticisi'ni kullanarak, kendi parçacıklarınızı Visual Studio yüklemenize ekleyebilirsiniz. Kod parçacıkları Yöneticisi'ni açın (**Araçlar/kod parçacıkları Yöneticisi**).  
  
2.  Tıklayın **alma** düğmesi.  
  
3.  Önceki yordamda kod parçacığını kaydedildiği konuma seçin ve tıklayın Git **açık**.  
  
4.  **Kod parçacığını içe aktar** iletişim kutusunu açar, sağ bölmedeki seçeneklerden parçacığın nereye isteyen. Seçeneklerden biri olmalıdır **kod Parçacıklarım**. Seçin ve **son**, ardından **Tamam**.  
  
5.  Parçacık aşağıdaki konuma kopyalanır:  
  
     `%USERPROFILE%\Documents\Visual Studio 2013\Code Snippets\Visual Basic\My Code Snippets`  
  
6.  Visual Basic projesi açarak ve kod bir dosyası açarak parçacığınızı test. Dosyada tıklatın **parçacık Ekle** bağlam menüsünde **kod Parçacıklarım**. Adlı bir parçacık görmelisiniz **My Visual Basic kod parçacığını**. Çift tıklatın.  
  
7.  Görmelisiniz `Console.WriteLine("Hello, World!")` kodda eklenir.  
  
### <a name="adding-description-and-shortcut-fields"></a>Açıklama ve kısayol alanları ekleme  
  
1.  Açıklama alanları, kod parçacıkları Yöneticisi'nde görüntülendiğinde, kod parçacığı hakkında daha fazla bilgi verin. Kısayol, kod parçacığını eklemek için kullanıcıların yazabileceği bir etikettir. Dosyasını açarak eklediğiniz parçacığı düzenleyin `%USERPROFILE%\Documents\Visual Studio 2013\Code Snippets\Visual Basic\My Code Snippet\VBCodeSnippet.snippet`.  
  
2.  Üstbilgi öğesine yazar ve açıklama öğeleri ekleyin ve bunları doldurun.  
  
3.  Üstbilgi öğesi şuna benzemelidir:  
  
    ```  
    <Header>  
        <Title>Hello World VB</Title>  
        <Author>Myself</Author>  
        <Description>Says Hello to the world.</Description>  
    </Header>  
  
    ```  
  
4.  Kod parçacıkları Yöneticisi'ni açın ve kod parçacığınızı seçin. Sağ bölmede açıklama ve yazar alanlarını artık doldurulmuş olduğunu görmelisiniz.  
  
5.  Bir kısayol eklemek için bir kısayol öğesi yazarı yanı sıra ve Description öğesi ekleyin:  
  
    ```  
    <Header>  
        <Title>Hello World VB</Title>  
        <Author>Myself</Author>  
        <Description>Says Hello to the world.</Description>  
        <Shortcut>hello</Shortcut>  
    </Header>  
  
    ```  
  
6.  Kod parçacığı dosyasını yeniden kaydedin.  
  
7.  Bir kısayolu sınamak için bir Visual Basic projesi açın ve bir kod dosyası açın. Tür `hello` dosya ve SEKME tuşuna basın. Kod parçacığı eklenmelidir.  
  
### <a name="to-add-references-and-imports"></a>Başvurular ve içe aktarmalar eklemek için  
  
1.  Visual Basic parçacıkları ile başvurular öğesini kullanarak projeye bir başvuru ekleyin ve almalar öğesini kullanarak bir almalar bildirimi ekleyin. (Diğer dillerdeki Parçacıklar bu özelliğe sahip değildir.) Örneğin, değiştirirseniz `Console.WriteLine` için kod örneğinde `MessageBox.Show`, System.Windows.Forms.dll derlemesini projeye eklemeniz gerekebilir.  
  
2.  Kod parçacığınızı açın.  
  
3.  Parçacık öğesinin altına başvurular öğesini ekleyin:  
  
    ```  
    <References>  
        <Reference>  
            <Assembly>System.Windows.Forms.dll</Assembly>  
        </Reference>  
    </References>  
  
    ```  
  
4.  Parçacık öğesinin altına içeri aktarmalar öğesini ekleyin:  
  
    ```  
    <Imports>  
        <Import>  
           <Namespace>System.Windows.Forms</Namespace>  
        </Import>  
    </Imports>  
  
    ```  
  
5.  CDATA bölümünü şu şekilde değiştirin:  
  
    ```  
    <![CDATA[MessageBox.Show("Hello, World!")]]>  
    ```  
  
6.  Kod parçacığını kaydedin.  
  
7.  Visual Basic projesi açın ve parçacık ekleyin.  
  
8.  Kod dosyasının en üstüne bir içe aktarmalar deyimi görürsünüz:  
  
    ```  
    Imports System.Windows.Forms  
  
    ```  
  
9. Projenin özelliklerini arayın. Başvurular sekmesi System.Windows.Forms.dll'e bir başvuru içerir.  
  
### <a name="adding-replacements"></a>Değişiklik ekleme  
  
1.  Örneğin bir değişken ekleyip, kullanıcının değişkeni geçerli projedeki biriyle değiştirin istediğiniz kullanıcı tarafından değiştirilmesi, kod parçacıklarınız bölümlerini isteyebilirsiniz. İki tür değişiklik sağlayabilirsiniz: sabit değerler ve nesneler. Değişmez değerler, bazı türdeki (dize değişmez değerleri, değişken adları veya sayısal değerlerin dize halinde temsili) dizelerdir. Bazı tür örnekleridir bir dize örneği nesneleridir. Bu yordamda bir değişmez değer değişikliği ve bir nesne değişikliği bildirimini ve bu değişikliklere başvuruda bulunmak için kodu değiştirin.  
  
2.  Kod parçacığınızı açın.  
  
3.  Bu örnek, bir SQL bağlantı dizesi kullanır, bu nedenle uygun başvuruları eklemek için içeri aktarmalar ve başvurular öğelerini değiştirmeniz gerekir:  
  
    ```  
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
  
4.  SQL bağlantı dizesi için bir değişmez değer değişikliği bildirmek için parçacık öğesinin altına bir bildirimler öğesi ekleyin ve alt öğeleri olan bir sabit değer öğesi kimliği, araç ipucu ve değiştirmeye yönelik varsayılan değer ekleyebilirsiniz:  
  
    ```  
    <Declarations>  
        <Literal>  
            <ID>SqlConnString</ID>  
            <ToolTip>Replace with a SQL connection string.</ToolTip>  
            <Default>"SQL connection string"</Default>  
        </Literal>  
    </Declarations>  
  
    ```  
  
5.  SQL bağlantısı için bir nesne değişikliği bildirmek için bildirimler öğesinin içine bir nesne öğesi ekleyin ve kimlik için alt öğeler, nesne, araç ipucu ve varsayılan değer türü ekleyin. Elde edilen bildirimler öğesi gibi görünmelidir:  
  
    ```  
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
  
    ```  
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
  
9. Kod aşağıdaki gibi görünmelidir nerede değişiklik `SQL connection string` ve `dcConnection` açık turuncu vurgulanır. Birinden diğerine gitmek için SEKME tuşuna basın.  
  
    ```  
    Dim daCustomers As SqlDataAdapter  
    Dim selectCommand As SqlCommand  
  
    daCustomers = New SqlClient.SqlDataAdapter()  
    selectCommand = New SqlClient.SqlCommand("SQL connection string")  
    daCustomers.SelectCommand = selectCommand  
    daCustomers.SelectCommand.Connection = dcConnection  
  
    ```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Kod Parçacıkları Şema Başvurusu](../ide/code-snippets-schema-reference.md)



