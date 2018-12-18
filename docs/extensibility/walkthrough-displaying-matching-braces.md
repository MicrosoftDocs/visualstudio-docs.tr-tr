---
title: 'İzlenecek yol: Eşleşen küme ayraçlarını görüntüleme | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - brace matching
ms.assetid: 5af08ac7-1d08-4ccf-997e-01aa6cb3d3d7
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 1f29596c95646db78145725f1f0cead424e1de5e
ms.sourcegitcommit: 1c2ed640512ba613b3bbbc9ce348e28be6ca3e45
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/03/2018
ms.locfileid: "39500442"
---
# <a name="walkthrough-display-matching-braces"></a>İzlenecek yol: eşleşen küme ayraçlarını görüntüleme
Ayraç eşleştirme eşleştirmek istediğiniz küme ayraçları tanımlayıp giriş işaretini bir küme ayraçlarının olduğunda eşleşen ayraçlar için bir metin işaretçisi etiket ekleme gibi dil tabanlı özellikler uygular. Küme ayraçları bir dil bağlamında tanımlayın, kendi dosya adı uzantısı ve içerik türünü tanımlayın ve etiketleri yalnızca yazın ya da mevcut bir içerik türüyle (örneğin, "metin") etiketler uygulayın. Aşağıdaki örneklerde, ayraç eşleştirme "metin" içerik türü etiketleri uygulamak gösterilmektedir.  
  
## <a name="prerequisites"></a>Önkoşullar  
 Visual Studio 2015'ten başlayarak, Visual Studio SDK İndirme Merkezi'nden yüklemeyin. Visual Studio kurulumunda isteğe bağlı bir özellik eklemiştir. VS SDK'yi daha sonra yükleyebilirsiniz. Daha fazla bilgi için [Visual Studio SDK'yı yükleme](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="create-a-managed-extensibility-framework-mef-project"></a>Yönetilen Genişletilebilirlik Çerçevesi (MEF) proje oluşturma  
  
#### <a name="to-create-a-mef-project"></a>MEF projesi oluşturmak için  
  
1.  Bir düzenleyici sınıflandırıcı projesi oluşturun. Çözüm adı `BraceMatchingTest`.  
  
2.  Bir düzenleyici sınıflandırıcı öğe şablonu, projeye ekleyin. Daha fazla bilgi için [bir düzenleyici öğesi şablonuyla uzantı oluşturma](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
3.  Varolan sınıf dosyaları silin.  
  
## <a name="implement-a-brace-matching-tagger"></a>Etiketlerde eşlemesi uygulayın  
 Visual Studio'da kullanılan benzer etkisi vurgulama ayraç almak için türü bir etiketlerde uygulayabileceğiniz <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>. Aşağıdaki kod, iç içe geçme herhangi bir düzeyde küme ayracı çiftleri için etiketlerde tanımlamak gösterilmektedir. Bu örnekte, küme ayracı çiftleri [] ve {} etiketlerde oluşturucusu, ancak ilgili küme ayracı çiftleri dil belirtiminde tanımlanmış bir tam dil uygulaması tanımlanır.  
  
### <a name="to-implement-a-brace-matching-tagger"></a>Etiketlerde eşlemesi uygulamak için  
  
1.  Bir sınıf dosyası ekleyin ve BraceMatching adlandırın.  
  
2.  Aşağıdaki ad alanlarını içeri aktarın.  
  
     [!code-csharp[VSSDKBraceMatchingTest#1](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_1.cs)]
     [!code-vb[VSSDKBraceMatchingTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_1.vb)]  
  
3.  Bir sınıf tanımlama `BraceMatchingTagger` öğesinden devralan <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> türü <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>.  
  
     [!code-csharp[VSSDKBraceMatchingTest#2](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_2.cs)]
     [!code-vb[VSSDKBraceMatchingTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_2.vb)]  
  
4.  Metin görünümünü, kaynak arabelleği, geçerli anlık görüntü noktası ve ayrıca küme ayracı çiftleri kümesini özellikleri ekleyin.  
  
     [!code-csharp[VSSDKBraceMatchingTest#3](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_3.cs)]
     [!code-vb[VSSDKBraceMatchingTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_3.vb)]  
  
5.  Etiketlerde oluşturucuda özellikleri ayarlayın ve görünüm değişiklik olaylara abone <xref:Microsoft.VisualStudio.Text.Editor.ITextCaret.PositionChanged> ve <xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged>. Bu örnekte, yalnızca tanım amaçlıdır için eşleşen çiftleri de oluşturucu içinde tanımlanır.  
  
     [!code-csharp[VSSDKBraceMatchingTest#4](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_4.cs)]
     [!code-vb[VSSDKBraceMatchingTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_4.vb)]  
  
6.  Bir parçası olarak <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> uygulaması TagsChanged olay bildirin.  
  
     [!code-csharp[VSSDKBraceMatchingTest#5](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_5.cs)]
     [!code-vb[VSSDKBraceMatchingTest#5](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_5.vb)]  
  
7.  Geçerli giriş işareti konumuna olay işleyicileri güncelleştirme `CurrentChar` özelliği ve raise TagsChanged olay.  
  
     [!code-csharp[VSSDKBraceMatchingTest#6](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_6.cs)]
     [!code-vb[VSSDKBraceMatchingTest#6](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_6.vb)]  
  
8.  Uygulama <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A> eşleştirilecek yöntemi ayraçları ya da geçerli karakteri açık bir ayraç veya önceki karakteri bir kapatma ayracı, Visual Studio olduğu gibi olduğunda olduğunda. Eşleşme bulunduğunda, bu yöntem için açık küme ayracı biri diğeri için kapatma ayracı iki etiket örneği oluşturur.  
  
     [!code-csharp[VSSDKBraceMatchingTest#7](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_7.cs)]
     [!code-vb[VSSDKBraceMatchingTest#7](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_7.vb)]  
  
9. Aşağıdaki özel yöntemler, eşleşen Ayraca iç içe geçme herhangi bir düzeyde bulun. İlk yöntem, açık bir karakterle eşleşir Kapat karakteri bulur:  
  
     [!code-csharp[VSSDKBraceMatchingTest#8](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_8.cs)]
     [!code-vb[VSSDKBraceMatchingTest#8](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_8.vb)]  
  
10. Aşağıdaki yardımcı yöntemini Kapat bir karakterle eşleşir açık karakteri bulur:  
  
     [!code-csharp[VSSDKBraceMatchingTest#9](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_9.cs)]
     [!code-vb[VSSDKBraceMatchingTest#9](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_9.vb)]  
  
## <a name="implement-a-brace-matching-tagger-provider"></a>Ayraç eşleştirme etiketlerde sağlayıcıyı uygulama  
 Bir etiketlerde uygulamadan ek olarak, ayrıca uygulamak ve gerekir etiketlerde sağlayıcısı dışarı aktarın. Bu durumda, içerik türü sağlayıcının "metin" dir. Bu nedenle, ayraç eşleştirme metin dosyalarının tüm türlerin görünür, ancak bir bileşen uygulaması Ayraç eşleştirme yalnızca belirli bir içerik türüne uygulanır.  
  
### <a name="to-implement-a-brace-matching-tagger-provider"></a>Ayraç eşleştirme etiketlerde sağlayıcısını uygulamak için  
  
1.  Devralınan bir etiketlerde sağlayıcısı bildirimini <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider>BraceMatchingTaggerProvider adlandırın ve ile dışarı aktarın bir <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> "metin" ve <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> , <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>.  
  
     [!code-csharp[VSSDKBraceMatchingTest#10](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_10.cs)]
     [!code-vb[VSSDKBraceMatchingTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_10.vb)]  
  
2.  Uygulama <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider.CreateTagger%2A> bir BraceMatchingTagger örneklemek için yöntemi.  
  
     [!code-csharp[VSSDKBraceMatchingTest#11](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_11.cs)]
     [!code-vb[VSSDKBraceMatchingTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_11.vb)]  
  
## <a name="build-and-test-the-code"></a>Kod oluşturup test  
 Bu kodu test etmek için BraceMatchingTest Çözümü derleyin ve deneysel örneğinde çalıştırın.  
  
#### <a name="to-build-and-test-bracematchingtest-solution"></a>Derleme ve BraceMatchingTest çözümü test etmek için  
  
1.  Çözümü oluşturun.  
  
2.  Bu projede hata ayıklayıcıda çalıştırdığınızda, Visual Studio'nun ikinci bir örneğini başlatılır.  
  
3.  Bir metin dosyası oluşturun ve eşleşen küme ayraçlarını içeren bir metin yazın.  
  
    ```  
    hello {  
    goodbye}  
  
    {}  
  
    {hello}  
    ```  
  
4.  Giriş işaretini bir açık ayraç önce getirdiğinizde, küme ayracı hem de eşleşen kapatma ayracı vurgulanmış olmalıdır. Yalnızca kapatma küme ayracından sonra işaretçiyi getirdiğinizde, küme ayracı hem de eşleşen açık küme ayracı vurgulanmış olmalıdır.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [İzlenecek yol: bir içerik türü için bir dosya adı uzantısına bağlama](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)