---
title: Nokta, çift doğrusal, Üçlü ve yön bağımlı doku filtreleme | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 57d14fc9-b5f7-45ee-9717-48086886742d
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ef054b1773b1f0d07e21ec25cb326594a4d3b2d9
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51791247"
---
# <a name="point-bilinear-trilinear-and-anisotropic-texture-filtering-variants"></a>Nokta, Çift Doğrusal, Üçlü Doğrusal ve Yön Bağımlı Doku Filtreleme Çeşitleri
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Uygun bir doku örnekleyici filtreleme modu geçersiz kılar.  
  
## <a name="interpretation"></a>Yorumu  
 Farklı performans maliyetleri ve görüntü kalitesi doku örnekleme farklı yöntemleri vardır. Maliyet artan sırada — ve görsel kaliteyi artırma — filtre modu:  
  
1. (En uygun maliyetli, en kötü görsel kalite) filtreleme noktası  
  
2. Filtreleme çeşitleri  
  
3. Üçlü filtreleme  
  
4. Anizotropik filtreleme (en pahalı, en iyi visual kalite)  
  
   Her değişken performans maliyeti önemli ya da daha fazla yoğun filtreleme modları ile artırır, maliyeti daha yüksek görüntü kalitesini karşı Tart. Değerlendirmesini temel alan, görsel kaliteyi artırmak için ek performans maliyetleri kabul edebilir ya da daha yüksek bir kare hızını elde etmek için veya diğer yollarla kullanabilirsiniz performans geri kazanmak için görsel kaliteyi azaldıkça kabul edebilirsiniz.  
  
   Performans maliyeti göz ardı edilebilir ya da filtre modu bağımsız olarak sabit mi olduğunu fark ederseniz — Örneğin, hedeflediğiniz GPU olduğunda gölgelendirici aktarım hızı ve bellek bant genişliği miktarda — anizotropik filtreleme en iyi görüntü elde etmek için kullanmayı düşünün uygulamanızda kalitesi.  
  
## <a name="remarks"></a>Açıklamalar  
 Bu çeşitleri için çağrılar üzerinde örnekleyici durumları geçersiz kılma `ID3D11DeviceContext::PSSetSamplers` uygulama tarafından sağlanan örnekleyici'nın filtre modu bunlardan biri olduğu:  
  
- `D3D11_FILTER_MIN_MAG_MIP_POINT`  
  
- `D3D11_FILTER_MIN_MAG_POINT_MIP_LINEAR`  
  
- `D3D11_FILTER_MIN_POINT_MAG_LINEAR_MIP_POINT`  
  
- `D3D11_FILTER_MIN_POINT_MAG_MIP_LINEAR`  
  
- `D3D11_FILTER_MIN_LINEAR_MAG_MIP_POINT`  
  
- `D3D11_FILTER_MIN_LINEAR_MAG_POINT_MIP_LINEAR`  
  
- `D3D11_FILTER_MIN_MAG_LINEAR_MIP_POINT`  
  
- `D3D11_FILTER_MIN_MAG_MIP_LINEAR`  
  
- `D3D11_FILTER_ANISOTROPIC`  
  
  İçinde **noktası doku filtreleme** uygulama tarafından sağlanan filtre modu ile variant değiştirilir `D3D11_FILTER_MIN_MAG_MIP_POINT`; **çeşitleri doku filtreleme** bunu ile değiştirilir variant `D3D11_FILTER_MIN_MAG_LINEAR_MIP_POINT`; ve **Üçlü doku filtreleme** bunu ile değiştirilir variant `D3D11_FILTER_MIN_MAG_MIP_LINEAR`.  
  
  İçinde **doku Anizotropik filtreleme** uygulama tarafından sağlanan filtre modu ile variant değiştirilir `D3D11_FILTER_ANISOTROPIC`, ve en fazla Anisotropy 16 olarak ayarlanır.  
  
## <a name="restrictions-and-limitations"></a>Kısıtlamalar ve sınırlamalar  
 Direct3D'de, en fazla bir anisotropy 2 x özellik düzeyi 9.1 belirtir. Çünkü **doku Anizotropik filtreleme** 16 x anisotropy özel olarak kullanma girişiminde değişken, bir özellik düzeyinde 9.1 cihazda çerçeve analizi çalıştırıldığında kayıttan yürütme başarısız olur. Bu sınırlama tarafından etkilenen Çağdaş cihazlar, ARM tabanlı Surface RT ve Surface 2 Windows tabletler içerir. Yine de bazı durumlarda bilgisayarları da etkilenebilir, ancak yaygın olarak geçersiz olarak kabul edilmeleri ve giderek daha fazla seyrek bulunabilir eski Gpu'lar.  
  
## <a name="example"></a>Örnek  
 **Noktası doku filtreleme** değişken bu kodu kullanarak yeniden oluşturduğunuzda:  
  
```  
D3D11_SAMPLER_DESC sampler_description;  
  
// ... other sampler description setup ...  
  
sampler_description.Filter = D3D11_FILTER_MIN_MAG_MIP_POINT;  
  
d3d_device->CreateSamplerState(&sampler_desc, &sampler);  
d3d_context->PSSetSamplers(0, 1, &sampler  
```  
  
## <a name="example"></a>Örnek  
 **Çeşitleri doku filtreleme** değişken bu kodu kullanarak yeniden oluşturduğunuzda:  
  
```  
D3D11_SAMPLER_DESC sampler_description;   
  
// ... other sampler description setup ...  
  
sampler_description.Filter = D3D11_FILTER_MIN_MAG_LINEAR_MIP_POINT;  
  
d3d_device->CreateSamplerState(&sampler_desc, &sampler);  
d3d_context->PSSetSamplers(0, 1, &sampler  
```  
  
## <a name="example"></a>Örnek  
 **Üçlü doku filtreleme** değişken bu kodu kullanarak yeniden oluşturduğunuzda:  
  
```  
D3D11_SAMPLER_DESC sampler_description;   
  
// ... other sampler description setup ...  
  
sampler_description.Filter = D3D11_FILTER_MIN_MAG_MIP_LINEAR;  
  
d3d_device->CreateSamplerState(&sampler_desc, &sampler);  
d3d_context->PSSetSamplers(0, 1, &sampler  
```  
  
## <a name="example"></a>Örnek  
 **Doku Anizotropik filtreleme** değişken bu kodu kullanarak yeniden oluşturduğunuzda:  
  
```  
D3D11_SAMPLER_DESC sampler_description;   
  
// ... other sampler description setup ...  
  
sampler_description.Filter = D3D11_FILTER_ANISOTROPIC;  
sampler_description.MaxAnisotropy = 16;  
  
d3d_device->CreateSamplerState(&sampler_desc, &sampler);  
d3d_context->PSSetSamplers(0, 1, &sampler  
```



