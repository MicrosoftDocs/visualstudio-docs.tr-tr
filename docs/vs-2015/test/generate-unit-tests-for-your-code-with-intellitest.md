---
title: Intellitest ile kodunuz için birim testleri oluşturma | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.UnitTest.CreateIntelliTest
ms.assetid: cd9ff940-e948-4d28-a72c-b291ef5c1e90
caps.latest.revision: 35
ms.author: gewarren
manager: douge
ms.openlocfilehash: 6743db0b10d8df4f131f8125b3e2f83bca262054
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49226518"
---
# <a name="generate-unit-tests-for-your-code-with-intellitest"></a>Intellitest ile kodunuz için birim testleri oluşturma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Intellitest, test verileri ve birim testleri paketi oluşturmak için .NET kodunuzu keşfeden. Koddaki her ifade için bir test girişi oluşturulur o ifadeyi yürütecek. Koddaki her koşullu şube için bir vaka analizi yapılır. Örneğin, deyimleri, onaylamalar ve özel durumlar oluşturabilecek tüm işlemler analiz edilirse. Bu analiz, yüksek kod kapsamı ile birim testleri oluşturma, yöntemlerinizin her biri için parametreleştirilmiş birim testi için test verilerini oluşturmak için kullanılır.  
  
 Intellitest çalıştırdığınızda, hangi testlerin başarısız oluyor ve onları düzeltmek için tüm gerekli kodu eklemek kolayca görebilirsiniz. Hangi testlerin bir regresyon paketi sağlamak için bir test projesine kaydetmek için seçebilirsiniz. Kodunuzu değiştikçe, üretilen testler, kod değişikliğine eşitlenmiş şekilde tutmanızı sağlayacak Intellitest yeniden çalıştırın.  
  
 Intellitest yalnızca C# için kullanılabilir ve x64 desteklemiyor yapılandırma.  
  
## <a name="get-started-with-intellitest"></a>Intellitest ile çalışmaya başlama  
 Visual Studio Enterprise gerekir.  
  
### <a name="explore-use-intellitest-to-explore-your-code-and-generate-unit-tests"></a>Keşfedin: kullanım Intellitest kodunuzu keşfetmek ve Birim testler üretmek  
 Birim testler üretmek için türler genel olmalıdır. Aksi takdirde, [birim testleri oluşturma](#NoRun) bunları oluşturmadan önce ilk.  
  
1.  Çözümünüzü Visual Studio'da açın. Ardından test etmek istediğiniz yöntemi içeren sınıf dosyasını açın.  
  
2.  Kodunuzdaki bir yöntemi sağ tıklatın ve seçin **Intellitest Çalıştır** , yönteminde kod için birim testleri oluşturmak için.  
  
     ![Sağ&#45;Birim testler üretmek için yönteminizi tıklayın](../test/media/runpex.png "RunPEX")  
  
     Intellitest kodunuz, farklı giriş ile birden çok kez çalışır. Her bir çalıştırmanın giriş test verileri ve elde edilen çıkış gösteren tablo ya da özel durum gösterilir.  
  
     ![Araştırma sonuçları penceresi testleriyle görüntülenen](../test/media/pexexplorationresults.png "PEXExplorationResults")  
  
     Bir sınıfta tüm genel metotlar için birim testleri üretmek için yalnızca belirli bir yöntem yerine sınıfı sağ tıklayın. Ardından **Intellitest Çalıştır**. Açılır listede araştırma Sonuçları penceresinde sınıfı, birim testleri ve her yöntem için giriş verilerini görüntülemek için kullanın.  
  
     ![Listeden görüntülemek için test sonuçlarını seçin](../test/media/selectpextest.png "SelectPEXTest")  
  
     Geçmek için kontrol testler için bildirilen sonuçları Sonuç sütunundaki kodunuz için beklentilerinizi. Başarısız testler için kodunuzu uygun şekilde düzeltin. Ardından düzeltmeler doğrulamak için Intellitest yeniden çalıştırın.  
  
### <a name="persist-save-the-unit-tests-as-a-regression-suite"></a>Kalıcı: birim testlerini bir regresyon paketi Kaydet  
  
1.  Parametreli birim test projesine kaydetmek istediğiniz veri satırları seçin.  
  
     ![Testleri seçin. doğru&#45;tıklayın ve Kaydet'i seçin](../test/media/savepextests.png "SavePEXTests")  
  
     Test projesini görüntüleyebilir ve oluşturuldu - parametreli birim testi tek tek birim testleri, her satır için karşılık gelen kaydedilir. g.cs dosyasında test projesini ve parametreli birim testi, karşılık gelen .cs dosyası içinde kaydedilir. Birim testlerini çalıştırmak ve el ile oluşturduğunuz herhangi bir birim test için yaptığınız gibi Test Explorer sonuçları görüntüleyin.  
  
     ![Birim testi görüntülemek için test yönteminin açık sınıf dosyasında](../test/media/testmethodpex.png "TestMethodPEX")  
  
     Gerekli tüm başvuruları da test projesine eklenir.  
  
     Yöntem kodunu değişirse birim testlerini değişiklikleri ile eşitlenmiş tutmak için Intellitest yeniden çalıştırın.  
  
### <a name="assist-use-intellitest-to-focus-code-exploration"></a>Yardımcı: Odağı kod araştırma kullanım Intellitest  
  
1.  Daha karmaşık bir kod varsa, Intellitest araştırma, kodunuzun odaklanarak ile yardımcı olur. Örneğin, bir parametre olarak arabirime sahip bir yöntemi varsa ve bu arabirimi uygulayan birden fazla sınıf, Intellitest söz konusu sınıfın bulur ve bir uyarı bildirir.  
  
     Yapmak istediğinize karar verirken uyarıları görüntüleyin.  
  
     ![Uyarılarını görüntüleme](../test/media/pexviewwarning.png "PEXViewWarning")  
  
2.  Kodu inceleme ve test etmek istediğiniz anlamak sonra arabirimi sınamak üzere kullanmak için hangi sınıfların seçmek için uyarı düzeltebilirsiniz.  
  
     ![Sağ&#45;uyarıya tıklayarak ve düzeltme seçin](../test/media/pexfixwarning.png "PEXFixWarning")  
  
     Bu seçenek PexAssemblyInfo.cs dosyasına eklenir.  
  
     `[assembly: PexUseType(typeof(Camera))]`  
  
3.  Artık bir parametreli birim testi oluşturma ve verileri yalnızca, sabit sınıfı kullanarak test etmek için Intellitest yeniden çalıştırabilirsiniz.  
  
     ![Test verilerini oluşturmak için Intellitest yeniden](../test/media/pexwarningsfixed.png "PEXWarningsFixed")  
  
### <a name="specify-use-intellitest-to-validate-correctness-properties-that-you-specify-in-code"></a>Belirtin: kullanım Intellitest kodda belirten doğruluk özellikleri doğrulamak  
 Giriş ve çıkışları doğrulamak için üretilmiş birim testlerini istediğiniz genel ilişkisi belirtin. Bu belirtim, bir test yöntemi gibi görünüyor, ancak Evrensel amaçlarıyla bir yöntem içinde kapsüllenir. Parametreli birim test yöntem budur ve yaptığınız herhangi bir onayları Intellitest oluşturabilen olası tüm giriş değerlerini tutmanız gerekir.  
  
##  <a name="QandALink"></a> SORU- CEVAP  
  
### <a name="q-can-you-use-intellitest-for-unmanaged-code"></a>Intellitest yönetilmeyen kod için kullanabilir miyim?  
 **Y:** Hayır, Intellitest, yalnızca yönetilen kod ile çalışır.  
  
### <a name="q-when-does-a-generated-test-pass-or-fail"></a>S: ne zaman oluşturulan bir test geçti başarısız veya?  
 **Y:** diğer herhangi bir birim test gibi hiçbir özel durum oluşursa bu geçirir. Herhangi bir onaylama işlemi başarısız olursa veya test edilen kod işlenmemiş bir özel durum oluşturursa başarısız olur.  
  
 Özel bazı durumlar oluşursa, geçirilebilecek bir test varsa, test yöntemi, test sınıfına veya derleme gereksinimlerinize göre aşağıdaki özniteliklerden birini düzeyi ayarlayabilirsiniz:  
  
-   **PexAllowedExceptionAttribute**  
  
-   **PexAllowedExceptionFromTypeAttribute**  
  
-   **PexAllowedExceptionFromTypeUnderTestAttribute**  
  
-   **PexAllowedExceptionFromAssemblyAttribute**  
  
### <a name="q-can-i-add-assumptions-to-the-parameterized-unit-test"></a>Parametreli birim testine varsayımlar ekleyebilir miyim?  
 **Y:** Evet, varsayım, belirli bir yöntem için birim testi için hangi test verileri gerekli değil belirtmek için kullanın. Kullanım <xref:Microsoft.Pex.Framework.PexAssume> varsayımlar eklemek için sınıfı. Örneğin, bir varsayım uzunluk değişkeni şu şekilde null olmadığından ekleyebilirsiniz.  
  
 `PexAssume.IsNotNull(lengths);`  
  
 Bir varsayım ekleyip Intellitest yeniden yitirmesi test verileri kaldırılır.  
  
### <a name="q-can-i-add-assertions-to-the-parameterized-unit-test"></a>Parametreli birim testine onaylar ekleyebilir miyim?  
 **Y:** Intellitest birim testleri çalıştırdığında ne raporunuza sunduğundan aslında doğru olduğunu Evet, kontrol eder. Kullanım <xref:Microsoft.Pex.Framework.PexAssert> sınıfı veya onaylama Onaylamalar eklemek için test framework ile birlikte gelen API. Örneğin, iki değişken eşit olduğunu onaylama ekleyebilirsiniz.  
  
 `PexAssert.AreEqual(a, b);`  
  
 Onaylama Ekle ve Intellitest yeniden çalıştırın, değerinizi geçerli olduğunu ve yüklü değilse test başarısız olduğunu denetler.  
  
###  <a name="NoRun"></a> Parametreli birim testleri çalıştırmadan önce Intellitest oluşturabilir miyim?  
 **Y:** Evet, sınıf veya yöntemi içinde sağ tıklayın ve ardından seçin **Intellitest oluşturma**.  
  
 ![Sağ&#45;Düzenleyicisi, Intellitest oluşturma seçin](../test/media/pexcreateintellitest.png "PEXCreateIntelliTest")  
  
 Testleriniz oluşturulmaya veya projenizin ve testleri nasıl adlandırıldığı değiştirmek için varsayılan biçimi kabul edin. Yeni bir test projesi oluşturun veya var olan bir projeye testlerinizi kaydedin.  
  
 ![Intellitest MSTest varsayılan oluşturun](../test/media/pexcreateintellitestmstest.png "PEXCreateIntelliTestMSTest")  
  
### <a name="q-can-i-use-other-unit-test-frameworks-with-intellitest"></a>Intellitest ile diğer birim testi çerçeveleri kullanabilir miyim?  
 **Y:** Evet, bu adımları [bulun ve diğer çatıları Yükle](../test/install-third-party-unit-test-frameworks.md). Visual Studio'yu yeniden başlatın ve çözümünüzü yeniden sonra sınıf veya yöntemi içinde sağ tıklayın ve ardından seçin **Intellitest oluşturma**. Burada yüklü Çerçevenizi seçin:  
  
 ![Diğer birim testi çerçevesi için Intellitest seçin](../test/media/pexcreateintellitestextensions.png "PEXCreateIntelliTestExtensions")  
  
 Ardından, ilgili tek tek birim testleri oluşturmak için Intellitest Çalıştır. g.cs dosyaları.  
  
### <a name="q-can-i-learn-more-about-how-the-tests-are-generated"></a>Testleri nasıl oluşturulacağını hakkında daha fazla bilgi miyim?  
 **Y:** bu üst düzey bir genel bakış edinmek için Evet'i, [blog gönderisi](http://blogs.msdn.com/b/visualstudioalm/archive/2015/07/05/intellitest-one-test-to-rule-them-all.aspx).



