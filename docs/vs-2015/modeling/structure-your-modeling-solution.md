---
title: Modelleme çözümünüzün yapısını | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2ba70ba4-2cea-4e01-93c2-055903d59470
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 995192b372b9c1909ad3a7f164474cfaf63f07bc
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51784461"
---
# <a name="structure-your-modeling-solution"></a>Modelleme çözümünüzün yapısını oluşturma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Modelleri geliştirme projesindeki etkili bir şekilde kullanmak için ekip üyelerinin aynı anda farklı bölümlerini proje modelleri çalışabilmek için olmalıdır. Bu konuda öneren bir düzen uygulama katmanları genel bir karşılık gelen farklı parçalara bölmek için katman diyagramı.  
  
 Bir projeye başlayın ya da hızlı bir şekilde alt proje için seçtiğiniz Proje yapısı aşağıdaki proje şablonuna sahip kullanışlıdır. Bu konu, oluşturmak ve bu tür bir şablon kullanmak açıklar.  
  
 Bu konuda, birkaç ekip üyeleri gerektirecek kadar büyük olduğunu ve belki de Takımlarınız bir proje üzerinde çalışmakta olduğunuz varsayılır. Proje modelleri ve kod üzerinde kaynak denetim sistemi gibi depolanan [!INCLUDE[esprtfs](../includes/esprtfs-md.md)]. En azından bazı ekip üyeleri, modelleri geliştirmek için Visual Studio'yu kullanın ve diğer takım üyelerinin diğer Visual Studio sürümlerini kullanarak modelleri görüntüleyebilirsiniz.  
  
 Visual Studio'nun hangi sürümlerinin her aracı ve modelleme özelliğini desteklemek için bkz [mimari ve Modelleme Araçları sürüm desteği](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
## <a name="solution-structure"></a>Çözüm yapısı  
 Orta veya büyük bir projede takım yapısı, yapıya uygulamanın temel alır. Her takım bir Visual Studio çözümünü kullanır.  
  
#### <a name="to-divide-an-application-into-layers"></a>Bir uygulamayı katmanlara ayırmak için  
  
1. Web uygulaması, hizmet uygulama veya masaüstü uygulaması gibi uygulamanızın yapısını çözümlerinizi yapısını temel. Yaygın mimarileri çeşitli içinde ele alınmıştır [Microsoft Uygulama Mimarisi Kılavuzu'ndaki uygulama mimarisi türleri](http://go.microsoft.com/fwlink/?LinkId=196681).  
  
2. Oluşturma bir [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] çözümü mimarisi çözümü diyoruz. Bu çözüm, genel sistem tasarımı oluşturmak için kullanılır. Modelleri, ancak hiçbir kodu içerecek.  
  
    Bir katman diyagramı, bu çözüme ekleyin. Katman diyagramı üzerinde uygulamanız için seçtiğiniz mimarisi çizin. Örneğin, diyagramda bu katmanlar ve aralarındaki bağımlılıkları gösterebilir: sunu; İş mantığı; ve verileri.  
  
    Kullanarak aynı anda katman diyagramına ve yeni bir Visual Studio çözümü oluşturabilirsiniz **yeni UML veya katman diyagramı** komutunu **mimarisi** menüsü.  
  
3. Önemli iş kavramlarını göstermek ve tasarım tüm katmanların başvurulan kullanım mimarisi modeli UML diyagramları ekleyin.  
  
4. Her katman için ayrı bir Visual Studio çözümü Mimari katman diyagramı oluşturun.  
  
    Bu çözümler, katmanları kodunu geliştirmek için kullanılır.  
  
5. Katmanlar ve tüm katmanlarda yaygın kavramları tasarımları temsil edecek bir UML modeller oluşturun. Modelleri, böylece tüm modelleri Mimari çözümünden görülebilir ve ilgili modellerin her katmandan görülebilir düzenleyin.  
  
    Aşağıdaki yordamlardan birini kullanarak bunu gerçekleştirebilirsiniz. İlk seçenek, her katman için ayrı bir modelleme projesi oluşturur ve ikinci katmanlar arasında paylaşılan tek bir modelleme projesi oluşturur.  
  
   ###### <a name="to-use-a-separate-modeling-project-for-each-layer"></a>Her katman için ayrı bir modelleme projesi kullanmak için  
  
   1. Her katman çözümde bir modelleme projesi oluşturun.  
  
       Bu model gereksinimleri ve katman tasarımını açıklayan UML diyagramları içerir. Katman diyagramları, iç içe katmanlar Göster de içerebilir.  
  
       Artık her katman için bir model yanı sıra, uygulama mimarisi için bir modeli vardır. Her model, kendi çözümde yer alır. Bu katmanlardaki aynı anda çalışmak takım üyeleri sağlar.  
  
   2. Her katman çözüm modelleme projesini Mimarisi çözüme ekleyin. Bunu yapmak için mimarisi çözümü açın. Çözüm Gezgini'nde çözüm düğümüne sağ tıklayın, işaret ekleme ve ardından **mevcut proje**. Çözümdeki bir katman modelleme projesi (.modelproj) gidin.  
  
       Her model iki çözümlerinde görülebilir: "home", çözüm ve çözüm mimarisi.  
  
   3. Her katman modelleme projesine bir katman diyagramı ekleyin. Mimari katman diyagramının bir kopyasını başlatın. Katman diyagramının bağımlılıkları olmayan parçaları silebilirsiniz.  
  
       Bu katman ayrıntılı yapısını temsil eden katman diyagramları da ekleyebilirsiniz.  
  
       Bu diyagramları bu katmanda geliştirilen kodu doğrulamak için kullanılır.  
  
   4. Visual Studio kullanarak tüm katmanlara yönelik tasarım modelleri ve gereksinimleri mimarisi çözümde düzenleyin.  
  
       Her katman çözümde modele başvuran, söz konusu katman için kod geliştirin. Modeli güncelleştirmek için aynı bilgisayara kullanmadan geliştirme yapmak içerik modeli okumak ve modelleri oluşturulamıyor Visual Studio sürümlerini kullanarak kod geliştirin. Kod modelinden bu sürümleri de oluşturabilirsiniz.  
  
      Bu yöntem, aynı anda katman modellerini düzenleme geliştiriciler tarafından hiçbir kesintiye neden garanti eder.  
  
      Ancak, modelleri ayrı olduğundan, ortak kavramlara başvurmak zor olabilir. Her model, diğer katmanları ve mimariye bağımlı olduğu öğeleri kendine ait kopyasını olmalıdır. Katman diyagramı her katmanda Mimari katman diyagramı ile eşitlenmiş durumda tutulmalıdır. Bu öğeleri değiştirdiğinizde, bunu gerçekleştirmek için Araçlar geliştirmeniz ancak eşitleme elde etmek zordur.  
  
   ###### <a name="to-use-a-separate-package-for-each-layer"></a>Her katman için ayrı bir paket kullanmak için  
  
   1. Her katmanın çözümde mimari modelleme projesine ekleyin. Çözüm Gezgini'nde çözüm düğümüne sağ tıklayın, fareyle **Ekle**ve ardından **mevcut proje**. Tek bir modelleme projesi artık her bir çözümden erişilebilir: Mimari proje ve her katman için geliştirme projesi.  
  
   2. Paylaşılan UML modelinde, her katman için paket oluşturma: Çözüm Gezgini'nde modelleme projesini seçin. UML Model Gezgini'nde model kök düğümünü sağ tıklatın, **Ekle**ve ardından **paket**.  
  
       Her paket gereksinimleri ve ilgili katmanı tasarımını açıklayan UML diyagramları içerir.  
  
   3. Gerekirse, her katmanın iç yapısı için yerel katman diyagramları ekleyin.  
  
      Bu yöntem, her katmanın doğrudan bu bağımlı olduğu bir yaygın mimari ve katman başvurmak için tasarım öğeleri sağlar.  
  
      Eşzamanlı işler farklı paketleri bazı çakışmalara neden olabilir, ancak paketleri ayrı dosyalarda depolandığından Yönetimi oldukça kolaydır. Bağımlı bir paket başvurulan bir öğeyi silme işlemi önemli güçlük kaynaklanır. Daha fazla bilgi için [sürüm denetimi altındaki modelleri ve diyagramları yönetme](../modeling/manage-models-and-diagrams-under-version-control.md).  
  
## <a name="creating-architecture-templates"></a>Mimari şablonları oluşturma  
 Uygulamada, aynı anda tüm Visual Studio çözümleri oluşturmaz ancak bunları Proje ilerledikçe ekleyin. Muhtemelen de aynı çözüm yapısını gelecekteki projeleri kullanın.  Yeni çözümleri hızlı bir şekilde oluşturmanıza yardımcı olmak için bir çözüm veya proje şablonu oluşturabilirsiniz. Böylece bir kolayca dağıtmak ve diğer bilgisayarlara yüklemek için bir Visual Studio Tümleştirme Uzantısı (VSIX) içinde şablon yakalayabilirsiniz.  
  
 Örneğin, sık sık sunu, iş ve veri katmanlarına sahip bir çözüm kullanıyorsanız, bu yapıya sahip yeni çözümler oluşturan şablondan yapılandırabilirsiniz.  
  
#### <a name="to-create-a-solution-template"></a>Bir çözüm şablonu oluşturmak için  
  
1.  [Şablonu Dışarı Aktarma Sihirbazı'nı indirip](http://go.microsoft.com/fwlink/?LinkId=196686), bu yapmış olduğunuz değil.  
  
2.  İleride gerçekleştirilecek projeler için bir başlangıç noktası olarak kullanmak istediğiniz çözüm yapısını oluşturun.  
  
3.  Üzerinde **dosya** menüsünde tıklatın **VSIX olarak şablonu dışarı aktar**. **VSIX Sihirbazı olarak dışarı aktarma şablonu** açılır.  
  
4.  Sihirbazdaki yönergeleri, şablona dahil, bir ad ve şablon için bir açıklama girin ve bir çıkış konumunu belirtme istediğiniz projeleri seçin.  
  
> [!NOTE]
>  Bu konudaki malzeme soyutlanır ve Visual Studio mimari araç kullanımı Visual Studio ALM, en değerli uzmanları (MVP), Microsoft Services ve Visual Studio arasında işbirliği Rangers tarafından yazılan yönergesi, gelen açıklanır ürün ekibi ve yazarlar. [Tam Kılavuzu paketi indirmek için buraya tıklayın.](http://go.microsoft.com/fwlink/?LinkID=191984)  
  
## <a name="related-materials"></a>İlgili malzemeler  
 [Düzenleme ve yönetme Modellerinizi](http://channel9.msdn.com/posts/clinted/UML-with-VS-2010-Part-9-Organizing-and-Managing-Your-Models/) - video Clint Edmondson tarafından.  
  
 [Visual Studio mimari araç kullanımı yönergesi](../modeling/visual-studio-architecture-tooling-guidance.md) – daha fazla takım modellerinde yönetme hakkında rehberlik  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Sürüm denetimi altındaki modelleri ve diyagramları yönetme](../modeling/manage-models-and-diagrams-under-version-control.md)   
 [Geliştirme sürecinizde modelleri kullanma](../modeling/use-models-in-your-development-process.md)



