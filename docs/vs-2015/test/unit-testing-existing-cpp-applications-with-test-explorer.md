---
title: Birim Test Gezgini ile mevcut C++ uygulamalarında testi | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7d08de69-c32e-4f0b-89aa-75347b15fb82
caps.latest.revision: 13
ms.author: gewarren
manager: douge
ms.openlocfilehash: 8dab39c5718b8872df5e81281ba9dda886ebf313
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49941210"
---
# <a name="unit-testing-existing-c-applications-with-test-explorer"></a>Test Gezgini ile mevcut C++ uygulamalarında birim testi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Mevcut bir uygulamayı değiştirmeden önce birim testlerinin yeterli derecede kapsamlı olduğundan emin olun, öneririz. Bu, değişikliklerinizi yeni hatalar oluşturmadığından emin olmanızı sağlar. Uygulama zaten birim testlerine sahip değilse, bu konuda gösterilen teknikleri kullanarak ekleyebilirsiniz. Bu konuda, kod ve sonra oluşturmak, test etme karar ile başlayarak, var olan Visual C++ kodu için birim testleri eklemeyi açıklar yazma ve son olarak, testler.  
  
## <a name="deciding-how-to-test-your-code"></a>Kodunuzu test etmek nasıl karar verme  
 Varolan C++ projesini açın ve nasıl birim testleri eklemek istediğinize karar verirken için inceleyin. Kodda bağımlılıklar bakın ve yardımcı Yardım parçaların birbirleriyle etkileşimini anlamanıza bazı modelleme araçları kullanmak isteyebilirsiniz. Daha fazla bilgi için [kodu görselleştirme](../modeling/visualize-code.md).  
  
 Değişikliklerinizi küçük görevlere ayırmanızı öneririz. Her küçük değişiklikten önce aynı kalacak davranışı yönleri için birim testleri yazma. Bu testler, değişiklik yaptıktan sonra da geçilmeye devam eder. Örneğin, bu kişilerin listesini göre yerine soyadlarına göre sıralar, böylece bir sıralama işlevini değiştirmeyi planlıyorsanız, tüm girilen adların çıktıda görüldüğünü bir birim testi yazabilirsiniz. Değişikliği yaptıktan sonra yeni davranış için yeni birim testleri eklemek isteyebilirsiniz.  
  
 Pratik ise, çoğu veya tüm Birim testlerinizin yalnızca dışa aktarılan işlevleri kullanmalıdır. Ancak, ardından tüm uygulamanın yalnızca küçük bir parçasını değiştiriyorsanız, dışa aktarılmayan işlevleri kullanmak isteyebilirsiniz. Örneğin, iç işlevleri çağıran testler ya da testler ayarlama ve iç değişkenlerin değerlerini alma isteyebilirsiniz.  
  
 Olup olmadığını test etmek istediğiniz arabirimleri kullanıma açıp bağlı olarak, ürün kodunu test etmek için birkaç yolu vardır. Aşağıdaki yöntemlerden birini seçin:  
  
 **Birim testleri yalnızca test altındaki koddan dışa aktarılan işlevleri kullanacaktır:**  
 Ayrı bir test projesi ekleyin. Test projesinde test altındaki projeye bir başvuru ekleyin.  
  
 Yordamına gidin [dışarı aktarılan işlevleri test projesinden başvurma](#projectRef).  
  
 **Test edilen kod bir .exe dosyası olarak derlenmiştir**  
 Ayrı bir test projesi ekleyin. Bu çıkış nesnesi dosyasına bağlayın.  
  
 Yordamına gidin [testleri nesneye veya kitaplık dosyalarına bağlama](#objectRef).  
  
 **Birim testleri özel işlevler ve veriler kullanmalıdır ve test edilen kod statik bir kitaplık olarak derlenebilir:**  
 Test altındaki projeyi değiştirin, böylece bir .lib dosyasına derlenir. Test altındaki projeye başvuran ayrı bir test projesi ekleyin.  
  
 Bu yaklaşım, testlerinizin özel üyeleri kullanmasına, ancak yine de ayrı bir projede testleri tutmak için izin verme avantajına sahiptir. Ancak, bunu burada bir dinamik bağlantı kitaplığı (.dll) sahip bazı uygulamalar için uygun olmayabilir.  
  
 Yordamına gidin [test edilen kod statik bir kitaplığa çevirme](#staticLink).  
  
 **Birim testleri özel işlevler ve veriler kullanmalıdır ve kod bir dinamik bağlantı kitaplığı (DLL) derlenmesi gerekir:**  
 Birim testlerini aynı projede ürün kodu olarak ekleyin.  
  
 Yordamına gidin [aynı projede birim testleri eklemek için](#sameProject).  
  
## <a name="creating-the-tests"></a>Testleri oluşturma  
  
###  <a name="staticLink"></a> Test edilen kod statik bir kitaplığa çevirme  
  
- Testlerinizin test edilen bir proje tarafından dışa aktarılmaz üyeleri kullanmalıdır ve test altındaki projeye bir dinamik kitaplık olarak oluşturulduysa, bir statik kitaplığa dönüştürmeyi düşünün.  
  
  1.  Çözüm Gezgini'nde test edilen projenin kısayol menüsünde seçin **özellikleri**. Proje Özellikleri penceresi açılır.  
  
  2.  Seçin **yapılandırma özellikleri**, **genel**.  
  
  3.  Ayarlama **yapılandırma türü** için **statik kitaplık (.lib)**.  
  
  Yordamı ile devam [testleri nesneye veya kitaplık dosyalarına bağlama](#objectRef).  
  
###  <a name="projectRef"></a> Dışarı aktarılmış işlevlerini test projesinden başvurma  
  
- Ardından test edilen bir proje test etmek istediğiniz işlevleri dışa aktarır, kod projesine test projesinden bir başvuru ekleyebilirsiniz.  
  
  1.  Bir C++ test projesi oluşturun.  
  
      1.  Üzerinde **dosya** menüsünde seçin **yeni**, **proje**, **Visual C++, Test**, **C++ birim testi projesi**.  
  
  2.  Çözüm Gezgini'nde testin projesinin kısayol menüsünden seçin **başvuruları**. Proje Özellikleri penceresi açılır.  
  
  3.  Seçin **ortak özellikler**, **çerçeve ve başvurular**ve ardından **Yeni Başvuru Ekle** düğmesi.  
  
  4.  Seçin **projeleri**ve ardından test edilecek projeyi.  
  
       Seçin **Ekle** düğmesi.  
  
  5.  Test projesi için Özellikler'de test edilen projenin konumunu ek içerik dizinlerine ekleyin.  
  
       Seçin **yapılandırma özellikleri**, **VC ++ dizinleri**, **ekleme kodu dizinleri**.  
  
       Seçin **Düzenle**ve ardından test edilen projenin üstbilgi dizinini ekleyin.  
  
  Git [birim testleri yazma](#addTests).  
  
###  <a name="objectRef"></a> Testleri nesneye veya kitaplık dosyalarına bağlama  
  
- Test edilen kod test etmek istediğiniz işlevleri dışa aktarmıyorsa çıktısını ekleyebilirsiniz **.obj** veya **.lib** dosyasını test projesinin bağımlılıklarına.  
  
  1.  Bir C++ test projesi oluşturun.  
  
      1.  Üzerinde **dosya** menüsünde seçin **yeni**, **proje**, **Visual C++, Test**, **C++ birim testi projesi**.  
  
  2.  Çözüm Gezgini'nde testin projesinin kısayol menüsünden seçin **özellikleri**. Proje Özellikleri penceresi açılır.  
  
  3.  Seçin **yapılandırma özellikleri**, **bağlayıcı**, **giriş**, **ek bağımlılıklar**.  
  
       Seçin **Düzenle**ve adını ekleyin **.obj** veya **.lib** dosyaları. Tam yol adlarını kullanmayın.  
  
  4.  Seçin **yapılandırma özellikleri**, **bağlayıcı**, **genel**, **ek kitaplık dizinleri**.  
  
       Seçin **Düzenle**ve dizin yolunu ekleyin **.obj** veya **.lib** dosyaları. Genellikle test edilen projenin derleme klasörü içindeki yoldur.  
  
  5.  Seçin **yapılandırma özellikleri**, **VC ++ dizinleri**, **ekleme kodu dizinleri**.  
  
       Seçin **Düzenle**ve ardından test edilen projenin üstbilgi dizinini ekleyin.  
  
  Git [birim testleri yazma](#addTests).  
  
###  <a name="sameProject"></a> Aynı projede birim testleri eklemek için  
  
1. Üst bilgiler ve birim testi için gerekli olan kitaplık dosyalarını içerecek şekilde ürün kodu proje özelliklerini değiştirin.  
  
   1.  Çözüm Gezgini'nde test edilen projenin kısayol menüsünde Özellikler'i seçin. Proje Özellikleri penceresi açılır.  
  
   2.  Seçin **yapılandırma özellikleri**, **VC ++ dizinleri**.  
  
   3.  Dahil et ve kitaplık dizinlerini düzenleyin:  
  
       |||  
       |-|-|  
       |**Ekleme kodu dizinleri**|**$(VCInstallDir)UnitTest\include;$(IncludePath)**|  
       |**Kitaplık dizinleri**|**$(VCInstallDir)UnitTest\lib;$(LibraryPath)**|  
  
2. Bir C++ birim testi dosyası ekleyin:  
  
   -   Çözüm Gezgini'nde, projenin kısayol menüsünde seçin **Ekle**, **yeni öğe**ve ardından **C++ birim testi**.  
  
   Git [birim testleri yazma](#addTests).  
  
##  <a name="addTests"></a> Birim testleri yazma  
  
1. Her birim testi kodu dosyasında, ekleme bir `#include` test edilen projenin üstbilgileri için bildirimi.  
  
2. Birim testi kod dosyalarına test sınıfları ve yöntemleri ekleyin. Örneğin:  
  
   ```cpp  
   #include "stdafx.h"  
   #include "CppUnitTest.h"  
   #include "MyProjectUnderTest.h"  
   using namespace Microsoft::VisualStudio::CppUnitTestFramework;  
   namespace MyTest  
   {  
     TEST_CLASS(MyTests)  
     {  
     public:  
         TEST_METHOD(MyTestMethod)  
         {  
             Assert::AreEqual(MyProject::Multiply(2,3), 6);  
         }  
     };  
   }  
   ```  
  
   Daha fazla bilgi için [yerel kod Test Gezgini ile birim testi](http://msdn.microsoft.com/en-us/8a09d6d8-3613-49d8-9ffe-11375ac4736c).  
  
## <a name="run-the-tests"></a>Testleri çalıştırın  
  
1. Üzerinde **görünümü** menüsünde seçin **diğer Windows**, **Test Gezgini**.  
  
2. Test Gezgini'nde seçin **tümünü Çalıştır**.  
  
   Daha fazla bilgi için [hızlı başlangıç: Test Gezgini ile Test odaklı geliştirme](../test/quick-start-test-driven-development-with-test-explorer.md).



