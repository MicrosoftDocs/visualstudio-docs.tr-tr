---
title: Test etmek için Windows Store denetimleri için benzersiz Otomasyon özelliği ayarlama | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9bdd74ff-2534-4fc7-a5c3-a77bf7843037
caps.latest.revision: 12
ms.author: gewarren
manager: douge
ms.openlocfilehash: 25890adaf22d1855426813c35e69766bba02a1c8
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49833934"
---
# <a name="set-a-unique-automation-property-for-windows-store-controls-for-testing"></a>Test yapma amacıyla Windows Mağazası Denetimleri için Benzersiz Otomasyon Özelliği ayarlama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

XAML tabanlı Windows Store uygulamanız için kodlanmış UI testlerini çalıştırmak istiyorsanız, her denetimi tanımlayan benzersiz Otomasyon özelliği olmalıdır.  
  
 Benzersiz Otomasyon özelliği, uygulamanızdaki XAML denetimi türüne göre atayabilirsiniz. Aşağıdaki durumlarda bu benzersiz Otomasyon özelliği atama şöyledir:  
  
-   [Denetimlerin statik XAML tanımı](#UniquePropertyWindowsStoreControlsStaticXAML)  
  
-   [Visual Studio veya Blend için Visual Studio kullanarak benzersiz Otomasyon özelliklerini atayın](#UniquePropertyWindowsStoreControlsExpressionBlend)  
  
-   [Bir DataTemplate'ı kullanın](#UniquePropertyWindowsStoreControlsDataTemplate)  
  
-   [Bir denetim şablonu kullanın](#UniquePropertyWindowsStoreControlsControlTemplate)  
  
-   [Dinamik denetimleri](#UniquePropertyWindowsStoreControlsDynamicControls)  
  
## <a name="use-methods-to-assign-a-unique-automation-property"></a>Benzersiz Otomasyon özelliği atamak için yöntemleri kullanın.  
  
###  <a name="UniquePropertyWindowsStoreControlsStaticXAML"></a> Statik XAML tanımı  
 XAML dosyanızda tanımlanan bir denetim için benzersiz Otomasyon özelliği belirtmek için AutomationProperties.AutomationId veya AutomationProperties.Name örtük veya açık olarak, aşağıdaki örneklerde gösterildiği gibi ayarlayabilirsiniz. Bu değerlerden birini ayarlama denetimi, bir kodlanmış UI test veya eylem kaydını oluşturduğunuzda denetimi tanımlamak için kullanılan benzersiz Otomasyon özelliği sağlar.  
  
 **Örtük olarak ayarlamayın**  
  
 AutomationProperties.AutomationId kümesine **ButtonX** ad özelliği XAML denetimi için kullanma.  
  
```xaml  
<Button Name="ButtonX" Height="31" HorizontalAlignment="Left" Margin="23,26,0,0"  VerticalAlignment="Top" Width="140" Click="ButtonX_Click" />  
  
```  
  
 AutomationProperties.Name kümesine **ButtonY** içerik özelliği XAML denetimi için kullanma.  
  
```xaml  
<Button Content="ButtonY" Height="31" HorizontalAlignment="Left" Margin="23,76,0,0" VerticalAlignment="Top" Width="140" Click="ButtonY_Click" />  
  
```  
  
 **Özelliğini açıkça ayarlayın**  
  
 AutomationProperties.AutomationId kümesine **ButtonX** açıkça denetimi için XAML içinde.  
  
```xaml  
<Button AutomationProperties.AutomationId=“ButtonX” Height="31" HorizontalAlignment="Left" Margin="23,26,0,0"  VerticalAlignment="Top" Width="140" Click="ButtonX_Click" />  
  
```  
  
 AutomationProperties.Name kümesine **ButtonY** açıkça denetimi için XAML içinde.  
  
```  
<Button AutomationProperties.Name="ButtonY" Height="31" HorizontalAlignment="Left" Margin="23,76,0,0" VerticalAlignment="Top" Width="140" Click="ButtonY_Click" />  
```  
  
###  <a name="UniquePropertyWindowsStoreControlsExpressionBlend"></a> Visual Studio veya Blend için Visual Studio kullanarak benzersiz Otomasyon özelliklerini atayın  
 Visual Studio veya Visual Studio için Blend, düğmeler, liste kutuları, birleşik giriş kutuları ve metin kutuları gibi etkileşimli öğeleri benzersiz bir ad atamak için kullanabilirsiniz. Bu denetimin AutomationProperties.Name için benzersiz bir değer sağlar.  
  
 **Visual Studio:** üzerinde **Araçları** menüsünde **seçenekleri** seçip **metin düzenleyici**, ardından **XAML**ve son olarak **Çeşitli**.  
  
 Seçin **oluşumda etkileşimli öğeleri'otomatik olarak ad** seçip **Tamam**.  
  
 ![XAML çeşitli seçenekleri](../test/media/cuit-windowsstoreapp-b.png "CUIT_WindowsStoreApp_B")  
  
 **Visual Studio için Blend:** Visual Studio için Blend Bunu yapmak için aşağıdaki yöntemlerden birini kullanın.  
  
> [!NOTE]
>  Yalnızca statik olarak XAML kullanılarak oluşturulan denetimler için bu yöntemi kullanabilirsiniz.  
  
 **Varolan denetimler için benzersiz bir ad vermek için**  
  
 Üzerinde **Araçları** menüsünde seçin **etkileşimli öğeleri Adlandır**, burada gösterildiği gibi:  
  
 ![Etkileşimli öğeleri Adlandır Araçlar menüsünden](../test/media/cuit-windowsstoreproperty-blend-1.png "CUIT_WindowsStoreProperty_Blend_1")  
  
 **Otomatik olarak oluşturduğunuz denetimleri için benzersiz bir ad vermek için**  
  
 Üzerinde **Araçları** menüsünde **seçenekleri**ve ardından **proje**. Seçin **oluşumda etkileşimli öğeleri'otomatik olarak ad** seçip **Tamam**, burada gösterildiği gibi:  
  
 ![Etkileşimli öğeleri Adlandır kümesi projesine](../test/media/cuit-windowsstoreproeprty-blend-2.png "CUIT_WindowsStoreProeprty_Blend_2")  
  
###  <a name="UniquePropertyWindowsStoreControlsDataTemplate"></a> Veri şablonu kullanın  
 Değişkenleri aşağıdaki XAML kullanarak değerleri bir liste kutusunda bağlamak için ItemTemplate kullanarak basit bir şablon tanımlayabilirsiniz.  
  
```xaml  
  
<ListBox Name="listBox1" ItemsSource="{Binding Source={StaticResource employees}}">  
   <ListBox.ItemTemplate>  
      <DataTemplate>  
         <StackPanel Orientation="Horizontal">  
            <TextBlock Text="{Binding EmployeeName}" />  
            <TextBlock Text="{Binding EmployeeID}" />  
         </StackPanel>  
      </DataTemplate>  
   </ListBox.ItemTemplate>  
</ListBox>  
```  
  
 Ayrıca, değerleri değişkenlere aşağıdaki XAML kullanarak bağlamak için ItemContainerStyle ile bir şablon kullanabilirsiniz.  
  
```xaml  
  
      <ListBox Name="listBox1" ItemsSource="{Binding Source={StaticResource employees}}">  
            <ListBox.ItemContainerStyle>  
                <Style TargetType="ListBoxItem">  
                    <Setter Property="Template">  
                        <Setter.Value>  
                            <ControlTemplate TargetType="ListBoxItem">  
                                <Grid>  
                                    <Button Content="{Binding EmployeeName}" AutomationProperties.AutomationId="{Binding EmployeeID}"/>  
                                </Grid>  
                            </ControlTemplate>  
                        </Setter.Value>  
                    </Setter>  
                </Style>  
            </ListBox.ItemContainerStyle>           
        </ListBox>  
  
```  
  
 Bu örneklerin her ikisi için ardından Itemsource'u, ToString() yöntemine aşağıdaki kodu kullanarak gösterildiği geçersiz kılmanız gerekir. Bu kod AutomationProperties.Name değeri ayarlanır ve bağlama kullanarak her bir veri bağlı liste öğesi için benzersiz Otomasyon özelliği ayarlanamıyor benzersiz olduğundan emin olur. Otomasyon Properties.Name için benzersiz bir değere ayarlanması bu durumda yeterli olur.  
  
> [!NOTE]
>  Bu yaklaşımı kullanarak, liste öğesinin iç içeriği de çalışan sınıfı içindeki bir dizeye bağlama aracılığıyla ayarlanabilir. Örnekte gösterildiği gibi düğme denetimini her liste öğesi içinde çalışan kimliği olan bir benzersiz Otomasyon kimliği atanır  
  
```  
  
Employee[] employees = new Employee[]   
{  
   new Employee("john", "4384"),  
   new Employee("margaret", "7556"),  
   new Employee("richard", "8688"),  
   new Employee("george", "1293")  
};  
  
listBox1.ItemsSource = employees;  
  
public override string ToString()  
{  
    return EmployeeName + EmployeeID; // Unique Identification to be set as the AutomationProperties.Name  
}  
  
```  
  
###  <a name="UniquePropertyWindowsStoreControlsControlTemplate"></a> Bir denetim şablonu kullanın  
 Kodda tanımlandığında belirli bir türün her örneğini benzersiz Otomasyon özelliği alır. böylece, bir denetim şablonu kullanabilirsiniz. Benzersiz bir kimlik denetimi örneğinde AutomationProperty bağlar, böylece şablon oluşturmanız gerekir. Aşağıdaki XAML bir denetim şablonu ile bu bağlamayı oluşturmak için bir yaklaşım gösterilmektedir.  
  
```xaml  
  
<Style x:Key="MyButton" TargetType="Button">  
<Setter Property="Template">  
   <Setter.Value>  
<ControlTemplate TargetType="Button">  
   <Grid>  
      <CheckBox HorizontalAlignment="Left" AutomationProperties.AutomationId="{TemplateBinding Content}"></CheckBox>  
      <Button Width="90" HorizontalAlignment="Right" Content="{TemplateBinding Content}" AutomationProperties.AutomationId="{TemplateBinding Content}"></Button>  
   </Grid>  
</ControlTemplate>  
   </Setter.Value>  
</Setter>  
</Style>  
  
```  
  
 Bu denetim şablonu kullanarak bir düğme iki örneğini tanımladığınızda, Otomasyon kimliği şablonda, denetimler için benzersiz içerik dizesi aşağıdaki XAML içinde gösterilen şekilde ayarlanır.  
  
```xaml  
  
<Button Content=”Button1” Style="{StaticResource MyButton}" Width="140"/>  
<Button Content=”Button2” Style="{StaticResource MyButton}" Width="140"/>  
```  
  
###  <a name="UniquePropertyWindowsStoreControlsDynamicControls"></a> Dinamik denetimleri  
 Kodunuz aracılığıyla dinamik olarak oluşturulan ve statik veya XAML dosyalarındaki Şablonlar aracılığıyla oluşturulmamış denetimleri varsa, denetim için içerik veya adı özelliklerini ayarlamanız gerekir. Bu, dinamik her denetimin benzersiz Otomasyon özelliği olduğundan emin olur. Örneğin, bir liste öğesi seçtiğinizde, görüntülenmesi gereken bir onay kutusu varsa, burada gösterildiği gibi bu özellikleri ayarlayabilirsiniz:  
  
```csharp  
  
private void CreateCheckBox(string txt, StackPanel panel)  
   {  
      CheckBox cb = new CheckBox();  
      cb.Content = txt; // Sets the AutomationProperties.Name  
      cb.Height = 50;  
      cb.Width = 100;  
      cb.Name = "DynamicCheckBoxAid"+ txt; // Sets the AutomationProperties.AutomationId  
      panel.Children.Add(cb);  
    }  
  
```  




