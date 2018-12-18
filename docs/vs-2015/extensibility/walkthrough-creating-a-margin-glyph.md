---
title: 'İzlenecek yol: dış boşluk karakteri oluşturma | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], new - margin glyph
ms.assetid: 814185db-24f9-417f-b3b1-7c5aabb42b45
caps.latest.revision: 30
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 172ac543f8777219bb7c5adc94d19e1baeea24e7
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51783213"
---
# <a name="walkthrough-creating-a-margin-glyph"></a>İzlenecek Yol: Dış Boşluk Karakteri Oluşturma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Özel düzenleyici uzantıları kullanarak, düzenleyici kenar boşlukları görünümünü özelleştirebilirsiniz. "Todo" sözcüğü kod açıklamada göründüğü her durumda bu kılavuzda bir özel karakter gösterge kenar boşluğu koyar.  
  
## <a name="prerequisites"></a>Önkoşullar  
 Visual Studio 2015'ten başlayarak, size Visual Studio SDK İndirme Merkezi'nden yüklemeyin. Visual Studio kurulumunda isteğe bağlı bir özellik olarak eklenmiştir. VS SDK'yi daha sonra yükleyebilirsiniz. Daha fazla bilgi için [Visual Studio SDK'sını yükleme](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-mef-project"></a>MEF proje oluşturma  
  
1.  Bir C# VSIX projesi oluşturun. (İçinde **yeni proje** iletişim kutusunda **Visual C# / genişletilebilirlik**, ardından **VSIX projesi**.) Çözüm adı `TodoGlyphTest`.  
  
2.  Bir düzenleyici sınıflandırıcı proje öğesi ekleyin. Daha fazla bilgi için [bir düzenleyici öğesi şablonuyla uzantı oluşturma](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
3.  Varolan sınıf dosyaları silin.  
  
## <a name="defining-the-glyph"></a>Glif tanımlama  
 Glif uygulayarak tanımlama <xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactory> arabirimi.  
  
#### <a name="to-define-the-glyph"></a>Glif tanımlamak için  
  
1.  Bir sınıf dosyası ekleyin ve adlandırın `TodoGlyphFactory`.  
  
2.  Aşağıdaki bildirimi kullanarak.  
  
     [!code-csharp[VSSDKTodoGlyphTest#1](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todoglyphfactory.cs#1)]
     [!code-vb[VSSDKTodoGlyphTest#1](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todoglyphfactory.vb#1)]  
  
3.  Adlı bir sınıf ekleyin `TodoGlyphFactory` uygulayan <xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactory>.  
  
     [!code-csharp[VSSDKTodoGlyphTest#2](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todoglyphfactory.cs#2)]
     [!code-vb[VSSDKTodoGlyphTest#2](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todoglyphfactory.vb#2)]  
  
4.  Karakter boyutları tanımlayan özel bir alan ekleyin.  
  
     [!code-csharp[VSSDKTodoGlyphTest#3](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todoglyphfactory.cs#3)]
     [!code-vb[VSSDKTodoGlyphTest#3](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todoglyphfactory.vb#3)]  
  
5.  Uygulama `GenerateGlyph` tanımlayarak karakter kullanıcı arabirimi (UI) öğesi. `TodoTag` Bu yönergelerin ilerleyen bölümünde tanımlanır.  
  
     [!code-csharp[VSSDKTodoGlyphTest#4](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todoglyphfactory.cs#4)]
     [!code-vb[VSSDKTodoGlyphTest#4](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todoglyphfactory.vb#4)]  
  
6.  Adlı bir sınıf ekleyin `TodoGlyphFactoryProvider` uygulayan <xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactoryProvider>. Bu sınıf ile dışarı aktarma bir <xref:Microsoft.VisualStudio.Utilities.NameAttribute> "TodoGlyph", bir <xref:Microsoft.VisualStudio.Utilities.OrderAttribute> VsTextMarker, sonra bir <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> "kod" ve <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> TodoTag biri.  
  
     [!code-csharp[VSSDKTodoGlyphTest#5](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todoglyphfactory.cs#5)]
     [!code-vb[VSSDKTodoGlyphTest#5](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todoglyphfactory.vb#5)]  
  
7.  Uygulama <xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactoryProvider.GetGlyphFactory%2A> örnekleme yöntemi `TodoGlyphFactory`.  
  
     [!code-csharp[VSSDKTodoGlyphTest#6](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todoglyphfactory.cs#6)]
     [!code-vb[VSSDKTodoGlyphTest#6](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todoglyphfactory.vb#6)]  
  
## <a name="defining-a-todo-tag-and-tagger"></a>Bir Todo etiketi ve etiketlerde tanımlama  
 Bir etiket türü ve etiketlerde oluşturarak ve etiketlerde sağlayıcısını kullanarak dışarı aktarma önceki adımlarda tanımlanan kullanıcı Arabirimi öğesi ve gösterge kenar boşluğunu arasındaki ilişkiyi tanımlar.  
  
#### <a name="to-define-a-todo-tag-and-tagger"></a>Bir todo etiketi ve etiketlerde tanımlamak için  
  
1.  Projeye yeni bir sınıf dosyası ekleyin ve adlandırın `TodoTagger`.  
  
2.  Aşağıdaki içeri aktarmaları ekleyin.  
  
     [!code-csharp[VSSDKTodoGlyphTest#7](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs#7)]
     [!code-vb[VSSDKTodoGlyphTest#7](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb#7)]  
  
3.  Adlı bir sınıf ekleyin `TodoTag`.  
  
     [!code-csharp[VSSDKTodoGlyphTest#8](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs#8)]
     [!code-vb[VSSDKTodoGlyphTest#8](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb#8)]  
  
4.  Adlı sınıfını değiştirmek `TodoTagger` uygulayan <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> türü `TodoTag`.  
  
     [!code-csharp[VSSDKTodoGlyphTest#9](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs#9)]
     [!code-vb[VSSDKTodoGlyphTest#9](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb#9)]  
  
5.  İçin `TodoTagger` sınıfı için özel alanlar ekleme bir <xref:Microsoft.VisualStudio.Text.Classification.IClassifier> ve sınıflandırma bulunacak metin için yayılır.  
  
     [!code-csharp[VSSDKTodoGlyphTest#10](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs#10)]
     [!code-vb[VSSDKTodoGlyphTest#10](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb#10)]  
  
6.  Sınıflandırıcı ayarlayan bir oluşturucu ekleyin.  
  
     [!code-csharp[VSSDKTodoGlyphTest#11](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs#11)]
     [!code-vb[VSSDKTodoGlyphTest#11](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb#11)]  
  
7.  Uygulama <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A> kapsayan tüm sınıflandırma bulma yöntemi, adları "Açıklama" sözcüğü içerir ve arama metnini metni içerir. Arama metni bulunduğunda, geri yeni bir yield <xref:Microsoft.VisualStudio.Text.Tagging.TagSpan%601> türü `TodoTag`.  
  
     [!code-csharp[VSSDKTodoGlyphTest#12](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs#12)]
     [!code-vb[VSSDKTodoGlyphTest#12](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb#12)]  
  
8.  Bildirme bir `TagsChanged` olay.  
  
     [!code-csharp[VSSDKTodoGlyphTest#13](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs#13)]
     [!code-vb[VSSDKTodoGlyphTest#13](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb#13)]  
  
9. Adlı bir sınıf ekleyin `TodoTaggerProvider` uygulayan <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider>ve ile dışarı aktarın bir <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> "kod" ve <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> TodoTag biri.  
  
     [!code-csharp[VSSDKTodoGlyphTest#14](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs#14)]
     [!code-vb[VSSDKTodoGlyphTest#14](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb#14)]  
  
10. İçeri aktarma <xref:Microsoft.VisualStudio.Text.Classification.IClassifierAggregatorService>.  
  
     [!code-csharp[VSSDKTodoGlyphTest#15](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs#15)]
     [!code-vb[VSSDKTodoGlyphTest#15](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb#15)]  
  
11. Uygulama <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider.CreateTagger%2A> örnekleme yöntemi `TodoTagger`.  
  
     [!code-csharp[VSSDKTodoGlyphTest#16](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs#16)]
     [!code-vb[VSSDKTodoGlyphTest#16](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb#16)]  
  
## <a name="building-and-testing-the-code"></a>Oluşturma ve kod test etme  
 Bu kodu test etmek için TodoGlyphTest Çözümü derleyin ve deneysel örneğinde çalıştırın.  
  
#### <a name="to-build-and-test-the-todoglyphtest-solution"></a>Derleme ve TodoGlyphTest çözümü test etmek için  
  
1.  Çözümü oluşturun.  
  
2.  F5 tuşuna basarak projeyi çalıştırın. Visual Studio'nun ikinci bir örneği oluşturulur.  
  
3.  Belirteç kenar boşluğu gösterildiğini doğrulayın. (Üzerinde **Araçları** menüsünü tıklatın **seçenekleri**. Üzerinde **metin düzenleyici** sayfasında, aşağıdakileri sağlayın **gösterge kenar boşluğunu** seçilir.)  
  
4.  Açıklamaları olan bir kod dosyası açın. "Todo" sözcüğü açıklama bölümlerden birine ekleyin.  
  
5.  Koyu mavi anahat sahip bir açık mavi daireye gösterge kenar boşluğunda kod penceresinin sol görüntülenmesi gerekir.

