---
title: Kod Çözümleme İade İlkeleri için Sürüm Uyumluluğu
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- version compatibility, code analysis check-in policy
- check-in policies, version compatibility for code analysis
ms.assetid: 1af376e3-3be7-4445-803b-76a858567a5b
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 5d04ac68140395cbc2dae9bd70f57e587d9b7732
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49898241"
---
# <a name="version-compatibility-for-code-analysis-check-in-policies"></a>Kod Çözümleme İade İlkeleri için Sürüm Uyumluluğu

Değerlendirmek ve kod çözümleme iade ilkeleri farklı sürümlerini kullanan Yazar [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)], nasıl farkları bilmeniz gerekir [!INCLUDE[vstsTfsOrcasLong](../code-quality/includes/vststfsorcaslong_md.md)] ve [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] iade ilkelerini değerlendirme.

## <a name="version-compatibility-for-evaluating-check-in-policies"></a>İade ilkelerini değerlendirme için sürüm uyumluluğu

- Ne zaman kod çözümleme iade ilkeleri değerlendirilir [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)], varolan herhangi bir kuralın [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] ancak içinde yok [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] göz ardı edilir.

- Ne zaman kod çözümleme iade ilkeleri değerlendirilir [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)], özel olan tüm yeni kuralları [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] göz ardı edilir.

- Kod çözümleme iade ilkesi kuralları derlemeleri belirtiyorsa [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] tarafından tanınmayan derlemeler tarafından belirtilen tüm kuralları yok sayar.

- Kod çözümleme iade ilkesi kuralları derlemeleri belirtirse, [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] tanımıyor, bir ileti görüntülenir.

## <a name="version-compatibility-for-authoring-check-in-policies"></a>İade ilkeleri yazmak için sürüm uyumluluğu

- İade Kod Analizi İlkesi kullanarak oluşturduysanız [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] sürümünü [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)], kullanamazsınız [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] sürümünü [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)] değiştirmek için. Ayrıca, [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] ilke değerlendirilemiyor.

- İade Kod Analizi İlkesi kullanarak oluşturduysanız [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)] içinde [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)], kullanabileceğiniz [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)] içinde [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] ve ilkeyi değiştirmek için de göre değerlendirilebilir [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)]. İlkeyi kullanarak değiştirdikten sonra [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)] içinde [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)], ilkeyi kullanarak artık düzenleyemezsiniz [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)] içinde [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)]. [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] eşleşmeyen tanımlayıcı adlarla sorunsuz ilkeleri değerlendirebilirsiniz.

- Kod Analizi İlkesi iade için her ikisinin de geçerli kural ayarları oluşturmak için [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] ve [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)], ilke oluşturmalıdır [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)], gerekli tüm değişiklikleri yapın ve ilkeyi kaydedin. Kuralları yapılan değişiklikler yalnızca varsa [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)], değiştirebilir ve ilke kaydetme [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)].

   İlkeyi kaydettikten sonra [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)], artık mevcut kurallarına yönelik ayarları değiştirebilirsiniz [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] yalnızca.