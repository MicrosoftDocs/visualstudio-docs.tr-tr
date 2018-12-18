---
title: 'UML etkinlik diyagramları: Yönergeler | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- UML diagrams, activity
- diagrams - modeling, activity
- diagrams - modeling, UML activity
- activity diagrams
- UML, activity diagrams
ms.assetid: fe5dbe96-79ab-483a-b9bc-44d0d1d3efc2
caps.latest.revision: 50
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: a13db375305e96c4657e007f9cd8bfffbf34f990
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51722689"
---
# <a name="uml-activity-diagrams-guidelines"></a>UML Etkinlik Diyagramları: Yönergeler
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio'da bir iş sürecini veya bir yazılım algoritması bir dizi eylem iş akışı olarak tanımlamak için bir etkinlik diyagramı çizebilirsiniz. Kişiler, yazılım bileşenleri ve cihazları bu eylemleri gerçekleştirebilirsiniz. Video gösterimi için bkz: [etkinlik diyagramları kullanarak iş akışlarını yakalama](http://channel9.msdn.com/posts/clinted/UML-with-VS-2010-Part-4-Capture-Business-Workflows/).  
  
 Bu özellik, Visual Studio'nun hangi sürümlerinin desteklediğini görmek için bkz: [mimari ve Modelleme Araçları sürüm desteği](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
 UML etkinlik diyagramı oluşturmak için **mimarisi** menüsünü tıklatın **yeni UML veya katman diyagramı**.  
  
 Birçok amaç için bir etkinlik diyagramı kullanabilirsiniz:  
  
- Bir iş sürecini veya kullanıcılar ve sistem arasındaki iş akışını tanımlamak için. Daha fazla bilgi için [kullanıcı gereksinimlerini modelleme](../modeling/model-user-requirements.md).  
  
- Adımları açıklamak için bir kullanım örneği, gerçekleştirdi. Daha fazla bilgi için [UML Kullanım durumu diyagramları: yönergeler](../modeling/uml-use-case-diagrams-guidelines.md).  
  
- Yöntemi, işlev veya yazılım işlemi tanımlamak için. Daha fazla bilgi için [uygulama Mimarinizi modelleme](../modeling/model-your-app-s-architecture.md).  
  
  Etkinlik diyagramı çizme işlem geliştirmenize yardımcı olabilir. Mevcut bir işlemi diyagramı çok karmaşık olduğu durumlarda, işlemin nasıl Basitleştirilmiş düşünebilirsiniz.  
  
  Etkinlik diyagramlarındaki öğeler hakkında başvuru bilgileri için bkz. [UML etkinlik diyagramları: başvuru](../modeling/uml-activity-diagrams-reference.md).  
  
##  <a name="Relationships"></a> Diğer diyagramlarla ilişki  
 Bir iş sürecini veya kullanıcıların sistemi kullanma bir şekilde açıklamak için bir etkinlik diyagramı çizme, aynı bilgilerle farklı bir görünüm göstermek için bir kullanım durumu diyagramı çizebilirsiniz. Kullanım durumu diyagramı, kullanım örnekleri gibi eylemler çizin. Kullanım örneklerine karşılık gelen eylem olarak aynı adı verin. Kullanım örneği görünümünün avantajları şunlardır:  
  
- Ne kadar büyük bir diyagram Göster Eylemler/kullanım örnekleri içeren ilişkisini kullanarak daha küçük depolara oluşur.  
  
- Kullanıcılara veya dış sistemler yürütülmesinde yer alan her eylem/kullanım örneğini açıkça bağlanın.  
  
- Sisteminizi ya da her ana bileşeni tarafından desteklenen eylemleri/kullanım durumları etrafında sınırlar çizer.  
  
  Ayrıca, bir yazılım işleminin ayrıntılı tasarım açıklamak için bir etkinlik diyagramı çizebilirsiniz.  
  
  Bir etkinlik diyagramı, eylemler arasında geçen veri akışını gösterebilirsiniz. Bölümüne [açıklayan veri akışı](#DataFlows). Ancak, bir etkinlik diyagramı, veri yapısını açıklamaz. Bu amaç için UML sınıf diyagramı çizebilirsiniz. Bilgi için [UML sınıf diyagramları: yönergeler](../modeling/uml-class-diagrams-guidelines.md).  
  
##  <a name="BasicSteps"></a> Etkinlik diyagramları çizmek için temel adımlar  
 Herhangi bir modelleme diyagramının oluşturmaya yönelik ayrıntılı adımlar açıklanmıştır [Düzenle UML modellerini ve diyagramları](../modeling/edit-uml-models-and-diagrams.md).  
  
#### <a name="to-draw-an-activity-diagram"></a>Etkinlik diyagramı çizmek için  
  
1.  Üzerinde **mimarisi** menüsünü tıklatın **yeni UML veya katman diyagramı**.  
  
2.  Altında **şablonları**, tıklayın **UML etkinlik diyagramı**.  
  
3.  Diyagrama ad verin.  
  
4.  İçinde **modelleme projesine Ekle**, çözümünüzde varolan modelleme projesini seçin veya **yeni modelleme projesi oluşturma**.  
  
#### <a name="to-draw-elements-on-an-activity-diagram"></a>Bir etkinlik diyagramında öğelerini çizmek için  
  
1.  Öğeleri araç diyagram üzerine sürükleyin.  
  
     Diyagram üzerinde ana etkinlikleri yerleştirme, bağlamayı ve sonra Son dokunuşları gibi ilk ve son düğümleri ekleyerek başlayın.  
  
    > [!NOTE]
    >  UML Model Gezgini'nden varolan öğeleri diyagram üzerine tasarıcıya sürükleyemezsiniz.  
  
2.  Öğeleri bağlamak için şu adımları izleyin:  
  
    1.  İçinde **etkinlik diyagramı** araç tıklayın **bağlayıcı**.  
  
    2.  Diyagram üzerinde kaynak öğeye tıklayın.  
  
    3.  Hedef öğeye tıklayın.  
  
        > [!NOTE]
        >  Birden çok kez bir aracı kullanmak için araç kutusunda araca çift tıklayın.  
  
#### <a name="to-move-an-activity-to-another-package"></a>Bir etkinlik başka bir pakete taşımak için  
  
-   İçinde **UML Model Gezgini**, pakete etkinliğini sürükleyin.  
  
     \- veya -  
  
-   İçinde **UML Model Gezgini**, etkinliğe sağ tıklayın ve tıklayın **Kes**. Ardından, pakete sağ tıklayın ve tıklayın **Yapıştır**.  
  
    > [!NOTE]
    >  Etkinlik, UML Model Gezgini'nde görünecektir yalnızca ilk öğeyi diyagrama eklerken.  
  
##  <a name="SimpleControlFlow"></a> Denetim akışı açıklayan  
 Etkinlik diyagramı bir dizi eylem bir iş işlem veya yazılım algoritması açıklar. Bağlayıcı oklar nasıl denetim sırayla bir eylemden geçtiğini gösterir. Normalde, yalnızca önceki eylemi tamamlandıktan sonra eylemin başlayabilirsiniz.  
  
 Aşağıdaki şekil, bir dizi eylem Eylemler, bağlayıcılar, dallar ve döngüler ile nasıl Göster, bir örnektir. Her öğe, aşağıdaki bölümlerde daha ayrıntılı açıklanmıştır.  
  
 ![Basit etkinlik diyagramı](../modeling/media/uml-actguidectrl.png "UML_ActGuideCtrl")  
  
 Etkinlik diyagramları kullanın **eylemleri** ve **Bağlayıcılar** sırayla bir eylemden akışı denetimi ile sistem veya uygulama bir dizi eylem olarak tanımlamak için.  
  
- Oluşturma bir **eylem** (1) için bir kullanıcı, sistem veya işbirliği içinde her ikisi tarafından gerçekleştirilen her ana görev.  
  
  > [!NOTE]
  >  İşlem veya yalnızca birkaç eylemleri algoritmasıyla açıklamaya çalışın. Kullanabileceğiniz **çağrı davranış eylemleri** açıklandığı gibi daha ayrıntılı olarak ayrı bir diyagramda her bir eylemin tanımlamak için [çağrı davranış eylemleri alt etkinliklerle açıklayan](#Subactivities).  
  
- Genellikle neyi hedeflediğini her eylemin başlık açıkça belirttiğinden emin olun.  
  
- Eylemler dizisi ile bağlantısını **Bağlayıcılar** (2).  
  
- Denetim akışı bir sonraki eylem başlamadan önce her eylem sona erer. Çakışma kullanmak eylemleri tanımlamak istiyorsanız bir **Çatal Düğüm** bölümünde açıklandığı gibi [eşzamanlı akışlar](#Concurrent).  
  
  Eylemlerin sırasını diyagrama açıklar ancak nasıl eylemleri yürütülür veya denetim sonraki bir eylemden nasıl geçirilir açıklamaz. Bir iş sürecini temsil etmek için diyagram kullanıyorsanız, bir kişinin e-posta gönderdiğinde denetimi, örneğin, geçirilebilir. Yazılım tasarımı göstermek için diyagramda kullanırsanız, Denetim yürütme normal akışa göre sonraki bir durumdan diğerine geçebilir.  
  
### <a name="describing-decisions-and-loops"></a>Açıklayan kararlarını ve döngüler  
  
-   Kullanım bir **karar düğümünde** burada karar sonucunu belirleyen bir sonraki adım bir noktasını belirtmek için (3). İstediğiniz sayıda giden yollar çizebilirsiniz.  
  
-   Bir uygulamanın parçası tanımlamak için etkinlik diyagramı kullanırsanız, böylece her bir yol kullanılsalar Temizle (4) koruma tanımlamanız gerekir. Bağlayıcı sağ tıklayın, **özellikleri**hem de **özellikleri** penceresinde, tür için bir değer **Guard** alan.  
  
-   Her zaman koruma tanımlamak gerekli değildir. Örneğin, bir iş sürecini veya etkileşim protokolünü açıklamak için etkinlik diyagramı kullanırsanız, bir dal çeşitli seçenekleri açık kullanıcıya veya etkileşim kuran bileşenler tanımlar.  
  
-   Kullanım bir **birleştirme düğümünü** , dallandırılmış iki veya daha fazla alternatif akışlar bir araya getirmek için (5) bir **karar düğümünde**.  
  
    > [!NOTE]
    >  Kullanmanız gereken bir **birleştirme düğümünü** akışlar bir eylemde bir araya getirmek yerine alternatif akışlar, bir araya getirmek için. Örnekte, bu kararı düğümünden bağlanmak doğru olmaz doğrudan tekrar **seçin menü öğesi**. Bu durum, tüm gelen bağlayıcılar denetimin iş parçacıklarını gelmiş kadar bir eylem başlatılamıyor çünkü. Bu nedenle, eşzamanlı akışlar yalnızca bir eylemde birlikte getirmelisiniz. Daha fazla bilgi için [eşzamanlı akışlar](#Concurrent).  
  
-   Dallar, örnekte gösterildiği gibi döngüleri açıklamak için kullanın.  
  
    > [!NOTE]
    >  Program kodunda yaptığınız gibi döngüler iyi yapılandırılmış bir biçimde iç içe deneyin. Mevcut bir iş sürecini tanımlar, bu geliştirecek bazı fırsatları açığa çıkarabilir.  
  
### <a name="starting-the-activity"></a>Etkinlik Başlangıç  
 İçinde bir etkinlik giriş noktaları göstermenin iki yolu vardır:  
  
-   **İlk düğüm**  
  
     Bir oluşturma **ilk düğüm** etkinliğin ilk eylemi belirtmek için (6).  
  
     Bu yöntem, bir alt etkinlik tanımlarken veya açıkça ne başlatan etkinlik durumu gerekmez en yararlı olur. Bir müşteri gereksinimi alır, örneğin, yemek siparişi etkinlik başlar.  
  
-   **Olay kabul düğümü**  
  
     Oluşturma **kabul olay düğümleri**bölümünde açıklandığı gibi [eşzamanlı akışlar](#Concurrent), bir kullanıcı girişi gibi belirli bir olaya yanıt veren bir iş parçacığı başlangıcını gösterir. Gelen akış düğümüne sağlamaz. Gelen bir akışı atlama olay gerçekleşen her zaman bir iş parçacığı başlatılır gösterir.  
  
     Belirli dış bir olaya yanıt açıklamak, bu yöntem kullanışlıdır.  
  
### <a name="ending-the-activity"></a>Etkinlik bitiş  
 Kullanım bir **etkinlik son düğümü** Etkinliğin sonunu belirtmek için (7).  
  
-   Bir iş parçacığı denetimi ulaştığında bir **etkinlik son düğümü**, etkinliğe ilişkin eşzamanlı Eylemler ve alt etkinlikleri sonlanır.  
  
-   Birden fazla etkinlik son düğümü, ek bağlayıcıları gösterip azaltmak için kullanabilirsiniz.  
  
### <a name="interrupting-the-activity"></a>Etkinliği kesme  
 Kullanıcı işlemi iptal etmeye karar verirse nasıl sıradan bir etkinlik akışı, örneğin, kesilebileceğini açıklamak için bir kabul olay, olay için dinleyeceği düğüm oluşturabilirsiniz. Daha fazla bilgi için konudaki [eşzamanlı akışlar](#Concurrent). Denetim akışı, bir etkinlik son düğümü (7) oluşturun.  
  
### <a name="swimlanes"></a>Kulvarlar  
 Bazen, bir etkinlik farklı nesneleri veya eylemler gerçekleştiren iş rolleri karşılık gelen alanlarına eylemleri düzenlemek yararlıdır. Bu alanlar sütunlarında standart olarak düzenlenir ve adlandırılır *Kulvarlar*.  
  
- Çizgiler veya dikdörtgenler gelen kullanın **Basit şekiller** Kulvarlar veya diğer alanları çizmek için araç bölümü.  
  
- Her Kulvar etiketlemek için bir açıklama oluşturun ve ayarlayın, **saydam** özelliğini **True**.  
  
  Basit şekiller UML modelinin bir parçası oluşturmuyor ve UML Model Gezgini'nde görünmez.  
  
##  <a name="DataFlows"></a> Veri akışı açıklayan  
 Bir etkinlik iki yöntemden biriyle içine ve dışına geçen verileri tanımlayabilirsiniz:  
  
-   Kullanım bir **nesne düğümü**. Etkinlikler arasında akan bilgileri açıklamak en basit yöntem budur. Bir programda bir değişken bir nesne düğümü gibidir. Başka bir eylemden geçen bir veya daha fazla değerlerini depolayan bir şeyi temsil eder.  
  
-   Kullanım bir **çıkış PIN** ve **PIN girişi**. Bu yöntem, ayrı ayrı bir eylem ve başka bir girişleri çıkışları açıklamak sağlar. PIN, programdaki parametreler gibidir. PIN burada nesneleri girin ve bir eylem bırakın bağlantı noktalarını gösterir.  
  
    > [!NOTE]
    >  Bu bölümde kullanılan öğelere genel bakış için bkz. veri akışları konunun bölümüne bakın [UML etkinlik diyagramları: başvuru](../modeling/uml-activity-diagrams-reference.md).  
  
### <a name="describing-data-flow-with-object-nodes"></a>Nesne düğümleri ile veri akışını açıklama  
 Çoğu denetim akışları veri taşır. Örneğin, "Müşteri ayrıntıları sağlar" eylem çıkış akışından teslimat adresini başvuru yapar.  
  
 Diyagramınızda verileri açıklamak isterseniz, bir nesne düğümü ile bir bağlayıcı ve aşağıdaki resimde gösterildiği gibi iki bağlayıcı değiştirebilirsiniz.  
  
 ![Nesne düğümleri, eylemler arasında geçirilen verileri gösterebilir](../modeling/media/uml-actguidedata.png "UML_ActGuideData")  
  
 Yuvarlatılmış Dikdörtgen mal gibi eylemler, işleme oluştuğu gösterdiğine dikkat edin. Köşeli dikdörtgen sevkiyat adresi gibi bir akış nesnelerin bir eylemden diğerine temsil eder.  
  
 Nesne düğümü düğüm rolünü veya anabelleği eylemler arasında akan nesnelerin olarak yansıtan bir ad verin.  
  
 Ayarlayabileceğiniz **türü** Özellikler penceresindeki nesne düğümünün. Tür, tamsayı veya sınıf, arabirim veya tanımladığınız bir sınıf diyagramında sabit listesi'gibi basit bir tür olabilir. Örneğin, bir sınıf sevkiyat adresi sokak adresi, şehir ve müşteri adlı başka bir sınıf için bir ilişkilendirme birlikte öznitelikleriyle oluşturabilirsiniz. Daha fazla bilgi için [UML sınıf diyagramları: yönergeler](../modeling/uml-class-diagrams-guidelines.md).  
  
> [!NOTE]
>  Altında henüz tanımlanmadı bir türün adını yazarsanız, öğeyi eklenecek **belirtilmemiş türler** UML Model Gezgini'nde. Bir sınıf diyagramında bir tür adı daha sonra tanımlarsanız, böylece yeni türe başvurur nesne düğümü türü sıfırlamalısınız.  
  
#### <a name="buffering-data-in-object-nodes"></a>Nesne düğümleri veri arabelleğe alma  
 Bir nesne düğümü birden çok nesne için bir arabellek olarak çalışabilir. Aşağıdaki çizimde, bir kullanıcının gidebileceği denetim akışı gösterilmektedir. [daha fazla seçin] (1) çoğu zaman, seçili menü öğeleri nesne düğümü (2) kullanıcının seçimlerini toplarken döngü. Son olarak, kullanıcının kendi seçimi tamamlandığında Denetim seçenekleri seçili menü öğeleri arabellekteki tam listesini kabul eden siparişi onayla eylemi (3) geçirir.  
  
 ![Nesne düğümleri verilerin arabelleğe](../modeling/media/uml-actguidebuffer.png "UML_ActGuideBuffer")  
  
 Nesne düğümü özelliklerini ayarlayarak bir arabellek öğeleri nasıl depolandığını belirtebilirsiniz:  
  
-   Ayarlama **sıralama** özelliği:  
  
    -   **Sırasız** rastgele veya belirtilmeyen bir sırayı belirtmek için. (Varsayılan)  
  
    -   **Sıralı** belirli bir anahtarın göre bir sıra belirtmek için.  
  
    -   **FIFO** ilk giren bir sırasını belirlemek için ilk çıkar.  
  
    -   **LIFO** bir sipariş son giren ilk çıkar belirtmek için.  
  
-   Ayarlama **üst sınır** özelliği arabellekteki bulunabilir nesneleri maksimum sayısını belirtin. Varsayılan *. Bu sınır olmadığını anlamına gelir.  
  
### <a name="describing-data-flow-with-input-and-output-pins"></a>Giriş ve çıkış sabitleyicileri açıklayan veri akışı  
 Kullanım bir **çıkış PIN** ve **giriş PIN** ayrı ayrı bir eylem ve başka bir girişleri çıkışları açıklamak için.  
  
 ![Giriş ve çıkış sabitleyicileri olan eylem parametrelerini](../modeling/media/uml-actguidepins.png "UML_ActGuidePins")  
  
 Bir PIN oluşturmak için tıklayın **giriş PIN** veya **çıkış PIN** araç ve eylem'ye tıklayın. Eylemin çevresinde PIN taşıyın ve adını değiştirin. Girdi oluşturma ve çıkış eylemi, herhangi bir türden iğneleri dahil olmak üzere **çağrı davranış eylemleri**, **arama işlemi Eylemler**, **Gönder sinyal Eylemler**, ve  **Olay eylemleri kabul**.  
  
 İki PIN arasında bir bağlayıcı, yalnızca bir nesne düğümü gelen ve giden akışlar gibi bir nesne akışını temsil eder.  
  
 Her PIN oluşturur veya kabul eder, bir parametre adı gibi nesneleri rolünü belirten bir ad verin.  
  
 İçinde aktarılan nesnelerin türünü belirleyebileceğiniz **türü** özelliği. Bu, bir UML sınıf diyagramında oluşturmuş olduğunuz bir tür olması gerekir.  
  
 Bağlı PIN arasında akan nesneleri başka bir yolla uyumlu olmalıdır. Çıkış PIN tarafından üretilen nesnelerin giriş PIN'in türü türetilen bir türe ait olmasından kaynaklanabilir.  
  
 Alternatif olarak, nesne akışı çıkış türü giriş PIN türünde arasında verileri dönüştüren bir dönüştürme içeren belirtebilirsiniz. En yaygın dönüşümü bu tür, yalnızca daha büyük bir türden uygun bölümü ayıklar. Şekil örnekte Sipariş Ayrıntısı'ndan sevkiyat adres ayıklayan dönüştürme varlığını gösterir.  
  
##  <a name="Details"></a> Daha ayrıntılı bir eylem tanımlama  
 Eylemin adı normalde elde edilecek sonucu netleştirmek için kullanmanın yanı sıra daha fazla ayrıntı için bir eylem ekleyebilirsiniz bazı yollar şunlardır:  
  
-   Daha ayrıntılı bir açıklama yazmak **gövdesi** özelliği. Örneğin, program kodu veya sahte kodun bir parçasını ve elde edilen sonuçları ilişkin kapsamlı bir açıklama yazabilirsiniz.  
  
-   Eylem Davranış Eylemi Çağırma ile değiştirin ve ayrıntılı davranışını içinde ayrı bir etkinlik diyagramı açıklayın. Bkz: [alt etkinliklerle çağrı davranışı eylemleri açıklayan](#Subactivities).  
  
-   Eylemin ayarlamak **yerel koşul Sonralarına** ve **yerel önkoşulları** sonucunu daha ayrıntılı tanımlamak için özellikleri. Daha fazla bilgi için [koşul Sonralarına tanımlama ve önkoşulları](#Postcondition).  
  
###  <a name="Subactivities"></a> Arama davranışını eylemleri açıklayan alt etkinliklerle  
 Ayrı bir etkinlik diyagramı kullanarak bir eylem ayrıntılı davranışını tanımlayabilirsiniz. Uygulamanızın ana etkinlik diyagramında Davranış Eylemi Çağırma tarafından temsil edilen etkinlik diyagramı buna çağrılan bir davranıştır. Davranış Eylemi Çağırma davranışı farklı etkinlikler arasında paylaşılan ve böylece birden çok kez alt etkinlik çizmek zorunda kalmazsınız açıklamak için de kullanabilirsiniz.  
  
 Aşağıdaki şekilde, bir davranış eylemi çağırma sahip etkinlik 1 gösterildiği Diyagram ve Diyagram 2 alt etkinlik diyagramı, aranan davranış gösterir.  
  
 ![Ayrıntılı Eylemler ayrı bir etkinlik diyagramı gösterir](../modeling/media/uml-actguidedetail.png "UML_ActGuideDetail")  
  
##### <a name="to-describe-a-sub-activity-with-a-call-behavior-action"></a>Arama davranışını eylemi ile bir alt etkinlik tanımlamak için  
  
1.  Alt etkinlik diyagramı oluşturmak için **Çözüm Gezgini**, modelleme projenize sağ tıklayın, fareyle **Ekle**ve ardından **yeni öğe**.  
  
2.  İçinde **Yeni Öğe Ekle** iletişim kutusunun **şablonları** tıklayın **etkinlik diyagramı** ve **adı** kutusunda vermeyi planladığınız adını yazın **davranışı eylem çağrısı**.  
  
3.  Alt etkinlik için ayrıntılı iş akışı çizin. Bu adlı bir davranıştır.  
  
    -   Adlı bir alt etkinlik diyagramında **ilk düğüm** çağrılan davranış çağrıldığında denetimin başladığını gösterir. **Etkinlik son düğümü** denetimi üst etkinliği için burada döndürmelidir gösterir.  
  
4.  Ayarlama **davranışı** özelliği **Davranış Eylemi Çağırma** çağrılan davranış diyagrama başvurmak için.  
  
    > [!NOTE]
    >  Alt etkinlik diyagramı üzerinde bazı öğelere sahip olmalıdır veya diyagram için aşağı açılan listesinde kullanılabilir olmayacak **davranışı** özelliği. Ayrıca, trident simgesi görünmez, **Davranış Eylemi Çağırma** ayarladığınız kadar şekil kendi **davranışı** özelliği.  
  
5.  Ayarlama **olduğu zaman uyumlu** özelliği eylemin, çağrılan bir etkinliğin tamamlanmasını bekleyip beklemediğini belirtin.  
  
    -   Ayarlarsanız **olduğu zaman uyumlu** false olarak çağrılan etkinlik tamamlanmadan önce akışı sonraki eyleme devam edebilirsiniz gösterirsiniz. Çıkış tanımlanmamalıdır PIN veya giden veri akışları eylem.  
  
### <a name="describing-data-flow-in-and-out-of-sub-activities"></a>Veri akışı alt etkinlikleri içine ve dışına açıklayan  
 Yazılım parametreleri kullanmak aynı şekilde alt etkinlikleri içine ve dışına akan verileri tanımlayabilirsiniz.  
  
- Giriş ve PIN (1) için her parça içine veya dışına eylemi akan veri adlı davranışı eylemi çıkış oluşturma. Her birini uygun şekilde adlandırın.  
  
- Alt etkinlik diyagramında oluşturma bir **etkinlik parametre düğümü** (2) için her giriş ve çıkış PIN çağıran eylem. Her düğüm, karşılık gelen PIN aynı adı verin.  
  
  > [!NOTE]
  >  Bir etkinlik parametre düğümü bir nesne düğümü benzer. Aradığınız düğüm türünü denetlemek için düğümüne sağ tıklayın ve ardından **özellikleri**. Düğüm türü, Özellikler penceresinde üst bilgisinde gösterilir.  
  
- Alt etkinlik diyagramında içine veya dışına her etkinlik parametresi düğüm nesneleri akışını göstermek bağlayıcıları çizin.  
  
  ![Etkinlik parametreleri için davranış çağrı haritada sabitler](../modeling/media/uml-actguidesub.png "UML_ActGuideSub")  
  
###  <a name="Postcondition"></a> Koşul Sonralarına ve önkoşulları tanımlama  
 Kullanabileceğiniz **yerel koşul Sonralarına** ve **yerel önkoşulları** özellikleri ayrıntılı olarak bir eylem sonucunu belirtmek için. Bu özellikler, etkisi nasıl elde edildiğini açıklamadan eylemi etkisini açıklar.  
  
 Bu özellikleri ayarlamak için eylem sağ tıklayın ve ardından **özellikleri**. Özellikler penceresindeki özellikleri değerleri yazın.  
  
#### <a name="local-postconditions"></a>Yerel koşul Sonralarına  
 Sonkoşul eylem kabul edilebilir önce karşılanması bir durumdur tamamlandı. Örnek uygulamada siparişi onayla Sonkoşul olabilir:  
  
 Müşteri, kredi kartı işlemek için gerekli olan tam ve geçerli ayrıntıları sağlamıştır.  
  
 Önce ve eylem oluştuktan sonra Sonkoşul durumları arasında bir ilişki ifade edebilirsiniz. Örneğin:  
  
 Faiz çift önce neydi oranıdır.  
  
 Verilerin belirli öznitelikleri başvuran ile Eylemler ele daha resmi bir stilde koşul sonralarına yazabilirsiniz. Örneğin:  
  
 `InvoiceTotal == Sum(OrderItem.MenuItem.Price)`  
  
#### <a name="local-preconditions"></a>Yerel önkoşulları  
 Bir önkoşulu eylemi başlamaya hazır olduğunda, true olması gereken bir durumdur. Örneğin, sipariş eylemini Onayla'ya önkoşuluna olabilir:  
  
 Müşteri menüsünden en az bir öğe seçti.  
  
### <a name="describing-calls-to-operations"></a>İşlemleri açıklayan çağrıları  
 Genellikle, kişiler, yazılım veya makineleri karışımından tarafından gerçekleştirilen iş eylemi açıklar. Ancak, belirli yazılım yöntemi veya işlev çağrısı açıklamak için bir çağrı işlemi eylemini kullanabilirsiniz.  
  
-   Hangi işlem çağrılır göstermek için arama işlemi eylemin ve hangi nesne veya bileşen adı ayarlayın.  
  
-   İşlem parametreleri ve dönüş değerleri eylemi çağırma için giriş ve çıkış sabitleyicileri ekleyin.  
  
-   Ayarlayabileceğiniz **olduğu zaman uyumlu** özelliği eylemin, işlemin tamamlanmasını bekleyip beklemediğini belirtin.  
  
    -   Ayarlarsanız **olduğu zaman uyumlu** false olarak çağrılan işlem tamamlanmadan önce akışı sonraki eyleme geçebilirsiniz gösterirsiniz. Çıkış tanımlanmamalıdır PIN veya giden veri akışları eylem.  
  
##  <a name="Concurrent"></a> Eşzamanlı Akışlar  
 Kullanabileceğiniz **Çatal Düğüm** ve **katılın düğüm** iki veya daha fazla iş parçacığı aynı anda çalışabilecek etkinlikleri tanımlamak için.  
  
 ![Eş zamanlı bir akış çatallanma ve birleşme düğümleri Göster](../modeling/media/uml-actguideconcurrent.png "UML_ActGuideConcurrent")  
  
 Etkisini **Çatal Düğüm** (1) iki veya daha fazla iş parçacığı denetimi iş parçacığı ayırmak için. Önceki eylemi sona erdiğinde, çatal çıkış tarafında tüm eylemleri başlatabilirsiniz.  
  
 A **katılın düğüm** (2) eşzamanlı iş parçacığı bir araya getirir. Sonra eylem **katılın düğüm** için önde gelen tüm eylemleri kadar başlatılamayabilir **katılın düğüm** getirildiğinden.  
  
### <a name="describing-signals-and-events"></a>Sinyaller ve olayları açıklama  
 Bir etkinlik gönderme sinyal eylem olarak bir sinyal gönderir bir işlemdeki bir adım gösterebilirsiniz. Belirli bir sinyal veya olay adımı kabul olay eylem olarak devam edebilmesi için bekleyen bir adım gösterebilirsiniz.  
  
 Örneğin, bir siparişi gönderen bir adım ve o sırada işlemeden önce siparişi alması gereken başka bir adım gösterebilir.  
  
#### <a name="sending-a-signal"></a>Sinyal gönderme  
 Sinyal gönderme Eylemi'ni (3), bir sinyal veya ileti tür diğer etkinlikler veya işlemlere gönderilen olduğunu belirtmek için kullanın. Eylem adını, ne tür iletiler gönderdiğini belirtmek için kullanın.  
  
-   Varsa Denetim denetim akışı bir sonraki eylem hemen geçirir.  
  
-   Sinyal gönderme Eylemi'ni işleminizi herhangi bir döndürülen bilgi nasıl yanıt vereceğini açıklamak için kullanamazsınız. Bunu yapmak için ayrı bir olayı kabul etme Eylemi'ni kullanın.  
  
-   Gelen veri akışını bir gönderme sinyal giden ileti ile hangi verilerin gönderilebilir belirtmek için eyleme gösterebilirsiniz. Daha fazla bilgi için [açıklayan veri akışı](#DataFlows).  
  
#### <a name="waiting-for-a-signal-or-event"></a>Bir sinyal veya olay bekleniyor  
 Bu etkinlik bazı dış olay veya gelen ileti için bekleyeceği göstermek için Olayı Kabul Etme Eylemi'ni (4) kullanın. Eylemin adı bekler olay türünü belirtmek için kullanın.  
  
-   Etkinlik bir dış olay veya iletinin, akışta belirli bir noktada bekler göstermek için Olayı Kabul Etme Eylemi'ni gelen akış ile bir etkinlik uygun yerde çizin.  
  
-   Etkinlik bir dış olay veya ileti herhangi bir zamanda yanıt verebileceğini göstermek için Olayı Kabul Etme Eylemi'ni herhangi bir gelen akış olmadan bir çizin. Adlandırılmış bir dış olay ortaya çıktığında, etkinlik Olayı Kabul Etme Eylemi'ni ' itibaren yeni bir iş parçacığı başlar.  
  
-   Sinyal gönderen için döndürülen tüm değerleri tanımlamak için Olayı Kabul Etme Eylemi'ni kullanamazsınız. Bu amaç için ayrı bir sinyal Gönder eylemini kullanın.  
  
-   Giden veri akışı etkinliğiniz sinyalin alınan veriler nasıl işlediğini göstermek için bu eylemden gösterebilirsiniz. Birden fazla çıkış akışını göstermek istiyorsanız ayarlamalısınız **IsUnmarshall türde** eylemi ayrı bileşenlerine gelen sinyal ayrıştırır belirtir kabul olayı eyleminin özelliği. Daha fazla bilgi için [açıklayan veri akışı](#DataFlows).  
  
### <a name="describing-multiple-data-flows"></a>Birden çok veri akışını tanımlama  
 Birden fazla denetim akışı veya işlem sona erdiğinde birden fazla iş parçacığı oluştuğunu göstermek için bir işlem dışı gelen nesne akışı çizebilirsiniz. Denetim ve nesne akışları bir karışımını kullanabilirsiniz etkisi, çatal benzer.  
  
 Aşağıdaki örnek, birden çok akış eylemleri içine ve dışına gösterir.  
  
 ![Paralel nesne akışlar](../modeling/media/uml-actguidemulti.png "UML_ActGuideMulti")  
  
 "Müşteri ayrıntıları sağlar" eylem tamamlandığında, iki nesne oluşturur: "Sevkiyat adresi" ve "Kredi kartı detayları." İki nesne, farklı eylemler tarafından işlenmek üzere İleri gidin.  
  
 Başlatabilmeniz için önce kullanılabilir olan tüm girişleri bir eylem gerektirdiğinden, son eylemi için tüm eylemlerde tamamlanana kadar başlatılmaz.  
  
### <a name="streams"></a>Akışlar  
 Etkinlik diyagramı, bir işlem hattı veya bir dizi aynı anda yürütülen eylem açıklamak ve sürekli olarak veri bir eylemden diğerine geçmesine yardımcı olması için kullanabilirsiniz.  
  
 Amaç aşağıdaki örnekte, her eylem nesneleri oluşturmak ve çalışmaya devam ' dir. Denetim akış olduğundan, ilk nesnelerini aldıktan hemen sonra her eylem başlayabilirsiniz.  
  
 Bunların tümü en az bir uç düğümde bir etkinlik parametresi, nesne düğümü veya bir giriş veya çıkış olmadığından bağlayıcıları Bu örnekte nesne akışları olduğuna dikkat edin.  
  
 ![Bir veri akışı](../modeling/media/uml-actguidestream.png "UML_ActGuideStream")  
  
 1. Örneğin, giriş ve çıkışlarını temsil eden üç etkinlik parametre düğümleri, sahiptir.  
  
 2. Nesne düğümleri, PIN giriş ve çıkış sabitleyicileri arabelleği temsil edebilir. Kaç nesnenin durumuna bir nesne düğümü özelliği aynı anda arabellekteki olabilir üst sınırı ayarlayabilirsiniz.  
  
 3. Bir akış böldüğünü aşağı farklı dallara farklı nesneler gönderiliyor göstermek için karar düğümleri kullanabilirsiniz. Bölme ölçütü açıklamak için yorum veya düğümler başlıklarını kullanabilirsiniz.  
  
 4. Çatal düğümler için eşzamanlı işlemeyi göndererek nesneleri iki veya daha fazla kopyasını yapıldığını göstermek için kullanabilirsiniz.  
  
 5. Birleştirme düğümleri, iki akış işleme geri birine birleştirilir göstermek için kullanabilirsiniz.  
  
### <a name="selection-and-transformation"></a>Seçim ve dönüştürme  
 Bir nesne akışı nesneleri, seçili dönüştürüldüğünü belirtebilirsiniz veya her ikisini de. Nesne akışı bir akış için veya bir PIN veya bir nesne düğümü olur.  
  
- Bir dönüştürme, bir akış girerek nesneleri başka bir türe nasıl dönüştürülür açıklar.  
  
- Bir seçim nasıl yalnızca açıklar bazı akış girerek nesneleri alıcı eyleme iletilir.  
  
  Örnek bir dönüştürmeyi gösterir. Bir posta kodu veya posta kodu, bir çıkış PIN Diyagram 1 ilk eylem üretir. Bu ikinci eylemi Giriş bir PIN bağlıdır. Ancak, tam olarak belirtilen bir adres ikinci eylemi bekliyor. Bir türden diğerine dönüştürme, adres arama gibi ikinci bir etkinlik içinde belirtilir. Bu nesne akışına dönüştürme özelliğinden başvuruluyor. Adres Arama etkinliği, gelen posta kodu için bir etkinlik parametre düğümü ve giden tam adresi için başka bir etkinlik parametresi düğümü içerir.  
  
  ![Nesne başka bir diyagrama tanımlanan dönüşüm](../modeling/media/uml-actguidetransform.png "UML_ActGuideTransform")  
  
  Bir dönüştürme ya da seçimi iki şekilde belirtebilirsiniz:  
  
- Giriş veya çıkış PIN için bir açıklama ekleyin.  
  
  -   Bu açıklamayı genel açıklamadan ayırt etmek için bir açıklama ile başlanması <\<**dönüştürme**>> veya <\<**seçimi**>>.  
  
- Ayrıntılı olarak ayrı bir etkinlik diyagramı, dönüştürme ya da seçimi belirtin.  
  
  -   Bu yöntemi kullanırsanız, bir açıklama ayrıca Temizle dönüştürme tanımlanmamış okuyucularına yapmak için iliştirin.  
  
##### <a name="to-specify-a-transformation-or-selection-in-a-separate-activity-diagram"></a>Bir dönüştürme ya da seçimi ayrı etkinlik diyagramında belirtmek için  
  
1. Dönüştürme ya da seçimi akışını açıklamak yeni bir etkinlik diyagramı oluşturun.  
  
   -   İçinde **Çözüm Gezgini**, projenize sağ tıklayın, fareyle **Ekle**, tıklayın **yeni öğe**ve ardından **etkinlik diyagramı**. Diyagram, dönüştürme ya da seçimi akış için uygun bir ad verin. **Ekle**'yi tıklatın.  
  
2. Yeni bir diyagramda:  
  
   1.  İki etkinlik parametre düğümleri, Giriş akışı için bir ve çıkış için bir tane oluşturun.  
  
   2.  Nesne akışları ile birbirine bağlı bir eylem oluşturun. Bu, dönüştürme ya da seçimi nasıl çalıştığını gösterir.  
  
3. Dönüştürme ya da seçimi kullanmak istediğiniz herhangi bir diyagrama içinde:  
  
   1.  Diğer bir deyişle, bağlayıcı için veya bir giriş veya çıkış PIN, bir nesne düğümü ya da bir etkinlik parametre düğümü bir nesne akış oluşturun.  
  
   2.  Nesne akışı sağ tıklayın ve ardından **özellikleri**.  
  
   3.  İçinde **dönüştürme** veya **seçimi** özelliği, belirtilen burada dönüştürme ya da seçimi akış diyagramı seçin.  
  
   Bir seçim tek tek giriş ve çıkış sabitleyicileri ve bir nesne düğümü de tanımlayabilirsiniz. Bir seçim etkinliği önceki yordamı tanımlayın ve ardından **seçimi** nesne düğümü veya giriş veya çıkış PIN özelliği.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [UML modellerini ve diyagramları düzenleme](../modeling/edit-uml-models-and-diagrams.md)   
 [UML sıralı diyagramlar: başvuru](../modeling/uml-sequence-diagrams-reference.md)   
 [UML Bileşen Diyagramları: başvuru](../modeling/uml-component-diagrams-reference.md)   
 [UML Kullanım durumu diyagramları: başvuru](../modeling/uml-use-case-diagrams-reference.md)   
 [UML sınıf diyagramları: başvuru](../modeling/uml-class-diagrams-reference.md)   
 [UML Bileşen Diyagramları: başvuru](../modeling/uml-component-diagrams-reference.md)   
 [Video: Etkinlik diyagramları kullanarak iş akışlarını yakalama](http://channel9.msdn.com/posts/clinted/UML-with-VS-2010-Part-4-Capture-Business-Workflows/)



