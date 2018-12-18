---
title: Dağıtıma genel bakış | Microsoft Docs
ms.custom: seodec18
ms.date: 06/22/2018
ms.technology: vs-ide-deployment
ms.topic: overview
dev_langs:
- FSharp
- VB
- CSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 93a389fdafb6167fb132578111c7a8b5d02c8495
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53068058"
---
# <a name="overview-of-deployment-in-visual-studio"></a>Visual Studio'da dağıtımına genel bakış

Bir uygulamayı, hizmeti ya da bileşeni dağıtarak bunu diğer bilgisayarlardaki, cihazlardaki, sunuculardaki ya da buluttaki yükleme için dağıtmış olursunuz. İhtiyacınız olan dağıtım türü için uygun yöntemi Visual Studio'da seçebilirsiniz.

Birçok ortak uygulama türleri için Visual Studio'daki Çözüm Gezgini'nde, uygulama doğrudan dağıtabilirsiniz. Bu özellik, hızlı bir tur bkz [dağıtıma ilk bakış](../deployment/deploying-applications-services-and-components.md).

![Yayımlama seçeneği](../deployment/media/quickstart-publish-azure.png)

## <a name="what-publishing-options-are-right-for-me"></a>Hangi Yayımlama seçenekleri benim için uygun?

Öğesinden, Visual Studio içinde uygulamaları için doğrudan aşağıdaki hedefleri yayımlanabilir:

- [Azure uygulama hizmeti](#azure-app-service)
- [Azure sanal makineleri](#azure-virtual-machines)
- [Dosya sistemi](#file-system)
- [Özel hedefleri (IIS, FTP, vb.) ](#custom-targets), tüm isteğe bağlı web sunucuları içerir.

Üzerinde **Yayımla** sekmesi, mevcut bir yayımlama profili seçin, var olan bir içeri aktarma veya aşağıda açıklanan seçenekler kullanılarak yeni bir tane oluşturun. Farklı uygulama türleri için IDE'de yayımlama seçeneklerini gezinmek için bkz: [dağıtıma ilk bakış](../deployment/deploying-applications-services-and-components.md).

## <a name="azure-app-service"></a>Azure uygulama hizmeti

[Azure App Service](/azure/app-service/app-service-web-overview) ve [Linux üzerinde App Service'te](/azure/app-service/containers/app-service-linux-intro) yardımcı altyapısına bakım uygulama olmadan çeşitli ölçeklenebilir web uygulamaları ve Hizmetleri hızlı bir şekilde oluşturun.

Ne kadar güç bir App Service bilgisayar seçerek sahip belirlemek bir [katmanı veya planı fiyatlandırması](/azure/app-service/azure-web-sites-web-hosting-plans-in-depth-overview) içeren App Service için. Birden çok Web sahip olduğunuz uygulamalar (ve diğer uygulama türleri) paylaşmak aynı App Service fiyatlandırma katmanını değiştirme olmadan. Örneğin, aynı App Service üzerinde birlikte geliştirme, hazırlama ve üretim Web apps'te barındırabilir.

Azure'da sanal makineler bulutta barındırılan bir App Service çalışır, ancak bu sanal makineler, sizin için yönetilir. Bir App Service her uygulamada benzersiz bir atanacak \*. azurewebsites.net URL'SİYLE; özel etki alanı adlarını siteye atamaya izin ver tüm fiyatlandırma katmanlarına ücretsiz dışında.

### <a name="when-to-choose-azure-app-service"></a>Ne zaman Azure App Service'ı seçin

- Internet üzerinden erişilebilen bir web uygulamasını dağıtmak istiyorsanız.
- Yeniden dağıtmaya gerek kalmadan web uygulamanızı talebe göre otomatik olarak ölçeklendirmek istiyorsunuz.
- (Yazılım güncelleştirmeleri dahil), sunucu altyapısını korumak istemezsiniz.
- Makine düzeyinde özelleştirmeler, web uygulamanızı barındıran sunucularda gerekmez.

> Azure App Service, kendi veri merkezinizde veya diğer şirket içi bilgisayarları kullanmak istiyorsanız, bunu kullanarak yapabilirsiniz [Azure Stack](https://azure.microsoft.com/overview/azure-stack/).

App Service'e yayımlama hakkında daha fazla bilgi için bkz. [hızlı başlangıç - Azure App Service'e yayımlama](quickstart-deploy-to-azure.md) ve [hızlı başlangıç - Linux için ASP.NET Core yayımlama](quickstart-deploy-to-linux.md).

## <a name="azure-virtual-machines"></a>Azure sanal makineleri

[Azure sanal makineleri (VM'ler)](https://azure.microsoft.com/documentation/services/virtual-machines/) oluşturmak ve bulutta bilgi işlem kaynaklarını herhangi bir sayıda yönetmenize olanak tanır. Tüm yazılım ve güncelleştirmeler vm'lerde sorumluluğunu üstlenerek, bunları gerektiğinde, uygulamanız tarafından istenen kadar özelleştirebilirsiniz. İstenen sürece her birine atanan IP adresini korur ve sanal makineleri Uzak Masaüstü aracılığıyla doğrudan erişebilirsiniz.

Sanal makinelerde barındırılan bir uygulamanın ölçeklendirilmesi talebe göre ek VM'ler'kurmak dönen ve ardından gerekli yazılımı dağıtmak içerir. Bu ek düzeyi denetimi sağlar, farklı genel bölgelerde farklı şekilde ölçeklendirin. Örneğin, uygulamanızın çalışanlar bölge ofisi çeşitli çalışıyorsa Vm'lerinizi bu bölgelerde, büyük olasılıkla maliyetleri azaltma çalışanların sayısını göre ölçeklendirebilirsiniz.

Ek bilgi için bkz [ayrıntılı karşılaştırma](https://azure.microsoft.com/documentation/articles/choose-web-site-cloud-service-vm/) Azure App Service, Azure sanal makineler ve Visual Studio'da özel seçeneğini kullanarak dağıtım hedefi olarak kullanabileceğiniz diğer Azure hizmetleri arasında.

### <a name="when-to-choose-azure-app-virtual-machines"></a>Ne zaman Azure uygulama sanal makineleri seçin

- Tam Denetim kullanım ömrüne yönelik atanmış IP adresleri Internet üzerinden erişilebilir olan bir web uygulamasını dağıtmak istiyorsanız.
- Sunucularınız üzerinde belirli ağ yapılandırmaları, disk bölümleri ve benzeri, özel bir veritabanı sistemi gibi ek yazılımlar içeren makine düzeyinde özelleştirmeler gerekir.
- Web uygulamanızı ölçeklendirme denetim ince bir düzey kullanmanız gerekir.
- Başka bir nedenle uygulamanızı barındıran sunuculara doğrudan erişmeniz gerekir.

> Azure sanal makineler, kendi veri merkezinizde veya diğer şirket içi bilgisayarları kullanmak istiyorsanız, bunu kullanarak yapabilirsiniz [Azure Stack](https://azure.microsoft.com/overview/azure-stack/).

## <a name="file-system"></a>Dosya sistemi

Yalnızca belirli bir klasöre kendi bilgisayarınıza uygulamanızın dosyaları kopyalamak, dosya sistemine dağıtma anlamına gelir. Bu, test amacıyla veya bilgisayar bir sunucu da çalışıyorsa, sınırlı sayıda kişiler tarafından kullanılmak üzere uygulamayı dağıtmak için en sık kullanılır. Hedef klasör, ağda paylaşılan sonra dosya sistemine dağıtma web uygulama dosyaları kişilere ardından belirli sunuculara dağıtabileceğiniz kullanılabilir yapabilirsiniz.

Çalıştıran bir sunucu herhangi bir yerel makine uygulamanızı Internet veya Intranet nasıl yapılandırıldığına bağlı olarak ve bağlı olduğu ağlar üzerinden kullanılabilir hale getirebilirsiniz. (Bir bilgisayar doğrudan Internet'e bağlanmanız durumunda, dış güvenlik tehditlerine karşı korumak özellikle dikkatli olun.) Bu makineleri yönetmek için yazılım ve donanım yapılandırmaları, tam denetim sizdedir.

Herhangi bir nedenle (örneğin, makine erişimi), Azure App Service veya Azure sanal makineler gibi bulut hizmetlerini kullanmadan erişemezseniz, kullanabileceğiniz unutmayın [Azure Stack](https://azure.microsoft.com/overview/azure-stack/) kendi veri merkezinizde. Azure Stack, yönetmek ve Azure App Service ve Azure sanal makineler bilgi işlem kaynaklarında henüz her şeyi şirket içi tutarken kullanmanıza olanak sağlar.

### <a name="when-to-choose-file-system-deployment"></a>Ne zaman dosya sistemi dağıtımı seçin

- Yalnızca bir dosya paylaşımına, başkalarının da farklı sunuculara dağıtacak dağıtırsınız.
- Yalnızca yerel test dağıtımını ihtiyacınız vardır.
- İnceleyin ve potansiyel olarak uygulama dosyalarının bağımsız olarak başka bir dağıtım hedefe göndermeden önce değiştirmek istiyorsunuz.

Daha fazla bilgi için [hızlı başlangıç - bir yerel klasöre dağıtma](quickstart-deploy-to-local-folder.md)

## <a name="custom-targets-iis-ftp"></a>Özel hedefleri (IIS, FTP)

Özel bir hedef uygulamanızı Azure App Service, Azure sanal makineler veya yerel dosya sistemi dışında bir hedef dağıtmanıza olanak tanır. Bir dosya sistemi veya diğer bulut Hizmetleri dahil olmak üzere erişim sahibi herhangi başka bir sunucuya (Internet veya Intranet) dağıtabilirsiniz. Web ile çalışabilir dağıtın (dosya veya. ZIP) ve FTP.

Bir özel hedef seçerken, Visual Studio, bir profil adı ve sonra toplama ek ister **bağlantı** hedef sunucuya veya konumu, bir site adı ve kimlik bilgileri gibi bilgileri. Aşağıdaki davranışları denetleyebileceğiniz **ayarları** sekmesinde:

- Dağıtmak istediğiniz yapılandırma.
- Varolan dosyalar'ı hedefinizden kaldırılıp kaldırılmayacağını belirtir.
- Yayımlama sırasında ön derleme verilmeyeceğini belirtir.
- App_Data klasöründeki dosyaları dışarıda dağıtımından verilmeyeceğini belirtir.

Farklı ayarlarla profillerini yönetmek edinerek Visual Studio, herhangi bir sayıda özel dağıtım profilleri oluşturabilirsiniz.

### <a name="when-to-choose-custom-deployment"></a>Ne zaman özel bir dağıtım seçin

- Bulut Hizmetleri URL'ler erişilebilen Azure dışında bir sağlayıcı kullanıyorsunuz.
- Visual Studio içinden kullanın veya bu şekilde Azure hesaplarınızı için doğrudan bağlı olanları dışında kimlik bilgileri kullanarak dağıtmak istediğiniz.
- Dağıttığınız her zaman hedeften dosyaları silmek istediğiniz.

Daha fazla bilgi için [hızlı başlangıç - bir web sitesine dağıtma](quickstart-deploy-to-a-web-site.md)

## <a name="next-steps"></a>Sonraki adımlar

Öğretici:

- [Yayımla aracı ile .NET Core uygulamasını dağıtma](/dotnet/core/deploying/deploy-with-vs?toc=/visualstudio/deployment/toc.json&bc=/visualstudio/deployment/_breadcrumb/toc.json)
- [Azure'a bir ASP.NET core uygulaması yayımlama](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs?toc=/visualstudio/deployment/toc.json&bc=/visualstudio/deployment/_breadcrumb/toc.json)
- [Visual C++ üzerinde Dağıtım](/cpp/ide/deployment-in-visual-cpp)
- [UWP uygulamaları dağıtma](/windows/uwp/packaging/packaging-uwp-apps?toc=/visualstudio/deployment/toc.json&bc=/visualstudio/deployment/_breadcrumb/toc.json)
- [Web dağıtımı kullanarak Azure'da bir Node.js uygulaması yayımlama](https://github.com/Microsoft/nodejstools/wiki/Publish-to-Azure-Website-using-Web-Deploy?toc=/visualstudio/deployment/toc.json&bc=/visualstudio/deployment/_breadcrumb/toc.json)
- [Python uygulamasını Azure App Service'e yayımlama](/visualstudio/python/publishing-python-web-applications-to-azure-from-visual-studio?toc=/visualstudio/deployment/toc.json&bc=/visualstudio/deployment/_breadcrumb/toc.json)
