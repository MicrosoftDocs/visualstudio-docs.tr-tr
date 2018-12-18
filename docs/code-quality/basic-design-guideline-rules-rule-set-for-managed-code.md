---
title: Yönetilen kod için Temel Tasarım Yönerge Kuralları kural kümesi
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
ms.assetid: 7eb384f5-f961-400b-b151-115d92addc6a
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 66c67c9c1a395c0684567acfed78c207422b59ba
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/26/2018
ms.locfileid: "31902278"
---
# <a name="basic-design-guideline-rules-rule-set-for-managed-code"></a>Yönetilen kod için Temel Tasarım Yönerge Kuralları kural kümesi
Microsoft temel tasarım yönerge kuralları kural kümesi kodunuzu anlamak ve kullanmak daha kolay hale üzerinde odaklanmak için kullanabilirsiniz. Bu kural, projenizin kitaplık kodu içeriyorsa veya korumak kolaydır kod için en iyi uygulamaları zorunlu kılmak istiyorsanız kümesi içermelidir.

 Temel tasarım yönerge kuralları Microsoft Minimum Recommeded kurallar kural kümesindeki tüm kurallar içerir. Minimum kurallar listesi için bkz: [yönetilen kod için yönetilen önerilen kurallar kural kümesi](../code-quality/managed-recommended-rules-rule-set-for-managed-code.md).

 Aşağıdaki tabloda Microsoft temel tasarım yönerge kuralları kural kümesi içindeki kurallarda açıklanmaktadır.

|Kural|Açıklama|
|----------|-----------------|
|[CA1001](../code-quality/ca1001-types-that-own-disposable-fields-should-be-disposable.md)|Atılabilir alanlara sahip olan türler atılabilir olmalıdır|
|[CA1009](../code-quality/ca1009-declare-event-handlers-correctly.md)|Olay işleyicilerini doğru bildirin|
|[CA1016](../code-quality/ca1016-mark-assemblies-with-assemblyversionattribute.md)|İşareti derlemeleri AssemblyVersionAttribute|
|[CA1033](../code-quality/ca1033-interface-methods-should-be-callable-by-child-types.md)|Arabirim yöntemleri alt türler tarafından çağırılabilir olmalıdır|
|[CA1049](../code-quality/ca1049-types-that-own-native-resources-should-be-disposable.md)|Yerel kaynaklara sahip olan türler atılabilir olmalıdır|
|[CA1060](../code-quality/ca1060-move-p-invokes-to-nativemethods-class.md)|Taşıma P/Invokes öğesini NativeMethods sınıfına|
|[CA1061](../code-quality/ca1061-do-not-hide-base-class-methods.md)|Taban sınıf yöntemlerini gizlemeyin|
|[CA1063](../code-quality/ca1063-implement-idisposable-correctly.md)|IDisposable doğru uygulama|
|[CA1065](../code-quality/ca1065-do-not-raise-exceptions-in-unexpected-locations.md)|Beklenmedik konumlarda özel durumlar yükseltmeyin|
|[CA1301](../code-quality/ca1301-avoid-duplicate-accelerators.md)|Yinelenen hızlandırıcılardan kaçının|
|[CA1400](../code-quality/ca1400-p-invoke-entry-points-should-exist.md)|P/Invoke giriş noktaları bulunmalıdır|
|[CA1401](../code-quality/ca1401-p-invokes-should-not-be-visible.md)|P/Invoke'lar görünür olmamalıdır|
|[CA1403](../code-quality/ca1403-auto-layout-types-should-not-be-com-visible.md)|Otomatik Yerleşim türleri COM görünebilir olmamalıdır|
|[CA1404](../code-quality/ca1404-call-getlasterror-immediately-after-p-invoke.md)|P/Invoke ardından hemen GetLastError Çağır|
|[CA1405](../code-quality/ca1405-com-visible-type-base-types-should-be-com-visible.md)|COM görünebilir tür taban türler COM görünebilir olmalıdır|
|[CA1410](../code-quality/ca1410-com-registration-methods-should-be-matched.md)|COM kayıt yöntemleri eşleşmesi|
|[CA1415](../code-quality/ca1415-declare-p-invokes-correctly.md)|P/Invokes doğru bildirin|
|[CA1821](../code-quality/ca1821-remove-empty-finalizers.md)|Boş Sonlandırıcıları kaldırın|
|[CA1900](../code-quality/ca1900-value-type-fields-should-be-portable.md)|Değer tür alanları taşınabilir olmalıdır|
|[CA1901](../code-quality/ca1901-p-invoke-declarations-should-be-portable.md)|P/Invoke bildirimleri taşınabilir olmalıdır|
|[CA2002](../code-quality/ca2002-do-not-lock-on-objects-with-weak-identity.md)|Zayıf kimliği olan nesneleri kilitlemeyin|
|[CA2100](../code-quality/ca2100-review-sql-queries-for-security-vulnerabilities.md)|SQL sorgularını güvenlik açıkları için gözden geçirin|
|[CA2101](../code-quality/ca2101-specify-marshaling-for-p-invoke-string-arguments.md)|P/Invoke dize bağımsız değişkenleri için sıralama belirtin|
|[CA2108](../code-quality/ca2108-review-declarative-security-on-value-types.md)|Değer türleri üzerinde bildirimsel güvenliği gözden geçirin|
|[CA2111](../code-quality/ca2111-pointers-should-not-be-visible.md)|İşaretçiler görünür olmamalıdır|
|[CA2112](../code-quality/ca2112-secured-types-should-not-expose-fields.md)|Güvenli türler alanları açığa çıkarmamalıdır|
|[CA2114](../code-quality/ca2114-method-security-should-be-a-superset-of-type.md)|Yöntem güvenliği türün bir üst kümesi olmalıdır|
|[CA2116](../code-quality/ca2116-aptca-methods-should-only-call-aptca-methods.md)|APTCA yöntemleri yalnızca APTCA yöntemlerini çağırmalıdır|
|[CA2117](../code-quality/ca2117-aptca-types-should-only-extend-aptca-base-types.md)|APTCA türleri yalnızca APTCA taban türlerini genişletmelidir|
|[CA2122](../code-quality/ca2122-do-not-indirectly-expose-methods-with-link-demands.md)|Bağlantı talepleri olan yöntemleri dolaylı olarak gösterme|
|[CA2123](../code-quality/ca2123-override-link-demands-should-be-identical-to-base.md)|Geçersiz kılma bağlantı talepleri taban ile özdeş olmalıdır|
|[CA2124](../code-quality/ca2124-wrap-vulnerable-finally-clauses-in-outer-try.md)|Kaydırma savunmasız son tümcelerini dış deneme|
|[CA2126](../code-quality/ca2126-type-link-demands-require-inheritance-demands.md)|Tür bağlantı talepleri devralma taleplerini gerektirir|
|[CA2131](../code-quality/ca2131-security-critical-types-may-not-participate-in-type-equivalence.md)|Güvenlik kritik türleri tür eşdeğerliğine katılamaz|
|[CA2132](../code-quality/ca2132-default-constructors-must-be-at-least-as-critical-as-base-type-default-constructors.md)|Varsayılan oluşturucular en az taban tür varsayılan oluşturucular kadar kritik olmalıdır|
|[CA2133](../code-quality/ca2133-delegates-must-bind-to-methods-with-consistent-transparency.md)|Temsilciler tutarlı saydamlığı olan yöntemlere bağlamanız gerekir|
|[CA2134](../code-quality/ca2134-methods-must-keep-consistent-transparency-when-overriding-base-methods.md)|Yöntemler taban yöntemleri geçersiz kılarken tutarlı saydamlığı tutmalıdır|
|[CA2137](../code-quality/ca2137-transparent-methods-must-contain-only-verifiable-il.md)|Saydam yöntemler yalnızca doğrulanabilir IL içermelidir|
|[CA2138](../code-quality/ca2138-transparent-methods-must-not-call-methods-with-the-suppressunmanagedcodesecurity-attribute.md)|Saydam yöntemler SuppressUnmanagedCodeSecurity özniteliğine sahip yöntemleri çağırmamalıdır|
|[CA2140](../code-quality/ca2140-transparent-code-must-not-reference-security-critical-items.md)|Saydam kod güvenlik kritik nesnelerine başvurmamalıdır|
|[CA2141](../code-quality/ca2141-transparent-methods-must-not-satisfy-linkdemands.md)|Saydam yöntemler LinkDemands getirmelidir değil|
|[CA2146](../code-quality/ca2146-types-must-be-at-least-as-critical-as-their-base-types-and-interfaces.md)|Türleri kendi taban türleri ve arabirimleri en az kadar kritik olmalıdır|
|[CA2147](../code-quality/ca2147-transparent-methods-may-not-use-security-asserts.md)|Saydam yöntemler güvenlik kullanamazsınız onaylar|
|[CA2149](../code-quality/ca2149-transparent-methods-must-not-call-into-native-code.md)|Saydam yöntemler yerel kod içine çağırmamalıdır|
|[CA2200](../code-quality/ca2200-rethrow-to-preserve-stack-details.md)|Yığın ayrıntılarını korumak için yeniden fırlatma|
|[CA2202](../code-quality/ca2202-do-not-dispose-objects-multiple-times.md)|Nesne birden çok kez atmayın|
|[CA2207](../code-quality/ca2207-initialize-value-type-static-fields-inline.md)|Değer türü statik alanları satır içi başlatın|
|[CA2212](../code-quality/ca2212-do-not-mark-serviced-components-with-webmethod.md)|Hizmet verilen bileşenleri WebMethod ile işaretlemeyin|
|[CA2213](../code-quality/ca2213-disposable-fields-should-be-disposed.md)|Atılabilen alanlar atılmalıdır|
|[CA2214](../code-quality/ca2214-do-not-call-overridable-methods-in-constructors.md)|Geçersiz kılınabilir yöntemleri oluşturucular içinde çağırmayın|
|[CA2216](../code-quality/ca2216-disposable-types-should-declare-finalizer.md)|Atılabilir türler sonlandırıcıyı bildirmelidir|
|[CA2220](../code-quality/ca2220-finalizers-should-call-base-class-finalizer.md)|Sonlandırıcılar taban sınıf çağırmalıdır|
|[CA2229](../code-quality/ca2229-implement-serialization-constructors.md)|Serileştirme oluşturucularını uygulayın|
|[CA2231](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)|ValueType.Equals geçersiz kılma üzerinde eşittir işlecini aşırı yükleme|
|[CA2232](../code-quality/ca2232-mark-windows-forms-entry-points-with-stathread.md)|İşareti Windows Forms giriş noktalarını STAThread ile|
|[CA2235](../code-quality/ca2235-mark-all-non-serializable-fields.md)|Tüm serileştirilebilir olmayan alanları işaretleyin|
|[CA2236](../code-quality/ca2236-call-base-class-methods-on-iserializable-types.md)|ISerializable türler üzerinde taban sınıf yöntemlerini çağırın|
|[CA2237](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)|İşareti ISerializable türleri SerializableAttribute ile|
|[CA2238](../code-quality/ca2238-implement-serialization-methods-correctly.md)|Serileştirme yöntemlerini doğru uygulama|
|[CA2240](../code-quality/ca2240-implement-iserializable-correctly.md)|ISerializable doğru uygulama|
|[CA2241](../code-quality/ca2241-provide-correct-arguments-to-formatting-methods.md)|Biçimlendirme yöntemlerine doğru bağımsız değişkenleri sağlayın|
|[CA2242](../code-quality/ca2242-test-for-nan-correctly.md)|NaN için doğru sınayın|
|[CA1000](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)|Genel türlerde statik üyeleri bildirme|
|[CA1002](../code-quality/ca1002-do-not-expose-generic-lists.md)|Genel listeleri gösterme|
|[CA1003](../code-quality/ca1003-use-generic-event-handler-instances.md)|Genel olay işleyici örnekleri kullan|
|[CA1004](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)|Genel yöntemler tür parametresi sağlamalıdır|
|[CA1005](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)|Genel türlerde aşırı parametrelerden kaçının|
|[CA1006](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)|Üye imzalarında genel türleri geçirmeyin|
|[CA1007](../code-quality/ca1007-use-generics-where-appropriate.md)|Uygun yerlerde genel türler kullanın|
|[CA1008](../code-quality/ca1008-enums-should-have-zero-value.md)|Numaralandırmalar sıfır değerine sahip olmalıdır|
|[CA1010](../code-quality/ca1010-collections-should-implement-generic-interface.md)|Koleksiyonlar genel arabirim uygulamalıdır|
|[CA1011](../code-quality/ca1011-consider-passing-base-types-as-parameters.md)|Temel türleri parametre olarak geçirmeyi düşünün|
|[CA1012](../code-quality/ca1012-abstract-types-should-not-have-constructors.md)|Soyut türler oluşturucular bulunmamalıdır|
|[CA1013](../code-quality/ca1013-overload-operator-equals-on-overloading-add-and-subtract.md)|Aşırı yüklemesi üzerinde eşittir aşırı işlecini ekleme ve çıkarma|
|[CA1014](../code-quality/ca1014-mark-assemblies-with-clscompliantattribute.md)|İşareti derlemeleri CLSCompliantAttribute|
|[CA1017](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)|İşareti derlemeleri ComVisibleAttribute ile|
|[CA1018](../code-quality/ca1018-mark-attributes-with-attributeusageattribute.md)|İşareti öznitelikleri AttributeUsageAttribute ile|
|[CA1019](../code-quality/ca1019-define-accessors-for-attribute-arguments.md)|Öznitelik bağımsız değişkenleri için erişimcileri tanımlayın|
|[CA1023](../code-quality/ca1023-indexers-should-not-be-multidimensional.md)|Dizin oluşturucular çok boyutlu olmamalıdır|
|[CA1024](../code-quality/ca1024-use-properties-where-appropriate.md)|Uygun yerlerde özellikler kullan|
|[CA1025](../code-quality/ca1025-replace-repetitive-arguments-with-params-array.md)|Tekrarlanan bağımsız değişkenleri params dizisi ile değiştirin|
|[CA1026](../code-quality/ca1026-default-parameters-should-not-be-used.md)|Varsayılan parametreler kullanılmamalıdır|
|[CA1027](../code-quality/ca1027-mark-enums-with-flagsattribute.md)|Numaralandırmaları FlagsAttribute ile işaretle|
|[CA1028](../code-quality/ca1028-enum-storage-should-be-int32.md)|Numaralandırma depolaması Int32 olmalıdır|
|[CA1030](../code-quality/ca1030-use-events-where-appropriate.md)|Uygun yerlerde olaylar kullanın|
|[CA1031](../code-quality/ca1031-do-not-catch-general-exception-types.md)|Genel özel durum türleri catch değil|
|[CA1032](../code-quality/ca1032-implement-standard-exception-constructors.md)|Standart özel durum oluşturucuları uygulayın|
|[CA1034](../code-quality/ca1034-nested-types-should-not-be-visible.md)|İç içe geçmiş türler görünebilir olmamalıdır|
|[CA1035](../code-quality/ca1035-icollection-implementations-have-strongly-typed-members.md)|ICollection uygulamalarında türü kesin olarak belirtilmiş üyeler olmalıdır|
|[CA1036](../code-quality/ca1036-override-methods-on-comparable-types.md)|Yöntemleri karşılaştırılabilir türlerde geçersiz kılın|
|[CA1038](../code-quality/ca1038-enumerators-should-be-strongly-typed.md)|Numaralandırmalar kesin türü belirtilmiş|
|[CA1039](../code-quality/ca1039-lists-are-strongly-typed.md)|Listeleri kesin türü belirtilmiş|
|[CA1041](../code-quality/ca1041-provide-obsoleteattribute-message.md)|ObsoleteAttribute iletisi sağlayın|
|[CA1043](../code-quality/ca1043-use-integral-or-string-argument-for-indexers.md)|Dizin oluşturucular için tamsayı veya dize bağımsız değişkeni kullanın|
|[CA1044](../code-quality/ca1044-properties-should-not-be-write-only.md)|Özellikler yalnızca yazma olmamalıdır|
|[CA1046](../code-quality/ca1046-do-not-overload-operator-equals-on-reference-types.md)|Başvuru türlerinde eşittir işlecini aşırı yüklemeyin|
|[CA1047](../code-quality/ca1047-do-not-declare-protected-members-in-sealed-types.md)|Korumalı türlerde korunan üyeleri bildirmeyin|
|[CA1048](../code-quality/ca1048-do-not-declare-virtual-members-in-sealed-types.md)|Korumalı türlerde sanal üyeleri bildirme|
|[CA1050](../code-quality/ca1050-declare-types-in-namespaces.md)|Ad alanlarında türleri bildirin|
|[CA1051](../code-quality/ca1051-do-not-declare-visible-instance-fields.md)|Görünür örnek alanlarını bildirme|
|[CA1052](../code-quality/ca1052-static-holder-types-should-be-sealed.md)|Statik tutucu türleri mühürlenmelidir|
|[CA1053](../code-quality/ca1053-static-holder-types-should-not-have-constructors.md)|Statik tutucu türlerinde oluşturucular bulunmamalıdır|
|[CA1054](../code-quality/ca1054-uri-parameters-should-not-be-strings.md)|URI parametreleri dizeler olmamalıdır|
|[CA1055](../code-quality/ca1055-uri-return-values-should-not-be-strings.md)|URI dönüş değerleri dizeler olmamalıdır|
|[CA1056](../code-quality/ca1056-uri-properties-should-not-be-strings.md)|URI özellikleri dizeler olmamalıdır|
|[CA1057](../code-quality/ca1057-string-uri-overloads-call-system-uri-overloads.md)|Dize URI aşırı yüklemeleri System.Uri aşırı çağırın|
|[CA1058](../code-quality/ca1058-types-should-not-extend-certain-base-types.md)|Türler belli temel türleri genişletmemelidir|
|[CA1059](../code-quality/ca1059-members-should-not-expose-certain-concrete-types.md)|Üyeler belli somut türleri göstermemelidir|
|[CA1064](../code-quality/ca1064-exceptions-should-be-public.md)|Özel durumlar genel olmamalıdır|
|[CA1500](../code-quality/ca1500-variable-names-should-not-match-field-names.md)|Değişken adları alan adlarıyla eşleşmemelidir|
|[CA1502](../code-quality/ca1502-avoid-excessive-complexity.md)|Aşırı karmaşıklıktan kaçının|
|[CA1708](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)|Tanımlayıcılar örnekten daha fazla farklı olmalıdır|
|[CA1716](../code-quality/ca1716-identifiers-should-not-match-keywords.md)|Tanımlayıcılar anahtar sözcükleri eşleşmemelidir|
|[CA1801](../code-quality/ca1801-review-unused-parameters.md)|Kullanılmayan parametreleri gözden geçir|
|[CA1804](../code-quality/ca1804-remove-unused-locals.md)|Kullanılmayan yerel öğeleri kaldırın|
|[CA1809](../code-quality/ca1809-avoid-excessive-locals.md)|Aşırı yerel öğelerden Kaçın|
|[CA1810](../code-quality/ca1810-initialize-reference-type-static-fields-inline.md)|Başvuru türü statik alanları satır içi başlatın|
|[CA1811](../code-quality/ca1811-avoid-uncalled-private-code.md)|Çağrılmayan özel kodlardan kaçının|
|[CA1812](../code-quality/ca1812-avoid-uninstantiated-internal-classes.md)|Örneklendirilmemiş iç sınıflardan kaçının|
|[CA1813](../code-quality/ca1813-avoid-unsealed-attributes.md)|Korumasız özniteliklerden kaçının|
|[CA1814](../code-quality/ca1814-prefer-jagged-arrays-over-multidimensional.md)|Basit diziler çok boyutlu dizilere tercih|
|[CA1815](../code-quality/ca1815-override-equals-and-operator-equals-on-value-types.md)|Geçersiz kılma eşittir ve işleç değer türlerinde eşittir|
|[CA1819](../code-quality/ca1819-properties-should-not-return-arrays.md)|Özellikler diziler döndürmemelidir|
|[CA1820](../code-quality/ca1820-test-for-empty-strings-using-string-length.md)|Dize uzunluğunu kullanarak boş dizeler için sınayın|
|[CA1822](../code-quality/ca1822-mark-members-as-static.md)|Statik olarak işareti üyeleri|
|[CA1823](../code-quality/ca1823-avoid-unused-private-fields.md)|Kullanılmayan özel alanlardan kaçının|
|[CA2201](../code-quality/ca2201-do-not-raise-reserved-exception-types.md)|Ayrılmış özel durum türleri yükseltmeyin|
|[CA2205](../code-quality/ca2205-use-managed-equivalents-of-win32-api.md)|Win32 API'sının yönetilen eşdeğerlerini kullanın|
|[CA2208](../code-quality/ca2208-instantiate-argument-exceptions-correctly.md)|Bağımsız değişken özel durumlarını doğru örnekleyin|
|[CA2211](../code-quality/ca2211-non-constant-fields-should-not-be-visible.md)|Sabit olmayan alanlar görünür olmamalıdır|
|[CA2217](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)|Numaralandırmaları FlagsAttribute ile işaretlemeyin|
|[CA2219](../code-quality/ca2219-do-not-raise-exceptions-in-exception-clauses.md)|Durum yan tümceleri içinde özel durumları yükseltmeyin|
|[CA2221](../code-quality/ca2221-finalizers-should-be-protected.md)|Sonlandırıcılar korunmalıdır|
|[CA2222](../code-quality/ca2222-do-not-decrease-inherited-member-visibility.md)|Devralınan üye görünürlüğünü azaltmayın|
|[CA2223](../code-quality/ca2223-members-should-differ-by-more-than-return-type.md)|Üyeler dönüş türünden daha farklı farklı olmalıdır|
|[CA2224](../code-quality/ca2224-override-equals-on-overloading-operator-equals.md)|Eşittir işlecini eşittiri geçersiz kılma|
|[CA2225](../code-quality/ca2225-operator-overloads-have-named-alternates.md)|İşleç aşırı yüklemeleri adlandırılmış Alternatiflere sahiptir|
|[CA2226](../code-quality/ca2226-operators-should-have-symmetrical-overloads.md)|İşleçler simetrik aşırı yüklemelere sahip|
|[CA2227](../code-quality/ca2227-collection-properties-should-be-read-only.md)|Koleksiyon Özellikleri salt okunur olmalıdır|
|[CA2230](../code-quality/ca2230-use-params-for-variable-arguments.md)|Değişken bağımsız değişkenler için params kullanın|
|[CA2234](../code-quality/ca2234-pass-system-uri-objects-instead-of-strings.md)|Dizeler yerine System.Uri nesneleri geçirin|
|[CA2239](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md)|İsteğe bağlı alanlar için seri kaldırma yöntemler sağlayın|