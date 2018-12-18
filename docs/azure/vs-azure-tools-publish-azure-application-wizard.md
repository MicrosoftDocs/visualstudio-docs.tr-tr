---
title: Azure bulut hizmeti yayımlama
description: Visual Studio Azure uygulaması Yayımlama Sihirbazı çeşitli ayarlarını yapılandırmayı öğrenin
author: ghogen
manager: douge
assetId: 7d8f1ac9-e439-47e0-a183-0642c4ea1920
ms.prod: visual-studio-dev15
ms.technology: vs-azure
ms.custom: seodec18
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 03/21/2017
ms.author: ghogen
ms.openlocfilehash: f25a4497fa79ba9d3bb09a7c7c666ea3e90e296a
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53061681"
---
# <a name="using-the-visual-studio-publish-azure-application-wizard"></a>Visual Studio Azure Uygulamasını Yayımlama Sihirbazı'nı kullanma

Visual Studio'da bir web uygulaması geliştirme sonra kullanarak bir Azure bulut hizmeti için bu uygulamayı yayımlayabilirsiniz **Azure uygulamasını Yayımla** Sihirbazı.

> [!Note]
> Bu makale, web siteleri için bulut Hizmetleri dağıtma hakkında yöneliktir. Web sitelerine dağıtma hakkında daha fazla bilgi için bkz: [bir Azure Web sitesinin nasıl dağıtılacağı](https://social.msdn.microsoft.com/Search/windowsazure?query=How%20to%20Deploy%20an%20Azure%20Web%20Site&Refinement=138&ac=4#refinementChanges=117&pageNumber=1&showMore=false).

## <a name="accessing-the-publish-azure-application-wizard"></a>Azure uygulamasını Yayımla Sihirbazı'na erişim

Azure uygulamasını Yayımla Sihirbazı'nı sahip olduğunuz Visual Studio projesi türüne bağlı olarak iki yolla erişebilir.

**Bir Azure bulut hizmeti projesi varsa:**

1. Oluşturun veya bir Azure bulut hizmeti projesini Visual Studio'da açın.

1. İçinde **Çözüm Gezgini**, projeye sağ tıklayın ve bağlam menüsünden seçin **Yayımla**.

**Azure için etkinleştirilmemiş bir web uygulaması projesi varsa:**

1. Oluşturun veya bir Azure bulut hizmeti projesini Visual Studio'da açın.

1. İçinde **Çözüm Gezgini**, projeye sağ tıklayın ve bağlam menüsünden seçin **dönüştürme** > **Azure bulut hizmeti projesine Dönüştür**. 

1. İçinde **Çözüm Gezgini**, Azure yeni oluşturulan projeye sağ tıklayın ve bağlam menüsünden seçin **Yayımla**.

## <a name="sign-in-page"></a>Oturum açma sayfası

![Oturum açma sayfası](./media/vs-azure-tools-publish-azure-application-wizard/sign-in.png)

**Hesap** - bir hesap seçin ya da seçin **Hesap Ekle** hesap açılır listesindeki.

**Aboneliğinizi seçin** -dağıtımınız için kullanılacak aboneliği seçin.

## <a name="settings-page---common-settings-tab"></a>Ayarları Sayfası - Genel Ayarları sekmesi

![Ortak ayarları](./media/vs-azure-tools-publish-azure-application-wizard/settings-common-settings.png)

**Bulut hizmeti** -açılan listeyi kullanarak ya da mevcut bir bulut hizmeti ya da seçin seçin  **&lt;Yeni Oluştur >** ve bir bulut hizmeti oluşturun. Veri Merkezi, her bir bulut hizmeti için parantez içinde görüntüler. Veriler aynı depolama hesabı (Gelişmiş) için veri merkezi konumu olarak bulut hizmeti için konumu merkezi önerilir.

**Ortam** -seçin **üretim** veya **hazırlama**. Uygulamanızı bir test ortamında dağıtmak istiyorsanız hazırlık ortamı seçin. 

**Derleme Yapılandırması** -seçin **hata ayıklama** veya **yayın**.

**Hizmet yapılandırması** -seçin **bulut** veya **yerel**.

**Tüm roller için Uzak masaüstünü etkinleştirme** -hizmete uzaktan bağlanmak istiyorsanız bu seçeneği belirleyin. Bu seçenek, öncelikli olarak sorun giderme için kullanılır. Daha fazla bilgi için [Visual Studio kullanarak Azure Cloud Services'ta bir rol için Uzak Masaüstü Bağlantısı etkinleştirme](/azure/cloud-services/cloud-services-role-enable-remote-desktop-visual-studio).

**Tüm web rolleri için Web dağıtımı etkinleştirmek** -web dağıtımı hizmeti etkinleştirmek için bu seçeneği belirleyin. Da seçmelisiniz **tüm roller için Uzak masaüstünü etkinleştir** bu özelliği kullanmak için seçeneği. Daha fazla bilgi için [Visual Studio kullanarak bir bulut hizmeti yayımlama](vs-azure-tools-publishing-a-cloud-service.md).

## <a name="settings-page---advanced-settings-tab"></a>Ayarları sayfası - Gelişmiş Ayarları sekmesi

![Gelişmiş ayarlar](./media/vs-azure-tools-publish-azure-application-wizard/settings-advanced-settings.png)

**Dağıtım etiketi** -varsayılan adını kabul edin veya seçtiğiniz bir ad girin. Dağıtım etiketi tarihi eklemek için onay kutusunu seçili bırakın. 

**Depolama hesabı** -bu dağıtım için kullanılacak depolama hesabını seçin **&lt;Yeni Oluştur > depolama hesabı oluşturmak için. Veri Merkezi, her depolama hesabı için parantez içinde görüntüler. Depolama hesabı için veri merkezi konumu (ortak ayarları) bulut hizmeti için veri merkezi konumu ile aynı olduğunu önerilir.

Azure depolama hesabı, uygulama dağıtımı için paketi depolar. Uygulama dağıtıldıktan sonra paket depolama hesabından kaldırıldı.

**Hata durumunda dağıtımı Sil** -yayımlama sırasında herhangi bir hatayla karşılaşılmazsa silinmiş dağıtım için bu seçeneği belirleyin. Bulut hizmetiniz için sabit bir sanal IP adresi korumak istiyorsanız bu seçeneği işaretli değil olmalıdır.

**Dağıtım güncelleştirme** -güncelleştirilmiş bileşenleri yalnızca dağıtmak istiyorsanız bu seçeneği belirleyin. Bu dağıtım türünde tam bir dağıtıma göre daha hızlı olabilir. Bulut hizmetiniz için sabit bir sanal IP adresi korumak istiyorsanız bu denetlenmelidir. 

**Dağıtım güncelleştirmesi - ayarları** -bu iletişim kutusunu daha rollerinin güncelleştirilmesi için nasıl istediğinizi belirtmek için kullanılır. Seçerseniz **Artımlı güncelleştirme**, uygulamanızın her örneği güncelleştirilir birbiri ardına, böylece uygulama her zaman kullanılabilir. Seçerseniz **eşzamanlı güncelleştirme**, uygulamanızın tüm örnekleri aynı anda güncelleştirilir. Eşzamanlı güncelleştirilmesi daha hızlıdır, ancak hizmet uygulamanızın güncelleştirme işlemi sırasında kullanılabilir olmayabilir.

![Dağıtım ayarları](./media/vs-azure-tools-publish-azure-application-wizard/deployment-settings.png)

**IntelliTrace'i etkinleştirme** -IntelliTrace'i etkinleştirmek isteyip istemediğinizi belirtin. IntelliTrace ile Azure içinde çalıştığında bir rol örneği için kapsamlı hata ayıklama bilgileri günlüğe kaydedebilirsiniz. Bir sorunun nedenini bulmak gerekiyorsa, IntelliTrace günlüklerini, Visual Studio'dan, Azure'da çalışıyormuş gibi kodunuzda adım adım ilerleyin için de kullanabilirsiniz. IntelliTrace'i kullanma hakkında daha fazla bilgi için bkz. [yayımlanan Azure bulut hizmeti Visual Studio ve IntelliTrace ile hata ayıklama](./vs-azure-tools-intellitrace-debug-published-cloud-services.md).

**Profil oluşturmayı etkinleştir** -performans profil oluşturmayı etkinleştirmek isteyip istemediğinizi belirtin. Visual Studio profil oluşturucu, bulut hizmetinizin nasıl çalışacağını hesaplama yönlerini detaylı olarak çözümlenmesi almanıza olanak sağlar. Visual Studio profil oluşturucu kullanma hakkında daha fazla bilgi için bkz. [bir Azure bulut hizmetinin performansını test etme](./vs-azure-tools-performance-profiling-cloud-services.md).

**Uzaktan hata ayıklayıcı tüm roller için etkinleştirme** -uzaktan hata ayıklamayı etkinleştirmek isteyip istemediğinizi belirtin. Visual Studio kullanarak bulut hizmetlerinde hata ayıklama ile ilgili daha fazla bilgi için bkz: [bir Azure bulut hizmeti veya sanal makinesinde Visual Studio'da hata ayıklama](./vs-azure-tools-debug-cloud-services-virtual-machines.md).

## <a name="diagnostics-settings-page"></a>Tanılama Ayarları sayfası

![Tanılama ayarları](./media/vs-azure-tools-publish-azure-application-wizard/diagnostic-settings.png)

Tanılama, bir Azure bulut hizmeti (veya Azure sanal makinesi) gidermek sağlar. Tanılama hakkında daha fazla bilgi için bkz. [Azure bulut Hizmetleri ve sanal makineler için yapılandırma tanılama](./vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines.md). Application Insights hakkında daha fazla bilgi için bkz: [Application Insights nedir?](/azure/application-insights/app-insights-overview).

## <a name="summary-page"></a>Özet sayfası

![Özet](./media/vs-azure-tools-publish-azure-application-wizard/summary.png)

**Hedef profil** -seçtiğiniz ayarları bir yayımlama profili oluşturmak seçim yapabilirsiniz. Örneğin, bir test ortamı için bir profil, diğeri üretim için oluşturabilirsiniz. Bu profilin kaydedileceği seçin **Kaydet** simgesi. Sihirbaz, profili oluşturur ve Visual Studio projesinde kaydeder. Profil adı değiştirmek için açın **hedef profil** listeleyin ve ardından  **&lt;Yönet... &gt;**.

   > [!Note]
   > Visual Studio'daki Çözüm Gezgini'nde yayımlama profilini görünür ve profil ayarları .azurePubxml uzantılı bir dosyaya yazılır. Ayarları XML etiketleri öznitelikleri kaydedilir.

## <a name="publishing-your-application"></a>Uygulamanızı yayımlama

Projenizin dağıtımı için tüm ayarları yapılandırdıktan sonra Seç **Yayımla** iletişim kutusunun alt kısmındaki. İşlem durumunu izleyebilirsiniz **çıkış** Visual Studio'daki.

## <a name="next-steps"></a>Sonraki adımlar

- [Geçiş ve Azure bulut hizmetinde Visual Studio'dan bir Web uygulaması yayımlama](./vs-azure-tools-migrate-publish-web-app-to-cloud-service.md)

- [Azure bulut hizmetinde yayımlamak için Visual Studio kullanmayı öğrenin](./vs-azure-tools-publishing-a-cloud-service.md)

- [Yayımlanan bir Azure bulut hizmeti Visual Studio ve IntelliTrace ile hata ayıklama](./vs-azure-tools-intellitrace-debug-published-cloud-services.md)

- [Bir Azure bulut hizmetinin performansını test etme](./vs-azure-tools-performance-profiling-cloud-services.md)

- [Azure bulut Hizmetleri ve sanal makineler için tanılamayı yapılandırma](./vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines.md).

- [Application Insights nedir?](/azure/application-insights/app-insights-overview)