---
title: 'İzlenecek yol: bir içerik türü için bir dosya adı uzantısına bağlama | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - link content type to file name extension
ms.assetid: 21ee64ce-9afe-4b08-94a0-8389cc4dc67c
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 54570ec03788f88f58f14249f200ed2028686c37
ms.sourcegitcommit: ef828606e9758c7a42a2f0f777c57b2d39041ac3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/06/2018
ms.locfileid: "39566759"
---
# <a name="walkthrough-link-a-content-type-to-a-file-name-extension"></a>İzlenecek yol: bir içerik türü için bir dosya adı uzantısına bağlama
Kendi içerik türü tanımlayabilir ve düzenleyici Yönetilen Genişletilebilirlik Çerçevesi (MEF) uzantılarını kullanarak bağlamak için bir dosya adı uzantısı. Bazı durumlarda, dosya adı uzantısı, bir dil hizmeti tarafından zaten tanımlandı. Ancak, MEF ile kullanmak için yine de bunu bir içerik türüyle bağlamanız gerekir.  
  
## <a name="prerequisites"></a>Önkoşullar  
 Visual Studio 2015'ten başlayarak, Visual Studio SDK İndirme Merkezi'nden yüklemeyin. Visual Studio kurulumunda isteğe bağlı bir özellik eklemiştir. VS SDK'yi daha sonra yükleyebilirsiniz. Daha fazla bilgi için [Visual Studio SDK'yı yükleme](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="create-a-mef-project"></a>MEF proje oluşturma  
  
1.  Bir C# VSIX projesi oluşturun. (İçinde **yeni proje** iletişim kutusunda **Visual C# / genişletilebilirlik**, ardından **VSIX projesi**.) Çözüm adı `ContentTypeTest`.  
  
2.  İçinde **source.extension.vsixmanifest** dosya, Git **varlıklar** sekmesini tıklatıp ayarlamak **türü** alanı **Microsoft.VisualStudio.MefComponent**, **kaynak** alanı **mevcut çözümde bir proje**ve **proje** projesinin adı alanı.  
  
## <a name="define-the-content-type"></a>İçerik türünü tanımlayın  
  
1.  Bir sınıf dosyası ekleyin ve adlandırın `FileAndContentTypes`.  
  
2.  Aşağıdaki derlemelere başvurular ekleyin:  
  
    1.  System.ComponentModel.Composition  
  
    2.  Microsoft.VisualStudio.Text.Logic  
  
    3.  Microsoft.VisualStudio.CoreUtility  
  
3.  Aşağıdaki `using` yönergeleri.  
  
    ```csharp  
    using System.ComponentModel.Composition;  
    using Microsoft.VisualStudio.Text.Classification;  
    using Microsoft.VisualStudio.Utilities;  
  
    ```  
  
4.  Tanımları içeren bir statik sınıf bildirin.  
  
    ```csharp  
    internal static class FileAndContentTypeDefinitions  
    {. . .}  
    ```  
  
5.  Bu sınıf, dışarı aktarma bir <xref:Microsoft.VisualStudio.Utilities.ContentTypeDefinition> "gizlenmiş" adlı ve temel tanımına "metin" olarak bildirin.  
  
    ```csharp  
    internal static class FileAndContentTypeDefinitions  
    {  
        [Export]  
        [Name("hid")]  
        [BaseDefinition("text")]  
        internal static ContentTypeDefinition hidingContentTypeDefinition;  
    }  
    ```  
  
## <a name="link-a-file-name-extension-to-a-content-type"></a>Bir içerik türü için bir dosya adı uzantısına bağlama  
  
-   Bu içerik türü için bir dosya adı uzantısı eşlemek için dışarı aktarma bir <xref:Microsoft.VisualStudio.Utilities.FileExtensionToContentTypeDefinition> uzantısı olan *.hid* ve "gizlenmiş" içerik türü.  
  
    ```csharp  
    internal static class FileAndContentTypeDefinitions  
    {  
         [Export]  
         [Name("hid")]  
         [BaseDefinition("text")]  
        internal static ContentTypeDefinition hidingContentTypeDefinition;  
  
         [Export]  
         [FileExtension(".hid")]  
         [ContentType("hid")]  
        internal static FileExtensionToContentTypeDefinition hiddenFileExtensionDefinition;  
    }  
    ```  
  
## <a name="add-the-content-type-to-an-editor-export"></a>İçerik türü için bir düzenleyici dışarı aktarma Ekle  
  
1.  Düzenleyici uzantısı oluşturun. Örneğin, açıklanan kenar boşluğu glif uzantısı kullanabilirsiniz [izlenecek yol: dış boşluk karakteri oluşturma](../extensibility/walkthrough-creating-a-margin-glyph.md).  
  
2.  Bu yordamda tanımlanan sınıfı ekleyin.  
  
3.  Extension sınıfının dışarı aktardığınızda ekleme bir <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> "kendisine HID" türü.  
  
    ```csharp  
    [Export]  
    [ContentType("hid")]  
    ```  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Dil hizmeti ve düzenleyici uzantı noktaları](../extensibility/language-service-and-editor-extension-points.md)