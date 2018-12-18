---
title: "Nasıl yapılır: Mipmap'leri İçeren Dokuyu Dışa Aktarma"
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: 3d1ad14b-44fb-4cf0-a995-5e2f60026524
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 67eb30f340afcd2f8e631170fc84fd00f5a9d43c
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49831335"
---
# <a name="how-to-export-a-texture-that-contains-mipmaps"></a>Nasıl yapılır: mipmap'leri içeren dokuyu dışa aktarma

Görüntü içeriği ardışık düzeni, projenizin yapı evresinin parçası olarak bir kaynak görüntüden mipmap'leri oluşturabilirsiniz. Bazı efektler elde etmek için bazı durumlarda, her MIP düzeyinin görüntü içeriğini el ile belirtmeniz gerekir. Her MIP düzeyinin görüntü içeriğini el ile belirtmek ihtiyacınız kalmadığında, derleme zamanında mipmap oluşturma mipmap içeriğinin asla eşitleme dışı duruma sağlar. Çalışma zamanında mipmap'leri oluşturmanın performans maliyetini ortadan kaldırır.

Bu makalede ele alınmıştır:

- Görüntü içeriği ardışık düzeni tarafından işlenecek kaynak görüntüyü yapılandırma.

- Mipmaps oluşturmak için görüntü içeriği ardışık yapılandırma.

## <a name="export-mipmaps"></a>Mipmap dışarı aktarma

Mipeşlem, 3D oyun veya uygulamada dokulu yüzeyler için otomatik ekran alanı düzeyi ayrıntı düzeyi sağlar. Bu, bir dokunun alt örneklenen sürümlerini önceden hesaplayarak bir oyunun veya uygulamanın işleme performansını geliştirir. Dokunun tamamı olmak zorunda değil anlamına gelir her zaman bu alt örneklenen alt örneklenen sürümlerini önceden bilgi işlem örneklenir.

### <a name="to-export-a-texture-that-has-mipmaps"></a>Mipmap içeren bir dokuyu dışarı aktarmak için

1. Temel doku ile başlayın. Varolan bir resim dosyasını yükleyin ya da açıklandığı gibi oluşturmak [nasıl yapılır: temel doku oluşturma](../designers/how-to-create-a-basic-texture.md). Mipmap'leri desteklemek için genişliği ve yüksekliği ikinin kuvveti, örneğin, 64 x 64, 256 x 256 veya 512 x 512 aynı güç olan olan bir doku belirtin.

2. Görüntü içeriği ardışık düzeni tarafından işlenir böylece yeni oluşturduğunuz doku dosyasını yapılandırarak. İçinde **Çözüm Gezgini**, oluşturduğunuz doku dosyası için kısayol menüsünü açın ve ardından **özellikleri**. Üzerinde **yapılandırma özellikleri** > **genel** sayfasında **öğesi türü** özelliğini **görüntü içeriği ardışık düzeni**. Emin olun **içerik** özelliği **Evet** ve **yapıdan hariç tut** ayarlanır **Hayır**. Seçin **uygulamak**.

   **Görüntü içeriği ardışık düzeni** yapılandırma özellik sayfası görüntülenir.

3. Mipmaps oluşturmak için görüntü içeriği ardışık yapılandırın. Üzerinde **yapılandırma özellikleri** > **görüntü içeriği ardışık düzeni** > **genel** sayfasında **Mipsüret** özelliğini **Evet (/ generatemips)**.

4. Seçin **Tamam**.

Proje oluşturduğunuzda, görüntü içeriği ardışık düzeni kaynak görüntüyü çalışma biçiminden MIP düzeyleri de dahil olmak üzere, belirttiğiniz çıkış biçimine dönüştürür. Sonuç projenin çıkış dizinine kopyalanır.