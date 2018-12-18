---
title: Visual Studio 2017'in genel bakış
titleSuffix: ''
ms.date: 10/26/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
author: gewarren
f1_keywords:
- vs.startpage
- VS.StartPage.HowDoI
- MSDNSTART
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6e73396510277e1616d78d650af3372d6c991ea2
ms.sourcegitcommit: 0cdd8e8a53fb4fd5e869f07c35204419fa12783d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53160272"
---
# <a name="welcome-to-the-visual-studio-ide"></a>Visual Studio IDE Hoş Geldiniz

Visual Studio *tümleşik geliştirme ortamı* bir yaratıcı launching düzenleme, hata ayıklama ve kod oluşturmak için kullanın ve ardından bir uygulama yayımlama takımdır. Bir tümleşik geliştirme ortamı (IDE) birçok yönüyle yazılım geliştirme için kullanılabilen zengin bir programdır. Standart Düzenleyici ve hata ayıklayıcı sağladığımız çoğu IDE'ler sağlamanızı, Visual Studio yazılım geliştirme işlemini kolaylaştırmak için derleyiciler, kod tamamlama araçları, grafik tasarımcıları ve daha birçok özellik içerir.

![Visual Studio IDE](media/visual-studio-ide.png)

Bu görüntü, büyük olasılıkla kullanacağınız birkaç anahtar araç pencereleri ve bir Proje Aç ile Visual Studio gösterir:

- [**Çözüm Gezgini** ](../ide/solutions-and-projects-in-visual-studio.md) (sağ üstte) görüntüleyin, gidin ve kodu dosyalarınızdaki dosyalardan yönetmenize olanak tanır. **Çözüm Gezgini** dosyalarına gruplandırarak kodunuzu düzenleme şeklinizdir yardımcı olabilecek [çözümler ve projeler](../get-started/tutorial-projects-solutions.md).

- [Düzenleyicisi penceresi](../ide/writing-code-in-the-code-and-text-editor.md) (Merkezi), büyük olasılıkla, zamanınızın çoğunu geçireceksiniz burada dosya içeriğini görüntüler. Burada kodunu düzenleyin veya düğme ve metin kutusu içeren bir pencere gibi bir kullanıcı arabirimi tasarım budur.

- [Çıkış penceresine](../ide/reference/output-window.md) (alt Merkezi), burada Visual Studio hata ayıklama ve hata iletileri, derleyici uyarılarını, yayımlama durum iletilerini ve diğer bildirimleri gönderir. Her ileti kaynağı kendi sekmesi vardır.

- [Takım Gezgini](/azure/devops/user-guide/work-team-explorer?view=vsts) (sağ alt) sağlar, iş öğelerini izlemek ve kod başkalarıyla paylaşmak gibi sürüm denetimi teknolojileri kullanarak [Git](https://git-scm.com/) ve [Team Foundation sürüm denetimi (TFVC)](/azure/devops/repos/tfvc/overview?view=vsts).

## <a name="editions"></a>Sürümler

Windows ve Mac için Visual Studio kullanılabilir [Mac için Visual Studio](/visualstudio/mac/) birçok Visual Studio 2017 aynı özelliklere sahiptir ve platformlar arası ve mobil uygulamalarını geliştirmek için optimize edilmiştir. Bu makalede Visual Studio 2017'in Windows sürümünde odaklanır.

Visual Studio 2017'in üç sürüm bulunur: Community, Professional ve Enterprise. Bkz: [Visual Studio 2017 IDE'lerini karşılaştırın](https://visualstudio.microsoft.com/vs/compare/) her iki sürümünde desteklenen hangi özellikler hakkında bilgi edinmek için.

## <a name="popular-productivity-features"></a>Popüler üretkenlik özellikleri

Visual Studio yazılım geliştirme sırasında daha üretken olmanıza yardımcı olan popüler özelliklerinden bazıları şunlardır:

- [Yeniden Düzenleme](../ide/refactoring-in-visual-studio.md)

   Yeniden düzenleme, bir veya daha fazla kod satırlarını yöntem parametreleri ve daha fazlasını sırasını değiştirerek yeni bir yönteme ayıklama değişkenlerin akıllı yeniden adlandırma gibi işlemleri içerir.

   ![Visual Studio'da yeniden düzenleme](media/refactoring-menu.png)

- [IntelliSense](../ide/using-intellisense.md)

   IntelliSense, doğrudan düzenleyicide kod hakkında bilgi görüntüler ve bazı durumlarda, küçük kod parçalarını sizin için yazma özellikleri kümesi için kullanılan bir terimdir. Bu temel belgeleri satır içi başka bir yerde türü bilgi aramak zorunda kalmaktan kurtarır düzenleyicisinde gibidir. IntelliSense özellikleri dile göre değişiklik gösterir. Daha fazla bilgi için [C# IntelliSense](../ide/visual-csharp-intellisense.md), [Visual C++ IntelliSense](../ide/visual-cpp-intellisense.md), [JavaScript IntelliSense](../ide/javascript-intellisense.md), ve [Visual Basic IntelliSense](../ide/visual-basic-specific-intellisense.md). Aşağıdaki çizimde, IntelliSense üye listesi bir türü için nasıl görüntülediğini gösterir:

   ![Visual Studio üye listesi](media/intellisense-list-members.png)

- [Hızlı Başlatma](../ide/reference/quick-launch-environment-options-dialog-box.md)

   Visual Studio zamanlarda sürü menüleri, seçenekleri ve özellikleri ile zor görünebilir. **Hızlı başlatma** arama kutusuna, Visual Studio'da aradığınızı hızla bulmak için harika bir yoludur. Aradığınız bir şey adını yazmaya başladığınızda, Visual Studio tam olarak gitmek gerek duyduğunuz aldığınız sonuçları listeler. Örneğin, ek bir programlama dili için destek eklemek Visual Studio işlevselliği eklemek gerekiyorsa **hızlı başlatma** bir iş yükü veya ayrı ayrı bileşen yüklemek için Visual Studio yükleyicisini açın sonuçlar sağlar.

   ![Visual Studio'da hızlı başlatma arama kutusu](media/quick-launch-nuget.png)

- Dalgalı çizgiler ve [hızlı Eylemler](../ide/quick-actions.md)

   Siz yazarken, hatalar veya kodunuzdaki olası sorunlar için uyarı dalgalı alt çizgiler dalgalı çizgiler var. Bu görsel ipuçları hata derleme sırasında veya programı çalıştırdığınızda bulunmak beklenmeden hemen sorunları düzeltmek etkinleştirin. Bir dalgalı çizgi gelin, hatayla ilgili ek bilgileri görürsünüz. Hatayı düzeltmek için hızlı Eylemler bilinen eylemlerle sol kenar boşluğunda bir ampul de görünebilir.

   ![Visual Studio'da dalgalı çizgiler](media/squiggles-error.png)

- [Çağrı Hiyerarşisi](../ide/reference/call-hierarchy.md)

   **Çağrı hiyerarşisi** penceresi seçili bir yöntemi çağıran yöntemleri gösterir. Bu, değiştirme veya kaldırma yöntemi düşündüğünüzü yararlı bilgiler olması veya bir hatayı izlemek çalışırken oluşturabilirsiniz.

   ![Çağrı hiyerarşisi penceresi](../ide/reference/media/call-hierarchy-csharp-expanded.png)

- [CodeLens](../ide/find-code-changes-and-other-history-with-codelens.md)

   CodeLens, kodunuz için başvurular bulmanıza yardımcı olur, düzenleyiciden çıkmadan, kod, bağlı hataları, iş öğeleri, kod incelemeleri ve birim testleri değiştirir.

   ![CodeLens](media/codelens-overview.png)

- [Tanıma Git](../ide/go-to-and-peek-definition.md)

   Tanıma özelliği, doğrudan bir işlev veya tür tanımlandığı konumuna götürür.

   ![Tanıma Git](media/go-to-definition-menu.png)

- [Tanıma göz at](../ide/how-to-view-and-edit-code-by-using-peek-definition-alt-plus-f12.md)

   **Özet tanım** penceresi, ayrı bir dosyayı açmaya gerek kalmadan bir yöntem veya tür tanımı gösterir.

   ![Tanıma göz at](media/peek-definition.png)

## <a name="install-the-visual-studio-ide"></a>Visual Studio IDE yükleyin

Bu genel bakış makalesinde basit bir proje oluşturma ve renk temasını değiştirme gibi Visual Studio ile yapabilir şeylerden bazıları çalışırken size kullanarak [IntelliSense](../ide/using-intellisense.md) bir yardımcı kodlama ve hata ayıklama değeri görmek için bir uygulama olarak bir program yürütme sırasında değişkeni. Başlamak için [Visual Studio 2017'yi indirin](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) ve sisteminize yüklenecek.

Modüler yükleyici seçin ve yüklemek sağlayan *iş yükleri*, programlama dili veya tercih ettiğiniz platform için gerekli özellikler grupları olduğu. İçin adımları [bir program oluşturma](#create-a-program), seçtiğinizden emin olun **.NET Core çoklu platform geliştirme** yüklemesi sırasında iş yükü.

![.NET core çoklu platform geliştirme iş yükünü Visual Studio yükleyicisi](media/dotnet-core-cross-platform-workload.png)

Visual Studio'yu ilk kez başlattığınızda, isteğe bağlı olarak yapabilecekleriniz [oturum](../ide/signing-in-to-visual-studio.md) Microsoft hesabınızı veya iş veya Okul hesabınızı kullanarak.

## <a name="create-a-program"></a>Bir program oluşturma

Şimdi kolları sıvayın ve basit bir program oluşturun.

1. Visual Studio'yu açın. Menüsünde **dosya** > **yeni** > **proje**.

   ![Dosya > Yeni Proje menü çubuğunda](media/file-new-project-menu.png)

2. **Yeni proje** iletişim kutusu gösterir birkaç proje *şablonları*. Şablon, belirtilen proje türü için gereken ayarları ve temel dosyaları içerir. Seçin **.NET Core** kategorisi altında **Visual C#** ve ardından **konsol uygulaması (.NET Core)** şablonu. İçinde **adı** metin kutusunda, **HelloWorld**ve ardından **Tamam** düğmesi.

   ![.NET core uygulaması şablonu](media/overview-new-project-dialog.png)

   Visual Studio projesi oluşturur. Çağıran basit bir "Hello World" uygulaması olan <xref:System.Console.WriteLine?displayProperty=nameWithType> "Hello World!" sabit dizesini görüntülemek için yöntemi (program çıktısı) konsol penceresinde.

   > [!NOTE]
   > Görmüyorsanız **.NET Core** kategorisi, yüklemeniz gereken **.NET Core çoklu platform geliştirme** iş yükü. Bunu yapmak için **açık Visual Studio yükleyicisi** alt sol tarafındaki bağlantıyı **yeni proje** iletişim. Visual Studio yükleyicisi açıldığında, aşağıya kaydırın ve **.NET Core çoklu platform geliştirme** iş yükü ve ardından **Değiştir**.

   Kısa bir süre sonra aşağıdaki gibi görmeniz gerekir:

   ![Visual Studio IDE](media/overview-ide-console-app.png)

   Alanı çoğu alan Düzenleyicisi penceresinde, uygulamanız için C# kodunu gösterir. Farklı anahtar sözcükleri ve türleri gibi bir kod bölümlerini göstermek için metni otomatik olarak renklendirilmiş dikkat edin. Ayrıca, hangi küme ayraçları başka bir eşleşen küçük, dikey kesikli satır kodda belirtmek ve satır numaralarını Yardım kodu daha sonra bulun. Daraltma veya genişletme kod blokları için küçük, kutulanmış eksi işaretleri seçebilirsiniz. Anahat oluşturma özelliği bu kod, ekranda dağınıklığı aza indirilmesine yardımcı ihtiyacınız olmayan kodu Gizle olanak tanır. Proje dosyalarını adlı bir pencerede sağ tarafta listelenen **Çözüm Gezgini**.

   ![Kırmızı kutuları ile Visual Studio IDE](media/overview-ide-console-app-red-boxes.png)

   Kullanılabilir diğer menüleri ve araç pencerelerini, ancak geçelim şimdilik.

3. Şimdi uygulamayı başlatın. Bunu seçerek yapabilirsiniz **hata ayıklama olmadan Başlat** gelen **hata ayıklama** menü çubuğundaki menü. Ayrıca basabilirsiniz **Ctrl**+**F5**.

   ![Hata ayıklama > menü hata ayıklama olmadan Başlat](media/overview-start-without-debugging.png)

   Visual Studio uygulamayı derler ve bir konsol penceresi iletiyle açılır **Merhaba Dünya!**. Artık çalışan bir uygulamanın var!

   ![Konsol penceresi](media/overview-console-window.png)

4. Konsol penceresini kapatmak için klavyenizde herhangi bir tuşa basın.

5. Uygulama için bazı ek kod ekleyelim. Aşağıdaki C# kodu yazan satırından önce ekleyin `Console.WriteLine("Hello World!");`:

   ```csharp
   Console.WriteLine("\nWhat is your name?");
   var name = Console.ReadLine();
   ```

   Bu kod görüntüler **adınız ne?** konsol penceresi, ve ardından kullanıcı tarafından izlenen metin girene kadar bekler **Enter** anahtarı.

6. Yazan satırı değiştirin `Console.WriteLine("Hello World!");` aşağıdaki koda:

   ```csharp
   Console.WriteLine($"\nHello {name}!");
   ```

7. Seçerek uygulama yeniden çalıştırma **hata ayıklama** > **hata ayıklama olmadan Başlat** veya basarak **Ctrl**+**F5**.

   Visual Studio uygulaması oluşturur ve bir konsol penceresi açar ve sizden adınız için ister.

8. Konsol penceresi ve ENTER tuşuna adınızı girin **Enter**.

   ![Konsol penceresi girdisi](media/overview-console-input.png)

9. Konsol penceresini kapatın ve çalışan programa durdurmak için herhangi bir tuşa basın.

## <a name="use-refactoring-and-intellisense"></a>Yeniden düzenleme ve IntelliSense kullanma

Birkaç farklı şekilde bakalım, [yeniden düzenleme](../ide/refactoring-in-visual-studio.md) ve [IntelliSense](../ide/using-intellisense.md) yardımcı olabilecek daha verimli bir şekilde kod.

İlk olarak, Şimdi Yeniden Adlandır `name` değişkeni:

1. Çift `name` değişkeni seçin.

2. Değişken için yeni adı yazın **username**.

   Değişkeni ve bir ampul gri kutu göründüğüne dikkat edin, kenar boşluğunda görünür.

3. Kullanılabilir göstermek için ampul simgesini [hızlı Eylemler](../ide/quick-actions.md). Seçin **Yeniden Adlandır 'name 'username' için'**.

   ![Visual Studio'da eylemini yeniden adlandır](media/rename-quick-action.png)

   Değişkeni, bu örnekte yalnızca iki basamağı olan proje boyunca yeniden adlandırılır.

   ![Visual Studio'da yeniden adlandırma düzenlemesi gösteren animasyonlu gif](media/rename-refactoring.gif)

4. Artık IntelliSense bir göz atalım. İfadesini içeren bir satırın altına `Console.WriteLine($"\nHello {username}!");`, türü **DateTime artık tarih/saat =.**.

   Bir kutu üyelerini görüntüler <xref:System.DateTime> sınıfı. Ayrıca, ayrı bir kutuda şu anda seçilen üyenin açıklamasını görüntüler.

   ![Visual Studio IntelliSense üyeleri Listele](media/intellisense-list-members.png)

5. Adlı üye seçin **artık**, üzerine çift tıklayarak veya basarak sınıfın bir özelliği olan **sekmesini**. Noktalı virgül ekleyerek kod satırının tamamlamak **;**.

6. Aşağıda, yazın veya aşağıdaki kod satırlarını kopyala:

   ```csharp
   int dayOfYear = now.DayOfYear;

   Console.Write("Day of year: ");
   Console.WriteLine(dayOfYear);
   ```

   > [!TIP]
   > <xref:System.Console.Write%2A?displayProperty=nameWithType> biraz farklı <xref:System.Console.WriteLine%2A?displayProperty=nameWithType> içeren Yazar sonra bir satır Sonlandırıcı eklemez. Bu sonraki çıkışa gönderilir metin parçası aynı satırda yazdırılır anlamına gelir. Bu yöntemlerin her biri kendi açıklamasını görmek için kodunuzda gelebilirsiniz.

7. Ardından, yeniden yeniden düzenleme kod biraz daha kısa olmak için kullanacağız. Değişkenin üzerine tıklayın `now` satırında `DateTime now = DateTime.Now;`.

   Kenar boşluğunda bu satırdaki bir tornavida ikonu görüntülendiğine dikkat edin.

8. Önerileri görmek için tornavida simgesine tıklayarak Visual Studio kullanılabilir sahiptir. Bu durumda, gösteren [satır içi geçici değişken](../ide/reference/inline-temporary-variable.md) düzenleme genel davranışını değiştirmeden bir kod satırı kaldırmak için:

   ![Satır içi geçici değişken Visual Studio'da yeniden düzenleme](media/inline-temporary-variable-refactoring.png)

9. Tıklayın **satır içi geçici değişken** kodun yeniden.

10. Tuşlarına basarak programı yeniden çalıştırın **Ctrl**+**F5**. Çıktı aşağıdakine benzer olacaktır:

   ![Konsol penceresi ile program çıktısı](media/overview-console-final.png)

## <a name="debug-code"></a>Kodda hata ayıklama

Kod yazmak, çalıştırmak ve hatalar için test gerekir. Visual Studio'nun hata ayıklama sistem aynı anda bir deyim kod adım adım ve kullandıkça, değişkenleri inceleyebilir olanak sağlar. Ayarlayabileceğiniz *kesme noktaları* belirli bir satır kod yürütmeyi durdurun. Bir değişken değişiklikleri değeri olarak kodu nasıl çalıştığını ve daha fazlasını gözlemleyebilirsiniz.

Değerini görmek için bir kesme noktası ayarlayalım `username` program "uçuşta" iken değişkeni.

1. İfadesini içeren kod satırını bulun `Console.WriteLine($"\nHello {username}!");`. Bu kod satırı, programın bu satırı yürütmeyi Duraklat yapmak için diğer bir deyişle, bir kesme noktası ayarlamak için düzenleyicisinin en sol kenar boşluğunda tıklayın. Ayrıca kod satırında herhangi bir yere tıklayın ve sonra basın **F9**.

   Kırmızı bir daire en sol kenar boşluğunda görünür ve kodu vurgulanır.

   ![Visual Studio'da kod satırında kesme noktası](media/breakpoint.png)

1. Seçerek hata ayıklamayı Başlat **hata ayıklama** > **hata ayıklamayı Başlat** veya basarak **F5**.

1. Konsol penceresinde görünür ve adınız için ister, yazın ve basın **Enter**.

   Visual Studio kod düzenleyicisine odağı döndürür ve kesme noktası ile kod satırı sarı renkle vurgulanır dikkat edin. Bu program yürütülen kodun sonraki satıra olduğunu gösterir.

1. Fareyi üzerine `username` değerini görmek için değişkeni. Alternatif olarak, üzerinde sağ tıklayabilirsiniz `username` seçip **Gözcü Ekle** değişkeni eklemek için **Watch** penceresinde de görebileceğiniz değeri.

   ![Visual Studio'da hata ayıklama sırasında değişken değeri](media/debugging-variable-value.png)

1. Programın tamamlanmaya kadar çalışmasına izin vermek için basın **F5** yeniden.

Visual Studio'da hata ayıklama hakkında daha fazla bilgi edinmek için bkz. [hata ayıklayıcısı özellik Turu](../debugger/debugger-feature-tour.md).

## <a name="customize-visual-studio"></a>Visual Studio'yu özelleştirme

Varsayılan renk temasını değiştirme dahil olmak üzere Visual Studio kullanıcı arabirimi kişiselleştirebilirsiniz. Değiştirilecek **koyu** teması:

1. Menü çubuğunda, **Araçları** > **seçenekleri** açmak için **seçenekleri** iletişim.

2. Üzerinde **ortam** > **genel** seçenekler sayfası, değişiklik **renk teması** seçimi **koyu**seçin **Tamam**.

   IDE renk temasını tamamı için değişir **koyu**.

   ![Visual Studio'da koyu tema](media/dark-theme.png)

IDE'yi kişiselleştirme diğer yollar hakkında bilgi edinmek için [kişiselleştirme Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

## <a name="next-steps"></a>Sonraki adımlar

Bu tanıtıcı makaleler biriyle boyunca izleyerek daha fazla Visual Studio'ı keşfedin:

- Kod Düzenleyicisi'nde ile tanışın [Kod Düzenleyicisi'ni kullanmayı öğrenin](../get-started/tutorial-editor.md)

- Visual Studio kodu nasıl düzenler öğrenin [projeler ve çözümler hakkında bilgi edinin](../get-started/tutorial-projects-solutions.md)

Daha fazla kodlama içine dalmaya hazır değilseniz aşağıdaki dile özgü hızlı başlangıçları iyi bir sonraki adım biridir:

- [İlk Python web uygulamanızı oluşturmak için Visual Studio](../ide/quickstart-python.md)

- [İlk C# web uygulamanızı oluşturmak için Visual Studio](../ide/quickstart-aspnet-core.md)

- [Visual Studio'yu ilk kez oluşturma kullanarak F# web uygulaması](../ide/quickstart-fsharp.md)

- [İlk Node.js uygulamanızı oluşturmak için Visual Studio](../ide/quickstart-nodejs.md)

- [Visual Studio'da C++ kullanmaya başlama](../ide/getting-started-with-cpp-in-visual-studio.md)

## <a name="see-also"></a>Ayrıca bkz.

- Bulma [daha fazla Visual Studio özellikleri](../ide/advanced-feature-overview.md)
- Ziyaret [visualstudio.microsoft.com](https://visualstudio.microsoft.com/vs/)
- Okuma [Visual Studio blogu](https://blogs.msdn.microsoft.com/visualstudio/)
- Ücretsiz Visual Studio kursları kullanıma [Microsoft Virtual Academy](https://mva.microsoft.com/product-training/visual-studio-courses#!index=2&lang=1033)
- Visual Studio'yu indirin [Visual Studio indirmeleri](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017)
