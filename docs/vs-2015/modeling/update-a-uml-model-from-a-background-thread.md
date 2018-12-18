---
title: Arka plan iş parçacığı'ndan bir UML modeli güncelleştirme | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 42c06b0b-b681-4e19-b5f3-6116dd2a4072
caps.latest.revision: 15
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 4173b70cda9df39ce8a4500817fff199ed1a2996
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51749990"
---
# <a name="update-a-uml-model-from-a-background-thread"></a>Bir UML modelini arka plan iş parçacığı aracılığıyla güncelleştirme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bazen bir arka plan iş parçacığı modelinde değişiklikler yapmak yararlı olabilir. Örneğin, yavaş bir dış kaynaktan bilgi yüklüyorsanız güncelleştirmeleri denetlemek için bir arka plan iş parçacığı kullanabilirsiniz. Bu, her güncelleştirme bu sürede görmesine olanak sağlar.  
  
 Ancak, UML depolamasının bir iş parçacığı kasası olmadığını bilmelisiniz. Aşağıdaki önlemler önemlidir:  
  
-   Bir modele veya diyagrama yapılan her güncelleştirme kullanıcı arabirimi (UI) iş parçacığında yapılması gerekir. Arka plan iş parçacığı kullanmalısınız <xref:System.Windows.Forms.Control.Invoke%2A> veya `Dispatcher.` <xref:System.Windows.Threading.Dispatcher.Invoke%2A> UI iş parçacığının gerçek güncelleştirmeleri yapmasını sağlamak için.  
  
-   Bir dizi değişikliği tek bir işleme gruplarsanız, kullanıcıyı işlem sürerken modeli düzenlemekten alıkoymanızı öneririz. Aksi takdirde, kullanıcı tarafından gerçekleştirilen düzenlemeler aynı işlemin bir parçası haline gelir. Kullanıcının kalıcı bir iletişim kutusu göstererek değişiklik yapmasını engelleyebilirsiniz. İsterseniz, iletişim kutusunda İptal düğmesi sağlayabilirsiniz. Gelişmelerden kullanıcı değişiklikleri görebilirsiniz.  
  
## <a name="example"></a>Örnek  
 Bu örnek, bir model için birkaç değişiklik yapmak için bir arka plan iş parçacığı kullanır. Bir iletişim kutusu, iş parçacığı çalışırken kullanıcıyı çıkarmak için kullanılır. Bu basit örnekte, iletişim kutusunda İptal düğmesi sağlanır. Ancak, bu özelliği eklemek kolay olurdu.  
  
#### <a name="to-run-the-example"></a>Örneği çalıştırmak için  
  
1. Bir komut işleyici açıklandığı gibi bir C# projesi oluşturma [modelleme diyagramında menü komutu tanımlama](../modeling/define-a-menu-command-on-a-modeling-diagram.md).  
  
2. Projeyi bu derlemelere başvuruları içerdiğinden emin olun:  
  
   -   Microsoft.VisualStudio.ArchitectureTools.Extensibility  
  
   -   Microsoft.VisualStudio.Modeling.Sdk.[version]  
  
   -   Microsoft.VisualStudio.Modeling.Sdk.Diagrams. [sürüm]  
  
   -   Microsoft.VisualStudio.Uml.Interfaces  
  
   -   System.ComponentModel.Composition  
  
   -   System.Windows.Forms  
  
3. Projeye adlı bir Windows formu eklemek **ProgressForm**. Güncelleştirmelerin sürmekte olduğunu bildiren bir ileti görüntülemelidir. Herhangi bir denetim yok.  
  
4. 7. adımdan sonra gösterilen kodu içeren C# dosyası ekleyin.  
  
5. Derleme ve projeyi çalıştırın.  
  
    Yeni bir örneğini [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Deneysel modda başlatılacaktır.  
  
6. Oluşturun veya bir UML sınıf diyagramı deneysel örneğinde açın [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
7. UML sınıf diyagramında herhangi bir yere sağ tıklayın ve ardından **birkaç UML sınıfı Ekle**.  
  
   Çeşitli yeni sınıf kutuları diyagramda, birbiri ardına yarım saniye aralıklarla görünür.  
  
```csharp  
using System;  
using System.ComponentModel;  
using System.ComponentModel.Composition;  
using System.Threading;  
using System.Windows.Forms;  
  
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation;  
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml;  
using Microsoft.VisualStudio.Modeling.ExtensionEnablement;  
using Microsoft.VisualStudio.Uml.Classes;  
  
namespace BackgroundThreadProgressUI // CHANGE TO YOUR NAMESPACE  
{  
  [Export(typeof(ICommandExtension))]  
  [ClassDesignerExtension]  
  class UmlClassAdderCommand : ICommandExtension  
  {  
  
    [Import]  
    IDiagramContext context { get; set; }  
  
    [Import]  
    ILinkedUndoContext linkedUndoContext { get; set; }  
  
    // Called when the user runs the command.  
    public void Execute(IMenuCommand command)  
    {  
      // The form that will exclude the user.  
      ProgressForm form = new ProgressForm();  
  
      // System.ComponentModel.BackgroundWorker is a  
      // convenient way to run a background thread.  
      BackgroundWorker worker = new BackgroundWorker();  
      worker.WorkerSupportsCancellation = true;  
  
      worker.DoWork += delegate(object sender, DoWorkEventArgs args)  
      {  
        // This block will be executed in a background thread.  
  
        IClassDiagram diagram = context.CurrentDiagram as IClassDiagram;  
        IModelStore store = diagram.ModelStore;  
        const int CLASSES_TO_CREATE = 15;  
  
        // Group all the changes together.  
        using (ILinkedUndoTransaction transaction = linkedUndoContext.BeginTransaction("Background Updates"))  
        {  
          for (int i = 1; i < CLASSES_TO_CREATE; i++)  
          {  
            if (worker.CancellationPending)   
               return; // No commit - undo all.  
  
            // Create model elements using the UI thread by using  
            // the Invoke method on the progress form. Always   
            // modify the model and diagrams from a UI thread.  
            form.Invoke((MethodInvoker)(delegate  
            {  
              IClass newClass = store.Root.CreateClass();  
              newClass.Name = string.Format("NewClass{0}", i);  
              diagram.Display(newClass);  
            }));  
  
            // Sleep briefly so that we can watch the updates.  
            Thread.Sleep(500);  
          }  
  
          // Commit the transaction or it will be rolled back.  
          transaction.Commit();  
        }  
      };  
  
      // Close the form when the thread completes.  
      worker.RunWorkerCompleted += delegate(object sender, RunWorkerCompletedEventArgs args)  
      {  
        form.Close();  
      };  
  
      // Start the thread before showing the modal progress dialog.  
      worker.RunWorkerAsync();  
  
      // Show the form modally, parented on VS.  
      // Prevents the user from making changes while in progress.  
      form.ShowDialog();  
    }  
  
    public void QueryStatus(IMenuCommand command)  
    {  
      command.Enabled = command.Visible = true;  
    }  
  
    public string Text  
    {  
      get { return "Add several classes"; }  
    }  
  }  
}  
```  
  
#### <a name="to-allow-the-user-to-cancel-the-thread-in-the-example"></a>Kullanıcının örnekteki iş parçacığını iptal etmek izin vermek için  
  
1.  İlerleme iletişim kutusuna iptal düğmesi ekleyin.  
  
2.  İlerleme iletişim kutusuna aşağıdaki kodu ekleyin:  
  
     `public event MethodInvoker Cancel;`  
  
     `private void CancelButton_Click(object sender, EventArgs e)`  
  
     `{`  
  
     `Cancel();`  
  
     `}`  
  
3.  Execute() yönteminde formun oluşumu sonra bu satırı ekleyin:  
  
     `form.Cancel += delegate() { worker.CancelAsync(); };`  
  
### <a name="other-methods-of-accessing-the-ui-thread"></a>UI iş parçacığına erişmenin diğer yöntemleri  
 Bir iletişim kutusu oluşturmak istemiyorsanız diyagram görüntüleyen denetime erişebilirsiniz:  
  
 `DiagramView uiThreadHolder = context.CurrentDiagram.GetObject<Diagram>().ActiveDiagramView;`  
  
 Kullanabileceğiniz `uiThreadHolder.Invoke()` UI iş parçacığında işlemler gerçekleştirmek için.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Modelleme Diyagramında Menü komutu tanımlama](../modeling/define-a-menu-command-on-a-modeling-diagram.md)   
 [Modelleme diyagramında hareket işleyicisi tanımlama](../modeling/define-a-gesture-handler-on-a-modeling-diagram.md)



