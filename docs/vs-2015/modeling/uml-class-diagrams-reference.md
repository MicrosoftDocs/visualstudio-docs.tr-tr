---
title: 'UML sınıf diyagramları: Başvuru | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.teamarch.common.generalization.properties
- vs.teamarch.logicalclassdiagram.toolbox
- vs.teamarch.UMLModelExplorer.association
- vs.teamarch.common.unspecifiedtype.properties
- vs.teamarch.logicalclassdiagram.diagram
- vs.teamarch.UMLModelExplorer.logicalclassdiagram
- vs.teamarch.UMLModelExplorer.generalization
- vs.teamarch.common.unspecifiedtype
helpviewer_keywords:
- UML diagrams, class
- diagrams - modeling, class
- UML, class diagrams
- class diagrams - UML
- diagrams - modeling, UML class
ms.assetid: b7c88be0-0d86-4d65-af74-f37e8812d20f
caps.latest.revision: 43
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 4f3a4fe9949236045238688a9edcd5eef911efb8
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51741058"
---
# <a name="uml-class-diagrams-reference"></a>UML Sınıf Diyagramları: Başvuru
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bir UML sınıf diyagramı nesne ve hem iç hem de kullanıcılar ile iletişim yapıları, uygulamanız tarafından kullanılan bilgileri açıklar. Bu, belirli bir uygulamaya başvuru olmadan bilgiler açıklanmaktadır. Alt sınıflar ve ilişkiler, veritabanı tablolarını, XML düğümüyle veya yazılım nesnelerin bileşimleri gibi pek çok yolla uygulanabilir.  
  
> [!NOTE]
>  Bu konu UML sınıf diyagramları hakkındadır. Başka tür bir sınıf diyagramı, program kodunu görselleştirmek için kullanılan .NET sınıf diyagramı vardır. Daha fazla bilgi için [tasarlama ve görüntüleme sınıfları ve türleri](http://go.microsoft.com/fwlink/?LinkId=142231).  
  
 Bir UML sınıf diyagramı oluşturmak için **mimarisi** menüsünde seçin **yeni UML veya katman diyagramı**. UML sınıf diyagramları çizmek hakkında daha fazla bilgi için bkz. [UML sınıf diyagramları: yönergeler](../modeling/uml-class-diagrams-guidelines.md). Modelleme diyagramları çizmek ve oluşturma hakkında daha fazla bilgi için bkz. [Düzenle UML modellerini ve diyagramları](../modeling/edit-uml-models-and-diagrams.md).  
  
 Bu özellik, Visual Studio'nun hangi sürümlerinin desteklediğini görmek için bkz: [mimari ve Modelleme Araçları sürüm desteği](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
## <a name="reading-class-diagrams"></a>Sınıf diyagramları okuma  
 Bu bölümde yer alan tabloda bir UML sınıf diyagramında gördüğünüz öğeleri açıklar. Bu öğelerin özellikleri hakkında daha fazla bilgi için aşağıdaki konulara bakın:  
  
- [UML sınıf diyagramlarındaki türlerin özellikleri](../modeling/properties-of-types-on-uml-class-diagrams.md)  
  
- [UML sınıf diyagramlarındaki özniteliklerin özellikleri](../modeling/properties-of-attributes-on-uml-class-diagrams.md)  
  
- [UML sınıf diyagramlarındaki işlemlerin özellikleri](../modeling/properties-of-operations-on-uml-class-diagrams.md)  
  
- [UML sınıf diyagramlarındaki ilişkilendirmelerin özellikleri](../modeling/properties-of-associations-on-uml-class-diagrams.md)  
  
  ![Üç ilişkileri gösteren ve Özellikler sınıfları](../modeling/media/uml-classovreading.png "UML_ClassOvReading")  
  
| **Şekil** |       **Öğe**        |                                                                                                                                                             **Açıklama**                                                                                                                                                              |
|-----------|--------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|     1.     |        **Sınıfı**         |                                                           Yapısal veya davranışsal özellikleri paylaşan nesnelerin tanımıdır. Daha fazla bilgi için [özellikleri türleri UML sınıf diyagramları](../modeling/properties-of-types-on-uml-class-diagrams.md).                                                            |
|     1.     |        Sınıflandırıcısı        |                                                                                                             Bir sınıf, arabirim veya numaralandırma genel adı. Bileşenler, kullanım örnekleri ve aktörler de sınıflandırıcıdır.                                                                                                             |
|     2     | Daraltma / genişletme denetimi |                                                                                         Sınıflandırıcı ayrıntılarını göremiyorsanız, genişletici sınıflandırıcı sol konumunda tıklayın. Öğesine tıklamanız her bir kesim üzerinde [+] olabilir.                                                                                         |
|     3     |      **Öznitelik**       |   Her bir sınıflandırıcı örneğine bağlı türü belirtilmiş bir değer.<br /><br /> Bir öznitelik eklemek için tıklatın **öznitelikleri** bölüm ve tuşuna **ENTER**. Öznitelik imzası yazın. Daha fazla bilgi için [özelliklerini öznitelikleri UML sınıf diyagramları](../modeling/properties-of-attributes-on-uml-class-diagrams.md).   |
|     4     |      **İşlemi**       | Bir yöntem veya işlev, sınıflandırıcı örneklerinin tarafından gerçekleştirilebilir. Bir işlem eklemek için tıklatın **işlemleri** bölüm ve tuşuna **ENTER**. İşlemin imzasını yazın. Daha fazla bilgi için [UML işlemlerin özellikleri sınıf diyagramları](../modeling/properties-of-operations-on-uml-class-diagrams.md). |
|     5     |     **İlişkilendirme**      |                                                                  Üyeleri, iki sınıflandırıcı arasındaki ilişki. Daha fazla bilgi için [UML İlişkilendirmelerin Özellikleri sınıf diyagramları](../modeling/properties-of-associations-on-uml-class-diagrams.md).                                                                   |
|    5a     |     **Toplama**      |                                                                                                    Paylaşılan sahiplik ilişkisini gösteren bir ilişkilendirmedir. **Toplama** özelliği sahip rolünün **paylaşılan**.                                                                                                     |
|    5b     |     **Oluşturma**      |                                                                                                      Bütün parça ilişkisini gösteren bir ilişkilendirmedir. **Toplama** özelliği sahip rolünün **bileşik**.                                                                                                      |
|     6     |   **İlişkilendirme adı**   |                                                                                                                                         Bir ilişkilendirmenin adı. Ad boş bırakılabilir.                                                                                                                                          |
|     7     |      **Rol adı**       |                       Diğer bir deyişle, bir ilişki sonu bir rolün adı. İlişkili nesneye başvurmak için kullanılabilir. Önceki çizimde, herhangi bir sırada `O`, `O.ChosenMenu` kendi ilişkili menü.<br /><br /> Her rol ilişkilendirmenin özellikleri altında listelenen, kendi özelliklerine sahiptir.                       |
|     8     |     **Çokluk**     |                                         Bu nesnelerin kaç son gösterir diğer her nesneye bağlı. Örnekte, her bir Order tam olarak bir menüye bağlanması gerekir.<br /><br /> **\\**\* yapılabilir bağlantılarının sayısı için üst sınır yoktur anlamına gelir.                                         |
|     9     |    **Genelleştirme**    |  *Belirli* sınıflandırıcının kendi tanımının bir parçası devralan *genel* sınıflandırıcı. Bağlayıcının ok sonunda genel sınıflandırıcıdır. Öznitelikler, ilişkileri ve işlemleri belirli bir sınıflandırıcının tarafından devralınır.<br /><br /> Kullanım **devralma** Genelleştirme iki sınıflandırıcı arasındaki oluşturmak için aracı.   |
  
 ![Arabirim ve sabit listesi içeren paket](../modeling/media/uml-classovpackage.png "UML_ClassOvPackage")  
  
|Şekil|Öğe|Açıklama|  
|-----------|-------------|-----------------|  
|10|**Arabirimi**|Dışarıdan görünen bir nesne davranışını parçası tanımı. Daha fazla bilgi için [özellikleri türleri UML sınıf diyagramları](../modeling/properties-of-types-on-uml-class-diagrams.md).|  
|11|**Sabit listesi**|Sınıflandırıcı değişmez değerler kümesi içerir.|  
|12|**Paket**|Sınıflandırıcılar, ilişkilendirmeler, Eylemler, yaşam çizgileri, bileşenleri ve paketleri grubu. Bir mantıksal bir sınıf diyagramı üye sınıflandırıcılar ve paketleri paket içinde bulunan gösterir.<br /><br /> Adları içindeki paketleri kapsamlı şekilde **Class1** içinde **Paket1** den farklıdır **Class1** , paketin dışında. Paket adı bir parçası olarak görünür **tam adı** içeriğini özellikleri.<br /><br /> Ayarlayabileceğiniz **bağlantılı paket** özelliği bir pakete başvurmak için herhangi bir UML diyagram. Diyagramda oluşturduğunuz tüm öğeleri ardından paketinin bir parçası haline gelir. Pakette altında görünür **UML Model Gezgini**.|  
|13|**İçeri Aktar**|Belirten bir paketin başka tüm tanımlarını içeren paketleri arasındaki ilişki.|  
|14|**Bağımlılık**|Ok ucu sonunda sınıflandırıcı değiştirilirse, tanım veya bağımlı sınıflandırıcı uygulama değişebilir.|  
  
 ![Bağlayıcı ve lollipop ile gösterilen gerçekleştirme](../modeling/media/uml-classovrealize.png "UML_ClassOvRealize")  
  
|Şekil|**Öğe**|Açıklama|  
|-----------|-----------------|-----------------|  
|15|**gerçekleştirme**|Sınıf, arabirim tarafından tanımlanan öznitelikleri ve işlemleri uygular.<br /><br /> Kullanım **devralma** gerçekleştirme arasında bir sınıf ve arabirim oluşturmak için aracı.|  
|16|**gerçekleştirme**|Alternatif bir sunu aynı ilişki. Lolipop simge etiketi arabirimi tanımlar.<br /><br /> Bu sunum oluşturmak için varolan gerçekleştirme ilişkisini seçin. İlişkilendirmenin yanında bir eylem etiketi görünür. Eylem etiketine ve ardından **Lolipop olarak göster**.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [UML modellerini ve diyagramları düzenleme](../modeling/edit-uml-models-and-diagrams.md)   
 [UML sınıf diyagramları: yönergeler](../modeling/uml-class-diagrams-guidelines.md)   
 [UML sınıf diyagramlarındaki türlerin özellikleri](../modeling/properties-of-types-on-uml-class-diagrams.md)   
 [UML sınıf diyagramlarındaki özniteliklerin özellikleri](../modeling/properties-of-attributes-on-uml-class-diagrams.md)   
 [UML sınıf diyagramlarındaki işlemlerin özellikleri](../modeling/properties-of-operations-on-uml-class-diagrams.md)   
 [UML sınıf diyagramlarındaki ilişkilendirmelerin özellikleri](../modeling/properties-of-associations-on-uml-class-diagrams.md)



