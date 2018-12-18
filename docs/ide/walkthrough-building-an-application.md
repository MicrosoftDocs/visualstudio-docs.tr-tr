---
title: 'İzlenecek yol: Uygulama oluşturma'
ms.date: 09/25/2017
ms.prod: visual-studio-dev15
ms.technology: vs-ide-compile
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 2987df6c8ed8a26c2cf95020e26f67c36721d676
ms.sourcegitcommit: be938c7ecd756a11c9de3e6019a490d0e52b4190
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50672788"
---
# <a name="walkthrough-build-an-application"></a>İzlenecek yol: Uygulama oluşturma

Bu izlenecek yolu tamamlayarak, Visual Studio ile uygulamalar oluştururken yapılandırabileceğiniz birçok seçeneği daha tanıdık hale gelirler. Özel bir yapı yapılandırması oluşturacak, belirli uyarı iletilerini gizleyecek ve örnek uygulama için yapı çıktı bilgisini artırın.

## <a name="install-the-sample-application"></a>Örnek uygulamayı yüklemek

İndirme [WPF uygulamalarını oluşturmaya giriş](https://code.msdn.microsoft.com/Introduction-to-Building-b8d16419) örnek. Seçin ya da C# veya Visual Basic. Sonra *.zip* dosyasını indirdiğiniz, ayıklayın ve açık *ExpenseItIntro.sln* Visual Studio kullanarak dosya.

## <a name="create-a-custom-build-configuration"></a>Özel bir yapı yapılandırması oluşturma

Bir çözüm oluşturduğunuzda, hata ayıklama ve yayın derleme yapılandırmaları ve varsayılan platform hedefleri, çözüm için otomatik olarak tanımlanır. Ardından, bu yapılandırmaları özelleştirebilir veya kendinizinkini oluşturun. Derleme yapılandırmaları derleme türünü belirtir. Derleme platformları, bir uygulamanın bu yapılandırma için hedeflediği işletim sistemini belirtin. Daha fazla bilgi için bkz. [anlayın derleme yapılandırmaları](../ide/understanding-build-configurations.md), [derleme platformlarını anlama](../ide/understanding-build-platforms.md), ve [nasıl yapılır: ayarlama hata ayıklama ve dağıtım yapılandırmalarını](../debugger/how-to-set-debug-and-release-configurations.md).

Değiştirme veya yapılandırma ve platform Ayarları'nı kullanarak oluşturma **Configuration Manager** iletişim kutusu. Bu yordamda, test etmek için bir yapı yapılandırması oluşturacaksınız.

### <a name="create-a-build-configuration"></a>Bir yapı yapılandırması oluşturma

1. Açık **Configuration Manager** iletişim kutusu.

   ![Menüsü, Configuration Manager komutu oluşturun](../ide/media/buildwalk_configurationmanagerdialogbox.png)

1. İçinde **etkin çözüm yapılandırması** listesinde  **\<yeni... \>**.

1. İçinde **yeni çözüm yapılandırması** iletişim kutusunda, yeni yapılandırmayı adı `Test`, kopya ayarlarını varolan **hata ayıklama** yapılandırma ve ardından **Tamam**düğmesi.

   ![Yeni çözüm yapılandırması iletişim kutusu](../ide/media/buildwalk_newsolutionconfigdlgbox.png)

1. İçinde **etkin çözüm platformu** listesinde  **\<yeni... \>**.

1. İçinde **yeni çözüm platformu** iletişim kutusunda **x64**ve ayarları x86 kopyalamayın platform.

   ![Yeni çözüm platformu iletişim kutusu](../ide/media/buildwalk_newsolutionplatform.png)

1. Seçin **Tamam** düğmesi.

   Etkin çözüm yapılandırması değiştirildi **Test** etkin çözüm platformuyla x64 ayarlayın.

   ![Configuration Manager ile Test yapılandırması](../ide/media/buildwalk_configmanagertestconfig.png)

1. Seçin **Kapat**.

Hızlıca doğrulayabilir veya kullanarak etkin çözüm yapılandırmasını değiştirme **çözüm yapılandırmaları** listesini **standart** araç çubuğu.

![Çözümü yapılandırma seçeneği standart araç çubuğu](../ide/media/buildwalk_standardtoolbarsolutioncongfig.png)

## <a name="build-the-application"></a>Uygulama oluşturma

Ardından, özel bir yapı yapılandırmasıyla çözümü oluşturacaksınız.

### <a name="build-the-solution"></a>Çözümü derleyin

-   Menü çubuğunda, **derleme** > **Çözümü Derle**.

    **Çıkış** penceresi yapının sonuçlarını görüntüler. Derleme başarılı oldu.

## <a name="hide-compiler-warnings"></a>Derleyici uyarılarını Gizle

Sonraki biz derleyici tarafından oluşturulacak bir uyarı neden olan bazı kod tanıtacağız.

1. İçinde C# projesini açarsanız *ExpenseReportPage.xaml.cs* dosya. İçinde **ExpenseReportPage** yöntemine aşağıdaki kodu ekleyin: `int i;`.

    VEYA

    Visual Basic projesinde açın *ExpenseReportPage.xaml.vb* dosya. Özel oluşturucu içinde **Public Sub New...** , aşağıdaki kodu ekleyin: `Dim i`.

1. Çözümü oluşturun.

**Çıkış** penceresi yapının sonuçlarını görüntüler. Derleme başarılı oldu ancak uyarılar oluşturuldu:

![Çıkış penceresi Visual Basic](../ide/media/buildwalk_vbbuildoutputwnd.png)

![Çıkış penceresi Visual C&#35;](../ide/media/buildwalk_csharpbuildoutputwnd.png)

Geçici olarak bir yapı sırasında belirli uyarı iletilerini gizleyecek yerine, bunları yapı çıktısını karmaşıklığa sahip.

### <a name="hide-a-specific-c-warning"></a>Belirli bir gizleme C# Uyarısı

1. İçinde **Çözüm Gezgini**, üst düzey proje düğümünü seçin.

1. Menü çubuğunda, **görünümü** > **özellik sayfaları**.

     **Proje Tasarımcısı** açılır.

1. Seçin **derleme** sayfasında, daha sonra **uyarıları bastırma** kutusunda, uyarı numarasını belirtin **0168**.

     ![Derleme sayfası, Proje Tasarımcısı](../ide/media/buildwalk_csharpsuppresswarnings.png)

     Daha fazla bilgi için [derleme sayfası, Proje Tasarımcısı (C#)](../ide/reference/build-page-project-designer-csharp.md).

1. Çözümü oluşturun.

     **Çıkış** penceresi sadece yapı için Özet bilgiler görüntüler.

     ![Çıktı penceresinde, Visual C&#35; uyarılar oluşturun](../ide/media/buildwalk_visualcsharpbuildwarnings.png)

### <a name="suppress-all-visual-basic-build-warnings"></a>Tüm Visual Basic derleme uyarılarını bastırmak

1. İçinde **Çözüm Gezgini**, üst düzey proje düğümünü seçin.

2. Menü çubuğunda, **görünümü** > **özellik sayfaları**.

     **Proje Tasarımcısı** açılır.

3. Üzerinde **derleme** sayfasında **tüm uyarıları devre dışı bırak** onay kutusu.

     ![Derleme sayfası, Proje Tasarımcısı](../ide/media/buildwalk_vbsuppresswarnings.png)

     Daha fazla bilgi için [Visual Basic ile uyarıları yapılandırma](../ide/configuring-warnings-in-visual-basic.md).

4. Çözümü oluşturun.

   **Çıkış** penceresi sadece yapı için Özet bilgiler görüntüler.

   ![Çıktı penceresinde, Visual Basic uyarıları oluşturma](../ide/media/buildwalk_visualbasicbuildwarnings.png)

   Daha fazla bilgi için [nasıl yapılır: Derleyici uyarılarını gizleme](../ide/how-to-suppress-compiler-warnings.md).

## <a name="display-additional-build-details-in-the-output-window"></a>Görüntü ek yapı çıktı penceresinde ayrıntıları

Yapı işlemi hakkında ne kadar bilgi gözükeceğini değiştirebilirsiniz **çıkış** penceresi. Derleme ayrıntısı genellikle ayarlandığında **Minimal**, anlamına **çıkış** penceresi yalnızca yüksek öncelikli uyarıları veya hataları yanı sıra yapı işleminin bir özetini görüntüler. Kullanarak yapı hakkında daha fazla bilgi görüntüleyebilirsiniz [Seçenekler iletişim kutusu, projeler ve çözümler, derleme ve çalıştırma](../ide/reference/options-dialog-box-projects-and-solutions-build-and-run.md).

> [!IMPORTANT]
> Daha fazla bilgi görüntülüyorsanız yapının tamamlanması uzun sürer.

### <a name="change-the-amount-of-information-in-the-output-window"></a>Çıkış penceresinde bilgi miktarını değiştirmek

1. Açık **seçenekleri** iletişim kutusu.

     ![Araçlar menüsünde Seçenekler komutu](../ide/media/exploreide-toolsoptionsmenu.png)

1. Seçin **projeler ve çözümler** kategori seçip **derleme ve çalıştırma** sayfası.

1. İçinde **MSBuild proje oluşturması çıkış ayrıntısı** listesinde **Normal**ve ardından **Tamam** düğmesi.

1. Menü çubuğunda, **derleme** > **çözümü Temizle**.

1. Çözüm oluşturun ve sonra bilgileri gözden **çıkış** penceresi.

     (Başında bulunur) derlemenin başladığı zaman ve hangi dosya işlendi sırası yapı bilgilerini içerir. Bu bilgiler ayrıca, Visual Studio'nun yapı sırasında çalıştırdığı gerçek derleyici sözdizimini de içerir.

     Örneğin, C# yapı [/nowarn](/dotnet/visual-basic/reference/command-line-compiler/nowarn) seçeneği uyarı kodunu listeler **1762**, diğer üç uyarıyla birlikte bu konunun önceki kısımlarında belirtilmiş.

     Visual Basic derleme [/nowarn](/dotnet/visual-basic/reference/command-line-compiler/nowarn) hiçbir uyarı görüntülenmez şekilde dışlanacak belirli uyarıları içermez.

    > [!TIP]
    > İçeriğini arayabilirsiniz **çıkış** görüntülerseniz penceresi **Bul** iletişim kutusunu **Ctrl**+**F** anahtarlar.

Daha fazla bilgi için bkz. [nasıl yapılır: görüntüleme, kaydetme ve yapılandırma derleme günlüğü dosyalarını](../ide/how-to-view-save-and-configure-build-log-files.md).

## <a name="create-a-release-build"></a>Yayın derlemesi oluşturma

Sevkiyat için optimize edilmiş örnek uygulamanın bir sürümünü oluşturabilirsiniz. Sürüm yapısı için yapı başlatılmadan önce çalıştırılabilir bir ağ paylaşımına kopyalandığını belirteceksiniz.

Daha fazla bilgi için [nasıl yapılır: Derleme çıktı dizinini değiştirme](../ide/how-to-change-the-build-output-directory.md) ve [derleme ve temizleme projeler ve çözümler Visual Studio'da](../ide/building-and-cleaning-projects-and-solutions-in-visual-studio.md).

### <a name="specify-a-release-build-for-visual-basic"></a>Visual Basic için bir yayın yapısı belirtmek

1. Açık **Proje Tasarımcısı**.

     ![Görünüm menüsü, özellik sayfaları komutu](../ide/media/buildwalk_viewpropertypages.png)

1. Seçin **derleme** sayfası.

1. İçinde **yapılandırma** listesinde **yayın**.

1. İçinde **Platform** listesinde **x86**.

1. İçinde **yapı çıkış yolu** kutusunda, bir ağ yolu belirtin.

     Örneğin, belirtebilirsiniz `\\myserver\builds`.

    > [!IMPORTANT]
    > Belirttiğiniz ağ paylaşımı güvenilir olmayabilir sizi uyaran bir ileti kutusu görünebilir. Belirttiğiniz konuma güveniyorsanız seçin **Tamam** ileti kutusunda düğmesi.

1. Uygulamayı oluşturun.

     ![Yapı menüsünde derleme çözümü komutu](../ide/media/exploreide-buildsolution.png)

### <a name="specify-a-release-build-for-c"></a>İçin bir yayın yapısı belirtmekC# #

1. Açık **Proje Tasarımcısı**.

     ![Görünüm menüsü, özellik sayfaları komutu](../ide/media/buildwalk_viewpropertypages.png)

1. Seçin **derleme** sayfası.

1. İçinde **yapılandırma** listesinde **yayın**.

1. İçinde **Platform** listesinde **x86**.

1. İçinde **çıkış yolu** kutusunda, bir ağ yolu belirtin.

     Örneğin, belirtebilirsiniz `\\myserver\builds`.

    > [!IMPORTANT]
    > Belirttiğiniz ağ paylaşımı güvenilir olmayabilir sizi uyaran bir ileti kutusu görünebilir. Belirttiğiniz konuma güveniyorsanız seçin **Tamam** ileti kutusunda düğmesi.

1. Üzerinde **standart araç çubuğu**, çözüm yapılandırmaları ayarlamak **yayın** ve çözüm platformları **x86**.

1. Uygulamayı oluşturun.

     ![Yapı menüsünde derleme çözümü komutu](../ide/media/exploreide-buildsolution.png)

   Yürütülebilir dosya, belirttiğiniz ağ yoluna kopyalanır. Kendi yol `\\myserver\builds\\FileName.exe`.

Tebrikler! Bu izlenecek yolda başarıyla tamamladınız.

## <a name="see-also"></a>Ayrıca bkz.

- [İzlenecek yol: derleme proje (C++)](/cpp/ide/walkthrough-building-a-project-cpp)
- [ASP.NET web uygulaması projesi ön derleme genel bakış](/previous-versions/aspnet/aa983464\(v\=vs.110\))
- [İzlenecek yol: MSBuild kullanma](../msbuild/walkthrough-using-msbuild.md)