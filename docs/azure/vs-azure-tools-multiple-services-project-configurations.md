---
title: Birden çok hizmet yapılandırması'nı kullanarak Azure projenizi yapılandırma | Microsoft Docs
description: Bir Azure bulut hizmeti projesi ServiceDefinition.csdef ve ServiceConfiguration.Local.cscfg ServiceConfiguration.Cloud.cscfg dosyaları değiştirerek yapılandırmayı öğrenin.
author: ghogen
manager: douge
assetId: a4fb79ed-384f-4183-9f74-5cac257206b9
ms.prod: visual-studio-dev15
ms.technology: vs-azure
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 11/11/2017
ms.author: ghogen
ms.openlocfilehash: e4dfa7276c217a7cf17203f6ac84bb0ce5585f94
ms.sourcegitcommit: e03b7a4cab26fbc792f368e3c6b4ca4a03caa786
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/28/2018
ms.locfileid: "52459712"
---
# <a name="configuring-your-azure-project-in-visual-studio-to-use-multiple-service-configurations"></a>Visual Studio'da Azure projenizi birden çok hizmet yapılandırması kullanacak şekilde yapılandırma

Visual Studio'da bir Azure bulut hizmeti projesi üç yapılandırma dosyalarını içerir: `ServiceDefinition.csdef`, `ServiceConfiguration.Local.cscfg`, ve `ServiceConfiguration.Cloud.cscfg`:

- `ServiceDefinition.csdef` Azure bulut hizmeti ve kendi rolleri gereksinimlerini açıklar ve tüm örnekleri için geçerli ayarları sağlamak için dağıtılır. Ayarlar çalışma zamanında Azure hizmet barındırma çalışma zamanı API'sini kullanarak okuyabilir. Bu dosya, yalnızca bulut hizmeti durdurulduğunda Azure'da güncelleştirilebilir.
- `ServiceConfiguration.Local.cscfg` ve `ServiceConfiguration.Cloud.cscfg` tanımında ayarları dosya ve her rol için çalıştırılacak örnek sayısını belirtin değerleri sağlayın. "Yerel" dosyasını yerel olarak hata ayıklama içinde kullanılan değerleri içerir. "Bulut" dosyası olarak azure'a dağıtılan `ServiceConfiguration.cscfg` ve sunucu ortamı için ayarları sağlar. Bu dosya, bulut hizmetinizin Azure üzerinde çalışırken güncelleştirilebilir.

Yapılandırma ayarları yönetilir ve uygun rolü için özellik sayfaları kullanarak Visual Studio'da değiştirdi (role sağ tıklayıp **özellikleri**, veya bir rolü çift tıklayın). Değişiklikleri hangi yapılandırma seçilir için kapsamı belirlenmiş **hizmet yapılandırması** açılır. Web ve çalışan rolleri için özellikleri aşağıdaki bölümlerde açıklanan durumlarda, dışında benzerdir.

![VS_Solution_Explorer_Roles_Properties](./media/vs-azure-tools-multiple-services-project-configurations/IC784076.png)

Hizmet yapılandırma dosyalarını ve hizmet tanımı için temel alınan şemalar hakkında daha fazla bilgi için bkz. [.csdef XML Şeması](/azure/cloud-services/schema-csdef-file) ve [.cscfg XML Şeması](/azure/cloud-services/schema-cscfg-file) makaleler. Hizmet yapılandırması hakkında daha fazla bilgi için bkz. [bulut hizmetlerini yapılandırma](/azure/cloud-services/cloud-services-how-to-configure-portal).


## <a name="configuration-page"></a>Yapılandırma sayfası

### <a name="service-configuration"></a>Hizmet yapılandırması

Seçer `ServiceConfiguration.*.cscfg` dosya değişikliklerden etkilenir. Varsayılan olarak, yerel ve bulut çeşitleri vardır ve kullanabileceğiniz **Yönet...**  kopyalayın, yeniden adlandırma ve yapılandırma dosyalarını kaldırmak için komutu. Bu dosyalar, bulut hizmeti projenizi eklenir ve görünür **Çözüm Gezgini**. Ancak, bu denetimden yalnızca yeniden adlandırma veya yapılandırmaları kaldırılıyor yapılabilir.

### <a name="instances"></a>Örnekler

Ayarlama **örneği** hizmetin bu rol için çalıştırılması örnek sayısı için özellik sayısı.

Ayarlama **VM boyutu** özelliğini **çok küçük**, **küçük**, **orta**, **büyük**, veya **Çok büyük**.  Daha fazla bilgi için [Cloud Services boyutları](/azure/cloud-services/cloud-services-sizes-specs).

### <a name="startup-action-web-role-only"></a>Başlangıç eylemi (yalnızca Web rolü)

Visual Studio hata ayıklamaya başladığınızda bir web tarayıcısı için HTTP uç noktaları veya HTTPS uç noktaları ya da her ikisini de başlatmalı belirtmek için bu özelliği ayarlayın.

**HTTPS uç noktası** seçenek, yalnızca zaten rolünüz için HTTPS uç noktasının tanımladıysanız kullanılabilir. Bir HTTPS uç noktası tanımlayabileceğiniz **uç noktaları** özellik sayfası.

Bir HTTPS uç noktası zaten eklediyseniz, HTTPS uç noktası seçeneği varsayılan olarak etkindir ve HTTP uç noktanız için bir tarayıcı yanı sıra hata ayıklama başlangıç seçeneklerin etkin olduğu varsayılırsa başlattığınızda, Visual Studio Bu uç nokta için bir tarayıcı başlatır.

### <a name="diagnostics"></a>Tanılamalar

Varsayılan olarak, tanılama Web rolü için etkinleştirilir. Azure bulut hizmeti projesi ve depolama hesabı, yerel depolama öykünücüsü kullanma için ayarlanır. Azure'a dağıtmaya hazır olduğunuzda builder düğmesini seçebilirsiniz (**...** ) Azure depolama yerine kullanılacak. İsteğe bağlı veya otomatik olarak zamanlanan aralıklarda tanılama verilerini depolama hesabına aktarabilir. Azure Tanılama hakkında daha fazla bilgi için bkz: [Azure bulut Hizmetleri ve sanal Makineler'de tanılamayı etkinleştirme](/azure/cloud-services/cloud-services-dotnet-diagnostics).

## <a name="settings-page"></a>Ayarları sayfası

Üzerinde **ayarları** sayfasında, ayarları bir yapılandırma için ad-değer çiftleri olarak ekleyebilirsiniz. Rolünde çalışan kod tarafından sağlanan sınıfları kullanarak çalışma zamanında yapılandırma ayarlarınızı değerlerini okuyabilir [Azure yönetilen kitaplığı](http://go.microsoft.com/fwlink?LinkID=171026), özellikle [GetConfigurationSettingValue](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.serviceruntime.roleenvironment.getconfigurationsettingvalue.aspx) yöntemi.

### <a name="configuring-a-connection-string-for-a-storage-account"></a>Bir depolama hesabı için bir bağlantı dizesi yapılandırma

Bir bağlantı dizesi veya Azure depolama hesabınız depolama öykünücüsü için bağlantı ve kimlik doğrulama bilgileri sağlayan bir ayardır. Her bir rolü kodunda Azure depolama (BLOB'lar, kuyruklar veya tablolar) eriştiğinde, bir bağlantı dizesi gerekir.

> [!Note]
> Azure depolama hesabı için bir bağlantı dizesi, tanımlı bir biçimi kullanmanız gerekir (bkz [Azure Storage bağlantı dizelerini yapılandırma](/azure/storage/common/storage-configure-connection-string)).

Bulut hizmeti uygulamayı dağıttığınızda bir Azure storage hesabını ayarlayın, gerektiği gibi yerel depolama kullanmak için bağlantı dizesini ayarlayabilirsiniz. Bağlantı dizesi düzgün bir şekilde ayarlamak için hata rolünüz başlatma veya başlatılıyor, meşgul ve durdurma durumları arasında geçiş yapmak için neden olabilir.

Bir bağlantı dizesi oluşturmak için Seç **ayar Ekle** ayarlayıp **türü** "Bağlantı dizesi".

Yeni veya var olan bağlantı dizeleri için seçin **...** * sağ tarafındaki **değer** açmak için alan **depolama bağlantı dizesi oluştur** iletişim:

1. Altında **bağlanırken**, seçin **aboneliğinizi** seçeneği bir abonelikten bir depolama hesabı seçin. Visual Studio, ardından depolama hesabı kimlik bilgilerini otomatik olarak edinir `.publishsettings` dosya.
1. Seçme **el ile kimlik bilgileri girilen** hesap adını belirtin ve anahtar kullanarak doğrudan Azure portalından bilgi sağlar. Hesap anahtarı kopyalamak için:
    1. Azure portal ve select depolama hesabına gidin **anahtarları Yönet**.
    1. Hesap anahtarı kopyalamak için depolama hesabı seçin Azure Portal'da gidin **ayarlar > erişim anahtarları**, sonra birincil erişim anahtarını panoya kopyalamak için Kopyala düğmesini kullanın.
1. Bağlantı seçeneklerinden birini seçin. **Özel uç noktalar belirtin** kuyruklar ve BLOB'lar, tablolar için belirli URL'leri belirtin isteyip istemediğinizi sorar. Özel uç noktalar kullanmanıza izin verir [özel etki alanları](/azure/storage/blobs/storage-custom-domain-name) ve daha kesin olarak erişimi denetleme. Bkz: [Azure Storage bağlantı dizelerini yapılandırma](/azure/storage/common/storage-configure-connection-string).
1. Seçin **Tamam**, ardından **Dosya > Kaydet** yeni bağlantı dizesiyle yapılandırmasını güncelleştirmek için.

Uygulamanızı Azure'da yayımlarken, Azure depolama hesabı bağlantı dizesi içeren hizmet yapılandırmasını yeniden seçin. Uygulamanızı yayımladıktan sonra uygulamanın Azure storage hizmetlerine karşı beklendiği gibi çalıştığını doğrulayın.

Hizmet yapılandırması güncelleştirme hakkında daha fazla bilgi için bkz [depolama hesapları için bağlantı dizelerini Yönet](vs-azure-tools-configure-roles-for-cloud-service.md#manage-connection-strings-for-storage-accounts).

## <a name="endpoints-page"></a>Uç noktaları sayfası

Bir web rolü, 80 numaralı bağlantı noktasında genellikle tek bir HTTP uç noktası vardır. Bir çalışan rolü, diğer taraftan, HTTP, HTTPS veya TCP uç noktaları herhangi bir sayıda olabilir. Uç noktalar dış istemciler için kullanılabilir olan giriş uç noktaları veya hizmet üzerinde çalışan diğer rollerin kullanılabilir iç uç nokta olabilir.

- Dış istemciler ve Web tarayıcıları için bir HTTP uç noktası kullanılabilir olması için giriş uç noktası türü değiştirme ve bir ad ve bir genel bağlantı noktası numarası belirtin.
- Dış istemciler ve Web tarayıcıları için HTTPS uç noktasının kullanılabilir olması için uç nokta türüne değiştirin **giriş**, bir ad, bir genel bağlantı noktası numarası ve bir yönetim sertifikası adı belirtin. Sertifika üzerinde tanımlamalıdır **sertifikaları** bir yönetim sertifikası belirtebilmeniz için önce özellik sayfası. 
- Bir uç nokta diğer rolleri bulut hizmetindeki iç erişimi için kullanılabilir yapmak için uç nokta türü için iç değiştirmek ve bir ad ve bu uç nokta için olası özel bağlantı noktalarını belirtin.

## <a name="local-storage-page"></a>Yerel depolama sayfası

Kullanabileceğiniz **yerel depolama** bir rol için bir veya daha fazla yerel depolama kaynaklarını ayırmak için özellik sayfası. Yerel depolama kaynağı, Azure sanal makinenin bir rol örneği çalıştığı dosya sistemindeki ayrılmış bir dizindir.

## <a name="certificates-page"></a>Sertifikalar sayfası

**Sertifikaları** özellik sayfası hizmet yapılandırmanıza, sertifikaları hakkında bilgi ekler. Hizmetinizle sertifikalarınızı paketlenmiş değil dikkat edin. sertifikalarınızı ayrı olarak azure'a üzerinden karşıya yüklediğiniz gerekir [Azure portalında](http://portal.azure.com).

Burada bir sertifika ekleme hizmet yapılandırmanıza sertifikalarınızı bilgileri ekler. Sertifikalar ile hizmet paketlenmiş değil; sertifikalarınızı Azure portalı üzerinden ayrı olarak yüklemeniz gerekir.

Bir sertifika rolünüz ile ilişkilendirmek için sertifika için bir ad sağlayın. Bir HTTPS uç noktası yapılandırdığınızda sertifika için başvurmak için bu adı kullanın **uç noktaları** sayfası. Ardından, sertifika deposuna olup olmadığını belirtin **yerel makine** veya **geçerli kullanıcının** ve deponun adı. Son olarak, sertifikanın parmak izini girin. Sertifika geçerli User\Personal (My) deposuna ise, sertifikanın parmak izi sertifika doldurulmuş bir listeden seçerek girebilirsiniz. Başka bir konumda yer alıyorsa, parmak izi değeri el ile girin.

Sertifika sertifika deposundan eklediğinizde, tüm ara sertifikaları sizin için yapılandırma ayarlarını otomatik olarak eklenir. Ayrıca, bu Ara sertifikaları doğru hizmetiniz için SSL yapılandırmasını azure'a karşıya yüklenmelidir.

Yalnızca bulutta çalışırken hizmetiniz ile ilişkilendirmek istediğiniz yönetim sertifikaları, hizmetinizin uygulayın. Hizmetinizi yerel geliştirme ortamında çalıştırırken işlem öykünücüsü tarafından yönetilen standart bir sertifika kullanır.
