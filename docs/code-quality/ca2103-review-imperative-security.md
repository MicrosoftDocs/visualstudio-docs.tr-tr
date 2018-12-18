---
title: 'CA2103: Kesinlik temelli güvenliği gözden geçirin'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2103
- ReviewImperativeSecurity
helpviewer_keywords:
- CA2103
- ReviewImperativeSecurity
ms.assetid: d24fde71-bdf6-46c0-8965-9a73dc33c1aa
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0f8975e3118e9907bf4688efe93dc60646b6d80b
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2018
ms.locfileid: "45547710"
---
# <a name="ca2103-review-imperative-security"></a>CA2103: Kesinlik temelli güvenliği gözden geçirin

|||
|-|-|
|TypeName|ReviewImperativeSecurity|
|CheckId|CA2103|
|Kategori|Microsoft.Security|
|Yeni Değişiklik|Yeni|

## <a name="cause"></a>Sebep
 Bir yöntem zorunlu güvenliği kullanır ve durum bilgileri veya dönüş değerlerini kullanarak izin oluşturursa, izin talebi etkin durumdayken değişebilir.

## <a name="rule-description"></a>Kural açıklaması
 Kesinlik temelli güvenlik izinleri ve güvenlik eylemleri bildirime dayalı güvenlik öznitelikleri, Eylemler ve izinler meta verileri depolamak için kullandığı karşılaştırıldığında kod yürütülürken belirtmek için yönetilen nesneleri kullanır. Kesinlik temelli güvenlik çok esnektir çünkü bir izin nesnesi durumunu ayarlamak ve çalışma zamanına kadar kullanılabilir olmayan bilgileri kullanarak güvenlik eylemleri seçin. İle birlikte esneklik eylemin yürürlükte olduğu sürece, bir izin durumu değil kalan belirlemek için kullandığınız çalışma zamanı bilgileri değişmeden riskini ortaya çıktı.

 Bildirime dayanan güvenliği mümkün olduğunca kullanın. Bildirim temelli talepleri anlamak kolaydır.

## <a name="how-to-fix-violations"></a>İhlaller nasıl düzeltilir?
 Kesinlik temelli güvenlik taleplerini izin durumu izni kullanılmakta olduğu sürece, değiştirebileceğiniz hakkında bilgi kullanmayan emin olmak için gözden geçirin.

## <a name="when-to-suppress-warnings"></a>Uyarılar bastırıldığında
 Değişen veri iznini kullanmayan varsa bu kuraldan bir uyarıyı bastırmak güvenlidir. Ancak, bildirim temelli eşdeğerine kesinlik temelli talep değiştirmek iyidir.

## <a name="see-also"></a>Ayrıca bkz.

- [Güvenli Kodlama Yönergeleri](/dotnet/standard/security/secure-coding-guidelines)
- [Veri ve Modelleme](/dotnet/framework/data/index)