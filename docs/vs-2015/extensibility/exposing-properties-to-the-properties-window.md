---
title: Özellikler ve özellik penceresini kullanıma sunma | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- properties [Visual Studio SDK], exposing in Property Browser
- properties [Visual Studio SDK]
- Property Browser, exposing properties
ms.assetid: 47f295b5-1ca5-4e7b-bb52-7b926b136622
caps.latest.revision: 37
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 026e7de7d56cb907682be52db2dbd32782822d9f
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51756904"
---
# <a name="exposing-properties-to-the-properties-window"></a>Özellikleri ve Özellik Penceresini Kullanıma Sunma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu izlenecek yol için bir nesnenin genel özellikleri gösterir **özellikleri** penceresi. Bu özellikler, yaptığınız değişiklikler yansıtılır **özellikleri** penceresi.  
  
## <a name="prerequisites"></a>Önkoşullar  
 Visual Studio 2015'ten başlayarak, size Visual Studio SDK İndirme Merkezi'nden yüklemeyin. Visual Studio kurulumunda isteğe bağlı bir özellik olarak eklenmiştir. VS SDK'yi daha sonra yükleyebilirsiniz. Daha fazla bilgi için [Visual Studio SDK'sını yükleme](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="exposing-properties-to-the-properties-window"></a>Özellikleri ve Özellik Penceresini Kullanıma Sunma  
 Bu bölümde, özel araç penceresi oluşturma ve ilişkili pencere bölmesi nesnesinde genel özelliklerini görüntülemek **özellikleri** penceresi.  
  
#### <a name="to-expose-properties-to-the-properties-window"></a>Özellikler ve özellik penceresini kullanıma sunmak için  
  
1.  Her Visual Studio uzantısı, uzantı varlıkları içeren bir VSIX dağıtım projesi ile başlar. Oluşturma bir [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] adlı VSIX projesi `MyObjectPropertiesExtension`. VSIX proje şablonunda bulabilirsiniz **yeni proje** iletişim altında **Visual C# / genişletilebilirlik**.  
  
2.  Adlı bir özel araç penceresi öğe şablonu ekleyerek bir araç penceresi `MyToolWindow`. İçinde **Çözüm Gezgini**, proje düğümüne sağ tıklayıp **Ekle / yeni öğe**. İçinde **Yeni Öğe Ekle iletişim**Git **Visual C# öğeleri / genişletilebilirlik** seçip **özel araç penceresi**. İçinde **adı** iletişim kutusunun altındaki alan, için dosya adını değiştirerek `MyToolWindow.cs`. Özel araç penceresi oluşturma hakkında daha fazla bilgi için bkz. [araç penceresi içeren bir uzantı oluşturma](../extensibility/creating-an-extension-with-a-tool-window.md).  
  
3.  MyToolWindow.cs açın ve aşağıdaki deyimi kullanarak:  
  
    ```  
    using System.Collections;  
    using System.ComponentModel;  
    using Microsoft.VisualStudio.Shell.Interop;  
    ```  
  
4.  Şimdi aşağıdaki alanları ekleyin `MyToolWindow` sınıfı.  
  
    ```csharp  
    private ITrackSelection trackSel;  
    private SelectionContainer selContainer;  
  
    ```  
  
5.  MyToolWindow sınıfa aşağıdaki kodu ekleyin.  
  
    ```csharp  
    private ITrackSelection TrackSelection  
    {  
        get  
        {  
            if (trackSel == null)  
                trackSel =  
                   GetService(typeof(STrackSelection)) as ITrackSelection;  
            return trackSel;  
        }  
    }  
  
    public void UpdateSelection()  
    {  
        ITrackSelection track = TrackSelection;  
        if (track != null)  
            track.OnSelectChange((ISelectionContainer)selContainer);  
    }  
  
    public void SelectList(ArrayList list)  
    {  
        selContainer = new SelectionContainer(true, false);  
        selContainer.SelectableObjects = list;  
        selContainer.SelectedObjects = list;  
        UpdateSelection();  
    }  
  
    public override void OnToolWindowCreated()  
    {  
        ArrayList listObjects = new ArrayList();  
        listObjects.Add(this);  
        SelectList(listObjects);  
    }  
    ```  
  
     `TrackSelection` Özelliği kullanan `GetService` almak için bir `STrackSelection` sağlayan hizmetini bir <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection> arabirimi. `OnToolWindowCreated` Olay işleyicisi ve `SelectList` yöntem birlikte yalnızca aracı penceresi bölmesi nesnenin kendisini içeren bir seçili nesnelerin listesi oluşturun. `UpdateSelection` Yöntemi söyler **özellikleri** penceresi araç penceresi bölmesi genel özelliklerini görüntülemek için.  
  
6.  Projeyi oluşturmak ve hata ayıklamaya başlayın. Visual Studio'nun deneysel örneğinde görüntülenmesi gerekir.  
  
7.  Varsa **özellikleri** penceresi görünür değilse, F4 tuşuna basarak açın.  
  
8.  Açık **MyToolWindow** penceresi. İçinde bulabilirsiniz **görünüm / diğer Windows**.  
  
     Penceresi açar ve genel özelliklerini pencere bölmesi görünür **özellikleri** penceresi.  
  
9. Değişiklik **açıklamalı alt yazı** özelliğinde **özellikleri** penceresine **My nesne özellikleri**.  
  
     MyToolWindow pencere başlığı buna göre değişir.  
  
## <a name="exposing-tool-window-properties"></a>Araç penceresi özelliklerini gösterme  
 Bu bölümde, bir araç penceresini ekleyin ve özelliklerini kullanıma sunar. Özelliklerine yaptığınız değişiklikler yansıtılır **özellikleri** penceresi.  
  
#### <a name="to-expose-tool-window-properties"></a>Araç penceresi özellikleri göstermek için  
  
1.  MyToolWindow.cs açın ve genel boolean özelliği IsChecked MyToolWindow sınıfına ekleyin.  
  
    ```csharp  
    [Category("My Properties")]  
    [Description("MyToolWindowControl properties")]  
    public bool IsChecked  
    {  
        get {  
            if (base.Content == null)  return false;  
            return (bool)(( MyToolWindowControl) base.Content).checkBox.IsChecked;   
        }  
        set {  
            ((MyToolWindowControl) base.Content).checkBox.IsChecked = value;  
        }  
    }  
    ```  
  
     Bu özellik, daha sonra oluşturacağınız WPF onay durumunu alır.  
  
2.  MyToolWindowControl.xaml.cs açın ve MyToolWindowControl Oluşturucu aşağıdaki kodla değiştirin.  
  
    ```vb  
    private MyToolWindow pane;  
    public MyToolWindowControl(MyToolWindow pane)  
    {  
        InitializeComponent();  
        this.pane = pane;  
        checkBox.IsChecked = false;  
    }  
    ```  
  
     Bu verir `MyToolWindowControl` erişim `MyToolWindow` bölmesi.  
  
3.  MyToolWindow.cs içinde değiştirmek `MyToolWindow` Oluşturucu aşağıdaki gibi:  
  
    ```csharp  
    base.Content = new MyToolWindowControl(this);  
    ```  
  
4.  MyToolWindowControl Tasarım görünümüne değiştirin.  
  
5.  Sil düğmesi ve onay kutusundan ekleme **araç kutusu** sol üst köşe için.  
  
6.  Checked ve Unchecked olaylar ekleyin. Tasarım görünümünde onay kutusunu işaretleyin. İçinde **özellikleri** penceresinde olay işleyicileri düğmesine tıklayın (üst sağında **özellikleri** pencere). Bulma **işaretli** ve türü **checkbox_Checked** metin kutusunda daha sonra bulmak **işaretlenmemiş** ve türü **checkbox_Unchecked** metin kutusuna.  
  
7.  Onay kutusu olay işleyicileri ekleyin:  
  
    ```csharp  
    private void checkbox_Checked(object sender, RoutedEventArgs e)  
    {  
        pane.IsChecked = true;  
        pane.UpdateSelection();  
    }  
    private void checkbox_Unchecked(object sender, RoutedEventArgs e)  
    {  
        pane.IsChecked = false;  
        pane.UpdateSelection();  
    }  
    ```  
  
8.  Projeyi oluşturmak ve hata ayıklamaya başlayın.  
  
9. Deneysel örneğinde açın **MyToolWindow** penceresi.  
  
     Pencerenin özelliklerinde arayın **özellikleri** penceresi. **IsChecked** özelliği penceresinin en altında görünür **My özellikleri** kategorisi.  
  
10. Onay kutusunu iade **MyToolWindow** penceresi. **IsChecked** içinde **özellikleri** penceresi değişiklikleri **True**. Onay kutusundaki işareti kaldırın **MyToolWindow** penceresi. **IsChecked** içinde **özellikleri** penceresi değişiklikleri **False**. Değiştirin **IsChecked** içinde **özellikleri** penceresi. Onay kutusuna **MyToolWindow** penceresi değişiklikleri, yeni değer ile eşleşmelidir.  
  
    > [!NOTE]
    >  Görüntülenen bir nesneyi elden gerekir, **özellikleri** penceresinin, çağrı `OnSelectChange` ile bir `null` seçim kapsayıcısı ilk. Özellik veya nesne disposing sonra güncelleştirilmiş bir seçim kapsayıcısı değiştirebilirsiniz <xref:Microsoft.VisualStudio.Shell.SelectionContainer.SelectableObjects%2A> ve <xref:Microsoft.VisualStudio.Shell.SelectionContainer.SelectedObjects%2A> listeler.  
  
## <a name="changing-selection-lists"></a>Seçim listeleri değiştiriliyor  
 Bu bölümde, bir özelliği temel sınıf için bir seçim listesi ekleyin ve araç penceresi arabirimi hangi seçim listesini görüntülemek için kullanın.  
  
#### <a name="to-change-selection-lists"></a>Seçim listelerini değiştirmek için  
  
1.  MyToolWindow.cs açın ve adlı bir ortak Sınıf Ekle `Simple`.  
  
    ```csharp  
    public class Simple  
    {  
        private string someText = "";  
  
        [Category("My Properties")]  
        [Description("Simple Properties")]  
        [DisplayName("My Text")]  
        public string SomeText  
        {  
            get { return someText; }  
            set { someText = value; }  
        }  
  
        [Category("My Properties")]  
        [Description("Read-only property")]  
        public bool ReadOnly  
        {  
            get { return false; }  
        }  
    }  
    ```  
  
2.  MyToolWindow sınıfı artı geçiş yapmak için iki yöntem SimpleObject özellik ekleme **özellikleri** penceresi seçim bölmesi arasındaki ve `Simple` nesne.  
  
    ```csharp  
    private Simple simpleObject = null;  
    public Simple SimpleObject  
    {  
        get  
        {  
            if (simpleObject == null) simpleObject = new Simple();  
            return simpleObject;  
        }  
    }  
  
    public void SelectSimpleList()  
    {  
        ArrayList listObjects = new ArrayList();  
        listObjects.Add(SimpleObject);  
        SelectList(listObjects);  
    }  
  
    public void SelectThisList()  
    {  
        ArrayList listObjects = new ArrayList();  
        listObjects.Add(this);  
        SelectList(listObjects);  
    }  
    ```  
  
3.  MyToolWindowControl.cs içinde onay kutusu işleyicileri bu kod satırlarını değiştirin:  
  
    ```csharp  
    private void checkbox_Checked(object sender, RoutedEventArgs e)  
     {  
        pane.IsChecked = true;  
        pane.SelectSimpleList();  
        pane.UpdateSelection();  
    }  
    private void checkbox_Unchecked(object sender, RoutedEventArgs e)  
    {  
        pane.IsChecked = false;  
        pane.SelectThisList();  
        pane.UpdateSelection();  
    }  
    ```  
  
4.  Projeyi oluşturmak ve hata ayıklamaya başlayın.  
  
5.  Deneysel örneğinde açın **MyToolWindow** penceresi.  
  
6.  Onay kutusunu seçin **MyToolWindow** penceresi. **Özellikleri** pencere görüntüler `Simple` nesnesinin özelliklerini, **SomeText** ve **salt okunur**. Onay kutusunu temizleyin. Ortak Özellikler penceresinin görünür **özellikleri** penceresi.  
  
    > [!NOTE]
    >  Görünen adı **SomeText** olduğu **Metnim**.  
  
## <a name="best-practice"></a>En iyi uygulama  
 Bu izlenecek yolda, <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> seçilebilir nesne koleksiyonu ve seçili nesne koleksiyonu aynı koleksiyonda olacak şekilde uygulanır. Yalnızca seçilen nesneyi özellik tarayıcısı listesinde görüntülenir. Daha eksiksiz bir ISelectionContainer uygulaması Reference.ToolWindow örneklere bakın.  
  
 Visual Studio araç pencereleri, Visual Studio oturumlar arasında devam ediyor. Araç pencere durumu kalıcı hale daha fazla bilgi için bkz: <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute>.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Özellikleri ve Özellik Penceresini Genişletme](../extensibility/extending-properties-and-the-property-window.md)

