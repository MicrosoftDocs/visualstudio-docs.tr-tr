---
title: Yeni bağlantı ekleme | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8a93c287-2834-4a83-a590-bdc3fe8d293f
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 03407962b4ea8160d492971367f121835fa39aae
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49218516"
---
# <a name="add-new-connections"></a>Yeni bağlantı ekleme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Bir veritabanı veya hizmet bağlantınızı test etmek ve veritabanı içeriklerini ve şemaları kullanarak keşfetme **Sunucu Gezgini**, **Cloud Explorer**, veya **SQL Server Nesne Gezgini**. Bu windows işlevlerini, bir aşamaya çakışıyor. Temel farklılıklar şunlardır:  
  
 Server Explorer  
 Visual Studio'da varsayılan olarak yüklüdür. Bağlantılarını test et ve SQL Server veritabanları, bir ADO.NET sağlayıcısı yüklü olan herhangi bir veritabanına ve bazı Azure hizmetleri görüntülemek için kullanılabilir. Ayrıca Sistem performans sayaçları, olay günlükleri ve ileti kuyrukları gibi alt düzey nesneleri gösterir. Bir veri kaynağına ADO.NET sağlayıcısı yok varsa, burada gösterilmez, ancak bunu Visual Studio'dan programlı bir şekilde bağlanarak kullanmaya devam edebilirsiniz.  
  
 Cloud Explorer  
 Visual Studio uzantısı olarak el ile yükleme seçerek bu pencereyi **Araçları** > **Uzantılar ve güncelleştirmeler** > **çevrimiçi**  >  **Visual Studio Galerisi**. İçin keşfetmek ve Azure hizmetlerine bağlanan özel işlevler sağlar.  
  
 SQL Server Object Explorer  
 SQL Server veri araçları ile birlikte yüklenir ve altında görünür **görünümü** menüsü. Burada görmüyorsanız, Git **programlar ve Özellikler** Denetim Masası ' nda Visual Studio'yu bulun ve ardından **değişiklik** SQL Server veri araçları için onay kutusunu işaretledikten sonra yükleyiciyi yeniden çalıştırın. Kullanım **SQL Server Nesne Gezgini** görünümü SQL veritabanlarına (bir ADO.NET sağlayıcısı yüklü değilse), yeni veritabanları oluşturmak, şemalar değiştirmek, saklı yordamlar oluşturma, bağlantı dizelerini almak, veri ve daha fazlasını görüntüleyin. Hiçbir ADO.NET sağlayıcısı yüklü olan SQL veritabanları burada gösterilmez, ancak yine de bunları programlı bir şekilde bağlanabilirsiniz.  
  
## <a name="add-a-connection-in-server-explorer"></a>Sunucu Gezgini'nde bir bağlantı Ekle  
 Veritabanına bir bağlantı oluşturmak için tıklayın **Bağlantı Ekle** simgesini **Sunucu Gezgini**, ya da sağ **Sunucu Gezgini** üzerinde **veri Bağlantıları** düğümünü seçip alt **Bağlantı Ekle**. Buradan, başka bir sunucu, bir SharePoint hizmet veya bir Azure hizmeti bir veritabanına bağlanabilirsiniz.  
  
 ![Sunucu Gezgini yeni bağlantı simgesi](../data-tools/media/raddata-server-explorer-new-connection-icon.png "raddata Sunucu Gezgini yeni bağlantı simgesi")  
  
 Bu işlem sonrasında **Bağlantı Ekle** iletişim kutusu. Burada, biz SQL Server LocalDB örneğinin adı girdiniz.  
  
 ![Yeni Bağlantı Ekle](../data-tools/media/raddata-add-new-connection-dialog.png "raddata yeni bağlantı iletişim kutusu Ekle")  
  
## <a name="change-the-provider"></a>Sağlayıcısını değiştirme  
 Veri kaynağı istemezsiniz tıklayarak **değişiklik** düğmesi, yeni bir veri kaynağı ve/veya yeni bir ADO.NET veri sağlayıcı seçin. Yeni sağlayıcıyı nasıl yapılandırdığınıza bağlı olarak, kimlik bilgilerini isteyebilir.  
  
 ![Değiştirme AD0.NET veri sağlayıcısı](../data-tools/media/raddata-change-ad0-net-data-provider.png "raddata değiştirme AD0.NET veri sağlayıcısı")  
  
## <a name="test-the-connection"></a>Bağlantıyı test edin  
 Veri kaynağını seçtikten sonra tıklayın **Bağlantıyı Sına**. Başarısız olursa sorun gidermek satıcı belgelerine göre ihtiyacınız olacak.  
  
 ![Bağlantıyı Sına](../data-tools/media/raddata-test-connection.png "raddata bağlantıyı Test Et")  
  
 Test başarılı olursa oluşturmaya hazır olduğunuz bir *veri kaynağı*, gerçekten anlamına gelen bir Visual Studio terimi olduğu bir *veri modeli* temel alınan veritabanı veya hizmet tabanlı.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [.NET için Visual Studio veri araçları](../data-tools/visual-studio-data-tools-for-dotnet.md)

