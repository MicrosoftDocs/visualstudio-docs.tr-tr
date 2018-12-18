---
title: 'Nasıl yapılır: modeli güncelleştirmek için işlemleri kullanma | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e24436a5-7f97-401b-bc83-20d188d10d5b
caps.latest.revision: 9
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 50f9d491ed52098edb8a8ccd1a7b2f9c8834447e
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49236866"
---
# <a name="how-to-use-transactions-to-update-the-model"></a>Nasıl yapılır: Modeli Güncelleştirmek için İşlemleri Kullanma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

İşlem depoya yapılan değişiklikler bir grup olarak kabul edilir emin olun. Gruplandırılmış değişiklikler kaydedilmiş veya tek bir birim olarak geri alındı.  
  
 Her program kodunuza değiştirir, ekler veya Store içinde herhangi bir öğeyi siler [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Görselleştirme ve modelleme SDK'sı, bir işlem içinde bunu yapmalısınız. Etkin örneği olmalıdır <xref:Microsoft.VisualStudio.Modeling.Transaction> değişiklik gerçekleştiğinde Store ile ilişkili. Bu, tüm model öğelerini, ilişkiler, şekiller, diyagramları ve özellikleri için geçerlidir.  
  
 İşlem mekanizması tutarsız durumları kaçınmanıza yardımcı olur. İşlem sırasında bir hata meydana gelirse, tüm değişiklikler geri alınır. Kullanıcı bir geri alma komutu gerçekleştiriyorsa, her bir son işlem tek bir adım olarak kabul edilir. Açıkça bunları ayrı işlemlerde yerleştirdiğiniz sürece kullanıcı son zamanlarda bir değişiklik bölümlerini geri alamazsınız.  
  
## <a name="opening-a-transaction"></a>Bir işlem açma  
 Bir işlem yönetmenin en kolay yöntemi olan bir `using` ifadesi içine bir `try...catch` deyimi:  
  
```  
Store store; ...  
try  
{  
  using (Transaction transaction =  
    store.TransactionManager.BeginTransaction("update model"))  
    // Outermost transaction must always have a name.  
  {  
    // Make several changes in Store:  
    Person p = new Person(store);  
    p.FamilyTreeModel = familyTree;  
    p.Name = "Edward VI";  
    // end of changes to Store  
  
    transaction.Commit(); // Don't forget this!  
  } // transaction disposed here  
}  
catch (Exception ex)  
{  
  // If an exception occurs, the Store will be   
  // rolled back to its previous state.  
}  
```  
  
 En son engelleyen bir özel durum, `Commit()` Store önceki durumuna sıfırlanacağı değişiklik sırasında gerçekleşir. Bu hataları modeli tutarsız bir durumda bırakmadığından emin olmanıza yardımcı olur.  
  
 Herhangi bir sayıda bir işlem içinde değişiklik yapabilirsiniz. Yeni işlemlerinin etkin bir işlem içinde açabilirsiniz. İç içe işlem işleme veya içeren işlem sona ermeden önce geri yüklemeniz gerekir. Daha fazla bilgi için örneğin bakın <xref:Microsoft.VisualStudio.Modeling.Transaction.TransactionDepth%2A> özelliği.  
  
 Yaptığınız değişiklikleri kalıcı hale getirmek için gereken `Commit` bırakılana önce işlem. İşlem içinde yakalanmamış özel bir durum oluşursa, Store değişiklikleri önce durumuna sıfırlar.  
  
## <a name="rolling-back-a-transaction"></a>Bir işlemi geri alınıyor  
 Store kalır veya işlem önce durumuna döner emin olmak için bu taktikleri birini kullanabilirsiniz:  
  
1.  İşlem kapsamı içinde yakalanmamış bir özel durum yükseltir.  
  
2.  Açıkça işlem geri alma:  
  
    ```  
    this.Store.TransactionManager.CurrentTransaction.Rollback();  
    ```  
  
## <a name="transactions-do-not-affect-non-store-objects"></a>İşlem Store olmayan nesneler etkilemez  
 İşlemler yalnızca Store durumunu yönetir. Bunlar, dosyaları, veritabanları veya sıradan türleriyle DSL tanımının dışında bildirilen nesneler gibi dış öğeleri için yapılmış kısmi değişiklikler geri alınamaz.  
  
 Bir özel durum böyle bir değişiklik Store hatasıyla tutarsız bırakabilir, özel durum işleyicisinde, olasılığını uğraşmanız. Dış kaynaklara Store nesneleriyle eşitlenmiş kalmasını sağlamak için bir olay işleyicilerini kullanarak dış her nesne bir mağaza öğeye eşleştirmektir yoludur. Daha fazla bilgi için [olay işleyicileri yaymak değişiklikleri dışında modeli](../modeling/event-handlers-propagate-changes-outside-the-model.md).  
  
## <a name="rules-fire-at-the-end-of-a-transaction"></a>Bir işlem sonunda kurallarını tetikleme  
 İşlem bırakılmadan önce bir işlem sonunda, deponun öğelere eklenen kurallar tetiklenir. Her kural değişen bir model öğesine uygulanan bir yöntemdir. Örneğin, alt model öğesi değiştirildiğinde bir şekil durumunu güncelleştirme "Düzelt" kuralları vardır ve bir model öğesi oluşturulduğunda, Şekil oluşturma. Hiçbir belirtilen tetikleyicisinin tetikleme sırasını yoktur. Bir kural tarafından gerçekleştirilen bir değişikliğin başka bir kural tetikleyebilir.  
  
 Kendi kurallarınızı tanımlayabilirsiniz. Kuralları hakkında daha fazla bilgi için bkz. [yanıt verme ve değişiklikleri yayma](../modeling/responding-to-and-propagating-changes.md).  
  
 Kurallar, bir geri alma, bir yineleme veya bir geri alma komutu sonrasında başlatılmaz.  
  
## <a name="transaction-context"></a>İşlem bağlamı  
 Her işlem, istediğiniz bilgileri depolamak sözlük sahiptir:  
  
 `store.TransactionManager`  
  
 `.CurrentTransaction.TopLevelTransaction`  
  
 `.Context.Add(aKey, aValue);`  
  
 Bu kurallar arasında bilgi aktarmak için kullanışlıdır.  
  
## <a name="transaction-state"></a>İşlem durumu  
 Değişiklikleri geri alma veya yineleme bir işlem tarafından neden oluyorsa önlemek için gereken bazı durumlarda bir değişiklik yayılıyor. Store içinde başka bir değere güncelleştirebilirsiniz bir özellik değeri işleyicisi yazma Bu, örneğin, durum ortaya çıkabilir. Geri alma işlemi Store tüm değerleri önceki durumlarına sıfırlar. çünkü, güncelleştirilmiş değeri hesaplamak gerekli değildir. Bu kodu kullanın:  
  
```  
if (!this.Store.InUndoRedoOrRollback) {...}  
```  
  
 Deponun bir dosyadan başlangıçta yüklenirken kuralları tetikleyebilir. Bu değişikliklere yanıt verme önlemek için bu seçeneği kullanın:  
  
```  
if (!this.Store.InSerializationTransaction) {...}  
  
```



