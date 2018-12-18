---
title: Unity için Visual Studio araçlarını kullanma | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- tgt-pltfrm-cross-plat
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e67ec9a2-a449-413e-8930-9a471bd43a06
caps.latest.revision: 7
author: conceptdev
ms.author: crdun
manager: ghogen
ms.openlocfilehash: a7dbe0e13691e5ac0dbf67945728bada3ef4e57f
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51771307"
---
# <a name="using-visual-studio-tools-for-unity"></a>Unity için Visual Studio Araçlarını Kullanma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Bu bölümde, Visual Studio Araçları Unity'nın tümleştirme ve verimlilik özellikleri için nasıl kullanılacağını ve Unity'de geliştirme için Visual Studio hata ayıklayıcısını kullanmayı öğreneceksiniz.  
  
## <a name="unity-integration-and-productivity"></a>Unity tümleştirmesi ve üretkenlik  
 Unity için Visual Studio Araçları, daha üretken olmanıza yardımcı olmak üzere Unity Editor ile tümleştirilir. Bu üretkenliği geliştirme özellikleri genel betik görevleri otomatik hale getirmek ve bilgi bulmak için Unity Editor geçmek zorunda kalmazsınız Unity'de Visual Studio'ya taşıyın.  
  
### <a name="unity-documentation-access"></a>Unity belgeleri erişimi  
 Unity betik belgelerine Visual Studio'dan hemen erişebilir. Unity için Visual Studio Araçları, yerel olarak API belgeleri bulamazsa, çevrimiçi bulmayı deneyecek.  
  
##### <a name="to-access-unity-documentation"></a>Unity belgeleri erişmek için  
  
-   Visual Studio'da vurgulayın veya Unity hakkında bilgi edinin ve basın istediğiniz API imleci **Ctrl + Alt + M, Ctrl + H**  
  
### <a name="unity-monobehavior-scripting-wizard"></a>Unity MonoBehavior komut dosyası Sihirbazı  
 Unity içinde çoğu betikleri MonoBehavior sınıftan türetme ve yöntemlerinden bazıları geçersiz kılma uygulanır. Hızlı bir şekilde MonoBehavior yöntemlerinin aşırı istediğiniz boş tanımları oluşturmak için MonoBehavior Sihirbazı'nı kullanabilirsiniz. Bu sihirbazı kullanarak, metotların listesinden aşırı yükleme, burada, kodunuza eklenir ve nasıl kullanıldıkları hakkında yorum eklenip eklenmeyeceğini karar'ı seçin, istediğiniz bir veya daha fazla yöntemleri belirtebilirsiniz.  
  
 ![Monobehavior Sihirbazı iletişim kutusu. ](../cross-platform/media/vstu-monobehavior-wizard-full.png "vstu_monobehavior_wizard_full")  
  
##### <a name="to-create-empty-monobehavior-method-definitions-by-using-the-monobehavior-wizard"></a>MonoBehavior Sihirbazı'nı kullanarak boş MonoBehavior yöntemi tanımları oluşturmak için  
  
1. Visual Studio'da eklenmesi, ardından basın yöntemleri isteyebileceğiniz imleci konumlandırma **Ctrl + Shift + M** MonoBehavior sihirbazını başlatmak için. Veya zaten uygulandığı bir sonraki yeni yöntemler eklemek istiyorsanız, daha sonra belirtebilirsiniz. tuşuna basarak **Ctrl + Shift + M**.  
  
2. Aşırı yükleme istediğiniz yöntemi seçin. İçinde **betik yöntemleri oluşturun** penceresinin altında **oluşturulacak metotları seçin**, aşırı yükleme istediğiniz her bir yöntemin adı yanındaki onay kutusunu işaretleyin.  
  
3. Görüntülenen framework sürümü emin **Framework sürümü** açılan kullandığınız sürüm eşleşir. Eşleşmiyorsa, açılan değerini kullanmak istediğiniz sürüm olarak değiştirin.  
  
4. Yöntemleri ekleneceği seçin. Varsayılan olarak, imlecin bulunduğu konumda yöntemleri eklenir; başka bir yere eklemek istiyorsanız, sınıfınız içinde zaten uygulanmış herhangi bir yöntemi sonra bunları eklemek seçebilirsiniz. Bu konumlardan birini seçmek için değerini değiştirmek **noktasını** açılan listeyi istediğiniz konum.  
  
5. Seçtiğiniz yöntemleri için yorum oluşturun, işaretlemek için sihirbazın istiyorsanız **metot açıklamaları oluştur** onay kutusu. Bu açıklamalar, yöntem zaman çağrılır ve genel sorumlulukları nelerdir anlamanıza yardımcı olması için yöneliktir.  
  
6. Seçin **Tamam** düğmesini tıklatarak sihirbazdan çıkın ve yöntemleri kodunuza ekleyin.  
  
   MonoBehavior Sihirbazı'nı Unity API hala öğrenme aşamasında veya alışkın olmadığınız bir yöntemi aşırı yüklemek, ihtiyacınız olduğunda özellikle yararlıdır. Unity API ile daha deneyimli haline geldiğinden, zaten alışık olduğunuz yöntemleri hızla oluşturmak için hızlı MonoBehavior Sihirbazı'nı tercih edebilirsiniz.  
  
#### <a name="quick-monobehavior-scripting-wizard"></a>Hızlı MonoBehavior komut dosyası Sihirbazı  
 Zaten Unity API ile ilgili bilgi sahibi olduğunuz, hızlı MonoBehavior Sihirbazı'nı kullanarak aşırı yüklenmiş yöntemler bile daha hızlı bir şekilde uygulayabilir. Bu sihirbazı kullanarak, imleç konumundan metot açıklamaları olmadan eklenen tek yöntemi belirtebilirsiniz.  
  
 ![Hızlı monobehavior Sihirbazı iletişim kutusu. ](../cross-platform/media/vstu-monobehavior-wizard-quick.png "vstu_monobehavior_wizard_quick")  
  
###### <a name="to-create-an-empty-monobehavior-method-definition-by-using-the-quick-monobehavior-wizard"></a>Hızlı MonoBehavior Sihirbazı'nı kullanarak bir boş MonoBehavior yöntem tanımını oluşturmak için  
  
1.  Visual Studio'da, eklenmesi, ardından basın yöntemi istediğiniz imleci konumlandırma **Ctrl + Shift + Q** hızlı MonoBehavior sihirbazını başlatmak için. Diğer MonoBehavior Sihirbazı, imleç kasıtlı olarak yeni yönteme eklenen her zaman bu sihirbaz var kullanırken hizalamanız gerekir.  
  
2.  Emin olun sağ alt köşesinde görüntülenen framework sürümü **betik yöntemi oluşturma** penceresi kullandığınız sürüm eşleşir. Eşleşmiyorsa, açılan değerini kullanmak istediğiniz sürüm olarak değiştirin.  
  
3.  Aşırı yükleme istediğiniz yöntemini bulun. Oluşturma betiği yöntemi penceresinde, metin kutusunda yöntemin adını yazmaya başlayın. Girmiş olduğunuz adları eşleşen yöntemlerin listesi görünür.  
  
4.  Aşırı yükleme istediğiniz yöntemi seçin. Listeden istediğiniz yöntemi görüntülendiğinde seçin fare ve ok tuşlarıyla tuşuna **Enter**. Listesindeki tek yöntem ise, yalnızca basabilirsiniz **Enter**. Yöntemi, kodunuza eklenir.  
  
### <a name="unity-project-explorer"></a>Unity Proje Gezgini  
 Unity Proje Gezgini, Visual Studio içinde Unity projenizde gitmek için kullanabilirsiniz.  
  
 ![Unity Proje Gezgini penceresi. ](../cross-platform/media/vstu-unity-project-explorer.png "vstu_unity_project_explorer")  
  
##### <a name="to-view-the-unity-project-explorer"></a>Unity Proje Gezgini görüntülemek için  
  
- Visual Studio'da ana menüde seçin **görünümü**, **Unity Proje Gezgini**. Klavye: **Alt + SHIFT + E**  
  
   ![Unity Proje Gezgini penceresini görüntüleyin. ](../cross-platform/media/vstu-view-unity-project-explorer.png "vstu_view_unity_project_explorer")  
  
  Unity Proje Gezgini tüm, Unity proje dosyalarınızı ve dizinlerinizi, Unity Editor'ın yaptığı aynı şekilde gösterir: Bu dosyalar ile yalnızca kodunuzu içeren Çözüm Gezgini'nde, unity betiklerinizde gezinmek ve bunları olarak görüntüler farklı Projeler ve Unity için Visual Studio Araçları tarafından oluşturulan çözüm bunları düzenler. Özellikle büyük projeler içinde Unity proje Gezgini'ni kullanarak değiştirmek istediğiniz betiğini bulmak kolaydır; Ayrıca, diğer dosya türlerini değiştirmek kolaylaştırır — Örneğin, metin tabanlı yapılandırma dosyaları — Visual Studio çözüm içindeki projeleri birine eklemeden olmadan Visual Studio'da.  
  
### <a name="unity-error-list"></a>Unity hata listesini  
 Bir Unity örneğine bağlı olduğunda, Visual Studio'nun içinde Unity konsolundan gelen iletileri görüntüleyebilirsiniz. Bu, hataları ve Uyarıları unity'den içerir. Visual Studio'nun iletilerinin görüntülenip **hata listesi** penceresi; hata Unity iletileri görüntülenir **hataları** sekmesi uyarı iletileri üzerinde **uyarıları** sekmesinde ve diğer iletiler — Örneğin, Debug.Log Unity API kullanılarak gönderilen iletileri — görüntülenir **iletileri** sekmesi.  
  
 İletileri görmek için Unity projeniz olmalıdır [projenize Unity Player'da hata ayıklama](#debugging-your-project-in-a-unity-player) betik hata ayıklama desteği ve Visual Studio Araçları Visual Studio sürümünüz için doğru olan Unity paketini içeri aktarmak için ve Visual Studio olmalıdır [Unity için Visual Studio bağlanma](#connecting-visual-studio-to-unity).  
  
 Hataları, uyarıları ve Visual Studio'nun içinde Unity iletileri görmek istemiyorsanız **hata listesi** penceresinde devre dışı bırakabilirsiniz bunları yapılandırma menüde.  
  
### <a name="keyboard-shortcuts"></a>Klavye kısayolları  
 Visual Studio işlevselliği için Unity araçları, klavye kısayollarını kullanarak hızlı şekilde erişebilirsiniz. Kullanılabilir kısayolları bir özeti aşağıda verilmiştir.  
  
|Komut|Kısayol|Kısayol komut adı|  
|-------------|--------------|---------------------------|  
|MonoBehavior Sihirbazı'nı açın|**Ctrl+Shift+M**|**EditorContextMenus.CodeWindow.ImplementMonoBehaviours**|  
|Hızlı MonoBehavior Sihirbazı'nı açın|**Ctrl+Shift+Q**|**EditorContextMenus.CodeWindow.QuickMonoBehaviours**|  
|Unity proje Gezgini'ni açın|**Alt+Shift+E**|**View.UnityProjectExplorer**|  
|Unity belgeleri erişimi|**Ctrl+Alt+M, Ctrl+H**|**Help.UnityAPIReference**|  
|Unity (oynatıcı veya düzenleyici) hata ayıklayıcının|**_Varsayılan yok_**|**Debug.AttachUnityDebugger**|  
  
 Varsayılan beğenmezseniz kısayol tuş birleşimleri değiştirebilirsiniz. Bunun nasıl değiştirileceği hakkında daha fazla bilgi için bkz: [belirleme ve Visual Studio'daki klavye kısayollarını özelleştirme](https://msdn.microsoft.com/library/5zwses53.aspx).  
  
## <a name="unity-debugging"></a>Unity hata ayıklama  
 Unity için Visual Studio Araçları hem Düzenleyici hem de Visual Studio'nun güçlü hata ayıklayıcısını kullanarak Unity projeniz için oyun betikleri hatalarını ayıklamanıza olanak tanır.  
  
###  <a name="connecting-visual-studio-to-unity"></a> Unity için Visual Studio bağlanma  
 Unity için Visual Studio Araçları UDP bağlantı Unity ile iletişim kurar. Başka bir deyişle, yerel olarak çalışan bir Unity örneğine veya ağ üzerindeki herhangi bir tam olarak aynı şekilde bağlanabilirsiniz. Herhangi bir Unity örnekleri kullanarak ağınızda görebilirsiniz bağlanabilir **Unity örneği Seç** iletişim.  
  
##### <a name="to-open-the-select-unity-instance-dialog"></a>Unity örneği Seç iletişim kutusunu açmak için  
  
-   Visual Studio'da ana menüde seçin **hata ayıklama**, **Unity hata ayıklayıcı iliştirmek**.  
  
     ![Unity, hata ayıklayıcısını İliştir. ](../cross-platform/media/vstu-debugging-attach-unity-debugger.png "vstu_debugging_attach_unity_debugger")  
  
-   *Veya*, Visual Studio durum çubuğunda Visual Studio'nun sağ alt köşedeki Tak simgesini seçin.  
  
     ![Bu simge, Unity için VSTU bağlı gösterir. ](../cross-platform/media/vstu-connection-connected.png "vstu_connection_connected")  
  
> [!TIP]
>  Tak simgeyi bir onay işareti gösterir, zaten bir Unity örneğine bağlı olursunuz.  
  
 **Unity örneği Seç** iletişim bağlanabilirsiniz her bir Unity örneğine hakkında bazı bilgiler görüntüler.  
  
 ![Bağlanmak için Unity örneği seçin. ](../cross-platform/media/vstu-connection-to-unity.png "vstu_connection_to_unity")  
  
 **Project**  
 Unity'nın bu örneğinde çalışan Unity proje adı.  
  
 **Makine**  
 Unity'nın bu örneğinin çalıştığı cihaz ve bilgisayar adı.  
  
 **Türü**  
 **Düzenleyici** Unity'nın bu örneğinin Unity Düzenleyicisi'nin; bir parçası olarak çalışıyorsa **Player** Unity'nın bu örneğinin bir oynatıcı ise.  
  
 **Bağlantı noktası**  
 Bu Unity örneği üzerinden iletişim UDP yuva bağlantı noktası numarası.  
  
> [!IMPORTANT]
>  Unity ve Unity örneği için Visual Studio Araçları bir UDP ağ yuva iletişim kuran olduğundan, bu konuda, güvenlik duvarınızı isteyebilir. Böyle bir durumda VSTU ve Unity iletişim kurabilmesi için bağlantıyı yetkilendirmek zorunda kalırsınız.  
  
###  <a name="debugging-your-project-in-a-unity-player"></a> Projenize Unity Player'da hata ayıklama  
 Unity için Visual Studio Araçları, Unity Editor çalışmadığında bir oynatıcı veya platforma özel sorunların hatalarını ayıklamak için çalışan doğrudan Unity uygulamanıza bağlanabilirsiniz.  
  
##### <a name="to-enable-script-debugging-in-a-unity-player"></a>Unity Player'da hata ayıklamayı etkinleştirmek için  
  
- Betik hata ayıklama etkin olan bir geliştirme derleme oluşturmakta olduğunuz emin olun. Unity projeniz yapı ayarlarında işaretlemek **geliştirme derleme** ve **betik hata ayıklamasını** onay kutularını.  
  
  ![Hata ayıklama için Unity derleme ayarlarını yapılandırın. ](../cross-platform/media/vstu-debugging-build-settings.png "vstu_debugging_build_settings")  
  
  Buna ek olarak, çalışan bir Unity uygulamasında hata ayıklama **Unity Web Oynatıcısı**, bunu kullanacak şekilde yapılandırmanız gerekir **geliştirme yayın kanal**.  
  
##### <a name="to-configure-the-development-release-channel-in-unity-web-player"></a>Unity Web Player geliştirme yayın kanalını yapılandırmak için  
  
- Unity Web Player'da bağlam menüsünde seçin **yayın kanal** emin olun **geliştirme** seçeneği etkinleştirilir.  
  
  > [!IMPORTANT]
  >  Unity 4.2 ve sonraki sürümlerinde, **yayın kanal** bağlam menüsü öğesi, yalnızca Web Oynatıcısı bağlam menüsünde kullanılabilir olduğunda **Alt** bağlam menüsü açıldığında tuşuna basıldığında. Web Oynatıcısı Mac OS X üzerinde çalışıyorsa, basın **seçeneği** bunun yerine anahtar.  
  
  Son olarak, hata ayıklamak istediğiniz bir Unity örneğine bağlı olduğunuzdan emin olun. Bunu nasıl yapacağınız hakkında daha fazla bilgi için bkz: [Unity için Visual Studio bağlanma](#connecting-visual-studio-to-unity) bölümü.  
  
### <a name="debugging-a-dll-in-your-unity-project"></a>Bir DLL içinde Unity projenizde hata ayıklama  
 Geliştirme işlevleri diğer projeleri ile kolayca paylaşılabilir böylece birçok Unity geliştiricileri dış DLL'leri kod bileşenlerinin yazıyorsunuz. Unity için Visual Studio Araçları, Unity projenizdeki başka bir kod ile sorunsuz bir şekilde bu DLL'lerdeki kodun hatalarını ayıklamak kolaylaştırır.  
  
> [!NOTE]
>  Şu anda yalnızca destekler Unity için Visual Studio Araçları DLL'leri yönetilen. C++ ile yazılmış olanlar gibi DLL'leri, yerel kod hata ayıklamayı desteklemiyor.  
  
 Burada açıklanan senaryo kaynak kodu seçtiğinizi varsaydığını unutmayın; diğer bir deyişle, geliştirme veya kendi birinci taraf kodu yeniden kullanarak veya bir üçüncü taraf kitaplığına kod ve Unity projenizde bir DLL olarak dağıtmayı planladığınız kaynağı sahip. Bu senaryoda, kaynak kodu içermeyen bir DLL'nin hata ayıklama açıklamaz.  
  
##### <a name="to-debug-a-managed-dll-project-used-in-your-unity-project"></a>Unity projenizde kullanılan yönetilen DLL projesinde hata ayıklamak için  
  
1. Unity için Visual Studio Araçları tarafından oluşturulan Visual Studio çözümünü mevcut DLL projenize ekleyin. Daha az yaygın olarak, Unity projenizde kod bileşenlerini içerecek yeni bir yönetilen DLL proje başlatılıyor; Bu durumda, Visual Studio çözümüne yeni bir yönetilen DLL projesi bunun yerine ekleyebilirsiniz. Bir çözüme yeni veya mevcut bir proje ekleme hakkında daha fazla bilgi için bkz. [nasıl yapılır: bir çözüme projeler ekleme](https://msdn.microsoft.com/library/vstudio/ff460187.aspx).  
  
    ![Mevcut DLL projenize ekleyin. ](../cross-platform/media/vstu-debugging-dll-add-existing.png "vstu_debugging_dll_add_existing")  
  
    Böylece, yalnızca bir kez bu adımları gerçekleştirmek proje ve çözüm dosyaları yeniden yeniden oluşturmak olsa bile her iki durumda da, Unity için Visual Studio Araçları proje başvurusu tutar.  
  
2. DLL projesi doğru Unity framework profilinde başvuru. Visual Studio'da DLL proje özelliklerinde ayarlama **hedef Framework'ü** özelliğini kullandığınız Unity framework sürümü. Unity temel sınıfı, Unity tam, mikro veya web gibi projenizin hedeflediği sınıf kitaplıklarını temel API uyumluluğuna eşleşen kitaplığı budur. Bu, DLL dosyanızı diğer çerçeveler ya da uyumluluk düzeyleri var, ancak kullandığınız Unity çerçeve sürümünde bulunmayabilir framework yöntemlerini çağırma engeller.  
  
    ![Unity çerçevesini DLL'nin hedef Framework'ü ayarlayın. ](../cross-platform/media/vstu-debugging-dll-target-framework.png "vstu_debugging_dll_target_framework")  
  
3. DLL Unity proje varlık klasörüne kopyalayın. Unity içinde paketlenir ve böylece kullanıcılar çalışma zamanında yüklenebilir Unity uygulamanız ile birlikte dağıtılan dosyaların varlıklardır. DLL çalışma zamanında bağlı olduğundan, DLL'leri varlıklar dağıtılması gerekir. Bir varlık dağıtılması için Unity projenizde varlıklar klasörün içine yerleştirilecek DLL'leri Unity Editor gerektirir. Bunu yapmak için iki yolu vardır:  
  
   - Çıktı DLL ve PDB dosyaları, kendi çıktı klasörüne kopyalar sonrası oluşturulan bir görev eklemek için DLL projesi oluşturma ayarlarını değiştirme **varlıklar** Unity projeniz klasörü.  
  
   - Çıkış klasörünün olacak şekilde ayarlamak için DLL projesi oluşturma ayarlarını değiştirme **varlıklar** Unity projeniz klasörü. DLL hem PDB dosyaları yerleştirilecek **varlıklar** klasör.  
  
     PDB dosyaları, çünkü bunlar DLL'nin hata ayıklama sembolleri içeren ve kaynak kod hâli DLL kod eşleme hata ayıklama için gereklidir. Unity için Visual Studio Araçları, bir DLL'yi oluşturmak için DLL ve PDB bilgileri kullanır. Unity betik altyapısı tarafından kullanılan hata ayıklama sembol biçimi MDB dosyası.  
  
4. Kodunuzdaki hataları ayıklamanıza. Artık, hata ayıklama DLL kaynak kodunuzu birlikte Unity projenizin kaynak kodunu ve tüm hata ayıklama özellikleri gibi kesme noktaları için kullanılır ve kod içerisinde ilerlemeye kullanabilirsiniz.

