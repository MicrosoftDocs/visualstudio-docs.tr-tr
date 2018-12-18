---
title: Yeni veri kaynağı ekleme | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.datasource.datasourcefieldspicker
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- data [Visual Studio], data sources
- data sources
ms.assetid: ed28c625-bb89-4037-bfde-cfa435d182a2
caps.latest.revision: 60
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 50a18de0fa3006e1cf95e48d50f24411347fd135
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49279155"
---
# <a name="add-new-data-sources"></a>Yeni veri kaynağı ekleme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Visual Studio'da .NET veri Araçları'nın içeriğinde terimi *veri kaynağı* bir veri deposuna bağlanan ve bir .NET uygulaması için verileri ortaya çıkaran .NET nesneleri gösterir. Visual Studio tasarımcıları, veritabanı nesnelerini sürükleyip yükleyen Veri formları bağlayan ortak kod oluşturmak için veri kaynağı çıkışını tüketebileceği **veri kaynakları** penceresi. Bu türdeki veri kaynağının olabilir:  
  
-   Bazı tür veritabanı ile ilişkili bir Entity Framework modelini sınıfta.  
  
-   Bazı tür veritabanı ile ilişkili bir veri kümesi.  
  
-   Bir Windows Communication Foundation (WCF) veri hizmeti veya bir REST hizmeti gibi bir ağ hizmeti temsil eden sınıf.  
  
-   SharePoint hizmet temsil eden sınıf.  
  
-   Bir sınıf veya çözümünüzdeki koleksiyonu.  
  
> [!NOTE]
>  Veri bağlama özellikleri kullanmıyorsanız, veri kümeleri, Entity Framework, LINQ to SQL, WCF ya da SharePoint, "veri kaynağı" kavramını geçerli değildir. Yalnızca SQLCommand nesnesi kullanarak veritabanına doğrudan bağlanmak ve veritabanıyla doğrudan iletişim kurar.  
  
 Oluşturma ve kullanarak veri kaynaklarını düzenleme **veri kaynağı Yapılandırma Sihirbazı** bir Windows Forms veya Windows Presentation Foundation uygulaması içinde. Entity Framework için ilk, varlık sınıfları oluşturun ve ardından seçerek Sihirbazı başlatın **proje** > **yeni veri kaynağı Ekle** (Bu makalenin sonraki bölümlerinde daha ayrıntılı açıklanmıştır).  
  
 ![Veri Kaynağı Yapılandırma Sihirbazı'nı](../data-tools/media/data-source-configuration-wizard.png "veri kaynağı Yapılandırma Sihirbazı")  
  
 Bir veri kaynağı oluşturduktan sonra görünür **veri kaynakları** araç penceresi (Shift + Alt + D ya da **görünümü** > **diğer Windows**  >  **Veri kaynağı**). Bir veri kaynağından sürükleyebilirsiniz **veri kaynakları** penceresinden bir form Tasarım yüzeyine veya denetimi. Bu ortak kod oluşturulmasına neden olur — kullanıcı veri deposundaki kaynaklanan veri görüntüleyen kod. Aşağıdaki çizimde, bir Windows forma bırakılan bir veri kümesi gösterir. Uygulamayı F5'i seçtiyseniz, veritabanından alınan veri form denetimlerinde görüntülenir.  
  
 ![Veri kaynağı işlemi sürükleyin](../data-tools/media/raddata-data-source-drag-operation.png "raddata veri kaynağı işlemi sürükleyin")  
  
## <a name="data-source-for-a-database-or-a-database-file"></a>Veri kaynağı için bir veritabanı veya veritabanı dosyası  
  
### <a name="dataset"></a>Veri kümesi  
 Veri kaynağı olarak bir veri kümesi oluşturmak için çalıştırılması **veri kaynağı Yapılandırma Sihirbazı** (**proje** > **yeni veri Ekle** kaynak) seçtikten  **Veritabanı** veri kaynağı türü. Yeni veya var olan veritabanı bağlantısı veya veritabanı dosyası belirtmek için istemleri izleyin.  
  
### <a name="entity-classes"></a>Varlık sınıfları  
 Veri kaynağı olarak bir Entity Framework modelini oluşturmak için ilk çalıştırma **varlık veri modeli Sihirbazı** varlık sınıfları oluşturma (**proje** > **Add New Item**  >  **ADO.NET varlık veri modeli**).  
  
 ![Yeni varlık çerçevesi modeli proje öğesi](../data-tools/media/raddata-new-entity-framework-model-project-item.png "raddata yeni Entity Framework modelini proje öğesi")  
  
 Model oluşturmak istediğiniz yöntemi seçin.  
  
 ![Varlık veri modeli Sihirbazı](../data-tools/media/raddata-entity-data-model-wizard.png "raddata varlık veri modeli Sihirbazı")  
  
 Model veri kaynağı olarak ekleyin. Oluşturulan sınıflar görünür **veri kaynağı Yapılandırma Sihirbazı** seçtiğinizde **nesneleri** kategorisi.  
  
 ![Veri Kaynağı Yapılandırma Sihirbazı ile varlık sınıfları](../data-tools/media/raddata-data-source-configuration-wizard-with-entity-classes.png "raddata varlık sınıfları ile veri kaynağı Yapılandırma Sihirbazı")  
  
## <a name="data-source-for-a-service"></a>Bir hizmet için veri kaynağı  
 Bir hizmetten veri kaynağı oluşturmak için çalıştırın **veri kaynağı Yapılandırma Sihirbazı** ve **hizmet** veri kaynağı türü. Bu, aslında bir kısayol **hizmet Başvurusu Ekle** projeye sağ tıklayarak erişebileceğiniz iletişim kutusu **Çözüm Gezgini** seçerek **hizmet Başvurusu Ekle** .  
  
 Bir hizmetten bir veri kaynağı oluşturduğunuzda, Visual Studio projenize bir hizmet başvurusu ekler. Visual Studio hizmetin döndürdüğü nesnelere karşılık gelen proxy nesnelerini de oluşturur. Örneğin, bir veri kümesi döndüren bir hizmet projenizde bir veri kümesi olarak temsil edilir; belirli bir tür, projenizdeki tür olarak temsil edilir döndürülen hizmet.  
  
 Aşağıdaki tür hizmetlerden veri kaynağı oluşturabilirsiniz:  
  
-   WCF Veri Hizmetleri. Daha fazla bilgi için [genel bakış](http://msdn.microsoft.com/library/7924cf94-c9a6-4015-afc9-f5d22b1743bb).  
  
-   WCF Veri Hizmetleri. Daha fazla bilgi için [Windows Communication Foundation Hizmetleri ve Visual Studio'da WCF Veri Hizmetleri](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md).  
  
-   Web Hizmetleri.  
  
    > [!NOTE]
    >  Görünen öğeler **veri kaynakları** penceresi, bağımlı hizmetin döndürdüğü verileri. Bazı hizmetler için yeterli bilgi sağlamayabilir **veri kaynağı Yapılandırma Sihirbazı** bağlanabilir nesneleri oluşturmak için. Hizmet yazılmamış bir veri kümesi döndürürse, örneğin, hiçbir öğe görünmez **veri kaynakları** Sihirbazı tamamladığınızda penceresi. Yazılmayan veri kümeleri, bir şema sağlamaması ve bu nedenle sihirbazın veri kaynağını oluşturmak için yeterli bilgi yok nedeni budur.  
  
## <a name="data-source-for-an-object"></a>Bir nesne için veri kaynağı  
 Bir veya daha fazla ortak özellik gösteren herhangi bir nesneden bir veri kaynağı oluşturabilirsiniz **veri kaynağı Yapılandırma Sihirbazı** seçip **nesne** veri kaynağı türü. Bir nesnenin tüm ortak özellikleri görüntülenir **veri kaynakları** penceresi.   Entity Framework kullanan ve bir modeli oluşturulmasını, uygulamanız için veri kaynakları olacak varlık sınıflarının nerede budur.  
  
 Üzerinde **veri nesnelerini seçin** sayfasında, ağaç görünümünde bağlamak istediğiniz nesneleri bulmak için düğümleri genişletin. Ağaç görünümünde, derlemeleri ve projeniz tarafından başvurulan diğer projeleri ve projeniz için düğüm içerir.  
  
 Derleme veya ağaç görünümünde görünmez projesinde bir nesneyi bağlamak isterseniz **Başvuru Ekle** ve **başvuru iletişim kutusunu** derlemeyi veya projeyi bir başvuru eklemek için. Başvuru ekledikten sonra derleme veya proje ağaç görünümüne eklenir.  
  
> [!NOTE]
>  Nesneleri, ağaç görünümünde görünmesi nesnelerinizi içeren proje oluşturmanız gerekebilir.  
  
> [!NOTE]
>  Sürükle ve bırak veri bağlama uygulayan nesneler desteklemek için <xref:System.ComponentModel.ITypedList> veya <xref:System.ComponentModel.IListSource> arabirimi, bir varsayılan oluşturucusu olmalıdır. Aksi takdirde, Visual Studio, veri kaynağı nesnesi başlatılamıyor ve öğe tasarım yüzeyine sürüklediğinizde bir hata görüntülenir.  
  
## <a name="data-source-for-a-sharepoint-list"></a>Veri kaynağı için bir SharePoint listesi  
 Çalıştırarak, bir SharePoint listesinden bir veri kaynağı oluşturabilirsiniz **veri kaynağı Yapılandırma Sihirbazı** seçerek **SharePoint** veri kaynağı türü. SharePoint üzerinden veri sunar [!INCLUDE[ssAstoria](../includes/ssastoria-md.md)], SharePoint veri kaynağı oluşturma hizmetten veri kaynağı oluşturma ile aynıdır. Seçme **SharePoint** öğesi **veri kaynağı Yapılandırma Sihirbazı** açılır **hizmet Başvurusu Ekle** SharePoint veri hizmetine eriştiğiniz, iletişim kutusu SharePoint sunucusuna işaret ederek.  Bu, SharePoint SDK'sını gerektirir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [.NET için Visual Studio veri araçları](../data-tools/visual-studio-data-tools-for-dotnet.md)

