---
title: 'İzlenecek yol: Visual C# veya Visual Basic ile basit uygulama oluşturma | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: f84339c7-d617-4f56-bfcd-af2215c347ba
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 51fc073046833165097a8a9a4fb2f169ed3a04e7
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49851692"
---
# <a name="walkthrough-create-a-simple-application-with-visual-c-or-visual-basic"></a>İzlenecek yol: Visual C# veya Visual Basic ile Basit Uygulama Oluşturma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu izlenecek yolu tamamlayarak, Visual Studio ile uygulamalar geliştirirken kullanabileceğiniz birçok araç, iletişim kutusu ve tasarımcı hakkında bilgi sahibi olacaksınız. Tümleşik geliştirme ortamında (IDE) çalışma hakkında daha fazla bilgi edinirken, basit bir "Merhaba Dünya" stili uygulama oluşturacak, kullanıcı arabirimini tasarlayacak, kod ekleyecek ve hataları ayıklayacaksınız.  
  
 Bu konu aşağıdaki bölümleri içermektedir:  
  
 [IDE'yi yapılandırma](../ide/walkthrough-create-a-simple-application-with-visual-csharp-or-visual-basic.md#BKMK_ConfigureIDE)  
  
 [Basit bir uygulama oluşturma](../ide/walkthrough-create-a-simple-application-with-visual-csharp-or-visual-basic.md#BKMK_CreateApp)  
  
 [Hata ayıklama ve uygulamayı test etme](../ide/walkthrough-create-a-simple-application-with-visual-csharp-or-visual-basic.md#BKMK_DebugTest)  
  
> [!NOTE]
>  Bu izlenecek yol, Visual Studio Prosessional sürümünü temel almaktadır ve bu sürüm, bu izlenecek yol için projeyi oluştururken temel olarak kullanacağınız WPF Uygulaması şablonunu sunar. Windows Masaüstü için Visual Studio Express sürümü de bu şablonu sağlar, ancak Windows için Visual Studio Express ve Web için Visual Studio Express sağlamaz. Visual Studio Express için Windows kullanımı hakkında tanıtıcı bilgiler için bkz [Windows Store uygulamaları için Geliştirici Merkezi](http://msdn.microsoft.com/windows/apps/br229519). Web için Visual Studio Express kullanımı hakkında tanıtıcı bilgiler için bkz [ASP.NET ile çalışmaya başlama](http://www.asp.net/get-started). Ayrıca, Visual Studio sürümünüz ve kullandığınız ayarlar, kullanıcı arabiriminin bazı öğelerinin adlarını ve bulundukları yerleri belirler. Bkz: [Visual Studio'da geliştirme ayarlarını özelleştirme](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
##  <a name="BKMK_ConfigureIDE"></a> IDE'yi yapılandırma  
 Visual Studio'yu ilk kez başlattığınızda, Visual Studio, bir Microsoft hizmeti hesabı (MSA oturum), oturum ister [Visual Studio'ya oturum](http://blogs.msdn.com/b/visualstudio/archive/2013/06/28/welcome-sign-in-to-visual-studio.aspx). Oturum açın ve gerekmez, daha sonra yapın.  
  
 Visual Studio başlatma, sonraki bir dizi önceden tanımlı bir özelleştirmeler grubunu IDE'ye uygulayan ayarlar bileşimini seçmelisiniz. Her bir ayarlar bileşimi, uygulamaları geliştirmenizi kolaylaştırmak amacıyla tasarlanmıştır.  
  
 Bu izlenecek yol, uyguladığınız varsayılmaktadır **genel geliştirme ayarları**, IDE'ye en az miktarda özelleştirmeyi uygulayan. Zaten C# veya Visual Basic (her ikisi de iyi bir seçenek olan) seçtiyseniz, ayarlarınızı değiştirmeniz gerekmez.  Ayarlarınızı değiştirmek istiyorsanız, kullanabileceğiniz **içeri ve dışarı aktarma ayarları Sihirbazı**. Bkz: [Visual Studio'da geliştirme ayarlarını özelleştirme](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
 Visual Studio'yu açtıktan sonra araç pencerelerini, menüleri ve araç çubuklarını ve ana pencere alanını tanıyabilirsiniz. Araç pencereleri tutturulmuştur ve uygulama penceresinin sol tarafında ile **hızlı başlatma**, menü çubuğu ve en üstte standart araç çubuğu. Uygulama penceresinin ortasında olup **başlangıç sayfası**. Bir çözüm veya projeyi yüklediğinizde, alanda görünür düzenleyiciler ve tasarımcılar burada **başlangıç sayfası** olduğu. Uygulama geliştirirken zamanınızın çoğunu bu orta alanda geçireceksiniz.  
  
 Şekil 2: Visual Studio IDE'si  
  
 ![Genel Ayarları uygulanmış IDE](../ide/media/exploreide-idewithgeneralsettings.png "ExploreIDE IDEwithgeneralsettings")  
  
 Düzenleyicideki metinlerin boyutunu veya IDE renk temasını ve yazı tipini kullanarak değiştirme gibi Visual Studio'da ek özelleştirmeler yapabilirsiniz **seçenekleri** iletişim kutusu. Uyguladığınız ayarlar bileşimine bağlı olarak, bu iletişim kutusundaki bazı öğeler otomatik olarak görünmeyebilir. Tüm olası seçeneklerin göründüğünden emin olun **tüm ayarları göster** onay kutusu.  
  
 Şekil 3: Seçenekler iletişim kutusu  
  
 ![Seçenekler iletişim kutusu wirh tüm ayarlar seçeneğini göster](../ide/media/exploreide-optionsdialogbox.png "ExploreIDE Optionsdialogbox")  
  
 Bu örnekte, IDE'nin renk temasını açıktan koyuya değiştireceksiniz.  İsterseniz, proje oluşturma atlayabilirsiniz.  
  
#### <a name="to-change-the-color-theme-of-the-ide"></a>IDE'nin renk temasını değiştirmek için  
  
1. Açık **seçenekleri** iletişim kutusunu **Araçları** üst menü ve ardından **seçenekleri...** öğe.  
  
    ![Komut Araçlar menüsünde Seçenekler](../ide/media/exploreide-toolsoptionsmenu.png "ExploreIDE ToolsOptionsmenu")  
  
2. Değişiklik **renk teması** için **koyu**, ardından **Tamam**.  
  
    ![Seçili koyu renk teması](../ide/media/exploreide-darkthemeoptionsdlgbox.png "ExploreIDE Darkthemeoptionsdlgbox")  
  
   Visual Studio'daki renkler aşağıdaki görüntüyle aynı olmalıdır:  
  
   ![IDE ile uygulanan koyu tema](../ide/media/exploreide-darkthemeide.png "ExploreIDE DarkThemeIDE")  
  
   Bu kılavuzda kalan resimler için kullanılan renk teması açık temadır. IDE'yi özelleştirme hakkında daha fazla bilgi için bkz. [Visual Studio'da geliştirme ayarlarını özelleştirme](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
##  <a name="BKMK_CreateApp"></a> Basit bir uygulama oluşturma  
  
### <a name="create-the-project"></a>Projeyi oluşturma  
 Visual Studio'da bir uygulama oluştururken önce bir proje ve bir çözüm oluşturursunuz. Bu örnekte, bir Windows Presentation Foundation (WPF) projesi oluşturacaksınız.  
  
##### <a name="to-create-the-wpf-project"></a>WPF projesini oluşturmak için  
  
1. Yeni bir proje oluşturun. Menü çubuğunda, **dosya**, **yeni**, **proje...** .  
  
    ![Menü çubuğunda, dosya, yeni seçin, proje](../ide/media/exploreide-filenewproject.png "ExploreIDE FileNewProject")  
  
    Ayrıca **yeni proje** içinde **hızlı başlatma** aynı şeyi yapmak için kutusu.  
  
    ![Hızlı Başlatma kutusuna yeni proje belirtin](../ide/media/exploreide-quicklaunchnewprojectsmall.png "ExploreIDE QuickLaunchNewProjectsmall")  
  
2. Sol bölmede seçerek Visual Basic veya Visual C# WPF uygulaması şablonunu seçin **yüklü**, **şablonları**, **Visual C#**, **Windows**, örneğin'yi ve ardından Orta bölmede WPF uygulaması seçme.  Projeyi yeni proje iletişim kutusunun alt kısmındaki hellowpfapp olarak adlandırın.  
  
    ![HelloWPFApp Visual Basic bir WPF projesi oluşturma](../ide/media/exploreide-newprojectvb.png "ExploreIDE NewProjectVB")  
  
    VEYA  
  
    ![Visual C oluşturma&#35; WPF projesi, HelloWPFApp](../ide/media/exploreide-newprojectcsharp.png "ExploreIDE NewProjectcsharp")  
  
   HelloWPFApp projesi ve çözüm, Visual Studio oluşturur ve **Çözüm Gezgini** çeşitli dosyaları gösterir. WPF Tasarımcısı, bölünmüş bir görünüm halinde bir MainWindow.XAML'in XAML görünümünü ve Tasarım görünümünü gösterir. Daha fazla veya daha az gösterilecek bölme kaydırabilirsiniz ya da görünümün.  Yalnızca bir görsel görünümünü veya yalnızca XAML görünümü görmek seçebilirsiniz. (Daha fazla bilgi için [Windows Forms geliştiriciler için WPF Tasarımcısı](http://msdn.microsoft.com/en-us/47ad0909-e89b-4996-b4ac-874d929f94ca)). Aşağıdaki öğeler görünür **Çözüm Gezgini**:  
  
   Şekil 5: Proje öğeleri  
  
   ![Çözüm Gezgini HelloWPFApp dosyalarla yüklenen](../ide/media/exploreide-hellowpfappfiles.png "ExploreIDE HelloWPFAppFiles")  
  
   Projeyi oluşturduktan sonra özelleştirebilirsiniz. Kullanarak **özellikleri** penceresi (bulunan **görünümü** menüsü), görüntüleyebilir ve proje öğelerine, denetimleri ve uygulamadaki diğer öğeler için seçeneklerini değiştirin. Proje özellikleri ve özellik sayfalarını kullanarak projelere ve çözümlere ilişkin seçenekleri görüntüleyebilir ve değiştirebilirsiniz.  
  
##### <a name="to-change-the-name-of-mainwindowxaml"></a>MainWindow.xaml adını değiştirmek için  
  
1. Aşağıdaki yordamda MainWindow'a daha belirleyici bir ad vereceksiniz. İçinde **Çözüm Gezgini**, MainWindow.XAML'yi seçin. Görmelisiniz **özellikleri** , seçerseniz yoktur ancak pencere, **görünümü** menü ve **özellik penceresi** öğesi. Değişiklik **dosya adı** özelliğini `Greetings.xaml`.  
  
    ![Vurgulanmış dosya adıyla Özellikler penceresi](../ide/media/exploreide-filenameinpropertieswindow.png "ExploreIDE FilenameinPropertiesWindow")  
  
    **Çözüm Gezgini** gösterilmektedir dosyanın adını artık Greetings.xaml olarak ve MainWindow.xaml.vb veya MainWindow.xaml.cs adını (odak düğümünde yerleştirme ve sağ ok tuşuna basarak) MainWindow.xaml düğümünü genişletirseniz, gördüğünüz sunuldu Greetings.xaml.vb veya Greetings.xaml.cs. Bu kod dosyasının, birbiriyle ilişkili çok yakın oldukları göstermek için .xaml dosyası düğümü altında yer alıyor.  
  
   > [!WARNING]
   >  Bu değişiklik, ayıklamayı ve düzeltmeyi sonraki adımlarda öğreneceğiniz bir hataya neden olur.  
  
2. İçinde **Çözüm Gezgini**(Greetings.xaml Tasarımcı görünümünde düğüm odaklanmışken Enter tuşuna basarak) açın ve fareyi kullanarak pencerenin başlık çubuğunu seçin.  
  
3. İçinde **özellikleri** penceresinde değiştirin **başlık** özelliğini `Greetings`.  
  
   MainWindow.xaml için başlık çubuğunda artık Greetings ifadesi görünür.  
  
### <a name="design-the-user-interface-ui"></a>Kullanıcı arabirimini (UI) tasarlama  
 Bu uygulamaya üç tür denetim ekleyeceğiz: TextBlock denetimi, iki RadioButton denetimi ve bir Button denetimi.  
  
##### <a name="to-add-a-textblock-control"></a>TextBlock denetimi eklemek için  
  
1. Açık **araç kutusu** penceresini seçerek **görünümü** menü ve **araç kutusu** öğesi.  
  
2. İçinde **araç kutusu**, TextBlock denetimini arayın.  
  
    ![Araç kutusu vurgulanmış TextBlock denetimini içeren](../ide/media/exploreide-textblocktoolbox.png "ExploreIDE TextBlockToolbox")  
  
3. TextBlock denetimi tasarım yüzeyine TextBlock öğeyi seçerek ve pencereyi tasarım yüzeyine sürükleyerek ekleyin.  Pencerenin üst kısmındaki denetim merkezi.  
  
   Pencereniz aşağıdaki gösterime benzemelidir:  
  
   Şekil 7: TextBlock denetimini içeren Greetings penceresi  
  
   ![TextBlock denetimi Greetings formdaki](../ide/media/exploreide-greetingswithtextblockonly.png "ExploreIDE GreetingswithTextblockonly")  
  
   XAML işaretlemesi aşağıdaki gibi görünmelidir:  
  
```  
<TextBlock HorizontalAlignment="Center" TextWrapping="Wrap" VerticalAlignment="Center" RenderTransformOrigin="4.08,2.312" Margin="237,57,221,238"><Run Text="TextBlock"/><InlineUIContainer><TextBlock TextWrapping="Wrap" Text="TextBlock"/>  
```  
  
##### <a name="to-customize-the-text-in-the-text-block"></a>Metin bloğu içindeki metni özelleştirmek için  
  
1. XAML görünümünde TextBlock için biçimlendirmeyi yerleştirin ve metin özniteliğini değiştirin: `Text=”Select a message option and then choose the Display button.”`  
  
2. Tasarım görünümüne sığacak şekilde TextBlock genişletmeyen, tüm metin görüntülenecek şekilde TextBlock denetimini (tutamaçların kenarlar kullanarak) genişletmek.  
  
3. CTRL + s tuşuna basarak veya kullanarak yaptığınız değişiklikleri kaydetmek **dosya** menü öğesi.  
  
   Ardından iki ekleyeceksiniz [RadioButton](http://msdn.microsoft.com/library/6c9ba847-eab7-4bba-9c74-6b56ef72067b) formu için denetimler.  
  
##### <a name="to-add-radio-buttons"></a>Radyo düğmeleri eklemek için  
  
1. İçinde **araç kutusu**, RadioButton denetimini arayın.  
  
    ![Araç penceresi seçili RadioButton denetimi ile](../ide/media/exploreide-radiobuttontoolbox.png "ExploreIDE RadioButtonToolbox")  
  
2. İki RadioButton denetimi tasarım yüzey RadioButton öğesini seçerek ve pencereyi tasarım yüzeyine iki kez sürükleyerek ekleyin ve düğmeler (bunları seçerek ve ok tuşlarını kullanarak) Taşı düğmeleri yan yana TextBlock altında görünecek şekilde denetimi.  
  
    Pencerenizin şuna benzemesi gerekir:  
  
    Şekil 8: Greetings penceresinde RadioButton denetimleri.  
  
    ![Greetings form textblock ve iki RadioButton'ları ile](../ide/media/exploreide-greetingswithradiobuttons.png "ExploreIDE Greetingswithradiobuttons")  
  
3. İçinde **özellikleri** değişiklik sol taraftaki RadioButton denetimi için pencere **adı** özelliği (özellik en üstündeki **özellikleri** penceresi) için `RadioButton1`.  RadioButton ve formdaki değil arka kılavuz seçtiğinizden emin olun; Ad alanı altında özellik penceresi tür alanını RadioButton yazması gerekir.  
  
4. İçinde **özellikleri** değişiklik sağ taraftaki RadioButton denetimi için pencere **adı** özelliğini `RadioButton2`ve ardından CTRL + s tuşuna basarak veya kullanarak değişikliklerinizi kaydedin **dosya**menü öğesi.  Değiştirme ve kaydetmeden önce RadioButton'ın seçili olduğundan emin olun.  
  
   Artık her bir RadioButton denetimi için görüntü metni ekleyebilirsiniz. Aşağıdaki yordam güncelleştirmeleri **içerik** özelliği bir RadioButton denetimi için.  
  
##### <a name="to-add-display-text-for-each-radio-button"></a>Her bir radyo düğmesine görüntü metni eklemek için  
  
1. Tasarım yüzeyinde, RadioButton1 seçerken sağ fare düğmesine basarak RadioButton1 için kısayol menüsünü açın, seçin **Metni Düzenle**yazıp enter `Hello`.  
  
2. Sağ fare düğmesine basarak RadioButton2 seçerken RadioButton2 için kısayol menüsünü açın, **Metni Düzenle**yazıp enter `Goodbye`.  
  
   Son ekleyeceğiniz UI öğesi bir [düğmesi](http://msdn.microsoft.com/library/a9d8f5a5-c98c-463e-808a-5a4e63173098) denetimi.  
  
##### <a name="to-add-the-button-control"></a>Düğme denetimini eklemek için  
  
1. İçinde **araç kutusu**, arama **düğmesi** denetlemek ve tasarım yüzeyinde RadioButton denetimlerinin altında düğmeyi seçerek ve Tasarım görünümünde forma sürükleyerek ekleyin.  
  
2. XAML Görünümü'nde değiştirin **içerik** Button denetimi için `Content=”Button”` için `Content=”Display”`ve değişiklikleri kaydedin (Ctrl-s veya kullanım **dosya** menü).  
  
    İşaretleme şu örneğe benzemelidir: `<Button Content="Display" HorizontalAlignment="Left" VerticalAlignment="Top" Width="75" Margin="215,204,0,0"/>`  
  
   Pencereniz aşağıdaki gösterime benzemelidir.  
  
   Şekil 9: Son Greetings Kullanıcı Arabirimi  
  
   ![Greetings form denetimi etiketleriyle](../ide/media/exploreide-greetingswithconrollabels.png "ExploreIDE Greetingswithconrollabels")  
  
### <a name="add-code-to-the-display-button"></a>Görüntüle Düğmesine kod ekleme  
 Bu uygulama çalışırken, bir kullanıcı önce radyo düğmesini seçerse ve sonra seçtiğinde bir ileti kutusu görünür **görünen** düğmesi. Merhaba için bir ileti kutusu ve Güle Güle için bir diğer ileti kutusu görünecektir. Bu davranışı oluşturmak için Greetings.xaml.vb veya Greetings.xaml.cs içinde Button_Click olayına kod ekleyeceksiniz.  
  
##### <a name="add-code-to-display-message-boxes"></a>İleti kutularını görüntülemek için kod ekleme  
  
1.  Tasarım yüzeyinde, çift **görünen** düğmesi.  
  
     Greetings.xaml.vb veya Greetings.xaml.cs açılır ve imleç Button_Click olayının içinde olur. (Büyük olasılıkla değil tasarım yüzeyinde RadioButton denetimlerinin seçer ve bunları yeniden adlandırabilir yapıştırılan koda herhangi bir adı altında bir kırmızı dalgalı varsa,) gibi bir tıklama olayı işleyicisi de ekleyebilirsiniz:  
  
     Visual Basic için olay işleyicisi aşağıdaki gibi görünmelidir:  
  
    ```vb  
    Private Sub Button_Click_1(sender As Object, e As RoutedEventArgs)  
  
    End Sub  
    ```  
  
     Visual C# için olay işleyicisi aşağıdaki gibi görünmelidir:  
  
    ```csharp  
    private void Button_Click_1(object sender, RoutedEventArgs e)  
    {  
  
    }  
    ```  
  
2.  Visual Basic için şu kodu girin:  
  
    ```vb  
    If RadioButton1.IsChecked = True Then  
        MessageBox.Show("Hello.")  
    Else RadioButton2.IsChecked = True  
        MessageBox.Show("Goodbye.")  
    End If  
  
    ```  
  
     Visual C# için şu kodu girin:  
  
    ```  
    if (RadioButton1.IsChecked == true)  
    {  
        MessageBox.Show("Hello.");  
    }  
    else  
    {  
        RadioButton2.IsChecked = true;  
        MessageBox.Show("Goodbye.");  
    }  
    ```  
  
3.  Uygulamayı kaydedin.  
  
##  <a name="BKMK_DebugTest"></a> Hata ayıklama ve uygulamayı test etme  
 Şimdi, hatalara bakmak için uygulamadan hata ayıklayacak ve her iki ileti kutusunun da doğru görünüp görünmediğini test edeceksiniz. Aşağıdaki yönergeler size nasıl oluşturacağınızı ve hata ayıklayıcıyı başlatma, ancak daha sonra okuyabilir [bir WPF uygulaması (WPF) oluşturma](http://msdn.microsoft.com/library/a58696fd-bdad-4b55-9759-136dfdf8b91c) ve [hata ayıklama WPF](../debugger/debugging-wpf.md) daha fazla bilgi için.  
  
### <a name="find-and-fix-errors"></a>Hataları bulma ve düzeltme  
 Bu adımda, daha önce XAML dosyası ana penceresinin adını değiştirerek sebep olduğumuz hatayı bulacaksınız.  
  
##### <a name="to-start-debugging-and-find-the-error"></a>Hata ayıklamayı başlatmak ve hatayı bulmak için  
  
1. Hata ayıklayıcı seçerek başlayın **hata ayıklama**, ardından **hata ayıklamayı Başlat**.  
  
    ![Hata ayıklama menüsünden hata ayıklamayı Başlat](../ide/media/exploreide-startdebugging.png "ExploreIDE StartDebugging")  
  
    Bir ileti kutusu görüntülenerek IOException hatası oluştuğu belirtilir: 'mainwindow.xaml' kaynağının yeri belirlenemiyor.  
  
2. Seçin **Tamam** düğmesini ve ardından hata ayıklayıcıyı durdurun.  
  
    ![Hata ayıklama menüsünden hata ayıklamayı durdurmak](../ide/media/exploreide-stopdebugging.png "ExploreIDE StopDebugging")  
  
   Biz Mainwindow.xaml bu kılavuzun başındaki Greetings.xaml olarak yeniden adlandırıldı, ancak proje başlatamazsınız kod hala Mainwindow.xaml uygulama ilişkin başlangıç URI olarak başvurur.  
  
##### <a name="to-specify-greetingsxaml-as-the-startup-uri"></a>Başlangıç URI'si olarak Greetings.xaml öğesini belirtmek için  
  
1. İçinde **Çözüm Gezgini**, App.xaml dosyasını (C# projesinde) veya Application.xaml dosyasını (Visual Basic projesinde) XAML görünümünde (açılamaz Tasarım Görünümü'nde) dosyasını seçip Enter tuşuna basarak veya çift açın tıklayarak.  
  
2. Değişiklik `StartupUri="MainWindow.xaml"` için `StartupUri="Greetings.xaml"`ve ardından Ctrl-s ile değişiklikleri kaydedin.  
  
   Hata ayıklayıcıyı yeniden (F5 tuşuna basın) başlatın. Uygulamanın Greetings penceresini görmeniz gerekir.  
  
### <a name="to-debug-with-breakpoints"></a>Kesme noktaları ile hata ayıklamak için  
 Birkaç kesme noktası ekleyerek, hata ayıklama sırasında kodu test edebilirsiniz. Kesme noktaları belirleyerek ekleyebileceğiniz **hata ayıklama** ana menüsündeki, ardından **iki durumlu kesme noktası** veya kesmenin istediğiniz yere sol kenar düzenleyicinin kod satırının yanındaki tıklayarak.  
  
##### <a name="to-add-breakpoints"></a>Kesme noktaları eklemek için  
  
1.  Greetings.xaml.vb veya Greetings.xaml.cs açın ve aşağıdaki satırı seçin: `MessageBox.Show("Hello.")`  
  
2.  Bir kesme noktası menüden seçerek ekleyin **hata ayıklama**, ardından **iki durumlu kesme noktası**.  
  
     ![Kesme noktası komutu hata ayıklama menüsünden geçiş](../ide/media/exploreide-togglebreakpoint.png "ExploreIDE ToggleBreakpoint")  
  
     Düzenleyici penceresinin en sol kenar boşluğunda, kod satırının yanında kırmızı bir daire görünür.  
  
3.  Aşağıdaki satırı seçin: `MessageBox.Show("Goodbye.")`.  
  
4.  Bir kesme noktası eklemek için F9 tuşuna basın ve ardından hata ayıklamayı başlatmak için F5 tuşuna basın.  
  
5.  İçinde **Greetings** penceresinde seçin **Hello** radyo düğmesini ve ardından **görünen** düğmesi.  
  
     Satır `MessageBox.Show("Hello.")` sarı renkle vurgulanır. IDE, Otolar, Yereller ve İzle altındaki windows birlikte sol tarafa yerleşir ve çağrı yığını, kesme noktaları, komut, anlık ve çıkış pencereleri birlikte sağ tarafta yerleşir.  
  
6.  Menü çubuğunda, **hata ayıklama**, **Step Out**.  
  
     Uygulama yürütmeyi devam ettirir ve "Merhaba" sözcüğünü içeren bir ileti kutusu görünür.  
  
7.  Seçin **Tamam** ileti kutusunu kapatmak için düğme.  
  
8.  İçinde **Greetings** penceresinde seçin **güle güle** radyo düğmesini ve ardından **görünen** düğmesi.  
  
     Satır `MessageBox.Show("Goodbye.")` sarı renkle vurgulanır.  
  
9. Hata ayıklamaya devam etmek için F5 tuşuna basın. İleti kutusu göründüğünde **Tamam** ileti kutusunu kapatmak için düğme.  
  
10. SHIFT + F5 tuşlarına basın (basın shift ilk ve F5 tuşuna basın, basılı tutarken) anahtarları hata ayıklamayı durdurmak için.  
  
11. Menü çubuğunda, **hata ayıklama**, **tüm kesme noktalarını devre dışı**.  
  
### <a name="build-a-release-version-of-the-application"></a>Uygulamanın yayın sürümünü oluşturma  
 Her şeyin çalıştığını doğruladığınıza göre artık, uygulamanın bir yayın derlemesini hazırlayabilirsiniz.  
  
##### <a name="to-clean-the-solution-files-and-build-a-release-version"></a>Çözüm dosyalarını temizlemek ve yayın sürümünü oluşturmak için  
  
1. Ana menüden **derleme**, ardından **temiz çözümü** Ara dosyaları ve önceki derlemeler sırasında oluşturulan çıktı dosyalarını silmek için.  Bu gerekli değildir, ancak hata ayıklama derleme çıktılarını ' temizler.  
  
    ![Yapı menüsünde çözümü Temizle komutunu](../ide/media/exploreide-cleansolution.png "ExploreIDE CleanSolution")  
  
2. HelloWPFApp için yapı yapılandırmasını değiştirme **hata ayıklama** için **yayın** (yazacaktır "Debug" şu anda) araç çubuğundaki aşağı açılır denetimden kullanarak.  
  
    ![Standart araç çubuğunda seçilen yayın](../ide/media/exploreide-releaseversion.png "ExploreIDE ReleaseVersion")  
  
3. Çözüm seçerek yapı **derleme**, ardından **Çözümü Derle** veya F6 tuşuna basın.  
  
    ![Derleme çözümü komutu yapı menüsünde](../ide/media/exploreide-buildsolution.png "ExploreIDE BuildSolution")  
  
   Tebrikler, bu izlenecek yolu tamamladınız! Çözüm ve proje dizininiz altında oluşturulan .exe bulabilirsiniz (...\HelloWPFApp\HelloWPFApp\bin\Release\\). Daha fazla örnek keşfetmek isterseniz bkz [Visual Studio örnekleri](../ide/visual-studio-samples.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual Studio 2015'teki yenilikler](../what-s-new-in-visual-studio-2015.md)   
 [Visual Studio ile geliştirmeye başlayın](../ide/get-started-developing-with-visual-studio.md)   
 [Üretkenlik İpuçları](../ide/productivity-tips-for-visual-studio.md)



