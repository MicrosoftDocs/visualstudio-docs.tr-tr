---
title: .NET Framework 4 veya .NET Framework 4. 5'e geçiş Outlook projelerindeki form bölgelerini güncelleştirme
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office projects [Office development in Visual Studio], migrating to .NET Framework 4
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 97778716ad5be8e110c022048a3d04f4c980f839
ms.sourcegitcommit: 4cd4aef53e7035d23e7d1d0f66f51ac8480622a1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/05/2018
ms.locfileid: "34767981"
---
# <a name="update-form-regions-in-outlook-projects-that-you-migrate-to-the-net-framework-4-or-the-net-framework-45"></a>.NET Framework 4 veya .NET Framework 4. 5'e geçiş Outlook projelerindeki form bölgelerini güncelleştirme
  Outlook VSTO eklenti projesinde form bölgesini hedef Framework'ü değiştirilirse [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] veya daha sonra oluşturulan form bölgesi kodunu ve çalışma zamanında bazı form bölgesi sınıflarını başlatır herhangi bir kod bazı değişiklikler yapmalısınız.  
  
## <a name="update-the-generated-form-region-code"></a>Oluşturulan form bölgesi kodunu güncelleştirin  
 Projenin hedef çerçevesini değiştirilirse [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] veya daha sonra oluşturulan form bölgesi kodunu değiştirmeniz gerekir. Yaptığınız değişiklikler, Visual Studio ve form bölgelerindeki Outlook'tan alınan tasarlanan form bölgeleri için farklıdır. Bu tür bir form bölgeleri arasındaki farklar hakkında daha fazla bilgi için bkz: [oluşturma Outlook form bölgeleri](../vsto/creating-outlook-form-regions.md).  
  
### <a name="to-update-the-generated-code-for-a-form-region-that-you-designed-in-visual-studio"></a>Visual Studio'da tasarlanmış bir form bölgesi için oluşturulan kodu güncelleştirmek için  
  
1.  Form bölgesi arka plan kod dosyasına kod düzenleyicisinde açın. Bu dosya adlı *YourFormRegion*. Designer.cs veya *YourFormRegion*. Designer.vb olarak adlandırılır. Visual Basic projeleri bu dosyada görmek için tıklatın **tüm dosyaları göster** düğmesini **Çözüm Gezgini**.  
  
2.  Öğesinden türetilen böylece form bölgesi sınıfının bildirimini değiştirmek <xref:Microsoft.Office.Tools.Outlook.FormRegionBase> yerine `Microsoft.Office.Tools.Outlook.FormRegionControl`.  
  
3.  Form bölgesi sınıf aşağıdaki kodu örneklerde gösterildiği gibi değiştirin.  
  
     Aşağıdaki kod örneğinde bir form bölgesi sınıf .NET Framework 3.5 hedefleyen bir projedeki gösterilmektedir.  
  
    ```vb  
    Public Sub New(ByVal formRegion As Microsoft.Office.Interop.Outlook.FormRegion)  
        MyBase.New(formRegion)  
        Me.InitializeComponent()  
    End Sub  
    ```  
  
    ```csharp  
    public FormRegion1(Microsoft.Office.Interop.Outlook.FormRegion formRegion)  
        : base(formRegion)  
    {  
        this.InitializeComponent();  
    }  
    ```  
  
     Aşağıdaki kod örneğinde bir form bölgesi sınıf bir projedeki hedefleyen gösterilmektedir [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)].  
  
    ```vb  
    Public Sub New(ByVal formRegion As Microsoft.Office.Interop.Outlook.FormRegion)  
        MyBase.New(Globals.Factory, formRegion)  
        Me.InitializeComponent()  
    End Sub  
    ```  
  
    ```csharp  
    public FormRegion1(Microsoft.Office.Interop.Outlook.FormRegion formRegion)  
        : base(Globals.Factory, formRegion)  
    {  
        this.InitializeComponent();  
    }  
    ```  
  
4.  İmzasını değiştirmek `InitializeManifest` aşağıda gösterildiği gibi yöntemi. Yöntemi kodda değişiklik yapmayın emin olun; Bu kod tasarımcıda uyguladığınız form bölgesi ayarlarını temsil eder. Visual C# projelerinde adlı bölge genişletmeniz gerekir `Form Region Designer generated code` bu yöntemi görmek için.  
  
     Aşağıdaki kod örneğinde imzasını gösterir `InitializeManifest` .NET Framework 3.5 hedefleyen bir projede yöntemi.  
  
    ```vb  
    Private Shared Sub InitializeManifest(ByVal manifest As Microsoft.Office.Tools.Outlook.FormRegionManifest)  
  
        ' Do not change code in this method.  
    End Sub  
    ```  
  
    ```csharp  
    private static void InitializeManifest(Microsoft.Office.Tools.Outlook.FormRegionManifest manifest)  
    {  
        // Do not change code in this method.  
    }  
    ```  
  
     Aşağıdaki kod örneğinde imzasını gösterir `InitializeManifest` hedefleyen bir projede yönteminde [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)].  
  
    ```vb  
    Private Shared Sub InitializeManifest(ByVal manifest As Microsoft.Office.Tools.Outlook.FormRegionManifest,   
        ByVal factory As Microsoft.Office.Tools.Outlook.Factory)  
  
        ' Do not change code in this method.  
    End Sub  
    ```  
  
    ```csharp  
    private static void InitializeManifest(Microsoft.Office.Tools.Outlook.FormRegionManifest manifest,   
        Microsoft.Office.Tools.Outlook.Factory factory)  
    {  
        // Do not change code in this method.  
    }  
    ```  
  
5.  Yeni bir Outlook Form bölgesi öğesi projenize ekleyin. Yeni form bölgesi için arka plan kodu dosyasını açın, bulun *YourNewFormRegion* `Factory` ve `WindowFormRegionCollection` dosyasında, sınıf ve bu sınıfların panoya kopyalayın.  
  
6.  Projenize eklenen yeni form bölgesini silin.  
  
7.  Güncellendiyse projede çalışmak üzere güncellediğiniz form bölgesi arka plan kod dosyasına bulun *YourOriginalFormRegion* `Factory` ve `WindowFormRegionCollection` sınıfları ve bunları öğesinden kopyalanan kod ile değiştirin Yeni form bölgesi.  
  
8.  İçinde *YourNewFormRegion* `Factory` ve `WindowFormRegionCollection` sınıfları aramak için yapılan tüm başvuruları *YourNewFormRegion* sınıfı ve her referansını değiştirme  *YourOriginalFormRegion* yerine sınıfı. Örneğin, form bölgesi, güncelleştiriyorsanız adlı `SalesDataFormRegion` ve 5. adımda oluşturduğunuz yeni form bölgesi adlı `FormRegion1`, tüm başvuruları değiştirme `FormRegion1` için `SalesDataFormRegion`.  
  
#### <a name="to-update-the-generated-code-for-a-form-region-that-you-imported-from-outlook"></a>Outlook'tan alınan bir form bölgesi için oluşturulan kodu güncelleştirmek için  
  
1.  Form bölgesi arka plan kod dosyasına kod düzenleyicisinde açın. Bu dosya adlı *YourFormRegion*. Designer.cs veya *YourFormRegion*. Designer.vb olarak adlandırılır. Visual Basic projeleri bu dosyada görmek için tıklatın **tüm dosyaları göster** düğmesini **Çözüm Gezgini**.  
  
2.  Öğesinden türetilen böylece form bölgesi sınıfının bildirimini değiştirmek <xref:Microsoft.Office.Tools.Outlook.ImportedFormRegionBase> yerine `Microsoft.Office.Tools.Outlook.ImportedFormRegion`.  
  
3.  Form bölgesi sınıf aşağıdaki kodu örneklerde gösterildiği gibi değiştirin.  
  
     Aşağıdaki kod örneğinde bir form bölgesi sınıf .NET Framework 3.5 hedefleyen bir projedeki gösterilmektedir.  
  
    ```vb  
    Public Sub New(ByVal formRegion As Microsoft.Office.Interop.Outlook.FormRegion)  
        MyBase.New(formRegion)  
    End Sub  
    ```  
  
    ```csharp  
    public ImportedFormRegion1(Microsoft.Office.Interop.Outlook.FormRegion formRegion)  
        : base(formRegion)  
    {  
        this.FormRegionShowing += new System.EventHandler(this.TaskFormRegion_FormRegionShowing);  
        this.FormRegionClosed += new System.EventHandler(this.TaskFormRegion_FormRegionClosed);  
    }  
    ```  
  
     Aşağıdaki kod örneğinde bir form bölgesi sınıf imzası projede hedefleyen gösterilmektedir [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)].  
  
    ```vb  
    Public Sub New(ByVal formRegion As Microsoft.Office.Interop.Outlook.FormRegion)  
        MyBase.New(Globals.Factory, formRegion)  
    End Sub  
    ```  
  
    ```csharp  
    public ImportedFormRegion1(Microsoft.Office.Interop.Outlook.FormRegion formRegion)  
        : base(Globals.Factory, formRegion)  
    {  
        this.FormRegionShowing += new System.EventHandler(this.TaskFormRegion_FormRegionShowing);  
        this.FormRegionClosed += new System.EventHandler(this.TaskFormRegion_FormRegionClosed);  
    }  
    ```  
  
4.  Her kod satırı için `InitializeControls` form bölgesi sınıfında bir denetim başlatan yöntem aşağıda gösterildiği gibi kodu değiştirin.  
  
     Aşağıdaki kod örneğinde bir projede bir denetimin başlatmak .NET Framework 3.5 hedefleyen gösterilmiştir. Bu kodda, `GetFormRegionControl` yöntemi döndürülen denetimin türünü belirleyen bir tür parametresi vardır.  
  
    ```vb  
    Me.olkTextBox1 = Me.GetFormRegionControl(Of Microsoft.Office.Interop.Outlook.OlkTextBox)("OlkTextBox1")  
    ```  
  
    ```csharp  
    this.olkTextBox1 = this.GetFormRegionControl<Microsoft.Office.Interop.Outlook.OlkTextBox>("OlkTextBox1");  
    ```  
  
     Aşağıdaki kod örneğinde bir projede bir denetimin başlatma hedefleyen gösterilmektedir [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]. Bu kodda, <xref:Microsoft.Office.Tools.Outlook.ImportedFormRegionBase.GetFormRegionControl%2A> yöntemi bir tür parametresi yok. Başlatma Denetim türü için dönüş değerini dönüştürmeniz gerekir.  
  
    ```vb  
    Me.olkTextBox1 = CType(GetFormRegionControl("OlkTextBox1"), Microsoft.Office.Interop.Outlook.OlkTextBox)  
    ```  
  
    ```csharp  
    this.olkTextBox1 = (Microsoft.Office.Interop.Outlook.OlkTextBox)GetFormRegionControl("OlkTextBox1");  
    ```  
  
5.  Yeni bir Outlook Form bölgesi öğesi projenize ekleyin. Yeni form bölgesi için arka plan kodu dosyasını açın, bulun *YourNewFormRegion* `Factory` ve `WindowFormRegionCollection` dosyasında, sınıf ve bu sınıfların panoya kopyalayın.  
  
6.  Projenize eklenen yeni form bölgesini silin.  
  
7.  Güncellendiyse projede çalışmak üzere güncellediğiniz form bölgesi arka plan kod dosyasına bulun *YourOriginalFormRegion* `Factory` ve `WindowFormRegionCollection` sınıfları ve bunları öğesinden kopyalanan kod ile değiştirin Yeni form bölgesi.  
  
8.  İçinde *YourNewFormRegion* `Factory` ve `WindowFormRegionCollection` sınıfları aramak için yapılan tüm başvuruları *YourNewFormRegion* sınıfı ve her referansını değiştirme  *YourOriginalFormRegion* yerine sınıfı. Örneğin, form bölgesi, güncelleştiriyorsanız adlı `SalesDataFormRegion` ve 5. adımda oluşturduğunuz yeni form bölgesi adlı `FormRegion1`, tüm başvuruları değiştirme `FormRegion1` için `SalesDataFormRegion`.  
  
## <a name="instantiate-form-region-classes"></a>Form bölgesi sınıflarını örneği  
 Dinamik olarak bazı form bölgesi sınıflarını başlatır herhangi bir kodu değiştirmeniz gerekir. .NET Framework 3.5 hedefleyen projelerde, form bölgesi sınıflarını gibi bir örneğini oluşturabilirsiniz `Microsoft.Office.Tools.Outlook.FormRegionManifest` doğrudan. ' İ hedefleyen projelerde [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ya da daha sonra bu sınıfların arabirimleri doğrudan örneği oluşturulamıyor.  
  
 Projenizin hedef çerçevesini değiştirilirse [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] veya tarafından sağlanan yöntemleri kullanarak arabirimler daha sonra oluşturmalıdır `Globals.Factory` özelliği. Hakkında daha fazla bilgi için `Globals.Factory` özelliği, bkz: [Office projelerindeki nesnelere genel erişim](../vsto/global-access-to-objects-in-office-projects.md).  
  
 Form bölgesi türleri aşağıdaki tabloda listelenmekte ve türler örneği oluşturmak için kullanılacak yöntemi hedefleyen projeler [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] veya sonraki bir sürümü.  
  
|Tür|Kullanmak için Üreteç yöntemi|  
|----------|---------------------------|  
|<xref:Microsoft.Office.Tools.Outlook.FormRegionCustomAction>|<xref:Microsoft.Office.Tools.Outlook.Factory.CreateFormRegionCustomAction%2A>|  
|<xref:Microsoft.Office.Tools.Outlook.FormRegionInitializingEventArgs>|<xref:Microsoft.Office.Tools.Outlook.Factory.CreateFormRegionInitializingEventArgs%2A>|  
|<xref:Microsoft.Office.Tools.Outlook.FormRegionManifest>|<xref:Microsoft.Office.Tools.Outlook.Factory.CreateFormRegionManifest%2A>|  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Office çözümlerini .NET Framework 4 veya sonraki bir sürümüne geçirme](../vsto/migrating-office-solutions-to-the-dotnet-framework-4-or-later.md)   
 [Outlook form bölgeleri oluşturma](../vsto/creating-outlook-form-regions.md)  
  