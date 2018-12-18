---
title: Veritabanı sistemleri, araçları ve örnek yükleme | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- sample databases
- databases, samples
ms.assetid: 821de34b-eaa9-40af-b9aa-b8305de16899
caps.latest.revision: 31
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: f18ace9a18eefd0758e581b83001b85c3f48a3da
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49244289"
---
# <a name="installing-database-systems-tools-and-samples"></a>Yükleme veritabanı sistemleri, araçları ve örnekleri
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Visual Studio kendi dahili olarak kullandığı dışındaki herhangi bir veritabanı sistemleri içermez. Visual Studio'da veri bağlı bir uygulama geliştirmek için genellikle veritabanı sistemi yerel geliştirme makinenize yükleyin ve hazır olduğunuzda uygulama ve veritabanı bir üretim ortamına ardından dağıtın. Veritabanı sistemi için .NET uygulamaları tarafından erişilebilir olmasını ve Visual Studio veri araçları pencerelerinde görünür olmasını, bir ADO.NET veri sağlayıcısının olması gerekir. Varlık veri modelleri .NET uygulamanızda kullanmayı planlıyorsanız bir sağlayıcı özellikle Entity Framework desteklemesi gerekir.     Birçok sağlayıcı, NuGet Paket Yöneticisi aracılığıyla veya Visual Studio Galerisi aracılığıyla sunulur.  
  
 SQL geliştirme için SQL Server veri araçları Visual Studio'da yüklü olduğundan emin olun. Tıklayın **görünümü** menüsü. SQL Server nesne Gezgini'ni görmüyorsanız, Denetim Masası'na gidin ve Visual Studio değiştirin. Yükleyicide **Microsoft SQL Server veri Araçları**.  
  
 Azure depolama API'leri kullanıyorsanız, Azure depolama öykünücüsünü üretime dağıtmaya hazır olana kadar ücret ödememek için geliştirme sırasında yerel makinenize yükleyin. Daha fazla bilgi için [geliştirme ve sınama için Azure depolama öykünücüsü kullanma](https://azure.microsoft.com/en-us/documentation/articles/storage-use-emulator/).  
  
 Aşağıdaki liste, bazı kullanılabilecek daha popüler veritabanı sistemleri Visual Studio projelerinde içerir. Listede hepsine yer verilmemiştir. Visual Studio Araçları ile derinlemesine tümleştirme sağlayan ADO.NET veri sağlayıcıları üçüncü taraf satıcılarla listesi için bkz. [ADO.NET veri sağlayıcıları](https://msdn.microsoft.com/library/dd363565.aspx).  
  
### <a name="microsoft-sql-server"></a>Microsoft SQL Server  
 SQL Server, Microsoft Gemisi veritabanı teklifidir. SQL Server 2016 performansından, Gelişmiş Güvenlik ve zengin, tümleşik raporlama ve analiz sunar. Farklı amaçlarla tasarlanmış çeşitli sürümlerinde sunulur: ile yüksek düzeyde ölçeklenebilir, yüksek performanslı iş analytics, tek bir bilgisayar üzerinde kullanılacak. SQL Server Express'in tam özellikli, bir yeniden dağıtımı ve ekleme için tasarlanmış bir SQL Server sürümüdür.  LocalDB, SQL Server, işlem yapılandırma gerektirmez ve uygulamanızın işlemde çalışan Express, Basitleştirilmiş bir sürümüdür. Ürünlerden biri veya her ikisi indirebileceğiniz [SQL Server Express indirme sayfasına](https://www.microsoft.com/en-us/server-cloud/Products/sql-server-editions/sql-server-express.aspx).    Bu bölümde yer alan SQL örnekler birçoğu, SQL Server LocalDB kullanın. SQL Server Management Studio (SSMS) Visual Studio SQL Server Nesne Gezgini içinde sağlanan değerinden daha fazla işlevselliği olan bir tek başına veritabanı yönetimi uygulamasıdır. SSMS kullanarak önceki bağlantıdan alabilirsiniz.  
  
### <a name="oracle"></a>Oracle  
 Oracle veritabanından ücretli veya ücretsiz bir sürümü indirebilirsiniz [Oracle teknolojisi ağ](http://www.oracle.com/technetwork/database/enterprise-edition/downloads/index-092322.html) sayfası. Entity Framework ve TableAdapter bağdaştırıcıları için tasarım zamanı desteği için ihtiyacınız olacak [Oracle Developer Tools for Visual Studio'nun](http://www.oracle.com/technetwork/developer-tools/visual-studio/overview/index.html). Oracle anlık istemci gibi diğer resmi Oracle ürünleri için NuGet Paket Yöneticisi aracılığıyla kullanılabilir.  Oracle örnek şemaları talimatları kullanarak indirebilirsiniz [Oracle çevrimiçi belgeleri](http://docs.oracle.com/cd/E11882_01/server.112/e10831/toc.htm).  
  
### <a name="mysql"></a>MySQL  
 MySQL, kurumlar ve Web siteleri yaygın olarak kullanılan bir popüler açık kaynak veritabanı sistemidir. Visual Studio ve ilgili ürünler için MySQL yüklemeleri için MySQL ndadır [Windows üzerinde MySQL](http://www.mysql.com/why-mysql/windows/).  Üçüncü taraflara, çeşitli Visual Studio uzantıları ve MySQL için tek başına Yönetim uygulamaları sunar. NuGet Paket Yöneticisi'nde tekliflerini göz atabilirsiniz (**Araçları** > **NuGet Paket Yöneticisi** > **çözüm için NuGet paketlerini Yönet**) .  
  
### <a name="postgresql"></a>PostgreSQL  
 PostgreSQL, ücretsiz, açık kaynaklı bir nesne ilişkisel veritabanı sistemidir. Windows üzerinde yüklemek için buradan indirebilirsiniz [PostgreSQL indirme sayfası](http://www.postgresql.org/download/windows/).  Ayrıca, kaynak kodundan PostgreSQL oluşturabilirsiniz.  PostgreSQL çekirdek sistem C dili arabirimi içerir. Çok sayıda üçüncü taraflara, .NET uygulamalarından kullanılarak PostgreSQL için NuGet paketlerini sağlar.  NuGet Paket Yöneticisi'nde tekliflerini göz atabilirsiniz (**Araçları** > **NuGet Paket Yöneticisi** > **çözüm için NuGet paketlerini Yönet**) . Belki de en popüler paketi tarafından sağlanan [npgsql.org](http://www.npgsql.org).  
  
### <a name="sqlite"></a>SQLite  
 SQLite uygulamanın kendi işlemde çalışan katıştırılmış bir SQL veritabanı altyapısıdır. Buradan indirebileceğiniz [SQLite indirme sayfası](http://www.sqlite.org/download.html). SQLite için çok sayıda üçüncü taraf NuGet paketlerini de mevcuttur. NuGet Paket Yöneticisi'nde tekliflerini göz atabilirsiniz (**Araçları** > **NuGet Paket Yöneticisi** > **çözüm için NuGet paketlerini Yönet**) .  
  
### <a name="firebird"></a>Firebird  
 Firebird bir açık kaynak SQL veritabanı sistemidir. Buradan indirebileceğiniz [Firebird indirme sayfası](http://firebirdsql.org/en/downloads/). Bir ADO.NET veri sağlayıcı, NuGet Paket Yöneticisi aracılığıyla kullanılabilir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [SQL Server ve bileşenlerinin sürümünü ve belirleme](http://support.microsoft.com/kb/321185)

