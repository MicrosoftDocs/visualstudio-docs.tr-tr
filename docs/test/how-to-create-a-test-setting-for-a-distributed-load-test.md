---
title: Dağıtılmış yük testi için bir Test ayarı oluşturun
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- test settings, for distributed load tests
ms.assetid: b63d4b71-3b74-4872-b2d1-f0bd1a9a8544
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: 69ce0f2504741c0bc48df0245202cdf0eefee20f
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53063328"
---
# <a name="how-to-create-a-test-setting-for-a-distributed-load-test"></a>Nasıl yapılır: Dağıtılmış yük testi için bir test ayarı oluşturun

Yapılandırma *test ayarları* bu testleri test aracıları kullanarak birden çok makine arasında dağıtmak ve test denetleyicilerine yük testleri için. Kullanılacak test ayarlarını da yapılandırabilirsiniz *tanılama veri bağdaştırıcıları*, toplamak istediğiniz veri türlerini belirtmek veya Visual Studio'dan yük testlerinizi çalıştırdığınızda test makinelerini nasıl etkileyeceğinizi.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Örneğin, kodun performans dökümünü toplamak için ASP.NET Profiler tanılama veri bağdaştırıcısı kullanabilirsiniz. Buna ek olarak, tanılama veri bağdaştırıcıları test makinaları üzerinde olası sorunların benzetimini yapmak veya kullanılabilir sistem belleğini azaltmak için kullanılabilir.

Visual Studio için test ayarları bir dosyada depolanır. Test ayarları, her rolle ilgili aşağıdaki bilgileri tanımlayın:

-   Test altındaki uygulamanız için gerekli olan roller kümesi

-   Testlerinizi çalıştırmak için kullanılacak rolü

-   Her rol için tanılama veri bağdaştırıcıları

Testlerinizi çalıştırdığınızda, test çalışması için gerekli bağlı olarak etkin test ayarlarını kullanmak için test ayarlarını seçin. Test ayarları dosyası çözümünüzün bir parçası olarak depolanır. Dosya adı uzantısına sahip *.testsettings*.

Bir çözüme web performansı ve yük testi eklediğinizde bir *varsayılan Local.testsettings* dosyası oluşturulur. Dosya altında çözüme otomatik olarak eklenir **çözüm öğeleri** klasör. Bu dosya, testlerinizi tanılama veri bağdaştırıcısı olmadan yerel olarak çalışır. Başka bir ekleyebilirsiniz *.testsettings* düzenlemek veya dosya bir *.testsettings* ve test denetleyicilerini tanılama veri bağdaştırıcıları belirtmek için dosya.

Test denetleyicisi test ayarlarınızda her rol için kullanılabilen aracılara sahip olacaktır. Test denetleyicileri ve test aracıları hakkında daha fazla bilgi için bkz. [test denetleyicileri ve test aracıları Visual Studio ile yönetme](../test/manage-test-controllers-and-test-agents.md).

Oluşturun ve Visual Studio'dan çalıştırmayı planladığınız yük testleri için çözümünüzdeki test ayarlarını kaldırmak için aşağıdaki adımları izleyin.

## <a name="create-a-test-setting-for-a-distributed-load-test"></a>Dağıtılmış yük testi için bir test ayarı oluşturun

### <a name="to-add-a-test-settings-for-a-distributed-load-test"></a>Dağıtılmış yük testi için test ayarları eklemek için

1.  İçinde **Çözüm Gezgini**, sağ **çözüm öğeleri**, işaret **Ekle**ve ardından **yeni öğe**.

     **Yeni Öğe Ekle** iletişim kutusu görüntülenir.

2.  İçinde **yüklü şablonlar** bölmesinde seçin **Test ayarları**.

3.  (İsteğe bağlı) İçinde **adı** kutusunda, test ayarları dosyasının adıyla değiştirin.

4.  Seçin **ekleme**.

     Yeni test ayarları dosyası görünür **Çözüm Gezgini**altında **çözüm öğeleri** klasör.

    > [!NOTE]
    > Visual Studio Enterprise görüntülediği test ayarları listesi test ayarları dosyalarının listesinden elde edilir **çözüm öğeleri** klasör. Örneğin, test ayarları dosyası içinde **çözüm öğeleri** klasörü kullandığınızda görüntülenir **Etkin Test ayarlarını seçin** seçeneğini **Test** menüsü. Bu test ayarları dosyasını çözüm hiyerarşiniz içinde başka bir konuma taşırsanız, artık Visual Studio tümleşik geliştirme ortamında bir test ayarı olarak kullanılabilmesi için anlamına gelir.

5.  **Test ayarları** iletişim kutusu görüntülenir. **Genel** sayfası seçili.

     Şimdi, düzenleme ve test ayarları değerlerini kaydedin.

    > [!NOTE]
    > Oluşturduğunuz her test ayarları için bir seçenek olarak listelendiğini **Etkin Test ayarlarını seçin** ve **Test Ayarlarını Düzenle** seçeneklerinden **Test** menüsü.

6.  Altında **adı**, test ayarları adını yazın.

7.  (İsteğe bağlı) Altında **açıklama**, diğer takım üyelerinin ne işe yaradıklarını bilmesi için test ayarında bir açıklama yazın.

8.  (İsteğe bağlı) Test çalışmalarınız için varsayılan adlandırma şemasını seçmek için **varsayılan adlandırma düzeni**. Kendi adlandırma düzeninizi tanımlamak için seçin **kullanıcı tanımlı Düzen** ve sonra istediğiniz metni yazın **önek metni**. Test çalışması ismine tarih ve saat damgasını eklemek için seçin **ekleme tarih ve saat damgası**.

9. Seçin **rolleri**.

     **Rolleri** sayfası görüntülenir.

     ![Test ayarı rolü](../test/media/load_testtestrole.png)

10. Testlerinizi uzaktan çalıştırmak veya testlerinizi uzaktan çalıştırmak ve uzaktan veri toplamak için kullanın **Test yürütme yöntemi** açılır ve select **uzaktan yürütme**.

11. Kullanım **denetleyicisi** test aracıları için bir test denetleyicisi seçmek için açılan **denetleyicisi** testlerinizi çalıştırmak veya veri toplamak için kullanılır.

    > [!NOTE]
    > Bu ilk kez denetleyici eklediğiniz ise, hiçbir denetleyicileri aşağı açılan listede listelenir. Liste diğer test ayarlarında belirttiğiniz önceki denetleyiciler tarafından doldurulur. Kutuya denetleyicinin adını yazmanız gerekir (örneğin, **TestControllerMachine1**).

12. Altında testleri çalıştırmak ve verileri toplamak için kullanmak istediğiniz rolleri eklemek için **rolleri**, seçin **Ekle**.

13. Rol için bir ad yazın **adı** sütun. Örneğin, rol "Web sunucusu" olabilir.

14. Adım 12 ve 13 ihtiyaç duyduğunuz tüm rolleri eklemek için yineleyin.

     Her rol test denetleyicisi tarafından yönetilen bir test aracısı kullanır.

15. Testlerinizi çalıştırmak ve ardından istediğiniz rolü seçin **testleri çalıştırmak için rol olarak ayarla**.

    > [!IMPORTANT]
    > Oluşturduğunuz ve tanımladığınız diğer roller testleri çalıştırmaz ancak yalnızca veri ve roller için belirttiğiniz tanıya göre veri toplamak için kullanılacak **veri ve tanı** sayfası.

16. Bir rol için kullanılabilecek aracıları sınırlamak için rolü seçin ve ardından **Ekle** araç çubuğunda altında **seçili rol için aracı öznitelikleri**.

     **Aracı seçim kuralı** iletişim kutusu görüntülenir.

     Adı yazın **öznitelik adı** ve değer **öznitelik değeri**ve ardından **Tamam**. Gereksinim duyduğunuz kadar çok sayıda öznitelik ekleyin.

     Örneğin, "RAM > 16"True"veya"False"fazla 16 GB belleğe sahip test aracısı makinelerinde filtrelemek için bir değere sahip GB" adlı özniteliği ekleyebilirsiniz. Aynı özniteliği bir veya daha fazla test aracısına uygulamak için kullandığınız **Test denetleyicisini Yönet** iletişim kutusu. Daha fazla bilgi için [test denetleyicileri ve test aracıları Visual Studio ile yönetme](../test/manage-test-controllers-and-test-agents.md).

17. Seçin **veri ve tanılama**.

     **Veri ve tanılama** sayfası görüntülenir.

     ![Test ayarı veri ve tanılama](../test/media/load_testtest.png)

18. İçinde **veri ve tanı** sayfasında seçerek rol yaptıklarını tanımlamak *tanılama veri bağdaştırıcıları* rolün veri toplamak için kullanacağını. Bu nedenle, bir veya daha fazla veri ve tanılama bağdaştırıcıları rolü için etkinse, test denetleyicisi belirtilen veri ve tanılama bağdaştırıcısı rol için tanımladığınız öznitelikleri temel alan verileri toplamak için bir uygun test aracısı makinesini seçecektir. Veri ve her rol için toplamak istediğiniz tanılama veri bağdaştırıcılarını seçmek için rolü seçin. Her rol için testin ihtiyaçlarına göre tanılama veri bağdaştırıcıları seçin. Her rol için seçtiğiniz her tanılama veri bağdaştırıcısını yapılandırmak için **yapılandırma**.

     **Roller ve tanılama veri bağdaştırıcıları örneği:**

     Örneğin, bir "" True"ve"RAM > 16 GB"olarak ayarlanan öznitelikle" SQL Server"adlı bir sunucu rolü olarak SQL kullanır" özniteliğine sahip "Masaüstü İstemcisi" adlı bir istemci rolü oluşturabilirsiniz. Seçim yaparak "Masaüstü İstemcisi" nin testleri çalıştıracağını belirtirseniz **testleri çalıştırmak için rol olarak ayarla** içinde **rolleri** sayfasında, test denetleyicisi özniteliğini içeren test aracıları bulunan makineleri seçer "" True", testleri çalıştırmak"SQL kullanır. Test denetleyicisi "RAM > 16 yalnızca veri ve rolüne dahil edilen tanılama bağdaştırıcıları tarafından tanımlanan veriyi toplamak için GB" özniteliğini içeren test aracıları olan SQL sunucu makinelerini de seçecektir. "Masaüstü İstemcisi" test aracısı, veri ve tanılama bağdaştırıcıları bu rol için çok seçerseniz, çalıştığı makinelerin veri toplayabilirsiniz.

     Her tanılama veri bağdaştırıcısı ve nasıl yapılandırılacağı hakkında daha fazla ayrıntı için aşağıdaki tabloda ilişkilendirilen konuyu görüntüleyebilirsiniz.

     Tanılama veri bağdaştırıcıları hakkında daha fazla bilgi için bkz. [test ayarlarını kullanarak tanılama bilgi toplayan](../test/collect-diagnostic-information-using-test-settings.md).

     **Yük testleri için tanılama veri bağdaştırıcıları**

    |Tanılama veri bağdaştırıcısı|Yük testlerinde kullanma|İlişkili konu|
    |-|-------------------------|-|
    |**ASP.NET İstemci Proxy for IntelliTrace and Test Impact:** bu proxy, IntelliTrace ve Test etkisi tanılama veri bağdaştırıcısı için bir web sunucusuna istemciden gelen http çağrıları ile ilgili bilgi toplamanıza olanak tanır.|![Bilgi simgesi](../test/media/vc364f4.gif)<br /><br /> Test aracısı makinelerden sistem bilgilerini toplamak için özel bir ihtiyacınız yoksa, bu bağdaştırıcıyı dahil etmeyin. **Dikkat:** yük testlerinde IntelliTrace bağdaştırıcısının kullanımını büyük toplanan veri miktarı nedeniyle oluşan sorunlar nedeniyle önermiyoruz. <br /><br /> Test etkisi verisi, yük testleri kullanılarak toplanmaz.||
    |**IntelliTrace:** günlük dosyasında depolanan belirli tanı izleme bilgilerini yapılandırabilirsiniz. Bir günlük dosyası uzantısına sahip *.tdlog*. Test ve bir test adımı başarısız çalıştırdığınızda, bir hata oluşturabilirsiniz. Tanılama izlemesini içeren günlük dosyası otomatik olarak bu hataya eklenir. Günlük dosyasında toplanan veri, kodda bir hata yeniden oluşturmak için gerekli olan zamanı azaltarak hata ayıklama verimliliğini artırır. Bu günlük dosyasından dosya yerel oturumun başka bir bilgisayarda yeniden oluşturulabilir. Bu hatanın tekrar oluşturulamama riskini azaltır.<br /><br /> Daha fazla bilgi için [toplamak IntelliTrace verilerini](../test/how-to-collect-intellitrace-data-to-help-debug-difficult-issues.md).|![Önemli simgesi](../test/media/vc364f3.gif)<br /><br /> Yük testlerinde IntelliTrace bağdaştırıcısının kullanımını büyük toplanan ve günlüğe kaydedilen veri miktarı nedeniyle oluşan sorunlar nedeniyle önermiyoruz. Çok sayıda test aracısı kullanmayan ve uzun çalıştırmayan yük testlerinde IntelliTrace bağdaştırıcısının kullanılacağını denemelidir.|[Nasıl yapılır: hata ayıklama zorluklarını çözmeye yardımcı olmak için IntelliTrace verilerini toplama](../test/how-to-collect-intellitrace-data-to-help-debug-difficult-issues.md)|
    |**ASP.NET Profiler:** ASP.NET web uygulamalarına performans verileri toplayan ASP.NET Profil içeren bir test ayarı oluşturabilirsiniz.|Bir geliştirme web sunucusuna karşı çalışmaması ASP.NET profiler tanılama veri bağdaştırıcısı Internet Information Services (IIS) işleminin profilini. Yük testinizde Web sitesinin profilini çıkarmak için IIS'in çalıştığı makineye bir test aracısı yüklemek zorunda. Test aracısı yük oluşturmayacak ancak yalnızca koleksiyon aracı olacak. Daha fazla bilgi için [yüklemek ve test denetleyicisilerinin](../test/lab-management/install-configure-test-agents.md).|[Nasıl yapılır: test ayarlarını kullanarak yük testleri için ASP.NET profil oluşturucuyu yapılandırma](../test/how-to-configure-aspnet-profiler-for-load-tests-using-test-settings.md)|
    |**Olay günlüğü:** test sonuçlarında yer alacak toplanan olay günlüğünü içerecek bir test ayarı yapılandırabilirsiniz.||[Nasıl yapılır: test ayarlarını kullanarak olay günlüğü koleksiyonunu yapılandırma](https://msdn.microsoft.com/48d67891-6018-4549-83e3-213d5d824a02)|
    |**Ağ öykünmesi:** yapay bir ağ yükü, bir test ayarı kullanarak testinize yerleştirmek istediğiniz belirtebilirsiniz. Ağ öykünmesi öykünmesi, çevirmeli gibi belirli ağ bağlantı hızı tarafından makine gelen ve giden iletişimi etkiler. **Not:** ağ öykünmesi, ağ bağlantı hızını artırmak için kullanılamaz.|Ağ öykünmesi bağdaştırıcısı yük testleri tarafından yok sayılır. Bunun yerine, yük testleri yük testi senaryosunun ağ karışımında belirtilen ayarları kullanın.<br /><br /> Daha fazla bilgi için [sanal ağ türlerini belirtme](../test/specify-virtual-network-types-in-a-load-test-scenario.md).||
    |**Sistem bilgisi:** Sistem Bilgileri tanısı ve veri toplayıcısının çalıştığı makine hakkında sistem bilgisi içermek için bir test ayarı ayarlanabilir. Sistem bilgileri, bir test ayarı kullanarak test sonuçlarında belirtilir.|![Bilgi simgesi](../test/media/vc364f4.gif)<br /><br /> Sistem bilgilerini hem yük aracılarından hem de test uygulanan sistemden toplayabilirsiniz.|Yapılandırma, bu bilgileri toplamak için gereklidir.|
    |**Test Etkisi:** hakkında uygulama kodunuzun yöntemleri kullanılmakta olan bir test durumu çalıştırdığınızda bilgi toplayabilirsiniz. Bu, uygulama koduna değişiklikleri ile hangi testlerin etkilendiğini belirlemek için geliştiriciler tarafından yapılan değişiklikler ile birlikte kullanılabilir.|Test etkisi verisi, yük testleri ile toplanmaz.||
    |**Video Kaydedicisi:** otomatikleştirilmiş bir testi çalıştırdığınızda masaüstü oturumunuzun bir video kaydını oluşturabilirsiniz. Bu, bir kodlanmış UI testi için kullanıcı eylemlerini görüntülemek için yararlı olabilir. Videoyu diğer takım üyelerinin yeniden oluşturulması zor olan uygulama sorunlarını yalıtmalarına yardımcı olabilir. **Not:** aracı etkileşimli işlem modunda çalışmadıkça testleri uzaktan çalıştırırken video Kaydedicisi çalışmaz.|![Önemli simgesi](../test/media/vc364f3.gif) **uyarısı:** yük testleri için Video Kaydedici bağdaştırıcısı kullanımını önermeyiz.|[Nasıl yapılır: test ayarlarını kullanarak testler sırasında ekran ve ses kayıtlarını dahil](../test/how-to-include-recordings-of-the-screen-and-voice-during-tests.md)|

19. Seçin **dağıtım**.

     **Dağıtım** sayfası görüntülenir.

20. Testlerinizi çalıştırdığınız her seferde dağıtım için ayrı bir dizin oluşturmak için Seç **etkinleştirme dağıtım**.

    > [!NOTE]
    > Bunu yaparsanız, testlerinizi çalıştırdığınızda uygulamanızı yapılandırmaya devam edebilirsiniz.

21. Testlerinizi çalıştırmak için kullandığınız dizine bir dosya eklemek için **Dosya Ekle**ve sonra eklemek istediğiniz dosyayı seçin.

    > [!NOTE]
    > Bir yük testi çalıştırdığınızda, Eklenti derlemeleri, veri dosyaları ve yüklenen dosyalar otomatik olarak dağıtılır.

22. Testlerinizi çalıştırmak için kullandığınız dizine bir dizin eklemek için **Dizin Ekle** ve ardından eklemek istediğiniz dizini seçin.

23. Betikleri önce ve sonra testlerinizi çalıştırmak için tercih **Kurulum ve temizleme betikleri**.

     **Kurulum ve temizleme betikleri** sayfası görüntülenir.

    1.  İçindeki betik dosyasının konumunu yazın **Kurulum betiği** veya üç noktayı seçin (**...** ) Kurulum betiğini bulmak için.

    2.  İçindeki betik dosyasının konumunu yazın **temizleme betiği** veya üç noktayı seçin (**...** ) temizleme betiğini bulmak için.

24. Testlerinizi farklı bir ana bilgisayar kullanarak çalıştırmak için tercih **konakları**.

    1.  İçinde **konak türü**, doğrulayın **varsayılan** seçilir.

        > [!NOTE]
        > **ASP.NET** içinde **konak türü** yük testlerinde desteklenmez.

    2.  Kullanım **32 bit veya 64 bit test çalıştırması** işlem 32 bit veya 64-bit işlem çalıştırmak için yük testinizde web başarım ve birim testleri isteyip istemediğinizi seçin için açılır.

        > [!NOTE]
        > Maksimum esneklik için size web performansınızı derlemek ve kullanarak yük **herhangi bir CPU** yapılandırma. Daha sonra hem 32-bit hem de 64 bit aracıların çalıştırabilirsiniz. Derleme web performansı ve yük testi projelerini kullanarak **64-bit** yapılandırma herhangi bir avantaj.

25. (İsteğe bağlı) Her test çalışması ve bireysel testler için süreyi sınırlamak üzere seçin **Test zaman aşımları.**

    1.  Bir zaman sınırı aşıldığında bir test durdurmayı seçin **toplam süre aşıldıysa test iptal** ve bu sınır için bir değer yazın.

    2.  Bir zaman sınırı aşıldığında belirli bir testi başarısız kılmak için seçin **tek bir testin yürütme zamanı aşılırsa, testi başarısız olarak işaretle**ve bu sınır için bir değer girin.

26. Skip **birim testi**. Yük testleri bu ayarları kullanmayın.

27. Skip **Web Test**. Yük testleri bu ayarları kullanmayın.

28. Test ayarlarını kaydetmek için seçin **Kaydet**. İstediğiniz dosya adını yazın **nesne adı**.

    > [!NOTE]
    > Test ayarlarınızı değiştirmeniz gerekiyorsa seçin **Test** seçip **Test Ayarlarını Düzenle** ve oluşturduğunuz test ayarlarının üzerine gelin.

### <a name="to-remove-a-test-settings-from-your-solution"></a>Çözümünüzden test ayarlarını kaldırmak için

Altında **çözüm öğeleri** klasöründe **Çözüm Gezgini**, kaldırın ve ardından istediğiniz test ayarlarını sağ **Kaldır**.

Test ayarları dosyası çözümünüzden kaldırılır. Bu değişiklik seçeneklerine ilişkin tercih listesine yansır **Etkin Test ayarlarını seçin** ve **Test Ayarlarını Düzenle** seçeneklerinden **Test** menüsü.

## <a name="see-also"></a>Ayrıca bkz.

- [Test denetleyicileri ve test aracıları](configure-test-agents-and-controllers-for-load-tests.md)
- [Test ayarlarını kullanarak tanılama bilgileri Topla](../test/collect-diagnostic-information-using-test-settings.md)