---
title: Model öğeleri ve iş öğeleri | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.teamarch.common.removeworkitemsdialog
- vs.teamarch.common.linkworkitemsdialog
helpviewer_keywords:
- UML - extending, linking to TFS work items
- UML - extending, linking work items
- work items, creating from UML models
- UML model, creating work items
- work items, linking to UML models
- UML model, linking work items
ms.assetid: e687a490-0f93-412c-a1ff-eea83cf7ba07
caps.latest.revision: 49
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 55dfd83f3c9324b08bbb88c8404350c2aebf129f
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51752075"
---
# <a name="link-model-elements-and-work-items"></a>Model öğelerini ve iş öğelerini bağlama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Görevler, test çalışmalarını, hataları, gereksinimleri, sorunları ve Visual Studio'da model öğelerini ve Team Foundation Server veya Visual Studio Team Services iş öğelerini bağlantılandırarak modelinize ilgili diğer işleri izleyin. Bağlantılı iş öğelerini model öğeleriyle ilişkilendirmek bunlara belgeler ekleyin.  
  
 Bu özellik, Visual Studio'nun hangi sürümlerinin desteklediğini görmek için bkz: [mimari ve Modelleme Araçları sürüm desteği](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
> [!NOTE]
>  Bağlantılar oluşturmak ve açmak için Takım Gezgini'ni kullanmanız gerekir. Modelleme projenizin ve diyagramlarınızın, başkalarının bağlantılı diyagramları açamaması için sürüm denetimine iade edildiğinden emin olun.  
  
 Örneğin, şunları bağlayabilirsiniz:  
  
- Hikayenin sıralı işlemler olarak nasıl gerçekleştiğini açıklayan kullanıcı hikayesi iş öğesi ve etkinlik diyagramı  
  
- Kullanım durumunun doğru bir şekilde uygulandığından emin olmanızı sağlayan, kullanım durumu ve test çalışması iş öğelerindeki bir kullanım durumu  
  
- Özniteliğin uygulanmasında bir hata gösteren UML sınıf diyagramındaki ve hata iş öğesindeki bir öznitelik  
  
- Bileşenin gelişimini izleyen bileşen diyagramındaki ve görev iş öğesindeki bir bileşen. Böyle bir görev genellikle daha küçük görevlere ayrılır  
  
  İş öğelerini, şu öğelerde olduğu gibi modelleme diyagramlarında veya UML Model Gezgini'nde seçebileceğiz herhangi bir öğeye bağlayabilirsiniz:  
  
- UML modellerindeki UML sınıfları, yaşam çizgileri, kullanım durumları, alt sistemler, etkinlikler, nesne düğümleri, bileşenler, arabirimler gibi tüm öğeler  
  
- UML modellerindeki ilişkilendirme, genelleştirme, bağımlılık, akış ve iletiler gibi tüm ilişkiler  
  
- Sınıfların öznitelikleri ve işlemleri, yaşam çizgilerinin yürütme örnekleri, etkinliklerin giriş ve çıkış bağlantı noktaları, bileşenlerin parça ve bağlantı noktaları gibi öğelerin parçaları  
  
- Katmanlar ve katman bağımlılıkları  
  
- Açıklamalar ve açıklama bağlantıları  
  
- Diyagramlar. Bir diyagram seçmek için diyagramın boş bir kısmını seçin.  
  
> [!WARNING]
>  Zaten için TFS kaynak kod denetimi (oluşturmak veya bir çalışma öğesiyle bağlantılandırmak için SCC) bağlı olmanız gerekir. Farklı bir TFS SCC bağlantı açmayı denerseniz, Visual Studio otomatik olarak geçerli çözümü kapatır. Zaten için uygun SCC oluşturmak veya bir çalışma öğesiyle bağlantılandırmak denemeden önce bağlı olduğunuzdan emin olun. Visual Studio daha sonraki sürümleri için bir SCC bağlı değilseniz, menü komutlarını kullanılamaz.  
  
-   [Bir takım projesine Bağlan](#ConnectTFS)  
  
-   [Bir model öğesini yeni bir iş öğesine bağlama](#LinkNew)  
  
-   [Bir model öğesini varolan iş öğesine bağlama](#LinkExisting)  
  
-   [Bir model öğesine bağlı iş öğelerini görüntüle](#OpenWorkItem)  
  
-   [Bir iş öğesine bağlı model öğelerini görüntüleme](#ViewLinkedModels)  
  
-   [Model öğelerini ve iş öğeleri arasındaki bağlantıları silme](#RemoveLinks)  
  
-   [Sorun giderme](#Troubleshooting)  
  
##  <a name="ConnectTFS"></a> Bir takım projesine Bağlan  
 Ayrıca, takım projenize oluşturmak, görüntülemek veya bağlantıları kaldırmak için önce bağlanmanız gerekir.  
  
1.  Üzerinde **takım** menüsünde seçin **bağlantıları Yönet** Ekip Gezgini penceresi gösterilecek.  
  
2.  Doğru proje görünmezse, Takım Gezgini'nde seçin **bağlantıları Yönet** seçip **takım projesine Bağlan**. Ardından gerekirse doğru projeleri veya sunucuyu seçin.  
  
3.  İçinde **Takım Gezgini**, oluşturmak, bağlamak veya iş öğelerini görüntülemek istediğiniz projeyi seçin.  
  
##  <a name="LinkNew"></a> Bir model öğesini yeni bir iş öğesine bağlama  
  
1.  Kullanmak istediğiniz TFS örneğine bağlandığınızdan emin olun.  
  
2.  Modelleme diyagramında veya **UML Model Gezgini**, model öğesinin kısayol menüsünü açın.  
  
3.  Seçin **iş öğesi oluştur** ve oluşturmak istediğiniz iş öğesi türü.  
  
4.  İş öğesi formunda alanları doldurun. Seçin **iş öğesini kaydetmeniz**.  
  
     Visual Studio model öğesini yeni iş öğesine bağlar. Simge model öğesi üzerinde veya yakınında görünür.  
  
> [!WARNING]
>  Zaten için TFS kaynak kod denetimi (oluşturmak veya bir çalışma öğesiyle bağlantılandırmak için SCC) bağlı olmanız gerekir. Farklı bir TFS SCC bağlantı açmayı denerseniz, Visual Studio otomatik olarak geçerli çözümü kapatır. Zaten için uygun SCC oluşturmak veya bir çalışma öğesiyle bağlantılandırmak denemeden önce bağlı olduğunuzdan emin olun. Visual Studio daha sonraki sürümleri için bir SCC bağlı değilseniz, menü komutlarını kullanılamaz.  
  
##  <a name="LinkExisting"></a> Bir model öğesini varolan iş öğesine bağlama  
 Model öğelerini iş öğelerine bağladığınızda, iş öğesinden değil, model öğesinden başlayın.  
  
1.  Kullanmak istediğiniz TFS örneğine bağlandığınızdan emin olun.  
  
2.  Modelleme diyagramında veya **UML Model Gezgini**, model öğesinin kısayol menüsünü açın. Seçin **iş öğesine Bağla**. Projenizde seçip **proje** alan.  
  
3.  Aşağıdaki adımlardan birini uygulayarak bir veya daha çok iş öğesini model öğesine bağlamak için seçin:  
  
    -   Bir sorgu seçin **kaydedilmiş sorgu**.  
  
    -   İçinde boşluklarla ayırarak bir veya daha fazla çalışma öğeleri kimliklerini yazın **kimlikleri**.  
  
    -   Bir sözcük veya tümcecik **başlık içerir**.  
  
4.  Seçin **Bul**.  
  
5.  İş öğesi listesinde, iş öğesi veya bağlamak istediğiniz iş öğelerini seçin.  
  
     İşiniz bittiğinde **iş öğelerini** model öğesi özelliği öncekinden daha büyük bir sayıyı gösterir. Simge model öğesi üzerinde veya yakınında da görünür.  
  
> [!WARNING]
>  Zaten için TFS kaynak kod denetimi (oluşturmak veya bir çalışma öğesiyle bağlantılandırmak için SCC) bağlı olmanız gerekir. Farklı bir TFS SCC bağlantı açmayı denerseniz, Visual Studio otomatik olarak geçerli çözümü kapatır. Zaten için uygun SCC oluşturmak veya bir çalışma öğesiyle bağlantılandırmak denemeden önce bağlı olduğunuzdan emin olun. Visual Studio daha sonraki sürümleri için bir SCC bağlı değilseniz, menü komutlarını kullanılamaz.  
  
##  <a name="OpenWorkItem"></a> Bir model öğesine bağlı iş öğelerini görüntüle  
  
1.  İçinde **Takım Gezgini**, bağlı olduğunuz takım projesi için model öğesine bağlı iş öğesi burada emin olun.  
  
2.  Modelleme diyagramında veya **UML Model Gezgini**, model öğesinin kısayol menüsünü açın. Seçin **iş öğelerini görüntüle** bağlı iş öğelerinin listesini görüntülemek için.  
  
    > [!NOTE]
    >  Yalnızca bağlı olan sunucudaki iş öğeleri görünür. Tüm iş öğelerini, doğru sunucuya bağlı olduğunuzdan emin olun görmüyorsanız **Takım Gezgini**.  
  
##  <a name="ViewLinkedModels"></a> Bir iş öğesine bağlı model öğelerini görüntüleme  
 Modelleme diyagramları ve bir iş öğesi Visual Studio Team Services ve Team Foundation Server 2012 veya sonraki sürümlerde bağlı öğeleri görüntüleyebilirsiniz. Örneğin, bir iş öğesi uygulanacak yeni sınıfların tasarımını gösteren sınıf modellerine bağlı olabilir.  
  
1.  İçinde **Takım Gezgini**, bağlı olduğunuz takım projesi için burada model öğelerini iş öğesine bağlı olduğundan emin olun.  
  
    > [!NOTE]
    >  Bağlantılı model öğelerini görüntülemek için yalnızca Takım Gezgini'ni kullanabilirsiniz; Team Web Access'i kullanamazsınız. Çalışma alanınızın modelleme diyagramlarını veya öğeleri içeren modelleme projesiyle eşleştiğinden emin olun. Çalışma alanınız yoksa, oluşturmanız gerekir. Bkz: [sorun giderme](#Troubleshooting) ve [oluşturma ve çalışma alanlarıyla çalışma](http://msdn.microsoft.com/library/1d7f6ed8-ec7c-48f8-86da-9aea55a90d5a).  
  
2.  İş öğesini açın, **bağlantıları**. Altında **Model bağlantısı**, bağlantılı model öğesinin kısayol menüsünü açın. Seçin **bağlı öğeyi Aç**.  
  
     ![Bir iş öğesi açık bağlantılı model öğesinden](../modeling/media/workitem-openlinkedmodelelement.png "WorkItem_OpenLinkedModelElement")  
  
##  <a name="RemoveLinks"></a> Model öğelerini ve iş öğeleri arasındaki bağlantıları silme  
 Model öğesinden başlayarak bağlantılı bir iş öğesini kaldırın. Bu, model öğesinin ters bağlantısını iş öğesinden kaldırır. Aksi takdirde, iş öğesiyle başlarsanız, model öğesinden iş öğesine giden ters bağlantı silinmez.  
  
1.  Modelleme diyagramında veya **UML Model Gezgini**, model öğesinin kısayol menüsünü açın.  
  
2.  Seçin **iş öğelerini Kaldır**.  
  
     \- veya -  
  
    1.  Seçin **özellikleri**, ardından **iş öğeleri** bağlantılı iş öğesi sayısı burada görünür.  
  
    2.  İçinde **iş öğelerini** özelliği, üç nokta düğmesini **[...]** .  
  
        > [!NOTE]
        >  Yalnızca geçerli sunucudaki iş öğeleri görünür. Liste boşsa, ancak iş öğelerinin sayısı sıfır değil, doğru sunucuya bağlandığınızdan emin olun **Takım Gezgini**.  
  
3.  Altında **iş öğelerinin bağlantılarını Kaldır**, bağlantısını kaldırmak istediğiniz seçili öğeleri temizleyin. Seçin **Tamam**.  
  
##  <a name="Troubleshooting"></a> Sorun giderme  
  
|**Sorunu**|**Olası nedeni**|**Çözümleme**|  
|---------------|------------------------|--------------------|  
|Bağlamak istediğiniz model öğesi bulunamıyor.|Öğe olan modelleme projesindeki diyagram üzerinde olabilir [!INCLUDE[esprscc](../includes/esprscc-md.md)]. Diyagramla eşleşen bir çalışma alanınız olmayabilir.|Çalışma alanınızı modelleme projesiyle ve diyagramla eşleştirin. Çalışma alanınız yoksa, oluşturmanız gerekir.<br /><br /> Bu sorun için görünen hata iletisi, çalışma alanınızı eşleştirmek için kullanabileceğiniz yolu içerir.<br /><br /> Bkz: [oluşturma ve çalışma alanlarıyla çalışma](http://msdn.microsoft.com/library/1d7f6ed8-ec7c-48f8-86da-9aea55a90d5a).|  
|Bağlantılı model öğesi bulunamıyor.|Bağlantılı öğe taşınmış, yeniden adlandırılmış veya silinmiş bir diyagram üzerinde olabilir.|1.  İş öğesinde model öğesinin bağlantısını silin.<br />2.  İş öğesinden model öğesine yeni bir bağlantı oluşturun.|  
|İş öğesinde beklediğiniz bağlantılı model öğeleri yoktur.|Bir iş öğesi, yalnızca bağlantılı iş öğesinden oluşturulmuşsa bağlantılı katmanı öğesini gösterir. Takım kullanmıyorsa [!INCLUDE[esprscc](../includes/esprscc-md.md)], diyagramların yerel yolu bağlantıları oluşturmak için kullanılır. Modelleme projesi ve diyagramları daysanız [!INCLUDE[esprscc](../includes/esprscc-md.md)], projeye erişebilen tüm takım üyeleri iş öğelerinde bağlantılı öğeleri görüntüleyebilir.|İş öğesini yenilemeyi deneyin.|  
|Bir iş öğesinden model öğesine giden bağlantının silinmesi, model öğesinden iş öğesine giden bağlantıyı silmez.||Model öğesinden başlayarak iş öğesine giden bağlantıyı silin.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [UML modellerini ve diyagramları düzenleme](../modeling/edit-uml-models-and-diagrams.md)   
 [Uygulamanız için model oluşturma](../modeling/create-models-for-your-app.md)



