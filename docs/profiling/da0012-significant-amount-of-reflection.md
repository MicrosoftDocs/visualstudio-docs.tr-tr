---
title: 'DA0012: Önemli miktarda yansıma | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.rules.DAReflection
- vs.performance.12
- vs.performance.rules.DA0012
- vs.performance.DA0011
ms.assetid: c92a1d76-21fa-426e-8b1b-a3c08e9bcbca
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 191edf9cc6a3dc9ff177b075e2967cb328afc9c5
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49893929"
---
# <a name="da0012-significant-amount-of-reflection"></a>DA0012: Önemli miktarda Yansıma

|||  
|-|-|  
|Kural Kimliği|DA0012|  
|Kategori|.NET framework kullanımı|  
|Profil oluşturma yöntemleri|Örnekleme|  
|İleti|Yansıma aşırı kullanıyor olabilirsiniz. Bu pahalı bir işlemdir.|  
|Kural türü|Uyarı|  

## <a name="cause"></a>Sebep  
 System.Reflection yöntemleri InvokeMember ve GetMember gibi veya türü yöntemleri MemberInvoke gibi profil oluşturma verilerinin önemli bir kısmı çağrılarıdır. Mümkün olduğunda, erken bağlama yöntemlerine bağımlı derlemelerin bu yöntemler yerine göz önünde bulundurun.  

## <a name="rule-description"></a>Kural açıklaması  
 Yansıma, uygulamanızın bağımlı bir çalışma zamanı derleme geç bağlama gerçekleştirmek veya oluşturmak ve yeni türler çalışma zamanında dinamik olarak yürütmek için kullanılan .NET Framework'ün esnek bir özelliğidir. Ancak, sık kullanılan veya sıkı Döngülerde adlı bu teknikler performansı düşürebilir.  

 Daha fazla bilgi için [yansıma ve geç bağlama](http://go.microsoft.com/fwlink/?LinkId=177826) bölüm 5 bölümüne — geliştirme yönetilen kod performansını iyileştirme .NET uygulama performansı ve ölçeklenebilirlik toplu uygulamaları ve Microsoft Patterns MSDN Kitaplığı.  

## <a name="how-to-investigate-a-warning"></a>Bir uyarı araştırma  
 Hata Listesi penceresindeki iletiyi gitmek için çift tıklatın [işlev Ayrıntıları görünümü](../profiling/function-details-view.md) profil oluşturma verilerinin. .NET yansıma API'lerin kullanımını en sık yaptığınız program bölümleri bulmak için System.Type veya System.Reflection yöntemini çağırma işlevlerini inceleyin. Meta veri döndüren yöntemler kullanmaktan kaçının. Uygulamanızın performans kritik olduğunda, geç bağlama ve türleri dinamik olarak çalışma zamanında oluşturma kullanmaktan kaçının gerekebilir.