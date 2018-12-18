---
title: 'DA0001: Birleştirmeler için StringBuilder kullanın | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.performance.DA0001
- vs.performance.rules.DAUseStringBuilder
- vs.performance.1
- vs.performance.rules.DA0001
ms.assetid: a7cc7613-ad5f-48c8-bd2b-56372cc12dfc
caps.latest.revision: 19
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4cbfbabc96273f6a39a69888025b80d12103dd4b
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51803324"
---
# <a name="da0001-use-stringbuilder-for-concatenations"></a>DA0001: Birleştirmeler için StringBuilder kullanın
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio 2017 ile ilgili en son belgeler için bkz. [DA0001: birleştirmeler için StringBuilder kullanın](https://docs.microsoft.com/visualstudio/profiling/da0001-use-stringbuilder-for-concatenations) docs.microsoft.com'da.  
  
|||  
|-|-|  
|Kural Kimliği|DA0001|  
|Kategori|.NET framework kullanımı|  
|Profil oluşturma yöntemleri|Örnekleme<br /><br /> İzleme|  
|İleti|Dize birleştirmeleri için StringBuilder kullanmayı düşünün|  
|İleti türü|Uyarı|  
  
## <a name="cause"></a>Sebep  
 System.String.Concat çağrıları, profil oluşturma verilerinin önemli bir kısmı aynıdır. Kullanmayı <xref:System.Text.StringBuilder> birden çok kesimi dizeleri oluşturmak için sınıf.  
  
## <a name="rule-description"></a>Kural Tanımı  
 A <xref:System.String> nesne değişmez. Bu nedenle, yeni bir dize nesnesi ve çöp toplama özgün dize değişiklik oluşturur. String.Concat açıkça çağırmak ya da dize birleştirme işleçleri kullanın Bu aynı, davranıştır + veya +=... Program performansı düşebilir, ne zaman karakter dizesine sıkı bir döngüde eklenir gibi bu yöntemleri sık denir.  
  
 StringBuilder sınıfını değişebilir bir nesne olan ve System.String, bu sınıfın bir örneği değiştiren StringBuilder yöntemlerin çoğu, aynı örneğe bir başvuru döndürür. Karakterleri eklemek veya bir StringBuilder örneği için metin ekleyin ve kaldırın veya karakter örneğinde yeni bir örneğini tahsis etme ve özgün örneği silme gerek kalmadan değiştirin.  
  
## <a name="how-to-investigate-a-warning"></a>Bir uyarı araştırma  
 Hata Listesi penceresindeki iletiyi gitmek için çift tıklatın [işlev Ayrıntıları görünümü](../profiling/function-details-view.md) örnekleme, profil verileri. Dize birleştirme en sık kullanılan olarak kullanabilmesine programın bölümlerini bulur. StringBuilder sınıfını sık dize birleştirme işlemleri dahil olmak üzere, karmaşık dize işlemeleri için kullanın.  
  
 Dizeler ile çalışma hakkında daha fazla bilgi için [dize işlemleri](http://go.microsoft.com/fwlink/?LinkId=177816) bölümünü [bölüm 5 - yönetilen kod performansını iyileştirme](http://go.microsoft.com/fwlink/?LinkId=177817) Microsoft Patterns and Practices Kitaplığı'nda.

