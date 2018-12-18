---
title: Yeni veri kaynağı ekleme
ms.date: 11/21/2018
ms.topic: conceptual
f1_keywords:
- vs.datasource.datasourcefieldspicker
helpviewer_keywords:
- data [Visual Studio], data sources
- data sources
ms.assetid: ed28c625-bb89-4037-bfde-cfa435d182a2
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: fe32424632d06ed637b41dcd3d4b614afde369bd
ms.sourcegitcommit: 81e9d90843ead658bc73b30c869f25921d99e116
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2018
ms.locfileid: "52304616"
---
# <a name="add-new-data-sources"></a>Yeni veri kaynağı ekleme

Visual Studio'da .NET veri Araçları'nın içeriğinde terimi *veri kaynağı* bir veri deposuna bağlanmak ve verileri, bir .NET uygulaması kullanımına .NET nesneleri gösterir. Visual Studio tasarımcıları, veritabanı nesnelerini sürükleyip yükleyen Veri formları bağlayan ortak kod oluşturmak için veri kaynağı çıkışını tüketebileceği **veri kaynakları** penceresi. Bu türdeki veri kaynağının olabilir:

- Bazı tür veritabanı ile ilişkili bir Entity Framework modelini sınıfta.

- Bazı tür veritabanı ile ilişkili bir veri kümesi.

- Bir Windows Communication Foundation (WCF) veri hizmeti veya bir REST hizmeti gibi bir ağ hizmeti temsil eden sınıf.

- SharePoint hizmet temsil eden sınıf.

- Bir sınıf veya çözümünüzdeki koleksiyonu.

> [!NOTE]
> Veri bağlama özellikleri kullanmıyorsanız, veri kümeleri, Entity Framework, LINQ to SQL, WCF ya da SharePoint, "veri kaynağı" kavramını geçerli değildir. Yalnızca SQLCommand nesnesi kullanarak veritabanına doğrudan bağlanmak ve veritabanıyla doğrudan iletişim kurar.

Oluşturma ve kullanarak veri kaynaklarını düzenleme **veri kaynağı Yapılandırma Sihirbazı** bir Windows Forms veya Windows Presentation Foundation uygulaması içinde. Entity Framework için ilk, varlık sınıfları oluşturun ve ardından seçerek Sihirbazı başlatın **proje** > **yeni veri kaynağı Ekle** (Bu makalenin sonraki bölümlerinde daha ayrıntılı açıklanmıştır).

![Veri Kaynağı Yapılandırma Sihirbazı](../data-tools/media/data-source-configuration-wizard.png)

## <a name="data-sources-window"></a>Veri Kaynakları penceresi

Bir veri kaynağı oluşturduktan sonra görünür **veri kaynakları** araç penceresi.

> [!TIP]
> Açmak için **veri kaynakları** penceresinde projenizi açık olduğundan emin olun ve tuşuna **Shift**+**Alt**+**D**veya **görünümü** > **diğer Windows** > **veri kaynakları**.

Bir veri kaynağından sürükleyebilirsiniz **veri kaynakları** penceresinden bir form Tasarım yüzeyine veya denetimi. Bu verileri veri deposundan görüntüleyen oluşturulacak ortak kod neden olur.

Aşağıdaki çizimde, bir Windows forma bırakılan bir veri kümesi gösterir. Seçerseniz **F5** uygulamayı, veritabanından alınan veri form denetimlerinde görüntülenir.

![Veri kaynağı sürükleme işlemi](../data-tools/media/raddata-data-source-drag-operation.png)

## <a name="data-source-for-a-database-or-a-database-file"></a>Veri kaynağı için bir veritabanı veya veritabanı dosyası

Bir veri kümesi veya bir veritabanı veya veritabanı dosyası için bir veri kaynağı olarak kullanılacak bir Entity Framework modelini oluşturabilirsiniz.

### <a name="dataset"></a>Veri kümesi

Veri kaynağı olarak bir veri kümesi oluşturmak için çalıştırılması **veri kaynağı Yapılandırma Sihirbazı** seçerek **proje** > **yeni veri kaynağı Ekle**. Seçin **veritabanı** veri kaynağı türü ve yeni veya var olan veritabanı bağlantısı veya veritabanı dosyası belirtmek için istemleri takip edin.

### <a name="entity-classes"></a>Varlık sınıfları

Veri kaynağı olarak bir Entity Framework modelini oluşturmak için:

1. Çalıştırma **varlık veri modeli Sihirbazı** varlık sınıfları oluşturmak için. Seçin **proje** > **Add New Item** > **ADO.NET varlık veri modeli**.

   ![Yeni varlık çerçevesi modeli proje öğesi](../data-tools/media/raddata-new-entity-framework-model-project-item.png)

1. Model tarafından oluşturulmasını istediğiniz yöntemi seçin.

   ![Varlık veri modeli Sihirbazı](../data-tools/media/raddata-entity-data-model-wizard.png)

1. Model veri kaynağı olarak ekleyin. Oluşturulan sınıflar görünür **veri kaynağı Yapılandırma Sihirbazı** seçtiğinizde **nesneleri** kategorisi.

   ![Veri Kaynağı Yapılandırma Sihirbazı ile varlık sınıfları](../data-tools/media/raddata-data-source-configuration-wizard-with-entity-classes.png)

## <a name="data-source-for-a-service"></a>Bir hizmet için veri kaynağı

Bir hizmetten veri kaynağı oluşturmak için çalıştırın **veri kaynağı Yapılandırma Sihirbazı** ve **hizmet** veri kaynağı türü. Bu, yalnızca bir kısayol **hizmet Başvurusu Ekle** projeye sağ tıklayarak erişebileceğiniz iletişim kutusu **Çözüm Gezgini** seçerek **hizmetBaşvurusuEkle**.

Bir hizmetten bir veri kaynağı oluşturduğunuzda, Visual Studio projenize bir hizmet başvurusu ekler. Visual Studio hizmetin döndürdüğü nesnelere karşılık gelen proxy nesnelerini de oluşturur. Örneğin, bir veri kümesi döndüren bir hizmet projenizde bir veri kümesi olarak temsil edilir; belirli bir tür, projenizdeki tür olarak temsil edilir döndürülen hizmet.

Aşağıdaki tür hizmetlerden veri kaynağı oluşturabilirsiniz:

- [WCF Veri Hizmetleri](/dotnet/framework/data/wcf/wcf-data-services-overview)

- [WCF hizmetleri](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)

- Web hizmetleri

    > [!NOTE]
    > Görünen öğeler **veri kaynakları** penceresi, bağımlı hizmetin döndürdüğü verileri. Bazı hizmetler için yeterli bilgi sağlamayabilir **veri kaynağı Yapılandırma Sihirbazı** bağlanabilir nesneleri oluşturmak için. Hizmet yazılmamış bir veri kümesi döndürürse, örneğin, hiçbir öğe görünür **veri kaynakları** Sihirbazı tamamladığınızda penceresi. Yazılmayan veri kümeleri, bir şema sağlamaması ve bu nedenle sihirbazın veri kaynağını oluşturmak için yeterli bilgi yok nedeni budur.

## <a name="data-source-for-an-object"></a>Bir nesne için veri kaynağı

Bir veya daha fazla ortak özellik gösteren herhangi bir nesneden bir veri kaynağı oluşturabilirsiniz **veri kaynağı Yapılandırma Sihirbazı** seçip **nesne** veri kaynağı türü. Bir nesnenin tüm ortak özellikleri görüntülenir **veri kaynakları** penceresi. Entity Framework kullanan ve bir modeli oluşturulmasını, uygulamanız için veri kaynakları varlık sınıflarının nerede budur.

Üzerinde **veri nesnelerini seçin** sayfasında, ağaç görünümünde bağlamak istediğiniz nesneleri bulmak için düğümleri genişletin. Ağaç görünümünde, derlemeleri ve projeniz tarafından başvurulan diğer projeleri ve projeniz için düğüm içerir.

Derleme veya ağaç görünümünde görünmez projesinde bir nesneyi bağlamak isterseniz **Başvuru Ekle** ve **başvuru iletişim kutusunu** derlemeyi veya projeyi bir başvuru eklemek için. Başvuru ekledikten sonra derleme veya proje ağaç görünümüne eklenir.

> [!NOTE]
> Nesneleri, ağaç görünümünde görünmesi nesnelerinizi içeren proje oluşturmanız gerekebilir.

> [!NOTE]
> Sürükle ve bırak veri bağlama uygulayan nesneler desteklemek için <xref:System.ComponentModel.ITypedList> veya <xref:System.ComponentModel.IListSource> arabirimi, bir varsayılan oluşturucusu olmalıdır. Aksi takdirde, Visual Studio, veri kaynağı nesnesi başlatılamıyor ve öğe tasarım yüzeyine sürüklediğinizde bir hata görüntüler.

## <a name="data-source-for-a-sharepoint-list"></a>Veri kaynağı için bir SharePoint listesi

Çalıştırarak, bir SharePoint listesinden bir veri kaynağı oluşturabilirsiniz **veri kaynağı Yapılandırma Sihirbazı** seçerek **SharePoint** veri kaynağı türü. SharePoint veri kaynağı oluşturma hizmetten veri kaynağı oluşturma ile aynı olacak şekilde SharePoint verilerini WCF veri hizmetleri sunar. Seçme **SharePoint** öğesi **veri kaynağı Yapılandırma Sihirbazı** açılır **hizmet Başvurusu Ekle** SharePoint veri hizmetine eriştiğiniz, iletişim kutusu SharePoint sunucusuna işaret ederek. Bu, SharePoint SDK'sını gerektirir.

## <a name="see-also"></a>Ayrıca bkz.

- [.NET için Visual Studio veri araçları](../data-tools/visual-studio-data-tools-for-dotnet.md)