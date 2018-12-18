---
title: Windows Forms'a Diyagram Ekleme
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 7afd12aa6277983f8b50eb1d7adfdd8396f8f960
ms.sourcegitcommit: ef828606e9758c7a42a2f0f777c57b2d39041ac3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/06/2018
ms.locfileid: "39567275"
---
# <a name="embed-a-diagram-in-a-windows-form"></a>Windows Formunda bir Diyagram ekleme

Bir DSL diyagramı Visual Studio penceresinde görünür bir Windows Denetim ekleyin.

## <a name="embed-a-dsl-diagram-in-a-windows-control"></a>Bir DSL diyagramı Windows denetimi ekleme

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
    private MyDSLDocView docView;
    ```

4.  Aşağıdaki içeriğe sahip DslPackage projeye yeni bir dosya ekleyin:

    ```csharp
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

5.  DSL test etmek için basın **F5** ve bir örnek model dosyasını açın. Denetim içinde diyagramda görünür. Araç kutusu ve diğer özellikler normal şekilde çalışır.

## <a name="update-the-form-using-store-events"></a>Formu deposu olayları kullanarak güncelleştirme

1.  Form Tasarımcısı'nda ekleme bir **ListBox** adlı `listBox1`. Bu modelde öğeleri listesi görüntülenir. Kullanarak modeli ile eşitlenir *olayları depolamak*. Daha fazla bilgi için [olay işleyicileri yaymak değişiklikleri dışında modeli](../modeling/event-handlers-propagate-changes-outside-the-model.md).

2.  Özel kod dosyasında, daha fazla DocView sınıfı yöntemleri geçersiz kıl:

    ```csharp
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

    ```csharp
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

4.  DSL test etmek için basın **F5** ve bir örnek model dosyasını Visual Studio'nun deneysel örneğinde açın.

     Liste kutusu model içinde öğeleri listesini gösterir ve sonra tüm ekleme veya silmeyi ve sonra geri al ve Yinele doğru olup olmadığını dikkat edin.

## <a name="see-also"></a>Ayrıca bkz.

- [Program Kodunda Modeli Gezinme ve Güncelleştirme](../modeling/navigating-and-updating-a-model-in-program-code.md)
- [Etki Alanına Özgü Dili Özelleştirmek için Kod Yazma](../modeling/writing-code-to-customise-a-domain-specific-language.md)
