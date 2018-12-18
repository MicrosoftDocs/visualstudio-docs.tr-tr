---
title: 'İzlenecek yol: bir uygulama oluşturma | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4842955d-8959-4e4e-98b8-2358360179b3
caps.latest.revision: 10
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: e6c45a552e66c2d256c191f6bd8296f5b2ca2c61
ms.sourcegitcommit: d462dd10746624ad139f1db04edd501e7737d51e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/29/2018
ms.locfileid: "50220215"
---
# <a name="walkthrough-building-an-application"></a>İzlenecek yol: Uygulama Oluşturma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu izlenecek yolu tamamlayarak, Visual Studio ile uygulamalar oluştururken yapılandırabileceğiniz birçok seçeneği daha tanıdık hale gelirler. Özel bir yapı yapılandırması oluşturacak, belirli uyarı iletilerini gizleyecek ve örnek uygulama için diğer görevlere ek yapı çıktı bilgisini artırın.  
  
 Bu konu aşağıdaki bölümleri içermektedir:  
  
 [Örnek uygulamayı yüklemek](../ide/walkthrough-building-an-application.md#BKMK_installapp)  
  
 [Özel bir yapı yapılandırması oluşturma](../ide/walkthrough-building-an-application.md#BKMK_CreateBuildConfig)  
  
 [Uygulamayı oluşturun](../ide/walkthrough-building-an-application.md#BKMK_building)  
  
 [Derleyici uyarılarını Gizle](../ide/walkthrough-building-an-application.md#BKMK_hidewarning)  
  
 [Çıkış penceresinde ek yapı ayrıntılarını görüntüle](../ide/walkthrough-building-an-application.md#BKMK_outputdetails)  
  
 [Yayın derlemesi oluşturma](../ide/walkthrough-building-an-application.md#BKMK_releasebuild)  
  
##  <a name="BKMK_installapp"></a> Örnek uygulamayı yüklemek  
 Kullanacağınız **Uzantılar ve güncelleştirmeler** bulmak ve yüklemek için iletişim kutusu [WPF uygulamalarını oluşturmaya giriş](http://code.msdn.microsoft.com/Introduction-to-Building-b8d16419?SRC=VSIDE) Microsoft Web sitesinde örnekler Galerisi'nden örnek. Örnekler Galerisi çeşitli örnek projeler ve indirip inceleyebileceğiniz planlayın ve uygulamalarınızı geliştirmek kod sağlar.  
  
#### <a name="to-install-the-sample-application"></a>Örnek uygulamayı yüklemek için  
  
1. Menü çubuğunda, **Araçları**, **Uzantılar ve güncelleştirmeler**.  
  
2. Seçin **çevrimiçi** kategori seçip **Örnekler Galerisi** kategorisi.  
  
3. Belirtin `Introduction` örneği bulmak için arama kutusuna.  
  
    ![Uzantılar ve güncelleştirmeler iletişim kutusu](../ide/media/buildwalk-extensionsdialogsampledownload.png "BuildWalk_ExtensionsDialogSampleDownload")  
  
4. Sonuçlar listesinde seçin **WPF uygulamaları oluşturma (Visual C#) giriş** veya **(Visual Basic) WPF uygulamalarını oluşturmaya giriş**.  
  
5. Seçin **indirme** düğmesine ve ardından **Kapat** düğmesi.  
  
   WPF uygulamalarını oluşturmaya giriş görünür **yeni proje** iletişim kutusu.  
  
#### <a name="to-create-a-solution-for-the-sample-application"></a>Örnek uygulama için bir çözüm oluşturmak için  
  
1.  Açık **yeni proje** iletişim kutusu.  
  
     ![Menü çubuğunda, dosya, yeni seçin, proje](../ide/media/exploreide-filenewproject.png "ExploreIDE FileNewProject")  
  
2.  İçinde **yüklü** kategorisi seçin **örnekleri** WPF uygulamalarını oluşturmaya giriş görüntülenecek kategori.  
  
3.  Çözüm adı `IntroWPFcsharp` Visual C# için.  
  
     ![Yeni Proje iletişim kutusu, yüklü örnekleri](../ide/media/buildwalk-newprojectdlgintrotowpfsample.png "BuildWalk_NewProjectdlgIntrotoWPFsample")  
  
     VEYA  
  
     Çözüm adı `IntroWPFvb` Visual Basic için.  
  
     ![Yeni Proje iletişim kutusunda, Visual Basic örnek](../ide/media/buildwalk-newprojectdlgintrotowpfsamplevb.png "BuildWalk_NewProjectdlgIntrotoWPFsampleVB")  
  
4.  Seçin **Tamam** düğmesi.  
  
##  <a name="BKMK_CreateBuildConfig"></a> Özel bir yapı yapılandırması oluşturma  
 Bir çözüm oluşturduğunuzda, hata ayıklama ve yayın derleme yapılandırmaları ve varsayılan platform hedefleri, çözüm için otomatik olarak tanımlanır. Ardından, bu yapılandırmaları özelleştirebilir veya kendinizinkini oluşturun. Derleme yapılandırmaları derleme türünü belirtir. Derleme platformları, bir uygulamanın bu yapılandırma için hedeflediği işletim sistemini belirtin. Daha fazla bilgi için [derleme yapılandırmalarını anlama](../ide/understanding-build-configurations.md), [derleme platformlarını anlama](../ide/understanding-build-platforms.md), ve [hata ayıklama ve dağıtım proje yapılandırmalarını](http://msdn.microsoft.com/en-us/0440b300-0614-4511-901a-105b771b236e).  
  
 Değiştirme veya yapılandırma ve platform Ayarları'nı kullanarak oluşturma **Configuration Manager** iletişim kutusu. Bu yordamda, test etmek için bir yapı yapılandırması oluşturacaksınız.  
  
#### <a name="to-create-a-build-configuration"></a>Bir yapı yapılandırması oluşturmak için  
  
1. Açık **Configuration Manager** iletişim kutusu.  
  
    ![Yapı menüsünde, Configuration Manager komutu](../ide/media/buildwalk-configurationmanagerdialogbox.png "BuildWalk_ConfigurationManagerDialogBox")  
  
2. İçinde **etkin çözüm yapılandırması** listesinde **yeni**.  
  
3. İçinde **yeni çözüm yapılandırması** iletişim kutusunda, yeni yapılandırmayı adı `Test`, varolan hata ayıklama yapılandırmasından ayarları kopyalayın ve ardından **Tamam** düğmesi.  
  
    ![Yeni çözüm yapılandırması iletişim kutusu](../ide/media/buildwalk-newsolutionconfigdlgbox.png "BuildWalk_NewSolutionConfigDlgBox")  
  
4. İçinde **etkin çözüm platformu** listesinde **yeni**.  
  
5. İçinde **yeni çözüm platformu** iletişim kutusunda **x64**ve ayarları x86 kopyalamayın platform.  
  
    ![Yeni çözüm platformu iletişim kutusu](../ide/media/buildwalk-newsolutionplatform.png "BuildWalk_NewSolutionPlatform")  
  
6. Seçin **Tamam** düğmesi.  
  
   Etkin çözüm yapılandırması için Test x64 ayarlama etkin çözüm platformu ile değiştirildi.  
  
   ![Configuration Manager ile Test yapılandırması](../ide/media/buildwalk-configmanagertestconfig.png "BuildWalk_ConfigManagerTestconfig")  
  
   Hızlıca doğrulayabilir veya kullanarak etkin çözüm yapılandırmasını değiştirme **çözüm yapılandırmaları** listesini **standart** araç çubuğu.  
  
   ![Çözümü yapılandırma seçeneği standart araç çubuğu](../ide/media/buildwalk-standardtoolbarsolutioncongfig.png "BuildWalk_StandardToolbarSolutionCongfig")  
  
##  <a name="BKMK_building"></a> Uygulamayı oluşturun  
 Ardından, özel bir yapı yapılandırmasıyla çözümü oluşturacaksınız.  
  
#### <a name="to-build-the-solution"></a>Çözümü derlemek için  
  
- Menü çubuğunda, **derleme**, **Çözümü Derle**.  
  
  **Çıkış** penceresi yapının sonuçlarını görüntüler. Derleme başarılı oldu, ancak birkaç uyarı iletisi oluşturuldu.  
  
  Şekil 1: Visual Basic uyarıları  
  
  ![Çıkış penceresi Visual Basic](../ide/media/buildwalk-vbbuildoutputwnd.png "BuildWalk_VBBuildOutputWnd")  
  
  Şekil 2: Visual C# uyarıları  
  
  ![Çıkış penceresi Visual C&#35;](../ide/media/buildwalk-csharpbuildoutputwnd.png "BuildWalk_CsharpBuildOutputWnd")  
  
##  <a name="BKMK_hidewarning"></a> Derleyici uyarılarını Gizle  
 Geçici olarak bir yapı sırasında belirli uyarı iletilerini gizleyecek yerine, bunları yapı çıktısını karmaşıklığa sahip.  
  
#### <a name="to-hide-a-specific-visual-c-warning"></a>Belirli bir Visual C# uyarısını gizlemek için  
  
1.  İçinde **Çözüm Gezgini**, üst düzey proje düğümünü seçin.  
  
2.  Menü çubuğunda, **görünümü**, **özellik sayfaları**.  
  
     **Proje Tasarımcısı** açılır.  
  
3.  Seçin **derleme** sayfasında, daha sonra **uyarıları bastırma** kutusunda, uyarı numarasını belirtin `1762`.  
  
     ![Derleme sayfası, Proje Tasarımcısı](../ide/media/buildwalk-csharpsuppresswarnings.png "BuildWalk_CsharpSuppressWarnings")  
  
     Daha fazla bilgi için [derleme sayfası, Proje Tasarımcısı (C#)](../ide/reference/build-page-project-designer-csharp.md).  
  
4.  Çözümü oluşturun.  
  
     **Çıkış** penceresi sadece yapı için Özet bilgiler görüntüler.  
  
     ![Çıktı penceresinde, Visual C&#35; uyarılar yapı](../ide/media/buildwalk-visualcsharpbuildwarnings.png "BuildWalk_VisualCsharpBuildWarnings")  
  
#### <a name="to-suppress-all-visual-basic-build-warnings"></a>Tüm Visual Basic derleme uyarılarını bastırmak için  
  
1. İçinde **Çözüm Gezgini**, üst düzey proje düğümünü seçin.  
  
2. Menü çubuğunda, **görünümü**, **özellik sayfaları**.  
  
    **Proje Tasarımcısı** açılır.  
  
3. Üzerinde **derleme** sayfasında **tüm uyarıları devre dışı bırak** onay kutusu.  
  
    ![Derleme sayfası, Proje Tasarımcısı](../ide/media/buildwalk-vbsuppresswarnings.png "BuildWalk_VBSuppressWarnings")  
  
    Daha fazla bilgi için [Visual Basic'teki uyarıları yapılandırma](../ide/configuring-warnings-in-visual-basic.md).  
  
4. Çözümü oluşturun.  
  
   **Çıkış** penceresi sadece yapı için Özet bilgiler görüntüler.  
  
   ![Çıktı penceresinde, Visual Basic derleme uyarılarını](../ide/media/buildwalk-visualbasicbuildwarnings.png "BuildWalk_VisualBasicBuildWarnings")  
  
   Daha fazla bilgi için [nasıl yapılır: Derleyici uyarılarını Gizle](../ide/how-to-suppress-compiler-warnings.md).  
  
##  <a name="BKMK_outputdetails"></a> Çıkış penceresinde ek yapı ayrıntılarını görüntüle  
 Yapı işlemi hakkında ne kadar bilgi gözükeceğini değiştirebilirsiniz **çıkış** penceresi. Derleme ayrıntısı genellikle Minimal olarak ayarlanır, yani **çıkış** penceresi yalnızca yüksek öncelikli uyarıları veya hataları yanı sıra yapı işleminin bir özetini görüntüler. Kullanarak yapı hakkında daha fazla bilgi görüntüleyebilirsiniz [Seçenekler iletişim kutusu, projeler ve çözümler, derleme ve çalıştırma](../ide/reference/options-dialog-box-projects-and-solutions-build-and-run.md).  
  
> [!IMPORTANT]
>  Daha fazla bilgi görüntülüyorsanız yapının tamamlanması uzun sürer.  
  
#### <a name="to-change-the-amount-of-information-in-the-output-window"></a>Çıkış penceresinde bilgi miktarını değiştirmek için  
  
1. Açık **seçenekleri** iletişim kutusu.  
  
    ![Komut Araçlar menüsünde Seçenekler](../ide/media/exploreide-toolsoptionsmenu.png "ExploreIDE ToolsOptionsmenu")  
  
2. Seçin **projeler ve çözümler** kategori seçip **derleme ve çalıştırma** sayfası.  
  
3. İçinde **MSBuild proje oluşturması çıkış ayrıntısı** listesinde **Normal**ve ardından **Tamam** düğmesi.  
  
4. Menü çubuğunda, **derleme**, **çözümü Temizle**.  
  
5. Çözüm oluşturun ve sonra bilgileri gözden **çıkış** penceresi.  
  
    Derleme bilgileri, hangi dosyaların sırayla işlendi (başında yer) derleme başlatıldı, zaman ve (sondadır) işlemin tamamlanması için geçen süreyi içerir. Bu bilgiler ayrıca, Visual Studio'nun yapı sırasında çalıştırdığı gerçek derleyici sözdizimini de içerir.  
  
    Örneğin, Visual C# derlemesinde içinde [/nowarn](http://msdn.microsoft.com/library/7ebf2106-0652-4fdc-bf60-70fc86465d83) seçeneği, diğer üç uyarıyla birlikte bu konu içinde daha önce belirttiğiniz 1762 uyarı kodunu listeler.  
  
    Visual Basic derleme [/nowarn](http://msdn.microsoft.com/library/7ebf2106-0652-4fdc-bf60-70fc86465d83) hiçbir uyarı görüntülenmez şekilde dışlanacak belirli uyarıları içermez.  
  
   > [!TIP]
   >  İçeriğini arayabilirsiniz **çıkış** görüntülerseniz penceresi **Bul** Ctrl + F tuşlarını seçerek iletişim kutusu.  
  
   Daha fazla bilgi için bkz. [nasıl yapılır: görünümü, kaydetme ve yapılandırma derleme günlük dosyalarını](../ide/how-to-view-save-and-configure-build-log-files.md).  
  
##  <a name="BKMK_releasebuild"></a> Yayın derlemesi oluşturma  
 Sevkiyat için optimize edilmiş örnek uygulamanın bir sürümünü oluşturabilirsiniz. Sürüm yapısı için yapı başlatılmadan önce çalıştırılabilir bir ağ paylaşımına kopyalandığını belirteceksiniz.  
  
 Daha fazla bilgi için [nasıl yapılır: Derleme çıktı dizinini değiştirme](../ide/how-to-change-the-build-output-directory.md) ve [oluşturma ve temizleme projeler ve çözümler Visual Studio'da](../ide/building-and-cleaning-projects-and-solutions-in-visual-studio.md).  
  
#### <a name="to-specify-a-release-build-for-visual-basic"></a>Visual Basic için bir yayın yapısı belirtmek için  
  
1.  Açık **Proje Tasarımcısı**.  
  
     ![Görünüm menüsü, özellik sayfaları komutu](../ide/media/buildwalk-viewpropertypages.png "BuildWalk_ViewPropertyPages")  
  
2.  Seçin **derleme** sayfası.  
  
3.  İçinde **yapılandırma** listesinde **yayın**.  
  
4.  İçinde **Platform** listesinde **x86**.  
  
5.  İçinde **yapı çıkış yolu** kutusunda, bir ağ yolu belirtin.  
  
     Örneğin, belirtebilirsiniz \\\myserver\builds.  
  
    > [!IMPORTANT]
    >  Belirttiğiniz ağ paylaşımı güvenilir olmayabilir sizi uyaran bir ileti kutusu görünebilir. Belirttiğiniz konuma güveniyorsanız seçin **Tamam** ileti kutusunda düğmesi.  
  
6.  Uygulamayı oluşturun.  
  
     ![Derleme çözümü komutu yapı menüsünde](../ide/media/exploreide-buildsolution.png "ExploreIDE BuildSolution")  
  
#### <a name="to-specify-a-release-build-for-visual-c"></a>Visual C# için bir yayın yapısı belirtmek için  
  
1. Açık **Proje Tasarımcısı**.  
  
    ![Görünüm menüsü, özellik sayfaları komutu](../ide/media/buildwalk-viewpropertypages.png "BuildWalk_ViewPropertyPages")  
  
2. Seçin **derleme** sayfası.  
  
3. İçinde **yapılandırma** listesinde **yayın**.  
  
4. İçinde **Platform** listesinde **x86**.  
  
5. İçinde **çıkış yolu** kutusunda, bir ağ yolu belirtin.  
  
    Örneğin, belirtebilirsiniz \\\myserver\builds.  
  
   > [!IMPORTANT]
   >  Belirttiğiniz ağ paylaşımı güvenilir olmayabilir sizi uyaran bir ileti kutusu görünebilir. Belirttiğiniz konuma güveniyorsanız seçin **Tamam** ileti kutusunda düğmesi.  
  
6. Uygulamayı oluşturun.  
  
    ![Derleme çözümü komutu yapı menüsünde](../ide/media/exploreide-buildsolution.png "ExploreIDE BuildSolution")  
  
   Yürütülebilir dosya, belirttiğiniz ağ yoluna kopyalanır. Kendi yol \\\myserver\builds\\*FileName*.exe.  
  
   Tebrikler: Bu kılavuzda başarıyla tamamladınız.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [İzlenecek yol: bir proje derleme (C++)](http://msdn.microsoft.com/library/d459bc03-88ef-48d0-9f9a-82d17f0b6a4d)   
 [ASP.NET Web uygulaması projesi ön derleme genel bakış](http://msdn.microsoft.com/en-us/b940abbd-178d-4570-b441-52914fa7b887)   
 [İzlenecek Yol: MSBuild Kullanma](../msbuild/walkthrough-using-msbuild.md)



