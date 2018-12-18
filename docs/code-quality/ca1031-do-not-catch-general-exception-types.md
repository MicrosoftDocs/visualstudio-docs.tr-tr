---
title: 'CA1031: Genel özel durum türlerini yakalamayın'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1031
- DoNotCatchGeneralExceptionTypes
helpviewer_keywords:
- CA1031
- DoNotCatchGeneralExceptionTypes
ms.assetid: cbc283ae-2a46-4ec0-940e-85aa189b118f
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 16b43aa25ef4e2d81b2d6f72e7e1c2bfa3e8b6f7
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2018
ms.locfileid: "45551642"
---
# <a name="ca1031-do-not-catch-general-exception-types"></a>CA1031: Genel özel durum türlerini yakalamayın

|||
|-|-|
|TypeName|DoNotCatchGeneralExceptionTypes|
|CheckId|CA1031|
|Kategori|Microsoft.Design|
|Yeni Değişiklik|Bölünemez|

## <a name="cause"></a>Sebep
 Genel bir özel durum gibi <xref:System.Exception?displayProperty=fullName> veya <xref:System.SystemException?displayProperty=fullName> , yakalanan bir `catch` deyimi veya bir genel bir catch yan tümcesi gibi `catch()` kullanılır.

## <a name="rule-description"></a>Kural açıklaması
 Genel özel durum yakalanmamalı.

## <a name="how-to-fix-violations"></a>İhlaller nasıl düzeltilir?
 Bu kural ihlalini düzeltmek için daha özel istisnaları yakalayın veya son ifade olarak genel özel durumu yeniden `catch` blok.

## <a name="when-to-suppress-warnings"></a>Uyarılar bastırıldığında
 Bu kuraldan uyarıyı bastırmayın. Genel özel durum türlerini yakalamak çalışma zamanı sorunlarını kitaplık kullanıcısından gizleyebilir ve hata ayıklama daha zor hale getirebilir.

> [!NOTE]
> İle başlayarak [!INCLUDE[net_v40_long](../code-quality/includes/net_v40_long_md.md)], ortak dil çalışma zamanı (CLR) erişim ihlali gibi yönetilen kod ve işletim sistemi ortaya bozuk durum özel durumlar artık teslim [!INCLUDE[TLA#tla_mswin](../code-quality/includes/tlasharptla_mswin_md.md)], yönetilen kod tarafından işlenecek. Bir uygulamada derlemek istiyorsanız [!INCLUDE[net_v40_short](../code-quality/includes/net_v40_short_md.md)] veya sonraki sürümler ve bakımını bozuk durum özel durumları işleme, uygulayabileceğiniz <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute> öznitelik bozuk durum özel durumu işleyen yöntem.

## <a name="example"></a>Örnek
 Aşağıdaki örnek bu kuralı ihlal eden bir tür ve doğru bir şekilde uygulayan bir tür gösterir `catch` blok.

 [!code-cpp[FxCop.Design.ExceptionAndSystemException#1](../code-quality/codesnippet/CPP/ca1031-do-not-catch-general-exception-types_1.cpp)]
 [!code-vb[FxCop.Design.ExceptionAndSystemException#1](../code-quality/codesnippet/VisualBasic/ca1031-do-not-catch-general-exception-types_1.vb)]
 [!code-csharp[FxCop.Design.ExceptionAndSystemException#1](../code-quality/codesnippet/CSharp/ca1031-do-not-catch-general-exception-types_1.cs)]

## <a name="related-rules"></a>İlgili kuralları
 [CA2200: Yığın ayrıntılarını korumak için yeniden fırlatma](../code-quality/ca2200-rethrow-to-preserve-stack-details.md)