---
title: 'İzlenecek yol: Güncelleştirme oluşturma saklı yordamlar için Northwind Customers tablosunu | Microsoft Docs'
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
- Northwind sample database
- stored procedures [Visual Studio]
- O/R Designer, stored procedures
ms.assetid: 6fd9e7e0-6862-44d3-9710-acc5a72d4ffd
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: 4972c1341490f78bba03bdd390ac13903c55be84
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49204054"
---
# <a name="walkthrough-creating-update-stored-procedures-for-the-northwind-customers-table"></a>İzlenecek yol: Northwind Müşterileri için Saklı Yordamları Güncelleştirme Tablosu Oluşturma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bazı Yardım konuları [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] belgeleri ek saklı yordamlar Northwind örnek veritabanındaki Müşteriler tablosunda (ekleme, güncelleştirme ve silme) veri güncelleştirmelerini gerçekleştirmek için gerekli.  
  
 Bu ek oluşturma yordamları için Northwind örnek veritabanı içinde depolanan için sunduğumuz yönergeleri sağlar. [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].  
  
 Sonraki adımlar bölümünde bu konunun ilerleyen bölümlerinde, bu ek saklı yordamlar ile çalışmaya nasıl gösteren konulara bağlantılar sağlar.  
  
 Bu kılavuz boyunca aşağıdaki görevlerin nasıl gerçekleştirileceğini öğreneceksiniz:  
  
-   Northwind örnek veritabanıyla kurulan veri bağlantısı oluşturun.  
  
-   Saklı yordamları oluştur.  
  
## <a name="prerequisites"></a>Önkoşullar  
 Bu kılavuzu tamamlamak için gerekenler:  
  
-   Northwind örnek veritabanındaki SQL Server sürümünü erişim. Daha fazla bilgi için [nasıl yapılır: örnek veritabanları yükleme](../data-tools/how-to-install-sample-databases.md).  
  
## <a name="connecting-to-the-northwind-database"></a>Northwind veritabanına bağlanma  
 Bu izlenecek yol Northwind veritabanının SQL Server sürümü gerektirir. Aşağıdaki yordam, veri bağlantısı oluşturma için yönergeler sağlar.  
  
> [!NOTE]
>  Northwind veritabanına bir veri bağlantısı zaten varsa, saklı yordamlar oluşturma sonraki bölümüne gidebilirsiniz.  
  
#### <a name="to-create-a-data-connection-to-the-northwind-sql-server-database"></a>SQL Server Northwind veritabanına bir veri bağlantısı oluşturmak için  
  
1.  Üzerinde **görünümü** menüsünü tıklatın **Sunucu Gezgini**/**veritabanı Gezgini**.  
  
2.  Sağ **veri bağlantıları** tıklatıp **Bağlantı Ekle**.  
  
3.  İçinde **veri kaynağı Seç** iletişim kutusu, tıklayın **Microsoft SQL Server**ve ardından **Tamam**.  
  
     Varsa **Bağlantı Ekle** iletişim kutusu açılır ve **veri kaynağı** değil **Microsoft SQL Server (SqlClient)**, tıklayın **değişiklik** açmak için **Veri kaynağını seç/Değiştir** iletişim kutusu, tıklayın **Microsoft SQL Server**ve ardından **Tamam**.  
  
4.  ' A tıklayın bir **sunucu adı** açılan liste veya Northwind veritabanının bulunduğu sunucunun adını yazın.  
  
5.  Veritabanı veya uygulama gereksinimlerinize bağlı olarak, ya da tıklayın **Windows kimlik doğrulaması kullanmak** veya SQL Server çalıştıran bilgisayarda oturum açmak için belirli bir kullanıcı adı ve parola kullanın (**SQL Server kimlik doğrulaması**).  
  
6.  Northwind veritabanındaki tıklayın **bir veritabanı adı seçin veya girin** listesi.  
  
7.  **Tamam**'ı tıklatın.  
  
     Veri bağlantısı eklenir **Sunucu Gezgini**/**veritabanı Gezgini**.  
  
## <a name="creating-the-stored-procedures"></a>Saklı yordamlar oluşturma  
 Saklı yordamları kullanarak Northwind veritabanına karşı sağlanan SQL komut dosyasını çalıştırarak oluşturun [Visual veritabanı araçları](http://msdn.microsoft.com/en-us/6b145922-2f00-47db-befc-bf351b4809a1) bulunan **Sunucu Gezgini** /  **Veritabanı Gezgini**.  
  
#### <a name="to-create-the-stored-procedures-by-using-a-sql-script"></a>Saklı yordamları, SQL komut dosyası kullanarak oluşturmak için  
  
1.  Northwind veritabanındaki genişletin **Sunucu Gezgini**/**veritabanı Gezgini**.  
  
2.  Sağ **saklı yordamlar** düğüm ve tıklatın **yeni saklı yordam Ekle**.  
  
3.  Kod düzenleyicisine, aşağıdaki kodu yapıştırın değiştirerek `CREATE PROCEDURE` şablonu:  
  
    ```  
    IF EXISTS (SELECT * FROM sysobjects WHERE name = 'SelectCustomers' AND user_name(uid) = 'dbo')  
        DROP PROCEDURE dbo.[SelectCustomers]  
    GO  
  
    CREATE PROCEDURE dbo.[SelectCustomers]  
    AS  
        SET NOCOUNT ON;  
    SELECT CustomerID, CompanyName, ContactName, ContactTitle, Address, City, Region, PostalCode, Country, Phone, Fax FROM dbo.Customers  
    GO  
  
    IF EXISTS (SELECT * FROM sysobjects WHERE name = 'InsertCustomers' AND user_name(uid) = 'dbo')  
        DROP PROCEDURE dbo.InsertCustomers  
    GO  
  
    CREATE PROCEDURE dbo.InsertCustomers  
    (  
        @CustomerID nchar(5),  
        @CompanyName nvarchar(40),  
        @ContactName nvarchar(30),  
        @ContactTitle nvarchar(30),  
        @Address nvarchar(60),  
        @City nvarchar(15),  
        @Region nvarchar(15),  
        @PostalCode nvarchar(10),  
        @Country nvarchar(15),  
        @Phone nvarchar(24),  
        @Fax nvarchar(24)  
    )  
    AS  
        SET NOCOUNT OFF;  
    INSERT INTO [dbo].[Customers] ([CustomerID], [CompanyName], [ContactName], [ContactTitle], [Address], [City], [Region], [PostalCode], [Country], [Phone], [Fax]) VALUES (@CustomerID, @CompanyName, @ContactName, @ContactTitle, @Address, @City, @Region, @PostalCode, @Country, @Phone, @Fax);  
  
    SELECT CustomerID, CompanyName, ContactName, ContactTitle, Address, City, Region, PostalCode, Country, Phone, Fax FROM Customers WHERE (CustomerID = @CustomerID)  
    GO  
  
    IF EXISTS (SELECT * FROM sysobjects WHERE name = 'UpdateCustomers' AND user_name(uid) = 'dbo')  
        DROP PROCEDURE dbo.UpdateCustomers  
    GO  
  
    CREATE PROCEDURE dbo.UpdateCustomers  
    (  
        @CustomerID nchar(5),  
        @CompanyName nvarchar(40),  
        @ContactName nvarchar(30),  
        @ContactTitle nvarchar(30),  
        @Address nvarchar(60),  
        @City nvarchar(15),  
        @Region nvarchar(15),  
        @PostalCode nvarchar(10),  
        @Country nvarchar(15),  
        @Phone nvarchar(24),  
        @Fax nvarchar(24),  
        @Original_CustomerID nchar(5)  
    )  
    AS  
        SET NOCOUNT OFF;  
    UPDATE [dbo].[Customers] SET [CustomerID] = @CustomerID, [CompanyName] = @CompanyName, [ContactName] = @ContactName, [ContactTitle] = @ContactTitle, [Address] = @Address, [City] = @City, [Region] = @Region, [PostalCode] = @PostalCode, [Country] = @Country, [Phone] = @Phone, [Fax] = @Fax WHERE (([CustomerID] = @Original_CustomerID));  
  
    SELECT CustomerID, CompanyName, ContactName, ContactTitle, Address, City, Region, PostalCode, Country, Phone, Fax FROM Customers WHERE (CustomerID = @CustomerID)  
    GO  
  
    IF EXISTS (SELECT * FROM sysobjects WHERE name = 'DeleteCustomers' AND user_name(uid) = 'dbo')  
        DROP PROCEDURE dbo.DeleteCustomers  
    GO  
  
    CREATE PROCEDURE dbo.DeleteCustomers  
    (  
        @Original_CustomerID nchar(5)  
    )  
    AS  
        SET NOCOUNT OFF;  
    DELETE FROM [dbo].[Customers] WHERE (([CustomerID] = @Original_CustomerID))  
    GO  
    ```  
  
4.  Kod Düzenleyicisi'nde tüm metni seçin, seçili metni sağ tıklayın ve tıklayın **Seçimi Çalıştır**.  
  
     SelectCustomers, InsertCustomers, UpdateCustomers ve DeleteCustomers saklı yordamlar için Northwind veritabanı oluşturulur.  
  
## <a name="next-steps"></a>Sonraki Adımlar  
 Saklı yordamları oluşturduğunuza göre nasıl bunlarla çalışılacağını gösteren aşağıdaki talimatlara deneyin:  
  
 [Nasıl yapılır: Güncelleştirme, ekleme ve silme işlemleri gerçekleştirmek için saklı yordamlar atama (O/R Tasarımcısı)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md)  
  
 [İzlenecek yol: LINQ to SQL sınıfları (O R Designer) oluşturma](http://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233)  
  
 [İzlenecek yol: Varlık sınıflarının ekleme, güncelleştirme ve silme davranışını özelleştirme](../data-tools/walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes.md)  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [LINQ to SQL araçlarını Visual Studio'da](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [LINQ to SQL](http://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655)   
 [Visual Studio'da verilere erişime](../data-tools/accessing-data-in-visual-studio.md)