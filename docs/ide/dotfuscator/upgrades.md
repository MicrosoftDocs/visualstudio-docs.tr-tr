---
title: Dotfuscator Community Edition (CE) yükseltme
ms.date: 02/08/2017
ms.devlang: dotnet
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
keywords: Dotfuscator, Dotfuscator CE, PreEmptive, PreEmptive Solutions, PreEmptive koruma, koruma, community edition, gizleme, .NET, ücretsiz, Visual Studio 2017, yükseltme, komut satırı
helpviewer_keywords:
- PreEmptive Protection Dotfuscator
- Dotfuscator Community Edition
- Dotfuscator CE
- Dotfuscator
- obfuscation
- protection
- Dotfuscator upgrade
- upgrade Dotfuscator
- upgrading Dotfuscator
- register Dotfuscator
- registering Dotfuscator
- Dotfuscator command line
- Dotfuscator Professional
description: Visual Studio 2017'de dahil edilen ücretsiz Dotfuscator Community Edition yükseltmeyi öğrenin.
ms.assetid: c7c60904-27f9-4f1f-b79b-ddf65041b810
author: Joe-Sewell-PreEmptive
ms.author: gewarren
manager: douge
ms.openlocfilehash: f1158b0e5f438e49acafad79af1b33ec43690e9a
ms.sourcegitcommit: 0cf1e63b6e0e6a0130668278489b21a6e5038084
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/02/2018
ms.locfileid: "39468549"
---
# <a name="upgrade-dotfuscator-community-edition-ce"></a>Dotfuscator Community Edition (CE) yükseltme

Dotfuscator Community Edition (Dotfuscator CE) birçok uygulama koruması ve sağlamlaştırma özelliklerini hemen Microsoft Visual Studio kullanarak tüm geliştiricilere sunar.
Ancak, daha fazla özellikler mevcuttur, Dotfuscator sürümüne yükseltme kullanıcılar için kullanılabilir.

## <a name="registering-dotfuscator-ce"></a>Dotfuscator CE'yi kaydediliyor

Dotfuscator CE kayıtlı kullanıcıları almak için ek özelliklere erişimi gibi [komut satırı desteğiyle][cli], hangi kolaylaştırır Dotfuscator CE, otomatik derleme sürecinizle tümleştirin. Kaydetme ayrıca erişim verir Lucidator için yerleşik bir aracı için kullanılan [karıştırılmış yığın izlemelerini kod çözme][decode-obfuscated].

Hızlı, basit ve ücretsiz olarak kayıttır.
Dotfuscator CE kaydetmek için bkz: [tam Dotfuscator CE Kullanıcı Kılavuzu'na Başlarken sayfasında kaydetme Dotfuscator CE bölümünü][register-ce].

## <a name="dotfuscator-professional"></a>Dotfuscator Professional

Dotfuscator Community Edition temel bir düzeyde koruma sağlarken  **_PreEmptive koruma - Dotfuscator_ Professional Edition** Gelişmiş karartma dönüşümler ve koruma içeren özellikleri. Gelişmiş dönüştürmeler ve özellikleri içerir:

* *Fikri mülkiyet koruması*
  * Ek seçenekler Enhanced Overload Induction™ ve rastgele tanımlayıcısı seçimi gibi yeniden adlandırma.
  * Kod çözme için Araçlar, yığın izlemelerini gizlenmiş.
  * Erişim için kurumsal düzeyde karartma dönüştürmeler de dahil olmak üzere, [iptal ediyor hedeflenen dönüşümler otomatik kod ılspy][control-flow].
  * Yeteneği [hassas dizeleri gizlememeniz][string-encryption], kaynak koda dönüştürülmüş kod basit bir arama imkansızdır.
  * Yeteneği [belirtmeyecek sahipliği ve dağıtım dizeleri, derlemelere gömmek][watermarking], yetkisiz yazılım sızıntılarını kaynağını belirlemek etmenize imkan sağlar.
  * Yeteneği [tek birden çok derleme birleştirme][linking], görev ayrımı nettir ortadan gibi kod öğelerinin rollerini belirleme saldırganların daha zor hale.
  * Yeteneği [kullanılmayan kod uygulamanızdan otomatik olarak kaldırmak][pruning], gönderildiğini hassas kod miktarını azaltır.
* *Uygulama bütünlüğünü koruma*
  * Ek [uygulama savunması davranışları][check-actions].
  * Bir uygulamanın yaşam bitiş tarihi önce bir uyarı dönemi sağlama yeteneği.
  * Uygulama kodu bir ömrü sonu uyarı dönemi sırasında veya son tarihten sonra bildirim özelliği.

Dotfuscator Professional sektör standardı olan [.NET belirsizleştirici] [ net-obfuscator] ve sürekli destek, Bakım ve ürün güncelleştirmeleri gerektiren Kurumsal geliştiriciler için uygundur.
Ayrıca, Dotfuscator Professional, Visual Studio ile sıkı tümleştirme sağlar ve Ticari kullanım için lisanslanmıştır.

PreEmptive Solutions Dotfuscator Professional Gelişmiş uygulama koruma özellikleri hakkında daha fazla bilgi için ziyaret [Dotfuscator genel bakış sayfasında] [ product-about] ve [kendisine karşılaştırın Community sürümü][product-compare].
[Tam destekli deneme sırasında preemptive.com][eval].

## <a name="see-also"></a>Ayrıca Bkz.

[Bu makalede tam Dotfuscator CE Kullanıcı Kılavuzu][full]

<!-- Copyright © 2017 PreEmptive Solutions, LLC -->

[control-flow]:  https://www.preemptive.com/products/dotfuscator/features#controlflow
[string-encryption]:  https://www.preemptive.com/products/dotfuscator/features#string
[watermarking]:  https://www.preemptive.com/products/dotfuscator/features#watermarking
[linking]:  https://www.preemptive.com/products/dotfuscator/features#linking
[pruning]:  https://www.preemptive.com/products/dotfuscator/features#pruning

[check-actions]:  https://www.preemptive.com/dotfuscator/pro/userguide/en/protection_checks_overview.html#actions

[net-obfuscator]:  https://www.preemptive.com/products/dotfuscator/overview
[eval]:  https://www.preemptive.com/eval-request

[product-about]:  https://www.preemptive.com/products/dotfuscator/overview
[product-compare]:  https://www.preemptive.com/products/dotfuscator/compare-editions

[cli]:  https://www.preemptive.com/dotfuscator/ce/docs/help/intro_cli.html
[register-ce]:  https://www.preemptive.com/dotfuscator/ce/docs/help/gui_getstarted.html#register

[full]:  https://www.preemptive.com/dotfuscator/ce/docs/help/intro_upgrades.html
[decode-obfuscated]:  https://www.preemptive.com/dotfuscator/ce/docs/help/gui_decode_stack_trace.html