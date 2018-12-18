---
title: 'DA0013: Yüksek oranda String.Split veya String.Substring kullanımı | Microsoft Docs'
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
- vs.performance.13
- vs.performance.rules.DAAvoidStringSubstr
- vs.performance.DA0013
- vs.performance.rules.DA0013
helpviewer_keywords:
- vs.performance.13
- vs.performance.rules.DA0013
ms.assetid: f501f423-bef9-4e08-bf96-c9ac9957e5a2
caps.latest.revision: 19
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b469a9931ea48b60e49f9b5210e4e4db05fda362
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51807485"
---
# <a name="da0013-high-usage-of-stringsplit-or-stringsubstring"></a>DA0013: Yüksek oranda String.Split veya String.Substring kullanımı
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Kural Kimliği | DA0013 |  
| Kategori |. NET Framework Kullanım Kılavuzu |  
| Profil oluşturma yöntemlerini | Örnekleme |  
| İleti | String.Split ve String.Substring işlevlerin kullanımını azaltmayı deneyin. |  
| Kural türü | Uyarı |  
  
## <a name="cause"></a>Sebep  
 System.String.Split veya System.String.Substring yöntemlere yapılan çağrılar, profil oluşturma verilerinin önemli bir parçasıdır. Bir dizedeki bir alt dizenin bulunup bulunmadığını test ediyorsanız System.String.IndexOf veya System.String.IndexOfAny kullanmayı düşünün.  
  
## <a name="rule-description"></a>Kural Tanımı  
 Split yöntemini bir dize nesnesi üzerinde çalışır ve özgün alt dizeler içeren yeni bir dizi dize döndürür. İşlevi, döndürülen dizi nesnesi için bellek ayırır ve bulduğu her dizi öğesi için yeni bir dize nesnesi ayırır. Benzer şekilde, Substr yöntemi, bir dize nesnesi üzerinde çalışır ve istenen alt dize için eşdeğer bir gruba yeni bir dize döndürür.  
  
 Bellek ayırmalarını yönetmek, uygulamanızda önemliyse, alternatifler String.Split ve String.Substr yöntemlerine göz önünde bulundurun. Örneğin, dize sınıfının yeni bir örneğini oluşturmadan bir karakter dizesi içinde belirli bir alt dizeyi bulmak için IndexOf veya IndexOfAny yöntemi kullanabilirsiniz.  
  
## <a name="how-to-investigate-a-warning"></a>Bir uyarı araştırma  
 Hata Listesi penceresindeki iletiyi gitmek için çift tıklatın [işlev Ayrıntıları görünümü](../profiling/function-details-view.md) örnekleme, profil verileri. En sık rastlanan System.String.Split veya System.String.Substr yöntemleri kullanabilmesine programın bölümlerini bulmak için arama işlevleri inceleyin. Mümkünse, dize sınıfının yeni bir örneğini oluşturmadan bir karakter dizesi içinde belirli bir alt dizeyi bulmak için IndexOf veya IndexOfAny yöntemi kullanın.



