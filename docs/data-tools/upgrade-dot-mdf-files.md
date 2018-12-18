---
title: .mdf dosyalarını yükseltme
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Express
- SQL Server LocalDB
- LocalDB
- SQLEXPRESS
- upgrading SQLExpress to SQLExpress
- upgrading to LocalDB
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 875208d068c791c0238c110ea0e83b04e18348fc
ms.sourcegitcommit: d9e4ea95d0ea70827de281754067309a517205a1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/29/2018
ms.locfileid: "37117946"
---
# <a name="upgrade-mdf-files"></a>.mdf dosyalarını yükseltme

Bu konuda bir veritabanı dosyası yükseltmek için seçenekler açıklanmaktadır (*.mdf*) Visual Studio'nun daha yeni bir sürümünü yükledikten sonra. Yönergeler için aşağıdaki görevleri içerir:

- SQL Server Express LocalDB, yeni bir sürümünü kullanmak için bir veritabanı dosyası yükseltme

- SQL Server Express, yeni bir sürümünü kullanmak için bir veritabanı dosyası yükseltme

- Visual Studio'da bir veritabanı dosyası ile çalışır ancak SQL Server Express LocalDB veya daha eski bir sürümü ile uyumluluk koru

- SQL Server Express varsayılan veritabanı altyapısı olun

Veritabanı dosyasını içeren bir projeyi açmak için Visual Studio'yu kullanabilirsiniz (*.mdf*) SQL Server Express LocalDB veya daha eski bir sürümü kullanılarak oluşturuldu. Ancak, projenizi Visual Studio'da geliştirmeye devam etmek için bu sürüm veya SQL Server Express LocalDB Visual Studio ile aynı makinede yüklü olmalıdır veya veritabanı dosyası yükseltmeniz gerekir. Veritabanı dosyasını yükseltirseniz, SQL Server Express veya yerel veritabanı eski sürümlerini kullanarak erişimi olmayacaktır.

Ayrıca dosya sürümü SQL Server Express veya şu an yüklü olan yerel veritabanı örneği ile uyumlu değilse, önceki bir SQL Server Express veya yerel veritabanı sürümü ile oluşturulmuş bir veritabanı dosyası yükseltme istenebilir. Sorunu çözmek için Visual Studio dosya yükseltme isteyip istemediğinizi sorar.

> [!IMPORTANT]
> Yükseltmeden önce veritabanı dosyasını yedeklemenizi öneririz.

> [!WARNING]
> Yükseltirseniz, bir *.mdf* LocalDB 2014'te (V12) 32 bit LocalDB 2016 (V13) ya da daha sonra oluşturulan dosya, edemeyecek dosya LocalDB 32-bit sürümünü yeniden açmak.

Bir veritabanını yükseltmeden önce aşağıdaki ölçütleri göz önünde bulundurun:

-   Eski bir sürümü ve Visual Studio'nun daha yeni sürümünü projenizde üzerinde çalışmak isterseniz yükseltmeyin.

-   SQL Server Express LocalDB yerine kullanan ortamlarda, uygulamanızın kullanılacaksa yükseltmeyin.

-   Uzak bağlantılar, uygulamanızın kullanıyorsa, yerel veritabanı kabul etmez çünkü yükseltmeyin.

-   Uygulamanızı Internet Information Services (IIS) üzerinde dayalıysa yükseltmeyin.

-   Veritabanı uygulamaları sanal ortamda test etmek istediğiniz, ancak bir veritabanını yönetmek istemediğiniz yükseltmeyi göz önünde bulundurun.

### <a name="to-upgrade-a-database-file-to-use-the-localdb-version"></a>Yerel veritabanı sürümü kullanmak için bir veritabanı dosyası yükseltmek için

1.  İçinde **Sunucu Gezgini**seçin **veritabanına bağlan** düğmesi.

2.  İçinde **Bağlantı Ekle** iletişim kutusunda, aşağıdaki bilgileri belirtin:

    -   **Veri kaynağı**: `Microsoft SQL Server (SqlClient)`

    -   **Sunucu adı**:

        -   Varsayılan sürümü kullanmak için: `(localdb)\MSSQLLocalDB`.  Bu ProjectV12 veya ProjectV13, Visual Studio hangi sürümünün yüklü olduğundan ve ilk yerel veritabanı örneği oluşturulduğu bağlı olarak belirtir. **MSSQLLocalDB** düğümünde **SQL Server Nesne Gezgini** hangi sürümü, işaret etmesi gösterir.

        -   Belirli bir sürümü kullanmak için: `(localdb)\ProjectsV12` veya `(localdb)\ProjectsV13`, burada V12 LocalDB 2014 ve V13 LocalDB 2016.

    -   **Bir veritabanı dosyası ekleme**: birincil fiziksel yolunu *.mdf* dosya.

    -   **Mantıksal ad**: dosya ile kullanmak istediğiniz adı.

3.  Seçin **Tamam** düğmesi.

4.  İstendiğinde, seçin **Evet** dosya yükseltmek için düğmesi.

    Veritabanı yükseltilir LocalDB veritabanına eklenir ve artık yerel veritabanı, daha eski sürümü ile uyumlu değil.

SQL Server Express bir bağlantıyı bağlantı için kısayol menüsünü açarak ve ardından seçerek LocalDB kullanacak şekilde de değiştirebilirsiniz **değiştirmek bağlantı**. İçinde **değiştirmek bağlantı** iletişim kutusunda, sunucu adını değiştirmek `(LocalDB)\MSSQLLocalDB`. İçinde **Gelişmiş Özellikler** iletişim kutusunda, olduğundan emin olun **kullanıcı örneği** ayarlanır **False**.

### <a name="to-upgrade-a-database-file-to-use-the-sql-server-express-version"></a>SQL Server Express sürümü kullanmak için bir veritabanı dosyası yükseltmek için

1.  Veritabanı bağlantısı için kısayol menüsünden seçin **değiştirmek bağlantı**.

2.  İçinde **değiştirmek bağlantı** iletişim kutusunda **Gelişmiş** düğmesi.

3.  İçinde **Gelişmiş Özellikler** iletişim kutusunda **Tamam** sunucu adını değiştirmeden düğmesi.

    Veritabanı dosyası, SQL Server Express geçerli sürümüyle eşleşecek şekilde yükseltilir.

### <a name="to-work-with-the-database-in-visual-studio-but-retain-compatibility-with-sql-server-express"></a>Visual Studio'da veritabanıyla çalışır ancak SQL Server Express ile uyumluluğu korumak için

-   Visual Studio'da yükseltme yapmadan projeyi açın.

    -   Projeyi çalıştırmak için seçin **F5** anahtarı.

    -   Veritabanı düzenlemek için açın *.mdf* dosyasını **Çözüm Gezgini**ve düğümünü genişletin **Sunucu Gezgini** veritabanı ile çalışmak için.

### <a name="to-make-sql-server-express-the-default-database-engine"></a>SQL Server Express varsayılan veritabanı altyapısı yapma

1.  Menü çubuğunda seçin **Araçları** > **seçenekleri**.

2.  İçinde **seçenekleri** iletişim kutusunda, genişletin **veritabanı araçları** seçenekleri ve ardından **veri bağlantıları**.

3.  İçinde **SQL Server örneği adı** metin kutusunda, SQL Server Express veya kullanmak istediğiniz yerel veritabanı örneğinin adını belirtin. Adlandırılmış örneği değil belirtebilmeniz `.\SQLEXPRESS or (LocalDB)\MSSQLLocalDB`.

4.  Seçin **Tamam** düğmesi.

    SQL Server Express, uygulamalarınız için varsayılan veritabanı altyapısı olacaktır.

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio'da verilere erişime](accessing-data-in-visual-studio.md)