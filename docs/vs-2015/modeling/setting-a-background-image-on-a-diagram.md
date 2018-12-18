---
title: Diyagram üzerinde arka plan görüntüsü ayarlama | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e334a24c-8521-4072-b50f-e59158dde145
caps.latest.revision: 4
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: fd9d5ca21dbe1b0444c650a127fc0184dfb640f1
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49240558"
---
# <a name="setting-a-background-image-on-a-diagram"></a>Diyagram Üzerinde Arka Plan Görüntüsü Ayarlama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

İçinde [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Görselleştirme ve modelleme SDK'sı, ayarlayabileceğiniz arka plan görüntüsü için oluşturulan bir tasarımcı özel kod kullanarak.  
  
## <a name="setting-the-background-image"></a>Arka plan görüntüsü ayarlama  
  
#### <a name="to-set-a-background-image-for-a-generated-designer"></a>İçin oluşturulan bir tasarımcının arka plan görüntüsü ayarlama  
  
1.  Diyagram arkaplanı olarak Dsl\Resources dizine geçerli proje için kullanmak istediğiniz görüntü dosyasını kopyalayın.  
  
2.  İçinde **Çözüm Gezgini**, Dsl\Resources klasöre sağ tıklayın, fareyle **Ekle**ve ardından **var olan öğe**.  
  
3.  İçinde **varolan öğeyi Ekle** iletişim kutusunda, Dsl\Resources klasöre gidin.  
  
4.  İçinde **dosya türü** listesinde **görüntü dosyaları**.  
  
5.  Kopyaladığınız dizine görüntü dosyasına tıklayın ve ardından **Ekle**.  
  
6.  DSL sağ tıklayın ve **özellikleri** Dsl proje özelliklerini açın.  
  
7.  Üzerinde **kaynakları** sekmesinde **bu projenin varsayılan kaynak dosyası içermiyor. Oluşturmak için buraya tıklayın.**  
  
8.  Resim sürükleyerek resim dosyası kaynak dosyaya ekleyin **Çözüm Gezgini** kaynakları penceresine.  
  
9. Dosya menüsünü açın ve proje özelliklerini Kaydet seçeneğine tıklayın.  
  
10. Dsl\Properties\Resources.resx dosya var ve ' % s'dosyası Resources.Designer.cs altındaki sahip olduğunu doğrulayın.  
  
11. Resources.Designer.cs eksikse, dosyaya Resources.resx tıklayın, **Çözüm Gezgini**.  
  
12. İçinde **özellikleri** penceresinde `Custom Tool` özelliğini `ResXFileCodeGenerator`.  
  
13. İçinde **Çözüm Gezgini**, Dsl projesini sağ tıklayın, fareyle **Ekle**, tıklatıp **yeni klasör**.  
  
14. Klasör adı **özel**.  
  
15. Özel klasörü sağ tıklatın, **Ekle**, tıklatıp **yeni öğe**.  
  
16. İçinde **Yeni Öğe Ekle** iletişim kutusundaki **şablonları** listesinde **kod dosyası**.  
  
17. İçinde **adı** kutusuna `BackgroundImage.cs`, tıklatıp **Ekle**.  
  
18. Ad alanı, diyagramı sınıf adı ve resim dosyası kaynak adını ayarlama BackgroundImage.cs dosyaya aşağıdaki kodu kopyalayın.  
  
     "MyDiagramClass" Dsl\GeneratedCode\Diagrams.cs içinde tanımlanan diyagram kısmi sınıf adıyla değiştirin. Bu gibi durumlarda, doğru ad alanı da Dsl\GeneratedCode\Diagrams.cs dosyadan alabilirsiniz.  
  
    ```  
    using System;  
    using Microsoft.VisualStudio.Modeling.Diagrams;  
  
    // Fix the namespace:  
    namespace Fabrikam.MyLanguage  
    {  
      // Fix the Diagram Class name - get it from GeneratedCode\Diagram.cs  
  
      public partial class Language29Diagram  
      {  
        protected override void InitializeInstanceResources()  
        {  
          // Fix the Resources namespace and the Image resource name:  
          ImageField backgroundField = new ImageField("background",  
              Fabrikam.MyLanguage.Properties.Resources.MyPicture);  
  
          backgroundField.DefaultFocusable = false;  
          backgroundField.DefaultSelectable = false;  
          backgroundField.DefaultVisibility = true;  
          backgroundField.DefaultUnscaled = false;  
  
          shapeFields.Add(backgroundField);  
  
          backgroundField.AnchoringBehavior  
            .SetTopAnchor(AnchoringBehavior.Edge.Top, 0.01);  
          backgroundField.AnchoringBehavior  
            .SetLeftAnchor(AnchoringBehavior.Edge.Left, 0.01);  
          backgroundField.AnchoringBehavior  
            .SetRightAnchor(AnchoringBehavior.Edge.Right, 0.01);  
          backgroundField.AnchoringBehavior  
            .SetBottomAnchor(AnchoringBehavior.Edge.Bottom, 0.01);  
  
          base.InitializeInstanceResources();  
        }  
      }  
    }  
    ```  
  
     Program kodunda modeli özelleştirme hakkında daha fazla bilgi için bkz. [gezinme ve güncelleştirme Program kodundaki modeli](../modeling/navigating-and-updating-a-model-in-program-code.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Şekiller ve bağlayıcıları tanımlama](../modeling/defining-shapes-and-connectors.md)   
 [Metin ve görüntü alanlarını özelleştirme](../modeling/customizing-text-and-image-fields.md)   
 [Gezinme ve Program kodundaki modeli güncelleştirme](../modeling/navigating-and-updating-a-model-in-program-code.md)   
 [Etki Alanına Özgü Dili Özelleştirmek için Kod Yazma](../modeling/writing-code-to-customise-a-domain-specific-language.md)



