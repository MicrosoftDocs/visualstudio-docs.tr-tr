---
title: Katman diyagramları ile kodu doğrulama | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- layer diagrams, validating
- validation, layer diagrams
- validation, code
- code exploration, validating
- architecture, validating
- Visual Studio Ultimate, validating code
- validation, architecture
- validation, dependencies
- MSBuild, tasks
- MSBuild, layer diagrams
- MSBuild, validating code
ms.assetid: 70cbe55d-4b33-4355-b0a7-88c770a6f75c
caps.latest.revision: 84
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 4d010345c551572bb6458110d2de9ca33fc73155
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51792170"
---
# <a name="validate-code-with-layer-diagrams"></a>Katman diyagramları ile kod doğrulama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Kodun tasarımıyla çakışmamasını sağlamak için kodunuzu Visual Studio'da katman diyagramları ile doğrulayın. Bu, şu konularda size yardımcı olabilir:  
  
- Kodunuzdaki ve katman diyagramındaki bağımlılıklar arasında çakışmaları bulun.  
  
- Önerilen değişiklikler tarafından etkilenebilecek bağımlılıkları bulun.  
  
   Örneğin, olası mimari değişiklikleri göstermek için katman diyagramını düzenleyebilir ve ardından etkilenen bağımlılıkları görmek için kodu doğrulayabilirsiniz.  
  
- Kodu yeniden düzenleyin veya kodu farklı bir tasarıma geçirin.  
  
   Kodu farklı bir mimariye taşıdığınız zaman iş gerektiren kodu veya bağımlılıkları bulun.  
  
  **Gereksinimler**  
  
- Visual Studio  
  
- Kodu Team Foundation Yapısı ile otomatik olarak doğrulamak için visual Studio Team Foundation Yapı sunucunuzda  
  
- Katman diyagramına sahip bir modelleme projesi olan çözüm. Bu katman diyagramı, doğrulamak istediğiniz Visual C# .NET veya Visual Basic .NET projelerindeki yapılara bağlı olmalıdır. Bkz: [kodunuz aracılığıyla katman diyagramları oluşturma](../modeling/create-layer-diagrams-from-your-code.md).  
  
  Bu özellik, Visual Studio'nun hangi sürümlerinin desteklediğini görmek için bkz: [mimari ve Modelleme Araçları sürüm desteği](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
  Visual Studio'daki açık bir katman diyagramından veya komut isteminden kodu el ile doğrulayabilirsiniz. Ayrıca yerel yapıları veya Team Foundation Yapısı'nı çalıştırırken kodu otomatik olarak doğrulayabilirsiniz. Bkz: [kanal 9 videosu: tasarım ve katman diyagramlarını kullanarak Mimarinizi geçerli](http://go.microsoft.com/fwlink/?LinkID=252073).  
  
> [!IMPORTANT]
>  Team Foundation Yapısı ile katman doğrulaması çalıştırmak istiyorsanız, yapı sunucunuzda ayrıca Visual Studio'nun aynı sürümünü yüklemeniz gerekir.  
  
-   [Bir öğenin doğrulamayı destekleyip desteklemediğini görme](#SupportsValidation)  
  
-   [Diğer .NET derlemelerini ve projelerini doğrulama için dahil](#IncludeReferences)  
  
-   [Kodu el ile doğrulama](#ValidateManually)  
  
-   [Kodu otomatik olarak doğrulama](#ValidateAuto)  
  
-   [Katman doğrulama sorunlarını giderme](#TroubleshootingValidation)  
  
-   [Katman doğrulama hatalarını anlama ve çözme](#UnderstandingValidationErrors)  
  
##  <a name="SupportsValidation"></a> Bir öğenin doğrulamayı destekleyip desteklemediğini görme  
 Katmanları Web sitelerine, Office belgeleri, düz metin dosyaları ve birden çok uygulama arasında paylaşılan projelerdeki dosyaları bağlayabilirsiniz, ancak doğrulama işlemi bunları içermeyecektir. Doğrulama hataları, aralarında hiçbir bağımlılığın görünmediği ayrı katmanlara bağlanmış projelere veya derlemelere olan başvurular için görünmez. Kod bu başvuruları kullanmazsa böyle başvurular bağımlılık olarak düşünülmez.  
  
1.  Katman diyagramında bir veya daha fazla katmanları seçin, seçiminize sağ tıklayın ve ardından **bağlantıları görüntüle**.  
  
2.  İçinde **Katman Gezgini**, bakmak **doğrulamayı destekler** sütun. Değer false ise, öğe doğrulamayı desteklemez.  
  
##  <a name="IncludeReferences"></a> Diğer .NET derlemelerini ve projelerini doğrulama için dahil  
 Öğeleri katman diyagramına sürüklediğinizde, karşılık gelen .NET derlemeleri veya projelerine başvurular otomatik olarak eklenir **katman başvuruları** modelleme projesindeki klasör. Bu klasör, doğrulama sırasında analiz edilen derlemeler ve projeler için başvurular içerir. Ayrıca, diğer .NET derlemelerini ve projeleri katman diyagramına el ile sürüklemeden doğrulama için ekleyebilirsiniz.  
  
1.  İçinde **Çözüm Gezgini**, modelleme projesine sağ tıklayın veya **katman başvuruları** klasörünü ve ardından **Başvuru Ekle**.  
  
2.  İçinde **Başvuru Ekle** iletişim kutusunda, derlemeleri veya projeleri seçin ve ardından **Tamam**.  
  
##  <a name="ValidateManually"></a> Kodu el ile doğrulama  
 Çözüm öğelerine bağlı açık bir katman diyagramınız varsa, çalıştırabileceğiniz **doğrulama** diyagramı kısayol komutu. Çalıştırmak için komut istemini kullanabilirsiniz **msbuild** komutunu **ValidateArchitecture** özel özellik kümesine **True**. Örneğin, kodda değişiklik yaparken bağımlılık çakışmalarını önceden yakalayabilmek için düzenli olarak katman doğrulama gerçekleştirin.  
  
#### <a name="to-validate-code-from-an-open-layer-diagram"></a>Kodu açık bir katman diyagramından doğrulamak için  
  
1.  Diyagram yüzeyine sağ tıklayın ve ardından **Mimariyi Doğrula**.  
  
    > [!NOTE]
    >  Varsayılan olarak, **derleme eylemi** özelliği için katman diyagramı (.layerdiagram) dosyasındaki **doğrulama** böylece doğrulama işleminde diyagramın dahildir.  
  
     **Hata listesi** penceresi oluşan hataları bildirir. Doğrulama hataları hakkında daha fazla bilgi için bkz. [katman doğrulama hatalarını anlama ve çözme](#UnderstandingValidationErrors).  
  
2.  Her hatanın kaynağını görüntülemek için hataya çift **hata listesi** penceresi.  
  
    > [!NOTE]
    >  [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] bir kod Haritası hata kaynağı yerine gösterebilir. Bu, kodun katman diyagramı tarafından belirlenmeyen derlemesinde bağımlılığı varsa ya da kodun katman diyagramı tarafından belirlenen bağımlılığı eksikse ortaya çıkar. Kod haritası veya bağımlılık var olup olmadığını belirlemek için kodu gözden geçirin. Kod haritaları hakkında daha fazla bilgi için bkz: [Çözümlerinizdeki bağımlılıkları eşleme](../modeling/map-dependencies-across-your-solutions.md).  
  
3.  Hataları yönetmek için bkz: [doğrulama hatalarını Yönet](#ManageErrors).  
  
#### <a name="to-validate-code-at-the-command-prompt"></a>Kodu komut isteminde doğrulamak için  
  
1. Açık [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] komut istemi.  
  
2. Aşağıdakilerden birini seçin:  
  
   - Çözümde belirli modelleme projesine karşı kodu doğrulamak için çalıştırma [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] aşağıdaki özel özelliklerle.  
  
     ```  
     msbuild <FilePath+ModelProjectFileName>.modelproj /p:ValidateArchitecture=true  
     ```  
  
     - veya -  
  
       Modelleme içeren klasöre göz atın projesi (.modelproj) dosyası hem de katman diyagramını ve ardından çalıştırın [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] aşağıdaki özel özelliklerle:  
  
     ```  
     msbuild /p:ValidateArchitecture=true   
     ```  
  
   - Kodu Çözümdeki tüm modelleme projelerine karşı doğrulamak için çalıştırma [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] aşağıdaki özel özelliklerle:  
  
     ```  
     msbuild <FilePath+SolutionName>.sln /p:ValidateArchitecture=true   
     ```  
  
     - veya -  
  
       Bir katman diyagramı içeren modelleme projesini içermesi gerekir ve ardından çalıştırın çözüm klasörüne gözatın [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] aşağıdaki özel özelliklerle:  
  
     ```  
     msbuild /p:ValidateArchitecture=true  
     ```  
  
     Oluşan hatalar listelenecektir. Hakkında daha fazla bilgi için [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)], bkz: [MSBuild](../msbuild/msbuild.md) ve [MSBuild görevi](../msbuild/msbuild-task.md).  
  
   Doğrulama hataları hakkında daha fazla bilgi için bkz. [katman doğrulama hatalarını anlama ve çözme](#UnderstandingValidationErrors).  
  
###  <a name="ManageErrors"></a> Doğrulama Hatalarını Yönet  
 Geliştirme işlemi sırasında, doğrulama esnasında bildirilen çakışmaların bazılarını gizlemek isteyebilirsiniz. Örneğin, zaten çözdüğünüz veya özel senaryonuzla ilgili olmayan hataları gizlemek isteyebilirsiniz. Hatayı gizlediğinizde, bir iş öğesi oturum açmak için iyi bir uygulamadır [!INCLUDE[esprfound](../includes/esprfound-md.md)].  
  
> [!WARNING]
>  Zaten için TFS kaynak kod denetimi (oluşturmak veya bir çalışma öğesiyle bağlantılandırmak için SCC) bağlı olmanız gerekir. Farklı bir TFS SCC bağlantı açmayı denerseniz, Visual Studio otomatik olarak geçerli çözümü kapatır. Zaten için uygun SCC oluşturmak veya bir çalışma öğesiyle bağlantılandırmak denemeden önce bağlı olduğunuzdan emin olun. Visual Studio daha sonraki sürümleri için bir SCC bağlı değilseniz, menü komutlarını kullanılamaz.  
  
##### <a name="to-create-a-work-item-for-a-validation-error"></a>Doğrulama hatası için bir öğesi oluşturmak üzere  
  
- İçinde **hata listesi** penceresinde hataya sağ tıklayın, fareyle **iş öğesi oluştur**ve ardından oluşturmak istediğiniz iş öğesinin türüne tıklayın.  
  
  Doğrulama hatalarını yönetmek için bu görevleri kullanın **hata listesi** penceresi:  
  
|**Hedef**|**Aşağıdaki adımları izleyin**|  
|------------|----------------------------|  
|Doğrulama sırasında seçili hataları gizleme|Bir veya birden çok seçili hataya sağ tıklayın, fareyle **doğrulama hatalarını Yönet**ve ardından **Hataları Gizle**.<br /><br /> Gizlenen hatalar üstü çizili biçimde görünür. Doğrulamayı daha sonra çalıştırdığınızda bu hatalar görünmez.<br /><br /> Gizlenen hatalar, ilgili katman diyagramı dosyası için .gizlenenler dosyasında izlenir.|  
|Seçili hataların gizlenmesini durdurma|Seçili gizlenen hata veya hatalara sağ tıklayın, fareyle **doğrulama hatalarını Yönet**ve ardından **hataları gizlemeyi Durdur**.<br /><br /> Doğrulamayı daha sonra çalıştırdığınızda seçili gizlenen hatalar görünecektir.|  
|Tüm gizlenmiş hataları geri yükleme **hata listesi** penceresi|Herhangi bir yere sağ **hata listesi** penceresi **doğrulama hatalarını Yönet**ve ardından **tüm gizlenmiş hataları göster**.|  
|Tüm gizlenmiş Hataları Gizle **hata listesi** penceresi|Herhangi bir yere sağ **hata listesi** penceresi **doğrulama hatalarını Yönet**ve ardından **tüm gizlenmiş Hataları Gizle**.|  
  
##  <a name="ValidateAuto"></a> Kodu otomatik olarak doğrulama  
 Her yerel bir yapı çalıştırışınızda katman doğrulama gerçekleştirebilirsiniz. Takınınız Team Foundation Yapısı kullanıyorsa, özel bir MSBuild görevi oluşturarak belirtebileceğiniz geçitli iadelerle katman doğrulaması gerçekleştirebilir ve doğrulama hatalarını toplamak için yapı raporları kullanabilirsiniz. Geçitli iade yapıları oluşturmak için bkz [değişiklikleri doğrulamak için geçişli iade derleme işlemi kullanın](http://msdn.microsoft.com/library/9cfc8b9c-1023-40fd-8ab5-1b1bd9c172ec).  
  
#### <a name="to-validate-code-automatically-during-a-local-build"></a>Kodu yerel yapı sırasında otomatik olarak doğrulamak için  
  
-   Modelleme projesi (.modelproj) dosyası açmak için metin düzenleyicisi kullanın ve ardından aşağıdaki özelliği ekleyin:  
  
```  
<ValidateArchitecture>true</ValidateArchitecture>  
```  
  
 \- veya -  
  
1. İçinde **Çözüm Gezgini**katman diyagramı veya diyagramları içeren modelleme projesine sağ tıklayın ve ardından **özellikleri**.  
  
2. İçinde **özellikleri** penceresinde modelleme projesinin ayarlayın **Mimariyi Doğrula** özelliğini **True**.  
  
    Bu, doğrulama işlemi içinde modelleme projesini içerir.  
  
3. İçinde **Çözüm Gezgini**, doğrulama için kullanmak istediğiniz katman diyagramı (.layerdiagram) dosyasına tıklayın.  
  
4. İçinde **özellikleri** penceresinde emin olun diyagramın **derleme eylemi** özelliği **doğrulama**.  
  
    Buna, doğrulama işlemindeki katman diyagramı dahildir.  
  
   Hata Listesi penceresindeki hataları yönetmek için bkz: [doğrulama hatalarını Yönet](#ManageErrors).  
  
#### <a name="to-validate-code-automatically-during-a-team-foundation-build"></a>Kodu Team Foundation Yapısı sırasında otomatik olarak doğrulamak için  
  
1. İçinde **Takım Gezgini**yapı tanımına çift tıklayın ve ardından **işlem**.  
  
2. Altında **yapı işlemi parametreleri**, genişletme **derleme**ve aşağıdakileri yazın **MSBuild bağımsız değişkenleri** parametresi:  
  
    `/p:ValidateArchitecture=true`  
  
   Doğrulama hataları hakkında daha fazla bilgi için bkz. [katman doğrulama hatalarını anlama ve çözme](#UnderstandingValidationErrors). Hakkında daha fazla bilgi için [!INCLUDE[esprbuild](../includes/esprbuild-md.md)], bkz:  
  
-   [Uygulamayı oluşturun](http://msdn.microsoft.com/library/a971b0f9-7c28-479d-a37b-8fd7e27ef692)  
  
-   [Yapı işleminiz için varsayılan şablonu kullanın](http://msdn.microsoft.com/library/43930b12-c21b-4599-a980-2995e3d16e31)  
  
-   [UpgradeTemplate.xaml temelindeki bir eski yapı değiştirme](http://msdn.microsoft.com/library/ee1a8259-1dd1-4a10-9563-66c5446ef41c)  
  
-   [Yapı işlemi şablonunuzu özelleştirme](http://msdn.microsoft.com/library/b94c58f2-ae6f-4245-bedb-82cd114f6039)  
  
-   [Bir çalışan yapı ilerlemesini izleme](http://msdn.microsoft.com/library/e51e3bad-2d1d-4b7b-bfcc-c43439c6c8ef)  
  
##  <a name="TroubleshootingValidation"></a> Katman doğrulama sorunlarını giderme  
 Aşağıdaki tabloda katman doğrulama sorunları ve bunların çözümü açıklanmaktadır. Bu sorunlar, kod ve tasarım arasındaki çakışmalarla sonuçlanan hatalardan ayrılır. Bu hatalar hakkında daha fazla bilgi için bkz. [katman doğrulama hatalarını anlama ve çözme](#UnderstandingValidationErrors).  
  
|**Sorunu**|**Olası nedeni**|**Çözümleme**|  
|---------------|------------------------|--------------------|  
|Doğrulama hataları beklendiği gibi gerçekleşmez.|Doğrulama Çözüm Gezgini'ndeki diğer katman diyagramlarından kopyalanmış ve aynı modelleme projesinde bulunan katman diyagramlarında işe yaramaz. Bu şekilde kopyalanan katman diyagramları, orijinal katman diyagramıyla aynı başvuruları içerir.|Modelleme projesine yeni bir katman diyagramı ekleyin.<br /><br /> Öğeleri kaynak katmanı diyagramından yeni diyagrama kopyalayın.|  
  
##  <a name="UnderstandingValidationErrors"></a> Anlama ve katman doğrulama hatalarını çözme  
 Kodu katman diyagramına karşı doğruladığınız zaman, kod tasarımla çakıştığında doğrulama hataları oluşur. Örneğin, aşağıdaki durumlar doğrulama hatalarının oluşmasına neden olabilir:  
  
- Yapı yanlış katmana atanmış. Bu durumda, yapıyı taşıyın.  
  
- Sınıf gibi bir yapı, başka bir sınıfı mimarinizle çakışacak şekilde kullanıyor. Bu durumda, bağımlılığı kaldırmak için kodu yeniden düzenleyin.  
  
  Bu hataları çözmek için doğrulama sırasında daha fazla hata görünmeyene kadar kodu güncelleştirin. Bu görevi yinelemeli bir şekilde gerçekleştirebilirsiniz.  
  
  Aşağıdaki bölümde, bu hatalarda kullanılan sözdizimi belirtilmekte, bu hataların anlamı açıklanmakta ve bunları çözmek veya yönetmek için yapabilecekleriniz önerilmektedir.  
  
|**Söz dizimi**|**Açıklama**|  
|----------------|---------------------|  
|*ArtifactN*(*ArtifactTypeN*)|*ArtifactN* Katman diyagramında bir katman ile ilişkilendirilmiş bir yapıdır.<br /><br /> *ArtifactTypeN* türü *ArtifactN*, gibi bir **sınıfı** veya **yöntemi**, örneğin:<br /><br /> MySolution.MyProject.MyClass.MyMethod(Method)|  
|*NamespaceNameN*|Bir ad alanının adı.|  
|*LayerNameN*|Katman diyagramındaki katmanın adı.|  
|*DependencyType*|Arasındaki bağımlılık ilişkisinin türü *Artifact1* ve *Artifact2*. Örneğin, *Artifact1* sahip bir **çağrıları** ilişkisine sahip *Artifact2*.|  
  
|**Hata sözdizimi**|**Hata açıklaması**|  
|----------------------|---------------------------|  
|AV0001: Geçersiz bağımlılık: *Artifact1*(*ArtifactType1*)--> *Artifact2*(*ArtifactType2*)<br /><br /> Katmanlar: *LayerName1*, *LayerName2* &#124; bağımlılıkları: *DependencyType*|*Artifact1* içinde *LayerName1* bir bağımlılık olmamalıdır *Artifact2* içinde *LayerName2* çünkü *LayerName1* doğrudan bir bağımlılık yok *LayerName2*.|  
|AV1001: Geçersiz Namespace: *Yapıt*<br /><br /> Katman: *LayerName* &#124; gerekli Namespace: *NamespaceName1* &#124; geçerli Namespace: *NamespaceName2*|*LayerName* , ilişkilendirilmiş yapılarının öğesine ait olmasını gerektirir *NamespaceName1*. *Yapıt* bulunduğu *NamespaceName2*değil *NamespaceName1*.|  
|AV1002: Yasak Namespace üzerinde bağlıdır: *Artifact1*(*ArtifactType1*) &#124; *Artifact2*(*ArtifactType2*)<br /><br /> Katman: *LayerName* &#124; Namespace Yasak: *NamespaceName* &#124; bağımlılıkları: *DependencyType*|*LayerName* gerektirir, ilişkilendirilmiş yapılarının bağımlı olduğunu *NamespaceName*. *Artifact1* bağlı olamaz *Artifact2* çünkü *Artifact2* bulunduğu *NamespaceName*.|  
|AV1003: Yasak Namespace içinde: *Yapıt*(*ArtifactType*)<br /><br /> Katman: *LayerName* &#124; Namespace Yasak: *NamespaceName*|*LayerName* , ilişkilendirilmiş yapılarının öğesine ait olmamasını gerektirir *NamespaceName*. *Yapıt* ait *NamespaceName*.|  
|AV3001: eksik bağlantı: katman '*LayerName*'bağlantı'*Yapıt*' bulunamıyor. Eksik bir derleme başvurunuz mu var?|*LayerName* , bulunamayan bir yapıya bağlanır. Örneğin, sınıfla kurulan bir bağlantı kayıp olabilir; çünkü modelleme projesinde sınıfı içeren derlemeye yapılan bir başvuru yoktur.|  
|AV9001: Mimari çözümleme iç hatalar buldu. Sonuçlar tamamlanmamış olabilir. Daha fazla bilgi için ayrıntılı yapı olay günlüğü veya çıkış penceresine bakın.|Daha fazla ayrıntı için yapı olay günlüğü veya çıkış penceresine bakın.|  
  
## <a name="security"></a>Güvenlik  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Geliştirme sırasında sisteminizi doğrulama](../modeling/validate-your-system-during-development.md)



