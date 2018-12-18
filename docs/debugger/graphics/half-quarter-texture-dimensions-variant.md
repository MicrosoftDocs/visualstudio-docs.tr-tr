---
title: Yarı Çeyrek doku boyutları çeşidi | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 282e9bbb-51aa-4cd0-8e5c-0901268c29e5
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 94820b2930bbe689c37b90443ac007b137f162d6
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49870204"
---
# <a name="halfquarter-texture-dimensions-variant"></a>Yarı/Çeyrek doku boyutları çeşidi
Doku boyutlarını hedefleri işlenmeyebilir dokular üzerinde azaltır.  
  
## <a name="interpretation"></a>Yorumu  
 Daha küçük dokular daha az bellek kaplar ve bu nedenle daha az bellek bant genişliği tüketebilir ve GPU'nun doku önbelleğinin Basıncı azaltın. Ancak, özellikle bunlar yakından 3B Sahne görüntülenebilir veya büyütme altında görüntülenen zaman, daha az ayrıntılı daha düşük bir görüntü kalitesini neden olabilir.  
  
 Bu değişken, bir büyük bir performans kazancı gösteriyorsa, uygulamanızın çok fazla bellek bant genişliği, doku önbelleğe verimsiz kullanan veya her ikisi de kullandığı belirtebilirsiniz. Doku kullanılabilir bellekten daha fazlasını GPU sistem belleği disk belleğine alınacak dokular neden kaplayabilir olduğunu gösterebilir.  
  
 Uygulamanız çok fazla bellek bant genişliği ya da verimsiz doku önbelleğinin kullanıyorsa, dokular, ancak yalnızca, mip eşlemeleri için uygun dokular etkinleştirmeyi düşünün sonra boyutunu küçültmeyi düşünün. Daha küçük dokular gibi daha az bellek bant genişliği MIP eşlemeli dokular tüketen — bunlar daha fazla GPU bellek kaplayan olsa da — ve artışı önbellek kullanımı, ancak doku ayrıntı azaltmak yok. Sistem belleği disk belleğine alınacak dokular bellek kullanımının artmasına neden olduğunda mip eşlemeleri öneririz.  
  
 Kullanılabilir alandan daha fazla GPU bellek, doku kaplayabilir, dokular, ancak yalnızca uygun doku sıkıştırma dikkate almanız sonra boyutunu küçültmeyi düşünün. Daha küçük dokular gibi sıkıştırılmış dokular daha az bellek kaplar ve sistem bellek sayfasına ihtiyacınızı azaltır, ancak kendi rengi güvenilirlik azalır. Sıkıştırma içeriğine bağlı olarak tüm dokular için uygun değildir — Örneğin, önemli olanlar küçük bir alanı varyasyonu renk — ancak birçok doku için kendi boyutunu küçültmeyi daha iyi genel görüntü kalitesini sıkıştırma koruyabilirsiniz.  
  
## <a name="remarks"></a>Açıklamalar  
 Doku boyutlarını üzerinde yapılan her çağrı sınırlı `ID3D11Device::CreateTexture2D` kaynak doku oluşturur. Doku boyutlarını D3D11_TEXTURE2D_DESC nesneden olduğunda özellikle azaltılır `pDesc` işlemede kullanılan; olan bir doku açıklar:  
  
- Yalnızca D3D11_BIND_SHADER_RESOURCE bayrağı ayarlanmış BindFlags üye var.  
  
- D3D11_RESOURCE_MISC_TILE_POOL bayrağı veya (döşenmiş kaynakları değil boyutlandırılır) D3D11_RESOURCE_MISC_TILED bayrağı ayarlanmış MiscFlags üye yok.  
  
- Bir işleme hedefi doku biçimi destekleniyor — D3D11_FORMAT_SUPPORT_RENDER_TARGET tarafından belirlenen şekilde — doku boyutunu azaltmak için gerekli olan. İşleme hedefleri olarak desteklenmeyen olsa bile BC1, BC2 ve BC3 biçimleri de desteklenir.  
  
  İlk veri uygulama tarafından sağlanmazsa, doku oluşturmadan önce bu değişken doku verilere uygun boyutta ölçeklendirir. İlk veri BC1, BC2 veya BC3 gibi blok sıkıştırılmış bir biçimde sağlanırsa, çözülmüş, ölçeklendirilebilir ve daha küçük bir doku oluşturmak için kullanılmadan önce yeniden kodlanmış. (Blok tabanlı sıkıştırma yapısını ek kod çözme-ölçeklendirme-kodlama işlemi neredeyse her zaman blok sıkıştırılmış bir doku değil önceden kodlanmış doku ölçeklendirilmiş bir sürümünden oluşturulduğunda daha düşük görüntü kalitesini neden anlamına gelir.)  
  
  Mip eşlemeleri için doku etkinleştirilirse, değişken mip düzeyi sayısı buna uygun olarak azaltır — üç boyutlu ölçeklendirme, bir yarı boyutlu ölçeklerken daha az ya da iki daha az.  
  
## <a name="example"></a>Örnek  
 Bu değişken dokular çağırmadan önce çalışma zamanında yeniden boyutlandırır `CreateTexture2D`. Üretim kodu için bu yaklaşım karşı daha fazla disk alanı tam boyutlu dokuları tükettiği için ek bir adım yükleme süreleri uygulamanızda artırabildiğinden öneririz — özellikle sıkıştırılmış dokular gerektiren önemli hesaplama kodlamak için kaynaklar. Bunun yerine, bir Resim Düzenleyicisi veya derleme işlem hattınızı parçası olan resim işlemci kullanarak çevrimdışı, doku yeniden boyutlandırma öneririz. Bu yaklaşımların disk alanı gereksinimlerini azaltmak ve uygulamanızdaki çalışma zamanı ek yükü ortadan kaldırmak ve daha fazla işleme süresi en iyi görüntü kalitesini küçültme veya, doku sıkıştırma tutabildiğiniz göze.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Mip-map oluşturma çeşidi](mip-map-generation-variant.md)   
 [BC Doku Sıkıştırma Çeşidi](bc-texture-compression-variant.md)