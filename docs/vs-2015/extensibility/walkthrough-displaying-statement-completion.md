---
title: 'İzlenecek yol: Deyim tamamlamayı görüntüleme | Microsoft Docs'
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
- editors [Visual Studio SDK], new - statement completion
ms.assetid: f3152c4e-7673-4047-a079-2326941d1c83
caps.latest.revision: 37
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 097cb671e15b75edd7e61f7860cf3a0c03123c9b
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51733044"
---
# <a name="walkthrough-displaying-statement-completion"></a>İzlenecek Yol: Deyim Tamamlamayı Görüntüleme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Dil tabanlı deyim tamamlama tamamlama sağlamak istediğiniz tanımlayıcıları tanımlama ve ardından tamamlama oturumu tetiklemeden uygulayabilir. Deyim tamamlama dil hizmeti bağlamında tanımlayın, kendi dosya adı uzantısı ve içerik türünü tanımlayabilir ve ardından bu tür için tamamlama görüntülemek ya da mevcut bir içerik türü için tamamlama tetikleyebilirsiniz — Örneğin, "Düz". Bu izlenecek yol, içerik türü metin dosyaları olan "Düz" içerik türü için deyim tamamlama tetikleme işlemi gösterilmektedir. Kod ve XML dosyaları dahil tüm diğer içerik türleri, üst "metin" içerik türü değil.  
  
 Deyim tamamlama, belirli karakter yazarak genellikle tetiklenir — Örneğin, "kullanma" gibi bir tanımlayıcının yazmaya tarafından. Bu genellikle bir seçim uygulamak için boşluk, sekme veya Enter tuşuna basarak kapatıldı. Tuş vuruşları için bir komut işleyici kullanarak bir karakter yazarak tetiklenen IntelliSense özelliklerini uygulayabilirsiniz ( <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> arabirimi) ve uygulayan bir işleyici sağlayıcısı <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> arabirimi. Tamamlama katılan tanımlayıcıları listesi olan tamamlama kaynak oluşturmak için uygulaması <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource> arabirimi ve bir tamamlanma kaynak sağlayıcısı ( <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSourceProvider> arabirimi). Bileşen parçalarına Yönetilen Genişletilebilirlik Çerçevesi (MEF) sağlayıcılarıdır. Kaynak ve denetleyici sınıfları dışarı aktarma ve Hizmetleri ve aracıları içeri aktarma için sorumlu oldukları — Örneğin, <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>, metin arabelleği gezinme sağlar ve <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionBroker>, tamamlama oturumu tetikler.  
  
 Bu izlenecek yol, sabit kodlanmış bir tanımlayıcılar için ifade tamamlama uygulamak gösterilmektedir. Dil hizmeti ve dil belgeleri tam uygulamalarında, bu içeriği sağlamak için yükümlü olursunuz.  
  
## <a name="prerequisites"></a>Önkoşullar  
 Visual Studio 2015'ten başlayarak, size Visual Studio SDK İndirme Merkezi'nden yüklemeyin. Visual Studio kurulumunda isteğe bağlı bir özellik olarak eklenmiştir. VS SDK'yi daha sonra yükleyebilirsiniz. Daha fazla bilgi için [Visual Studio SDK'sını yükleme](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-mef-project"></a>MEF proje oluşturma  
  
#### <a name="to-create-a-mef-project"></a>MEF projesi oluşturmak için  
  
1.  Bir C# VSIX projesi oluşturun. (İçinde **yeni proje** iletişim kutusunda **Visual C# / genişletilebilirlik**, ardından **VSIX projesi**.) Çözüm adı `CompletionTest`.  
  
2.  Bir düzenleyici sınıflandırıcı öğe şablonu, projeye ekleyin. Daha fazla bilgi için [bir düzenleyici öğesi şablonuyla uzantı oluşturma](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
3.  Varolan sınıf dosyaları silin.  
  
4.  Aşağıdaki başvuruları projeye ekleyin ve doğrulayın **CopyLocal** ayarlanır `false`:  
  
     Microsoft.VisualStudio.Editor  
  
     Microsoft.VisualStudio.Language.Intellisense  
  
     Microsoft.VisualStudio.OLE.Interop  
  
     Microsoft.VisualStudio.Shell.14.0  
  
     Microsoft.VisualStudio.Shell.Immutable.10.0  
  
     Microsoft.VisualStudio.TextManager.Interop  
  
## <a name="implementing-the-completion-source"></a>Tamamlama kaynağı uygulama  
 Tamamlama kaynak tanımlayıcıları Kümesi toplanıyor ve bir kullanıcı, bir tanımlayıcının ilk harflerini gibi bir tamamlanma tetikleyicisi yazdığında tamamlama penceresini için içerik ekleme sorumludur. Bu örnekte, sabit kodlanmış tanımlayıcıları ve açıklamalarının <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource.AugmentCompletionSession%2A> yöntemi. Çoğu gerçek kullanım dilinizin ayrıştırıcı, tamamlanma listesini doldurmak için belirteçlerini almak için kullanırsınız.  
  
#### <a name="to-implement-the-completion-source"></a>Tamamlama kaynak uygulamak için  
  
1.  Bir sınıf dosyası ekleyin ve adlandırın `TestCompletionSource`.  
  
2.  Aşağıdaki içeri aktarmaları ekleyin:  
  
     [!code-csharp[VSSDKCompletionTest#1](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletionsource.cs#1)]
     [!code-vb[VSSDKCompletionTest#1](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletionsource.vb#1)]  
  
3.  Sınıf bildirimi için değiştirme `TestCompletionSource` uygular, böylece <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource>:  
  
     [!code-csharp[VSSDKCompletionTest#2](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletionsource.cs#2)]
     [!code-vb[VSSDKCompletionTest#2](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletionsource.vb#2)]  
  
4.  Kaynak sağlayıcısı, metin arabelleği ve bir listesi için özel alanlar ekleyin <xref:Microsoft.VisualStudio.Language.Intellisense.Completion> (tamamlama oturumu katılacak tanımlayıcıları karşılık gelir) nesneler:  
  
     [!code-csharp[VSSDKCompletionTest#3](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletionsource.cs#3)]
     [!code-vb[VSSDKCompletionTest#3](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletionsource.vb#3)]  
  
5.  Kaynak sağlayıcısı ve arabellek ayarlayan bir oluşturucu ekleyin. `TestCompletionSourceProvider` Sınıfı, sonraki adımlarda tanımlanır:  
  
     [!code-csharp[VSSDKCompletionTest#4](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletionsource.cs#4)]
     [!code-vb[VSSDKCompletionTest#4](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletionsource.vb#4)]  
  
6.  Uygulama <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource.AugmentCompletionSession%2A> bağlamında sağlamak istediğiniz tamamlamaları içeren bir tamamlama kümesi ekleyerek yöntemi. Her bir tamamlama kümesi içerir <xref:Microsoft.VisualStudio.Language.Intellisense.Completion> tamamlamaları, bir tamamlama penceresini sekmesine karşılık gelir. (Visual Basic projelerinde tamamlama penceresini sekmeleri adlandırılır **ortak** ve **tüm**.) Sonraki adımda FindTokenSpanAtPosition yöntemi tanımlanır.  
  
     [!code-csharp[VSSDKCompletionTest#5](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletionsource.cs#5)]
     [!code-vb[VSSDKCompletionTest#5](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletionsource.vb#5)]  
  
7.  Aşağıdaki yöntem, imleç konumundan geçerli kelimenin bulmak için kullanılır:  
  
     [!code-csharp[VSSDKCompletionTest#6](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletionsource.cs#6)]
     [!code-vb[VSSDKCompletionTest#6](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletionsource.vb#6)]  
  
8.  Uygulama `Dispose()` yöntemi:  
  
     [!code-csharp[VSSDKCompletionTest#7](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletionsource.cs#7)]
     [!code-vb[VSSDKCompletionTest#7](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletionsource.vb#7)]  
  
## <a name="implementing-the-completion-source-provider"></a>Tamamlama kaynak sağlayıcısı uygulama  
 Tamamlama kaynak sağlayıcısı tamamlama kaynak başlatan MEF Bileşeni parçasıdır.  
  
#### <a name="to-implement-the-completion-source-provider"></a>Tamamlama kaynak sağlayıcısını uygulamak için  
  
1.  Adlı bir sınıf ekleyin `TestCompletionSourceProvider` uygulayan <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSourceProvider>. Bu sınıf ile dışarı aktarma bir <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> "Düz" ve <xref:Microsoft.VisualStudio.Utilities.NameAttribute> "test tamamlama".  
  
     [!code-csharp[VSSDKCompletionTest#8](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletionsource.cs#8)]
     [!code-vb[VSSDKCompletionTest#8](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletionsource.vb#8)]  
  
2.  İçeri aktarma bir <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>, geçerli sözcüğü tamamlama kaynak bulmak için kullanılır.  
  
     [!code-csharp[VSSDKCompletionTest#9](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletionsource.cs#9)]
     [!code-vb[VSSDKCompletionTest#9](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletionsource.vb#9)]  
  
3.  Uygulama <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSourceProvider.TryCreateCompletionSource%2A> tamamlama kaynak örneklemek için yöntemi.  
  
     [!code-csharp[VSSDKCompletionTest#10](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletionsource.cs#10)]
     [!code-vb[VSSDKCompletionTest#10](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletionsource.vb#10)]  
  
## <a name="implementing-the-completion-command-handler-provider"></a>Tamamlama komut işleyicisi sağlayıcıyı uygulama  
 Tamamlama komut işleyicisi sağlayıcısı türetilmiş bir <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener>, bir metin görünümünü oluşturma olayını dinler ve görünümden dönüştürür bir <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>— Visual Studio Kabuğu komut zincirini komutu eklenmesini sağlar — bir için<xref:Microsoft.VisualStudio.Text.Editor.ITextView>. Bu sınıf, MEF dışarı aktarma olduğundan, bu komut işleyici kendisi tarafından gerekli hizmetleri almak için kullanabilirsiniz.  
  
#### <a name="to-implement-the-completion-command-handler-provider"></a>Tamamlama komut işleyicisi sağlayıcısını uygulamak için  
  
1.  Adlı bir dosya ekleyin `TestCompletionCommandHandler`.  
  
2.  Bu using deyimlerini ekleyin:  
  
     [!code-csharp[VSSDKCompletionTest#11](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletioncommandhandler.cs#11)]
     [!code-vb[VSSDKCompletionTest#11](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletioncommandhandler.vb#11)]  
  
3.  Adlı bir sınıf ekleyin `TestCompletionHandlerProvider` uygulayan <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener>. Bu sınıf ile dışarı aktarma bir <xref:Microsoft.VisualStudio.Utilities.NameAttribute> "belirteci tamamlama işleyicisinin" bir <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> "Düz" ve <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute> , <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Editable>.  
  
     [!code-csharp[VSSDKCompletionTest#12](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletioncommandhandler.cs#12)]
     [!code-vb[VSSDKCompletionTest#12](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletioncommandhandler.vb#12)]  
  
4.  İçeri aktarma <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService>, dönüştürme sağlayan bir <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> için bir <xref:Microsoft.VisualStudio.Text.Editor.ITextView>, <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionBroker>ve bir <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider> standart Visual Studio hizmetlerine erişim sağlayan.  
  
     [!code-csharp[VSSDKCompletionTest#13](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletioncommandhandler.cs#13)]
     [!code-vb[VSSDKCompletionTest#13](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletioncommandhandler.vb#13)]  
  
5.  Uygulama <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener.VsTextViewCreated%2A> komut işleyici örneklemek için yöntemi.  
  
     [!code-csharp[VSSDKCompletionTest#14](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletioncommandhandler.cs#14)]
     [!code-vb[VSSDKCompletionTest#14](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletioncommandhandler.vb#14)]  
  
## <a name="implementing-the-completion-command-handler"></a>Tamamlama komut işleyici uygulama  
 Deyim tamamlama tamamlayarak tetiklendiğinden uygulamalıdır <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> almak ve tetiklemek için işleme ve tamamlama Oturumu Kapat tuş vuruşları işlemek için arabirim.  
  
#### <a name="to-implement-the-completion-command-handler"></a>Tamamlama komut işleyici uygulamak için  
  
1. Adlı bir sınıf ekleyin `TestCompletionCommandHandler` uygulayan <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>:  
  
    [!code-csharp[VSSDKCompletionTest#15](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletioncommandhandler.cs#15)]
    [!code-vb[VSSDKCompletionTest#15](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletioncommandhandler.vb#15)]  
  
2. Sonraki komut işleyici (kendisine geçirdiğiniz komutu), metin görünümünü (çeşitli hizmetlere erişim sağlayan) komut işleyicisi sağlayıcı özel alanlar ekleyin ve bir tamamlama oturumu:  
  
    [!code-csharp[VSSDKCompletionTest#16](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletioncommandhandler.cs#16)]
    [!code-vb[VSSDKCompletionTest#16](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletioncommandhandler.vb#16)]  
  
3. Metin görünümünü ve sağlayıcı alanları ayarlar ve komut, komut zinciri ekler. bir oluşturucu ekleyin:  
  
    [!code-csharp[VSSDKCompletionTest#17](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletioncommandhandler.cs#17)]
    [!code-vb[VSSDKCompletionTest#17](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletioncommandhandler.vb#17)]  
  
4. Uygulama <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> boyunca komutu geçirerek yöntemi:  
  
    [!code-csharp[VSSDKCompletionTest#18](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletioncommandhandler.cs#18)]
    [!code-vb[VSSDKCompletionTest#18](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletioncommandhandler.vb#18)]  
  
5. Uygulama <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> yöntemi. Bu yöntem bir tuş vuruşu aldığında, bunlardan birini yapmanız gerekir:  
  
   - Karakter arabelleği için yazılmış ve ardından tetikleyin veya tamamlama filtre izin verir. (Bunu yazdırma karakter yapın.)  
  
   - İşleme tamamlandığında, ancak arabelleğe yazılacak karakter izin verme. (Bir tamamlama oturumu görüntülendiğinde, boşluk, sekme ve Enter bunu.)  
  
   - Bir sonraki işleyici geçirilmesi için komuta izin. (Tüm diğer komutlar.)  
  
     Bu yöntem Arabirim görüntüleyebilir de görüntülenmeyebilir olduğundan, çağrı <xref:Microsoft.VisualStudio.Shell.VsShellUtilities.IsInAutomationFunction%2A> bir Otomasyon bağlamda çağrılmaz emin olmak için:  
  
     [!code-csharp[VSSDKCompletionTest#19](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletioncommandhandler.cs#19)]
     [!code-vb[VSSDKCompletionTest#19](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletioncommandhandler.vb#19)]  
  
6. Bu kod tamamlama oturumu tetikleyen özel bir yöntemdir:  
  
    [!code-csharp[VSSDKCompletionTest#20](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletioncommandhandler.cs#20)]
    [!code-vb[VSSDKCompletionTest#20](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletioncommandhandler.vb#20)]  
  
7. Sonraki örnekte gelen abonelikten çıkma özel bir yöntemdir <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseSession.Dismissed> olay:  
  
    [!code-csharp[VSSDKCompletionTest#21](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletioncommandhandler.cs#21)]
    [!code-vb[VSSDKCompletionTest#21](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletioncommandhandler.vb#21)]  
  
## <a name="building-and-testing-the-code"></a>Oluşturma ve kod test etme  
 Bu kodu test etmek için CompletionTest Çözümü derleyin ve deneysel örneğinde çalıştırın.  
  
#### <a name="to-build-and-test-the-completiontest-solution"></a>Derleme ve CompletionTest çözümü test etmek için  
  
1.  Çözümü oluşturun.  
  
2.  Bu projede hata ayıklayıcıda çalıştırdığınızda, Visual Studio'nun ikinci bir örneğini başlatılır.  
  
3.  Bir metin dosyası oluşturun ve "Ekle" sözcüğünü içeren bir metin yazın.  
  
4.  İlk "a" ve "d" ardından yazdığınız sırada "ekleme" ve "uyarlama" içeren bir liste görüntülenmesi gerekir. Ayrıca seçildiğini dikkat edin. Başka bir "d" yazdığınızda, listenin "artık seçilen yalnızca ek olarak" içermelidir. Boşluk, sekme veya Enter tuşuna basarak "ekleme" işleme ya da Esc ya da herhangi bir tuşa yazarak listeyi kapatın.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [İzlenecek Yol: Bir İçerik Türünü Dosya Adı Uzantısına Bağlama](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)

