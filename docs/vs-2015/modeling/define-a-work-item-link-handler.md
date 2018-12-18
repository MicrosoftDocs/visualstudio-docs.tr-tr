---
title: Bir iş öğesi bağlantı işleyicisini tanımlama | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- UML API
ms.assetid: d52e0bbf-0166-4bb4-a2e3-cefed6188875
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 7ce74627d1d2d48ab02e0b124fbc38949f1f76f9
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51733064"
---
# <a name="define-a-work-item-link-handler"></a>İş öğesi bağlantı işleyicisi tanımlama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio tümleştirmesi kullanıcı bir UML modeli öğesi ile bir iş öğesi arasında bir bağlantı oluşturur veya sildiğinde cevap veren uzantısı oluşturabilirsiniz. Örneğin, kullanıcı yeni bir iş öğesi bir model öğesine bağlamayı seçerse, kodunuz modeldeki değerlerden iş öğesi alanlarını başlatabilir.  
  
## <a name="set-up-a-uml-extension-solution"></a>Bir UML Uzantısı çözümü ayarlama  
 Bu, işleyicileri geliştirmenize ve bunları diğer kullanıcılara dağıtmanıza olanak tanır. İki Visual Studio projelerini ayarlamanız gerekir:  
  
-   Bağlantı işleyici kodu içeren bir sınıf kitaplığı projesi.  
  
-   Komut yüklemek için bir kapsayıcı görevi gören bir VSIX projesi. İsterseniz, aynı VSIX içine diğer bileşenleri dahil edebilirsiniz.  
  
#### <a name="to-set-up-the-visual-studio-solution"></a>Visual Studio çözümünü ayarlamak için  
  
1.  Varolan bir VSIX çözümüne ekleyerek veya yeni bir çözüm oluşturarak bir sınıf kitaplığı projesi oluşturun.  
  
    1.  Üzerinde **dosya** menüsünde seçin **yeni**, **proje**.  
  
    2.  Altında **yüklü şablonlar**, genişletme **Visual C#** veya **Visual Basic**, ardından Orta sütundaki tıklayın **sınıf kitaplığı**.  
  
    3.  Ayarlama **çözüm** yeni bir çözüm oluşturmak veya önceden açmış olduğunuz VSIX çözümüne bir bileşen eklemek isteyip istemediğinizi belirtmek için.  
  
    4.  Proje kümesi adını ve konumunu ve Tamam'a tıklayın.  
  
2.  Çözümünüz bir tane içermiyorsa, bir VSIX projesi oluşturun.  
  
    1.  İçinde **Çözüm Gezgini**, çözümün kısayol menüsünde **Ekle**, **yeni proje**.  
  
    2.  Altında **yüklü şablonlar**, genişletme **Visual C#** veya **Visual Basic**, ardından **genişletilebilirlik**. Orta sütundaki seçin **VSIX projesi**.  
  
3.  VSIX projesinin çözümün başlangıç projesi olarak ayarlayın.  
  
    -   Çözüm Gezgini'nde VSIX projesinin kısayol menüsünden seçin **başlangıç projesi olarak ayarla**.  
  
4.  İçinde **source.extension.vsixmanifest**altında **içerik**, sınıf kitaplığı projesini MEF Bileşeni olarak ekleyin.  
  
    1.  Üzerinde **meta verileri** sekmesinde, VSIX için bir ad belirleyin.  
  
    2.  Üzerinde **hedefleri Yükle** sekmesinde, hedefler olarak Visual Studio sürümleri ayarlayın.  
  
    3.  Üzerinde **varlıklar** sekmesini, bir **yeni**ve iletişim kutusunda şunu ayarlayın:  
  
         **Tür** = **MEF Bileşeni**  
  
         **Kaynak** = **mevcut çözümde bir proje**  
  
         **Proje** = *, sınıf kitaplığı projesi*  
  
## <a name="defining-the-work-item-link-handler"></a>İş öğesi bağlantı işleyicisini tanımlama  
 Aşağıdaki görevlerin tümünü sınıf kitaplığı projesinde gerçekleştirin.  
  
### <a name="project-references"></a>Proje başvuruları  
 Aşağıdaki [!INCLUDE[TLA2#tla_net](../includes/tla2sharptla-net-md.md)] derlemelerini projenizin başvurularına:  
  
 `Microsoft.TeamFoundation.WorkItemTracking.Client.dll`  
  
 `Microsoft.VisualStudio.TeamFoundation.WorkItemTracking.dll Microsoft.VisualStudio.Modeling.Sdk.[version]`  
  
 `Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml`  
  
 `Microsoft.VisualStudio.Uml.Interfaces`  
  
 `System.ComponentModel.Composition`  
  
 `System.Drawing` -Örnek kodu ile kullanılan  
  
 Altında bu başvurulardan birini bulamazsa **.Net** sekmesinde **Başvuru Ekle** iletişim kutusunda Visual Studio [sürüm] \Common7\IDE\ \Program bulmak için Gözat sekmesini kullanın PrivateAssemblies\\.  
  
### <a name="import-the-work-item-namespace"></a>İş öğesi Namespace içeri aktarma  
 İçinde [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] proje **başvuruları**, aşağıdaki derlemelere başvurular ekleyin:  
  
- Microsoft.TeamFoundation.WorkItemTracking.Client.dll  
  
- Microsoft.VisualStudio.TeamFoundation.WorkItemTracking.dll  
  
  Program kodunuzda aşağıdaki ad alanlarını içeri aktarın:  
  
```  
using System.ComponentModel.Composition;  
using Microsoft.VisualStudio.Uml.Classes;  
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml;  
using Microsoft.VisualStudio.TeamFoundation.WorkItemTracking;  
using System.Linq;  
```  
  
### <a name="define-the-linked-work-item-event-handler"></a>Bağlantılı iş öğesi olay işleyicisini tanımlama  
 Sınıf kitaplığı projesine bir sınıf dosyası ekleyin ve içeriğini aşağıdaki gibi ayarlayın. Ad alanını ve sınıf adları, istediğiniz şekilde değiştirin.  
  
```  
using System.ComponentModel.Composition;  
using Microsoft.VisualStudio.Uml.Classes;  
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml;  
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation;  
using Microsoft.VisualStudio.TeamFoundation.WorkItemTracking;  
using System.Linq;  
  
namespace WorkItems  
{  
  [Export(typeof(ILinkedWorkItemExtension))]  
  public class MyWorkItemExtension : ILinkedWorkItemExtension  
  {  
    // Called before a new work item is edited by the user.  
    // Use this to initialize work item fields from the model element.  
    public void OnWorkItemCreated(System.Collections.Generic.IEnumerable<IElement> elementsToBeLinked, IWorkItemDocument workItemDocument)  
    {  
      INamedElement namedElement =  
            elementsToBeLinked.First() as INamedElement;  
      if (namedElement != null)  
        workItemDocument.Item.Title = namedElement.Name;  
  
    }  
  
    // Called when any work item is linked to a model element.  
    public void OnWorkItemLinked(System.Collections.Generic.IEnumerable<IElement> elements, string serverUri, int workItemId)  
    {  
      foreach (IElement element in elements)  
        foreach (IShape shape in element.Shapes())  
          shape.Color = System.Drawing.Color.Red;  
    }  
  
    // Called when a work item is unlinked from a model element.  
    public void OnWorkItemRemoved(IElement element, string serverUri, int workItemId)  
    {  
      foreach (IShape shape in element.Shapes())  
        shape.Color = System.Drawing.Color.White;  
    }  
  }  
}  
```  
  
## <a name="testing-the-link-handler"></a>Bağlantı işleyicisini test etme  
 Test amaçları için Bağlantı işleyicinizi hata ayıklama modunda yürütün.  
  
> [!WARNING]
>  Zaten için TFS kaynak kod denetimi (oluşturmak veya bir çalışma öğesiyle bağlantılandırmak için SCC) bağlı olmanız gerekir. Farklı bir TFS SCC bağlantı açmayı denerseniz, Visual Studio otomatik olarak geçerli çözümü kapatır. Zaten için uygun SCC oluşturmak veya bir çalışma öğesiyle bağlantılandırmak denemeden önce bağlı olduğunuzdan emin olun. Visual Studio daha sonraki sürümleri için bir SCC bağlı değilseniz, menü komutlarını kullanılamaz.  
  
#### <a name="to-test-the-link-handler"></a>Bağlantı işleyicisini test etmek için  
  
1.  Tuşuna **F5**, veya **hata ayıklama** menüsünde seçin **hata ayıklamayı Başlat**.  
  
     Deneysel örneği [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] başlatır.  
  
     **Sorun giderme**: yeni [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] değil başlatın, VSIX projesinin çözümün başlangıç projesi olarak ayarlandığından emin olun.  
  
2.  Deneysel [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], açın veya bir modelleme projesi oluşturmak ve açmak veya bir modelleme diyagramı oluşturun.  
  
3.  UML sınıfı gibi bir model öğesi oluşturun ve adını ayarlayın.  
  
4.  Öğeye sağ tıklayın ve ardından **iş öğesi oluşturma**.  
  
    -   Gösteriyorsa **açık Team Foundation Server bağlantısı**, projeyi kapatın, uygun TFS'ye bağlanmak ve bu yordamı yeniden başlatmanız gerekir.  
  
    -   Alt iş öğesi türlerinin bir listesini gösterirse, birini tıklayın.  
  
         Yeni bir iş öğesi formu açılır.  
  
5.  Önceki bölümdeki örnek kodu kullandıysanız, çalışma öğesi başlığının model öğesi ile aynı olduğunu doğrulayın. Bu gösterir `OnWorkItemCreated()` çalışmıştır.  
  
6.  Kaydetme, formu doldurun ve iş öğesini kapatın.  
  
7.  Çalışma öğesinin artık kırmızı renk olduğunu doğrulayın. Bu gösterir `OnWorkItemLinked()` örnek kodda.  
  
     **Sorun giderme**: işleyici yöntemler çalışmadıysa doğrulayın:  
  
    -   Sınıf Kitaplığı projesini MEF Bileşeni olarak listelenir **içerik** listesinde **source.extensions.manifest** VSIX projesinde.  
  
    -   Doğru `Export` özniteliği işleyici sınıfına ve sınıf uygulayan bağlı `ILinkedWorkItemExtension`.  
  
    -   Tüm parametreleri `Import` ve `Export` öznitelikleri geçerlidir.  
  
## <a name="about-the-work-item-handler-code"></a>İş öğesi işleyici kodu hakkında  
  
### <a name="listening-for-new-work-items"></a>Yeni çalışma öğelerine yönelik dinleme  
 `OnWorkItemCreated` Kullanıcı model öğelere bağlanacak yeni bir iş öğesi oluşturmayı seçtiğinde çağrılır. Kodunuzu, iş öğesi alanlarını başlatabilir. İş öğesi alanları güncelleştirebilirsiniz kullanıcıyı sonra sunulan iş öğesi. İş öğesi başarıyla kaydedilene kadar model öğesine bağlantı oluşturulmaz.  
  
```  
public void OnWorkItemCreated(  
    IEnumerable<IElement> elementsToBeLinked,  
    IWorkItemDocument workItem)  
{  
  INamedElement namedElement =   
         elementsToBeLinked.First() as INamedElement;  
  if (namedElement != null)  
      workItem.Item.Title = namedElement.Name;  
}  
```  
  
### <a name="listening-for-link-creation"></a>Bağlantı oluşturmaya yönelik dinleme  
 `OnWorkItemLinked` bağlantı oluşturulduktan hemen sonra çağrılır. Bağlantıya yeni bir iş öğesi veya var olan bir öğe olup olmadığını çağrılır. Ayrıca, her iş öğesi için bir kez çağrılır.  
  
```  
public void OnWorkItemLinked  
        (IEnumerable<IElement> elements,   
         string serverUri, // TFS server  
         int workItemId)  
{  
  foreach (IElement element in elements)  
    foreach (IShape shape in element.Shapes())  
         shape.Color = System.Drawing.Color.Red;  
}  
```  
  
> [!NOTE]
>  Bu örneğin çalışması için bir proje başvurusu eklemelisiniz `System.Drawing.dll`ve ad alanı içe `Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation`. Ancak, bu eklemeler diğer uygulamaları için gerekli değildir `OnWorkItemLinked`.  
  
### <a name="listening-for-link-removal"></a>Bağlantı kaldırmaya yönelik dinleme  
 `OnWorkItemRemoved` silinmeden hemen her iş öğesi bağlantısı önce bir kez çağrılır. Bir model öğesi silinirse, onun tüm bağlantıları kaldırılacak.  
  
```  
public void OnWorkItemRemoved  
         (IElement element, string serverUri, int workItemId)  
{...}  
```  
  
## <a name="updating-a-work-item"></a>Bir iş öğesi güncelleştiriliyor  
 Team Foundation ad alanlarını kullanarak bir çalışma öğesini değiştirebilirsiniz.  
  
 Aşağıdaki örneği kullanmak için bu .NET derlemelerini projenizin başvurular ekleyin:  
  
-   Microsoft.TeamFoundation.Client.dll  
  
-   Microsoft.TeamFoundation.WorkItemTracking.Client.dll  
  
```  
  
using Microsoft.TeamFoundation.Client;  
using Microsoft.TeamFoundation.WorkItemTracking.Client;  
...  
public void OnWorkItemLinked  
        (IEnumerable<IElement> elements,   
         string serverUri, // TFS server  
         int workItemId)  
{  
  TfsTeamProjectCollection tfs =  
        TfsTeamProjectCollectionFactory  
            .GetTeamProjectCollection(new Uri(serverUri));  
  WorkItemStore workItemStore = new WorkItemStore(tfs);  
  WorkItem item = workItemStore.GetWorkItem(workItemId);  
  item.Open();  
  item.Title = "something";  
  item.Save();  
}   
```  
  
## <a name="accessing-the-work-item-reference-links"></a>İş öğesi başvuru bağlantılarına erişme  
 Bağlantıları gibi erişebilirsiniz:  
  
```  
//Get:  
string linkString = element.GetReference(ReferenceConstants.WorkItem);  
// Set:  
element.AddReference(ReferenceConstants.WorkItem, linkString, true);  
  
```  
  
 Biçimi `linkString` olan:  
  
 `string.Format(@"%{0}\{1}#{1}${2}", tfServer, projectCollection, RepositoryGuid, workItem.Id);`  
  
 burada:  
  
- Sunucunuz için URI şu şekilde olur:  
  
   `http://tfServer:8080/tfs/projectCollection`  
  
   Servis talebi önem `projectCollection`.  
  
- `RepositoryGuid` TFS bağlantınızdan elde edilebilir:  
  
  ```csharp  
  TfsTeamProjectCollection tpc = TfsTeamProjectCollectionFactory...;  
  RepositoryGuid= tpc.InstanceId;  
  
  ```  
  
  Başvurular hakkında daha fazla bilgi için bkz. [iliştirme başvuru dizeleri UML model öğelerini](../modeling/attach-reference-strings-to-uml-model-elements.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:Microsoft.TeamFoundation.WorkItemTracking.Client.WorkItemStore?displayProperty=fullName>   
 [Ve iş öğelerini model öğelere bağlama](../modeling/link-model-elements-and-work-items.md)   
 [Model öğelerine başvuru dizelerini iliştirme](../modeling/attach-reference-strings-to-uml-model-elements.md)   
 [Modelleme Uzantısı Tanımlama ve yükleme](../modeling/define-and-install-a-modeling-extension.md)   
 [UML API ile programlama](../modeling/programming-with-the-uml-api.md)



