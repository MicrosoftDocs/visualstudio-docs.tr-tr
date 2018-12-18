---
title: Geçiş ve Azure bulut hizmeti için bir Web uygulaması yayımlama
description: Visual Studio kullanarak web uygulamanızı bir Azure bulut hizmetinde yayımlama ve geçirme hakkında bilgi edinin
author: ghogen
manager: douge
ms.assetid: 9394adfd-a645-4664-9354-dd5df08e8c91
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 11/10/2017
ms.author: ghogen
ms.openlocfilehash: dd81e33d34cd3e61c01e62f941edd074304499be
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/08/2018
ms.locfileid: "53072791"
---
# <a name="how-to-migrate-and-publish-a-web-application-to-an-azure-cloud-service-from-visual-studio"></a>Nasıl yapılır: geçirme ve Azure bulut hizmetinde Visual Studio'dan bir Web uygulaması yayımlama

Barındırma hizmetlerinin avantajlarından ve Azure ölçekleme yeteneğini yararlanmak için geçirme ve web uygulamanızı bir Azure bulut hizmeti dağıtmak isteyebilirsiniz. Sadece küçük değişiklikler gereklidir. Bu makalede, yalnızca bulut hizmetlerini dağıtma ele alınmıştır; App Service için bkz: [Azure App Service'te bir web uygulaması dağıtma](/azure/app-service/app-service-deploy-local-git).

> [!Important]
> Bu geçiş, yalnızca belirli ASP.NET, Silverlight, WCF ve WCF iş akışı projeleri için desteklenir. ASP.NET Core projeleri için desteklenmiyor. Bkz: [desteklenen proje şablonları](#supported-project-templates).

## <a name="migrate-a-project-to-cloud-services"></a>Bir proje cloud Services'a geçme

1. Web uygulaması projesine sağ tıklayıp **dönüştürme > Microsoft Azure bulut hizmeti projesine Dönüştür**. (Bir web rolü proje çözümde zaten varsa bu komut görünmüyor unutmayın.)
1. Visual Studio gerekli web rolü içeren bir çözümde bir bulut hizmeti projesi oluşturur. Uygulama projenizin ve son bu projenin adı aynı olan `.Azure`.
1. Visual Studio ayrıca ayarlar **Yereli Kopyala** özelliğini MVC 2, MVC 3, MVC 4 ve Silverlight iş kolu uygulamaları için gerekli olan herhangi bir derleme için true. Bu özellik bu derlemeler dağıtım için kullanılan hizmet paketi ekler.

   > [!Important]
   > Diğer derlemeleri veya bu web uygulaması için gerekli olan dosyalar varsa, bu dosyalar için özellikleri el ile ayarlamanız gerekir. Bu özellikleri ayarlama hakkında daha fazla bilgi için bkz: [hizmet paketi dosyaları şunlardır](#include-files-in-the-service-package).

### <a name="errors-and-warnings"></a>Hatalar ve uyarılar

Herhangi bir uyarı veya hatalar gibi eksik derlemeleri Azure'a dağıtmadan önce düzeltmek için sorunları gösterir.

Uygulamanızı çalıştırın ve işlem öykünücüsü kullanarak yerel olarak veya Azure'a yayımlama varsa aşağıdaki hatayı görebilirsiniz: "Belirtilen yol, dosya adı veya her ikisi çok uzun." Bu hata, tam Azure proje adının uzunluğu 146 karakterden uzun olduğunu gösterir. Bu sorunu çözmek için çözümünüz daha kısa bir yol ile farklı bir klasöre taşıyın.

Tüm uyarıları hata olarak değerlendir hakkında daha fazla bilgi için bkz. [Visual Studio ile bir Azure bulut hizmeti projesi yapılandırma](vs-azure-tools-configuring-an-azure-project.md).

### <a name="test-the-migration-locally"></a>Geçişi yerel olarak test etme

1. Visual Studio'da **Çözüm Gezgini**, eklenen bir bulut hizmeti projesine sağ tıklayıp **başlangıç projesi olarak ayarla**.
1. Seçin **hata ayıklama > hata ayıklamayı Başlat** Azure hata ayıklama ortamını başlatmak için (F5). Bu ortam, özellikle öykünmesi çeşitli Azure hizmetleri sağlar.

### <a name="use-an-azure-sql-database-for-your-application"></a>Uygulamanız için bir Azure SQL veritabanını kullan

Kullanan bir şirket içi SQL Server veritabanı, web uygulamanız için bir bağlantı dizesi varsa, veritabanınızı Azure SQL veritabanı'na geçirilmesini ve bağlantı dizesini güncelleştirmeniz gerekir. Bu işlemle ilgili yönergeler için aşağıdaki konulara bakın:

- [SQL veritabanı bulutta SQL Server veritabanını geçirme](/azure/sql-database/sql-database-cloud-migrate)
- [Azure SQL veritabanına bağlanmak ve sorgulamak için Visual Studio ile .NET (C#) kullanma](/azure/sql-database/sql-database-connect-query-dotnet-visual-studio).

## <a name="publish-the-application-to-azure-cloud-service"></a>Azure bulut Hizmeti'ne uygulama için yayımlama

1. Üzerinde açıklandığı gibi gerekli bulut hizmeti ve depolama hesapları Azure aboneliğinizde oluşturma [yayımlamak veya Visual Studio'dan Azure bir uygulamayı dağıtmak hazırlama](vs-azure-tools-cloud-service-publish-set-up-required-services-in-visual-studio.md).
1. Visual Studio'da Uygulama projesine sağ tıklayıp **Microsoft Azure'da Yayımla...**  (olan "Yayımla..." komutunu farklı.).
1. İçinde **Azure uygulamasını Yayımla** görüntülenir, Azure aboneliğinizde bir hesabı kullanarak oturum açın ve seçin **İleri >**.
1. İçinde **ayarlar > Genel ayarları** sekmesinde, hedef bulut hizmetinden seçin **bulut hizmeti** aşağı açılan listesinde, seçilen ortam ve yapılandırmalarıyla birlikte.
1. İçinde **Ayarları > Gelişmiş ayarlar**, depolama hesabı kullanmak **İleri >**.
1. İçinde **tanılama**, Application Insights'a bilgileri göndermek isteyip istemediğinizi seçin.
1. Seçin **İleri >** özeti görüntülemek için ardından **Yayımla** dağıtımını başlatmak için.
1. Visual Studio burada ilerleme durumunu izleyebilirsiniz. bir etkinlik günlüğü penceresi açılır:

    ![VST_AzureActivityLog](./media/vs-azure-tools-migrate-publish-web-app-to-cloud-service/IC744149.png)

1. (İsteğe bağlı) Dağıtım işlemini iptal etmek için etkinlik günlüğü'nde satır öğeyi sağ tıklatıp seçin **iptal edip Kaldır**. Bu komut, dağıtım işlemi durdurur ve Azure'dan dağıtım ortamı siler. Not: Bu dağıtım ortamı dağıtıldıktan sonra kaldırmak için kullanmalısınız [Azure portalında](https://portal.azure.com).
1. (İsteğe bağlı) Rol örneklerinizin başlattıktan sonra Visual Studio dağıtım ortamı otomatik olarak gösterir. **Sunucu Gezgini > bulut Hizmetleri** düğümü. Buradan, tek tek rol örneklerini durumunu görüntüleyebilirsiniz.
1. Dağıtımdan sonra uygulamaya erişmek için dağıtımınızın durumunu zaman yanındaki oku seçin **tamamlandı** görünür **Azure etkinlik günlüğü** birlikte URL. Belirli türde bir web uygulaması Azure'dan başlama hakkında ayrıntılar için aşağıdaki tabloya bakın.

## <a name="using-the-compute-emulator-and-starting-application-in-azure"></a>İşlem öykünücüsü'nü ve Azure'da uygulama başlatılıyor

Tüm uygulama türleri seçerek Visual Studio hata ayıklayıcıya bağlı bir tarayıcıda başlatılabilir **hata ayıklama > hata ayıklamayı Başlat** (F5). ASP.NET boş Web uygulaması projesinde, önce eklemelisiniz bir `.aspx` sayfasında uygulamanızda ve web projeniz için başlangıç sayfası olarak ayarlayın.

Aşağıdaki tabloda, Azure'da uygulama başlatma hakkında ayrıntılar verilmiştir:

   | Web uygulaması türü | Azure'da çalışan |
   | --- | --- | --- |
   | ASP.NET Web uygulaması<br/>(2 MVC, MVC 3, MVC 4 dahil) | URL'de seçin **dağıtım** için sekmesinde **Azure etkinlik günlüğü**. |
   | ASP.NET boş Web uygulaması | Varsayılan varsa `.aspx` sayfasında uygulamanızda, URL'de **dağıtım** için sekmesinde **Azure etkinlik günlüğü**. Başka bir sayfaya gitmek için bir tarayıcıda bir URL aşağıdaki biçimde girin: `<deployment_url>/<page_name>.aspx` |
   | Silverlight uygulaması<br/>Silverlight iş kolu uygulaması<br/>Silverlight gezinti uygulaması | Şu URL biçimi kullanarak uygulamanız için belirli bir sayfaya gidin: `<deployment_url>/<page_name>.aspx` |
    WCF hizmeti uygulaması<br/>WCF İş Akışı Hizmeti Uygulaması | Ayarlama `.svc` WCF Hizmeti projeniz için başlangıç sayfası olarak dosya. Ardından gidin `<deployment_url>/<service_file>.svc` |
   | ASP.NET dinamik varlıkları<br/>ASP.NET dinamik veri Linq to SQL | Bağlantı dizesi, sonraki bölümde açıklandığı gibi güncelleştirin. Ardından gidin `<deployment_url>/<page_name>.aspx`. Bir Azure SQL veritabanı için bir LINQ to SQL kullanmanız gerekir. |

## <a name="update-a-connection-string-for-aspnet-dynamic-entities"></a>ASP.NET dinamik varlıklar için bir bağlantı dizesini güncelleştirme

1. Bir ASP.NET dinamik varlıkları web uygulaması için bir SQL Azure veritabanı, daha önce (#use-an-azuresql-database-for-your-application) açıklandığı gibi oluşturun.
1. Tablo ve Azure portalından bu veritabanı için gereken alanları ekleyin.
1. Bir bağlantı dizesini belirtin `web.config` dosya şu biçimde ve dosyayı kaydedin:

    ```xml
    <addname="tempdbEntities"connectionString="metadata=res://*/Model1.csdl|res://*/Model1.ssdl|res://*/Model1.msl;provider=System.Data.SqlClient;provider connection string=&quot;data source=<server name>\SQLEXPRESS;initial catalog=<database name>;integrated security=True;multipleactiveresultsets=True;App=EntityFramework&quot;"providerName="System.Data.EntityClient"/>
    ```

    Güncelleştirme *connectionString* SQL Azure veritabanınızın ADO.NET bağlantı dizesi şu şekilde değeri:

    ```xml
    XMLCopy<addname="tempdbEntities"connectionString="metadata=res://*/Model1.csdl|res://*/Model1.ssdl|res://*/Model1.msl;provider=System.Data.SqlClient;provider connection string=&quot;Server=tcp:<SQL Azure server name>.database.windows.net,1433;Database=<database name>;User ID=<user name>;Password=<password>;Trusted_Connection=False;Encrypt=True;multipleactiveresultsets=True;App=EntityFramework&quot;"providerName="System.Data.EntityClient"/>
    ```

## <a name="supported-project-templates"></a>Desteklenen proje şablonları

Aşağıdaki tabloda geçişi ve bulut hizmetlerine yayımlanan uygulamalar şablonlardan birini kullanmanız gerekir. ASP.NET Core desteklenmiyor.

| Şablon grubu | Proje Şablonu |
| --- | --- |
| Web | ASP.NET Web uygulaması (.NET Framework) |
| Web | ASP.NET MVC 2 Web uygulaması |
| Web | ASP.NET MVC 3 Web uygulaması |
| Web | ASP.NET MVC4 Web uygulaması |
| Web | ASP.NET boş Web uygulaması (veya Site) |
| Web | ASP.NET MVC 2 boş Web uygulaması |
| Web | ASP.NET dinamik veri varlıkları Web uygulaması |
| Web | ASP.NET dinamik veri Linq to SQL Web uygulaması |
| Silverlight | Silverlight uygulaması |
| Silverlight | Silverlight iş kolu uygulaması |
| Silverlight | Silverlight gezinti uygulaması |
| WCF | WCF hizmeti uygulaması |
| WCF | WCF İş Akışı Hizmeti Uygulaması |
| İş Akışı | WCF İş Akışı Hizmeti Uygulaması |

## <a name="next-steps"></a>Sonraki adımlar

- [Yayımlama veya Visual Studio'dan Azure uygulaması dağıtmak hazırlama](vs-azure-tools-cloud-service-publish-set-up-required-services-in-visual-studio.md)
- [Adlı kimlik doğrulama bilgilerini ayarlama](vs-azure-tools-setting-up-named-authentication-credentials.md).
