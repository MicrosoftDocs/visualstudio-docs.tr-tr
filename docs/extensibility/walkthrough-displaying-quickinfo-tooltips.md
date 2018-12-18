---
title: 'İzlenecek yol: Hızlıbilgi araç ipuçlarını görüntüleme | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - QuickInfo
ms.assetid: 23fb8384-4f12-446f-977f-ce7910347947
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: e5ff8b850287e91cf2a1e5e6a546980c9087541d
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49824197"
---
# <a name="walkthrough-display-quickinfo-tooltips"></a>İzlenecek yol: Görüntü Hızlıbilgi araç ipuçları
Hızlıbilgi yöntem imzaları görüntüleyen bir IntelliSense özelliğidir ve açıklamaları bir kullanıcı işaretçiyi bir yöntem adı üzerinde taşır. Quickınfo'da açıklamaları sağlamak istediğiniz tanımlayıcıları tanımlayıp ardından, içeriği görüntülemek bir araç ipucu oluşturma dil tabanlı özellikleri gibi Hızlıbilgi uygulayabilirsiniz. Bir dil hizmeti bağlamında Hızlıbilgi tanımlayabilirsiniz kendi dosya adı uzantısı ve içerik türünü tanımlayın ve bu tür için Hızlıbilgi görüntülemek veya mevcut bir içerik türü (örneğin, "metin") için Hızlıbilgi görüntüleyebilirsiniz. Bu izlenecek yol, Hızlıbilgi görüntülemek için "metin" içerik türü gösterilmektedir.  
  
 Bu kılavuzda Hızlıbilgi örnek, bir kullanıcı, bir yöntem adı işaretçiyi hareket ettirdiğinde araç ipuçları görüntüler. Bu tasarım, dört bu arabirimlerin uygulanma gerektirir:  
  
- Kaynak arabirimi  
  
- Kaynak sağlayıcı arabirimi  
  
- denetleyici arabirimi  
  
- Denetleyici sağlayıcı arabirimi  
  
  Kaynak ve denetleyici sağlayıcıları, Yönetilen Genişletilebilirlik Çerçevesi (MEF) bileşeni bölümleri ve kaynak ve denetleyici sınıflarını dışarı aktarmak için sorumludur ve içeri aktarma ve Hizmetleri gibi aracıları <xref:Microsoft.VisualStudio.Text.ITextBufferFactoryService>, araç ipucu metni oluşturur Arabellek ve <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoBroker>, Hızlıbilgi oturumu tetikler.  
  
  Bu örnekte, yöntem adları ve açıklamaları, sabit kodlanmış listesini Hızlıbilgi kaynak kullanır, ancak dil hizmeti ve dil belgeleri tam uygulamalarında, bu içeriği sağlamaktan sorumlu.  
  
## <a name="prerequisites"></a>Önkoşullar  
 Visual Studio 2015'ten başlayarak, Visual Studio SDK İndirme Merkezi'nden yüklemeniz gerekmez. Visual Studio kurulumunda isteğe bağlı bir özellik eklemiştir. VS SDK'yi daha sonra yükleyebilirsiniz. Daha fazla bilgi için [Visual Studio SDK'yı yükleme](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="create-a-mef-project"></a>MEF proje oluşturma  
  
### <a name="to-create-a-mef-project"></a>MEF projesi oluşturmak için  
  
1.  Bir C# VSIX projesi oluşturun. (İçinde **yeni proje** iletişim kutusunda **Visual C# / genişletilebilirlik**, ardından **VSIX projesi**.) Çözüm adı `QuickInfoTest`.  
  
2.  Bir düzenleyici sınıflandırıcı öğe şablonu, projeye ekleyin. Daha fazla bilgi için [bir düzenleyici öğesi şablonuyla uzantı oluşturma](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
3.  Varolan sınıf dosyaları silin.  
  
## <a name="implement-the-quickinfo-source"></a>Quickınfo'da kaynak uygulama  
 Quickınfo'da Kaynak Tanımlayıcıları ve açıklamalarının kümesini toplamak ve tanımlayıcılarından birini karşılaşıldığında, araç ipucu metin arabelleği için içerik ekleme sorumludur. Bu örnekte, tanımlayıcıların ve açıklamalarının yalnızca kaynak oluşturucuda eklenir.  
  
#### <a name="to-implement-the-quickinfo-source"></a>Quickınfo'da kaynak uygulamak için  
  
1.  Bir sınıf dosyası ekleyin ve adlandırın `TestQuickInfoSource`.  
  
2.  Bir başvuru ekleyin *Microsoft.VisualStudio.Language.IntelliSense*.  
  
3.  Aşağıdaki içeri aktarmaları ekleyin.  
  
     [!code-vb[VSSDKQuickInfoTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_1.vb)]
     [!code-csharp[VSSDKQuickInfoTest#1](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_1.cs)]  
  
4.  Uygulayan bir sınıf bildirme <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSource>ve adlandırın `TestQuickInfoSource`.  
  
     [!code-vb[VSSDKQuickInfoTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_2.vb)]
     [!code-csharp[VSSDKQuickInfoTest#2](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_2.cs)]  
  
5.  Quickınfo'da kaynak sağlayıcısı, metin arabelleği ve bir dizi yöntem adlarını ve yöntem imzaları için alanlar ekleyin. Bu örnekte, yöntem adlarını ve imzalar, başlatılır `TestQuickInfoSource` Oluşturucusu.  
  
     [!code-vb[VSSDKQuickInfoTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_3.vb)]
     [!code-csharp[VSSDKQuickInfoTest#3](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_3.cs)]  
  
6.  Quickınfo'da kaynak sağlayıcısı ve metin arabelleğini ayarlar ve yöntem adlarını ve yöntem imzaları ve açıklamaları kümesini dolduran bir oluşturucu ekleyin.  
  
     [!code-vb[VSSDKQuickInfoTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_4.vb)]
     [!code-csharp[VSSDKQuickInfoTest#4](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_4.cs)]  
  
7.  Uygulama <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSource.AugmentQuickInfoSession%2A> yöntemi. İmleç çizgi veya bir metin arabelleği sonunda ise bu örnekte, yöntem geçerli sözcüğü ya da önceki sözcüğe bulur. Word yöntemi adlarından birini kullanıyorsanız, bu yöntem adı için açıklama Hızlıbilgi içeriği eklenir.  
  
     [!code-vb[VSSDKQuickInfoTest#5](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_5.vb)]
     [!code-csharp[VSSDKQuickInfoTest#5](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_5.cs)]  
  
8.  Dispose() yöntemini beri uygulamalıdır <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSource> uygulayan <xref:System.IDisposable>:  
  
     [!code-vb[VSSDKQuickInfoTest#6](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_6.vb)]
     [!code-csharp[VSSDKQuickInfoTest#6](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_6.cs)]  
  
## <a name="implement-a-quickinfo-source-provider"></a>Quickınfo'da kaynak sağlayıcıyı uygulama  
 Hızlıbilgi kaynak sağlayıcısı, öncelikle kendisi bir MEF Bileşeni parçası dışarı aktarma ve Hızlıbilgi kaynak örneği için kullanılır. Bir MEF Bileşeni parçası olduğundan, diğer MEF Bileşeni parçaları içeri aktarabilirsiniz.  
  
#### <a name="to-implement-a-quickinfo-source-provider"></a>Quickınfo'da kaynak sağlayıcısını uygulamak için  
  
1.  Adlı bir Hızlıbilgi kaynak sağlayıcısı bildirimini `TestQuickInfoSourceProvider` uygulayan <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSourceProvider>ve ile dışarı aktarın bir <xref:Microsoft.VisualStudio.Utilities.NameAttribute> "Araç ipucu Hızlıbilgi kaynak" bir <xref:Microsoft.VisualStudio.Utilities.OrderAttribute> , önce "varsayılan" = ve <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> "metin".  
  
     [!code-vb[VSSDKQuickInfoTest#7](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_7.vb)]
     [!code-csharp[VSSDKQuickInfoTest#7](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_7.cs)]  
  
2.  İki Düzenleyici hizmet alma <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> ve <xref:Microsoft.VisualStudio.Text.ITextBufferFactoryService>, özellikleri olarak `TestQuickInfoSourceProvider`.  
  
     [!code-vb[VSSDKQuickInfoTest#8](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_8.vb)]
     [!code-csharp[VSSDKQuickInfoTest#8](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_8.cs)]  
  
3.  Uygulama <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSourceProvider.TryCreateQuickInfoSource%2A> yeni döndürülecek `TestQuickInfoSource`.  
  
     [!code-vb[VSSDKQuickInfoTest#9](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_9.vb)]
     [!code-csharp[VSSDKQuickInfoTest#9](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_9.cs)]  
  
## <a name="implement-a-quickinfo-controller"></a>Uygulama Hızlıbilgi denetleyicisi  
 Quickınfo'da denetleyicileri Hızlıbilgi ne zaman gösterileceğini belirler. Yöntem adları birine karşılık gelen bir sözcük üzerinden işaretçisi olduğunda bu örnekte, Hızlıbilgi görünür. Quickınfo'da denetleyicisi Hızlıbilgi oturumu tetikleyen bir fare üzerine gelindiğinde kullanılacak olay işleyicisi uygular.  
  
### <a name="to-implement-a-quickinfo-controller"></a>Quickınfo'da denetleyicisi uygulamak için  
  
1.  Uygulayan bir sınıf bildirme <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController>ve adlandırın `TestQuickInfoController`.  
  
     [!code-vb[VSSDKQuickInfoTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_10.vb)]
     [!code-csharp[VSSDKQuickInfoTest#10](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_10.cs)]  
  
2.  Özel alanlar metin görünümü için metin görünümü, Hızlıbilgi oturumu ve Hızlıbilgi controller sağlayıcısı temsil metin arabelleği ekleyin.  
  
     [!code-vb[VSSDKQuickInfoTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_11.vb)]
     [!code-csharp[VSSDKQuickInfoTest#11](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_11.cs)]  
  
3.  Alanları ayarlayan ve fareyi üzerine gelindiğinde kullanılacak olay işleyicisi ekler bir oluşturucu ekleyin.  
  
     [!code-vb[VSSDKQuickInfoTest#12](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_12.vb)]
     [!code-csharp[VSSDKQuickInfoTest#12](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_12.cs)]  
  
4.  Quickınfo'da oturumu tetikler fare vurgulu olayı işleyicisi ekleyin.  
  
     [!code-vb[VSSDKQuickInfoTest#13](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_13.vb)]
     [!code-csharp[VSSDKQuickInfoTest#13](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_13.cs)]  
  
5.  Uygulama <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController.Detach%2A> denetleyicisi metin görünümden ayrıldığında BT'nin fareyi üzerine gelindiğinde kullanılacak olay işleyicisi kaldırır. Bu nedenle yöntemi.  
  
     [!code-vb[VSSDKQuickInfoTest#14](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_14.vb)]
     [!code-csharp[VSSDKQuickInfoTest#14](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_14.cs)]  
  
6.  Uygulama <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController.ConnectSubjectBuffer%2A> yöntemi ve <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController.DisconnectSubjectBuffer%2A> boş Bu örnek yöntemler olarak yöntemi.  
  
     [!code-vb[VSSDKQuickInfoTest#15](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_15.vb)]
     [!code-csharp[VSSDKQuickInfoTest#15](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_15.cs)]  
  
## <a name="implementing-the-quickinfo-controller-provider"></a>Quickınfo'da denetleyicisi sağlayıcıyı uygulama  
 Sağlayıcı Hızlıbilgi denetleyicisinin, öncelikle kendisi bir MEF Bileşeni parçası dışarı aktarma ve Hızlıbilgi denetleyici örneği için kullanılır. Bir MEF Bileşeni parçası olduğundan, diğer MEF Bileşeni parçaları içeri aktarabilirsiniz.  
  
### <a name="to-implement-the-quickinfo-controller-provider"></a>Quickınfo'da denetleyicisi sağlayıcısını uygulamak için  
  
1.  Adlı bir sınıf bildirme `TestQuickInfoControllerProvider` uygulayan <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseControllerProvider>ve ile dışarı aktarın bir <xref:Microsoft.VisualStudio.Utilities.NameAttribute> "Araç ipucu Hızlıbilgi denetleyicisinin" ve <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> "metin":  
  
     [!code-vb[VSSDKQuickInfoTest#16](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_16.vb)]
     [!code-csharp[VSSDKQuickInfoTest#16](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_16.cs)]  
  
2.  İçeri aktarma <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoBroker> özelliği olarak.  
  
     [!code-vb[VSSDKQuickInfoTest#17](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_17.vb)]
     [!code-csharp[VSSDKQuickInfoTest#17](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_17.cs)]  
  
3.  Uygulama <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseControllerProvider.TryCreateIntellisenseController%2A> Hızlıbilgi denetleyicisi örnekleme yöntemi.  
  
     [!code-vb[VSSDKQuickInfoTest#18](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_18.vb)]
     [!code-csharp[VSSDKQuickInfoTest#18](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_18.cs)]  
  
## <a name="build-and-test-the-code"></a>Kod oluşturup test  
 Bu kodu test etmek için QuickInfoTest Çözümü derleyin ve deneysel örneğinde çalıştırın.  
  
### <a name="to-build-and-test-the-quickinfotest-solution"></a>Derleme ve QuickInfoTest çözümü test etmek için  
  
1.  Çözümü oluşturun.  
  
2.  Bu projede hata ayıklayıcıda çalıştırdığınızda, Visual Studio'nun ikinci bir örneğini başlatılır.  
  
3.  Bir metin dosyası ve türü "sözcüklerini içeren metin Ekle" ve "çıkarmayı" oluşturun.  
  
4.  İşaretçiyi "Ekle" oluşumları birinin üzerine getirin. İmza ve açıklamasını `add` yöntemi görüntülenmesi gerekir.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [İzlenecek yol: bir içerik türü için bir dosya adı uzantısına bağlama](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)