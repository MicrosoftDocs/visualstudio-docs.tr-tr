---
title: Salt okunur kesimler oluşturmak için kilitleme ilkesi tanımlama | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fa549c71-2bf6-4b08-b7b2-7756dd6f1dc8
caps.latest.revision: 14
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 298e649704731157164db363dfa198ff6f2cdc41
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49893838"
---
# <a name="defining-a-locking-policy-to-create-read-only-segments"></a>Salt Okunur Kesimler Oluşturmak için Kilitleme İlkesi Tanımlama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Olan Değiştirilemezlik API'si [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Görselleştirme ve modelleme SDK'sını okuyun ancak değiştirilmemiş kilit bölümünü veya tümünü bir etki alanına özgü dil (DSL) modeli için bir program sağlar. Bu salt okunur seçeneği, örneğin, bir kullanıcı iş arkadaşlarınızı Not ekleme ve bir DSL model gözden geçirmek isteyebilirsiniz ancak bunları özgün değiştirmesini engelleyebilirsiniz kullanılabilir.  
  
 Ayrıca, bir DSL yazarı olarak tanımlayabilirsiniz bir *kilitleme ilkesi.* İzin verilen, izin verilmiyor veya zorunlu hangi kilitleri kilitleme ilkesi tanımlar. Örneğin, bir DSL yayımladığınızda, yeni komutları ile genişletmek için üçüncü taraf geliştiriciler teşvik edebilir. Ancak belirli bölümlerini model salt okunur durumunu değiştirmesini önlemek için kilitleme ilkesi kullanabilirsiniz.  
  
> [!NOTE]
>  Yansıma kullanarak kilitleme ilkesi atlatılabilir. Üçüncü taraf geliştiriciler için açık bir sınır sağlar, ancak güçlü güvenlik sağlamaz.  
  
 Daha fazla bilgi ve örnekler kullanılabilir [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] [Görselleştirme ve modelleme SDK'sı](http://go.microsoft.com/fwlink/?LinkId=186128) Web sitesi.  
  
## <a name="setting-and-getting-locks"></a>Ayarlama ve alma kilitleri  
 Kilit deposu, bölüm veya tek bir öğe ayarlayabilirsiniz. Örneğin, bu ifade, model öğesinin silinmesini önlemek ve değiştirilmesini özelliklerini de engeller:  
  
```  
using Microsoft.VisualStudio.Modeling.Immutability; ...  
element.SetLocks(Locks.Delete | Locks.Property);  
```  
  
 Diğer kilit değerler ilişkileri, öğe oluşturma, taşıma bölümleri yeniden sıralama bağlantıları bir role arasındaki değişiklikleri önlemek için kullanılabilir.  
  
 Kilitler, hem kullanıcı eylemlerini ve program kodu için geçerlidir. Program kodu bir değişiklik çalışırsa bir `InvalidOperationException` oluşturulur. Kilitleri, bir geri alma veya yineleme işleminde göz ardı edilir.  
  
 Bir öğenin herhangi bir kilidi belirtilen bir kümede kullanarak sahip olup olmadığını keşfetmek `IsLocked(Locks)` ve geçerli bir öğe üzerinde kilit kümesini kullanarak edinebilirsiniz `GetLocks()`.  
  
 Bir kilit, bir işlem kullanmadan ayarlayabilirsiniz. Kilit veritabanı deponun bir parçası değil. Örneğin T:System.Windows.PropertyChangedCallback içinde bir kilit bir değerin bir değişikliğe yanıt deposunda ayarlarsanız, geri alma işleminin bir parçası olan değişiklik sağlamalıdır.  
  
 Bu yöntemler tanımlanan genişletme yöntemleri olan <xref:Microsoft.VisualStudio.Modeling.Immutability> ad alanı.  
  
### <a name="locks-on-partitions-and-stores"></a>Bölümleri ve depoları kilitler  
 Kilitleri, bölümler ve mağazası için uygulanabilir. Bölüm üzerinde ayarlanmış olan bir kilidi bölümündeki tüm öğelere uygulanır. Bu nedenle, örneğin, aşağıdaki deyim bir bölümdeki tüm öğeleri, kendi kilit durumlarını bağımsız olarak silinmesini engeller. Bununla birlikte, diğer gibi kilitler `Locks.Property` yine de ayrı ayrı öğeler üzerinde ayarlanabilir:  
  
```  
partition.SetLocks(Locks.Delete);  
```  
  
 Bölümleri ve öğeleri bu kilit ayarlarını ne olursa olsun tüm alt öğeleri, Store üzerinde ayarlanmış olan bir kilidi uygular.  
  
### <a name="using-locks"></a>Kilitleri kullanma  
 Aşağıdaki örnekler gibi düzenleri uygulamak için kilit kullanabilirsiniz:  
  
-   Tüm öğeleri ve ilişkileri açıklamaları temsil eden hariç değişiklikleri izin vermeyin. Bu, değişiklik yapmadan bir model öğesine açıklama eklemek kullanıcıların sağlar.  
  
-   Değişiklikleri varsayılan bir bölüme izin verme, ancak Diyagram bölümünde yapılan değişikliklere izin. Kullanıcı diyagramda düzenleyebilir, ancak temel alınan model değiştirilemez.  
  
-   Ayrı bir veritabanında kayıtlı kullanıcılardan oluşan bir grubu dışında Store değişiklikleri izin vermeyin. Diğer kullanıcılar için diyagrama ve modele salt okunurdur.  
  
-   Diyagramın bir Boolean özelliği ayarlanmışsa değişiklikleri modele engellemek için true. Bu özelliği değiştirmek için bir menü komutu belirtin. Bu değişiklikleri yapmaları olmayan kullanıcıların yanlışlıkla olun yardımcı olur.  
  
-   Eklenmesini ve silinmesini öğeleri ve ilişkileri belirli sınıfların izin verme, ancak özellik değişikliklerine izin. Bu kullanıcılar özelliklerini doldurabilirsiniz için sabit bir form sağlar.  
  
## <a name="lock-values"></a>Kilit değerler  
 Kilitleri Store, bölüm veya bireysel ModelElement ayarlayabilirsiniz. Kilitler olduğu bir `Flags` numaralandırma: kullanarak değerleri birleştirebilirsiniz '&#124;'.  
  
- Bir ModelElement kilitler, kilitler, bölümün her zaman ekleyin.  
  
- Bir bölümün kilitleri her zaman Store kilitler ekleyin.  
  
  Bölüm üzerinde bir kilit ayarlayın veya depolar ve aynı anda tek bir öğe üzerinde kilit devre dışı olamaz.  
  
|Değer|Yani `IsLocked(Value)` geçerlidir|  
|-----------|------------------------------------------|  
|Yok.|Kısıtlama yok.|  
|Özellik|Öğelerin etki alanı özellikleri değiştirilemez. Bu rolü ilişkisinde bir etki alanı sınıfı tarafından oluşturulan özellikler için geçerli değildir.|  
|Ekle|Bir bölümde yeni öğeleri ve bağlantılarına oluşturulamıyor veya depolar.<br /><br /> Uygulanamaz `ModelElement`.|  
|Taşıma|Öğesi, bölümler arasında taşınamaz `element.IsLocked(Move)` true ise veya `targetPartition.IsLocked(Move)` geçerlidir.|  
|Sil|Bu kilit öğe üzerinde ayarlanır veya herhangi bir öğelerine silme işlemi, katıştırılmış öğeleri ve şekiller gibi yayar bir öğe silinemiyor.<br /><br /> Kullanabileceğiniz `element.CanDelete()` öğenin silinip silinemeyeceği bulunacak.|  
|Yeniden sıralama|Bir roleplayer bağlantıları sıralama değiştirilemez.|  
|İçinde RolePlayer|Bu öğede kaynaklanan bağlantı kümesi değiştirilemez. Örneğin, yeni öğeler altında bu öğe eklenemiyor. Bu, bu öğenin hedefi olan bağlantılar etkilemez.<br /><br /> Bu öğe bir bağlantı varsa, kaynak ve hedef etkilenmez.|  
|Tümü|Bit düzeyinde OR diğer değerlerden.|  
  
## <a name="locking-policies"></a>Kilitleme ilkeleri  
 Bir DSL yazarı, tanımladığınız bir *kilitleme ilkesi*. Kilitleme ilkesi SetLocks(), işlemi moderates, böylece belirli kilitleri ayarlayın ya da belirli kilitleri ayarlanmalıdır zorunlu kılabilir olmasını engelleyebilir. Genellikle, kullanıcılar ya da kullanım, DSL'nin bir değişken bildirebilir aynı şekilde yanlışlıkla contravening gelen geliştiriciler önlemek için kilitleme ilkesi kullanacağınız `private`.  
  
 Kilitleme ilkesi, tüm öğelerde kilitleri öğe türünün bağımlı ayarlamak için de kullanabilirsiniz. Bunun nedeni, `SetLocks(Locks.None)` bir öğenin ilk kez oluşturulduğunda veya dosyasından seri durumdan her zaman çağrılır.  
  
 Ancak, bir ilke ömrü öğeye yer alan kilitlerin değiştirmek için kullanamazsınız. Bu etkiyi elde etmek için çağrıları kullanmalısınız `SetLocks()`.  
  
 Bir kilitleme ilkesi tanımlama için için gerekenler:  
  
-   Uygulayan bir sınıf oluşturma <xref:Microsoft.VisualStudio.Modeling.Immutability.ILockingPolicy>.  
  
-   Bu sınıf, DSL'nin DocData kullanılabilir olan hizmetlerini ekleyin.  
  
### <a name="to-define-a-locking-policy"></a>Kilitleme ilkesi tanımlama  
 <xref:Microsoft.VisualStudio.Modeling.Immutability.ILockingPolicy> Aşağıdaki tanımları içerir:  
  
```  
public interface ILockingPolicy  
{  
  Locks RefineLocks(ModelElement element, Locks proposedLocks);  
  Locks RefineLocks(Partition partition, Locks proposedLocks);  
  Locks RefineLocks(Store store, Locks proposedLocks);  
}  
```  
  
 Bir çağrı yapıldığında bu yöntem de çağrıldığında `SetLocks()` Store, bölüm veya model öğesi. Her bir yöntemin, önerilen bir kilit kümesi ile sağlanır. Önerilen kümeyi döndürebilir veya ekleme ve çıkarma kilitler.  
  
 Örneğin:  
  
```  
using Microsoft.VisualStudio.Modeling;  
using Microsoft.VisualStudio.Modeling.Immutability;  
namespace Company.YourDsl.DslPackage // Change  
{  
  public class MyLockingPolicy : ILockingPolicy  
  {  
    /// <summary>  
    /// Moderate SetLocks(this ModelElement target, Locks locks)  
    /// </summary>  
    /// <param name="element">target</param>  
    /// <param name="proposedLocks">locks</param>  
    /// <returns></returns>  
    public Locks RefineLocks(ModelElement element, Locks proposedLocks)  
    {  
      // In my policy, users can never delete an element,  
      // and other developers cannot easily change that:  
      return proposedLocks | Locks.Delete);  
    }  
    public Locks RefineLocks(Store store, Locks proposedLocks)  
    {  
      // Only one user can change this model:  
      return Environment.UserName == "aUser"   
           ? proposedLocks : Locks.All;  
    }  
  
```  
  
 Diğer kod olsa bile kullanıcılar öğeleri her zaman silebilir emin olmak için `SetLocks(Lock.Delete):`  
  
 `return proposedLocks & (Locks.All ^ Locks.Delete);`  
  
 Değişiklik MyClass her öğenin tüm özelliklerini engellemek için:  
  
 `return element is MyClass ? (proposedLocks | Locks.Property) : proposedLocks;`  
  
### <a name="to-make-your-policy-available-as-a-service"></a>İlkenizi hizmet olarak kullanılabilir hale getirmek için  
 İçinde `DslPackage` projesinde, aşağıdaki örneğe benzeyen kod içeren yeni bir dosya ekleyin:  
  
```  
using Microsoft.VisualStudio.Modeling;  
using Microsoft.VisualStudio.Modeling.Immutability;  
namespace Company.YourDsl.DslPackage // Change  
{   
  // Override the DocData GetService() for this DSL.  
  internal partial class YourDslDocData // Change  
  {  
    /// <summary>  
    /// Custom locking policy cache.  
    /// </summary>  
    private ILockingPolicy myLockingPolicy = null;  
  
    /// <summary>  
    /// Called when a service is requested.  
    /// </summary>  
    /// <param name="serviceType">Service requested</param>  
    /// <returns>Service implementation</returns>  
    public override object GetService(System.Type serviceType)  
    {  
      if (serviceType == typeof(SLockingPolicy)   
       || serviceType == typeof(ILockingPolicy))  
      {  
        if (myLockingPolicy == null)  
        {  
          myLockingPolicy = new MyLockingPolicy();  
        }  
        return myLockingPolicy;  
      }  
      // Request is for some other service.  
      return base.GetService(serviceType);  
    }  
}  
```



