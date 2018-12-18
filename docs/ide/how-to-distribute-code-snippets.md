---
title: 'Nasıl yapılır: kod parçacıklarını dağıtma'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- code snippets, distributing
ms.assetid: 5f717abd-e167-47ae-818c-6b0bae100ceb
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- VB
ms.workload:
- multiple
ms.openlocfilehash: cd6aba7c20c920c0c4351a1e9aa263fc73cd4415
ms.sourcegitcommit: 495bba1d8029646653f99ad20df2f80faad8d58b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/31/2018
ms.locfileid: "39380423"
---
# <a name="how-to-distribute-code-snippets"></a>Nasıl yapılır: kod parçacıklarını dağıtma

Kod parçacıklarınızı arkadaşlarınıza verebilir ve bunları kullanarak kendi bilgisayarlarındaki parçacıkları yükleme **kod parçacıkları Yöneticisi**. Bununla birlikte, dağıtılacak çok sayıda kod olması ya da daha yaygın olarak dağıtmak istiyorsanız, kod parçacığı dosyanızı bir Visual Studio uzantısına dahil etme. Visual Studio kullanıcılarına, uzantıyı daha sonra yükleyebilirsiniz.

Visual Studio uzantıları oluşturmak için Visual Studio SDK'yı yüklemeniz gerekir. Visual Studio yüklemenizle eşleşen VSSDK sürümünü bulun [Visual Studio indirmeleri](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017).

## <a name="set-up-the-extension"></a>Uzantı ayarlayın

Bu yordamda oluşturulan Hello World kod parçacığını kullanacağız [izlenecek yol: bir kod parçacığı oluşturma](../ide/walkthrough-creating-a-code-snippet.md). Biz verin *.snippet* geri dönün ve bir yapmak zorunda kalmamak için metin.

1. Adlı yeni bir VSIX projesi oluşturun **TestSnippet**. (**Dosya** > **yeni** > **proje** > **Visual C# (veya Visual Basic)**  >  **Genişletilebilirlik**.)

2. İçinde **TestSnippet** proje, yeni bir XML dosyası ekleyin ve onu çağırmak *VBCodeSnippet.snippet*. İçerik, aşağıdaki XML ile değiştirin:

    ```xml
    <?xml version="1.0" encoding="utf-8"?>
    <CodeSnippets
        xmlns="http://schemas.microsoft.com/VisualStudio/2005/CodeSnippet">
      <CodeSnippet Format="1.0.0">
        <Header>
          <Title>Hello World VB</Title>
          <Shortcut>HelloWorld</Shortcut>
          <Description>Inserts code</Description>
          <Author>MSIT</Author>
          <SnippetTypes>
            <SnippetType>Expansion</SnippetType>
            <SnippetType>SurroundsWith</SnippetType>
          </SnippetTypes>
        </Header>
        <Snippet>
          <Code Language="VB">
            <![CDATA[Console.WriteLine("Hello, World!")]]>
          </Code>
        </Snippet>
      </CodeSnippet>
    </CodeSnippets>
    ```

### <a name="set-up-the-directory-structure"></a>Dizin yapısını oluşturma

1. İçinde **Çözüm Gezgini**, proje düğümünü seçin ve üzerindeki kod parçacığı, istediğiniz ada sahip bir klasör eklemek **kod parçacıkları Yöneticisi**. Bu durumda, olmalıdır **HelloWorldVB**.

2. Taşıma *.snippet* dosyasını *HelloWorldVB* klasör.

3. Seçin *.snippet* dosyası **Çözüm Gezgini**hem de **özellikleri** penceresi emin olun **derleme eylemi** içinayarlanmış**İçerik**, **çıkış dizinine Kopyala** ayarlanır **her zaman Kopyala**, ve **VSIX Ekle** ayarlanır **true**.

### <a name="add-the-pkgdef-file"></a>.Pkgdef dosyası ekleyin

1. Bir metin dosyasına ekleme *HelloWorldVB* klasörünü adlandırın *HelloWorldVB.pkgdef*. Bu dosya, belirli anahtarlar kayıt defterinde eklemek için kullanılır. Bu durumda, yeni bir alt anahtar ekler **HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\15.0\Languages\CodeExpansions\Basic** anahtarı.

2. Dosyasına aşağıdaki satırları ekleyin.

    ```txt
    // Visual Basic
    [$RootKey$\Languages\CodeExpansions\Basic\Paths]
    "HelloWorldVB"="$PackageFolder$"
    ```

    Bu anahtar incelerseniz, farklı dillerde belirleme görebilirsiniz.

3. Seçin *.pkgdef* dosyası **Çözüm Gezgini**hem de **özellikleri** penceresi emin olun:

   - **Derleme eylemi** ayarlanır **içerik**
   - **Çıkış Dizinine Kopyala** ayarlanır **her zaman Kopyala**
   - **VSIX'e Ekle** ayarlanır **true**

4. Ekleme *.pkgdef* VSIX bildirimi bir varlığı olarak dosya. İçinde *source.extension.vsixmanifest* dosya, Git **varlıklar** sekmesine **yeni**.

5. İçinde **yeni varlık Ekle** iletişim kutusunda, kümesi **türü** için **Microsoft.VisualStudio.VsPackage**, **kaynak** için **dosya çubuğunda dosya sistemi**ve **yolu** için **HelloWorldVB.pkgdef** (hangi açılır listede görüntülenecek).

### <a name="test-the-snippet"></a>Kod parçacığını test

1. Artık kod parçacığının Visual Studio'nun deneysel örneğinde çalıştığından emin olmak. Deneysel örneği, Visual Studio'nun kod yazmak için kullandığınız diskten ayrı olan ikinci bir kopyasıdır. Uzantı üzerinde geliştirme ortamınızı etkilemeden çalışmanıza olanak sağlar.

2. Projeyi oluşturmak ve hata ayıklamaya başlayın.

   Visual Studio ikinci bir örneğini görünür.

3. Deneysel örneğinde Git **Araçları** > **kod parçacıkları Yöneticisi** ayarlayıp **dil** için **temel**. Görmelisiniz *HelloWorldVB* klasörler için ve biri görmek için klasörü genişletmek mümkün olması gerektiği gibi *HelloWorldVB* kod parçacığı.

4. Kod parçacığını test edin. Deneysel örneğinde, bir Visual Basic projesi açın ve kod dosyalarından birini açın. İmleci kodda bir yere yerleştirinceye sağ tıklatın ve bağlam menüsünü seçin **parçacık Ekle**.

5. Görmelisiniz *HelloWorldVB* klasörlerden biri olarak. Çift tıklatın. Bir açılır pencere görmeniz gerekir **parçacık Ekle: HelloWorldVB >** bir açılan olan **HelloWorldVB**. Tıklayın **HelloWorldVB** açılır. Dosyaya eklenen aşağıdaki satırı görmeniz gerekir:

    ```vb
    Console.WriteLine("Hello, World!")
    ```

## <a name="see-also"></a>Ayrıca bkz.

- [Kod parçacıkları](../ide/code-snippets.md)