---
title: 'İzlenecek yol: Benim ilk WPF Masaüstü Uygulama2 dizinlerini | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3c460fa9-2ea1-413f-ae54-54a1f2a499d1
caps.latest.revision: 8
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 7d8af02051774b744f9229e15a6184603c4d9f6b
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49899285"
---
# <a name="walkthrough-my-first-wpf-desktop-application"></a>İzlenecek yol: İlk WPF Masaüstü Uygulamam
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

name = "Giriş" ></a> bu kılavuzda Windows Presentation Foundation (WPF) geliştirme tanıtır. Çoğu WPF Masaüstü uygulamaları için ortak olan öğeler içeren temel bir uygulama oluşturacaksınız: XAML biçimlendirme, arka plan kod, uygulama tanımları, denetimler, düzen, veri bağlama ve stilleri.  
  
##  <a name="Create_The_Application_Code_Files"></a> Uygulama projesi oluşturma  
 Bu bölümde, proje ana penceresi veya form içeren uygulama altyapısı oluşturacaksınız.  
  
#### <a name="to-create-the-project"></a>Proje oluşturmak için  
  
1.  Menü çubuğunda, **dosya**, **yeni**, **proje**.  
  
2.  İçinde **yeni proje** iletişim kutusunda, ya da genişletin **Visual C#** veya **Visual Basic** düğüm ve **Windows** düğümünü ve ardından **Windows** düğümünü seçip **Klasik Masaüstü** düğümü.  
  
3.  Şablon listesinde **WPF uygulaması** şablonu.  
  
4.  İçinde **adı** metin kutusuna `ExpenseIt`ve ardından **Tamam** düğmesi.  
  
     Proje oluşturulur ve proje dosyaları eklenir **Çözüm Gezgini**ve adlı varsayılan uygulama penceresi için tasarımcı **MainWindow.xaml** görüntülenir.  
  
#### <a name="to-modify-the-main-window"></a>Ana pencereyi değiştirmek için  
  
1.  Tasarımcısı'nda **MainWindow.xaml** etkin Tasarımcı sekme yoksa sekme.  
  
2.  C# kullanıyorsanız satırını bulun `<Window x:Class="ExpenseIt.MainWindow"` değiştirin `<NavigationWindow x:Class="ExpenseIt.MainWindow"`.  
  
     Visual Basic kullanıyorsanız satırını bulun `<Window x:Class=" MainWindow"` değiştirin `<NavigationWindow x:Class="MainWindow"`.  
  
     Değiştirdiğinizde dikkat `<Window` etiketini `<NavigationWindow`, IntelliSense otomatik olarak kapanış etiketi için değişiklikleri `</NavigationWindow>` de.  
  
    > [!NOTE]
    >  Etiket, değiştirdikten sonra **hata listesi** penceresi açıksa, çeşitli hatalar da görebilirsiniz. Endişelenmeyin, bu Git hemen sonraki birkaç adımda yaptığınız değişiklikler yapar.  
  
3.  Seçin `<Grid>` ve `</Grid>` etiketleri ve silebilirsiniz.  
  
     A **NavigationWindow** gibi diğer kullanıcı Arabirimi öğeleri içeremez bir **kılavuz**.  
  
4.  İçinde **özellikleri** penceresinde genişletin **ortak** kategorisi düğümünü seçip **başlık** özelliği ve enter `ExpenseIt` tuşuna basın **Enter**  anahtarı.  
  
     Dikkat **başlık** XAML pencere öğesinde değişiklikler yeni değer ile eşleşmelidir. XAML penceresinde XAML özellikleri değiştirebilirsiniz veya **özellikleri** penceresi ve değişiklikleri eşitlenir.  
  
5.  XAML penceresinde değerini **yükseklik** öğesine `375`ve değerini ayarlama **genişliği** özelliğini `500`.  
  
     Bu öğeler karşılık **yükseklik** ve **genişliği** bulunan özellikler, **Düzen** kategorisinde **özellikleri** penceresi.  
  
     **MainWindow.xaml** dosyası artık şu şekilde görünmelidir C# ' de:  
  
    ```xaml  
    <NavigationWindow x:Class="ExpenseIt.MainWindow"  
            xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
            xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
            xmlns:d="http://schemas.microsoft.com/expression/blend/2008"  
            xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"  
            xmlns:local="clr-namespace:ExpenseIt"  
            mc:Ignorable="d"  
            Title="ExpenseIt" Height="375" Width="500">  
  
    </NavigationWindow>  
    ```  
  
     Veya Visual Basic'te şöyle:  
  
    ```xaml  
    <NavigationWindow x:Class="MainWindow"  
            xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
            xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
            xmlns:d="http://schemas.microsoft.com/expression/blend/2008"  
            xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"  
            xmlns:local="clr-namespace:ExpenseIt"  
            mc:Ignorable="d"  
            Title="ExpenseIt" Height="375" Width="500">  
  
    </NavigationWindow>  
    ```  
  
#### <a name="to-modify-the-code-behind-file-c"></a>Arka plan kod dosyasını (C#) değiştirmek için  
  
1.  İçinde **Çözüm Gezgini**, genişletme **MainWindow.xaml** düğüm ve açık **MainWindow.xaml.cs** dosya.  
  
2.  Satırı bulun `public partial class MainWindow : Window` değiştirin `public partial class MainWindow : NavigationWindow`.  
  
     Bu değişiklikleri `MainWindow` öğesinden türetilen sınıfın `NavigationWindow`. Visual Basic'te, kod değişikliği yapmadan gerekli olacak şekilde, XAML, pencerede değiştirdiğinizde, bu otomatik olarak gerçekleşir.  
  
##  <a name="add_files_to_the_application"></a> Dosyalar uygulamaya ekleme  
 Bu bölümde, uygulamaya iki sayfaları ve görüntü ekleyeceksiniz.  
  
#### <a name="to-add-a-home-screen"></a>Giriş ekranı ekleme  
  
1.  İçinde **Çözüm Gezgini**, kısayol menüsünü açın **ExpenseIt** düğüm ve **Ekle**, **sayfa**.  
  
2.  İçinde **Yeni Öğe Ekle** iletişim kutusunda seçin **adı** metin kutusu ve girin `ExpenseItHome`ve ardından **Ekle** düğmesi.  
  
     Uygulama başlatıldığında görüntülenen pencerenin ilk sayfadır.  
  
3.  Tasarımcısı'nda **ExpenseItHome.XAML** etkin Tasarımcı sekme yoksa sekme.  
  
4.  Seçin `<Title>` öğesi başlığı değiştirip **ExpenseIt – giriş**.  
  
     **ExpenseItHome.XAML** dosyası artık şu şekilde görünmelidir C# ' de:  
  
    ```xaml  
    <Page x:Class="ExpenseIt.ExpenseItHome"  
          xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
          xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
          xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"   
          xmlns:d="http://schemas.microsoft.com/expression/blend/2008"   
          xmlns:local="clr-namespace:ExpenseIt"  
          mc:Ignorable="d"   
          d:DesignHeight="300" d:DesignWidth="300"  
          Title="ExpenseIt - Home">  
  
        <Grid>  
  
        </Grid>  
    </Page>  
    ```  
  
     Veya Visual Basic'te şöyle:  
  
    ```xaml  
    <Page x:Class="ExpenseItHome"  
          xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
          xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
          xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"   
          xmlns:d="http://schemas.microsoft.com/expression/blend/2008"   
          xmlns:local="clr-namespace:ExpenseIt"  
          mc:Ignorable="d"   
          d:DesignHeight="300" d:DesignWidth="300"  
          Title="ExpenseIt - Home">  
        <Grid>  
  
        </Grid>  
    </Page>  
    ```  
  
5.  Tasarımcısı'nda **MainWindow.xaml** sekmesi.  
  
6.  Satırı bulun `Title="ExpenseIt" Height="375" Width="500">` öğesi ve bir `Source="ExpenseItHome.xaml"` özelliği.  
  
     Bu ayarlar **ExpenseItHome.XAML** ilk olarak uygulama başladığında açılır. **MainWindow.xaml** dosyası artık şu şekilde görünmelidir C# ' de:  
  
    ```xaml  
    <NavigationWindow x:Class="ExpenseIt.MainWindow"  
            xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
            xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
            xmlns:d="http://schemas.microsoft.com/expression/blend/2008"  
            xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"  
            xmlns:local="clr-namespace:ExpenseIt"  
            mc:Ignorable="d"  
            Title="ExpenseIt" Height="375" Width="500" Source="ExpenseItHome.xaml">  
  
    </NavigationWindow>  
    ```  
  
     Veya Visual Basic'te şöyle:  
  
    ```xaml  
    <NavigationWindow x:Class="MainWindow"  
            xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
            xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
            xmlns:d="http://schemas.microsoft.com/expression/blend/2008"  
            xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"  
            xmlns:local="clr-namespace:ExpenseIt"  
            mc:Ignorable="d"  
            Title="ExpenseIt" Height="375" Width="500" Source="ExpenseItHome.xaml">  
  
    </NavigationWindow>  
    ```  
  
     Daha önce ayarladığınız özellikleri ile ayarladığınız gibi `Source` özelliğinde **çeşitli** kategorisi **özellikleri** penceresi.  
  
#### <a name="to-add-a-details-window"></a>Bir Ayrıntılar penceresi eklemek için  
  
1.  İçinde **Çözüm Gezgini**, kısayol menüsünü açın **ExpenseIt** düğüm ve **Ekle**, **sayfa**.  
  
2.  İçinde **Yeni Öğe Ekle** iletişim kutusunda seçin **adı** metin kutusu ve girin `ExpenseReportPage`ve ardından **Ekle** düğmesi.  
  
     Bu pencereyi tek bir gider raporunu görüntüler.  
  
3.  Tasarımcısı'nda **ExpenseReportPage.xaml** etkin Tasarımcı sekme yoksa sekme.  
  
4.  Seçin `<Title>` öğesi başlığı değiştirip **ExpenseIt – görünümü gider**.  
  
     ExpenseReportPage.xaml dosyanızı gibi C# dilinde görünmesi gerekir:  
  
    ```xaml  
    <Page x:Class="ExpenseIt.ExpenseReportPage"  
          xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
          xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
          xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"   
          xmlns:d="http://schemas.microsoft.com/expression/blend/2008"   
          xmlns:local="clr-namespace:ExpenseIt"  
          mc:Ignorable="d"   
          d:DesignHeight="300" d:DesignWidth="300"  
          Title="ExpenseIt - View Expense">  
  
        <Grid>  
  
        </Grid>  
    </Page>  
    ```  
  
     Veya Visual Basic'te şöyle:  
  
    ```xaml  
    <Page x:Class="ExpenseReportPage"  
          xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
          xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
          xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"   
          xmlns:d="http://schemas.microsoft.com/expression/blend/2008"   
          xmlns:local="clr-namespace:ExpenseIt"  
          mc:Ignorable="d"   
          d:DesignHeight="300" d:DesignWidth="300"  
          Title="ExpenseIt - View Expense">  
        <Grid>  
  
        </Grid>  
    </Page>  
    ```  
  
5.  Menü çubuğunda, **hata ayıklama**, **hata ayıklamayı Başlat** (veya F5 tuşuna basın) uygulamayı çalıştırın.  
  
     Uygulama penceresi gezinti düğmeleri ile aşağıda gösterilmiştir.  
  
     ![ExpenseIt örnek ekran görüntüsünde](../designers/media/gettingstartedfigure1.png "GettingStartedFigure1")  
  
6.  Tasarım moduna dönmek için uygulamayı kapatın.  
  
##  <a name="Add_Layout"></a> Kullanıcı arabirimi oluşturma  
 Düzen öğeleri yerleştirmek için sıralı bir yol sağlar ve bir formu yeniden boyutlandırıldığında boyutunu ve konumunu söz konusu öğelerin da yönetir. Bu bölümde, üç satır tek sütunlu kılavuz oluşturacaksınız. Denetimler için iki sayfa ekleme, bazı kodlar ekleyin ve son denetimler için yeniden kullanılabilir stiller tanımlayın.  
  
#### <a name="to-create-the-layout"></a>Bir düzen oluşturmak için  
  
1.  Açık **ExpenseItHome.XAML** ve `<Grid>` öğesi.  
  
2.  İçinde **özellikleri** penceresini genişletin **Düzen** kategorisi düğümünü ve kümesi **kenar boşluğu** değerler `10`, `10`, `0`ve `10`, sol, sağ, üst ve alt kenar boşlukları karşılık gelir.  
  
     Öğe `Margin="10,0,10,10"` eklenir `<Grid>` XAML öğesinde. Bir kez daha, bu değerleri yerine, XAML kod içinde doğrudan girebiliriz **özellikleri** aynı sonucu penceresi.  
  
3.  Aşağıdaki XAML kodu `Grid` öğesi satır ve sütun tanımları oluşturmak için:  
  
    ```xaml  
    <Grid.ColumnDefinitions>  
        <ColumnDefinition />  
    </Grid.ColumnDefinitions>  
    <Grid.RowDefinitions>  
        <RowDefinition Height="Auto"/>  
        <RowDefinition />  
        <RowDefinition Height="Auto"/>  
    </Grid.RowDefinitions>  
    ```  
  
#### <a name="to-add-controls"></a>Denetimler ekleme  
  
1.  Açık **ExpenseItHome.XAML**.  
  
2.  Aşağıdaki XAML kodu ekleyin hemen üzerinde `</Grid>` oluşturmak için etiket `Border`, `ListBox` ve `Button` kontrol eder.  
  
    ```xaml  
    <!-- People list -->  
      <Border Grid.Column="0" Grid.Row="0" Height="35" Padding="5" Background="#4E87D4">  
          <Label VerticalAlignment="Center" Foreground="White">Names</Label>  
      </Border>  
      <ListBox Name="peopleListBox" Grid.Column="0" Grid.Row="1">  
          <ListBoxItem>Mike</ListBoxItem>  
          <ListBoxItem>Lisa</ListBoxItem>  
          <ListBoxItem>John</ListBoxItem>  
          <ListBoxItem>Mary</ListBoxItem>  
      </ListBox>  
  
      <!-- View report button -->  
      <Button Grid.Column="0" Grid.Row="2" Margin="0,10,0,0" Width="125"  
    Height="25" HorizontalAlignment="Right">View</Button>  
  
    ```  
  
     Denetimleri tasarım penceresinde görüntülendiğine dikkat edin. Sizin de denetimlere sürükleyerek oluşturmuş olabileceğiniz **araç kutusu** tasarım penceresini ve özelliklerini ayarlayarak penceresinden **özellikleri** penceresi.  
  
3.  Derleme ve uygulamayı çalıştırın. Aşağıdaki çizimde, bu yordamdaki XAML oluşturan denetimlerin çalışma zamanı görünümünü gösterir.  
  
     ![ExpenseIt örnek ekran görüntüsünde](../designers/media/gettingstartedfigure2.png "GettingStartedFigure2")  
  
4.  Tasarım moduna dönmek için uygulamayı kapatın.  
  
#### <a name="to-add-a-background-image"></a>Arka plan görüntüsü eklemek için  
  
1.  Aşağıdaki görüntü ve kaydedileceği seçin `watermark.png`.  
  
     ![Filigran resmi için izlenecek yol](../designers/media/wpf-watermark.png "WPF_watermark")  
  
    > [!NOTE]
    >  Alternatif olarak kendi görüntünüzü oluşturabilir ve kaydedileceği `watermark.png`.  
  
2.  İçinde **Çözüm Gezgini**, kısayol menüsünü açın **ExpenseIt** düğüm ve **Ekle**, **var olan öğe**.  
  
3.  İçinde **varolan öğeyi Ekle** iletişim kutusunda, bulmak **watermark.png** eklediğiniz, onu seçin ve ardından görüntüyü **Ekle** düğmesi.  
  
    > [!NOTE]
    >  Genişletmeniz gerekebilir **dosya türleri** listesindeki **görüntü dosyaları**.  
  
4.  Açık **ExpenseItHome.XAML** dosyasını açıp aşağıdaki XAML kodu ekleyin hemen üzerinde `</Grid>` etiketi arka plan görüntüsü oluşturmak için:  
  
    ```xaml  
    <Grid.Background>  
        <ImageBrush ImageSource="watermark.png"/>  
    </Grid.Background>  
  
    ```  
  
#### <a name="to-add-a-title"></a>Başlık eklemek için  
  
1.  Açık **ExpenseItHome.XAML**.  
  
2.  Satırı bulun `<Grid.ColumnDefinitions>` ve aşağıdaki yeni altına ekleyin:  
  
    ```xaml  
    <ColumnDefinition Width="230" />  
  
    ```  
  
     Bu, sabit bir 230 piksel genişlik ile diğer sütunları solundaki ek bir sütun oluşturur.  
  
3.  Satırı bulun `<Grid.RowDefinitions>` ve aşağıdaki yeni altına ekleyin:  
  
    ```xaml  
    <RowDefinition />  
  
    ```  
  
     Bu kılavuz en üste bir satır ekler.  
  
4.  Denetimleri ayarlayarak ikinci sütuna Taşı `Grid.Column` değerini 1. Her denetim, her artırarak bir satır aşağı taşı `Grid.Row` değeri 1.  
  
    1.  Satırı bulun `<Border Grid.Column="0" Grid.Row="0" Height="35" Padding="5" Background="#4E87D4">`. Değiştirme `Grid.Column="0"` için `Grid.Column="1"` değiştirip `Grid.Row="0"` için `Grid.Row="1"`.  
  
    2.  Satırı bulun `<ListBox Name="peopleListBox" Grid.Column="0" Grid.Row="1"`. Değiştirme `Grid.Column="0"` için `Grid.Column="1"` değiştirip `Grid.Row="1"` için `Grid.Row="2"`.  
  
    3.  Satırı bulun `<Button Grid.Column="0" Grid.Row="2" Margin="0,10,0,0" Width="125"`. Değiştirme `Grid.Column="0"` için `Grid.Column="1"` değiştirip `Grid.Row="2"` için `Grid.Row="3"`.  
  
5.  Hemen önce `<Border` öğesi başlığı görüntülemek için aşağıdaki XAML kodu ekleyin:  
  
    ```xaml  
    <Label Grid.Column="1" VerticalAlignment="Center" FontFamily="Trebuchet MS"   
            FontWeight="Bold" FontSize="18" Foreground="#0066cc">  
        View Expense Report  
    </Label>  
  
    ```  
  
     İçeriğini **ExpenseItHome.XAML** gibi C# dilinde görünmesi gerekir:  
  
    ```xaml  
    <Page x:Class="ExpenseIt.ExpenseItHome"  
          xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
          xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
          xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"   
          xmlns:d="http://schemas.microsoft.com/expression/blend/2008"   
          xmlns:local="clr-namespace:ExpenseIt"  
          mc:Ignorable="d"   
          d:DesignHeight="300" d:DesignWidth="300"  
          Title="ExpenseIt - Home">  
        <Grid Margin="10,0,10,10">  
            <Grid.ColumnDefinitions>  
                <ColumnDefinition Width="230" />  
                <ColumnDefinition />  
            </Grid.ColumnDefinitions>  
            <Grid.RowDefinitions>  
                <RowDefinition />  
                <RowDefinition Height="Auto"/>  
                <RowDefinition />  
                <RowDefinition Height="Auto"/>  
            </Grid.RowDefinitions>  
            <Border Grid.Column="1" Grid.Row="1" Height="35" Padding="5" Background="#4E87D4">  
                <Label VerticalAlignment="Center" Foreground="White">Names</Label>  
            </Border>  
            <!-- People list -->  
            <Label Grid.Column="1" VerticalAlignment="Center" FontFamily="Trebuchet MS"   
            FontWeight="Bold" FontSize="18" Foreground="#0066cc">  
                View Expense Report  
            </Label>  
            <ListBox Name="peopleListBox" Grid.Column="1" Grid.Row="2">  
                <ListBoxItem>Mike</ListBoxItem>  
                <ListBoxItem>Lisa</ListBoxItem>  
                <ListBoxItem>John</ListBoxItem>  
                <ListBoxItem>Mary</ListBoxItem>  
            </ListBox>  
  
            <!-- View report button -->  
            <Button Grid.Column="1" Grid.Row="3" Margin="0,10,0,0" Width="125"  
    Height="25" HorizontalAlignment="Right">View</Button>  
            <Grid.Background>  
                <ImageBrush ImageSource="watermark.png"/>  
            </Grid.Background>  
        </Grid>  
    </Page>  
    ```  
  
     Veya Visual Basic'te şöyle:  
  
    ```xaml  
    <Page x:Class="ExpenseItHome"  
          xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
          xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
          xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"   
          xmlns:d="http://schemas.microsoft.com/expression/blend/2008"   
          xmlns:local="clr-namespace:ExpenseIt"  
          mc:Ignorable="d"   
          d:DesignHeight="300" d:DesignWidth="300"  
          Title="ExpenseIt - Home" >  
        <Grid Margin="10,0,10,10">  
            <Grid.ColumnDefinitions>  
                <ColumnDefinition Width="230" />  
                <ColumnDefinition />  
            </Grid.ColumnDefinitions>  
            <Grid.RowDefinitions>  
                <RowDefinition />  
                <RowDefinition Height="Auto"/>  
                <RowDefinition />  
                <RowDefinition Height="Auto"/>  
            </Grid.RowDefinitions>  
            <Border Grid.Column="1" Grid.Row="1" Height="35" Padding="5" Background="#4E87D4">  
                <Label VerticalAlignment="Center" Foreground="White">Names</Label>  
            </Border>  
            <!-- People list -->  
            <Label Grid.Column="1" VerticalAlignment="Center" FontFamily="Trebuchet MS"   
            FontWeight="Bold" FontSize="18" Foreground="#0066cc">  
                View Expense Report  
            </Label>  
            <ListBox Name="peopleListBox" Grid.Column="1" Grid.Row="2">  
                <ListBoxItem>Mike</ListBoxItem>  
                <ListBoxItem>Lisa</ListBoxItem>  
                <ListBoxItem>John</ListBoxItem>  
                <ListBoxItem>Mary</ListBoxItem>  
            </ListBox>  
  
            <!-- View report button -->  
            <Button Grid.Column="1" Grid.Row="3" Margin="0,10,0,0" Width="125"  
    Height="25" HorizontalAlignment="Right">View</Button>  
            <Grid.Background>  
                <ImageBrush ImageSource="watermark.png"/>  
            </Grid.Background>  
        </Grid>  
    </Page>  
    ```  
  
6.  Derleme ve bu noktada uygulamayı çalıştırın, bunu aşağıdaki gibi görünmelidir:  
  
     ![ExpenseIt örnek ekran görüntüsünde](../designers/media/gettingstartedfigure3.png "GettingStartedFigure3")  
  
#### <a name="to-add-code-to-the-button"></a>Kod, düğme eklemek için  
  
1.  Açık **ExpenseItHome.XAML**.  
  
2.  Seçtiğiniz `<Button` öğesi ve aşağıdaki XAML kodu ekleyin hemen sonra **HorizontalAlignment = "Sağ"** öğesi: `Click="Button_Click"`.  
  
     Bu düğme için bir olay işleyicisi ekler `Click` olay. **< Düğmesi** öğe kodu artık şu şekilde görünmelidir:  
  
    ```  
    <!-- View report button -->  
      <Button Grid.Column="1" Grid.Row="3" Margin="0,10,0,0" Width="125"  
    Height="25" HorizontalAlignment="Right" Click="Button_Click">View</Button>  
    ```  
  
3.  Açık **ExpenseItHome.xaml.cs** veya **ExpenseItHome.xaml.vb** dosya.  
  
4.  Aşağıdaki kodu ekleyin `ExpenseItHome` sınıfı:  
  
    ```csharp  
    private void Button_Click(object sender, RoutedEventArgs e)  
    {  
        // View Expense Report  
        ExpenseReportPage expenseReportPage = new ExpenseReportPage();  
        this.NavigationService.Navigate(expenseReportPage);  
  
    }  
    ```  
  
    ```vb  
    Private Sub Button_Click(ByVal sender As Object, ByVal e As RoutedEventArgs)  
        ' View Expense Report  
        Dim expenseReportPage As New ExpenseReportPage()  
    Me.NavigationService.Navigate(expenseReportPage)  
    End Sub  
    ```  
  
     Düğme tıklandığında bu olay işleyicisi harcama raporu sayfası açılır.  
  
#### <a name="to-create-the-ui-for-the-report-page"></a>Rapor sayfası için kullanıcı Arabirimi oluşturmak için  
  
1.  Açık **ExpenseReportPage.xaml**.  
  
     Bu sayfa giriş sayfasında seçilen kişi için harcama raporlarını görüntüler.  
  
2.  Aşağıdaki XAML kodu arasında ekleyin `<Grid>` ve `</Grid>` etiketler:  
  
    ```xaml  
    <Grid.Background>  
        <ImageBrush ImageSource="watermark.png" />  
    </Grid.Background>  
    <Grid.ColumnDefinitions>  
        <ColumnDefinition Width="230" />  
        <ColumnDefinition />  
    </Grid.ColumnDefinitions>  
    <Grid.RowDefinitions>  
        <RowDefinition Height="Auto" />  
        <RowDefinition />  
    </Grid.RowDefinitions>  
  
    <Label Grid.Column="1" VerticalAlignment="Center" FontFamily="Trebuchet MS"   
    FontWeight="Bold" FontSize="18" Foreground="#0066cc">  
        Expense Report For:  
    </Label>  
    <Grid Margin="10" Grid.Column="1" Grid.Row="1">  
  
        <Grid.ColumnDefinitions>  
            <ColumnDefinition />  
            <ColumnDefinition />  
        </Grid.ColumnDefinitions>  
        <Grid.RowDefinitions>  
            <RowDefinition Height="Auto" />  
            <RowDefinition Height="Auto" />  
            <RowDefinition />  
        </Grid.RowDefinitions>  
  
        <!-- Name -->  
        <StackPanel Grid.Column="0" Grid.ColumnSpan="2" Grid.Row="0" Orientation="Horizontal">  
            <Label Margin="0,0,0,5" FontWeight="Bold">Name:</Label>  
            <Label Margin="0,0,0,5" FontWeight="Bold"></Label>  
        </StackPanel>  
  
        <!-- Department -->  
        <StackPanel Grid.Column="0" Grid.ColumnSpan="2" Grid.Row="1" Orientation="Horizontal">  
            <Label Margin="0,0,0,5" FontWeight="Bold">Department:</Label>  
            <Label Margin="0,0,0,5" FontWeight="Bold"></Label>  
        </StackPanel>  
  
        <Grid Grid.Column="0" Grid.ColumnSpan="2" Grid.Row="2" VerticalAlignment="Top"   
              HorizontalAlignment="Left">  
            <!-- Expense type and Amount table -->  
            <DataGrid  AutoGenerateColumns="False" RowHeaderWidth="0" >  
                <DataGrid.ColumnHeaderStyle>  
                    <Style TargetType="{x:Type DataGridColumnHeader}">  
                        <Setter Property="Height" Value="35" />  
                        <Setter Property="Padding" Value="5" />  
                        <Setter Property="Background" Value="#4E87D4" />  
                        <Setter Property="Foreground" Value="White" />  
                    </Style>  
                </DataGrid.ColumnHeaderStyle>  
                <DataGrid.Columns>  
                    <DataGridTextColumn Header="ExpenseType" />  
                    <DataGridTextColumn Header="Amount"  />  
                </DataGrid.Columns>  
            </DataGrid>  
        </Grid>  
    </Grid>  
    ```  
  
     Bu kullanıcı Arabirimi için giriş sayfası için oluşturulan kullanıcı Arabiriminde benzer, ancak rapor verilerini görüntülenen bir **DataGrid** denetimi.  
  
3.  Derleme ve uygulamayı çalıştırın.  
  
4.  Seçin **görünümü** düğmesi.  
  
     Harcama Raporu sayfası görüntülenir.  
  
     Harcama Raporu sayfası aşağıda gösterilmektedir. Geri gezinme düğmesi etkin olduğunu dikkat edin.  
  
     ![ExpenseIt örnek ekran görüntüsünde](../designers/media/gettingstartedfigure4.png "GettingStartedFigure4")  
  
#### <a name="to-style-controls"></a>Stil denetimleri  
  
1.  Açık **App.xaml** dosyası (C#) veya **Application.xaml** dosyasını (Visual Basic).  
  
2.  Aşağıdaki XAML arasında ekleme `<Application.Resources>` ve `</Application.Resources>` etiketler:  
  
    ```xaml  
    <!-- Header text style -->  
    <Style x:Key="headerTextStyle">  
        <Setter Property="Label.VerticalAlignment" Value="Center"></Setter>  
        <Setter Property="Label.FontFamily" Value="Trebuchet MS"></Setter>  
        <Setter Property="Label.FontWeight" Value="Bold"></Setter>  
        <Setter Property="Label.FontSize" Value="18"></Setter>  
        <Setter Property="Label.Foreground" Value="#0066cc"></Setter>  
    </Style>  
  
    <!-- Label style -->  
    <Style x:Key="labelStyle" TargetType="{x:Type Label}">  
        <Setter Property="VerticalAlignment" Value="Top" />  
        <Setter Property="HorizontalAlignment" Value="Left" />  
        <Setter Property="FontWeight" Value="Bold" />  
        <Setter Property="Margin" Value="0,0,0,5" />  
    </Style>  
  
    <!-- DataGrid header style -->  
    <Style x:Key="columnHeaderStyle" TargetType="{x:Type DataGridColumnHeader}">  
        <Setter Property="Height" Value="35" />  
        <Setter Property="Padding" Value="5" />  
        <Setter Property="Background" Value="#4E87D4" />  
        <Setter Property="Foreground" Value="White" />  
    </Style>  
  
    <!-- List header style -->  
    <Style x:Key="listHeaderStyle" TargetType="{x:Type Border}">  
        <Setter Property="Height" Value="35" />  
        <Setter Property="Padding" Value="5" />  
        <Setter Property="Background" Value="#4E87D4" />  
    </Style>  
  
    <!-- List header text style -->  
    <Style x:Key="listHeaderTextStyle" TargetType="{x:Type Label}">  
        <Setter Property="Foreground" Value="White" />  
        <Setter Property="VerticalAlignment" Value="Center" />  
        <Setter Property="HorizontalAlignment" Value="Left" />  
    </Style>  
  
    <!-- Button style -->  
    <Style x:Key="buttonStyle" TargetType="{x:Type Button}">  
        <Setter Property="Width" Value="125" />  
        <Setter Property="Height" Value="25" />  
        <Setter Property="Margin" Value="0,10,0,0" />  
        <Setter Property="HorizontalAlignment" Value="Right" />  
    </Style>  
    ```  
  
     Bu XAML aşağıdaki stilleri ekler:  
  
    -   `headerTextStyle`: Sayfa başlığı biçimine `Label`.  
  
    -   `labelStyle`: Biçimine `Label` kontrol eder.  
  
    -   `columnHeaderStyle`: Biçimine `DataGridColumnHeader`.  
  
    -   `listHeaderStyle`: List üstbilgisi biçimine `Border` kontrol eder.  
  
    -   `listHeaderTextStyle`: List üstbilgisi biçimine **etiket**.  
  
    -   `buttonStyle`: Biçimine `Button` üzerinde **ExpenseItHome.XAML** pppage.  
  
3.  Açık **ExpenseItHome.XAML** ve arasındaki her şeyi değiştirin `<Grid>` ve `</Grid>` aşağıdaki XAML ile öğeleri  
  
    ```xaml  
    <Grid.ColumnDefinitions>  
                <ColumnDefinition Width="230" />  
                <ColumnDefinition />  
            </Grid.ColumnDefinitions>  
  
            <Grid.RowDefinitions>  
                <RowDefinition/>  
                <RowDefinition Height="Auto"/>  
                <RowDefinition />  
                <RowDefinition Height="Auto"/>  
            </Grid.RowDefinitions>  
            <Label Grid.Column="1" Style="{StaticResource headerTextStyle}" >  
                View Expense Report  
            </Label>  
            <!-- People list -->  
                  <Border Grid.Column="1" Grid.Row="1" Style="{StaticResource listHeaderStyle}">  
                <Label Style="{StaticResource listHeaderTextStyle}">Names</Label>  
            </Border>  
            <ListBox Name="peopleListBox" Grid.Column="1" Grid.Row="2">  
                <ListBoxItem>Mike</ListBoxItem>  
                <ListBoxItem>Lisa</ListBoxItem>  
                <ListBoxItem>John</ListBoxItem>  
                <ListBoxItem>Mary</ListBoxItem>  
            </ListBox>  
  
            <!-- View report button -->  
            <Button Grid.Column="1" Grid.Row="3" Click="Button_Click" Style="{StaticResource buttonStyle}">View</Button>  
            <Grid.Background>  
                <ImageBrush ImageSource="watermark.png"  />  
            </Grid.Background>  
    ```  
  
     Gibi özellikler `VerticalAlignment` ve `FontFamily` her denetimin görünümünü tanımlamak kaldırılır ve stilleri uygulayarak değiştirilir.  
  
4.  Açık **ExpenseReportPage.xaml** ve arasındaki her şeyi değiştirin `<Grid>` ve son `</Grid>` aşağıdaki XAML ile öğeleri  
  
    ```xaml  
    <Grid.Background>  
        <ImageBrush ImageSource="watermark.png" />  
    </Grid.Background>  
    <Grid.ColumnDefinitions>  
        <ColumnDefinition Width="230" />  
        <ColumnDefinition />  
    </Grid.ColumnDefinitions>  
    <Grid.RowDefinitions>  
        <RowDefinition Height="Auto" />  
        <RowDefinition />  
    </Grid.RowDefinitions>  
    <Label Grid.Column="1" Style="{StaticResource headerTextStyle}">  
        Expense Report For:  
    </Label>  
    <Grid Margin="10" Grid.Column="1" Grid.Row="1">  
        <Grid.ColumnDefinitions>  
            <ColumnDefinition />  
            <ColumnDefinition />  
        </Grid.ColumnDefinitions>  
        <Grid.RowDefinitions>  
            <RowDefinition Height="Auto" />  
            <RowDefinition Height="Auto" />  
            <RowDefinition />  
        </Grid.RowDefinitions>  
  
        <!-- Name -->  
        <StackPanel Grid.Column="0" Grid.ColumnSpan="2" Grid.Row="0" Orientation="Horizontal">  
            <Label Style="{StaticResource labelStyle}">Name:</Label>  
            <Label Style="{StaticResource labelStyle}"></Label>  
        </StackPanel>  
  
        <!-- Department -->  
        <StackPanel Grid.Column="0" Grid.ColumnSpan="2" Grid.Row="1"   
    Orientation="Horizontal">  
            <Label Style="{StaticResource labelStyle}">Department:</Label>  
            <Label Style="{StaticResource labelStyle}"></Label>  
        </StackPanel>  
  
        <Grid Grid.Column="0" Grid.ColumnSpan="2" Grid.Row="2" VerticalAlignment="Top"   
              HorizontalAlignment="Left">  
            <!-- Expense type and Amount table -->  
            <DataGrid ColumnHeaderStyle="{StaticResource columnHeaderStyle}"   
                      AutoGenerateColumns="False" RowHeaderWidth="0" >  
                <DataGrid.Columns>  
                    <DataGridTextColumn Header="ExpenseType" />  
                    <DataGridTextColumn Header="Amount"  />  
                </DataGrid.Columns>  
            </DataGrid>  
        </Grid>  
    </Grid>  
  
    ```  
  
     Bu stiller ekler `<Label>` ve `<Border>` öğeleri.  
  
## <a name="connecting-to-data"></a>Verilere Bağlanma  
 Bu bölümde, bir veri sağlayıcısı ve veri şablonu oluşturun ve ardından verileri görüntülemek için denetimler bağlama.  
  
#### <a name="to-bind-data-to-a-control"></a>Bir denetimi veri bağlamak için  
  
1.  Açık **ExpenseItHome.XAML** ve `<Grid>` öğesi...  
  
2.  Aşağıdaki XAML kodu ekleyin:  
  
    ```xaml  
  
    <Grid.Resources>  
    <!-- Expense Report Data -->  
    <XmlDataProvider x:Key="ExpenseDataSource" XPath="Expenses">  
        <x:XData>  
            <Expenses xmlns="">  
                <Person Name="Mike" Department="Legal">  
                    <Expense ExpenseType="Lunch" ExpenseAmount="50" />  
                    <Expense ExpenseType="Transportation" ExpenseAmount="50" />  
                </Person>  
                <Person Name="Lisa" Department="Marketing">  
                    <Expense ExpenseType="Document printing"  
          ExpenseAmount="50"/>  
                    <Expense ExpenseType="Gift" ExpenseAmount="125" />  
                </Person>  
                <Person Name="John" Department="Engineering">  
                    <Expense ExpenseType="Magazine subscription"   
         ExpenseAmount="50"/>  
                    <Expense ExpenseType="New machine" ExpenseAmount="600" />  
                    <Expense ExpenseType="Software" ExpenseAmount="500" />  
                </Person>  
                <Person Name="Mary" Department="Finance">  
                    <Expense ExpenseType="Dinner" ExpenseAmount="100" />  
                </Person>  
            </Expenses>  
        </x:XData>  
    </XmlDataProvider>  
    </Grid.Resources>  
    ```  
  
     Bu kod oluşturur bir `XmlDataProvider` her kişi için veriler içeren sınıf. Normalde bu dosya olarak yüklenir, ancak kolaylık olması için satır içi veriler eklenir.  
  
3.  İçinde `<Grid.Resources>` öğesi, aşağıdaki XAML kodu ekleyin:  
  
    ```xaml  
    <!-- Name item template -->  
    <DataTemplate x:Key="nameItemTemplate">  
        <Label Content="{Binding XPath=@Name}"/>  
    </DataTemplate>  
    ```  
  
     Bu ekler bir `Data Template` içinde verilerin nasıl görüntüleneceğini tanımlar **ListBox**.  
  
4.  Varolan `<ListBox>` aşağıdaki XAML bir öğeyle.  
  
    ```xaml  
    <ListBox Name="peopleListBox" Grid.Column="1" Grid.Row="2"   
             ItemsSource="{Binding Source={StaticResource ExpenseDataSource}, XPath=Person}"  
             ItemTemplate="{StaticResource nameItemTemplate}">  
    </ListBox>  
    ```  
  
     Bu kod bağlar `ItemsSource` özelliği `ListBox` veri kaynağı ve veri şablonu olarak geçerli `ItemTemplate`.  
  
#### <a name="to-connect-data-to-controls"></a>Veri denetimleri bağlanmak için  
  
1.  Açık **ExpenseReportPage.xaml.vb** veya **ExpenseReportPage.xaml.cs**.  
  
2.  C# ' ta aşağıdaki oluşturucuyu ekleyin **ExpenseReportPage** sınıfı veya Visual Basic içinde varolan bir sınıf aşağıdakiyle değiştirin:  
  
    ```csharp  
    // Custom constructor to pass expense report data  
        public ExpenseReportPage(object data):this()  
        {  
            // Bind to expense report data.  
            this.DataContext = data;  
        }  
    ```  
  
    ```vb  
    Partial Public Class ExpenseReportPage  
    Inherits Page  
    Public Sub New()  
    InitializeComponent()  
    End Sub  
  
    ' Custom constructor to pass expense report data  
    Public Sub New(ByVal data As Object)  
    Me.New()  
    ' Bind to expense report data.  
    Me.DataContext = data  
    End Sub  
  
    End Class  
    ```  
  
     Bu oluşturucu, bir veri nesnesini parametre olarak alır. Bu durumda veri nesnesi seçili kişinin adını içerir.  
  
3.  Açık **ExpenseItHome.xaml.vb** veya **ExpenseItHome.xaml.cs**.  
  
4.  Değiştirin `Click` aşağıdaki olay işleyicisini:  
  
    ```csharp  
    private void Button_Click(object sender, RoutedEventArgs e)  
    {  
        // View Expense Report  
        ExpenseReportPage expenseReportPage = new ExpenseReportPage(this.peopleListBox.SelectedItem);  
        this.NavigationService.Navigate(expenseReportPage);  
  
    }  
    ```  
  
    ```vb  
    Private Sub Button_Click(ByVal sender As Object, ByVal e As RoutedEventArgs)  
        ' View Expense Report  
        Dim expenseReportPage As New ExpenseReportPage(Me.peopleListBox.SelectedItem)  
        Me.NavigationService.Navigate(expenseReportPage)  
    End Sub  
    ```  
  
     Bu kod, yeni oluşturucuyu çağırır.  
  
#### <a name="to-update-the-ui-with-data-templates"></a>Veri şablonları ile kullanıcı arabirimini güncelleştirmek için  
  
1.  Açık **ExpenseReportPage.xaml**.  
  
2.  XAML kodunu değiştirin **adı** ve **departmanı** `<StackPanel` aşağıdaki öğeleri:  
  
    ```xaml  
    <!-- Name -->  
    <StackPanel Grid.Column="0" Grid.ColumnSpan="2" Grid.Row="0" Orientation="Horizontal">  
        <Label Style="{StaticResource labelStyle}">Name:</Label>  
        <Label Style="{StaticResource labelStyle}" Content="{Binding XPath=@Name}"></Label>  
    </StackPanel>  
  
    <!-- Department -->  
    <StackPanel Grid.Column="0" Grid.ColumnSpan="2" Grid.Row="1" Orientation="Horizontal">  
        <Label Style="{StaticResource labelStyle}">Department:</Label>  
        <Label Style="{StaticResource labelStyle}" Content="{Binding XPath=@Department}"></Label>  
    </StackPanel>  
  
    ```  
  
     Bu bağlar **etiket** denetimleri için uygun bir veri kaynağı özellikleri.  
  
3.  Aşağıdaki XAML kodu ekleme `<Grid>` öğesi:  
  
    ```xaml  
    <!--Templates to display expense report data-->  
    <Grid.Resources>  
        <!-- Reason item template -->  
        <DataTemplate x:Key="typeItemTemplate">  
            <Label Content="{Binding XPath=@ExpenseType}"/>  
        </DataTemplate>  
        <!-- Amount item template -->  
        <DataTemplate x:Key="amountItemTemplate">  
            <Label Content="{Binding XPath=@ExpenseAmount}"/>  
        </DataTemplate>  
    </Grid.Resources>  
  
    ```  
  
     Bu, harcama rapor verilerinin nasıl görüntüleneceğini tanımlar.  
  
4.  Değiştirin `<DataGrid>` aşağıdaki öğe:  
  
    ```xaml  
    <!-- Expense type and Amount table -->  
    <DataGrid ItemsSource="{Binding XPath=Expense}" ColumnHeaderStyle="{StaticResource columnHeaderStyle}" AutoGenerateColumns="False" RowHeaderWidth="0" >  
  
        <DataGrid.Columns>  
            <DataGridTextColumn Header="ExpenseType" Binding="{Binding XPath=@ExpenseType}"  />  
            <DataGridTextColumn Header="Amount" Binding="{Binding XPath=@ExpenseAmount}" />  
        </DataGrid.Columns>  
  
    </DataGrid>  
    ```  
  
     Bu ekler bir **Itemsource'u** gider öğeleri için olan bağlamaları tanımlar.  
  
5.  Derleme ve uygulamayı çalıştırın.  
  
6.  Bir kişi seçin ve ardından **görünümü** düğmesi.  
  
     Aşağıdaki çizimde, iki sayfaları ExpenseIt uygulama denetimleri, düzeni, stiller, veri bağlama ve uygulanan veri şablonları ile gösterilmektedir.  
  
     ![Örnek ekran görüntüleri ExpenseIt](../designers/media/gettingstartedfigure5.png "GettingStartedFigure5")  
  
##  <a name="Best_Practices"></a> En iyi uygulamalar  
 Bu örnek, WPF ilişkin temel bilgileri gösterir ve sonuç olarak, uygulama geliştirme en iyi izlemez. WPF ve .NET Framework uygulama geliştirme en iyi uygulamalar kapsamlı kapsamını, uygun şekilde aşağıdaki konulara bakın:  
  
-   Erişilebilirlik - [en iyi erişilebilirlik uygulamaları](https://msdn.microsoft.com/library/aa350483\(v=vs.100\).aspx)  
  
-   Güvenlik - [Windows Presentation Foundation güvenliği](https://msdn.microsoft.com/library/aa970906\(v=vs.100\).aspx)  
  
-   Yerelleştirme - [WPF genelleştirmesi ve yerelleştirmesine genel bakış](https://msdn.microsoft.com/library/ms788718\(v=vs.100\).aspx)  
  
-   Performans - [WPF uygulama performansını iyileştirme](https://msdn.microsoft.com/library/aa970683\(v=vs.100\).aspx)  
  
##  <a name="Whats_Next"></a> Yenilikler  
 Artık elinizin altında WPF kullanarak bir masaüstü uygulaması oluşturmak için çeşitli teknikler vardır. Şimdi yapı taşlarını, veri bağlama WPF uygulaması temel bir anlayışa sahip olmalıdır. Bu konuda olmadığı göre en kapsamlı ancak Umarım bazı bu konudaki tekniklerin ötesinde kendiniz keşfedebilirsiniz olasılık da gerekir.  
  
 WPF mimarisi ve programlama modelleri hakkında daha fazla bilgi için aşağıdaki konulara bakın:  
  
- [WPF Mimarisi](https://msdn.microsoft.com/library/ms750441\(v=vs.100\).aspx)  
  
- [XAML genel bakış](https://msdn.microsoft.com/library/ms752059\(v=vs.100\).aspx)  
  
- [Bağımlılık Özelliklerine Genel Bakış](https://msdn.microsoft.com/library/ms752914\(v=vs.100\).aspx)  
  
- [Düzen sistemi](https://msdn.microsoft.com/library/ms745058\(v=vs.100\).aspx)  
  
- [Stiller ve Şablonlar](https://msdn.microsoft.com/library/bb613570\(v=vs.100\).aspx)  
  
  Uygulamaları oluşturma hakkında daha fazla bilgi için aşağıdaki konulara bakın:  
  
- [Uygulaması geliştirmeye genel bakış](https://msdn.microsoft.com/library/bb613549\(v=vs.100\).aspx)  
  
- [Denetimlerine genel bakış](https://msdn.microsoft.com/library/bb613551\(v=vs.100\).aspx)  
  
- [Veri Bağlamaya Genel Bakış](https://msdn.microsoft.com/library/ms752347\(v=vs.100\).aspx)  
  
- [WPF Grafik, animasyon ve medya genel bakış](https://msdn.microsoft.com/library/ms742562\(v=vs.100\).aspx)  
  
- [WPF'deki Belgeler](https://msdn.microsoft.com/library/ms748388\(v=vs.100\).aspx)  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [İzlenecek yol: bir Azure mobil hizmetinize bağlanan bir WPF masaüstü uygulaması oluşturma](../designers/walkthrough-create-a-wpf-desktop-application-connected-to-an-azure-mobile-service.md)   
 [Windows Presentation Foundation ile Modern Masaüstü Uygulamaları Oluşturma](../designers/create-modern-desktop-applications-with-windows-presentation-foundation.md)



