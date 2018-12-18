---
title: UML modelleme projeleri ve diyagramları oluşturma | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.teamarch.addnewdiagramdialog
- vs.teamarch.createnewmodelingprojectdialog
helpviewer_keywords:
- projects [Visual Studio ALM], modeling
- diagrams - modeling, modeling
- modeling diagrams
- projects, UML
- UML, deleting diagrams
- UML
- UML diagrams, adding
- UML, projects
- Visual Studio ALM, modeling projects
- modeling projects
- UML diagrams
- projects, modeling
ms.assetid: c178b04b-4fd2-4bed-97e3-d793dae8649c
caps.latest.revision: 50
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 5d841c9fde677eb4a8fb17e952a817364dab277e
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51738392"
---
# <a name="create-uml-modeling-projects-and-diagrams"></a>UML modelleme projeleri ve diyagramları oluşturma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

UML anlamanıza, tartışın ve tasarım yazılım sistemlerinin Yardım modeller. Visual Studio, UML diyagramları beş en sık kullanılan için şablonlar sağlar: etkinlik, sınıf, bileşen, dizisi ve kullanım örneği. Ayrıca, yardımcı katman diyagramları oluşturabilirsiniz sisteminizin yapısını tanımlar.  
  
 UML modelleme diyagramları ve katman diyagramları, yalnızca bir modelleme projesinin içinde bulunabilir. Her bir modelleme projesi, paylaşılan bir UML model ve birkaç UML diyagramları içerir. Her diyagram, modeli kısmi bir görünümüdür. UML modeli diyagramlarındaki tüm öğelerini içeren ve UML Model Gezgini kullanılarak görüntülenebilir. Modelleri ve diyagramları ilişkilerini hakkında daha fazla bilgi için bkz. [Düzenle UML modellerini ve diyagramları](../modeling/edit-uml-models-and-diagrams.md). Modelleme projeleri sürüm denetimi altında hakkında daha fazla bilgi için bkz: [sürüm denetimi altındaki modelleri ve diyagramları yönetme](../modeling/manage-models-and-diagrams-under-version-control.md) ve [modelleme çözümünüzün yapısını oluşturma](../modeling/structure-your-modeling-solution.md)  
  
> [!NOTE]
>  Başka tür bir program kodunu görselleştirmek için kullanılan .NET sınıf diyagramına diyagramın yoktur. Daha fazla bilgi için [tasarlama ve görüntüleme sınıfları ve türleri](http://go.microsoft.com/fwlink/?LinkId=142231).  
  
##  <a name="CreatingModelingDiagrams"></a> Bir modelleme projesinde bir diyagram oluşturma  
 Bu özellik, Visual Studio'nun hangi sürümlerinin desteklediğini görmek için bkz: [mimari ve Modelleme Araçları sürüm desteği](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
#### <a name="to-create-a-diagram-and-add-it-to-a-project"></a>Bir diyagram oluşturma ve bunu projeye ekleyin  
  
1. Üzerinde **mimarisi** menüsünde seçin **yeni UML veya katman diyagramı**.  
  
2. İçinde **Yeni Diyagram Ekle** iletişim kutusunda, istediğiniz modelleme diyagramında türüne tıklayın.  
  
    ![Yeni Diyagram Ekle iletişim kutusu](../modeling/media/uml-adddiagram.png "UML_AddDiagram")  
  
3. Yeni Diyagram için bir ad yazın.  
  
4. İçinde **modelleme projesine Ekle** kutusunda:  
  
   - Çözümünüzde zaten bir modelleme projesi seçin ve ardından **Tamam**.  
  
     \- veya -  
  
   1.  Seçin **yeni modelleme projesi oluşturma**ve ardından **Tamam**.  
  
   2.  İçinde **yeni modelleme projesi** iletişim kutusu, bir ad ve yeni proje için bir konum yazın ve ardından **Tamam**.  
  
        ![Yeni modelleme projesi oluştur iletişim kutusu](../modeling/media/uml-createmodel.png "UML_CreateModel")  
  
        Çözümünüzü açık değilse, yeni projesi çözüme eklenir. Açık çözümünüz varsa, yeni bir çözüm için bir ad yazabilirsiniz.  
  
   Bir modelleme projesi zaten varsa, aşağıdaki yordamı kullanabilirsiniz.  
  
#### <a name="to-add-a-diagram-to-an-existing-modeling-project"></a>Varolan bir modelleme projesine bir diyagramı eklemek için  
  
1.  İçinde **Çözüm Gezgini**, modelleme tıklayın proje düğümü.  
  
    > [!NOTE]
    >  Adlı bir model tanımı klasör modelleme projesini içerir **ModelDefinition**.  
  
2.  Üzerinde **proje** menüsünü tıklatın **Yeni Öğe Ekle**.  
  
3.  İçinde **Yeni Öğe Ekle -**  *\<proje adı >* iletişim kutusunun **şablonları**, modelleme tıklayın diyagram türü, örneğin, **UML Bileşen Diyagramı**.  
  
4.  Diyagram için bir ad yazın ve ardından **Ekle**.  
  
     Modelleme Diyagramında açılır ve modelleme projesinde görünür.  
  
    > [!CAUTION]
    >  Değil ekleme, kopyalama veya var olan diyagram dosyaları diğer modelleme projeleri veya iş çözümdeki diğer konumlara sürükleyin. Bu, öğelerin kopyalanan diyagramları ya da diyagram açtığınızda hata kaybolmasına neden olur. İçinde oluşturulmuş bir modelleme projesinden diyagram dosyasını açmanız gerekir. Bir UML diyagram, modelleme projesi tarafından sahip olunan modelinin bir görünüm olduğundan budur. Bir diyagram dosyasını kopyalamak için yeni bir diyagram oluşturun ve ardından öğeleri kaynak diyagramdan yeni diyagrama kopyalayın. Daha fazla bilgi için [sorun giderme modelleme projeleri ve diyagramları](#TroubleshootingModelingProjects).  
  
#### <a name="to-create-a-blank-modeling-project"></a>Boş bir modelleme projesi oluşturmak için  
  
1.  Üzerinde **dosya** menüsünde **yeni**ve ardından **proje**.  
  
2.  İçinde **yeni proje** iletişim kutusunun **yüklü şablonlar**, tıklayın **modelleme projeleri**.  
  
3.  Orta pencerede **modelleme projesine**.  
  
4.  Projeyi adlandırın ve bir konumda belirtin **adı** ve **konumu** kutuları.  
  
5.  İçinde **çözüm** kutusunda **eklemek için çözüm** zaten açık; bir çözüme yeni projeyi eklemek için veya **yeni çözüm oluşturma** herhangi bir açık çözümü kapatın ve eklemek için Yeni bir çözüme proje.  
  
##  <a name="RemovingModelingDiagrams"></a> Modelleme diyagramları bir projeden kaldırılıyor  
 Bir diyagram kalıcı olarak silebilir veya geçici olarak bir diyagram bir projeden çıkarın ve sonra geri yükleyin.  
  
#### <a name="to-permanently-delete-a-diagram-from-a-project"></a>Bir diyagram bir projeden kalıcı olarak silmek için  
  
-   İçinde **Çözüm Gezgini**diyagramda temsil eden ana dosyaya sağ tıklayın ve ardından **Sil**.  
  
     Diyagramı proje ve dosya sistemi kaldırılır. Diyagram üzerinde gösterilen öğeler kaldırılmaz **UML Model Gezgini**.  
  
    > [!NOTE]
    >  Her diyagram iki dosya için başka bir yan kuruluşu çalışanı vardır. Örneğin, bir bileşen diyagramı adıyla varsa `CD1`, adlı dosyayı silmeniz gerekir `CD1.componentdiagram`. Adlı dosyası `CD1.componentdiagram.layout` otomatik olarak silinir.  
  
#### <a name="to-temporarily-exclude-a-diagram-from-a-project"></a>Geçici olarak bir diyagram bir projeden Çıkart  
  
-   İçinde **Çözüm Gezgini**diyagram dosyasını sağ tıklayın ve ardından **projeden Çıkart**.  
  
     Diyagram projeden kaldırıldı. Dosya sisteminden kaldırılmaz.  
  
    > [!NOTE]
    >  Diyagram üzerinde gösterilen öğeler kaldırılmaz **UML Model Gezgini**.  
  
#### <a name="to-restore-a-temporarily-excluded-diagram-to-a-project"></a>Geçici olarak çıkarılmış bir diyagramı projeye geri yüklemek için  
  
1.  İçinde **Çözüm Gezgini**, modelleme tıklayın proje düğümü.  
  
    > [!NOTE]
    >  Adlı bir model tanımı klasör modelleme projesini içerir **ModelDefinition**.  
  
2.  Üzerinde **proje** menüsünde tıklatın **varolan öğeyi Ekle**.  
  
3.  İçinde **varolan öğeyi Ekle** iletişim kutusunda diyagram dosyasını bulun, dosyayı seçin ve ardından **Ekle**.  
  
     Modelleme Diyagramında açılır ve modelleme projesinde görünür.  
  
    > [!NOTE]
    >  Her diyagram dosyalarının bir çiftini dosya sisteminde yok. Uzantılı bir dosya seçmeyin `.layout`. Ayrıca, Visual Studio için birden fazla modelleme projesine mevcut UML diyagramları eklemeyi desteklemez. Her diyagram dosyası içinde oluşturulmuş bir modelleme projesi içinde açılması gerekir. Bir UML diyagram, modelleme projesi tarafından sahip olunan bir modelin görüntüler olmasıdır.  
  
##  <a name="NonModelDiagrams"></a> Modelleme projeleri gerektirmeyen diyagramları  
 Aşağıdaki tür diyagramlar bir modelleme projesi parçası değildir:  
  
-   Sınıf diyagramları kaynak kodunun bir görünüm oluşturulur. Bunlar için UML sınıf diyagramları ilgili değildir. Daha fazla bilgi için [tasarlama ve görüntüleme sınıfları ve türleri](../ide/designing-and-viewing-classes-and-types.md).  
  
-   Kod haritaları. Bkz: [Çözümlerinizdeki bağımlılıkları eşleme](../modeling/map-dependencies-across-your-solutions.md).  
  
-   UML diyagramları veya etki alanına özgü diller gibi katman diyagramları olmayan diyagramları.  
  
##  <a name="TroubleshootingModelingProjects"></a> Modelleme projeleri ve diyagramları sorunlarını giderme  
 Aşağıdaki tabloda modelleme projeleri veya diyagramları ve bunların nasıl çözüleceğine ile ortaya çıkabilecek sorunları açıklar:  
  
|**Sorunu**|**Neden olur**|**Çözümleme**|  
|---------------|----------------|--------------------|  
|Modelleme projesi açılamıyor veya çözümün içine yüklenir.<br /><br /> Aşağıdaki ileti görüntülenir:<br /><br /> "Çözümdeki bir veya daha fazla proje doğru şekilde yüklenmedi. Lütfen ayrıntılar için çıkış penceresine bakın."<br /><br /> Çıkış penceresi, şu iletiyi görüntüler:<br /><br /> "*ModelingProjectFilenameAndPath*.modelproj: hata: Tanınmayan bir GUID biçimi."|Bir modelleme projesi, aynı ada sahip ve aynı çözüm içinde projelerine başvurular var.<br /><br /> Örneğin, aynı ada sahip ve aynı çözümdeki projeleri için katman bağlanır.|Modelleme projesini açmak için bir metin düzenleyicisi kullanın dosya başvuruları kaldırın ve ardından modelleme projesinin yeniden açmayı deneyin.<br /><br /> Bu sorunu önlemek için aynı ada sahip projelerine başvurular eklemeyin. Projeleri benzersiz adlara sahip olduğundan emin olun.|  
|Eksik eklenen kopyalanmış veya diğer modelleme projeleri veya iş çözümdeki diğer konumlara sürüklediğiniz diyagramlarından öğeleridir.<br /><br /> - veya -<br /><br /> Bir diyagramı açmaya çalıştığınızda, aşağıdaki ileti görüntülenir:<br /><br /> -"Tanımlarını bu projede mevcut değildir çünkü bazı Şekil veya diyagram üzerinde bağlayıcıları eksik. Ya da tanımları modelden diyagram kapatıldı ya da diyagramda bu tanımları içermeyen başka bir projeye kopyalanan silindi."<br /><br /> - veya -<br /><br /> -"Bu belge başka bir projede açıldı."|Diyagramı dosyası eklenir, sürüklenen veya bir modelleme projesinden başka bir modelleme projesine veya çözüm içindeki başka bir konuma kopyalanır.|Bir diyagram dosyasını kopyalamak için yeni bir diyagram oluşturun ve ardından öğeleri kaynak diyagramdan yeni diyagrama kopyalayın.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [UML modellerini ve diyagramları düzenleme](../modeling/edit-uml-models-and-diagrams.md)   
 [Modelleme çözümünüzün yapısını oluşturma](../modeling/structure-your-modeling-solution.md)



