---
title: Mstest'i assert sınıflar ve yöntemler
ms.date: 06/07/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: reference
helpviewer_keywords:
- Assert classes
- Assert methods
- unit tests, Assert classes
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 91198e9b7048b384bf2095840abbd012042025ed
ms.sourcegitcommit: ce154aee5b403d5c1c41da42302b896ad3cf8d82
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/07/2018
ms.locfileid: "34844267"
---
# <a name="use-assert-classes-for-unit-testing"></a>Birim testi için onay sınıfları kullanma

Assert sınıflarını kullanmak <xref:Microsoft.VisualStudio.TestTools.UnitTesting> belirli işlevselliğini doğrulamak için ad alanı. Birim testi yöntemine uygulamanızın kodu yönteminde kod uygular ancak yalnızca Assert deyimleri eklerseniz kodun davranışı doğruluğunu bildiriyor.

## <a name="kinds-of-asserts"></a>Tür, onaylar

<xref:Microsoft.VisualStudio.TestTools.UnitTesting> Ad alanı, çeşitli türlerde onay sınıfları sağlar.

Test yönteminize, herhangi bir yöntem çağrısı <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert?displayProperty=fullName> gibi sınıfı <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.AreEqual%2A?displayProperty=nameWithType>. <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> Sınıfı aralarından seçim yapabileceğiniz birçok yöntem ve birçok yöntem birçok aşırı yüklemeye sahip.

### <a name="compare-strings-and-collections"></a>Dizeler ve koleksiyonları karşılaştırma

Kullanım <xref:Microsoft.VisualStudio.TestTools.UnitTesting.CollectionAssert> sınıfı nesne koleksiyonları karşılaştırmak ya da bir koleksiyon durumunu doğrulayın.

Kullanım <xref:Microsoft.VisualStudio.TestTools.UnitTesting.StringAssert> karşılaştırın ve dizeleri incelemek için sınıf. Bu sınıf gibi çeşitli kullanışlı yöntemler içerir <xref:Microsoft.VisualStudio.TestTools.UnitTesting.StringAssert.Contains%2A?displayProperty=nameWithType>, <xref:Microsoft.VisualStudio.TestTools.UnitTesting.StringAssert.Matches%2A?displayProperty=nameWithType>, ve <xref:Microsoft.VisualStudio.TestTools.UnitTesting.StringAssert.StartsWith%2A?displayProperty=nameWithType>.

### <a name="exceptions"></a>Özel Durumlar

<xref:Microsoft.VisualStudio.TestTools.UnitTesting.AssertFailedException> Bir test başarısız olduğunda özel durum. Zaman aşımına uğradı, beklenmeyen bir özel durum oluşturur veya üreten bir onay deyimi içeriyorsa, bir test başarısız bir **başarısız** sonucu.

<xref:Microsoft.VisualStudio.TestTools.UnitTesting.AssertInconclusiveException> Bir test sonucu üreten her durum **Inconclusive**. Genellikle, eklediğiniz bir <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.Inconclusive%2A?displayProperty=nameWithType> hala, onu henüz çalıştırılmaya hazır değil belirtmek için çalışmakta olduğunuz bir test bildirimi.

> [!NOTE]
> Bir alternatif ile çalıştırmak hazır değil bir test işaretlemek için stratejidir <xref:Microsoft.VisualStudio.TestTools.UnitTesting.IgnoreAttribute> özniteliği. Ancak, bu uygulanmadı sınamaların sayısı üzerinde bir rapor kolayca oluşturamıyor olumsuz sahiptir.

Yeni bir özel durum sınıfı assert yazarsanız temel sınıfından <xref:Microsoft.VisualStudio.TestTools.UnitTesting.UnitTestAssertException> özel bir onaylama işlemi hatasına yerine test veya üretim kodunuzdan durum beklenmeyen bir özel durum olarak tanımlamak daha kolay.

Bir test yöntemi ile işaretleme <xref:Microsoft.VisualStudio.TestTools.UnitTesting.ExpectedExceptionAttribute> özniteliği, uygulama kodunuzda yöntemi tarafından oluşturulan beklediğiniz bir özel durum gerçekten durum doğrulamak için test yöntemi istediğinizde.

## <a name="see-also"></a>Ayrıca bkz.

- [Birim testi kodunuz](../test/unit-test-your-code.md)