---
title: 'Nasıl yapılır: kod parçacıklarını dağıtma | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- code snippets, distributing
ms.assetid: 5f717abd-e167-47ae-818c-6b0bae100ceb
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: e1a692ee29ea9d43e1a0a4fbed5c52934d69256d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "77476979"
---
# <a name="how-to-distribute-code-snippets"></a>Nasıl Yapılır: Kod Parçacıklarını Dağıtma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Yalnızca kod parçacıklarını Arkadaşlarınıza verebilir ve kod parçacıkları Yöneticisi 'Ni kullanarak kendi bilgisayarlarına kod parçacıklarını yükleyebilirsiniz. Ancak, dağıtılacak birkaç kod parçacığı varsa veya bunları daha yaygın olarak dağıtmak istiyorsanız, kod parçacığı dosyanızı Visual Studio kullanıcılarının yükleyebileceği bir Visual Studio uzantısına dahil edersiniz.

 Visual Studio uzantıları oluşturmak için Visual Studio SDK 'sını yüklemelisiniz. Visual [studio 2015 Indirmelerinde](https://visualstudio.microsoft.com/vs/older-downloads/)Visual Studio yüklemenize uyan VSSDK sürümünü bulun.

## <a name="setting-up-the-extension"></a>Uzantıyı ayarlama
 Bu yordamda, [Izlenecek yol: kod parçacığı oluşturma](../ide/walkthrough-creating-a-code-snippet.md)bölümünde oluşturulan Merhaba Dünya kod parçacığını kullanacağız. . Kod parçacığı metnini sağlayacağız, bu yüzden geri dönüp bir tane yapmanız gerekmez.

1. **Testparçacığında**adlı yenı bir VSIX projesi oluşturun. (**Dosya/yeni/proje/Visual C# (veya Visual Basic/genişletilebilirlik**)

2. **Testparçacığının** projesinde yenı bir XML dosyası ekleyin ve bu dosyayı **vbcodeparçacığın. parçacığını**çağırın. İçeriği aşağıdaki kodla değiştirin:

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

#### <a name="setting-up-the-directory-structure"></a>Dizin yapısını ayarlama

1. Çözüm Gezgini, proje düğümünü seçin ve kod parçacıkları yöneticisinde, kod parçacığında olmasını istediğiniz ada sahip bir klasör ekleyin. Bu durumda, **Merhaba Worldvb**olmalıdır.

2. . Parçacığının dosyasını **HelloWorldVB** klasörüne taşıyın.

3. Çözüm Gezgini. kod parçacığı dosyasını seçin ve **Özellikler** penceresinde **derleme eyleminin** **içerik**olarak ayarlandığından emin olun, **Çıkış Dizinine Kopyala** özelliği **her zaman Kopyala**olarak ayarlanır ve **VSIX 'e dahil et** özelliği **true**olarak ayarlanır.

#### <a name="adding-the-pkgdef-file"></a>. Pkgdef dosyasını ekleme

1. **Merhaba worldvb** klasörüne bir metin dosyası ekleyin ve **Merhaba worldvb. pkgdef**olarak adlandırın. Bu dosya, kayıt defterine belirli anahtarlar eklemek için kullanılır. Bu durumda, öğesine yeni bir anahtar ekler

     **Hkcu\software\microsoft\visualstudio\14.0\languages\codeexpansions\basic**.

2. Dosyasına aşağıdaki satırları ekleyin.

    ```
    // Visual Basic
    [$RootKey$\Languages\CodeExpansions\Basic\Paths]
    "HelloWorldVB"="$PackageFolder$"
    ```

     Bu anahtarı incelerseniz, farklı dillerin nasıl gösterileceğini görebilirsiniz.

3. Çözüm Gezgini. pkgdef dosyasını seçin ve **Özellikler** penceresinde **derleme eyleminin** **içerik**olarak ayarlandığından emin olun, **Çıkış Dizinine Kopyala** özelliği **her zaman Kopyala**olarak ayarlanır ve **VSIX 'e dahil et** özelliği **true**olarak ayarlanır.

4. . Pkgdef dosyasını VSıX bildiriminde bir varlık olarak ekleyin. Source. Extension. valtmanifest dosyasında, **varlıklar** sekmesine gidin ve **Yeni**' ye tıklayın.

5. **Yeni varlık Ekle** iletişim kutusunda, **türü** **Microsoft. VisualStudio. VSPackage**, **FileSystem üzerinde dosya** **türüne** ve **HelloWorldVB. pkgdef** **yolunu** (açılan menüde görünmelidir) ayarlayın.

### <a name="testing-the-snippet"></a>Kod parçacığını test etme

1. Artık kod parçacığının Visual Studio 'nun deneysel örneğinde çalıştığından emin olabilirsiniz. Deneysel örnek, Visual Studio 'nun kod yazmak için kullandığınız bir ikinci kopyasıdır. Geliştirme ortamınızı etkilemeden bir uzantı üzerinde çalışmanıza olanak sağlar.

2. Projeyi derleyin ve hata ayıklamayı başlatın. Visual Studio 'nun ikinci bir örneği görünmelidir.

3. Deneysel örnekte, **Araçlar/kod parçacıkları Yöneticisi** ' ne gidin ve **dili** **temel**olarak ayarlayın. Bir klasörden birine merhaba Worldvb görmeniz gerekir ve Merhaba Worldvb kod parçacığını görmek için klasörü genişletmeniz gerekir.

4. Kod parçacığını test edin. Deneysel örnekte, bir Visual Basic projesi açın ve kod dosyalarından birini açın. İmlecinizi kodda bir yere yerleştirin, sağ tıklayın ve bağlam menüsünde kod **parçacığı Ekle**' yi seçin.

5. Bir klasörden biri olarak Merhaba Worldvb görmeniz gerekir. Çift tıklayın. Açılan bir **ekleme kod parçacığı görmeniz gerekir >: ** bir açılır **Merhaba**çalışma parçacığı. Merhaba Worldvb açılan listesine tıklayın. Dosyasına aşağıdaki satırı eklendiğini görmeniz gerekir:

    ```vb
    Console.WriteLine("Hello, World!")
    ```

## <a name="see-also"></a>Ayrıca Bkz.
 [Kod Parçacıkları](../ide/code-snippets.md)
