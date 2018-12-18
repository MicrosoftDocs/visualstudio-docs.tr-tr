---
title: Bir düzenleyici öğesi şablonuyla uzantı oluşturma | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - extensions
ms.assetid: fa3b993b-ab95-47fa-a38b-b788f3a5b2d8
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: a13c62d9fadfe105bd8e645ba6e7758c2b3195a3
ms.sourcegitcommit: 1c2ed640512ba613b3bbbc9ce348e28be6ca3e45
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/03/2018
ms.locfileid: "39500901"
---
# <a name="create-an-extension-with-an-editor-item-template"></a>Bir düzenleyici öğesi şablonuyla uzantı oluşturma
Sınıflandırıcılar, kenarlıklar ve kenar boşlukları Düzenleyici ekleme temel Düzenleyici uzantıları oluşturmak için Visual Studio SDK'sı dahil edilen öğe şablonları kullanabilirsiniz. Düzenleyici öğesi şablonları, Visual C# veya Visual Basic VSIX projeleri için kullanılabilir.  
  
## <a name="prerequisites"></a>Önkoşullar  
 Visual Studio 2015'ten başlayarak, size Visual Studio SDK İndirme Merkezi'nden yüklemeyin. Visual Studio kurulumunda isteğe bağlı bir özellik olarak eklenmiştir. VS SDK'yi daha sonra yükleyebilirsiniz. Daha fazla bilgi için [Visual Studio SDK'yı yükleme](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="create-a-classifier-extension"></a>Bir sınıflandırıcı uzantısı oluşturma  
 Uygun metni renkler bir düzenleyici sınıflandırıcı Düzenleyicisi sınıflandırıcı öğe şablonu oluşturur (Bu durumda, her şeyi) herhangi bir metin dosyası olarak.  
  
1.  İçinde **yeni proje** iletişim kutusunda **Visual C#** veya **Visual Basic** ve ardından **genişletilebilirlik**. İçinde **şablonları** bölmesinde **VSIX projesi**. İçinde **adı** kutusuna `TestClassifier`. **Tamam**'ı tıklatın.  
  
2.  İçinde **Çözüm Gezgini**, proje düğümüne sağ tıklayıp **Ekle** > **yeni öğe**. Git için Visual C# **genişletilebilirlik** düğümünü seçip alt **Düzenleyicisi sınıflandırıcı**. Varsayılan dosya adı bırakın (*EditorClassifier1.cs*).  
  
3.  Aşağıdaki gibi dört kod dosyası vardır:  
  
    -   *EditorClassifier1.cs* içeren `EditorClassifier1` sınıfı.  
  
    -   *EditorClassifier1ClassificationDefinition.cs* içeren `EditorClassifier1ClassificationDefinition` sınıfı.  
  
    -   *EditorClassifier1Format.cs* içeren `EditorClassifier1Format` sınıfı.  
  
    -   *EditorClassifier1Provider.cs* içeren `EditorClassifier1Provider` sınıfı.  
  
4.  Projeyi oluşturmak ve hata ayıklamaya başlayın. Visual Studio'nun deneysel örneğinde görünür.  
  
     Bir metin dosyası açarsanız, tüm metin karşı Menekşe arka plan çizilir.  
  
## <a name="create-a-text-relative-adornment-extension"></a>Bir metin göreli kenarlığı uzantısı oluşturma  
 Tüm metin karakteri örneklerini düzenler bir metin göreli kenarlığı düzenleyici metin kenarlığı şablon oluşturur kırmızı anahat ve mavi bir arka plana sahip bir kutusunu kullanarak ' bir'. Metin göreli olduğundan kutusunu her zaman katmanları bile bunlar yeniden biçimlendirildi veya taşınırsa 'bir' karakter.  
  
1.  İçinde **yeni proje** iletişim kutusunda **Visual C#** veya **Visual Basic** ve ardından **genişletilebilirlik**. İçinde **şablonları** bölmesinde **VSIX projesi**. İçinde **adı** kutusuna `TestAdornment`. **Tamam**'ı tıklatın.  
  
2.  İçinde **Çözüm Gezgini**, proje düğümüne sağ tıklayıp **Ekle** > **yeni öğe**. Git için Visual C# **genişletilebilirlik** düğümünü seçip alt **düzenleyici metin kenarlığı**. Varsayılan dosya adı bırakın (*TextAdornment1.cs/vb*).  
  
3.  Şu şekilde iki kod dosyası vardır:  
  
    -   *TextAdornment1.cs* içeren `TextAdornment1` sınıfı.  
  
    -   *TextAdornment1TextViewCreationListener.cs* içeren `TextAdornment1TextViewCreationListener` sınıfı.  
  
4.  Projeyi oluşturmak ve hata ayıklamaya başlayın. Deneysel örneği açılır. Bir metin dosyası açarsanız, metindeki 'bir' tüm karakterleri mavi arka plan kırmızı özetlenmiştir.  
  
## <a name="create-a-viewport-relative-adornment-extension"></a>Görünüm penceresi göreli kenarlığı uzantısı oluşturma  
 Görünüm penceresinin sağ üst köşesinde kırmızı bir anahattına içeren bir Menekşe kutusu ekleyen bir Görünüm penceresi göreli kenarlığı Düzenleyicisi Görünüm penceresi kenarlığı şablon oluşturur.  
  
> [!NOTE]
>  **Görünüm penceresi** şu anda görüntülenen metin görünümünü alanıdır.  
  
### <a name="to-create-a-viewport-adornment-extension-by-using-the-editor-viewport-adornment-template"></a>Düzenleyici Görünüm penceresi kenarlığı şablonu kullanarak bir Görünüm penceresi kenarlığı uzantısı oluşturmak için  
  
1.  İçinde **yeni proje** iletişim kutusunda **Visual C#** veya **Visual Basic** ve ardından **genişletilebilirlik**. İçinde **şablonları** bölmesinde **VSIX projesi**. İçinde **adı** kutusuna `ViewportAdornment`. **Tamam**'ı tıklatın.  
  
2.  İçinde **Çözüm Gezgini**, proje düğümüne sağ tıklayıp **Ekle** > **yeni öğe**. Git için Visual C# **genişletilebilirlik** düğümünü seçip alt **Düzenleyicisi Görünüm penceresi kenarlığı**. Varsayılan dosya adı bırakın (*ViewportAdornment1.cs/vb*).  
  
3.  Şu şekilde iki kod dosyası vardır:  
  
    -   *ViewportAdornment1.cs* içeren `ViewportAdornment1` sınıfı.  
  
    -   *ViewportAdornment1TextViewCreationListener.cs* içeren `ViewportAdornment1TextViewCreationListener` sınıfı  
  
4.  Projeyi oluşturmak ve hata ayıklamaya başlayın. Deneysel örneği açılır. Yeni bir metin dosyası oluşturursanız, görünüm penceresinin sağ üst köşesinde kırmızı anahat içeren bir Menekşe kutusu görüntülenir.  
  
## <a name="create-a-margin-extension"></a>Bir kenar boşluğu uzantısı oluşturma  
 Düzenleyici kenar şablon sözcükleri birlikte görünen yeşil bir kenar boşluğu oluşturur **Merhaba Dünya!* Yatay kaydırma çubuğunun altında.  
  
### <a name="to-create-a-margin-extension-by-using-the-editor-margin-template"></a>Düzenleyici kenar şablonu kullanarak bir kenar boşluğu uzantısı oluşturma  
  
1.  İçinde **yeni proje** iletişim kutusunda **Visual C#** veya **Visual Basic** ve ardından **genişletilebilirlik**. İçinde **şablonları** bölmesinde **VSIX projesi**. İçinde **adı** kutusuna `MarginExtension`. **Tamam**'ı tıklatın.  
  
2.  İçinde **Çözüm Gezgini**, proje düğümüne sağ tıklayıp **Ekle** > **yeni öğe**. Git için Visual C# **genişletilebilirlik** düğümünü seçip alt **Düzenleyici kenar**. Varsayılan dosya adı (EditorMargin1.cs/vb) bırakın.  
  
3.  Şu şekilde iki kod dosyası vardır:  
  
    -   *EditorMargin1.cs* içeren `EditorMargin1` sınıfı.  
  
    -   *EditorMargin1Factory.cs* içeren `EditorMargin1Factory` sınıfı.  
  
4.  Bu projeyi oluşturun ve hata ayıklamayı başlatın. Deneysel örneği açılır. Sözcükleri olan yeşil bir kenar boşluğu bir metin dosyası açarsanız **Hello EditorMargin1** yatay kaydırma çubuğunun altında görüntülenir.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Dil hizmeti ve düzenleyici uzantı noktaları](../extensibility/language-service-and-editor-extension-points.md)
