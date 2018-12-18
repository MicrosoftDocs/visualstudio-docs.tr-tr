---
title: Yerelleştirme için kaynakların hiyerarşik organizasyonu | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- resource files, localized
- localization [Visual Studio], resources
- fallback resources
- international applications [Visual Studio], storing resources
- satellite assemblies, resource hierarchies
- globalization [Visual Studio], resources
- satellite assemblies
- resources [Visual Studio], fallback system
- resource files, fallback processes
ms.assetid: dadf8f2c-f74c-44d7-bec0-a1e956d8d38d
caps.latest.revision: 9
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 11eeaa2c6742675372acf8b96280737f556c7799
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49914144"
---
# <a name="hierarchical-organization-of-resources-for-localization"></a>Yerelleştirme için Kaynakların Hiyerarşik Organizasyonu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio'da yerelleştirilmiş kaynaklar (dizeler ve her bir kültür için uygun görüntü gibi veri) ayrı dosyalarında depolanan ve UI kültürü ayarına göre yüklenir. Anlamak için yerelleştirilmiş kaynaklar yüklenen nasıl hiyerarşik olarak düzenlenmiş olarak bunları düşünmek yararlı olur.  
  
## <a name="kinds-of-resources-in-the-hierarchy"></a>Kaynak hiyerarşideki türleri  
  
- Örneğin İngilizce ("tr"), varsayılan kültür için geri dönüş kaynak hiyerarşisinin en üstünde bulunur. Bunları kendi dosyalarına sahip olmayan tek kaynaklardır; Bunlar, ana derlemesinde depolanır.  
  
- Geri dönüş kaynakları nötr kültürler için kaynaklardır. Bağımsız kültür, bir dil ancak değil bir ülke/bölge ile ilişkilidir. Örneğin, Fransızca ("fr"), bağımsız kültür olur. (Geri dönüş kaynakları da bağımsız bir kültür, ancak bir özel olduğunu unutmayın.)  
  
- Kaynaklarını belirli kültürler için olanlardır. Belirli bir kültür, bir dil ve ülke/bölge ile ilişkilidir. Örneğin, Kanada Fransızcası ("fr-CA") belirli bir kültür olur.  
  
  Bir uygulama gibi bir dize, yerelleştirilmiş tüm kaynak yüklemeye çalışır ve bunu bulamaz, istenen kaynak içeren bir kaynak dosyayı bulana kadar hiyerarşisinde yukarı taşınır.  
  
  Kaynaklarınızı depolamak için en iyi yolu bunları mümkün olduğunca generalize sağlamaktır. Bu, kaynak dosyalarında özel kültürler mümkün olduğunda yerine nötr kültürler için yerelleştirilmiş dizeler, görüntüler vb. depolamak anlamına gelir. Örneğin, Fransızca Belçika için kaynaklarınız varsa ("fr-olabilir") kültürü ve hemen yukarıdaki kaynakları geri dönüş kaynakları İngilizce, biri Fransızcası kültürü için yapılandırılmış bir sistemde, uygulamanızın kullandığında bir sorun meydana gelebilir. Sistem "fr-CA" için bir uydu derleme aramak değil bulmak ve İngilizce, Fransızca kaynakları yüklemek yerine geri dönüş kaynağı içeren ana derlemesi yüklenemiyor. Aşağıdaki resimde, bu istenmeyen bir senaryo gösterir.  
  
  ![Yalnızca belirli kaynakları](../ide/media/vbspecificresourcesonly.gif "vbSpecificResourcesOnly")  
  
  Önerilen uygulama "fr" kültür için bir bağımsız kaynak dosyasında mümkün olduğunca fazla kaynak yerleştirme izlerseniz, Fransızca Kanada kullanıcı için işaretlenen kaynakları görmek "fr-olması" kültür, ancak kendisine getirirseniz dizeleri Fransızca. Aşağıdaki durum bu tercih edilen bir senaryo gösterir.  
  
  ![NeutralSpecificResources grafiği](../ide/media/vbneutralspecificresources.gif "vbNeutralSpecificResources")  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Yerelleştirme için bağımsız kaynak dilleri](../ide/neutral-resources-languages-for-localization.md)   
 [Güvenlik ve yerelleştirilmiş yardımcı derlemeler](../ide/security-and-localized-satellite-assemblies.md)   
 [Uygulamaları yerelleştirme](../ide/localizing-applications.md)   
 [Uygulamaları Genelleştirme ve yerelleştirme](../ide/globalizing-and-localizing-applications.md)   
 [Nasıl yapılır: Windows Forms Genelleştirme için kültürü ve kullanıcı Arabirimi kültürünü ayarlama](http://msdn.microsoft.com/en-us/694e049f-0b91-474a-9789-d35124f248f0)   
 [Nasıl yapılır: ASP.NET Web sayfası Genelleştirme için kültürü ve kullanıcı Arabirimi kültürünü ayarlama](http://msdn.microsoft.com/library/76091f86-f967-4687-a40f-de87bd8cc9a0)

