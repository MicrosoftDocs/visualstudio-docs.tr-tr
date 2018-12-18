---
title: 'İzlenecek yol: İmza yardımını görüntüleme | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - signature help/parameter info
ms.assetid: 4a6a884b-5730-4b54-9264-99684f5b523c
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: cc260fe45bf4c6cf801718c2f4c3bbaa98842dd6
ms.sourcegitcommit: 1c2ed640512ba613b3bbbc9ce348e28be6ca3e45
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/03/2018
ms.locfileid: "39498914"
---
# <a name="walkthrough-display-signature-help"></a>İzlenecek yol: İmza Yardımı görüntüleme
İmza Yardımı (diğer adıyla *parametre bilgisi*) kullanıcı parametre listesi başlangıç karakteri (genellikle bir açma ayracı) yazdığında bir yöntem imzası bir araç ipucunda görüntüler. Bir parametre ve parametre ayırıcı (genellikle bir virgül) yazılı olarak araç ipucu bir sonraki parametreyi kalın olarak göstermek için güncelleştirilir. Aşağıdaki yollarla imza Yardımı tanımlayabilirsiniz: bir dil hizmeti bağlamında, kendi dosya adı uzantısı ve içerik türünü tanımlayın ve bu tür için imza Yardımı'nı görüntülemek veya mevcut bir içerik türünü (örneğin, "metin") için imza Yardımı'nı görüntülemek. Bu yönerge "metin" içerik türü için imza Yardımı'nı görüntülemek nasıl gösterir.  
  
 İmza Yardımı, belirli bir karakterin, örneğin, yazarak genellikle tetiklenir "(" (açılış ayracı) ve başka bir karakter yazarak kapatılır ")" (kapanış parantezi). Bir karakter yazarak tetiklenen IntelliSense özellikleri tuş vuruşları için bir komut işleyici kullanarak uygulanabilir ( <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> arabirimi) ve uygulayan bir işleyici sağlayıcısı <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> arabirimi. İmza Yardımı'ndaki katılan imzaları listesidir, imza Yardım kaynak oluşturmak için uygulaması <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource> arabirimi ve çalıştıran bir kaynak sağlayıcısı <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSourceProvider> arabirimi. Sağlayıcılar Yönetilen Genişletilebilirlik Çerçevesi (MEF) bileşeni bölümleri ve kaynak ve denetleyici sınıfları dışarı aktarma ve Hizmetleri ve aracıları, örneğin, içeri aktarma sorumlu <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>, metin arabelleğinde ulaşmanıza olanak sağlayan ve <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpBroker>, imza Yardım oturumu tetikler.  
  
 Bu izlenecek yol, imza Yardım tanımlayıcıları için sabit kodlanmış kümesi ayarlama işlemi gösterilmektedir. Tam uygulamalarında, dil içeriği sağlamaktan sorumludur.  
  
## <a name="prerequisites"></a>Önkoşullar  
 Visual Studio 2015'ten başlayarak, Visual Studio SDK İndirme Merkezi'nden yüklemeyin. Visual Studio kurulumunda isteğe bağlı bir özellik eklemiştir. VS SDK'yi daha sonra yükleyebilirsiniz. Daha fazla bilgi için [Visual Studio SDK'yı yükleme](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-mef-project"></a>MEF proje oluşturma  
  
#### <a name="to-create-a-mef-project"></a>MEF projesi oluşturmak için  
  
1.  Bir C# VSIX projesi oluşturun. (İçinde **yeni proje** iletişim kutusunda **Visual C# / genişletilebilirlik**, ardından **VSIX projesi**.) Çözüm adı `SignatureHelpTest`.  
  
2.  Bir düzenleyici sınıflandırıcı öğe şablonu, projeye ekleyin. Daha fazla bilgi için [bir düzenleyici öğesi şablonuyla uzantı oluşturma](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
3.  Varolan sınıf dosyaları silin.  
  
4.  Aşağıdaki başvuruları projeye ekleyin ve doğrulayın **CopyLocal** ayarlanır `false`:  
  
     Microsoft.VisualStudio.Editor  
  
     Microsoft.VisualStudio.Language.Intellisense  
  
     Microsoft.VisualStudio.OLE.Interop  
  
     Microsoft.VisualStudio.Shell.14.0  
  
     Microsoft.VisualStudio.TextManager.Interop  
  
## <a name="implement-signature-help-signatures-and-parameters"></a>İmza Yardımı imzalar ve parametreleri  
 İmza Yardımı kaynak uygulayan imzalarını dayanır <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature>, her biri uygulayan parametreleri içeren <xref:Microsoft.VisualStudio.Language.Intellisense.IParameter>. Tam bir uygulama bu bilgileri, dil belgelerinden alınabileceğinden, ancak bu örnekte, sabit kodlanmış imzalar.  
  
#### <a name="to-implement-the-signature-help-signatures-and-parameters"></a>Parametreleri ve imza Yardımı imzaları uygulamak için  
  
1.  Bir sınıf dosyası ekleyin ve adlandırın `SignatureHelpSource`.  
  
2.  Aşağıdaki içeri aktarmaları ekleyin.  
  
     [!code-vb[VSSDKSignatureHelpTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_1.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#1](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_1.cs)]  
  
3.  Adlı bir sınıf ekleyin `TestParameter` uygulayan <xref:Microsoft.VisualStudio.Language.Intellisense.IParameter>.  
  
     [!code-vb[VSSDKSignatureHelpTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_2.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#2](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_2.cs)]  
  
4.  Tüm özellikleri ayarlayan bir oluşturucu ekleyin.  
  
     [!code-vb[VSSDKSignatureHelpTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_3.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#3](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_3.cs)]  
  
5.  Özelliklerini eklemek <xref:Microsoft.VisualStudio.Language.Intellisense.IParameter>.  
  
     [!code-vb[VSSDKSignatureHelpTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_4.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#4](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_4.cs)]  
  
6.  Adlı bir sınıf ekleyin `TestSignature` uygulayan <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature>.  
  
     [!code-vb[VSSDKSignatureHelpTest#5](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_5.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#5](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_5.cs)]  
  
7.  Bazı özel alanlar ekleyin.  
  
     [!code-vb[VSSDKSignatureHelpTest#6](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_6.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#6](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_6.cs)]  
  
8.  Alanları ayarlayan ve abone olduğu bir oluşturucu ekleyin <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> olay.  
  
     [!code-vb[VSSDKSignatureHelpTest#7](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_7.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#7](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_7.cs)]  
  
9. Bildirme bir `CurrentParameterChanged` olay. Parametrelerden biri imzasında kullanıcı doldurur bu olay tetiklenir.  
  
     [!code-vb[VSSDKSignatureHelpTest#8](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_8.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#8](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_8.cs)]  
  
10. Uygulama <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature.CurrentParameter%2A> BT'nin harekete geçirmeyecek şekilde özelliği `CurrentParameterChanged` özellik değeri değiştiğinde bir olay.  
  
     [!code-vb[VSSDKSignatureHelpTest#9](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_9.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#9](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_9.cs)]  
  
11. Başlatan bir yöntem ekleyin `CurrentParameterChanged` olay.  
  
     [!code-vb[VSSDKSignatureHelpTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_10.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#10](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_10.cs)]  
  
12. Geçerli parametre sayısı virgül, karşılaştırarak hesaplar bir yöntem ekleyin <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature.ApplicableToSpan%2A> imzasında virgül sayısı.  
  
     [!code-vb[VSSDKSignatureHelpTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_11.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#11](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_11.cs)]  
  
13. İçin bir olay işleyicisi ekleme <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> çağıran olay `ComputeCurrentParameter()` yöntemi.  
  
     [!code-vb[VSSDKSignatureHelpTest#12](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_12.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#12](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_12.cs)]  
  
14. Uygulama <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature.ApplicableToSpan%2A> özelliği. Bu özellik tutan bir <xref:Microsoft.VisualStudio.Text.ITrackingSpan> karşılık gelen imza uygulandığı arabellekteki metni aralık.  
  
     [!code-vb[VSSDKSignatureHelpTest#13](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_13.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#13](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_13.cs)]  
  
15. Diğer parametreler uygulayın.  
  
     [!code-vb[VSSDKSignatureHelpTest#14](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_14.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#14](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_14.cs)]  
  
## <a name="implement-the-signature-help-source"></a>İmza Yardımı kaynak uygulama  
 İmza Yardımı kaynak bilgi verdiğiniz imza kümesidir.  
  
#### <a name="to-implement-the-signature-help-source"></a>İmza Yardımı kaynak uygulamak için  
  
1.  Adlı bir sınıf ekleyin `TestSignatureHelpSource` uygulayan <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource>.  
  
     [!code-vb[VSSDKSignatureHelpTest#15](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_15.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#15](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_15.cs)]  
  
2.  Metin arabelleği için bir başvuru ekleyin.  
  
     [!code-vb[VSSDKSignatureHelpTest#16](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_16.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#16](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_16.cs)]  
  
3.  Metin arabelleği ve imza Yardımı kaynak sağlayıcısı ayarlar bir oluşturucu ekleyin.  
  
     [!code-vb[VSSDKSignatureHelpTest#17](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_17.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#17](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_17.cs)]  
  
4.  Uygulama <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource.AugmentSignatureHelpSession%2A> yöntemi. Bu örnekte, sabit kodlanmış imzalar, ancak tam bir uygulamada dil belgelerinden bu bilgileri elde edersiniz.  
  
     [!code-vb[VSSDKSignatureHelpTest#18](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_18.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#18](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_18.cs)]  
  
5.  Yardımcı yöntemi `CreateSignature()` çizim için sağlanmıştır.  
  
     [!code-vb[VSSDKSignatureHelpTest#19](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_19.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#19](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_19.cs)]  
  
6.  Uygulama <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource.GetBestMatch%2A> yöntemi. Bu örnekte, her biri iki parametreye sahip iki imzalar vardır. Bu nedenle, bu yöntem gerekli değil. İmza Yardımı birden fazla kaynak kullanılabilir bir bileşen uygulamasında, bu yöntem, imza Yardım en yüksek öncelikli kaynak eşleşen bir imza verebilirsiniz karar vermek için kullanılır. Erişilemiyorsa yöntemi null değerini döndürür ve next-en yüksek öncelikli kaynak bir eşleşme sağlamanız istenir.  
  
     [!code-vb[VSSDKSignatureHelpTest#20](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_20.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#20](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_20.cs)]  
  
7.  Uygulama `Dispose()` yöntemi:  
  
     [!code-vb[VSSDKSignatureHelpTest#21](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_21.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#21](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_21.cs)]  
  
## <a name="implement-the-signature-help-source-provider"></a>İmza Yardımı kaynak sağlayıcısını uygulama  
 İmza Yardımı kaynak sağlayıcısı, Yönetilen Genişletilebilirlik Çerçevesi (MEF) bileşen parçası dışarı aktarma ve imza Yardımı kaynak oluşturmak için sorumludur.  
  
#### <a name="to-implement-the-signature-help-source-provider"></a>İmza Yardımı kaynak sağlayıcısını uygulamak için  
  
1.  Adlı bir sınıf ekleyin `TestSignatureHelpSourceProvider` uygulayan <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSourceProvider>ve ile dışarı aktarın bir <xref:Microsoft.VisualStudio.Utilities.NameAttribute>, <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> "metin" ve <xref:Microsoft.VisualStudio.Utilities.OrderAttribute> , önce = "varsayılan".  
  
     [!code-vb[VSSDKSignatureHelpTest#22](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_22.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#22](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_22.cs)]  
  
2.  Uygulama <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSourceProvider.TryCreateSignatureHelpSource%2A> örnekleme tarafından `TestSignatureHelpSource`.  
  
     [!code-vb[VSSDKSignatureHelpTest#23](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_23.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#23](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_23.cs)]  
  
## <a name="implement-the-command-handler"></a>Komut işleyici uygulamak  
 İmza Yardımı ardına bir sol ayraç genellikle tetiklenir "(" karakteri ve bir kapatma ayracı tarafından kapatıldı")" karakter. Çalıştırarak bu tuş vuruşları işleyebilen bir <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> böylece bir imza Yardım oturumu açma aldığında tetikler parantezi karakterinde bir bilinen bir yöntem adını izlediği ve bir kapanış aldığında oturum kapatılana parantez karakteri.  
  
#### <a name="to-implement-the-command-handler"></a>Komut işleyici uygulamak için  
  
1.  Adlı bir sınıf ekleyin `TestSignatureHelpCommand` uygulayan <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>.  
  
     [!code-vb[VSSDKSignatureHelpTest#24](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_24.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#24](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_24.cs)]  
  
2.  İçin özel alanlar ekleme <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> (Bu komuta zincirini işleyicilere komut işleyici eklemenize olanak sağlayan) bağdaştırıcısı, metin görünümünü, imza Yardım aracısı ve oturumu bir <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigator>ve sonraki <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>.  
  
     [!code-vb[VSSDKSignatureHelpTest#25](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_25.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#25](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_25.cs)]  
  
3.  Bu alanlar ve komuta zincirini filtrelerde komut filtre eklemek için bir oluşturucu ekleyin.  
  
     [!code-vb[VSSDKSignatureHelpTest#26](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_26.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#26](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_26.cs)]  
  
4.  Uygulama <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> komut filtre bir açma ayracı aldığında imza Yardım oturumu tetiklemek için yöntemi "(" karakteri sonra bilinen bir yöntem adlarını ve bir kapatma ayracı aldığında oturumu kapatmak için")" karakteri oturumu hala etkinken. Her durumda komutu iletilir.  
  
     [!code-vb[VSSDKSignatureHelpTest#27](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_27.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#27](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_27.cs)]  
  
5.  Uygulama <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> BT'nin her zaman komut iletir için yöntemi.  
  
     [!code-vb[VSSDKSignatureHelpTest#28](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_28.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#28](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_28.cs)]  
  
## <a name="implement-the-signature-help-command-provider"></a>İmza Yardımı komut sağlayıcıyı uygulama  
 İmza Help komutunu uygulayarak sağlayabilir <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> metni görünümü oluşturulduğunda komut işleyicisi oluşturmak için.  
  
### <a name="to-implement-the-signature-help-command-provider"></a>İmza Yardımı komutu sağlayıcısı uygulamak için  
  
1.  Adlı bir sınıf ekleyin `TestSignatureHelpController` uygulayan <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> ve ile dışarı aktarın <xref:Microsoft.VisualStudio.Utilities.NameAttribute>, <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>, ve <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute>.  
  
     [!code-vb[VSSDKSignatureHelpTest#29](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_29.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#29](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_29.cs)]  
  
2.  İçeri aktarma <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService> (almak için kullanılan <xref:Microsoft.VisualStudio.Text.Editor.ITextView>, verilen <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> nesne), <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> (geçerli kelimenin bulmak için kullanılan) ve <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpBroker> (imza Yardım oturumu tetiklemek için).  
  
     [!code-vb[VSSDKSignatureHelpTest#30](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_30.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#30](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_30.cs)]  
  
3.  Uygulama <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener.VsTextViewCreated%2A> örnekleme yöntemi `TestSignatureCommandHandler`.  
  
     [!code-vb[VSSDKSignatureHelpTest#31](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_31.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#31](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_31.cs)]  
  
## <a name="build-and-test-the-code"></a>Kod oluşturup Test  
 Bu kodu test etmek için SignatureHelpTest Çözümü derleyin ve deneysel örneğinde çalıştırın.  
  
#### <a name="to-build-and-test-the-signaturehelptest-solution"></a>Derleme ve SignatureHelpTest çözümü test etmek için  
  
1.  Çözümü oluşturun.  
  
2.  Bu projede hata ayıklayıcıda çalıştırdığınızda, Visual Studio'nun ikinci bir örneğini başlatılır.  
  
3.  Bir metin dosyası türü "Ekle" sözcüğünü içeren metin ve yanı sıra bir açma ayracı oluşturun.  
  
4.  Açma parantezinden yazdıktan sonra iki imzaları listesini görüntüleyen bir araç ipucu görmelisiniz `add()` yöntemi.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [İzlenecek yol: bir içerik türü için bir dosya adı uzantısına bağlama](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)