---
title: XSLT Varsayılan Şablonları
description: Stil sayfasında eşleşen açık şablon kuralı olmadığında XSLT işleme sırasında kullanılan XSLT varsayılan şablonları hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 773dd34e-67d3-4997-8df9-b71e7f880d88
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 74b4cfebc7a6160577f1e817c9171f2eae69533c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99874762"
---
# <a name="xslt-default-templates"></a>XSLT varsayılan şablonları

Stil sayfasında eşleşen açık şablon kuralı olmadığında XSLT işleme sırasında varsayılan bir şablon kullanılır. Ayrıca, yerleşik şablon kuralı olarak da adlandırılan varsayılan şablon, W3C XSLT 1,0 önerisi 5,8 bölümünde tanımlanmıştır. Varsayılan şablon, XSLT işlemcisinin bir düğümü işlemesini sağlar, bununla eşleşen açık bir şablon kuralı olmasa da. Ancak, yerleşik şablon kuralı stil sayfasında açıkça tanımlanmadığı için, bu durum beklenmedik veya kafa karıştırıcı XSLT dönüştürme sonuçlarına yol açabilir.

XSLT hata ayıklayıcısı şimdi XSLT varsayılan şablonlarının kodunu görüntüler. Bir XSLT dönüşümünde, varsayılan bir şablon kullanılıyorsa, hata ayıklayıcı varsayılan şablonu bir pencerede görüntüler. Bu, varsayılan şablonun kodunda ilerlemenize ve yönergeleri üzerinde kesme noktaları ayarlamanıza olanak sağlar.

## <a name="see-also"></a>Ayrıca bkz.

- [XSLT Hatalarını Ayıklama](../xml-tools/debugging-xslt.md)
