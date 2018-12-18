---
title: Genel Bakış etki alanına özgü dil araçları kullanıcı arabirimi | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.dsltools.dsldesigner.editor
helpviewer_keywords:
- Domain-Specific Language Tools, user interface
ms.assetid: 81ae6b35-6819-41d0-953b-6b4ed81f9227
caps.latest.revision: 27
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 2d88c7ee14acc1916e56010784224f8e44b73f45
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49251439"
---
# <a name="overview-of-the-domain-specific-language-tools-user-interface"></a>Etki Alanına Özgü Dil Araçları Kullanıcı Arabirimine Genel Bakış
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

İlk kez açtığınızda, bir etki alanına özgü dil Araçları (DSL araçları) çözümünde [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], kullanıcı arabirimi aşağıdaki resme benzeyecektir.  
  
 ![DSL Tasarımcısı](../modeling/media/dsl-designer.png "dsl_designer")  
  
 Aşağıdaki tablo, kullanıcı Arabiriminin bölümlerini nasıl kullanılacağını açıklar.  
  
|**Öğe**|**Tanım**|  
|-----------------|--------------------|  
|Diyagram|Etki alanı modeli diyagramı görüntülenir.<br /><br /> Diyagramda iki kenara sahiptir. Bir yüzü Modellerinizi içinde öğelerin türlerini tanımlar. Diğer taraftan, Modellerinizi ekranda nasıl görüntüleneceğini tanımlar.|  
|Araç Kutusu|Araçlar, etki alanı sınıfları eklemek ve Şekil diyagrama türleri için araç kutusundan sürükleyin. İlişkileri, bağlayıcılar ve Şekil eşlemeleri eklemek için Aracı'nı tıklatın ve diyagram kaynak düğümde ve hedef düğümü tıklayın.|  
|DSL Gezgini|**DSL Gezgini** bir DSL tanımını etkin pencere olduğunda görünür. Bu DSL ağaç olarak gösterir. DSL Gezgini diyagram üzerinde görüntülenmez model özelliklerini düzenlemenize olanak tanır. Örneğin, araç kutusu öğeleri ekleme ve doğrulama işlemi üzerinde kullanarak geçiş **DSL Gezgini**.|  
|DSL Ayrıntıları penceresi|**DSL ayrıntıları** pencere öğeleri nasıl görüntüleneceğini ve öğeleri nasıl kopyalanır ve Silinen denetlemenize izin modeli öğeleri etki alanının özelliklerini gösterir.<br /><br /> -Varsayılan olarak, **DSL ayrıntıları** penceresi görünür yanındaki **hata listesi** ve **çıkış** windows.|  
  
## <a name="the-domain-model-diagram"></a>Etki alanı modeli diyagramı  
 Etki alanı modeli diyagramı, iki bölüme ayrılmıştır. Diyagram bir tarafı model içinde öğeleri ve ilişkileri gösterir. Diğer taraftan nasıl model görüntülenecek gösterilir ve öğeleri ve modeli diyagramı özelliklerini görüntülemek için kullanılan şekilleri içerir. Aşağıdaki resimde, diyagramın öğeleri gösterir.  
  
 ![DSL Tasarımcısı Kulvar ile](../modeling/media/dsl-desinger.png "dsl_desinger")  
  
 Aşağıdaki tabloda, etki alanı modeli diyagramı öğelerinden bazıları açıklanmaktadır.  
  
|**Terim**|**Tanım**|  
|--------------|--------------------|  
|Etki alanı sınıfı|Etki alanı, modellerinizde öğelerin türlerini sınıflardır.<br /><br /> Birden fazla ilişki hedefinin ise bir alan sınıfına bir diyagramda, birden fazla kez görünebilir.<br /><br /> Bir etki alanı sınıfı eklemek için etki alanı sınıfı aracından sürükleyin **araç kutusu** için **sınıflar ve ilişkiler** tarafında diyagram.|  
|Etki alanı ilişkisi|Etki alanı ilişkileri Modellerinizi öğeler arasında bağlantılar türleridir.<br /><br /> Bir *gömme ilişkisi* hedef öğenin sahibi olduğu veya kaynak öğe tarafından içerilen gösterir ve düz bir çizgi olarak görünür. Bir ağaç modeli forms modeldeki her öğe bir gömme ilişkisi hedef olmalıdır. A *başvuru ilişkisi* model öğeleri arasında genel bir bağlantı gösterir ve kesikli bir çizgi olarak görünür. Herhangi bir öğeye referans bağlantıları herhangi bir sayıda olabilir.<br /><br /> Aracı'nı tıklatarak bir ilişki oluşturmak **araç kutusu**, kaynak etki alanı sınıfı ve ardından hedef sınıf'nı tıklatın.|  
|Şekilleri ve bağlayıcıları|Şekiller nasıl model öğelerini bir DSL diyagramı. görüntüleneceğini belirtmek, bağlayıcılar satırları ilişkileri görüntülemek için kullanılan bir DSL diyagramında belirtin.<br /><br /> Bir şekil veya bağlayıcının oluşturmak için araç sürükleyin **diyagram öğelerine** tarafında diyagram.|  
|Şekil eşlemeleri|Şekil Haritası bir şekil bağlama görüntüler, etki alanı sınıfı için etki alanı modeli diyagramı ya da bağlayıcıyı görüntüler etki alanı ilişkisi üzerinde bir çizgi görünür.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Etki alanına özgü dil araçlarına genel bakış](../modeling/overview-of-domain-specific-language-tools.md)   
 [Etki alanına özgü dil araçları sözlüğü](http://msdn.microsoft.com/en-us/ca5e84cb-a315-465c-be24-76aa3df276aa)   
 [Etki Alanına Özgü Dili Özelleştirme ve Genişletme](../modeling/customizing-and-extending-a-domain-specific-language.md)



