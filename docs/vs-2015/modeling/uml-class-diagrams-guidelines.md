---
title: 'UML sınıf diyagramları: Yönergeler | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.teamarch.logicalclassdiagram.overrideoperationsdialog
helpviewer_keywords:
- UML diagrams, class
- diagrams - modeling, class
- UML, class diagrams
- class diagrams - UML
- diagrams - modeling, UML class
ms.assetid: 94dbfd55-b300-4b49-9049-0831ed849486
caps.latest.revision: 56
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: bfd0b13942f5faee82e284c435b7f937d3ae5094
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51726517"
---
# <a name="uml-class-diagrams-guidelines"></a>UML Sınıf Diyagramları: Yönergeler
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio'da kullanabileceğiniz bir *UML sınıf diyagramı* veri türlerini ve ilişkilerini uygulamalarından ayrı olarak açıklamak için. Diyagram, sınıfların uygulamaları yerine mantıksal yönlerine odaklanmak için kullanılır.  
  
 Bir UML sınıf diyagramı oluşturmak için **mimarisi** menüsünde seçin **yeni UML diyagram veya katman diyagramı**.  
  
 Bu özellik, Visual Studio'nun hangi sürümlerinin desteklediğini görmek için bkz: [mimari ve Modelleme Araçları sürüm desteği](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
> [!NOTE]
>  Bu konu UML sınıf diyagramları hakkındadır. Program kodunu görselleştirmek için oluşturabileceğiniz ve kullanabileceğiniz başka tür bir sınıf diyagramı vardır. Bkz: [sınıfları ve türleri tasarlama ve görüntüleme](http://go.microsoft.com/fwlink/?LinkId=142231).  
  
##  <a name="Using"></a> UML sınıf diyagramlarını kullanma  
 Bir UML sınıf diyagramını çeşitli amaçlarla kullanabilirsiniz:  
  
-   Bir sistemde kullanılan ve bileşenleri arasında geçirilen türlerin uygulamadan bağımsız açıklamasını sağlamak için.  
  
     Örneğin, Yemek Siparişi türü iş katmanı içinde .NET kodda, bileşenler arasındaki arabirimlerde XML'de, veritabanı içinde SQL'de ve kullanıcı arabirimi içinde HTML'de uygulanabilir. Bu uygulamalar ayrıntıları bakımından farklı olsa da, Yemek Siparişi ile Menü ve Ödeme gibi diğer türler arasındaki ilişki her zaman aynıdır. UML sınıf diyagramı, uygulamalardan ayrı olarak bu ilişkileri tartışmanıza olanak sağlar.  
  
-   Uygulama ve kullanıcıları arasında iletişim kurmak ve kullanıcı ihtiyaçlarını açıklamak kullanılan terimlerin sözlüğünü açıklığa kavuşturmak amacıyla. Bkz: [kullanıcı gereksinimlerini modelleme](../modeling/model-user-requirements.md).  
  
     Örneğin, bir restoran uygulamasının kullanıcı öykülerini, kullanım örneklerini veya diğer gereksinim açıklamalarını düşünün. Böyle bir açıklamada; Menü, Sipariş, Öğün, Fiyat, Ödeme ve buna benzer terimleri bulabilirsiniz. Bu terimler arasındaki ilişkileri tanımlayan UML sınıf diyagramı çizebilirsiniz. Bu; gereksinim tanımlamalarında, kullanıcı arabiriminde ve yardım belgelerinde tutarsızlık oluşma riskini azaltacaktır.  
  
### <a name="relationship-to-other-diagrams"></a>Diğer Diyagramlarla İlişki  
 Bir UML sınıf diyagramı genellikle kullandıkları türlerin açıklamasını sağlamak için diğer modelleme diyagramları ile birlikte çizilir. Her durumda, türlerin fiziksel gösterimi herhangi bir diyagram tarafından kullanılmaz.  
  
 Etkinlik diyagramı  
  
 Bir Nesne Düğümü'nden geçen veri türü.  
  
 Giriş ve çıkış sabitleyicileri ve etkinlik parametresi düğümlerinin türleri.  
  
 Bkz: [UML etkinlik diyagramları: yönergeler](../modeling/uml-activity-diagrams-guidelines.md).  
  
 Sıralı diyagram  
  
 Parametre türleri ve iletilerin dönüş değerleri.  
  
 Yaşam çizgilerinin türleri. Bir yaşam çizgisi sınıfı alabileceği tüm iletiler için işlemler içermelidir.  
  
 Bkz: [UML sıralı diyagramlar: yönergeler](../modeling/uml-sequence-diagrams-guidelines.md).  
  
 Bileşen diyagramı  
  
 İşlemlerini listeleyen bileşen arabirimleri.  
  
 Bkz: [UML Bileşen Diyagramları: yönergeler](../modeling/uml-component-diagrams-guidelines.md).  
  
 Kullanım örneği diyagramı  
  
 Amaçların açıklamalarında ve kullanım örneğinin adımlarında bahsedilen türler.  
  
 Bkz: [UML Kullanım durumu diyagramları: yönergeler](../modeling/uml-use-case-diagrams-guidelines.md).  
  
##  <a name="BasicSteps"></a> Sınıf diyagramları çizmek için temel adımlar  
 UML sınıf diyagramlarındaki öğeler hakkında başvuru bilgileri için bkz [UML sınıf diyagramları: başvuru](../modeling/uml-class-diagrams-reference.md).  
  
> [!NOTE]
>  Herhangi bir modelleme diyagramının oluşturmaya yönelik ayrıntılı adımlar açıklanmıştır [Düzenle UML modellerini ve diyagramları](../modeling/edit-uml-models-and-diagrams.md).  
  
#### <a name="to-create-a-uml-class-diagram"></a>Bir UML Sınıf diyagramı oluşturmak için  
  
1.  Üzerinde **mimarisi** menüsünde seçin **yeni UML veya katman diyagramı**.  
  
2.  Altında **şablonları**, seçin **UML sınıf diyagramı**.  
  
3.  Diyagrama ad verin.  
  
4.  İçinde **modelleme projesine Ekle**, çözümünüzde varolan modelleme projesini seçin veya **yeni modelleme projesi oluşturma**ve ardından **Tamam**.  
  
     Yeni bir sınıf diyagramı görünür **UMLClass diyagram** araç kutusu. Araç Kutusu gereken öğeleri ve ilişkileri içerir.  
  
#### <a name="to-draw-a-uml-class-diagram"></a>UML Sınıf Diyagramı çizmek için  
  
1.  Bir tür oluşturmak için Seç **sınıfı**, **arabirimi** veya **numaralandırma** araç ve ardından diyagramın boş bir kısmına tıklayın. (Araç Kutusunu göremiyorsanız, CTRL+ALT+X tuşlarına basın.)  
  
2.  Öznitelikler veya işlemler türleri veya sabit listesine değişmez değerler eklemek için **öznitelikleri**, **işlemleri** veya **değişmez değerleri** başlık yazın ve ENTER tuşuna basın.  
  
     Gibi bir imza yazabilirsiniz `f(x:Boolean):Integer`. Bkz: [öznitelikler ve işlemler](#AttributesAndOperations).  
  
     Çeşitli öğeleri hızlıca eklemek için her öğenin sonunda ENTER tuşuna iki kez basın. Listeyi yukarı veya aşağı taşımak için ok tuşlarını kullanabilirsiniz.  
  
3.  Bir türü genişletmek veya daraltmak için üst sol köşesindeki köşeli çift ayraç simgesini seçin. Siz de genişletebileceğiniz ve daraltabileceğiniz **öznitelikleri** ve **işlemleri** bölümünü bir sınıf veya arabirim.  
  
4.  Türler arasındaki ilişkilendirmeler, devralma veya bağımlılık bağlantılarını çizmek için uygun araca tıklayın ve ardından kaynak türüne ve hedef türüne tıklayın.  
  
5.  Bir pakette türleri oluşturmak için kullanarak bir paket oluşturun **paket** aracını ve ardından paket içinde yeni türler ve paketler oluşturun. Ayrıca, türleri kopyalamak için kopyala komutunu kullanabilir ve onları pakete yapıştırabilirsiniz.  
  
6.  Her diyagram, aynı projede diğer diyagramlar arasında paylaşılan modeldeki bir görünümdür. Tam modelin ağaç görünümünü görmek için **görünümü**, **diğer Windows**, **UML Model Gezgini**.  
  
##  <a name="UsingTypes"></a> Sınıfları, arabirimleri ve sabit listelerini kullanma  
 Araç kutusunda kullanılabilir olan standart üç tür sınıflandırıcı vardır. Bunlar olarak adlandırılır *türleri* bu belge boyunca.  
  
 ![Bir sınıf, bir numaralandırma ve bir arabirim](../modeling/media/uml-classguidetypes.png "UML_ClassGuideTypes")  
  
- Kullanım **sınıfları** birçok amaç için veri veya nesne türlerini temsil etmek için (1).  
  
- Kullanım **arabirimleri** (2) saf arabirimler ve iç uygulamaları olan somut sınıflar arasında ayırt etmek için sahip olduğu bir bağlam içinde. Bu fark, diyagramın amacının bir yazılım uygulamasını açıklamak olduğunda yararlıdır. Bu, edilgen veri tanımladığınız zaman veya kullanıcı gereksinimlerini tanımlamak için kavramlar tanımladığınız yerde daha az yararlıdır.  
  
- Kullanım bir **numaralandırma** (örneğin sınırlı sayıda değişmez değeri olan bir türü temsil etmek için 3) `Stop` ve `Go`.  
  
  -   Sabit listesine değişmez değerleri ekleyin. Her birine ayrı bir ad verin.  
  
  -   İsterseniz her değişmez değer için sayısal bir değer de sağlayabilirsiniz. Açık listesinde değişmez değerin kısayol menüsünü seçin **özellikleri**, bir sayı yazın **değer** alanındaki **özellikleri** penceresi.  
  
  Her türe benzersiz bir ad verin.  
  
### <a name="getting-types-from-other-diagrams"></a>Diğer Diyagramlardan Türleri Alma  
 Diğer diyagramdaki türleri UML sınıf diyagramınızda görünür yapabilirsiniz.  
  
 UML Sınıf Diyagramı  
  
 Bir sınıfı birden fazla UML sınıf diyagramında görünür yapabilirsiniz. Bir diyagram üzerinde sınıf oluşturduğunuz zaman sınıfı sürükleyin **UML Model Gezgini** diğer diyagram üzerine.  
  
 Bu, her diyagramın belirli bir ilişki grubuna odaklanmasını istiyorsanız yararlıdır.  
  
 Örneğin, bir diyagramdaki Yemek Siparişi ve restoran Menüsü arasındaki ilişkilendirmeleri ve diğer diyagramdaki Yemek Siparişi ve Ödeme arasındaki ilişkilendirmeleri gösterebilirsiniz.  
  
 Bileşen Diyagramı  
  
 Bileşen diyagramında bileşenlerdeki arabirimleri tanımladıysanız, bir arabirimden sürükleyebilirsiniz **UML Model Gezgini** sınıf diyagramına sürükleyebilirsiniz. Sınıf diyagramında, arabirimin içerdiği yöntemleri tanımlayabilirsiniz.  
  
 Bkz: [UML Bileşen Diyagramları: yönergeler](../modeling/uml-component-diagrams-guidelines.md).  
  
 UML Sıralı Diyagramı  
  
 Sınıfları ve arabirimleri yaşam çizgilerinden sıralı diyagramda oluşturabilirsiniz ve sınıftan sürükleyin **UML Model Gezgini** UML sınıf diyagramına. Sıralı diyagramdaki her yaşam çizgisi bir nesnenin, bileşenin veya aktörün bir örneğini gösterir.  
  
 Yaşam çizgisinden bir sınıf oluşturmak için Yaşam çizgisinin kısayol menüsünü açın ve ardından **Sınıf Oluştur** veya **oluşturma arabirimi**. Bkz: [UML sıralı diyagramlar: yönergeler](../modeling/uml-sequence-diagrams-guidelines.md).  
  
##  <a name="AttributesAndOperations"></a> Öznitelikler ve işlemler  
 Bir öznitelik (4) bir türün her örneğinin sahip olabileceği adlandırılmış değerdir. Bir özniteliğe erişme, örneğin durumunu değiştirmez.  
  
 Bir işlem (5), türün örneklerinin gerçekleştirebildiği bir yöntem veya işlevdir. Bir değer döndürebilir. Varsa, **isQuery** özelliği true ise, örneğinin durumunu değiştiremezsiniz.  
  
 Bir türe öznitelik veya işlem eklemek için türün kısayol menüsünü açın, **Ekle**ve ardından **özniteliği** veya **işlemi**.  
  
 Özelliklerini görmek için özniteliğin veya işlemin kısayol menüsünü açın ve ardından **özellikleri**. Özellikleri görünür **özellikleri** penceresi.  
  
 Bir işlemin parametrelerinin özelliklerini görmek için <strong>[...]</strong> içinde **parametreleri** özelliği. Yeni özellikler iletişim kutusu görünür.  
  
 Ayarlayabileceğiniz tüm özellikler hakkında ayrıntılı bilgi için bkz.  
  
-   [UML sınıf diyagramlarındaki özniteliklerin özellikleri](../modeling/properties-of-attributes-on-uml-class-diagrams.md)  
  
-   [UML sınıf diyagramlarındaki işlemlerin özellikleri](../modeling/properties-of-operations-on-uml-class-diagrams.md)  
  
### <a name="types-of-attributes-and-operations"></a>Öznitelik ve İşlemlerin Türleri  
 Her *türü* bir öznitelik veya işlem ve her bir parametre türü, aşağıdakilerden biri olabilir:  
  
- **(hiçbiri)**  -Türü önceki iki gt;(yok) imzada belirtilmemiş bırakabilirsiniz (`:`).  
  
- Standart basit türlerden biri: **Boole**, **tamsayı**, **dize**.  
  
- Modelinizde tanımlı bir tür.  
  
- Şablon yazılmış bir şablon türünün parametreli değeri\<parametresi >. Bkz: [şablonu türleri](#Templates).  
  
  Henüz modelinizde tanımlamadığınız bir türün adını da yazabilirsiniz. Adı altında listelenen **belirtilmemiş türler** UML Model Gezgini'nde.  
  
> [!NOTE]
>  Modelinizde o adın sınıfını veya arabirimini daha sonra tanımlarsanız, eski öznitelikler ve işlemler hala Belirtilmemiş Türler'deki öğeye başvuracaktır. Yeni sınıfa başvurmak için onları değiştirmek istiyorsanız, her özniteliği veya işlemi ziyaret etmeli ve aşağı açılan menüden yeni sınıfı seçerek türü sıfırlamalısınız.  
  
#### <a name="multiple-types"></a>Çoklu Türler  
 Herhangi bir öznitelik, işlem veya parametre türünün çokluğunu ayarlayabilirsiniz.  
  
 İzin verilen değerler aşağıdaki gibidir:  
  
 `[1]`  
  
 Verilen türden bir değer. Bu varsayılandır.  
  
 `[0..1]`  
  
 **Null** veya verilen türden bir değer.  
  
 `[*]`  
  
 Herhangi bir sayıdaki verilen türden örneklerin koleksiyonu.  
  
 `[1..*]`  
  
 Verilen türden en az bir örnekli koleksiyon.  
  
 `[n..m]`  
  
 Koleksiyonu arasında `n` ve `m` verilen tür örneği.  
  
 Çokluk 1'den fazla ise, bu özellikleri de ayarlayabilirsiniz:  
  
-   **IsOrdered** - true, koleksiyonun tanımlanmış bir düzeni vardır.  
  
-   **IsUnique** - true, koleksiyonda yinelenen değerler varsa.  
  
### <a name="visibility"></a>Görünürlük  
 *Görünürlük* özniteliğin veya işlemin sınıf dışından erişilebilir olup olmadığını gösterir. İzin verilen değerler aşağıdaki gibidir:  
  
 **Public**  
  
 **+**  
  
 Diğer tüm türlerden erişilebilir.  
  
 **Private**  
  
 **-**  
  
 Yalnızca bu türün iç tanımı için erişilebilir.  
  
 **Paket**  
  
 **~**  
  
 Yalnızca bu türü içeren paketin içinde ve onu açıkça içeri aktaran herhangi bir pakette erişilebilir. Bkz: [ad alanlarını ve paketleri tanımlama](#Packages).  
  
 **Protected**  
  
 **#**  
  
 Yalnızca bu tür ve ondan devralınan türler için erişilebilir. Bkz: [devralma](#Inheritance).  
  
### <a name="setting-the-signature-of-an-attribute-or-an-operation"></a>Bir Özniteliğin veya İşlemin İmzasını Ayarlama  
 Bir özniteliğin veya işlemin imzası; onun görünürlüğünü, adını, parametrelerini (işlemler için) ve türünü içeren özellikler koleksiyonudur.  
  
 İmzayı doğrudan diyagramda yazabilirsiniz. Seçmek için özniteliğe veya işleme tıklayın ve ardından ona tekrar tıklayın.  
  
 İmzayı şu biçimde yazın:  
  
```  
visibility attribute-name : Type  
```  
  
 \- veya -  
  
```  
visibility operation-name (parameter1 : Type1, ...) : Type  
```  
  
 Örneğin:  
  
```  
+ AddItem (item : MenuItem, quantity : Integer) : Boolean  
```  
  
 Görünürlüğün kısa biçimini kullanın. Varsayılan değer `+` (Genel).  
  
 Her tür modelde tanımladığınız türlere, Tamsayı veya Dize gibi standart türlere veya henüz tanımlamadığınız yeni türün adına sahip olabilir.  
  
> [!NOTE]
>  Bir parametre listesinde türü içermeyen bir ad yazarsanız, bu parametrenin türü yerine adını gösterir. Bu örnekte, MenuItem ve Tamsayı belirtilmemiş türlere sahip iki parametrenin adı olur:  
>   
>  `AddItem(MenuItem, Integer) /* parameter names, not types! */`  
  
 Bir imzada türün çokluğunu ayarlamak için tür adından sonra köşeli ayraçlar içinde çokluğu yazın, örneğin:  
  
```  
+ AddItems (items : MenuItem [1..*])  
+ MenuContent : MenuItem [*]  
```  
  
 Öznitelik veya işlem statikse, adı imzada altı çizili olarak görünecektir. Soyutsa, ad italik yazı tipinde görünecektir.  
  
 Ancak, yalnızca ayarlayabilirsiniz **Is Static** ve **soyut** özelliklerinde **özellikleri** penceresi.  
  
#### <a name="full-signature"></a>Tam imza  
 Özniteliğini veya işlemin imzasını düzenlediğinizde, bazı ek özellikler çizginin sonunda ve her parametreden sonra görünebilir. Küme ayraçları {…} içinde görünürler. Bu özellikleri düzenleyebilir veya ekleyebilirsiniz. Örneğin:  
  
```  
+ AddItems (items: MenuItem [1..*] {unique, ordered})  
+ GetItems (filter: String) : MenuItem [*] {ordered, query}  
```  
  
 Bu özellikler aşağıdaki gibidir:  
  
 `unique`  
  
 **Benzersiz**  
  
 Koleksiyonda yinelenen değerler yoktur. 1'den büyük çokluktaki türlere uygulanır.  
  
 `ordered`  
  
 **Sıralı**  
  
 Koleksiyon bir dizidir. False ise, kesin bir ilk öğe yoktur. 1'den büyük çokluktaki türlere uygulanır.  
  
 `query`  
  
 **Sorgu**  
  
 İşlem, örneğinin durumunu değiştirmez. Yalnızca işlemlere uygulanır.  
  
 `/`  
  
 **Türetilmiş**  
  
 Öznitelik, diğer özniteliklerin veya ilişkilendirmelerin değerlerinden hesaplanır.  
  
 "/" özniteliğin adından önce görünür. Örneğin:  
  
```  
/TotalPrice: Integer  
```  
  
 Genellikle tam imza, yalnızca siz onu düzenlerken diyagramda görünür. Düzenlemeyi bitirdiğinizde, ek özellikler gizlenir. Tam imzayı her zaman görmek istiyorsanız, türün kısayol menüsünü açın ve ardından **tam imzayı Göster**.  
  
##  <a name="Associations"></a> İlişkilendirmeleri çizme ve kullanma  
 Bağlantının yazılımda nasıl uygulandığını dikkate almaksızın, iki öğe arasındaki herhangi bir türden bağlantıyı göstermek için bir ilişkilendirme kullanın. Örneğin; C#'ta işaretçiyi, veritabanındaki ilişkiyi veya XML dosyasının bir bölümünden diğerine yapılan çapraz başvuruyu göstermek için ilişkilendirme kullanabilirsiniz. Gerçek dünyada, dünya ve güneş gibi nesneler arasındaki ilişkilendirmeyi gösterebilir. İlişkilendirme bağlantının nasıl gösterildiğini değil, yalnızca bilginin var olduğunu söyler.  
  
### <a name="properties-of-an-association"></a>Bir İlişkilendirmenin Özellikleri  
 Bir ilişkilendirme oluşturduktan sonra, özelliklerini ayarlayın. İlişkilendirme için kısayol menüsünü açın ve ardından **özellikleri**.  
  
 Bir bütün olarak ilişkilendirmenin özelliklerine ek olarak her *rol*, diğer bir deyişle ilişkilendirmenin her ucundaki kendi bazı özelliklere sahiptir. Bunları görüntülemek için genişletin **ilk rol** ve **ikinci rol** özellikleri.  
  
 Her rolün bazı özellikleri doğrudan diyagramda görülebilir. Bunlar şu şekildedir:  
  
- Rol adı. Bu, diyagramda ilişkilendirmenin uygun sonunda görünür. Diyagramda veya içinde ayarlayabilirsiniz **özellikleri** penceresi.  
  
- **Çokluk**, bunun varsayılan **1**. Bu da diyagramda ilişkilendirmenin uygun sonunun yakınında görünür.  
  
- **Toplama**. Bu, bağlayıcının bir ucunda elmas şeklinde görünür. Bunu, toplama rolündeki örneklerin diğerlerinin örneklerini içerdiğini veya onlara sahip olduğunu göstermek için kullanabilirsiniz.  
  
- **Gezinebilir**. Yalnızca tek bir rol için true ise, gezinebilir yönde bir ok görünür. Bunu, yazılımda bağlantıların ve veritabanı ilişkilerinin gezinebilirliğini göstermek için kullanabilirsiniz.  
  
  Bunlar ve diğer özelliklerin tam ayrıntıları için bkz. [UML İlişkilendirmelerin Özellikleri sınıf diyagramları](../modeling/properties-of-associations-on-uml-class-diagrams.md).  
  
### <a name="navigability"></a>Gezinebilirlik  
 Bir ilişkilendirme çizdiğinizde, ilişkilendirmenin bir ucunda, ilişkilendirmenin o yönde gezilebilir olduğunu gösteren bir ok olur. Bu, sınıf diyagramınız yazılım sınıflarını ve ilişkilendirmeler işaretçileri veya başvuruları temsil ediyorsa yararlıdır. Ancak varlıkları ve ilişkileri ya da iş kavramlarını göstermek için bir sınıf diyagramı kullandığınızda, gezinebilirliği göstermek pek uygun olmayacaktır. Bu durumda, oklar olmadan ilişkilendirmeler çizmeyi tercih edebilirsiniz. Bunu ayarlayarak yapabilirsiniz **gezilebilir** özelliği True olarak ilişkilendirmenin her iki ucunda. Bunu kolaylaştırmak için kod örneğini indirebilirsiniz [etki alanı UML modelleme](http://code.msdn.microsoft.com/UML-Domain-Modeling-6df6f7f4).  
  
### <a name="attributes-and-associations"></a>Öznitelikler ve İlişkilendirmeler  
 Bir ilişkilendirme, bir özniteliği göstermenin resimsel bir yoludur. Örneğin, Menü türünde bir öznitelik ile Restoran sınıfı oluşturmak yerine, Restoran'dan Menü'ye bir ilişkilendirme çizebilirsiniz.  
  
 Her öznitelik adı bir rol adı olur. Sahip olan türden ilişkilendirmenin karşı ucunda görünür. , Örneğin, bakmak `myMenu` çizimde.  
  
 Genellikle, yalnızca diyagramda çizemeyeceğiniz temel türler gibi türler için öznitelikleri kullanmak daha uygundur.  
  
 ![Eşdeğer ilişkilendirme ve öznitelikler](../modeling/media/uml-classguideattrib.png "UML_ClassGuideAttrib")  
  
##  <a name="Inheritance"></a> Devralma  
 Kullanım **devralma** aşağıdaki ilişkileri oluşturmak için aracı:  
  
- A *Genelleştirme* uzmanlaşmış bir türü ve genel bir tür arasındaki ilişki  
  
   \- veya -  
  
- A *gerçekleştirme* bir sınıf ve uyguladığı arabirimin arasındaki ilişki.  
  
  Devralma ilişkilerinde döngüler oluşturamazsınız.  
  
### <a name="generalization"></a>Genelleştirme  
 Genelleştirme, özelleştirilmiş veya türetilmiş türün öznitelikleri, işlemleri ve genel veya taban türün ilişkilendirmelerini devralması anlamına gelir.  
  
 Genel tür, ilişkinin ok ucu sonunda görünür.  
  
 Devralınan işlemler ve öznitelikler genellikle özelleştirilmiş türlerde gösterilmez. Ancak, devralınan işlemleri özelleştirilmiş türün işlemler listesine ekleyebilirsiniz. Bu, özelleştirilmiş türdeki işlemlerin bazı özelliklerini geçersiz kılmak veya uygulanan kodun bunu yapmasını göstermek istiyorsanız yararlıdır.  
  
##### <a name="to-override-an-operations-definition-in-a-specializing-type"></a>Özelleştirilmiş türden bir işlemin tanımını geçersiz kılmak için  
  
1. Genelleştirme ilişkisine tıklayın.  
  
    Vurgulu olarak görünür ve yanında bir Eylem etiketi görünür.  
  
2. Eylem etiketine ve ardından **işlemleri geçersiz kıl**.  
  
    **İşlemleri geçersiz kıl** iletişim kutusu görüntülenir.  
  
3. Özelleştirilmiş türde görünür ve ardından istediğiniz işlemleri seçin **Tamam**.  
  
   Şimdi seçtiğiniz işlemler özelleştirilmiş türde görünür.  
  
### <a name="realization"></a>Gerçekleştirme  
 Gerçekleştirme, bir sınıfın arabirim tarafından belirtilen öznitelikler ve işlemleri uygulaması anlamına gelir. Arabirim bağlayıcının ok ucundadır.  
  
 Bir gerçekleştirme bağlayıcısı oluşturduğunuz zaman, arabirim işlemleri otomatik olarak gerçekleştirilmiş sınıfta çoğaltılır. Arabirime yeni işlemler eklerseniz, arabirimin gerçekleştirme sınıflarında çoğaltılırlar.  
  
 Gerçekleştirme ilişkisi oluşturduktan sonra, lolipop gösterimine dönüştürebilirsiniz. İlişkiye sağ tıklayın ve seçin **Lolipop olarak göster**.  
  
 Bu, bir sınıfın uyguladığı arabirimleri sınıf diyagramları ile gerçekleştirme bağlantılarını karıştırmadan göstermenize olanak sağlar. Ayrıca ayrı diyagramlarda gerçekleştirdiğiniz arabirim ve sınıfları da gösterebilirsiniz.  
  
 ![Bağlayıcı ve lollipop ile gösterilen gerçekleştirme](../modeling/media/uml-classguiderealize.png "UML_ClassGuideRealize")  
  
##  <a name="Templates"></a> Şablon türleri  
 Diğer türler veya değerler tarafından parametrelendirilebilen genel veya şablon türü tanımlayabilirsiniz.  
  
 Örneğin, anahtar ve değer türleri tarafından parametrelendirilmiş genel bir Sözlük oluşturabilirsiniz:  
  
 ![Şablon sınıfının iki parametre ile](../modeling/media/uml-classguidetemplate1.png "UML_ClassGuideTemplate1")  
  
#### <a name="to-create-a-template-type"></a>Bir şablon türü oluşturmak için  
  
1. Bir sınıf veya arabirim oluşturun. Bu, sizin şablon türünüz olacaktır. Örneğin, buna göre ad `Dictionary`.  
  
2. Yeni türün kısayol menüsünü açın ve ardından **özellikleri**.  
  
3. İçinde **özellikleri** penceresinde tıklayın **[...]**  içinde **şablon parametreleri** alan.  
  
    **Şablon parametre Koleksiyonu Düzenleyicisi** iletişim kutusu görüntülenir.  
  
4. Seçin **ekleme**.  
  
5. Örneğin, name özelliği şablon türünüz için parametre adına ayarlayın `Key`.  
  
6. Ayarlama **parametre türü**. Varsayılan değer **sınıfı**.  
  
7. Belirli bir taban sınıfın yalnızca türetilmiş sınıflarını kabul etmek için parametre istiyorsanız ayarlayın **kısıtlanmış değer** istediğiniz temel sınıf.  
  
8. Ardından, ihtiyacınız kadar parametre ekleyin **Tamam**.  
  
9. Diğer sınıflar için yaptığınız gibi öznitelikleri ve işlemleri şablon türüne ekleyin.  
  
     Türü olan parametreleri kullanabilirsiniz **sınıfı**, **arabirimi** veya **numaralandırma** öznitelikler ve işlemler tanımında. Parametre sınıflarını kullanarak örneğin, `Key` ve `Value`, bu işlemde tanımlayabilirsiniz `Dictionary`:  
  
     `Get(k : Key) : Value`  
  
     Bir parametre türü kullanabileceğiniz **tamsayı** çoklukta bağımlı olarak. Örneğin, en büyük parametre tamsayısı öznitelik olarak çokluğu tanımlamak için kullanılabilir `[0..max]`.  
  
   Şablon türlerini oluşturduğunuz zaman, onları şablon bağlarını tanımlamak için kullanabilirsiniz:  
  
   ![Bir sınıf bağlı sözlük şablonundan](../modeling/media/uml-classguidetemplate2.png "UML_ClassGuideTemplate2")  
  
#### <a name="to-use-a-template-type"></a>Bir şablon türü kullanmak için  
  
1.  Örneğin, yeni bir tür oluşturma `AddressTable`.  
  
2.  Yeni türün kısayol menüsünü açın ve ardından **özellikleri**.  
  
3.  İçinde **şablon bağlama** şablon türünün, örneğin özelliği, select `Dictionary`, aşağı açılan listeden.  
  
4.  Genişletin **şablon bağlama** özelliği.  
  
     Şablon türünün her parametresi için bir satır görünür.  
  
5.  Her parametreyi uygun bir değere ayarlayın. Örneğin, `Key` parametresine bir sınıf adlı `Name`.  
  
##  <a name="Packages"></a> Paketleri  
 Bir UML sınıf diyagramında paketleri görüntüleyebilirsiniz. Bir paket diğer model öğeleri için bir kapsayıcıdır. Bir paket içinde herhangi bir öğe oluşturabilirsiniz. Diyagramda, paketi taşıdığınız zaman paket içindeki öğeler de taşınacaktır.  
  
 Paketin içeriğini gizlemek veya göstermek için daralt/genişlet denetimini kullanabilirsiniz.  
  
 Bkz: [paketleri ve ad alanlarını tanımlama](../modeling/define-packages-and-namespaces.md).  
  
##  <a name="generating"></a> UML sınıf diyagramlarından kod üretme  
 UML sınıf diyagramında sınıfları uygulamaya başlamak için C# kodu oluşturabilir veya kod oluşturma için şablonları özelleştirebilirsiniz. Sağlanan C# şablonlarını kullanarak kod oluşturmaya başlamak için:  
  
-   Diyagram veya öğenin kısayol menüsünü açın seçin **kod üret**ve ardından gerekli özellikleri ayarlayın.  
  
     Bu özellikleri ayarlama ve sağlanan şablonları özelleştirme hakkında daha fazla bilgi için bkz. [UML sınıf diyagramlarından kod oluşturma](../modeling/generate-code-from-uml-class-diagrams.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [UML modellerini ve diyagramları düzenleme](../modeling/edit-uml-models-and-diagrams.md)   
 [UML sınıf diyagramları: başvuru](../modeling/uml-class-diagrams-reference.md)   
 [Kullanıcı gereksinimlerini modelleme](../modeling/model-user-requirements.md)   
 [UML Bileşen Diyagramları: başvuru](../modeling/uml-component-diagrams-reference.md)   
 [UML sıralı diyagramlar: başvuru](../modeling/uml-sequence-diagrams-reference.md)   
 [UML Kullanım durumu diyagramları: başvuru](../modeling/uml-use-case-diagrams-reference.md)   
 [UML Bileşen Diyagramları: Başvuru](../modeling/uml-component-diagrams-reference.md)



