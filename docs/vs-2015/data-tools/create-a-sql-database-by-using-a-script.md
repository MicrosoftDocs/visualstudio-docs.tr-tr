---
title: Bir komut dosyası kullanarak SQL veritabanı oluşturma | Microsoft Docs
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
ms.assetid: 36f913c0-f5a7-4831-83a0-baba721ac95c
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 13816c499002f8eaf81067aba8d1854d06a41445
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49266597"
---
# <a name="create-a-sql-database-by-using-a-script"></a>Bir komut dosyası kullanarak SQL veritabanı oluşturma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Bu izlenecek yolda, Visual Studio için örnek kod içeren küçük bir veritabanı oluşturmak için kullandığınız [ADO.NET kullanarak basit veri uygulaması oluşturma](../data-tools/create-a-simple-data-application-by-using-adonet.md).  
  
 **Bu konudaki**  
  
-   [Veritabanı şeması içeren bir komut dosyası oluşturma](../data-tools/create-a-sql-database-by-using-a-script.md#CreateScript)  
  
-   [Bir veritabanı projesi oluşturun ve şemayı içe aktarın](../data-tools/create-a-sql-database-by-using-a-script.md#CreateProject)  
  
-   [Veritabanı dağıtma](../data-tools/create-a-sql-database-by-using-a-script.md#DeployDatabase)  
  
## <a name="prerequisites"></a>Önkoşullar  
 Bu izlenecek yolu tamamlamak için SQL Server Express LocalDB veya başka bir SQL veritabanı, yüklü olmalıdır.  
  
##  <a name="CreateScript"></a> Veritabanı şeması içeren bir komut dosyası oluşturma  
  
#### <a name="to-create-a-script-from-which-you-can-import-a-schema"></a>Şema içe aktarabileceğiniz bir komut dosyası oluşturmak için  
  
1.  İçinde [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], menü çubuğunda, seçin **dosya** > **yeni** > **dosya**.  
  
     **Yeni dosya** iletişim kutusu görüntülenir.  
  
2.  İçinde **kategorileri** listesinden **genel**.  
  
3.  İçinde **şablonları** listesinden **Sql dosyası**ve ardından **açık** düğmesi.  
  
     Transact-SQL editor açılır.  
  
4.  Aşağıdaki Transact-SQL kodunu kopyalayın ve ardından Transact-SQL düzenleyicisine yapıştırın.  
  
    ```  
    PRINT N'Creating Sales...';  
    GO  
    CREATE SCHEMA [Sales]  
        AUTHORIZATION [dbo];  
    GO  
    PRINT N'Creating Sales.Customer...';  
    GO  
    CREATE TABLE [Sales].[Customer] (  
        [CustomerID]   INT           IDENTITY (1, 1) NOT NULL,  
        [CustomerName] NVARCHAR (40) NOT NULL,  
        [YTDOrders]    INT           NOT NULL,  
        [YTDSales]     INT           NOT NULL  
    );  
    GO  
    PRINT N'Creating Sales.Orders...';  
    GO  
    CREATE TABLE [Sales].[Orders] (  
        [CustomerID] INT      NOT NULL,  
        [OrderID]    INT      IDENTITY (1, 1) NOT NULL,  
        [OrderDate]  DATETIME NOT NULL,  
        [FilledDate] DATETIME NULL,  
        [Status]     CHAR (1) NOT NULL,  
        [Amount]     INT      NOT NULL  
    );  
    GO  
    PRINT N'Creating Sales.Def_Customer_YTDOrders...';  
    GO  
    ALTER TABLE [Sales].[Customer]  
        ADD CONSTRAINT [Def_Customer_YTDOrders] DEFAULT 0 FOR [YTDOrders];  
    GO  
    PRINT N'Creating Sales.Def_Customer_YTDSales...';  
    GO  
    ALTER TABLE [Sales].[Customer]  
        ADD CONSTRAINT [Def_Customer_YTDSales] DEFAULT 0 FOR [YTDSales];  
    GO  
    PRINT N'Creating Sales.Def_Orders_OrderDate...';  
    GO  
    ALTER TABLE [Sales].[Orders]  
        ADD CONSTRAINT [Def_Orders_OrderDate] DEFAULT GetDate() FOR [OrderDate];  
    GO  
    PRINT N'Creating Sales.Def_Orders_Status...';  
    GO  
    ALTER TABLE [Sales].[Orders]  
        ADD CONSTRAINT [Def_Orders_Status] DEFAULT 'O' FOR [Status];  
    GO  
    PRINT N'Creating Sales.PK_Customer_CustID...';  
    GO  
    ALTER TABLE [Sales].[Customer]  
        ADD CONSTRAINT [PK_Customer_CustID] PRIMARY KEY CLUSTERED ([CustomerID] ASC) WITH (ALLOW_PAGE_LOCKS = ON, ALLOW_ROW_LOCKS = ON, PAD_INDEX = OFF, IGNORE_DUP_KEY = OFF, STATISTICS_NORECOMPUTE = OFF);  
    GO  
    PRINT N'Creating Sales.PK_Orders_OrderID...';  
    GO  
    ALTER TABLE [Sales].[Orders]  
        ADD CONSTRAINT [PK_Orders_OrderID] PRIMARY KEY CLUSTERED ([OrderID] ASC) WITH (ALLOW_PAGE_LOCKS = ON, ALLOW_ROW_LOCKS = ON, PAD_INDEX = OFF, IGNORE_DUP_KEY = OFF, STATISTICS_NORECOMPUTE = OFF);  
    GO  
    PRINT N'Creating Sales.FK_Orders_Customer_CustID...';  
    GO  
    ALTER TABLE [Sales].[Orders]  
        ADD CONSTRAINT [FK_Orders_Customer_CustID] FOREIGN KEY ([CustomerID]) REFERENCES [Sales].[Customer] ([CustomerID]) ON DELETE NO ACTION ON UPDATE NO ACTION;  
    GO  
    PRINT N'Creating Sales.CK_Orders_FilledDate...';  
    GO  
    ALTER TABLE [Sales].[Orders]  
        ADD CONSTRAINT [CK_Orders_FilledDate] CHECK ((FilledDate >= OrderDate) AND (FilledDate < '01/01/2020'));  
    GO  
    PRINT N'Creating Sales.CK_Orders_OrderDate...';  
    GO  
    ALTER TABLE [Sales].[Orders]  
        ADD CONSTRAINT [CK_Orders_OrderDate] CHECK ((OrderDate > '01/01/2005') and (OrderDate < '01/01/2020'));  
    GO  
    PRINT N'Creating Sales.uspCancelOrder...';  
    GO  
    CREATE PROCEDURE [Sales].[uspCancelOrder]  
    @OrderID INT  
    AS  
    BEGIN  
    DECLARE @Delta INT, @CustomerID INT  
    BEGIN TRANSACTION  
        SELECT @Delta = [Amount], @CustomerID = [CustomerID]  
         FROM [Sales].[Orders] WHERE [OrderID] = @OrderID;  
  
    UPDATE [Sales].[Orders]  
       SET [Status] = 'X'  
    WHERE [OrderID] = @OrderID;  
  
    UPDATE [Sales].[Customer]  
       SET  
       YTDOrders = YTDOrders - @Delta  
        WHERE [CustomerID] = @CustomerID  
    COMMIT TRANSACTION  
    END  
    GO  
    PRINT N'Creating Sales.uspFillOrder...';  
    GO  
    CREATE PROCEDURE [Sales].[uspFillOrder]  
    @OrderID INT, @FilledDate DATETIME  
    AS  
    BEGIN  
    DECLARE @Delta INT, @CustomerID INT  
    BEGIN TRANSACTION  
        SELECT @Delta = [Amount], @CustomerID = [CustomerID]  
         FROM [Sales].[Orders] WHERE [OrderID] = @OrderID;  
  
    UPDATE [Sales].[Orders]  
       SET [Status] = 'F',  
           [FilledDate] = @FilledDate  
    WHERE [OrderID] = @OrderID;  
  
    UPDATE [Sales].[Customer]  
       SET  
       YTDSales = YTDSales + @Delta  
        WHERE [CustomerID] = @CustomerID  
    COMMIT TRANSACTION  
    END  
    GO  
    PRINT N'Creating Sales.uspNewCustomer...';  
    GO  
    CREATE PROCEDURE [Sales].[uspNewCustomer]  
    @CustomerName NVARCHAR (40),  
    @CustomerID INT OUTPUT  
    AS  
    BEGIN  
    INSERT INTO [Sales].[Customer] (CustomerName) VALUES (@CustomerName);  
    SET @CustomerID = SCOPE_IDENTITY();  
    RETURN @@ERROR  
    END  
    GO  
    PRINT N'Creating Sales.uspPlaceNewOrder...';  
    GO  
    CREATE PROCEDURE [Sales].[uspPlaceNewOrder]  
    @CustomerID INT, @Amount INT, @OrderDate DATETIME, @Status CHAR (1)='O'  
    AS  
    BEGIN  
    DECLARE @RC INT  
    BEGIN TRANSACTION  
    INSERT INTO [Sales].[Orders] (CustomerID, OrderDate, FilledDate, Status, Amount)   
         VALUES (@CustomerID, @OrderDate, NULL, @Status, @Amount)  
    SELECT @RC = SCOPE_IDENTITY();  
    UPDATE [Sales].[Customer]  
       SET  
       YTDOrders = YTDOrders + @Amount  
        WHERE [CustomerID] = @CustomerID  
    COMMIT TRANSACTION  
    RETURN @RC  
    END  
    GO  
    CREATE PROCEDURE [Sales].[uspShowOrderDetails]  
    @CustomerID INT=0  
    AS  
    BEGIN  
    SELECT [C].[CustomerName], CONVERT(date, [O].[OrderDate]), CONVERT(date, [O].[FilledDate]), [O].[Status], [O].[Amount]  
      FROM [Sales].[Customer] AS C  
      INNER JOIN [Sales].[Orders] AS O  
         ON [O].[CustomerID] = [C].[CustomerID]  
      WHERE [C].[CustomerID] = @CustomerID  
    END  
    GO  
    ```  
  
5.  Menü çubuğunda, seçin **dosya** > **SqlQuery_1.sql farklı**.  
  
     **Dosyayı farklı Kaydet** iletişim kutusu görüntülenir.  
  
6.  İçinde **dosya adı** kutusuna `SampleImportScript.sql`, burada, dosyayı kaydedin ve ardından konum Not **Kaydet** düğmesi.  
  
7.  Menü çubuğunda, seçin **dosya** > **çözümü Kapat**.  
  
     Ardından, bir veritabanı projesi oluşturun ve ardından şemayı oluşturduğunuz komut dosyasından içe aktarın.  
  
##  <a name="CreateProject"></a> Bir veritabanı projesi oluşturun ve şemayı içe aktarın  
  
#### <a name="to-create-a-database-project"></a>Veritabanı projesi oluşturmak için  
  
1.  Menü çubuğunda, seçin **dosya** > **yeni** > **proje**.  
  
     **Yeni proje** iletişim kutusu görüntülenir.  
  
2.  Altında **yüklü**, genişletme **şablonları** düğümünü genişletin **diğer diller** düğümünü **SQL Server** kategorisi ve ardından seçin **SQL Server veritabanı projesi** şablonu.  
  
    > [!NOTE]
    >  **Diğer diller** düğümü, Visual Studio'nun tüm yüklemelerinde görünmez.  
  
3.  İçinde **adı** kutusuna `Small Database`.  
  
4.  Seçin **çözüm için dizin oluştur** zaten seçili değilse, onay kutusu.  
  
5.  NET **kaynak denetimine Ekle** zaten temizlenmiş ve ardından değilse, onay kutusunu **Tamam** düğmesi.  
  
     Veritabanı projesi oluşturulur ve görünür **Çözüm Gezgini**.  
  
     Ardından, veritabanı şemasını komut dosyasından içe aktarın.  
  
#### <a name="to-import-a-database-schema-from-a-script"></a>Veritabanı şemasını komut dosyasından içeri aktarmak için  
  
1.  Menü çubuğunda, seçin **proje** > **alma** > **betik**.  
  
2.  Üzerinde **Hoş Geldiniz** sayfasında metni gözden geçirin ve ardından **sonraki** düğmesi.  
  
3.  Seçin **tek dosya** seçenek düğmesini ve ardından **Gözat** düğmesi.  
  
     **SQL komut dosyasını içeri aktar** iletişim kutusu görüntülenir.  
  
4.  Sampleımportscript.SQL dosyasını kaydettiğiniz klasörü açın, dosyayı seçin ve ardından **açık** düğmesi.  
  
5.  Seçin **son** kapatmak için düğme **SQL komut dosyasını içeri aktar** iletişim kutusu.  
  
     Komut dosyası içe aktarılır ve komut dosyasını tanımlayan nesneler veritabanı projenize eklenir.  
  
6.  Özeti gözden geçirin ve ardından **son** kapatmak için düğme **alma SQL betik dosyası** iletişim kutusu.  
  
7.  İçinde **Çözüm Gezgini**, Satışlar, betikler ve güvenlik'i genişletin, projenizin klasörler ve bunların .sql dosyaları içerdiğini doğrulayın.  
  
8.  İçinde **SQL Server Nesne Gezgini**, veritabanı altında göründüğünü doğrulayın **projeleri** düğümü.  
  
     Bu noktada, veritabanı, tablolar ve depolanmış yordamlar gibi sistem nesnelerini yalnızca içerir. Veritabanını dağıttıktan sonra kullanıcı tablolarını ve betiğin tanımlandığı saklı yordamları içerecektir.  
  
##  <a name="DeployDatabase"></a> Veritabanı dağıtma  
 Bastığınızda **F5** anahtar dağıttığınızda (veya yayımlama) bir LocalDB veritabanına varsayılan veritabanı. Proje için Özellikler sayfasını açarak veritabanını farklı bir konuma dağıtabilirsiniz seçerek **hata ayıklama** sekmesini ve sonra bağlantı dizesini değiştirerek.

