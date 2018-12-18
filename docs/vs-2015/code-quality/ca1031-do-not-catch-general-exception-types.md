---
title: 'CA1031: genel özel durum türlerini yakalamayın | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CA1031
- DoNotCatchGeneralExceptionTypes
helpviewer_keywords:
- CA1031
- DoNotCatchGeneralExceptionTypes
ms.assetid: cbc283ae-2a46-4ec0-940e-85aa189b118f
caps.latest.revision: 22
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 2548fe0e54e57e4374f8ae92e9d43302df419aa4
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49940196"
---
# <a name="ca1031-do-not-catch-general-exception-types"></a>CA1031: Genel özel durum türlerini yakalamayın
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DoNotCatchGeneralExceptionTypes|
|CheckId|CA1031|
|Kategori|Microsoft.Design|
|Yeni Değişiklik|Bölünemez|

## <a name="cause"></a>Sebep
 Genel bir özel durum gibi <xref:System.Exception?displayProperty=fullName> veya <xref:System.SystemException?displayProperty=fullName> , yakalanan bir `catch` deyimi veya bir genel bir catch yan tümcesi gibi `catch()` kullanılır.

## <a name="rule-description"></a>Kural Tanımı
 Genel özel durum yakalanmamalı.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bu kural ihlalini düzeltmek için daha özel istisnaları yakalayın veya son ifade olarak genel özel durumu yeniden `catch` blok.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Bu kuraldan uyarıyı bastırmayın. Genel özel durum türlerini yakalamak çalışma zamanı sorunlarını kitaplık kullanıcısından gizleyebilir ve hata ayıklama daha zor hale getirebilir.

> [!NOTE]
>  İle başlayarak [!INCLUDE[net_v40_long](../includes/net-v40-long-md.md)], ortak dil çalışma zamanı (CLR) erişim ihlali gibi yönetilen kod ve işletim sistemi ortaya bozuk durum özel durumlar artık teslim [!INCLUDE[TLA#tla_mswin](../includes/tlasharptla-mswin-md.md)], yönetilen kod tarafından işlenecek. Bir uygulamada derlemek istiyorsanız [!INCLUDE[net_v40_short](../includes/net-v40-short-md.md)] veya sonraki sürümler ve bakımını bozuk durum özel durumları işleme, uygulayabileceğiniz <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute> öznitelik bozuk durum özel durumu işleyen yöntem.

## <a name="example"></a>Örnek
 Aşağıdaki örnek bu kuralı ihlal eden bir tür ve doğru bir şekilde uygulayan bir tür gösterir `catch` blok.

 [!code-cpp[FxCop.Design.ExceptionAndSystemException#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.ExceptionAndSystemException/cpp/FxCop.Design.ExceptionAndSystemException.cpp#1)]
 [!code-csharp[FxCop.Design.ExceptionAndSystemException#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.ExceptionAndSystemException/cs/FxCop.Design.ExceptionAndSystemException.cs#1)]
 [!code-vb[FxCop.Design.ExceptionAndSystemException#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.ExceptionAndSystemException/vb/FxCop.Design.ExceptionAndSystemException.vb#1)]

## <a name="related-rules"></a>İlgili kuralları
 [CA2200: Yığın ayrıntılarını korumak için yeniden fırlatma](../code-quality/ca2200-rethrow-to-preserve-stack-details.md)



