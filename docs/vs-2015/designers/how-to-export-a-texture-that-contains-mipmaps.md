---
title: "Nasıl yapılır: Mipmap'leri içeren dokuyu dışa aktarma | Microsoft Docs"
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3d1ad14b-44fb-4cf0-a995-5e2f60026524
caps.latest.revision: 9
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 847655d04359fa795f878ea921e69b1b5cd16460
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49811743"
---
# <a name="how-to-export-a-texture-that-contains-mipmaps"></a>Nasıl yapılır: Mipmap'leri İçeren Dokuyu Dışa Aktarma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Görüntü içeriği ardışık düzeni, projenizin yapı evresinin parçası olarak bir kaynak görüntüden mipmap'leri oluşturabilirsiniz. Ne zaman değil her MIP düzeyinin görüntü içeriğini el ile belirtmeniz gerekir — bazı efektler elde etmek için yapabileceğiniz gibi — derleme zamanında mipmap oluşturma sağlar mipmap içeriğinin asla eşitleme dışı olur ve mipmap'leri oluşturmanın performans maliyetini ortadan kaldırır Çalışma zamanında.  
  
 Bu belgede şu faaliyetler gösterilmiştir:  
  
-   Görüntü içeriği ardışık düzeni tarafından işlenecek kaynak görüntüyü yapılandırma.  
  
-   Mipmaps oluşturmak için görüntü içeriği ardışık yapılandırma.  
  
## <a name="exporting-mipmaps"></a>Mipmapları dışa aktarma  
 Mipeşlem, 3D oyun veya uygulamada dokulu yüzeyler için otomatik ekran alanı düzeyi ayrıntı düzeyi sağlar. Bu dokunun tamamı her zaman, örneklenen alt örneklenen gerekmez böylece bir dokunun alt örneklenen sürümlerini önceden hesaplayarak bir oyunun veya uygulamanın işleme performansını geliştirir.  
  
#### <a name="to-export-a-texture-that-has-mipmaps"></a>Mipmap içeren bir dokuyu dışarı aktarmak için  
  
1. Temel doku ile başlayın. Varolan bir resim dosyasını yükleyin ya da açıklandığı gibi oluşturmak [nasıl yapılır: temel doku oluşturma](../designers/how-to-create-a-basic-texture.md). Mipmap'leri desteklemek için genişliği ve yüksekliği ikinin kuvveti, örneğin, 64 x 64, 256 x 256 veya 512 x 512 aynı güç olan olan bir doku belirtin.  
  
2. Görüntü içeriği ardışık düzeni tarafından işlenir böylece yeni oluşturduğunuz doku dosyasını yapılandırarak. İçinde **Çözüm Gezgini**, yeni oluşturduğunuz doku dosyası için kısayol menüsünü açın ve ardından **özellikleri**. Üzerinde **yapılandırma özellikleri**, **genel** sayfasında **öğesi türü** özelliğini **görüntü içeriği ardışık düzeni**. Emin olun **içerik** özelliği **Evet** ve **yapıdan hariç tut** ayarlanır **Hayır**ve ardından  **Uygulama** düğmesi. **Görüntü içeriği ardışık düzeni** yapılandırma özellik sayfası görüntülenir.  
  
3. Mipmaps oluşturmak için görüntü içeriği ardışık yapılandırın. Üzerinde **yapılandırma özellikleri**, **görüntü içeriği ardışık düzeni**, **genel** sayfasında **Mips üret** özelliğini**Evet (/ generatemips)**.  
  
4. Seçin **Tamam** düğmesi.  
  
   Proje oluşturduğunuzda, görüntü içeriği ardışık düzeni kaynak görüntüyü çalışma biçiminden MIP düzeyleri de dahil olmak üzere, belirtilen ve sonuç projenin çıkış dizinine kopyalanır çıkış biçimine dönüştürür.



