---
title: Katman diyagramları için uzantı sorunlarını giderme | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- layer diagrams, extension errors
- layer diagrams, troubleshooting extensions
ms.assetid: 1fda4f8a-38b8-482b-87b8-eade1a4e5662
caps.latest.revision: 27
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 6361651672e72df6661f030a4b6c8e451fdaea89
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51738769"
---
# <a name="troubleshoot-extensions-for-layer-diagrams"></a>Katman diyagramları için uzantı sorunlarını giderme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu konuda, katman model uzantıları oluştururken karşılaşabileceğiniz bazı sorunlar ele alınmaktadır.  
  
#### <a name="when-i-press-f5-to-debug-my-extension-my-commands-gesture-handlers-validation-extensions-or-custom-properties-do-not-appear-on-layer-diagrams-in-the-experimental-instance-of-includevsprvsincludesvsprvs-mdmd"></a>Uzantımı ayıklamak için F5 tuşuna bastığımda, komutları, hareket işleyicileri, doğrulama uzantıları veya özel özellikler deneysel örneğinde katman diyagramlarında görünmez. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]  
  
1. Uzantı çözümünüzü deneysel örneğinde açın [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]ve **derleme** menüsünde tıklatın **çözümü yeniden derle**.  
  
2. Tuşuna **F5** veya **CTRL + F5** Deneysel örneğini başlatmak için [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Bir katman diyagramı açın ve uzantınızı sınayın.  
  
   Gerekirse, sonraki yordama geçin.  
  
#### <a name="an-old-version-of-my-extension-runs"></a>Uzantım eski bir sürümünü çalıştırır.  
  
1. Emin olun, Deneysel örnek yok [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] çalışıyor.  
  
2. Aşağıdaki klasörü silin: %LocalAppData%\Microsoft\VisualStudio\\[sürüm] \ComponentModelCache  
  
   > [!NOTE]
   >  % LocalAppData %, genellikle *DriveName*: \Users\\*kullanıcıadı*\AppData\Local.  
  
   Gerekirse, sonraki yordama geçin.  
  
#### <a name="an-old-version-of-my-validation-results-appears-or-my-validation-method-is-not-called"></a>Doğrulama sonuçlarımın eski bir sürümü görünüyor veya doğrulama Yöntemim çağrılmıyor.  
  
1.  Deneysel örneğinde [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], **derleme** menüsünde tıklatın **çözümü Temizle**. Bu, önceki doğrulama analizinin önbelleğe alınan sonuçlarını temizler.  
  
2.  Modelinizdeki katmanların kod öğeleriyle ilişkili olduğundan ve modelde en az bir bağımlılık bağlantısı olduğundan emin olun. Doğrulanacak bir şey yoksa, doğrulama çağrılmaz.  
  
3.  Ayrı bir işlemde çalıştığından, bir doğrulama yönteminde normal kesme noktaları çalışmayabilir. Bir çağrı eklemeniz gerekir `System.Diagnostics.Debugger.Launch()` yönteminizde ilerlemek istiyorsanız.  
  
4.  İçinde **source.extension.vsixmanifest** katman doğrulama projenizdeki her ikisi de eklediğinizden emin olun bir **MEF Bileşeni** öğesi ve bir **özel uzantı türü** altında öğesi **İçerik**.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Katman diyagramlarını genişletme](../modeling/extend-layer-diagrams.md)



