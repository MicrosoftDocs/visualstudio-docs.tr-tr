---
title: Modelinizi profiller ve stereotipler aracılığıyla özelleştirme | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- UML model, profiles
- UML model, stereotypes
- UML model, customizing
ms.assetid: fd607157-0d3a-4583-a84e-427a4b2a5acb
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 33e887764c535083c2449a7d333868b2ccd9c4c5
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51727701"
---
# <a name="customize-your-model-with-profiles-and-stereotypes"></a>Modelinizi profiller ve stereotipler aracılığıyla özelleştirme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio'da sınıfları ve bunları belirli amaçlarla özelleştirmek için bileşenleri gibi standart UML model öğelerini uyarlayabilirsiniz. Uygulayabileceğiniz bir *stereotip* bir model öğesine öğenin özellikler listesini değiştirebilirsiniz. Stereotipler adlı koleksiyon içinde tanımlanan *profilleri*.  
  
 Bu özellik, Visual Studio'nun hangi sürümlerinin desteklediğini görmek için bkz: [mimari ve Modelleme Araçları sürüm desteği](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
 Stereotip kullanmak için bir profil için bir paket bağlayın. Bu, paket öğe profilinde tanımlanan stereotiplerin sağlar. Bazı profiller, Visual Studio ile birlikte yüklenir. Ayrıca, kendi profilinizi tanımlayabilirsiniz.  
  
 Bir öğenin özellikler listesinde bulunan stereotipler ayarlanabilir. Şekli diyagram üzerinde temel türleri için uygulanan stereotipler da örnekte gösterildiği gibi şeklinde görünür.  
  
 ![UML sınıf ile bir stereotip. ](../modeling/media/uml-class-stereotype.png "UML_class_stereotype")  
  
> [!NOTE]
>  Bir model oluşturmak ve ardından model başkalarıyla paylaşmak için bir profil kullanıyorsanız, bunlar aynı profili kendi bilgisayarınızda yüklü olan sürece stereotipleri görme olanakları mümkün olmayacaktır.  
  
## <a name="related-topics"></a>İlgili Konular  
  
|Başlık|Açıklama|  
|-----------|-----------------|  
|[UML model öğelerine stereotipler ekleme](../modeling/add-stereotypes-to-uml-model-elements.md)|Profile paket bağlama ve bir stereotip öğeye uygulayarak bir paket içindeki bir model öğesini yapılıyor.|  
|[UML modelleri için standart stereotipler](../modeling/standard-stereotypes-for-uml-models.md)|L3 ve UML Standart profilleri L2 Visual Studio ile yüklenir ve her model için varsayılan olarak bağlanır. Bunlar, modellerinize eklemek için kullanabileceğiniz stereotipler sağlar.<br /><br /> Örneğin, yalnızca kendi örnekleri dışarıdan görünen davranışını tanımlamak üzere tasarlanmış olduğunu belirtmek için bir sınıf «belirtimi» stereotipi uygulayabilirsiniz,|  
|[UML’yi genişletmek için profil tanımlama](../modeling/define-a-profile-to-extend-uml.md)|Kendi uygulama alanına kendi stereotipleri ve uyumlu araçları tanımlayabilirsiniz.<br /><br /> Örneğin, bankacılık yazılımı geliştiriyorsanız, sınıflara uygulanabilecek bir «Hesap» stereotipi tanımlayabilirsiniz. Ardından, farklı türdeki hesabı ve ilişkilerini açıklamak için sınıf diyagramlarını kullanabilirsiniz.|  
|[UML profili yükleme](../modeling/install-a-uml-profile.md)|Birisi bir UML profili verdiği, bilgisayarınıza yükleyebilirsiniz.|  
|[Özel bir modelleme araç kutusu öğesi tanımlama](../modeling/define-a-custom-modeling-toolbox-item.md)|Özel araç kutusu öğesi bir stereotip yeni öğeler üzerinde sürekli olarak ayarlama özelliğinden kaydeder.|  
|[Sterotipe göre renkli UML sınıfları](http://code.msdn.microsoft.com/UML-Color-Classes-by-07de2b70)|Bu örnek kod, UML diyagramları genişletir. Otomatik olarak, bir UML şekli göre stereotip öğenin rengini ayarlar.|



