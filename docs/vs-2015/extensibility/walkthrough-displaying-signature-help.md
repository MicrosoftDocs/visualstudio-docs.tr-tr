---
title: 'İzlenecek yol: İmza yardımını görüntüleme | Microsoft Docs'
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
- editors [Visual Studio SDK], new - signature help/parameter info
ms.assetid: 4a6a884b-5730-4b54-9264-99684f5b523c
caps.latest.revision: 29
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 7a3b902c32563da6bc21778a09b4aeaebaeabeaa
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51734636"
---
# <a name="walkthrough-displaying-signature-help"></a>İzlenecek Yol: İmza Yardımını Görüntüleme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

İmza Yardımı (diğer adıyla *parametre bilgisi*) kullanıcı parametre listesi başlangıç karakteri (genellikle bir açma ayracı) yazdığında bir yöntem imzası bir araç ipucunda görüntüler. Bir parametre ve parametre ayırıcı (genellikle bir virgül) yazılı olarak araç ipucu bir sonraki parametreyi kalın olarak göstermek için güncelleştirilir. Bir dil hizmeti bağlamında imza Yardımı tanımlayabilirsiniz kendi dosya adı uzantısı ve içerik türünü tanımlayın ve bu tür için imza Yardımı'nı görüntülemek veya mevcut bir içerik türünü (örneğin, "metin") için imza Yardım görüntüleyebilirsiniz. Bu yönerge "metin" içerik türü için imza Yardımı'nı görüntülemek nasıl gösterir.  
  
 İmza Yardımı, belirli bir karakterin, örneğin, yazarak genellikle tetiklenir "(" (açılış ayracı) ve başka bir karakter yazarak kapatılır ")" (kapanış parantezi). Bir karakter yazarak tetiklenen IntelliSense özellikleri tuş vuruşları için bir komut işleyici kullanarak uygulanabilir ( <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> arabirimi) ve uygulayan bir işleyici sağlayıcısı <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> arabirimi. İmza Yardımı'ndaki katılan imzaları listesidir, imza Yardım kaynak oluşturmak için uygulaması <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource> arabirimi ve uygulayan bir kaynak sağlayıcısı <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSourceProvider> arabirimi. Sağlayıcılar Yönetilen Genişletilebilirlik Çerçevesi (MEF) bileşeni bölümleri ve kaynak ve denetleyici sınıfları dışarı aktarma ve Hizmetleri ve aracıları, örneğin, içeri aktarma sorumlu <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>, metin arabelleğinde ulaşmanıza olanak sağlayan ve <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpBroker>, imza Yardım oturumu tetikler.  
  
 Bu izlenecek yol tanımlayıcıları sabit kodlanmış kümesi için imza Yardımı'nı uygulamak nasıl gösterir. Tam uygulamalarında, dil içeriği sağlamaktan sorumludur.  
  
## <a name="prerequisites"></a>Önkoşullar  
 Visual Studio 2015'ten başlayarak, size Visual Studio SDK İndirme Merkezi'nden yüklemeyin. Visual Studio kurulumunda isteğe bağlı bir özellik olarak eklenmiştir. VS SDK'yi daha sonra yükleyebilirsiniz. Daha fazla bilgi için [Visual Studio SDK'sını yükleme](../extensibility/installing-the-visual-studio-sdk.md).  
  
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
  
## <a name="implementing-signature-help-signatures-and-parameters"></a>İmza uygulama imzalar ve parametreleri yardımcı olur.  
 İmza Yardımı kaynak uygulayan imzalarını dayanır <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature>, her biri uygulayan parametreleri içeren <xref:Microsoft.VisualStudio.Language.Intellisense.IParameter>. Tam bir uygulama bu bilgileri, dil belgelerinden alınabileceğinden, ancak bu örnekte, sabit kodlanmış imzalar.  
  
#### <a name="to-implement-the-signature-help-signatures-and-parameters"></a>Parametreleri ve imza Yardımı imzaları uygulamak için  
  
1.  Bir sınıf dosyası ekleyin ve adlandırın `SignatureHelpSource`.  
  
2.  Aşağıdaki içeri aktarmaları ekleyin.  
  
     [!code-csharp[VSSDKSignatureHelpTest#1](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#1)]
     [!code-vb[VSSDKSignatureHelpTest#1](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#1)]  
  
3.  Adlı bir sınıf ekleyin `TestParameter` uygulayan <xref:Microsoft.VisualStudio.Language.Intellisense.IParameter>.  
  
     [!code-csharp[VSSDKSignatureHelpTest#2](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#2)]
     [!code-vb[VSSDKSignatureHelpTest#2](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#2)]  
  
4.  Tüm özellikleri ayarlayan bir oluşturucu ekleyin.  
  
     [!code-csharp[VSSDKSignatureHelpTest#3](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#3)]
     [!code-vb[VSSDKSignatureHelpTest#3](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#3)]  
  
5.  Özelliklerini eklemek <xref:Microsoft.VisualStudio.Language.Intellisense.IParameter>.  
  
     [!code-csharp[VSSDKSignatureHelpTest#4](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#4)]
     [!code-vb[VSSDKSignatureHelpTest#4](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#4)]  
  
6.  Adlı bir sınıf ekleyin `TestSignature` uygulayan <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature>.  
  
     [!code-csharp[VSSDKSignatureHelpTest#5](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#5)]
     [!code-vb[VSSDKSignatureHelpTest#5](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#5)]  
  
7.  Bazı özel alanlar ekleyin.  
  
     [!code-csharp[VSSDKSignatureHelpTest#6](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#6)]
     [!code-vb[VSSDKSignatureHelpTest#6](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#6)]  
  
8.  Alanları ayarlayan ve abone olduğu bir oluşturucu ekleyin <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> olay.  
  
     [!code-csharp[VSSDKSignatureHelpTest#7](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#7)]
     [!code-vb[VSSDKSignatureHelpTest#7](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#7)]  
  
9. Bildirme bir `CurrentParameterChanged` olay. Parametrelerden biri imzasında kullanıcı doldurur bu olay tetiklenir.  
  
     [!code-csharp[VSSDKSignatureHelpTest#8](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#8)]
     [!code-vb[VSSDKSignatureHelpTest#8](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#8)]  
  
10. Uygulama <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature.CurrentParameter%2A> BT'nin harekete geçirmeyecek şekilde özelliği `CurrentParameterChanged` özellik değeri değiştiğinde bir olay.  
  
     [!code-csharp[VSSDKSignatureHelpTest#9](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#9)]
     [!code-vb[VSSDKSignatureHelpTest#9](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#9)]  
  
11. Başlatan bir yöntem ekleyin `CurrentParameterChanged` olay.  
  
     [!code-csharp[VSSDKSignatureHelpTest#10](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#10)]
     [!code-vb[VSSDKSignatureHelpTest#10](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#10)]  
  
12. Geçerli parametre sayısı virgül, karşılaştırarak hesaplar bir yöntem ekleyin <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature.ApplicableToSpan%2A> imzasında virgül sayısı.  
  
     [!code-csharp[VSSDKSignatureHelpTest#11](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#11)]
     [!code-vb[VSSDKSignatureHelpTest#11](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#11)]  
  
13. İçin bir olay işleyicisi ekleme <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> çağıran olay `ComputeCurrentParameter()` yöntemi.  
  
     [!code-csharp[VSSDKSignatureHelpTest#12](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#12)]
     [!code-vb[VSSDKSignatureHelpTest#12](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#12)]  
  
14. Uygulama <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature.ApplicableToSpan%2A> özelliği. Bu özellik tutan bir <xref:Microsoft.VisualStudio.Text.ITrackingSpan> karşılık gelen imza uygulandığı arabellekteki metni aralık.  
  
     [!code-csharp[VSSDKSignatureHelpTest#13](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#13)]
     [!code-vb[VSSDKSignatureHelpTest#13](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#13)]  
  
15. Diğer parametreler uygulayın.  
  
     [!code-csharp[VSSDKSignatureHelpTest#14](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#14)]
     [!code-vb[VSSDKSignatureHelpTest#14](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#14)]  
  
## <a name="implementing-the-signature-help-source"></a>İmza Yardımı kaynağı uygulama  
 İmza Yardımı kaynak bilgi verdiğiniz imza kümesidir.  
  
#### <a name="to-implement-the-signature-help-source"></a>İmza Yardımı kaynak uygulamak için  
  
1.  Adlı bir sınıf ekleyin `TestSignatureHelpSource` uygulayan <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource>.  
  
     [!code-csharp[VSSDKSignatureHelpTest#15](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#15)]
     [!code-vb[VSSDKSignatureHelpTest#15](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#15)]  
  
2.  Metin arabelleği için bir başvuru ekleyin.  
  
     [!code-csharp[VSSDKSignatureHelpTest#16](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#16)]
     [!code-vb[VSSDKSignatureHelpTest#16](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#16)]  
  
3.  Metin arabelleği ve imza Yardımı kaynak sağlayıcısı ayarlar bir oluşturucu ekleyin.  
  
     [!code-csharp[VSSDKSignatureHelpTest#17](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#17)]
     [!code-vb[VSSDKSignatureHelpTest#17](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#17)]  
  
4.  Uygulama <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource.AugmentSignatureHelpSession%2A> yöntemi. Bu örnekte, sabit kodlanmış imzalar, ancak tam bir uygulamada dil belgelerinden bu bilgileri elde edersiniz.  
  
     [!code-csharp[VSSDKSignatureHelpTest#18](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#18)]
     [!code-vb[VSSDKSignatureHelpTest#18](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#18)]  
  
5.  Yardımcı yöntemi `CreateSignature()` çizim için sağlanmıştır.  
  
     [!code-csharp[VSSDKSignatureHelpTest#19](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#19)]
     [!code-vb[VSSDKSignatureHelpTest#19](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#19)]  
  
6.  Uygulama <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource.GetBestMatch%2A> yöntemi. Bu örnekte, her biri iki parametreye sahip iki imzalar vardır. Bu nedenle, bu yöntem gerekli değil. İmza Yardımı birden fazla kaynak kullanılabilir bir bileşen uygulamasında, bu yöntem, imza Yardım en yüksek öncelikli kaynak eşleşen bir imza verebilirsiniz karar vermek için kullanılır. Erişilemiyorsa yöntemi null değerini döndürür ve next-en yüksek öncelikli kaynak bir eşleşme sağlamanız istenir.  
  
     [!code-csharp[VSSDKSignatureHelpTest#20](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#20)]
     [!code-vb[VSSDKSignatureHelpTest#20](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#20)]  
  
7.  Dispose() yöntemini uygulayın:  
  
     [!code-csharp[VSSDKSignatureHelpTest#21](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#21)]
     [!code-vb[VSSDKSignatureHelpTest#21](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#21)]  
  
## <a name="implementing-the-signature-help-source-provider"></a>İmza Yardımı kaynak sağlayıcısı uygulama  
 İmza Yardımı kaynak sağlayıcısı, Yönetilen Genişletilebilirlik Çerçevesi (MEF) bileşen parçası dışarı aktarma ve imza Yardımı kaynak oluşturmak için sorumludur.  
  
#### <a name="to-implement-the-signature-help-source-provider"></a>İmza Yardımı kaynak sağlayıcısını uygulamak için  
  
1.  Adlı bir sınıf ekleyin `TestSignatureHelpSourceProvider` uygulayan <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSourceProvider>ve ile dışarı aktarın bir <xref:Microsoft.VisualStudio.Utilities.NameAttribute>, <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> "metin" ve <xref:Microsoft.VisualStudio.Utilities.OrderAttribute> , önce = "varsayılan".  
  
     [!code-csharp[VSSDKSignatureHelpTest#22](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#22)]
     [!code-vb[VSSDKSignatureHelpTest#22](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#22)]  
  
2.  Uygulama <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSourceProvider.TryCreateSignatureHelpSource%2A> örnekleme tarafından `TestSignatureHelpSource`.  
  
     [!code-csharp[VSSDKSignatureHelpTest#23](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#23)]
     [!code-vb[VSSDKSignatureHelpTest#23](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#23)]  
  
## <a name="implementing-the-command-handler"></a>Komut işleyici uygulama  
 İmza Yardımı tarafından tetiklenen genellikle bir (karakter ve tarafından kapatıldı bir) karakter. Uygulayarak bu tuş vuruşları işleyebilir bir <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> böylece aldığında bir imza Yardım oturumu tetikleyen bir (karakter, bir bilinen bir yöntem adını izlediği ve aldığında oturum kapatılana bir) karakter.  
  
#### <a name="to-implement-the-command-handler"></a>Komut işleyici uygulamak için  
  
1.  Adlı bir sınıf ekleyin `TestSignatureHelpCommand` uygulayan <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>.  
  
     [!code-csharp[VSSDKSignatureHelpTest#24](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#24)]
     [!code-vb[VSSDKSignatureHelpTest#24](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#24)]  
  
2.  İçin özel alanlar ekleme <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> (Bu komuta zincirini işleyicilere komut işleyici eklemenize olanak sağlayan) bağdaştırıcısı, metin görünümünü, imza Yardım aracısı ve oturumu bir <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigator>ve sonraki <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>.  
  
     [!code-csharp[VSSDKSignatureHelpTest#25](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#25)]
     [!code-vb[VSSDKSignatureHelpTest#25](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#25)]  
  
3.  Bu alanlar ve komuta zincirini filtrelerde komut filtre eklemek için bir oluşturucu ekleyin.  
  
     [!code-csharp[VSSDKSignatureHelpTest#26](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#26)]
     [!code-vb[VSSDKSignatureHelpTest#26](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#26)]  
  
4.  Uygulama <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> komut filtre aldığında imza Yardım oturumu tetiklemek için yöntemi bir (bilinen bir yöntem adlarını ve aldığında oturumu kapatmak için sonra karakteri bir) oturumu hala etkin durumdayken karakter. Her durumda komutu iletilir.  
  
     [!code-csharp[VSSDKSignatureHelpTest#27](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#27)]
     [!code-vb[VSSDKSignatureHelpTest#27](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#27)]  
  
5.  Uygulama <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> BT'nin her zaman komut iletir için yöntemi.  
  
     [!code-csharp[VSSDKSignatureHelpTest#28](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#28)]
     [!code-vb[VSSDKSignatureHelpTest#28](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#28)]  
  
## <a name="implementing-the-signature-help-command-provider"></a>İmza Yardımı komutu sağlayıcısı uygulama  
 İmza Help komutunu uygulayarak sağlayabilir <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> metni görünümü oluşturulduğunda komut işleyicisi oluşturmak için.  
  
#### <a name="to-implement-the-signature-help-command-provider"></a>İmza Yardımı komutu sağlayıcısı uygulamak için  
  
1.  Adlı bir sınıf ekleyin `TestSignatureHelpController` uygulayan <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> ve ile dışarı aktarın <xref:Microsoft.VisualStudio.Utilities.NameAttribute>, <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>, ve <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute>.  
  
     [!code-csharp[VSSDKSignatureHelpTest#29](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#29)]
     [!code-vb[VSSDKSignatureHelpTest#29](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#29)]  
  
2.  İçeri aktarma <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService> (almak için kullanılan <xref:Microsoft.VisualStudio.Text.Editor.ITextView>, verilen <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> nesne), <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> (geçerli kelimenin bulmak için kullanılan) ve <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpBroker> (imza Yardım oturumu tetiklemek için).  
  
     [!code-csharp[VSSDKSignatureHelpTest#30](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#30)]
     [!code-vb[VSSDKSignatureHelpTest#30](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#30)]  
  
3.  Uygulama <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener.VsTextViewCreated%2A> örnekleme yöntemi `TestSignatureCommandHandler`.  
  
     [!code-csharp[VSSDKSignatureHelpTest#31](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#31)]
     [!code-vb[VSSDKSignatureHelpTest#31](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#31)]  
  
## <a name="building-and-testing-the-code"></a>Oluşturma ve kod test etme  
 Bu kodu test etmek için SignatureHelpTest Çözümü derleyin ve deneysel örneğinde çalıştırın.  
  
#### <a name="to-build-and-test-the-signaturehelptest-solution"></a>Derleme ve SignatureHelpTest çözümü test etmek için  
  
1.  Çözümü oluşturun.  
  
2.  Bu projede hata ayıklayıcıda çalıştırdığınızda, Visual Studio'nun ikinci bir örneğini başlatılır.  
  
3.  Bir metin dosyası türü "Ekle" sözcüğünü içeren metin ve yanı sıra bir açma ayracı oluşturun.  
  
4.  Açma parantezinden yazdıktan sonra iki imzaları listesini görüntüleyen bir araç ipucu görmelisiniz `add()` yöntemi.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [İzlenecek Yol: Bir İçerik Türünü Dosya Adı Uzantısına Bağlama](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)

