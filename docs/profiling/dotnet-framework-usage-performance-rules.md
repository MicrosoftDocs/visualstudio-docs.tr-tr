---
title: .NET framework kullanımı performans kuralları | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: ab573755-6370-48aa-853d-a7321c424c79
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1903b61fce39bdd68b471472530857d720bac906
ms.sourcegitcommit: 4cd4aef53e7035d23e7d1d0f66f51ac8480622a1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/05/2018
ms.locfileid: "34766028"
---
# <a name="net-framework-usage-performance-rules"></a>.NET Framework kullanımı performans kuralları
.NET Framework kullanımı kategorideki performans kuralları iyileştirilebilir ve ayrıca çöp toplama ve performans sorunları için araştırılan kilit çakışması gibi daha genel kullanım düzenlerini tanımlamak belirli yöntemleri tanımlar.  
  
|||  
|-|-|  
|[DA0001: Birleştirmeler için StringBuilder kullanın](../profiling/da0001-use-stringbuilder-for-concatenations.md)|Çağrılar <xref:System.String.Concat(System.String,System.String)?displayProperty=fullName> profil oluşturma verileri önemli bir kısmının şunlardır. Kullanmayı <xref:System.Text.StringBuilder> birden çok parçalı dizelerden oluşturmak için sınıfı.|  
|[DA0005: Sık kullanılan GC2 koleksiyonları](../profiling/da0005-frequent-gc2-collections.md)|.NET bellek nesneleri görece yüksek sayıda nesil 2 çöp toplama kazanılır. Çok fazla kısa süreli nesne 1. nesil koleksiyonu yaşarsanız, bellek yönetimi maliyetini kolayca aşırı haline gelebilir.|  
|[DA0006: Değer türleri için Eşittir()'lerin üzerine yaz](../profiling/da0006-override-equals-parens-for-value-types.md)|Çağrılar `Equals` yöntemi veya ortak değer türünün eşitlik işleçleri olan önemli bir profil oluşturma verileri oranı. Daha verimli bir yöntem uygulayın.|  
|[DA0007: Denetim akışı için özel durumlar kullanmaktan kaçının](../profiling/da0007-avoid-using-exceptions-for-control-flow.md)|.NET Framework özel durum işleyicileri yüksek oranda profil oluşturma verileri çağrılır. Oluşturulan özel durum sayısını azaltmak için diğer denetim akışı mantığı kullanmayı düşünün.|  
|[DA0010: Pahalı GetHashCode](../profiling/da0010-expensive-gethashcode.md)|Çağrılar `GetHashCode` türü yöntemi olan profil oluşturma verileri önemli bir kısmının veya `GetHashCode` yöntemi bellek ayırır. Yöntem karmaşıklığını azaltın.|  
|[DA0011: Pahalı CompareTo](../profiling/da0011-expensive-compareto.md)|`CompareTo` Pahalı türü yöntemi veya yöntem bellek ayırır. Karmaşıklığını azaltmak `CompareTo` yöntemi.|  
|[DA0012: Önemli miktarda Yansıma](../profiling/da0012-significant-amount-of-reflection.md)|Çağrılar <xref:System.Reflection?displayProperty=fullName> gibi yöntemler <xref:System.Reflection.IReflect.InvokeMember%2A> ve <xref:System.Reflection.IReflect.GetMember%2A> veya türü yöntemleri gibi <xref:System.Type.InvokeMember%2A> profil oluşturma verileri önemli bir kısmının şunlardır. Mümkün olduğunda, bu yöntemleri bağımlı derlemeleri yöntemleri için erken bağlama değiştirerek göz önünde bulundurun.|  
|[DA0013: Yüksek oranda String.Split veya String.Substring kullanımı](../profiling/da0013-high-usage-of-string-split-or-string-substring.md)|Çağrılar <xref:System.String.Split%2A?displayProperty=fullName> veya <xref:System.String.Substring%2A> profil oluşturma verileri önemli bir kısmını yöntemleridir. Kullanmayı <xref:System.String.IndexOf%2A> veya <xref:System.String.IndexOfAny%2A> substring dize varlığı için sınıyorsanız.|  
|[DA0018: 32 bitlik Uygulama işlem tarafından yönetilen bellek sınırlarında çalışıyor](../profiling/da0018-32-bit-application-running-at-process-managed-memory-limits.md)|Profil oluşturma çalışması sırasında toplanan sistem verilerini, .NET Framework bellek yığınlardaki Yönetilen yığın bir 32 bit işlemde ulaşabileceği en büyük boyutu yaklaşıldığında gösterir. .NET bellek profili oluşturma yöntemi kullanarak yeniden ve uygulama tarafından yönetilen kaynaklarının kullanımını en iyi duruma getirme profil göz önünde bulundurun.|  
|[DA0021: Yüksek oranda Gen 1 çöp koleksiyonları](../profiling/da0021-high-rate-of-gen-1-garbage-collections.md)|.NET bellek nesneleri görece yüksek sayıda nesil 1 çöp toplama kazanılır. Çok kısa süreli nesneleri oluşturma 0 koleksiyonu yaşarsanız, bellek yönetimi maliyetini kolayca aşırı haline gelebilir.|  
|[DA0022: Yüksek oranda Gen 2 çöp koleksiyonları](../profiling/da0022-high-rate-of-gen-2-garbage-collections.md)|Çok sayıda .NET bellek nesneleri nesil 2 çöp toplama kazanılır. Çok fazla kısa süreli nesne 1. nesil koleksiyonu yaşarsanız, bellek yönetimi maliyetini kolayca aşırı haline gelebilir. Kilit çakışmaları oranı kuralı DA0005 üst eşik değerini aştığında, bu kural ateşlenir.|  
|[DA0023: Yüksek GC CPU süresi](../profiling/da0023-high-gc-cpu-time.md)|Profil oluşturma sırasında toplanan sistem performans verileri, toplam uygulama işleme süresi ile karşılaştırıldığında, çöp toplama harcanan süreyi önemli olduğunu gösterir.|  
|[DA0024: Aşırı GC CPU süresi](../profiling/da0024-excessive-gc-cpu-time.md)|Profil oluşturma sırasında toplanan sistem performans verileri, toplam uygulama işleme süresi ile karşılaştırıldığında, çöp toplama harcanan süreyi aşırı yüksek olduğunu gösterir. Çöp toplama harcanan süre miktarını kural DA0023 üst eşik değerini aştığında bu kural ateşlenir.|  
|[DA0038: Yüksek oranda kilit çakışmaları](../profiling/da0038-high-rate-of-lock-contentions.md)|Toplanan sistem performans verilerini profil oluşturma verileri, önemli ölçüde yüksek oranda kilit çakışmaları uygulama yürütmesi sırasında oluştuğunu gösterir. Yeniden çekişmeleri nedenini bulmak için eşzamanlılık profili oluşturma yöntemi kullanarak profil oluşturmayı düşünün.|  
|[DA0039: Çok yüksek oranda kilit çakışmaları](../profiling/da0039-very-high-rate-of-lock-contentions.md)|Toplanan sistem performans verilerini profil oluşturma verileri, bir aşırı yüksek oranda kilit çakışmaları uygulama yürütmesi sırasında oluştuğunu gösterir. Yeniden çekişmeleri nedenini bulmak için eşzamanlılık profili oluşturma yöntemi kullanarak profil oluşturmayı düşünün. Kilit çakışmaları oranı kuralı DA0038 üst eşik değerini aştığında, bu kural ateşlenir.|