---
title: Yeni bağlantı ekleme
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 14df0183076125e487873bbb9865b2481e277a5b
ms.sourcegitcommit: ce154aee5b403d5c1c41da42302b896ad3cf8d82
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/07/2018
ms.locfileid: "34845021"
---
# <a name="add-new-connections"></a>Yeni bağlantı ekleme

Bir veritabanı veya hizmet bağlantınızı test ve veritabanı içeriklerini ve şemalarını kullanarak keşfedin **Sunucu Gezgini**, **Cloud Explorer**, veya **SQL Server Nesne Gezgini**. Bu windows işlevselliğini bazı ölçüde çakışıyor. Temel farklılıklar şunlardır:

- Server Explorer

   Visual Studio'da varsayılan olarak yüklüdür. Bağlantıları sınamak ve SQL Server veritabanları, yüklü bir ADO.NET sağlayıcısı diğer veritabanlarına ve bazı Azure hizmetleri görüntülemek için kullanılabilir. Ayrıca Sistem performans sayaçları, olay günlüklerini ve ileti kuyrukları gibi alt düzey nesneleri gösterir. Bir veri kaynağı hiçbir ADO.NET sağlayıcısı varsa, burada görüntülenmeyecektir, ancak bunu Visual Studio'dan program aracılığıyla bağlanarak kullanmaya devam edebilirsiniz.

- Bulut Gezgini

   Visual Studio uzantısı olarak el ile yüklemeniz seçerek bu pencereyi **Araçları** > **Uzantılar ve güncelleştirmeler** > **çevrimiçi**  >  **Visual Studio Markeplace**. Keşfetmek ve Azure hizmetlerine bağlanmak için özel işlevler sağlar.

- SQL Server Object Explorer

   SQL Server veri araçları ile birlikte yüklenir ve altında görünür **Görünüm** menüsü. Var. görmüyorsanız, Git **programlar ve Özellikler** Denetim Masası ' nda Visual Studio bulun ve ardından **değişiklik** SQL Server veri araçları için onay kutusunu işaretledikten sonra yükleyiciyi yeniden çalıştırın. Kullanım **SQL Server Nesne Gezgini** görünümü SQL veritabanları (bunlar bir ADO.NET sağlayıcısı varsa) için yeni veritabanları oluşturma, şemalar değiştirmek, saklı yordamlar oluşturma, bağlantı dizeleri almak, verileri görüntüleyebilir. Yüklü hiçbir ADO.NET sağlayıcısı SQL veritabanları burada görünmez, ancak hala kendisine programlı olarak bağlayabilirsiniz.

## <a name="add-a-connection-in-server-explorer"></a>Sunucu Gezgini Bağlantı Ekle

Veritabanına bir bağlantı oluşturmak için tıklatın **Bağlantı Ekle** simgesine **Sunucu Gezgini**, veya sağ **Sunucu Gezgini** üzerinde **veri Bağlantıları** düğümü ve select **Bağlantı Ekle**. Buradan, başka bir sunucuda, bir SharePoint hizmeti veya bir Azure hizmeti bir veritabanına bağlanabilir.

![Sunucu Gezgini yeni bağlantı simgesi](../data-tools/media/raddata-server-explorer-new-connection-icon.png)

Bu işlem sonrasında **Bağlantı Ekle** iletişim kutusu. Burada, biz SQL Server yerel veritabanı örneğinin adı girdiniz.

![Yeni bağlantı ekleme](../data-tools/media/raddata-add-new-connection-dialog.png)

## <a name="change-the-provider"></a>Sağlayıcı değiştirme

Veri kaynağı istemezsiniz ise, tıklatın **değişiklik** düğmesi yeni bir veri kaynağı ve/veya yeni bir ADO.NET veri sağlayıcı seçin. Yeni sağlayıcıyı nasıl yapılandırdığınıza bağlı olarak, kimlik bilgilerini isteyebilir.

![Değişiklik AD0.NET veri sağlayıcısı](../data-tools/media/raddata-change-ad0.net-data-provider.png)

## <a name="test-the-connection"></a>Bağlantıyı sınayın

Veri kaynağını seçtikten sonra tıklatın **Bağlantıyı Sına**. İşlemi başarılı değil, sorun giderme satıcısının belgelerine göre yapmanız gerekir.

![Bağlantıyı Sına](../data-tools/media/raddata-test-connection.png)

Test başarılı olursa, oluşturmak için hazır bir *veri kaynağı*, gerçekten anlamına gelir bir Visual Studio terimi olduğu bir *veri modeli* temel alınan veritabanı veya hizmet tabanlı.

## <a name="see-also"></a>Ayrıca bkz.

- [.NET için Visual Studio veri araçları](../data-tools/visual-studio-data-tools-for-dotnet.md)