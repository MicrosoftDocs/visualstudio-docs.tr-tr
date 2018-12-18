---
title: Test denetleyicilerini ve test aracılarını yönetme
ms.date: 09/18/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ccc3a6342857d1f228118ef7b26601f3787908e4
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53059502"
---
# <a name="manage-test-controllers-and-test-agents"></a>Test denetleyicilerini ve test aracılarını yönetme

Visual Studio testleri uzaktan çalıştırmak, testleri birden fazla makine arasında dağıtmak için kullanacağınız veya yük testleri, test denetleyicisi yapılandırmanız gerekir, test aracılarını ve test ayarları dosyası. Bu konu, test denetleyicilerini Yönet ve test aracılarını yükledikten ve bunları ilk kez yapılandırdıktan sonra açıklar.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Laboratuvar ortamlarında testleri çalıştırmak için Microsoft Test Yöneticisi'ni kullanırsanız, test denetleyicilerini ve aracılarını kullanarak yönettiğiniz **Test denetleyicisi Yöneticisi** içinde **Laboratuvar Merkezi** Microsoft Test Yöneticisi için. Bu konu yalnızca testleri çalıştırmak için Visual Studio kullanıyorsanız geçerlidir.

Yükleme ve test aracıları yapılandırmak ve test denetleyicilerini Visual Studio'da testleri çalıştırmak için hakkında daha fazla bilgi için bkz. [test aracıları ve denetleyicileri yapılandırma](../test/configure-test-agents-and-controllers-for-load-tests.md).

Yapılandırma ve test denetleyicisini ve herhangi kayıtlı aracıyı izlemek için test projenizi çalıştırmak istediğiniz testleri içeren test ayarları dosyası olmalıdır. Test ayarları dosyasını açın, **rol** ve **Test Denetleyicilerini Yönet** için açılan **denetleyicisi** alan.

Bir yük testi projesi için de seçebilirsiniz **Test Denetleyicilerini Yönet** gelen **yük testi** menüsü.

## <a name="add-a-test-agent-to-a-test-controller"></a>Test aracısı test denetleyicisine eklemek

Farklı test denetleyicisine test aracısı eklemek isteyebilirsiniz veya yüklü olan bir test denetleyicisine test aracısı eklemek zorunda kalabilirsiniz.

### <a name="to-add-a-test-agent-to-a-test-controller"></a>Bir test aracısı test denetleyicisine eklemek için

1. Seçin **Başlat** > **Test Aracısı Yapılandırma Aracı**.

     **Test aracısını Yapılandır** iletişim kutusu görüntülenir.

    > [!NOTE]
    > Bir test aracısı test denetleyicisine eklemek için zaten yüklü olması gerekir. Bir test aracısı yükleme hakkında daha fazla bilgi için bkz. [yüklemek ve test denetleyicisilerinin](../test/lab-management/install-configure-test-agents.md).

2. Test aracısını nasıl çalıştırılabilir için iki seçenek sunulur:

   - **Hizmet**: Masaüstü ile etkileşmesi gereken otomatik testleri çalıştırmak zorunda değilsiniz gibi kodlanmış UI testleri veya test, altında çalıştığında bir video kaydı oluşturmak, **test aracısını farklı çalıştır**seçin **hizmeti**. Test aracısı hizmet olarak başlatılacak. Seçin **sonraki**.

      Artık test aracısı hizmet olarak başladığında kullanıcı hakkındaki ayrıntıları girebilirsiniz.

      1. Adı girin **kullanıcı adı**.

      2. Parolayı girin **parola**.

        |**Önemli kullanıcı hesabı bilgileri**|
        |-|
        |-Null parolalar kullanıcı hesapları için desteklenmez.|
        |IntelliTrace collector ya da ağ öykünmesini kullanmak istiyorsanız, kullanıcı hesabı Yöneticileri grubunun bir üyesi olmalıdır.|
        |-Aracı kullanıcı adı Aracı hizmeti içinde değilse, bunu eklemek test denetleyicisi üzerinde izinler gerektirir dener.|
        |-Test denetleyicisini kullanmaya çalışan kullanıcı test denetleyicisinin kullanıcı hesabında olmalıdır ya da denetleyiciye karşı testleri çalıştırmak mümkün olmayacaktır.|

   - **Etkileşimli işlem**: Masaüstü ile etkileşmesi gereken otomatik testleri çalıştırmak istiyorsanız, aşağıdaki gibi kodlanmış UI testleri veya testiniz çalıştığında bir video kaydı oluşturma, seçin **etkileşimli işlem**. Test aracısı hizmet yerine etkileşimli bir işlem olarak başlatılacak.

      Sonraki sayfada, test aracısını bir işlem ve diğer seçenekleri başladığında kullanıcı hakkındaki ayrıntıları girin.

      1. Adı girin **kullanıcı adı**.

      2. Parolayı girin **parola**.

        > [!NOTE]
        > Şu anda etkin kullanıcı olmayan farklı bir kullanıcı ile interaktif bir süreç olarak çalıştırmak için test aracını yapılandırırsanız, bilgisayarı yeniden başlatın ve aracıyı başlatabilmek bu farklı bir kullanıcı oturum açın. Ayrıca, null parolalar kullanıcı hesapları için desteklenmez. IntelliTrace collector ya da ağ öykünmesini kullanmak istiyorsanız, kullanıcı hesabının Yöneticiler grubunun bir üyesi olması gerekir.

      3. Bir test aracısı olan bilgisayarın yeniden başlattıktan sonra testleri çalıştıracağından emin olmak için bilgisayarı otomatik olarak test aracısı olarak oturumu açması için ayarlayabilirsiniz. Seçin **otomatik olarak oturum açma**. Bu kullanıcı adını ve parolasını şifrelenmiş bir biçimde kayıt defterinde depolar.

      4. Masaüstüyle etkileşimde olması gereken otomatikleştirilmiş testleri engelleyebilmesi yüzünden ekran koruyucunun devre dışı bırakıldığından emin olmak için seçin **olun ekran koruyucu devre dışı**.

        > [!WARNING]
        > Otomatik olarak oturum açın veya ekran koruyucuyu devre dışı güvenlik riskleri vardır. Otomatik oturum açmayı etkinleştirerek, diğer kullanıcıların bilgisayarı başlatmasını ve otomatik olarak oturum hesabını kullanabilmelerini sağlar. Ekran koruyucu devre dışı bırakırsanız, bilgisayar kullanıcının oturum açmak bilgisayarın kilidini açmak istemeyebilir. Bu, herkesin bilgisayara fiziksel erişimi olan makineye erişmesine olanak tanır. Bu özellikleri bir bilgisayarda etkinleştirirseniz, bu bilgisayarların fiziksel olarak güvenli olduğundan emin olun. Örneğin, bu bilgisayarların fiziksel olarak güvenli laboratuarda bulunur. (Silerseniz **olun ekran koruyucu devre dışı**, bu ekran koruyucunuzu etkinleştirmez.)

3. Bu aracıyı farklı bir test denetleyicisiyle kaydetmek için seçin **test denetleyicisiyle birlikte Kaydet.** Ardından, test denetleyicisinin adını yazın **:** ve içinde kullandığınız bağlantı noktası numarasını **test aracısını aşağıdaki test denetleyicisiyle**. Örneğin **agent1: 6901**.

    > [!NOTE]
    > Varsayılan bağlantı noktası numarası 6901'dir.

4. Değişikliklerinizi kaydetmek için seçin **ayarlarını uygula**. Kapatma **Yapılandırma Özeti** iletişim kutusunu ve sonra close **Test Aracısı Yapılandırma Aracı**.

> [!WARNING]
> Aracı şu anda başka bir test denetleyicisinde çalıştırmak için yapılandırıldıysa, test aracısını o denetleyiciden kaldırmanız gerekir.

## <a name="remove-a-test-agent-from-a-test-controller"></a>Bir test aracısı test denetleyicisinden kaldırın.

Bir test aracısı kaldırılmadan önce çevrimdışı duruma ayarlanması gerekir.

> [!NOTE]
> Bu yordamı, bir denetleyici için bir laboratuvar ortamının bir parçası kayıtlı aracıları kaldırmak için kullanamazsınız. Bir denetleyiciden bu aracıları kaldırmak için Microsoft Test Yöneticisi'ni kullanarak ortama kaldırmanız gerekir.

### <a name="to-remove-a-test-agent-from-a-test-controller"></a>Test denetleyicisinden test aracısı kaldırmak için

1. Test denetleyicisi bir proje ile kayıtlı değilse, aşağıdaki adımları izleyin.

    1. Visual Studio'dan test projeniz için test ayarları dosyasını açın, **rol** ve **Test Denetleyicilerini Yönet** için açılan **denetleyicisi** alan.

         **Test denetleyicisini Yönet** iletişim kutusu görüntülenir.

    2. İçinde **denetleyicisi** aşağı açılan listesinde, test denetleyicisini üzerinde ayarladığınız bilgisayarın adını yazın. Daha önce belirli bir test denetleyicisi yönettiyseniz, adı listeden seçebilirsiniz.

    3. İçinde **aracıları** bölmesinde, test aracısı adı seçin. Aracı hala çevrimiçiyse seçin **çevrimdışı.** Kaldırmak için seçin **Kaldır**.

        > [!NOTE]
        > Yalnızca bir test aracısı kaldırmak, bu test denetleyicisiyle ilişkisini keser. Test aracısını tümüyle kaldırmak için kullanın **programlar ve Özellikler** test aracısı bilgisayarında Denetim Masası.

2. Test denetleyicisi bir projesiyle kayıtlıysa, Microsoft Test Yöneticisi'ni kullanarak aracıyı kaldırın.

## <a name="change-the-settings-for-a-test-agent"></a>Test aracısı için ayarları değiştirme

Test aracısın durumu aşağıdaki değerlerden biri olabilir:

|Durum|Açıklama|
|-|-----------------|
|Çalışan Test|Testleri çalıştırma|
|Hazır|Testleri çalıştırmak veya veri toplamak ve tanılamak kullanılabilir|
|Çevrimdışı|Testleri çalıştırmak veya veri toplamak ve tanılamak kullanılamaz|
|Bağlantısı kesildi|Test aracısı başlatılmadı|

Durum ve diğer ayarları için aşağıdaki yordamları kullanarak test aracısın değiştirebilirsiniz.

### <a name="to-change-the-settings-of-a-test-agent"></a>Test aracısın ayarlarını değiştirmek için

> [!NOTE]
> Test aracısını bir projesiyle kayıtlı bir test denetleyicisine kayıtlı değilse, Microsoft Test Yöneticisi ayarlarını değiştirin.

1. Yapılandırma ve test denetleyicisini ve tüm kayıtlı aracıları için bir yük testi izleme için seçmek **yük testi** Visual Studio'da menü seçip **Test Denetleyicilerini Yönet**. Diğer herhangi bir test için test projeniz için test ayarları dosyasını Visual Studio'da açın, **rol** ve **Test Denetleyicilerini Yönet** için açılan **denetleyicisi**alan.

   **Test denetleyicisini Yönet** iletişim kutusu açılır.

1. Test aracısı test denetleyicisi listesinde değiştirmek istediğiniz test denetleyicisinin adını seçin. Test denetleyicisi listede görünmüyorsa, test denetleyicisinin doğru kaydedilmiş olduğunu denetleyin. Daha fazla bilgi için test denetleyicisinin nasıl yapılandırılacağı hakkında aşağıdaki yordama bakın.

1. (İsteğe bağlı) İçinde **Test aracıları** bölmesinde, özelliklerini değiştirmek istediğiniz test aracısı bilgisayarı seçin.

1. Seçin **özellikleri**.

1. Aşağıdaki test aracısı özelliklerini gerektiği gibi değiştirin:

|Test aracısı özelliği|Açıklama|
|-|-----------------|
|**Ağırlığı**|Test aracılarını farklı performans düzeyleriyle kullandığınızda yükü dağıtmak için kullanılır. Örneğin, 100 ağırlığı ile bir test aracısı, 50 ağırlığı ile bir test aracısı yükünün iki katı alır.|
|**IP geçişi**|IP geçişini yapılandırmak için kullanılır. IP geçişi, bir IP adresi aralığı kullanarak bir sunucuya istek göndermek bir test aracısı sağlar. Bu, farklı istemci bilgisayarlardan gelen çağrıların benzetimini yapar.<br /><br /> Yük testiniz web grubuna erişiyorsa IP geçişi önemlidir. Çoğu yük dengeleyicileri, istemcinin IP adresini kullanarak bir istemci ve belirli bir web sunucusu arasında benzeşim kurar. Tüm istekler tek bir istemciden geliyor gibi görünüyorsa, yük dengeleyicisi yükü dengelemez. Web grubunda iyi bir yük dengesi edinmek için istekleri bir dizi IP adreslerinden geldiğinden emin olun. **Not:** bir ağ bağdaştırıcısı belirtebilir veya kullanın **(Tümü Atanmamış)** otomatik olarak şu anda kullanılmayan birini seçmek için. <br /><br /> IP geçiş özelliğini kullanmak için Visual Studio Test aracısı hizmetinin o aracı bilgisayar için Yöneticiler grubundaki bir kullanıcı olarak çalıştırılması gerekir. Bu kullanıcı, aracı kurulumu sırasında seçilir, ancak hizmet özelliklerini değiştirme ve yeniden başlatarak değiştirilebilir.<br /><br /> IP geçişinin düzgün çalıştığını doğrulamak için IIS web sunucusunda günlüğe kaydetmeyi etkinleştirmek için isteklerin yapılandırdığınız IP adreslerinden geldiğini doğrulamak için IIS günlüğü işlevini kullanın.|
|**Öznitelikler**|Test aracısı seçiminde kullanılabilecek ad/değer çiftleri kümesi. Örneğin, bir test belirli bir OS gerektirebilir. Öznitelik ekleyebilirsiniz **rolleri** sekmesinde test öznitelikleri eşleşen bir test aracısı seçmek için ayarları dosyası ve bunlar kullanılabilir. Birden fazla makinede test çalıştırmak isterseniz, testlerinizi çalıştırmak üzere yapılandırılmış test ayarları rolünde bir öznitelik oluşturun ve sonra ilgili rolde kullanmak istediğiniz her test aracısı üzerinde eşleştirme özniteliğini yapılandırın... **Not:** Bu ayar yalnızca bu öznitelikler sadece Visual Studio için test ayarlarında kullanılır çünkü bir proje için kaydedilmemiş bir test denetleyicisiyle kayıtlı test aracıları için kullanılabilir.|

Değişiklikleri hemen yürürlüğe girer fakat çalışan testleri etkilemez Aracısı ağırlığı ve test aracısı özniteliği test edin. IP adresi aralığı, test denetleyicisi yeniden başlatıldıktan sonra etkili olur.

(İsteğe bağlı) Bir test aracısı durumunu değiştirmek için listedeki aracıyı seçin ve ardından aracının geçerli duruma dayanarak kullanılabilir seçeneklerden eylemini seçin.

> [!NOTE]
> Test aracısını bir işlem olarak çalışıyorsa, test aracısının yüklü olduğu bilgisayarda çalışan bildirim alanında simgesinden test aracısın durumu yönetin. Bu test aracısı durumunu gösterir. Başlat, Durdur veya bu aracı kullanarak bir işlem olarak çalışıyorsa aracıyı yeniden başlatın.

## <a name="configure-a-test-controller"></a>Bir test denetleyicisi yapılandırın

Bir test denetleyicisini yapılandırmak için kullanmanız gerekir **Takım Test denetleyicisi yapılandırma aracı**. Test denetleyicinizi yapılandırırken, farklı proje koleksiyonuyla test denetleyicisini Kaydet veya proje koleksiyonundan test denetleyicisi kaydını silin.

Test denetleyiciniz, Team Foundation Server Proje koleksiyonu ile kaydetmek istiyorsanız, test denetleyicisi hizmeti için kullandığınız hesabın hesabı veya proje koleksiyonu için proje koleksiyonu Test hizmeti hesapları grubunun bir üyesi olması gerekir test denetleyicisi yapılandırma aracını çalıştırmak için kullandığınız bir proje koleksiyonu yöneticisi olması gerekir.

> [!NOTE]
> Mevcut ortamlar proje koleksiyonunda bulunan proje koleksiyonundan test denetleyicisi kaydını kaldırırsanız da, ortamları, Proje Koleksiyonu taşıdığınız, yine de korunur ve taşınan projesi koleksiyonundaki test denetleyicisine yeniden kaydedin.

### <a name="to-configure-a-test-controller"></a>Bir test denetleyicisini yapılandırmak için

1. Test denetleyicinizi istediğiniz zaman yeniden yapılandırmak üzere aracı çalıştırmak için seçin **Başlat** > **Test denetleyicisi yapılandırma aracı**.

     **Test denetleyicisini Yapılandır** iletişim kutusu görüntülenir.

2. Test denetleyicisi hizmetinizin oturum açma hesabı olarak kullanılacak olan kullanıcıyı seçin.

    > [!NOTE]
    > Null parolalar kullanıcı hesapları için desteklenmez.

4. (İsteğe bağlı) Test denetleyicinizi bir laboratuar ortamında kullanmak istiyor musunuz, ancak yalnızca çalıştırmak için Visual Studio'dan Temizle testleri **kaydı test denetleyicisi takım projesi koleksiyonuyla**.

5. (İsteğe bağlı) Yük testi için test denetleyicisi yapılandırmak için seçin **yük testi için test denetleyicisini Yapılandır**. SQL Server örneği girmeniz **Oluştur yük testi sonuçları veritabanında aşağıdaki SQL Server örneğinde**.

> [!NOTE]
> Daha fazla sorun giderme test denetleyicileri hakkında daha fazla bilgi için bkz. [yüklemek ve test denetleyicisilerinin](../test/lab-management/install-configure-test-agents.md).

## <a name="manage-your-agents-when-you-run-your-tests-with-a-test-controller"></a>Bir test denetleyicisiyle testlerinizi çalıştırdığınızda aracılarınızı yönetme

Visual Studio için test ayarlarınıza uygulamanız için roller eklediğinizde, her rolünüz için aracı özellikleri ekleyebilirsiniz. Bu, hangi test aracılarının bu rol için kullanılabilen belirler. Kullanarak testlerinizi çalıştırdığınızda, bu test ayarları, test ayarları için seçili test denetleyicisi gerekli aracıların kullanılabilirliğini belirler. Aşağıdaki aracı kullanılabilirliği belirlendiğinde oluşabilecek durumlar şunlardır:

-   Testlerin çalıştırılması gereken rol için kullanılabilen hiçbir aracı yoktur. Testleriniz çalıştırılamaz. Aşağıdaki eylemlerden birini gerçekleştirin ve sonra testlerinizi yeniden çalıştırın:

    -   Bir aracının bu rol testleri çalıştırmak kullanılabilir olmasını bekleyebilirsiniz.

    -   Çevrimdışı aracılar varsa, bu rol için kullanılabilir, böylece kullanılabilir aracı yeniden başlatabilirsiniz.

    -   Bu rol için doğru aracı özellikleriyle başka bir aracı için test denetleyicisi ekleyebilirsiniz.

    -   Test ayarlarını kullanmak istediğiniz diğer aracıları etkinleştirmek üzere bu rol için aracı özelliklerini değiştirebilirsiniz.

-   Tanılama veri bağdaştırıcılarını çalıştıran bir veya daha fazla rol için kullanılabilir aracı yok. Testleriniz çalıştırılabilir, ancak tanılama veri bağdaştırıcısı çalıştırılamaz. Testlerinizi tanılama veri bağdaştırıcısı olmadan çalıştırabilir veya aşağıdaki eylemlerden birini gerçekleştirin ve testlerinizi yeniden çalıştırın:

    -   Bir aracının bu rol için kullanılabilir olmasını bekleyebilirsiniz.

    -   Çevrimdışı aracılar varsa, bu rol için kullanılabilen, Online'dan için aracı durumunu değiştirme **Test denetleyicisini Yönet** üzerinde **Test** menüsü. Ayrıca, denetleyiciden bağlantısı kesilmişse aracıyı yeniden başlatmanız gerekebilir.

    -   Bu test için ihtiyacınız olabilecek aracılarının testleri çalıştırmakla meşgul olmadığından emin olun. Tüm aracıların durumunu kontrol edebilirsiniz **Test denetleyicisini Yönet** üzerinde **Test** menüsü.

    -   Test denetleyicisi rolü için doğru aracı özellikleriyle başka bir aracı ekleyebilirsiniz.

    -   Kullanmak istediğiniz diğer aracıları etkinleştirmek üzere test ayarları rolünde için aracı özelliklerini değiştirebilirsiniz.

## <a name="load-tests-from-delay-signed-assemblies"></a>Gecikmeli İmzalanmış Derlemelerden Test Yükleme

Test denetleyicisi ve test aracıları yalnızca sağlam imzalı veya imzasız derlemeler test derlemelerini yükleyebilir. Bazı test derlemeleri gecikme-uygulama için üretim derlemelerine erişimi gerektiğinden imzalanmıştır. Ancak, bu derlemeler kuvvetle imzalanmamıştır çünkü bunlar yalnızca test derlemeleridir ve dağılımı değil. Burada derleme test denetleyicisi makineyi de yüklenecek tüm makinelerde bu derlemeler için tanımlayıcı ad doğrulaması devre dışı bırakmalısınız gecikmeli imzalanmış oldukları için bu bütünleştirilmiş kodları yüklenemiyor. Gecikmeli imzalanmış doğrulamayı devre dışı bırakmak için *sn.exe*. Tanımlayıcı ad doğrulamasının atlanmasını istendiği gecikmeli imzalanmış derlemenin ortak anahtar belirteci de eklenmesi gerekebilir.

Kullanım *Sn.exe* (gecikmeli imzalanmış doğrulamayı devre dışı bırakmak için tanımlayıcı ad aracı).

Bu, yalnızca belirtilen derleme için tanımlayıcı ad doğrulamasının komutu çalıştırdığınız bilgisayarda devre dışı bırakır. Bunu sadece yeterli izinleriniz varsa yapabilirsiniz.

Test çalıştırması tamamlandıktan sonra Gecikmeli İmza doğrulamasını kullanarak yeniden etkinleştirebilir *SN.exe* komutu.

İmza doğrulamasını yeniden etkinleştirin ve devre dışı bırakmak için önerilen yol kullanmaktır *SN.exe* betik komutları. Kurulum betik doğrulamayı devre dışı bırakabilir ve bir temizleme betik doğrulamayı yeniden etkinleştirin.

## <a name="see-also"></a>Ayrıca bkz.

- [Test aracılarını yükleme ve yapılandırma](../test/lab-management/install-configure-test-agents.md)