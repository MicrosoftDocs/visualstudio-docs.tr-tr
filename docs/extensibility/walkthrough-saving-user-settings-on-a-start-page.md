---
title: 'İzlenecek yol: Kullanıcı ayarlarını başlangıç sayfasına kaydetme | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: 754b9bf3-8681-4c77-b0a4-09146a4e1d2d
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: fa57fb8c4e0c85ff7a9c1b258f1c326a241442c3
ms.sourcegitcommit: ef828606e9758c7a42a2f0f777c57b2d39041ac3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/06/2018
ms.locfileid: "39566723"
---
# <a name="walkthrough-save-user-settings-on-a-start-page"></a>İzlenecek yol: bir başlangıç sayfasında kullanıcı ayarlarını Kaydet
Başlangıç sayfası için kullanıcı ayarlarını kalıcı hale getirebilirsiniz. Bu izlenecek yolu takip ederek, kullanıcı bir düğmeye tıkladığında ve ardından başlangıç sayfası yükleyen her zaman bu ayarı alır bir ayarı kayıt defterine kaydeder bir denetim oluşturabilirsiniz. Başlangıç sayfası proje şablonu özelleştirilebilir kullanıcı denetimini içerir ve söz konusu denetim varsayılan başlangıç sayfası XAML çağrıları olduğundan, başlangıç sayfası kendisini değiştirmek zorunda değilsiniz.  
  
 Bu izlenecek yolda örneği ayarlar deposu örneğidir <xref:Microsoft.VisualStudio.Shell.Interop.IVsWritableSettingsStore> okuyan ve bunu çağrıldığında aşağıdaki kayıt defteri konumuna yazma arabirimi: **HKCU\Software\Microsoft\VisualStudio\14.0\\ \<KoleksiyonAdı >**  
  
 Visual Studio'nun deneysel örneğinde çalıştığı sırada ayarlar deposu okuyan ve yazan **HKCU\Software\Microsoft\VisualStudio\14.0Exp\\\<KoleksiyonAdı >.**  
  
 Ayarlarını kalıcı yapma hakkında daha fazla bilgi için bkz: [genişletme kullanıcı ayarları ve seçenekleri](../extensibility/extending-user-settings-and-options.md).  
  
## <a name="prerequisites"></a>Önkoşullar  
  
> [!NOTE]
>  Bu izlenecek yolda takip etmek için Visual Studio SDK'yı yüklemeniz gerekir. Daha fazla bilgi için [Visual Studio SDK](../extensibility/visual-studio-sdk.md).  
>   
>  Başlangıç sayfası proje şablonu kullanarak indirebilirsiniz **Uzantı Yöneticisi**.  
  
## <a name="setting-up-the-project"></a>Projeyi ayarlama  
  
### <a name="to-configure-the-project-for-this-walkthrough"></a>Bu izlenecek yol için projeyi yapılandırmak için  
  
1.  Bölümünde anlatıldığı gibi bir başlangıç sayfası proje oluşturma [özel bir başlangıç sayfası oluşturma](creating-a-custom-start-page.md). Projeyi adlandırın **SaveMySettings**.  
  
2.  İçinde **Çözüm Gezgini**, aşağıdaki derleme başvurularının StartPageControl projeye ekleyin:  
  
    -   EnvDTE  
  
    -   EnvDTE80  
  
    -   Microsoft.VisualStudio.OLE.Interop  
  
    -   Microsoft.VisualStudio.Shell.Interop.11.0  
  
3.  Açık *MyControl.xaml*.  
  
4.  XAML bölmesinden, üst düzey <xref:System.Windows.Controls.UserControl> öğe tanımı; ad alanı bildirimi sonra aşağıdaki olay bildirimi ekleyin.  
  
    ```xml 
    Loaded="OnLoaded"  
    ```  
  
5.  Tasarım bölmesini denetimin ana alana tıklayın ve ardından tuşuna basın **Sil**.  
  
     Bu adım kaldırır <xref:System.Windows.Controls.Border> öğe ve içindeki her şeyi ve yalnızca en üst düzey bırakır <xref:System.Windows.Controls.Grid> öğesi.  
  
6.  Gelen **araç kutusu**, sürükleyin bir <xref:System.Windows.Controls.StackPanel> kılavuz denetimi.  
  
7.  Artık sürükleyin bir <xref:System.Windows.Controls.TextBlock>, <xref:System.Windows.Controls.TextBox>ve bir düğmeyi <xref:System.Windows.Controls.StackPanel>.  
  
8.  Ekleme bir **x: Name** özniteliğini <xref:System.Windows.Controls.TextBox>ve `Click` olayı <xref:System.Windows.Controls.Button>, aşağıdaki örnekte gösterildiği gibi.  
  
    ```xml  
    <StackPanel Width="300" HorizontalAlignment="Center" VerticalAlignment="Center">  
        <TextBlock Width="140" FontSize="14">Enter your setting</TextBlock>  
        <TextBox x:Name="txtblk" Margin="0, 5, 0, 10" Width="140" />  
        <Button Click="Button_Click" Width="100">Save My Setting</Button>  
    </StackPanel>  
    ```  
  
## <a name="implement-the-user-control"></a>Kullanıcı denetimi uygulayın  
  
### <a name="to-implement-the-user-control"></a>Kullanıcı denetimi uygulamak için  
  
1.  XAML bölmesinde, `Click` özniteliği <xref:System.Windows.Controls.Button> öğesini ve ardından **olay işleyicisine Git**.  
  
     Bu adım açılır *MyControl.xaml.cs*ve için bir saplama işleyici oluşturur `Button_Click` olay.  
  
2.  Aşağıdaki `using` deyimlerini dosyanın üstüne.  
  
     [!code-csharp[StartPageDTE#11](../extensibility/codesnippet/CSharp/walkthrough-saving-user-settings-on-a-start-page_1.cs)]  
  
3.  Özel bir ekleme `SettingsStore` özelliği, aşağıdaki örnekte gösterildiği gibi.  
  
    ```csharp  
    private IVsWritableSettingsStore _settingsStore = null;  
    private IVsWritableSettingsStore SettingsStore  
    {  
        get  
        {  
            if (_settingsStore == null)  
            {  
                // Get a reference to the DTE from the DataContext.   
                var typeDescriptor = DataContext as ICustomTypeDescriptor;  
                var propertyCollection = typeDescriptor.GetProperties();  
                var dte = propertyCollection.Find("DTE", false).GetValue(  
                    DataContext) as DTE2;  
  
                // Get the settings manager from the DTE.   
                var serviceProvider = new ServiceProvider(  
                    (Microsoft.VisualStudio.OLE.Interop.IServiceProvider)dte);  
                var settingsManager = serviceProvider.GetService(  
                    typeof(SVsSettingsManager)) as IVsSettingsManager;  
  
                // Write the user settings to _settingsStore.  
                settingsManager.GetWritableSettingsStore(  
                    (uint)__VsSettingsScope.SettingsScope_UserSettings,  
                    out _settingsStore);  
            }  
            return _settingsStore;  
        }  
    }  
    ```  
  
     Bu özellik, önce bir başvuru edinir <xref:EnvDTE80.DTE2> Otomasyon nesne modeli içerir arabirimi <xref:System.Windows.FrameworkElement.DataContext%2A> kullanıcı denetimi ve ardından kullanan bir kopyasını almak için DTE <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsManager> arabirimi. Daha sonra geçerli kullanıcı ayarları döndürmek için bu örneği kullanır.  
  
4.  Doldurun `Button_Click` aşağıdaki gibi olay.  
  
    ```csharp  
    private void Button_Click(object sender, RoutedEventArgs e)  
    {  
        int exists = 0;  
        SettingsStore.CollectionExists("MySettings", out exists);  
        if (exists != 1)  
        {  
            SettingsStore.CreateCollection("MySettings");  
        }  
        SettingsStore.SetString("MySettings", "MySetting", txtblk.Text);  
    }  
    ```  
  
     Bu kayıt defteri "MySettings" koleksiyonunda "MySetting" alanına metin kutusunun içeriğini yazar. Koleksiyon mevcut değilse oluşturulur.  
  
5.  Aşağıdaki işleyicisi eklemek `OnLoaded` kullanıcı denetiminin olay.  
  
    ```csharp  
    private void OnLoaded(Object sender, RoutedEventArgs e)  
    {  
        string value;  
        SettingsStore.GetStringOrDefault(  
            "MySettings", "MySetting", "", out value);  
        txtblk.Text = value;  
    }  
    ```  
  
     Bu kod metni metin kutusunun geçerli değeri "MySetting" olarak ayarlar.  
  
6.  Kullanıcı denetimi oluşturun.  
  
7.  İçinde **Çözüm Gezgini**açın *source.extension.vsixmanifest*.  
  
8.  Bildirim düzenleyicisinde ayarlama **ürün adı** için **My ayarlarını başlangıç sayfası Kaydet**.  
  
     Görünür olduğundan, bu özellik başlangıç sayfası adını ayarlar **başlangıç sayfasını Özelleştir** listesinde **seçenekleri** iletişim kutusu.  
  
9. Derleme *StartPage.xaml*.  
  
## <a name="test-the-control"></a>Denetimi test  
  
### <a name="to-test-the-user-control"></a>Kullanıcı denetimi test etmek için  
  
1.  Tuşuna **F5**.  
  
     Visual Studio'nun deneysel örneği açılır.  
  
2.  Deneysel örneğinde üzerinde **Araçları** menüsünde tıklatın **seçenekleri**.  
  
3.  İçinde **ortam** düğümünü tıklatın **başlangıç**ve ardından **başlangıç sayfasını Özelleştir** listesinden **[yüklü uzantı] Kaydet My ayarlarını başlangıç sayfası** .  
  
     **Tamam**'ı tıklatın.  
  
4.  Başlangıç sayfası açıksa ve ardından kapatın **görünümü** menüsünde tıklatın **başlangıç sayfası**.  
  
5.  Başlangıç sayfasında tıklayın **Denetimim** sekmesi.  
  
6.  Metin kutusuna **Cat**ve ardından **Kaydet My ayarı**.  
  
7.  Başlangıç sayfasını kapatın ve yeniden açın.  
  
     Metin kutusuna "Cat" sözcüğü görüntülenmesi gerekir.  
  
8.  "Cat" sözcük "Köpek" sözcüğüyle değiştirin. Düğmesine tıklamayın.  
  
9. Başlangıç sayfasını kapatın ve yeniden açın.  
  
     Visual Studio araç pencereleri, bellekte tuttuğu bile Visual Studio'nun kendisi kapatana kadar bunlar kapalı olduğundan ayarı kaydetmediyseniz olsa bile "Köpek" sözcük metin kutusuna görüntülenmesi gerekir.  
  
10. Visual Studio'nun deneysel örneği kapatın.  
  
11. Tuşuna **F5** deneysel örneğinde yeniden açmak için.  
  
12. Metin kutusuna "Cat" sözcüğü görüntülenmesi gerekir.  
  
## <a name="next-steps"></a>Sonraki adımlar  
 Kaydedip almak ve ayarlamak için farklı değerleri farklı olay işleyicileri'ı kullanarak herhangi bir sayıda özel ayarları almak için bu kullanıcı denetimi değiştirebilirsiniz `SettingsStore` özelliği. Farklı bir kullandığınız sürece `propertyName` her çağrı için parametre <xref:Microsoft.VisualStudio.Shell.Interop.IVsWritableSettingsStore.SetString%2A>, değerleri başka bir kayıt defterinde üzerine yazmayın.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 <xref:EnvDTE80.DTE2?displayProperty=fullName>     
 [Visual Studio komutları için bir başlangıç sayfası ekleme](../extensibility/adding-visual-studio-commands-to-a-start-page.md)