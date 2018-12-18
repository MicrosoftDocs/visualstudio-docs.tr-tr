---
title: .NET Framework 4 veya .NET Framework 4.5 için geçirdiğiniz Office projelerindeki Şerit Özelleştirmelerini Güncelleştirme
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
ms.openlocfilehash: 4cfd5fb259db7903541e0a86f16c720c9ff9c4d2
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49937427"
---
# <a name="update-ribbon-customizations-in-office-projects-that-you-migrate-to-the-net-framework-4-or-the-net-framework-45"></a>.NET Framework 4 veya .NET Framework 4.5 için geçirdiğiniz Office projelerindeki Şerit Özelleştirmelerini Güncelleştirme
  Projenizi kullanılarak oluşturulmuş bir Şerit özelleştirme içerip içermediğini **Şerit (Görsel Tasarımcı)** proje öğesi, hedef Framework'ü değiştirilirse proje kodunuzu aşağıdaki değişiklikleri yapmalısınız [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] veya Daha sonra.  
  
-   Oluşturulan Şerit kod değiştirin.  
  
-   Şerit denetimlerini çalışma zamanında başlatır, Şerit olaylarını işleme veya program aracılığıyla bir Şerit bileşeninin konumunu ayarlar herhangi bir kodu değiştirin.  
  
## <a name="update-the-generated-ribbon-code"></a>Oluşturulan Şerit kodunu güncelleştirme  
 Hedef Çerçeve proje değiştirilirse [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] veya daha sonra aşağıdaki adımları uygulayarak Şerit öğesi için oluşturulan kodu değiştirmeniz gerekir. Kod dosyaları güncelleştirmeye gerek duyduğunuz programlama diline ve proje nasıl oluşturduğunuz bağlıdır:  
  
-   Visual Basic projeleri veya ya da oluşturduğunuz Visual C# projelerinde [!INCLUDE[vs_dev11_long](../sharepoint/includes/vs-dev11-long-md.md)] veya [!INCLUDE[vs_dev10_long](../sharepoint/includes/vs-dev10-long-md.md)] Şerit arka plan kod dosyasında tüm adımları gerçekleştirin (*ŞeritÖğeniz*. Designer.cs veya *ŞeritÖğeniz*. Designer.vb olarak adlandırılır). Visual Basic projeleri arka plan kod dosyasında görmek için tıklayın **tüm dosyaları göster** düğmesine **Çözüm Gezgini**.  
  
-   Visual Studio 2008'de oluşturduğunuz ve ardından yükseltme Visual C# projelerinde [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)], Şerit kod dosyasını ilk iki adımı gerçekleştirin (*ŞeritÖğeniz*.cs veya *ŞeritÖğeniz*.vb), ve Şerit arka plan kod dosyasında kalan adımları gerçekleştirin.  
  
### <a name="to-change-the-generated-ribbon-code"></a>Oluşturulan Şerit kod değiştirmek için  
  
1.  Öğesinden türetilen Şerit sınıf bildirimini değiştirin <xref:Microsoft.Office.Tools.Ribbon.RibbonBase> yerine `Microsoft.Office.Tools.Ribbon.OfficeRibbon`.  
  
2.  Şerit sınıfının oluşturucusu, aşağıda gösterildiği gibi değiştirin. Oluşturucuya herhangi birini kendi kod eklediyseniz, kodunuzu değiştirmeyin. Visual Basic projelerinde yalnızca parametresiz oluşturucu değiştirin. Diğer Oluşturucu yoksayın.  
  
     Aşağıdaki kod örneği bir Şerit sınıf varsayılan oluşturucusuna bir projedeki hedefleyen .NET Framework 3.5 gösterilmektedir.  
  
    ```vb  
    Public Sub New()  
        MyBase.New()  
        InitializeComponent()  
    End Sub  
    ```  
  
    ```csharp  
    public Ribbon1()  
    {  
        InitializeComponent();  
    }  
    ```  
  
     Aşağıdaki kod örneği bir Şerit sınıf varsayılan oluşturucusuna hedefleyen bir projeye gösterilmektedir [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] veya üzeri.  
  
    ```vb  
    Public Sub New()  
        MyBase.New(Globals.Factory.GetRibbonFactory())  
        InitializeComponent()  
    End Sub  
    ```  
  
    ```csharp  
    public Ribbon1()  
        : base(Globals.Factory.GetRibbonFactory())  
    {  
        InitializeComponent();  
    }  
    ```  
  
3.  İçinde `InitializeComponent` yöntemi, Şerit denetimi oluşturur ve böylece kod yerine yardımcı yöntemlerinden birini kullanan herhangi bir kod değiştirme <xref:Microsoft.Office.Tools.Ribbon.RibbonFactory> nesne.  
  
    > [!NOTE]  
    >  Visual C# projelerinde, adlı bölgeyi Genişlet gerekir `Component Designer generated code` görmek için `InitializeComponent` yöntemi.  
  
     Örneğin, dosyanızın örneğini oluşturan kod aşağıdaki satırı içerdiğini varsayın. bir <xref:Microsoft.Office.Tools.Ribbon.RibbonButton> adlı `button1` içinde .NET Framework 3. 5'i hedefleyen bir proje.  
  
    ```vb  
    Me.button1 = New Microsoft.Office.Tools.Ribbon.RibbonButton()  
    ```  
  
    ```csharp  
    this.button1 = new Microsoft.Office.Tools.Ribbon.RibbonButton();  
    ```  
  
     Hedefleyen bir proje içinde [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] veya daha sonra aşağıdaki kodu yerine kullanmanız gerekir.  
  
    ```vb  
    Me.button1 = Me.Factory.CreateRibbonButton()  
    ```  
  
    ```csharp  
    this.button1 = this.Factory.CreateRibbonButton();  
    ```  
  
     Şerit denetimleri için yardımcı yöntemler tam bir listesi için bkz. [örneği Şerit denetimlerini](#ribboncontrols).  
  
4.  Visual C# projelerinde, kod satırıyla değiştirin `InitializeComponent` kullanan yöntemi bir <xref:System.EventHandler%601> belirli bir Şerit temsilcisi kullanmanız için temsilci.  
  
     Örneğin, dosyanızın işleyen kod aşağıdaki satırı içerdiğini varsayın <xref:Microsoft.Office.Tools.Ribbon.RibbonButton.Click> olay .NET Framework 3. 5'i hedefleyen bir proje.  
  
    <CodeContentPlaceHolder>8</CodeContentPlaceHolder>  
     Hedefleyen bir proje içinde [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] veya daha sonra aşağıdaki kodu yerine kullanmanız gerekir.  
  
    <CodeContentPlaceHolder>9</CodeContentPlaceHolder>  
     Şerit temsilcileri tam bir listesi için bkz. [işlemek Şerit olaylarını](#ribbonevents).  
  
5.  Visual Basic projelerinde bulun `ThisRibbonCollection` dosyanın sonunda sınıfı. Bu sınıf bildirimi artık öğesinden devralacak şekilde değiştirin `Microsoft.Office.Tools.Ribbon.RibbonReadOnlyCollection`.  
  
##  <a name="ribboncontrols"></a> Şerit denetimleri örneği  
 Şerit denetimlerini dinamik olarak başlatan herhangi bir kodu değiştirmeniz gerekir. Projelerinde hedefleyen .NET Framework 3.5, Şerit denetimlerini doğrudan belirli senaryolarda oluşturabileceğiniz sınıflardır. ' İ hedefleyen projelerde [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] veya daha sonra bu denetimlerin doğrudan oluşturamayacağınız arabirimdir. Tarafından sağlanan yöntemleri kullanarak denetimleri oluşturmalısınız <xref:Microsoft.Office.Tools.Ribbon.RibbonFactory> nesne.  
  
 Erişmenin iki yöntemi vardır <xref:Microsoft.Office.Tools.Ribbon.RibbonFactory> nesnesi:  
  
- Şerit sınıfının Fabrika özelliğini kullanarak. Bu yaklaşım koddan Şerit sınıfınızda kullanın.  
  
- Kullanarak `Globals.Factory.GetRibbonFactory` yöntemi. Şerit sınıfınıza dışındaki kod bu yaklaşımı kullanın. Globals sınıfı hakkında daha fazla bilgi için bkz: [Office projelerindeki nesnelere genel erişim](../vsto/global-access-to-objects-in-office-projects.md).  
  
  Aşağıdaki kod örneğinde nasıl oluşturulacağını gösterir. bir <xref:Microsoft.Office.Tools.Ribbon.RibbonButton> hedefleyen bir projeye bir Şerit sınıfında [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] veya üzeri.  
  
<CodeContentPlaceHolder>10</CodeContentPlaceHolder>  
<CodeContentPlaceHolder>11</CodeContentPlaceHolder>  
 Programlı olarak oluşturabilir denetimleri ve hedefleyen projelerde bu denetimleri oluşturmak için kullanılacak yöntemi aşağıdaki tabloda listelenmektedir [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] veya üzeri.  
  
|Denetim|Kullanılacak RibbonFactory yöntemi [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ve sonraki projeleri|  
|-------------| - |  
|<xref:Microsoft.Office.Tools.Ribbon.RibbonButton>|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonButton%2A>|  
|<xref:Microsoft.Office.Tools.Ribbon.RibbonButtonGroup>|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonButtonGroup%2A>|  
|<xref:Microsoft.Office.Tools.Ribbon.RibbonCheckBox>|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonCheckBox%2A>|  
|<xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox>|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonComboBox%2A>|  
|<xref:Microsoft.Office.Tools.Ribbon.RibbonDialogLauncher>|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonDialogLauncher%2A>|  
|<xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown>:|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonDropDown%2A>|  
|<xref:Microsoft.Office.Tools.Ribbon.RibbonDropDownItem>|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonDropDownItem%2A>|  
|<xref:Microsoft.Office.Tools.Ribbon.RibbonEditBox>|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonEditBox%2A>|  
|<xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonGallery%2A>|  
|<xref:Microsoft.Office.Tools.Ribbon.RibbonGroup>|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonGroup%2A>|  
|<xref:Microsoft.Office.Tools.Ribbon.RibbonLabel>|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonLabel%2A>|  
|<xref:Microsoft.Office.Tools.Ribbon.RibbonManager>|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonManager%2A>|  
|<xref:Microsoft.Office.Tools.Ribbon.RibbonMenu>|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonMenu%2A>|  
|<xref:Microsoft.Office.Tools.Ribbon.RibbonSeparator>|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonSeparator%2A>|  
|<xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton>|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonSplitButton%2A>|  
|<xref:Microsoft.Office.Tools.Ribbon.RibbonTab>|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonTab%2A>|  
|<xref:Microsoft.Office.Tools.Ribbon.RibbonToggleButton>|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonToggleButton%2A>|  
  
##  <a name="ribbonevents"></a> Şerit olaylarını işleme  
 Şerit denetim olaylarını işleme herhangi bir kodu değiştirmeniz gerekir. .NET Framework 3. 5'i hedefleyen projelerde bu olayları genel tarafından işlenen <xref:System.EventHandler%601> temsilci. ' İ hedefleyen projelerde [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] veya daha sonra bu olaylar diğer temsilcileri tarafından artık işlenir.  
  
 Aşağıdaki tablo Şerit olayları ve hedefleyen projelerde bunlarla ilişkili temsilcileri listeler [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] veya üzeri.  
  
|Olay|Kullanılacak temsilci [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ve sonraki projeleri|  
|-----------| - |  
|<xref:Microsoft.Office.Tools.Ribbon.OfficeRibbon.LoadImage> oluşturulan Şerit sınıfında olay|<xref:Microsoft.Office.Tools.Ribbon.RibbonLoadImageEventHandler>|  
|<xref:Microsoft.Office.Tools.Ribbon.OfficeRibbon.Load>|<xref:Microsoft.Office.Tools.Ribbon.RibbonUIEventHandler>|  
|<xref:Microsoft.Office.Tools.Ribbon.RibbonButton.Click><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonCheckBox.Click><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox.ItemsLoading><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox.TextChanged><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown.ButtonClick><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown.ItemsLoading><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown.SelectionChanged><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonEditBox.TextChanged><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery.ButtonClick><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery.Click><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery.ItemsLoading><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGroup.DialogLauncherClick><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu.ItemsLoading><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton.Click><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonToggleButton.Click>|<xref:Microsoft.Office.Tools.Ribbon.RibbonControlEventHandler>|  
  
## <a name="set-the-position-of-a-ribbon-component-programmatically"></a>Bir Şerit bileşeninin konumunu programlı olarak ayarlama  
 Şerit grupları, sekmeler veya denetimleri konumunu ayarlar herhangi bir kodu değiştirmeniz gerekir. .NET Framework 3. 5'i hedefleyen projelerde kullanabilirsiniz `AfterOfficeId` ve `BeforeOfficeId` statik yöntemleri `Microsoft.Office.Tools.Ribbon.RibbonPosition` atamak için sınıf `Position` grubu, sekme veya denetimi özellik. ' İ hedefleyen projelerde [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] veya daha sonra bu yöntemleri kullanarak erişmeniz gerekir <xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.RibbonPosition%2A> özelliği tarafından sağlanan <xref:Microsoft.Office.Tools.Ribbon.RibbonFactory> nesne.  
  
 Erişmenin iki yöntemi vardır <xref:Microsoft.Office.Tools.Ribbon.RibbonFactory> nesnesi:  
  
- Kullanarak `Factory` Şerit sınıfın özelliği. Bu yaklaşım koddan Şerit sınıfınızda kullanın.  
  
- Kullanarak `Globals.Factory.GetRibbonFactory` yöntemi. Şerit sınıfınıza dışındaki kod bu yaklaşımı kullanın. Globals sınıfı hakkında daha fazla bilgi için bkz: [Office projelerindeki nesnelere genel erişim](../vsto/global-access-to-objects-in-office-projects.md).  
  
  Aşağıdaki kod örneğinde nasıl ayarlanacağını gösterir `Position` .NET Framework 3. 5'i hedefleyen bir projeye bir Şerit sınıfında bir sekmede özelliği.  
  
```vb  
Me.tab1.Position = RibbonPosition.AfterOfficeId("TabHome")  
```  
  
```csharp  
this.tab1.Position = RibbonPosition.AfterOfficeId("TabHome");  
```  
  
 Aşağıdaki kod örneği hedefleyen bir proje içinde aynı görevi gösterir [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)].  
  
```vb  
Me.tab1.Position = Me.Factory.RibbonPosition.AfterOfficeId("TabHome")  
```  
  
```csharp  
this.tab1.Position = this.Factory.RibbonPosition.AfterOfficeId("TabHome");  
```  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Office çözümlerini .NET Framework 4 veya sonraki sürümlere geçirme](../vsto/migrating-office-solutions-to-the-dotnet-framework-4-or-later.md)   
 [Şerit Tasarımcısı](../vsto/ribbon-designer.md)  
  
  