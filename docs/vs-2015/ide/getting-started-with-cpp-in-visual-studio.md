---
title: C++ Kullanmaya Başlarken
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 99c73344-86ba-4b08-9e15-f6111cc04185
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 7e982db6bf37caf201f75e563a23a28a528a61e7
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53052390"
---
# <a name="getting-started-with-c-in-visual-studio"></a>Visual Studio'da C++ Kullanmaya Başlarken
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu izlenecek yolu tamamlayarak, Visual Studio ile uygulamalar geliştirirken kullanabileceğiniz iletişim kutuları ve araçları birçoğu ile sahibi olacaksınız. Bir basit "Hello, World" oluşturacaksınız-tümleşik geliştirme ortamında (IDE) çalışma hakkında daha fazla bilgi edinirken stil uygulaması.

 Bu konu aşağıdaki bölümleri içermektedir:

 [Visual Studio'da oturum açın](../ide/getting-started-with-cpp-in-visual-studio.md#BKMK_Configure)

 [Basit bir uygulama oluşturma](../ide/getting-started-with-cpp-in-visual-studio.md#BKMK_CreateApp)

 [Uygulamanıza kod eklemek](../ide/getting-started-with-cpp-in-visual-studio.md#BKMK_AddCode)

 [Hata ayıklama ve uygulamayı test etme](../ide/getting-started-with-cpp-in-visual-studio.md#BKMK_DebugTest)

 [Uygulama sürümü oluşturma](../ide/getting-started-with-cpp-in-visual-studio.md#BKMK_BuildRelease)

##  <a name="BKMK_Configure"></a> Visual Studio'da oturum açın
 Visual Studio'yu ilk kez başlattığınızda, Live veya Outlook gibi bir Microsoft hesabı ile oturum açması olasılığını verilir. Oturum açarken ayarlarınızı tüm cihazlarınızda eşitlenmesine izin verir. Daha fazla bilgi için [Visual Studio'da oturum açma](../ide/signing-in-to-visual-studio.md)

 Şekil 1: Visual Studio IDE

 ![Visual C ile IDE&#43; &#43; uygulanan ayarları](../ide/media/c-ide-defaultenvironmentlayout.png "C ++ IDE_DefaultEnvironmentLayout")

 Visual Studio'yu açtıktan sonra IDE üç temel bölümlerini görebilirsiniz: windows, menüler ve araç çubuklarını ve ana pencere alanını aracı. Araç pencereleri tutturulmuştur ve uygulama penceresinin sol tarafında ile **hızlı başlatma**, menü çubuğu ve en üstte standart araç çubuğu. Uygulama penceresinin merkezi içerir **başlangıç sayfası**. Bir çözüm veya projeyi açtığınızda, düzenleyiciler ve tasarımcılar Bu alanda görüntülenir. Uygulama geliştirirken zamanınızın çoğunu bu orta alanda geçireceksiniz.

##  <a name="BKMK_CreateApp"></a> Basit bir uygulama oluşturma
 Visual Studio'da bir uygulama oluşturduğunuzda, proje ve çözüm ilk oluşturun. Bu örnekte, bir Windows konsol uygulaması oluşturacaksınız.

#### <a name="to-create-a-console-app"></a>Bir konsol uygulaması oluşturmak için

1. Menü çubuğunda, **dosya**, **yeni**, **proje**.

    ![Menü çubuğunda, dosya, yeni seçin, proje](../ide/media/exploreide-filenewproject.png "ExploreIDE FileNewProject")

2. İçinde **Visual C++** kategorisi seçin **Win32 konsol uygulaması** şablonu ve ardından ad proje `GreetingsConsoleApp`.

    ![Win32 konsol uygulaması şablonu](../ide/media/c-ide-newprojectdlg.png "C ++ IDE_NewProjectDlg")

3. Win32 Uygulama Sihirbazı'nı göründüğünde **son** düğmesi.

    ![Win32 Konsol Uygulama Sihirbazı'nı](../ide/media/c-ide-win32consoleappwizard.png "C ++ IDE_Win32ConsoleAppWizard")

   GreetingsConsoleApp projeyi ve çözümü, bir Win32 konsol uygulaması için temel dosyalar oluşturulur ve otomatik olarak yüklenen **Çözüm Gezgini**. GreetingsConsoleApp.cpp dosyası Kod Düzenleyicisi'nde açılır. Aşağıdaki öğeler görünür **Çözüm Gezgini**:

   Şekil 4: Proje öğeleri

   ![Çözüm Gezgini'nde çözüm dosyalarını](../ide/media/c-ide-solutioncontents.png "C ++ IDE_SolutionContents")

##  <a name="BKMK_AddCode"></a> Uygulamanıza kod eklemek
 Ardından konsol penceresinde "Hello" word görüntülenecek kod ekleyeceksiniz.

#### <a name="to-display-hello-in-the-console-window"></a>"Hello" Konsol penceresinde görüntülemek için

1.  Boş bir satır satırından önce GreetingsConsoleApp.cpp dosyasında girin `return 0;` ve ardından aşağıdaki kodu girin:

    ```
    cout << "Hello\n";
    ```

     Altında kırmızı dalgalı çizgi görünür `cout`. Üzerine bir hata iletisi görüntülenir.

     ![Hata metni cout](../ide/media/c-ide-couterror.png "C ++ IDE_CoutError")

     Hata iletisi ayrıca görünür **hata listesi** penceresi. Pencere tarafından menü çubuğundan seçme görüntüleyebileceğiniz **görünümü**, **hata listesi**.

     [cout](http://msdn.microsoft.com/library/d87db6c3-e4e1-4d09-9ec5-458f55018257) dahil \<iostream\> üst bilgi dosyası.

2.  İostream üstbilgi eklemek için sonra aşağıdaki kodu girin. `#include "stdafx.h"`:

    ```
    #include \<iostream\>
    using namespace std;
    ```

     Girdiğiniz karakterler için önerileri sağlama kodu girildiği gibi görünen bir kutu büyük bir olasılıkla fark. Bu kutuyu C++ IntelliSense, sınıf veya arabirim üyeleri ve parametre bilgileri de dahil olmak üzere kodlama yönergeleri sağlayan bir parçasıdır. Önceden tanımlanmış kod bloklarını olan kod parçacıklarını da kullanabilirsiniz. Daha fazla bilgi için [IntelliSense kullanarak](../ide/using-intellisense.md) ve [kod parçacıkları](../ide/code-snippets.md).

     Altında kırmızı dalgalı çizgi `cout` hatayı düzeltmeniz kaybolur.

3.  Değişiklikleri dosyaya kaydedin.

     ![Cout hata düzeltmeleri kod](../ide/media/c-ide-coutfix.png "C ++ IDE_CoutFix")

##  <a name="BKMK_DebugTest"></a> Hata ayıklama ve uygulamayı test etme
 "Hello" sözcüğünü konsol penceresinde görünür olup olmadığını görmek için GreetingsConsoleApp ayıklayabilirsiniz.

#### <a name="to-debug-the-application"></a>Uygulamada hata ayıklamak için

-   Hata ayıklayıcıyı başlatın.

     ![Hata ayıklama menüsünden hata ayıklamayı Başlat](../ide/media/exploreide-startdebugging.png "ExploreIDE StartDebugging")

     Hata ayıklayıcıyı başlatır ve kodu çalıştırır. Konsol penceresi (bir komut istemi gibi görünüyor ayrı bir pencerede) için birkaç saniye görüntülenir ancak hata ayıklayıcı çalışmayı durdurduğunda hızla kapatır. Metin görmek için program yürütme durdurmak için bir kesme noktasını ayarlamanız gerekir.

#### <a name="to-add-a-breakpoint"></a>Bir kesme noktası eklemek için

1. Menü çubuğundan satırında bir kesme noktası ekleyin `return 0;`. Ayrıca, bir kesme noktası ayarlamak için sol kenar boşluğunda tıklayabilirsiniz.

    ![Kesme noktası komutu hata ayıklama menüsünden geçiş](../ide/media/exploreide-togglebreakpoint.png "ExploreIDE ToggleBreakpoint")

    Düzenleyici penceresinin en sol kenar boşluğunda, kod satırının yanında kırmızı bir daire görünür.

2. Hata ayıklamayı başlatmak için F5 tuşuna basın.

    Hata ayıklayıcıyı başlatır, word gösteren bir konsol penceresi görünür **Hello**.

    ![Merhaba Windows Komut İstemi penceresindeki metin](../ide/media/c-ide-hellocommandwindow.png "C ++ IDE_HelloCommandWindow")

3. SHIFT + hata ayıklamayı durdurmak için F5 tuşuna basın.

   Daha fazla bilgi için [konsol projeleri](../debugger/debugging-preparation-console-projects.md).

##  <a name="BKMK_BuildRelease"></a> Uygulama sürümü oluşturma
 Her şeyin çalıştığını doğruladığınıza göre artık, uygulamanın bir yayın derlemesini hazırlayabilirsiniz.

#### <a name="to-clean-the-solution-files-and-build-a-release-version"></a>Çözüm dosyalarını temizlemek ve yayın sürümünü oluşturmak için

1. Menü çubuğundan ara dosyaları ve önceki derlemeler sırasında oluşturulan çıktı dosyalarını silin.

    ![Yapı menüsünde çözümü Temizle komutunu](../ide/media/exploreide-cleansolution.png "ExploreIDE CleanSolution")

2. GreetingsConsoleApp için yapı yapılandırmasını değiştirme **hata ayıklama** için **yayın**.

    ![Uygulamanın yayın sürümünü oluşturmak](../ide/media/c-ide-changingbuildtorelease.png "C ++ IDE_ChangingBuildtoRelease")

3. Çözümü oluşturun.

    ![Derleme çözümü komutu yapı menüsünde](../ide/media/exploreide-buildsolution.png "ExploreIDE BuildSolution")

   Tebrikler, bu izlenecek yolu tamamladınız! Daha fazla örnek keşfetmek isterseniz bkz [Visual Studio örnekleri](../ide/visual-studio-samples.md).

## <a name="see-also"></a>Ayrıca Bkz.
 [İzlenecek yol: basit bir uygulama oluşturma](../ide/walkthrough-create-a-simple-application-with-visual-csharp-or-visual-basic.md) [üretkenlik ipuçları](../ide/productivity-tips-for-visual-studio.md) [Visual Studio örnekleri](../ide/visual-studio-samples.md) [Visual Studio ile geliştirmeye başlayın](../ide/get-started-developing-with-visual-studio.md)
