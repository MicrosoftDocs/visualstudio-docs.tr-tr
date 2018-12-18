---
title: 'CA2232: Windows Forms giriş noktalarını STAThread ile işaretleyin'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- MarkWindowsFormsEntryPointsWithStaThread
- CA2232
helpviewer_keywords:
- CA2232
- MarkWindowsFormsEntryPointsWithStaThread
ms.assetid: a3c95130-8e7f-4419-9fcd-b67d077e8efb
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 97c5ad926ecc2a0480a612575eca7e4fe0af31e5
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2018
ms.locfileid: "45551447"
---
# <a name="ca2232-mark-windows-forms-entry-points-with-stathread"></a>CA2232: Windows Forms giriş noktalarını STAThread ile işaretleyin

|||
|-|-|
|TypeName|MarkWindowsFormsEntryPointsWithStaThread|
|CheckId|CA2232|
|Kategori|Microsoft.Usage|
|Yeni Değişiklik|Bozucu olmayan|

## <a name="cause"></a>Sebep
 Bir derlemeye başvuran <xref:System.Windows.Forms> ad alanı ve kendi giriş noktası olarak işaretlenmemiş ile <xref:System.STAThreadAttribute?displayProperty=fullName> özniteliği.

## <a name="rule-description"></a>Kural açıklaması
 <xref:System.STAThreadAttribute> iş parçacığı modeli uygulama için COM tek iş parçacıklı grup olduğunu gösterir. Bu öznitelik Windows Forms kullanan herhangi bir uygulamanın girişinde sunulur; atlanırsa, Windows bileşenleri doğru çalışmayabilir. Öznitelik mevcut değilse, uygulamanın Windows Forms için desteklenmiyor çok iş parçacıklı grubun modeli kullanır.

> [!NOTE]
> [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] Uygulama Çerçevesi kullanan projeler işaretlemek gerekmez **ana** yöntemi STAThread ile işaretleyin. [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] Derleyici her şeyi otomatik olarak.

## <a name="how-to-fix-violations"></a>İhlaller nasıl düzeltilir?
 Bu kural ihlalini düzeltmek için ekleme <xref:System.STAThreadAttribute> özniteliği giriş noktası. Varsa <xref:System.MTAThreadAttribute?displayProperty=fullName> özniteliği varsa, bunu kaldırın.

## <a name="when-to-suppress-warnings"></a>Uyarılar bastırıldığında
 .NET Compact Framework için kendisi için geliştiriyorsanız, bu kuraldan bir uyarıyı bastırmak güvenlidir <xref:System.STAThreadAttribute> özniteliktir gereksiz ve desteklenmiyor.

## <a name="example"></a>Örnek
 Aşağıdaki örnekler doğru kullanımını gösterir <xref:System.STAThreadAttribute>:

 [!code-csharp[FxCop.Usage.StaThread#1](../code-quality/codesnippet/CSharp/ca2232-mark-windows-forms-entry-points-with-stathread_1.cs)]
 [!code-vb[FxCop.Usage.StaThread#1](../code-quality/codesnippet/VisualBasic/ca2232-mark-windows-forms-entry-points-with-stathread_1.vb)]