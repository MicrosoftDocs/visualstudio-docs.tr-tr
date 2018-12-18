---
title: 'İzlenecek yol: Hızlıbilgi araç ipuçlarını görüntüleme | Microsoft Docs'
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
- editors [Visual Studio SDK], new - QuickInfo
ms.assetid: 23fb8384-4f12-446f-977f-ce7910347947
caps.latest.revision: 28
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 9cd0e331536c194acdde95bdd74e5f41668a23e1
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51806288"
---
# <a name="walkthrough-displaying-quickinfo-tooltips"></a>İzlenecek Yol: HızlıBilgi Araç İpuçlarını Görüntüleme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Hızlıbilgi yöntem imzaları görüntüleyen bir IntelliSense özelliğidir ve açıklamaları bir kullanıcı işaretçiyi bir yöntem adı üzerinde taşır. Quickınfo'da açıklamaları sağlamak istediğiniz tanımlayıcıları tanımlayıp ardından, içeriği görüntülemek bir araç ipucu oluşturma dil tabanlı özellikleri gibi Hızlıbilgi uygulayabilirsiniz. Bir dil hizmeti bağlamında Hızlıbilgi tanımlayabilirsiniz kendi dosya adı uzantısı ve içerik türünü tanımlayın ve bu tür için Hızlıbilgi görüntülemek veya mevcut bir içerik türü (örneğin, "metin") için Hızlıbilgi görüntüleyebilirsiniz. Bu izlenecek yol, Hızlıbilgi görüntülemek için "metin" içerik türü gösterilmektedir.  
  
 Bu kılavuzda Hızlıbilgi örnek, bir kullanıcı, bir yöntem adı işaretçiyi hareket ettirdiğinde araç ipuçları görüntüler. Bu tasarım, dört bu arabirimlerin uygulanma gerektirir:  
  
- Kaynak arabirimi  
  
- Kaynak sağlayıcı arabirimi  
  
- denetleyici arabirimi  
  
- Denetleyici sağlayıcı arabirimi  
  
  Kaynak ve denetleyici sağlayıcıları, Yönetilen Genişletilebilirlik Çerçevesi (MEF) bileşeni bölümleri ve kaynak ve denetleyici sınıflarını dışarı aktarmak için sorumludur ve içeri aktarma ve Hizmetleri gibi aracıları <xref:Microsoft.VisualStudio.Text.ITextBufferFactoryService>, araç ipucu metni oluşturur Arabellek ve <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoBroker>, Hızlıbilgi oturumu tetikler.  
  
  Bu örnekte, yöntem adları ve açıklamaları, sabit kodlanmış listesini Hızlıbilgi kaynak kullanır, ancak dil hizmeti ve dil belgeleri tam uygulamalarında, bu içeriği sağlamaktan sorumlu.  
  
## <a name="prerequisites"></a>Önkoşullar  
 Visual Studio 2015'ten başlayarak, size Visual Studio SDK İndirme Merkezi'nden yüklemeyin. Visual Studio kurulumunda isteğe bağlı bir özellik olarak eklenmiştir. VS SDK'yi daha sonra yükleyebilirsiniz. Daha fazla bilgi için [Visual Studio SDK'sını yükleme](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-mef-project"></a>MEF proje oluşturma  
  
#### <a name="to-create-a-mef-project"></a>MEF projesi oluşturmak için  
  
1.  Bir C# VSIX projesi oluşturun. (İçinde **yeni proje** iletişim kutusunda **Visual C# / genişletilebilirlik**, ardından **VSIX projesi**.) Çözüm adı `QuickInfoTest`.  
  
2.  Bir düzenleyici sınıflandırıcı öğe şablonu, projeye ekleyin. Daha fazla bilgi için [bir düzenleyici öğesi şablonuyla uzantı oluşturma](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
3.  Varolan sınıf dosyaları silin.  
  
## <a name="implementing-the-quickinfo-source"></a>Quickınfo'da kaynağı uygulama  
 Quickınfo'da Kaynak Tanımlayıcıları ve açıklamalarının kümesini toplamak ve tanımlayıcılarından birini karşılaşıldığında, araç ipucu metin arabelleği için içerik ekleme sorumludur. Bu örnekte, tanımlayıcıların ve açıklamalarının yalnızca kaynak oluşturucuda eklenir.  
  
#### <a name="to-implement-the-quickinfo-source"></a>Quickınfo'da kaynak uygulamak için  
  
1.  Bir sınıf dosyası ekleyin ve adlandırın `TestQuickInfoSource`.  
  
2.  Microsoft.VisualStudio.Language.IntelliSense bir başvuru ekleyin.  
  
3.  Aşağıdaki içeri aktarmaları ekleyin.  
  
     [!code-csharp[VSSDKQuickInfoTest#1](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#1)]
     [!code-vb[VSSDKQuickInfoTest#1](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#1)]  
  
4.  Uygulayan bir sınıf bildirme <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSource>ve adlandırın `TestQuickInfoSource`.  
  
     [!code-csharp[VSSDKQuickInfoTest#2](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#2)]
     [!code-vb[VSSDKQuickInfoTest#2](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#2)]  
  
5.  Quickınfo'da kaynak sağlayıcısı, metin arabelleği ve bir dizi yöntem adlarını ve yöntem imzaları için alanlar ekleyin. Bu örnekte, yöntem adlarını ve imzalar, başlatılır `TestQuickInfoSource` Oluşturucusu.  
  
     [!code-csharp[VSSDKQuickInfoTest#3](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#3)]
     [!code-vb[VSSDKQuickInfoTest#3](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#3)]  
  
6.  Quickınfo'da kaynak sağlayıcısı ve metin arabelleğini ayarlar ve yöntem adlarını ve yöntem imzaları ve açıklamaları kümesini dolduran bir oluşturucu ekleyin.  
  
     [!code-csharp[VSSDKQuickInfoTest#4](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#4)]
     [!code-vb[VSSDKQuickInfoTest#4](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#4)]  
  
7.  Uygulama <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSource.AugmentQuickInfoSession%2A> yöntemi. İmleç çizgi veya bir metin arabelleği sonunda ise bu örnekte, yöntem geçerli sözcüğü ya da önceki sözcüğe bulur. Word yöntemi adlarından birini kullanıyorsanız, bu yöntem adı için açıklama Hızlıbilgi içeriği eklenir.  
  
     [!code-csharp[VSSDKQuickInfoTest#5](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#5)]
     [!code-vb[VSSDKQuickInfoTest#5](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#5)]  
  
8.  Dispose() yöntemini beri uygulamalıdır <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSource> uygulayan <xref:System.IDisposable>:  
  
     [!code-csharp[VSSDKQuickInfoTest#6](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#6)]
     [!code-vb[VSSDKQuickInfoTest#6](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#6)]  
  
## <a name="implementing-a-quickinfo-source-provider"></a>Quickınfo'da kaynak sağlayıcısı uygulama  
 Hızlıbilgi kaynak sağlayıcısı, öncelikle kendisi bir MEF Bileşeni parçası dışarı aktarma ve Hızlıbilgi kaynak örneği için kullanılır. Bir MEF Bileşeni parçası olduğundan, diğer MEF Bileşeni parçaları içeri aktarabilirsiniz.  
  
#### <a name="to-implement-a-quickinfo-source-provider"></a>Quickınfo'da kaynak sağlayıcısını uygulamak için  
  
1.  Adlı bir Hızlıbilgi kaynak sağlayıcısı bildirimini `TestQuickInfoSourceProvider` uygulayan <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSourceProvider>ve ile dışarı aktarın bir <xref:Microsoft.VisualStudio.Utilities.NameAttribute> "Araç ipucu Hızlıbilgi kaynak" bir <xref:Microsoft.VisualStudio.Utilities.OrderAttribute> , önce "varsayılan" = ve <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> "metin".  
  
     [!code-csharp[VSSDKQuickInfoTest#7](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#7)]
     [!code-vb[VSSDKQuickInfoTest#7](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#7)]  
  
2.  İki Düzenleyici hizmet alma <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> ve <xref:Microsoft.VisualStudio.Text.ITextBufferFactoryService>, özellikleri olarak `TestQuickInfoSourceProvider`.  
  
     [!code-csharp[VSSDKQuickInfoTest#8](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#8)]
     [!code-vb[VSSDKQuickInfoTest#8](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#8)]  
  
3.  Uygulama <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSourceProvider.TryCreateQuickInfoSource%2A> yeni döndürülecek `TestQuickInfoSource`.  
  
     [!code-csharp[VSSDKQuickInfoTest#9](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#9)]
     [!code-vb[VSSDKQuickInfoTest#9](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#9)]  
  
## <a name="implementing-a-quickinfo-controller"></a>Quickınfo'da denetleyicisi uygulama  
 Quickınfo'da denetleyicileri Hızlıbilgi ne zaman görüntüleneceğini belirler. Bu örnekte, yöntem adları birine karşılık gelen bir sözcük üzerinden işaretçisidir Hızlıbilgi görüntülenir. Quickınfo'da denetleyicisi Hızlıbilgi oturumu tetikleyen bir fare üzerine gelindiğinde kullanılacak olay işleyicisi uygular.  
  
#### <a name="to-implement-a-quickinfo-controller"></a>Quickınfo'da denetleyicisi uygulamak için  
  
1.  Uygulayan bir sınıf bildirme <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController>ve adlandırın `TestQuickInfoController`.  
  
     [!code-csharp[VSSDKQuickInfoTest#10](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#10)]
     [!code-vb[VSSDKQuickInfoTest#10](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#10)]  
  
2.  Özel alanlar metin görünümü için metin görünümü, Hızlıbilgi oturumu ve Hızlıbilgi controller sağlayıcısı temsil metin arabelleği ekleyin.  
  
     [!code-csharp[VSSDKQuickInfoTest#11](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#11)]
     [!code-vb[VSSDKQuickInfoTest#11](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#11)]  
  
3.  Alanları ayarlayan ve fareyi üzerine gelindiğinde kullanılacak olay işleyicisi ekler bir oluşturucu ekleyin.  
  
     [!code-csharp[VSSDKQuickInfoTest#12](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#12)]
     [!code-vb[VSSDKQuickInfoTest#12](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#12)]  
  
4.  Quickınfo'da oturumu tetikler fare vurgulu olayı işleyicisi ekleyin.  
  
     [!code-csharp[VSSDKQuickInfoTest#13](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#13)]
     [!code-vb[VSSDKQuickInfoTest#13](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#13)]  
  
5.  Uygulama <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController.Detach%2A> denetleyicisi metin görünümden ayrıldığında BT'nin fareyi üzerine gelindiğinde kullanılacak olay işleyicisi kaldırır. Bu nedenle yöntemi.  
  
     [!code-csharp[VSSDKQuickInfoTest#14](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#14)]
     [!code-vb[VSSDKQuickInfoTest#14](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#14)]  
  
6.  Uygulama <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController.ConnectSubjectBuffer%2A> yöntemi ve <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController.DisconnectSubjectBuffer%2A> boş Bu örnek yöntemler olarak yöntemi.  
  
     [!code-csharp[VSSDKQuickInfoTest#15](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#15)]
     [!code-vb[VSSDKQuickInfoTest#15](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#15)]  
  
## <a name="implementing-the-quickinfo-controller-provider"></a>Quickınfo'da denetleyicisi sağlayıcıyı uygulama  
 Sağlayıcı Hızlıbilgi denetleyicisinin, öncelikle kendisi bir MEF Bileşeni parçası dışarı aktarma ve Hızlıbilgi denetleyici örneği için kullanılır. Bir MEF Bileşeni parçası olduğundan, diğer MEF Bileşeni parçaları içeri aktarabilirsiniz.  
  
#### <a name="to-implement-the-quickinfo-controller-provider"></a>Quickınfo'da denetleyicisi sağlayıcısını uygulamak için  
  
1.  Adlı bir sınıf bildirme `TestQuickInfoControllerProvider` uygulayan <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseControllerProvider>ve ile dışarı aktarın bir <xref:Microsoft.VisualStudio.Utilities.NameAttribute> "Araç ipucu Hızlıbilgi denetleyicisinin" ve <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> "metin":  
  
     [!code-csharp[VSSDKQuickInfoTest#16](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#16)]
     [!code-vb[VSSDKQuickInfoTest#16](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#16)]  
  
2.  İçeri aktarma <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoBroker> özelliği olarak.  
  
     [!code-csharp[VSSDKQuickInfoTest#17](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#17)]
     [!code-vb[VSSDKQuickInfoTest#17](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#17)]  
  
3.  Uygulama <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseControllerProvider.TryCreateIntellisenseController%2A> Hızlıbilgi denetleyicisi örnekleme yöntemi.  
  
     [!code-csharp[VSSDKQuickInfoTest#18](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#18)]
     [!code-vb[VSSDKQuickInfoTest#18](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#18)]  
  
## <a name="building-and-testing-the-code"></a>Oluşturma ve kod test etme  
 Bu kodu test etmek için QuickInfoTest Çözümü derleyin ve deneysel örneğinde çalıştırın.  
  
#### <a name="to-build-and-test-the-quickinfotest-solution"></a>Derleme ve QuickInfoTest çözümü test etmek için  
  
1.  Çözümü oluşturun.  
  
2.  Bu projede hata ayıklayıcıda çalıştırdığınızda, Visual Studio'nun ikinci bir örneğini başlatılır.  
  
3.  Bir metin dosyası ve türü "sözcüklerini içeren metin Ekle" ve "çıkarmayı" oluşturun.  
  
4.  İşaretçiyi "Ekle" oluşumları birinin üzerine getirin. İmza ve açıklamasını `add` yöntemi görüntülenmesi gerekir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [İzlenecek Yol: Bir İçerik Türünü Dosya Adı Uzantısına Bağlama](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)

