---
title: Sabit Düğümler
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-designers
ms.topic: reference
ms.assetid: 2c798a50-a2d7-459b-9879-ad4ad8290c9b
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 00185a4165c6b97a8fcf1dd8d7ce81b219abef75
ms.sourcegitcommit: 522ba712c0d625e51352506146b0556414681964
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/06/2018
ms.locfileid: "37890122"
---
# <a name="constant-nodes"></a>Sabit düğümler

Gölgelendirici Tasarımcısı'nda sabit düğümler değişmez değerleri temsil eder ve piksel gölgelendirici hesaplamalarında köşe öznitelikleri ilişkilendirilmiş. Köşe öznitelikleri ilişkilendirilmiş olduğundan — ve bu nedenle, her bir pikseli farklıdır — sabiti farklı bir sürümünü her piksel gölgelendiricisi örneği alır. Bu, her pikselin benzersiz bir görünüm sağlar.

## <a name="vertex-attribute-interpolation"></a>Köşe özniteliği ilişkilendirme

Oyunlarda veya uygulamalarda 3B Sahne görüntüsü matematiksel olarak nesne sayısı dönüştürerek yapılan — köşe, köşe öznitelikleri ve temel tanımları tarafından tanımlanan — içine ekrandaki piksel. Tüm bir piksel benzersiz görünümünü sağlamak için gereken bilgileri oluşturan farklı köşeler için pikselin yakınlık göre birlikte karışık köşe öznitelikleri, aracılığıyla sağlanmaktadır kendi *ilkel*. Basit bir tür temel bir işleme öğedir; diğer bir deyişle, basit bir nokta, bir satırı veya bir üçgen gibi şekil. Bu köşe için neredeyse aynı sabitleri çok yalnızca biri köşeleri yakın bir piksel alır, ancak bu köşeler ortalamasını olan sabitleri, temel tüm köşeler arasında eşit aralıklı bir piksel alır. Grafik programlamada piksel alma sabitleri olduğu söylenir *ilişkilendirilmiş*. Bu şekilde piksel sabit veri sağlayan çok iyi görsel kaliteyi oluşturur ve aynı anda bellek Ayak izi ve bant genişliği gereksinimlerini azaltır.

Her piksel gölgelendiricisi örneği yalnızca bir sabit değerler kümesini alır ve bu değerleri değiştiremezsiniz ancak farklı piksel gölgelendiricisi örnekleri farklı sabit veri kümelerini alır. Bu tasarım, her pikselin temel için bir farklı renk çıktı oluşturmak bir gölgelendirici programla sağlar.

## <a name="constant-node-reference"></a>Sabit düğüm başvurusu

|Düğüm|Ayrıntılar|Özellikler|
|----------|-------------|----------------|
|**Kamera vektörü**|Geçerli pikselden, dünya alanındaki kameraya genişleyen vektör.<br /><br /> Bunu, dünya alanındaki yansımaları hesaplamak için kullanabilirsiniz.<br /><br /> **Output**<br /><br /> `Output`: `float3`<br /> Geçerli pikselin öğesinden kameraya.|Yok.|
|**Renk sabiti**|Bir sabit renk değeri.<br /><br /> **Output**<br /><br /> `Output`: `float4`<br /> Renk değeri.|**Output**<br /> Renk değeri.|
|**Sabit**|Sabit bir skaler değer.<br /><br /> **Output**<br /><br /> `Output`: `float`<br /> Skaler değer.|**Output**<br /> Skaler değer.|
|**2B sabiti**|Bir iki bileşenli bir vektör sabiti.<br /><br /> **Output**<br /><br /> `Output`: `float2`<br /> Vektör değeri.|**Output**<br /> Vektör değeri.|
|**3B sabiti**|Bir üç bileşenli bir vektör sabiti.<br /><br /> **Output**<br /><br /> `Output`: `float3`<br /> Vektör değeri.|**Output**<br /> Vektör değeri.|
|**4b sabiti**|Bir dört bileşenli bir vektör sabiti.<br /><br /> **Output**<br /><br /> `Output`: `float4`<br /> Renk değeri.|**Output**<br /> Vektör değeri.|
|**Normalleştirilmiş konum**|Normalleştirilmiş cihaz koordinatlarında belirtilen geçerli pikselin konumu.<br /><br /> X koordinatını ve y koordinatını aralığında değerlere sahip [-1, 1], z koordinatı aralığında bir değere sahip. [0, 1] ve w bileşeni görüntüleme alanı; noktası derinlik değerini içerir. w normale döndürülemez.<br /><br /> **Output**<br /><br /> `Output`: `float4`<br /> Geçerli pikselin konumu.|Yok.|
|**Nokta rengi**|Malzeme yayınık renk ve köşe renk öznitelikleri birleşimi geçerli pikselin yayınık rengi.<br /><br /> **Output**<br /><br /> `Output`: `float4`<br /> Geçerli pikselin yayınık rengi.|Yok.|
|**Nokta derinliği**|Görünüm alanında geçerli pikselin derinliği.<br /><br /> **Output**<br /><br /> `Output`: `float`<br /> Geçerli pikselin derinliği.|Yok.|
|**Normalleştirilmiş nokta derinliği**|Normalleştirilmiş cihaz koordinatlarında belirtilen geçerli pikselin derinliği.<br /><br /> Sonuç aralığında bir değere sahip. [0, 1].<br /><br /> **Output**<br /><br /> `Output`: `float`<br /> Geçerli pikselin derinliği.|Yok.|
|**Ekran konumu**|Ekran koordinatlarında belirtilen geçerli pikselin konumu.<br /><br /> Ekran koordinatları, geçerli görünüm penceresine bağlı temel alır. X ve y bileşenleri içeren ekran koordinatları, z bileşen içeren bir aralığına normalleştirilmiş derinliği [0, 1] ve w bileşeni görüntüleme alanı derinlik değerini içerir.<br /><br /> **Output**<br /><br /> `Output`: `float4`<br /> Geçerli pikselin konumu.|Yok.|
|**Yüzey normali**|Nesne alanındaki geçerli pikselin yüzey normali.<br /><br /> Bu, nesne alanındaki aydınlatma katkılarını ve yansımalarını hesaplamak için kullanabilirsiniz.<br /><br /> **Output**<br /><br /> `Output`: `float3`<br /> Geçerli pikselin yüzey normali.|Yok.|
|**Eğim alanı kamera vektörü**|Geçerli pikselden, eğim alanındaki kameraya genişleyen vektör.<br /><br /> Bunu, eğim alanındaki yansımaları hesaplamak için kullanabilirsiniz.<br /><br /> **Output**<br /><br /> `Output`: `float3`<br /> Geçerli pikselin öğesinden kameraya.|Yok.|
|**Eğim alanı ışık yönü**|Işığın, geçerli pikselin Eğim alanındaki bir ışık kaynağından saçıldığı yönü tanımlayan vektör.<br /><br /> Bunu, eğim alanındaki aydınlatma ve Yansımalı Katkıları hesaplamak için kullanabilirsiniz.<br /><br /> **Çıkış:**<br /><br /> `Output`: `float3`<br /> Geçerli pikselin öğesinden bir ışık kaynağına.|Yok.|
|**Dünya normali**|Dünya alanındaki geçerli pikselin yüzey normali.<br /><br /> Bunu, dünya alanındaki aydınlatma katkılarını ve yansımalarını hesaplamak için kullanabilirsiniz.<br /><br /> **Output**<br /><br /> `Output`: `float3`<br /> Geçerli pikselin yüzey normali.|Yok.|
|**Dünya konumu**|Dünya alanındaki geçerli pikselin konumu.<br /><br /> **Output**<br /><br /> `Output`: `float4`<br /> Geçerli pikselin konumu.|Yok.|