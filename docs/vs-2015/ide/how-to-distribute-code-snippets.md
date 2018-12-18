---
title: 'Nasıl yapılır: kod parçacıklarını dağıtma | Microsoft Docs'
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
- code snippets, distributing
ms.assetid: 5f717abd-e167-47ae-818c-6b0bae100ceb
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 14dea3842289b626b79d8dc7e294ba5f335d0351
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49185711"
---
# <a name="how-to-distribute-code-snippets"></a>Nasıl Yapılır: Kod Parçacıklarını Dağıtma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Yalnızca, kod parçacıklarınız arkadaşlarınıza verebilir ve bunları kod parçacıkları Yöneticisi'ni kullanarak kendi bilgisayarlarındaki parçacıkları yükleyin. Bununla birlikte, dağıtılacak çok sayıda kod olması ya da daha yaygın olarak dağıtmak istiyorsanız, Visual Studio kullanıcıları yükleyebilmeniz için Visual Studio uzantısı kod parçacığı dosyanızı içerir.  
  
 Visual Studio uzantıları oluşturmak için Visual Studio SDK'yı yüklemeniz gerekir. Visual Studio yüklemenizle eşleşen VSSDK sürümünü bulun [Visual Studio 2015 indirmeleri](http://www.visualstudio.com/downloads/visual-studio-2015-downloads-vs.aspx).  
  
## <a name="setting-up-the-extension"></a>Uzantı ayarlama  
 Bu yordamda oluşturulan Hello World kod parçacığını kullanacağız [izlenecek yol: kod parçacığı oluşturma](../ide/walkthrough-creating-a-code-snippet.md). Geri dönün ve bir yapmak zorunda kalmamak için Biz .snippet metin kullanacaksınız.  
  
1.  Adlı yeni bir VSIX projesi oluşturun **TestSnippet**. (**Dosya / yeni / Project / Visual C# (veya Visual Basic / genişletilebilirlik**)  
  
2.  İçinde **TestSnippet** proje, yeni bir XML dosyası ekleyin ve onu çağırmak **VBCodeSnippet.snippet**. İçeriği aşağıdakiyle değiştirin:  
  
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
  
#### <a name="setting-up-the-directory-structure"></a>Dizin yapısı kurma  
  
1.  Çözüm Gezgini'nde proje düğümünü seçin ve kod parçacığını kod parçacıkları Yöneticisi'nde olmasını istediğiniz ada sahip bir klasör ekleyin. Bu durumda olmalıdır **HelloWorldVB**.  
  
2.  .Snippet dosyasına taşımak **HelloWorldVB** klasör.  
  
3.  .Snippet dosyasını seçin ve Çözüm Gezgini'nde **özellikleri** penceresi emin olun **derleme eylemi** ayarlanır **içerik**, **çıktıya Kopyala Dizin** ayarlanır **her zaman Kopyala**, ve **VSIX Ekle** ayarlanır **true**.  
  
#### <a name="adding-the-pkgdef-file"></a>.Pkgdef dosyası ekleme  
  
1.  Bir metin dosyasına ekleme **HelloWorldVB** klasörünü adlandırın **HelloWorldVB.pkgdef**. Bu dosya, belirli anahtarlar kayıt defterinde eklemek için kullanılır. Bu durumda, yeni bir anahtara ekler.  
  
     **HKCU\Software\Microsoft\VisualStudio\14.0\Languages\CodeExpansions\Basic**.  
  
2.  Dosyasına aşağıdaki satırları ekleyin.  
  
    ```  
    // Visual Basic   
    [$RootKey$\Languages\CodeExpansions\Basic\Paths]   
    "HelloWorldVB"="$PackageFolder$"  
    ```  
  
     Bu anahtar incelerseniz, farklı dillerde belirleme görebilirsiniz.  
  
3.  .Pkgdef dosyası seçin ve Çözüm Gezgini'nde **özellikleri** penceresi emin olun **derleme eylemi** ayarlanır **içerik**, **çıkış dizinine Kopyala**  ayarlanır **her zaman Kopyala**, ve **VSIX Ekle** ayarlanır **true**.  
  
4.  VSIX bildirimi bir varlığı olarak .pkgdef dosyası ekleyin. Source.extension.vsixmanifest dosyası içinde Git **varlıklar** sekmesine **yeni**.  
  
5.  İçinde **yeni varlık Ekle** iletişim kutusunda, kümesi **türü** için **Microsoft.VisualStudio.VsPackage**, **türü** için **dosya çubuğunda dosya sistemi**ve **yolu** için **HelloWorldVB.pkgdef** (hangi açılır listede görüntülenecek).  
  
### <a name="testing-the-snippet"></a>Kod parçacığını test etme  
  
1.  Artık kod parçacığının Visual Studio'nun deneysel örneğinde çalıştığından emin olmak. Deneysel örneği, Visual Studio'nun kod yazmak için kullandığınız diskten ayrı olan ikinci bir kopyasıdır. Uzantı üzerinde geliştirme ortamınızı etkilemeden çalışmanıza olanak sağlar.  
  
2.  Projeyi oluşturmak ve hata ayıklamaya başlayın. Visual Studio ikinci bir örneğini görüntülenmesi gerekir.  
  
3.  Deneysel örneğinde Git **Araçlar / kod parçacıkları Yöneticisi** ayarlayıp **dil** için **temel**. Klasörleri biri olarak HelloWorldVB görmeniz gerekir ve HelloWorldVB kod parçacığı görmek için klasörü genişletmek mümkün olması gerekir.  
  
4.  Kod parçacığını test edin. Deneysel örneğinde, bir Visual Basic projesi açın ve kod dosyalarından birini açın. İmleci kodda bir yere yerleştirinceye sağ tıklatın ve bağlam menüsünü seçin **parçacık Ekle**.  
  
5.  HelloWorldVB klasörlerden biri görmeniz gerekir. Çift tıklatın. Bir açılır pencere görmeniz gerekir **parçacık Ekle: HellowWorldVB >** bir açılan olan **HelloWorldVB**. HelloWorldVB açılır menüyü tıklayın. Dosyaya eklenen aşağıdaki satırı görmeniz gerekir:  
  
    ```vb  
    Console.WriteLine("Hello, World!")  
    ```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Kod Parçacıkları](../ide/code-snippets.md)



