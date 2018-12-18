---
title: Bir düzenleyici öğesi şablonuyla uzantı oluşturma | Microsoft Docs
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
- editors [Visual Studio SDK], new - extensions
ms.assetid: fa3b993b-ab95-47fa-a38b-b788f3a5b2d8
caps.latest.revision: 17
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ab22549550c0564f7e27b88adae4627f24ab9acc
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51772748"
---
# <a name="creating-an-extension-with-an-editor-item-template"></a>Düzenleyici Öğesi Şablonuyla Uzantı Oluşturma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sınıflandırıcılar, kenarlıklar ve kenar boşlukları Düzenleyici ekleme temel Düzenleyici uzantıları oluşturmak için Visual Studio SDK'sı dahil edilen öğe şablonları kullanabilirsiniz. Düzenleyici öğesi şablonları, Visual C# veya Visual Basic VSIX projeleri için kullanılabilir.  
  
## <a name="prerequisites"></a>Önkoşullar  
 Visual Studio 2015'ten başlayarak, size Visual Studio SDK İndirme Merkezi'nden yüklemeyin. Visual Studio kurulumunda isteğe bağlı bir özellik olarak eklenmiştir. VS SDK'yi daha sonra yükleyebilirsiniz. Daha fazla bilgi için [Visual Studio SDK'sını yükleme](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-classifier-extension"></a>Bir sınıflandırıcı uzantısı oluşturma  
 Uygun metni renkler bir düzenleyici sınıflandırıcı Düzenleyicisi sınıflandırıcı öğe şablonu oluşturur (Bu durumda, her şeyi) herhangi bir metin dosyası olarak.  
  
1.  İçinde **yeni proje** iletişim kutusunda **Visual C#** veya **Visual Basic** ve ardından **genişletilebilirlik**. İçinde **şablonları** bölmesinde **VSIX projesi**. İçinde **adı** kutusuna `TestClassifier`. **Tamam**'ı tıklatın.  
  
2.  İçinde **Çözüm Gezgini**, proje düğümüne sağ tıklayıp **Ekle / yeni öğe**. Git için Visual C# **genişletilebilirlik** düğümünü seçip alt **Düzenleyicisi sınıflandırıcı**. Varsayılan dosya adı (EditorClassifier1.cs) bırakın.  
  
3.  Aşağıdaki gibi üç kod dosyası vardır:  
  
    -   EditorClassifier1.cs içeren `EditorClassifier1` sınıfı.  
  
    -   EditorClassifier1ClassificationDefinition.cs içeren `OEditorClassifier1ClassificationDefinition` sınıfı.  
  
    -   EditorClassifier1Format.cs içeren `EditorClassifier1Format` sınıfı.  
  
    -   EditorClassifier1Provider.cs içeren `EditorClassifier1Provider` sınıfı.  
  
4.  Projeyi oluşturmak ve hata ayıklamaya başlayın. Visual Studio'nun deneysel örneğinde görünür.  
  
     Bir metin dosyası açarsanız, tüm metin karşı Menekşe arka plan çizilir.  
  
## <a name="creating-a-text-relative-adornment-extension"></a>Bir metin göreli kenarlığı uzantısı oluşturma  
 Tüm metin karakteri örneklerini düzenler bir metin göreli kenarlığı düzenleyici metin kenarlığı şablon oluşturur kırmızı anahat ve mavi bir arka plana sahip bir kutusunu kullanarak ' bir'. Metin göreli olduğundan kutusunu her zaman katmanları bile bunlar yeniden biçimlendirildi veya taşınırsa 'bir' karakter.  
  
1.  İçinde **yeni proje** iletişim kutusunda **Visual C#** veya **Visual Basic** ve ardından **genişletilebilirlik**. İçinde **şablonları** bölmesinde **VSIX projesi**. İçinde **adı** kutusuna `TestAdornment`. **Tamam**'ı tıklatın.  
  
2.  İçinde **Çözüm Gezgini**, proje düğümüne sağ tıklayıp **Ekle / yeni öğe**. Git için Visual C# **genişletilebilirlik** düğümünü seçip alt **düzenleyici metin kenarlığı**. Varsayılan dosya adı (TextAdornment1.cs/vb) bırakın.  
  
3.  Şu şekilde iki kod dosyası vardır:  
  
    -   TextAdornment1.cs içeren `TextAdornment1` sınıfı.  
  
    -   extAdornment1TextViewCreationListener.cs içeren `TextAdornment1TextViewCreationListener` sınıfı.  
  
4.  Projeyi oluşturmak ve hata ayıklamaya başlayın. Deneysel örneği açılır. Bir metin dosyası açarsanız, metindeki 'bir' tüm karakterleri mavi arka plan kırmızı özetlenmiştir.  
  
## <a name="creating-a-viewport-relative-adornment-extension"></a>Bir Görünüm penceresi göreli kenarlığı uzantısı oluşturma  
 Görünüm penceresinin sağ üst köşesinde kırmızı bir anahattına içeren bir Menekşe kutusu ekleyen bir Görünüm penceresi göreli kenarlığı Düzenleyicisi Görünüm penceresi kenarlığı şablon oluşturur.  
  
> [!NOTE]
>  *Görünüm penceresi* şu anda görüntülenen metin görünümünü alanıdır.  
  
#### <a name="to-create-a-viewport-adornment-extension-by-using-the-editor-viewport-adornment-template"></a>Düzenleyici Görünüm penceresi kenarlığı şablonu kullanarak bir Görünüm penceresi kenarlığı uzantısı oluşturmak için  
  
1.  İçinde **yeni proje** iletişim kutusunda **Visual C#** veya **Visual Basic** ve ardından **genişletilebilirlik**. İçinde **şablonları** bölmesinde **VSIX projesi**. İçinde **adı** kutusuna `ViewportAdornment`. **Tamam**'ı tıklatın.  
  
2.  İçinde **Çözüm Gezgini**, proje düğümüne sağ tıklayıp **Ekle / yeni öğe**. Git için Visual C# **genişletilebilirlik** düğümünü seçip alt **Düzenleyicisi Görünüm penceresi kenarlığı**. Varsayılan dosya adı (ViewportAdornment1.cs/vb) bırakın.  
  
3.  Şu şekilde iki kod dosyası vardır:  
  
    -   ViewportAdornment1.cs içeren `ViewportAdornment1` sınıfı.  
  
    -   ViewportAdornment1TextViewCreationListener.cs içeren `ViewportAdornment1TextViewCreationListener` sınıfı  
  
4.  Projeyi oluşturmak ve hata ayıklamaya başlayın. Deneysel örneği açılır. Yeni bir metin dosyası oluşturursanız, görünüm penceresinin sağ üst köşesinde kırmızı anahat içeren bir Menekşe kutusu görüntülenir.  
  
## <a name="creating-a-margin-extension"></a>Bir kenar boşluğu uzantısı oluşturma  
 Düzenleyici kenar şablon, "Hello world!" sözcüklerini birlikte görünen yeşil bir kenar boşluğu oluşturur. Yatay kaydırma çubuğunun altında.  
  
#### <a name="to-create-a-margin-extension-by-using-the-editor-margin-template"></a>Düzenleyici kenar şablonu kullanarak bir kenar boşluğu uzantısı oluşturma  
  
1.  İçinde **yeni proje** iletişim kutusunda **Visual C#** veya **Visual Basic** ve ardından **genişletilebilirlik**. İçinde **şablonları** bölmesinde **VSIX projesi**. İçinde **adı** kutusuna `MarginExtension`. **Tamam**'ı tıklatın.  
  
2.  İçinde **Çözüm Gezgini**, proje düğümüne sağ tıklayıp **Ekle / yeni öğe**. Git için Visual C# **genişletilebilirlik** düğümünü seçip alt **Düzenleyicisi Görünüm penceresi kenarlığı**. Varsayılan dosya adı (EditorMargin1.cs/vb) bırakın.  
  
3.  Şu şekilde iki kod dosyası vardır:  
  
    -   EditorMargin1.cs içeren `EditorMargin1` sınıfı.  
  
    -   EditorMargin1Factory.cs içeren `EditorMargin1Factory` sınıfı.  
  
4.  Bu projeyi oluşturun ve hata ayıklamayı başlatın. Deneysel örneği açılır. Bir metin dosyası açarsanız, "Hello EditorMargin1" sözcüklerini içeren bir yeşil bir kenar boşluğu yatay kaydırma çubuğunun altında görüntülenir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Dil Hizmeti ve Düzenleyici Uzantı Noktaları](../extensibility/language-service-and-editor-extension-points.md)

