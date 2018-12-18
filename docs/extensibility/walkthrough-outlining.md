---
title: 'İzlenecek yol: Ana hat oluşturma | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - outlining
ms.assetid: d75a44aa-265a-44d4-9c28-457f59c4ff9f
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 740ed444770a440b54fe61b0c8ec8189691fe9a1
ms.sourcegitcommit: ef828606e9758c7a42a2f0f777c57b2d39041ac3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/06/2018
ms.locfileid: "39566940"
---
# <a name="walkthrough-outlining"></a>İzlenecek Yol: Ana Hat Oluşturma
Dil tabanlı özellikleri genişletmek veya daraltmak için istediğiniz metin bölgeleri türleri tanımlayarak anahat oluşturma gibi ayarlayın. Bir dil hizmeti bağlamında bölgeleri tanımlamak veya kendi dosya adı uzantısı ve içerik türünü tanımlayın ve bölge tanımı yalnızca bu türü için geçerli veya bölge tanımları var olan bir içerik türüyle (örneğin, "metin") uygulamak. Bu izlenecek yol, tanımlamak ve ana hat oluşturma bölgeleri görüntülemek gösterilmektedir.  
  
## <a name="prerequisites"></a>Önkoşullar  
 Visual Studio 2015'ten başlayarak, Visual Studio SDK İndirme Merkezi'nden yüklemeyin. Visual Studio kurulumunda isteğe bağlı bir özellik eklemiştir. VS SDK'yi daha sonra yükleyebilirsiniz. Daha fazla bilgi için [Visual Studio SDK'yı yükleme](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="create-a-managed-extensibility-framework-mef-project"></a>Yönetilen Genişletilebilirlik Çerçevesi (MEF) proje oluşturma  
  
### <a name="to-create-a-mef-project"></a>MEF projesi oluşturmak için  
  
1.  Bir VSIX projesi oluşturun. Çözüm adı `OutlineRegionTest`.  
  
2.  Bir düzenleyici sınıflandırıcı öğe şablonu, projeye ekleyin. Daha fazla bilgi için [bir düzenleyici öğesi şablonuyla uzantı oluşturma](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
3.  Varolan sınıf dosyaları silin.  
  
## <a name="implement-an-outlining-tagger"></a>Bir anahat oluşturma etiketlerde uygulayın  
 Anahat oluşturma bölgeleri etiketi bir tür tarafından işaretlenir (<xref:Microsoft.VisualStudio.Text.Tagging.OutliningRegionTag>). Bu etiket davranışı anahat oluşturma standart sağlar. Anahatları belirlenmiş bölge genişletilebilir veya daraltılabilir. Anahatları belirlenmiş bölge bir artı işareti işaretlenir (**+**) daraltılmışsa veya eksi işareti (**-**), genişletilmiş ve genişletilmiş bölge, dikey bir çizgiyle güncelleştireceğinizi.  
  
 Aşağıdaki adımlarda, köşeli parantez ayrılmış tüm bölgeler için anahat oluşturma bölgeleri oluşturan bir etiketlerde tanımlanacağı gösterilmektedir (**[**,**]**).  
  
### <a name="to-implement-an-outlining-tagger"></a>Bir anahat oluşturma etiketlerde uygulamak için  
  
1.  Bir sınıf dosyası ekleyin ve adlandırın `OutliningTagger`.  
  
2.  Aşağıdaki ad alanlarını içeri aktarın.  
  
     [!code-csharp[VSSDKOutlineRegionTest#1](../extensibility/codesnippet/CSharp/walkthrough-outlining_1.cs)]
     [!code-vb[VSSDKOutlineRegionTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_1.vb)]  
  
3.  Adlı bir sınıf oluşturun `OutliningTagger`, ve uygulama <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601>:  
  
     [!code-csharp[VSSDKOutlineRegionTest#2](../extensibility/codesnippet/CSharp/walkthrough-outlining_2.cs)]
     [!code-vb[VSSDKOutlineRegionTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_2.vb)]  
  
4.  Anlık görüntü ve metin arabelleğini izlemek için ve bölgeler anahat oluşturma olarak etiketlenmesi satır kümesi ulaşıncaya kadar bazı alanlar ekleyin. Bu kod, anahat oluşturma bölgeleri temsil eden (daha sonra tanımlanacak) bölge nesneleri listesini içerir.  
  
     [!code-csharp[VSSDKOutlineRegionTest#3](../extensibility/codesnippet/CSharp/walkthrough-outlining_3.cs)]
     [!code-vb[VSSDKOutlineRegionTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_3.vb)]  
  
5.  Alanları başlatan bir etiketlerde oluşturucu ekleyin arabellek ayrıştırır ve bir olay işleyici ekler <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> olay.  
  
     [!code-csharp[VSSDKOutlineRegionTest#4](../extensibility/codesnippet/CSharp/walkthrough-outlining_4.cs)]
     [!code-vb[VSSDKOutlineRegionTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_4.vb)]  
  
6.  Uygulama <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A> etiket başlatır yöntemi yayılan. Bu örnek olduğunu varsayar, yayılma <xref:Microsoft.VisualStudio.Text.NormalizedSpanCollection> yönteme geçirilen durumu her zaman olmayabilir rağmen bitişiktir. Bu yöntem her bir ana hat oluşturma bölgeleri için yeni bir etiket aralık başlatır.  
  
     [!code-csharp[VSSDKOutlineRegionTest#5](../extensibility/codesnippet/CSharp/walkthrough-outlining_5.cs)]
     [!code-vb[VSSDKOutlineRegionTest#5](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_5.vb)]  
  
7.  Bildirme bir `TagsChanged` olay işleyicisi.  
  
     [!code-csharp[VSSDKOutlineRegionTest#6](../extensibility/codesnippet/CSharp/walkthrough-outlining_6.cs)]
     [!code-vb[VSSDKOutlineRegionTest#6](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_6.vb)]  
  
8.  Ekleme bir `BufferChanged` yanıt veren bir olay işleyicisi <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> metin arabelleğini ayrıştırma tarafından olayları.  
  
     [!code-csharp[VSSDKOutlineRegionTest#7](../extensibility/codesnippet/CSharp/walkthrough-outlining_7.cs)]
     [!code-vb[VSSDKOutlineRegionTest#7](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_7.vb)]  
  
9. Arabellek ayrıştıran bir yöntem ekleyin. Burada verilen örnek yalnızca gösterim amaçlıdır. İç içe geçmiş ana hat oluşturma bölgelere arabellek zaman uyumlu olarak ayrıştırır.  
  
     [!code-csharp[VSSDKOutlineRegionTest#8](../extensibility/codesnippet/CSharp/walkthrough-outlining_8.cs)]
     [!code-vb[VSSDKOutlineRegionTest#8](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_8.vb)]  
  
10. Aşağıdaki yardımcı yöntemini sol ayraç eşleştirme 1., anahat düzeyini temsil eden bir tamsayı olarak alır.  
  
     [!code-csharp[VSSDKOutlineRegionTest#9](../extensibility/codesnippet/CSharp/walkthrough-outlining_9.cs)]
     [!code-vb[VSSDKOutlineRegionTest#9](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_9.vb)]  
  
11. Aşağıdaki yardımcı yöntemini (Bu makalenin sonraki bölümlerinde tanımlı) bir bölge içinde bir SnapshotSpan çevirir.  
  
     [!code-csharp[VSSDKOutlineRegionTest#10](../extensibility/codesnippet/CSharp/walkthrough-outlining_10.cs)]
     [!code-vb[VSSDKOutlineRegionTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_10.vb)]  
  
12. Aşağıdaki kod, yalnızca gösterim amaçlıdır. Bu, anahat oluşturma bir bölge ve üst bölgesi (varsa) başvuru başlangıç uzaklığı ve satır numarası içeren bir PartialRegion sınıfı tanımlar. Bu kod, bölgeler anahat oluşturma iç içe geçmiş ayarlamak ayrıştırıcı sağlar. Bölge türetilen bir anahat oluşturma bölgesi sonuna satır sayısı bir başvuru içeriyor.  
  
     [!code-csharp[VSSDKOutlineRegionTest#11](../extensibility/codesnippet/CSharp/walkthrough-outlining_11.cs)]
     [!code-vb[VSSDKOutlineRegionTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_11.vb)]  
  
## <a name="implement-a-tagger-provider"></a>Etiketlerde sağlayıcıyı uygulama  
 Etiketlerde sağlayıcısı, etiketlerde için dışarı aktarın. Etiketlerde sağlayıcısı oluşturur bir `OutliningTagger` "metin" içerik türü veya başka döndürür bir arabelleği için bir `OutliningTagger` arabellek zaten varsa.  
  
### <a name="to-implement-a-tagger-provider"></a>Etiketlerde sağlayıcısını uygulamak için  
  
1.  Adlı bir sınıf oluşturun `OutliningTaggerProvider` uygulayan <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider>ve ContentType ve TagType özniteliklerle dışarı aktarın.  
  
     [!code-csharp[VSSDKOutlineRegionTest#12](../extensibility/codesnippet/CSharp/walkthrough-outlining_12.cs)]
     [!code-vb[VSSDKOutlineRegionTest#12](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_12.vb)]  
  
2.  Uygulama <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider.CreateTagger%2A> ekleyerek yöntemi bir `OutliningTagger` özelliklerine arabellek.  
  
     [!code-csharp[VSSDKOutlineRegionTest#13](../extensibility/codesnippet/CSharp/walkthrough-outlining_13.cs)]
     [!code-vb[VSSDKOutlineRegionTest#13](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_13.vb)]  
  
## <a name="build-and-test-the-code"></a>Kod oluşturup test  
 Bu kodu test etmek için OutlineRegionTest Çözümü derleyin ve deneysel örneğinde çalıştırın.  
  
### <a name="to-build-and-test-the-outlineregiontest-solution"></a>Derleme ve OutlineRegionTest çözümü test etmek için  
  
1.  Çözümü oluşturun.  
  
2.  Bu projede hata ayıklayıcıda çalıştırdığınızda, Visual Studio'nun ikinci bir örneğini başlatılır.  
  
3.  Bir metin dosyası oluşturun. Açma köşeli ayraçlar hem sağ köşeli içeren bir metin yazın.  
  
    ```  
    [  
       Hello  
    ]  
    ```  
  
4.  İki ayraç içeren bir anahat oluşturma bölgesi olmalıdır. Anahat oluşturma bölge daraltmak için eksi işaretini sol tarafındaki açık ayraç olması gerekir. Ne zaman bölgesi daraltıldığında, üç nokta simgesine (*...* ) daraltılmış bölgeye ve metni içeren bir açılır pencere solunda görünmesi gereken **gelin metin** üç nokta üzerinde işaretçiyi getirdiğinizde görünmelidir.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [İzlenecek yol: bir içerik türü için bir dosya adı uzantısına bağlama](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)