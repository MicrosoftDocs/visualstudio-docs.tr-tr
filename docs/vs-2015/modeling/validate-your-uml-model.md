---
title: UML modelinizi doğrulama | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- UML, constraints
- UML, validation
ms.assetid: deed5092-c11d-4431-a801-1e866a103075
caps.latest.revision: 12
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: fea958a20e5eee78f79f324ad19ef646f7920951
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51739963"
---
# <a name="validate-your-uml-model"></a>UML modelinizi doğrulama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio'da çizebilirsiniz UML modellerini bazıları projenizde geçersiz olarak kabul edilebilir. Örneğin, bir kullanım durumu her zaman yaşam çizgileri kullanım örneklerinin aktörler temsil eden bir sıralı diyagrama bağlanmalıdır gerektirebilir. Yüklediğinizde veya tanımlama *kısıtlamaları* takımınızın bu gibi gereksinimlere uyum sağlamasına yardımcı olur. Kısıtlamalar uygulanabilir kullanıcı kaydederken ya da bir modeli açar ve menü komutu tarafından çağrılabilir.  
  
 Hiçbir kısıtlama ile sağlanan [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], bunların nasıl takımınızın yorumlar ve UML modellerini kullandığına bağlıdır. Ancak kendi kısıtlamaları tanımlamak ve diğer kullanıcılar tarafından tanımlanan kısıtlamaları yükleyebilirsiniz. Kısıtlamaları tanımlamak ve bunları dağıtım için paket hakkında bilgi edinmek için [UML modelleri için doğrulama kısıtlamaları tanımlama](../modeling/define-validation-constraints-for-uml-models.md).  
  
## <a name="invoking-validation"></a>Doğrulamayı çağırma  
 Bir doğrulama uzantısı yüklendiğinde, aşağıdaki durumlarda sağladığı kısıtlamalar uygulanabilir. Bazı kısıtlamalar yalnızca bazı durumlarda uygulamak için ayarlanır.  
  
- **Doğrulama komutu.** Doğrulama herhangi bir zamanda başlatmak için tıklatın **UML modeli doğrula** üzerinde **mimarisi** menüsü.  
  
  > [!NOTE]
  >  Komutu, yalnızca doğrulama kısıtlamalarını yüklüyse görünür.  
  
- **Bir modeli kaydederken.** Modeli kaydettiğinizde doğrulama kısıtlamalarını uygulanabilir. Bu kısıtlamaların amacı projenizin yorumu göre geçersiz bir modeli kaydettiğinizden emin olun yardımcı olmaktır.  
  
   Hatalar varsa, yine de modelini kaydetmek isteyip istemediğinizi istenecektir. Hataları düzeltin ya da yine de modeli kaydetmeyi tercih edebilirsiniz.  
  
- **Model açılırken.** Bir modeli açtığınızda, doğrulama yöntemlerinin modeli kaydettiğinizde var olan hata iletilerini geri yüklemek için uygulanabilir. Hataları, farklı bir model kısımlarına çalışan kullanıcılar tarafından yapılan değişiklikleri arasındaki tutarsızlıkları tarafından da tanıtılabilir. Daha fazla bilgi için [paylaşmak modelleri ve diyagramları dışarı aktarma](../modeling/share-models-and-exporting-diagrams.md).  
  
  Doğrulama hataları bildirilir [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] hatalar penceresinde.  
  
  Yanlış olan öğeler bir diyagramda seçmek için hataya çift tıklayın. Bu, yanlış öğeler yalnızca açık bir diyagramda görünür olması durumunda çalışır.  
  
## <a name="installing-validation-constraints"></a>Doğrulama kısıtlamalarını yükleme  
 Kısıtlamaları içinde paketlenir [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] uzantısı (VSIX) dosyaları. Genellikle, bir dizi kısıtlamaları da menü komutları, profilleri ve araç kutusu öğeleri gibi diğer tanımları içeren bir uzantının parçası olacaktır.  
  
#### <a name="to-install-a-visual-studio-extension"></a>Visual Studio Uzantısı'nı yüklemek için  
  
1.  Çift **.vsix** Windows Explorer (veya dosya Gezgini) dosyası.  
  
2.  Herhangi bir örneğini yeniden başlatmanız [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] zaten çalışıyor.  
  
## <a name="disabling-and-uninstalling-validation-constraints"></a>Doğrulama kısıtlamaları kaldırma ve devre dışı bırakma  
 Kısıtlamaları değil uygulama modeli ile çalışmak istediğinizde, bunları içeren bir uzantı geçici olarak devre dışı bırakabilirsiniz. Bu şekilde, modeli farklı türlerde farklı zamanlarda farklı uzantılarını devre dışı bırakma ve etkinleştirme ile çalışabilirsiniz.  
  
#### <a name="to-disable-or-uninstall-a-visual-studio-extension"></a>Devre dışı bırakın veya Visual Studio Uzantısı'nı kaldırmak için  
  
1.  Üzerinde [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] **Araçları** menüsünü tıklatın **Uzantılar ve güncelleştirmeler**.  
  
2.  Uzantıyla birlikte tıklayın **devre dışı** uzantısı geçici olarak devre dışı. Daha sonra dönme tarafından yeniden etkinleştirebilmeniz için **Uzantılar ve güncelleştirmeler** penceresi.  
  
     \- veya -  
  
     Tıklayın **kaldırma** uzantıyı kaldırmak için.  
  
3.  Yeniden [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [UML modelleri için doğrulama kısıtlamaları tanımlama](../modeling/define-validation-constraints-for-uml-models.md)   
 [Uygulamanız için model oluşturma](../modeling/create-models-for-your-app.md)   
 [Geliştirme sürecinizde modelleri kullanma](../modeling/use-models-in-your-development-process.md)



