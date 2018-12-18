---
title: .Mdf dosyalarını yükseltme | Microsoft Docs
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
- SQL Server Express
- SQL Server LocalDB
- LocalDB
- SQLEXPRESS
- upgrading SQLExpress to SQLExpress
- upgrading to LocalDB
ms.assetid: 14ca6f76-f80e-4926-8020-3fee2d802b75
caps.latest.revision: 36
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: d71b38fe0d4aef412860a9dc65002c9b8d98c79c
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49812640"
---
# <a name="upgrade-mdf-files"></a>.mdf dosyalarını yükseltme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Bu konuda, Visual Studio'nun daha yeni bir sürümünü yükledikten sonra veritabanı dosyasına (.mdf) yükseltme seçenekleriniz açıklanmaktadır. Yönergeler için aşağıdaki görevleri içerir:  
  
- Yükseltme daha yeni bir SQL Server Express LocalDB sürümünü kullanmak için bir veritabanı dosyası  
  
- SQL Server Express daha yeni sürümü kullanmak için bir veritabanı dosyası yükseltme  
  
- Visual Studio'da bir veritabanı dosyası ile çalışır ancak veya SQL Server Express LocalDB daha eski bir sürümüyle uyumluluğu korumak  
  
- Varsayılan veritabanı altyapısı SQL Server Express olun  
  
  Visual Studio veya SQL Server Express LocalDB daha eski bir sürümü kullanılarak oluşturulmuş bir veritabanı dosyasını (.mdf) içeren bir proje açmak için kullanabilirsiniz. Ancak, projenizi Visual Studio'da geliştirmeye devam etmek için bu sürüm veya SQL Server Express LocalDB Visual Studio ile aynı makinede yüklü olmalıdır veya veritabanı dosyasını yükseltmeniz gerekir. Veritabanını yükseltirseniz, veya SQL Server Express LocalDB daha eski sürümleri kullanılarak erişmek mümkün olmayacaktır.  
  
  Ayrıca dosya sürümü SQL Server Express veya şu anda yüklü olan LocalDB örneği ile uyumlu değilse veya SQL Server Express LocalDB önceki bir sürümü ile oluşturulmuş bir veritabanı dosyanız yükseltme istenebilir. Sorunu çözmek için Visual Studio dosyayı yükseltme yapmanızı ister.  
  
> [!IMPORTANT]
>  Yükseltmeden önce veritabanı dosyasını yedekleyin öneririz.  
  
> [!WARNING]
>  LocalDB 2014 (V12) 32 bit LocalDB 2016'ya (V13) içinde oluşturulmuş bir .mdf dosyası yükseltirseniz, dosyayı açmayı LocalDB 32-bit sürümünde mümkün olmayacaktır.  Güncelleştirme 2'de LocalDB V13 yalnızca 64 bit ' dir.  
  
 Bir veritabanını yükseltmeden önce aşağıdaki ölçütleri dikkate alın:  
  
-   Projeniz daha eski bir sürümü hem de Visual Studio'nun daha yeni bir sürümü üzerinde çalışmak istiyorsanız yükseltmeyin.  
  
-   Uygulamanızı SQL Server Express LocalDB yerine kullanan ortamlarda kullanılacaksa yükseltmeyin.  
  
-   Uzak bağlantılar, uygulamanız kullanıyorsa LocalDB kabul etmez çünkü yükseltmeyin.  
  
-   Uygulamanızı Internet Information Services (IIS) üzerinde dayanıyorsa yükseltmeyin.  
  
-   Bir korumalı alan ortamında veritabanı uygulamalarını test etmek istediğiniz ancak bir veritabanını yönetmek istemiyorsanız, yükseltme yapmayı düşünün.  
  
### <a name="to-upgrade-a-database-file"></a>Bir veritabanını yükseltmek için  
  
1. İçinde **Sunucu Gezgini**seçin **veritabanına bağlan** düğmesi.  
  
2. İçinde **Bağlantı Ekle** iletişim kutusunda, aşağıdaki bilgileri belirtin:  
  
   -   **Veri kaynağı**: `Microsoft SQL Server (SqlClient)`  
  
   -   **Sunucu adı**:  
  
       -   Varsayılan sürümü kullanmak için: `(localdb)\MSSQLLocalDB`.  Bu ProjectV12 ya da ProjectV13, Visual Studio'nun hangi sürümünün yüklü olduğunu ve ilk LocalDB örneği oluşturulduğu bağlı olarak belirtin. **İfadesini MSSQLLocalDB** düğümünde **SQL Server Nesne Gezgini** hangi sürümün onu işaret etmesi gösterir.  
  
       -   Belirli bir sürümünü kullanmak için: `(localdb)\ProjectsV12` veya `(localdb)\ProjectsV13`, burada V12 LocalDB 2014 ve V13 LocalDB 2016.  
  
   -   **Bir veritabanı dosyası iliştirmek**: birincil .mdf dosyasının fiziksel yolu.  
  
   -   **Mantıksal ad**: dosya ile kullanmak istediğiniz adı.  
  
3. Seçin **Tamam** düğmesi.  
  
4. İstendiğinde, seçin **Evet** dosya yükseltme düğmesi.  
  
   Veritabanı yükseltilir LocalDB veritabanına ekli ve artık LocalDB eski sürümü ile uyumlu değil.  
  
   Bağlantı için kısayol menüsünü açarak ve ardından seçerek Localdb'yi kullanmak üzere bir SQL Server Express bağlantı değiştirebilirsiniz **değiştirme bağlantı**. İçinde **değiştirme bağlantı** iletişim kutusunda, sunucu adına değiştirin `(LocalDB)\MSSQLLocalDB`. İçinde **Gelişmiş Özellikler** iletişim kutusunda, emin **kullanıcı örneği** ayarlanır **False**.  
  
### <a name="to-upgrade-to-a-newer-version-of-sql-server-express"></a>SQL Server Express'in yeni bir sürüme yükseltmek için  
  
1. Veritabanı bağlantısı için kısayol menüsünden seçin **değiştirme bağlantı**.  
  
2. İçinde **değiştirme bağlantı** iletişim kutusunda **Gelişmiş** düğmesi.  
  
3. İçinde **Gelişmiş Özellikler** iletişim kutusunda **Tamam** sunucu adını değiştirmeden düğmesi.  
  
   Veritabanı dosyası geçerli SQL Server Express sürümüyle eşleşecek şekilde yükseltilir.  
  
### <a name="to-work-with-the-database-in-visual-studio-but-retain-compatibility-with-sql-server-express"></a>Visual Studio'da veritabanıyla çalışmaya, ancak SQL Server Express ile uyumluluğu korumak için  
  
-   Visual Studio'da, yükseltme yapmadan projeyi açın.  
  
    -   Projeyi çalıştırmak için F5 tuşunu seçin.  
  
    -   Veritabanı düzenlemek için .mdf dosyası açın **Çözüm Gezgini**ve düğümde genişletme **Sunucu Gezgini** , veritabanı ile çalışmak üzere.  
  
### <a name="to-make-sql-server-express-the-default-database-engine"></a>Varsayılan veritabanı altyapısı SQL Server Express yapma  
  
1. Menü çubuğunda, seçin **Araçları** > **seçenekleri**.  
  
2. İçinde **seçenekleri** iletişim kutusunda **veri Araçları** seçenekleri ve ardından **veri bağlantıları** düğümü.  
  
3. İçinde **SQL Server örneği adı** metin kutusunda, SQL Server Express veya kullanmak istediğiniz LocalDB örneğinin adını belirtin. Adlandırılmış bir örnek değil belirtebilmeniz `.\SQLEXPRESS or (localdb)\MSSQLLocalDB`.  
  
4. Seçin **Tamam** düğmesi.  
  
   SQL Server Express, uygulamalarınız için varsayılan veritabanı altyapısı olacaktır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Yerel verilere genel bakış](../data-tools/local-data-overview.md)   
 [İzlenecek yol: bir yerel veritabanı dosyası (Windows Forms) verilere bağlanma](../data-tools/walkthrough-connecting-to-data-in-a-local-database-file-windows-forms.md)

