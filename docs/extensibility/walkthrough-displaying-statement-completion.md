---
title: 'İzlenecek yol: Deyim tamamlamayı görüntüleme | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - statement completion
ms.assetid: f3152c4e-7673-4047-a079-2326941d1c83
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: bdd96c124dafabf5584dfa13547cdea1e2b843b8
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49879330"
---
# <a name="walkthrough-display-statement-completion"></a>İzlenecek yol: Görüntü deyim tamamlama
Dil tabanlı deyim tamamlama tamamlama sağlamak istediğiniz tanımlayıcıları tanımlama ve ardından tamamlama oturumu tetiklemeden uygulayabilir. Deyim tamamlama dil hizmeti bağlamında tanımlayın, kendi dosya adı uzantısı ve içerik türünü tanımlayın ve ardından bu tür için tamamlama görüntüleyebilirsiniz. Veya mevcut bir içerik türü için tamamlama tetikleyebilirsiniz — Örneğin, "Düz". Bu izlenecek yol, içerik türü metin dosyaları olan "Düz" içerik türü için deyim tamamlama tetikleme işlemi gösterilmektedir. Kod ve XML dosyaları dahil tüm diğer içerik türleri, üst "metin" içerik türü değil.  
  
 Deyim tamamlama, belirli karakter yazarak genellikle tetiklenir — Örneğin, "kullanma" gibi bir tanımlayıcının yazmaya tarafından. Genellikle tuşlarına basarak kapatıldıktan **boşluk**, **sekmesini**, veya **Enter** seçim uygulamak için anahtar. Bir karakter tuş vuruşları için bir komut işleyici kullanarak yazarken tetiklemek için IntelliSense özellikleri uygulayabilirsiniz ( <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> arabirimi) ve uygulayan bir işleyici sağlayıcısı <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> arabirimi. Tamamlama katılan tanımlayıcıları listesi olan tamamlama kaynak oluşturmak için uygulaması <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource> arabirimi ve bir tamamlanma kaynak sağlayıcısı ( <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSourceProvider> arabirimi). Bileşen parçalarına Yönetilen Genişletilebilirlik Çerçevesi (MEF) sağlayıcılarıdır. Kaynak ve denetleyici sınıfları dışarı aktarma ve Hizmetleri ve aracıları alma sorumlu oldukları — Örneğin, <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>, metin arabelleği gezinme sağlar ve <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionBroker>, tamamlama oturumu tetikler.  
  
 Bu izlenecek yol, sabit kodlanmış bir tanımlayıcılar için ifade tamamlama uygulamak gösterilmektedir. Dil hizmeti ve dil belgeleri tam uygulamalarında, bu içeriği sağlamak için yükümlü olursunuz.  
  
## <a name="prerequisites"></a>Önkoşullar  
 Visual Studio 2015'ten başlayarak, Visual Studio SDK İndirme Merkezi'nden yüklemeyin. Visual Studio kurulumunda isteğe bağlı bir özellik eklemiştir. VS SDK'yi daha sonra yükleyebilirsiniz. Daha fazla bilgi için [Visual Studio SDK'yı yükleme](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="create-a-mef-project"></a>MEF proje oluşturma  
  
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
  
## <a name="implement-the-completion-source"></a>Tamamlama kaynak uygulama  
 Tamamlama kaynak tanımlayıcıları Kümesi toplanıyor ve bir kullanıcı, bir tanımlayıcının ilk harflerini gibi bir tamamlanma tetikleyicisi yazdığında tamamlama penceresini için içerik ekleme sorumludur. Bu örnekte, sabit kodlanmış tanımlayıcıları ve açıklamalarının <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource.AugmentCompletionSession%2A> yöntemi. Çoğu gerçek kullanım dilinizin ayrıştırıcı, tamamlanma listesini doldurmak için belirteçlerini almak için kullanırsınız.  
  
### <a name="to-implement-the-completion-source"></a>Tamamlama kaynak uygulamak için  
  
1.  Bir sınıf dosyası ekleyin ve adlandırın `TestCompletionSource`.  
  
2.  Aşağıdaki içeri aktarmaları ekleyin:  
  
     [!code-csharp[VSSDKCompletionTest#1](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_1.cs)]
     [!code-vb[VSSDKCompletionTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_1.vb)]  
  
3.  Sınıf bildirimi için değiştirme `TestCompletionSource` uygular, böylece <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource>:  
  
     [!code-csharp[VSSDKCompletionTest#2](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_2.cs)]
     [!code-vb[VSSDKCompletionTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_2.vb)]  
  
4.  Kaynak sağlayıcısı, metin arabelleği ve bir listesi için özel alanlar ekleyin <xref:Microsoft.VisualStudio.Language.Intellisense.Completion> (tamamlama oturumu katılacak tanımlayıcıları karşılık gelir) nesneler:  
  
     [!code-csharp[VSSDKCompletionTest#3](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_3.cs)]
     [!code-vb[VSSDKCompletionTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_3.vb)]  
  
5.  Kaynak sağlayıcısı ve arabellek ayarlayan bir oluşturucu ekleyin. `TestCompletionSourceProvider` Sınıfı, sonraki adımlarda tanımlanır:  
  
     [!code-csharp[VSSDKCompletionTest#4](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_4.cs)]
     [!code-vb[VSSDKCompletionTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_4.vb)]  
  
6.  Uygulama <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource.AugmentCompletionSession%2A> bağlamında sağlamak istediğiniz tamamlamaları içeren bir tamamlama kümesi ekleyerek yöntemi. Her bir tamamlama kümesi içerir <xref:Microsoft.VisualStudio.Language.Intellisense.Completion> tamamlamaları, bir tamamlama penceresini sekmesine karşılık gelir. (Visual Basic projelerinde tamamlama penceresini sekmeleri adlandırılır **ortak** ve **tüm**.) `FindTokenSpanAtPosition` Yöntemi, bir sonraki adımda tanımlanır.  
  
     [!code-csharp[VSSDKCompletionTest#5](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_5.cs)]
     [!code-vb[VSSDKCompletionTest#5](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_5.vb)]  
  
7.  Aşağıdaki yöntem, imleç konumundan geçerli kelimenin bulmak için kullanılır:  
  
     [!code-csharp[VSSDKCompletionTest#6](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_6.cs)]
     [!code-vb[VSSDKCompletionTest#6](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_6.vb)]  
  
8.  Uygulama `Dispose()` yöntemi:  
  
     [!code-csharp[VSSDKCompletionTest#7](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_7.cs)]
     [!code-vb[VSSDKCompletionTest#7](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_7.vb)]  
  
## <a name="implement-the-completion-source-provider"></a>Tamamlama kaynak sağlayıcısını uygulama  
 Tamamlama kaynak sağlayıcısı tamamlama kaynak başlatan MEF Bileşeni parçasıdır.  
  
### <a name="to-implement-the-completion-source-provider"></a>Tamamlama kaynak sağlayıcısını uygulamak için  
  
1.  Adlı bir sınıf ekleyin `TestCompletionSourceProvider` uygulayan <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSourceProvider>. Bu sınıf ile dışarı aktarma bir <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> "Düz" ve <xref:Microsoft.VisualStudio.Utilities.NameAttribute> "test tamamlama".  
  
     [!code-csharp[VSSDKCompletionTest#8](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_8.cs)]
     [!code-vb[VSSDKCompletionTest#8](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_8.vb)]  
  
2.  İçeri aktarma bir <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>, tamamlama kaynakta geçerli kelimenin bulur.  
  
     [!code-csharp[VSSDKCompletionTest#9](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_9.cs)]
     [!code-vb[VSSDKCompletionTest#9](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_9.vb)]  
  
3.  Uygulama <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSourceProvider.TryCreateCompletionSource%2A> tamamlama kaynak örneklemek için yöntemi.  
  
     [!code-csharp[VSSDKCompletionTest#10](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_10.cs)]
     [!code-vb[VSSDKCompletionTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_10.vb)]  
  
## <a name="implement-the-completion-command-handler-provider"></a>Tamamlama komut işleyicisi sağlayıcıyı uygulama  
 Tamamlama komut işleyicisi sağlayıcısı türetilmiş bir <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener>, bir metin görünümünü oluşturma olayını dinler ve görünümden dönüştürür bir <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>— Visual Studio Kabuğu komut zincirini komutu eklenmesini sağlar — bir için<xref:Microsoft.VisualStudio.Text.Editor.ITextView>. Bu sınıf, MEF dışarı aktarma olduğundan, bu komut işleyici kendisi tarafından gerekli hizmetleri almak için kullanabilirsiniz.  
  
#### <a name="to-implement-the-completion-command-handler-provider"></a>Tamamlama komut işleyicisi sağlayıcısını uygulamak için  
  
1.  Adlı bir dosya ekleyin `TestCompletionCommandHandler`.  
  
2.  Bu using deyimlerini ekleyin:  
  
     [!code-csharp[VSSDKCompletionTest#11](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_11.cs)]
     [!code-vb[VSSDKCompletionTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_11.vb)]  
  
3.  Adlı bir sınıf ekleyin `TestCompletionHandlerProvider` uygulayan <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener>. Bu sınıf ile dışarı aktarma bir <xref:Microsoft.VisualStudio.Utilities.NameAttribute> "belirteci tamamlama işleyicisinin" bir <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> "Düz" ve <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute> , <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Editable>.  
  
     [!code-csharp[VSSDKCompletionTest#12](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_12.cs)]
     [!code-vb[VSSDKCompletionTest#12](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_12.vb)]  
  
4.  İçeri aktarma <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService>, dönüştürme sağlayan bir <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> için bir <xref:Microsoft.VisualStudio.Text.Editor.ITextView>, <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionBroker>ve bir <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider> standart Visual Studio hizmetlerine erişim sağlayan.  
  
     [!code-csharp[VSSDKCompletionTest#13](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_13.cs)]
     [!code-vb[VSSDKCompletionTest#13](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_13.vb)]  
  
5.  Uygulama <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener.VsTextViewCreated%2A> komut işleyici örneklemek için yöntemi.  
  
     [!code-csharp[VSSDKCompletionTest#14](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_14.cs)]
     [!code-vb[VSSDKCompletionTest#14](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_14.vb)]  
  
## <a name="implement-the-completion-command-handler"></a>Uygulama tamamlama komut işleyicisi  
 Deyim tamamlama tamamlayarak tetiklendiğinden uygulamalıdır <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> almak ve tetiklemek için işleme ve tamamlama Oturumu Kapat tuş vuruşları işlemek için arabirim.  
  
#### <a name="to-implement-the-completion-command-handler"></a>Tamamlama komut işleyici uygulamak için  
  
1. Adlı bir sınıf ekleyin `TestCompletionCommandHandler` uygulayan <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>:  
  
    [!code-csharp[VSSDKCompletionTest#15](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_15.cs)]
    [!code-vb[VSSDKCompletionTest#15](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_15.vb)]  
  
2. Sonraki komut işleyici (kendisine geçirdiğiniz komutu), metin görünümünü (çeşitli hizmetlere erişim sağlayan) komut işleyicisi sağlayıcı özel alanlar ekleyin ve bir tamamlama oturumu:  
  
    [!code-csharp[VSSDKCompletionTest#16](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_16.cs)]
    [!code-vb[VSSDKCompletionTest#16](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_16.vb)]  
  
3. Metin görünümünü ve sağlayıcı alanları ayarlar ve komut, komut zinciri ekler. bir oluşturucu ekleyin:  
  
    [!code-csharp[VSSDKCompletionTest#17](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_17.cs)]
    [!code-vb[VSSDKCompletionTest#17](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_17.vb)]  
  
4. Uygulama <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> boyunca komutu geçirerek yöntemi:  
  
    [!code-csharp[VSSDKCompletionTest#18](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_18.cs)]
    [!code-vb[VSSDKCompletionTest#18](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_18.vb)]  
  
5. Uygulama <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> yöntemi. Bu yöntem bir tuş vuruşu aldığında, bunlardan birini yapmanız gerekir:  
  
   - Karakter arabelleği için yazılmış ve ardından tetikleyin veya tamamlama filtre izin verir. (Bunu yazdırma karakter yapın.)  
  
   - İşleme tamamlandığında, ancak arabelleğe yazılacak karakter izin verme. (Boşluk, **sekmesini**, ve **Enter** tamamlama oturumu görüntülendiğinde bunu.)  
  
   - Bir sonraki işleyici geçirilmesi için komuta izin. (Tüm diğer komutlar.)  
  
     Bu yöntem Arabirim görüntüleyebilir de görüntülenmeyebilir olduğundan, çağrı <xref:Microsoft.VisualStudio.Shell.VsShellUtilities.IsInAutomationFunction%2A> bir Otomasyon bağlamda çağrılmaz emin olmak için:  
  
     [!code-csharp[VSSDKCompletionTest#19](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_19.cs)]
     [!code-vb[VSSDKCompletionTest#19](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_19.vb)]  
  
6. Bu kod tamamlama oturumu tetikleyen özel bir yöntemdir:  
  
    [!code-csharp[VSSDKCompletionTest#20](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_20.cs)]
    [!code-vb[VSSDKCompletionTest#20](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_20.vb)]  
  
7. Sonraki örnekte gelen abonelikten çıkma özel bir yöntemdir <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseSession.Dismissed> olay:  
  
    [!code-csharp[VSSDKCompletionTest#21](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_21.cs)]
    [!code-vb[VSSDKCompletionTest#21](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_21.vb)]  
  
## <a name="build-and-test-the-code"></a>Kod oluşturup test  
 Bu kodu test etmek için CompletionTest Çözümü derleyin ve deneysel örneğinde çalıştırın.  
  
#### <a name="to-build-and-test-the-completiontest-solution"></a>Derleme ve CompletionTest çözümü test etmek için  
  
1.  Çözümü oluşturun.  
  
2.  Bu projede hata ayıklayıcıda çalıştırdığınızda, Visual Studio'nun ikinci bir örneğini başlatılır.  
  
3.  Bir metin dosyası oluşturun ve "Ekle" sözcüğünü içeren bir metin yazın.  
  
4.  "Ekleme" ve "uyarlama" içeren bir listeyi ilk "a" ve "d" ardından yazdığınız sırada görünmelidir. Ayrıca seçildiğini dikkat edin. Başka bir "d" yazdığınızda, listenin "artık seçilen yalnızca ek olarak" içermelidir. Tuşlarına basarak "ekleme" taahhüdünde **boşluk**, **sekmesini**, veya **Enter** anahtar ya da Esc ya da herhangi bir tuşa yazarak listeyi kapatın.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [İzlenecek yol: bir içerik türü için bir dosya adı uzantısına bağlama](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)