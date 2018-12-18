---
title: Veri erişimi ve araçları
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- "80025080"
helpviewer_keywords:
- data [Visual Studio]
- data access [Visual Studio]
- data [C#]
- ADO.NET, data access
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: e31eeaf3061968cfa916d2ec5a0d0e522b9f6ebb
ms.sourcegitcommit: 0cdd8e8a53fb4fd5e869f07c35204419fa12783d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53159535"
---
# <a name="access-data-in-visual-studio"></a>Visual Studio'da verilere erişime

Visual Studio'da verilere neredeyse tüm veritabanı ürün veya hizmeti, herhangi bir biçimde, her yerden bağlanma uygulamalar oluşturabilirsiniz: yerel bir makinede, yerel alan ağı veya genel, özel veya hibrit bulut.

JavaScript, Python, PHP, Ruby ve C++ için uygulamalar, başka herhangi bir şey kitaplıkları alma ve kod yazmaya yaptığı gibi verilere bağlanın. .NET uygulamaları için Visual Studio veri kaynakları keşfedin, depolamak ve bellekte verileri işlemek ve veri kullanıcı arabirimine bağlamak için nesne modelleri oluşturmak için kullanabileceğiniz araçlar sağlar. Microsoft Azure Azure depolamaya bağlanmak için .NET, Java, Node.js, PHP, Python, Ruby ve mobil uygulamalar ve Visual Studio Araçları için SDK'lar sağlar.

Aşağıdaki listelerde, Visual Studio'dan kullanılabilecek çok sayıda veritabanı ve depolama sistemlerini birkaçı gösterilir. [Microsoft Azure](https://azure.microsoft.com/) tüm sağlama ve yönetim temel alınan veri deposu içeren veri hizmetleri tekliflerdir. **Azure geliştirme** iş yükünde [Visual Studio 2017](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) doğrudan Visual Studio'dan Azure veri depoları ile çalışmanıza olanak tanır.

![Azure geliştirme iş yükü](media/azure-development-workload.png)

Burada listelenen SQL ve NoSQL veritabanı ürünlerin çoğunu, yerel bir makinede, Microsoft azure'da veya yerel ağdaki bir sanal makine üzerinde barındırılabilir. Microsoft Azure sanal makinesinde veritabanında barındırıyorsanız, veritabanı yönetmekten sorumlu.

**Microsoft Azure**

- SQL Veritabanı
- Azure Cosmos DB
- Depolama (BLOB'lar, tablolar, kuyruklar, dosyalar)
- SQL veri ambarı
- SQL Server Stretch Database
- StorSimple
- ve daha fazlası...

**SQL**

- SQL Server 2005-2016 (Express ve LocalDB içerir)
- Firebird
- MariaDB
- MySQL
- Oracle
- PostgreSQL
- SQLite
- ve daha fazlası...

**NoSQL**

- Apache Cassandra
- CouchDB
- MongoDB
- NVeritabanı
- OrientDB |
- RavenDB
- VelocityDB
- ve daha fazlası...

Birçok veritabanı satıcılar ve üçüncü taraflar tarafından NuGet paketlerini Visual Studio tümleştirmesini desteklemiyor. Nuget.org veya Visual Studio'da NuGet Paket Yöneticisi aracılığıyla tekliflerini keşfedin (**Araçları** > **NuGet Paket Yöneticisi** > **Manage NuGet Çözüm için paketler**). Diğer veritabanı ürünleri bir uzantısı olarak Visual Studio ile tümleştirin. Bu teklifler Visual Studio Market'te giderek göz atabilirsiniz **Araçları**, **Uzantılar ve güncelleştirmeler** seçip **çevrimiçi** sol bölmesinde iletişim kutusu. Daha fazla bilgi için [Visual Studio için uyumlu veritabanı sistemleri](../data-tools/installing-database-systems-tools-and-samples.md).

> [!NOTE]
> SQL Server 2005'e yönelik genişletilmiş destek 12 Nisan 2016 tarihinde sona erdi. Veri araçları Visual Studio 2015 ve sonraki sürümlerinde bu tarihten sonra SQL Server 2005 ile çalışmaya devam edeceği kesin değildir. Daha fazla bilgi için [SQL Server 2005'e yönelik uç destek Duyurusu](https://www.microsoft.com/sql-server/sql-server-2005).

## <a name="net-languages"></a>.NET dilleri

.NET Core dahil olmak üzere tüm .NET veri erişimi, ADO.NET, veri kaynağı, ilişkisel ve ilişkisel olmayan herhangi bir türden erişmek için bir arabirim tanımlayan bir sınıf kümesi dayanır. Visual Studio çeşitli araçları vardır ve veritabanlarına bağlanmanıza yardımcı olması için ADO.NET çalışmak tasarımcıları verileri işlemek ve kullanıcıya verileri sunar. Bu bölümdeki belgeler bu araçlarının nasıl kullanılacağını açıklar. Ayrıca, doğrudan ADO.NET komut nesneleri karşı programlama yapabilirsiniz. ADO.NET API'lerini doğrudan çağırma hakkında daha fazla bilgi için bkz. [ADO.NET](/dotnet/framework/data/adonet/index).

ASP.NET ile ilgili veri erişim belgeleri için bkz. [verilerle çalışma](https://www.asp.net/web-forms/overview/presenting-and-managing-data) ASP.NET sitesinde. ASP.NET MVC ile Entity Framework kullanan bir öğretici için bkz. [Entity Framework 6 Code MVC 5 kullanarak First ile çalışmaya başlama](/aspnet/mvc/overview/getting-started/getting-started-with-ef-using-mvc/creating-an-entity-framework-data-model-for-an-asp-net-mvc-application).

C# veya Visual Basic'te Evrensel Windows Platformu (UWP) uygulamaları, .NET için Microsoft Azure SDK'sı, Azure depolama ve diğer Azure hizmetlerine erişmek için kullanabilirsiniz. Herhangi bir RESTful hizmeti ile iletişimi Windows.Web.HttpClient sınıfı sağlar. Daha fazla bilgi için [Windows.Web.Http kullanarak bir HTTP sunucusuna bağlanmak üzere nasıl](https://msdn.microsoft.com/library/windows/apps/dn469430.aspx).

Yerel makinede veri depolama için önerilen yaklaşım uygulama ile aynı işlemde çalışan SQLite kullanmaktır. Bir nesne ilişkisel eşleme (ORM) katman gerekiyorsa, Entity Framework kullanabilirsiniz. Daha fazla bilgi için [veri erişimi](/windows/uwp/data-access/index) Windows Geliştirici Merkezi'nde.

En son sürümünü indirin emin olun, Azure hizmetlerine bağlanıyorsanız [Azure SDK Araçları](https://azure.microsoft.com/downloads/).

### <a name="data-providers"></a>Veri sağlayıcıları

ADO.NET kullanılabilir olması için bir veritabanı için özel bir olmalıdır *ADO.NET veri sağlayıcısının* veya başka bir ODBC ve OLE DB arabirimi kullanıma sunması gerekir. Microsoft'un sağladığı bir [ADO.NET veri sağlayıcıları listesini](https://docs.microsoft.com/dotnet/framework/data/adonet/ado-net-overview) SQL Server ürünlerinin yanı sıra, ODBC ve OLE DB sağlayıcıları için.

### <a name="data-modeling"></a>Veri modelleme

. NET'te, modelleme ve veri kaynağından aldıktan sonra bellekteki verileri işlemek için üç seçeneğiniz vardır:

[Entity Framework](../data-tools/entity-data-model-tools-in-visual-studio.md) tercih edilen Microsoft ORM teknoloji. Bunu ilişkisel verilere karşı programlama birinci sınıf .NET nesneleri kullanabilirsiniz. Yeni uygulamalar için bir model gerekli olduğunda varsayılan ilk seçenek olmalıdır. Bu, temel alınan ADO.NET sağlayıcısı özel desteğini gerektirir.

[LINQ to SQL](../data-tools/linq-to-sql-tools-in-visual-studio2.md) eski kuşak nesne ilişkisel eşleyicidir. Daha az karmaşık senaryolar için iyi çalışır, ancak artık etkin geliştirme değildir.

[Veri kümeleri](../data-tools/dataset-tools-in-visual-studio.md) üç modelleme teknolojilerinin en eski. Bu, öncelikli olarak hangi, katılmamaları büyük miktarlarda veri işleme veya karmaşık sorgular veya dönüşüm gerçekleştiren "veriler üzerinden formlar" uygulamaların hızlı geliştirme için tasarlandı. DataTable ve DataRow nesnelerin mantıksal olarak SQL veritabanı nesnelerini .NET nesneleri birden çok fazla benzer bir veri kümesi nesnesi oluşur. SQL veri kaynağını temel alan görece basit uygulamalar için veri kümeleri yine de iyi bir seçim olabilir.

Bu teknolojiler birini kullanmak için bir gereksinim değildir. Performans kritik olduğunda özellikle bazı senaryolarda, yalnızca bir DataReader nesnesi veritabanından okunan ve bir koleksiyon nesnesi listesi gibi ihtiyaç duyduğunuz değerleri kopyalayın için kullanabileceğiniz\<T >.

## <a name="native-c"></a>Yerel C++

SQL Server'a bağlanma C++ uygulamalarını kullanması gereken [SQL Server için Microsoft® ODBC sürücüsü 13.1](https://www.microsoft.com/download/details.aspx?id=53339) çoğu durumda. Sunucuları bağlıysa, OLE DB gerekli ise ve söz konusu kullandığınız [SQL Server Native Client](/sql/relational-databases/native-client/sql-server-native-client). Diğer veritabanlarını kullanarak erişebileceğiniz [ODBC](https://docs.microsoft.com/sql/odbc/microsoft-open-database-connectivity-odbc?view=sql-server-2017) veya doğrudan OLE DB sürücüleri. ODBC için geçerli standart veritabanı arabirimi olsa da, çoğu veritabanı sistemi ODBC arabirimi üzerinden erişilemeyen özel işlevsellik sağlar. OLE DB, yine de desteklenir, ancak yeni uygulamalar için önerilen eski bir COM veri erişimi teknolojisidir. Daha fazla bilgi için [Visual C++'da veri erişimi](/cpp/data/data-access-in-cpp).

C++ programları, REST hizmetlerini kullanabileceğiniz [C++ REST SDK](https://github.com/Microsoft/cpprestsdk).

Microsoft Azure depolamasıyla çalışmayı C++ programları kullanabileceğiniz [Microsoft Azure depolama istemci](https://www.nuget.org/packages/Microsoft.Azure.Storage.CPP).

Veri modelleme&mdash;Visual Studio C++ için ORM katman sağlamaz. [ODBC](https://www.codesynthesis.com/products/odb/) C++ için popüler bir açık kaynak ORM olduğu.

C++ uygulamalarından veritabanlarına bağlanma hakkında daha fazla bilgi için bkz: [C++ için Visual Studio veri Araçları](../data-tools/visual-studio-data-tools-for-cpp.md). Eski Visual C++ veri erişim teknolojileri hakkında daha fazla bilgi için bkz. [veri erişimi](/cpp/data/data-access-in-cpp).

## <a name="javascript"></a>JavaScript

[Visual Studio'da JavaScript](/scripting/javascript/javascript-language-reference) platformlar arası uygulamalar, UWP uygulamaları, bulut Hizmetleri, Web siteleri ve web uygulamaları oluşturmaya yönelik birinci sınıf bir dildir. Sık kullandığınız JavaScript kitaplıklarını ve veritabanı ürünleri yüklemek için Bower, Grunt, Gulp, npm ve Visual Studio içinden Nuget'ten kullanabilirsiniz. SDK'larından yükleyerek Azure depolama ve hizmetlere bağlanma [Azure Web sitesi](https://azure.microsoft.com/). Edge.js sunucu tarafı JavaScript (Node.js) için ADO.NET veri kaynaklarına bağlanan bir kitaplıktır.

## <a name="python"></a>Python

Yükleme [Visual Studio'da Python desteği](../python/overview-of-python-tools-for-visual-studio.md) Python uygulamaları oluşturmak için. Azure belgeleri, aşağıdakiler dahil olmak üzere verilere bağlanma hakkında birkaç öğreticiler vardır:

- [Django ve Azure SQL veritabanı](/azure/app-service/app-service-web-get-started-python)
- [Django ve MySQL Azure üzerinde](/azure/app-service-web/web-sites-python-ptvs-django-mysql)
- Çalışmak [blobları](/azure/storage/blobs/storage-quickstart-blobs-python), [dosyaları](/azure/storage/files/storage-python-how-to-use-file-storage), [kuyrukları](/azure/storage/queues/storage-python-how-to-use-queue-storage), ve [tablolar (Cosmo DB)](/azure/cosmos-db/table-storage-how-to-use-python).

## <a name="related-topics"></a>İlgili konular

[Microsoft AI platform](https://azure.microsoft.com/overview/ai-platform/?v=17.42w)&mdash;Cortana Analytics Suite ve nesnelerin interneti için destek dahil olmak üzere Microsoft Akıllı bulut tanıtır.

[Microsoft Azure depolama](/azure/storage/)&mdash;açıklar Azure depolama ve Azure BLOB'ları, tabloları, kuyrukları ve dosyalarını kullanarak uygulama oluşturma.

[Azure SQL veritabanı](/azure/sql-database/)&mdash;hizmet olarak ilişkisel bir veritabanı olan Azure SQL Database'e bağlanma işlemini açıklamaktadır.

[SQL Server veri Araçları](/sql/ssdt/download-sql-server-data-tools-ssdt)&mdash;tasarımı, test ve veri bağlı uygulamalar ve veritabanları dağıtma araştırma basitleştiren araçlar açıklanmaktadır.

[ADO.NET](/dotnet/framework/data/adonet/index)&mdash;ADO.NET mimarisini ve ADO.NET sınıflarının uygulama verilerini yönetmek ve XML ve veri kaynakları ile etkileşim kurmak için nasıl kullanılacağını açıklar.

[ADO.NET Entity Framework](https://docs.microsoft.com/ef/ef6/)&mdash;geliştiricilere doğrudan ilişkisel bir veritabanında yerine kavramsal bir modeli karşı tanıyan veri uygulamalarının nasıl oluşturulacağını açıklar.

[WCF Veri Hizmetleri 4.5](/dotnet/framework/data/wcf/index)&mdash;nasıl kullanılacağını açıklar [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)] web veya intranet uygulayan veri hizmetlerini dağıtmanızı [açık veri Protokolü (OData)](https://www.odata.org/).

[Office çözümlerindeki veriler](../vsto/data-in-office-solutions.md)&mdash;Office çözümlerinde verilerin nasıl çalıştığını açıklayan konulara bağlantılar içerir. Burada şema tabanlı programlama, verileri önbelleğe alma ve sunucu tarafında veri erişimi hakkında bilgiler bulunur.

[LINQ (dil ile tümleşik sorgu)](/dotnet/csharp/linq/)&mdash;C# ve Visual Basic ve ilişkisel veritabanlarını, XML belgeleri, veri kümelerini ve bellek içi koleksiyonları sorgulamak için ortak bir Modeli'ne yerleşik sorgu yetenekleri açıklanır.

[Visual Studio'daki XML araçları](../xml-tools/xml-tools-in-visual-studio.md)&mdash;çalışma ile XML verileri, hata ayıklama XSLT, .NET Framework XML özelliklerini ve XML sorgusu mimarisini açıklar.

[XML belgeleri ve verileri](/dotnet/standard/data/xml/index)&mdash;XML belgeleri ve .NET Framework Veri çalışmak sınıf kapsamlı ve tümleşik kümesi için genel bir bakış sağlar.
