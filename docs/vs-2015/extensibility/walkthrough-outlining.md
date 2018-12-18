---
title: 'İzlenecek yol: Ana hat oluşturma | Microsoft Docs'
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
- editors [Visual Studio SDK], new - outlining
ms.assetid: d75a44aa-265a-44d4-9c28-457f59c4ff9f
caps.latest.revision: 31
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 897ff6a39716f424c40fa587d905847a0dbb3682
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51805274"
---
# <a name="walkthrough-outlining"></a>İzlenecek Yol: Ana Hat Oluşturma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Dil tabanlı özellikleri genişletmek veya daraltmak için istediğiniz metin bölgeleri türleri tanımlayarak anahat oluşturma gibi uygulayabilirsiniz. Bir dil hizmeti bağlamında bölgeleri tanımlayabilirsiniz kendi dosya adı uzantısı ve içerik türünü tanımlayın ve bölge tanımı yalnızca bu türü için geçerli veya mevcut bir içerik türüyle (örneğin, "metin") bölge tanımları uygulayabilirsiniz. Bu izlenecek yol, tanımlamak ve ana hat oluşturma bölgeleri görüntülemek gösterilmektedir.  
  
## <a name="prerequisites"></a>Önkoşullar  
 Visual Studio 2015'ten başlayarak, size Visual Studio SDK İndirme Merkezi'nden yüklemeyin. Visual Studio kurulumunda isteğe bağlı bir özellik olarak eklenmiştir. VS SDK'yi daha sonra yükleyebilirsiniz. Daha fazla bilgi için [Visual Studio SDK'sını yükleme](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-managed-extensibility-framework-mef-project"></a>Yönetilen Genişletilebilirlik Çerçevesi (MEF) proje oluşturma  
  
#### <a name="to-create-a-mef-project"></a>MEF projesi oluşturmak için  
  
1.  Bir VSIX projesi oluşturun. Çözüm adı `OutlineRegionTest`.  
  
2.  Bir düzenleyici sınıflandırıcı öğe şablonu, projeye ekleyin. Daha fazla bilgi için [bir düzenleyici öğesi şablonuyla uzantı oluşturma](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
3.  Varolan sınıf dosyaları silin.  
  
## <a name="implementing-an-outlining-tagger"></a>Bir anahat oluşturma etiketlerde uygulama  
 Anahat oluşturma bölgeleri etiketi bir tür tarafından işaretlenir (<xref:Microsoft.VisualStudio.Text.Tagging.OutliningRegionTag>). Bu etiket davranışı anahat oluşturma standart sağlar. Anahatları belirlenmiş bölge genişletilebilir veya daraltılabilir. Anahatları belirlenmiş bölge, genişletilir ve genişletilmiş bölge, dikey bir çizgiyle güncelleştireceğinizi bir daraltılmışsa artı veya eksi işareti tarafından işaretlenir.  
  
 Nasıl tarafından ayrılmış tüm bölgeler için anahat oluşturma bölgeleri oluşturan bir etiketlerde tanımlamak aşağıdaki adımları Göster "[" ve "]".  
  
#### <a name="to-implement-an-outlining-tagger"></a>Bir anahat oluşturma etiketlerde uygulamak için  
  
1.  Bir sınıf dosyası ekleyin ve adlandırın `OutliningTagger`.  
  
2.  Aşağıdaki ad alanlarını içeri aktarın.  
  
     [!code-csharp[VSSDKOutlineRegionTest#1](../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs#1)]
     [!code-vb[VSSDKOutlineRegionTest#1](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb#1)]  
  
3.  Adlı bir sınıf oluşturun `OutliningTagger`, ve uygulama <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601>:  
  
     [!code-csharp[VSSDKOutlineRegionTest#2](../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs#2)]
     [!code-vb[VSSDKOutlineRegionTest#2](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb#2)]  
  
4.  Anlık görüntü ve metin arabelleğini izlemek için ve bölgeler anahat oluşturma olarak etiketlenmesi satır kümesi ulaşıncaya kadar bazı alanlar ekleyin. Bu kod, anahat oluşturma bölgeleri temsil eden (daha sonra tanımlanacak) bölge nesneleri listesini içerir.  
  
     [!code-csharp[VSSDKOutlineRegionTest#3](../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs#3)]
     [!code-vb[VSSDKOutlineRegionTest#3](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb#3)]  
  
5.  Alanları başlatan bir etiketlerde oluşturucu ekleyin arabellek ayrıştırır ve bir olay işleyici ekler <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> olay.  
  
     [!code-csharp[VSSDKOutlineRegionTest#4](../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs#4)]
     [!code-vb[VSSDKOutlineRegionTest#4](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb#4)]  
  
6.  Uygulama <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A> etiket başlatır yöntemi yayılan. Bu örnek olduğunu varsayar, yayılma <xref:Microsoft.VisualStudio.Text.NormalizedSpanCollection> yönteme geçirilen bu her zaman çalışması olmayabilir rağmen bitişiktir. Bu yöntem her bir ana hat oluşturma bölgeleri için yeni bir etiket aralık başlatır.  
  
     [!code-csharp[VSSDKOutlineRegionTest#5](../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs#5)]
     [!code-vb[VSSDKOutlineRegionTest#5](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb#5)]  
  
7.  Bildirme bir `TagsChanged` olay işleyicisi.  
  
     [!code-csharp[VSSDKOutlineRegionTest#6](../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs#6)]
     [!code-vb[VSSDKOutlineRegionTest#6](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb#6)]  
  
8.  Ekleme bir `BufferChanged` yanıt veren bir olay işleyicisi <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> metin arabelleğini ayrıştırma tarafından olayları.  
  
     [!code-csharp[VSSDKOutlineRegionTest#7](../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs#7)]
     [!code-vb[VSSDKOutlineRegionTest#7](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb#7)]  
  
9. Arabellek ayrıştıran bir yöntem ekleyin. Burada verilen örnek yalnızca gösterim amaçlıdır. İç içe geçmiş ana hat oluşturma bölgelere arabellek zaman uyumlu olarak ayrıştırır.  
  
     [!code-csharp[VSSDKOutlineRegionTest#8](../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs#8)]
     [!code-vb[VSSDKOutlineRegionTest#8](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb#8)]  
  
10. Aşağıdaki yardımcı yöntemini sol ayraç eşleştirme 1., anahat düzeyini temsil eden bir tamsayı olarak alır.  
  
     [!code-csharp[VSSDKOutlineRegionTest#9](../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs#9)]
     [!code-vb[VSSDKOutlineRegionTest#9](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb#9)]  
  
11. Aşağıdaki yardımcı yöntemini (Bu konunun ilerleyen bölümlerinde tanımlı) bir bölge içinde bir SnapshotSpan çevirir.  
  
     [!code-csharp[VSSDKOutlineRegionTest#10](../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs#10)]
     [!code-vb[VSSDKOutlineRegionTest#10](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb#10)]  
  
12. Aşağıdaki kod, yalnızca gösterim amaçlıdır. Bu, bir anahat oluşturma bölgede ve aynı zamanda üst bölgesi (varsa) başvuru başlangıç uzaklığı ve satır numarası içeren bir PartialRegion sınıfı tanımlar. Bu bölgeler anahat oluşturma iç içe geçmiş ayarlamak ayrıştırıcı sağlar. Bölge türetilen bir anahat oluşturma bölgesi sonuna satır sayısı bir başvuru içeriyor.  
  
     [!code-csharp[VSSDKOutlineRegionTest#11](../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs#11)]
     [!code-vb[VSSDKOutlineRegionTest#11](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb#11)]  
  
## <a name="implementing-a-tagger-provider"></a>Etiketlerde sağlayıcıyı uygulama  
 Etiketlerde sağlayıcısı, etiketlerde için dışarı aktarmanız gerekir. Etiketlerde sağlayıcısı oluşturur bir `OutliningTagger` "metin" içerik türü veya başka döndürür bir arabelleği için bir `OutliningTagger` arabellek zaten varsa.  
  
#### <a name="to-implement-a-tagger-provider"></a>Etiketlerde sağlayıcısını uygulamak için  
  
1.  Adlı bir sınıf oluşturun `OutliningTaggerProvider` uygulayan <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider>ve ContentType ve TagType özniteliklerle dışarı aktarın.  
  
     [!code-csharp[VSSDKOutlineRegionTest#12](../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs#12)]
     [!code-vb[VSSDKOutlineRegionTest#12](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb#12)]  
  
2.  Uygulama <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider.CreateTagger%2A> ekleyerek yöntemi bir `OutliningTagger` özelliklerine arabellek.  
  
     [!code-csharp[VSSDKOutlineRegionTest#13](../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs#13)]
     [!code-vb[VSSDKOutlineRegionTest#13](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb#13)]  
  
## <a name="building-and-testing-the-code"></a>Oluşturma ve kod test etme  
 Bu kodu test etmek için OutlineRegionTest Çözümü derleyin ve deneysel örneğinde çalıştırın.  
  
#### <a name="to-build-and-test-the-outlineregiontest-solution"></a>Derleme ve OutlineRegionTest çözümü test etmek için  
  
1.  Çözümü oluşturun.  
  
2.  Bu projede hata ayıklayıcıda çalıştırdığınızda, Visual Studio'nun ikinci bir örneğini başlatılır.  
  
3.  Bir metin dosyası oluşturun. Hem açılış ayracı hem de kapanış ayracı içeren bir metin yazın.  
  
    ```  
    [  
       Hello  
    ]  
    ```  
  
4.  Her iki küme ayraçları içeren bir anahat oluşturma bölgesi olmalıdır. Anahat oluşturma bölge daraltmak için eksi işaretini açık küme ayracı solundaki olması gerekir. Ne zaman bölgesi daraltıldığında, üç nokta simgesine (...) daraltılmış bölgeye ve metni içeren bir açılır pencere solunda görünmesi gereken **gelin metin** üç nokta üzerinde işaretçiyi getirdiğinizde görünmelidir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [İzlenecek Yol: Bir İçerik Türünü Dosya Adı Uzantısına Bağlama](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)

