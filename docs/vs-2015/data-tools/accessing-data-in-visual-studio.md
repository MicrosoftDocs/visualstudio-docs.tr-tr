---
title: Verilere erişme
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- "80025080"
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- data [Visual Studio]
- data access [Visual Studio]
- data [C#]
- ADO.NET, data access
ms.assetid: 9812a6d5-23d2-4427-8b98-70a2abfec3bc
caps.latest.revision: 103
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: 20efcabb39049f1cfced3b6f941bc7e5bbd984d5
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53067352"
---
# <a name="accessing-data-in-visual-studio"></a>Visual Studio'da verilere erişme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]


Visual Studio'da verilere neredeyse tüm veritabanı ürün veya hizmeti, herhangi bir biçimde, her yerden bağlanma uygulamalar oluşturabilirsiniz: yerel bir makinede, yerel alan ağı veya genel, özel veya hibrit bulut.

 JavaScript, Python, PHP, Ruby ve C++ için uygulamalar, başka herhangi bir şey kitaplıkları alma ve kod yazmaya yaptığı gibi verilere bağlanın. .NET uygulamaları için Visual Studio veri kaynakları keşfedin, depolamak ve bellekte verileri işlemek ve veri kullanıcı arabirimine bağlamak için nesne modelleri oluşturmak için kullanabileceğiniz araçlar sağlar.     Microsoft Azure Azure depolamaya bağlanmak için .NET, Java, Node.js, PHP, Python, Ruby ve mobil uygulamalar ve Visual Studio Araçları için SDK'lar sağlar.

 Aşağıdaki listelerde, Visual Studio'dan kullanılabilecek çok sayıda veritabanı ve depolama sistemlerini birkaçı gösterilir. [Microsoft Azure](https://azure.microsoft.com/en-us/) tüm sağlama ve yönetim temel alınan veri deposu içeren veri hizmetleri tekliflerdir.  [Visual Studio için Azure Araçları](https://www.visualstudio.com/en-us/features/azure-tools-vs.aspx) doğrudan Visual Studio'dan Azure veri depoları ile çalışmanıza olanak sağlayan isteğe bağlı bir bileşendir. Burada listelenen SQL ve NoSQL veritabanı ürünlerin çoğunu, yerel bir makinede, Microsoft azure'da veya yerel ağdaki bir sanal makine üzerinde barındırılabilir. Bu senaryoda, veritabanı yönetmekten sorumlu olursunuz.

 **Microsoft Azure**

||||
|-|-|-|
|SQL veritabanı|DocumentDB|Depolama (BLOB'lar, tablolar, kuyruklar, dosyalar)|
|SQL veri ambarı|SQL Server Stretch Database|StorSimple|

 ve daha fazlası...

 **SQL**

||||
|-|-|-|
|SQL Server 2005 – 2016 Express ve LocalDB dahil,|Firebird|MariaDB|
|MySQL|Oracle|PostgreSQL|
|SQLite|||

 ve daha fazlası...

 **NoSQL**

||||
|-|-|-|
|Apache Cassandra|CouchDB|MongoDB|
|NVeritabanı|OrientDB|RavenDB|
|VelocityDB|||

 ve daha fazlası...

 Birçok veritabanı satıcılar ve üçüncü taraflar tarafından NuGet paketlerini Visual Studio tümleştirmesini desteklemiyor. Nuget.org veya Visual Studio'da NuGet Paket Yöneticisi aracılığıyla tekliflerini keşfedin (**Araçları** > **NuGet Paket Yöneticisi** > **Manage NuGet Çözüm için paketler**). Diğer veritabanı ürünleri bir uzantısı olarak Visual Studio ile tümleştirin.   Bu teklifler Visual Studio Galerisi'nde giderek göz atabilirsiniz **Araçları** > **Uzantılar ve güncelleştirmeler** seçip **çevrimiçi** sol iletişim kutusunun bölmesi.  Daha fazla bilgi için [veritabanı sistemleri, araçları ve örnek yükleme](../data-tools/installing-database-systems-tools-and-samples.md).

> [!NOTE]
>  SQL Server 2005'e yönelik genişletilmiş destek 12 Nisan 2016 tarihinde sona erdi.   Veri araçları Visual Studio 2015 ve sonraki sürümlerinde bu tarihten sonra SQL Server 2005 ile çalışmaya devam edeceği kesin değildir. Daha fazla bilgi için [SQL Server 2005'e yönelik uç destek Duyurusu](https://www.microsoft.com/en-us/server-cloud/products/sql-server-2005/).

### <a name="net-languages"></a>.NET dilleri
 .NET Core dahil olmak üzere tüm .NET veri erişimi, ADO.NET, veri kaynağı, ilişkisel ve ilişkisel olmayan herhangi bir türden erişmek için bir arabirim tanımlayan bir sınıf kümesi dayanır. Visual Studio çeşitli araçları vardır ve veritabanlarına bağlanmanıza yardımcı olması için ADO.NET çalışmak tasarımcıları verileri işlemek ve kullanıcıya verileri sunar. Bu bölümdeki belgeler bu araçlarının nasıl kullanılacağını açıklar. Ayrıca, doğrudan ADO.NET komut nesneleri karşı programlama yapabilirsiniz. ADO.NET API'lerini doğrudan çağırma hakkında daha fazla bilgi için bkz. [ADO.NET](https://msdn.microsoft.com/library/e80y5yhx\(v=vs.110\).aspx) MSDN Kitaplığı'nda.

 Özel ASP.NET ile ilgili veri erişim belgelerine bakın [verilerle çalışma](http://www.asp.net/web-forms/overview/presenting-and-managing-data) ASP.NET sitesinde. ASP.NET MVC ile Entity Framework kullanan bir öğretici için bkz. [Entity Framework 6 Code MVC 5 kullanarak First ile çalışmaya başlama](http://www.asp.net/mvc/overview/getting-started/getting-started-with-ef-using-mvc/creating-an-entity-framework-data-model-for-an-asp-net-mvc-application).

 C# veya Visual Basic'te Evrensel Windows Platformu (UWP) uygulamaları, .NET için Microsoft Azure SDK'sı, Azure depolama ve diğer Azure hizmetlerine erişmek için kullanabilirsiniz. Herhangi bir RESTful hizmeti ile iletişimi Windows.Web.HttpClient sınıfı sağlar. Daha fazla bilgi için [Windows.Web.Http kullanarak bir HTTP sunucusuna bağlanma](https://msdn.microsoft.com/library/windows/apps/dn469430.aspx.)

 Yerel makinede veri depolama için önerilen yaklaşım uygulama ile aynı işlemde çalışan SQLite kullanmaktır. Bir nesne ilişkisel eşleme (ORM) katman gerekiyorsa, Entity Framework kullanabilirsiniz. Daha fazla bilgi için [veri erişimi](https://msdn.microsoft.com/windows/uwp/data-access/index) Windows Geliştirici Merkezi'nde.

 En son sürümünü indirin emin olun, Azure hizmetlerine bağlanıyorsanız [Azure SDK Araçları](https://azure.microsoft.com/en-us/downloads/).

#### <a name="data-providers"></a>Veri sağlayıcıları
 ADO.NET kullanılabilir olması için bir veritabanı için özel bir olmalıdır *ADO.NET veri sağlayıcısının* veya başka bir ODBC ve OLE DB arabirimi kullanıma sunması gerekir. Microsoft'un sağladığı bir [ADO.NET veri sağlayıcıları listesini](https://msdn.microsoft.com/data/dd363565) SQL Server ürünlerinin yanı sıra, ODBC ve OLE DB sağlayıcıları.

#### <a name="data-modeling"></a>Veri modelleme
 . NET'te, modelleme ve veri kaynağından aldıktan sonra bellekteki verileri işlemek için üç seçeneğiniz vardır:

 Entity Framework tercih edilen Microsoft ORM teknoloji. Bunu ilişkisel verilere karşı programlama birinci sınıf .NET nesneleri kullanabilirsiniz. Yeni uygulamalar için bir model gerekli olduğunda varsayılan ilk seçenek olmalıdır. Bu, temel alınan ADO.NET sağlayıcısı özel desteğini gerektirir.

 LINQ to SQL eski kuşak nesne ilişkisel eşleyicidir. Daha az karmaşık senaryolar için iyi çalışır, ancak artık etkin geliştirme değildir.

 Veri kümeleri üç modelleme teknolojilerinin en eski. Bu, öncelikli olarak hangi, katılmamaları büyük miktarlarda veri işleme veya karmaşık sorgular veya dönüşüm gerçekleştiren "veriler üzerinden formlar" uygulamaların hızlı geliştirme için tasarlandı. DataTable ve DataRow nesnelerin mantıksal olarak SQL veritabanı nesnelerini .NET nesneleri birden çok fazla benzer bir veri kümesi nesnesi oluşur. SQL veri kaynağını temel alan görece basit uygulamalar için veri kümeleri yine de iyi bir seçim olabilir.

 Bu teknolojiler birini kullanmak için bir gereksinim değildir. Performans kritik olduğunda özellikle bazı senaryolarda, yalnızca bir DataReader nesnesi veritabanından okunan ve bir koleksiyon nesnesi listesi gibi ihtiyaç duyduğunuz değerleri kopyalayın için kullanabileceğiniz\<T >.

### <a name="native-c"></a>Yerel C++
 SQL Server'a bağlanma C++ uygulamalarını kullanması gereken [SQL Server Native Client](https://msdn.microsoft.com/sqlserver/aa937733.aspx). Diğer veritabanlarını kullanarak erişebileceğiniz [ODBC](https://msdn.microsoft.com/library/ms710252\(v=vs.85\).aspx) veya doğrudan OLE DB sürücüleri. ODBC için geçerli standart veritabanı arabirimi olsa da, çoğu veritabanı sistemi ODBC arabirimi üzerinden erişilemeyen özel işlevsellik sağlar.  OLE DB, yine de desteklenir, ancak yeni uygulamalar için önerilen eski bir COM veri erişimi teknolojisidir.  Daha fazla bilgi için [veri erişimi](http://msdn.microsoft.com/library/a9455752-39c4-4457-b14e-197772d3df0b).

 C++ programları, REST hizmetlerini kullanabileceğiniz [C++ REST SDK](https://github.com/Microsoft/cpprestsdk).

 Microsoft Azure depolamasıyla çalışmayı C++ programları kullanabileceğiniz [Microsoft Azure depolama istemci](http://www.nuget.org/packages/wastorage).

#### <a name="data-modeling"></a>Veri modelleme
 Visual Studio C++ için ORM katman sağlamaz.  [ODBC](http://www.codesynthesis.com/products/odb/) C++ için popüler bir açık kaynak ORM olduğu.

 Eski Visual C++ veri erişim teknolojileri hakkında daha fazla bilgi için bkz. [veri erişimi](http://msdn.microsoft.com/library/a9455752-39c4-4457-b14e-197772d3df0b)

### <a name="javascript"></a>JavaScript
 [Visual Studio'da JavaScript](https://msdn.microsoft.com/library/hh334522.aspx) platformlar arası uygulamalar, UWP uygulamaları, bulut Hizmetleri, Web siteleri ve web uygulamaları oluşturmaya yönelik birinci sınıf bir dildir. Sık kullandığınız JavaScript kitaplıklarını ve veritabanı ürünleri yüklemek için Bower, Grunt, Gulp, npm ve Visual Studio içinden Nuget'ten kullanabilirsiniz. SDK'larından yükleyerek Azure depolama ve hizmetlere bağlanma [Azure Web sitesi](https://azure.microsoft.com/).  Edge.js sunucu tarafı JavaScript (Node.js) için ADO.NET veri kaynaklarına bağlanan bir kitaplıktır.

### <a name="python"></a>Python
 Yükleme [Visual Studio için Python Araçları](http://microsoft.github.io/PTVS/) birlikte en sevdiğiniz Python Çerçevenizi CPython veya IronPython (.NET) uygulamaları oluşturabilir.  Visual Studio Web sitesi için Python araçları da dahil olmak üzere verilere bağlanma hakkında birkaç öğreticiler sahip [Django ve SQL veritabanı azure'da](https://github.com/Microsoft/PTVS/wiki/Django-and-SQL-Database-on-Azure), [Django ve MySQL azure'da](https://github.com/Microsoft/PTVS/wiki/Django-and-MySQL-on-Azure) ve [Bottle ve MongoDB üzerinde Azure](https://github.com/Microsoft/PTVS/wiki/Bottle-and-MongoDB-on-Azure).

## <a name="in-this-section"></a>Bu bölümde
 [Veritabanı sistemleri, araçları ve örnek yükleme](../data-tools/installing-database-systems-tools-and-samples.md) veritabanı ürünleri ve Visual Studio uzantıları veya bunları destekleyen sürücüleri edinme ve örnek veritabanları için deneme ve öğrenme amacıyla nerede bulunacağı açıklanır.

 [.NET için Visual Studio veri Araçları](http://msdn.microsoft.com/en-us/6b145922-2f00-47db-befc-bf351b4809a1) veri kaynaklarına bağlanmak, veri kümeleri veya Entity Framework modelleri oluşturma ve kullanıcı arabirimi denetimlerine veri bağlama için Visual Studio araç pencereleri kullanmayı açıklar.

## <a name="related-topics"></a>İlgili konular
 [Veriler, cihazlar ve analiz](https://msdn.microsoft.com/data-and-devices) Cortana Analytics Suite ve nesnelerin interneti için destek dahil olmak üzere Microsoft Akıllı bulut tanıtır.

 [Microsoft Azure depolama](https://azure.microCsoft.com/en-us/documentation/services/storage/) açıklar Azure depolama ve Azure BLOB'ları, tabloları, kuyrukları ve dosyalarını kullanarak uygulama oluşturma.

 [Azure SQL veritabanı](https://azure.microsoft.com/en-us/documentation/services/sql-database/) hizmet olarak ilişkisel bir veritabanı olan Azure SQL Database'e bağlanma işlemini açıklamaktadır.

 [SQL Server veri Araçları](https://msdn.microsoft.com/library/hh272686\(v=vs.103\).aspx) tasarımı, test ve veri bağlı uygulamalar ve veritabanları dağıtma araştırma basitleştiren araçlar açıklanmaktadır.

 [ADO.NET](http://msdn.microsoft.com/library/5b96ed06-9759-4966-a797-a1d5f6ee50ca) ADO.NET mimarisini ve ADO.NET sınıflarının uygulama verilerini yönetmek ve XML ve veri kaynakları ile etkileşim kurmak için nasıl kullanılacağını açıklar.

 [ADO.NET Entity Framework](https://msdn.microsoft.com/data/ef) geliştiricilere doğrudan ilişkisel bir veritabanında yerine kavramsal bir modeli karşı tanıyan veri uygulamalarının nasıl oluşturulacağını açıklar.

 [WCF Veri Hizmetleri 4.5](http://msdn.microsoft.com/library/73d2bec3-7c92-4110-b905-11bb0462357a) nasıl kullanılacağını açıklar [!INCLUDE[ssAstoria](../includes/ssastoria-md.md)] web veya intranet uygulayan veri hizmetlerini dağıtmanızı [açık veri Protokolü (OData)](http://go.microsoft.com/fwlink/?LinkID=182204).

 [Office çözümlerindeki veriler](http://msdn.microsoft.com/library/8478c095-864b-4ed3-8a70-1fc19b411c6a) Office çözümlerinde verilerin nasıl çalıştığını açıklayan konulara bağlantılar içerir. Burada şema tabanlı programlama, verileri önbelleğe alma ve sunucu tarafında veri erişimi hakkında bilgiler bulunur.

 [LINQ (dil ile tümleşik sorgu)](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d) yerleşik sorgu yetenekleri açıklanmaktadır C# ve Visual Basic ve ilişkisel veritabanlarını, XML belgeleri, veri kümelerini ve bellek içi koleksiyonları sorgulamak için ortak modeli.

 [Visual Studio'daki XML araçları](../xml-tools/xml-tools-in-visual-studio.md) çalışma ile XML verileri, hata ayıklama XSLT, .NET Framework XML özelliklerini ve XML sorgusu mimarisini açıklar.

 [XML belgeleri ve verileri](http://msdn.microsoft.com/library/e695047f-3c0f-4045-8708-5baea91cc380) XML belgeleri ve .NET Framework Veri çalışmak sınıf kapsamlı ve tümleşik kümesi için genel bir bakış sağlar.
