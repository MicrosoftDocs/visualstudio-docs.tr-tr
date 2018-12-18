---
title: Forms uygulamalarında Windows verilere bağlanma | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- System.Data.SqlClient.SqlConnection
- System.Data.Odbc.OdbcConnection
- System.Data.OleDb.OleDbConnection
- System.Data.OracleClient.OracleConnection
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- connection objects, tools for working with
- OleDbConnection class, ADO.NET connection objects
- databases [Visual Studio], connecting to
- data adapters, connections
- connection pooling, ADO.NET connections
- connection strings [Visual Studio], ADO.NET
- connection objects, types of
- dynamic properties, ADO.NET connections
- connections, about connections
- data [Visual Studio], connecting
- design-time connections
- connections, design-time
- TableAdapters, connections
- connection objects
- SqlConnection class, ADO.NET connection objects
- connecting to databases, ADO.NET connections
- transactions, ADO.NET
- database connections [Visual Studio], ADO.NET
ms.assetid: 184cbd0d-3b26-418d-a11c-f9f8f004fbff
caps.latest.revision: 31
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: d8da35b32f3dd25bd7ed47b25f722c6b0aa21ac7
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49208955"
---
# <a name="connecting-to-data-in-windows-forms-applications"></a>Windows Forms Uygulamalarındaki Verilere Bağlanma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] veritabanları, web servisleri ve nesneler gibi birçok farklı kaynaktan veri uygulamanızı bağlamak için araçlar sağlar. Veri tasarım araçlarına kullanıyorsanız [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], genellikle açıkça form veya bileşeni için bir bağlantı nesnesi oluşturmanız gerekmez. Bağlantı nesnesi, genellikle bir veri sihirbazları veya veri nesneleri formunuza sürükleyerek Tamamlanıyor sonucu olarak oluşturulur. Uygulamanızı bir veritabanı, web hizmeti veya nesne verilere bağlanmak için çalıştırın [veri kaynağı Yapılandırma Sihirbazı](http://msdn.microsoft.com/library/c4df7de5-5da0-4064-940c-761dd6d9e28f) seçerek **yeni veri kaynağı Ekle** gelen [veri kaynakları penceresi](http://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992).  
  
 Aşağıdaki diyagramda, veri alma ve bir Windows uygulaması bir formda görüntülemek için TableAdapter sorgu çalıştırarak verileri bağlanırken operations standart akışı gösterilmektedir.  
  
 ![Bir istemci uygulama, veri akışında](../data-tools/media/clientdatadiagram.gif "ClientDataDiagram")  
  
 Bazı durumlarda, tüm veri Tasarım araçları yardımı olmadan bir bağlantı nesnesi oluşturmak kullanışlıdır. Bağlantıları program aracılığıyla oluşturma hakkında daha fazla bilgi için bkz: [bir veri kaynağına bağlanma](http://msdn.microsoft.com/library/9abc3f92-1be3-4e1a-b360-762dc689650e).  
  
> [!NOTE]
>  Web uygulamaları verilere bağlanma hakkında daha fazla bilgi için bkz. [ASP.NET Data Access içerik haritası](http://msdn.microsoft.com/en-us/f9219396-a0fa-481f-894d-e3d9c67d64f2).  
  
## <a name="walkthroughs-for-connecting-windows-forms-applications-to-data"></a>Veri uygulamaları Windows bağlamak için izlenecek yollar oluşturur  
 Aşağıdaki izlenecek Windows Forms uygulamalarındaki verilere bağlanmaya yönelik yordamlar sağlar:  
  
-   [İzlenecek yol: (Windows Forms) bir veritabanındaki verilere bağlanma](http://msdn.microsoft.com/library/02d39aa6-8993-4602-be13-a13536af3d1c)  
  
-   [İzlenecek yol: bir yerel veritabanı dosyası (Windows Forms) verilere bağlanma](../data-tools/walkthrough-connecting-to-data-in-a-local-database-file-windows-forms.md)  
  
-   [İzlenecek yol: bir Web hizmetindeki (Windows Forms) verilere bağlanma](http://msdn.microsoft.com/library/079fb9b0-c733-40c1-acd1-d0d68834354d)  
  
-   [İzlenecek yol: nesnelerdeki (Windows Forms) verilere bağlanma](http://msdn.microsoft.com/library/21a7fba2-b38b-4726-8cbe-d22154b75a05)  
  
-   [Bir Access veritabanındaki verilere bağlanma (Windows Forms)](../data-tools/connect-to-data-in-an-access-database-windows-forms.md)  
  
## <a name="creating-connections"></a>Bağlantı oluşturma  
 İçinde [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], bağlantıları kullanarak yapılandırılmış **Bağlantı Ekle/Değiştir** iletişim kutusu. **Bağlantı Ekle** düzenlerken veya veri sihirbazlardan birini içindeki bağlantılar oluşturma iletişim kutusu görünür veya [Sunucu Gezgini/veritabanı Gezgini](http://msdn.microsoft.com/library/4ea29b3b-bbb2-45e4-9082-eaf635c41c4d) veya ne zaman düzenlediğiniz bağlantı özellikleri **özellikleri** penceresi.  
  
 Aşağıdaki eylemlerden birini gerçekleştirdiğinizde veri bağlantıları otomatik olarak yapılandırılır.  
  
|Eylem|Açıklama|  
|------------|-----------------|  
|Çalıştırma [veri kaynağı Yapılandırma Sihirbazı'nı](http://msdn.microsoft.com/library/c4df7de5-5da0-4064-940c-761dd6d9e28f).|Bağlantıları yapılandırılan veritabanı yolu seçildiğinde **veri kaynağı Yapılandırma Sihirbazı**. Daha fazla bilgi için [nasıl yapılır: bir veritabanındaki verilere bağlanma](../data-tools/how-to-connect-to-data-in-a-database.md).|  
|Çalıştırma [TableAdapter Yapılandırma Sihirbazı'nı](http://msdn.microsoft.com/library/3a373dd9-7b34-4d3c-a48b-69414512bac8).|Bağlantılar içinde oluşturulan **TableAdapter Yapılandırma Sihirbazı'nı**. Daha fazla bilgi için [oluştur ve TableAdapter yapılandırma](../data-tools/create-and-configure-tableadapters.md).|  
|Çalıştırma [TableAdapters düzenleme](../data-tools/editing-tableadapters.md).|Bağlantılar içinde oluşturulan **TableAdapter sorgu Yapılandırma Sihirbazı'nı**. Daha fazla bilgi için [nasıl yapılır: TableAdapter sorguları oluşturma](../data-tools/how-to-create-tableadapter-queries.md).|  
|Öğeleri sürükleme [veri kaynakları penceresi](http://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992) forma veya [Bileşen Tasarımcısı](http://msdn.microsoft.com/library/61a3a450-5b15-465e-bd9a-72a6c8c2b282).|Bağlantı nesneleri öğeleri sürüklerken oluşturulan **veri kaynakları** penceresinden **Windows Form Tasarımcısı** veya **Bileşen Tasarımcısı**. Daha fazla bilgi için [Visual Studio'da verilere denetimler bağlama](../data-tools/bind-controls-to-data-in-visual-studio.md).|  
|Yeni veri bağlantıları Ekle [Sunucu Gezgini/veritabanı Gezgini](http://msdn.microsoft.com/library/4ea29b3b-bbb2-45e4-9082-eaf635c41c4d).|Veri bağlantılarını, **Sunucu Gezgini/veritabanı Gezgini** veri sihirbazlarda kullanılabilir bağlantılar listesinde görünür.|  
  
## <a name="connection-strings"></a>Bağlantı dizeleri  
 Bağlantı dizeleri, derlenmiş uygulamanızda veya uygulama yapılandırma dosyasında depolanabilir. Daha fazla bilgi için [nasıl yapılır: Kaydet ve bağlantı dizeleri düzenleme](~/E:/Repos/visualstudio-docs-pr/docs/data-tools/how-to-save-and-edit-connection-strings.md).  
  
## <a name="connection-information-and-security"></a>Bağlantı bilgilerini ve güvenlik  
 Bir bağlantı açmak önemli bir kaynağa erişim sağlama içerdiğinden — bir veritabanı — genellikle güvenlik sorunları yapılandırma ve bir bağlantıyla çalışma kullanılan vardır.  
  
 Nasıl uygulamasını güvenli hale getirmek ve sistem mimarisine erişimini veri kaynağına bağlıdır. Web tabanlı bir uygulama, örneğin, kullanıcılar genellikle anonim erişim için Internet Information Services (IIS) alma ve güvenlik kimlik bilgileri sağlamaz. Bu durumda, uygulamanızı kendi oturum açma bilgilerini tutar ve bağlantıyı açın ve veritabanına erişmek için bunun yerine herhangi belirli kullanıcı bilgileri kullanır.  
  
> [!IMPORTANT]
>  Parola gibi bağlantı dizesi ayrıntılarını depolama, uygulamanızın güvenliğini etkileyebilir. Windows tümleşik güvenlik'i kullanarak bir veritabanına erişimi denetlemek için daha güvenli bir yoludur. Daha fazla bilgi için [bağlantı bilgilerini koruma](http://msdn.microsoft.com/library/1471f580-bcd4-4046-bdaf-d2541ecda2f4).  
  
 İntranet veya çok katmanlı uygulamalar, Windows, IIS ve SQL Server tarafından sağlanan tümleşik güvenlik seçeneği yararlanabilir. Bu modelde, yerel ağ için bir kullanıcının kimlik bilgilerine de veritabanı kaynaklarına erişmek için kullanılır ve bağlantı dizesinde açık bir kullanıcı adı veya parola kullanılır. Genellikle, böylece veritabanı erişebilen her kullanıcı için tek tek izinleri gerekmez izinleri grupları yoluyla veritabanı sunucusu bilgisayarında oluşturulur. Bu model, her bağlantı için oturum açma bilgilerini depolamak gerekmez ve bağlantı dizesi bilgilerini korumak için gereken ek adımları yoktur.  
  
 Güvenlik hakkında daha fazla bilgi için aşağıdaki konulara bakın:  
  
-   [ADO.NET Uygulamalarının Güvenliğini Sağlama](http://msdn.microsoft.com/library/005a1d43-6ee5-471e-ad98-1d30a44d49d5)  
  
-   [Windows Forms'ta Daha Güvenli Dosya ve Veri Erişimi](http://msdn.microsoft.com/library/3cd3e55b-2f5e-40dd-835d-f50f7ce08967)  
  
## <a name="design-time-connections-in-server-explorerdatabase-explorer"></a>Sunucu Gezgini/veritabanı Gezgini tasarım zamanı bağlantıları  
 **Sunucu Gezgini/veritabanı Gezgini** tasarım zamanı veri kaynaklarına bağlantı oluşturmak bir yol sağlar. Bu, mevcut veri kaynaklarına göz atmanıza izin verir; tabloları, sütunları ve içerdikleri diğer öğelerin ilgili bilgileri görüntüler; Düzenle ve veritabanı öğeleri oluşturun.  
  
 Kullanılabilir bağlantılar, uygulamanızın doğrudan kullanmaz **Sunucu Gezgini/veritabanı Gezgini**. Bu bağlantı tarafından kullanılan [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] tasarım zamanında uygulamanızın veritabanıyla çalışmak için. Daha fazla bilgi için [Visual veritabanı araçları](http://msdn.microsoft.com/en-us/6b145922-2f00-47db-befc-bf351b4809a1).  
  
 Örneğin, tasarım zamanında kullanabilirsiniz **Sunucu Gezgini/veritabanı Gezgini** veritabanına bir bağlantı oluşturmak için. Daha sonra bir form tasarlarken, veritabanı göz atabilir, bir tablodan sütunları seçin ve üzerine sürükleyerek [veri kümesi Tasarımcısı](../data-tools/creating-and-editing-typed-datasets.md). Bu, oluşturur bir [TableAdapter](../data-tools/tableadapter-overview.md) veri kümenizde. Ayrıca, yeni oluşturulan TableAdapter'ın parçası olan yeni bir bağlantı nesnesi oluşturur.  
  
 Tasarım zamanı bağlantıları hakkında bilgi, belirli bir proje veya çözüm bağımsız olarak, yerel bilgisayarınızda depolanır. Bir uygulamada çalışırken bir tasarım zamanı bağlantı kurduktan sonra bu nedenle, görünür **Sunucu Gezgini/veritabanı Gezgini** , çalıştığınız her [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], olduğu sürece hangi sunucunun bağlantı noktaları kullanılabilir. Daha fazla bilgi için [nasıl yapılır: sunucu gezgininden veritabanına bağlanma](http://msdn.microsoft.com/en-us/7c1c3067-0d77-471b-872b-639f9f50db74).  
  
 [!INCLUDE[SQLObjectExplorer](../includes/sqlobjectexplorer-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual Studio'da verilere bağlanma](../data-tools/connecting-to-data-in-visual-studio.md)   
 [Nasıl yapılır: bir veritabanındaki verilere bağlanma](../data-tools/how-to-connect-to-data-in-a-database.md)   
 [İzlenecek yol: (Windows Forms) bir veritabanındaki verilere bağlanma](http://msdn.microsoft.com/library/02d39aa6-8993-4602-be13-a13536af3d1c)   
 [ASP.NET Data Access içerik haritası](http://msdn.microsoft.com/en-us/f9219396-a0fa-481f-894d-e3d9c67d64f2)   
 [Uygulamanızı veri almaya hazırlama](http://msdn.microsoft.com/library/c17bdb7e-c234-4f2f-9582-5e55c27356ad)   
 [Uygulamanıza veri getirme](../data-tools/fetching-data-into-your-application.md)   
 [Visual Studio'da verilere denetimler bağlama](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [Uygulamanızdaki verileri düzenleme](../data-tools/editing-data-in-your-application.md)   
 [Verileri doğrulama](http://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e)   
 [Verileri Kaydetme](../data-tools/saving-data.md)