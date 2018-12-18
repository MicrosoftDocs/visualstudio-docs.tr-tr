---
title: 'CA1726: Tercih edilen terimleri kullanın'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- UsePreferredTerms
- CA1726
helpviewer_keywords:
- UsePreferredTerms
ms.assetid: 642b2acd-3a33-4d1f-b0a7-67073ae73be2
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c81bd543a6695adcea37db5ab8570ff7749c0160
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2018
ms.locfileid: "45551460"
---
# <a name="ca1726-use-preferred-terms"></a>CA1726: Tercih edilen terimleri kullanın

|||
|-|-|
|TypeName|UsePreferredTerms|
|CheckId|CA1726|
|Kategori|Microsoft.Naming|
|Yeni Değişiklik|-Derlemelerini tetiklendiğinde sonu<br /><br /> Tür parametrelerinde tetiklendiğinde bölünemez-|

## <a name="cause"></a>Sebep

Dışarıdan görünen bir tanımlayıcının adı, tercih edilen terim varolduğunda alternatif olarak bir terim içerir. Ya da terimi bayrağı veya bayrak adı içerir.

## <a name="rule-description"></a>Kural açıklaması

Bu kural, bir tanımlayıcı belirteçlere ayrıştırır. Her tek belirteç ve her bir bitişik belirteci çift bileşimi, kural ve özel sözlükler kullanım dışı bölümünde yerleşik koşulları karşılaştırılır. Aşağıdaki tabloda, kural ve kendi tercih edilen alternatif yerleşik koşulları gösterir.

|Eski terimi|Tercih edilen terim|
|-------------------|--------------------|
|`Arent`|`AreNot`|
|`Cancelled`|`Canceled`|
|`Cant`|`Cannot`|
|`ComPlus`|`EnterpriseServices`|
|`Couldnt`|`CouldNot`|
|`Didnt`|`DidNot`|
|`Doesnt`|`DoesNot`|
|`Dont`|`DoNot`|
|`Flag` veya `Flags`|Hiçbir değişiklik terimi yoktur. Kullanmayın.|
|`Hadnt`|`HadNot`|
|`Hasnt`|`HasNot`|
|`Havent`|`HaveNot`|
|`Indices`|`Indexes`|
|`Isnt`|`IsNot`|
|`LogIn`|`LogOn`|
|`LogOut`|`LogOff`|
|`Shouldnt`|`ShouldNot`|
|`SignOn`|`SignIn`|
|`SignOff`|`SignOut`|
|`Wasnt`|`WasNot`|
|`Werent`|`WereNot`|
|`Wont`|`WillNot`|
|`Wouldnt`|`WouldNot`|
|`Writeable`|`Writable`|

## <a name="how-to-fix-violations"></a>İhlaller nasıl düzeltilir?
 Bu kural ihlalini düzeltmek için tercih edilen alternatif terimiyle terimi değiştirin.

## <a name="when-to-suppress-warnings"></a>Uyarılar bastırıldığında
 Yalnızca tanımlayıcı adını kasıtlıdır ve özgün terimi yerine tercih edilen terim özellikle ilgili bu kuraldan bir uyarıyı gizler.

## <a name="related-rules"></a>İlgili kuralları
 [Adlandırma Uyarıları](../code-quality/naming-warnings.md)