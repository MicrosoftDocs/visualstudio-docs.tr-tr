---
title: Test Etme Amacıyla UWP Denetimleri için Benzersiz Otomasyon Özelliği Ayarlama
ms.date: 05/31/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: conceptual
ms.author: gewarren
manager: douge
ms.workload:
- uwp
author: gewarren
ms.openlocfilehash: 1cc8986c3101bb2048e0cd4ace739974031344ed
ms.sourcegitcommit: ae46be4a2b2b63da7e7049e9ed67cd80897c8102
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/05/2018
ms.locfileid: "52894787"
---
# <a name="set-a-unique-automation-property-for-uwp-controls-for-testing"></a>Test etmek için UWP denetimleri için benzersiz Otomasyon özelliği ayarlama

XAML tabanlı UWP uygulamanız için kodlanmış UI testlerini çalıştırmak istiyorsanız, her denetimin benzersiz Otomasyon özelliği tarafından tanımlanması gerekir. Benzersiz Otomasyon özelliği, uygulamanızdaki XAML denetimi türüne göre atayabilirsiniz.

[!INCLUDE [coded-ui-test-deprecation](includes/coded-ui-test-deprecation.md)]

## <a name="static-xaml-definition"></a>Statik XAML tanımı

XAML dosyanızda tanımlanan bir denetim için benzersiz Otomasyon özelliği belirtmek için ayarlayabileceğiniz **AutomationProperties.AutomationId** veya **AutomationProperties.Name** örtük veya açık olarak, Aşağıdaki örneklerde gösterildiği gibi. Bu değerlerden birini ayarlama denetimi, bir kodlanmış UI test veya eylem kaydını oluşturduğunuzda denetimi tanımlamak için kullanılan benzersiz Otomasyon özelliği sağlar.

### <a name="set-the-property-implicitly"></a>Örtük olarak ayarlamayın

Ayarlama **AutomationProperties.AutomationId** için **ButtonX** kullanarak **adı** XAML denetimi için bir özellik.

```xaml
<Button Name="ButtonX" Height="31" HorizontalAlignment="Left" Margin="23,26,0,0"  VerticalAlignment="Top" Width="140" Click="ButtonX_Click" />
```

Ayarlama **AutomationProperties.Name** için **ButtonY** kullanarak **içerik** XAML denetimi için bir özellik.

```xaml
<Button Content="ButtonY" Height="31" HorizontalAlignment="Left" Margin="23,76,0,0" VerticalAlignment="Top" Width="140" Click="ButtonY_Click" />
```

### <a name="set-the-property-explicitly"></a>Özelliğini açıkça ayarlayın

Ayarlama **AutomationProperties.AutomationId** için **ButtonX** açıkça denetimi için XAML içinde.

```xaml
<Button AutomationProperties.AutomationId="ButtonX" Height="31" HorizontalAlignment="Left" Margin="23,26,0,0"  VerticalAlignment="Top" Width="140" Click="ButtonX_Click" />
```

Ayarlama **AutomationProperties.Name** için **ButtonY** açıkça denetimi için XAML içinde.

```xaml
<Button AutomationProperties.Name="ButtonY" Height="31" HorizontalAlignment="Left" Margin="23,76,0,0" VerticalAlignment="Top" Width="140" Click="ButtonY_Click" />
```

## <a name="assign-unique-names"></a>Benzersiz adları atama

Visual Studio için Blend'de düğmeler, liste kutuları, birleşik giriş kutuları ve denetimler için benzersiz değerler sağlayan, metin kutuları gibi etkileşimli öğeler için benzersiz bir ad atamak için bir seçenek seçebileceğiniz **AutomationProperties.Name**.

Varolan denetimler için benzersiz bir ad atamak için **Araçları** > **etkileşimli öğeleri Adlandır**.

![Visual Studio için blend'de etkileşimli öğeleri Adlandır](../test/media/cuit_windowsstoreproperty_blend_1.png)

Otomatik olarak eklediğiniz yeni denetimler için benzersiz adlar vermek istiyorsanız, **Araçları** > **seçenekleri** açmak için **seçenekleri** iletişim. Seçin **XAML Tasarımcısı** seçip **oluşumda etkileşimli öğeleri'otomatik olarak ad**. Seçin **Tamam** iletişim kutusunu kapatın.

## <a name="use-a-data-template"></a>Veri şablonu kullanın

Kullanarak basit bir şablon tanımlayabilirsiniz **ItemTemplate** değişkenleri için değerleri bir liste kutusunda bağlamak için:

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

Bir şablonla kullanabilirsiniz **ItemContainerStyle** değişkenler değerlerini bağlamak için:

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

Bu örneklerin her ikisi için ardından tanımlamalısınız **ToString()** yöntemi **Itemsource'u**aşağıdaki kod örneğinde gösterildiği gibi. Bu kod, xenapp'i **AutomationProperties.Name** değeri ayarlanır ve bağlama kullanarak her bir veri bağlantılı liste öğesi için benzersiz Otomasyon özelliği ayarlanamıyor çünkü benzersizdir. Ayar için benzersiz bir değer **Otomasyon Properties.Name** bu durumda yeterlidir.

> [!NOTE]
> Bu yaklaşımı kullanarak, liste öğesinin iç içeriği de çalışan sınıfı içindeki bir dizeye bağlama aracılığıyla ayarlanabilir. Örnekte gösterildiği gibi düğme denetimini her liste öğesi içinde çalışan kimliği olan bir benzersiz Otomasyon kimliği atanır

```csharp
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

## <a name="use-a-control-template"></a>Bir denetim şablonu kullanın

Kodda tanımlandığında belirli bir türün her örneğini benzersiz Otomasyon özelliği alır. böylece, bir denetim şablonu kullanabilirsiniz. Şablonu oluşturmak için **AutomationProperty** benzersiz bir kimlik denetimi örneğinde bağlar. Aşağıdaki XAML bir denetim şablonu ile bu bağlamayı oluşturmak için bir yaklaşım gösterilmektedir:

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

Bu denetim şablonu kullanarak bir düğme iki örneğini tanımladığınızda, Otomasyon kimliği şablonda, denetimler için benzersiz içerik dizesi aşağıdaki XAML içinde gösterilen şekilde ayarlanır:

```xaml
<Button Content="Button1" Style="{StaticResource MyButton}" Width="140"/>
<Button Content="Button2" Style="{StaticResource MyButton}" Width="140"/>
```

### <a name="dynamic-controls"></a>Dinamik denetimleri

Kodunuz aracılığıyla dinamik olarak oluşturulan ve statik veya XAML dosyalarındaki Şablonlar aracılığıyla oluşturulmamış denetimleri varsa ayarlamalısınız **içerik** veya **adı** denetimin özelliklerini. Bu eylem, dinamik her denetimin benzersiz Otomasyon özelliği olduğundan emin olur. Örneğin, bir liste öğesi seçtiğinizde, görüntülenmesi gereken bir onay kutusu varsa, burada gösterildiği gibi bu özellikleri ayarlayabilirsiniz:

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

## <a name="see-also"></a>Ayrıca bkz.

- [Kodlanmış UI testleriyle UWP uygulamalarını test etme](../test/test-uwp-app-with-coded-ui-test.md)
