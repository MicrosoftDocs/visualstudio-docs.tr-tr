---
title: 16bpp işleme hedef biçim çeşidi | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 24b22ad9-5ad0-4161-809a-9b518eb924bf
caps.latest.revision: 8
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bf00bf536e5f1ee140a818ee59c66703906860f0
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51727636"
---
# <a name="16bpp-render-target-format-variant"></a>16bpp İşleme Hedef Biçim Çeşidi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Piksel biçimlendirmek için DXGI_FORMAT_B5G6R5_UNORM tüm ayarlar, işleme hedefleri ve arabellek yedekleyin.  
  
## <a name="interpretation"></a>Yorumu  
 İşleme hedefi veya geri arabelleği genellikle B8G8R8A8_UNORM gibi bir 32bpp (32 bit / piksel) biçimi kullanır. 32bpp biçimleri, çok miktarda bellek bant genişliği tüketebilir. B5G6R5_UNORM biçimi 32bpp biçimlerinin boyutunda bir 16bpp biçimde olduğundan, bunu kullanan baskısı bellek bant genişliği, ancak daha az renk uygunluk, hafifletmek.  
  
 Bu değişken, bir büyük bir performans kazancı gösteriyorsa, bu büyük olasılıkla uygulamanızı çok fazla bellek bant genişliği tüketir gösterir. Profili oluşturulan çerçeve overdraw önemli ölçüde düşebilir veya çok sayıda alfa karıştırma içeren performans artışı özellikle bildirilebilir.  
  
 Uygulamanız tarafından işlenen sahneler türlerini yüksek kaliteli renk üretimi gerektirmeyen, alfa kanalı için işleme hedefi gerektirmeyen ve kesintisiz gradyanlar genellikle içermeyen — daha az renk altında yapıtları bant oluşturma için açık olan uygunluk — bellek bant genişliği kullanımını azaltmak için 16bpp işleme hedef biçim kullanmayı düşünün.  
  
 Yüksek kaliteli renk çoğaltılması ya da bir alfa kanalı uygulamanızda işlenen Sahne gerektirir ya da kesintisiz gradyanlar ortak, bellek bant genişliği kullanımını azaltmak için diğer stratejiler göz önünde — Örneğin, overdraw veya alfa karıştırma miktarını azaltmayı framebuffer boyutunu azaltma veya sıkıştırmayı etkinleştirme veya kendi boyutlarını azaltmak daha az bellek bant genişliği tüketmeye doku kaynakları değiştirme. Her zamanki şekilde resmi kalite herhangi birini bu iyileştirmeler ile gelen dengelemeler düşünmek zorunda.  
  
 Uygulamanızı bir 16bpp arka arabellek geçiş yapmasını avantaj elde edecektir, ancak bir parçası, takas zinciri DXGI_FORMAT_B5G6R5_UNORM desteklenen arka arabellek biçimi kullanılarak oluşturulan takas zincirleri için olmadığı için ek adımlar uygulamanız sahip `D3D11CreateDeviceAndSwapChain` veya `IDXGIFactory::CreateSwapChain`. Bunun yerine, kullanarak B5G6R5_UNORM biçimi işleme hedefi oluşturmak kullandığınız `CreateTexture2D` ve bunun yerine işlemek için. Ardından, takas zinciri üzerinde mevcut çağırmadan önce takas zinciri arka arabelleği üzerine işleme hedefi bir tam ekran dört işleme hedefi olarak, kaynak doku ile çizerek kopyalayın. Bu bazı bellek bant genişliği tüketir fazladan bir adım olsa da, bunlar 16bpp işleme hedef etkilediğinden çoğu oluşturma işlemi daha az bant genişliği tüketir; ardından bu işleme hedefi için takas zinciri arka arabelleği kopyalayarak tüketilen daha fazla bant genişliği kaydederse, işleme performansı geliştirildi.  
  
 Döşenmiş işleme tekniklerini GPU mimarileri framebuffer daha büyük bir kısmını her kutucuğun yerel framebuffer önbellekte sığabilen 16bpp framebuffer biçimi kullanarak önemli performans avantajlarını görebiliyorum. Döşenmiş işleme mimarisi, bazen ahizeleri mobil ve tablet bilgisayarlar Gpu'lar bulunur; Bu özel dışında nadiren görünürler.  
  
## <a name="remarks"></a>Açıklamalar  
 İşleme hedef biçim üzerinde yapılan her çağrı için DXGI_FORMAT_B5G6R5_UNORM sıfırlanır `ID3D11Device::CreateTexture2D` işleme hedefi oluşturur. Özellikle, pDesc içinde geçirilen D3D11_TEXTURE2D_DESC nesnesi bir işleme hedefi açıkladığında biçimi geçersiz; Yani:  
  
-   BindFlags üyesi, ayarlayın D3D11_BIND_REDNER_TARGET bayrağı vardır.  
  
-   BindFlags üye temizlenmiş D3D11_BIND_DEPTH_STENCIL bayrağı vardır.  
  
-   Kullanım üye D3D11_USAGE_DEFAULT için ayarlanır.  
  
## <a name="restrictions-and-limitations"></a>Kısıtlamalar ve sınırlamalar  
 Alfa kanalını B5G6R5 biçim olmadığından, alfa içerik bu değişken tarafından korunmaz. Uygulamanızın işleme, işleme hedefi bir alfa kanalına gerektiriyorsa, yalnızca B5G6R5 biçimine geçiş yapamazsınız.  
  
## <a name="example"></a>Örnek  
 **16bpp işleme hedef biçim** değişken çoğaltılamaz kullanılarak oluşturulan işleme hedefleri için `CreateTexture2D` aşağıdakine benzer bir kod kullanarak:  
  
```  
D3D11_TEXTURE2D_DESC target_description;  
  
target_description.BindFlags = D3D11_BIND_RENDER_TARGET;  
target_description.Format = DXGI_FORMAT_B5G6R5_UNORM;  
d3d_device->CreateTexture2D(&target_description, nullptr, &render_target);  
```



