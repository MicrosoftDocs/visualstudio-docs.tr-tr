---
title: Model öğelerine stereotipler ekleme | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- UML model, stereotypes
ms.assetid: 82545252-83ce-4e11-a419-61373be75d16
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: dbd5f4288833a29bdfef2df97ee71ac765ae168f
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51725381"
---
# <a name="add-stereotypes-to-uml-model-elements"></a>UML model öğelerine stereotipler ekleme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

UML model öğesine açıklama eklemek ve özel özellikler sağlamak için bir stereotip ekleyebilirsiniz. Stereotip bir model öğesine eklemek için bir profilde stereotip tanımlanmış olmalıdır ve bir paket veya model öğeyi içeren modeli profili bağlamanız gerekir. Her stereotip yalnızca belirli türdeki bir UML sınıfları, kullanım durumları veya bileşenleri gibi model öğesi eklenebilir.  
  
 Örneğin, bir UML sınıfıyla «belirtimi» stereotipi tanımlamak istiyorsanız, bir paket veya standart profil L2'ye bağlı bir model oluşturmalısınız.  
  
 Varsayılan olarak, her model L3 ve UML Standart profilleri L2 bağlanır.  
  
### <a name="to-link-a-profile-to-a-model-or-a-package"></a>Bir profili bir model veya paket bağlamak için  
  
1.  Açık **UML Model Gezgini**. Üzerinde **mimarisi** menüsünde **Windows**ve ardından **UML Model Gezgini**.  
  
2.  Bir paket veya profildeki stereotiplerin uygulamak istediğiniz tüm öğeleri içeren bir model bulun.  
  
3.  Paket veya model sağ tıklayın ve ardından **özellikleri**.  
  
4.  İçinde **özellikleri** penceresinde **profilleri** kullanmak istediğiniz stereotipler içeren profillerini özelliği.  
  
     Profil stereotipler model veya paket içindeki tüm öğelerde artık kullanılabilir. Paket diğer paketler içeriyorsa, stereotip ayrıca içinde öğeleri üzerinde kullanılabilir.  
  
### <a name="to-add-stereotypes-to-model-elements-or-relationships"></a>Model öğelerini veya ilişkileri stereotipler eklemek için  
  
1.  Model öğe veya ilişki, diyagram üzerinde veya sağ **UML Model Gezgini**ve ardından **özellikleri**.  
  
    > [!NOTE]
    >  Birkaç öğe için aynı stereotipler eklemek, birçok öğeyi seçin ve ardından bunları birine sağ tıklayın.  
  
2.  Tıklayın **stereotipler** özelliği ve uygulamak istediğiniz stereotipler seçin.  
  
     «Ayraç» içinde model öğesi çoğu öğe ve ilişki türleri için Seçili stereotipler görünür.  
  
    > [!NOTE]
    >  Göremiyorsanız **stereotipler** özelliği veya istediğiniz stereotip görünmüyorsa, model öğesi bir paket veya model için uygun profili bağlandı içinde olduğundan emin olun.  
  
3.  Bazı stereotipler model öğesi için ek özelliklerin değerlerini ayarlamanıza olanak sağlar. Bu özellikleri görmek için genişletin **stereotipler** özelliği.  
  
### <a name="to-create-model-elements-within-a-package"></a>Bir paket içindeki model öğelerini oluşturmak için  
  
1.  Bir UML sınıf diyagramı içinde veya bir paket oluşturma **UML Model Gezgini**.  
  
2.  Model öğelerini paketi aşağıdaki yollardan birini ekleyin:  
  
    -   UML sınıf diyagramında, bir öğe için Aracı'nı tıklatın ve ardından diyagram üzerinde paket içine tıklayın.  
  
         \- veya -  
  
    -   UML Model Gezgini'nde, pakete sağ tıklayın, fareyle **Ekle**ve ardından bir öğe türüne tıklayın.  
  
         \- veya -  
  
    -   UML Model Gezgini'nde, var olan bir öğe pakete sürükleyin.  
  
         \- veya -  
  
    -   Bir diyagram paketi bağlantısını ve ardından diyagram öğeleri oluşturun.  
  
         Bunu yapmak için diyagramın boş bir bölümüne sağ tıklayın ve ardından **özellikleri**. İçinde **özellikleri** penceresinde **bağlantılı paket** istediğiniz paket için.  
  
         Diyagramda oluşturduğunuz tüm yeni öğeleri paket içinde tanımlanır.  
  
         Yalnızca bazı diyagram türleri ile bunu yapabilirsiniz.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [UML genişletmek için profil tanımlama](../modeling/define-a-profile-to-extend-uml.md)   
 [Modelinizi profiller ve stereotipler aracılığıyla özelleştirme](../modeling/customize-your-model-with-profiles-and-stereotypes.md)   
 [Paketleri ve ad alanlarını tanımlama](../modeling/define-packages-and-namespaces.md)   
 [Sterotipe göre renkli UML sınıfları](http://code.msdn.microsoft.com/UML-Color-Classes-by-07de2b70)



