---
title: Azure Cloud Services ve sanal makineler için tanılama ayarlama ayarlama | Microsoft Docs
description: Azure cloude Hizmetleri ve sanal makineleri (VM'ler), Visual Studio'da hata ayıklama tanılama ayarlama konusunda bilgi edinin.
author: ghogen
manager: douge
ms.assetid: e70cd7b4-6298-43aa-adea-6fd618414c26
ms.topic: conceptual
ms.workload: azure-vs
ms.date: 06/28/2018
ms.author: mikejo
ms.prod: visual-studio-dev15
ms.technology: vs-azure
ms.openlocfilehash: 2553adf10e2617a43d4e78ded22314088927e348
ms.sourcegitcommit: e03b7a4cab26fbc792f368e3c6b4ca4a03caa786
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/28/2018
ms.locfileid: "52459736"
---
# <a name="set-up-diagnostics-for-azure-cloud-services-and-virtual-machines"></a>Azure Cloud Services ve sanal makineler için tanılamayı ayarlama
Bir Azure bulut hizmeti veya sanal makine sorunlarını gidermek, ihtiyacınız olduğunda, Visual Studio, daha kolay Azure Tanılama'yı ayarlamak için kullanabilirsiniz. Tanılama sistemi veri ve sanal makineler ve bulut hizmetinizi çalıştıran sanal makine örneği günlük verilerini yakalar. Tanılama verileri, seçtiğiniz bir depolama hesabına aktarılır. Azure'da günlüğe kaydetme Tanılama hakkında daha fazla bilgi için bkz [Azure App Service'te Web uygulamaları için tanılama günlüğünü etkinleştirme](/azure/app-service/web-sites-enable-diagnostic-log).

Bu makalede, Visual Studio'yu açın ve Azure tanılama ayarlama öncesinde ve sonrasında dağıtım ayarlamak için kullanma gösteriyoruz. Azure sanal makinelerinde tanılama ayarlama yapma, nasıl tanılama bilgilerini toplamak için türlerini seçin ve toplandıktan sonra bilgileri nasıl görüntüleyeceğinizi öğrenin.

Azure Tanılama'yı ayarlamak için aşağıdaki seçeneklerden birini kullanabilirsiniz:

* Tanılama ayarlarını değiştirin **tanılama Yapılandırması** Visual Studio'da iletişim kutusu. Ayarlar diagnostics.wadcfgx (Azure SDK 2.4 ve önceki sürümlerinde, dosya diagnostics.wadcfg denir) adlı bir dosyaya kaydedilir. Yapılandırma dosyasını doğrudan değiştirebilirsiniz. Dosyayı el ile güncelleştirirseniz, yapılandırma değişiklikleri etkili bulut dağıttığınız açtığında Azure hizmet veya hizmet öykünücüde çalıştırma.
* Cloud Explorer'ı veya Sunucu Gezgini Visual Studio'da bir bulut hizmeti veya çalıştıran bir sanal makine için tanılama ayarları değiştirmek için kullanın.

## <a name="azure-sdk-26-diagnostics-changes"></a>Azure SDK 2.6 tanılama değişiklikleri
Azure SDK 2.6 ve daha sonra Visual Studio projelerinde aşağıdaki değişiklikleri uygulayın:

* Yerel öykünücü artık tanılama destekler. Bu tanılama verileri toplamak ve uygulamanızı geliştirin ve Visual Studio'da test ederken sağ izlemeleri oluşturduğundan emin olmak anlamına gelir. Bağlantı dizesi `UseDevelopmentStorage=true` Azure storage öykünücüsü kullanarak Visual Studio'da bulut hizmeti projenizi çalıştırırken tanılama veri toplamayı etkinleştirir. Tüm Tanılama verileri geliştirme depolama depolama hesabında toplanır.
* Tanılama depolama hesabı bağlantı dizesi `Microsoft.WindowsAzure.Plugins.Diagnostics.ConnectionString` hizmet yapılandırma (.cscfg) dosyasında depolanır. Azure SDK 2.5 diagnostics.wadcfgx dosyasında tanılama depolama hesabı belirtilir.

Bağlantı dizesini temel bazı yolları Azure SDK 2.6 sürümündeki yenilik ve daha sonra Azure SDK 2.4 karşı ve daha önce farklı şekilde çalışır:

* Azure SDK 2.4 ve önceki sürümlerinde, bağlantı dizesini aktarma tanılama günlükleri için depolama hesabı bilgileri almak için tanılama eklentisi bir çalışma zamanı kullanılır.
* Visual Studio Azure SDK 2.6 sürümündeki yenilik ve daha sonra tanılama bağlantı dizesini Azure tanılama uzantısı yayımlama sırasında uygun depolama hesap bilgileriyle ayarlamak için kullanır. Bağlantı dizesini, Visual Studio yayımlama sırasında kullanan farklı hizmet yapılandırması için farklı depolama hesaplarında tanımlamak için kullanabilirsiniz. Ancak, Azure SDK 2.5 sonra eklenti tanılama kullanılamadığından .cscfg dosyası kendisi tarafından tanılama uzantı olarak ayarlanamıyor. Visual Studio veya PowerShell gibi araçlar kullanarak uzantı ayrı olarak ayarlamanız gerekir.
* Tanılama uzantı PowerShell kullanarak ayarlama işlemini basitleştirmek için her rol için tanılama uzantısı için XML ortak yapılandırma Visual Studio Paket çıktısını içerir. Visual Studio tanılama bağlantı dizesinde ortak yapılandırma depolama hesabı bilgilerini doldurmak için kullanır. Genel yapılandırma dosyaları Uzantıları klasöründe oluşturulur. Genel yapılandırma dosyalarına PaaSDiagnostics adlandırma modelini kullanın. &lt;rol adı\>. PubConfig.xml. Tüm PowerShell tabanlı dağıtımların bu desen, her yapılandırma bir role eşlemek için kullanabilirsiniz.
* [Azure portalında](http://go.microsoft.com/fwlink/p/?LinkID=525040) tanılama verilere erişmek için .cscfg dosyasında bağlantı dizesini kullanır. Verilerin görünen **izleme** sekmesi. Ayrıntılı izleme verileri portalda göstermek için hizmeti için bağlantı dizesi gerekir.

## <a name="migrate-projects-to-azure-sdk-26-and-later"></a>Projeleri için Azure SDK 2.6 ve geçirme
Depolama hesabı, .wadcfgx dosyasında belirtilen tanılama depolama hesabı varsa Azure SDK 2.5-Azure SDK 2.6 veya sonraki sürümleri geçiş yaptığınızda, bu dosyada kalır. Farklı depolama yapılandırmaları için farklı depolama hesaplarını kullanma esnekliğini yararlanmak için el ile bağlantı dizesi projenize ekleyin. Bir proje, bir Azure SDK 2.4 veya daha önceki Azure SDK 2.6 geçiriyorsanız, tanılama bağlantı dizelerini korunur. Ancak, önceki bölümde açıklanan Azure SDK 2.6 sürümündeki yenilik bağlantı dizeleri nasıl ele alındığı değişiklikler unutmayın.

### <a name="how-visual-studio-determines-the-diagnostics-storage-account"></a>Visual Studio tanılama depolama hesabı nasıl belirler
* .Cscfg dosyasında belirtilen tanılama bağlantı dizesini, Visual Studio, tanılama uzantı yayımlama sırasında ve genel yapılandırma XML dosyalarını paketleme sırasında oluşturduğunda ayarlamak için kullanır.
* Bir tanılama bağlantı dizesi .cscfg dosyasında belirtilmemişse, Visual Studio geri ortak yapılandırma XML'i oluşturma ve yayımlama için tanılama uzantısını ayarlamanız .wadcfgx dosyasında belirtilen depolama hesabı kullanarak döner paketleme sırasında dosyaları.
* .Cscfg dosyasını tanılama bağlantı dizesinde .wadcfgx dosyasında depolama hesabı daha önceliklidir. Bir tanılama bağlantı dizesi ise .cscfg dosyasında belirtilen Visual Studio bu bağlantı dizesini kullanır ve .wadcfgx depolama hesabında yok sayar.

### <a name="what-does-the-update-development-storage-connection-strings-check-box-do"></a>"Geliştirme depolama bağlantı dizelerini güncelleştir" onay kutusunu ne yapar?
**Güncelleştirme geliştirme depolama bağlantı dizelerini tanılama ve önbelleğe alma için Microsoft Azure depolama hesabı kimlik bilgileriyle Microsoft Azure'a yayımlarken** onay kutusunu, herhangi bir geliştirme depolama alanı güncelleştirmek için kullanışlı bir yoludur Yayımlama sırasında belirttiğiniz Azure depolama hesabı ile hesap bağlantı dizeleri.

Örneğin, bu onay kutusunu ve tanılama bağlantı dizesinde seçerseniz belirtir `UseDevelopmentStorage=true`, proje, Azure'da yayımladığınızda, Visual Studio otomatik olarak güncelleştirir tanılama bağlantı dizesinde belirtilen depolama hesabı ile Yayımlama Sihirbazı. Ancak, bu hesabın gerçek depolama hesabı tanılama bağlantı dizesi olarak belirtilmişse, bunun yerine kullanılır.

## <a name="diagnostics-functionality-differences-in-azure-sdk-24-and-earlier-vs-azure-sdk-25-and-later"></a>Azure SDK 2.4 ve önceki vs Tanılama işlevleri farklılıkları. Azure SDK 2.5 ve üzeri
Projenizi Azure SDK 2.4'den ve daha önce Azure SDK 2.5 veya sonraki bir sürüme yükseltme yapıyorsanız aşağıdaki tanılama işlev farklılıkları göz önünde bulundurun:

* **Yapılandırma API'leri kullanım dışı bırakılmıştır**. Tanılama program yapılandırması önceki ve Azure SDK 2.4 içinde kullanılabilir, ancak Azure SDK 2.5 ve daha sonra kullanım dışı bırakılmıştır. Tanılama yapılandırmanızı kodda şu anda tanımlanmış olması durumunda, tanılama için geçirilen proje sıfırdan çalışmaya devam etmek için bu ayarları yeniden yapılandırmanız gerekir. Tanılama yapılandırması için Azure SDK 2.4 diagnostics.wadcfg dosyasıdır. Tanılama yapılandırma dosyası ve sonraki sürümler için Azure SDK 2.5 diagnostics.wadcfgx ' dir.
* **Bulut hizmet uygulamaları için tanılama yalnızca rol düzeyinde yapılandırılabilir**. Azure SDK 2.5 ve daha sonra bulut hizmet uygulamaları için tanılama örnek düzeyinde ayarlayamazsınız.
* **Uygulamanızı dağıtma her seferinde, tanılama yapılandırması güncelleştirilir**. Visual Studio sunucu Gezgini'nde, Tanılama yapılandırmasını değiştirin ve ardından uygulamanızı yeniden dağıtın, bu eşlik sorunlara neden olabilir.
* **Azure SDK 2.5 ve sonraki sürümlerinde, kilitlenme bilgi dökümleri tanılama yapılandırma dosyası ve kod içinde değil yapılandırılmış**. Kilitlenme bilgi dökümleri kodda yapılandırılmış varsa, el ile yapılandırma koddan yapılandırma dosyasına aktarmanız gerekir. Kilitlenme bilgi dökümleri geçiş sırasında için Azure SDK 2.6 aktarılmaz.

## <a name="turn-on-diagnostics-in-cloud-service-projects-before-you-deploy-them"></a>Bulut hizmeti projelerini Microsoft Azure tanılama dağıtmadan önce Aç
Visual Studio öykünücüsü dağıtımdan önce hizmet çalıştırdığınızda Azure'da çalışan rolleri için Tanılama verileri toplayabilirsiniz. Visual Studio tanılama ayarlarında yapılan tüm değişiklikler diagnostics.wadcfgx yapılandırma dosyasında kaydedilir. Bu ayarlar, tanılama veri, bulut hizmetinizin dağıtırken kaydedildiği depolama hesabı belirtin.

[!INCLUDE [cloud-services-wad-warning](./includes/cloud-services-wad-warning.md)]

### <a name="to-turn-on-diagnostics-in-visual-studio-before-deployment"></a>Visual Studio'da tanılama dağıtımdan önce etkinleştirmek için

1. Rolü için kısayol menüsünden seçin **özellikleri**. Rolün içindeki **özellikleri** iletişim kutusunda **yapılandırma** sekmesi.
2. İçinde **tanılama** bölümünde, emin **tanılamayı etkinleştir** onay kutusu seçilidir.
   
    ![Tanılamayı etkinleştir seçeneğine erişme](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC796660.png)
3. Depolama hesabı için tanılama verilerini belirtmek için üç nokta (...) düğmesini seçin.
   
    ![Kullanılacak depolama hesabı belirtin](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC796661.png)
4. İçinde **depolama bağlantı dizesi oluştur** iletişim kutusunda, bir Azure aboneliği ve Azure storage öykünücüsü kullanarak bağlanmak istiyorsanız veya el ile kimlik bilgileri girilen olup olmadığını belirtin.
   
    ![Depolama hesabı iletişim kutusu](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC796662.png)
   
   * Seçerseniz **Microsoft Azure depolama öykünücüsü**, bağlantı dizesini ayarlayalım `UseDevelopmentStorage=true`.
   * Seçerseniz **aboneliğinizi**, kullanmak istediğiniz Azure aboneliğini seçin ve bir hesap adı girin. Azure aboneliklerinizi yönetmek için seçin **hesaplarını yönetme**.
   * Seçerseniz **el ile kimlik bilgileri girilen**, kullanmak istediğiniz Azure hesap anahtarı ve adını girin.
5. Görüntülenecek **tanılama Yapılandırması** iletişim kutusunda **yapılandırma**. Dışında **genel** ve **günlük dizinleri**, her sekme Toplayabileceğiniz bir tanılama veri kaynağını temsil eder. Varsayılan **genel** sekme aşağıdaki tanılama veri toplama seçeneklerini sunar: **yalnızca hataları**, **tüm bilgileri**, ve **özel planı**. Varsayılan **yalnızca hataları** seçenek, uyarı veya izleme iletileri aktarmaz çünkü depolama, en az miktarda kullanır. **Tüm bilgileri** seçeneği en bilgi aktarır, en fazla depolama kullanır ve bu nedenle, en pahalı bir seçenektir.

   > [!NOTE]
   > "MB, Disk kotası" için desteklenen minimum Boyut 4 GB'dir. Bellek dökümleri topluyorsanız, ancak bu daha yüksek bir değere gibi 10 GB artırın.
   >
  
    ![Azure tanılama ve yapılandırmasını etkinleştir](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC758144.png)
6. Bu örnekte, seçin **özel planı** seçeneği için toplanan verileri özelleştirebilirsiniz.
7. İçinde **MB Disk kotası** kutusunda tanılama verilerini depolama hesabınızda ayırmak üzere ne kadar alan ayarlayabilirsiniz. Değiştirin veya varsayılan değeri kabul edin.
8. Her toplamak istediğiniz tanılama veri sekmesinde seçin **etkinleştirme Aktarım, \<günlük türü\>**  onay kutusu. Örneğin, üzerinde uygulama günlüklerini toplamak istiyorsanız **uygulama günlükleri** sekmesinde **etkinleştirme uygulama günlükleri aktarımını** onay kutusu. Ayrıca, her tanılama veri türüne göre gerekli herhangi bir bilgi belirtin. Her sekme için yapılandırma bilgileri için bkz **tanılama veri kaynaklarını'kurmak** bu makalenin ilerleyen bölümlerinde. 
9. İstediğiniz tüm tanılama veri koleksiyonu etkinleştirdikten sonra seçin **Tamam**.
10. Azure bulut hizmeti projenizi Visual Studio'da her zaman olduğu gibi çalıştırın. Uygulamanızı kullandıkça, etkinleştirdiğiniz günlüğü bilgilerini, belirttiğiniz Azure depolama hesabına kaydedilir.

## <a name="turn-on-diagnostics-on-azure-virtual-machines"></a>Azure sanal makineler'de tanılamayı Aç
Visual Studio'da Azure sanal makineleri için Tanılama verileri toplayabilirsiniz.

### <a name="to-turn-on-diagnostics-on-azure-virtual-machines"></a>Azure sanal makineler'de tanılamayı etkinleştirmek için

1. Sunucu Gezgini'nde Azure düğümü seçin ve henüz bağlı değilseniz, ardından Azure aboneliğinize bağlanın.
2. Genişletin **sanal makineler** düğümü. Yeni bir sanal makine oluşturun veya var olan bir düğüm seçin.
3. Seçmek istediğiniz sanal makinenin kısayol menüsünde **yapılandırma**. Sanal makine yapılandırma iletişim kutusu görüntülenir.
   
    ![Bir Azure sanal makine yapılandırma](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC796663.png)
4. Henüz yüklü değilse, Microsoft İzleme Aracısı tanılama uzantısını ekleyin. Bu uzantıya sahip Azure sanal makine için Tanılama verileri toplayabilirsiniz. Altında **yüklü uzantıları**, **kullanılabilir bir uzantı seçin** aşağı açılan liste kutusunda seçin **Microsoft İzleme Aracısı tanılamaları**.
   
    ![Bir Azure sanal makine uzantısı yükleme](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC766024.png)
   
    > [!NOTE]
   > Diğer bir tanılama uzantısı, sanal makineleriniz için kullanılabilir. Daha fazla bilgi için [sanal makine uzantıları ve özellikleri Windows için](https://docs.microsoft.com/azure/virtual-machines/windows/extensions-features).
   > 
   > 
5. Uzantı ve görünüm eklemek için kendi **tanılama Yapılandırması** iletişim kutusunda **Ekle**.
6. Bir depolama hesabı belirtmek için seçin **yapılandırma**ve ardından **Tamam**.
   
    Her sekme (dışında **genel** ve **günlük dizinleri**) toplamak bir tanılama veri kaynağını temsil eder.
   
    ![Azure tanılama ve yapılandırmasını etkinleştir](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC758144.png)
   
    Varsayılan sekmeyi **genel**, aşağıdaki tanılama veri toplama seçeneklerini sunar: **yalnızca hataları**, **tüm bilgileri**, ve **Özelplanı**. Varsayılan seçenek **yalnızca hataları**, uyarı veya izleme iletileri aktarmaz çünkü en az miktarda depolama alır. **Tüm bilgileri** seçenek en çok bilgi aktarır ve, bu nedenle, en pahalı depolama açısından bir seçenektir.
7. Bu örnekte, seçin **özel planı** toplanan verileri özelleştirme olanağı seçeneği.
8. **MB Disk kotası** ayırmak istediğiniz depolama hesabınız için Tanılama verileri ne kadar alan kutusunu belirtir. Varsayılan değer, isterseniz değiştirebilirsiniz.
9. Her toplamak istediğiniz tanılama veri sekmesinde seçin, **etkinleştirme Aktarım, \<günlük türü\>**  onay kutusu.
   
    Örneğin, uygulama günlüklerini toplamak istiyorsanız, seçin **aktarımını uygulama günlüklerini etkinleştirin** onay kutusunu **uygulama günlükleri** sekmesi. Ayrıca, her tanılama veri türü için gerekli herhangi bir bilgi belirtin. Her sekme için yapılandırma bilgileri için bkz **tanılama veri kaynaklarını'kurmak** bu makalenin ilerleyen bölümlerinde.
10. İstediğiniz tüm tanılama veri koleksiyonu etkinleştirdikten sonra seçin **Tamam**.
11. Güncelleştirilmiş Projeyi kaydedin.
    
    Bir ileti **Microsoft Azure etkinlik günlüğü** penceresi belirten sanal makine güncelleştirildi.

## <a name="set-up-diagnostics-data-sources"></a>Tanılama veri kaynakları ayarlayın
Tanılama veri toplama etkinleştirildikten sonra tam olarak hangi veri kaynaklarını toplamak istediğinize ve hangi bilgilerin toplandığı seçebilirsiniz. Sonraki bölümlerde sekmeleri **tanılama Yapılandırması** iletişim kutusu ve her hangi bir yapılandırma seçeneği anlamına gelir.

### <a name="application-logs"></a>Uygulama günlükleri
Uygulama günlükleri, web uygulaması tarafından üretilen tanılama bilgilerine sahip. Uygulama günlükleri tutmak isteyip istemediğinizi seçin **etkinleştirme uygulama günlükleri aktarımını** onay kutusu. Artırmak ya da uygulama günlükleri aktarımını depolama hesabınıza arasındaki süreyi azaltmak için değiştirme **aktarım süresi (dak)** değeri. Ayrıca oturum açma ayarı yakalanan bilgilerin miktarını değiştirebilirsiniz **günlük düzeyi** değeri. Örneğin, **ayrıntılı** daha fazla bilgi edinin veya **kritik** yalnızca kritik hataları yakalamak için. Uygulama günlükleri yayan bir belirli tanılama sağlayıcısı varsa, sağlayıcıya ait GUID ekleyerek günlükleri yakalayabilirsiniz **sağlayıcısı GUID** kutusu.

  ![Uygulama günlükleri](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC758145.png)

Uygulama günlükleri hakkında daha fazla bilgi için bkz. [Azure App Service'te Web uygulamaları için tanılama günlüğünü etkinleştirme](/azure/app-service/web-sites-enable-diagnostic-log).

### <a name="windows-event-logs"></a>Windows olay günlükleri
Windows olay günlükleri tutmak için seçin **aktarımı, Windows olay günlüklerini etkinleştirme** onay kutusu. Artırmak ya da olay günlüklerini aktarımını depolama hesabınıza arasındaki süreyi azaltmak için değiştirme **aktarım süresi (dak)** değeri. İzlemek istediğiniz olay türleri için onay kutularını seçin.

![Olay günlükleri](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC796664.png)

Azure SDK 2.6 veya sonraki sürümleri kullanıyorsanız ve özel bir veri kaynağı belirtmek istiyorsanız bu alana giriş **\<veri kaynağı adı\>** metin kutusuna tıklayın ve ardından **Ekle**. Veri kaynağı diagnostics.cfcfg dosyasına eklenir.

Azure SDK 2.5 kullanıyorsanız ve özel bir veri kaynağı belirtmek istiyorsanız, bunu ekleyebilirsiniz `WindowsEventLog` diagnostics.wadcfgx bölümünü dosyası gibi aşağıdaki örnekte:

```
<WindowsEventLog scheduledTransferPeriod="PT1M">
   <DataSource name="Application!*" />
   <DataSource name="CustomDataSource!*" />
</WindowsEventLog>
```
### <a name="performance-counters"></a>Performans sayaçları
Performans sayacı bilgileri, performans sorunlarını bulun, sistem ve uygulama performansını ayarlamanıza yardımcı olabilir. Daha fazla bilgi için [bir Azure uygulamasında performans sayaçları oluşturma ve kullanma](https://msdn.microsoft.com/library/azure/hh411542.aspx). Performans sayaçları yakalamak için seçin **etkinleştirme performans sayaçları aktarımını** onay kutusu. Artırmak ya da olay günlüklerini aktarımını depolama hesabınıza arasındaki süreyi azaltmak için değiştirme **aktarım süresi (dak)** değeri. İzlemek istediğiniz performans sayaçları için onay kutularını seçin.

![Performans sayaçları](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC758147.png)

Listede bir performans sayacı izlemek için önerilen söz dizimini kullanarak performans sayacı'nı girin. ve ardından **Ekle**. Sanal makinedeki işletim sistemi, izleyebilirsiniz hangi performans sayaçlarını belirler. Sözdizimi hakkında daha fazla bilgi için bkz. [sayaç yolunu belirtin](https://msdn.microsoft.com/library/windows/desktop/aa373193.aspx).

### <a name="infrastructure-logs"></a>Protokoly infrastruktury
Azure tanılama altyapısı, modül RemoteAccess ve RemoteForwarder modülü hakkında bilgi altyapı günlükleri vardır. Protokoly infrastruktury hakkında bilgi toplamak için seçin **etkinleştirme protokoly İnfrastruktury aktarımını** onay kutusu. Artırmak ya da altyapı günlükleri aktarımını depolama hesabınıza arasındaki süreyi azaltmak için değiştirme **aktarım süresi (dak)** değeri.

![Tanılama Altyapısı günlükleri](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC758148.png)

Daha fazla bilgi için [Azure Tanılama'yı kullanarak günlük verilerini toplama](https://msdn.microsoft.com/library/azure/gg433048.aspx).

### <a name="log-directories"></a>Günlük dizinleri
Günlük dizinleri günlük dizinleri Internet Information Services (IIS) istek, başarısız isteklerin veya seçtiğiniz klasör için toplanan verileri var. Günlük dizinleri yakalamak için seçin **etkinleştirme günlük dizinlerini aktarımını** onay kutusu. Artırmak ya da günlükleri aktarımını depolama hesabınıza arasındaki süreyi azaltmak için değiştirme **aktarım süresi (dak)** değeri.

Gibi toplamak istediğiniz günlüklerinin onay kutularını işaretleyin **IIS günlükler** ve **başarısız istek** günlükleri. Varsayılan depolama kapsayıcısı adları sağlanır, ancak adlarını değiştirebilirsiniz.

Herhangi bir klasörden günlükleri yakalayabilirsiniz. Yoldaki **mutlak dizin günlüğünden** bölümüne ve ardından **Dizin Ekle**. Günlükler, belirtilen kapsayıcı içinde yakalanır.

![Günlük dizinleri](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC796665.png)

### <a name="etw-logs"></a>ETW günlükleri
Kullanırsanız [olay izleme için Windows](https://msdn.microsoft.com/library/windows/desktop/bb968803\(v=vs.85\).aspx) (ETW) ve ETW günlükleri tutmak istiyorsanız seçin **etkinleştirme ETW günlükleri aktarımını** onay kutusu. Artırmak ya da günlükleri aktarımını depolama hesabınıza arasındaki süreyi azaltmak için değiştirme **aktarım süresi (dak)** değeri.

Olaylar, olay kaynakları ve belirttiğiniz olay bildirimleri yakalanır. Bir olay kaynağı belirtmek için **olay kaynakları** bölümünde bir ad girin ve ardından **olay kaynağı ekleme**. Benzer şekilde, bir olay bildiriminde belirtebilirsiniz **olay bildirimlerini** bölümüne ve ardından **ekleme olay bildirim**.

![ETW günlükleri](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC766025.png)

ETW framework ASP.NET'te sınıflarda aracılığıyla desteklenen [System.Diagnostics.aspx](https://msdn.microsoft.com/library/system.diagnostics(v=vs.110)) ad alanı. Devralır ve standart genişletir Microsoft.WindowsAzure.Diagnostics ad alanını [System.Diagnostics.aspx](https://msdn.microsoft.com/library/system.diagnostics(v=vs.110)) sınıfları, kullanımını etkinleştirir [System.Diagnostics.aspx](https://msdn.microsoft.com/library/system.diagnostics(v=vs.110)) bir günlük olarak Azure ortamında çerçevesi. Daha fazla bilgi için [Microsoft Azure'da günlüğe kaydetme ve izleme denetimini ele](https://msdn.microsoft.com/magazine/ff714589.aspx) ve [Azure bulut Hizmetleri ve sanal makineler'de tanılamayı etkinleştirme](/azure/cloud-services/cloud-services-dotnet-diagnostics).

### <a name="crash-dumps"></a>Kilitlenme bilgi dökümleri
Ne zaman bir rol örneği kilitleniyor hakkında bilgileri toplamak için seçin **etkinleştirme kilitlenme dökümleri aktarımını** onay kutusu. (ASP.NET çoğu özel durumları işler çünkü yalnızca çalışan rolleri için genellikle kullanışlıdır.) Artırmak ya da depolama alanı için kilitlenme bilgi dökümleri şekillendiriyorsa yüzdesini azaltmak için değiştirme **dizin kota (%)** değeri. Burada kilitlenme bilgi dökümleri depolanır ve yakalama isteyip istemediğinizi seçin depolama kapsayıcısını değiştirebileceğiniz bir **tam** veya **Mini** dökümü.

Şu anda izlenen işlemler sonraki ekran görüntüsünde listelenir. Yakalamak istediğiniz işlemler için onay kutularını seçin. Başka bir işlem listeye eklemek için işlem adı girin ve ardından **ekleme işlemi**.

![Kilitlenme bilgi dökümleri](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC766026.png)

Daha fazla bilgi için [Microsoft Azure'da günlüğe kaydetme ve izleme denetimini ele](https://msdn.microsoft.com/magazine/ff714589.aspx) ve [Microsoft Azure tanılama bölüm 4: özel günlük bileşenleri ve Azure tanılama 1.3 değişiklikleri](http://justazure.com/microsoft-azure-diagnostics-part-4-custom-logging-components-azure-diagnostics-1-3-changes/).

## <a name="view-the-diagnostics-data"></a>Tanılama verileri görüntüleyin
Bulut hizmeti veya sanal makine için Tanılama verileri derledik sonra görüntüleyebilirsiniz.

### <a name="to-view-cloud-service-diagnostics-data"></a>Bulut hizmeti tanılama verilerini görüntülemek için
1. Bulut hizmetinizi normal olarak dağıtın ve çalıştırın.
2. Visual Studio'nun ürettiği bir raporda veya tablolarda tanılama verilerini depolama hesabınızda görüntüleyebilirsiniz. Cloud Explorer veya Sunucu Gezgini, açık bir raporda veri açın ve ardından rolü için düğümün kısayol menüsünü görüntülemek **görünüm tanılama verilerini**.
   
    ![Tanılama verilerini görüntüle](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC748912.png)
   
    Kullanılabilir verileri gösteren bir rapor görüntülenir.
   
    ![Visual Studio'da Microsoft Azure tanılama raporu](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC796666.png)
   
    En son veriler gösterilmiyor aktarım süresi geçmesini beklemeniz gerekebilir.
   
    Verileri hemen güncelleştirmek için seçin **Yenile** bağlantı. Otomatik olarak güncelleştirilen veri sağlamak için bir zaman aralığı seçin **otomatik yenileme** aşağı açılan liste kutusu. Hata verileri dışarı aktarmak için seçin **CSV'ye aktar** bir Excel çalışma sayfasında açabileceğiniz bir virgülle ayrılmış değer dosyası oluşturmak için düğme.
   
    Cloud Explorer veya sunucu Gezgini'nde, dağıtımla ilişkili depolama hesabını açın.
3. Tanılama tabloları Tablo Görüntüleyicisi'nde açın ve sonra toplanan verileri gözden geçirin. IIS günlükleri ve özel günlükler için bir blob kapsayıcısı açabilirsiniz. Aşağıdaki tabloda, farklı günlük dosyaları için verileri içeren blob kapsayıcıları ve tabloları listeler. Bu günlük dosyası için veri ek olarak tablo girişleri **EventTickCount**, **Deploymentıd**, **rol**, ve **Roleınstance** , hangi sanal makine ve rol verileri oluşturulan tanımlamanıza yardımcı olması için ne zaman. 
   
   | Tanılama verileri | Açıklama | Konum |
   | --- | --- | --- |
   | Uygulama günlükleri |Kodunuzu yöntemleri çağırarak oluşturduğu günlükleri **System.Diagnostics.Trace** sınıfı. |WADLogsTable |
   | Olay günlükleri |Windows olay günlüklerini sanal makinelerde verileri. Windows, bu günlüklerde bilgileri depolar, ancak uygulamalar ve hizmetler ayrıca rapor hataları için günlükleri kullanın veya bilgileri günlüğe kaydetmek. |WADWindowsEventLogsTable |
   | Performans sayaçları |Sanal makinede kullanılabilir olan herhangi bir performans sayacı hakkında veri toplayabilirsiniz. İşletim sistemi, bellek kullanımı ve işlemci zamanı gibi birçok istatistikleri içeren performans sayaçları sağlar. |WADPerformanceCountersTable |
   | Protokoly infrastruktury |Tanılama altyapı kendisi tarafından oluşturulan günlükleri. |WADDiagnosticInfrastructureLogsTable |
   | IIS günlükleri |Web istekleri kayıt günlükleri. Bulut hizmetinizi önemli miktarda trafiği alır, bu günlükleri uzun olabilir. Toplamak ve yalnızca ihtiyacınız olduğunda bu verileri depolamak için iyi bir fikirdir. |İstek başarısız oldu blob kapsayıcısı altında wad-IIS-failedreqlogs, bu dağıtım, rol ve örnek için bir yol altındaki günlüklerinin bulabilirsiniz. Günlüklerin tamamını wad IIS logfiles altında bulabilirsiniz. Her dosya için girişler WADDirectories tabloda oluşturulur. |
   | Kilitlenme bilgi dökümleri |Bulut hizmetinizin işlemin (genellikle bir çalışan rolü) ikili görüntüleri sağlar. |wad crush dökümleri blob kapsayıcısı |
   | Özel günlük dosyaları |Günlükleri, önceden tanımlanmış veri. |Kodda, depolama hesabınızdaki özel günlük dosyalarının konumunu belirtebilirsiniz. Örneğin, bir özel blob kapsayıcısı belirtebilirsiniz. |
4. Herhangi bir türde veriler kesildi durumunda bu veriler için arabellek miktara artırmayı deneyebilirsiniz türü veya veri depolama hesabınıza aktarımları sanal makineden aralığını kısaltmayı.
5. (İsteğe bağlı) Bazen genel depolama maliyetlerini azaltmak için depolama hesabından veri temizleme.
6. Tam bir dağıtım yaptığınızda, diagnostics.cscfg dosyası (.wadcfgx için Azure SDK 2.5) Azure'da güncelleştirilir ve bulut hizmetinizi tanılama yapılandırma değişiklikleri alır. .Cscfg dosyasını, bunun yerine mevcut bir dağıtımı güncelleştiriyorsanız, Azure'da güncelleştirilmez. Tanılama ayarları, sonraki bölümde yer alan adımları izleyerek, ancak yine de değiştirebilirsiniz. Tam dağıtımını gerçekleştirme ve mevcut bir dağıtımı güncelleştirme hakkında daha fazla bilgi için bkz. [Azure uygulaması Yayımlama Sihirbazı](vs-azure-tools-publish-azure-application-wizard.md).

### <a name="to-view-virtual-machine-diagnostics-data"></a>Sanal makine tanılama verilerini görüntülemek için
1. Sanal makine için kısayol menüsünden seçin **tanılama verilerini görüntüle**.
   
    ![Bir Azure sanal makinesinde tanılama verilerini görüntüle](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC766027.png)
   
    **Souhrn Diagnostiky** iletişim kutusu görüntülenir.
   
    ![Azure sanal makinesi tanılama özeti](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC796667.png)  
   
    En son veriler gösterilmiyor aktarım süresi geçmesini beklemeniz gerekebilir.
   
    Verileri hemen güncelleştirmek için seçin **Yenile** bağlantı. Otomatik olarak güncelleştirilen veri sağlamak için bir zaman aralığı seçin **otomatik yenileme** aşağı açılan liste kutusu. Hata verileri dışarı aktarmak için seçin **CSV'ye aktar** bir Excel çalışma sayfasında açabileceğiniz bir virgülle ayrılmış değer dosyası oluşturmak için düğme.

## <a name="set-up-cloud-service-diagnostics-after-deployment"></a>Dağıtımdan sonra bulut hizmeti tanılama ayarlama ayarlayın
Zaten çalışan bir bulut hizmeti ile ilgili bir sorun araştırdığınızı, belirtmediğiniz veri toplamak isteyebilirsiniz rol ilk olarak dağıtılan önce. Bu durumda, Sunucu Gezgini ayarlarını değiştirerek bu veri toplamaya başlayabilirsiniz. Tek bir örnek için veya açık olup olmadığına bağlı olarak bir roldeki tüm örnekleri için tanılama ayarlayabilirsiniz **tanılama Yapılandırması** kısayol menüsünden veya rol örneği için iletişim kutusu. Rol düğüm yapılandırırsanız, yaptığınız tüm değişiklikler tüm örneklerine uygulanır. Örneği düğümünün yapılandırırsanız, yaptığınız tüm değişiklikler yalnızca bu örneği için geçerlidir.

### <a name="to-set-up-diagnostics-for-a-running-cloud-service"></a>Çalışan bir bulut hizmeti için tanılama ayarlamak için
1. Sunucu Gezgini'nde **Cloud Services** düğümünü ve ardından rolü veya örneği (veya her ikisi de) bulmak için düğümleri listesini genişletin araştırmak istediğiniz.
   
    ![Tanılama Yapılandır](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC748913.png)
2. Bir örnek düğümü veya bir rolü düğümü için kısayol menüsünden seçin **güncelleştirme tanılama ayarları**ve ardından toplamak istediğiniz tanılama ayarlarını seçin.
   
    Yapılandırma ayarları hakkında daha fazla bilgi için bkz **tanılama veri kaynaklarını'kurmak** bu makaledeki. Tanılama verilerini görüntüleme hakkında daha fazla bilgi için bkz **tanılama verilerini görüntüleme** bu makaledeki.
   
    Sunucu Gezgini içinde veri toplama değiştirirseniz, değişiklikler bulut hizmetinizin tam olarak yeniden kadar yürürlükte kalır. Varsayılan kullanırsanız yayımlama ayarları, değişikliklerin üzerine yazılmaz. Varsayılan ayar yayımlama mevcut dağıtımı güncelleştirmek için yerine tam bir yeniden dağıtım yapmak için olan. Ayarlar'ın dağıtım sırasında Temizle emin olmak için Git **Gelişmiş ayarlar** Yayımla Sihirbazı'nda sekmesine ve ardından temizleyin **dağıtım güncelleştirme** onay kutusu. Bu onay kutusu işaretli yeniden dağıtırken, ayarları bulunanlar .wadcfgx (veya .wadcfg) dosyası olarak kümesi üzerinden geri **özellikleri** rolü için düzenleyici. Azure, dağıtımınızı güncelleştirmek, önceki ayarları tutar.

## <a name="troubleshoot-azure-cloud-service-issues"></a>Azure bulut hizmeti sorunları giderme
Gibi bir "meşgul" durumunda takılı bir rolün sürekli geri dönüştürülmesi veya bir iç sunucu hatası oluşturur, bulut hizmeti projeleri sorunlar yaşıyorsanız, araçları ve tanılama ve sorun gidermek için kullanabileceğiniz teknikleri vardır. Yaygın sorunlar ve çözümleri belirli örnekler ve kavramlar ve bu hataları düzeltin ve tanılamak için kullanabileceğiniz araçları genel bir bakış için bkz. [Azure PaaS işlem Tanılama verileri](http://blogs.msdn.com/b/kwill/archive/2013/08/09/windows-azure-paas-compute-diagnostics-data.aspx).

## <a name="q--a"></a>Soru - Yanıt
**Arabellek boyutu nedir ve ne kadar büyük olmalıdır?**

Her sanal makine örneğinde yerel dosya sisteminde tanılama veri miktarını depolanabilir kotalar sınırlayın. Ayrıca, her kullanılabilir tanılama veri türü için bir arabellek boyutu belirtin. Bu arabellek boyutu, veri türü için ayrı bir kota gibi davranır. Genel kotasını ve kalan bellek miktarını belirlemek için tanılama veri türü için iletişim kutusunun altına bakın. Daha büyük arabellekler ya da daha fazla veri türleri belirtirseniz, genel kotasını yaklaşımını. Genel kotasını diagnostics.wadcfg veya .wadcfgx yapılandırma dosyasını değiştirerek değiştirebilirsiniz. Tanılama verilerini aynı dosya sistemi, uygulamanızın veri olarak depolanır. Uygulamanız çok miktarda disk alanı kullanıyorsa, genel tanılama kotasından artırın olmamalıdır.

**Aktarım süresi nedir ve ne kadar olmalıdır?**

Aktarım süresi geçtiğinde verileri arasında yakalar zaman miktarıdır. Her aktarım süresi verileri yerel dosya sisteminden bir sanal makinede, depolama hesabındaki tablolar taşınır. Toplanan veri miktarı aktarım süresi bitmeden önce kotasını aşarsa, eski veriler atılır. Verilerinizi arabellek boyutu veya genel kotasını aştığı için veri kaybı, aktarım süresi azaltmak isteyebilirsiniz.

**Ne zaman dilimi içinde zaman damgaları misiniz?**

Bulut hizmetinizi barındıran veri merkezinde yerel saat diliminizde zaman damgaları var. Günlük tablolarda aşağıdaki üç zaman damgası sütunu kullanılır:

* **PreciseTimeStamp**: ETW olayın zaman damgası. Diğer bir deyişle, saat istemciden olay günlüğe kaydedilir.
* **Zaman damgası**: değeri **PreciseTimeStamp** yuvarlatılmış karşıya yükleme frekansı sınır gösteriyor. Örneğin, karşıya yükleme frekansı saat 00:17:12 5 dakika ile olay ise, zaman damgası 00:15:00 ' dir.
* **Zaman damgası**: hangi varlık Azure tablosunda oluşturulduğu zaman damgası.

**Maliyetleri nasıl tanılama bilgileri toplanırken yönetebilirsiniz?**

Varsayılan ayarlar (**günlük düzeyi** kümesine **hata**, ve **aktarım süresi** kümesine **1 dakika**) maliyetlerini en aza indirmek için tasarlanmıştır. Daha fazla tanılama verisi toplama veya aktarım süresi azaltırsanız, işlem maliyetleri artırır. Gereksinim ve artık ihtiyacınız olmadığında veri toplamayı devre dışı unutmayın daha fazla veri toplama. Her zaman yeniden bile çalışma zamanında, bu makalenin önceki bölümlerinde açıklandığı şekilde etkinleştirebilirsiniz.

**IIS nasıl başarısız istek günlükleri topluyor?**

Varsayılan olarak, IIS başarısız istek günlükleri toplamaz. IIS web rolünüz için web.config dosyasını düzenleyerek başarısız istek günlükleri toplamak için ayarlayabilirsiniz.

**İzleme bilgileri RoleEntryPoint yöntemlerinden OnStart gibi almıyorum. Ne oldu?**

Yöntemlerinin **RoleEntryPoint** IIS içinde değil, WAIISHost.exe bağlamında olarak adlandırılır. Yapılandırma bilgilerini Web.Config'de normalde izleme etkinleştirir geçerli değildir. Bu sorunu çözmek için web rolü projeniz .config dosyasına ekleyin ve içeren çıktı derlemesine eşleştirilecek dosya adı **RoleEntryPoint** kod. Varsayılan web rolü projesinde WAIISHost.exe.config .config dosyası adı olmalıdır. Bu dosyaya aşağıdaki satırları ekleyin:

```
<system.diagnostics>
  <trace>
      <listeners>
          <add name “AzureDiagnostics” type=”Microsoft.WindowsAzure.Diagnostics.DiagnosticMonitorTraceListener”>
              <filter type=”” />
          </add>
      </listeners>
  </trace>
</system.diagnostics>
```

İçinde **özellikleri** penceresinde **çıkış dizinine Kopyala** özelliğini **her zaman Kopyala**.

## <a name="next-steps"></a>Sonraki adımlar
Azure'da günlüğe kaydetme Tanılama hakkında daha fazla bilgi için bkz: [Azure bulut Hizmetleri ve sanal makineler'de tanılamayı etkinleştirme](/azure/cloud-services/cloud-services-dotnet-diagnostics) ve [Azure App Service'te Web uygulamaları için tanılama günlüğünü etkinleştirme](/azure/app-service/web-sites-enable-diagnostic-log).

