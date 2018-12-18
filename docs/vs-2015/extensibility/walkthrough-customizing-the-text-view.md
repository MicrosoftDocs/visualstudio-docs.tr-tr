---
title: 'İzlenecek yol: metin görünümünü özelleştirme | Microsoft Docs'
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
- editors [Visual Studio SDK], new - customizing the view
ms.assetid: 32d32ac8-22ff-4de7-af69-bd46ec4ad9bf
caps.latest.revision: 23
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 38cbd0117f5f49666ee5da42d0f60dadf451ffda
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51781822"
---
# <a name="walkthrough-customizing-the-text-view"></a>İzlenecek Yol: Metin Görünümünü Özelleştirme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bir metin görünümünü kendi Düzenleyicisi biçim eşlemesi şu özelliklerde değiştirerek özelleştirebilirsiniz:  
  
-   Belirteç kenar boşluğu  
  
-   Ekleme düzeltme işareti  
  
-   Giriş işaretini üzerine yaz  
  
-   Seçili metni  
  
-   Etkin olmayan seçili metin (odağını kaybetmiş diğer bir deyişle, seçilen metin)  
  
-   Görünür boşluk  
  
## <a name="prerequisites"></a>Önkoşullar  
 Visual Studio 2015'ten başlayarak, size Visual Studio SDK İndirme Merkezi'nden yüklemeyin. Visual Studio kurulumunda isteğe bağlı bir özellik olarak eklenmiştir. VS SDK'yi daha sonra yükleyebilirsiniz. Daha fazla bilgi için [Visual Studio SDK'sını yükleme](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-mef-project"></a>MEF proje oluşturma  
  
1.  Bir C# VSIX projesi oluşturun. (İçinde **yeni proje** iletişim kutusunda **Visual C# / genişletilebilirlik**, ardından **VSIX projesi**.) Çözüm adı `ViewPropertyTest`.  
  
2.  Bir düzenleyici sınıflandırıcı öğe şablonu, projeye ekleyin. Daha fazla bilgi için [bir düzenleyici öğesi şablonuyla uzantı oluşturma](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
3.  Varolan sınıf dosyaları silin.  
  
## <a name="defining-the-content-type"></a>İçerik türü tanımlama  
  
1. Bir sınıf dosyası ekleyin ve adlandırın `ViewPropertyModifier`.  
  
2. Aşağıdaki `using` yönergeleri:  
  
    [!code-csharp[VSSDKViewPropertyTest#1](../snippets/csharp/VS_Snippets_VSSDK/vssdkviewpropertytest/cs/viewpropertymodifier.cs#1)]
    [!code-vb[VSSDKViewPropertyTest#1](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkviewpropertytest/vb/viewpropertymodifier.vb#1)]  
  
3. Adlı bir sınıf bildirme `TestViewCreationListener` öğesinden devralan <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener>. Bu sınıf aşağıdaki özniteliklerle dışarı aktarın:  
  
   - <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> Bu dinleyici uygulandığı içerik türünü belirtmek için.  
  
   - <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute> Bu dinleyici rolünü belirtmek için.  
  
     [!code-csharp[VSSDKViewPropertyTest#2](../snippets/csharp/VS_Snippets_VSSDK/vssdkviewpropertytest/cs/viewpropertymodifier.cs#2)]
     [!code-vb[VSSDKViewPropertyTest#2](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkviewpropertytest/vb/viewpropertymodifier.vb#2)]  
  
4. Bu sınıf, içeri aktarma <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMapService>.  
  
    [!code-csharp[VSSDKViewPropertyTest#3](../snippets/csharp/VS_Snippets_VSSDK/vssdkviewpropertytest/cs/viewpropertymodifier.cs#3)]
    [!code-vb[VSSDKViewPropertyTest#3](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkviewpropertytest/vb/viewpropertymodifier.vb#3)]  
  
## <a name="changing-the-view-properties"></a>Görünüm özelliklerini değiştirme  
  
1.  Uygulama <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener.TextViewCreated%2A> yöntemi böylece görünüm açıldığında Görünüm Özellikleri değiştirilir. Değişiklik yapmak için öncelikle bulma <xref:System.Windows.ResourceDictionary> bulmak istediğiniz görünümü en/boy karşılık gelir. Ardından uygun kaynak sözlüğü özelliğini değiştirin ve özelliklerini ayarlayın. Toplu işlem çağrıları <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap.SetProperties%2A> yöntemi çağırarak <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap.BeginBatchUpdate%2A> özellikleri ayarlanmadan önce yöntemi ve ardından <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap.EndBatchUpdate%2A> özellikleri ayarladıktan sonra.  
  
     [!code-csharp[VSSDKViewPropertyTest#4](../snippets/csharp/VS_Snippets_VSSDK/vssdkviewpropertytest/cs/viewpropertymodifier.cs#4)]
     [!code-vb[VSSDKViewPropertyTest#4](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkviewpropertytest/vb/viewpropertymodifier.vb#4)]  
  
## <a name="building-and-testing-the-code"></a>Oluşturma ve kod test etme  
  
1.  Çözümü oluşturun.  
  
     Bu projede hata ayıklayıcıda çalıştırdığınızda, Visual Studio'nun ikinci bir örneğini başlatılır.  
  
2.  Bir metin dosyası oluşturun ve bir metin yazın.  
  
    -   Ekleme giriş işaretini Eflatun olmalıdır ve üzerine yazma giriş işaretini Turkuaz olmalıdır.  
  
    -   Belirteç kenar boşluğu ('metin görünümünü sol) açık olması gereken yeşil.  
  
3.  Yazdığınız metni seçin. Seçili metnin rengini açık olmalıdır pembe.  
  
4.  Metin seçili durumdayken metni penceresi dışında herhangi bir yere tıklayın. Seçili metnin rengini koyu pembe olmalıdır.  
  
5.  Üzerinde görünür boşluk bırakın. (Üzerinde **Düzenle** menüsünde **Gelişmiş** ve ardından **beyaz boşluğu görüntüle**). Bazı sekmeler metin girin. Sekmeleri temsil eden kırmızı ok görüntülenmesi gerekir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Dil Hizmeti ve Düzenleyici Uzantı Noktaları](../extensibility/language-service-and-editor-extension-points.md)

