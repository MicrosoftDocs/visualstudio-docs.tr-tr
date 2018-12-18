---
title: 'Nasıl yapılır: belirli bir sürüm yükleyin | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-install
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- install a specific release, Visual Studio
ms.assetid: d69ad0f8-f0a0-438e-a0ef-777c4868f139
caps.latest.revision: 20
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.openlocfilehash: 1f8da9b0a577ba7810c3895d9492ce4be7c69cd4
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53065914"
---
# <a name="how-to-install-a-specific-release-of-visual-studio"></a>Nasıl yapılır: Visual Studio'nun belirli bir sürüm yükleyin
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

İsteğe bağlı özelliklerimizi en güncel ve iyileştirilmiş sürümünü elde etmeniz Visual Studio kurulumunu sık sık güncelleştiriyoruz.  Ancak Visual Studio 2015'in önceki bir sürümünü yüklemek istiyorsanız — örneğin, bir güncelleştirme 1 öncesi sürümünden Visual Studio iOS desteği — daha sonra kendi özellik bildirim dosyaları önceki bir sürümünü kullanmak için Visual Studio kurulumunu zorlamanız gerekir. Bu makalede bunun nasıl yapılacağı açıklanmaktadır.

## <a name="installing-the-current-release"></a>Geçerli sürümü yükleme
 Visual Studio 2015'in ilk sürümünden sonra Kurulum altyapısı ve bildirim dosyalarını birkaç kez güncelleştirdik.  Web yükleyicisini indirmeniz halinde buna [Visual Studio indirmeleri](https://www.visualstudio.com/downloads/download-visual-studio-vs) temiz, İnternet'e bağlı bir makinede Web sitesi, Kurulum'ın yüklediği en son Visual Studio 2015 güncelleştirme, en son ürün geliştirmeleri içerir yanı sıra daha yeni ve en son sürümleri isteğe bağlı özellikler ve araçlar.

## <a name="installing-earlier-releases"></a>Önceki sürümler yükleme
 Oluşturabilir ve bir ISO görüntüsü bağlayın veya indirin ve doğrudan yükleyiciyi başlatın [My.VisualStudio.com](https://my.visualstudio.com/downloads?q=visual%20studio%20enterprise%202015) ve ardından ek komut satırı parametreleri .exe dosyasıyla ekleme (/CustomInstallPath gibi/tam / Installselectableıtems/norestart, vs.) Visual Studio nasıl yükleneceğini denetlemek için.

 Aşağıdaki tablo, bazı belirli zaman içinde nokta senaryolar ve Enterprise edition yükleyicinin geçmelidir gerekli komut satırı parametrelerini içerir. (Aynı parametreleri topluluk ya da Professional edition yükleyicileri ile de çalışır.)

|Visual Studio 2015 sürümü|Ne çalıştırmak için|Kullanılacak komut satırı|Hangi kurulumu yok|
|--------------------------------|-----------------|--------------------------|---------------------|
|Visual Studio Enterprise (en son genel sürüm)|Güncelleştirme ile Visual Studio Enterprise (kullanılabilir [My.VisualStudio.com](https://my.visualstudio.com/downloads?q=visual%20studio%20enterprise%202015))|`vs_enterprise.exe` **Not:** varsayılan davranışı Bu yükleme, en son isteğe bağlı özellikler sunar ve bu nedenle, herhangi bir komut satırı parametreleri gerektirmez.|Visual Studio Kurulum en son feed.xml kullanın ve en son dosyaları yükleme|
|Visual Studio Enterprise güncelleştirme 3 (daha fazla güncelleştirme 3-dönem güncelleştirmelerden olmadan özgün Aktualizace 3)|Visual Studio Enterprise RTM (kullanılabilir [MSDN Abonelikleri indirme sayfasına](https://msdn.microsoft.com/subscriptions/downloads/))|`vs_enterprise.exe /OverrideFeedURI http://download.microsoft.com/download/6/B/B/6BBD3561-D764-4F39-AB8E-05356A122545/20160628.2/enu/feed.xml`|Visual Studio Kurulum güncelleştirme 3 yayınlandığında, kullanılabilir feed.xml kullanır|
|Visual Studio Enterprise güncelleştirme (özgün güncelleştirme 2 ancak önceden tarihi bu güncelleştirme 3'ü güncelleştirir) 2|Visual Studio Enterprise RTM (kullanılabilir [MSDN Abonelikleri indirme sayfasına](https://msdn.microsoft.com/subscriptions/downloads/))|`vs_enterprise.exe /OverrideFeedURI http://download.microsoft.com/download/6/B/B/6BBD3561-D764-4F39-AB8E-05356A122545/20160620.2/enu/feed.xml`|Visual Studio Kurulum güncelleştirme 3 önce piyasaya Sürüldü geçerli feed.xml kullanır|
|Visual Studio Enterprise (daha fazla güncelleştirme 2-dönem güncelleştirmelerden olmadan özgün Update 2)|Visual Studio Enterprise RTM (kullanılabilir [MSDN Abonelikleri indirme sayfasına](https://msdn.microsoft.com/subscriptions/downloads/))|`vs_enterprise.exe /OverrideFeedURI http://download.microsoft.com/download/0/6/B/06BB0C5C-C767-4250-91DA-AB463377597E/20160405.3/enu/feed.xml`|Visual Studio Kurulumu güncelleştirme 2 yayımlandığında kullanılabilir feed.xml kullanır|
|Visual Studio Enterprise güncelleştirme (özgün güncelleştirme 1 ancak önceden tarihi bu güncelleştirme 2 ile güncelleştirmeleri) 1|Visual Studio Enterprise RTM (kullanılabilir [MSDN Abonelikleri indirme sayfasına](https://msdn.microsoft.com/subscriptions/downloads/))|`vs_enterprise.exe /OverrideFeedURI http://download.microsoft.com/download/3/2/A/32A1974F-D236-43C1-8981-97DDCBAEF14A/20160225.3/enu/feed.xml`|Visual Studio Kurulum güncelleştirmesini yayımlanan 2'den önce geçerli feed.xml kullanır|
|Visual Studio Enterprise güncelleştirme 1 (daha fazla güncelleştirme dönemi 1 güncelleştirmelerden olmadan özgün güncelleştirme 1)|Visual Studio Enterprise RTM (kullanılabilir [MSDN Abonelikleri indirme sayfasına](https://msdn.microsoft.com/subscriptions/downloads/))|`vs_enterprise.exe /OverrideFeedURI https://download.microsoft.com/download/3/2/A/32A1974F-D236-43C1-8981-97DDCBAEF14A/20151201.1/enu/feed.xml`|Visual Studio Kurulum Güncelleştirmesi 1 yayınlandığı zaman, kullanılabilir feed.xml kullanır|
|Visual Studio Enterprise (özgün RTM, ancak, önceden tarihi bu güncelleştirme 1'güncelleştirmeleri)|Visual Studio Enterprise RTM (kullanılabilir [MSDN Abonelikleri indirme sayfasına](https://msdn.microsoft.com/en-us/subscriptions/downloads/))|`vs_enterprise.exe /OverrideFeedURI https://download.microsoft.com/download/3/6/1/36188D5F-479F-4A46-BF55-6AE5928D1EBB/20151102.3/enu/feed.xml`|Visual Studio Kurulum Güncelleştirmesi 1 önce piyasaya Sürüldü geçerli feed.xml kullanır|
|Visual Studio Enterprise (özgün RTM ile güncelleştirme yok)|Visual Studio Enterprise RTM (kullanılabilir [MSDN Abonelikleri indirme sayfasına](https://msdn.microsoft.com/subscriptions/downloads/))|`vs_enterprise.exe /OverrideFeedURI https://download.microsoft.com/download/5/7/B/57BF5016-E4F0-4EB5-BE27-2BFA87E7723F/20150713.1/enu/feed.xml`|Visual Studio Kurulumu RTM yayınlandığı zaman, kullanılabilir feed.xml kullanır|

> [!IMPORTANT]
>  Kullanmak istediğiniz dile bağlı olarak, lütfen "enu" (İngilizce) aşağıdaki değerlerden biriyle değiştirin:
>
> - CHS (için Çince (Basitleştirilmiş))
>   -   CHT (için Çince (Geleneksel))
>   -   CSY (Çekçe için)
>   -   Almanca (Almanya için)
>   -   ESN (İspanyolca için)
>   -   FRA (için Fransızca)
>   -   ITA (İtalyanca için)
>   -   jpa (Japonca için)
>   -   KOR (için Korece)
>   -   PLK (Lehçe için)
>   -   PTB (Portekizce için)
>   -   RUS (Rusça)
>   -   Dim (Türkçe için)

## <a name="see-also"></a>Ayrıca Bkz.
 [Visual Studio Yönetici Kılavuzu](../install/visual-studio-administrator-guide.md)