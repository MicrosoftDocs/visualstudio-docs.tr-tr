---
title: Bulma ve uzantıları kullanma
ms.date: 06/07/2017
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.ExtensionManager
helpviewer_keywords:
- install extensions
- install packages
- managing extensions visual studio
ms.assetid: 4ca92d93-31b9-47ef-8109-4a429d9e2ca3
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: cc67602db2d830283bb47fe7c3a9728d0d9fd799
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53067913"
---
# <a name="find-and-use-visual-studio-extensions"></a>Visual Studio uzantıları bulma ve kullanma

Visual Studio uzantıları Visual Studio içinde çalıştırın ve yeni veya geliştirilmiş Visual Studio özellikleri sağlayan kod paketlerdir. Visual Studio uzantıları hakkında daha fazla bilgi bulabilirsiniz: [Visual Studio SDK](../extensibility/visual-studio-sdk.md).

Kullanabileceğiniz **Uzantılar ve güncelleştirmeler** iletişim kutusunda, Web siteleri ve diğer konumlardan Visual Studio uzantılarını ve örneklerini yüklemek ve etkinleştirmek, devre dışı bırakmak, güncelleştirmek veya bunları kaldırmak için. (**Araçlar > Uzantılar ve güncelleştirmeler**, veya tür **uzantıları** içinde **hızlı başlatma** pencere). İletişim kutusu, yüklü örnekler ve uzantılar için güncelleştirmeleri de gösterir. Ayrıca, Web sitelerinden uzantıları indirmesi veya diğer geliştiricilerden alın.

> [!NOTE]
> Visual Studio 2015'ten başlayarak, Visual Studio Market'te barındırılan uzantıları otomatik olarak güncelleştirilir. Bu ayarı yoluyla değiştirebilirsiniz **Uzantılar ve güncelleştirmeler** iletişim.  Bölümüne **otomatik uzantı güncelleştirmeleri** altındaki ayrıntılar için.

## <a name="finding-visual-studio-extensions"></a>Visual Studio uzantıları bulma

Uzantılardan yükleyebileceğiniz [Visual Studio Market](https://marketplace.visualstudio.com/vs). Uzantılar; denetimler, örnekler, şablonlar, araçlar veya Visual Studio'ya işlevsellik katan diğer bileşenler olabilir. Visual Studio, VSIX paketi biçimindeki uzantıları destekler; bu proje şablonları içerir, öğe şablonları, **araç kutusu** öğeleri, yönetilen uzantı çerçevesi (MEF) bileşenleri ve VSPackages. Ayrıca indirin ve MSI tabanlı uzantılar yükleyin ancak **Uzantılar ve güncelleştirmeler** iletişim kutusunu etkinleştirin veya devre dışı. Visual Studio Market VSIX hem de MSI uzantıları içerir.

## <a name="installing-or-uninstalling-visual-studio-extensions"></a>Visual Studio uzantıları yükleme veya kaldırma

İçinde **Uzantılar ve güncelleştirmeler**, yüklemek istediğiniz uzantıyı bulun. (Adı veya uzantı adının bir kısmını biliyorsanız, içinde arama yapabilirsiniz **arama** penceresi.) **İndir**'e tıklayın.  Uzantı yükleme için zamanlanır. Visual Studio'nun tüm örneklerini kapatıldıktan sonra uzantınızı yüklenir.

Bağımlılıkları olan bir uzantıyı yüklemeye çalışırsanız, yükleyici bunların yüklenmiş olup olmadığını denetler. Bunlar yüklü değilse **Uzantılar ve güncelleştirmeler** iletişim kutusunda uzantıyı yükleyebilmeniz için önce yüklenmesi gereken bağımlılıklar listelenmiştir.

Bir uzantıyı kullanmayı bırakmak isterseniz devre dışı bırakabilir veya kaldırabilirsiniz. Bir uzantı devre dışı bırakıldığında yüklü kalır, ancak etkin değildir. Yalnızca VSIX uzantılarını devre dışı bırakabilirsiniz; MSI kullanarak yüklenmiş uzantıları sadece kaldırılabilir. Uzantı bulun ve tıklatın **kaldırma** veya **devre dışı**. Devre dışı bırakılmış bir uzantıyı kaldırmak için Visual Studio'yu yeniden başlatmanız gerekir.

## <a name="per-user-and-administrative-extensions"></a>Kullanıcı başına ve yönetim uzantıları

Uzantıların çoğu kullanıcı başına uzantılar ve yüklenmiş *%LocalAppData%\Microsoft\VisualStudio\\< Visual Studio sürümü\>\Extensions\\*  klasör. Bazı uzantılar yönetimsel uzantıları ve yüklenmiş *\<Visual Studio yükleme klasörü > \Common7\IDE\Extensions\\* klasör.

Hata veya kötü amaçlı kod içerebilecek uzantıları karşı sisteminizi korumak için yalnızca Visual Studio normal kullanıcı izinleriyle çalıştırıldığında yüklemek için kullanıcı başına uzantılar kısıtlayabilirsiniz. Başka bir deyişle, Visual Studio Yönetici kullanıcı izinleriyle çalıştırdığınızda kullanıcı başına uzantılar devre dışı bırakılır. Bunu yapmak için Git **Uzantılar ve güncelleştirmeler** seçenekler sayfası (**Araçlar > Seçenekler** > **ortam** > **uzantıları ve güncelleştirmeler**, veya yazmanız yeterlidir **uzantısı** içinde **hızlı başlatma** pencere). NET **bağımsız kullanıcı uzantılarının yönetici olarak çalışırken yük** onay kutusunu işaretleyin ve ardından Visual Studio'yu yeniden başlatın.

## <a name="automatic-extension-updates"></a>Otomatik uzantı güncelleştirmeleri

Kullanıcı başına uzantılar, yeni bir sürümü için Visual Studio Market kullanılabilir olduğunda otomatik olarak güncelleştirilir.  Uzantının yeni sürümünü algılanır ve arka planda ve sonraki yeniden başlatmada Visual Studio'nun yüklü, uzantının yeni sürümünü çalıştırırsınız.

Yalnızca kullanıcı başına uzantılar otomatik olarak güncelleştirilebilir.  Tüm kullanıcılar güncelleştirilmez ve aracılığıyla yeni sürümleri yine de el ile yüklemek için yüklenen yönetim uzantıları **Uzantılar ve güncelleştirmeler** iletişim kutusunun **güncelleştirmeleri** düğümü. Hangi uzantıların uzantının Ayrıntılar bölmesinde otomatik olarak güncelleştirilecek gördüğünüz **Uzantılar ve güncelleştirmeler** iletişim.

Otomatik Güncelleştirmeler devre dışı bırakmak istiyorsanız, tüm uzantıları veya yalnızca belirli uzantılara özelliği devre dışı bırakabilirsiniz.

- Tüm uzantılar için Otomatik Güncelleştirmeler devre dışı bırakmayı tercih **Uzantılar ve güncelleştirmeler ayarlarınızı değiştirin** bağlantısını **Uzantılar ve güncelleştirmeler** iletişim kaldırın **otomatik olarak güncelleştir Uzantıları**.

- Belirli bir uzantı için Otomatik Güncelleştirmeler devre dışı bırakmak için işareti kaldırın **bu uzantıyı otomatik olarak güncelleştir** seçeneği uzantının ayrıntıları bölmesinde sağ alt tarafında **Uzantılar ve güncelleştirmeler** iletişim.

> [!NOTE]
> Visual Studio 2015 güncelleştirme 2'de başlayarak, belirtebilirsiniz (içinde **Araçlar > Seçenekler > ortam > Uzantılar ve güncelleştirmeler**) için kullanıcı başına uzantılar, tüm kullanıcı uzantıları veya her ikisi (varsayılan Otomatik Güncelleştirmeler isteyip istemediğinizi ayar).

## <a name="extension-crashunresponsiveness-notifications"></a>Uzantı kilitlenme/yanıt vermeyi durdurma sorununa bildirimleri

Yeni **Visual Studio 2017 sürüm 15.3**, Visual Studio bildirir, bir uzantı bir önceki oturumu sırasında içindeki bir kilitlenme konusuydu gerçeğe aykırı. Visual Studio kilitleniyor, özel durum yığını depolar. Visual Studio başlatılır, sonraki açışınızda yaprak ile başlayan ve temel çalışma yığını inceler. Visual Studio çerçeve uzantı yüklü ve etkin bir parçası olan bir modüle ait olduğunu belirlerse, bir bildirim gösterilir.

Yeni **Visual Studio 2017 sürüm 15.6**, Visual Studio ayrıca bildirir, bir uzantı yanıt vermediği UI neden gerçeğe aykırı.

Bu bildirimleri gösterilirken, bildirim Yoksay veya aşağıdaki eylemlerden birini gerçekleştirin:

- Seçin **bu uzantıyı devre dışı**. Visual Studio, uzantıyı devre dışı bırakır ve devre dışı bırakma etkinleşmesi için sisteminizi yeniden başlatması gerek olup olmadığını bildirir. Uzantı yeniden etkinleştirebilirsiniz **Uzantılar ve güncelleştirmeler** istiyorsanız iletişim kutusu.

- Seçin **bu iletiyi bir daha gösterme**.
  - Bildirim önceki bir oturumda bir kilitlenme ilgiliyse, Visual Studio artık bu uzantıyla ilişkili bir kilitlenme olduğunda bir uyarı gerçekleşir gösterilir. Bu uzantı veya kilitlenme veya diğer uzantıları ile ilişkilendirilebilen yanıt vermeyi durdurma sorununa yanıt vermeyi durdurma sorununa ilişkilendirilebilir zaman visual Studio hala bildirimleri göster.
  - Bildirim yanıt vermeyi durdurma sorununa ilgiliyse, bu uzantının yanıt vermeyi durdurma sorununa ile ilişkili olduğunda IDE artık bir bildirim gösterilir. Visual Studio hala bu uzantı için kilitlenme ile ilgili bildirimleri ve diğer uzantılar için kilitlenme ve yanıt vermeyi durdurma sorununa ilgili bildirimleri de gösterilir.

- Seçin **daha fazla bilgi edinin** bu sayfaya geliyor.

- Seçin **X** bildirimi kapatmak için bildirim sonunda düğmesi. Gelecekteki bir kilitlenme veya kullanıcı Arabirimi yanıt vermeyi durdurma sorununa ile ilişkilendiriliyor uzantısı örneklerinin yeni bir bildirim görüntülenir.

> [!NOTE]
> Bir kullanıcı Arabirimi yanıt vermeyi durdurma sorununa veya kilitlenme bildirimi yalnızca bir uzantının modüllerinin yığında UI yanıt vermiyor veya kilitlenme ortaya çıktığında anlamına gelir. Bu mutlaka uzantısı sorunlu olduğunu gelmez. Bu uzantı, yanıt vermeyen kullanıcı Arabirimi veya kilitlenme sırayla sonuçlandı Visual Studio'nun bir parçası olan kod adlı mümkündür. Ancak, bildirim yine de kullanıcı Arabirimi yanıt vermeyi durdurma sorununa veya kilitlenme sonuçlanan uzantı sizin için önemli değilse yararlı olabilir. Bu durumda, uzantıyı devre dışı kullanıcı Arabirimi yanıt vermeyi durdurma sorununa veya kilitlenme gelecekte üretkenliğinizi etkilemeden önler.

## <a name="sample-master-copies-and-working-copies"></a>Örnek ana kopyalar ve çalışma kopyaları

Çevrimiçi bir örneği yüklediğinizde, çözüm iki konumda depolanır:

- Belirtilen konumda bir çalışma kopyası depolanır **yeni proje** iletişim kutusu.

- Ayrı bir ana kopya bilgisayarınızda depolanır.

Kullanabileceğiniz **Uzantılar ve güncelleştirmeler** iletişim kutusu örneklerle ilgili şu görevleri gerçekleştirebilirsiniz:

- Yüklediğiniz örneklerin ana kopyalarını listeleyin.

- Bir örneğin ana kopyasını devre dışı bırakın veya kaldırın.

- Örnek Paketleri (bir teknoloji veya özellik ile ilgili örnek koleksiyonları) yükleyin.

- Tek tek çevrimiçi örnekleri yükleyin. (Ayrıca bunu yapabilirsiniz **yeni proje** iletişim kutusu.)

- Yüklü örnekler için kaynak kodu değişiklikleri yayımlandığında güncelleştirme bildirimlerini görüntüleyin.

- Bir güncelleştirme bildirimi olduğunda yüklü bir örneğin ana kopyasını güncelleştirin.

## <a name="installing-without-using-the-extensions-and-updates-dialog-box"></a>Uzantılar ve güncelleştirmeler iletişim kutusunu kullanmadan yükleme

İçinde paketlenmiş Uzantılar *.vsix* dosyaları kullanılabilir Visual Studio Market dışındaki konumlarda. **Uzantılar ve güncelleştirmeler** iletişim kutusunda, bu dosyaları silemese ancak yükleyebileceğiniz bir *.vsix* dosyasına çift veya bir dosya seçip tuşuna basarak dosya **Enter**anahtarı. Bundan sonra yalnızca yönergeleri izleyin. Uzantı yüklendiğinde, kullanabileceğiniz **Uzantılar ve güncelleştirmeler** etkinleştirmek, devre dışı bırakmak veya kaldırmak için iletişim kutusu.

## <a name="extension-types-not-supported-by-the-extensions-and-updates-dialog-box"></a>Uzantı türleri Uzantılar ve güncelleştirmeler iletişim kutusu tarafından desteklenmiyor

Visual Studio Microsoft Installer (MSI) tarafından yüklenen Uzantıları desteği devam eder ancak ile **Uzantılar ve güncelleştirmeler** yapmadan iletişim kutusu.

> [!TIP]
> MSI tabanlı bir uzantı içeriyorsa bir *extension.vsixmanifest* dosya, uzantısı görünür **Uzantılar ve güncelleştirmeler** iletişim kutusu.