---
title: Başlangıç sayfasına kullanıcı denetimi ekleme | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- start page dll
- custom start page
- start page assembly
ms.assetid: 5b7997db-af6f-4fa9-a128-bceb42bddaf1
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 96b280221ba7efdefd3023f015bd4075b8c03aaa
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49910505"
---
# <a name="add-user-control-to-the-start-page"></a>Başlangıç sayfasına kullanıcı denetimi Ekle
Bu izlenecek yol, özel bir başlangıç sayfası için bir DLL başvurusu ekleme işlemi gösterilmektedir. Örnek bir kullanıcı denetimi çözüme ekler, kullanıcı denetimi oluşturur ve ardından derlemesi başlangıç sayfasından başvuran *.xaml* dosya. Yeni bir sekmede temel bir Web tarayıcısı olarak işlevler kullanıcı denetimi barındırır.  
  
 Aynı işlem öğesinden çağrılması herhangi bir derleme eklemek için kullanabileceğiniz bir *.xaml* dosya.  
  
## <a name="add-a-wpf-user-control-to-the-solution"></a>Çözüme bir WPF kullanıcı denetimi Ekle  
 İlk olarak, bir Windows Presentation Foundation (WPF) kullanıcı denetimi başlangıç sayfası çözüme ekleyin.  
  
1.  Kullanarak başlangıç sayfası oluşturma oluşturduğumuz [özel bir başlangıç sayfası oluşturma](../extensibility/creating-a-custom-start-page.md).  
  
2.  İçinde **Çözüm Gezgini**, çözüme sağ tıklayın, **Ekle**ve ardından **yeni proje**.  
  
3.  Sol bölmesinde **yeni proje** iletişim kutusunda, ya da genişletin **Visual Basic** veya **Visual C#** düğüm seçeneğine tıklayıp **Windows**. Orta bölmede seçin **WPF kullanıcı denetimi Kitaplığı**.  
  
4.  Denetim adı `WebUserControl` ve ardından **Tamam**.  
  
## <a name="implement-the-user-control"></a>Kullanıcı denetimi uygulayın  
 WPF kullanıcı denetimi uygulamak için XAML kullanıcı arabiriminde (UI) oluşturma ve arka plan kod olayları C# veya başka bir .NET dil yazın.  
  
### <a name="to-write-the-xaml-for-the-user-control"></a>XAML için kullanıcı denetimi yazmak için  
  
1.  Kullanıcı denetimi için XAML dosyasını açın. İçinde `<Grid>` öğesi, aşağıdaki satır tanımları denetimine ekleyin.  
  
    ```vb  
    <Grid.RowDefinitions>  
        <RowDefinition Height="Auto"/>  
        <RowDefinition Height="*" />  
    </Grid.RowDefinitions>  
  
    ```  
  
2.  Ana `<Grid>` öğesi, aşağıdaki yeni `<Grid>` Web adresleri ve yeni adresini ayarlamak için bir düğme yazmak için bir metin kutusu içeren öğe.  
  
    ```xml  
    <Grid Grid.Row="0">  
        <Grid.ColumnDefinitions>  
            <ColumnDefinition Width="*" />  
            <ColumnDefinition Width="Auto" />  
        </Grid.ColumnDefinitions>  
        <TextBox x:Name="UserSource" Grid.Column="0" />  
        <Button Grid.Column="1" x:Name="SetButton" Content="Set Address" Click="SetButton_Click" />  
    </Grid>  
    ```  
  
3.  Aşağıdaki çerçeve için üst düzey ekleme `<Grid>` öğesi hemen sonrasına `<Grid>` düğme ve metin kutusu içeren öğe.  
  
    ```vb  
    <Frame Grid.Row="1" x:Name="WebFrame" Source="http://www.bing.com" Navigated="WebFrame_Navigated" />  
    ```  
  
4.  Aşağıdaki örnekte, tamamlanmış XAML için kullanıcı denetimi gösterilmektedir.  
  
    ```xml  
    <UserControl x:Class="WebUserControl.UserControl1"  
                 xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
                 xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
                 xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"   
                 xmlns:d="http://schemas.microsoft.com/expression/blend/2008"   
                 mc:Ignorable="d"   
                 d:DesignHeight="300" d:DesignWidth="300">  
        <Grid>  
            <Grid.RowDefinitions>  
                <RowDefinition Height="Auto"/>  
                <RowDefinition Height="*" />  
            </Grid.RowDefinitions>  
            <Grid Grid.Row="0">  
                <Grid.ColumnDefinitions>  
                    <ColumnDefinition Width="*" />  
                    <ColumnDefinition Width="Auto" />  
                </Grid.ColumnDefinitions>  
                <TextBox x:Name="UserSource" Grid.Column="0" />  
                <Button Grid.Column="1" x:Name="SetButton" Content="Set Address" Click="SetButton_Click" />  
            </Grid>  
            <Frame Grid.Row="1" x:Name="WebFrame" Source="http://www.bing.com" Navigated="WebFrame_Navigated" />  
        </Grid>  
    </UserControl>  
  
    ```  
  
### <a name="to-write-the-code-behind-events-for-the-user-control"></a>Kullanıcı denetiminin arka plan kod olayları yazmak için  
  
1.  XAML Tasarımcısı'nda çift **adresinde** düğmesi denetimi eklendi.  
  
     *UserControl1.cs* dosyası Kod Düzenleyicisi'nde açılır.  
  
2.  SetButton_Click olay işleyicisi aşağıdaki gibi doldurun.  
  
    ```csharp  
    private void SetButton_Click(object sender, RoutedEventArgs e)  
    {  
        try  
        {  
            this.WebFrame.Source = new Uri(this.UserSource.Text, UriKind.Absolute);  
        }  
        catch (Exception error)  
        {  
            MessageBox.Show(error.Message);  
        }  
    }  
    ```  
  
     Bu kod, Web tarayıcısı için hedef olarak metin kutusuna yazdığınız Web adresini ayarlar. Adres geçerli değilse, kod bir hata oluşturur.  
  
3.  Ayrıca WebFrame_Navigated olay işlemesi gerekir:  
  
    ```csharp  
    private void WebFrame_Navigated(object sender, EventArgs e)  
    { }  
    ```  
  
4.  Çözümü oluşturun.  
  
## <a name="add-the-user-control-to-the-start-page"></a>Başlangıç sayfasına kullanıcı denetimi Ekle  
 Bu denetim başlangıç sayfası proje dosyasında başlangıç sayfası projenin kullanılabilir hale getirmek için yeni denetim kitaplığına bir başvuru ekleyin. Ardından, başlangıç sayfası XAML biçimlendirme denetimi ekleyebilirsiniz.  
  
1. İçinde **Çözüm Gezgini**, başlangıç sayfası projeye sağ **başvuruları** ve ardından **Başvuru Ekle**.  
  
2. Üzerinde **projeleri** sekmesinde **WebUserControl** ve ardından **Tamam**.  
  
3. Üzerinde **derleme** menüsünde tıklatın **Çözümü Derle**.  
  
    Çözümü derledikten kullanıcı denetimi için IntelliSense çözümdeki diğer dosyalar için kullanılabilmesini sağlar.  
  
   Başlangıç sayfası XAML biçimlendirme denetimi eklemek için bir ad alanı derlemesine başvuru ekleyin ve denetimi sayfasına yerleştirin.  
  
### <a name="to-add-the-control-to-the-markup"></a>Denetim için biçimlendirme eklemek için  
  
1. İçinde **Çözüm Gezgini**, başlangıç sayfasını açmak *.xaml* dosya.  
  
2. İçinde **XAML** bölmesinde, aşağıdaki ad alanı bildirimi için üst düzey ekleme <xref:System.Windows.Controls.Grid> öğesi.  
  
   ```xml  
   xmlns:vsc="clr-namespace:WebUserControl;assembly=WebUserControl"  
   ```  
  
3. İçinde **XAML** bölmesinde gidin \<kılavuz > bölümü.  
  
    Bölüm içeren bir <xref:System.Windows.Controls.TabControl> öğesinde bir <xref:System.Windows.Controls.Grid> öğesi.  
  
4. Ekleme bir \<TabControl > öğesini içeren bir \<TabItem >, kullanıcı denetiminiz bir başvuru içeriyor.  
  
   ```xml  
  
   <TabItem Header="Web" Height="Auto">  
       <vsc:UserControl1 />  
   </TabItem>  
  
   ```  
  
   Artık denetim test edebilirsiniz.  
  
## <a name="test-a-manually-created-custom-start-page"></a>Testi el ile oluşturulan özel bir başlangıç sayfası  
  
1.  XAML dosyanızın ve destekleyici metin dosyaları veya biçimlendirme dosyaları, çok kopya *%USERPROFILE%\My Documents\Visual Studio 2015\StartPages\\*  klasör.  
  
2.  Başlangıç sayfanızı herhangi bir denetim veya Visual Studio yüklü olmayan bütünleştirilmiş kodlar içindeki türleri başvuruyorsa, derlemeleri kopyalamak ve ardından bunları yapıştırın _Visual Studio yükleme klasörü_**\Common7\IDE\ PrivateAssemblies\\**.  
  
3.  Bir Visual Studio komut isteminde **devenv /rootsuffix Exp** Visual Studio'nun deneysel örneği açın.  
  
4.  Deneysel örneğinde Git **Araçları** > **seçenekleri** > **ortam** > **başlatma** sayfasında ve XAML dosyanızı seçin **başlangıç sayfasını Özelleştir** açılır.  
  
5.  Üzerinde **görünümü** menüsünü tıklatın **başlangıç sayfası**.  
  
     Özel başlangıç sayfanızı görüntülenmesi gerekir. Dosyaları değiştirmek istiyorsanız, size gerekir deneysel örneği kapatın, değişiklik, kopyalayın ve değiştirilen dosyaları yapıştırın ve ardından değişiklikleri görüntülemek için deneysel örneğinde yeniden açın.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [WPF kapsayıcı denetimleri](https://msdn.microsoft.com/library/a0177167-d7db-4205-9607-8ae316952566)   
 [İzlenecek yol: başlangıç sayfasına özel XAML ekleme](../extensibility/walkthrough-adding-custom-xaml-to-the-start-page.md)