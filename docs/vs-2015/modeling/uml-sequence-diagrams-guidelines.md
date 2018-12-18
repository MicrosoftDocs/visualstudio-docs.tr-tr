---
title: 'UML sıralı diyagramlar: Yönergeler | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.teamarch.sequencediagram.linktosequencediagram
- vs.teamarch.logicalclassdiagram.createlifeline
- vs.teamarch.componentdiagram.createlifeline
helpviewer_keywords:
- diagrams - modeling, sequence
- sequence diagrams
- UML diagrams, sequence
- interactions, UML
- diagrams - modeling, UML sequence
- UML interactions
- UML, sequence diagrams
- UML sequence diagrams
- behaviors, UML
ms.assetid: 5990ef7c-ba60-4e20-a36d-e29c1fa6c8bb
caps.latest.revision: 55
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 56ecc5c54611f94cdbfb0f08ec54a4e0722f0cbd
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51803636"
---
# <a name="uml-sequence-diagrams-guidelines"></a>UML Sıralı Diyagramlar: Yönergeler
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio'da çizdiğiniz bir *sıralı diyagram* etkileşim göstermek için. Etkileşim, sınıflar, bileşenleri, alt sistemler veya aktörler tipik örnekleri arasında iletileri dizisidir.  
  
 UML sıralı diyagramlar bir UML modeli bir parçasıdır ve yalnızca UML modelleme projeleri içinde mevcuttur. Bir UML sıralı diyagramı oluşturmak için **mimarisi** menüsünde tıklatın **yeni UML veya katman diyagramı**. Hakkında daha fazla bilgi edinin [UML sıralı diyagram öğelerini](../modeling/uml-sequence-diagrams-reference.md) veya [UML modelleme diyagramlarını](../modeling/edit-uml-models-and-diagrams.md) genel. Video gösterimi için bkz. [tasarlamaktan sıralı diyagramlar (2010) kullanarak etkileşimleri](http://channel9.msdn.com/Blogs/clinted/UML-with-VS-2010-Part-7-Sketching-Interactions-with-Sequence-Diagrams).  
  
 Bu özellik, Visual Studio'nun hangi sürümlerinin desteklediğini görmek için bkz: [mimari ve Modelleme Araçları sürüm desteği](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
## <a name="in-this-topic"></a>Bu konuda  
 [UML sıralı diyagramları kullanma](#Using)  
  
 [Sıralama diyagramları çizmek için temel adımlar](#BasicSteps)  
  
 [Oluşturma ve basit sıralı diyagramları kullanma](#Simple)  
  
 [Sınıfları ve yaşam çizgileri](#ClassesAndLifelines)  
  
 [Yeniden kullanılabilir etkileşimi dizileri oluşturma](#Multiple)  
  
 [Yaşam çizgileri gruplarını daraltma](#Collapse)  
  
 [Denetim Yapılarını Parçalarla Açıklama](#Fragments)  
  
##  <a name="Using"></a> UML sıralı diyagramları kullanma  
 Çeşitli amaçlarla farklı program ayrıntı düzeylerinde için sıralı diyagramlar kullanabilirsiniz. Sıralı diyagram çizmek için tipik durumlar aşağıdaki gibidir:  
  
- Sisteminizin kullanıcıları ve onların hedeflerini özetleyen bir kullanım durumu diyagramı varsa, her kullanım örneği amacı karşılamak için sistemin ana bileşenlerini nasıl etkileşimde bulunduğunu açıklamak için sıralı diyagramlar çizebilirsiniz. Daha fazla bilgi için [UML Kullanım durumu diyagramları: yönergeler](../modeling/uml-use-case-diagrams-guidelines.md).  
  
- Bir arabirimin bir bileşenin gelen iletiler belirlediyseniz, bileşenin iç parçalarını gelen her ileti için gereken sonucu elde etmek üzere nasıl etkileşimde bulunduğunu açıklamak için sıralı diyagramlar çizebilirsiniz. Daha fazla bilgi için [UML Bileşen Diyagramları: yönergeler](../modeling/uml-component-diagrams-guidelines.md).  
  
  Sıralı diyagram çizmenin birçok faydası vardır:  
  
- Görevleri bileşenleri arasında nasıl dağıtıldığını kolayca görebilirsiniz.  
  
- Yazılım güncelleştirme zorlaştıran etkileşimi örneklerini tanımlayabilirsiniz.  
  
## <a name="relationship-to-other-diagrams"></a>Diğer diyagramlarla ilişki  
 Diğer diyagramlarla birlikte UML sıralı diyagramlar çeşitli yollarla kullanabilirsiniz.  
  
#### <a name="lifelines-and-types"></a>Yaşam çizgilerini ve türleri  
 Bir sıralı diyagramda çizim yaşam çizgilerini bileşenler veya sınıflara tipik örneklerini sisteminizde temsil edebilir. Yaşam çizgilerini türler, yaşam çizgilerini türler oluşturmak ve türleri UML sınıf diyagramları ve UML Bileşen diyagramları göster. Daha fazla bilgi için [sınıfları ve yaşam çizgilerini](#ClassesAndLifelines).  
  
#### <a name="parameter-types"></a>Parametre türleri  
 Bir UML sınıf diyagramında parametre türleri de tanımlayabilirsiniz ve yaşam çizgileri arasında gönderilen iletilerde kullanılan değerleri döndürdü.  
  
#### <a name="use-case-details"></a>Servis talebi ayrıntıları  
 Kullanım örneği, bir kullanıcının hedef, hedefe ulaşmak için adımlar dizisini temsil eder. Adımların sırasını birkaç şekilde açıklanabilir. Kullanıcılar ve sistemin ana bileşenleri arasındaki etkileşimler gösteren sıralı diyagram çizmek bir seçenektir. Daha fazla bilgi için [UML Kullanım durumu diyagramları: yönergeler](../modeling/uml-use-case-diagrams-guidelines.md).  
  
##  <a name="BasicSteps"></a> Sıralama diyagramları çizmek için temel adımlar  
 Öğeleri sıralı diyagramlar üzerinde tam bir listesi için bkz. [UML sıralı diyagramlar: başvuru](../modeling/uml-sequence-diagrams-reference.md).  
  
> [!NOTE]
>  Herhangi bir modelleme diyagramının oluşturulması için ayrıntılı adımlar açıklanmıştır [Düzenle UML modellerini ve diyagramları](../modeling/edit-uml-models-and-diagrams.md).  
  
#### <a name="to-create-a-sequence-diagram"></a>Bir sıralı diyagram oluşturmak için  
  
1. Üzerinde **mimarisi** menüsünü tıklatın **yeni UML veya katman diyagramı**.  
  
2. Altında **şablonları**, tıklayın **UML sıralı diyagramı**.  
  
3. Diyagrama ad verin.  
  
4. İçinde **modelleme projesine Ekle**, çözümünüzde varolan modelleme projesini seçin veya **yeni modelleme projesi oluşturma**ve ardından **Tamam**.  
  
    Yeni bir sıralı diyagram görünür **sıralı diyagram** araç kutusu. Araç kutusu gereken öğeleri ve bağlayıcıları içerir.  
  
   ![Sıralı Diyagram bölümlerini](../modeling/media/uml-sequence.png "UML_Sequence")  
  
#### <a name="to-draw-a-sequence-diagram"></a>Bir sıralı diyagram çizmek için  
  
1.  Sürükleme **yaşam çizgilerini** (1) öğesinden **araç kutusu** sınıfları, bileşenleri, aktör veya cihazları örneklerini temsil etmek için diyagram üzerine.  
  
    > [!NOTE]
    >  Varolan bir sınıf, arabirim, aktör veya bileşeninden sürükleyerek bir yaşam çizgisi oluşturabilirsiniz **UML Model Gezgini** diyagram üzerine. Bu, seçilen türünün bir örneği temsil eden bir yaşam çizgisi oluşturur.  
  
2.  Yaşam çizgilerini belirli bir hedefe ulaşmak için nasıl işbirliği yaptığını göstermek için iletileri çizin.  
  
     (3, 4, 6, 7) bir ileti oluşturmak için bir ileti Aracı'nı tıklatın. İletinin başlamasını istediğiniz noktada gönderme yaşam çizgisine'a tıklayın ve ardından alma yaşam çizgisine tıklayın.  
  
     Bir yürütme örneği (5), alıcı çizgisinde görünür. Yürütme oluşumunun yöntem yürütme örneği sırasında süreyi temsil eder. Bir yürütme örnekten başlayan diğer mesajları oluşturabilir.  
  
3.  Bilinmeyen olay kaynağından (9) gelir ve yayınlar bir ileti bilinmeyen bir alıcıya (10) göstermek için diyagramda ya da boş alan için bir zaman uyumsuz ileti çizin. Bu iletiler olarak adlandırılan *bulunan iletileri* (9) ve *kayıp iletiler* (10).  
  
    > [!NOTE]
    >  Kayıp veya bulunan iletileri olan yaşam çizgileri grubu taşımak için yaşam çizgilerini taşımadan önce seçmek için aşağıdaki adımları izleyin: Bu yaşam çizgileri veya basılı tutarak çevresinde bir dikdörtgen çizin **CTRL** her yaşam çizgisi tıklatırken anahtar. Kullanırsanız **Tümünü Seç** veya **CTRL**+**A** tüm yaşam çizgilerini seçin ve ardından bunları taşımak için kayıp veya bulunan bu yaşam çizgilerine iliştirilmiş iletiler taşınmayacaktır. Bu senaryo ortaya çıkarsa, bu iletileri ayrı olarak taşıyabilirsiniz.  
  
4.  Aynı bileşen veya sistemin ana her ileti için sıralı diyagramlar çizin.  
  
#### <a name="to-change-the-order-of-messages"></a>İletilerin sırasını değiştirmek için  
  
-   Kendi yaşam çizgisi bir ileti yukarı veya aşağı sürükleyin. Diğer iletiler üzerinden veya içine veya dışına yürütme bloklarıyla sürükleyebilirsiniz.  
  
     \- veya -  
  
-   İletiye tıklayın ve kullanmak **yukarı ok** ve **aşağı ok** ileti pozisyonlarını ayarlamak için anahtarları. Kullanım **SHIFT + Yukarı ok** ve **SHIFT + Aşağı ok** iletilerin sırasını değiştirmek için.  
  
#### <a name="to-move-or-copy-message-sequences-on-the-sequence-diagram"></a>Taşınacak veya kopyalanacak sıralı diyagramda ileti dizileri  
  
1.  İleti (3, 4) sağ tıklayın ve ardından **kopyalama**.  
  
2.  Yürütme oluşumu (5) veya yeni bir ileti gönderilir ve ardından istediğiniz bir yaşam çizgisi (1) sağ **Yapıştır**. İsterseniz, yeni gönderen farklı bir diyagram üzerinde olabilir.  
  
     İletiyi ve onun yan iletilerini bir kopyasını yürütme oluşumu sonuna veya bir yaşam çizgisi sonuna eklenir.  
  
    > [!NOTE]
    >  Yapıştırılan ileti yürütme oluşumuna veya çizgisine sonunda her zaman görünür. Yapıştırdıktan sonra bir önceki konumuna kadar sürükleyin.  
  
#### <a name="to-display-and-edit-the-signature-text-for-a-message"></a>Görüntülemek ve bir ileti imzası metnini düzenlemek için  
  
- Hedef yaşam çizgisi bağlı veya görünür olması için imza metni türlerine eşlenir. Bu görevi gerçekleştirmek için aşağıdaki adımlardan birini gerçekleştirin:  
  
  - Yaşam çizgisine sağ tıklayın ve ardından **Sınıf Oluştur**.  
  
     veya  
  
  - Tuşuna yaşam çizgisi seçin **F4**ve ardından **özellikleri** penceresinde **türü** mevcut bir özellik yazın veya yeni bir tür adını belirtin. İleti etiketi sağ tıklatın ve ardından **oluşturma işlemi**.  
  
    İmza metin ileti görünür. Artık, imza metni düzenleyebilirsiniz. Daha fazla bilgi için [sınıfları ve yaşam çizgilerini](#ClassesAndLifelines).  
  
#### <a name="to-improve-the-layout-of-a-sequence-diagram"></a>Sıralı diyagram düzenini iyileştirmek için  
  
-   Diyagramın boş bir bölümüne sağ tıklayın ve ardından **düzeni yeniden Düzenle**.  
  
-   İşlemi geri almak için tıklayın **Düzenle**ve ardından **geri**.  
  
#### <a name="to-change-the-package-that-owns-the-interaction"></a>Etkileşim sahibi paketini değiştirmek için  
  
1.  İçinde **UML Model Gezgini**, sıralı diyagram görüntüleyen etkileşimi bulun.  
  
    > [!NOTE]
    >  Etkileşim görünmez **UML Model Gezgini** sıralı diyagramda ilk yaşam çizgisini ekleyene kadar.  
  
2.  Etkileşim, pakete sürükleyin.  
  
     \- veya -  
  
     Etkileşim sağ tıklayın ve ardından **Kes**. Pakete sağ tıklayın ve ardından **Yapıştır**.  
  
##  <a name="Simple"></a> Oluşturma ve basit sıralı diyagramları kullanma  
 Sıralı diyagram, basit ve en yaygın olarak kullanılan form yaşam çizgilerini ve iletileri içerir. Bu tür bir diyagram, sisteminiz ve kullanıcılar arasındaki etkileşimler tasarımınızda nesneler arasındaki veya tipik bir dizi açıkça göstermek sağlar. Bu, sık tartışmanıza ve tasarımınızı iletişim kurmanıza yardımcı olması yeterli.  
  
 Basit sıralı diyagram çizmek yaparken dikkate alınması gereken bazı işlemler aşağıda verilmiştir.  
  
### <a name="types-of-message"></a>İleti türleri  
 İletileri oluşturmak için kullanabileceğiniz üç aracı vardır.  
  
-   Kullanım **zaman uyumlu** aracı gönderenin alıcı (3) yanıt döndürmesine olanak beklediği etkileşim açıklar.  
  
     A  **< \<dönüş >>** ok, yürütme oluşumunun sonunda gösterilir. Bu denetimin dönüşü gönderene gösterir.  
  
-   Kullanım **zaman uyumsuz** , gönderen hemen devam edebilir (4) için alıcı beklemenize gerek kalmadan etkileşim açıklamak için aracı.  
  
-   Kullanım **Oluştur** aracı gönderenin alıcı (8) oluşturduğu etkileşim açıklar.  
  
     Bir oluşturma iletisi alıcı aldığı ilk iletiyi olmalıdır.  
  
### <a name="annotating-the-interactions"></a>Etkileşimler yorumlama  
 Dizi hakkında daha ayrıntılı tanımlamak için yerleştirebilirsiniz bir **yorum** diyagram üzerindeki herhangi bir yerde.  
  
 Kullanarak **açıklama bağlantıları**, yaşam çizgileri, yürütme, etkileşim kullanımları ve parçalar açıklamayı bağlayabilirsiniz.  
  
> [!CAUTION]
>  Dizideki belirli bir noktaya açıklama eklemek istediğiniz zaman etkileşim kullanımı, bir yürütme örneği bağlantı veya parçası. Bu durumda, bu dizideki doğru bağlantı noktasına bağlı kalmaz çünkü bir yaşam çizgisi bağlamayın.  
  
 Yorum kullanın:  
  
-   Dizideki önemli anlarda ne elde edildiğini unutmayın. Bu etkileşimlerin amaçlarını görmek için Okuyucular yardımcı olur.  
  
-   Genel amacı, tüm dizinin açıklanmaktadır. İlk yürütme oluşum için yorum ekleyebilir veya eklenmemiş bırakın. Örneğin, "Müşteri öğeleri menüsünden seçtiği ve bir fiyat verildi."  
  
-   Her yaşam çizgisinin sorumluluklarını tanımlayın. Açıklama çizgisine ekleyin. Örneğin, "Manager sıralama müşterinin menü seçenekleri toplar."  
  
-   Özel durumlar veya alternatif olarak gösterilen tipik sıra gerçekleştirilebilecek alternatifleri unutmayın. Örneğin "Müşteri bu dizisi geri kalanını atlamak seçebilirsiniz."  
  
    -   Bu tür bir not daha resmi bir alternatif olarak, parça kullanmayı düşünün. Bkz: [Denetim Yapılarını Parçalarla Açıklama](#Fragments)  
  
## <a name="deciding-the-scope-of-the-diagram"></a>Diyagramın kapsamını karar verme  
 Hangi diyagram göstermek için tasarlanmıştır hakkında açık bir şekilde anlaşılması önemlidir.  
  
#### <a name="initiating-event"></a>Olay başlatma  
 Her diyagram başlatan bir olayın sonucunda etkileşimler dizisini göstermelidir. Bu, örneğin olabilir:  
  
-   Örneğin bir kullanım örneği başlatılıyor, Yemek satın almak için bu Web sayfasını açarak bir kullanıcı.  
  
-   Bir müşteri satın almak isterse bu öğeleri kullanılabilirliğini sorgulama iletiden bir sistem bileşeni diğerine, örneğin.  
  
-   Bir olay durumu, değişikliği tarafından Örneğin, bir öğenin bir eşiğin altına dönülüyor stocks tetiklenir.  
  
#### <a name="level-of-detail"></a>Ayrıntı düzeyi  
 Sıralı diyagramları farklı ayrıntı düzeyleri gösterebilirsiniz. Bağımsız olarak neredeyse iki farklı boyutta ayrıntı düzeyini karar verebilirsiniz:  
  
 Yaşam çizgilerini aşağıdaki ayrıntı düzeylerinden birini temsil edebilir:  
  
- Program kodunda nesneleri, hangi ya mevcut değil veya geliştirdiğiniz.  
  
- Bileşenler veya onların alt cepheleri Ara sunucuları ve diğer bileşenler genellikle atlama.  
  
- Sistem ve harici aktörler  
  
  İletileri bu ayrıntı düzeylerinden birini temsil edebilir:  
  
- Program kodunda API'de yazılım iletileri ya da Web arabirimi.  
  
- İşlem veya alt işlemlerin, kodu ve veritabanı arasında veya örneğin, kullanıcılar ve sistem arasında.  
  
- Kullanım örnekleri - ana etkileşimler kullanıcılar ve sistem arasında.  
  
  Ayrıntılı görünümleri mevcut kodu keşfettiğiniz ya da yeni bir tasarım açıklayan, onu çizmek ve daha az tartışmak çoğunlukla yararlı olur.  
  
## <a name="describing-variations"></a>Değişimleri Açıklama  
 Olayları tek, normal bir dizi diyagramda gösterilmektedir. Hata senaryoları gibi alternatif olasılıkları göstermek istiyorsanız, bu seçeneklerden birini ya da kullanabilirsiniz:  
  
-   Bu senaryoları açıklamak için ayrı bir sıralı diyagramlar çizin  
  
-   Kullanım [Parçalarla Açıklama denetim yapıları](#Fragments) döngüler, alternatifleri ve benzeri gösterilecek.  
  
## <a name="assessing-the-design"></a>Tasarım değerlendirme  
 Diyagram, görevleri onun nesneleri ve bileşenleri arasında dağıtımı değerlendirmek için kullanabilirsiniz. Bu düzenleri görürseniz, yeniden düzenleme göz önünde bulundurun:  
  
-   Bir yaşam çizgisi diğer yaşam çizgilerini yalnızca yordamlarınıza yanıt ise başka her şey için çağrı yapmaya her şeyi gibi görünüyor.  
  
-   Çok sayıda ileti yaşam çizgilerini keser. Her yaşam çizgisi iletileri yalnızca birkaç Komşulardan göndermesi gerektiğini ve komşuları komşuları ile iletişim yok. Genellikle, yalnızca birkaç yerde nerede iletileri yaşam çizgilerini çapraz böylece yaşam çizgilerini düzenlemek olası olmalıdır; ve kesişimlerin olduğu hedef yaşam çizgisi de çapraz yaşam çizgilerini sahip mesaj alışverişi değil.  
  
-   Bazı yaşam çizgilerini, birden fazla görev türünü işlemek için gibi görünüyor. Her çizgisinin aldığı her iletiye yanıt olarak yaptığı işi özetleyen sorumluluklarını tanımlayan bir Sözün cümle bulmak için kolay olmalıdır.  
  
##  <a name="ClassesAndLifelines"></a> Sınıfları ve yaşam çizgileri  
 Yaşam çizgilerini, sıralı diyagramlar, sınıfları veya bileşen arabirimleri örneklerini gösterir. Örneğin, iki yolla yaşam çizgisi adı verebilirsiniz:  
  
|**Bu amaç için**|**Bu biçimi kullanın**|  
|--------------------------|-------------------------|  
|Anonim bir tür örneği.<br /><br /> Her türün yalnızca bir yaşam çizgisi varsa bunu kullanın.|*typeName*|  
|Adlandırılmış bir tür örneği.<br /><br /> Aynı türde birden fazla örneğini içeren bir dizi göstermek istiyorsanız bunu kullanın.|*objectName*:*typeName*|  
  
### <a name="creating-lifelines-from-types"></a>Yaşam çizgilerini türler oluşturma  
 Yeni yaşam çizgileri, tanımladığınız zaten, örneğin bir sınıf diyagramında sınıfları oluşturabilirsiniz.  
  
> [!NOTE]
>  Bu görevi gerçekleştirmeden önce varolan bir sıralı diyagrama sahip olduğunuzdan emin olun.  
  
##### <a name="to-create-a-lifeline-from-an-existing-type"></a>Varolan türden bir yaşam çizgisi oluşturmak için  
  
- Bir sınıf, bileşen veya arabirimi UML Model Gezgini'nden bir sıralama diyagramına sürükleyin.  
  
   \- veya -  
  
  1. Sınıf, bileşen veya arabirimi ilgili diyagram üzerinde sağ tıklayın ve ardından **yaşam çizgisi Oluştur**.  
  
  2. İçinde **yaşam çizgisi Oluştur** iletişim kutusunda, sıralı diyagramı seçin ve ardından **Tamam**.  
  
     Yeni bir adlandırılmış örnek yaşam çizgisi türü sürüklediğiniz türü görüntülenir.  
  
  > [!NOTE]
  >  Bu eylem sayısı dilediğiniz kadar tekrarlayabilirsiniz. Bu örneği farklı adlarla yaşam çizgilerini oluşturur.  
  
##### <a name="to-change-the-type-of-a-lifeline"></a>Bir yaşam çizgisi türünü değiştirmek için  
  
1.  Bir yaşam çizgisine sağ tıklayın ve ardından **özellikleri**.  
  
2.  İçinde **özellikleri** penceresinde **türü** özelliği. Aşağı açılan menüden bir türü seçin veya yeni bir ad yazın.  
  
### <a name="creating-classes-from-lifelines"></a>Çizgilerinden sınıfları oluşturma  
 Bir veya daha fazla sıralı diyagramları oluştururken, sınıf veya arabirim oluşturarak yaşam çizgilerini özetleyebilir.  
  
##### <a name="to-create-a-class-or-interface-from-a-lifeline"></a>Yaşam çizgisinden bir sınıf veya arabirim oluşturmak için  
  
1.  Yaşam çizgisine sağ tıklayın ve ardından **Sınıf Oluştur** veya **oluşturma arabirimi**.  
  
     Yeni sınıfı veya arabirimi UML Model Gezgini'nde görünür.  
  
2.  Sınıf veya arabirim yaşam çizgisinin aldığı her ileti için oluşturma işlemleri:  
  
    1.  Dahil etmek istediğiniz tüm iletileri seçin.  
  
    2.  İletileri birine sağ tıklayın ve ardından **oluşturma yöntemi**.  
  
         Yeni sınıf veya arabirim seçili her ileti için işlemler vardır.  
  
         İşlem adı altındaki her iletiyi oku ve buna görünür **işlemi** iletinin özelliği.  
  
         İleti parametreleri biçiminde içeriyorsa "(parameter: type)", yeni bir işlem parametre listesinde görünürler.  
  
        > [!NOTE]
        >  Sıralı diyagramda yeni iletileri eklerseniz, bu adımı tekrarlamalısınız.  
  
3.  Yeni sınıf veya arabirim ayrıntılı olarak görüntülemek için bir sınıf veya bileşen diyagramı ekleyin.  
  
    1.  Bir sınıf veya bileşen diyagramı oluşturun veya açın.  
  
    2.  Yeni bir sınıf sürükleyin veya alanından arabirim **UML Model Gezgini** sınıf diyagramına.  
  
         Sınıf diyagramında sınıf veya arabirim görünür.  
  
         \- veya -  
  
    3.  Yeni arabiriminden sürükleyin **UML Model Gezgini** üzerine bir bileşen ya da bir bileşen diyagramı bağlantı noktası.  
  
         Arabirim bileşende Lolipop olarak görünür.  
  
### <a name="creating-classes-for-parameters"></a>Parametreler için sınıflar oluşturma  
 Parametreleri bir sıralı diyagram üzerinde iletileri ekleyebilirsiniz. Bir UML sınıf diyagramı, parametre türleri tanımlamak için kullanabilirsiniz.  
  
##  <a name="Multiple"></a> Yeniden kullanılabilir etkileşimi dizileri oluşturma  
 Ayrı bir diyagram, ayırmak istediğiniz veya birkaç diyagramları arasında ortak olan ayrıntı içeren bir dizi tanımlamak için kullanabilirsiniz.  
  
 Başka bir diyagrama ayrıntıları gösteren bir diyagram üzerinde etkileşim kullanımı dikdörtgeni (12) oluşturabilirsiniz.  
  
 Etkileşim kullanımı ona bağlı sıralı diyagramı açmak için çift tıklayın.  
  
#### <a name="to-create-a-reusable-interaction-sequence-from-existing-lifelines"></a>Mevcut çizgilerinden bir yeniden kullanılabilir etkileşimi dizisi oluşturmak için  
  
1.  İçinde **araç kutusu**, tıklayın **etkileşim kullanımı**.  
  
2.  Yeniden kullanılabilir bir dizide dahil etmek istediğiniz yaşam çizgileri arasında sürüklerken sıralı diyagram üzerinde fare düğmesini basılı tutun. Etkileşim kullanımını eklemek istediğiniz dikey konumda başlatın.  
  
     Sıralı diyagramda seçilen yaşam çizgileri arasında etkileşim kullanımı görünür.  
  
3.  Etkileşim kullanımı adına çift tıklayın ve yeniden kullanılabilir bir dizi Bu diyagramda etkisini tanımlamak için yeniden adlandırın.  
  
     \- veya -  
  
     Parametrelere sahip bir işlev çağrısı gibi bir ad yazın.  
  
4.  Etkileşim kullanımı için başka bir sıralı diyagram bağlayın. Etkileşim kullanın ve ardından aşağıdakilerden birini sağ tıklayın:  
  
     Tıklayın **yeni sırası oluştur** yeni bir sıralı diyagram oluşturmak için  
  
     \- veya -  
  
     Tıklayın **dizisi bağlantı** Varolan diyagrama bağlamak için.  
  
     Visual Studio etkileşim kullanımı ve yeni etkileşim sırası arasında bir bağlantı oluşturur.  
  
     Yeni bir sıralı diyagram, çözümünüzde görünür. Bu etkileşim kullanımı oluşturmak için kullanılan yaşam çizgilerini içerir.  
  
    > [!NOTE]
    >  Yalnızca etkileşim kullanımı oluşturmak için kullanılan yaşam çizgilerini dahil edilir. Yeni Diyagram etkileşimi sonra oluşturduğunuz yaşam çizgilerini içermez etkileşim kullanımı artık bunları kapsayan bile kullanın.  
  
#### <a name="to-create-a-reusable-sequence-from-existing-messages"></a>Var olan iletileri yeniden kullanılabilir bir dizi oluşturmak için  
  
-   Taşıyın ve ardından istediğiniz iletiyi sağ **diyagrama Taşı**.  
  
     Visual Studio:  
  
    -   Etkileşim yerini alır, seçili ileti ve tüm yan iletilerini kullanın.  
  
    -   Değiştirilen iletileri için yeni bir sıralı diyagram taşır.  
  
    -   Etkileşim kullanımı ve yeni sıralı diyagram arasında bir bağlantı oluşturur.  
  
#### <a name="to-navigate-to-the-sequence-referenced-by-an-interaction-use"></a>Etkileşim kullanımı tarafından başvurulan dizisi gitmek için  
  
-   Etkileşim kullanımı çift tıklayın.  
  
     \- veya -  
  
     Etkileşim kullanımı sağ tıklayın ve ardından **diziye Git**.  
  
### <a name="creating-a-placeholder-with-an-interaction-use"></a>Bir yer tutucu etkileşim kullanımı ile oluşturma  
 Başka bir diyagrama bağlantılandırmadan etkileşim kullanımı oluşturabilirsiniz. Bu yer tutucu olarak sıralı bir parçası için çalıştırılan ayrıntılarını henüz olan kullanabilirsiniz. İstediğiniz sonuçları göstermek için etkileşim kullanımı adını kullanın.  
  
##  <a name="Collapse"></a> Yaşam çizgileri gruplarını daraltma  
 Grup bir yaşam çizgisi görünür, böylece bir dizi yaşam çizgilerini birlikte daraltabilirsiniz. Bu nesne grubu tek bir bileşen olarak görselleştirmenize yardımcı olur. İletiler ve daraltılmış grubundaki yaşam çizgileri arasında etkileşim kullanımları gizlenir. İletileri ve diğer yaşam çizgilerini içeren etkileşim dizileri gösterilmektedir.  
  
#### <a name="to-collapse-a-group-of-lifelines-together"></a>Bir grup yaşam çizgisini birlikte daraltmak için  
  
1.  İki veya daha fazla yaşam çizgilerini seçin.  
  
2.  Bunlardan birini sağ tıklayın ve ardından **Daralt**.  
  
     Ayrı yaşam çizgileri, tek bir yaşam çizgisi tarafından değiştirilir.  
  
     İletiler ve yalnızca grubun üyeleri içeren bir etkileşim kullanımları gizlenir.  
  
3.  Grubunu yeniden adlandırmak için adına tıklayın.  
  
    > [!NOTE]
    >  Bir grubu genişlettiğinizde grup adı kaybolacak.  
  
#### <a name="to-expand-a-collapsed-group"></a>Daraltılmış bir grubu genişletilemiyor  
  
-   Daraltılmış yaşam çizgisine sağ tıklayın ve ardından **genişletme**.  
  
    > [!NOTE]
    >  Grubun adı yorum grubundan tüm bağlantılar ile birlikte kayıp veya iş öğeleri.  
  
##  <a name="Fragments"></a> Denetim Yapılarını Parçalarla Açıklama  
 Döngüler, dalları ve eşzamanlı işlemeyi sıralı diyagramda tanımlamak için birleştirilmiş parçaları (13) kullanabilirsiniz. Alternatif olarak, etkinlik diyagramı kullanmayı düşünün. Etkinlik diyagramı aktörler arasında iletileri gösterme konusunda kadar kullanışlı değildir, ancak bazı durumlarda döngüleri, dalları ve eşzamanlılık gösterme konusunda daha iyidir.  
  
 Parça türlerinin tam listesi için bkz. [açıklayın denetim akışını UML sıralı diyagramlarda parçalarla](../modeling/describe-control-flow-with-fragments-on-uml-sequence-diagrams.md).  
  
#### <a name="to-create-a-combined-fragment"></a>Birleştirilmiş parça oluşturmak için  
  
1.  Bir ileti ya da aynı yürütme örneği veya yaşam çizgisi başlayan tüm iletiler dizisini seçin.  
  
    > [!NOTE]
    >  İletileri işaret yürütme örnekleri ileti okları seçin.  
  
2.  İletileri birine sağ tıklayın, fareyle **Surround With**ve ardından ihtiyaç duyduğunuz parçanın türüne tıklayın.  
  
     Yeni bir parça görünür. Bu, seçtiğiniz iletileri içerir.  
  
     Birleştirilmiş parça türü birden çok parçaya izin veriyorsa, boş bir parçasını da görünür.  
  
3.  Bir parça korumasını ayarlamak için parça kenarlık sağ tıklayın ve ardından **özellikleri**. Ayarlama **Guard** özelliği.  
  
     Koruma, bir dalda veya bir döngü için koşulu tanımlamak için kullanılır.  
  
4.  Birden çok parçaya sağlayan bir tür için yeni bir parça eklemek, bir parça sınır sağ tıklayın ve işaret **Ekle**. Tıklayın **önce etkileşim işleneni** veya **sonra etkileşim işleneni**.  
  
5.  Yeni iletiler için bir parça eklemek için ileti araçlarını kullanın veya kopyalayıp yapıştırın.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [UML sıralı diyagramlar: başvuru](../modeling/uml-sequence-diagrams-reference.md)   
 [UML modellerini ve diyagramları düzenleme](../modeling/edit-uml-models-and-diagrams.md)   
 [UML Kullanım durumu diyagramları: başvuru](../modeling/uml-use-case-diagrams-reference.md)   
 [UML sınıf diyagramları: başvuru](../modeling/uml-class-diagrams-reference.md)   
 [UML Bileşen Diyagramları: başvuru](../modeling/uml-component-diagrams-reference.md)   
 [UML Bileşen Diyagramları: başvuru](../modeling/uml-component-diagrams-reference.md)   
 [Video: Sıralı diyagramlar kullanarak etkileşimleri tasarlamaktan](http://go.microsoft.com/fwlink/?LinkId=201113)



