---
title: Yönetilen kod için yönetilen önerilen kurallar kural kümesi | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1d1160f8-4e51-4e70-99cd-82ad10ee7b32
caps.latest.revision: 12
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 33c35304643d0743b5da53a75cae9a01125b7da6
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49296107"
---
# <a name="managed-recommended-rules-rule-set-for-managed-code"></a>Yönetilen kod için Yönetilen Önerilen Kurallar kural kümesi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Microsoft yönetilen önerilen kurallar kural potansiyel güvenlik boşluklarını, uygulama kilitlenmesi ve diğer önemli mantık ve tasarım hataları gibi yönetilen kodunuzda en kritik sorunlara odaklanmak için kümesi kullanabilirsiniz. Bu kural projeleriniz için oluşturduğunuz herhangi bir özel kural kümesi kümesini içermelidir.  
  
|Kural|Açıklama|  
|----------|-----------------|  
|[CA1001](../code-quality/ca1001-types-that-own-disposable-fields-should-be-disposable.md)|Atılabilir alanlara sahip türler atılabilir olmalıdır|  
|[CA1009](../code-quality/ca1009-declare-event-handlers-correctly.md)|Olay işleyicilerini doğru bildirin|  
|[CA1016](../code-quality/ca1016-mark-assemblies-with-assemblyversionattribute.md)|Derlemeleri AssemblyVersionAttribute ile işaretleyin|  
|[CA1033](../code-quality/ca1033-interface-methods-should-be-callable-by-child-types.md)|Arabirim yöntemleri alt türler tarafından çağırılabilir olmalıdır|  
|[CA1049](../code-quality/ca1049-types-that-own-native-resources-should-be-disposable.md)|Yerel kaynaklara sahip türler atılabilir olmalıdır|  
|[CA1060](../code-quality/ca1060-move-p-invokes-to-nativemethods-class.md)|P/Invokes öğesini NativeMethods sınıfına taşıyın|  
|[CA1061](../code-quality/ca1061-do-not-hide-base-class-methods.md)|Taban sınıf yöntemlerini gizlemeyin|  
|[CA1063](../code-quality/ca1063-implement-idisposable-correctly.md)|IDisposable'ı doğru uygulayın|  
|[CA1065](../code-quality/ca1065-do-not-raise-exceptions-in-unexpected-locations.md)|Beklenmedik konumlarda özel durumlar harekete geçirmeyin|  
|[CA1301](../code-quality/ca1301-avoid-duplicate-accelerators.md)|Yinelenen hızlandırıcılardan kaçının|  
|[CA1400](../code-quality/ca1400-p-invoke-entry-points-should-exist.md)|P/Invoke giriş noktaları bulunmalıdır|  
|[CA1401](../code-quality/ca1401-p-invokes-should-not-be-visible.md)|P/Invoke'lar görünür olmamalıdır|  
|[CA1403](../code-quality/ca1403-auto-layout-types-should-not-be-com-visible.md)|Otomatik Yerleşim türleri COM görünebilir olmamalıdır|  
|[CA1404](../code-quality/ca1404-call-getlasterror-immediately-after-p-invoke.md)|P/Invoke ardından hemen GetLastError çağırın|  
|[CA1405](../code-quality/ca1405-com-visible-type-base-types-should-be-com-visible.md)|COM görünebilir tür taban türler COM görünebilir olmalıdır|  
|[CA1410](../code-quality/ca1410-com-registration-methods-should-be-matched.md)|COM kayıt yöntemleri eşleşmelidir|  
|[CA1415](../code-quality/ca1415-declare-p-invokes-correctly.md)|P/Invoke'lar doğru bildirin|  
|[CA1821](../code-quality/ca1821-remove-empty-finalizers.md)|Boş Sonlandırıcıları kaldırın|  
|[CA1900](../code-quality/ca1900-value-type-fields-should-be-portable.md)|Değer tür alanları taşınabilir olmalıdır|  
|[CA1901](../code-quality/ca1901-p-invoke-declarations-should-be-portable.md)|P/Invoke bildirimleri taşınabilir olmalıdır|  
|[CA2002](../code-quality/ca2002-do-not-lock-on-objects-with-weak-identity.md)|Zayıf kimliği olan nesneleri kilitlemeyin|  
|[CA2100](../code-quality/ca2100-review-sql-queries-for-security-vulnerabilities.md)|SQL sorgularını güvenlik açıkları için gözden geçirin|  
|[CA2101](../code-quality/ca2101-specify-marshaling-for-p-invoke-string-arguments.md)|P/Invoke dize bağımsız değişkenleri için hazırlama belirtin|  
|[CA2108](../code-quality/ca2108-review-declarative-security-on-value-types.md)|Değer türleri üzerinde bildirimsel güvenliği gözden geçirin|  
|[CA2111](../code-quality/ca2111-pointers-should-not-be-visible.md)|İşaretçiler görünür olmamalıdır|  
|[CA2112](../code-quality/ca2112-secured-types-should-not-expose-fields.md)|Güvenli türler alanları açığa çıkarmamalıdır|  
|[CA2114](../code-quality/ca2114-method-security-should-be-a-superset-of-type.md)|Yöntem güvenliği türün bir üst kümesi olmalıdır|  
|[CA2116](../code-quality/ca2116-aptca-methods-should-only-call-aptca-methods.md)|APTCA yöntemleri yalnızca APTCA yöntemlerini çağırmalıdır|  
|[CA2117](../code-quality/ca2117-aptca-types-should-only-extend-aptca-base-types.md)|APTCA türleri yalnızca APTCA taban türlerini genişletmelidir|  
|[CA2122](../code-quality/ca2122-do-not-indirectly-expose-methods-with-link-demands.md)|Bağlantı talepleri olan yöntemleri dolaylı olarak açığa çıkarmayın|  
|[CA2123](../code-quality/ca2123-override-link-demands-should-be-identical-to-base.md)|Geçersiz kılma bağlantı talepleri taban ile özdeş olmalıdır|  
|[CA2124](../code-quality/ca2124-wrap-vulnerable-finally-clauses-in-outer-try.md)|Savunmasız sonunda yan tümcelerini dış sarmalayın|  
|[CA2126](../code-quality/ca2126-type-link-demands-require-inheritance-demands.md)|Tür bağlantı talepleri devralma taleplerini gerektirir|  
|[CA2131](../code-quality/ca2131-security-critical-types-may-not-participate-in-type-equivalence.md)|Güvenlik kritik türleri tür eşdeğerliğine katılamaz|  
|[CA2132](../code-quality/ca2132-default-constructors-must-be-at-least-as-critical-as-base-type-default-constructors.md)|Varsayılan oluşturucular en az taban tür varsayılan oluşturucular kadar kritik olmalıdır|  
|[CA2133](../code-quality/ca2133-delegates-must-bind-to-methods-with-consistent-transparency.md)|Temsilciler tutarlı saydamlığı olan yöntemlere bağlanmalıdır|  
|[CA2134](../code-quality/ca2134-methods-must-keep-consistent-transparency-when-overriding-base-methods.md)|Yöntemler taban yöntemleri geçersiz kılarken tutarlı saydamlığı tutmalıdır|  
|[CA2137](../code-quality/ca2137-transparent-methods-must-contain-only-verifiable-il.md)|Saydam yöntemler yalnızca doğrulanabilir IL içermelidir|  
|[CA2138](../code-quality/ca2138-transparent-methods-must-not-call-methods-with-the-suppressunmanagedcodesecurity-attribute.md)|Saydam yöntemler SuppressUnmanagedCodeSecurity özniteliğine sahip yöntemleri çağırmamalıdır|  
|[CA2140](../code-quality/ca2140-transparent-code-must-not-reference-security-critical-items.md)|Saydam kod güvenlik kritik başvurmamalıdır|  
|[CA2141](../code-quality/ca2141-transparent-methods-must-not-satisfy-linkdemands.md)|Saydam yöntemleri LinkDemands karşılamalıdır değil|  
|[CA2146](../code-quality/ca2146-types-must-be-at-least-as-critical-as-their-base-types-and-interfaces.md)|Türler kendi taban türleri ve arabirimleri en az kadar kritik olmalıdır|  
|[CA2147](../code-quality/ca2147-transparent-methods-may-not-use-security-asserts.md)|Saydam yöntemler güvenlik kullanamazsınız onaylar|  
|[CA2149](../code-quality/ca2149-transparent-methods-must-not-call-into-native-code.md)|Saydam metotlar yerel kod içine çağırmamalıdır|  
|[CA2200](../code-quality/ca2200-rethrow-to-preserve-stack-details.md)|Yığın ayrıntılarını korumak için yeniden fırlatma|  
|[CA2202](../code-quality/ca2202-do-not-dispose-objects-multiple-times.md)|Nesneleri birden çok kez atmayın|  
|[CA2207](../code-quality/ca2207-initialize-value-type-static-fields-inline.md)|Değer türü statik alanları satır içi başlatın|  
|[CA2212](../code-quality/ca2212-do-not-mark-serviced-components-with-webmethod.md)|Servis verilen bileşenleri WebMethod ile işaretlemeyin|  
|[CA2213](../code-quality/ca2213-disposable-fields-should-be-disposed.md)|Atılabilen alanlar atılmalıdır|  
|[CA2214](../code-quality/ca2214-do-not-call-overridable-methods-in-constructors.md)|Geçersiz kılınabilir yöntemleri oluşturucular içinde çağırmayın|  
|[CA2216](../code-quality/ca2216-disposable-types-should-declare-finalizer.md)|Atılabilir türler sonlandırıcıyı bildirmelidir|  
|[CA2220](../code-quality/ca2220-finalizers-should-call-base-class-finalizer.md)|Sonlandırıcılar taban Sonlandırıcıları çağırmalıdır|  
|[CA2229](../code-quality/ca2229-implement-serialization-constructors.md)|Serileştirme oluşturucularını uygulayın|  
|[CA2231](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)|Eşittir işlecini ValueType.equals'ı geçersiz kılarak üzerinde|  
|[CA2232](../code-quality/ca2232-mark-windows-forms-entry-points-with-stathread.md)|İşareti Windows Forms giriş noktalarını STAThread ile işaretleyin|  
|[CA2235](../code-quality/ca2235-mark-all-non-serializable-fields.md)|Tüm serileştirilebilir olmayan alanları işaretleyin|  
|[CA2236](../code-quality/ca2236-call-base-class-methods-on-iserializable-types.md)|ISerializable türler üzerinde taban sınıf yöntemlerini çağırın|  
|[CA2237](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)|İşareti ISerializable türleri SerializableAttribute ile işaretleyin|  
|[CA2238](../code-quality/ca2238-implement-serialization-methods-correctly.md)|Serileştirme yöntemlerini doğru uygulama|  
|[CA2240](../code-quality/ca2240-implement-iserializable-correctly.md)|ISerializable'ı doğru uygulayın|  
|[CA2241](../code-quality/ca2241-provide-correct-arguments-to-formatting-methods.md)|Biçimlendirme yöntemlerine doğru bağımsız değişkenleri sağlayın|  
|[CA2242](../code-quality/ca2242-test-for-nan-correctly.md)|NaN için doğru sınayın|



