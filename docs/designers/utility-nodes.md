---
title: Yardımcı Program Düğümleri
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-designers
ms.topic: reference
ms.assetid: ff732221-b731-424c-ad5b-82ef5f21dff5
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b4d3371001c3df3b5233562ce7b30e711ed12d4c
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/26/2018
ms.locfileid: "31918211"
---
# <a name="utility-nodes"></a>Yardımcı programı düğümler

Gölgelendirici Tasarımcısı'nda düzgün diğer kategorilere uymayan ortak, yararlı gölgelendirici hesaplamalar yardımcı programı düğümleri temsil eder. Bazı yardımcı programı düğümler vektörlerinin birlikte ekleyerek veya sonuçları koşullu seçme gibi basit işlemleri ve diğerleri aydınlatma Katkıları popüler aydınlatma modelleri göre bilgi işlem gibi karmaşık işlemleri gerçekleştirin.

## <a name="utility-node-reference"></a>Yardımcı programı düğümü başvurusu

|Düğüm|Ayrıntılar|Özellikler|
|----------|-------------|----------------|
|**Vektör ekleme**|Vektör belirtilen girişleri birlikte ekleyerek oluşturur.<br /><br /> **Giriş:**<br /><br /> `Vector`: `float`, `float2`, veya `float3`<br /> Eklenecek değerleri.<br /><br /> `Value to Append`: `float`<br /> Eklenecek değer.<br /><br /> **Çıktı:**<br /><br /> `Output`: `float2`, `float3`, veya `float4` giriş türüne bağlı olarak `Vector`<br /> Yeni vektörü.|Yok.|
|**Fresnel**|Normal belirtilen yüzeyine göre Fresnel sonbaharda dışı hesaplar.<br /><br /> Ne kadar yakından geçerli piksel yüzey normal görünüm vektörü ile örtüşür sonbaharda dışı Fresnel değeri ifade eder. Vektörler hizalanır işlevin sonucu 0 olur; sonucu vektörlerinin daha az benzer hale geldikçe artırır ve vektörlerinin resme olduğunda maksimum ulaşır. Geçerli piksel yönünü ve kamera arasındaki ilişkiyi dayalı bir efekt fazla veya az görünür yapmak için kullanabilirsiniz.<br /><br /> **Giriş:**<br /><br /> `Surface Normal`: `float3`<br /> Geçerli piksel Eğim alanında tanımlanan geçerli piksel yüzey normal. Bu, normal normal eşleme olduğu gibi görünen yüzeyini perturb için kullanabilirsiniz.<br /><br /> **Çıktı:**<br /><br /> `Output`: `float`<br /> Geçerli piksel yansımasını.|**Üs**<br /> Fresnel sonbaharda dışı hesaplamak için kullanılan üs.|
|**If**|Koşullu bileşen başına üç olası sonuçları birini seçer. Koşul iki belirtilen giriş arasındaki ilişkiyi tarafından tanımlanır.<br /><br /> Sonuç her bileşen için ilk iki girdi ilgili bileşenler arasındaki ilişki göre üç olası sonuçları birinin ilgili bileşen seçilir.<br /><br /> **Giriş:**<br /><br /> `X`: `float`, `float2`, `float3`, veya `float4`<br /> Karşılaştırılacak taraftaki değeri.<br /><br /> `Y`: aynı giriş olarak yazın `X`<br /> Karşılaştırmak için sağ taraftaki değeri.<br /><br /> `X > Y`: aynı giriş olarak yazın `X`<br /> Ne zaman seçilen değerleri `X` değerinden daha büyük `Y`.<br /><br /> `X = Y`: aynı giriş olarak yazın `X`<br /> Ne zaman seçilen değerleri `X` eşittir `Y`.<br /><br /> `X < Y`: aynı giriş olarak yazın `X`<br /> Ne zaman seçilen değerleri `X` olan değerinden `Y`.<br /><br /> **Çıktı:**<br /><br /> `Output`: `float3`<br /> Seçilen bileşen başına neden.|Yok.|
|**Lambert**|Geçerli piksel Lambert aydınlatma modele göre rengini normal belirtilen yüzeyini kullanarak hesaplar.<br /><br /> Bu renk ortam rengi ve doğrudan ışık altında dağıtma aydınlatma Katkıları toplamıdır. Ortam rengi dolaylı aydınlatma toplam katkı yakın ancak düz ve ek aydınlatma yardımı olmadan Mat arar. Dağıtma aydınlatma şekli ve derinliği nesneye eklemenize yardımcı olur.<br /><br /> **Giriş:**<br /><br /> `Surface Normal`: `float3`<br /> Geçerli piksel Eğim alanında tanımlanan geçerli piksel yüzey normal. Bu, normal normal eşleme olduğu gibi görünen yüzeyini perturb için kullanabilirsiniz.<br /><br /> `Diffuse Color`: `float3`<br /> Geçerli piksel dağıtma rengini genellikle **nokta rengi**. Herhangi bir giriş verdiyse, varsayılan beyaz değerdir.<br /><br /> **Çıktı:**<br /><br /> `Output`: `float3`<br /> Geçerli piksel dağıtma rengi.|Yok.|
|**Maske vektör**|Belirtilen vektör maskeleri bileşenleri.<br /><br /> Bu, belirli bir renk kanalları bir renk değerinden kaldırmak için veya belirli bileşenlerini sonraki hesaplamalar üzerinde bir etkisi bırakılmasını engellemek için kullanabilirsiniz.<br /><br /> **Giriş:**<br /><br /> `Vector`: `float4`<br /> Vektör maskesi.<br /><br /> **Çıktı:**<br /><br /> `Output`: `float4`<br /> Maskeli vektörü.|**Kırmızı / X**<br /> **Yanlış** maskelemek kırmızı (x) bileşeni; Aksi halde, **doğru**.<br /><br /> **Yeşil / Y**<br /> **Yanlış** maskelemek yeşil (y) bileşeni; Aksi halde, **doğru**.<br /><br /> **Mavi / Z**<br /> **Yanlış** maskelemek mavi (z) bileşeni; Aksi halde, **doğru**.<br /><br /> **Alpha / W**<br /> **Yanlış** maskelemek alfa (w) bileşeni; Aksi halde, **doğru**.|
|**Yansıma vektör**|Yansıma vektör kamera konumlarına göre Eğim boşluk, geçerli piksel için hesaplar.<br /><br /> Yansımaları, cubemap koordinatları ve aynasal aydınlatma Katkıları hesaplamak için bunu kullanabilirsiniz<br /><br /> **Giriş:**<br /><br /> `Tangent Space Surface Normal`: `float3`<br /> Geçerli piksel Eğim alanında tanımlanan geçerli piksel yüzey normal. Bu, normal normal eşleme olduğu gibi görünen yüzeyini perturb için kullanabilirsiniz.<br /><br /> **Çıktı:**<br /><br /> `Output`: `float3`<br /> Yansıma vektörü.|Yok.|
|**Aynasal**|Phong aydınlatma modele göre aynasal aydınlatma katkı normal belirtilen yüzeyini kullanarak hesaplar.<br /><br /> Aynasal aydınlatma nesneye, örneğin, su, plastik veya metals parlak, yansıtıcı bir görünümünü sağlar.<br /><br /> **Giriş:**<br /><br /> `Surface Normal`: `float3`<br /> Geçerli piksel Eğim alanında tanımlanan geçerli piksel yüzey normal. Bu, normal normal eşleme olduğu gibi görünen yüzeyini perturb için kullanabilirsiniz.<br /><br /> **Çıktı:**<br /><br /> `Output`: `float3`<br /> Renk payını aynasal vurgular.|Yok.|