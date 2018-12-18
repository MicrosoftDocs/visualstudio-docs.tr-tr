---
title: 'DA0013: Yüksek oranda String.Split veya String.Substring kullanımı | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.13
- vs.performance.rules.DAAvoidStringSubstr
- vs.performance.DA0013
- vs.performance.rules.DA0013
helpviewer_keywords:
- vs.performance.13
- vs.performance.rules.DA0013
ms.assetid: f501f423-bef9-4e08-bf96-c9ac9957e5a2
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 722277e65a30d8c40cc245123120650108ebc560
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49831464"
---
# <a name="da0013-high-usage-of-stringsplit-or-stringsubstring"></a>DA0013: Yüksek oranda String.Split veya String.Substring kullanımı

|||  
|-|-|  
|Kural Kimliği|DA0013|  
|Kategori|.NET framework Kullanım Kılavuzu|  
|Profil oluşturma yöntemleri|Örnekleme|  
|İleti|String.Split ve String.Substring işlevlerin kullanımını azaltmayı deneyin.|  
|Kural türü|Uyarı|  

## <a name="cause"></a>Sebep  
 System.String.Split veya System.String.Substring yöntemlere yapılan çağrılar, profil oluşturma verilerinin önemli bir parçasıdır. Bir dizedeki bir alt dizenin bulunup bulunmadığını test ediyorsanız System.String.IndexOf veya System.String.IndexOfAny kullanmayı düşünün.  

## <a name="rule-description"></a>Kural açıklaması  
 Split yöntemini bir dize nesnesi üzerinde çalışır ve alt dizeler özgün tutan yeni bir dizi dize döndürür. İşlevi, döndürülen dizi nesnesi için bellek ayırır ve bulduğu her dizi öğesi için yeni bir dize nesnesi ayırır. Benzer şekilde, Substr yöntemi, bir dize nesnesi üzerinde çalışır ve istenen alt dize için eşdeğer bir gruba yeni bir dize döndürür.  

 Bellek ayırmalarını yönetmek, uygulamanızda önemliyse, alternatifler String.Split ve String.Substr yöntemlerine göz önünde bulundurun. Örneğin, dize sınıfının yeni bir örneğini oluşturmadan bir karakter dizesi içinde belirli bir alt dizeyi bulmak için IndexOf veya IndexOfAny yöntemi kullanabilirsiniz.  

## <a name="how-to-investigate-a-warning"></a>Bir uyarı araştırma  
 İletide çift **hata listesi** gitmek için pencere [işlev Ayrıntıları görünümü](../profiling/function-details-view.md) örnekleme, profil verileri. En sık rastlanan System.String.Split veya System.String.Substr yöntemleri kullanabilmesine programın bölümlerini bulmak için arama işlevleri inceleyin. Mümkünse, dize sınıfının yeni bir örneğini oluşturmadan bir karakter dizesi içinde belirli bir alt dizeyi bulmak için IndexOf veya IndexOfAny yöntemi kullanın.