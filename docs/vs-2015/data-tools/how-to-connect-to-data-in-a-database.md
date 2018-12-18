---
title: 'Nasıl yapılır: bir veritabanındaki verilere bağlanma | Microsoft Docs'
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
- databases, connecting to
- data sources, databases
- data [Visual Studio], connecting to databases
- data sources, creating
- database connections
ms.assetid: 6c56e54e-8834-4297-85aa-cc1a443ba556
caps.latest.revision: 55
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: e75de3c81270449da6fe6bb504b476b912f51583
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49273812"
---
# <a name="how-to-connect-to-data-in-a-database"></a>Nasıl yapılır: Bir Veritabanındaki Verilere Bağlanma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Uygulamanızı bir veritabanına bağlanmak için Visual Studio'yu kullanabilirsiniz. Veri bağlantısı oluşturduktan sonra Visual Studio, uygulamanızın veritabanındaki verilerle etkileşim kurmak için kullandığı bir veri modeli oluşturur. Veri modelindeki nesneler görünür [veri kaynakları penceresi](http://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992). Ardından, öğeleri sürükleyerek verilere bağlı denetimler oluşturabilirsiniz **veri kaynakları penceresi** bir tasarım yüzeyine bırakın. Daha fazla bilgi için [Visual Studio'da verilere denetimler bağlama](../data-tools/bind-controls-to-data-in-visual-studio.md).  
  
 Bu konu, bir veritabanına bağlanmak ve aşağıdaki türde veri modelleri oluşturmak için yönergeler sağlar:  
  
-   Veri kümesi  
  
-   Varlık Veri Modeli (EDM)  
  
> [!NOTE]
>  Visual Studio, LINQ, bir veritabanından SQL sınıfları oluşturmak için de kullanabilirsiniz. Ancak LINQ to SQL sınıfları görünmez **veri kaynakları** penceresinde ve dolayısıyla veriye bağlı denetimler oluşturmak için bir tasarımcıya doğrudan sürüklenemez. LINQ, bir veritabanından SQL sınıfları oluşturma hakkında daha fazla bilgi için bkz. [nasıl yapılır: tablolar ve görünümler (O/R Tasarımcısı) ile eşlenen SQL sınıflarına LINQ oluşturma](../data-tools/how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md).  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
##  <a name="dataset"></a> Bir veritabanına bağlanma ve veri kümesi oluşturma  
 Bir veritabanını temel alan bir veri kümesi oluşturduğunuzda, Visual Studio verilerin programlanabilir bir görünümünü temsil eden sınıf kümesi oluşturur. Ana sınıfa bir *yazılan veri kümesi*. Türü belirtilmiş veri kümesi, veritabanındaki tabloları temsil eden veri tablosu nesnelerini içerir. Türü belirtilmiş veri kümeleri hakkında daha fazla bilgi için bkz. [Visual Studio'daki veri kümesi Araçları](../data-tools/dataset-tools-in-visual-studio.md).  
  
 Bir veri kümesi oluşturduktan sonra veri kümesi nesnelerini veri kaynakları penceresinden WPF veya Windows Forms tasarımcısına sürükleyerek veri bağlama WPF ya da Windows Formları denetimleri oluşturabilirsiniz.  
  
#### <a name="to-connect-your-application-to-a-database-and-create-a-dataset"></a>Uygulamanızı bir veritabanına bağlanma ve veri kümesi oluşturma  
  
1.  Varolan bir projeyi Visual Studio'da açın veya yeni bir proje oluşturun.  
  
2.  Üzerinde **veri** menüsünü tıklatın **yeni veri kaynağı Ekle**.  
  
     **Veri kaynağı Yapılandırma Sihirbazı** açılır.  
  
3.  Üzerinde **bir veri kaynağı türü seçin** sayfasında **veritabanı**ve ardından **sonraki**.  
  
4.  Üzerinde **veritabanı modeli seçin** sayfasında **veri kümesi**ve ardından **sonraki**.  
  
5.  Üzerinde **veri bağlantınızı seçin** sayfasında, kullanılabilir bağlantılar listesinden bir veri bağlantısı seçin ve ardından **sonraki**.  
  
     İstenen veri bağlantısı kullanılamıyorsa içindeki adımları izleyerek yeni bir bağlantı oluşturmak [yeni bir veritabanı bağlantısı oluşturma](#CreatingDataConnection).  
  
6.  Üzerinde **bağlantı dizesini uygulama yapılandırma dosyasına Kaydet** sayfasında, isteğe bağlı olarak temizleyin **Evet, bağlantıyı bu adla Kaydet** doğrudan derlenmiş bağlantı dizesini kaydetmek istiyorsanız kutuyu uygulama. Varsayılan olarak, bağlantı, uygulama yapılandırma dosyasına kaydedilir. Daha fazla bilgi için [nasıl yapılır: Kaydet ve bağlantı dizeleri düzenleme](~/E:/Repos/visualstudio-docs-pr/docs/data-tools/how-to-save-and-edit-connection-strings.md).  
  
7.  Üzerinde **veritabanı nesnelerinizi seçin** sayfasında, uygulamanızda kullanacağı veritabanı nesnelerini seçin. Varsayılan değiştirme seçeneği de **veri kümesi adı**.  
  
8.  **Son**'a tıklayın. Yeni oluşturduğunuz veri kümesi kullanıma sunulduğunu **veri kaynakları** penceresi.  
  
    > [!NOTE]
    >  Varsa **veri kaynakları** penceresi açık değilse, tıklayın **veri kaynaklarını Göster** üzerinde **veri** penceresini açmak için menü.  
  
9. Şimdi öğeleri sürükleyebilirsiniz **veri kaynakları** penceresinden WPF tasarımcısına, Windows Form Tasarımcısı'nda, veya [Bileşen Tasarımcısı](http://msdn.microsoft.com/library/61a3a450-5b15-465e-bd9a-72a6c8c2b282) verilere bağlı denetimler oluşturabilirsiniz. Daha fazla bilgi için [Visual Studio'da verilere denetimler bağlama](../data-tools/bind-controls-to-data-in-visual-studio.md).  
  
##  <a name="edm"></a> Veritabanına bağlanma ve bir varlık veri modeli oluşturma  
 Bir veritabanını temel alan bir varlık veri modeli oluşturduğunuzda, Visual Studio verilerin programlanabilir bir görünümünü temsil eden sınıf kümesi oluşturur. Varlık veri modelleri ve ADO.NET varlık çerçevesi hakkında daha fazla bilgi için bkz. [Entity Framework'e Genel Bakış](http://msdn.microsoft.com/library/a2166b3d-d8ba-4a0a-8552-6ba1e3eaaee0).  
  
 Bir varlık veri modeli oluşturduktan sonra varlık nesnelerini veri kaynakları penceresinden WPF tasarımcısına sürükleyerek veri bağlama WPF denetimleri oluşturabilirsiniz.  
  
#### <a name="to-connect-your-application-to-a-database-and-create-an-entity-data-model"></a>Uygulamanızı bir veritabanına bağlanma ve bir varlık veri modeli oluşturma  
  
1.  Varolan bir projeyi Visual Studio'da açın veya yeni bir proje oluşturun.  
  
2.  Bağlantısındaki **varlık veri modeli Sihirbazı** bir veritabanına bağlamak ve modelin içeriğini belirtmek için. Daha fazla bilgi için [nasıl yapılır: yeni bir .edmx dosyası oluşturma](http://msdn.microsoft.com/en-us/beb8189e-e51c-4051-839c-9902c224abf2).  
  
3.  Tamamladıktan sonra **varlık veri modeli Sihirbazı**, oluşturduğunuz varlık veri modeli varlık veri modeli Tasarımcısı'nda açılır ve veri nesneleri kullanıma sunulmuştur **veri kaynakları** penceresi.  
  
    > [!NOTE]
    >  Varsa **veri kaynakları** penceresi açık değilse, tıklayın **veri kaynaklarını Göster** üzerinde **veri** penceresini açmak için menü.  
  
4.  WPF Tasarımcısı açıksa artık öğeleri sürükleyebilirsiniz **veri kaynakları** penceresinden tasarımcıya varlık veri Modeli'ne bağlı denetimler oluşturmak için. Daha fazla bilgi için [Visual Studio'da veri bağlama WPF denetimleri](../data-tools/bind-wpf-controls-to-data-in-visual-studio2.md).  
  
     Windows Forms Tasarımcısı açıksa öğeleri sürükleyemezsiniz **veri kaynakları** tasarımcıya. Varlık veri Modeli'ne bağlı denetimler oluşturmak için projeyi derleyin, varlık veri Modeli'ni temel alan yeni bir nesne veri kaynağı ekleyin ve ardından bu nesneleri tasarımcıya sürükleyebilirsiniz.  
  
##  <a name="CreatingDataConnection"></a> Yeni bir veritabanı bağlantısı oluşturma  
 Kullanırken **veri kaynağı Yapılandırma Sihirbazı**veya **varlık veri modeli Sihirbazı**, kullanmak istediğiniz veritabanına bir bağlantı belirtmelisiniz. Veritabanına bir bağlantı zaten yoksa, bağlantı oluşturmak için aşağıdaki adımları gerçekleştirin.  
  
 Bu yönergelerde başlattığınız varsayılır **veri kaynağı Yapılandırma Sihirbazı** veya **varlık veri modeli Sihirbazı** açıklandığı [veritabanına bağlanma ve veri kümesi oluşturma ](#dataset) ve [veritabanına bağlanma ve bir varlık veri modeli oluşturma](#edm).  
  
#### <a name="to-create-a-new-database-connection"></a>Yeni bir veritabanı bağlantısı oluşturmak için  
  
1.  Üzerinde **veri bağlantınızı seçin** sayfasının **veri kaynağı Yapılandırma Sihirbazı** veya **varlık veri modeli Sihirbazı**, tıklayın **Yenibağlantı**.  
  
     Aşağıdaki eylemlerden biri gerçekleşir:  
  
    -   Visual Studio'da bir veri bağlantısı oluşturduysanız **Bağlantı Ekle** iletişim kutusu açılır.  
  
    -   Bu Visual Studio'da oluşturduğunuz ilk veri bağlantısıysa **veri kaynağı Seç** iletişim kutusu görüntüler. Bağlanmak ve ardından istediğiniz veritabanı türünü seçin **Tamam** görüntülenecek **Bağlantı Ekle** iletişim kutusu.  
  
2.  İçinde **Bağlantı Ekle** iletişim kutusunda, istenen bilgileri girin. **Bağlantı Ekle** iletişim kutusunda, her veri sağlayıcı türü için farklıdır.  
  
    > [!NOTE]
    >  Seçili **veri kaynağı** içinde **Bağlantı Ekle** iletişim kutusunu tıklatın, bağlanmak istediğiniz veri kaynağını değil **değişiklik** açmak için **değişikliği verileri Kaynak** iletişim kutusuna ve ardından farklı bir veri kaynağı seçin.  
  
3.  İçinde **Bağlantı Ekle** iletişim kutusu, tıklayın **Tamam**.  
  
     Geri **veri bağlantınızı seçin** sayfasının **veri kaynağı Yapılandırma Sihirbazı** veya **varlık veri modeli Sihirbazı**.  
  
4.  Üzerinde **veri bağlantınızı seçin** sayfasında, yeni veri bağlantısı'nın seçili olduğundan emin olun ve ardından **sonraki**.  
  
5.  Kalan adımları tamamlayın **veri kaynağı Yapılandırma Sihirbazı** veya **varlık veri modeli Sihirbazı**.  
  
## <a name="net-framework-security"></a>.NET Framework Güvenliği  
 Önemli bilgileri depolamak (örneğin bir parolayı), uygulamanızın güvenliğini etkileyebilir. Windows Kimlik Doğrulaması (tümleşik güvenlik olarak da bilinir) kullanılarak bir veritabanına erişimi denetlemek için daha güvenli bir yoldur. Daha fazla bilgi için [bağlantı bilgilerini koruma](http://msdn.microsoft.com/library/1471f580-bcd4-4046-bdaf-d2541ecda2f4).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Yeni veri kaynağı ekleme](../data-tools/add-new-data-sources.md)   
 [Veri izlenecek yollar](http://msdn.microsoft.com/library/15a88fb8-3bee-4962-914d-7a1f8bd40ec4)   
 [Visual Studio'da verilere Windows Forms denetimleri bağlama](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Visual Studio'da verilere bağlanma](../data-tools/connecting-to-data-in-visual-studio.md)   
 [Veri Kaynağına Bağlanma](http://msdn.microsoft.com/library/9abc3f92-1be3-4e1a-b360-762dc689650e)