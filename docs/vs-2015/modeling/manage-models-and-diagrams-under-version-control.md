---
title: Sürüm denetimi altındaki modelleri ve diyagramları yönetme | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- models, version control
ms.assetid: ca6443e3-6d11-4da8-aae7-ca7dcc410076
caps.latest.revision: 32
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 20cb2e89a85f00782a172245dcdd8f47025ddd12
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51738042"
---
# <a name="manage-models-and-diagrams-under-version-control"></a>Sürüm denetimi altındaki modelleri ve diyagramları yönetme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Modelleme projeleri ve diyagramları, kod haritaları (.dgml dosyaları) dahil olmak üzere farklı sürümlerini yönetmek [Team Foundation sürüm denetimi veya Git kullanan](http://msdn.microsoft.com/library/33267cee-fe5f-4aa3-b2cd-6d22ceace314); ya da şirket içi Team Foundation Server ile veya Visual ile bulutta Studio Team Services.  
  
 Bu özellik, Visual Studio'nun hangi sürümlerinin desteklediğini görmek için bkz: [mimari ve Modelleme Araçları sürüm desteği](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
> [!IMPORTANT]
>  Birkaç kullanıcı aynı modelleme projesinde çalıştığı zaman dikkatli olun. Kullanıma alabilirsiniz nasıl [Orta veya büyük ölçekli projelerde modelleri düzenlemek](../modeling/structure-your-modeling-solution.md).  
  
##  <a name="ModelingProjects"></a> Bir modelleme projesindeki dosyalar  
 Farklı dosyalar üzerinde çalıştıkları sağlanan birden fazla kullanıcı aynı zamanda, bir modelleme projesi üzerinde çalışabilir.  
  
 Farklı kullanıcılar tarafından yapılan değişiklikler arasındaki çakışmaları gidermek veya önlemek için modelin dosyalarda nasıl depolandığını anlamak önemlidir.  
  
-   Her bir paketi ayrı bir depolanır **.uml** tutulan dosya **ModelDefinition** proje klasörü. Modeli de sahip bir **.uml** dosya. Bu dosyalardan biri silinirse veya bozulursa, karşılık gelen paket veya model kaybolacaktır.  
  
-   Her diyagram iki dosyada depolanır. Örneğin, bir sınıf diyagramı vardır:  
  
    -   **DiagramName.classdiagram** -bu dosya silinir veya bozulursa diyagram kaybolacaktır değilse, ancak sınıflar ve ilişkilendirmeler modelde olmaya devam eder ve UML Model Gezgini'nde görülebilir.  
  
    -   **DiagramName.classdiagram.layout** -bu dosya, şekiller hala diyagramda görünür fakat boyutlarını ve konumlarını kaybederler. Her Düzen dosyası, diyagram dosyasına kuruluşudur. Bunu görmek için Çözüm Gezgini'nde diyagram dosyasının yanındaki [+]'e tıklayın.  
  
> [!NOTE]
>  Dosyalar arasında tutarlılık sağlamak önemlidir. Bir .uml dosyasındaki değişiklikleri geri almak için kaynak denetimi kullanın, örneğin, karşılık gelen değişiklikleri geri. * diyagramı ve .layout dosyaları aynı anda. Öğeleri temsil bir. \*diyagram dosyasını kaybolacak, ayrıca bir .uml dosyasındaki gösterilmez.  
  
##  <a name="Shared"></a> Paylaşılan modelleme projelerinde çalışma  
 Bir projenin farklı kısımlarındaki eşzamanlı işler arasındaki çakışmaları en aza indirmek için:  
  
-   Modelleme projenizi, işin farklı alanlarını gösteren paketlere bölün. Tüm modeli, kök modelde bırakmak yerine paketlerin içine taşıyın. Daha fazla bilgi için [paketleri ve ad alanlarını tanımlama](../modeling/define-packages-and-namespaces.md).  
  
-   Farklı kullanıcılar aynı anda aynı paket veya diyagram üzerinde çalışmamalıdır.  
  
-   Profilleri kullanıyorsanız, herkesin aynı profili yüklediğinden emin olun. Bkz: [modelinizi profiller ve stereotipler aracılığıyla özelleştirme](../modeling/customize-your-model-with-profiles-and-stereotypes.md).  
  
-   Yalnızca üzerinde çalıştığınız paketi değiştirdiğinizden emin olmak için:  
  
    -   Ayarlama **LinkedPackage** özelliği bir UML sınıfı, bileşenin veya kullanım durumu diyagramı.  
  
    -   Oluşturduktan hemen sonra UML Model Gezgini'nde, etkinlik veya etkileşimi paketinize sürükleyin. İlk düğümü etkinlik veya sıralı diyagramda oluşturduğunuzda bu öğe UML Model Gezgini'nde görünecektir.  
  
-   Paketleri izlemenize yardımcı olmak için gerçek paket adlarını yansıtmak için paket dosyalarını yeniden adlandırın.  
  
-   İçinde [!INCLUDE[esprscc](../includes/esprscc-md.md)], her zaman gerçekleştirmek **iade** ve **en son sürümü Al** tam modelleme projesinde işlemlerini tek dosyalarda.  
  
-   Her zaman gerçekleştirmek bir **alma** hemen, modelleme projesini iade etmeden önce işlemi.  
  
-   Gerçekleştirmeden önce her zaman tüm diyagramları kapatın bir **alma** işlemi.  
  
    > [!NOTE]
    >  Bir dosya açık değilse gerçekleştirirken bir **alma**, ve sonra dosyayı yeniden istenir işlem yerel değişikliklerde sonuçlanır. Bu durumda, tıklayın **Hayır**ve sonra tam projeyi yeniden yükleyin. İçinde **Çözüm Gezgini**, modelleme sağ proje düğümünü, tıklayın **projeyi**ve ardından **projeyi**.  
  
###  <a name="Exclusive"></a> Modeli özel erişim gerektiren değişiklikler  
 Aşağıdaki tür değişiklikleri yapmadan önce tüm projenin kullanıma al kilidine sahip olduğunuzdan emin olun.  
  
-   Yeniden adlandırma veya diğer paketlerden başvurulan öğeleri silme.  
  
-   Paket sınırları ilişkilerin özelliklerini değiştirme.  
  
-   Kullanıma Al kilitleri hakkında bilgi edinmek için [denetleyin bulun ve dosyaları düzenleme](http://msdn.microsoft.com/library/eb404d63-c448-4994-9416-3e6d50ec554a).  
  
##### <a name="to-move-a-diagram-file-in-or-out-of-a-project-folder"></a>Bir diyagram dosyası ya da proje klasörünün dışına taşımak için  
  
1.  Başlangıç **Visual Studio için geliştirici komut istemi**.  
  
2.  Kullanım **tf Yeniden Adlandır** diyagram dosyasını taşımak ve kendi **.layout** dosyası:  
  
     `tf rename sourcePath targetPath`  
  
3.  Çözüm Gezgini'nde, dosyaya sağ tıklayın ve ardından **projeden Çıkart**.  
  
4.  Dosyayı hedef klasöre ekleyin.  
  
     Çözüm Gezgini içinde hedef klasöre veya projeye sağ tıklayın, fareyle **Ekle**ve ardından **var olan öğe**. İletişim kutusunda, diyagram dosyasını seçin ve ardından **Ekle**. Düzen dosyası otomatik olarak eklenir.  
  
    > [!NOTE]
    >  Dosyayı farklı bir projeye taşıyamazsınız.  
  
##  <a name="Merging"></a> Değişiklikleri Model dosya ve diyagramlarında birleştirme  
 Birden fazla kullanıcı bir model üzerinde aynı anda çalıştıktan sonra [!INCLUDE[esprscc](../includes/esprscc-md.md)] değişiklikleri model dosyalarında birleştirme isteyip istemediğinizi sorar. Ayrı proje üzerinde çalışmak birleştirmelerin çoğundan kaçınacaktır önceki bölümlerde açıklandığı gibi kaçınır. Normalde, kalan çakışmalar güvenli bir şekilde otomatik olarak birleştirilebilir. Aşağıdaki tür değişiklikler hiçbir zorluğa neden olmamalıdır:  
  
-   Yaşam çizgilerinin türleri. Bir yaşam çizgisini etkileşime (sıralı diyagram) eklediğinizde, yaşam çizgisini varolan türden oluşturmadıysanız, türü kök modelde depolanır.  
  
-   Yeni etkinlikler ve etkileşimler başlangıçta kök modelde depolanır.  
  
-   Öğeleri ve ilişkileri ekleme.  
  
-   Yeniden adlandırma veya sadece kendi paketleri içinde başvurulmuş öğeleri silme.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Çözümleme ve mimarinin modelini oluşturma](../modeling/analyze-and-model-your-architecture.md)   
 [Modelleri paylaşma ve diyagramları dışarı aktarma](../modeling/share-models-and-exporting-diagrams.md)



