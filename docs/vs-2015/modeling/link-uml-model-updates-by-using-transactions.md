---
title: İşlemleri kullanarak UML model güncelleştirmelerini bağlama | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- UML API, transactions
ms.assetid: a1df6c38-a3d1-4a3f-82bc-c8f363ab916e
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: fb8bb5dfd5238871324b786f120d618d70f14b43
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51800412"
---
# <a name="link-uml-model-updates-by-using-transactions"></a>İşlemleri kullanarak UML model güncelleştirmelerini bağlama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Uzantı, Visual Studio'da UML tasarımcılarına tanımladığınızda, birkaç değişiklik adlı tek bir işlem içinde gruplandırabilirsiniz bir *bağlantılı geri alma bağlamının*. Visual Studio'nun hangi sürümlerinin UML modellerini desteklemek için bkz [mimari ve Modelleme Araçları sürüm desteği](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
 Varsayılan olarak, kodunuzun modelde yaptığı her değişikliği ayrı ayrı kullanıcı tarafından alınabilir. Örneğin, eğer iki UML sınıf adlarını değiştirir bir menü komutu tanımlarsanız, bir kullanıcı komutunu çağırın ve ardından tek bir geri alma gerçekleştirin. Bu, bir ad, ancak diğer, modelinizi istenmeyen bir durumda bırakarak değişikliği geri.  
  
 Bunu önlemek için kodunuzu bir dizi değişikliği bir işlem içinde gerçekleştirebilirsiniz. Bu kullanıcı için tek bir değişiklik gibi değişiklikleri yapar. Bir sonraki geri alma komutu tüm dizileri geri alacaktır.  
  
 Bir ek yararı kodunuzun özel bir durum yaratarak veya işlemi iptal ediliyor kısmen tamamlanmış değişiklikler dizisini geri olur.  
  
## <a name="to-group-changes-into-a-single-transaction"></a>Tek bir işlem grubu değişiklikleri  
 Proje başvurularınızın bu .NET derlemesini içerdiğinden emin olun:  
  
 **Microsoft.VisualStudio.Modeling.Sdk. [sürüm] .dll**  
  
 Sınıfınız içinde türüne sahip içeri aktarılmış bir özelliğini bildirin <xref:Microsoft.VisualStudio.Modeling.ExtensionEnablement.ILinkedUndoContext>:  
  
 `using Microsoft.VisualStudio.Modeling.ExtensionEnablement;`  
  
 `...`  
  
 `class … {`  
  
 `[Import]`  
  
 `public ILinkedUndoContext LinkedUndoContext { get; set; }`  
  
 Modeli değiştiren bir yöntem içinde değişikliklerinizi bir işlem içine alın:  
  
 `using (ILinkedUndoTransaction transaction =`  
  
 `LinkedUndoContext.BeginTransaction("my updates"))`  
  
 `{`  
  
 `// code to update model elements or shapes goes here`  
  
 `transaction.Commit();`  
  
 `}`  
  
 Aşağıdakilere dikkat edin:  
  
-   Her zaman dahil etmelisiniz `Commit()` işlem sonunda. Bir işlem uygulanmadan, işlem geri alınacaktır. Diğer bir deyişle, model işlemin başındaki durumuna geri yüklenecektir.  
  
-   Eğer işlem içinde yakalanmamış özel bir durum oluşursa, işlem geri alınacaktır. İçine almak için sıklıkla kullanılan bir desendir `using` işlem içinde bloğunu bir `try…catch` blok.  
  
-   İşlemleri iç içe geçirebilirsiniz.  
  
-   Herhangi bir boş olmayan ad sağlayabilirsiniz `BeginTransaction()`.  
  
-   Yalnızca UML Model Store bu işlemlerden etkilenir. İşlemlerin modellenmesi şunları etkilemez: değişkenler, dosyalar ve veritabanları gibi harici depolar katman diyagramları ve kod modelleri.  
  
## <a name="example"></a>Örnek  
  
```  
    using Microsoft.VisualStudio.Modeling.ExtensionEnablement;  
    using Microsoft.VisualStudio.Uml.Interfaces;  
    using Microsoft.VisualStudio.Uml.Classes;  
    using Microsoft.VisualStudio.Uml.Extensions;  
    using System.Linq;  
    using System.ComponentModel.Composition;  
 ...  
  [Import]  
  public ILinkedUndoContext LinkedUndoContext { get; set; }  
  
  /// <summary>  
  /// Swap the names of the currently selected elements.  
  /// </summary>  
  public void Execute(IMenuCommand command)  
  {  
    var selectedShapes =  
      Context.CurrentDiagram.GetSelectedShapes<IClassifier>();  
    if (selectedShapes.Count() < 2) return;  
    IClassifier firstElement = selectedShapes.First().Element;  
    IClassifier lastElement = selectedShapes.Last().Element;  
    string firstName = firstElement.Name;  
    // Perform changes inside a transaction so that undo  
    // works as a single change.  
    using (ILinkedUndoTransaction transaction =   
      LinkedUndoContext.BeginTransaction("Swap names"))  
    {  
        firstElement.Name = lastElement.Name;  
        lastElement.Name = firstName;  
        transaction.Commit();  
    }  
 }  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [UML API ile programlama](../modeling/programming-with-the-uml-api.md)   
 [Modelleme Diyagramında Menü komutu tanımlama](../modeling/define-a-menu-command-on-a-modeling-diagram.md)   
 [UML modellerini ve diyagramları genişletme](../modeling/extend-uml-models-and-diagrams.md)



