---
title: Bir Windows formunda bir diyagram ekleme | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fa6cd040-7c88-4329-b9c3-2a80b312610f
caps.latest.revision: 3
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 04ecf5bd7bfc91e03f48e624d208a5b4f29b10b7
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49292532"
---
# <a name="embedding-a-diagram-in-a-windows-form"></a>Windows Forms'a Diyagram Ekleme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

DSL diyagramı içinde görüntülenen bir Windows Denetim, katıştırabilirsiniz [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] penceresi.  
  
## <a name="embedding-a-diagram"></a>Diyagram ekleme  
  
#### <a name="to-embed-a-dsl-diagram-in-a-windows-control"></a>Bir Windows denetiminde bir DSL diyagramı eklemek için  
  
1.  Yeni bir **kullanıcı denetimi** DslPackage projeye dosya.  
  
2.  Panel denetimi, kullanıcı denetimine ekleyin. Bu panelde DSL diyagramı içerir.  
  
     İhtiyacınız olan diğer denetimleri ekleyin.  
  
     Denetimin bağlantı özelliklerini ayarlayın.  
  
3.  Çözüm Gezgini'nde, kullanıcı denetimi dosyaya sağ tıklayın ve **kodu görüntüle**. Bu oluşturucu ve değişken için kodu ekleyin:  
  
    ```csharp  
  
    internal UserControl1(MyDSLDocView docView, Control content)  
      : this()  
    {  
      panel1.Controls.Add(content);  
      this.docView = docView;  
    }  
    private MyDSLDSLDocView docView;  
  
    ```  
  
4.  Aşağıdaki içeriğe sahip DslPackage projeye yeni bir dosya ekleyin:  
  
    ```  
    using System.Windows.Forms;  
    namespace Company.MyDSL  
    {  
      partial class MyDSLDocView  
      {  
        private UserControl1 container;  
        public override IWin32Window Window  
        {  
          get  
          {  
            if (container == null)  
            {  
              // Put our own form inside the DSL window:  
              container = new UserControl1(this,  
                (Control)base.Window);  
            }  
            return container;  
    } } } }  
  
    ```  
  
5.  DSL test etmek için F5 tuşuna basın ve bir örnek model dosyasını açın. Denetim içinde diyagramda görünür. Araç kutusu ve diğer özellikler normal şekilde çalışır.  
  
#### <a name="updating-the-form-using-store-events"></a>Store olayları kullanarak Form güncelleştiriliyor  
  
1.  Form Tasarımcısı'nda ekleme bir **ListBox** adlı `listBox1`. Bu modelde öğeleri listesi görüntülenir. Kullanarak modeli ile synchronism içinde tutulacak *olayları depolamak*. Daha fazla bilgi için [olay işleyicileri yaymak değişiklikleri dışında modeli](../modeling/event-handlers-propagate-changes-outside-the-model.md).  
  
2.  Özel kod dosyasında, daha fazla DocView sınıfı yöntemleri geçersiz kıl:  
  
    ```  
  
    partial class MyDSLDocView  
    {  
     /// <summary>  
     /// Register store event listeners.  
     /// This method is called when the model and diagram    
     /// have completed loading.   
     /// </summary>  
     protected override bool LoadView()  
      {  
        bool result = base.LoadView();  
        Store store = this.DocData.Store;  
        EventManagerDirectory emd = store.EventManagerDirectory;  
        DomainClassInfo componentClass = store.DomainDataDirectory.FindDomainClass(typeof(ExampleElement));  
        emd.ElementAdded.Add(componentClass, new EventHandler<ElementAddedEventArgs>(AddElement));  
        emd.ElementDeleted.Add(componentClass, new EventHandler<ElementDeletedEventArgs>(RemoveElement));  
  
        // Do the initial parts list:  
        container.SetUpFormFromModel();  
        return result;  
      }  
     /// <summary>  
     /// Listener method called on creation of each instance of   
     /// the ExampleElement class or its subclasses.  
     /// </summary>  
     private void AddElement(object sender, ElementAddedEventArgs e)  
     {  
       container.Add(e.ModelElement as ExampleElement);  
     }  
     /// <summary>  
     /// Listener method called after deletion of each instance of   
     /// the ExampleElement class or its subclasses.  
     /// </summary>  
     private void RemoveElement(object sender, ElementDeletedEventArgs e)  
     {  
       container.Remove(e.ModelElement as ExampleElement);  
     }  
  
    ```  
  
3.  Kullanıcı denetimi arkasındaki kodda eklenebilen ve kaldırılabilen öğelerde dinlemek için yöntemleri ekleyin:  
  
    ```  
  
          public partial class UserControl1 : UserControl { ...  
  
    private ExampleModel modelRoot;  
  
    internal void Add(ExampleElement e) { UpdatePartsList(); }  
    internal void Remove(ExampleElement e) { UpdatePartsList(); }  
  
    internal void SetUpFormFromModel()  
    {  
      modelRoot = this.docView.CurrentDiagram.ModelElement as ExampleModel;  
      UpdatePartsList();  
    }  
  
    private void UpdatePartsList()  
    {  
      StringBuilder builder = new StringBuilder();  
      listBox1.Items.Clear();  
      foreach (ExampleElement c in modelRoot.Elements)  
      {  
        listBox1.Items.Add(c.Name);  
      }  
    }  
  
    ```  
  
4.  DSL test etmek için F5 tuşuna basın ve deneysel örneğinde [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], örnek model dosyasını açın.  
  
     Liste kutusu model içinde öğeleri listesini gösterir ve sonra tüm ekleme veya silmeyi ve sonra geri al ve Yinele doğru olup olmadığını dikkat edin.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Gezinme ve Program kodundaki modeli güncelleştirme](../modeling/navigating-and-updating-a-model-in-program-code.md)   
 [Etki Alanına Özgü Dili Özelleştirmek için Kod Yazma](../modeling/writing-code-to-customise-a-domain-specific-language.md)

