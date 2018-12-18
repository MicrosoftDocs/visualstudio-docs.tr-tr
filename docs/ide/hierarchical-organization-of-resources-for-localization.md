---
title: Yerelleştirme için kaynakların hiyerarşik organizasyonu
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
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
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f21b4c6d53a70cb3d695c05e412b0e2f52a607bb
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49874572"
---
# <a name="hierarchical-organization-of-resources-for-localization"></a>Yerelleştirme için kaynakların hiyerarşik organizasyonu

Visual Studio'da yerelleştirilmiş kaynaklar (dizeler ve her bir kültür için uygun görüntü gibi veri) ayrı dosyalarında depolanan ve UI kültürü ayarına göre yüklenir. Anlamak için yerelleştirilmiş kaynaklar yüklenen nasıl hiyerarşik olarak düzenlenmiş olarak bunları düşünmek yararlı olur.

## <a name="kinds-of-resources-in-the-hierarchy"></a>Kaynak hiyerarşideki türleri

- Örneğin İngilizce ("tr"), varsayılan kültür için geri dönüş kaynak hiyerarşisinin en üstünde bulunur. Bu geri dönüş kaynakları kendi dosyalarına sahip olmayan tek olanlardır; Bunlar, ana derlemesinde depolanır.

- Geri dönüş kaynakları nötr kültürler için kaynaklardır. Bağımsız kültür, bir dil ancak değil bir ülke/bölge ile ilişkilidir. Örneğin, Fransızca ("fr"), bağımsız kültür olur. (Geri dönüş de nötr bir kültür ancak özel bir kaynaklardır.)

- Bağımsız kültür kaynaklarını belirli kültürler için kaynaklardır. Belirli bir kültür, bir dil ve ülke/bölge ile ilişkilidir. Örneğin, Kanada Fransızcası ("fr-CA") belirli bir kültür olur.

Bir uygulama gibi bir dize, yerelleştirilmiş tüm kaynak yüklemeye çalışır ve bunu bulamaz, istenen kaynak içeren bir kaynak dosyayı bulana kadar hiyerarşisinde yukarı taşınır.

Kaynaklarınızı depolamak için en iyi yolu bunları mümkün olduğunca generalize sağlamaktır. Bu, kaynak dosyalarında özel kültürler mümkün olduğunda yerine nötr kültürler için yerelleştirilmiş dizeler, görüntüler vb. depolamak anlamına gelir. Örneğin, Fransızca Belçika için kaynaklarınız varsa ("fr-olabilir") kültürü ve hemen yukarıdaki kaynakları geri dönüş kaynakları İngilizce, biri Fransızcası kültürü için yapılandırılmış bir sistemde, uygulamanızın kullandığında bir sorun meydana gelebilir. Sistem için bir uydu derlemesi için "fr-CA" görünüyor ancak bunun yerine bulmuyorsa, bu nedenle geri dönüş kaynağı içeren ana derleme yükler İngilizce, Fransızca kaynakları yüklemek yerine. Aşağıdaki resimde, bu istenmeyen bir senaryo gösterir.

![Yalnızca belirli kaynakları](../ide/media/vbspecificresourcesonly.gif)

Önerilen uygulama "fr" kültür için bir bağımsız kaynak dosyasında mümkün olduğunca fazla kaynak yerleştirme izlerseniz, Fransızca Kanada kullanıcı için işaretlenen kaynakları görmek "fr-olması" kültür ve Fransızca dizeler gösteriliyordu. Aşağıdaki durum bu tercih edilen bir senaryo gösterir.

![NeutralSpecificResources grafiği](../ide/media/vbneutralspecificresources.gif)

## <a name="see-also"></a>Ayrıca bkz.

- [Yerelleştirme için bağımsız kaynak dilleri](../ide/neutral-resources-languages-for-localization.md)
- [Güvenlik ve yerelleştirilmiş yardımcı derlemeler](../ide/security-and-localized-satellite-assemblies.md)
- [Uygulamaları yerelleştirme](../ide/localizing-applications.md)
- [Uygulamaları Genelleştirme ve yerelleştirme](../ide/globalizing-and-localizing-applications.md)