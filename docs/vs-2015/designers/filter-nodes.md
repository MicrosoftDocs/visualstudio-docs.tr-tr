---
title: Filtre düğümleri | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f7cae2dc-e9a7-49d4-8be5-58b79868624e
caps.latest.revision: 14
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: ec8046fcbeebe2af0c6c7ebb725ffe4ed6cfa263
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49178587"
---
# <a name="filter-nodes"></a>Filtre Düğümleri
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Gölgelendirici Tasarımcısı'nda giriş filtre düğümlerinin dönüştürme — Örneğin, bir renk veya doku örnek — içine mecazi renk değeri. Bu mecazi renk değerleri genellikle başınıza olmayan işleme veya diğer görsel efektler bileşen olarak kullanılır.  
  
## <a name="filter-node-reference"></a>Filtre düğümü başvurusu  
  
|Düğüm|Ayrıntılar|Özellikler|  
|----------|-------------|----------------|  
|**Bulanıklaştırma**|Bir Gauss işlevi kullanarak doku bulanıklaştırır.<br /><br /> Renk ayrıntısı veya bir dokudaki gürültüsünü azaltmak için bunu kullanabilirsiniz.<br /><br /> **Giriş:**<br /><br /> `UV`: `float2`<br /> Test etmek için örnek doku hücresi koordinatları.<br /><br /> **Çıkış:**<br /><br /> `Output`: `float4`<br /> Bulanık renk değeri.|**Doku**<br /> Bulanıklaştırma sırasında kullanılan örnekleyici ile ilişkili doku kaydı.|  
|**Doygunluğu Azalt**|Belirtilen renk rengin miktarını azaltır.<br /><br /> Renk kaldırıldığından, renk değeri da gri ölçekli eşdeğerine yaklaşır.<br /><br /> **Giriş:**<br /><br /> `RGB`: `float3`<br /> Doygunluğu Azalt rengi.<br /><br /> `Percent`: `float`<br /> Kaldırmak için renk yüzdesi olarak ifade normalleştirilmiş değeri [0, 1] aralığında olarak.<br /><br /> **Çıkış:**<br /><br /> `Output`: `float3`<br /> Renk doygunluğu azaltılmış.|**Parlaklık**<br /> Kırmızı, yeşil ve mavi renk bileşenlerine verilen Ağırlıklar.|  
|**Kenar algılama**|Kenarları Canny kenar algılayıcısı kullanarak bir dokudaki algılar. Kenar pikselleri beyaz olarak çıkışıdır; Kenar-olmayan piksel siyah olarak çıkışıdır.<br /><br /> Bu, böylece ek etkileri kenar piksellerinin değerlendirmek için kullanabileceğiniz bir dokudaki kenarları tanımlamak için kullanabilirsiniz.<br /><br /> **Giriş:**<br /><br /> `UV`: `float2`<br /> Test etmek için örnek doku hücresi koordinatları.<br /><br /> **Çıkış:**<br /><br /> `Output`: `float4`<br /> Doku hücresi bir edge üzerinde ise beyaz; Aksi takdirde, siyah.|**Doku**<br /> Kenar algılama sırasında kullanılan örnekleyici ile ilişkili doku kaydı.|  
|**Keskinleştirin**|Bir dokuyu netleştirir.<br /><br /> Bu, ince bir dokudaki vurgulamak için kullanabilirsiniz.<br /><br /> **Giriş:**<br /><br /> `UV`: `float2`<br /> Test etmek için örnek doku hücresi koordinatları.<br /><br /> **Çıkış:**<br /><br /> `Output`: `float4`<br /> Bulanık renk değeri.|**Doku**<br /> Netleştirme sırasında kullanılan örnekleyici ile ilişkili doku kaydı.|



