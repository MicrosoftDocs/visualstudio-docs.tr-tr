---
title: 'Nasıl yapılır: İş Akışı Tasarımcısında Aramayı kullanma'
description: Daha büyük, daha karmaşık iş akışları oluşturmayı kolaylaştırmak için, öğeleri anahtar sözcüğe göre bulmak için İş Akışı Tasarımcısı içinde arama yapmayı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: f42d3115-2ed2-4941-8f1e-92dac41c30fa
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 6fb30d4846c24638f87989d2a7a716df06b0523b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99894120"
---
# <a name="how-to-use-search-in-the-workflow-designer"></a>Nasıl yapılır: İş Akışı Tasarımcısında Aramayı kullanma

Daha büyük, daha karmaşık iş akışları oluşturmayı kolaylaştırmak için, öğeleri anahtar sözcüğe göre bulmak için İş Akışı Tasarımcısı içinde arama yapabilirsiniz. Tasarımcının değiştirme 'yi desteklemediğine unutmayın.

## <a name="quick-find"></a>Hızlı Bul

Hızlı bul, tasarımcıda aşağıdakileri bulur:

- <xref:System.Activities.Activity>Nesnelerin, <xref:System.Activities.Statements.FlowNode> nesnelerin, <xref:System.Activities.Statements.State> nesnelerin, geçişlerin ve diğer özel akış denetimi öğelerinin özellikleri.

- Değişkenler

- Bağımsız değişkenler

- İfadeler

### <a name="use-quick-find"></a>Hızlı bul kullanma

1. İş akışı Tasarımcısı açıkken, **CTRL + F** tuşlarına basın veya **Düzenle**  >  **Bul ve Değiştir '** i seçerek  >  **hızlı bul**' u seçin.

2. **Aranan metin kutusuna** arama terimini girin ve **Sonrakini Bul**' a tıklayın.

3. Arama terimi geçerli iş akışında bulunur. Aşağıdaki görüntüde, tasarımcıda bulunan bir etkinlik görünen adı gösterilmektedir:

   ![İş Akışı Tasarımcısı arama sonucu](../workflow-designer/media/designersearch.png)

## <a name="find-in-files"></a>Dosyalarda bul

Dosyalarda bul, XAML dosyaları da dahil olmak üzere iş akışı dosyalarındaki dizeleri bulur.

### <a name="use-find-in-files"></a>Dosyalarda bul kullanma

1. Visual Studio 'da **CTRL** + **SHIFT** + **F** tuşlarına basın veya **Düzenle** bul ' u  >  **ve**  >  **dosyalardaki bul** Değiştir ' i seçin.

2. **Aranan metin kutusuna** arama öğesini girin ve **Tümünü Bul**' a tıklayın.

3. Bulma sonucu **bul sonucu** görünümünde gösterilir. Bir sonuç öğesine çift tıklamak, iş akışı tasarımcısında eşleşmeyi içeren etkinliğe gider.