---
title: Bir etki alanına özgü dil tanımlama | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.dsltools.dsldesigner.domainrelationship
- vs.dsltools.dsldesigner.domainclass
- vs.dsltools.dsldesigner.domaintype
helpviewer_keywords:
- Domain-Specific Language, domain class
- Domain-Specific Language, external types
- Domain-Specific Language, relationships
- Domain-Specific Language, domain properties
ms.assetid: d1772463-0eb1-40a5-b7c0-9a008bc76760
caps.latest.revision: 45
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: b3c83ded60359bff2f84d35aec41eb387227022a
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49880747"
---
# <a name="how-to-define-a-domain-specific-language"></a>Nasıl yapılır: Etki Alanına Özgü bir Dili Tanımlama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bir etki alanına özgü dil (DSL) tanımlamak için oluşturduğunuz bir [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] bir şablondan bir çözüm. Anahtar çözüm DslDefinition.dsl içinde depolanan DSL tanımı diyagramı parçasıdır. DSL tanımını DSL şekilleri ve sınıfları tanımlar. Sonra değiştirmek ve bu öğeleri eklemek, DSL daha ayrıntılı bir şekilde özelleştirmek için program kodu ekleyebilirsiniz.  
  
 DSL için yeni başladıysanız, aracılığıyla çalışmanızı öneririz **DSL araçları Laboratuvar**, bu sitede bulabileceğiniz: [Visualizaton ve modelleme SDK'sı](http://go.microsoft.com/fwlink/?LinkID=186128)  
  
##  <a name="templates"></a> Bir şablon çözümü seçme  
 Bir DSL tanımlamak için aşağıdaki bileşenler yüklemiş olmanız gerekir:  
  
|||  
|-|-|  
|[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]|[http://go.microsoft.com/fwlink/?LinkId=185579](http://go.microsoft.com/fwlink/?LinkId=185579)|  
|[!INCLUDE[vssdk_current_short](../includes/vssdk-current-short-md.md)]|[http://go.microsoft.com/fwlink/?LinkId=185580](http://go.microsoft.com/fwlink/?LinkId=185580)|  
|Visual Studio Görselleştirme ve modelleme SDK'sı|[http://go.microsoft.com/fwlink/?LinkID=186128](http://go.microsoft.com/fwlink/?LinkID=186128)|  
  
 Yeni bir etki alanına özgü dil oluşturmak için yeni oluşturduğunuz [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] etki alanına özgü dil proje şablonunu kullanarak çözüm.  
  
#### <a name="to-create-a-dsl-solution"></a>Bir DSL çözüm oluşturmak için  
  
1. Bir Çözümle oluşturun **etki alanına özgü dil** altında bulunan şablon **diğer proje türleri/genişletilebilirlik** içinde **yeni proje** iletişim kutusu.  
  
    ![DSL iletişim oluşturma](../modeling/media/create-dsldialog.png "Create_DSLDialog")  
  
    Tıkladığınızda **Tamam**, **etki alanına özgü dil Sihirbazı** açılır ve şablon DSL çözümlerinin bir listesini görüntüler.  
  
2. Her şablon açıklamasını görmek için tıklayın. Oluşturmak istediğiniz en çok benzeyen bir çözüm seçin.  
  
    Her bir DSL şablonu temel çalışan bir DSL tanımlar. Bu DSL kendi gereksinimlerinize uyacak şekilde düzenleyeceksiniz.  
  
    Daha fazla bilgi için her örnek'e tıklayın.  
  
   -   Seçin **Görev akışı** Kulvarlar sahip bir DSL oluşturmak için. Kulvarlar diyagramın dikey veya yatay bölümlerdir.  
  
   -   Seçin **bileşeni modelleri** bağlantı noktası içeren bir DSL oluşturmak için. Daha büyük bir şekil kenarında küçük şekiller bağlantı noktalarıdır.  
  
   -   Seçin **sınıf diyagramları** bölme şekilleri sahip bir DSL tanımlamak için. Bölme şekilleri öğeleri listesini içerir.  
  
   -   Seçin **Minimal dil** diğer durumlarda, veya emin değilseniz.  
  
       > [!NOTE]
       >  Bir sınıf diyagramında veya bileşen diyagramı oluşturmak istiyorsanız, UML modelleri kullanarak göz önünde bulundurun. UML modelleme araçlarının tek bir model tümleşik diyagramları kümesi sağlar. Bunlar genişletilebilir ve ModelBus kullanarak DSL'nizi ile tümleştirilebilir. Daha fazla bilgi için [uygulamanız için model oluşturma](../modeling/create-models-for-your-app.md).  
  
   -   Seçin **Minimal WinForm Tasarımcısı** veya **en az bir WPF Tasarımcısı** bir Windows Formları ya da WPF yüzeyinde görüntülenen bir DSL oluşturmak için. Düzenleyici tanımlamak için kod yazmanız gerekir. Daha fazla bilgi için aşağıdaki konulara bakın:  
  
        [Windows Forms Tabanlı Etki Alanına Özgü Dil Oluşturma](../modeling/creating-a-windows-forms-based-domain-specific-language.md)  
  
        [WPF Tabanlı Etki Alanına Özgü Dil Oluşturma](../modeling/creating-a-wpf-based-domain-specific-language.md)  
  
3. Uygun Sihirbazı sayfasında DSL'nizi için bir dosya adı uzantısını girin. Bu örnekleri DSL'nizi içeren dosyalar kullanacağınız uzantısıdır.  
  
   -   Bilgisayarınızda veya DSL yüklemek istediğiniz herhangi bir bilgisayarda herhangi bir uygulama ile ilişkilendirilmemiş bir dosya adı uzantısı'nı seçin. Örneğin, **docx** ve **htm** kabul edilemez bir dosya adı uzantıları olacaktır.  
  
   -   Girdiğiniz uzantısı DSL kullanılıp kullanılmadığını, sihirbaz sizi uyarır. Farklı dosya adı uzantısını kullanmayı düşünün. Eski Deneysel tasarımcıları temizlemek için Visual Studio SDK deneysel örneği de sıfırlayabilirsiniz. Tıklayın **Başlat**, tıklayın **tüm programlar**, **Microsoft Visual Studio 2010 SDK**, **Araçları**, ardından **Microsoft sıfırlama Visual Studio 2010 deneysel örneği**.  
  
4. Diğer sayfalardaki ayarları değiştirebilir veya varsayılan değerleri değiştirmeyin.  
  
5. **Son**'a tıklayın.  
  
    Sihirbaz, iki veya üç projeleri içeren ve DSL tanımını kod oluşturur bir çözüm oluşturur.  
  
   Kullanıcı arabirimi artık aşağıdaki resme benzer.  
  
   ![DSL Tasarımcısı](../modeling/media/dsl-designer.png "dsl_designer")  
  
   Bu çözüm, bir etki alanına özgü dil tanımlar. Daha fazla bilgi için [etki alanına özgü dil araçları kullanıcı arabirimine genel bakış](../modeling/overview-of-the-domain-specific-language-tools-user-interface.md).  
  
### <a name="test-the-solution"></a>Çözüm test  
 Şablon, çalışan bir değiştirdiğinizde ya da olduğu gibi kullanın, DSL çözümüdür.  
  
 Çözümü test etmek için F5'e ya da CTRL + F5 tuşuna basın. Yeni bir örneğini [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Deneysel modda açılır.  
  
 Yeni bir örneğini [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], Çözüm Gezgini'nde örnek dosyasını açın. Bir araç kutusu ile bir diyagramı olarak açılır.  
  
 Bir çözüm çalıştırırsanız, gelen oluşturduğunuz **Minimal dil** şablonu, Deneysel [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] aşağıdaki örneğe benzer:  
  
 ![](../modeling/media/dsl-min.png "DSL_min")  
  
 Araçlar ile denemeler yapın. Öğeleri oluşturun ve bunları bağlayın.  
  
 Deneysel örneği kapatın [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
> [!NOTE]
>  DSL değiştirildiğinde, artık test dosyası şekilleri örneği görmek mümkün olacaktır. Ancak, yeni öğeleri oluşturmak mümkün olacaktır.  
  
### <a name="modifying-the-template-dsl"></a>DSL şablonu değiştirme  
 Yeniden adlandırmak ve bazı veya tüm etki alanı sınıflarını ve şekil sınıfları DSL tanımını şablonda tutun. Yeni, sınıf adları, boşluk veya noktalama işareti olmadan geçerli CLR adları olmalıdır.  
  
 Bu sınıfların tutmak kullanışlıdır:  
  
- Kök sınıf DSL tanımı diyagramı sol altında görünür **sınıflar ve ilişkiler**. DSL farklı bir adla yeniden adlandırın. Örneğin, adında bir DSL **MusicLibrary** adlı bir kök sınıfı olabilir **müzik**.  
  
- DSL tanım diyagramı, alt sağ tarafta görünür diyagramı sınıf **diyagram öğelerine** sütun. Bunu görmek için sağa kaydırmanız gerekebilir. Genellikle adlı _YourDsl_**diyagram**.  
  
- Kullandıysanız **Görev akışı** şablon ve istediğiniz ile Kulvarlar diyagramları oluşturmak, korumak ve ActorSwimlane şekli ve aktör etki alanı sınıfı yeniden adlandırın.  
  
  Silin veya diğer sınıflar gereksinimlerinize uyacak şekilde yeniden adlandırın.  
  
##  <a name="patterns"></a> Bir DSL tanımlama desenleri  
 Bir DSL ekleyerek veya aynı anda bir veya iki özellik ayarlama geliştirme öneririz. Özellik ekleme, DSL çalıştırın ve test ve ardından bir veya iki daha fazla özellik ekleyin. Tipik bir özellik, DSL'nin olabilir:  
  
- Bir etki alanı sınıfı öğelerini model şekli Diyagram ve kullanıcıların olanak sağlayan öğe araç o sınıfı öğelerini görüntülemek için gerekli öğe bağlandığı gömme ilişkisi oluşturun.  
  
- Bir etki alanı sınıfı ve şekli görüntüler dekoratörler etki alanı özellikleri.  
  
- Başvuru ilişkisi ve Diyagram ve kullanıcıların sağlayan bağlayıcı aracını görüntüler bağlayıcı bağlantılar oluşturun.  
  
- Doğrulama kısıtlaması veya bir menü komutu gibi program kodu gerektirir özelleştirme.  
  
  Aşağıdaki bölümlerde, DSL özellikleri en kullanışlı türlerini oluşturmak nasıl açıklanmaktadır. Bir DSL ile oluşturulabilir birçok desen vardır ancak bunlar en sık kullanılır.  
  
> [!NOTE]
>  Özelliği ekledikten sonra tıklamayı değil **tüm Şablonları Dönüştür** DSL'nizi çalıştıran ve Çözüm Gezgini araç çubuğunda, önce oluşturun.  
  
 Aşağıdaki şekilde, bu konudaki örnek olarak kullanılan DSL sınıflar ve ilişkiler parçası gösterilmiştir.  
  
 ![Başvuru ekleme ve ilişkileri](../modeling/media/music-classes.png "Music_Classes")  
  
 Sonraki şekilde bu DSL bir örnek modelidir:  
  
 ![Oluşturulan bir DSL örneği modelinin](../modeling/media/music-instance.png "Music_Instance")  
  
> [!NOTE]
>  "Modeli" kullanıcıların oluşturun ve genellikle bir diyagramı olarak görüntülenen DSL'nizi örneğine başvurur. DSL tanım diyagramı hem DSL'nizi kullanıldığında görüntülenen modeli diyagramları, bu konuda ele alınmıştır.  
  
##  <a name="classes"></a> Etki alanı sınıfları tanımlama  
 Etki alanı sınıfları DSL'nizi kavramlarını temsil eder. Örnekleri *model öğeleri*. Örneğin bir **MusicLibrary** DSL adlı etki alanı sınıfları olabilir **albüm** ve **şarkı**.  
  
 Bir etki alanı sınıfı oluşturmak için gelen sürükleyebilirsiniz **adlı etki alanı sınıfı** aracı diyagrama ve sınıfı yeniden adlandırın.  
  
 Daha fazla bilgi için [etki alanı sınıflarının özellikleri](../modeling/properties-of-domain-classes.md).  
  
### <a name="create-an-embedding-relationship-for-each-domain-class"></a>Gömme ilişkisi oluşturmak için her etki alanı sınıfı  
 En az bir gömme ilişkisi hedef kök sınıfı dışındaki her etki alanı sınıfı olmalıdır veya hedefi gömme ilişkisi olan bir sınıftan devralmalıdır.  
  
 Bir modelde her model öğe ilişkileri ekleme tek ağacındaki bir düğümdür. Kaynak ve hedef gömme ilişkisi, sık için üst ve alt adlandırılır.  
  
 Bir etki alanı sınıfı için bir üst öğe seçimi, diğer öğelerde bağımlı öğeleri ömürleri nasıl istediğinize bağlıdır. Bir ağaç düğümünün silinirse, onun bir alt ağacı genellikle de silinir. Bağımsız bir varlığı olan sınıfları öğesinin, bu nedenle doğrudan kök sınıfı altında katıştırılır.  
  
 Genellikle, başka bir öğenin içine bir öğe görüntülerseniz, sahibi ilişki belirtmek istersiniz. Bu durumda, en uygun üst sınıfı kapsayıcının sınıftır. Bir kapsayıcı içinde gördüğünüz öğesi aslında bağımsız bir öğeye başvuru bağlantısı olduğunda istisnadır. Bu durumda, kapsayıcıyı silmeden başvuru ancak kendi hedef siler.  
  
 Bu konuda açıklanan DSL tanımının desenlerinde kapsayıcı silindiğinde bir kapsayıcı içinde görüntülenen öğeler silinecek varsayacağız. Daha karmaşık düzenleri mümkündür ve kurallar tanımlayarak gerçekleştirilebilir.  
  
|Öğe nasıl görüntülenir|(Ekleme) üst sınıfı|Örnekte DSL çözüm şablonu|  
|------------------------------|--------------------------------|--------------------------------------|  
|Diyagram üzerinde şekil.<br /><br /> Kulvar.|DSL kök sınıfı.|Minimal dil.<br /><br /> Görev akışı: Aktör sınıfı.|  
|Kulvar şekil.|Etki alanı sınıfı Kulvarlar görüntülenen öğeler.|Görev akışı: Görev sınıfı.|  
|Öğe kapsayıcı silinirse burada öğesi silindiğinde şeklinde listesinde.<br /><br /> Şeklin edge üzerinde bağlantı noktası.|Kapsayıcı şekli için eşlenmiş etki alanı sınıfı.|Sınıf diyagramı: öznitelik sınıfı.<br /><br /> Bileşen Diyagramı: bağlantı noktası sınıfı.|  
|Öğe listesinde, kapsayıcı silinirse silinmez.|DSL kök sınıfı.<br /><br /> Referans bağlantıları listesini görüntüler.||  
|Doğrudan görüntülenir.|Bu bölümü forms sınıfı.||  
  
 Müzik Kitaplığı örnekte albümleri şarkıya başlıklarını listelendiği dikdörtgenler olarak görüntülenir. Bu nedenle albüm üst müzik kök sınıfı ve şarkı üst albüm.  
  
 Bir etki alanı sınıfı ve aynı anda ekleme oluşturmak için tıklayın **gömme ilişkisi** aracı, ardından üst sınıfın tıklayın ve ardından diyagramın boş bir kısmına tıklayın.  
  
 Gömme ilişkisi ve kendi rolleri adını ayarlamak genellikle gerekli değildir, çünkü sınıf adları otomatik olarak izler.  
  
 Daha fazla bilgi için [etki alanı ilişkilerinin özellikleri](../modeling/properties-of-domain-relationships.md) ve [etki alanı rollerinin özellikleri](../modeling/properties-of-domain-roles.md).  
  
> [!NOTE]
>  Gömme devralma ile aynı değil. Gömme ilişkisi çocuklarını özellikleri devralması değil.  
  
### <a name="add-domain-properties-to-each-domain-class"></a>Her etki alanı sınıfı için etki alanı özellikleri ekleyin  
 Etki alanı özellikleri değerlerini depolar. Örnekler: ad, Unvan, yayın tarihi.  
  
 Tıklayın **etki alanı özellikleri** sınıfında, ENTER tuşuna basın ve ardından bir özelliğin adını yazın. Bir etki alanı özelliğinin varsayılan türü dizedir. Türü değiştirmek istiyorsanız, etki alanı özelliğini seçin ve ayarlayın **türü** içinde **özellikleri** penceresi. İstediğiniz türü açılan listesinde değilse bkz [özellik türleri ekleme](#addTypes).  
  
 **Bir öğe adı özelliği ayarlayın.** Dil Gezgini'nde öğeleri tanımlamak için kullanılan bir alan özelliği seçin. Başlık etki alanı özelliği seçebilirsiniz, şarkı etki alanı sınıfı. İçinde **özellikleri** penceresinde **öğe adı** için `true`.  
  
### <a name="create-derived-domain-classes"></a>Türetilmiş etki alanı sınıfları oluşturma  
 Bir etki alanı sınıfı, özelliklerini ve ilişkileri devral çeşitleri olmasını istiyorsanız, ondan türetilen sınıflar oluşturun. Örneğin, albüm WMA ve MP3 türetilmiş sınıflar.  
  
 Türetilmiş sınıfını kullanarak oluşturmak **etki alanı sınıfı** aracı.  
  
 Tıklayın **devralma** aracı, türetilmiş sınıf tıklayın ve temel sınıfı'ye tıklayın.  
  
 Ayarlamayı düşünün **devralma değiştiricisi** için temel sınıf **soyut**. Temel sınıf örneklerini gerekebilir düşünüyorsanız, bunun yerine ayrı bir oluşturma türetilmiş düşünün bunlar için sınıf.  
  
 Türetilmiş sınıflar temel sınıflarının işaretçilerine rolleri ve özellikleri devralır.  
  
### <a name="tidy-the-dsl-definition-diagram"></a>DSL tanım diyagramı tutuyor  
 İlişkiler eklediğinizde, sınıfların bazıları birden fazla yerde görünür. Görünümler sayısını azaltın ve daha geniş bir diyagram yapmak için bir ilişki hedef sınıfını sağ tıklayın ve ardından **ağacı buraya getirin**. Bir ilişki girip __iade hedef sınıfını karşı efekt için sağ **ağacı Böl**. Bu menü komutları görmüyorsanız, yalnızca etki alanı sınıfı'nın seçili olduğundan emin olun.  
  
 Etki alanı sınıfları ve şekil sınıfları taşımak için CTRL + YUKARI OK ve CTRL + AŞAĞI OK kullanın.  
  
### <a name="test-the-domain-classes"></a>Test etki alanı sınıfları  
  
##### <a name="to-test-the-new-domain-classes"></a>Yeni etki alanı sınıfları test etmek için  
  
1.  **Tüm Şablonları Dönüştür'e tıklayın** DSL Tasarımcısı kodunu oluşturmak için Çözüm Gezgini araç çubuğundaki. Bu adım otomatik hale getirebilirsiniz. Daha fazla bilgi için [otomatikleştirmek tüm Şablonları Dönüştür nasıl](http://msdn.microsoft.com/en-us/b63cfe20-fe5e-47cc-9506-59b29bca768a).  
  
2.  **Oluşturup DSL çalıştırın.** Yeni bir örneğini çalıştırmak için F5'e ya da CTRL + F5 tuşuna basın [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Deneysel modda. Deneysel örneğinde [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], DSL'nin dosya adı uzantısına sahip bir dosya oluşturun veya açın.  
  
3.  **Explorer'ı açın.** AT diyagramı olarak adlandırılan tarafıdır genellikle adlı dil Gezgini penceresi *YourLanguage* Gezgini. Bu pencereyi görmüyorsanız, Çözüm Gezgini altında bir sekmede olabilir. Üzerinde bulamazsa, **görünümü** menüsünde **diğer Windows**ve ardından _YourLanguage_**Gezgini**.  
  
     Gezgininizde modelin ağaç görünümünü gösterir.  
  
4.  **Yeni öğe oluşturun.** Üst kök düğümüne sağ tıklayın ve ardından **yeni Ekle**_YourClass_.  
  
     Sınıfınıza yeni bir örneğini dilinizi Gezgini görüntülenir.  
  
5.  Yeni örnekleri oluşturduğunuzda her örnek farklı bir ad olduğunu doğrulayın. Yalnızca ayarladıysanız meydana gelir **öğe adı** bir alan özelliği bayrağı.  
  
6.  **Etki alanı özelliklerini inceleyin. Seçili sınıfının bir örneğiyle** Özellikler penceresini inceleyin. Bu, bu etki alanı sınıf üzerinde tanımlanan etki alanı özellikleri göstermesi gerekir.  
  
7.  **Dosyayı kaydedin, kapatın ve yeniden açın**. Düğümleri genişlettikten sonra oluşturduğunuz tüm örnekleri Gezgini'nde görünür olmalıdır.  
  
##  <a name="shapes"></a> Şekilleri diyagram üzerinde tanımlama  
 Diyagram üzerinde görünen öğelerin sınıfları dikdörtgenler, üç nokta veya simgeler tanımlayabilirsiniz.  
  
#### <a name="to-define-a-class-of-elements-that-appear-as-shapes-on-a-diagram"></a>Bir sınıf diyagramında şekilleri olarak görüntülenen öğelerin tanımlamak için  
  
1. **Tanımlayın ve test bölümünde anlatıldığı gibi bir etki alanı sınıfı**[alan sınıfları tanımlama](#classes) **.**  
  
   -   Üst sınıf kök sınıfı olmalıdır. Diğer bir deyişle, kök sınıfı ile yeni alan sınıfı arasındaki gömme ilişkisi olmalıdır.  
  
   -   Diyagram Kulvarlar varsa, üst etki alanı sınıfı, bir kulvara eşlenen olabilir. Bu yordama devam etmeden önce bkz [Kulvarlar sahip bir DSL tanımlama](#swimlanes).  
  
2. **Bir şekil Sınıf Ekle** model diyagram üzerindeki öğeleri göstermek için. DSL tanım diyagramı üzerine aşağıdaki araçlardan birini sürükleyin:  
  
   - **Geometri şekli** dikdörtgen veya elips sağlar.  
  
   - **Görüntü şekli** sağlayan bir resim görüntüler.  
  
   - **Bölme şekli** bir veya daha fazla öğe listesini içeren bir dikdörtgen.  
  
     DSL tanım diyagramı, şekilleri ve bağlayıcıları altında sağ tarafında görünür şeklini sınıfı yeniden adlandırın.  
  
3. **Bir resim şekli oluşturduysanız, bir görüntünün tanımlamak**.  
  
   1.  Her boyuttaki bir görüntü dosyası oluşturun. BMP, JPEG, GIF ve EMF biçimleri desteklenir.  
  
   2.  Çözüm Gezgini'nde dosyayı Dsl\Resources altında çözüme ekleyin.  
  
   3.  DSL tanım diyagramı için geri dönün ve yeni görüntüyü şeklin sınıfını seçin.  
  
   4.  Özellikler penceresinde tıklayın **görüntü** özelliği.  
  
   5.  İçinde **görüntü Seç** iletişim kutusunda, altındaki açılan menüye tıklayın **dosya adı**ve görüntüyü seçin.  
  
4. **Metin dekoratörleri etki alanı özelliklerini görüntülemek için şekle ekleyin.**  
  
    Görünen adı veya başlığının model öğesi için büyük olasılıkla en az bir metin dekoratör gerekir.  
  
    Shape sınıfının üst bilgisine sağ tıklayın, fareyle **Ekle**ve ardından **metin Dekoratör**. Dekoratörün ve Özellikler penceresinde kümesinin adını ayarlayın, **konumu**.  
  
5. **Her bir şeklin görüntülemelidir alan sınıfına bir diyagram öğesi eşlemesi ile bağlanma**.  
  
    Tıklayın **diyagram öğesi eşlemesi** aracı, sonra etki alanı sınıfı, ardından shape sınıfı tıklatın.  
  
6. **Metin dekoratörleri için harita özellikleri.**  
  
   1. Diyagram öğesi eşlemesi temsil eden şekle sınıfı ile alan sınıfı arasındaki gri satırı seçin.  
  
   2. İçinde **DSL ayrıntıları** penceresinde tıklayın **Dekoratör eşlemeleri** sekmesi. Görmüyorsanız, **DSL ayrıntıları** penceresi, **görünümü** menüsünde **diğer Windows** ve ardından **DSL ayrıntıları**. Tüm içeriği görmek için bu pencerenin en üstünü yükseltmek sıklıkla gereklidir.  
  
   3. Bir dekoratör adını seçin. Altında **görüntü özelliği**, etki alanı sınıfı, bir özelliğin adını seçin. Bu, her dekoratör için yineleyin.  
  
       Bir özellik ilgili bir öğe görüntülemek istiyorsanız, aşağı açılan ağaç Gezgin altında tıklayın **görüntü özelliğinin yolu**.  
  
   4. Her dekoratör adının bir onay işareti göründüğünden emin olun.  
  
      ![Şekil eşlemeleri ve DSL Ayrıntıları penceresi](../modeling/media/dsldetailswindow.png "DslDetailsWindow")  
  
7. **Alan sınıfının öğe oluşturmaya yönelik bir araç kutusu öğesi olun.**  
  
   1.  İçinde **DSL Gezgini**, genişletme **Düzenleyicisi** düğümü ve tüm alt düğümleri.  
  
   2.  Düğümü altında **araç kutusu sekmeleri** örneğin MusicLibrary DSL'nizi aynı ada sahip. Tıklayın **öğesi aracı Ekle**.  
  
       > [!NOTE]
       >  Sağ varsa **Araçları** düğümünü görmezsiniz **öğesi aracı ekleme**. Bunun yerine, yukarıdaki düğüme tıklayın.  
  
   3.  Yeni öğe aracı seçiliyken Özellikler penceresinde ayarlayın **sınıfı** son eklediğiniz etki alanı sınıfı için.  
  
   4.  Ayarlama **açıklamalı alt yazı** ve **araç ipucu**.  
  
   5.  Ayarlama **araç kutusu simgesi** araç kutusunda görüntülenecek simge. Rapordaki yeni simge veya başka bir aracı için zaten kullanılan bir simge ayarlayabilirsiniz.  
  
        Rapordaki yeni simge oluşturmak için de Dsl\Resources açın **Çözüm Gezgini**. Kopyalayın ve var olan öğe araç BMP dosyaları birini yapıştırın. Yapıştırılan kopyalama yeniden adlandırın ve düzenlemek için çift tıklayın.  
  
        Dönüş DSL tanım diyagramı için Aracı'nı seçin ve Özellikler penceresinde tıklayın **[...]**  içinde **araç kutusu simgesi**. İçinde **bit eşlem seçin** Seç iletişim kutusunda. Aşağı açılan menüden BMP dosyası.  
  
   Daha fazla bilgi için [geometrik şekiller özellikleri](../modeling/properties-of-geometry-shapes.md) ve [resim şekilleri özellikleri](../modeling/properties-of-image-shapes.md).  
  
#### <a name="to-test-shapes"></a>Şekiller test etmek için  
  
1. **Tüm Şablonları Dönüştür'e tıklayın** DSL Tasarımcısı kodunu oluşturmak için Çözüm Gezgini araç çubuğundaki.  
  
2. **Oluşturup DSL çalıştırın.** Yeni bir örneğini çalıştırmak için F5'e ya da CTRL + F5 tuşuna basın [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Deneysel modda. Deneysel örneğinde [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], DSL'nin dosya adı uzantısına sahip bir dosya oluşturun veya açın.  
  
3. **Öğe araçlarını araç göründüğünü doğrulayın.**  
  
4. **Şekiller oluşturma** aracından model diyagram üzerine sürükleyerek.  
  
5. **Her metin dekoratör göründüğünü doğrulayın** ve:  
  
   1.  Ayarlamış olduğunuz sürece, düzenleyebilirsiniz **kullanıcı Arabirimi salt okunur** domain özelliği bayrağı.  
  
   2.  Özelliği, Özellikler penceresinde veya dekoratörün düzenlediğinizde, diğer görünümdeki güncelleştirilir.  
  
   Bir şeklin ilk test ettikten sonra bazı özelliklerini ayarlamak ve bazı daha gelişmiş özellikler eklemek isteyebilirsiniz. Daha fazla bilgi için [bir etki alanına özgü dili özelleştirme ve genişletme](../modeling/customizing-and-extending-a-domain-specific-language.md).  
  
##  <a name="references"></a> Başvuru ilişkileri tanımlama  
 Tüm kaynak etki alanı sınıfı ve hiçbir hedef alan sınıfı arasındaki bir başvuru ilişkisi tanımlayabilirsiniz. Başvuru ilişkilerini satırlar şekiller arasında bağlayıcıları, bir diyagram üzerinde genellikle görüntülenir.  
  
 Örneğin, müzik albümlerini ve sanatçılar, diyagramdaki şekilleri olarak görüntüleniyorsa, sanatçıların albümleri, üzerinde çalıştıkları bağlantılar ArtistsAppearedOnAlbums adlı bir ilişki tanımlayabilirsiniz. Şekil örneğe bakın.  
  
 ![Oluşturulan bir DSL örneği modelinin](../modeling/media/music-instance.png "Music_Instance")  
  
 Başvuru ilişkilerini öğeleri aynı türde da bağlayabilirsiniz. Örneğin, Aile ağacı temsil eden bir DSL içinde üst ve alt öğelerini arasındaki başvuru ilişkisi kişi başka bir kişi ilişkidir.  
  
### <a name="define-a-reference-relationship"></a>Başvuru ilişkisi tanımlayın  
 Başvuru ilişkisi Aracı'nı tıklatın ardından ilişkinin kaynak etki alanı sınıfı tıklayın ve hedef etki alanı sınıfı'ye tıklayın. Hedef sınıf kaynak sınıfı aynı olabilir.  
  
 Her ilişki ilişki kutuyu her tarafındaki satır tarafından temsil edilen iki rol vardır. Her bir rol seçin ve Özellikler penceresinde özelliklerini ayarlayın.  
  
 **Rolleri yeniden adlandırma göz önünde bulundurun**. Örneğin, kişi ve kişi arasında bir ilişki üst ve alt öğeleri, yönetici ve Astları, Öğretmen ve Öğrenci varsayılan adlarını değiştirmek ve benzeri isteyebilirsiniz.  
  
 **Her rol çeşitliliği ayarlamak**, gerekirse. Her kişi bir Yöneticisi'nin en fazla diyagram 0.. 1 Yöneticisi etiketi altında görünen çoğulluk ayarlayın.  
  
 **Etki alanı özellikleri ilişkinin ekleyin.** Şekilde, sanatçının albüm ilişki rolü bir özelliğine sahiptir.  
  
 **İlişkiyi sağlayan yinelenenleri özelliğini ayarlayın** aynı sınıfın birden fazla bağlantı modeli öğeleri aynı çifti arasında varsa. Örneğin, bir Öğretmen birden fazla aynı Öğrenci tabi öğretmeyi izin verebilir.  
  
 ![Şekil eşlemeleri bağlayıcıların](../modeling/media/music-connector.png "Music_Connector")  
  
 Daha fazla bilgi için [etki alanı ilişkilerinin özellikleri](../modeling/properties-of-domain-relationships.md) ve [etki alanı rollerinin özellikleri](../modeling/properties-of-domain-roles.md).  
  
### <a name="define-a-connector-to-display-the-relationship"></a>İlişki görüntülemek için bir bağlayıcı tanımlayın  
 Bir bağlayıcı modeli diyagramı üzerindeki iki şekil arasına bir satır görüntüler.  
  
 Sürükleme **bağlayıcı** DSL tanım diyagramı üzerine aracı.  
  
 Bağlayıcı etiketleri görüntülemek istiyorsanız, metin dekoratörleri ekleyin. Konumlarına ayarlayın. Bir metin dekoratör taşıma izin vermek için ayarlanmış kendi **taşınabilir olan** özelliği.  
  
 Kullanım **diyagram öğesi eşlemesi** bağlayıcı için başvuru ilişkisi bağlamak için aracı.  
  
 Seçili diyagram öğesi eşlemesi ile açın **DSL ayrıntıları** penceresi ve açık **Dekoratör eşlemeleri** sekmesi.  
  
 Her **Dekoratör** ayarlayıp **görüntü özelliği** doğru etki alanı özelliğine.  
  
 Her öğe yanında bir onay işareti görünür olduğundan emin olun **dekoratörler** listesi.  
  
### <a name="define-a-connection-builder-tool"></a>Bir bağlantı Oluşturucu aracı tanımlayın  
 İçinde **DSL Gezgini** penceresini genişletin **Düzenleyicisi** düğümü ve tüm alt düğümlerini.  
  
 DSL'nizi aynı ada sahip düğümüne sağ tıklayın ve ardından **ekleme yeni bağlantı aracını**.  
  
 Yeni araç seçiliyken, Özellikler penceresinde:  
  
-   Ayarlama **açıklamalı alt yazı** ve **araç ipucu**.  
  
-   Tıklayın **bağlantı Oluşturucu** ve yeni ilişki için uygun Oluşturucusu'nu seçin.  
  
-   Ayarlama **araç kutusu simgesi** araç kutusunda görünmesini istediğiniz simge. Rapordaki yeni simge veya başka bir aracı için zaten kullanılan bir simge ayarlayabilirsiniz.  
  
     Rapordaki yeni simge oluşturmak için de Dsl\Resources açın **Çözüm Gezgini**. Kopyalayın ve var olan öğe araç BMP dosyaları birini yapıştırın. Yapıştırılan kopyalama yeniden adlandırın ve düzenlemek için çift tıklayın.  
  
     Dönüş DSL tanım diyagramı için Aracı'nı seçin ve Özellikler penceresinde tıklayın **[...]**  içinde **araç kutusu simgesi**. İçinde **bit eşlem seçin** Seç iletişim kutusunda. Aşağı açılan menüden BMP dosyası.  
  
##### <a name="to-test-a-reference-relationship-and-connector"></a>Başvuru ilişkisi ve Bağlayıcısı'nı Test etmek için  
  
1. **Tüm Şablonları Dönüştür'e tıklayın** DSL Tasarımcısı kodunu oluşturmak için Çözüm Gezgini araç çubuğundaki.  
  
2. **Oluşturup DSL çalıştırın.** Yeni bir örneğini çalıştırmak için F5'e ya da CTRL + F5 tuşuna basın [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Deneysel modda. Deneysel örneğinde [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], DSL'nin dosya adı uzantısına sahip bir dosya oluşturun veya açın.  
  
3. **Bağlantı aracını araç göründüğünü doğrulayın.**  
  
4. **Şekiller oluşturma** aracından model diyagram üzerine sürükleyerek.  
  
5. **Bağlantıları oluşturma** şekiller arasında. Bağlayıcı Aracı'nı tıklatın, bir şekle tıklayın ve ardından başka bir şekle tıklayın.  
  
6. **Uygun olmayan sınıflar arasında bağlantı oluşturamazsınız doğrulayın.** Örneğin, ilişkiniz Albümler ve sanatçıların arasındaysa için Sanatçılar Sanatçılar bağlayamazsınız doğrulayın.  
  
7. **Çeşitlilikler doğru olduğundan emin olun. Örneğin, bir kişinin birden fazla Manager'a bağlanamıyor doğrulayın.**  
  
8. **Her metin dekoratör göründüğünü doğrulayın** ve:  
  
   1.  Ayarlamış olduğunuz sürece, düzenleyebilirsiniz **kullanıcı Arabirimi salt okunur** domain özelliği bayrağı.  
  
   2.  Özelliği, Özellikler penceresinde veya dekoratörün düzenlediğinizde, diğer görünümdeki güncelleştirilir.  
  
   Bir bağlayıcı ilk test ettikten sonra bazı özelliklerini ayarlamak ve bazı daha gelişmiş özellikler eklemek isteyebilirsiniz. Daha fazla bilgi için [bir etki alanına özgü dili özelleştirme ve genişletme](../modeling/customizing-and-extending-a-domain-specific-language.md).  
  
##  <a name="compartments"></a> Liste içeren şekilleri tanımlama: bölme şekilleri  
 Bir veya daha fazla öğe listeleri içeren bir bölme şekli içeriyor. Örneğin, bir müzik kitaplığı DSL müzik Albümler temsil etmek için bölme şekilleri kullanabilirsiniz. Her albüm içinde şarkıya bir listesi bulunur.  
  
 ![Bölme şekli](../modeling/media/compartmentshape.png "CompartmentShape")  
  
 Bir DSL tanımındaki Bu etkiyi elde etmek, en basit yöntem kapsayıcı için bir etki alanı sınıfı ve her liste için bir etki alanı sınıfı tanımlayın. Kapsayıcı sınıfı bölme şekli için eşlenmiş.  
  
 ![Şekil Haritası](../modeling/media/music-mapcomp.png "Music_MapComp")  
  
 Daha fazla bilgi için [bölme şekilleri özellikleri](../modeling/properties-of-compartment-shapes.md).  
  
#### <a name="to-define-a-compartment-shape"></a>Bölme şekli tanımlamak için  
  
1.  **Kapsayıcı alan sınıfı oluşturun**. Tıklayın **gömme ilişkisi** aracı, modelin kök sınıfı tıklayın ve ardından DSL tanım diyagramı boş bir kısmına tıklayın. Bu örnek resimde albüm adlı etki alanı sınıfı oluşturur.  
  
     Alternatif olarak kök sınıfında eklemek yerine bir kulvara eşlenmiş bir etki alanı sınıfı, kapsayıcı ekleyebilir.  
  
     Sınıf için bir alan özelliği adı gibi ekleyin ve ayarlayın, **öğe adı** Özellikler penceresindeki bayrağı.  
  
2.  **Liste öğesi alan sınıfı oluşturun**. Tıklayın **gömme ilişkisi** aracı, kapsayıcı sınıfı (albümü) ve ardından diyagramın boş bir kısmına tıklayın. Bu örnek resimde şarkı adlı etki alanı sınıfı oluşturur.  
  
     Sınıfı için başlık gibi bir alan özelliği ekleyin ve ayarlayın, **öğe adı** bayrağı.  
  
     Diğer etki alanı özellikleri ekleyin.  
  
     Görüntülemek istediğiniz her bir listesi için başka bir liste öğesi alan sınıfına ekleyin.  
  
3.  **Birden fazla öğe karıştırılacak**, liste sınıfından devralınan sınıflar oluşturun. Liste sınıfı soyut belirleyerek kendi **devralma değiştiricisi**.  
  
     Örneğin, sanatçının yerine oluşturucusu tarafından sıralanacak klasik müzik istiyorsanız, iki alt sınıfları şarkı, ClassicalSong ve NonClassicalSong oluşturabilirsiniz.  
  
4.  **Bölme şekli oluşturma**. Sürükleyin **bölme şekli** DSL tanım diyagramı üzerine aracı.  
  
     Bir metin dekoratör ekleyin ve adını ayarlayın.  
  
     Bir bölme ekleyin ve adını ayarlayın.  
  
5.  Bölme şekli sınıfı sağ tıklatın, liste bölmeleri gizleme izin vermek için üzerine **Ekle**ve ardından **Genişlet/Daralt Dekoratör**. Özellikler penceresinde dekoratör konumunu ayarlayın.  
  
6.  Tıklayın **diyagram öğesi eşlemesi** aracı, kapsayıcı etki alanı sınıfı tıklayın ve bölme şekli'ye tıklayın.  
  
7.  Şekil ile alan sınıfı arasındaki diyagram öğesi eşlemesi bağlantıyı seçin. İçinde **DSL ayrıntıları** penceresi:  
  
    1.  Tıklayın **dekoratörler** sekmesi. Dekoratörün adına tıklayın ve ardından uygun öğesini altında seçin **görüntüleme özelliği**. Dekoratörün adının yanında bir onay işareti göründüğünden emin olun.  
  
    2.  Tıklayın **bölme eşlemeleri** sekmesi.  
  
         Bölme adına tıklayın.  
  
         Altında **görüntülenen eler koleksiyon yolu**, liste öğesi sınıfı (şarkı) gidin. Gezgin aracı kullanmak için aşağı açılan oka tıklayın.  
  
         Altında **görüntüleme özelliği**, listede görüntülenmesi gereken özelliği seçin. Örnekte, başlık budur.  
  
> [!NOTE]
>  Yol alanları dekoratörünün Dekoratör eşlemesindeki ve bölme harita alanları kullanarak, daha karmaşık ilişkileri bölme şekli ile alan sınıfları arasındaki yapabilirsiniz.  
  
#### <a name="to-define-a-tool-for-creating-the-shape"></a>Şekli oluşturmak için bir araç tanımlamak için  
  
1.  **Alan sınıfının öğe oluşturmaya yönelik bir araç kutusu öğesi olun.**  
  
2.  İçinde **DSL Gezgini**, genişletme **Düzenleyicisi** düğümü ve tüm alt düğümleri.  
  
3.  Düğümü altında **araç kutusu sekmeleri** örneğin MusicLibrary DSL'nizi aynı ada sahip. Tıklayın **öğesi aracı Ekle**.  
  
    > [!NOTE]
    >  Sağ varsa **Araçları** düğümünü görmezsiniz **öğesi aracı ekleme**. Bunun yerine, yukarıdaki düğüme tıklayın.  
  
4.  Yeni öğe aracı seçiliyken Özellikler penceresinde ayarlayın **sınıfı** son eklediğiniz etki alanı sınıfı için.  
  
5.  Ayarlama **açıklamalı alt yazı** ve **araç ipucu**.  
  
6.  Ayarlama **araç kutusu simgesi** araç kutusunda görüntülenecek simge. Rapordaki yeni simge veya başka bir aracı için zaten kullanılan bir simge ayarlayabilirsiniz.  
  
     Rapordaki yeni simge oluşturmak için de Dsl\Resources açın **Çözüm Gezgini**. Kopyalayın ve var olan öğe araç birini yapıştırın. BMP dosyaları. Yapıştırılan kopyalama yeniden adlandırın ve düzenlemek için çift tıklayın.  
  
     Dönüş DSL tanım diyagramı için Aracı'nı seçin ve Özellikler penceresinde tıklayın **[...]**  içinde **araç kutusu simgesi**. İçinde **bit eşlem seçin** iletişim kutusunda, açılır menüden BMP dosyanızı seçin.  
  
#### <a name="to-test-a-compartment-shape"></a>Bölme şekli test etmek için  
  
1. **Tüm Şablonları Dönüştür'e tıklayın** DSL Tasarımcısı kodunu oluşturmak için Çözüm Gezgini araç çubuğundaki.  
  
2. **Oluşturup DSL çalıştırın.** Yeni bir örneğini çalıştırmak için F5'e ya da CTRL + F5 tuşuna basın [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Deneysel modda. Deneysel örneğinde [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], DSL'nin dosya adı uzantısına sahip bir dosya oluşturun veya açın.  
  
3. **Aracı araç göründüğünü doğrulayın.**  
  
4. Araç modeli diyagram üzerine sürükleyin. Bir şekil oluşturulur.  
  
    Öğe adı görüntülenir ve otomatik olarak varsayılan bir değere ayarlanmış olduğunu doğrulayın.  
  
5. Yeni şeklin üst bilgisine sağ tıklayın ve Ekle'yi tıklatın *bilgisayarınızı liste öğesi.* Örnekte, ekleme şarkı bir komuttur.  
  
    Yeni bir ada sahip ve bir öğe listesinde göründüğünü doğrulayın.  
  
6. Liste öğeleri birine tıklayın ve Özellikler penceresini inceleyin. Liste öğeleri özelliklerini görmeniz gerekir.  
  
7. Dil Gezgini açın. İçindeki liste madde düğümleri ile kapsayıcı düğümlerini görebildiğinizi doğrulayın.  
  
   ![DSL oluşturulan explorer](../modeling/media/music-explorer.png "Music_Explorer")  
  
   Bölme şekli ilk test ettikten sonra bazı özelliklerini ayarlamak ve bazı daha gelişmiş özellikler eklemek isteyebilirsiniz. Daha fazla bilgi için [bir etki alanına özgü dili özelleştirme ve genişletme](../modeling/customizing-and-extending-a-domain-specific-language.md).  
  
### <a name="displaying-a-reference-link-in-a-compartment"></a>Bir referans bağlantı bir bölme içinde görüntüleme  
 Genellikle, bir bölme içinde görüntülenen bir bölme şekli tarafından temsil edilen öğesinin bir alt öğesidir. Ancak bazı durumlarda, ona bir başvuru ilişkisi ile bağlı bir öğe görüntülemek istiyorsanız.  
  
 Örneğin, biz albümü bağlı Sanatçılar listesini görüntüler AlbumShape için ikinci bir bölme ekleyebilirsiniz.  
  
 Bu durumda, bölme başvurulan öğenin yerine bağlantısına görüntülenmelidir. Silinecek bağlantı istediğiniz kullanıcı bölmede öğeyi seçer ve DELETE tuşuna bastığında olmasıdır başvurulan öğe.  
  
 Bununla birlikte, başvurulan öğenin adını bölmede görünür olabilir.  
  
 Bu bölümde daha önce açıklandığı gibi aşağıdaki yordamı zaten etki alanı sınıfı, başvuru ilişkisi, bölme şekli ve diyagram öğesi eşlemesi oluşturduğunuz varsayılır.  
  
##### <a name="to-display-a-reference-link-in-a-compartment"></a>Bir referans bağlantı bir bölme içinde görüntülemek için  
  
1.  **Bölme şekli bir bölme ekleme**. Bölme şekli sınıfı DSL tanım diyagramı üzerinde sağ tıklatın, **Ekle**ve ardından **bölme**.  
  
2.  Ayarlama **görüntülenen eler koleksiyon yolu** yerine, hedef öğesi bağlantısına gidin. Aşağı açılan menüsüne tıklayın ve hedef yerine başvuru ilişkisi seçmek için ağaç görünümünü kullanın. Örnekte, bir ilişkidir **ArtistAppearedOnAlbums**.  
  
3.  Ayarlama **görüntü özelliğinin yolu** bağlantıdan hedef öğesine gidilemiyor. Bu örnekte, olan **sanatçının**.  
  
4.  Ayarlama **görüntüleme özelliği** örneğin hedef öğenin uygun özelliğine **adı**.  
  
5.  **Tüm Şablonları dönüştürme**, derleme ve DSL çalıştırma ve test modeli açın.  
  
6.  Modeli Diyagramı şeklin uygun sınıflar oluşturmak, bunların adları Ayarla ve bunlar arasında bir bağlantı oluşturun. Bölme şekli bağlantılı öğe adları görüntülenmesi gerekir.  
  
7.  Bölme şekli bağlantısını ya da öğeyi seçin. Bağlantı hem de öğe ortadan kalkması gerekir.  
  
##  <a name="ports"></a> Bağlantı noktaları başka bir şekil sınırında tanımlama  
 Bir bağlantı noktası başka bir şekil sınırında bulunan şekildir.  
  
 Bağlantı noktaları, bir sabit bağlantı noktası kullanıcı bağlayıcılar çizmek başka bir şekil sağlamak için de kullanılabilir. Bu durumda, bağlantı noktası şekli saydam hale getirebilirsiniz.  
  
 Bağlantı noktası kullanan bir örnek görmek için seçin **bileşen diyagramı** DSL yeni bir çözüm oluşturduğunuzda, şablon. Aşağıdaki örnek, bağlantı noktaları tanımlarken göz önünde ana noktaları göstermektedir:  
  
- Bağlantı noktalarının, kapsayıcıyı temsil eden bir alan sınıfına yoktur `Component`.  
  
- Bağlantı noktalarını temsil eden bir etki alanı sınıfı yoktur. Bu örnekte, olan `ComponentPort`.  
  
- Bağlantı noktası etki alanı sınıfı için kapsayıcı etki alanı sınıfından gömme ilişkisi yoktur. Daha fazla bilgi için [alan sınıfları tanımlama](#classes).  
  
- Bağlantı noktası aynı kapsayıcı üzerinde karma için farklı türde isterseniz, bağlantı noktası etki alanı sınıfı alt sınıfları oluşturabilirsiniz. Örnekte, `InPort` ve `OutPort` devralınacak `ComponentPort`.  
  
- Kapsayıcı etki alanı sınıfı, herhangi bir türden şekil eşlenebilir. Örnek, `ComponentShape`. Daha fazla bilgi için [tanımlama şekiller](#shapes).  
  
- Bağlantı noktası etki alanı sınıfları için bağlantı noktası şekiller eşlenir. Bağlantı noktası şekil sınıflarını ayırmak için türetilmiş sınıfları harita veya bir bağlantı noktası şekli sınıfı için temel sınıf eşleyin.  
  
  Diğer açılardan, bağlantı noktası şekiller açıklandığı gibi davranır [tanımlama şekiller](#shapes).  
  
  Daha fazla bilgi için [bağlantı noktası özellikleri şekiller](../modeling/properties-of-port-shapes.md).  
  
##  <a name="swimlanes"></a> Kulvarlar sahip bir DSL tanımlama  
 Kulvarlar diyagramının bir yatay veya dikey bölüm var. Kulvar her model öğesine karşılık gelir. DSL tanımını bir etki alanı sınıfı Kulvar öğeleri gerektirir.  
  
 Bir DSL Kulvarlar ile oluşturmak için en iyi yolu, yeni bir DSL çözümü oluşturun ve Görev akışı çözümü şablonu seçme sağlamaktır. DSL tanımındaki kulvara eşlenmiş etki alanı sınıfı aktör sınıftır. Bu ve diğer sınıflar projenizi uyacak şekilde yeniden adlandırın.  
  
 Bir şeklin içindeki bir Kulvar olarak görüntülenecek bir sınıf eklemek için yeni sınıfınıza Kulvar sınıfı arasındaki bir gömme ilişkisi oluşturun. Kullanıcılar bir Kulvar öğeleri sürükleyerek olacaktır, ancak her öğe her zaman içinde belirli bir Kulvar olacaktır. Görev akışı çözüm şablonunda, FlowElement Kulvar sınıfı bir alt öğesidir.  
  
 Bir şekil Kulvarlar bağımsız olarak görüntülenecek bir sınıf eklemek için bir kök sınıfı ile yeni sınıfınıza arasındaki katıştırma ilişkisi oluşturun. Kullanıcılar bu şekilleri diyagram kulvarların ve Kulvarlar dışında sınırları dahil olmak üzere, herhangi bir yere yerleştirmek mümkün olacaktır. Görev akışı çözüm şablonunda, açıklama, kök sınıfı bir alt öğesidir.  
  
 Daha fazla bilgi için [özellikleri, Kulvarlar](../modeling/properties-of-swimlanes.md).  
  
##  <a name="addTypes"></a> Özellik türleri ekleme  
  
### <a name="domain-enumerations-and-literals"></a>Etki alanı sabit listeleri ve değişmez değerleri  
 Bir etki alanı numaralandırmasının birkaç değişmez değerler ile bir türdür.  
  
 Bir alan sabit listesine eklemek için kök modelde sağ **DSL Gezgini** ve ardından **ekleyebilir, yeni etki alanı numaralandırma**. Öğe görünür **DSL Gezgini** altında **etki alanı türleri** düğümü. Bu öğe diyagram üzerinde görünmez.  
  
 Etki alanı numaralandırma sabit listesi değişmez değerler eklemek için etki alanı numaralandırmada sağ **DSL Gezgini** ve ardından **ekleme yeni numaralandırma sabit değeri**.  
  
 Varsayılan olarak, bir numaralandırma türüne sahip bir özellik numaralandırma aynı anda yalnızca bir değere ayarlanabilir. Kullanıcılar ve programcıların değerleri - herhangi bir birleşimini ayarlayabilmek için istediğiniz bir "bit alanı" - verilirse **Isflags** numaralandırma özelliği.  
  
### <a name="external-types"></a>Dış türler  
 Türü bulamazsanız, bir etki alanı özelliğinin türü ayarladığınızda istediğiniz **türü** aşağı açılan listesinde, dış tür ekleyebilirsiniz. Örneğin, ekleyebilirsiniz **System.Drawing.Color** listesine türü.  
  
 Bir türü eklemek için DSL Gezgini'nde modelin kökünü sağ tıklayın ve ardından **yeni dış türü Ekle**. Özellikler penceresinde adı kümesine **renk** ve ad alanına **System.Drawing**. Bu tür artık DSL Gezgini altında görünür **etki alanı türleri**. Her bir alan özelliği türünü ayarlama seçebilirsiniz.  
  
##  <a name="custom"></a> DSL özelleştirme  
 Bu konuda açıklanan teknikleri kullanarak, hızlı bir şekilde bir DSL grafiksel gösterimi, okunabilir XML form ve kodu ve diğer yapıları üretmek için gerekli olan temel araçları oluşturabilirsiniz.  
  
 DSL tanımı genişletmek için iki yöntem vardır:  
  
1.  DSL DSL tanımının daha fazla özellik kullanarak hassas ayarlamalar yapabilirsiniz. Örneğin, birden fazla bağlayıcı oluşturabilirsiniz bir tek bağlayıcı aracını yapabilir ve hangi silerek bir öğe ayrıca ilgili öğeleri siler kuralları kontrol edebilirsiniz. DSL tanımındaki değerleri ayarlayarak bu teknikler genellikle sağlanır ve bazı program kodu birkaç satır gerektirir.  
  
     Daha fazla bilgi için [bir etki alanına özgü dili özelleştirme ve genişletme](../modeling/customizing-and-extending-a-domain-specific-language.md).  
  
2.  Daha gelişmiş efektler elde etmek için program kodunu kullanarak, modelleme araçları genişletir. Örneğin, model değiştirebilirsiniz menü komutları oluşturabilirsiniz ve iki veya daha fazla DSL'ler tümleştirme araçları oluşturabilirsiniz. VMSDK uzantılarınızı DSL tanımını oluşturan kod ile tümleştirmeyi kolaylaştırmak için tasarlanmıştır.  Daha fazla bilgi için [bir etki alanına özgü dili özelleştirmek için kod yazma](../modeling/writing-code-to-customise-a-domain-specific-language.md).  
  
### <a name="changing-the-dsl-definition"></a>DSL tanımını değiştirme  
 Bir DSL tanımındaki herhangi bir öğe oluşturduğunuzda, çok sayıda varsayılan değerleri otomatik olarak ayarlanır. Ayarlandıktan sonra bunları değiştirebilirsiniz. Bu güçlü özelleştirmeler için hala verirken bir DSL geliştirilmesini kolaylaştırır.  
  
 Örneğin, bir öğeye bir şekil eşlediğinizde, eşlemenin üst öğe yolu alan sınıfının gömme ilişkisi göre otomatik olarak ayarlanır. Ancak, gömme ilişkisi daha sonra değiştirirseniz, üst öğe yolu otomatik olarak değiştirilmez.  
  
 Bu nedenle, DSL tanımındaki bazı ilişkiler değiştirdiğinizde, bu tanımı kaydettiğinizde veya tüm şablonları dönüştürdüğünüzde bildirilmesini hataları için olağan dışı olduğunu bilmeniz gerekir. Bu hataların çoğunu düzeltmeye kolaydır. Hatanın konumunu görmek için hata raporuna çift tıklayın.  
  
 Ayrıca bkz: [nasıl yapılır: bir etki alanına özgü dil Namespace değiştirme](../modeling/how-to-change-the-namespace-of-a-domain-specific-language.md).  
  
##  <a name="trouble"></a> Sorun giderme  
 Aşağıdaki tabloda çözüm önerileri ile birlikte bir DSL tasarlarken, karşılaşılan en yaygın sorunlardan bazıları listelenmektedir. Daha fazla öneri kullanılabilir [görselleştirme araçları Extensibililty Forumu](http://go.microsoft.com/fwlink/?LinkId=186074).  
  
|Sorun|Öneri|  
|-------------|----------------|  
|DSL tanım dosyasında yapmış olduğunuz değişiklikleri hiçbir etkisi yoktur.|Tıklayın **tüm Şablonları Dönüştür** Çözüm Gezgini ve sonra yeniden çözüm üstündeki araç çubuğundan.|  
|Şekiller bir dekoratör özellik değeri yerine adını gösterir.|Dekoratör eşlemesi ayarlayın. DSL tanım diyagramı üzerinde gri çizgi etki alanı sınıfı ve şekli sınıfı arasında olduğu diyagram öğesi eşlemesi'a tıklayın.<br /><br /> Açık **DSL ayrıntıları** penceresi. Görünüm menüsünde, göremiyorsanız, işaret **diğer Windows**ve ardından **DSL ayrıntıları**.<br /><br /> Tıklayın **Dekoratör eşlemeleri** sekmesi. Dekoratörün adı seçin. Yanındaki onay kutusunun seçili olduğundan emin olun. Altında **görüntü özelliği**, bir etki alanı özellik adını seçin.<br /><br /> Daha fazla bilgi için [diyagramdaki şekilleri](#shapes).|  
|DSL Gezgini içinde ben bir koleksiyona eklenemiyor. Örneğin, araçları sağ tıkladığımda olduğunda "Aracı Ekle" Komut menüsünde.<br /><br /> My DSL Gezgini içinde bir listesine bir öğe ekleyemiyorum.|Üzerinde çalıştığınız düğüm öğeye sağ tıklayın. Bir listeye eklemek istediğiniz zaman Ekle komut listesi düğümünde, ancak sahibi olur.|  
|Oluşturduğum bir etki alanı sınıfı, ancak dil Gezgini'nde örnekleri oluşturulamaz.|Gömme ilişkisi hedef kök dışındaki her etki alanı sınıfı olmalıdır.|  
|My DSL Gezgini içinde öğeleri yalnızca tür adları ile gösterilir.|Sınıfın bir etki alanı özelliği DSL tanımındaki seçin ve Özellikler penceresinde ayarlayın **öğe adı** true.|  
|My DSL her zaman XML Düzenleyicisi'nde açılır.|Dosya okunurken bir hata nedeniyle oluşabilir. Ancak, bile, bu hatayı düzelttikten sonra DSL Tasarımcısı olarak Düzenleyici açıkça sıfırlamanız gerekir.<br /><br /> Proje öğesi sağ tıklayın, **birlikte Aç** seçip _YourLanguage_**Tasarımcısı (varsayılan)**.|  
|Derleme adları değiştirdim sonra my DSL araç görünmez.|İnceleyin ve güncelleştirme **DslPackage\GeneratedCode\Package.tt** daha fazla bilgi için bkz [nasıl yapılır: bir etki alanına özgü dil Namespace değiştirme](../modeling/how-to-change-the-namespace-of-a-domain-specific-language.md).|  
|My DSL araç görünmez, ancak derleme adı değişmemiştir.<br /><br /> Veya, bir uzantı yüklemek için hata raporlama bir ileti kutusu görünür.|Deneysel örneğini sıfırlama ve çözümünüzü yeniden oluşturun.<br /><br /> 1.  Windows Başlat menüsü, altında **tüm programlar**, genişletin [!INCLUDE[vssdk_current_long](../includes/vssdk-current-long-md.md)], ardından **Araçları**ve ardından **Microsoft Visual Studio Deneysel örneğini sıfırlama**.<br />2.  Üzerinde [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] **derleme** menüsünde tıklatın **çözümü yeniden derle**.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Etki alanına özgü dillerle çalışmaya başlama](../modeling/getting-started-with-domain-specific-languages.md)   
 [Bir Windows Forms tabanlı etki alanına özgü dil oluşturma](../modeling/creating-a-windows-forms-based-domain-specific-language.md)   
 [WPF Tabanlı Etki Alanına Özgü Dil Oluşturma](../modeling/creating-a-wpf-based-domain-specific-language.md)



