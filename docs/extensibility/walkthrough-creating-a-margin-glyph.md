---
title: 'İzlenecek yol: dış boşluk karakteri oluşturma | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - margin glyph
ms.assetid: 814185db-24f9-417f-b3b1-7c5aabb42b45
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 1ac8d70c401d543afe73ac14d6f8617e5f375482
ms.sourcegitcommit: 1c2ed640512ba613b3bbbc9ce348e28be6ca3e45
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/03/2018
ms.locfileid: "39497823"
---
# <a name="walkthrough-create-a-margin-glyph"></a>İzlenecek yol: dış boşluk karakteri oluşturma
Özel düzenleyici uzantıları kullanarak, düzenleyici kenar boşlukları görünümünü özelleştirebilirsiniz. "Todo" sözcüğü kod açıklamada göründüğü her durumda bu kılavuzda bir özel karakter gösterge kenar boşluğu koyar.  
  
## <a name="prerequisites"></a>Önkoşullar  
 Visual Studio 2015'ten başlayarak, Visual Studio SDK İndirme Merkezi'nden yüklemeyin. Visual Studio kurulumunda isteğe bağlı bir özellik eklemiştir. VS SDK'yi daha sonra yükleyebilirsiniz. Daha fazla bilgi için [Visual Studio SDK'yı yükleme](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="create-a-mef-project"></a>MEF proje oluşturma  
  
1.  Bir C# VSIX projesi oluşturun. (İçinde **yeni proje** iletişim kutusunda **Visual C# / genişletilebilirlik**, ardından **VSIX projesi**.) Çözüm adı `TodoGlyphTest`.  
  
2.  Bir düzenleyici sınıflandırıcı proje öğesi ekleyin. Daha fazla bilgi için [bir düzenleyici öğesi şablonuyla uzantı oluşturma](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
3.  Varolan sınıf dosyaları silin.  
  
## <a name="define-the-glyph"></a>Glif tanımlayın  
 Glif çalıştırarak tanımlamak <xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactory> arabirimi.  
  
### <a name="to-define-the-glyph"></a>Glif tanımlamak için  
  
1.  Bir sınıf dosyası ekleyin ve adlandırın `TodoGlyphFactory`.  
  
2.  Bildirimleri kullanarak aşağıdaki kodu ekleyin.  
  
     [!code-csharp[VSSDKTodoGlyphTest#1](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_1.cs)]
     [!code-vb[VSSDKTodoGlyphTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_1.vb)]  
  
3.  Adlı bir sınıf ekleyin `TodoGlyphFactory` uygulayan <xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactory>.  
  
     [!code-csharp[VSSDKTodoGlyphTest#2](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_2.cs)]
     [!code-vb[VSSDKTodoGlyphTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_2.vb)]  
  
4.  Karakter boyutları tanımlayan özel bir alan ekleyin.  
  
     [!code-csharp[VSSDKTodoGlyphTest#3](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_3.cs)]
     [!code-vb[VSSDKTodoGlyphTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_3.vb)]  
  
5.  Uygulama `GenerateGlyph` tanımlayarak karakter kullanıcı arabirimi (UI) öğesi. `TodoTag` Bu yönergelerin ilerleyen bölümünde tanımlanır.  
  
     [!code-csharp[VSSDKTodoGlyphTest#4](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_4.cs)]
     [!code-vb[VSSDKTodoGlyphTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_4.vb)]  
  
6.  Adlı bir sınıf ekleyin `TodoGlyphFactoryProvider` uygulayan <xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactoryProvider>. Bu sınıf ile dışarı aktarma bir <xref:Microsoft.VisualStudio.Utilities.NameAttribute> "TodoGlyph", bir <xref:Microsoft.VisualStudio.Utilities.OrderAttribute> VsTextMarker, sonra bir <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> "kod" ve <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> TodoTag biri.  
  
     [!code-csharp[VSSDKTodoGlyphTest#5](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_5.cs)]
     [!code-vb[VSSDKTodoGlyphTest#5](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_5.vb)]  
  
7.  Uygulama <xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactoryProvider.GetGlyphFactory%2A> örnekleme yöntemi `TodoGlyphFactory`.  
  
     [!code-csharp[VSSDKTodoGlyphTest#6](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_6.cs)]
     [!code-vb[VSSDKTodoGlyphTest#6](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_6.vb)]  
  
## <a name="define-a-todo-tag-and-tagger"></a>Bir Todo etiketi ve etiketlerde tanımlayın  
 Önceki adımlarda tanımlanan kullanıcı Arabirimi öğesi ve gösterge kenar boşluğunu arasındaki ilişkiyi tanımlar. Bir etiket türü ve etiketlerde oluşturun ve etiketlerde sağlayıcısını kullanarak dışarı aktarın.  
  
### <a name="to-define-a-todo-tag-and-tagger"></a>Bir todo etiketi ve etiketlerde tanımlamak için  
  
1.  Projeye yeni bir sınıf dosyası ekleyin ve adlandırın `TodoTagger`.  
  
2.  Aşağıdaki içeri aktarmaları ekleyin.  
  
     [!code-csharp[VSSDKTodoGlyphTest#7](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_7.cs)]
     [!code-vb[VSSDKTodoGlyphTest#7](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_7.vb)]  
  
3.  Adlı bir sınıf ekleyin `TodoTag`.  
  
     [!code-csharp[VSSDKTodoGlyphTest#8](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_8.cs)]
     [!code-vb[VSSDKTodoGlyphTest#8](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_8.vb)]  
  
4.  Adlı sınıfını değiştirmek `TodoTagger` uygulayan <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> türü `TodoTag`.  
  
     [!code-csharp[VSSDKTodoGlyphTest#9](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_9.cs)]
     [!code-vb[VSSDKTodoGlyphTest#9](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_9.vb)]  
  
5.  İçin `TodoTagger` sınıfı için özel alanlar ekleme bir <xref:Microsoft.VisualStudio.Text.Classification.IClassifier> ve sınıflandırma bulunacak metin için yayılır.  
  
     [!code-csharp[VSSDKTodoGlyphTest#10](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_10.cs)]
     [!code-vb[VSSDKTodoGlyphTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_10.vb)]  
  
6.  Sınıflandırıcı ayarlayan bir oluşturucu ekleyin.  
  
     [!code-csharp[VSSDKTodoGlyphTest#11](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_11.cs)]
     [!code-vb[VSSDKTodoGlyphTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_11.vb)]  
  
7.  Uygulama <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A> kapsayan tüm sınıflandırma bulma yöntemi, adları "Açıklama" sözcüğü içerir ve arama metnini metni içerir. Arama metni bulunduğunda, geri yeni bir yield <xref:Microsoft.VisualStudio.Text.Tagging.TagSpan%601> türü `TodoTag`.  
  
     [!code-csharp[VSSDKTodoGlyphTest#12](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_12.cs)]
     [!code-vb[VSSDKTodoGlyphTest#12](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_12.vb)]  
  
8.  Bildirme bir `TagsChanged` olay.  
  
     [!code-csharp[VSSDKTodoGlyphTest#13](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_13.cs)]
     [!code-vb[VSSDKTodoGlyphTest#13](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_13.vb)]  
  
9. Adlı bir sınıf ekleyin `TodoTaggerProvider` uygulayan <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider>ve ile dışarı aktarın bir <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> "kod" ve <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> TodoTag biri.  
  
     [!code-csharp[VSSDKTodoGlyphTest#14](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_14.cs)]
     [!code-vb[VSSDKTodoGlyphTest#14](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_14.vb)]  
  
10. İçeri aktarma <xref:Microsoft.VisualStudio.Text.Classification.IClassifierAggregatorService>.  
  
     [!code-csharp[VSSDKTodoGlyphTest#15](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_15.cs)]
     [!code-vb[VSSDKTodoGlyphTest#15](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_15.vb)]  
  
11. Uygulama <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider.CreateTagger%2A> örnekleme yöntemi `TodoTagger`.  
  
     [!code-csharp[VSSDKTodoGlyphTest#16](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_16.cs)]
     [!code-vb[VSSDKTodoGlyphTest#16](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_16.vb)]  
  
## <a name="build-and-test-the-code"></a>Kod oluşturup test  
 Bu kodu test etmek için TodoGlyphTest Çözümü derleyin ve deneysel örneğinde çalıştırın.  
  
### <a name="to-build-and-test-the-todoglyphtest-solution"></a>Derleme ve TodoGlyphTest çözümü test etmek için  
  
1.  Çözümü oluşturun.  
  
2.  Tuşuna basarak projeyi çalıştırın **F5**. Visual Studio'nun ikinci bir örneğini başlatır.  
  
3.  Belirteç kenar boşluğu gösterildiğini doğrulayın. (Üzerinde **Araçları** menüsünü tıklatın **seçenekleri**. Üzerinde **metin düzenleyici** sayfasında, aşağıdakileri sağlayın **gösterge kenar boşluğunu** seçilir.)  
  
4.  Açıklamaları olan bir kod dosyası açın. "Todo" sözcüğü açıklama bölümlerden birine ekleyin.  
  
5.  Gösterge kenar boşluğunda kod penceresinin sol Koyu mavi anahat açık mavi daire görünür.