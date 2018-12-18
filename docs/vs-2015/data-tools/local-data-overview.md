---
title: Yerel verilere genel bakış | Microsoft Docs
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
- local data
- SQL Server LocalDB
- LocalDB
- SQLEXPRESS
- SQL Server, local data
- SQL Express
- SQL Server Compact
- data access [Visual Studio], troubleshooting
- Access, .mdb files in Visual Studio
- data [Visual Studio], local
ms.assetid: d6afa5ac-2bb8-49f2-a50e-f71f611ed506
caps.latest.revision: 71
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: 94b3f066a66a380875609b4f6485d56a19ebde3e
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49885583"
---
# <a name="local-data-overview"></a>Yerel Verilere Genel Bakış
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Üretim verilerini hatalara neden değil, veri uygulamaları geliştirirken, bir veritabanının yerel kopyasını kullanmak en iyisidir. İki geliştiriciler sabit algılamak şekillerde etkileşim kuran hatalara varsa bile bir test veritabanı diğer geliştiricilerle paylaşımı olası sorunları oluşturur. Kendi yerel bilgisayarınızda test verilerini kullanarak tüm tuzaklar önleyebilirsiniz. Tüm veritabanı sistemleri, çoğu yerel veri dosyaları oluşturmanıza olanak sağlar. .NET projeleri için Visual Studio yerel SQL Server veritabanı dosyaları (.mdf) ve Microsoft Access veritabanı dosyaları (.mdb) için özel destek sağlar.  
  
 Visual Studio bu senaryoları destekler:  
  
1.  
  
2.  
  
- 
  
- 
  
- Çözüm Gezgini'nde çözüm düğümüne tıklayarak ve seçerek bir SQL Server veritabanı projesi oluşturma **Ekle &#124; yeni proje**.  Sol bölmede seçin **SQL Server &#124; veritabanı** proje ve Tamam'a tıklayın. Çözüm Gezgini'nde, bir yerel veritabanı dosyasına aktarmak için veritabanı proje düğümüne sağ tıklayın ve ardından Proje tarafından üretilen veritabanı bağlanan bir uygulama geliştirin. Geliştirme ve veritabanı şeması uygulama geliştiriyorsunuz aynı anda değiştirme İyi.  
  
   ![Veritabanı, veritabanı projesine içeri aktarmalısınız](../data-tools/media/raddata-import-database-into-database-project.png "veritabanı projesine raddata Veritabanını İçeri Aktar")  
  
- Yeni bir veritabanı oluşturuyorsanız, ilk olarak ekleyin. bir **hizmet tabanlı veritabanı dosyasını** projenize (**proje &#124; Yeni Öğe Ekle)**. Bu, varsayılan olarak (localdb) \MSSQLocalDB olan yerel makinede SQL Server örneğine bağlı yeni bir .mdf dosyası oluşturur. Veritabanı Sunucu Gezgini içinde görüntülenmesi gerekir. Düğümünü genişletin ve düğümleri tablolar, görünümler, İşlevler vb. gibi yeni veritabanı nesneleri eklemek için sağ tıklayın.  
  
  SQL Server Express LocalDB hakkında daha fazla bilgi için bkz: [Localdb'ye giriş, Gelişmiş bir SQL Express](http://go.microsoft.com/fwlink/?LinkId=234375) ve [LocalDB: Veritabanım nerede?](http://go.microsoft.com/fwlink/?LinkId=234376) Microsoft Web sitesinde.  
  
  Aşağıdaki tabloda, uygulamanızı yerel verilere bağlanma açıklayan konulara bağlantılar sağlar:  
  
|Konu|Açıklama|  
|-----------|-----------------|  
|[Tasarımcı kullanarak SQL veritabanı oluşturma](../data-tools/create-a-sql-database-by-using-a-designer.md)|Veri özelliklerini test etmek ve uygulamalar oluşturmak için kullanabileceğiniz bir yerel veritabanı dosyası oluşturmak için adım adım yönergeler sağlar.|  
|[İzlenecek yol: bir yerel veritabanı dosyası (Windows Forms) verilere bağlanma](../data-tools/walkthrough-connecting-to-data-in-a-local-database-file-windows-forms.md)|Basit bir Windows uygulaması oluştururken, bir SQL Server Express LocalDB veritabanına bağlanmak için adım adım yönergeler sağlar.|  
|[Bir Access veritabanındaki verilere bağlanma (Windows Forms)](../data-tools/connect-to-data-in-an-access-database-windows-forms.md)|Bir Microsoft Access veritabanına bağlanmak için adım adım yönergeler sağlar.|  
|[Nasıl yapılır: Northwind veritabanına bağlanma](../data-tools/how-to-connect-to-the-northwind-database.md)|Northwind örnek veritabanına bağlanma yönergeleri sağlar [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], SQL Server Compact, SQL Server Express ve erişim.|  
  
## <a name="use-the-connection-string"></a>Bağlantı dizesini kullanın  
 Bu en basit yaklaşımdır ve uygulamanız yalnızca veritabanından okuduğunda ve üçüncü taraf veritabanlarını kullanırken olduğunda iyi bir seçimdir. Veritabanı dosyasını herhangi bir yerde uygulamanızı erişim iznine sahip ve bir veritabanı sisteminin desteklediği yerel makine üzerinde bulunabilir.  
  
1.  (İsteğe bağlı) Açıklanan şekilde yeni bir bağlantı oluşturmak [yeni bağlantı ekleme](../data-tools/add-new-connections.md). Üçüncü taraf veritabanları ve kendisi için zaten bağlantı dizesini bilmeniz ve değil veri bağlama yapmak veya kaldırılacak varlık çerçevesi sınıflarını veya veri kümeleri gibi bir veri kaynağı kullanarak .mdf dosyaları için bu adım gerekli değildir. Yalnızca yerel dosyasına bağlanmak için bağlantı dizesini kullanın. .Mdf dosyaları için bkz: [.mdf dosyalarını yükseltme](../data-tools/upgrade-dot-mdf-files.md) ve [bağlantı kurma](https://msdn.microsoft.com/en-us/library/ms254507.aspx).  
  
2.  (İsteğe bağlı) Veri kümeleri, Entity Framework veya LINQ to SQL, kullanıyorsanız veri kaynağını veri kaynağı Yapılandırma Sihirbazı'nı kullanarak oluşturun. Daha fazla bilgi için [yeni veri kaynağı ekleme](../data-tools/add-new-data-sources.md).  
  
## <a name="add-an-existing-mdf-to-your-project"></a>Mevcut bir .mdf projenize ekleyin.  
 Uygulamanın ekleme, silme veya verileri güncelleştirme ve özgün dosyanın bir kopyasını tutmak istediğiniz, dosyayı projenize eklemeyi düşünün. Bunu yaptığınızda dayanarak öğesi özelliği ayarlayabilirsiniz **çıkış dizinine Kopyala** için **her zaman Kopyala** veya **yeniyse Kopyala**ve uygulama geliştirin. Uygulamayı, her zaman özgün veritabanına çıktı klasörüne kopyalanır ve uygulamanızın değişiklikleri kopya gerçekleştirilir. Bu şekilde her zaman temiz bir özgün veri kopyası olacaktır.  
  
1.  Kullanım **Windows dosya Gezgini** sürükleyip .mdf dosyasının üzerine Visual Studio'daki Çözüm Gezgini'nde proje düğümü geçerli konumundan.  Dosya bir localDB örneğine zaten bağlıysa, ilk ayırmanız gerekir. Projeye bıraktıktan sonra Visual Studio otomatik olarak bu varsayılan localDB örneğine iliştirilir.  
  
2.  Yeni veritabanı düğümüne sağ tıklayın ve Özellikler'i seçin. Kopyalama davranışını seçin **her zaman Kopyala** veya **yeniyse Kopyala**.  
  
## <a name="create-a-sql-server-database-project-and-import-your-database"></a>Bir SQL Server veritabanı projesi oluşturun ve veritabanı içeri aktarma  
 Bu, veritabanının kendisi, belki de sütunları veya tabloları ekleme veya veri türlerini değiştirme geliştirme, iyi bir seçenektir.  
  
## <a name="each-project-contains-two-copies-of-the-database"></a>Her proje veritabanı iki kopyasını içerir.  
 Bir proje oluşturduğunuzda, veritabanı dosyası kök proje klasöründen çıkış kopyalanabilir **bin**, klasör. Bu çalışma biçimi **çıkış dizinine Kopyala** dosyasının özelliği ve bu özelliğin varsayılan değeri, kullanmakta olduğunuz veritabanı dosyasının türüne bağlıdır.  
  
 Görüntülenecek **bin** klasöründe **Çözüm Gezgini**, seçin **tüm dosyaları göster** araç çubuğunda.  
  
> [!NOTE]
>  **Çıkış dizinine Kopyala** özelliği web veya C++ projeleri için geçerli değildir.  
  
 Kök proje klasörünüzdeki veritabanı dosyası yalnızca, veritabanı şemasını veya verileri kullanarak düzenlediğinizde değiştirilir **Sunucu Gezgini**/**veritabanı Gezgini** veya diğer [Visual Veritabanı Araçları](http://msdn.microsoft.com/en-us/6b145922-2f00-47db-befc-bf351b4809a1).  
  
 Uygulama geliştirme sırasında verileri değiştirirken, veritabanını değiştiriyorsunuz **bin** klasör. Örneğin, uygulamanızda hata ayıklamak için F5 tuşuna basın, bu klasörde veritabanına bağlandınız.  
  
|Değeri **çıkış dizinine Kopyala** özelliği|Davranış|  
|----------------------------------------------------|--------------|  
|**Yeniyse Kopyala** (varsayılan değer .sdf dosyaları için)|Veritabanı dosyası proje dizinine kopyalanır **bin** dizin projeyi ilk kez. **Değiştirme tarihi** dosyaları özelliği daha sonra projeyi yeniden derleyin her seferinde karşılaştırılır. Proje klasöründeki dosya daha yeniyse kopyalanır **bin** klasörü, önceki dosyanın yerini alır. Aksi takdirde, hiçbir dosya kopyalanmaz. **Dikkat:** bu değeri .mdb veya .mdf dosyaları için önermemekteyiz. Veriler değişmese bile, veritabanı dosyası değişebilir. Dosyanın yalnızca bir bağlantıyı açarsanız daha yeni olarak işaretlenebilir. (örneğin, genişletme **tabloları** düğümünde **Sunucu Gezgini**).|  
|**Her zaman Kopyala** (varsayılan değer .mdf ve .mdb dosyaları için)|Veritabanı dosyası proje dizinine kopyalanır **bin** dizin, uygulamanızı her zaman. Çıkış klasörü veri dosyasında yapılan değişiklikler, uygulama sonraki kez üzerine yazılır.|  
|**Kopyalamayın**|Sistem hiçbir zaman dosyanın üzerine yazmaz **bin** dizin. Uygulamanız çıkış dizinindeki veritabanı dosyasına işaret eden bir dinamik bağlantı dizesi oluşturur. Bu nedenle, verileri çıkış dizinindeki verilerin proje dizinindeki eşleşmesi için isterseniz çıkış dizinine dosyayı el ile kopyalamalısınız.|  
  
## <a name="common-issues-with-local-data"></a>Yerel veri ile ilgili yaygın sorunları  
 Aşağıdaki tablo, yerel veri dosyalarıyla çalışırken karşılaşabileceğiniz genel sorunları açıklar.  
  
|Sorun|Açıklama|  
|-----------|-----------------|  
|Değişikliklerimi Uygulamam test edin ve verileri değiştirme her zaman, ı uygulamamı bir sonraki çalıştırmanızda kaldırılmıştır.|Değerini **çıkış dizinine Kopyala** özelliği **yeniyse Kopyala** veya **her zaman Kopyala**. Çıkış klasöründeki (uygulamanızı test ederken değiştirilmekte olan veritabanı) veritabanı projenizi her seferinde üzerine yazılır. Daha fazla bilgi için [nasıl yapılır: Manage Local Data Files in Your Project](../data-tools/how-to-manage-local-data-files-in-your-project.md).|  
|Veri dosyası kilitli olduğunu belirten bir ileti görüntülenir.|Access (.mdb dosyaları): dosyanın Access gibi başka bir programda açık olmadığını doğrulayın.<br /><br /> SQL Server Express (.mdf dosyaları): SQL Express veri dosyasını kilitler kopyalamak, taşıyın veya Visual Studio IDE dışında yeniden adlandırmak çalışırsanız.|  
|Birden fazla kullanıcı aynı anda aynı veritabanına erişmeye çalıştığında, erişim reddedildi.|Visual Studio yararlanır *kullanıcı örnekleri*, her kullanıcı için ayrı bir SQL Server örneğini oluşturur. SQL Server Express'in bir özelliği olan. Bir kullanıcı dosyaya eriştikten sonra sonraki kullanıcılar bağlanamıyor. IIS genellikle farklı bir hesap altında çalıştığından gibi bir web uygulamasını ASP.NET Geliştirme Sunucusu ve Internet Information Services (IIS) aynı anda çalıştırmak denerseniz bu sorun oluşabilir.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [İzlenecek yol: bir yerel veritabanı dosyası (Windows Forms) verilere bağlanma](../data-tools/walkthrough-connecting-to-data-in-a-local-database-file-windows-forms.md)   
 [Bir Access veritabanındaki verilere bağlanma (Windows Forms)](../data-tools/connect-to-data-in-an-access-database-windows-forms.md)