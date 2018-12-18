---
title: Canlı birim testi ile 2017 kullanarak kodunuzu test etme hakkında bilgi edinin | Microsoft Docs
ms.date: 08/31/2017
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio ALM
- Live Unit Testing
author: rpetrusha
ms.author: ronpet
ms.workload:
- dotnet
ms.openlocfilehash: 8908b592283f81d8c60a2adb93c12af3f5e61ba7
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53056791"
---
# <a name="get-started-with-live-unit-testing-in-visual-studio"></a>Visual Studio Live Unit Testing kullanmaya başlama

Visual Studio çözümünde Live Unit Testing ' ı etkinleştirdiğinizde, Live Unit Testing görsel olarak test kapsamınızı ve testlerinizi durumunu gösterir. Bu, kodunuzu değiştirmeniz olduğunda da dinamik testleri yürütür ve hemen değişikliklerinizi testleri başarısız olmasına neden olduğunda size bildirir.

Live Unit Testing .NET Framework veya .NET Core hedef çözümlerini test etmek için kullanılabilir. Bu öğreticide, Live Unit Testing hedefleyen .NET Standard basit sınıf kitaplığı oluşturarak öğreneceksiniz ve test etmek için .NET Core hedefleyen bir MSTest projesi oluşturacaksınız.

# <a name="ctabcsharp"></a>[C#](#tab/csharp)
Tam C# çözümünü indirilebileceğini [MicrosoftDocs/visualstudio-docs](https://github.com/MicrosoftDocs/visualstudio-docs/tree/master/docs/test/samples/csharp/UtilityLibraries/) github deposu.
# <a name="visual-basictabvisual-basic"></a>[Visual Basic](#tab/visual-basic)
Visual Basic çözümü indirilebileceğini [MicrosoftDocs/visualstudio-docs](https://github.com/MicrosoftDocs/visualstudio-docs/tree/master/docs/test/samples/visual-basic/UtilityLibraries/) github deposu.

---

## <a name="prerequisites"></a>Önkoşullar

Bu öğretici, .NET Core 2.0 iş yüküyle Visual Studio 2017 Enterprise Edition Sürüm 15.3 yüklediğinizi gerektirir.

## <a name="create-the-solution-and-the-class-library-project"></a>Çözüm ve sınıf kitaplığı projesi oluşturma

Adlı bir Visual Studio çözümü oluşturarak başlayın `UtilityLibraries` bir tek .NET Standard sınıf kitaplığı projesi oluşur `StringLibrary`. Yazabileceğiniz `StringLibrary` C# veya Visual Basic içinde.

Yalnızca bir veya daha fazla proje için bir kapsayıcı çözümüdür. Çözümü oluşturmak için Visual Studio 2017'yi açın ve aşağıdakileri yapın:

1. Seçin **dosya** > **yeni** > **proje** en üst düzey Visual Studio menüsünde.

1. İçinde **yeni proje** iletişim kutusunda genişletin **diğer proje türleri** düğümünü seçip alt **Visual Studio çözümleri**. Seçin **boş çözüm** sağ bölmede şablon girin `UtilityLibraries` içinde **adı** metin kutusunda, aşağıdaki şekilde gösterildiği gibi:

   ![** ** Yeni Proje iletişim kutusu](./media/lut-start/new-solution.png)

1. Seçin **Tamam** çözümü oluşturmak için.

Çözüm oluşturduğunuza göre adlı bir sınıf kitaplığı oluşturursunuz `StringLibrary` birkaç dizelerle genişletme yöntemleri içerir.

# <a name="ctabcsharp"></a>[C#](#tab/csharp)
1. İçinde **Çözüm Gezgini**, sağ `UtilityLibraries` çözüm ve select **Ekle** > **yeni proje**.

1. İçinde **Yeni Proje Ekle** iletişim kutusunda Seç C# düğümünü seçip **.NET Standard**.

   > [!NOTE]
   > Kitaplığımızı .NET Standard yerine belirli bir .NET uygulamasını hedeflediğinden, .NET Standard sürümünü destekleyen bir .NET uygulamasından çağrılabilir. Daha fazla bilgi için [.NET Standard](/dotnet/standard/net-standard).

1. Seçin **sınıf kitaplığı (.NET Standard)** sağ bölmede, şablon ve girin `StringLibrary` içinde **adı** metin kutusunda, aşağıdaki şekilde gösterildiği gibi:

   ![** Ekleme yeni proje ** iletişim](./media/lut-start/add-project-cs.png)

1. Seçin **Tamam** projeyi oluşturmak için.

1. Tüm mevcut kodlar kod penceresinde, aşağıdaki kodla değiştirin:

   [!code-csharp[StringLibrary source code](samples/csharp/utilitylibraries/stringlibrary/class1.cs)]

   `StringLibrary` üç statik yöntemleri vardır:

      - `StartsWithUpper` döndürür `true` Aksi halde, bir dizeyi büyük harfli bir karakterle; başlarsa döndürür `false`.

      - `StartsWithLower`döndürür `true` Aksi halde, bir dize bir küçük harf karakteri ile; başlarsa döndürür `false`.

      - `HasEmbeddedSpaces` döndürür `true` bir katıştırılmış bir boşluk karakteri; bir dize içeriyorsa, aksi takdirde, döndürür `false`.

1.  Seçin **derleme** > **Çözümü Derle** en üst düzey Visual Studio menüsünde. Visual Studio başarıyla kitaplığınızı oluşturması gerekir.

# <a name="visual-basictabvisual-basic"></a>[Visual Basic](#tab/visual-basic)
1. İçinde **Çözüm Gezgini**, sağ `UtilityLibraries` çözüm ve select **Ekle** > **yeni proje**.

1. İçinde **Yeni Proje Ekle** iletişim kutusunda Visual Basic düğümünü seçin ve ardından **.NET Standard**.

   > [!NOTE]
   > Kitaplığımızı .NET Standard yerine belirli bir .NET uygulamasını hedeflediğinden, .NET Standard sürümünü destekleyen bir .NET uygulamasından çağrılabilir. Daha fazla bilgi için [.NET Standard](/dotnet/standard/net-standard).

1. Seçin **sınıf kitaplığı (.NET Standard)** sağ bölmede, şablon ve girin `StringLibrary` içinde **adı** metin kutusunda, aşağıdaki şekilde gösterildiği gibi:

   ![** Ekleme yeni proje ** iletişim](./media/lut-start/add-project-vb.png)

1. Seçin **Tamam** projeyi oluşturmak için.

1. Tüm mevcut kodlar kod penceresinde, aşağıdaki kodla değiştirin:

   [!code-vb[StringLibrary source code](samples/visual-basic/utilitylibraries/stringlibrary/class1.vb)]

   `StringLibrary` üç statik yöntemleri vardır:

      - `StartsWithUpper` döndürür `true` Aksi halde, bir dizeyi büyük harfli bir karakterle; başlarsa döndürür `false`.

      - `StartsWithLower`döndürür `true` Aksi halde, bir dize bir küçük harf karakteri ile; başlarsa döndürür `false`.

      - `HasEmbeddedSpaces` döndürür `true` bir katıştırılmış bir boşluk karakteri; bir dize içeriyorsa, aksi takdirde, döndürür `false`.

1. StringLibrary projeye sağ tıklayarak **Çözüm Gezgini** seçip **özellikleri**. İçinde **uygulama** sekmesinde, metni silmek **kök ad alanı** metin kutusunda, aşağıdaki şekilde gösterildiği gibi. Kök ad alanı tarafından tanımlanan [Namespace deyimi](/dotnet/visual-basic/language-reference/statements/namespace-statement) kaynak kodunda.

   ![Visual Basic projesi için Proje Özellikleri iletişim kutusu](./media/lut-start/vb-properties.png)

1.  Seçin **derleme** > **Çözümü Derle** en üst düzey Visual Studio menüsünde. Visual Studio başarıyla kitaplığınızı oluşturması gerekir.

---

## <a name="create-the-test-project"></a>Test projesi oluşturma

Sonraki adım, test etmek için birim test projesi oluşturmaktır `StringLibrary` kitaplığı. Birim testleri, aşağıdaki adımları uygulayarak oluşturun:

# <a name="ctabcsharp"></a>[C#](#tab/csharp)
1. İçinde **Çözüm Gezgini**, sağ `UtilityLibraries` çözüm ve select **Ekle** > **yeni proje**.

1. İçinde **Yeni Proje Ekle** iletişim kutusunda Seç C# düğümünü seçip **.NET Core**.

   > [!NOTE]
   > Birim testleri, sınıf kitaplığı olarak aynı dilde yazmak zorunda değildir.

1. Seçin **birim testi projesi (.NET Core)** sağ bölmede, şablon ve girin `StringLibraryTests` içinde **adı** metin kutusunda, aşağıdaki şekilde gösterildiği gibi:

   ![** Ekleme yeni proje ** iletişim kutusu için birim test projesi](./media/lut-start/add-unit-test-cs.png)

1. Seçin **Tamam** projeyi oluşturmak için.

   > [!NOTE]
   > Bu kullanmaya başlama öğreticilerinde Live Unit Testing ile MSTest test çerçevesi kullanır. XUnit ve NUnit test çerçeveleri de kullanabilirsiniz.

1. Birim test projesi otomatik olarak test ettiği sınıf kitaplığı erişemez. Sınıf kitaplığı projesine bir başvuru ekleyerek, test kitaplığı erişimi sağlar. Bunu yapmak için sağ `StringLibraryTests` seçin ve proje **Ekle** > **başvuru**. İçinde **başvuru Yöneticisi** iletişim kutusunda, emin **çözüm** sekmesi seçili ve select `StringLibrary` aşağıdaki şekilde gösterildiği gibi proje.

   ![** ** Başvuru Yöneticisi iletişim kutusu](./media/lut-start/add-reference.png)

1. Aşağıdaki kod ile şablon tarafından sağlanan Demirbaş birim testi kodu değiştirin:

   [!code-csharp[StringLibraryTest source code](samples/snippets/csharp/lut-start/unittest1.cs)]

1. Seçerek projenizi kaydetmek **Kaydet** araç çubuğundaki simgeye.

1. Birim testi kod bazı ASCII olmayan karakterler içeren, Visual Studio bize kendi varsayılan ASCII biçiminde dosyayı kaydederseniz şu bazı karakterler kaybolur uyarmak için aşağıdaki iletişim kutusunu görüntüler. Seçin **diğer kodlama ile Kaydet** düğmesi.

   ![Dosya kodlama seçin](media/lut-start/ascii-encoding.png)

1. İçinde **kodlama** aşağı açılan listesi **Gelişmiş kaydetme seçenekleri** iletişim kutusunda seçin **Unicode (UTF-8 imza olmadan) - kod sayfası 65001**aşağıdaki şekilde gösterildiği gibi:

   ![UTF-8 kodlaması seçme](media/lut-start/utf8-encoding.png)

1. Birim test projesi seçerek derleyin **derleme** > **çözümü yeniden derle** en üst düzey Visual Studio menüsünde.

# <a name="visual-basictabvisual-basic"></a>[Visual Basic](#tab/visual-basic)

1. İçinde **Çözüm Gezgini**, sağ `UtilityLibraries` çözüm ve select **Ekle** > **yeni proje**.

1. İçinde **Yeni Proje Ekle** iletişim kutusunda Visual Basic düğümünü seçin ve ardından **.NET Core**.

   > [!NOTE]
   > Birim testleri, sınıf kitaplığı olarak aynı dilde yazmak zorunda değildir.

1. Seçin **birim testi projesi (.NET Core)** sağ bölmede, şablon ve girin `StringLibraryTests` içinde **adı** metin kutusunda, aşağıdaki şekilde gösterildiği gibi:

   ![** Ekleme yeni proje ** iletişim kutusu için birim testi](./media/lut-start/add-unit-test-vb.png)

1. Seçin **Tamam** projeyi oluşturmak için.

   > [!NOTE]
   > Bu kullanmaya başlama öğreticilerinde Live Unit Testing ile MSTest test çerçevesi kullanır. XUnit ve NUnit test çerçeveleri de kullanabilirsiniz.

1. Birim test projesi otomatik olarak test ettiği sınıf kitaplığı erişemez. Sınıf kitaplığı projesine bir başvuru ekleyerek, test kitaplığı erişimi sağlar. Bunu yapmak için sağ `StringLibraryTests` seçin ve proje **Ekle** > **başvuru**. İçinde **başvuru Yöneticisi** iletişim kutusunda, emin **çözüm** sekmesi seçili ve select `StringLibrary` aşağıdaki şekilde gösterildiği gibi proje.

   ![** ** Başvuru Yöneticisi iletişim kutusu](./media/lut-start/add-reference.png)

1. Aşağıdaki kod ile şablon tarafından sağlanan Demirbaş birim testi kodu değiştirin:

   [!code-vb[StringLibraryTest source code](samples/snippets/visual-basic/lut-start/unittest1.vb)]

1. Seçerek projenizi kaydetmek **Kaydet** araç çubuğundaki simgeye.

1. Birim testi kod bazı ASCII olmayan karakterler içeren, Visual Studio bize kendi varsayılan ASCII biçiminde dosyayı kaydederseniz şu bazı karakterler kaybolur uyarmak için aşağıdaki iletişim kutusunu görüntüler. Seçin **diğer kodlama ile Kaydet** düğmesi.

   ![Dosya kodlama seçin](media/lut-start/ascii-encoding.png)

1. İçinde **kodlama** aşağı açılan listesi **Gelişmiş kaydetme seçenekleri** iletişim kutusunda seçin **Unicode (UTF-8 imza olmadan) - kod sayfası 65001**aşağıdaki şekilde gösterildiği gibi:

   ![UTF-8 kodlaması seçme](media/lut-start/utf8-encoding.png)

1. Birim test projesi tarafından derleme **derleme** > **çözümü yeniden derle** en üst düzey Visual Studio menüsünde.

---

Bunun için bir sınıf kitaplığı ve bunun yanı sıra bazı birim testlerinin oluşturdunuz. Live Unit Testing kullanmak için gereken hazırlık aşamaları artık tamamladınız.

## <a name="enable-live-unit-testing"></a>Live Unit Testing etkinleştir

Şimdiye, testler için yazdığınız rağmen `StringLibrary` sınıf kitaplığı, henüz yürütülen bunları. Etkinleştirdikten sonra Live Unit Testing bunları otomatik olarak yürütür. Bunu yapmak için aşağıdakileri yapın:

1. İsteğe bağlı olarak, kodu içeren kod penceresi seçin `StringLibrary`. Bu *Class1.cs* bir C# projesi için veya *Class1.vb* Visual Basic projesi için. (Bu adım, Live Unit Testing etkinleştirdikten sonra testlerinizi sonucunu ve kod kapsamınızla kapsamını görsel olarak incelemenize olanak.)

1. Seçin **Test** > **Live Unit Testing** > **Başlat** en üst düzey Visual Studio menüsünde.

1. Canlı birim testlerinizi otomatik olarak çalışan Test, Visual Studio başlatılır.

Testlerinizi çalıştıran tamamlandığında **Test Gezgini** hem genel sonuçları, hem de tek tek testlerin sonuçlarını görüntüler. Ayrıca, kod penceresi grafik, test kod kapsamı hem testleriniz için sonuç görüntüler. Aşağıdaki şekilde gösterildiği gibi üç testi başarıyla yürüttünüz. Ayrıca testlerimizin tüm kod yollarında kapsamına gösterir `StartsWithUpper` yöntemi ve başarılı bir şekilde yürütüldü bu testlerin tümü ("✓" Yeşil onay işaretiyle belirtilir). Son olarak, bu diğer yöntemlerden hiçbiri gösteren `StringLibrary` (Bu, "➖" gibi mavi bir çizgi gösterilir) kod kapsamı vardır.

# <a name="ctabcsharp"></a>[C#](#tab/csharp)
![Live Unit testing'i başlatma sonra Test Gezgini ve kod penceresi](media/lut-start/lut-results-cs.png)

# <a name="visual-basictabvisual-basic"></a>[Visual Basic](#tab/visual-basic)
![Live Unit testing'i başlatma sonra Test Gezgini ve kod penceresi](media/lut-start/lut-results-vb.png)

---

Kod penceresinde belirli kod kapsamı simgesini seçerek kapsamı ve test sonuçlarını test hakkında daha ayrıntılı bilgiler de alabilirsiniz. Bu ayrıntılı incelemek için aşağıdakileri yapın:

# <a name="ctabcsharp"></a>[C#](#tab/csharp)
1. Yeşil bir onay işareti yazan satıra tıklayın `if (String.IsNullOrWhiteSpace(s))` içinde `StartsWithUpper` yöntemi. Aşağıdaki şekilde gösterildiği gibi Live Unit Testing üç testleri kodun o satırına kapsar ve tüm başarıyla yürüttünüz gösterir.

   !['If' koşul deyimi için kod kapsamı](media/lut-start/code-coverage-cs1.png)

1. Yeşil bir onay işareti yazan satıra tıklayın `return Char.IsUpper(s[0])` içinde `StartsWithUpper` yöntemi. Aşağıdaki şekilde gösterildiği gibi Live Unit Testing yalnızca iki testten kodun o satırına kapsar ve tüm başarıyla yürüttünüz gösterir.

   ![Return deyimi için kod kapsamı](media/lut-start/code-coverage-cs2.png)

# <a name="visual-basictabvisual-basic"></a>[Visual Basic](#tab/visual-basic)
1. Yeşil bir onay işareti yazan satıra tıklayın `If (String.IsNullOrWhiteSpace(s)) Then` içinde `StartsWithUpper` yöntemi. Aşağıdaki şekilde gösterildiği gibi Live Unit Testing üç testleri kodun o satırına kapsar ve tüm başarıyla yürüttünüz gösterir.

   !['If' koşul deyimi için kod kapsamı](media/lut-start/code-coverage-vb1.png)

1. Yeşil bir onay işareti yazan satıra tıklayın `Return Char.IsUpper(s(0))` içinde `StartsWithUpper` yöntemi. Aşağıdaki şekilde gösterildiği gibi Live Unit Testing yalnızca iki testten kodun o satırına kapsar ve tüm başarıyla yürüttünüz gösterir.

   ![Return deyimi için kod kapsamı](media/lut-start/code-coverage-vb2.png)

---

Live Unit Testing tanımlayan önemli bir sorun tamamlanmamış kod kapsamı ' dir. Sonraki bölümde karşılayabilirsiniz.

## <a name="expand-test-coverage"></a>Test kapsamı genişletin

Birim testleriniz genişletmek Bu bölümde, `StartsWithLower` yöntemi. Bunu, ancak Live Unit Testing dinamik olarak kodunuzu test etmek devam eder.

Kod kapsamını genişletmek için `StartsWithLower` yöntemi, aşağıdakileri yapın:

# <a name="ctabcsharp"></a>[C#](#tab/csharp)
1. Aşağıdaki `TestStartsWithLower` ve `TestDoesNotStartWithLower` projenizin test kaynak kodunu yöntemleri:

    [!code-csharp[StringLibraryTest source code](samples/snippets/csharp/lut-start/unittest2.cs#1)]

1. Değiştirme `DirectCallWithNullOrEmpty` yöntem çağrısının hemen sonra aşağıdaki kodu ekleyerek [ `Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsFalse` ](/dotnet/api/microsoft.visualstudio.testtools.unittesting.assert.isfalse) yöntemi.

    [!code-csharp[StringLibraryTest source code](samples/snippets/csharp/lut-start/unittest2.cs#2)]

1. Kaynak kodunuzu değiştirdiğinizde Live Unit Testing yeni ve değiştirilen testleri otomatik olarak yürütür. Aşağıdaki şekil olarak **Test Gezgini** gösterir, tüm testleri eklediğiniz iki ve değişiklik, bir tane de dahil olmak üzere, başarılı.

   ![Test kapsamını genişleterek sonra Test Gezgini.](media/lut-start/test-dynamic.png)

1. Geçiş için kaynak kodu içeren bir pencere için `StringLibrary` sınıfı. Live Unit Testing bizim kod kapsamı için genişletilmiş şimdi gösterir `StartsWithLower` yöntemi.

    ![Kod kapsamı StartsWithLower yöntemi](media/lut-start/lut-extended-cs.png)

# <a name="visual-basictabvisual-basic"></a>[Visual Basic](#tab/visual-basic)
1. Aşağıdaki `TestStartsWithLower` ve `TestDoesNotStartWithLower` projenizin test kaynak kodunu yöntemleri:

    [!code-vb[StringLibraryTest source code](samples/snippets/visual-basic/lut-start/unittest2.vb#1)]

1. Değiştirme `DirectCallWithNullOrEmpty` yöntem çağrısının hemen sonra aşağıdaki kodu ekleyerek [ `Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsFalse` ](/dotnet/api/microsoft.visualstudio.testtools.unittesting.assert.isfalse) yöntemi.

    [!code-vb[StringLibraryTest source code](samples/snippets/visual-basic/lut-start/unittest2.vb#2)]

1. Kaynak kodunuzu değiştirdiğinizde Live Unit Testing yeni ve değiştirilen testleri otomatik olarak yürütür. Aşağıdaki şekil olarak **Test Gezgini** gösterir, tüm testleri eklediğiniz iki ve değişiklik, bir tane de dahil olmak üzere, başarılı.

   ![Test kapsamını genişleterek sonra Test Gezgini.](media/lut-start/test-dynamic.png)

1. Geçiş için kaynak kodu içeren bir pencere için `StringLibrary` sınıfı. Live Unit Testing bizim kod kapsamı için genişletilmiş şimdi gösterir `StartsWithLower` yöntemi.

    ![StartsWithLower için kod kapsamı](media/lut-start/lut-extended-vb.png)

---

Bazı durumlarda, başarılı testler **Test Gezgini** grileştirilmiş olabilir. Bir test şu anda yürütülmekte olan veya son yürütülen olduğundan test olduğundan, kod değişiklikleri yeniden çalıştırılamayan test erişememeleri gösterir.

Şu ana kadar tüm yaptığımız testleri başarılı olduğunda. Sonraki bölümde, test hatası nasıl işleyebileceğini inceleyeceğiz.

## <a name="handle-a-test-failure"></a>Test hatası işleme

Bu bölümde, nasıl Live Unit Testing belirlemek, sorun giderme ve test hatalarını gidermek için kullanabileceğiniz hakkında bilgi edineceksiniz. İçin test kapsamını genişleterek bunu yaparsınız `HasEmbeddedSpaces` yöntemi.

# <a name="ctabcsharp"></a>[C#](#tab/csharp)
1. Test dosyanıza aşağıdaki yöntemi ekleyin:

    [!code-csharp[The TestHasEmbeddedSpaces test method](samples/snippets/csharp/lut-start/unittest2.cs#3)]

1. Test yürütüldüğünde, Live Unit Testing belirten `TestHasEmbeddedSpaces` yöntemi başarısız olmuşsa, aşağıdaki şekilde gösterildiği gibi:

   ![Başarısız bir test bildirimi Test Gezgini.](media/lut-start/test-failure.png)

1. Kitaplık kodu görüntüler penceresi seçin. Live Unit Testing kod kapsamı için genişletmiştir Not `HasEmbeddedSpaces` yöntemi. Kırmızı ekleyerek de test hatası raporları "🞩" testler başarısız tarafından kapsanan satırlar için.

1. Satırı üzerine `HasEmbeddedSpaces` metodu imzası. Live Unit Testing yöntemi aşağıdaki şekilde gösterildiği gibi bir test tarafından kapsanan raporları bir araç ipucu görüntülenir:

   ![Live Unit Testing başarısız bir test hakkında bilgiler.](media/lut-start/test-failure-info-cs.png)

1. Başarısız seçin **TestHasEmbeddedSpaces** test edin. Live Unit Testing sunar, birçok seçenek, tüm testler, select testleri çalıştırmak, tüm testlerde hata ayıklama ve hata ayıklama gibi testler, aşağıdaki şekilde seçtiğiniz gösterilir unutmayın:

   ![Live Unit Testing başarısız bir test için Seçenekler.](media/lut-start/test-failure-options.png)

1. Seçin **seçili hata ayıklama** başarısız test hatalarını ayıklamak için.

1. Visual Studio test hata ayıklama modunda yürütülür. Bizim test bir dizideki her bir dizenin adlı bir değişkene atar. `phrase` ve buna ileten `HasEmbeddedSpaces` yöntemi. Program yürütme duraklatır ve hata ayıklayıcı ilk saat onayı ifade çağırır `false`. Beklenmeyen değerinden sonuçları özel durum iletişim [ `Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsTrue` ](/dotnet/api/microsoft.visualstudio.testtools.unittesting.assert.istrue) yöntemi çağrısı, aşağıdaki şekilde gösterilmiştir.

   ![Live Unit Testing özel durum iletişim.](media/lut-start/exception-dialog-cs.png)

   Ayrıca, tüm sağlayan Visual Studio hata ayıklama araçlarını aşağıdaki şekilde gösterildiği gibi bizim başarısız test giderme yardımcı olmak mevcuttur:

   ![Visual Studio hata ayıklama araçları.](media/lut-start/debugging-tools-cs.png)

   İçinde Not **Otolar** penceresi, değerini `phrase` değişkeni "Name\tDescription" olduğu dizinin ikinci öğesi ise. Test yöntemi bekliyor `HasEmbeddedSpaces` döndürülecek `true` bunun yerine, bu dize; geçirildiğinde döndürür `false`. Evidently, onu sekme karakteri, "\t", katıştırılmış bir boşluk algılamaz.

1. Seçin **hata ayıklama** > **devam**, basın **F5**, veya **devam** yürütmeye devam araç çubuğunda Test programı. İşlenmeyen bir özel durum oluştuğundan test sonlandırır.

# <a name="visual-basictabvisual-basic"></a>[Visual Basic](#tab/visual-basic)
1. Test dosyanıza aşağıdaki yöntemi ekleyin:

    [!code-vb[The TestHasEmbeddedSpaces test method](samples/snippets/visual-basic/lut-start/unittest2.vb#3)]

1. Test yürütüldüğünde, Live Unit Testing belirten `TestHasEmbeddedSpaces` yöntemi başarısız olmuşsa, aşağıdaki şekilde gösterildiği gibi:

   ![Başarısız bir test bildirimi Test Gezgini.](media/lut-start/test-failure.png)

1. Kitaplık kodu görüntüler penceresi seçin. Live Unit Testing kod kapsamı için genişletmiştir Not `HasEmbeddedSpaces` yöntemi. Kırmızı ekleyerek de test hatası raporları "🞩" testler başarısız tarafından kapsanan satırlar için.

1. Satırı üzerine `HasEmbeddedSpaces` metodu imzası. Live Unit Testing yöntemi aşağıdaki şekilde gösterildiği gibi bir test tarafından kapsanan raporları bir araç ipucu görüntülenir:

   ![Live Unit Testing başarısız bir test hakkında bilgiler.](media/lut-start/test-failure-info-vb.png)

1. Başarısız seçin **TestHasEmbeddedSpaces** test edin. Live Unit Testing sunar, birçok seçenek, tüm testler, seçilen testleri çalıştırmak, tüm testlerde hata ayıklama ve hata ayıklama gibi testler, aşağıdaki şekilde seçtiğiniz gösterilir unutmayın:

   ![Live Unit Testing başarısız bir test için Seçenekler.](media/lut-start/test-failure-options.png)

1. Seçin **seçili hata ayıklama** başarısız test hatalarını ayıklamak için.

1. Visual Studio test hata ayıklama modunda yürütülür. Bizim test bir dizideki her bir dizenin adlı bir değişkene atar. `phrase` ve buna ileten `HasEmbeddedSpaces` yöntemi. Program yürütme duraklatır ve hata ayıklayıcı ilk saat onayı ifade çağırır `false`. Beklenmeyen değerinden sonuçları özel durum iletişim [ `Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsTrue` ](/dotnet/api/microsoft.visualstudio.testtools.unittesting.assert.istrue) yöntemi çağrısı, aşağıdaki şekilde gösterilmiştir.

   ![Live Unit Testing özel durum iletişim.](media/lut-start/exception-dialog-vb.png)

   Ayrıca, tüm sağlayan Visual Studio hata ayıklama araçlarını aşağıdaki şekilde gösterildiği gibi bizim başarısız test giderme yardımcı olmak mevcuttur:

   ![Visual Studio hata ayıklama araçları.](media/lut-start/debugging-tools-vb.png)

   İçinde Not **Otolar** penceresi, değerini `phrase` değişkeni olan "Name" + vbTab dizinin ikinci öğe ise "Description". Test yöntemi bekliyor `HasEmbeddedSpaces` döndürülecek `true` bunun yerine, bu dize; geçirildiğinde döndürür `false`. Evidently, onu sekme karakterinin katıştırılmış bir boşluk algılamaz.

1. Seçin **hata ayıklama** > **devam**, basın **F5**, veya **devam** yürütmeye devam araç çubuğunda Test programı. İşlenmeyen bir özel durum oluştuğundan test sonlandırır.

---

Bu hatanın bir ön araştırma için yeterli bilgi sağlar. Her iki `TestHasEmbeddedSpaces` (test yordamı) yapılan yanlış bir varsayım veya `HasEmbeddedSpaces` doğru tüm gömülü boşluklar tanımıyor. Tanılama ve sorun gidermek için başlayın `StringLibrary.HasEmbeddedSpaces` yöntemi:

# <a name="ctabcsharp"></a>[C#](#tab/csharp)
1. Karşılaştırmada bakın `HasEmbeddedSpaces` yöntemi. Bunu, U + 0020 olmasını katıştırılmış bir boşluk olarak kabul eder. Ancak, Unicode standardı diğer boşluk karakterleri içerir. Bu, kitaplık kodu yanlış bir boşluk karakteri sınadığı önerir.

1. Eşitlik karşılaştırma çağrısı ile Değiştir <xref:System.Char.IsWhiteSpace%2A?displayProperty=fullName> yöntemi:

    [!code-csharp[The TestHasEmbeddedSpaces test method](samples/snippets/csharp/lut-start/program2.cs#1)]

1. Otomatik olarak başarısız test yöntemi yeniden çalıştırır Live Unit Testing ve güncelleştirmeleri kod penceresinde hem de sonuçları **Test Gezgini**aşağıdaki şekilde gösterildiği gibi:

    ![Başarılı HasEmbeddedSpaces test.](media/lut-start/test-success-cs.png)

# <a name="visual-basictabvisual-basic"></a>[Visual Basic](#tab/visual-basic)
1. Karşılaştırmada bakın `HasEmbeddedSpaces` yöntemi. Bunu, U + 0020 olmasını katıştırılmış bir boşluk olarak kabul eder. Ancak, Unicode standardı diğer boşluk karakterleri içerir. Bu, kitaplık kodu yanlış bir boşluk karakteri sınadığı önerir.

1. Eşitlik karşılaştırma çağrısı ile Değiştir <xref:System.Char.IsWhiteSpace%2A?displayProperty=fullName> yöntemi:

    [!code-vb[The TestHasEmbeddedSpaces test method](samples/snippets/visual-basic/lut-start/class2.vb#1)]

1. Otomatik olarak yeniden başarısız test metodunu çalıştırır Live Unit Testing ve güncelleştirmeleri kod penceresinde hem de sonuçları **Test Gezgini**aşağıdaki şekilde gösterildiği gibi:

    ![Başarılı HasEmbeddedSpaces test.](media/lut-start/test-success-vb.png)

---

## <a name="see-also"></a>Ayrıca bkz.
- [Visual Studio Live Unit Testing](live-unit-testing.md)
- [Live Unit Testing sık sorulan sorular](live-unit-testing-faq.md)
