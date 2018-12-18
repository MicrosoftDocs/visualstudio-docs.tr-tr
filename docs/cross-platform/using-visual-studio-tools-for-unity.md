---
title: Unity için Visual Studio araçlarını kullanma | Microsoft Docs
ms.custom: ''
ms.date: 07/03/2018
ms.technology: vs-unity-tools
ms.topic: conceptual
ms.assetid: e67ec9a2-a449-413e-8930-9a471bd43a06
author: therealjohn
ms.author: johmil
manager: crdun
ms.workload:
- unity
ms.openlocfilehash: 380618e0cee57a1cf0f45a1324d150170e5ee16e
ms.sourcegitcommit: 5c049194fa256b876ad303f491af11edd505756c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53027347"
---
# <a name="use-visual-studio-tools-for-unity"></a>Unity için Visual Studio Araçları’nı Kullanma

Bu bölümde, Visual Studio Araçları Unity'nın tümleştirme ve verimlilik özellikleri için nasıl kullanılacağını ve Unity'de geliştirme için Visual Studio hata ayıklayıcısını kullanmayı öğreneceksiniz.

## <a name="open-unity-scripts-in-visual-studio"></a>Visual Studio'da Unity betikleri açma

Visual Studio olduğunda [Unity için dış betik düzenleyicisi olarak](getting-started-with-visual-studio-tools-for-unity.md#configure-unity-for-use-with-visual-studio), Unity Düzenleyicisi'nden herhangi bir komut dosyası açılırken otomatik olarak başlatılır veya Visual Studio anahtara seçilen betiğiyle açın. Yalnızca bir betik Unity projenizde çift tıklayın.

Alternatif olarak, Visual Studio komut dosyası içermeyen kaynak düzenleyicide açık seçerek açabilirsiniz **C# proje Aç** gelen **varlıklar** Unity menüsünde.

![C# proje Aç](media/vstu_open-csharp-project.png)

## <a name="unity-documentation-access"></a>Unity belgeleri erişimi

Unity betik belgelerine Visual Studio'dan hemen erişebilir. Unity için Visual Studio Araçları, yerel olarak API belgeleri bulamazsa, çevrimiçi bulmayı deneyecek.

- Visual Studio'da vurgulayın veya Unity hakkında bilgi edinin ve basın istediğiniz API imleci **Ctrl**+**Alt**+**M**, **Ctrl**+**H**

## <a name="intellisense-for-unity-api-messages"></a>API Unity iletileri için IntelliSense

IntelliSense kod tamamlama, MonoBehaviour betiklerde API Unity iletilerini Uygula kolaylaştırır ve Unity API öğrenmeye yardımcı olur. Unity iletileri için IntelliSense kullanmak için:

1. Türetilen bir sınıfın gövdesi içinde yeni bir satıra imleci `MonoBehaviour`.

2. Gibi bir Unity adını yazmaya başlama iletisi `OnTriggerEnter`.

3. Harf "**ontri**" bir IntelliSense Öneri listesi görünür girilmiş.

   ![IntelliSense Kullanma](media/vstu_intellisense1.png)

4. Seçim listesindeki üç yolla değiştirilebilir:

    - İle **yukarı** ve **aşağı** ok tuşları.

    - İstenen öğe üzerinde fare ile tıklayarak.

    - İstenen öğe adı devam ederek.

5. IntelliSense, tüm gerekli parametreleri de dahil olmak üzere seçili Unity ileti ekleyebilirsiniz:

    - Tuşuna basarak **sekmesini**.

    - Tuşuna basarak **Enter**.

    - Seçili öğeyi çift tıklayarak.

   ![Unity iletisi IntelliSense'de Ekle](media/vstu_intellisense2.png)

## <a name="unity-monobehavior-scripting-wizard"></a>Unity MonoBehavior komut dosyası Sihirbazı

Unity API yöntemlerin listesini görüntülemek ve hızlı bir şekilde boş bir tanım uygulamak için MonoBehavior Sihirbazı'nı kullanabilirsiniz. Bu özellik, özellikle **metot açıklamaları oluştur** seçeneği etkin, Unity API'SİNDE kullanılabilir hala öğreniyorsanız yardımcı olur.

Boş MonoBehavior yöntemi tanımları MonoBehavior Sihirbazı'nı kullanarak oluşturmak için:

1. Visual Studio'da, eklenmesi, ardından basın yöntemleri istediğiniz imleci konumlandırma **Ctrl**+**Shift**+**M** başlatmak için MonoBehavior Sihirbazı.

2. İçinde **betik yöntemleri oluşturun** penceresinde, eklemek istediğiniz her bir yöntemin adı yanındaki onay kutusunu işaretleyin.

3. Kullanım **Framework sürümü** açılır menüsünü kullanarak, istediğiniz sürümü seçin.

4. Varsayılan olarak, yöntemleri imleç konuma eklenir. Alternatif olarak, bunları sınıfınızda değerinin değiştirilmesi tarafından zaten uygulanmış herhangi bir yöntemi sonra eklemeyi seçebilirsiniz **noktasını** istediğiniz konum için açılır.

5. Seçtiğiniz yöntemleri için yorum oluşturun, işaretlemek için sihirbazın istiyorsanız **metot açıklamaları oluştur** onay kutusu. Bu açıklamalar, yöntem zaman çağrılır ve genel sorumlulukları nelerdir anlamanıza yardımcı olması için yöneliktir.

6. Seçin **Tamam** düğmesini tıklatarak sihirbazdan çıkın ve yöntemleri kodunuza ekleyin.

   ![Monobehavior Sihirbazı iletişim kutusu. ](../cross-platform/media/vstu_monobehavior_wizard_full.png "vstu_monobehavior_wizard_full")

## <a name="unity-project-explorer"></a>Unity Proje Gezgini

![Unity Proje Gezgini penceresi. ](../cross-platform/media/vstu_unity_project_explorer.png "vstu_unity_project_explorer")

Unity Proje Gezgini tüm, Unity proje dosyalarınızı ve dizinlerinizi, Unity Editor'ın yaptığı aynı şekilde gösterir. Bu, normal Visual Studio çözümü, projeleri ve Visual Studio tarafından oluşturulan bir çözüm halinde bunları düzenler Gezgini ile Unity betiklerinizde gezinmek daha farklıdır.

- Ana Visual Studio menüsünde **Görüntüle > Unity Proje Gezgini**. Klavye kısayolu: **Alt**+**Shift**+**E**

   ![Unity Proje Gezgini penceresini görüntüleyin. ](../cross-platform/media/vstu_view_unity_project_explorer.png "vstu_view_unity_project_explorer")

## <a name="unity-debugging"></a>Unity hata ayıklama

Unity için Visual Studio Araçları hem Düzenleyici hem de Visual Studio'nun güçlü hata ayıklayıcısını kullanarak Unity projeniz için oyun betikleri hatalarını ayıklamanıza olanak tanır.

### <a name="debug-in-the-unity-editor"></a>Unity Düzenleyicisi'nde hata ayıklama

#### <a name="start-debugging"></a>Hata Ayıklamayı Başlat

1. Visual Studio için Unity tıklayarak bağlanma **yürütmek** etiketli düğme **eklemek için Unity**, veya klavye kısayolunu kullanın **F5**.

   ![Visual Studio'da Yürüt'e tıklayın](media/vstu_play-button.png)

2. Geçiş'i tıklatın ve Unity ile **Play** Düzenleyici'de oyuna çalıştırmak için düğme.

   ![Unity Yürüt'e tıklayın](media/vstu_unity-play-button.png)

3. Oyun bağlıyken, Visual Studio için Unity Düzenleyicisi'nde çalışırken karşılaşılan herhangi bir kesme noktası oyun yürütülmesini Duraklat ve burada oyun Visual Studio'da kesme noktası isabet kod satırının getirecek.

#### <a name="stop-debugging"></a>Hata ayıklamayı Durdur

- Tıklayın **Durdur** düğme Visual Studio'da veya klavye kısayolunu kullanın **Shift + F5 tuşlarına basarak**.

  ![Visual Studio'da Durdur'u tıklatın](media/vstu_stop-debugger.png)

Visual Studio'da hata ayıklama hakkında daha fazla bilgi için bkz: [Visual Studio hata ayıklayıcı ilk bakış](../debugger/debugger-feature-tour.md).

#### <a name="attach-to-unity-and-play"></a>Unity ve Play ekleyin

Eklenen kolaylık sağlamak için değiştirebileceğiniz **eklemek için Unity** düğmesi **ekleme Unity ve Yürüt** modu.

1. Küçük tıklatın **aşağı ok** yanındaki **eklemek için Unity** düğmesi.

1. Seçin **ekleme Unity ve Yürüt** açılan menüden.

    ![Ekleme ve Yürüt](media/vstu_attach-and-play.png)

Yürüt düğmesine etiketli olur **ekleme Unity ve Yürüt**. Bu düğmeye tıklandığında veya klavye kısayolunu kullanarak **F5** artık otomatik olarak geçer Unity Düzenleyicisi ve oyun Visual Studio hata ayıklayıcısını yanı sıra bu düzenleyicide çalıştırır.

Tıklayarak **Durdur** düğme Visual Studio'da veya klavye kısayolunu kullanarak **Shift**+**F5** Unity editor oyun otomatik olarak durdurulur.

### <a name="debug-unity-player-builds"></a>Hata ayıklama Unity Player'da derlemeleri

Visual Studio Unity oyuncularla çeşitli geliştirme derlemelerini ayıklayabilirsiniz.

#### <a name="enable-script-debugging-in-a-unity-player"></a>Unity Player'da betik hata ayıklamasını etkinleştirme

1. Unity yapı ayarları seçerek açın **Dosya > Yapı ayarları**.

2. Yapı Ayarları penceresinde işaretlemek **geliştirme derleme** ve **betik hata ayıklamasını** onay kutularını.

   ![Hata ayıklama için Unity derleme ayarlarını yapılandırın. ](../cross-platform/media/vstu_debugging_build_settings.png "vstu_debugging_build_settings")

#### <a name="select-a-unity-instance-to-attach-the-debugger-to"></a>Hata ayıklayıcıyı iliştirmek için bir Unity örneği Seç

- Visual Studio'da ana menüde seçin **hata ayıklama > Unity hata ayıklayıcı iliştirmek**.

   ![Unity, hata ayıklayıcısını İliştir. ](../cross-platform/media/vstu_debugging_attach_unity_debugger.png "vstu_debugging_attach_unity_debugger")

   **Unity örneği Seç** iletişim bağlanabilirsiniz her bir Unity örneğine hakkında bazı bilgiler görüntüler.

   ![Bağlanmak için Unity örneği seçin. ](../cross-platform/media/vstu_attach-debugger.png "vstu_connection_to_unity")

   **Project**

   Unity'nın bu örneğinde çalışan Unity proje adı.

   **Makine** Unity'nın bu örneğinin çalıştığı cihaz ve bilgisayar adı.

   **Tür** **Düzenleyicisi** Unity'nın bu örneğinin Unity Düzenleyicisi'nin; bir parçası olarak çalışıyorsa **Player** Unity'nın bu örneğinin bir oynatıcı ise.

   **Bağlantı noktası** Unity'nın bu örneğinin üzerinden iletişim UDP yuva bağlantı noktası numarası.

> [!IMPORTANT]
> Unity ve Unity örneği için Visual Studio Araçları bir UDP ağ yuva iletişim kuran olduğundan, bu konuda, güvenlik duvarınızı isteyebilir. Böyle bir durumda VSTU ve Unity iletişim kurabilmesi için bağlantıyı yetkilendirmek zorunda kalırsınız.

### <a name="debug-a-dll-in-your-unity-project"></a>Unity projenizde bir DLL'nin hatasını ayıklayın

Geliştirme işlevleri diğer projeleri ile kolayca paylaşılabilir böylece birçok Unity geliştiricileri dış DLL'leri kod bileşenlerinin yazıyorsunuz. Unity için Visual Studio Araçları, Unity projenizdeki başka bir kod ile sorunsuz bir şekilde bu DLL'lerdeki kodun hatalarını ayıklamak kolaylaştırır.

> [!NOTE]
> Şu anda yalnızca destekler Unity için Visual Studio Araçları DLL'leri yönetilen. C++ ile yazılmış olanlar gibi DLL'leri, yerel kod hata ayıklamayı desteklemiyor.

Burada açıklanan senaryo kaynak kodu seçtiğinizi varsaydığını unutmayın; diğer bir deyişle, geliştirme veya kendi birinci taraf kodu yeniden kullanarak veya bir üçüncü taraf kitaplığına kod ve Unity projenizde bir DLL olarak dağıtmayı planladığınız kaynağı sahip. Bu senaryoda, kaynak kodu içermeyen bir DLL'nin hata ayıklama açıklamaz.

#### <a name="to-debug-a-managed-dll-project-used-in-your-unity-project"></a>Unity projenizde kullanılan yönetilen DLL projesinde hata ayıklamak için

1. Unity için Visual Studio Araçları tarafından oluşturulan Visual Studio çözümünü mevcut DLL projenize ekleyin. Daha az yaygın olarak, Unity projenizde kod bileşenlerini içerecek yeni bir yönetilen DLL proje başlatılıyor; Bu durumda, Visual Studio çözümüne yeni bir yönetilen DLL projesi bunun yerine ekleyebilirsiniz. Bir çözüme yeni veya mevcut bir proje ekleme hakkında daha fazla bilgi için bkz. [nasıl yapılır: bir çözüme projeler ekleme](https://msdn.microsoft.com/library/ff460187.aspx).

   ![Mevcut DLL projenize ekleyin. ](../cross-platform/media/vstu_debugging_dll_add_existing.png "vstu_debugging_dll_add_existing")

   Böylece, yalnızca bir kez bu adımları gerçekleştirmek proje ve çözüm dosyaları yeniden yeniden oluşturmak olsa bile her iki durumda da, Unity için Visual Studio Araçları proje başvurusu tutar.

2. DLL projesi doğru Unity framework profilinde başvuru. Visual Studio'da DLL proje özelliklerinde ayarlama **hedef Framework'ü** özelliğini kullandığınız Unity framework sürümü. Unity temel sınıfı, Unity tam, mikro veya web gibi projenizin hedeflediği sınıf kitaplıklarını temel API uyumluluğuna eşleşen kitaplığı budur. Bu, DLL dosyanızı diğer çerçeveler ya da uyumluluk düzeyleri var, ancak kullandığınız Unity çerçeve sürümünde bulunmayabilir framework yöntemlerini çağırma engeller.

   ![Unity çerçevesini DLL'nin hedef Framework'ü ayarlayın. ](../cross-platform/media/vstu_debugging_dll_target_framework.png "vstu_debugging_dll_target_framework")

3. DLL Unity proje varlık klasörüne kopyalayın. Unity içinde paketlenir ve böylece kullanıcılar çalışma zamanında yüklenebilir Unity uygulamanız ile birlikte dağıtılan dosyaların varlıklardır. DLL çalışma zamanında bağlı olduğundan, DLL'leri varlıklar dağıtılması gerekir. Bir varlık dağıtılması için Unity projenizde varlıklar klasörün içine yerleştirilecek DLL'leri Unity Editor gerektirir. Bunu yapmak için iki yolu vardır:

   - Çıktı DLL ve PDB dosyaları, kendi çıktı klasörüne kopyalar sonrası oluşturulan bir görev eklemek için DLL projesi oluşturma ayarlarını değiştirme **varlıklar** Unity projeniz klasörü.

   - Çıkış klasörünün olacak şekilde ayarlamak için DLL projesi oluşturma ayarlarını değiştirme **varlıklar** Unity projeniz klasörü. DLL hem PDB dosyaları yerleştirilecek **varlıklar** klasör.

   PDB dosyaları, çünkü bunlar DLL'nin hata ayıklama sembolleri içeren ve kaynak kod hâli DLL kod eşleme hata ayıklama için gereklidir. Unity için Visual Studio Araçları, bir DLL'yi oluşturmak için DLL ve PDB bilgileri kullanır. Unity betik altyapısı tarafından kullanılan hata ayıklama sembol biçimi MDB dosyası.

4. Kodunuzdaki hataları ayıklamanıza. Artık, hata ayıklama DLL kaynak kodunuzu birlikte Unity projenizin kaynak kodunu ve tüm hata ayıklama özellikleri gibi kesme noktaları için kullanılır ve kod içerisinde ilerlemeye kullanabilirsiniz.

## <a name="keyboard-shortcuts"></a>Klavye kısayolları

Visual Studio işlevselliği için Unity araçları, klavye kısayollarını kullanarak hızlı şekilde erişebilirsiniz. Kullanılabilir kısayolları bir özeti aşağıda verilmiştir.

|Komut|Kısayol|Kısayol komut adı|
|-------------|--------------|---------------------------|
|MonoBehavior Sihirbazı'nı açın|**CTRL**+**Shift**+**M**|**EditorContextMenus.CodeWindow.ImplementMonoBehaviours**|
|Unity proje Gezgini'ni açın|**Alt**+**Shift**+**E**|**View.UnityProjectExplorer**|
|Unity belgeleri erişimi|**CTRL**+**Alt**+**M, Ctrl**+**H**|**Help.UnityAPIReference**|
|Unity (oynatıcı veya düzenleyici) hata ayıklayıcının|**_Varsayılan yok_**|**Debug.AttachUnityDebugger**|

Varsayılan beğenmezseniz kısayol tuş birleşimleri değiştirebilirsiniz. Bunun nasıl değiştirileceği hakkında daha fazla bilgi için bkz: [tanımlayın ve Visual Studio'daki klavye kısayollarını özelleştirme](../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md).
