---
title: Hata ayıklama sırasında XAML özelliklerini denetleme | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 390edde4-7b8d-4c89-8d69-55106b7e6b11
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- uwp
ms.openlocfilehash: fcb2877a79afc310985102972d870caae560b393
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2018
ms.locfileid: "31480221"
---
# <a name="inspect-xaml-properties-while-debugging"></a>Hata ayıklama sırasında XAML özelliklerini denetleme
Çalışan XAML kodunuzu ile gerçek zamanlı bir görünümünü elde edebilirsiniz **Canlı görsel ağaç** ve **dinamik özellik Explorer**. Bu araçlar, çalışan XAML uygulamanızın kullanıcı Arabirimi öğeleri ağaç görünümünü sunmak ve seçtiğiniz herhangi bir kullanıcı Arabirimi öğesi çalışma zamanı özelliklerini göster.  
  
 Aşağıdaki yapılandırmaları bu araçları kullanabilirsiniz:  
  
|Uygulama türü|İşletim sistemi ve araçları|  
|-----------------|--------------------------------|  
|Windows Presentation Foundation (4.0 ve üstü) uygulamaları|Windows 7 ve üstü|  
|Evrensel Windows uygulamaları|Windows 10 ve üstü ile [Windows 10 SDK'sı](https://dev.windows.com/en-us/downloads/windows-10-sdk)|  
  
## <a name="looking-at-elements-in-the-live-visual-tree"></a>Canlı görsel ağaç öğeleri bakarak  
 Bir liste görünümü ve bir düğme olan çok basit WPF uygulaması başlayalım. Her zaman düğmesini tıklatın, başka bir öğeyi listeye eklenir. Tek sayılı öğeleri gri renkte görünür ve tek sayılı öğeleri sarı renkli.  
  
 Yeni bir C# WPF uygulaması oluşturma (Dosya > Yeni > Proje, ardından seçin C# ve Bul WPF uygulaması). Bu ad **TestXAML**.  
  
 MainWindow.xaml aşağıdaki gibi değiştirin:  
  
```xaml  
<Window x:Class="TestXAML.MainWindow"  
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
    xmlns:d="http://schemas.microsoft.com/expression/blend/2008"  
    xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"  
    xmlns:local="clr-namespace:TestXAML"  
    mc:Ignorable="d"  
     Title="MainWindow" Height="350" Width="525">  
    <Grid>  
        <Button x:Name="button" Background="LightBlue" Content="Add Item" HorizontalAlignment="Left" Margin="216,206,0,0" VerticalAlignment="Top" Width="75" Click="button_Click"/>  
        <ListBox x:Name="listBox" HorizontalAlignment="Left" Height="100" VerticalAlignment="Top" Width="100" Margin="205,80,0,0"/>  
    </Grid>  
</Window>  
```  
  
 Aşağıdaki komut işleyici MainWindow.xaml.cs dosyasına ekleyin:  
  
```csharp 
int count;

private void button_Click(object sender, RoutedEventArgs e)  
{  
    ListBoxItem item = new ListBoxItem();  
    item.Content = "Item" + ++count;  
    if (count % 2 == 0)  
    {  
        item.Background = Brushes.LightGray;  
    }  
    else  
    {  
        item.Background = Brushes.LightYellow;  
    }  
    listBox.Items.Add(item);  
}  
```  
  
 Projeyi derleyin ve hata ayıklamayı Başlat. (Derleme yapılandırması hata ayıklama, değil sürüm olmalıdır. Derleme yapılandırmaları hakkında daha fazla bilgi için bkz: [derleme yapılandırmalarını anlama](../ide/understanding-build-configurations.md).)  
  
 Pencere ortaya çıktığında tıklatın **Öğe Ekle** birkaç kez düğmesine tıklayın. Şöyle bir şey görmeniz gerekir:  
  
 ![Uygulamanın ana penceresi](../debugger/media/livevisualtree-app.png "LiveVIsualTree uygulama")  
  
 Şimdi açmak **Canlı görsel ağaç** penceresi (**hata ayıklama > Windows > Canlı görsel ağaç**, veya IDE sol tarafında Bul). Biz bu pencereyi görebilecekleri yerleştirme konumunu uzağa doğru sürükleyin ve **Canlı özellikleri** penceresi yan yana. İçinde **Canlı görsel ağaç** penceresinde genişletin **ContentPresenter** düğümü. Düğmesini ve liste kutusu için düğümleri içermelidir. Liste kutusu genişletin (ve daha sonra **ScrollContentPresenter** ve **ItemsPresenter**) liste kutusu öğeleri bulmak için. Pencerenin aşağıdaki gibi görünmelidir:  
  
 ![Canlı görsel ağaç ListBoxItems](../debugger/media/livevisualtree-listboxitems.png "LiveVisualTree ListBoxItems")  
  
 Uygulama penceresine geri dönün ve birkaç daha fazla öğe ekleyin. Daha fazla liste kutusu öğeleri görünür görmelisiniz **Canlı görsel ağaç**.  
  
 Artık liste kutusu öğeleri birinin özelliklerini göz atalım. İlk liste kutusu öğesi seçin **Canlı görsel ağaç** tıklatıp **özellikleri göster** araç çubuğunda simge. **Dinamik özellik Explorer** görünmelidir. Unutmayın **içerik** "Item1" bir alandır ve **arka plan** alandır **#FFFFFFE0** (Açık Sarı). Geri dönerek **Canlı görsel ağaç** ve ikinci liste kutusu öğesini seçin. **Dinamik özellik Explorer** , göstermelidir **içerik** alandır "Item2" ve **arka plan** alandır **#FFD3D3D3** (açık gri ).  
  
 XAML gerçek yapısını çok doğrudan ilgi büyük olasılıkla öğelerinin var ve kod iyi bilmiyorsanız, aradığınız ne bulmak için ağaç gezinme sabit bir zaman olabilir. Bu nedenle **Canlı görsel ağaç** incelemek istediğiniz öğe bulmanıza yardımcı olmak için uygulamanın kullanıcı Arabirimi kullandığınız olanak veren çeşitli şekillerde sahiptir.  
  
 **Çalışan uygulama seçimini etkinleştirin**. Soldaki düğmesi seçilirse bu modu etkinleştirmek **Canlı görsel ağaç** araç. Bu moduyla uygulamada bir kullanıcı Arabirimi öğesi seçebilirsiniz ve **Canlı görsel ağaç** (ve **dinamik özellik Görüntüleyicisi**) o öğeye karşılık gelen ağaç düğümü göstermek için otomatik olarak güncelleştirilir. ve özellikleri.  
  
 **Uygulama çalışırken düzeni Donatıcılar görüntülemek**. Hemen etkinleştir seçimi düğmesinin sağında düğmesi seçtiğinizde, bu mod etkinleştirebilirsiniz. Zaman **görüntüleme düzeni Donatıcılar** açıktır, uygulama penceresini ne bunu, kenar boşluklarını gösteren dikdörtgenler yanı sıra hizalar görebilmeniz için seçili nesnenin sınırları boyunca yatay ve dikey çizgileri göster neden olur. Örneğin, her ikisi de kapatma **etkinleştirmek seçimi** ve **görüntüleme düzeni** açık ve select **Öğe Ekle** uygulama metin bloğunda. Metin bloğu düğümünde görmelisiniz **Canlı görsel ağaç** ve metin engelleyin özellikleri **dinamik özellik Görüntüleyicisi**, metin bloğu sınırlarına yatay ve dikey satırlarında yanı sıra.  
  
 ![DisplayLayout LivePropertyViewer](../debugger/media/livevisualtreelivepropertyviewer-displaylayout.png "LiveVisualTreeLivePropertyViewer DisplayLayout")  
  
 **Önizleme seçimi**. Bu mod Canlı görsel ağaç araç soldan üçüncü düğmesini seçerek etkinleştirebilirsiniz. Uygulamanın kaynak koduna erişim varsa, bu mod burada öğesi bildirildi, XAML gösterir. Seçin **etkinleştirmek seçimi** ve **Önizleme seçim**, ve ardından test uygulamamız düğmesini seçin. Visual Studio'da MainWindow.xaml dosyasını açar ve satırda düğmesi tanımlandığı imlecin bulunduğu.  
  
## <a name="using-xaml-tools-with-running-applications"></a>Çalışan uygulamalar XAML araçlarını kullanma  
 Kaynak kodu yok olsa bile bu XAML araçları kullanabilirsiniz. Çalışan bir XAML uygulamaya taktığınızda, kullanabileceğiniz **Canlı görsel ağaç** uygulamasının kullanıcı Arabirimi öğeleri üzerinde çok. Burada, önce kullandık WPF test uygulaması kullanarak bir örnek verilmiştir.  
  
1.  Başlat **TestXaml** sürüm yapılandırmasında uygulama. Çalıştıran bir işlem bağlanamaz bir **hata ayıklama** yapılandırma.  
  
2.  Visual Studio ikinci bir örneğini açarak **hata ayıklama > ekleme işlemi için**. Bul **TestXaml.exe** kullanılabilir işlemler'i tıklatın ve listedeki **Attach**.  
  
3.  Uygulama çalışmaya başlar.  
  
4.  Visual Studio ikinci örneği açın **Canlı görsel ağaç** (**hata ayıklama > Windows > Canlı görsel ağaç**). Görmeniz gerekir **TestXaml** kullanıcı Arabirimi öğeleri ve uygulama doğrudan hata ayıklama while gibi bunları yönetmek kullanabilirsiniz.