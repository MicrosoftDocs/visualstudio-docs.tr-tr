---
title: Yardımcı program düğümleri | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ff732221-b731-424c-ad5b-82ef5f21dff5
caps.latest.revision: 13
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 1d85735c5fb355163f2003a27a96675ed097d66e
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49174427"
---
# <a name="utility-nodes"></a>Yardımcı Program Düğümleri
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Gölgelendirici Tasarımcısı'nda diğer kategorilerde düzgünce uygun olmayan bir ortak, kullanışlı gölgelendirici hesaplamalarında yardımcı program düğümleri temsil eder. Bazı yardımcı program düğümleri vektörleri birlikte ekleyerek veya koşullu olarak sonuçları seçme gibi basit işlemler gerçekleştiren ve diğer popüler aydınlatma modelleri göre aydınlatma katkılarını bilgi işlem gibi karmaşık işlemleri gerçekleştirin.  
  
## <a name="utility-node-reference"></a>Yardımcı program düğüm başvurusu  
  
|Düğüm|Ayrıntılar|Özellikler|  
|----------|-------------|----------------|  
|**Vektör Ekle**|Belirtilen giriş birlikte ekleyerek bir vektör oluşturur.<br /><br /> **Giriş:**<br /><br /> `Vector`: `float`, `float2`, veya `float3`<br /> Eklemenin yapılacağı değerleri.<br /><br /> `Value to Append`: `float`<br /> Eklenecek değer.<br /><br /> **Çıkış:**<br /><br /> `Output`: `float2`, `float3`, veya `float4` giriş türüne bağlı olarak `Vector`<br /> Yeni vektör.|Yok.|  
|**Fresnel**|Hesaplar. Fresnel fall normal belirtilen yüzeyinde bağlı alma.<br /><br /> Fresnel fall dışı değer, geçerli pikselin yüzey normali görünüm vektörü ile ne kadar yakın örtüşür ifade eder. Vektörler hizalandığında, işlevin sonucu 0'dır; sonucu vektörler daha az benzer oldukça artar ve vektörler dikgen olduğunda en yüksek ulaşır. Bu, geçerli pikselin yönü ve kamera arasındaki ilişkiye bağlı bir efekti daha çok veya daha az belirgin hale getirmek için kullanabilirsiniz.<br /><br /> **Giriş:**<br /><br /> `Surface Normal`: `float3`<br /> Tanımlanan geçerli pikselin Eğim alanında geçerli pikselin yüzey normali. Bu, normal normal eşleme olduğu gibi görünen surface perturb için kullanabilirsiniz.<br /><br /> **Çıkış:**<br /><br /> `Output`: `float`<br /> Geçerli pikselin maskeleyen.|**Üs**<br /> Fresnel fall dışı hesaplamak için kullanılan üs.|  
|**If**|Koşullu olarak üç olası sonuçlarını bileşen her birini seçer. Koşulu, iki belirtilen giriş arasındaki ilişkiye göre tanımlanır.<br /><br /> Sonucun her bileşeni için ilk iki girişe karşılık gelen bileşenleri arasındaki ilişkiye bağlı potansiyel olarak üç sonuçtan birine karşılık gelen bileşen seçilir.<br /><br /> **Giriş:**<br /><br /> `X`: `float`, `float2`, `float3`, veya `float4`<br /> Karşılaştırmak için sol taraftaki değer.<br /><br /> `Y`: aynı tür giriş `X`<br /> Karşılaştırmak için sağ taraftaki değer.<br /><br /> `X > Y`: aynı tür giriş `X`<br /> Ne zaman seçilen değerlerin `X` büyüktür `Y`.<br /><br /> `X = Y`: aynı tür giriş `X`<br /> Ne zaman seçilen değerlerin `X` eşittir `Y`.<br /><br /> `X < Y`: aynı tür giriş `X`<br /> Ne zaman seçilen değerlerin `X` olduğu küçüktür `Y`.<br /><br /> **Çıkış:**<br /><br /> `Output`: `float3`<br /> Seçilen bileşen başına neden.|Yok.|  
|**Lambert**|Belirtilen yüzey normalini kullanarak göre Lambert aydınlatma modeli, geçerli pikselin rengini hesaplar.<br /><br /> Bu renk, ortam rengi ve doğrudan aydınlatma altında yayınık aydınlatma katkılarını toplamıdır. Ortam rengi, dolaylı Aydınlatmanın toplam katkısını eder, ancak düz ve donuk ek aydınlatma yardımı olmadan arar. Yayınık aydınlatma, bir nesneye şekil ve derinlik ekleme yardımcı olur.<br /><br /> **Giriş:**<br /><br /> `Surface Normal`: `float3`<br /> Tanımlanan geçerli pikselin Eğim alanında geçerli pikselin yüzey normali. Bu, normal normal eşleme olduğu gibi görünen surface perturb için kullanabilirsiniz.<br /><br /> `Diffuse Color`: `float3`<br /> Geçerli pikselin yayınık rengine genellikle **nokta rengi**. Varsayılan değer beyaz: sağlanan giriş yok ise.<br /><br /> **Çıkış:**<br /><br /> `Output`: `float3`<br /> Geçerli pikselin yayınık rengi.|Yok.|  
|**Vektörü Gizle**|Belirtilen vektör maskeleri bileşenleri.<br /><br /> Bu, bir renk değerinden belirli renk kanallarını kaldırmak ya da belirli bileşenlerin sonraki hesaplamalar üzerinde bir etkisi önlemek için kullanabilirsiniz.<br /><br /> **Giriş:**<br /><br /> `Vector`: `float4`<br /> Vektör maskesi.<br /><br /> **Çıkış:**<br /><br /> `Output`: `float4`<br /> Maskeli vektör.|**Kırmızı / X**<br /> **False** ; kırmızı (x) bileşenini gizlemek için Aksi takdirde, **True**.<br /><br /> **Yeşil / Y**<br /> **False** ; yeşil (y) bileşenini gizlemek için Aksi takdirde, **True**.<br /><br /> **Mavi / Z**<br /> **False** ; mavi (z) bileşenini gizlemek için Aksi takdirde, **True**.<br /><br /> **Alfa / W**<br /> **False** ; alfa (w) bileşenini gizlemek için Aksi takdirde, **True**.|  
|**Yansıma vektörü**|Kamera konumuna bağlı geçerli pikselin Eğim alanındaki için yansıma vektörü hesaplar.<br /><br /> Bunu, yansımaları, küp harita koordinatlarını ve Yansımalı aydınlatma katkılarını hesaplamak için kullanabilirsiniz<br /><br /> **Giriş:**<br /><br /> `Tangent Space Surface Normal`: `float3`<br /> Tanımlanan geçerli pikselin Eğim alanında geçerli pikselin yüzey normali. Bu, normal normal eşleme olduğu gibi görünen surface perturb için kullanabilirsiniz.<br /><br /> **Çıkış:**<br /><br /> `Output`: `float3`<br /> Yansıma vektörü.|Yok.|  
|**Yansımalı**|Belirtilen yüzey normalini kullanarak Phong aydınlatma modeli göre Yansımalı aydınlatma katkısını hesaplar.<br /><br /> Yansımalı aydınlatma, su, plastik veya maden satıcılarından bir nesneye parlak, yansıyan bir görünüm sağlar.<br /><br /> **Giriş:**<br /><br /> `Surface Normal`: `float3`<br /> Tanımlanan geçerli pikselin Eğim alanında geçerli pikselin yüzey normali. Bu, normal normal eşleme olduğu gibi görünen surface perturb için kullanabilirsiniz.<br /><br /> **Çıkış:**<br /><br /> `Output`: `float3`<br /> Renk katkısı Yansımalı vurgular.|Yok.|



