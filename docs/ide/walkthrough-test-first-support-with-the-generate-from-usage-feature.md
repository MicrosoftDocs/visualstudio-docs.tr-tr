---
title: 'İzlenecek yol: Kullanımdan oluşturma özelliği ile önce Test geliştirmesi'
ms.date: 10/09/2017
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
dev_langs:
- VB
- CSharp
ms.topic: conceptual
helpviewer_keywords:
- Generate From Usage
- Test-First Development
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c500f7a245ffd3a0dec175dd5f016cf1b2596fa4
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49821496"
---
# <a name="walkthrough-test-first-development-with-the-generate-from-usage-feature"></a>İzlenecek yol: Kullanımdan oluşturma özelliği ile önce Test geliştirmesi

Bu konu nasıl kullanılacağını gösterir [kullanımından Oluştur](../ide/visual-csharp-intellisense.md#generate-from-usage) önce test geliştirmesi destekler özelliğine sahiptir.

 *Test öncelikli geliştirme* , ilk ürün belirtimlerini temel birim testleri yazma ve ardından başarılı testler yapmak için gereken kaynak kodunu yazma yazılım tasarımı bir yaklaşımdır. Visual Studio tanımlanmadan önce ilk önce bunları test çalışmalarınızı başvurduğunuzda yeni türler ve üyeler kaynak kodunda oluşturarak önce test geliştirmesi destekler.

 Visual Studio, yeni türler ve üyeler, iş akışı için minimum kesintiyle oluşturur. Geçerli konumunuzu kodda çıkmadan türleri, yöntemler, özellikler, alanlar veya oluşturucular için saplamalar oluşturabilirsiniz. Tür oluşturma için seçenekleri belirtmek için bir iletişim kutusunu açtığınızda, iletişim kutusu kapandığında odağı geçerli açık dosya için hemen döndürür.

 **Kullanımından Oluştur** özelliği, Visual Studio ile tümleştirme test çerçeveleri ile kullanılabilir. Bu konu başlığında, Microsoft birim testi çerçevesi gösterilmiştir.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

### <a name="create-a-windows-class-library-project-and-a-test-project"></a>Windows sınıf kitaplığı projesi ve bir Test projesi oluşturma

1. İçinde [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] veya [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)], yeni bir **Windows sınıf kitaplığı** proje. Adlandırın `GFUDemo_VB` veya `GFUDemo_CS`hangi dil, kullanmakta olduğunuz bağlı olarak.

2. İçinde **Çözüm Gezgini**, çözüm simgesine sağ tıklayın, seçin **Ekle**ve ardından **yeni proje**. Sol bölmesinde **yeni proje** iletişim kutusunda **Test**.

3. Orta bölmede seçin **birim testi projesi** ve varsayılan adını kabul `UnitTestProject1`. Görünür olduğunda iletişim kutusunda aşağıdaki çizimde [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)]. İçinde [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)], iletişim kutusuna benzer.

    ![Yeni Test projesi iletişim kutusu](../ide/media/newproject_test.png)

4. Seçin **Tamam** kapatmak için **yeni proje** iletişim kutusu.

### <a name="add-a-reference-to-the-class-library-project"></a>Sınıf kitaplığı projesine bir başvuru ekleyin

1.  İçinde **Çözüm Gezgini**, altında birim testi projesi, sağ **başvuruları** girişi ve **Başvuru Ekle**.

2.  İçinde **başvuru Yöneticisi** iletişim kutusunda **projeleri** ve sınıf kitaplığı Projesi'ni seçin.

3.  Seçin **Tamam** kapatmak için **başvuru Yöneticisi** iletişim kutusu.

4.  Çözümünüzü kaydedin. Artık testleri yazmaya başlamak hazırsınız.

### <a name="generate-a-new-class-from-a-unit-test"></a>Yeni bir sınıf bir birim testi oluşturma

1. Adlı bir dosyaya test projesini içeren *UnitTest1*. Bu dosyayı çift **Çözüm Gezgini** Kod Düzenleyicisi'nde açın. Bir test sınıfı ve test yöntemi üretilmedi.

2. Sınıf bildirimi bulun `UnitTest1` ve yeniden adlandırın `AutomobileTest`.

   > [!NOTE]
   >  IntelliSense için IntelliSense deyim tamamlamada artık iki seçenek sunar: *tamamlama modunu* ve *öneri modu*. Öneri Modu tanımlanmadan önce sınıflar ve üyeler kullanılır durumlar için kullanın. Olduğunda bir **IntelliSense** penceresi açıksa, basabilirsiniz **Ctrl**+**Alt**+**alanı** arasında geçiş yapmak için tamamlama modu ile öneri modu. Bkz: [kullanım IntelliSense](../ide/using-intellisense.md) daha fazla bilgi için. Öneri Modu yardımcı olacak yazarken `Automobile` sonraki adımda.

3. Bulun `TestMethod1()` yöntemi ve yeniden adlandırın `DefaultAutomobileIsInitializedCorrectly()`. Bu yöntemde, bir sınıf adlı yeni bir örneğini oluşturma `Automobile`aşağıdaki ekran görüntülerinde gösterildiği gibi. Bir derleme zamanı hatası gösteren dalgalı çizgi görünür ve bir [hızlı Eylemler](../ide/quick-actions.md) ampul sol kenar boşluğunda görünür (C# yalnızca), veya üzerine gelin, doğrudan dalgalı çizgi altında.

    ![Visual Basic'te hızlı Eylemler](../ide/media/genclass_underlinevb.png)

    ![C'de hızlı Eylemler&#35;](../ide/media/genclass_underline.png)

4. Seçin veya tıklatın **hızlı Eylemler** ampul. Bildiren bir hata iletisi görürsünüz türü `Automobile` tanımlı değil. Ayrıca, bazı çözümleri ile sunulur.

5. Tıklayın **yeni tür oluşturma** açmak için **oluşturma türü** iletişim kutusu. Bu iletişim kutusu içeren farklı bir proje türü oluşturma seçenekleri sunar.

6. İçinde **proje** listesinde **GFUDemo\_VB** veya **GFUDemo_CS** test yerine sınıf kitaplığı projesi dosyası eklemek için Visual Studio istemek için Proje. Henüz seçili değilse **yeni dosya oluştur** ve adlandırın *Automobile.cs* veya *Automobile.vb*.

     ![Yeni türü iletişim kutusu oluşturma](../ide/media/genotherdialog.png)

7. Tıklayın **Tamam** iletişim kutusunu kapatmak ve yeni bir dosya oluşturun.

8. İçinde **Çözüm Gezgini**, altına bakın **GFUDemo_VB** veya **GFUDemo_CS** doğrulamak için proje düğümünü yeni *Automobile.vb* veya  *Automobile.cs* dosyasıdır vardır. Kod Düzenleyicisi'nde odağı hala kullanımda `AutomobileTest.DefaultAutomobileIsInitializedCorrectly`, kesinti en az test yazma devam sağlar.

### <a name="generate-a-property-stub"></a>Bir özellik taslağı oluşturmak
Ürün belirtimi belirten varsayar `Automobile` sınıfında adlı iki genel özelliği `Model` ve `TopSpeed`. Bu özellikler varsayılan değerleri ile başlatılmalıdır `"Not specified"` ve `-1` varsayılan oluşturucu tarafından. Aşağıdaki birim sınama, varsayılan oluşturucu doğru varsayılan değerlerine özelliklerini ayarlar doğrular.

1. Aşağıdaki kod satırını ekleyin `DefaultAutomobileIsInitializedCorrectly` test metodu.

     [!code-csharp[VbTDDWalkthrough#1](../ide/codesnippet/CSharp/walkthrough-test-first-support-with-the-generate-from-usage-feature_1.cs)]
     [!code-vb[VbTDDWalkthrough#1](../ide/codesnippet/VisualBasic/walkthrough-test-first-support-with-the-generate-from-usage-feature_1.vb)]

2. Kod üzerinde iki tanımlanmamış özelliklere başvurduğundan `Automobile`, altında dalgalı çizgi görünüyor `Model` ve `TopSpeed`. Üzerine `Model` ve **hızlı Eylemler** ampul ve ardından **'Automobile.Model' özelliğini üret**.

3. İçin bir özellik taslağı oluşturmak `TopSpeed` özelliği aynı şekilde.

     İçinde `Automobile` sınıfı, yeni özelliklerin türleri doğru bağlamdan sonuçlandı.

### <a name="generate-a-stub-for-a-new-constructor"></a>Yeni bir oluşturucu için bir saplama oluşturun
Şimdi başlatmak için bir oluşturucu saptama oluşturacaktır bir test yöntemi oluşturacağız `Model` ve `TopSpeed` özellikleri. Daha sonra test tamamlamak için daha fazla kod ekleyeceksiniz.

1. Aşağıdaki ek test yöntemine ekleyin, `AutomobileTest` sınıfı.

     [!code-csharp[VbTDDWalkthrough#2](../ide/codesnippet/CSharp/walkthrough-test-first-support-with-the-generate-from-usage-feature_2.cs)]
     [!code-vb[VbTDDWalkthrough#2](../ide/codesnippet/VisualBasic/walkthrough-test-first-support-with-the-generate-from-usage-feature_2.vb)]

2.  Tıklayın **hızlı Eylemler** ampul altında kırmızı dalgalı oku ve ardından **'Otomobil' Oluşturucu üret**.

     İçinde `Automobile` sınıf dosyası, yeni oluşturucuyu Oluşturucusu çağrısında kullanılan yerel değişkenlerin adlarını incelenmiştir dikkat edin, aynı adlara sahip özellikler bulundu `Automobile` sınıf ve oluşturucu gövdesinde için sağlanan kod bağımsız değişken değerleri depolamak `Model` ve `TopSpeed` özellikleri.


3.  Yeni oluşturucuyu oluşturduktan sonra varsayılan oluşturucu çağrısı altında dalgalı çizgi görünür `DefaultAutomobileIsInitializedCorrectly`. Hata iletisi `Automobile` sınıfın sıfır bağımsız değişken alan hiçbir oluşturucu vardır. Parametreleri olmayan bir açık bir varsayılan oluşturucu oluşturmak için tıklayın **hızlı Eylemler** ampul ve ardından **'Otomobil' Oluşturucu üret**.

### <a name="generate-a-stub-for-a-method"></a>Bir yöntem Saplaması
Belirtimi belirten varsayar yeni bir `Automobile` içine koyabilirsiniz bir `IsRunning` , durum, `Model` ve `TopSpeed` özellikleri için varsayılan değerlerin dışında bir şey ayarlanır.

1. Aşağıdaki satırları ekleyin `AutomobileWithModelNameCanStart` yöntemi.

     [!code-csharp[VbTDDWalkthrough#3](../ide/codesnippet/CSharp/walkthrough-test-first-support-with-the-generate-from-usage-feature_3.cs)]
     [!code-vb[VbTDDWalkthrough#3](../ide/codesnippet/VisualBasic/walkthrough-test-first-support-with-the-generate-from-usage-feature_3.vb)]

2.  Tıklayın **hızlı Eylemler** ampul için `myAuto.Start` yöntemi çağırın ve ardından **'Automobile.Start' metodunu üret**.

3.  Tıklayın **hızlı Eylemler** ampul için `IsRunning` özelliği ve ardından **'Automobile.IsRunning' özelliğini üret**.

     `Automobile` Sınıf adlı bir yöntem artık içeren `Start()` ve adlı bir özellik `IsRunning`.

### <a name="run-the-tests"></a>Testleri çalıştırın

1.  Üzerinde **Test** menüsünde seçin **çalıştırma** > **tüm testleri**.

     **Çalıştırma** > **tüm testleri** komut için geçerli çözüm yazılan tüm test çerçeveleri tüm testleri çalıştırır. Bu durumda, iki test, ve her ikisi de beklendiği gibi başarısız olur. `DefaultAutomobileIsInitializedCorrectly` Test başarısız çünkü `Assert.IsTrue` koşul döndürür `False`. `AutomobileWithModelNameCanStart` Test başarısız çünkü `Start` yönteminde `Automobile` sınıfı bir özel durum oluşturur.

     **Test sonuçlarını** penceresi, aşağıdaki çizimde gösterilmiştir.

     ![Başarısız olan test sonuçları](../ide/media/testsfailed.png)

2.  İçinde **Test sonuçları** penceresi, her test sonucu sırada her test konuma gitmek için çift tıklatın.

### <a name="implement-the-source-code"></a>Uygulama kaynak kodu

1.  Aşağıdaki kod için varsayılan oluşturucu bu nedenle, ekleme `Model`, `TopSpeed` ve `IsRunning` özellikleri tüm başlatıldığı için doğru varsayılan değerleri `"Not specified"`, `-1`, ve `False` (veya `false` için C#).

     [!code-csharp[VbTDDWalkthrough#5](../ide/codesnippet/CSharp/walkthrough-test-first-support-with-the-generate-from-usage-feature_5.cs)]
     [!code-vb[VbTDDWalkthrough#5](../ide/codesnippet/VisualBasic/walkthrough-test-first-support-with-the-generate-from-usage-feature_5.vb)]

2.  Zaman `Start` yöntemi çağrıldığında, ayarlamanız gerekir `IsRunning` bayrak yalnızca gerekirse true `Model` veya `TopSpeed` özellikleri varsayılan değerlerine dışında bir şey ayarlanır. Kaldırma `NotImplementedException` yönteminden gövde ve aşağıdaki kodu ekleyin.

     [!code-csharp[VbTDDWalkthrough#6](../ide/codesnippet/CSharp/walkthrough-test-first-support-with-the-generate-from-usage-feature_6.cs)]
     [!code-vb[VbTDDWalkthrough#6](../ide/codesnippet/VisualBasic/walkthrough-test-first-support-with-the-generate-from-usage-feature_6.vb)]

### <a name="run-the-tests-again"></a>Testleri yeniden çalıştırın

- Üzerinde **Test** menüsünde **çalıştırma**ve ardından **tüm testleri**.

     Şu testler başarılı. **Test sonuçlarını** penceresi, aşağıdaki çizimde gösterilmiştir.

     ![Başarılı olan test sonuçları](../ide/media/testspassed.png)

## <a name="see-also"></a>Ayrıca bkz.

- [Kullanımdan oluştur](../ide/visual-csharp-intellisense.md#generate-from-usage)
- [Kod Düzenleyicisi özellikleri](../ide/writing-code-in-the-code-and-text-editor.md)
- [IntelliSense kullanma](../ide/using-intellisense.md)
- [Birim testi kod](../test/unit-test-your-code.md)
- [Hızlı Eylemler](../ide/quick-actions.md)