---
title: Bir XCode projesini içeri aktarma | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: aa4b8161-d98f-4a1a-9db3-520133bfc82f
ms.technology: vs-ide-mobile
author: corob-msft
ms.author: corob
manager: douge
ms.workload:
- xplat-cplusplus
ms.openlocfilehash: ef3bcde043118d101180c3e21c2278b1fbe6473d
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49846830"
---
# <a name="import-an-xcode-project"></a>Bir XCode Projesini İçeri Aktarma
Microsoft Visual C++ platformlar arası Mobil Geliştirme için Visual Studio'yla, platformlar arası kitaplıklar oluşturun ve diğer projeleri ile kod paylaşın, XCode projelerinizi taşımak için destek içerir. İçeri Aktar Sihirbazı XCode projeleri içeri aktarma işlemini basitleştirir ve C++ kodunu, XCode hedefler için bölme bir statik kitaplık kullanmak ya da paylaşılan kod projesi. İOS özel kodunuzu Visual Studio yönetin ve XCode film şeritleri ve yapıları yapmak için kullanmaya devam edebilirsiniz. Kodu sürekli Visual Studio ve XCode arasında kolaylıkla geçiş hakkında daha fazla bilgi için XCode arasında taşıma değişiklikleri ve Visual Studio bakın.  
  
## <a name="use-the-import-from-xcode-wizard"></a>Xcode'dan İçeri Aktar Sihirbazı'nı kullanma  
 Bu konuda, kod paylaşımı ve platformlar arası çözümler yararlanmak için Visual Studio'ya bir XCode projesini taşıma gösterilmektedir. Bir önkoşul olarak içeri aktarma, dışarı aktarma ve derleme için Visual Studio Mac eşleştirin gerekir. Eşleştirme konusunda yönergeler için bkz [yükleme ve yapılandırma araçları kullanarak iOS derleme](../cross-platform/install-and-configure-tools-to-build-using-ios.md). Ayrıca XCode projenizin ağ üzerinden paylaşın veya taşımak için XCode Sihirbazı'nı İçeri Aktar'ı kullanmak için Visual Studio bilgisayarınızı gerekir.  
  
#### <a name="import-from-xcode"></a>Xcode'dan İçeri Aktar  
  
1. Üzerinde **dosya** menüsünde seçin **yeni**, **alma**, **xcode'dan içeri aktar**. Bu başlatır **xcode'dan içeri aktar** Sihirbazı iletişim kutusu.  
  
    ![İçeri aktarmak için XCode hedef proje seçin](../cross-platform/media/cppmdd_u2_importxcode_choose.PNG "CPPMDD_U2_ImportXCode_Choose")  
  
2. İçinde **bir proje seçin** bölmesinde bir XCode seçmek için Gözat düğmesini seçin *.pbxproj* dosya. Proje dosyasında gidin **seçin XCode proje dosyası** iletişim kutusunda ve ardından **açık**.  
  
    ![Bir proje dosyası seçin Xcode proje dosyası iletişim kutusuna seçin](../cross-platform/media/cppmdd_u2_importxcode_browse.PNG "CPPMDD_U2_ImportXCode_Browse")  
  
    XCode sihirbazından alma seçin **sonraki**.  
  
3. İçinde **varış hedefleri** bölmesinde XCode projesi, Visual Studio projelerine aktarılacak hedefleri seçin. XCode hedefleri, Visual Studio projelerine benzerdir; çoğu, kod ve üreten bir ikili kaynaklar koleksiyonudur. XCode Sihirbazı yalnızca bir ikili, ancak statik bir kitaplık değil, hedef hedefler olarak üretmek hedefler içe izin verir. Sonraki adım konusunu XCode statik kitaplık hedeflerdir.  
  
    ![İçeri Aktarma Sihirbazı Hedef hedefleri bölmesinden XCode](../cross-platform/media/cppmdd_u2_importxcode_destination.jpg "CPPMDD_U2_ImportXCode_Destination")  
  
    Seçilen her hedef için **içeri aktarılacak hedefler**, sihirbaz otomatik olarak ayrı bir statik kitaplık projesine bölünebilir C++ kod dosyaları algılar ve bunları koyar **C++ proje öğeleri** bölümü. Diğer kod ve kaynaklar içinde bırakılır **XCode proje öğeleri** bölümü. Sihirbaz, içeri aktarma işlemi tamamlandığında bu ayrı bir statik kitaplık ve uygulama projeleri Visual Studio'da haline gelir. Varsayılan olarak, birim testi ve framework hedefleri ayrı projelere sihirbaz tarafından bölünür değil.  
  
    Her projede dosyalarıdır değiştirmek için yukarı ve aşağı düğmeleri. Her proje dosyalarında memnun olduğunuzda seçin **sonraki** devam etmek için.  
  
4. İçinde **kitaplık hedefleri** bölmesinde, hangi statik kitaplık hedefler, Visual Studio projelerine aktarılacak bir XCode projesi seçin. Bu bölmede hangi dosyaların bir paylaşılan kod projesinde yerleştirilir ve statik kitaplığı projesinde yerleştirilen sanal seçebilirsiniz. Her hedef **içeri aktarılacak hedefler** listesinde denetleyebilir, dosyaları yerleştirildiğinde **paylaşılan kod proje öğeleri** ve **statik kitaplık proje öğeleri** kullanarak Yukarı ve aşağı düğmeleri.  
  
    ![İçeri aktarma XCode kitaplık hedefleri bölmesinden](../cross-platform/media/cppmdd_u2_importxcode_library.jpg "CPPMDD_U2_ImportXCode_Library")  
  
    Paylaşılan kod proje, kaynak kodu dosyaları Visual Studio'da projeler arasında bir dizi paylaşım bir yoludur. Kod, kendine ait bir proje olarak değil, içeren projenin bir parçası olarak oluşturulmuştur. Paylaşılan kodu içeren projeler farklı mimarileri ve yapılandırmaları olabileceğinden, pek çok platform için oluşturulan kodu içeren tek bir projeye sağlamak için en iyi yolu budur.  
  
    Her proje dosyalarında memnun olduğunuzda seçin **sonraki** devam etmek için.  
  
5. **Genel özellikleri** bölmesi, bir çerçeve arama yolu ve bir üst bilgi arama yoluna tüm iOS projeleri için Visual Studio'da ayarlamak için kullanılabilir. Visual Studio IntelliSense ve kaynak kod gözatma için bu yolları kullanır. Üst bilgiler ve çerçeveleri ortak bir dizi kullanan iOS projeleri oluşturduğunuzda bu genel yolları yararlı olur.  
  
    ![İçeri aktarma XCode genel özellikleri bölmesinden](../cross-platform/media/cppmdd_u2_importxcode_global.jpg "CPPMDD_U2_ImportXCode_Global")  
  
    Bu genel yolları da Visual Studio'da ayarlanabilir **seçenekleri** iletişim. Bunları bulmak için **Araçları** menüsünde **seçenekleri**. İçinde **seçenekleri** iletişim kutusunda Genişlet **Çoklu Platform**, **C++**, **iOS**, **genel özellikleri**.  
  
    Seçin **sonraki** devam etmek için.  
  
6. **Çerçeveleri** bölmesinde göz atmak için Visual Studio tarafından kullanılan yolları yapılandırmak için kullanılır ve projeniz için IntelliSense. Yolları XCode projenizin başvurduğu her bir çerçeve için Visual Studio için erişilebilir olmalıdır. Framework XCode projeleri atıfta bulunan ve Visual Studio framework bulup bulamayacağını görüntüler Sihirbazı'nı denetler. Genel Özellikler ayarladığınız herhangi bir yolu, Visual Studio tarafından bulunması gerekir. Özel durumları çerçeveleri listede listelenir. Bir X ile listelenen her framework framework bulmak Visual Studio için PC tarafından erişilebilen bir yol sağlar. Gözat düğmesini kullanabilirsiniz **...**  kullanmak için bir **klasörü seçin** iletişim yolu bulunamadı. Çerçeve yolu için yerel bir kopya veya ağ üzerinden erişilebilen bir paylaşıma mac'inizde olabilir.  
  
    ![İçeri aktarma XCode çerçeveleri bölmesinden](../cross-platform/media/cppmdd_u2_importxcode_frameworks.jpg "CPPMDD_U2_ImportXCode_Frameworks")  
  
    Seçin **sonraki** devam etmek için.  
  
7. **Proje ayarları** bölmesinde Framework'ü değiştirmek ve Sihirbazın oluşturduğu her proje için üst bilgi arama yolu ayarları dahil olanak tanır. Bu bölme, genel ayarlardan farklı bir projeye özgü yolları ayarlamak için kullanın.  
  
    Belirli bir proje için bir yol ayarlamak için **hedef proje** açılan, proje dosyasını seçin ve ardından öğesinde değerleri ayarlamasına **çerçeve arama Yolu'nu** ve **üst bilgi arama yoluEkle** kontrol eder. Gözat düğmesini kullanabilirsiniz **...**  kullanmak için her denetimi yanında bir **Klasör Seç** yolunu bulmak için iletişim.  
  
    ![XCode projeleri bölmesinden alma](../cross-platform/media/cppmdd_u2_importxcode_projects.jpg "CPPMDD_U2_ImportXCode_Projects")  
  
    Uzak hiçbir Mac Visual Studio'da bu bilgisayar ile eşleştirilmiş varsa **uzak makineyi Yapılandır** bağlantı gösterilir. Eşleştirme konusunda yönergeler için bkz [yükleme ve yapılandırma araçları kullanarak iOS derleme](../cross-platform/install-and-configure-tools-to-build-using-ios.md).  
  
    Sihirbazın ayarlarını kullanarak XCode projesini içeri aktarmayı tercih **alma**.  
  
   İçeri Aktar Sihirbazı XCode projeleri seçili XCode Proje hedefleri için karşılık gelen Visual Studio'da oluşturur. Diğer C++ projeleriyle paylaşılan kodu ayrı bir paylaşılan kod ve statik kitaplık projeleri içinde bölünür. Geri kalan kod iOS uzaktan Visual Studio tarafından oluşturulan kitaplık ve uygulama projeleri yerleştirilir. XCode ve Visual Studio arasında kod taşıma hakkında daha fazla bilgi için bkz. [XCode ve Visual Studio arasındaki eşitleme](../cross-platform/sync-changes-between-xcode-and-visual-studio.md).