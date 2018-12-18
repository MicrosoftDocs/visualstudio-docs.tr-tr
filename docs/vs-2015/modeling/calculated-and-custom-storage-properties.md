---
title: Hesaplanan ve özel depolama özellikleri | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Domain-Specific Language, programming domain properties
ms.assetid: 42b785f9-2b0f-4f13-a6b4-246e5e0d477a
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 82d90d6965558ba6d28753fb71b3b227a84467a6
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49852862"
---
# <a name="calculated-and-custom-storage-properties"></a>Hesaplanan ve Özel Depolama Özellikleri
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Tüm etki alanı özellikleri bir etki alanına özgü dil (DSL) diyagramı ve dil gezgininizde kullanıcıya görüntülenen ve program kodu tarafından erişilebilir. Ancak, özellikleri değerlerini depolanan şekilde farklılık gösterir.  
  
## <a name="kinds-of-domain-properties"></a>Tür etki alanı özelliklerinin özellikleri  
 DSL tanımındaki ayarladığınız **tür** aşağıdaki tabloda listelendiği gibi bir etki alanı özelliği:  
  
|Etki alanı özellik türü|Açıklama|  
|--------------------------|-----------------|  
|**Standart** (varsayılan)|Kaydedilen bir alan özelliği *depolamak* ve dosyaya seri hale getirilmiş.|  
|**Hesaplanan**|Depoda kaydedilmez, ancak diğer değerlerinden hesaplanır salt okunur etki alanı özelliği.<br /><br /> Örneğin, `Person.Age` hesaplanmasını `Person.BirthDate`.<br /><br /> Hesaplamayı gerçekleştiren kod sağlamanıza gerek. Genellikle, diğer etki alanı özellikleri değerini hesaplayın. Bununla birlikte, dış kaynaklara de kullanabilirsiniz.|  
|**Özel depolama**|Doğrudan deposunda kaydedilmez ancak hem get hem de set olabilir bir etki alanı özelliği.<br /><br /> Alma ve değerini ayarlama yöntemleri sağlaması gerekir.<br /><br /> Örneğin, `Person.FullAddress` içinde depolanacak `Person.StreetAddress`, `Person.City`, ve `Person.PostalCode`.<br /><br /> Örneğin almak ve bir veritabanından değerleri ayarlamak, dış kaynaklara da erişebilirsiniz.<br /><br /> Kod deposundaki değerleri ayarlanmamalıdır olduğunda `Store.InUndoRedoOrRollback` geçerlidir. Bkz: [işlemleri ve özel ayarlayıcılar](#setters).|  
  
## <a name="providing-the-code-for-a-calculated-or-custom-storage-property"></a>Kod bir hesaplanmış ya da özel depolama özelliği için sağlama  
 Hesaplanmış veya özel depolama alanına bir alan özelliği türünü ayarlarsanız, erişim yöntemi sağlamak zorunda. Çözümünüzü oluşturduğunuzda, bir hata raporu ne gereklidir bildirir.  
  
#### <a name="to-define-a-calculated-or-custom-storage-property"></a>Hesaplanmış veya özel depolama özelliği tanımlamak için  
  
1.  DslDefinition.dsl, diyagram veya etki alanı özelliği seçin **DSL Gezgini**.  
  
2.  İçinde **özellikleri** penceresinde **tür** alanı **hesaplanan** veya **özel depolama**.  
  
     Siz de ayarladığınızdan emin olun, **türü** istediğiniz.  
  
3.  Tıklayın **tüm Şablonları Dönüştür** araç **Çözüm Gezgini**.  
  
4.  Üzerinde **derleme** menüsünde tıklatın **Çözümü Derle**.  
  
     Aşağıdaki hata iletisini alıyorsunuz: "*YourClass* Get için bir tanım içermiyor*YourProperty*."  
  
5.  Hata iletisini çift tıklayın.  
  
     Dsl\GeneratedCode\DomainClasses.cs veya DomainRelationships.cs açılır. Vurgulanan yöntemi çağrısı, yorum, Get için bir uygulama sunmak amacıyla ister*YourProperty*().  
  
    > [!NOTE]
    >  Bu dosya, DslDefinition.dsl oluşturulur. Bu dosyayı düzenlerseniz, değişikliklerinizi bir sonraki tıklayışınızda olmalıdır **tüm Şablonları Dönüştür**. Bunun yerine ayrı bir dosyada gerekli yöntemi ekleyin.  
  
6.  Oluşturun veya bir sınıf dosyası ayrı bir klasörde, örneğin CustomCode açın\\*YourDomainClass*. cs.  
  
     Ad alanı oluşturulan kod ile aynı olduğundan emin olun.  
  
7.  Sınıf dosyasında, bir etki alanı sınıfı kısmi uygulaması yazma. Sınıfında, eksik bir tanımı yazma `Get` aşağıdaki örneğe benzer yöntemi:  
  
    ```  
    namespace Company.FamilyTree  
    {  public partial class Person  
       {  int GetAgeValue()  
          { return System.DateTime.Today.Year - this.BirthYear; }  
    }  }  
    ```  
  
8.  Ayarlarsanız **tür** için **özel depolama**, sağlamanız gerekecektir bir `Set` yöntemi. Örneğin:  
  
    ```  
    void SetAgeValue(int value)  
    { if (!Store.InUndoRedoOrRollback)  
        this.BirthYear =   
            System.DateTime.Today.Year - value; }  
    ```  
  
     Kod deposundaki değerleri ayarlanmamalıdır olduğunda `Store.InUndoRedoOrRollback` geçerlidir. Bkz: [işlemleri ve özel ayarlayıcılar](#setters).  
  
9. Derleme ve çözümü çalıştırın.  
  
10. Test özelliği. Denemek emin **geri** ve **Yinele**.  
  
##  <a name="setters"></a> İşlemler ve özel ayarlayıcılar  
 Yöntemi genellikle etkin bir işlem çağrıldığı için özel depolama özellik kümesi yönteminde, açık bir işlem gerekmez.  
  
 Ancak, küme yöntemini kullanıcı geri alma veya yineleme çağırır veya bir işlem geri alınıyor çağrılabilir. Zaman <xref:Microsoft.VisualStudio.Modeling.Store.InUndoRedoOrRollback%2A> true kümesi yönteminizi davranış şu şekilde olur:  
  
- Bu değişiklikler diğer etki alanı özellikleri için değerler atama deposundaki yapmamanız gerekir. Geri alma yöneticisi değerlerini ayarlar.  
  
- Ancak, veritabanı veya dosya içeriklerini mağazası dışındaki nesnelere gibi herhangi bir dış kaynağa güncelleştirmeniz gerekir. Bu bunlar içinde synchronism deposundaki değerlerle tutulur emin olmanızı sağlar.  
  
  Örneğin:  
  
```  
void SetAgeValue(int value)  
{   
  // If we are in Undo, no changes to Store objects:  
  if (!this.Store.InUndoRedoOrRollback)  
  {   
    this.BirthYear = System.DateTime.Today.Year - value;   
  }  
  // But always update external objects:  
  System.IO.File.WriteAllText(AgeFile, value);  
}  
```  
  
 İşlemler hakkında daha fazla bilgi için bkz. [gezinme ve güncelleştirme Program kodundaki modeli](../modeling/navigating-and-updating-a-model-in-program-code.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Gezinme ve Program kodundaki modeli güncelleştirme](../modeling/navigating-and-updating-a-model-in-program-code.md)   
 [Etki alanı özelliklerinin özellikleri](../modeling/properties-of-domain-properties.md)   
 [Nasıl yapılır: Etki Alanına Özgü bir Dili Tanımlama](../modeling/how-to-define-a-domain-specific-language.md)



