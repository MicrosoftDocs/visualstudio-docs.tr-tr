---
title: 'İzlenecek yol: temel bir oluşturma yalıtılmış Kabuk uygulaması | Microsoft Docs'
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
- Visual Studio shell, walkthroughs
- Shell [Visual Studio], walkthroughs
- walkthroughs [Visual Studio], isolated shell-based application
ms.assetid: 8b12e223-aae3-4c23-813d-ede1125f5f69
caps.latest.revision: 55
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 901bbf12c9c1d153b84b3ed74f6ae8e97ebb2c9b
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51777324"
---
# <a name="walkthrough-creating-a-basic-isolated-shell-application"></a>İzlenecek yol: temel yalıtılmış Kabuk uygulaması oluşturma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu izlenecek yol, yalıtılmış Kabuk çözümünü oluşturun, Yardım konusu araç penceresi özelleştirme ve yalıtılmış Kabuk yükleyen bir Kurulum programı oluşturma işlemi gösterilmektedir.  
  
## <a name="prerequisites"></a>Önkoşullar  
 Bu izlenecek yolda takip etmek için Visual Studio SDK'yı yüklemeniz gerekir. Daha fazla bilgi için [Visual Studio SDK](../extensibility/visual-studio-sdk.md). Yalıtılmış Kabuğu dağıtmak için Visual Studio Kabuğu (yalıtılmış) yeniden dağıtılabilir paketi kullanmanız gerekir.  
  
## <a name="creating-an-isolated-shell-solution"></a>Bir yalıtılmış Kabuk çözümü oluşturma  
 Bu bölümde, yalıtılmış Kabuk çözümünü oluşturmak için Visual Studio Kabuğu yalıtılmış proje şablonu kullanmayı gösterir. Çözüm, aşağıdaki projeler içeriyor:  
  
-   *SolutionName*. AboutBoxPackage proje Yardım/hakkında kutusu görünümünü özelleştirmenize olanak sağlar.  
  
-   Yalıtılmış Kabuk uygulaması farklı bileşenleri tanımlayan source.extension.vsixmanifest dosyasını içeren ShellExtensionsVSIX projesi.  
  
-   *SolutionName* yalıtılmış Kabuk uygulaması çağıran yürütülebilir dosya üreten bir proje. Bu proje, özelleşt görünümünü ve davranışını yalıtılmış Kabuk uygulaması sağlayan Kabuğu özelleştirme klasör içerir.  
  
-   *SolutionName* etkin menü komutları ve yerelleştirilebilir dize tanımlayan bir uydu derleme oluşturan UI projesi.  
  
#### <a name="to-create-a-basic-isolated-shell-solution"></a>Temel yalıtılmış Kabuk çözüm oluşturmak için  
  
1.  Visual Studio'yu açın ve yeni bir proje oluşturun.  
  
2.  İçinde **yeni proje** penceresini genişletin **diğer proje türleri** ardından **genişletilebilirlik**. Seçin **Visual Studio Kabuğu yalıtılmış** proje şablonu.  
  
3.  Projeyi adlandırın `MyVSShellStub` ve konumu belirtin. Emin olun **çözüm için dizin oluştur** denetlenir ve ardından **Tamam**.  
  
     Yeni çözüm görünür **Çözüm Gezgini**.  
  
4.  Çözümü derleyin ve yalıtılmış Kabuk uygulaması hata ayıklamaya başlayın.  
  
     Visual Studio yalıtılmış Kabuğu görüntülenir. Başlık çubuğunda okur **MyVSShellStub**. Başlık çubuğu simgesi \MyVSShellStub\Resource Files\ApplicationIcon.ico oluşturulur.  
  
## <a name="customizing-the-application-name-and-icon"></a>Uygulama adını ve simgesini özelleştirme  
 Başlık çubuğunda şirketiniz ve kendi logosu adını kullanarak uygulamanızı marka isteyebilirsiniz. Aşağıdaki adımlar, adı ve paket tanımı dosyası MyVSShellStub.Application.pkgdef değiştirerek özel uygulama başlık çubuğunda görüntülenecek simge nasıl değiştirileceğini gösterir.  
  
#### <a name="to-customize-the-application-name-and-icon"></a>Uygulama adı ve simgesi özelleştirmek için  
  
1.  MyVSShellStub projesinde \Shell Customization\MyVSShellStub.Application.pkgdef açın.  
  
2.  Değişiklik `AppName` öğe değeri **"AppName" = "Fabrikam müzik Editor"**  
  
3.  Uygulama simgesi değiştirmek için farklı bir simgeye \MyVSShellStub\MyVSShellStub\MyVSShellStub\ dizinine kopyalayın. Mevcut ApplicationIcon.ico dosyayı ApplicationIcon1.ico için yeniden adlandırın. Yeni dosya için ApplicationIcon.ico yeniden adlandırın.  
  
4.  Çözümü derleyin ve hata ayıklamaya başlayın. Yalıtılmış Kabuğu IDE görünür. Başlık çubuğunda sözcükleri yanında, yeni simgesine sahip **Fabrikam müzik Düzenleyicisi**.  
  
## <a name="customizing-the-default-web-browser-home-page"></a>Varsayılan Web tarayıcısı giriş sayfasını özelleştirme  
 Bu bölümde, varsayılan giriş sayfası değiştirmek gösterilmektedir **Web tarayıcısı** paket tanımlama dosyasını değiştirerek penceresi.  
  
#### <a name="to-customize-the-default-web-browser-home-page"></a>Varsayılan Web tarayıcısı giriş sayfasını özelleştirme  
  
1. MyVSShellStub.Application.pkgdef dosyasında değiştirmek `DefaultHomePage` öğesi değeri "<http://www.microsoft.com>".  
  
2. MyVSShellStub projeyi yeniden derleyin.  
  
3. Çözümü derleyin ve hata ayıklamaya başlayın.  
  
4. İçinde **görünüm / diğer Windows**, tıklayın **Web tarayıcısı**. **Web tarayıcısı** penceresi Microsoft Corporation'ın ana sayfası görüntüler.  
  
## <a name="removing-the-print-command"></a>Yazdır komutu kaldırılıyor  
 Yalıtılmış Kabuk UI projesinde .vsct dosyası biçiminde bildirimlerinin kümesinden oluşur `<Define name=No_` *öğesi*`>`burada *öğesi* standart Visual Studio menülerinin biridir ve komutları.  
  
 Bir bildirimi açıklamalı olmayan ise, o menüsünden veya komut yalıtılmış Kabuğu'ndan çıkarılır. Buna karşılık, bir bildirimi geçersiz kılınan, menü veya komut yalıtılmış Kabuğu'nda bulunur.  
  
 Aşağıdaki adımlarda, yazdırma komut .vsct dosyanızda açıklamasını kaldırın.  
  
#### <a name="to-remove-the-print-command"></a>Yazdır komutu kaldırmak için  
  
1.  Doğrulayın **yazdırma** komut görünür **dosya** yalıtılmış Kabuk uygulaması menüsünde.  
  
2.  MyVSShellStubUI projesinde \Resource Files\MyVSShellStubUI.vsct düzenleme için açın.  
  
3.  Bu satırı açıklamadan çıkarın:  
  
    ```  
    <!-- <Define name="No_PrintChildrenCommand"/> -->  
    ```  
  
4.  Bu, yazdırma komutu kaldırır.  
  
5.  Yalıtılmış Kabuk uygulaması hatalarını ayıklamaya başlayın. Doğrulayın **dosya / yazdırma** komuttur kayboldu.  
  
## <a name="removing-features-from-the-isolated-shell"></a>Yalıtılmış Kabuğu'ndan özellikleri kaldırma  
 Bazı özel yalıtılmış Kabuk uygulamanızda bu özellikleri istemiyorsanız .pkgundef dosyası düzenleyerek Visual Studio ile yüklenen paketler kaldırabilir. Paketi $RootKey$ \Packages kayıt defteri anahtarının alt anahtarlarından birini belirtin.  
  
> [!NOTE]
>  Visual Studio GUID'leri özellikleri bulmak için bkz: [paket GUID'leri, Visual Studio özellikleri](../extensibility/package-guids-of-visual-studio-features.md).  
  
 Aşağıdaki yordam, yalıtılmış Kabuk düzenleyicisinden XML kaldırma gösterir.  
  
#### <a name="to-remove-the-xml-editor"></a>XML Düzenleyicisi'ni kaldırmak için  
  
1.  MyVSShellStub projenin Kabuğu özelleştirme klasöründeki MyVSShellStub.pkgundef dosyasını açın.  
  
2.  Aşağıdaki satırı açıklamadan çıkarın:  
  
     [$RootKey$ \Packages\\{87569308-4813-40a0-9cd0-d7a30838ca3f}]  
  
3.  Çözümü yeniden oluşturun ve yalıtılmış Kabuk hata ayıklamaya başlayın. Örneğin, \MyVSShellStub\MyVSShellStub\MyVSShellStubUI\MyVSShellStubUI.vsct bir XML dosyasını açın. XML dosyasındaki anahtar sözcükleri yok renklendirilmiş doğrulayın ve söz konusu yazarak "<" bir satıra XML tooltips neden olmaz.  
  
## <a name="customizing-the-helpabout-box"></a>Özelleştirme Yardım/hakkında kutusu  
 Özelleştirebileceğiniz Yardım/hakkında kutusu, yalıtılmış Kabuk proje şablonunun bir parçası oluşturulur.  
  
#### <a name="to-customize-the-company-name"></a>Şirket adı özelleştirmek için  
  
1.  Şirket adı, telif hakkı bilgileri, ürün sürümü ve ürün açıklaması MyVSShellStub.AboutBoxPackage projesinde \Properties\AssemblyInfo.cs dosyasında bulunamadı. Bu dosyayı açın.  
  
2.  Değişiklik `AssemblyCompany` değerini **Fabrikam**, `AssemblyProduct` ve `AssemblyTitle` değerler **Fabrikam müzik Düzenleyicisi**ve `AssemblyCopyright` değerini **telif hakkı © Fabrikam 2015**:  
  
    ```  
    [assembly: AssemblyTitle("Fabrikam Music Editor")]  
    [assembly: AssemblyDescription("")]  
    [assembly: AssemblyConfiguration("")]  
    [assembly: AssemblyCompany("Fabrikam")]  
    [assembly: AssemblyProduct("Fabrikam Music Editor")]  
    [assembly: AssemblyCopyright("Copyright © Fabrikam 2015")] [assembly: AssemblyCompany("Fabrikam")]  
    [assembly: AssemblyProduct("Fabrikam Music Editor ")]  
    [assembly: AssemblyCopyright("Copyright © Fabrikam 2015”)]  
    ```  
  
3.  Ürün açıklamasını eklemek, değiştirmek `AssemblyDescription` değerini **Fabrikam müzik Düzenleyicisi açıklaması.**:  
  
    ```  
    [assembly: AssemblyDescription("The description of Fabrikam Music editor.”)]  
    ```  
  
4.  Yalıtılmış Kabuk uygulaması içinde açın ve hata ayıklamayı Başlat **Yardım / hakkında** kutusu. Değiştirilen dizelerin görmeniz gerekir. Yardım/hakkında kutusu başlığı aynıdır `AssemblyTitle` AssemblyInfo.cs değeri.  
  
5.  Özelliklerini **Yardım/hakkında** kendisi MyVSShellStub.AboutBoxPackage\AboutBox.xaml dosyasında bulunur. Yardım/hakkında kutusu genişliği değiştirmek için Git `AboutDialogStyle` engelleme ve ayarlama `Width` 200 özelliği:  
  
    ```  
    <Style x:Key="AboutDialogStyle" TargetType="Window">  
        <Setter Property="Height" Value="Auto" />  
        <Setter Property="Width" Value="200" />  
        <Setter Property="ShowInTaskbar" Value="False" />  
        <Setter Property="ResizeMode" Value="NoResize" />  
        <Setter Property="WindowStyle" Value="SingleBorderWindow" />  
        <Setter Property="SizeToContent" Value="Height" />  
    </Style>  
    ```  
  
6.  Çözümü yeniden oluşturun ve yalıtılmış Kabuk hata ayıklamaya başlayın. Yardım/hakkında kutusu yaklaşık kare olmalıdır.  
  
## <a name="before-you-deploy-the-isolated-shell-application"></a>Yalıtılmış Kabuk uygulaması dağıtmadan önce  
 Visual Studio Kabuğu (yalıtılmış) yeniden dağıtılabilir paketi olan herhangi bir bilgisayarda, yalıtılmış Kabuk uygulaması yüklenebilir. Yeniden dağıtılabilir paketi hakkında daha fazla bilgi için bkz: [Visual Studio genişletilebilirlik indirmeleri](http://go.microsoft.com/fwlink/?LinkID=119298) Web sitesi.  
  
## <a name="deploying-the-isolated-shell-application"></a>Yalıtılmış Kabuk uygulaması dağıtma  
 Bir hedef bilgisayara, yalıtılmış Kabuk uygulaması, bir kurulum projesi oluşturarak dağıtın. Bunları belirtmeniz gerekir:  
  
- Hedef bilgisayarda dosya ve klasörleri düzeni.  
  
- Hedef bilgisayarda yüklü çalışma zamanı .NET Framework ve Visual Studio Kabuğu garanti başlatma koşulları.  
  
  Aşağıdaki yordamda InstallShield Limited Edition'ı bilgisayarınıza yüklemeniz gerekir.  
  
#### <a name="to-create-the-setup-project"></a>Kurulum projesi oluşturmak için  
  
1. İçinde **Çözüm Gezgini**, çözüm düğümüne sağ tıklayın ve ardından **Yeni Proje Ekle**.  
  
2. İçinde **yeni proje** iletişim kutusunda **diğer proje türleri** seçip **Kurulum ve dağıtım**. InstallShield şablonu seçin. Yeni proje adını `MySetup` ve ardından **Tamam**.  
  
3. InstallShield Limited Edition'ı zaten yüklediyseniz, sonraki adıma devam edin.  
  
    InstallShield Limited Edition zaten yüklü değilse InstallShield karşıdan yükleme sayfası görüntülenir. İndirip Visual Studio sürümünüzle uyumlu InstallShield sürümünü seçerek bu ürünü yüklemek için yönergeleri izleyin. InstallShield yüklemenizin kaydetmek veya değerlendirme sürümü kullanmak karar vermeniz gerekir. Yüklemeyi tamamladıktan sonra Visual Studio'yu yeniden başlatmanız gerekir.  
  
   > [!IMPORTANT]
   >  InstallShield projesi oluşturmadan önce Visual Studio'yu yönetici olarak başlatmanız gerekir. Bunu yaparsanız projeyi oluşturduğunuzda bir hata alırsınız.  
  
   Sonraki adımlar, Kurulum projesini yapılandırma gösterilmektedir.  
  
> [!IMPORTANT]
>  Kurulum projesi yapılandırmadan önce en az bir kez sürüm yapılandırmasını yalıtılmış Kabuk projenizin oluşturduğunuzdan emin olun.  
  
#### <a name="to-configure-the-setup-project"></a>Kurulum projesi yapılandırmak için  
  
1.  İçinde **Çözüm Gezgini**altında **MySetup** projesinin **proje Yardımcısı**. En alttaki **proje Yardımcısı** penceresinde seçin **uygulama bilgilerini**. Girin **Fabrikam** şirket adınızı olarak ve **Fabrikam müzik Düzenleyicisi** olarak uygulamanızın adı. Sağ alt köşesindeki ileri oku seçin **proje Yardımcısı**.  
  
2.  Seçin **Evet** altında **uygulamanızı herhangi bir yazılımı makinede yüklü olmasını gerektiriyor mu?** seçip **Microsoft .NET Framework 4.5 tam paket**.  
  
3.  Seçin **uygulama dosyaları** düğmesini pencerenin alt kısmında ve emin olun **Fabrikam müzik Düzenleyicisi** klasör seçili.  
  
4.  Seçin **Add Files** düğmesi. İçinde **Add Files** iletişim kutusunda, aşağıdaki dosyaları ekleyin **MyVSShellStub\Release** klasörü:  
  
    1.  MyVSShellStub.exe.config  
  
    2.  DebuggerProxy.dll  
  
    3.  DebuggerProxy.dll.manifest  
  
    4.  MyVSShellStub.pkgdef  
  
    5.  MyVSShellStub.pkgundef  
  
    6.  MyVSShellStub.winprf  
  
    7.  Splash.bmp  
  
5.  Tıklayın **proje çıktıları Ekle** düğmesine tıklayın ve Ekle **MyVSShellStub/birincil çıkış**. **Tamam**'ı tıklatın.  
  
6.  Sol bölmede altında **hedef bilgisayar**, sağ tıklayın **Fabrikam müzik Düzenleyicisi [INSTALLDIR]** düğüm ekleyin bir **yeni klasör** adlı **uzantıları** .  
  
7.  Sağ **uzantıları** sol bölmedeki düğüm ve adlı yeni bir klasör eklemek **uygulama**.  
  
8.  Seçin **uygulama** klasörü ve tıklatın **proje çıktıları Ekle** düğmesine ve ardından birincil çıkışının MyVSShellStub.AboutBoxPackage projeden seçin.  
  
9. Tıklayın **Add Files** düğmesi ve \MyVSShellStub\Release\Extensions\Application\ klasöründen aşağıdaki dosyaları ekleyin:  
  
    -   MyVSShellStub.AboutBoxPackage.pkgdef  
  
    -   MyVSShellStub.Application.pkgdef  
  
10. Sağ **Fabrikam müzik Düzenleyicisi [INSTALLDIR]** sol bölmedeki düğüm ve adlı yeni bir klasör eklemek **1033**.  
  
11. 1033 klasörü seçin ve ardından **proje çıktıları Ekle** düğmesini ve MyVSShellStubUI projenin birincil çıkışının seçin.  
  
12. Taşı **uygulama kısayolları** penceresi.  
  
13. Tıklayın **yeni** bir kısayol oluşturun ve seçin için **[ProgramFilesFolder] \Fabrikam\Fabrikam Music Editor\MyVSShellStub.Primary Output**.  
  
14. Taşı **Kurulum Mülakatı** bölmesi.  
  
15. Tüm öğeleri kümesine **Hayır**.  
  
16. İçinde **Çözüm Gezgini**, MySetup projeyi **Kurulum gereksinimlerini tanımlayın ve eylemleri \ gereksinimleri**. **Gereksinimleri** penceresi açılır.  
  
17. Sağ tıklayın **sistem yazılım gereksinimleri** seçip **yeni başlatma koşulu oluşturma**. **Sistem Arama Sihirbazı'nı** görünür.  
  
18. İçinde **ne bulmak istediğiniz?** bölmesinde seçin **kayıt defteri girdisini** açılır listede tıklayıp **sonraki**.  
  
19. İçinde **nasıl aramanız istiyorsunuz?** bölmesinde **HKEY_LOCAL_MACHINE** kayıt defteri kökü. Girin **SOFTWARE\Wow6432Node\Microsoft\DevDiv\vs\Servicing\14.0\isoshell** 64-bit sistemler için veya **SOFTWARE\Microsoft\DevDiv\vs\Servicing\14.0\isoshell** 32-bit sistemler için girin **Yükleme** kayıt defteri değeri. **İleri**'ye tıklayın.  
  
20. İçinde **ne değeriyle yapmak istiyor musunuz?** bölmesinde girin **bu ürünün Visual Studio 2015 yalıtılmış Kabuk yüklenmesi yeniden dağıtılabilir gerektirir.** ' a tıklayın ve görünen metin olarak **son**.  
  
21. Kurulum projesi oluşturmak için yalıtılmış Kabuk çözümü yeniden oluşturun.  
  
     Setup.exe dosyasını aşağıdaki klasörde bulabilirsiniz:  
  
     \MyVSShellStub\MySetup\MySetup\Express\SingleImage\DiskImages\DISK1  
  
## <a name="testing-the-installation-program"></a>Yükleme programını test etme  
 Test kurulumu için setup.exe dosyasını farklı bir bilgisayara kopyalayın ve kurulum yürütülebilir dosyayı çalıştırmak. Yalıtılmış Kabuk uygulaması çalıştırın olması gerekir.

