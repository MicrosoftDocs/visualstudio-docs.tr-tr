---
title: 'Nasıl yapılır: örnek veritabanları yükleme | Microsoft Docs'
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
- sample databases, Adventure Works
- data [Visual Studio], sample databases
- sample databases, Northwind
- Northwind sample database
- Adventure Works sample database
ms.assetid: ed1291f6-604c-4972-ae22-0345c6dea12e
caps.latest.revision: 56
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: d3ffe88fb54da26468ca510a2f1a7ab6170d88db
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49881728"
---
# <a name="how-to-install-sample-databases"></a>Nasıl Yapılır: Örnek Veritabanları Yükleme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Birçok veri örneği, Northwind, Pubs, AdventureWorks örnek veritabanlarına bağlanma yeteneğini gerektirir. Yükleme ve bu veritabanları için aşağıdaki yordamları kullanarak bağlanın.  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
## <a name="installing-databases"></a>Veritabanlarını yükleme  
 Birçok veri örneği, web sitelerinden yüklenebilen örnek veritabanlarının kullanılabilirliğini gerektirir. Örnek veritabanları AdventureWorks, Northwind ve Pubs veritabanlarını içerir.  
  
#### <a name="to-install-the-northwind-and-pubs-sample-databases-for-sql-server"></a>SQL Server için Northwind ve Pubs örnek veritabanlarını yüklemek için  
  
1.  Git [Northwind ve Pubs örnek veritabanları](http://go.microsoft.com/fwlink?linkid=64296) web sitesi.  
  
2.  İndirin ve yükleyiciyi çalıştırın.  
  
     Yükleyici bir klasör ekler **SQL Server 2000 Sample Databases** bilgisayarınızın kök klasörüne. (Örneğin: **C:\SQL Server 2000 Sample Databases**).  
  
3.  SQL komut dosyasını istediğiniz veritabanı Northwind ya da Pubs için bulun.  
  
    > [!WARNING]
    >  . MDF veritabanı dosyası, veritabanını oluşturmak için betik kullanmak en iyisidir, SQL Server'ın geçerli sürümlerinde kullanabileceğiniz bir biçime kolayca dönüştürülemez.  
  
4.  İçinde **Sunucu Gezgini**, veritabanını yüklemek istediğiniz bir SQL Server örneğine bir bağlantı oluşturun. Kullanmak istediğiniz belirli bir SQL Server yoksa, Visual Studio ile otomatik olarak yüklenen veritabanı kullanabilirsiniz. Bunu yapmak için belirtin `(localdb)\v11.0` sunucu adı olarak.  
  
     Bağlantı oluşturmak için aşağıdaki adımları izleyin.  
  
    ###### <a name="to-create-a-connection-to-an-instance-of-sql-server"></a>SQL Server örneğine bir bağlantı oluşturmak için  
  
    1.  İçinde **Sunucu Gezgini**, kısayol menüsünü açın **veri bağlantıları** düğümünü seçip **Bağlantı Ekle**.  
  
         **Bağlantı Ekle** iletişim kutusu görüntülenir.  
  
    2.  Northwind ya da Pubs veritabanı oluşturmak istediğiniz SQL Server adını girin ya da (localdb) \v11.0 girin.  
  
    3.  Altında **bir veritabanı adı seçin veya girin**, örneğin, tempdb listeden herhangi bir veritabanı seçin.  
  
    4.  Seçin **Test Bağlantısı** her şeyin çalıştığını doğrulamak için düğmesine ve ardından **Tamam** düğmesi.  
  
         Yeni bir bağlantı düğümü görünür **Sunucu Gezgini**.  
  
5.  Sunucunuzun bağlantı düğümünün kısayol menüsünde seçip **yeni sorgu** düğmesi.  
  
     Bir düzenleyici penceresi açılır ve bir boş .sql komut dosyasını gösterir.  
  
6.  İnstnwnd.sql ya da instpubs.sql içeriklerini Düzenleyici penceresine yapıştırın.  
  
7.  Sorgu yürütme düğmesini (açık yeşil üçgeni simgesine tıklayın Sorgu penceresinin sağ).  
  
     Sorgu başarılı olursa, ileti **Komut başarıyla tamamlandı** görünür. Başka bir deyişle, Northwind ya da pubs veritabanı oluşturuldu.  
  
     Hala örnek veritabanına bir bağlantı eklemek gerekir. İçinde **Sunucu Gezgini**, kısayol menüsünü açın **veri bağlantıları** düğümünü seçip **Bağlantı Ekle**.  
  
8.  Aynı veritabanı önce ancak bu kez, Select altında seçtiğiniz sunucusu veya veritabanı adı girin seçin, Northwind ya da pubs veritabanı seçin ve seçin **Tamam** düğmesi.  
  
     Yeni bir düğüm, örnek veritabanı için veri bağlantıları altında görünür.  
  
9. Düzenleyici penceresini kapatın ve sorgu dosyasını kaydetmek istemediğiniz onaylayın. Veritabanını oluşturduktan sonra veritabanı oluşturma betiği kaydetmek gerekli değildir.  
  
#### <a name="to-install-the-adventureworks-sample-databases"></a>AdventureWorks örnek veritabanlarını yüklemek için  
  
-   AdventureWorks örnek veritabanlarını indirme [CodePlex Web site](http://go.microsoft.com/fwlink/?linkid=87843).  
  
#### <a name="to-install-the-northwind-sample-database-for-microsoft-access"></a>Microsoft Access için Northwind örnek veritabanını yüklemek için  
  
1. Microsoft Access 2010 veya sonraki sürümlerde, Northwind için çevrimiçi şablonlar arayın ve seçin **Desktop Northwind 2007 örnek veritabanına**.  
  
2. Microsoft Access içinde veritabanı dosyasını Northwind.accdb kaydedin.  
  
   Access veritabanları için yeni uzantı. accdb'dir. Bkz: [Microsoft Access 2010 ile veri programlama](http://msdn.microsoft.com/library/office/ff965871.aspx). Access'i kullanarak Northwind veritabanına bağlanmak için bkz: [nasıl yapılır: Northwind veritabanına bağlanmak](../data-tools/how-to-connect-to-the-northwind-database.md).  
  
## <a name="net-framework-security"></a>.NET Framework Güvenliği  
 Örnek veritabanları yalnızca gösterim amaçlıdır ve mutlaka en iyi güvenlik yöntemlerini ortaya koymaz.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [SQL Server ve bileşenlerinin sürümünü ve belirleme](http://support.microsoft.com/kb/321185)   
 [Bir tasarımcı kullanarak bir SQL veritabanı oluşturma](../data-tools/create-a-sql-database-by-using-a-designer.md)   
 [Nasıl yapılır: Northwind veritabanına bağlanma](../data-tools/how-to-connect-to-the-northwind-database.md)