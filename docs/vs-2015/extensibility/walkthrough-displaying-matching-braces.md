---
title: 'İzlenecek yol: Eşleşen küme ayraçlarını görüntüleme | Microsoft Docs'
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
- editors [Visual Studio SDK], new - brace matching
ms.assetid: 5af08ac7-1d08-4ccf-997e-01aa6cb3d3d7
caps.latest.revision: 28
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 9795cd3c40eeff714d55f4bb95f78cf1f7f8aea9
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51745882"
---
# <a name="walkthrough-displaying-matching-braces"></a>İzlenecek Yol: Eşleşen Küme Ayraçlarını Görüntüleme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ayraç eşleştirme eşleştirmek istediğiniz küme ayraçları tanımlayıp giriş işaretini bir küme ayraçlarının olduğunda bir metin işaretçisi etiketi için eşleşen küme ayraçlarını ekleme gibi dil tabanlı özellikleri uygulayabilir. Küme ayraçları bir dil bağlamında tanımlayabilirsiniz kendi dosya adı uzantısı ve içerik türünü tanımlayın ve bu türe yalnızca etiketler veya mevcut bir içerik türüyle (örneğin, "metin") etiketler uygulayabilirsiniz. Aşağıdaki örneklerde, ayraç eşleştirme "metin" içerik türü etiketleri uygulamak gösterilmektedir.  
  
## <a name="prerequisites"></a>Önkoşullar  
 Visual Studio 2015'ten başlayarak, size Visual Studio SDK İndirme Merkezi'nden yüklemeyin. Visual Studio kurulumunda isteğe bağlı bir özellik olarak eklenmiştir. VS SDK'yi daha sonra yükleyebilirsiniz. Daha fazla bilgi için [Visual Studio SDK'sını yükleme](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-managed-extensibility-framework-mef-project"></a>Yönetilen Genişletilebilirlik Çerçevesi (MEF) proje oluşturma  
  
#### <a name="to-create-a-mef-project"></a>MEF projesi oluşturmak için  
  
1.  Bir düzenleyici sınıflandırıcı projesi oluşturun. Çözüm adı `BraceMatchingTest`.  
  
2.  Bir düzenleyici sınıflandırıcı öğe şablonu, projeye ekleyin. Daha fazla bilgi için [bir düzenleyici öğesi şablonuyla uzantı oluşturma](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
3.  Varolan sınıf dosyaları silin.  
  
## <a name="implementing-a-brace-matching-tagger"></a>Etiketlerde eşlemesi uygulama  
 Visual Studio'da kullanılan benzer etkisi vurgulama ayraç almak için türü bir etiketlerde uygulayabileceğiniz <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>. Aşağıdaki kod, iç içe geçme herhangi bir düzeyde küme ayracı çiftleri için etiketlerde tanımlamak gösterilmektedir. Bu örnekte, küme ayracı çiftleri [']. [], ve {} etiketlerde oluşturucusu, ancak ilgili küme ayracı çiftleri dil belirtiminde tanımlanmış bir tam dil uygulaması tanımlanır.  
  
#### <a name="to-implement-a-brace-matching-tagger"></a>Etiketlerde eşlemesi uygulamak için  
  
1.  Bir sınıf dosyası ekleyin ve BraceMatching adlandırın.  
  
2.  Aşağıdaki ad alanlarını içeri aktarın.  
  
     [!code-csharp[VSSDKBraceMatchingTest#1](../snippets/csharp/VS_Snippets_VSSDK/vssdkbracematchingtest/cs/bracematching.cs#1)]
     [!code-vb[VSSDKBraceMatchingTest#1](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkbracematchingtest/vb/bracematching.vb#1)]  
  
3.  Bir sınıf tanımlama `BraceMatchingTagger` öğesinden devralan <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> türü <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>.  
  
     [!code-csharp[VSSDKBraceMatchingTest#2](../snippets/csharp/VS_Snippets_VSSDK/vssdkbracematchingtest/cs/bracematching.cs#2)]
     [!code-vb[VSSDKBraceMatchingTest#2](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkbracematchingtest/vb/bracematching.vb#2)]  
  
4.  Metin görünümünü, kaynak arabelleği ve geçerli anlık görüntü noktası ve ayrıca küme ayracı çiftleri kümesini özellikler ekleyin.  
  
     [!code-csharp[VSSDKBraceMatchingTest#3](../snippets/csharp/VS_Snippets_VSSDK/vssdkbracematchingtest/cs/bracematching.cs#3)]
     [!code-vb[VSSDKBraceMatchingTest#3](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkbracematchingtest/vb/bracematching.vb#3)]  
  
5.  Etiketlerde oluşturucuda özellikleri ayarlayın ve görünüm değişiklik olaylara abone <xref:Microsoft.VisualStudio.Text.Editor.ITextCaret.PositionChanged> ve <xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged>. Bu örnekte, yalnızca tanım amaçlıdır için eşleşen çiftleri de oluşturucu içinde tanımlanır.  
  
     [!code-csharp[VSSDKBraceMatchingTest#4](../snippets/csharp/VS_Snippets_VSSDK/vssdkbracematchingtest/cs/bracematching.cs#4)]
     [!code-vb[VSSDKBraceMatchingTest#4](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkbracematchingtest/vb/bracematching.vb#4)]  
  
6.  Bir parçası olarak <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> uygulaması TagsChanged olay bildirin.  
  
     [!code-csharp[VSSDKBraceMatchingTest#5](../snippets/csharp/VS_Snippets_VSSDK/vssdkbracematchingtest/cs/bracematching.cs#5)]
     [!code-vb[VSSDKBraceMatchingTest#5](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkbracematchingtest/vb/bracematching.vb#5)]  
  
7.  Geçerli giriş işareti konumuna olay işleyicileri güncelleştirme `CurrentChar` özelliği ve raise TagsChanged olay.  
  
     [!code-csharp[VSSDKBraceMatchingTest#6](../snippets/csharp/VS_Snippets_VSSDK/vssdkbracematchingtest/cs/bracematching.cs#6)]
     [!code-vb[VSSDKBraceMatchingTest#6](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkbracematchingtest/vb/bracematching.vb#6)]  
  
8.  Uygulama <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A> eşleştirilecek yöntemi ayraçları ya da geçerli karakteri açık bir ayraç veya önceki karakteri bir kapatma ayracı, Visual Studio olduğu gibi olduğunda olduğunda. Eşleşme bulunduğunda, bu yöntem için açık küme ayracı biri diğeri için kapatma ayracı iki etiket örneği oluşturur.  
  
     [!code-csharp[VSSDKBraceMatchingTest#7](../snippets/csharp/VS_Snippets_VSSDK/vssdkbracematchingtest/cs/bracematching.cs#7)]
     [!code-vb[VSSDKBraceMatchingTest#7](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkbracematchingtest/vb/bracematching.vb#7)]  
  
9. Aşağıdaki özel yöntemler, eşleşen Ayraca iç içe geçme herhangi bir düzeyde bulun. İlk yöntem, açık bir karakterle eşleşir Kapat karakteri bulur:  
  
     [!code-csharp[VSSDKBraceMatchingTest#8](../snippets/csharp/VS_Snippets_VSSDK/vssdkbracematchingtest/cs/bracematching.cs#8)]
     [!code-vb[VSSDKBraceMatchingTest#8](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkbracematchingtest/vb/bracematching.vb#8)]  
  
10. Aşağıdaki yardımcı yöntemini Kapat bir karakterle eşleşir açık karakteri bulur:  
  
     [!code-csharp[VSSDKBraceMatchingTest#9](../snippets/csharp/VS_Snippets_VSSDK/vssdkbracematchingtest/cs/bracematching.cs#9)]
     [!code-vb[VSSDKBraceMatchingTest#9](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkbracematchingtest/vb/bracematching.vb#9)]  
  
## <a name="implementing-a-brace-matching-tagger-provider"></a>Etiketlerde sağlayıcısı ile eşleşen bir küme ayracı uygulama  
 Bir etiketlerde uygulamadan ek olarak, ayrıca uygulamak ve gerekir etiketlerde sağlayıcısı dışarı aktarın. Bu durumda, içerik türü sağlayıcının "metin" dir. Bu, ayraç eşleştirme metin dosyalarının tüm türlerin görünür, ancak bir bileşen uygulaması Ayraç eşleştirme yalnızca belirli bir içerik türüne uygulanacak anlamına gelir.  
  
#### <a name="to-implement-a-brace-matching-tagger-provider"></a>Ayraç eşleştirme etiketlerde sağlayıcısını uygulamak için  
  
1.  Devralınan bir etiketlerde sağlayıcısı bildirimini <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider>BraceMatchingTaggerProvider adlandırın ve ile dışarı aktarın bir <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> "metin" ve <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> , <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>.  
  
     [!code-csharp[VSSDKBraceMatchingTest#10](../snippets/csharp/VS_Snippets_VSSDK/vssdkbracematchingtest/cs/bracematching.cs#10)]
     [!code-vb[VSSDKBraceMatchingTest#10](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkbracematchingtest/vb/bracematching.vb#10)]  
  
2.  Uygulama <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider.CreateTagger%2A> bir BraceMatchingTagger örneklemek için yöntemi.  
  
     [!code-csharp[VSSDKBraceMatchingTest#11](../snippets/csharp/VS_Snippets_VSSDK/vssdkbracematchingtest/cs/bracematching.cs#11)]
     [!code-vb[VSSDKBraceMatchingTest#11](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkbracematchingtest/vb/bracematching.vb#11)]  
  
## <a name="building-and-testing-the-code"></a>Oluşturma ve kod test etme  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [İzlenecek Yol: Bir İçerik Türünü Dosya Adı Uzantısına Bağlama](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)

