---
title: 0 x-2 x-4 x MSAA çeşitleri | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 668a6603-5082-4c78-98e6-f3dc871aa55b
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8e661823a07945c22679832dc716ad2f25f4f6aa
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51793782"
---
# <a name="0x2x4x-msaa-variants"></a>0 x / 2 x / 4 x MSAA çeşitleri
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Geçersiz kılmalar birden çok örnek düzgünleştirme (MSAA) ayarları tüm işleme hedefleri ve takas zincirleri.  
  
## <a name="interpretation"></a>Yorumu  
 Birden çok örnek düzgünleştirme, her pikselin içinde birden çok konumda örnekleri katılarak visual kalite yükselir; Daha fazla örnek MSAA daha yüksek düzeylerde yararlanın ve MSAA, yalnızca bir örnek pikselin Merkezi'nden alınır. Genellikle uygulamanızda MSAA özelliklerini etkinleştirme vardır ancak belirgin bir büyüklükteki işleme performansını, ancak bazı iş yüklerinin altında veya belirli Gpu'lar üzerindeki maliyeti, neredeyse hiçbir etkisi ile önceki.  
  
 Uygulamanız etkin MSAA zaten varsa, daha düşük MSAA çeşitleri var olan ve daha üst düzey MSAA doğurur göreli performans maliyetini gösterir. Özellikle, 0 x MSAA değişken MSAA olmadan performanslarını gösterir.  
  
 Uygulamanız zaten etkin MSAA yoksa, 2 x MSAA ve 4 x MSAA çeşitleri bunları uygulamanızda etkinleştirme göreli performans maliyetini gösterir. Maliyet çalışarak düşük olduğunda, uygulamanızın resim kalitesini artırmak MSAA etkinleştirme göz önünde bulundurun.  
  
> [!NOTE]
>  Donanımınız için tüm biçimler MSAA tam olarak desteklemeyebilir. Bu çeşitleri birini çalışan olamaz etrafında bir donanım sınırlama karşılaşırsanız, kendi sütununda bir performans Özet Tablo boş olur ve bir hata iletisi oluşturulur.  
  
## <a name="remarks"></a>Açıklamalar  
 Örnek sayısı ve örnek kalitesi bağımsız değişkenler için çağrılar üzerinde bu çeşitleri geçersiz kılma `ID3DDevice::CreateTexture2D` işleme hedefleri oluşturun. Özellikle, bu parametreleri geçersiz olduğunda:  
  
- `D3D11_TEXTURE2D_DESC` Geçirilen nesne `pDesc` olan bir işleme hedefi; açıklar:  
  
  -   BindFlags üyesi D3D11_BIND_TARGET bayrağı veya D3D11_BIND_DEPTH_STENCIL bayrağı ayarlanmış sahiptir.  
  
  -   Kullanım üye D3D11_USAGE_DEFAULT için ayarlanır.  
  
  -   CPUAccessFlags üye 0 olarak ayarlanır.  
  
  -   MipLevels üye 1 olarak ayarlayın.  
  
- İstenen işleme tarafından belirlenen şekilde hedef biçimi (D3D11_TEXTURE2D_DESC::Format üyesi) için cihaz istenen örnek sayısı (0, 2 veya 4) ve örnek kalitesi (0) destekler. `ID3D11Device::CheckMultisampleQualityLevels`.  
  
  Daha sonra D3D11_TEXTURE2D_DESC::BindFlags üye ayarlanmış D3D_BIND_SHADER_RESOUCE veya D3D11_BIND_UNORDERED_ACCESS bayrağı varsa, doku iki sürümü oluşturulur; işleme hedefi olarak kullanılmak üzere işaretli Bu bayraklar ilk vardır ve diğer MSAA olmayan doku ilk sürümü için Çözümle arabellek olarak görev yapacak dokunulmadan Bu bayraklar. Sırasız erişim için veya bir gölgelendirici kaynak olarak bir MSAA doku kullanarak geçerli olmayacaktır, çünkü bu gereklidir; Örneğin, bir MSAA olmayan doku beklediğiniz gibi olduğundan hatalı sonuçlar üzerinde çalışan bir gölgelendirici karşılaşırsınız. Ardından değişken MSAA olmayan ikincil doku oluşturduysa MSAA işleme hedef cihaz bağlamında unset olduğunda içeriği MSAA olmayan doku çözümlenir. Benzer şekilde, MSAA işleme her hedef bir gölgelendirici kaynak olarak bağlı veya bir sırasız erişim Görünümü'nde kullanılır, çözümlenen MSAA olmayan doku yerine bağlıdır.  
  
  Ayrıca geçersiz kılma kullanılarak oluşturulan tüm takas zincirleri MSAA ayarlarını bu çeşitleri `IDXGIFactory::CreateSwapChain`, `IDXGIFactory2::CreateSwapChainForHwnd`, `IDXGIFactory2::CreateSwapChainForCoreWindow`, `IDXGIFactory2::CreateSwapChainForComposition`, ve `ID3D11CreateDeviceAndSwapChain`.  
  
  Bu değişikliklerin net etkisiyle tüm işleme bir MSAA işleme hedefi gerçekleştirilir ancak uygulamanızın bunlardan birini kullanıp kullanmadığını işleme hedefler ya da takas zinciri arabellekler gölgelendirici kaynağı görünümü veya sırasız erişim görünümü olarak ve ardından veri örneklenen olan çözümlenen gelen , işleme hedefinin MSAA olmayan kopyalama.  
  
## <a name="restrictions-and-limitations"></a>Kısıtlamalar ve sınırlamalar  
 Direct3D11 içinde MSAA dokular MSAA olmayan dokular daha büyük/küçük harf kısıtlanır. Örneğin, çağıramazsınız `ID3D11DeviceContext::UpdateSubresource` MSAA doku ve arama `ID3D11DeviceContext::CopySubresourceRegion` kaynak kaynak ve hedef kaynak örnek kalitesini ve örnek sayısı, bu değişken bir MSAA ayarları geçersiz kılan kurduğunuzda gerçekleşebilir eşleşmezse başarısız Kaynak ancak diğer.  
  
 Kayıttan yürütme bu çakışma türlerini algıladığında, amaçlanan bir davranış çoğaltmak için en iyi çaba İlkesi kolaylaştırır, ancak sonuçları tam olarak eşleşmesi mümkün olmayabilir. Bunun etkilerine yanlış bilgilendirici bir şekilde bu çeşitleri performansını seyrek olsa da, olası — Örneğin, ne zaman piksel gölgelendiricisi akış denetimi belirlenir kesin bir doku içeriğini tarafından — çünkü çoğaltılmış doku özdeş içeriğe sahip olmayabilir.  
  
## <a name="example"></a>Örnek  
 İşleme hedefleri kullanarak oluşturduğunuz için bu çeşitleri üretilebilmeleri `ID3D11Device::CreateTexture2D` aşağıdakine benzer bir kod kullanarak:  
  
```  
D3D11_TEXTURE2D_DESC target_description;  
target_description.BindFlags = D3D11_BIND_RENDER_TARGET;  
target_description.SampleDesc.Count = 4; // 4x MSAA, can be 2 or 0 instead  
target_description.SampleDesc.Quality = 0;  
d3d_device->CreateTexture2D(&target_description, nullptr, &render_target);  
```  
  
## <a name="example"></a>Örnek  
 Veya IDXGISwapChain::CreateSwapChain veya D3D11CreateDeviceAndSwapChain aşağıdakine benzer bir kod kullanarak kullanılarak oluşturulan takas zincirleri için:  
  
```  
DXGI_SWAP_CHAIN_DESC chain_description;  
chain_description.SampleDesc.Count = 4; // 4x MSAA, can be 2 or 0 instead  
chain_description.SampleDesc.Quality = 0;  
  
// Call IDXGISwapChain::CreateSwapChain or D3D11CreateDeviceAndSwapChain, etc.  
```



