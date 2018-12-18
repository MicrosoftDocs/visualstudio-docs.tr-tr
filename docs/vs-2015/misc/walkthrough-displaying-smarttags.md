---
title: 'İzlenecek yol: Akıllı etiketler görüntüleme | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], new - smart tags
ms.assetid: 10bb4f69-b259-41f0-b91a-69b04385d9a5
caps.latest.revision: 31
manager: douge
ms.openlocfilehash: 459530726628819587a3c228910baa3b902ae865
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49939104"
---
# <a name="walkthrough-displaying-smarttags"></a>İzlenecek yol: Akıllı etiketler görüntüleme
Akıllı etiketler ampuller yerine kullanım dışı bırakılmıştır. Bkz: [izlenecek yol: ampul önerilerini görüntüleme](../extensibility/walkthrough-displaying-light-bulb-suggestions.md).  
  
 Akıllı etiketler, bir dizi eylemi gösterecek şekilde genişletmek metni etiketlerdir. Örneğin, bir Visual Basic veya Visual C# projesinde bir değişken adı gibi bir tanımlayıcıyı yeniden adlandırdığınızda Word'ün altında kırmızı bir çizgi görünür. Alt çizginin işaretçiyi bir düğme imlecini görüntülenir. Düğmeye tıklarsanız, önerilen eylem, örneğin, görüntülenir **IsRead yeniden adlandırmak için IsReady**. Eylem tıklarsanız, başvurularını **IsRead** projede yeniden adlandırılır **IsReady**.  
  
 Akıllı etiketler Düzenleyicisi IntelliSense uygulamasında bir parçası olsa da, sınıflara göre akıllı etiketler uygulayabilirsiniz <xref:Microsoft.VisualStudio.Language.Intellisense.SmartTag>ve ardından uygulama <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> arabirimi ve <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider> arabirimi.  
  
> [!NOTE]
>  Benzer şekilde diğer türlerdeki etiketler uygulanabilir.  
  
 Aşağıdaki örneklerde, geçerli sözcüğü görüntülenen akıllı etiket oluşturma işlemi gösterilmektedir ve iki sahip önerilen eylemler: **büyük harfe Dönüştür** ve **küçük harfe Dönüştür**.  
  
## <a name="prerequisites"></a>Önkoşullar  
 Bu izlenecek yolda takip etmek için Visual Studio SDK'yı yüklemeniz gerekir. Daha fazla bilgi için [Visual Studio SDK](../extensibility/visual-studio-sdk.md).  
  
## <a name="creating-a-managed-extensibility-framework-mef-project"></a>Yönetilen Genişletilebilirlik Çerçevesi (MEF) proje oluşturma  
  
#### <a name="to-create-a-mef-project"></a>MEF projesi oluşturmak için  
  
1.  Bir düzenleyici sınıflandırıcı projesi oluşturun. Çözüm adı `SmartTagTest`.  
  
2.  VSIX bildirim Düzenleyicisi'nde source.extension.vsixmanifest dosyası açın.  
  
3.  Emin olun **varlıklar** bölümü içeren bir `Microsoft.VisualStudio.MefComponent` türü **kaynak** ayarlanır `A project in current solution`, ve **proje** SmartTagTest.dll için ayarlanır.  
  
4.  Kaydedip source.extension.vsixmanifest kapatın.  
  
5.  Proje şu başvuruyu ekleyin ve ayarlayın **CopyLocal** için `false`:  
  
     Microsoft.VisualStudio.Language.Intellisense  
  
6.  Varolan sınıf dosyaları silin.  
  
## <a name="implementing-a-tagger-for-smart-tags"></a>Akıllı etiketler için bir etiketlerde uygulama  
  
#### <a name="to-implement-a-tagger-for-smart-tags"></a>Akıllı etiketler için bir etiketlerde uygulamak için  
  
1.  Bir sınıf dosyası ekleyin ve adlandırın `TestSmartTag`.  
  
2.  Aşağıdaki içeri aktarmaları ekleyin:  
  
     [!code-csharp[VSSDKSmartTagTest#1](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#1)]
     [!code-vb[VSSDKSmartTagTest#1](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#1)]  
  
3.  Adlı bir sınıf ekleyin `TestSmartTag` öğesinden devralan <xref:Microsoft.VisualStudio.Language.Intellisense.SmartTag>.  
  
     [!code-csharp[VSSDKSmartTagTest#2](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#2)]
     [!code-vb[VSSDKSmartTagTest#2](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#2)]  
  
4.  Temel oluşturucu ile çağıran Bu sınıf için bir oluşturucu ekleyin bir <xref:Microsoft.VisualStudio.Language.Intellisense.SmartTagType> , <xref:Microsoft.VisualStudio.Language.Intellisense.SmartTagType>, mavi bir çizgi bir sözcüğün ilk karakterin altında görünmesine neden olur. (Kullanırsanız <xref:Microsoft.VisualStudio.Language.Intellisense.SmartTagType>, word'ün son karakterin altında kırmızı bir çizgi görünür.)  
  
     [!code-csharp[VSSDKSmartTagTest#3](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#3)]
     [!code-vb[VSSDKSmartTagTest#3](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#3)]  
  
5.  Adlı bir sınıf ekleyin `TestSmartTagger` öğesinden devralan <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> türü `TestSmartTag`ve uygulayan <xref:System.IDisposable>.  
  
     [!code-csharp[VSSDKSmartTagTest#4](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#4)]
     [!code-vb[VSSDKSmartTagTest#4](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#4)]  
  
6.  Etiketlerde sınıfına aşağıdaki özel alanlar ekleyin.  
  
     [!code-csharp[VSSDKSmartTagTest#5](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#5)]
     [!code-vb[VSSDKSmartTagTest#5](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#5)]  
  
7.  Özel alanları ayarlar ve abone olduğu bir oluşturucu ekleyin <xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged> olay.  
  
     [!code-csharp[VSSDKSmartTagTest#6](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#6)]
     [!code-vb[VSSDKSmartTagTest#6](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#6)]  
  
8.  Uygulama <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A> böylece etiket için geçerli kelimenin oluşturulur. (Bu yöntem aynı zamanda özel bir yöntem çağırır `GetSmartTagActions` , daha sonra açıklanmıştır.)  
  
     [!code-csharp[VSSDKSmartTagTest#7](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#7)]
     [!code-vb[VSSDKSmartTagTest#7](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#7)]  
  
9. Ekleme bir `GetSmartTagActions` akıllı etiket eylemleri ayarlamak için yöntemi. Eylemler, sonraki adımlarda uygulanır.  
  
     [!code-csharp[VSSDKSmartTagTest#8](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#8)]
     [!code-vb[VSSDKSmartTagTest#8](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#8)]  
  
10. Bildirme `SmartTagsChanged` olay.  
  
     [!code-csharp[VSSDKSmartTagTest#9](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#9)]
     [!code-vb[VSSDKSmartTagTest#9](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#9)]  
  
11. Uygulama `OnLayoutChanged` yükseltmek için olay işleyicisi `TagsChanged` neden olan olay <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A> çağrılabilir.  
  
     [!code-csharp[VSSDKSmartTagTest#10](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#10)]
     [!code-vb[VSSDKSmartTagTest#10](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#10)]  
  
12. Uygulama <xref:System.IDisposable.Dispose%2A> gelen BT'nin kaldırması için yöntemi <xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged> olay.  
  
     [!code-csharp[VSSDKSmartTagTest#11](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#11)]
     [!code-vb[VSSDKSmartTagTest#11](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#11)]  
  
## <a name="implementing-the-smart-tag-tagger-provider"></a>Akıllı etiket etiketlerde sağlayıcıyı uygulama  
  
#### <a name="to-implement-the-smart-tag-tagger-provider"></a>Akıllı etiket etiketlerde sağlayıcısını uygulamak için  
  
1.  Adlı bir sınıf ekleyin `TestSmartTagTaggerProvider` öğesinden devralan <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider>. İle dışarı bir <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> "metin" bir <xref:Microsoft.VisualStudio.Utilities.OrderAttribute> , önce "varsayılan" = ve <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> , <xref:Microsoft.VisualStudio.Language.Intellisense.SmartTag>.  
  
     [!code-csharp[VSSDKSmartTagTest#12](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#12)]
     [!code-vb[VSSDKSmartTagTest#12](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#12)]  
  
2.  İçeri aktarma <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> özelliği olarak.  
  
     [!code-csharp[VSSDKSmartTagTest#13](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#13)]
     [!code-vb[VSSDKSmartTagTest#13](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#13)]  
  
3.  Uygulama <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider.CreateTagger%2A> yöntemi.  
  
     [!code-csharp[VSSDKSmartTagTest#14](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#14)]
     [!code-vb[VSSDKSmartTagTest#14](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#14)]  
  
## <a name="implementing-smart-tag-actions"></a>Akıllı etiket eylemleri uygulama  
  
#### <a name="to-implement-smart-tag-actions"></a>Akıllı etiket eylemlerini uygulamak için  
  
1. İki sınıf oluşturma ilk adlı `UpperCaseSmartTagAction` ve ikinci adlı `LowerCaseSmartTagAction`. Her iki sınıfları uygulayan <xref:Microsoft.VisualStudio.Language.Intellisense.ISmartTagAction>.  
  
    [!code-csharp[VSSDKSmartTagTest#15](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#15)]
    [!code-vb[VSSDKSmartTagTest#15](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#15)]  
  
    [!code-csharp[VSSDKSmartTagTest#16](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#16)]
    [!code-vb[VSSDKSmartTagTest#16](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#16)]  
  
   Bir çağrı dışında her iki sınıflar benzer <xref:System.String.ToUpper%2A> ve diğer çağrılar <xref:System.String.ToLower%2A>. Yalnızca büyük harf Eylem sınıfına aşağıdaki adımları kapsar, ancak her iki sınıf uygulamalıdır. Büyük harf eylem olarak küçük eylemi uygulamak için bir desen uygulamak için adımları kullanın.  
  
2. Bir özel alan kümesi bildirin.  
  
    [!code-csharp[VSSDKSmartTagTest#17](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#17)]
    [!code-vb[VSSDKSmartTagTest#17](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#17)]  
  
3. Alanları ayarlayan bir oluşturucu ekleyin.  
  
    [!code-csharp[VSSDKSmartTagTest#18](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#18)]
    [!code-vb[VSSDKSmartTagTest#18](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#18)]  
  
4. Özellikleri aşağıdaki gibi uygulayın.  
  
    [!code-csharp[VSSDKSmartTagTest#19](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#19)]
    [!code-vb[VSSDKSmartTagTest#19](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#19)]  
  
5. Uygulama <xref:Microsoft.VisualStudio.Language.Intellisense.ISmartTagAction.Invoke%2A> aralık içindeki metni kendi büyük harf eşdeğeri ile değiştirerek yöntemi.  
  
    [!code-csharp[VSSDKSmartTagTest#20](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#20)]
    [!code-vb[VSSDKSmartTagTest#20](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#20)]  
  
## <a name="building-and-testing-the-code"></a>Oluşturma ve kod test etme  
 Bu kodu test etmek için SmartTagTest Çözümü derleyin ve deneysel örneğinde çalıştırın.  
  
#### <a name="to-build-and-test-the-smarttagtest-solution"></a>Derleme ve SmartTagTest çözümü test etmek için  
  
1.  Çözümü oluşturun.  
  
2.  Bu projede hata ayıklayıcıda çalıştırdığınızda, Visual Studio'nun ikinci bir örneğini başlatılır.  
  
3.  Bir metin dosyası oluşturun ve bir metin yazın.  
  
     Metnin ilk sözcüğün ilk harfini altında mavi bir çizgi görüntülenmesi gerekir.  
  
4.  İşaretçiyi mavi çizginin üzerine getirin.  
  
     Bir düğme imlecini görüntülenmesi gerekir.  
  
5.  Düğmeye tıkladığınızda, iki eylemleri görüntülenecek önerilen: **büyük harfe Dönüştür** ve **küçük harfe Dönüştür**. İlk eylem tıklarsanız, geçerli kelimenin tüm metni büyük harfe dönüştürülmelidir. İkinci eylem tıklarsanız, bütün metni küçük harflere dönüştürülmelidir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [İzlenecek Yol: Bir İçerik Türünü Dosya Adı Uzantısına Bağlama](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)