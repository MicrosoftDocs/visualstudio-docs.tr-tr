---
title: UML modellerini diğer modeller ve araçlarla tümleştirme | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- UML - extending, references to models
ms.assetid: 9e75e7d1-93cf-4196-baa3-bd10b9af16d3
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: d1cc5a26a9c2febb0dd1dff3c0d14ba3786dde9f
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51764136"
---
# <a name="integrate-uml-models-with-other-models-and-tools"></a>UML modellerini diğer modeller ve araçlarla tümleştirme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

UML modellerini diğer modeller ve etki alanına özgü diller ile tümleştirilebilir.  
  
 Çeşitli işlevleri gerçekleştirmek için uzantı kodu yazarak aşağıdaki yollarla modelleri tümleştirebilirsiniz:  
  
 Başvuruları herhangi bir öğedeki dosyaları gibi diğer öğelere ya da diğer model öğelerine bağlayın.  
 Bir UML öğesi içinde kimliklerini dize olarak kodlama bağlantılar diğer UML öğeleri, dosyaları ya da diğer nesneleri depolayabilirsiniz.  
  
 Örneğin, başka bir etkinlik diyagramı için herhangi bir UML eylem (diğer bir deyişle, bir etkinlik diyagramı öğesinde) bağlayabilirsiniz bir uzantı yazabilirsiniz. Eylem kullanıcı çift tıkladığında diğer diyagram açılır. Bu eylem daha ayrıntılı bir görünümünü sağlamak kullanıcı sağlar.  
  
 Dizeler ve diğer verileri herhangi bir öğede depolayabilirsiniz iki yolu vardır:  
  
- **Stereotip özellikleri.** UML öğesi belirtilen türde özellikler ekleyen bir stereotip tanımladığınız bir UML profili tanımlayabilirsiniz. Örneğin, adında bir özellik ekleyen bir profil tanımlayabilirsiniz **MoreDetail** UML eylem. Depoları stereotip uygulayarak ve ardından özelliğinde verilerin depolanması veriler bir eylem arasında bağlantı uzantı kodu yazabilirsiniz.  
  
   Stereotip ve özellikleri kullanıcıya Özellikler penceresinde görünür.  
  
   Bu uzantıyı dağıtmak için profil tanımı ve tek bir uzantı kodunda paketlemeniz gerekir [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] uzantısı.  
  
   Daha fazla bilgi için [UML genişletmek için profil tanımlama](../modeling/define-a-profile-to-extend-uml.md).  
  
   Bir örnek proje için bir profil dağıtıldığı menü komutları ve hareket işleyicileri birlikte bkz [örnek: UML profilleri](http://go.microsoft.com/fwlink/?LinkID=213811).  
  
- **Başvuruları.** Dizeler kümesi için herhangi bir UML öğesi ekleyebilirsiniz. Bir dosya adı veya başka bir öğenin GUİD'si gibi bilgileri depolayan bir kod yazabilirsiniz. Bu, ek tanımları sağlamadan yapılabilir. Başvuru doğrudan kullanıcıya görünür değildir.  
  
   Daha fazla bilgi için [iliştirme başvuru dizeleri UML model öğelerini](../modeling/attach-reference-strings-to-uml-model-elements.md). Bir örnek için bkz. [diyagramlara veya diğer dosyaları bağlantı UML öğelerini](http://go.microsoft.com/fwlink/?LinkId=213813).  
  
  Model öğelere başvuruları kodlamak için iki yolu vardır:  
  
- **GUID ve dosya adı** hedef model öğesine ve içerdiği modeli ya da belirli bir diyagram görüntüler.  
  
   Bir örnek için bkz. [diyagramlara veya diğer dosyaları bağlantı UML öğelerini](http://go.microsoft.com/fwlink/?LinkId=213813).  
  
- **ModelBus başvuruları.** ModelBus oluşturup modelleri arasında başvurularını çözümlemek için bir çerçevedir. Bu, bir modelinde bir öğedeki kullanıcının seçmesine olanak tanır ModelBus Seçici içerir. Ayrıca kullanıcının hedef model içinde yapılan değişiklikler nedeniyle kaybolur başvurularını çözümlemek için yardımcı olur.  
  
   Daha fazla bilgi için [Visual Studio Modelbus kullanarak modelleri tümleştirme](../modeling/integrating-models-by-using-visual-studio-modelbus.md).  
  
  Bir modeldeki değişiklikleri yayar.  
  Örneğin, kullanıcı bir değişirse, diğeri de değişir. böylece bir öğenin adını bağlantılı, diyagramın adı ile eşitleyebilirsiniz. Bunu yapmak için iki mekanizma vardır:  
  
1. **VMSDK kuralları** aynı modelin içindeki değişiklikleri yaymak için kullanılabilir.  
  
    Bir örnek için bkz. [diyagramlara veya diğer dosyaları bağlantı UML öğelerini](http://go.microsoft.com/fwlink/?LinkId=213813).  
  
2. **VMSDK olayları** değişiklikleri – modelin dışına örneğin yayılması, bağlı bir belgenin dosya adını değiştirmek için veya başka bir modelinde bir öğedeki değiştirmek için kullanılabilir.  
  
   Bu iki mekanizmaları hakkında daha fazla bilgi için bkz: [nasıl yapılır: bir UML modelindeki değişikliklere yanıt](../misc/how-to-respond-to-changes-in-a-uml-model.md).  
  
   Öğeleri bir modelden diğerine kopyalamak için sürükleyin  
   Öğeleri bir UML diyagram üzerine sürükleyerek öğeleri oluşturmalarına izin verebilirsiniz. Bir kopyası özgün olarak oluşturulan öğe yok. Örneğin, etkinlik diyagramı yeni bir eylem oluşturmak için çözüm gezgininden başka bir etkinlik diyagramı, sürükleyin kullanıcı izin verebilirsiniz.  
  
   Daha fazla bilgi için [modelleme diyagramında hareket işleyicisi tanımlama](../modeling/define-a-gesture-handler-on-a-modeling-diagram.md) ve [nasıl yapılır: sürükle ve bırak işleyicisi ekleme](../modeling/how-to-add-a-drag-and-drop-handler.md).  
  
## <a name="samples"></a>Örnekler  
 Kod örneği, lütfen bakın [diyagramlara veya diğer dosyaları bağlantı UML öğelerini](http://go.microsoft.com/fwlink/?LinkId=213813). Örnek bir dosya herhangi bir UML öğesi üzerine sürükleyin ve daha sonra öğeyi çift tıklayarak dosyayı açmak olanak sağlar. Örneğin, etkinlik diyagramı bir kullanım örneği öğesine bağlayabilirsiniz. Hangi öğelerin bağlantılara sahip bir simge gösterilir.  
  
 Bu kod örneği aşağıdaki teknikleri gösterir:  
  
- [Model öğelerine başvuru dizeleri ekleme](../modeling/attach-reference-strings-to-uml-model-elements.md)  
  
   Örnek kod dosya yolları ve dizelerindeki öğesiyle ilişkilendirilmiş başvuru dizeleri depolar.  
  
- Dekoratörler için UML öğeleri ekleme. Dekoratörler hakkında genel bilgi için bkz: [özelleştirme metin ve görüntü alanlarını](../modeling/customizing-text-and-image-fields.md).  
  
   Örnek bir görüntü dekoratör UML şekillere ekler.  
  
- [Nasıl yapılır: bir UML modelindeki değişikliklere yanıt verme](../misc/how-to-respond-to-changes-in-a-uml-model.md)  
  
   Örnek bir diyagram üzerinde görünen yeni şekiller yanıt veren bir kural tanımlamak nasıl gösterir.  
  
- [Modelleme diyagramında menü komutu tanımlama](../modeling/define-a-menu-command-on-a-modeling-diagram.md)  
  
- [Modelleme diyagramında hareket işleyicisi tanımlama](../modeling/define-a-gesture-handler-on-a-modeling-diagram.md)  
  
   Örnek üstesinden nasıl gelineceğini gösterir öğeleri, Windows Explorer (veya dosya Gezgini), Çözüm Gezgini ve diğer UML öğeleri sürüklediğiniz.  
  
  DSL tarafından okunan bir UML modeli olduğu bir örnek için bkz: [nasıl yapılır: sürükle ve bırak işleyicisi ekleme](../modeling/how-to-add-a-drag-and-drop-handler.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Modelleme Diyagramında Menü komutu tanımlama](../modeling/define-a-menu-command-on-a-modeling-diagram.md)   
 [Modelleme Diyagramında hareket işleyicisi tanımlama](../modeling/define-a-gesture-handler-on-a-modeling-diagram.md)   
 [Nasıl yapılır: sürükle ve bırak işleyicisi ekleme](../modeling/how-to-add-a-drag-and-drop-handler.md)   
 [Nasıl yapılır: bir UML modelindeki değişikliklere yanıt verme](../misc/how-to-respond-to-changes-in-a-uml-model.md)   
 [Örnek: UML profilleri](http://go.microsoft.com/fwlink/?LinkID=213811)   
 [Bağlantı UML öğeleri diyagramlara veya diğer dosyaları](http://go.microsoft.com/fwlink/?LinkId=213813)



