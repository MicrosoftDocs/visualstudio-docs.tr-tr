---
title: 'Nasıl yapılır: kesme noktaları XSLT ile kullanma'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-xml-tools
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 430b7f14f35506b45fe73be47d056cdd7b6a9c95
ms.sourcegitcommit: 697162f54d3c4e30df702fd0289e447e211e3a85
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/25/2018
ms.locfileid: "34548365"
---
# <a name="how-to-use-breakpoints-with-xslt"></a>Nasıl yapılır: kesme noktaları XSLT ile kullanma

XSLT stil sayfasını veya XML kaynak belge kesme noktaları ayarlayabilirsiniz. Ayarlarsanız bir kesme noktası etikette yürütme kesme başladığında, kaynak satırı bilgileri içeren sonraki ifadeye taşınır.

Daha fazla bilgi için bkz: [temelleri hata ayıklama: kesme noktaları](../debugger/using-breakpoints.md).

## <a name="set-a-breakpoint-in-a-style-sheet"></a>Bir stil sayfanızda bir kesme noktası ayarlama

Kesme noktaları başlangıç etiketleri, bitiş etiketleri ve XSLT stil sayfasını metin düğümleri üzerinde ayarlanabilir. Kesme noktaları ayrıca kod bir betik bloğu içinde ayarlanabilir.

### <a name="to-set-a-breakpoint-in-a-style-sheet"></a>Bir stil sayfanızda bir kesme noktası ayarlamak için

1.  Stil sayfası XML düzenleyicisinde açın.

2.  Kesme noktası konumda imleci getirin, sağ tıklayın, fareyle **kesme noktası**, tıklatıp **kesme noktası Ekle**.

3.  Gözat düğmesine (**...** ) üzerinde **giriş** belge penceresinin alan.

4.  XML kaynak belge bulun ve tıklatın **açık**.

     XSLT dönüşümü için kullanılan kaynak belge dosyasını ayarlar.

5.  Tıklatın **hata ayıklama XSL** XML Düzenleyicisi araç çubuğunda.

## <a name="set-a-breakpoint-in-an-xml-source-document"></a>Bir XML kaynağını belgede bir kesme noktası ayarlayın

Kesme noktaları öğeleri, öznitelikleri, düğüm ad, açıklama, işlem yönergesi ve XML kaynak belgesinin metin düğümleri ayarlayabilirsiniz. Belge düğümü veya üst öğesinden devralınan bir ad alanı düğümünde bir kesme noktası ayarlanamıyor.

### <a name="to-set-a-breakpoint-in-an-xml-source-document"></a>Bir XML kaynağını belgesinde bir kesme noktası ayarlamak için

1.  XML belgesi XML düzenleyicisinde açın.

2.  Kesme noktası konumda imleci getirin, sağ tıklayın, fareyle **kesme noktası**, tıklatıp **kesme noktası Ekle**.

3.  Gözat düğmesine (**...** ) üzerinde **stil** belge penceresinin alan.

4.  XML kaynak belge bulun ve tıklatın **açık**.

     XSLT dönüşümü için kullanılan kaynak belge dosyasını ayarlar.

5.  Tıklatın **hata ayıklama XSL** XML Düzenleyicisi araç çubuğunda.

## <a name="see-also"></a>Ayrıca bkz.

- [İzlenecek yol: bir XSLT stil sayfası hata ayıklama](../xml-tools/walkthrough-debug-an-xslt-style-sheet.md)