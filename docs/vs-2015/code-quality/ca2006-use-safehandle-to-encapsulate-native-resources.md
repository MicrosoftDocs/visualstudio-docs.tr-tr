---
title: 'CA2006: yerel kaynakları kapsamak için SafeHandle kullanın | Microsoft Docs'
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
- CA2006
- UseSafeHandleToEncapsulateNativeResources
helpviewer_keywords:
- UseSafeHandleToEncapsulateNativeResources
- CA2006
ms.assetid: a71950bd-bcc1-463d-b1f2-5233bc451456
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 88d53d90d00f58706e366b54dfa78b59e499bc24
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49935386"
---
# <a name="ca2006-use-safehandle-to-encapsulate-native-resources"></a>CA2006: Yerel kaynakları kapsamak için SafeHandle kullanın
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|UseSafeHandleToEncapsulateNativeResources|
|CheckId|CA2006|
|Kategori|Microsoft.Reliability|
|Yeni Değişiklik|Bölünemez|

## <a name="cause"></a>Sebep
 Yönetilen kod kullandığı <xref:System.IntPtr> yerel kaynaklara erişmek için.

## <a name="rule-description"></a>Kural Tanımı
 Kullanım `IntPtr` yönetilen kodda olası bir güvenlik ve güvenilirlik sorunu belirtebilir. Tüm kullanımları `IntPtr` belirlemek için gözden geçirilmesi gereken olup olmadığını kullanımı bir <xref:System.Runtime.InteropServices.SafeHandle> , veya benzer teknoloji ve onun yerine gereklidir. Sorunları varsa gerçekleşir `IntPtr` bazı bellek, dosya tanıtıcısı veya yönetilen kod için kendi olarak değerlendirilir, bir yuva gibi yerel bir kaynak temsil eder. Yönetilen kod kaynak sahipse, bunu yapmak için bir hata kaynak sızıntısına neden olacağından, ayrıca ilişkili yerel kaynakları bırakmalıdır.

 Çok iş parçacıklı erişimi izni olup olmadığını böyle senaryolarda, güvenlik ve güvenilirlik sorunları da sunulacaktır `IntPtr` ve tarafından temsil edilen kaynak serbest bir şekilde `IntPtr` sağlanır. Bu sorunları, geri dönüştürme içeren `IntPtr` başka bir iş parçacığında eşzamanlı kullanım kaynak yapılırken kaynak sürüm değeri. Bu, burada bir iş parçacığı okuma veya yanlış kaynakla ilişkilendirilen veri yazma yarış durumlarını neden olabilir. Örneğin, bir işletim sistemi tanıtıcısı olarak türünüz depolar bir `IntPtr` ve kullanıcıların çağırın olanak tanıyan **Kapat** ve aynı anda ve eşitleme tür olmadan, tanıtıcı kullanan başka bir yöntem, kodunuzu bir tanıtıcı geri dönüştürme vardır. sorun oluştu.

 Bu tanıtıcı geri dönüştürme sorun veri bozulması ve genellikle, bir güvenlik açığına neden olabilir. `SafeHandle` ve kendi eşdüzey sınıfı <xref:System.Runtime.InteropServices.CriticalHandle> tür iş parçacığı oluşturma sorunları önlenebilir bir kaynak için yerel bir tanıtıcı yalıtılacak bir mekanizma sağlar. Ayrıca, kullanabileceğiniz `SafeHandle` ve kendi eşdüzey sınıfı `CriticalHandle` dikkatle yerel yöntemlere yapılan çağrılar üzerinden yerel tanıtıcı bir kopyasını içeren, yönetilen nesnelerin ömrünü denetlemek için diğer iş parçacığı oluşturma sorunları gibi. Bu durumda, genellikle çağrıları kaldırabilirsiniz `GC.KeepAlive`. Ücretler kullanırken performans ek yükü aşamalarına `SafeHandle` ve daha düşük bir düzeyde `CriticalHandle`, dikkatli bir tasarım sık azaltılabilir.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Dönüştürme `IntPtr` kullanımı `SafeHandle` yerel kaynaklara erişimi güvenli bir şekilde yönetmek için. Bkz: <xref:System.Runtime.InteropServices.SafeHandle> örnekler için başvuru konusu.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Bu uyarı göndermeme değil.

## <a name="see-also"></a>Ayrıca Bkz.
 <xref:System.IDisposable>



