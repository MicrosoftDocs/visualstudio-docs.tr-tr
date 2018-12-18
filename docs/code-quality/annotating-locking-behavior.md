---
title: Kilitlenme Davranışını Yorumlama
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- _Releases_nonreentrant_lock_
- _Lock_kind_mutex_
- _Lock_kind_critical_section_
- _Acquires_lock_
- _Releases_lock_
- _Has_lock_kind_
- _Releases_exclusive_lock_
- _Post_same_lock_
- _Requires_exclusive_lock_held_
- _Requires_shared_lock_held_
- _Lock_kind_semaphore_
- _Requires_lock_held_
- _Acquires_exclusive_lock_
- _Create_lock_level_
- _Acquires_nonreentrant_lock_
- _Releases_shared_lock_
- _Has_lock_level_
- _Lock_kind_spin_lock_
- _Requires_lock_not_held_
- _Acquires_shared_lock_
- _Requires_no_locks_held_
- _Lock_level_order_
- _Lock_kind_event_
ms.assetid: 07769c25-9b97-4ab7-b175-d1c450308d7a
author: mikeblome
ms.author: mblome
manager: wpickett
ms.workload:
- multiple
ms.openlocfilehash: 21c67bb8b99c2772e107ded9063a99940a7fac74
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/26/2018
ms.locfileid: "31901534"
---
# <a name="annotating-locking-behavior"></a>Kilitlenme Davranışını Yorumlama
Birden çok iş parçacıklı programınızdaki eşzamanlılık hataları önlemek için her zaman uygun kilitleme uzmanlık alanı izleyin ve SAL ek açıklamaları kullanın.

 Eşzamanlılık hataların yeniden, tanılama ve belirleyici olduğu için hata ayıklama notoriously zordur. İş parçacığı Interleaving hakkında mantığı en iyi zordur ve birkaç iş parçacığı yok kod gövdesi tasarlarken pratik olur. Bu nedenle, kilitleme uzmanlık çoklu iş parçacığı kullanan programlarda izlemeniz iyi bir uygulamadır. Örneğin, birden çok kilit alınırken kilitlenmeleri önlemeye yardımcı olur ancak kilit sipariş obeying ve paylaşılan bir kaynağa erişmeden önce uygun guarding kilit alınırken yarış durumları önlemeye yardımcı olur.

 Ne yazık ki, görünen basit kilitleme kuralları uygulamada izleyin şaşırtıcı zor olabilir. Günümüzün programlama dilleri ve derleyicileri temel bir sınırlama bunlar doğrudan çözümleme eşzamanlılık gereksinimleri ve belirtimi değil desteklemesidir. Kilitleri nasıl kullandıkları hakkında kendi amaçları ifade etmek için resmi olmayan kod açıklamaları güvenemeyeceklerini programcıları sahip.

 Eşzamanlılık SAL ek açıklamaları sorumluluk, veri guardianship, kilit sipariş hiyerarşi ve diğer beklenen kilitlenme davranışını kilitleme Kilitleme yan etkileri belirlemenize yardımcı olmak için tasarlanmıştır. Örtük kuralları açık hale getirerek SAL eşzamanlılık ek açıklamaları, kodunuzu kilitleme kuralları nasıl kullandığını belge tutarlı bir yol sağlar. Eşzamanlılık ek açıklamaları da yarış durumları, kilitlenmeler, eşleşmeyen eşitleme işlemleri ve diğer Zarif eşzamanlılık hataları bulmak için kod çözümleme araçları yeteneklerini artırır.

## <a name="general-guidelines"></a>Genel Yönergeler
 Ek Açıklamalar'ı kullanarak uygulamaları (callees) ve istemciler (arayanlar) arasında işlev tanımları tarafından kapsanan sözleşmeleri durum ve hızlı invariants ve diğer özellikleri daha fazla programın analiz geliştirmek.

 SAL destekleyen kilitleme elemanlar birçok farklı türdeki — Örneğin, kritik bölümler, zaman uyumu sağlayıcılar, döndürme kilitler ve diğer kaynak nesneleri. Birçok eşzamanlılık ek açıklamaları kilit ifade bir parametre olarak alın. Kurala göre bir kilit kilit nesnesini yol ifadesi tarafından belirtilir.

 Dikkate alınması gereken bazı iş parçacığı sahipliği kuralları:

-   Döndürme kilitlerini Temizle iş parçacığı sahipliğine uncounted kilitleri ' dir.

-   Zaman uyumu sağlayıcılar ve kritik bölümler Temizle iş parçacığı sahipliğine kilitleri sayılır.

-   Semafor ve olayları Temizle iş parçacığı sahipliği olmayan kilitleri sayılır.

## <a name="locking-annotations"></a>Kilitleme ek açıklamaları
 Aşağıdaki tabloda kilitleme ek açıklamaları listelenmektedir.

|Ek Açıklama|Açıklama|
|----------------|-----------------|
|`_Acquires_exclusive_lock_(expr)`|Bir işlev açıklama ekler ve postasına durumu işlevi bir tarafından adlı kilit nesnesi özel kullanım kilidi sayısını artırır olduğunu gösteren `expr`.|
|`_Acquires_lock_(expr)`|Bir işlev açıklama ekler ve postasına durumu işlevi bir tarafından adlı kilit nesnesi kilit sayısını artırır olduğunu gösteren `expr`.|
|`_Acquires_nonreentrant_lock_(expr)`|Tarafından adlı kilidi `expr` alınır.  Kilidi zaten tutulursa bir hata bildirilir.|
|`_Acquires_shared_lock_(expr)`|Bir işlev açıklama ekler ve postasına durumu işlevi bir tarafından adlı kilit nesnesi paylaşılan kilit sayısını artırır olduğunu gösteren `expr`.|
|`_Create_lock_level_(name)`|Simgenin bildiren bir deyim `name` ek açıklamalar kullanılabilir kilit düzeyi olmasını `_Has_Lock_level_` ve `_Lock_level_order_`.|
|`_Has_lock_kind_(kind)`|Bir kaynak nesne türü bilgilerini iyileştirmek için herhangi bir nesne açıklama ekler. Bazen ortak bir türü farklı kaynak türleri için kullanılır ve aşırı yüklenmiş türü anlamsal gereksinimleri çeşitli kaynaklar arasında ayrım yapmak yeterli değil. İşte bir listesi, önceden tanımlanmış `kind` Parametreler:<br /><br /> `_Lock_kind_mutex_`<br /> Kilit zaman uyumu sağlayıcılar için tür kimliği.<br /><br /> `_Lock_kind_event_`<br /> Tür kimliği için olaylar kilitleyin.<br /><br /> `_Lock_kind_semaphore_`<br /> Tür kimliği için semafor kilitleyin.<br /><br /> `_Lock_kind_spin_lock_`<br /> Kilit döndürme kilit için tür kimliği.<br /><br /> `_Lock_kind_critical_section_`<br /> Kritik bölümler için kilit tür kimliği.|
|`_Has_lock_level_(name)`|Kilit nesnesi açıklama ekler ve kilit düzeyi verir `name`.|
|`_Lock_level_order_(name1, name2)`|Arasında sıralama kilit sağlayan bir deyim `name1` ve `name2`.|
|`_Post_same_lock_(expr1, expr2)`|Bir işlev açıklama ekler ve postasına iki kilit durumunu gösteren `expr1` ve `expr2`, aynı kilit nesnesi varsa olarak kabul edilir.|
|`_Releases_exclusive_lock_(expr)`|Bir işlev açıklama ekler ve postasında tek tarafından adlı kilit nesnesi özel kilit sayısı işlevi azaltır durumunu gösteren `expr`.|
|`_Releases_lock_(expr)`|Bir işlev açıklama ekler ve postasında tek tarafından adlı kilit nesnesi kilit sayısı işlevi azaltır durumunu gösteren `expr`.|
|`_Releases_nonreentrant_lock_(expr)`|Tarafından adlı kilidi `expr` yayımlanır. Kilit şu anda düzenlenmemiş durumunda bir hata bildirilir.|
|`_Releases_shared_lock_(expr)`|Bir işlev açıklama ekler ve postasında tek tarafından adlı kilit nesnesi paylaşılan kilit sayısı işlevi azaltır durumunu gösteren `expr`.|
|`_Requires_lock_held_(expr)`|Bir işlev açıklama ekler ve öncesi içinde kilit sayısı tarafından adlı nesnenin durumunu gösteren `expr` en az biri.|
|`_Requires_lock_not_held_(expr)`|Bir işlev açıklama ekler ve öncesi içinde kilit sayısı tarafından adlı nesnenin durumunu gösteren `expr` sıfırdır.|
|`_Requires_no_locks_held_`|Bir işlev açıklama ekler ve denetleyicisi için bilinen tüm kilitleri kilit sayısı sıfır olduğunu gösterir.|
|`_Requires_shared_lock_held_(expr)`|Bir işlev açıklama ekler ve öncesi içinde paylaşılan kilit sayısı tarafından adlı nesnenin durumunu gösteren `expr` en az biri.|
|`_Requires_exclusive_lock_held_(expr)`|Bir işlev açıklama ekler ve öncesi içinde tarafından adlı nesne özel kilit sayısı durumunu gösteren `expr` en az biri.|

## <a name="sal-intrinsics-for-unexposed-locking-objects"></a>Gösterilmeyen kilitleme nesneler için SAL iç bilgileri
 Belirli kilit nesneleri ilişkili kilitleme işlevleri uygulaması tarafından sunulmaz.  Aşağıdaki tabloda gösterilmeyen kilit nesneler üzerinde çalışan işlevler hakkında ek açıklamalar etkinleştirmek SAL iç değişkenlerini listeler.

|Ek Açıklama|Açıklama|
|----------------|-----------------|
|`_Global_cancel_spin_lock_`|İptal döndürme kilit açıklar.|
|`_Global_critical_region_`|Kritik bölge açıklar.|
|`_Global_interlock_`|Birbirine kenetlenmiş işlemler açıklanmaktadır.|
|`_Global_priority_region_`|Öncelik bölge açıklar.|

## <a name="shared-data-access-annotations"></a>Paylaşılan veri erişim ek açıklamaları
 Aşağıdaki tabloda, paylaşılan veri erişimi için ek açıklamalar listelenmektedir.

|Ek Açıklama|Açıklama|
|----------------|-----------------|
|`_Guarded_by_(expr)`|Bir değişken açıklama ekler ve her değişken eriştiğinden, gösterir tarafından adlı kilit nesnesi kilit sayısı `expr` en az biri.|
|`_Interlocked_`|Bir değişken açıklama ekler ve eşdeğerdir `_Guarded_by_(_Global_interlock_)`.|
|`_Interlocked_operand_`|Açıklamalı işlevi, hedef işleneni çeşitli Interlocked işlevleri birinin parametresidir.  Bu işlenen özgü ek özellikleri olması gerekir.|
|`_Write_guarded_by_(expr)`|Bir değişken açıklama ekler ve her değişken değiştirildiğini, tarafından adlı kilit nesnesi kilit sayısı gösterir `expr` en az biri.|

## <a name="see-also"></a>Ayrıca Bkz.
 [C/C++ kod hatalarını azaltmak için SAL ek açıklamalarını kullanma](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md) [SAL anlama](../code-quality/understanding-sal.md) [işlev parametrelerini ve dönüş değerlerini açıklama](../code-quality/annotating-function-parameters-and-return-values.md) [işlevdavranışınıyorumlama](../code-quality/annotating-function-behavior.md) [Yapıları ve sınıfları yorumlama](../code-quality/annotating-structs-and-classes.md) [açıklamanın ne zaman ve nereye uygulanacağını belirtme](../code-quality/specifying-when-and-where-an-annotation-applies.md) [iç işlevler](../code-quality/intrinsic-functions.md) [en iyi uygulamalar ve Örnekler](../code-quality/best-practices-and-examples-sal.md) [kod çözümleme ekip blogu](http://go.microsoft.com/fwlink/p/?LinkId=251197)