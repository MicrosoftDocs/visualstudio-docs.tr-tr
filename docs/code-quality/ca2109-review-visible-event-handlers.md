---
title: 'CA2109: Görünen olay işleyicileri gözden geçirin'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2109
- ReviewVisibleEventHandlers
helpviewer_keywords:
- ReviewVisibleEventHandlers
- CA2109
ms.assetid: 8f8fa0ee-e94e-400e-b516-24d8727725d7
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 4df271f5427d005ef94c4c09d6c0a1eb05c850b0
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2018
ms.locfileid: "45548890"
---
# <a name="ca2109-review-visible-event-handlers"></a>CA2109: Görünen olay işleyicileri gözden geçirin

|||
|-|-|
|TypeName|ReviewVisibleEventHandlers|
|CheckId|CA2109|
|Kategori|Microsoft.Security|
|Yeni Değişiklik|Yeni|

## <a name="cause"></a>Sebep
 Ortak veya korunan olay işleme yöntemi algılandı.

## <a name="rule-description"></a>Kural açıklaması
 Dışarıdan görünen bir olay işleme yöntem gözden geçirme gerektiren bir güvenlik sorunu gösterir.

Olay işleme yöntemleri sürece açığa çıkarmamak kesinlikle gerekli. İmzalar işleyici ve olay eşleştiği sürece herhangi bir olay için bir olay işleyicisi kullanıma sunulan bir yöntemi çağıran bir temsilci türü eklenebilir. Olaylar, büyük olasılıkla herhangi bir kod tarafından oluşturulan ve yanıt olarak bir düğmeye tıklanması gibi kullanıcı eylemlerini yüksek derecede Güvenilen Sistem kodu tarafından sık gerçekleştirilen. Güvenlik denetimi, bir olay işleme yöntemine ekleyerek, kod yöntemi çağıran bir olay işleyicisi kaydetmesinin engellemez.

 İsteğe bağlı bir olay işleyicisi tarafından çağrılan bir yöntem güvenilir bir şekilde koruyamaz. Güvenlik talepleri Yardım çağrı yığınında çağıranlar inceleyerek güvenilmeyen çağrı yapanlardan kod koruma. Olay işleyicinin yöntemleri çalıştırdığınızda bir olay için bir olay işleyicisi ekler kod çağrı yığınındaki mutlaka mevcut değil. Bu nedenle, olay işleyicisi yöntemi çağrıldığında çağrı yığınını çağıranlar yalnızca yüksek oranda güvenilir. Bu, başarılı olması için olay işleyicisi yöntemi tarafından yapılan talepleri neden olur. Ayrıca, yöntem çağrıldığında talep edilen izni onaylanan. Bu nedenlerle, olay işleme yöntemi gözden geçirdikten sonra riskini bu kural ihlalini düzeltmek için değil yalnızca belirlenebilir. Kodunuzu gözden geçirirken, aşağıdaki konuları göz önünde bulundurun:

- Olayı işleyicinizi tehlikeli ya da açıklardan izinleri bırakmışsa veya yönetilmeyen kod iznini gizleme gibi herhangi bir işlem gerçekleştirir?

- İle herhangi bir zamanda yalnızca yüksek oranda çalışması için kodunuzu gelen ve giden güvenlik tehditlerini nelerdir yığında çağıranlar güvenilen?

## <a name="how-to-fix-violations"></a>İhlaller nasıl düzeltilir?
 Bu kural ihlalini düzeltmek için yöntemin gözden geçirin ve aşağıdakileri değerlendirin:

- Olay işleme yöntemi genel olmayan yapabilirsiniz?

- Olay işleyicisi tehlikeli tüm işlevsellik taşıyabilir miyim?

- Bir güvenlik talebi uygulanmaz, bu diğer herhangi bir biçimde gerçekleştirilebilir?

## <a name="when-to-suppress-warnings"></a>Uyarılar bastırıldığında
 Kodunuzu bir güvenlik tehdidi yol açmaz emin olmak için dikkatli bir güvenlik incelemesinden sonra yalnızca uyarı bu kuraldan gösterme.

## <a name="example"></a>Örnek
 Aşağıdaki kod, kötü amaçlı kod tarafından kötüye bir olay işleme yöntemi gösterir.

 [!code-csharp[FxCop.Security.EventSecLib#1](../code-quality/codesnippet/CSharp/ca2109-review-visible-event-handlers_1.cs)]

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Security.CodeAccessPermission.Demand%2A?displayProperty=fullName>
- <xref:System.EventArgs?displayProperty=fullName>