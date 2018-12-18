---
title: "Nasıl yapılır: Northwind veritabanı'na bağlanma | Microsoft Docs"
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
- connections [Visual Studio], Northwind database
- Northwind sample database
ms.assetid: cc6cb79f-d035-41f8-b398-8d4a45922bfb
caps.latest.revision: 29
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: 3f64fa378029546f7a3126b324c282f6a91d7231
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49897640"
---
# <a name="how-to-connect-to-the-northwind-database"></a>Nasıl yapılır: Northwind Veritabanına Bağlanma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio kullanarak veritabanı uygulamaları oluşturmayı öğrenin gibi birçok örnek için ürün belgelerinde izlemek için Northwind veritabanına bağlanmak gerekir. Takip ettiğiniz örnek bağlı olarak, SQL Server'ı veya bir Microsoft Access veya SQL Server gibi bir veritabanı dosyası veritabanına bağlanırsınız.  
  
## <a name="creating-data-connections-to-the-northwind-database"></a>Northwind veritabanına veri bağlantıları oluşturma  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
#### <a name="to-create-a-data-connection-to-the-northwind-database-sql-server"></a>Northwind veritabanı (SQL Server) için bir veri bağlantısı oluşturmak için  
  
1. Üzerinde **görünümü** menüsünde seçin **Sunucu Gezgini**/**veritabanı Gezgini**.  
  
2. İçinde **Sunucu Gezgini**/**veritabanı Gezgini**, kısayol menüsünü açın **veri bağlantıları** ve **Add Connection**.  
  
    Seçtiğiniz sonra **Bağlantı Ekle**, ya da **veri kaynağı Seç** iletişim kutusu veya **Bağlantı Ekle** iletişim kutusu görüntülenir.  
  
3. Varsa **veri kaynağı Seç** iletişim kutusu görüntülenirse, seçin **Microsoft SQL Server**ve ardından **Tamam**.  
  
    Varsa **Bağlantı Ekle** iletişim kutusu görünür ve **veri kaynağı** değil **Microsoft SQL Server (SqlClient)**, seçin **değişiklik** açmak için düğmeyi **değişimi veri kaynağı** iletişim kutusunda **Microsoft SQL Server**ve ardından **Tamam** düğmesi.  
  
4. İçinde **sunucu adı** listesinde, Northwind veritabanının bulunduğu sunucunun adını belirtin.  
  
5. Sürümünüz SQL Server ve Northwind veritabanının gereksinimlerine bağlı olarak seçin ya da **Windows kimlik doğrulamasını kullan** veya **SQL Server kimlik doğrulamasını kullan** ve bir kullanıcı adı girin ve SQL Server çalıştıran bilgisayarda oturum açmak için parola.  
  
6. Northwind veritabanındaki seçin **bir veritabanı adı seçin veya girin** listesi.  
  
7. Seçin **Test Bağlantısı** Northwind veritabanı bağlantısını doğrulamak için.  
  
8. Seçin **Tamam**.  
  
    Bir veri bağlantısı Northwind veritabanına eklenir **Sunucu Gezgini**/**veritabanı Gezgini**.  
  
   Uzak bir SQL Server veritabanı örneğine bağlanma yanı sıra veritabanı içeren doğrudan gerçek dosyalarına da bağlanabilirsiniz. Bu, veritabanı dosyalarını doğrudan uygulamanın bir parçası bunlar burada dağıtılabilir projesine eklemenize olanak sağlar. Aşağıdaki yerel veritabanı dosyaları şu anda desteklenen: SQL Server Compact veritabanı dosyaları (.sdf) [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ve SQL Server Express veritabanı dosyaları (.mdf) ve Microsoft Access veritabanı dosyaları (.mdb veya .accdb).  
  
#### <a name="to-create-a-data-connection-to-the-northwind-databasesql-server-database-file-mdf"></a>Northwind veritabanına bir veri bağlantısı oluşturmak için: SQL Server veritabanı dosyasına (.mdf)  
  
1.  Üzerinde **görünümü** menüsünde seçin **Sunucu Gezgini**/**veritabanı Gezgini**.  
  
2.  İçinde **Sunucu Gezgini**/**veritabanı Gezgini**, kısayol menüsünü açın **veri bağlantıları** ve **Add Connection**.  
  
     Seçtiğiniz sonra **Bağlantı Ekle**, ya da **Bağlantı Ekle** iletişim kutusu veya **veri kaynağı Seç** iletişim kutusu görüntülenir.  
  
3.  Varsa **veri kaynağı Seç** iletişim kutusu görüntülenirse, seçin **Microsoft SQL Server veritabanı dosyası**ve ardından **Tamam**.  
  
4.  Varsa **Bağlantı Ekle** iletişim kutusu görüntülenirse, doğrulayın **veri kaynağı** ayarlanır **Microsoft SQL Server veritabanı dosyası (SqlClient)**. Bunun ayarlanmazsa **Microsoft SQL Server veritabanı dosyası (SqlClient)**, seçin **değişiklik** açmak için **değişimi veri kaynağı** iletişim kutusunda **Microsoft SQL Server veritabanı dosyası**ve ardından **Tamam** düğmesi.  
  
5.  Seçin **Gözat** içeren Northwind veritabanı .mdf dosyası bulunamıyor.  
  
6.  Sürümünüzü Northwind veritabanının gereksinimlerine bağlı olarak seçin **Windows kimlik doğrulamasını kullan** veya **SQL Server kimlik doğrulaması** ve kullanıcı adını ve oturum açmak için parola girin SQL Server çalıştıran bilgisayar.  
  
7.  Seçin **Tamam** düğmesi.  
  
     Bir veri bağlantısı Northwind veritabanına eklenir **Sunucu Gezgini**/**veritabanı Gezgini**.  
  
> [!NOTE]
>  [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] Northwind veritabanı dosyasını (.mdf) uygulanacak değişiklikler var. Bilgi için [nasıl yapılır: örnek veritabanları yükleme](../data-tools/how-to-install-sample-databases.md).  
  
#### <a name="to-create-a-data-connection-to-the-northwind-databaseaccess-database-file-mdb-or-accdb"></a>Northwind veritabanına bir veri bağlantısı oluşturmak için: Access veritabanı dosyası (.mdb veya .accdb)  
  
1.  Üzerinde **görünümü** menüsünde seçin **Sunucu Gezgini**/**veritabanı Gezgini**.  
  
2.  İçinde **Sunucu Gezgini**/**veritabanı Gezgini**, kısayol menüsünü açın **veri bağlantıları** ve **Add Connection**.  
  
     Seçtiğiniz sonra **Bağlantı Ekle**, ya da **Bağlantı Ekle** iletişim kutusu veya **veri kaynağı Seç** iletişim kutusu görüntülenir.  
  
3.  Varsa **veri kaynağı Seç** iletişim kutusu görüntülenirse, seçin **Microsoft Access veritabanı dosyası**ve ardından **Tamam**.  
  
4.  Varsa **Bağlantı Ekle** iletişim kutusu görüntülenirse, doğrulayın **veri kaynağı** ayarlanır **Microsoft Access veritabanı dosyası**. Bunun ayarlanmazsa **Microsoft Access veritabanı dosyası**, seçin **değişiklik** açmak için **değişimi veri kaynağı** iletişim kutusunda **Microsoft Access veritabanı Dosya**ve ardından **Tamam** düğmesi.  
  
5.  Seçin **Gözat** Northwind veritabanına içeren .mdb veya .accdb dosyası bulunamıyor.  
  
6.  Northwind veritabanı sürümü tarafından gerekiyorsa, bir kullanıcı adı ve parola girin.  
  
7.  Seçin **Tamam**.  
  
     Bir veri bağlantısı Northwind veritabanına eklenir **Sunucu Gezgini**/**veritabanı Gezgini**.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Nasıl yapılır: örnek veritabanları yükleme](../data-tools/how-to-install-sample-databases.md)   
 [Microsoft Access 2010 ile veri programlama](http://msdn.microsoft.com/library/office/ff965871.aspx)   
 [Veri izlenecek yollar](http://msdn.microsoft.com/library/15a88fb8-3bee-4962-914d-7a1f8bd40ec4)