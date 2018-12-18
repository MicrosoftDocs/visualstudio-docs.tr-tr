---
title: BC doku sıkıştırma çeşidi | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 2d0f5305-585b-4b01-bc9a-7a32d6e991da
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 919191ec29ad45a8385d32b82de99d44fcdaa2ea
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49922451"
---
# <a name="bc-texture-compression-variant"></a>BC Doku Sıkıştırma Çeşidi
Etkinleştirir sıkıştırma B8G8R8X8, B8G8R8A8 veya R8G8B8A8 çeşididir bir piksel biçimi dokular hakkında engelleyin.  
  
## <a name="interpretation"></a>Yorumu  
 Blok tabanlı sıkıştırma biçimleri BC1, BC2, ister ve BC3 görüntü biçimlerini sıkıştırılmamış ve bu nedenle önemli ölçüde daha az bellek bant genişliği kullanmak daha önemli ölçüde daha az bellek kaplar. Piksel başına 32 bit kullanan sıkıştırılmamış biçime karşılaştırıldığında 8:1 sıkıştırma (eski adıyla DXT1 da bilinir) BC1 ulaşır ve 4:1 (önceki adıyla DXT5 da bilinir) BC3 ulaşır. BC1 BC3 arasındaki fark, blok sıkıştırılmış bir alfa kanalı BC3 desteklese de BC1 bir alfa kanalı desteklemiyor ' dir. Yüksek sıkıştırma oranlarına rağmen görüntü kalitesini tipik dokular için küçük bir düşüş yoktur. Ancak, belirli türde bir doku sıkıştırma block — Örneğin, önemli olanlar küçük bir alanı varyasyonu rengi — kabul edilemez sonuçları olabilir.  
  
 Dokular, blok tabanlı sıkıştırma için uygundur ve renk uygunluk mükemmel yoksa, daha az bant genişliği tüketebilir ve bellek kullanımını azaltmak için bir blok sıkıştırılmış biçimi kullanarak göz önünde bulundurun.  
  
## <a name="remarks"></a>Açıklamalar  
 Yapılan her çağrı bir blok tabanlı sıkıştırma biçimini kullanarak doku sıkıştırma `ID3DDevice::CreateTexture2D` kaynak doku oluşturur. Özellikle, doku sıkıştırılmış olduğunda:  
  
- `D3D11_TEXTURE2D_DESC` Geçirilen nesne `pDesc` olan değişmeyen bir gölgelendirici kaynak; açıklar:  
  
  -   Yalnızca D3D11_BIND_SHADER_RESOURCE bayrağı ayarlanmış BindFlags üye var.  
  
  -   Kullanım üye D3D11_USAGE_DEFAULT ya da D3D11_USAGE_IMMUTABLE ayarlanır.  
  
  -   CPUAccessFlags üyesi (CPU erişim yok) 0 olarak ayarlanır.  
  
  -   (Hiçbir çok örnekli düzgünleştirme (MSAA)) 1 olarak ayarlayın, sayım üyesi SamplerDesc üye var.  
  
- İlk veri çağrısına sağlanan `CreateTexture2D`.  
  
  Desteklenen kaynak biçimleri ve bunların blok sıkıştırılmış biçimlerden aşağıda verilmiştir.  
  
|Özgün biçiminde (Başlangıç)|Sıkıştırılmış biçimi (Bitiş)|  
|------------------------------|------------------------------|  
|`DXGI_FORMAT_B8G8R8X8_UNORM`|BC1 (eski adıyla DXT1)|  
|`DXGI_FORMAT_B8G8R8X8_UNORM_SRGB`|BC1|  
|`DXGI_FORMAT_B8G8R8X8_TYPELESS`|BC1|  
|`DXGI_FORMAT_B8G8R8A8_UNORM`|BC3 (eski adıyla DXT5)|  
|`DXGI_FORMAT_B8G8R8A8_UNORM_SRGB`|BC3|  
|`DXGI_FORMAT_B8G8R8A8_TYPELESS`|BC3|  
|`DXGI_FORMAT_R8G8B8A8_UNORM`|BC3|  
|`DXGI_FORMAT_R8G8B8A8_UNORM_SRGB`|BC3|  
|`DXGI_FORMAT_R8G8B8A8_TYPELESS`|BC3|  
  
 Listede olmayan bir biçimde, doku varsa doku değiştirilmez.  
  
## <a name="restrictions-and-limitations"></a>Kısıtlamalar ve sınırlamalar  
 Bazen B8G8R8A8 veya R8G8B8A8 görüntü biçimlerini çeşitlemesi ile oluşturulan dokular alfa kanalı gerçekte kullanmadığınız, ancak veya kullanılan olup olmadığını bilmek değişken için bir yolu yoktur. Alfa kanalını kullanılır durumda doğruluğunu sağlamak için değişken her zaman daha az verimli BC3 biçime şu biçimlerden kodlar. Grafik çerçevesi analizi değişken daha etkili BC1 biçimi kullanabilmesi için alfa kanalı kullanmadığınızda B8G8R8X8 görüntü biçimi çeşitlemesi kullanarak uygulamanızın olası işleme performansını Bu değişken ile daha iyi anlamanıza yardımcı olabilir.  
  
## <a name="example"></a>Örnek  
 Bu değişken blok-dokular çağırmadan önce çalışma zamanında sıkıştırır `CreateTexture2D`. Bu yaklaşım üretim kodu için karşı daha fazla disk alanı sıkıştırılmamış dokular tükettiği için ve blok tabanlı sıkıştırma önemli gerektirdiğinden ek adım uygulamanız yükleme sürelerini önemli ölçüde artırabildiğinden öneririz kodlanacak hesaplama kaynaklarını sağlar. Bunun yerine, bir Resim Düzenleyicisi'ni veya derleme işlem hattınızı parçası olan görüntü işlemci kullanarak çevrimdışı, doku sıkıştırma öneririz. Bu yaklaşımların disk alanı gereksinimlerini azaltmak, çalışma zamanı uygulamanızda ek yükü ortadan kaldırır ve daha fazla işleme süresi en iyi görüntü kalitesini tutabildiğiniz göze.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Yarı/Çeyrek Doku Boyutları Çeşidi](half-quarter-texture-dimensions-variant.md)