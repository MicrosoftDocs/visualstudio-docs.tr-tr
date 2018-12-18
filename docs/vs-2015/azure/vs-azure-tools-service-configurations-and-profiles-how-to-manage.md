---
title: Hizmet yapılandırması ve profillerini yönetme | Microsoft Docs
description: Hizmet yapılandırmalarını ve profilleri yapılandırma dosyaları ile çalışma hakkında bilgi edinin | hangi dağıtım ortamlarının ayarlarını depolamak ve bulut Hizmetleri için ayarları yayımlama.
author: ghogen
manager: douge
assetId: 7da8c551-fb06-4057-b5c7-c77f4b39d803
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 8/11/2017
ms.author: ghogen
ms.openlocfilehash: 3f7c7341b115f0899ac4c90d574a65dfdb4087bc
ms.sourcegitcommit: e481d0055c0724d20003509000fd5f72fe9d1340
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/05/2018
ms.locfileid: "51003699"
---
# <a name="how-to-manage-service-configurations-and-profiles"></a>Hizmet yapılandırmalarını ve profillerini yönetme
## <a name="overview"></a>Genel Bakış
Visual Studio bir bulut hizmetinde yayımladığınızda, yapılandırma dosyalarını iki tür yapılandırma bilgileri depolar: hizmet yapılandırmaları ve Profiller. Hizmet yapılandırma (.cscfg dosyaları), Azure bulut hizmeti için dağıtım ortamlarının ayarlarını saklar. Azure, bulut hizmetlerinizi yönetirken bu yapılandırma dosyalarını kullanır. Öte yandan, profilleri (.azurePubxml dosyaları) depolama, bulut Hizmetleri için ayarları yayımlayın. Bu ayarlar, Yayımla Sihirbazı'nı kullanın ve yerel olarak Visual Studio tarafından kullanılır, seçtiğiniz kaydını yöneliktir. Bu konuda, her iki tür yapılandırma dosyaları ile çalışma konusunda açıklanmaktadır.

## <a name="service-configurations"></a>Hizmet yapılandırması
Her dağıtım ortamlarınızda kullanmak için birden çok hizmet yapılandırması oluşturabilirsiniz. Örneğin, bir hizmet yapılandırması ve Azure uygulaması ve başka bir hizmet yapılandırması, üretim ortamınız için test çalıştırmak için kullandığınız yerel ortam için oluşturabilirsiniz.

Ekleme, silme, yeniden adlandırmak ve gereksinimlerinize göre bu hizmet yapılandırması değiştirme. Aşağıdaki çizimde gösterildiği gibi bu hizmet yapılandırması Visual Studio'dan yönetebilirsiniz.

![Hizmet yapılandırmalarını Yönet](./media/vs-azure-tools-service-configurations-and-profiles-how-to-manage/manage-service-config.png)

Ayrıca açabilirsiniz **yapılandırmaları yönetme** rolün özellik sayfaları iletişim kutusu. Azure, projenizde bir rol için Özellikleri'ni açmak için o rol için kısayol menüsünü açın ve ardından **özellikleri**. Üzerinde **ayarları** sekmesinde, genişletme **hizmet yapılandırması** listeleyin ve ardından **Yönet** açmak için **yapılandırmaları yönetme** iletişim kutusu.

### <a name="to-add-a-service-configuration"></a>Bir hizmet yapılandırması eklemek için
1. Çözüm Gezgini'nde bir Azure projesi için kısayol menüsünü açın ve ardından **yapılandırmaları yönetme**.
   
    **Hizmet yapılandırmalarını Yönet** iletişim kutusu görüntülenir.
2. Bir hizmet yapılandırması eklemek için mevcut bir yapılandırmayı bir kopyasını oluşturmanız gerekir. Bunu yapmak için adı listeden kopyalayın ve ardından istediğiniz yapılandırmayı seçin **kopya oluştur**.
3. (İsteğe bağlı) Hizmet yapılandırması farklı bir ad vermek için yeni hizmet yapılandırması adı listeden seçin ve ardından **Yeniden Adlandır**. İçinde **adı** metin kutusuna, bu hizmet yapılandırması'nı kullanın ve ardından istediğiniz adı yazın **Tamam**.
   
    ServiceConfiguration adlı bir yeni hizmet yapılandırma dosyası. [Yeni adı] .cscfg, Çözüm Gezgini'nde bir Azure projesi eklenir.

### <a name="to-delete-a-service-configuration"></a>Bir hizmet yapılandırması silinemedi
1. Çözüm Gezgini'nde bir Azure projesi için kısayol menüsünü açın ve ardından **yapılandırmaları yönetme**.
   
    **Hizmet yapılandırmalarını Yönet** iletişim kutusu görüntülenir.
2. Hizmet yapılandırmasını silmek için silmek için istediğiniz yapılandırmayı seçin **adı** listeleyin ve ardından **Kaldır**. Bu yapılandırmayı silmek istediğinizi doğrulamak için bir iletişim kutusu görüntülenir.
3. Seçin **Sil**.
   
     Hizmet yapılandırma dosyası, Çözüm Gezgini'nde bir Azure projesi kaldırılır.

### <a name="to-rename-a-service-configuration"></a>Bir hizmet yapılandırması yeniden adlandırmak için
1. Çözüm Gezgini'nde, bir Azure projesi için kısayol menüsünü açın ve ardından **yapılandırmaları yönetme**.
   
    **Hizmet yapılandırmalarını Yönet** iletişim kutusu görüntülenir.
2. Yeni hizmet yapılandırmasından bir hizmet yapılandırması yeniden adlandırmak için seçin **adı** listeleyin ve ardından **Yeniden Adlandır**. İçinde **adı** metin kutusuna, bu hizmet yapılandırması'nı kullanın ve ardından istediğiniz adı yazın **Tamam**.
   
    Hizmet yapılandırma dosyasının adını, Çözüm Gezgini'nde Azure projedeki değiştirilir.

### <a name="to-change-a-service-configuration"></a>Hizmet yapılandırmasını değiştirmek için
* Hizmet yapılandırmasını değiştirmek istiyorsanız, Azure projede değiştirin ve ardından istediğiniz belirli bir rol için kısayol menüsünü açın **özellikleri**. Bkz: [nasıl yapılır: Visual Studio ile Azure bulut hizmeti için rolleri yapılandırmak](vs-azure-tools-configure-roles-for-cloud-service.md) daha fazla bilgi için.

## <a name="make-different-setting-combinations-by-using-profiles"></a>Profilleri kullanılarak farklı ayar bileşimleri olun
Bir profil kullanarak otomatik olarak doldurabilirsiniz **Yayımlama Sihirbazı** farklı amaçlar için ayarları farklı birleşimlerini ile. Örneğin, hata ayıklama için bir profil olabilir ve başka bir yayın oluşturur. Bu durumda, **hata ayıklama** profili haritamın **IntelliTrace** etkin ve **hata ayıklama** seçiliyken, yapılandırma ve **yayın** profili haritamın **IntelliTrace** devre dışı ve **yayın** seçili yapılandırma. Farklı bir depolama hesabı kullanarak bir hizmet dağıtmak için farklı profiller de kullanabilirsiniz.

Sihirbazı ilk kez çalıştırdığınızda, bir varsayılan profili oluşturulur. Visual Studio profili altında Azure projenize eklenir ve .azurePubXml uzantısı, bir dosyada depolar **profilleri** klasör. Daha sonra sihirbazı çalıştırdığınızda farklı seçenekleri el ile belirtin, dosyayı otomatik olarak güncelleştirir. Aşağıdaki yordamı çalıştırmadan önce önceden bulut hizmetinizi en az bir kez yayımladığınız.

### <a name="to-add-a-profile"></a>Bir profili eklemek için
1. Azure, projeniz için kısayol menüsünü açın ve ardından **Yayımla**.
2. Yanındaki **hedef profil** listesinden **profili Kaydet** düğmesi, aşağıdaki çizimde gösterildiği gibi. Bu profil sizin için oluşturur.
   
    ![Yeni bir profil oluşturun](./media/vs-azure-tools-service-configurations-and-profiles-how-to-manage/create-new-profile.png)
3. Profil oluşturulduktan sonra seçip **< Yönet... >** içinde **hedef profil** listesi.
   
    **Spravovat Profily** iletişim kutusu görüntülenirse, aşağıdaki çizimde gösterildiği gibi.
   
    ![Profilleri Yönet iletişim kutusu](./media/vs-azure-tools-service-configurations-and-profiles-how-to-manage/manage-profiles.png)
4. İçinde **adı** listesinde, bir profil seçin ve ardından **kopya oluştur**.
5. Seçin **Kapat** düğmesi.
   
    Yeni profili hedef profil listesinde görüntülenir.
6. İçinde **hedef profil** listesinde, az önce oluşturduğunuz profili seçin. Yayımlama Sihirbazı ayarları, Seçenekler, seçtiğiniz profilden doldurulur.
7. Seçin **önceki** ve **sonraki** düğmeler Yayımla Sihirbazı'nın her sayfasında görüntüleyin ve ardından bu profili için ayarları özelleştirebilirsiniz. Bkz: [Azure uygulaması Yayımlama Sihirbazı](http://go.microsoft.com/fwlink/p/?LinkID=623085) bilgi.
8. Ayarları özelleştirme tamamladıktan sonra seçin **sonraki** ayarlar sayfasına geri gidin. Bu ayarları kullanarak hizmet yayımladığınızda veya seçerseniz profil kaydedildi **Kaydet** profil listesinin yanındaki.

### <a name="to-rename-or-delete-a-profile"></a>Profili sildiğinizde veya yeniden adlandırmak için
1. Azure, projeniz için kısayol menüsünü açın ve ardından **Yayımla**.
2. İçinde **hedef profil** listesinden **Yönet**.
3. İçinde **Spravovat Profily** iletişim kutusunda, silmek istediğiniz profili seçin ve ardından **Kaldır**.
4. Görünen onay iletişim kutusunda seçin **Tamam**.
5. Seçin **Kapat**.

### <a name="to-change-a-profile"></a>Bir profili değiştirmek için
1. Azure, projeniz için kısayol menüsünü açın ve ardından **Yayımla**.
2. İçinde **hedef profil** listesinde, değiştirmek istediğiniz profili seçin.
3. Seçin **önceki** ve **sonraki** düğmeler Yayımla Sihirbazı'nın her sayfasında görüntüleyin ve ardından istediğiniz ayarları değiştirin. Bkz: [Azure uygulaması Yayımlama Sihirbazı](http://go.microsoft.com/fwlink/p/?LinkID=623085) bilgi.
4. Ayarları değiştirmeyi bitirdiğinizde seçin **sonraki** dönmek için **ayarları** sayfası.
5. (İsteğe bağlı) **Yayımla** yeni ayarlar kullanılarak bulut hizmetine yayımlamak için. Şu anda bulut hizmetinizi yayımlayın istemediğiniz ve yayınlama Sihirbazı'nı kapatın, Visual Studio, profil için değişiklikleri kaydetmek isteyip istemediğinizi sorar.

## <a name="next-steps"></a>Sonraki adımlar
Azure Visual Studio projenizden diğer bölümlerini yapılandırma hakkında bilgi edinmek için [bir Azure projesi yapılandırma](http://go.microsoft.com/fwlink/p/?LinkID=623075)

