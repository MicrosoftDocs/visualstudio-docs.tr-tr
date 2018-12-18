---
title: 'İzlenecek yol: İle önce Test desteği kullanımdan üret özelliği | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Generate From Usage
- Test-First Development
ms.assetid: 764c17a4-cd95-4c23-bf63-d92d9c5adfb2
caps.latest.revision: 68
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: b2b45b75b689279a19dc1423a0cbf2b62d14a5c1
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49232849"
---
# <a name="walkthrough-test-first-support-with-the-generate-from-usage-feature"></a>İzlenecek Yol: Kullanımdan Üret Özelliği ile Önce Test Desteği
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu konu nasıl kullanılacağını gösterir [kullanımından Oluştur](../misc/generate-from-usage.md) önce test geliştirmesi destekler özelliğine sahiptir.  
  
 *Test öncelikli geliştirme* , ilk ürün belirtimlerini temel birim testleri yazma ve ardından başarılı testler yapmak için gereken kaynak kodunu yazma yazılım tasarımı bir yaklaşımdır. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] destekleyen geliştirme tanımlanmadan önce ilk önce bunları test çalışmalarınızı başvurduğunuzda yeni türler ve üyeler kaynak kodunda oluşturarak önce test.  
  
 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] yeni türler ve üyeler, iş akışı için minimum kesintiyle oluşturur. Geçerli konumunuzu kodda çıkmadan türleri, yöntemler, özellikler, alanlar veya oluşturucular için saplamalar oluşturabilirsiniz. Tür oluşturma için seçenekleri belirtmek için bir iletişim kutusunu açtığınızda, iletişim kutusu kapandığında odağı geçerli açık dosya için hemen döndürür.  
  
 Kullanımından Oluştur özelliği ile tümleştirme test çerçeveleri ile kullanılabilir [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Bu konu başlığında, Microsoft birim testi çerçevesi gösterilmiştir.  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
### <a name="to-create-a-windows-class-library-project-and-a-test-project"></a>Windows sınıf kitaplığı projesi ve bir Test projesi oluşturmak için  
  
1.  İçinde [!INCLUDE[csprcs](../includes/csprcs-md.md)] veya [!INCLUDE[vbprvb](../includes/vbprvb-md.md)], yeni bir Windows sınıf kitaplığı projesi oluşturun. Adlandırın `GFUDemo_VB` veya `GFUDemo_CS`hangi dil, kullanmakta olduğunuz bağlı olarak.  
  
2.  İçinde **Çözüm Gezgini**, çözüm simgesine sağ tıklayın, fareyle **Ekle**ve ardından **yeni proje**. İçinde **yeni proje** iletişim kutusundaki **proje türleri** bölmesi sol tıklayın **Test**.  
  
3.  İçinde **şablonları** bölmesinde tıklayın **birim testi projesi** UnitTestProject1 varsayılan adını kabul edin. Görünür olduğunda iletişim kutusunda aşağıdaki çizimde [!INCLUDE[csprcs](../includes/csprcs-md.md)]. İçinde [!INCLUDE[vbprvb](../includes/vbprvb-md.md)], iletişim kutusuna benzer.  
  
     ![Yeni Test projesi iletişim kutusu](../ide/media/newproject-test.png "NewProject_Test")  
Yeni Proje iletişim kutusu  
  
4.  Tıklayın **Tamam** kapatmak için **yeni proje** iletişim kutusu.

5.  Sınıf projenizde, içinde **Çözüm Gezgini**, sağ **başvuruları** girişi ve tıklayın **Başvuru Ekle**.

6.  İçinde **başvuru Yöneticisi** iletişim kutusunda **projeleri** ve birim test projenizi seçin.

7.  Tıklayın **Tamam** kapatmak için **başvuru Yöneticisi** iletişim kutusu.

8.  İçinde **Class1** varolan son hemen sonra dosya **kullanarak** deyimleri Ekle bir **kullanarak** test projesi için bildirimi:

    * Visual Basic'te Ekle `Using UnitTestProject1`
    
    * C# ' ta Ekle `using UnitTestProject1;`
    
9.  Çözümünüzü kaydedin. Testleri yazmaya başlamak artık hazırsınız  
  
### <a name="to-generate-a-new-class-from-a-unit-test"></a>Bir birim testi yeni bir sınıf oluşturmak için  
  
1.  Test projesi UnitTest1 adlı bir dosya içerir. Bu dosyayı çift **Çözüm Gezgini** Kod Düzenleyicisi'nde açın. Bir test sınıfı ve test yöntemi üretilmedi.  
  
2.  Sınıf bildirimi bulun `UnitTest1` ve yeniden adlandırın `AutomobileTest`. C# ' ta, bir `UnitTest1()` Oluşturucusu varsa, yeniden adlandırın `AutomobileTest()`.  
  
    > [!NOTE]
    >  IntelliSense için IntelliSense deyim tamamlamada artık iki seçenek sunar: *tamamlama modunu* ve *öneri modu*. Öneri Modu tanımlanmadan önce sınıflar ve üyeler kullanılır durumlar için kullanın. Bir IntelliSense penceresinin açık olduğunda, tamamlama modu ile öneri modu arasında geçiş yapmak için CTRL + ALT + ARA ÇUBUĞU tuşlarına basabilirsiniz. Bkz: [IntelliSense kullanarak](../ide/using-intellisense.md) daha fazla bilgi için. Öneri Modu yardımcı olacak yazarken `Automobile` sonraki adımda.  
  
3.  Bulun `TestMethod1()` yöntemi ve yeniden adlandırın `DefaultAutomobileIsInitializedCorrectly()`. Bu yöntemde, bir sınıf adlı yeni bir örneğini oluşturma `Automobile`aşağıdaki resimlerde gösterildiği gibi. Bir derleme zamanı hatası gösteren dalgalı çizgi görünür ve akıllı etiket türü adı altında görünür. Akıllı etiket konumunu tam değişir, kullanmanıza bağlı olarak [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] veya [!INCLUDE[csprcs](../includes/csprcs-md.md)].  
  
     ![Akıllı etiket altı çizili Visual Basic'te](../ide/media/genclass-underlinevb.png "GenClass_UnderlineVB")  
Visual Basic  
  
     ![Akıllı etiket altı çizili C'de&#35;](../ide/media/genclass-underline.png "GenClass_Underline")  
Visual C#  
  
4.  Tür yok adlı olduğunu bildiren bir hata iletisini görmek için akıllı etiket üzerine fare işaretçisini `Automobile` henüz tanımlanır. Akıllı etiket tıklayın veya CTRL tuşuna basın. (CTRL + nokta) aşağıdaki resimlerde gösterildiği kullanımından Oluştur kısayol menüsünü açın.  
  
     ![Akıllı etiket bağlam menüsü Visual Basic'te](../ide/media/genclass-smartvb.png "GenClass_SmartVB")  
Visual Basic  
  
     ![Akıllı etiket bağlam menüsü C'de&#35;](../ide/media/genclass-smartcs.png "GenClass_SmartCS")  
Visual C#  
  
5.  Şimdi iki seçeneğiniz vardır. ' Ya tıklayarak **Oluştur 'Sınıf otomobil'** test projenizde yeni bir dosya oluşturun ve adlı boş bir sınıf ile doldurmak için `Automobile`. Bu, yeni bir sınıf geçerli projedeki varsayılan erişim değiştiricileri sahip yeni bir dosya oluşturmak için hızlı bir yoludur. Ayrıca **yeni tür oluşturma** açmak için **yeni tür Oluştur** iletişim kutusu. Bu sınıfın var olan bir dosyaya koymak ve dosyayı başka bir projeye ekleme içeren seçenekler sağlar.  
  
     Tıklayın **yeni tür oluşturma** açmak için **yeni tür Oluştur** iletişim kutusunda, aşağıdaki çizimde gösterilmiştir. İçinde **proje** listesinde **GFUDemo_VB** veya **GFUDemo_CS** istemek için [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] kaynak kod projesine test projesini yerine dosya eklemek için.  
  
     ![Yeni türü iletişim kutusu üretmek](../ide/media/genotherdialog.png "GenOtherDialog")  
Yeni türü iletişim kutusu oluşturma  
  
6.  Tıklayın **Tamam** iletişim kutusunu kapatmak ve yeni bir dosya oluşturun.  
  
7.  İçinde **Çözüm Gezgini**, doğrulamak için GFUDemo_VB veya GFUDemo_CS proje düğümünde yeni Automobile.vb arayın veya Automobile.cs dosyasıdır vardır. Kod Düzenleyicisi'nde odağı hala kullanımda `AutomobileTest.DefaultAutomobileIsInitializedCorrectly`. En az kesinti test yazma devam edebilirsiniz.  
  
### <a name="to-generate-a-property-stub"></a>Bir özellik taslağı oluşturmak için  
  
1.  Ürün belirtimi belirten varsayar `Automobile` sınıfında adlı iki genel özelliği `Model` ve `TopSpeed`. Bu özellikler varsayılan değerleri ile başlatılmalıdır `"Not specified"` ve `-1` varsayılan oluşturucu tarafından. Aşağıdaki birim sınama, varsayılan oluşturucu doğru varsayılan değerlerine özelliklerini ayarlar doğrular.  
  
     Aşağıdaki kod satırını ekleyin `DefaultAutomobileIsInitializedCorrectly`.  
  
     [!code-csharp[VbTDDWalkthrough#1](../snippets/csharp/VS_Snippets_VBCSharp/vbtddwalkthrough/cs/unittest1.cs#1)]
     [!code-vb[VbTDDWalkthrough#1](../snippets/visualbasic/VS_Snippets_VBCSharp/vbtddwalkthrough/vb/unittest1.vb#1)]  
  
     Kod üzerinde iki tanımlanmamış özelliklere başvurduğundan `Automobile`, akıllı etiket görünür. Akıllı etiket için tıklatın `Model` ve ardından **Oluştur özellik taslağı**. İçin bir özellik taslağı oluşturmak `TopSpeed` özelliği de.  
  
     İçinde `Automobile` sınıfı, yeni özelliklerin türleri doğru bağlamdan sonuçlandı.  
  
     Akıllı etiket kısayol menüsünü aşağıdaki çizimde gösterilmektedir.  
  
     ![Visual Basic'te özelliği bağlam menüsü oluşturmak](../ide/media/genpropertysmarttagvb.png "GenPropertySmartTagVB")  
Visual Basic  
  
     ![C'de özelliği bağlam menüsü oluşturmak&#35;](../ide/media/genpropertysmarttagcs.png "GenPropertySmartTagCS")  
Visual C#  
  
### <a name="to-locate-the-source-code"></a>Kaynak kodunu bulmak için  
  
1.  Kullanım **gitmek için** özelliği, yeni özellikleri oluşturulduğunu doğrulayabilirsiniz Automobile.cs veya Automobile.vb kaynak kod dosyasına gidin.  
  
     **Gitmek için** özelliği, hızlı bir şekilde bir tür adı veya bir ad parçası gibi bir metin dizesi girin ve sonuç listesi öğesinde tıklayarak istediğiniz konuma gidin olanak tanır.  
  
     Açık **gitmek için** iletişim kutusu, Kod Düzenleyicisi'nde tıklatıp CTRL +, (CTRL + virgül) tuşuna basın. Metin kutusuna `automobile`. Tıklayın **otomobil** sınıf listesinde ve ardından **Tamam**.  
  
     **Gitmek için** penceresi, aşağıdaki çizimde gösterilmiştir.  
  
     ![Git iletişim kutusu](../ide/media/navigate-2.png "Navigate_2")  
Git penceresini  
  
### <a name="to-generate-a-stub-for-a-new-constructor"></a>Yeni bir oluşturucu için bir saplama oluşturmak için  
  
1.  Bu test yönteminde başlatacak bir oluşturucu saplama oluşturacak `Model` ve `TopSpeed` belirttiğiniz değerlere sahip özellikler. Daha sonra test tamamlamak için daha fazla kod ekleyeceksiniz. Aşağıdaki ek test yöntemine ekleyin, `AutomobileTest` sınıfı.  
  
     [!code-csharp[VbTDDWalkthrough#2](../snippets/csharp/VS_Snippets_VBCSharp/vbtddwalkthrough/cs/intermediate.cs#2)]
     [!code-vb[VbTDDWalkthrough#2](../snippets/visualbasic/VS_Snippets_VBCSharp/vbtddwalkthrough/vb/intermediate.vb#2)]  
  
2.  Yeni sınıf oluşturucusu altında akıllı etiket tıklayın ve ardından **Oluştur Oluşturucusu saplama**. İçinde `Automobile` sınıf dosyası, yeni oluşturucuyu Oluşturucusu çağrısında kullanılan yerel değişkenlerin adlarını incelenmiştir dikkat edin, aynı adlara sahip özellikler bulundu `Automobile` sınıf ve oluşturucu gövdesinde için sağlanan kod bağımsız değişken değerleri depolamak `Model` ve `TopSpeed` özellikleri. (İçinde [!INCLUDE[vbprvb](../includes/vbprvb-md.md)], `_model` ve `_topSpeed` alanları yeni oluşturucuda örtülü olarak tanımlanan destekleyen alanlar için `Model` ve `TopSpeed` özelliklerini.)  
  
3.  Yeni oluşturucuyu oluşturduktan sonra varsayılan oluşturucu çağrısı altında dalgalı çizgi görünür `DefaultAutomobileIsInitializedCorrectly`. Hata iletisi `Automobile` sınıfın sıfır bağımsız değişken alan hiçbir oluşturucu vardır. Parametreleri olmayan bir açık bir varsayılan oluşturucu oluşturmak için akıllı etiket tıklayın ve ardından **Oluştur Oluşturucusu saplama**.  
  
### <a name="to-generate-a-stub-for-a-method"></a>Bir yöntem için bir saplama oluşturmak için  
  
1.  Belirtimi belirten varsayar yeni `Automobile` çalışır duruma durumunda yerleştirme kendi `Model` ve `TopSpeed` özellikleri için varsayılan değerlerin dışında bir şey ayarlanır. Aşağıdaki satırları ekleyin `AutomobileWithModelNameCanStart` yöntemi.  
  
     [!code-csharp[VbTDDWalkthrough#3](../snippets/csharp/VS_Snippets_VBCSharp/vbtddwalkthrough/cs/unittest1.cs#3)]
     [!code-vb[VbTDDWalkthrough#3](../snippets/visualbasic/VS_Snippets_VBCSharp/vbtddwalkthrough/vb/unittest1.vb#3)]  
  
2.  Akıllı etiket için tıklatın `myAuto.Start` yöntemi çağırın ve ardından **metot taslağı üret**.  
  
3.  Akıllı etiket için tıklatın `IsRunning` özelliği ve ardından **Oluştur özellik taslağı**. `Automobile` Sınıfı artık aşağıdaki kodu içerir.  
  
     [!code-csharp[VbTDDWalkthrough#4](../snippets/csharp/VS_Snippets_VBCSharp/vbtddwalkthrough/cs/intermediate.cs#4)]
     [!code-vb[VbTDDWalkthrough#4](../snippets/visualbasic/VS_Snippets_VBCSharp/vbtddwalkthrough/vb/intermediate.vb#4)]  
  
### <a name="to-run-the-tests"></a>Testleri çalıştırmak için  
  
1.  Üzerinde **birim testi** menüsünde **birim testlerini Çalıştır**ve ardından **tüm testleri**. Bu komut, geçerli çözüm için yazılan tüm test çerçeveleri, tüm testleri çalıştırır.  
  
     Bu durumda, iki test, ve her ikisi de beklendiği gibi başarısız olur. `DefaultAutomobileIsInitializedCorrectly` Test başarısız çünkü `Assert.IsTrue` koşul döndürür `False`. `AutomobileWithModelNameCanStart` Test başarısız çünkü `Start` yönteminde `Automobile` sınıfı bir özel durum oluşturur.  
  
     **Test sonuçlarını** penceresi, aşağıdaki çizimde gösterilmiştir.  
  
     ![Başarısız olan test sonuçları](../ide/media/testsfailed.png "TestsFailed")  
Test Sonuçları penceresi  
  
2.  İçinde **Test sonuçları** penceresi, her test sonucu sırada her test hata konumuna gitmek için çift tıklatın.  
  
### <a name="to-implement-the-source-code"></a>Kaynak kodu uygulamak için  
  
1.  Aşağıdaki kod için varsayılan oluşturucu bu nedenle, ekleme `Model`, `TopSpeed` ve `IsRunning` özellikleri tüm başlatıldığı için doğru varsayılan değerleri `"Not specified"`, `-1`, ve `True` (`true`).  
  
     [!code-csharp[VbTDDWalkthrough#5](../snippets/csharp/VS_Snippets_VBCSharp/vbtddwalkthrough/cs/automobile.cs#5)]
     [!code-vb[VbTDDWalkthrough#5](../snippets/visualbasic/VS_Snippets_VBCSharp/vbtddwalkthrough/vb/automobile.vb#5)]  
  
2.  Zaman `Start` yöntemi çağrıldığında, ayarlamanız gerekir `IsRunning` bayrak yalnızca gerekirse true `Model` veya `TopSpeed` özellikleri varsayılan değerlerine dışında bir şey ayarlanır. Kaldırma `NotImplementedException` yönteminden gövde ve aşağıdaki kodu ekleyin.  
  
     [!code-csharp[VbTDDWalkthrough#6](../snippets/csharp/VS_Snippets_VBCSharp/vbtddwalkthrough/cs/automobile.cs#6)]
     [!code-vb[VbTDDWalkthrough#6](../snippets/visualbasic/VS_Snippets_VBCSharp/vbtddwalkthrough/vb/automobile.vb#6)]  
  
### <a name="to-run-the-tests-again"></a>Testleri yeniden çalıştırmak için  
  
1.  Üzerinde **Test** menüsünde **çalıştırma**ve ardından **Çözümdeki tüm testleri**. Şu testler başarılı. **Test sonuçlarını** penceresi, aşağıdaki çizimde gösterilmiştir.  
  
     ![Test sonuçları geçirilen](../ide/media/testspassed.png "TestsPassed")  
Test Sonuçları penceresi  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Kullanımdan oluştur](../misc/generate-from-usage.md)   
 [Kod yazma](../ide/writing-code-in-the-code-and-text-editor.md)   
 [IntelliSense kullanma](../ide/using-intellisense.md)   
 [Kodunuza Birim Testi Uygulama](../test/unit-test-your-code.md)



