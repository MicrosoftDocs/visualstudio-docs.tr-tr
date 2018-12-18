---
title: 'UML Bileşen Diyagramları: Yönergeler | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- UML diagrams, component
- diagrams - modeling, component
- diagrams - modeling, UML component
- UML, component diagrams
- component diagrams
ms.assetid: 6c1bdd60-369e-477e-83ed-7f6fe75c9f0b
caps.latest.revision: 37
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 7400bac1fa6dcbf086718e54d18288b8ab80f1b0
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51801486"
---
# <a name="uml-component-diagrams-guidelines"></a>UML Bileşen Diyagramları: Yönergeler
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio'da çizdiğiniz bir *bileşen diyagramı* bir yazılım sisteminin yapısını göstermek için. Video gösterimi için bkz. [Bileşen diyagramları kullanarak fiziksel yapıyı tasarlama](http://channel9.msdn.com/posts/clinted/UML-with-VS-2010-Part-6-Designing-a-Projects-Physical-Structure/).  
  
 Bu özellik, Visual Studio'nun hangi sürümlerinin desteklediğini görmek için bkz: [mimari ve Modelleme Araçları sürüm desteği](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
 Bir UML bileşen diyagramı oluşturmak için **mimarisi** menüsünü tıklatın **yeni UML veya katman diyagramı**.  
  
 Bir bileşen kendi ortamında değiştirilebilen modüler bir birimdir. Kendi iç yapıları gizlidir, ancak olduğu bir veya daha fazla iyi tanımlanmış *sağlanan arabirimleri* üzerinden işlevlere erişilebilen. Bir bileşen bulundurabilirsiniz *gerekli arabirimleri*. Gerekli arabirim, diğer bileşenlerden hangi işlevleri veya hizmetleri beklediğini tanımlar. Birçok bileşenin sağlanan ve gerekli arabirimleri bağlanarak daha büyük bir bileşen oluşturulabilir. Tam bir yazılım sistemi bir bileşen olarak anlaşılabilir.  
  
 Bileşen diyagramı çizmenin birçok faydası vardır:  
  
- Tasarımınızı ana blokları dikkate alarak göz önünde bulundurmak, geliştirme takımının varolan tasarımı anlamasına ve yeni bir tane oluşturmasına yardım eder.  
  
- Sisteminizi iyi tanımlanmış sağlanan ve gerekli arabirimlerden oluşan bir bileşenler koleksiyonu gibi düşünerek, bileşenler arasındaki ayrımı daha iyi anlayabilirsiniz. Böylece, tasarımın anlaşılması ve gereksinimler değiştiğinde değiştirilmesi daha kolay hale gelir.  
  
  Bileşen diyagramını, tasarımın kullandığı veya kullanacağı dile ya da platforma bakılmaksızın tasarımınızı göstermek için kullanabilirsiniz.  
  
##  <a name="OtherDiagrams"></a> Diğer diyagramlarla ilişki  
 Bileşen diyagramını başka diyagramlarla birlikte kullanabilirsiniz.  
  
|Başka diyagram|Tasarımınızın bu yönlerini tartışmanıza ve iletişim kurmanıza yardımcı olur|  
|-------------------|--------------------------------------------------------------------|  
|UML Sıralı Diyagramı|-Sistemin bileşenleri arasındaki etkileşimler<br />-Etkileşimler ve bileşen içindeki bölümlerin arasında.<br /><br /> Daha fazla bilgi için [UML sıralı diyagramlar: yönergeler](../modeling/uml-sequence-diagrams-guidelines.md).|  
|UML Sınıf Diyagramı|-Bir bileşenin arabirimleri. Sınıf diyagramı arabirimin yöntemlerini ayrıntılı olarak incelemenizi sağlar.<br />-Bileşenlerin arabirimleri arasında parametrelerde gönderilen verileri.<br /><br /> Daha fazla bilgi için [UML sınıf diyagramları: yönergeler](../modeling/uml-class-diagrams-guidelines.md).|  
|Etkinlik Diyagramları|-Gelen iletilere yanıt olarak bir bileşen tarafından gerçekleştirilen iç işleme.<br /><br /> Daha fazla bilgi için [UML etkinlik diyagramları: yönergeler](../modeling/uml-activity-diagrams-guidelines.md).|  
|Katman Diyagramları|-Mantıksal mimari katmanları bileşenleriniz için.<br /><br /> Daha fazla bilgi için [katman diyagramları: başvuru](../modeling/layer-diagrams-reference.md).|  
  
##  <a name="Basics"></a> Bileşen diyagramları çizmek için temel adımlar  
 Bileşen diyagramlarındaki öğeler hakkında başvuru bilgileri için bkz [UML Bileşen Diyagramları: başvuru](../modeling/uml-component-diagrams-reference.md).  
  
 Tasarım aşamasında Bileşen diyagramlarının nasıl kullanıldığı hakkında daha fazla bilgi için bkz. [uygulama Mimarinizi modelleme](../modeling/model-your-app-s-architecture.md).  
  
> [!NOTE]
>  Herhangi bir modelleme diyagramının oluşturmaya yönelik ayrıntılı adımlar açıklanmıştır [Düzenle UML modellerini ve diyagramları](../modeling/edit-uml-models-and-diagrams.md).  
  
#### <a name="to-create-a-component-diagram"></a>Bir bileşen diyagramı oluşturmak için  
  
1.  Üzerinde **mimarisi** menüsünü tıklatın **yeni UML veya katman diyagramı**.  
  
2.  Altında **şablonları**, tıklayın **UML bileşen diyagramı**.  
  
3.  Diyagrama ad verin.  
  
4.  İçinde **modelleme projesine Ekle**, çözümünüzde varolan modelleme projesini seçin veya **yeni modelleme projesi oluşturma**ve ardından **Tamam**...  
  
     Yeni bileşen diyagramı UML görünür **bileşen diyagramı** araç kutusu. Araç kutusu gereken öğeleri ve ilişkileri içerir.  
  
### <a name="drawing-components"></a>Bileşenleri Çizme  
 ![Bileşenlerin arabirimleri ile](../modeling/media/uml-compdrawing.png "UML_CompDrawing")  
  
 Oluşturma bir *bileşen* (1) sisteminizdeki veya uygulamanızdaki her ana işlevsel birim için.  
  
 Örnekler arasında uygulama, donanım cihazı, Web hizmeti, .NET derleme, program sınıfı veya sınıflar grubu ya da programın herhangi bir ayrılabilen kesimi bulunur.  
  
##### <a name="to-create-components"></a>Bileşenler oluşturmak için  
  
1.  Tıklayın **bileşen** Araç Kutusu'nda ve ardından diyagramın boş bir kısmına tıklayın.  
  
     \- veya -  
  
     Varolan bileşeni kopyalayıp yapıştırın.  
  
    1.  Diyagramda veya varolan bileşeni bulun **UML Model Gezgini**.  
  
    2.  Bileşene sağ tıklayın ve ardından **kopyalama**.  
  
    3.  Kopyalanan bileşenin görünmesini istediğiniz yerde diyagramı açın.  
  
    4.  Diyagramın boş bir bölümüne sağ tıklayın ve ardından **Yapıştır**.  
  
         Bileşenin kopyası yeni bir adla görünür.  
  
2.  Değiştirmek için bileşenin adına tıklayın.  
  
3.  Yalnızca bileşenin başlığını görmek istiyorsanız köşeli çift ayraca (5) tıklayın.  
  
### <a name="showing-the-ports-of-a-component"></a>Bileşenin Bağlantı Noktalarını Gösterme  
 A *bağlantı noktası* (2, 3) temsil grubunu iletileri ya da veya bir bileşen dışından geçen, işlem çağrıları gösterir. Grup, bağlantı noktasının türünü tanımlayan arabirim tarafından açıklanır. Bağlantı noktası, arabirim sağlar veya arabirim gerektirir.  
  
 Bir bağlantı noktası ile bir *sağlanan arabirime* bileşen tarafından uygulanan ve diğer bileşenler tarafından kullanılabilen işlemleri (2) sağlar.  
  
 Örnekler, herhangi bir programlama dilinde kullanıcı arabirimi, Web hizmeti, .NET arabirimi veya işlevler topluluğunu içerir.  
  
 Bir bağlantı noktası ile bir *gerekli arabirime* (3) bir grup diğer bileşenler veya dış sistemler tarafından sağlanan işlemler veya hizmetler için bileşenin gereksinimini gösterir.  
  
 Örneğin, Web tarayıcısı Web hizmetleri gerektirir veya uygulama eklentisi uygulamadan hizmetler gerektirir.  
  
 Bir bileşen herhangi bir sayıda bağlantı noktasına sahip olabilir.  
  
##### <a name="to-add-ports-to-a-component"></a>Bileşene bağlantı noktaları eklemek için  
  
1. Araç kutusunda tıklayın **sağlanan arabirim** veya **gerekli arabirim**.  
  
2. Eklemek istediğiniz bileşene tıklayın.  
  
    Bir bağlantı noktası bileşenin sınırında görünür.  
  
    Yeni arabirim bir bağlantı noktası türü olarak oluşturulur. Bu arabirim görünür **UML Model Gezgini**.  
  
3. Bağlantı noktasını bileşen sınırı etrafında istediğiniz yere yerleştirmek için sürükleyin.  
  
4. Bağlantı noktasının etiketini konumunu ayarlamak için sürükleyin.  
  
5. Etiketi değiştirmek için ona tıklayın. Etiket arabirimin adını gösterir. Etiketi değiştirirseniz, arabirimin adı da değişir.  
  
   Arabirimin özniteliklerini ve işlemlerini listelemek istiyorsanız, bunu UML Model Gezgini'nde arabirime ekleyerek yapabilirsiniz. Alternatif olarak, arabirimi UML Model Gezgini'nden sınıf diyagramına sürükleyebilir ve işlemleri ve öznitelikleri buraya ekleyebilirsiniz.  
  
### <a name="linking-between-components"></a>Bileşenler arasında bağlama  
 Bir bileşen gereksiniminin başka bileşen tarafından sağlanan işlemler veya hizmetler tarafından karşılanabileceğini göstermek için bir bağımlılık (4) kullanın.  
  
##### <a name="to-show-that-a-provided-interface-can-satisfy-a-required-interface"></a>Sağlanan arabirimin gerekli arabirimi karşılayabileceğini göstermek için  
  
1. Araç kutusunda tıklayın **bağımlılık**.  
  
2. Bir bileşende gerekli arabirime sahip bağlantı noktasına tıklayın ve ardından başka bir bileşende sağlanan arabirime sahip bağlantı noktasına tıklayın.  
  
   Gruptaki her bileşenin diğer bileşenlere bağlı olduğu bağımlılık döngülerini tasarlamaktan kaçınmayı denemelisiniz.  
  
##### <a name="to-add-a-port-for-an-existing-interface-to-a-component"></a>Varolan arabirim için bileşene bağlantı noktası eklemek üzere  
  
-   Ndeki arabirimi bulun **UML Model Gezgini** ve onu buradan bileşene sürükleyin.  
  
     veya  
  
-   Başvuruyu diyagramdan arabirime kopyalayıp yapıştırın.  
  
    1.  Bir sınıf diyagramı veya bileşen diyagramında arabirime sağ tıklayın ve ardından **kopyalama**.  
  
    2.  Bileşen diyagramında bileşene sağ tıklayın ve ardından **başvuruyu Yapıştır**.  
  
         Sağlanan arabirim bileşende görünür. Yakında bir Eylem etiketi görünür.  
  
        > [!NOTE]
        >  Kullanırsanız **Yapıştır** yerine **başvuruyu Yapıştır**, yeni bir ada sahip bir yeni arabirim oluşturulacaktır.  
  
    3.  Gerekli arabirimi oluşturmak istediyseniz, eylem'e ve ardından **gerekli arabirime Dönüştür**.  
  
##  <a name="Parts"></a> Bir bileşenin iç parçalarını gösterme  
 ![Bileşen Diyagramı iç parçalarını gösterme](../modeling/media/uml-compshowing.png "UML_CompShowing")  
  
 Nasıl birbiriyle etkileşim kuran daha küçük bileşenlerden oluştuğunu göstermek için bileşene (1) parçalar (3) yerleştirebilirsiniz.  
  
 Şekildeki diyagram, Şimdi Akşam Yemeği Web Hizmeti türünün her örneğinin bir Müşteri Hizmeti Sunucusu ve bir Mutfak Hizmeti Sunucusu içerdiğini belirtir.  
  
 Bir parça, sıradan bir sınıfa ait öznitelik gibi onun ana bileşeninin bir özelliğidir. Bir parçanın genellikle bileşen olan kendi türü vardır. Parçanın etiketi, sıradan bir öznitelikle aynı biçime sahiptir:  
  
 `+ partName : TypeName`  
  
 Ana bileşenin içinde, her parça türü (4, 5) için tanımlanmış sağlanan ve gerekli arabirimleri gösterir. Bir parça için gereken işlemler veya hizmetler bir diğeri tarafından sağlanabilir. Kullanabileceğiniz **parça derlemesi** parçaların birbirleriyle (6) nasıl bağlandığını göstermek için.  
  
 Ana bileşenin arabiriminin gerçekte parçalarından biri tarafından sağlandığını veya gerekli kılındığını da gösterebilirsiniz. Üst bağlantı noktasını kullanarak bir iç parçanın bağlantı noktasına bağlanabileceğiniz bir **temsilci** ilişkisi (9). İki bağlantı noktası aynı türden olmalıdır (sağlanan veya gerekli) ve onların arabirim türleri uyumlu olmalıdır.  
  
 Yeni bir tür ile veya varolan türden yeni bir parça oluşturabilirsiniz.  
  
#### <a name="to-add-parts-to-a-component"></a>Bileşene parçalar eklemek için  
  
1.  Ana bileşenin bir parçası olarak düşündüğünüz her ana işlevsel birim için parça oluşturun.  
  
    1.  Tıklayın **bileşen** araç ve (1) ana bileşenin içine tıklayın.  
  
         Yeni parça (3) ana bileşenin içinde görünür.  
  
         Yeni bir bileşen oluşturulan **UML Model Gezgini**. Bu, yeni parçanın türüdür.  
  
         \- veya -  
  
         Varolan bileşeni UML Model Gezgini'nden ana bileşen üzerine sürükleyin.  
  
         Yeni parça (3) ana bileşenin içinde görünür. Türü UML Model Gezgini'nden sürüklediğiniz bileşendir.  
  
         \- veya -  
  
         Diyagramda veya UML Model Gezgini'nde bileşene sağ tıklayın ve ardından **kopyalama**.  
  
         Ana bileşen üzerinde sağ tıklayın ve ardından **başvuruyu Yapıştır**.  
  
         Yeni parça (3) ana bileşenin içinde görünür. Türü kopyaladığınız bileşendir.  
  
    2.  Değiştirmek için yeni parçanın adına tıklayın. Türünü değiştiremezsiniz.  
  
    3.  Yeni parçaya sağlanan ve gerekli arabirimleri (4, 5) ekleyebilirsiniz. Tıklayın **sağlanan arabirim** veya **gerekli arabirim** aracını ve ardından parçanın içine tıklayın.  
  
         \- veya -  
  
         Mevcut bir arabirimden sürükleyin **UML Model Gezgini** parçaya.  
  
         Arabirimler parçanın türüne eklenir ve kendi parçası üzerinde görünür. Gerekirse ana bileşen kendi boyutunu ayarlar.  
  
2.  Parçaları birbirine bağlayın.  
  
    -   Kullanım **bağımlılık** (6) farklı parçaların bağlantı noktalarını bağlanmak için aracı.  
  
3.  Parçaları ana bileşenin bağlantı noktalarına bağlayın:  
  
    1.  Ana bileşen üzerinde bir veya daha çok bağlantı noktası (7) oluşturun. Tıklayın **gerekli arabirim** veya **sağlanan arabirim** araç kutusunda ve ardından ana bileşene tıklayın.  
  
    2.  Bağlantı noktalarını (9) bir veya daha çok parçaya atayın. Tıklayın **temsilci** aracı sonra ana bileşen üzerindeki bir bağlantı noktası ve bir bağlantı noktasında bir parçası. Bağlantı noktalarını sağlanan veya gerekli arabirimlerle aynı şekilde bağlayabilirsiniz.  
  
### <a name="showing-the-parts-of-a-part"></a>Bir Parçanın Parçalarını Gösterme  
 Bir bileşeni parçalara ayırdıktan sonra, parça türlerinin her birini kendi iç parçalarına ayırabilirsiniz.  
  
 Ayrışımın her katmanının, ayrı bileşen diyagramında tutulması en kolay yoldur. İlk önce parçanın türünü bulmanız gerekir. Örneğin, çizimdeki parçalarından adlandırılır `DNCustomerServer`, ve türü olarak adlandırılan bir bileşendir `CustomerServer`. Bu türü UML Model Gezgini'nde bulabilir ve onu başka bir diyagrama yerleştirebilirsiniz. Daha sonra onun kendi iç parçalarını oluşturabilirsiniz.  
  
##### <a name="to-place-a-parts-type-on-a-diagram"></a>Diyagrama parçanın türünü yerleştirmek için  
  
1.  Parça türünün tam adını belirleyin.  
  
     Parçaya sağ tıklayın ve ardından **özellikleri**.  
  
     Tür adı görünür **türü** Özellikler penceresinin alan.  
  
2.  Nde parçanın türünü bulun **UML Model Gezgini**.  
  
     Tıklayın **görünümü**, işaret **diğer Windows**ve ardından **UML Model Gezgini**.  
  
     Projeyi ve gerekirse türün ait olduğu herhangi bir paketi genişletin.  
  
     Türü olarak listelenen bir **bileşeni**.  
  
     İsterseniz adını burada değiştirebilirsiniz.  
  
3.  Başka bir bileşen diyagramı açın veya oluşturun.  
  
4.  UML Model Gezgini'ndeki türden diyagram üzerine sürükleyin.  
  
     Türün görünümü diyagramda bileşen olarak görüntülenir.  
  
     Parça için tanımladığınızla aynı arabirimlere sahiptir.  
  
     Artık parçaları içine ekleyebilirsiniz.  
  
##  <a name="Designing"></a> Bileşeni tasarlama  
  
### <a name="describing-how-the-parts-collaborate"></a>Parçaların Birlikte Nasıl Çalıştığını Açıklama  
 Parçaların ana bileşene ulaşan iletiye yanıt olarak birlikte nasıl çalıştığını göstermek için sıralı diyagram çizebilirsiniz.  
  
 Bu diyagramları hem varolan bileşeni açıklamak hem de yeni bileşen tasarlamak için kullanabilirsiniz.  
  
 Hala bileşeni tasarlıyorsanız, hangi parçalara sahip olacağına karar vermeden önce sıralı diyagramlar çizebilirsiniz. Sıralı diyagramları farklı parçalar, gerekli arabirimler ve ileti dizileri ile denemek için kullanabilirsiniz. En sık ve en önemli gelen iletiler için sıralı diyagramlar çizin. Daha sonra üzerinde karar verdiğiniz yaşam çizgilerine karşılık gelen bileşeninizde parçalar oluşturabilirsiniz.  
  
 Sistem işinin farklı bileşenler arasında nasıl yayıldığını değerlendirmek için sıralı diyagramlar kullanın.  
  
- Bir parçaya çok fazla yüklenilirse, işin eşit bir şekilde dağıtıldığı durumlara göre uygulamanın güncelleştirilmesi daha zor olacaktır.  
  
- İş birçok etkileşimle yetersiz bir şekilde dağıtılmışsa, sistem kötü bir şekilde çalışabilir ve anlaşılması zor olabilir.  
  
  ![Sıralı diyagram gösterme işbirliği bölümleri](../modeling/media/uml-compdescparts.png "UML_CompDescParts")  
  
##### <a name="to-draw-a-sequence-diagram-that-shows-collaboration-between-parts"></a>Parçalar arasındaki işbirliğini gösteren sıralı diyagram çizmek için  
  
1.  Yeni bir sıralı diyagram oluşturun.  
  
     Daha fazla bilgi için [UML sıralı diyagramlar: yönergeler](../modeling/uml-sequence-diagrams-guidelines.md).  
  
2.  Dış bileşen, kullanıcı, cihaz veya bu bileşene iletiler gönderen diğer aktör (1) için yaşam çizgisi oluşturun.  
  
     Ayarlayabileceğiniz **aktör** özelliği bu yaşam çizgisinin bileşenin olduğunu belirtmek için true. Çubuk şekli yaşam çizgisinin üzerinde görünür.  
  
3.  Seçilen aktörün iletiler gönderdiği bu bileşenin sağlanan arabirimi (2) için yaşam çizgisi oluşturun.  
  
4.  Bileşenin her parçası (3) için yaşam çizgisi oluşturun.  
  
5.  Bileşenin gerekli her arabirimi (4) için yaşam çizgisi oluşturun.  
  
6.  Dış aktörden (5) gelen iletileri çizin. İletinin parçalara nasıl geçtiğini ve iletiye yanıt vermek için nasıl işbirliği yaptıklarını gösterin.  
  
7.  Gerektiği yerde gerekli arabirime (6) gönderilen iletileri gösterin. İletinin yürütmesi içinde hiçbir ayrıntıyı göstermeyin.  
  
### <a name="is-the-component-more-than-its-parts"></a>Bileşen Parçalarından Daha Fazla Mıdır?  
 Bazı durumlarda bileşen, parçalar topluluğuna verilen bir addan daha fazlası değildir. Tüm iş parçalar tarafından yapılır ve çalışma zamanında bileşeni gösteren kod veya başka bir yapı yoktur.  
  
 Ayarlayarak bu modelde gösterebilir **dolaylı olarak Örneklendirilmiş** bileşenin özelliği. Bu durumda, bileşenin tüm arabirimleri yetki iç parçalara aktarılarak bağlantı noktaları üzerinde olmalıdır.  
  
### <a name="describing-the-process-inside-each-part"></a>Her Parça İçindeki İşlemi Açıklama  
 Etkinlik diyagramlarını bileşenin gelen her iletiyi nasıl işlediğini göstermek için kullanabilirsiniz. Daha fazla bilgi için [UML etkinlik diyagramları: yönergeler](../modeling/uml-activity-diagrams-guidelines.md).  
  
 ![Etkinlik diyagramı veri arabelleği ile](../modeling/media/uml-compdescribingproc.png "UML_CompDescribingProc")  
  
 Gelen iletinin yeni bir iş parçacığı başlattığını göstermek için Olayı Kabul Etme Eylemi'ni (1) kullanın.  
  
 Bilgi akışını ve bilginin nerede depolandığını göstermek için nesne düğümlerini ve giriş/çıkış sabitleyicilerini kullanın. Örnekte, bir nesne düğümü (2), bir iş parçacığı ile diğeri arasında arabelleğe alınan öğeleri göstermek için kullanılır.  
  
### <a name="defining-data-and-classes"></a>Veri ve Sınıfları Tanımlama  
 UML sınıf diyagramını şunların ayrıntılı içeriğini açıklamak için kullanabilirsiniz:  
  
-   Bileşenlerin arabirimleri. Bir bileşene gerektirir veya sağlar bağlantı noktası eklediğinizde, UML Model Gezgini'nde bir arabirim görünür. Bunu, özniteliklerini, işlemlerini ve diğer arabirimleriyle olan ilişkilerini göstermek için UML Sınıf Diyagramına sürükleyebilir veya kopyalayabilirsiniz.  
  
-   Arabirimlerdeki işlemlerin parametrelerinde geçirilen veriler.  
  
-   Etkinlik diyagramlarındaki nesne akışlarında gösterildiği gibi bileşenlerde depolanan veriler.  
  
### <a name="general-dependencies-between-components"></a>Bileşenler Arasındaki Genel Bağımlılıklar  
 Yalnızca tasarımınızın ana parçalarını ve onların bağımlılıklarını göstermek için bileşen diyagramını kullanabilirsiniz.  
  
 ![Bileşenler arasındaki bağımlılık](../modeling/media/uml-compdepend.png "UML_CompDepend")  
  
 Kullanım **bağımlılık** bağımlılığı çizmek için araç. Bu, bir bileşenin tasarımının başka birine bağlı olduğunu gösterir.  
  
 Bağımlılığın tipik türleri şunlardır:  
  
- Bir bileşen diğeri içindeki kodu çağırır.  
  
- Bir bileşen başka bir sınıfın içinde tanımlanan sınıfın örneğini oluşturur.  
  
- Bir bileşen başka bir bileşen tarafından oluşturulan bilgileri kullanır.  
  
  Kullanımın belirli bir türünü göstermek için bağımlılık okunun adını kullanabilirsiniz. Adı ayarlamak için oka sağ tıklayın ve ardından **özellikleri**, ayarlayıp **adı** Özellikler penceresindeki alan.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [UML modellerini ve diyagramları düzenleme](../modeling/edit-uml-models-and-diagrams.md)   
 [UML Bileşen Diyagramları: başvuru](../modeling/uml-component-diagrams-reference.md)   
 [UML sıralı diyagramlar: başvuru](../modeling/uml-sequence-diagrams-reference.md)   
 [UML Kullanım durumu diyagramları: başvuru](../modeling/uml-use-case-diagrams-reference.md)   
 [UML sınıf diyagramları: başvuru](../modeling/uml-class-diagrams-reference.md)   
 [UML Bileşen Diyagramları: başvuru](../modeling/uml-component-diagrams-reference.md)   
 [Video: Bileşen diyagramları kullanarak fiziksel yapıyı tasarlama](http://channel9.msdn.com/posts/clinted/UML-with-VS-2010-Part-6-Designing-a-Projects-Physical-Structure/)



