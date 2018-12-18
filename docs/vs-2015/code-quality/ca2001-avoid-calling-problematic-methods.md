---
title: 'CA2001: sorunlu yöntemleri çağırmaktan kaçının | Microsoft Docs'
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
- CA2001
- AvoidCallingProblematicMethods
helpviewer_keywords:
- CA2001
- AvoidCallingProblematicMethods
ms.assetid: 19db8edb-31ce-441c-b0de-a0f2746155b7
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: ddc96857cf0c3c54472eded5545ca0f328eba213
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49902795"
---
# <a name="ca2001-avoid-calling-problematic-methods"></a>CA2001: Sorunlu yöntemleri çağırmaktan kaçının
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|AvoidCallingProblematicMethods|
|CheckId|CA2001|
|Kategori|Microsoft.Reliability|
|Yeni Değişiklik|Bölünemez|

## <a name="cause"></a>Sebep
 Bir üye olası tehlikeli ya da sorunlu yöntemi çağırır.

## <a name="rule-description"></a>Kural Tanımı
 Gereksiz ve tehlikeli yöntem çağrıları yapmaktan kaçının.

 Bu kural ihlalini üyesi aşağıdaki yöntemlerden birini çağırır oluşur.

|Yöntem|Açıklama|
|------------|-----------------|
|<xref:System.GC.Collect%2A?displayProperty=fullName>|GC çağrılıyor. Toplama, uygulama performansını önemli ölçüde etkileyebilir ve nadiren gereklidir. Daha fazla bilgi için [Rico Mariani'nın performans ipuçları](http://go.microsoft.com/fwlink/?LinkId=169256) MSDN'de blog girişi.|
|<xref:System.Threading.Thread.Resume%2A?displayProperty=fullName><br /><br /> <xref:System.Threading.Thread.Suspend%2A?displayProperty=fullName>|Thread.Suspend ve Thread.Resume öngörülemeyen davranışları nedeniyle kullanım dışı bırakıldı.  Diğer sınıfları kullanın <xref:System.Threading> ad gibi <xref:System.Threading.Monitor>, <xref:System.Threading.Mutex>, ve <xref:System.Threading.Semaphore> iş parçacığı eşitleme veya kaynakları korumak için.|
|<xref:System.Runtime.InteropServices.SafeHandle.DangerousGetHandle%2A?displayProperty=fullName>|Geçersiz bir tanıtıcı döndürebildiğinden DangerousGetHandle yöntemi bir güvenlik riski oluşturur. Bkz: <xref:System.Runtime.InteropServices.SafeHandle.DangerousAddRef%2A> ve <xref:System.Runtime.InteropServices.SafeHandle.DangerousRelease%2A> DangerousGetHandle yöntemi güvenli bir şekilde kullanma hakkında daha fazla bilgi için yöntemleri.|
|<xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=fullName><br /><br /> <xref:System.Reflection.Assembly.LoadFile%2A?displayProperty=fullName><br /><br /> <xref:System.Reflection.Assembly.LoadWithPartialName%2A?displayProperty=fullName>|Bu yöntemler, beklenmeyen konumlardan derlemelerini yükleyebilir. Örneğin, Suzanne Cook'ın .NET CLR notları blog gönderilerini görün [önce LoadFile işlevini vs. LoadFrom](http://go.microsoft.com/fwlink/?LinkId=164450) ve [bir bağlama bağlamı seçme](http://go.microsoft.com/fwlink/?LinkId=164451) derlemeleri yükleme yöntemleri hakkında daha fazla bilgi için MSDN Web sitesinde.|
|[CoSetProxyBlanket](http://go.microsoft.com/fwlink/?LinkID=169250) (Ole32)<br /><br /> [CoInitializeSecurity](http://go.microsoft.com/fwlink/?LinkId=169255) (Ole32)|Zaman yönetilen bir işlemde çalışan kullanıcı kodu başlatır, bu çok geç güvenilir bir şekilde CoSetProxyBlanket çağırmaktır. Ortak dil çalışma zamanı (CLR), P/Invoke kullanıcıların başarılı engelleyebilir başlatma eylemleri gerçekleştirir.<br /><br /> Yönetilen bir uygulama için CoSetProxyBlanket çağırmak varsa, yerel kod (C++) yürütülebilir dosya kullanarak işleme başlayın CoSetProxyBlanket yerel kodu çağırın ve ardından işlemde yönetilen kod uygulamanızı başlatmak öneririz. (Çalışma zamanı sürüm numarası belirttiğinizden emin olun.)|

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bu kural ihlalini düzeltmek için kaldırın veya tehlikeli ya da sorunlu yöntemi çağrısını değiştirin.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Sorunlu yöntemi hiçbir alternatifleri kullanılabilir olduğunda bu kuraldan iletilerini.

## <a name="see-also"></a>Ayrıca Bkz.
 [Güvenilirlik Uyarıları](../code-quality/reliability-warnings.md)



