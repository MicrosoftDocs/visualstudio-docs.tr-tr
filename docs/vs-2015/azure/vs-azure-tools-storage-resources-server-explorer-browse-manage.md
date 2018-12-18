---
title: Gözat ve Sunucu Gezgini kullanarak depolama kaynaklarını yönetme | Microsoft Docs
description: Göz atma ve Sunucu Gezgini kullanarak depolama kaynaklarını yönetme
author: ghogen
manager: douge
assetId: 658dc064-4a4e-414b-ae5a-a977a34c930d
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 8/24/2017
ms.author: ghogen
ms.openlocfilehash: 00229cd88ddcab4d2d59ae40202620c374415e4b
ms.sourcegitcommit: e481d0055c0724d20003509000fd5f72fe9d1340
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/05/2018
ms.locfileid: "51003725"
---
# <a name="browse-and-manage-storage-resources-by-using-server-explorer"></a>Sunucu Gezgini'ni kullanarak depolama kaynaklarına göz atma ve bu kaynakları yönetme

[!INCLUDE [storage-try-azure-tools](./includes/storage-try-azure-tools.md)]

## <a name="overview"></a>Genel Bakış

Microsoft Visual Studio için Azure Araçları'nı yüklediyseniz, depolama hesaplarınızı blob, kuyruk ve tablo verilerini Azure'a görüntüleyebilirsiniz. Azure **depolama** Sunucu Gezgininde yerel depolama öykünücüsü hesabınız ve diğer Azure depolama hesaplarınızı verileri gösterir.

Sunucu Gezgini Visual Studio'da, menü çubuğunda görüntülemek için seçin **görünümü** > **Sunucu Gezgini**. **Depolama** düğüm altında her bir Azure aboneliği veya bağlı olduğunuz sertifika mevcut tüm depolama hesaplarını gösterir. Depolama hesabınızı görünmüyorsa, bu yönergeleri takip ederek ekleyebileceğiniz [bu makalenin ilerleyen bölümlerinde](#add-storage-accounts-by-using-server-explorer).

Azure SDK 2.7 başlayarak, Cloud Explorer görüntülemek ve Azure kaynaklarınızı yönetmek için de kullanabilirsiniz. Daha fazla bilgi için [Cloud Explorer ile yönetme Azure kaynaklarını](vs-azure-tools-resources-managing-with-cloud-explorer.md).

## <a name="view-and-manage-storage-resources-in-visual-studio"></a>Visual Studio'da depolama kaynakları görüntüleme ve yönetme

Sunucu Gezgini, depolama öykünücüsü hesabınızdaki BLOB'lar, kuyruklar ve tablolar listesini otomatik olarak gösterir. Depolama öykünücüsü hesabı altında Sunucu Gezgini içinde listelenen **depolama** düğümü olarak **geliştirme** düğümü.

Depolama öykünücüsü hesabının kaynakları görmek için genişletin **geliştirme** düğümü. Depolama öykünücüsü genişlettikten başlamadı, **geliştirme** düğümü, otomatik olarak başlar. Bu işlem birkaç saniye sürebilir. Depolama öykünücüsü başlatılırken Visual Studio'nun diğer alanlarında çalışmaya devam edebilirsiniz.

Bir depolama hesabında kaynakları görüntülemek için depolama hesabının Sunucu Gezgininde gördüğünüz genişletin **Blobları**, **kuyrukları**, ve **tabloları** düğümleri.

## <a name="work-with-blob-resources"></a>BLOB kaynakları ile çalışma

**Blobları** düğümü kapsayıcılar için seçilen depolama hesabına bir listesini görüntüler. BLOB kapsayıcıları blob dosyaları içerir ve bu bloblar klasörlere ve alt düzenleyebilirsiniz. Daha fazla bilgi için [net'ten Blob storage kullanma](/azure/storage/blobs/storage-dotnet-how-to-use-blobs).

### <a name="to-create-a-blob-container"></a>Bir blob kapsayıcısı oluşturmak için

1. Kısayol menüsünü açın **Blobları** düğümüne tıklayın ve ardından **Blob kapsayıcısı Oluştur**.
1. İçinde **Blob kapsayıcısı Oluştur** iletişim kutusunda, yeni bir kapsayıcı adını girin.  
1. Enter'ı seçin, klavye veya tıklayabilir veya blob kapsayıcısını kaydetmek için ad alanı dokunun.

   > [!NOTE]
   > Blob kapsayıcısı adı, bir sayı (0-9) ya da küçük harf (a-z) başlaması gerekir.

### <a name="to-delete-a-blob-container"></a>Bir blob kapsayıcısını silmek için

Kaldırın ve ardından istediğiniz blob kapsayıcısı için kısayol menüsünü açın **Sil**.

### <a name="to-display-a-list-of-the-items-in-a-blob-container"></a>Bir blob kapsayıcısını öğelerinin listesini görüntülemek için

Listede bir blob kapsayıcı adı için kısayol menüsünü açın ve ardından **açık**.

Bir blob kapsayıcı içeriğini görüntülediğinizde, blob kapsayıcı görünümü olarak bilinen bir sekmesinde görünür.

![BLOB kapsayıcı görünümü](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC749016.png)

Blob kapsayıcı görünümü sağ üst köşesinde bulunan düğmeleri kullanarak BLOB'ları aşağıdaki işlemleri gerçekleştirebilirsiniz:

* Bir filtre değeri girin ve uygulayın.
* Kapsayıcıdaki blobların listesini yenileyin.
* Bir dosyayı karşıya yükleyin.
* Bir blobu silin. (Bir dosya silindiğinde bir blob kapsayıcısından temel alınan dosya silinmiyor. Bu yalnızca bir blob kapsayıcısından kaldırır.)
* Bir blob açın.
* Bir blobu yerel bilgisayara kaydedin.

### <a name="to-create-a-folder-or-subfolder-in-a-blob-container"></a>Bir klasörü veya alt klasör bir blob kapsayıcısını oluşturmak için

1. Blob kapsayıcısını Cloud Explorer'ı seçin. Kapsayıcı penceresinde **Blob karşıya** düğmesi.

1. İçinde **karşıya yeni dosya** iletişim kutusunda **Gözat** karşıya yüklemek istediğiniz dosyayı belirtmek için düğmesini ve ardından bir klasör adı girin **(isteğe bağlı) klasör** kutusu.

   ![Blob klasörüne bir dosya karşıya yükleme](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC766037.png)

   Aynı adımı takip ederek, kapsayıcı klasörlerinde alt klasörleri ekleyebilirsiniz. Dosya, klasör adı belirtmezseniz, blob kapsayıcısının en üst düzeye karşıya yüklendi. Dosya belirtilen kapsayıcı klasöründe görünür.

   ![Klasör bir blob kapsayıcıya eklendi](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC766038.png)

1. Klasörü çift tıklatın veya klasörün içeriğini görmek için Enter tuşuna basın. Kapsayıcının klasöründe olduğunuzda kapsayıcı köküne seçerek dönebilirsiniz **açık üst dizin** (ok) düğmesini.

### <a name="to-delete-a-container-folder"></a>Bir kapsayıcı klasörü silmek için

Klasördeki tüm dosyaları silin.

Blob kapsayıcıları klasörlerinde sanal klasörler olduğundan, boş bir klasör oluşturulamıyor. Ayrıca dosya içeriğini silmek için bir klasör silinemez, ancak bunun yerine klasörü silmek için bir klasörün tüm içeriğini silmeniz gerekir.

### <a name="to-filter-blobs-in-a-container"></a>Bir kapsayıcıdaki blobları filtrelemek için

Ortak bir önek belirleyerek görüntülenen blobları filtreleyebilirsiniz.

Ön eki girin, örneğin, **hello** filtre metin kutusuna ve ardından **yürütme** (**!**) "hello" ile başlayan blobları düğmesi görünür.

![Filtre metin kutusu](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC519076.png)

Filtre metin kutusuna büyük küçük harfe duyarlıdır ve joker karakterlerle filtrelemeyi desteklemez. BLOB'ları yalnızca ön eke göre filtrelenebilir. Sanal bir hiyerarşide blobları düzenlemek için bir sınırlayıcı kullanıyorsanız öneki bir sınırlayıcı içerebilir. Örneğin, ön ek filtreleme "HelloFabric /" Bu dize ile başlayan tüm BLOB'ları döndürür.

### <a name="to-download-blob-data"></a>BLOB verilerini indirmek için

Cloud Explorer'da, aşağıdaki yöntemlerden birini kullanın:

* Bir veya daha fazla bloblar için kısayol menüsünü açın ve ardından **açık**.
* Blob adı seçin ve ardından **açık** düğmesi.
* Blob adına çift tıklayın.

Bir blob Yükleme ilerlemesini görünür **Azure etkinlik günlüğü** penceresi.

Blob, dosya türü için varsayılan Düzenleyicisi'nde açılır. Dosya türü işletim sistemini algılar, dosyayı yerel olarak yüklenmiş bir uygulamada açılır. Aksi takdirde, blob dosya türü için uygun bir uygulama seçmeniz istenir. Bir blob yüklediğinizde oluşturduğunuz yerel dosya salt okunur olarak işaretlenmiş.

BLOB verilerini yerel olarak önbelleğe alınmış ve Azure Blob Depolama alanında blob son değiştirilme zamanına karşılaştırılarak. Son yüklemenizden sonra blob güncelleştirildiyse, yeniden yüklenir. Aksi takdirde, blob yerel diskten yüklenir.

Varsayılan olarak, bir blob geçici bir dizine yüklenir. Blobları belirli bir dizine indirmek için seçilen blob adları için kısayol menüsünü açın ve seçin **Kaydet**. Bu şekilde bir blob kaydettiğinizde, blob dosyası açık değil ve yerel dosya okuma/yazma öznitelikleri ile oluşturulur.

### <a name="to-upload-blobs"></a>Blobları karşıya yüklemek için

Blobları karşıya yüklemek için seçin **Blob karşıya** kapsayıcıya blob kapsayıcı görünümünde görüntülemek için açık olduğunda düğme.

Karşıya yüklenecek bir veya daha fazla dosyaları seçebilirsiniz ve tüm dosya türlerini karşıya yükleyebilirsiniz. **Azure etkinlik günlüğü** penceresi karşıya yükleme ilerlemesini gösterir. Blob veri ile çalışma hakkında daha fazla bilgi için bkz. [. NET'te Azure Blob Depolama kullanma](http://go.microsoft.com/fwlink/p/?LinkId=267911).

### <a name="to-view-logs-transferred-to-blobs"></a>Blob'lara aktarılan günlükleri görüntülemek için

Azure Tanılama verileri Azure uygulamanızdan günlüğe kaydetmek için kullandığınız ve depolama hesabınıza günlükleri aktardınız, Azure için bu günlükleri oluşturulan kapsayıcı görürsünüz. Özellikle Azure'a dağıtıldıktan, sunucu Gezgini'nde bu günlükleri görüntüleme, uygulamanızdaki sorunları tanımlamak için kolay bir yoludur.

Azure Tanılama hakkında daha fazla bilgi için bkz: [kullanarak Azure Tanılama ile günlük verileri topla](https://msdn.microsoft.com/library/azure/gg433048.aspx).

### <a name="to-get-the-url-for-a-blob"></a>Bir blobu URL'si almak için

Blobun kısayol menüsünü açın ve ardından **kopya URL**.

### <a name="to-edit-a-blob"></a>Bir blob düzenlemek için

Blob seçin ve ardından **açık Blob** düğmesi.

Dosyanın geçici bir konuma indirilir ve yerel bilgisayarda açılır. Blob, değişiklikleri yaptıktan sonra yeniden yükleyin.

## <a name="work-with-queue-resources"></a>Kuyruk kaynaklarını ile çalışma

Depolama Hizmetleri kuyrukları bir Azure depolama hesabında barındırılır. Bulut hizmeti rolleri, ileti geçirme mekanizması tarafından birbirleriyle ve diğer hizmetlerle iletişim kurmak izin vermek için kullanabilirsiniz. Sıranın program aracılığıyla bir bulut hizmeti aracılığıyla ve dış istemciler için bir web hizmeti üzerinden erişebilirsiniz. Sıranın doğrudan Visual Studio'da Sunucu Gezgini kullanarak da erişebilirsiniz.

Kuyrukları kullanan bir bulut hizmeti geliştirdiğinizde, Kuyrukları Oluşturma ve bunlarla etkileşimli olarak geliştirip kodunuzu test ederken çalışmak için Visual Studio'u kullanmayı isteyebilirsiniz.

Sunucu Gezgini'nde, kuyrukları bir depolama hesabında görüntülemek, oluşturmak ve sırayı silmek, iletileri görüntülemek için bir kuyruk açın ve bir kuyruğuna ileti ekleme. Bir kuyruğu görüntüleme açtığınızda, tek bir ileti görüntüleyebilir ve sol üst köşedeki düğmeleri kullanarak sıraya aşağıdaki eylemleri gerçekleştirebilirsiniz:

* Kuyruk görünümü yenileyin.
* Kuyruğa bir ileti ekleyin.
* En üstteki iletiyi sıradan çıkar.
* Kuyruğun tamamı temizleyin.

Aşağıdaki görüntüde, iki ileti içeren bir kuyruk gösterilmektedir:

![Bir kuyruğu görüntüleme](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC651470.png)

Hizmetleri kuyruk depolama hakkında daha fazla bilgi için bkz: [.NET kullanarak Azure kuyruk depolama ile çalışmaya başlama](http://go.microsoft.com/fwlink/?LinkID=264702). Kuyruk depolama hizmetleri için web hizmeti hakkında bilgi için bkz [kuyruk hizmeti kavramları](http://go.microsoft.com/fwlink/?LinkId=264788). Visual Studio kullanarak bir depolama hizmetleri kuyruğa ileti göndermek nasıl hakkında daha fazla bilgi için bkz. [depolama hizmetleri kuyruğuna iletiler gönderme](https://docs.microsoft.com/azure/visual-studio/vs-storage-cloud-services-getting-started-queues).

> [!NOTE]
> Depolama Hizmetleri kuyruklarına, Azure Service Bus sıralarından farklıdır. Service Bus kuyrukları hakkında daha fazla bilgi için bkz: [Service Bus kuyrukları, konular ve abonelikler](https://docs.microsoft.com/azure/service-bus-messaging/service-bus-queues-topics-subscriptions).

## <a name="work-with-table-resources"></a>Tablo kaynakları ile çalışma

Azure tablo depolama, büyük miktarlarda yapısal veriyi depolar. Kimliği doğrulanmış çağrılarından içindeki ve Azure Bulutu dışındaki kabul eden bir NoSQL veri deposu hizmetidir. Azure tabloları, yapılandırılmış ve ilişkisel olmayan verilerin depolanması için idealdir.

### <a name="to-create-a-table"></a>Bir tablo oluşturmak için

1. Bulut Gezgini'nde seçin **tabloları** depolama hesabına tıklayın ve ardından düğümü **Create Table**.
1. İçinde **Create Table** iletişim kutusunda, tablo için bir ad girin.

### <a name="to-view-table-data"></a>Tablo verilerini görüntülemek için

1. Bulut Gezgini'nde açma **Azure** düğümünü ve ardından açın **depolama** düğümü.
1. İlgileniyor ve açın depolama hesabı düğümünü açın **tabloları** düğüm bir depolama hesabı için tabloların listesini görmek için.
1. Bir tablo için kısayol menüsünü açın ve ardından **görünüm tablosu**.

    ![Çözüm Gezgini'nde bir Azure tablosu](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC744165.png)

Tablo, varlıkları (satırlarda gösterilen) ve özellikleri (sütunları gösterilmiştir) göre düzenlenir. Örneğin, bir sonraki çizimde Tablo Tasarımcısı'nda listelenen varlıkları gösterir.

### <a name="to-edit-table-data"></a>Tablo verileri düzenlemek için

Tablo Tasarımcısı'nda bir varlık (tek satır) ya da bir özellik (tek bir hücre) için kısayol menüsünü açın ve ardından **Düzenle**.

    ![Add or edit a table entity](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC656238.png)

Varlıkları tek bir tabloda aynı özellikleri (sütunları) olan gerekli değildir. Görüntüleme ve düzenleme tablo verilerini aşağıdaki kısıtlamaları göz önünde bulundurun:

* Görüntüleyemez veya ikili verileri düzenleme (`type byte[]`), ancak bir tabloya kaydedin.
* Düzenleyemediğiniz **PartitionKey** veya **RowKey** değerleri, çünkü bu işlemi Azure tablo depolamada desteklemez.
* Adlı bir özellik oluşturulamıyor **zaman damgası**. Azure depolama hizmetleri, bu ada sahip bir özelliğini kullanın.
* Girerseniz bir **DateTime** değeri, bilgisayarınızın bölge ve dil ayarları için uygun bir biçimde izlemelidir (örneğin, GG/AA/YYYY SS: dd: [AM | PM] ABD İngilizce için).

### <a name="to-add-entities"></a>Varlık eklemek için

1. Tablo Tasarımcısı'nda seçin **varlık Ekle** düğmesi.

    ![Varlık düğmesi ekleme](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC655336.png)

1. İçinde **varlık Ekle** iletişim kutusunda, değerlerini girin **PartitionKey** ve **RowKey** özellikleri.

    ![Varlık Ekle iletişim kutusu](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC655335.png)

    Değerleri dikkatli bir şekilde girin. Bir varlığı silme ve yeniden ekleyin sürece iletişim kutusunu kapattıktan sonra değiştiremezsiniz.

### <a name="to-filter-entities"></a>Varlıkları filtrelemek için

Sorgu Oluşturucu kullanırsanız, bir tablodaki görünen varlık kümesini özelleştirebilirsiniz.

1. Sorgu tasarımcısını açmak için bir tablo görüntüleme için açın.
1. Seçin **Sorgu Oluşturucu** Tablo görünümünün araç çubuğunda.

    **Sorgu Oluşturucu** iletişim kutusu görüntülenir. Aşağıdaki çizimde, Sorgu Oluşturucu'da oluşturulmakta olan bir sorguyu gösterir.

    ![Sorgu Oluşturucu](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC652231.png)
1. Bitirdiğinizde, sorgu oluşturma iletişim kutusunu kapatın. Sorgu sonuç metin biçiminde metin kutusunda, WCF Veri Hizmetleri filtre olarak görünür.
1. Sorguyu çalıştırmak için yeşil üçgeni simgesini seçin.

Ayrıca, girerseniz filtre metin kutusuna doğrudan bir WCF Veri Hizmetleri filtre dizesi Tablo Tasarımcısı'nda görüntülenen varlık verilerini filtreleyebilirsiniz. Bu tür bir dize, bir SQL WHERE yan tümcesine benzer ancak sunucusu bir HTTP isteği olarak gönderilir. Filtre dizeleri oluşturmak nasıl hakkında daha fazla bilgi için bkz. [Constructing filtre dizeleri için Tablo Tasarımcısı](https://docs.microsoft.com/azure/vs-azure-tools-table-designer-construct-filter-strings).

Geçerli filtre dizesinin aşağıda gösterilmiştir:

![Filtre dizesi](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC655337.png)

## <a name="refresh-storage-data"></a>Depolama veri yenileme

Sunucu Gezgini bağlanır veya bir depolama hesabından verileri alır, işlem bir dakika kadar son kadar sürebilir. Sunucu Gezgini bağlanamıyorsanız, işlemi zaman aşımına uğrayabilir. Veriler alınır, ancak Visual Studio'nun diğer bölümlerinde çalışmaya devam edebilirsiniz. Çok uzun sürüyorsa işlemi iptal etmek için işaretleyin **Yenilemeyi Durdur** Sunucu Gezgini araç çubuğundan.

### <a name="to-refresh-blob-container-data"></a>BLOB kapsayıcı verileri yenilemek için

* Seçin **Blobları** düğümün altında **depolama**ve ardından **Yenile** Sunucu Gezgini araç çubuğundan.
* Görüntülenen BLOB listesini yenilemek için seçin **yürütme** düğmesi.

### <a name="to-refresh-table-data"></a>Tablo verileri yenilemek için

* Seçin **tabloları** düğümün altında **depolama**ve ardından **Yenile** Sunucu Gezgini araç çubuğundan.
* Tablo Tasarımcısı'nda görüntülenen varlıkların listesini yenilemek için seçin **yürütme** Tablo Tasarımcısı'nda düğme.

### <a name="to-refresh-queue-data"></a>Kuyruk verileri yenilemek için

Seçin **kuyrukları** düğümün altında **depolama**ve ardından **Yenile** Sunucu Gezgini araç çubuğundan.

### <a name="to-refresh-all-items-in-a-storage-account"></a>Bir depolama hesabındaki tüm öğeleri yenilemek için

Hesap adı seçin ve ardından **Yenile** Sunucu Gezgini araç çubuğundan.

## <a name="add-storage-accounts-by-using-server-explorer"></a>Sunucu Gezgini kullanarak depolama hesapları ekleme

Sunucu Gezgini kullanarak depolama hesapları eklemek için iki yolu vardır. Azure aboneliğinizde bir depolama hesabı oluşturabilir veya mevcut bir depolama hesabı ekleyebilirsiniz.

### <a name="to-create-a-storage-account-by-using-server-explorer"></a>Sunucu Gezgini kullanarak bir depolama hesabı oluşturmak için

1. Sunucu Gezgini'nde, kısayol menüsünü açın **depolama** düğümüne tıklayın ve ardından **depolama hesabı oluştur**.

1. İçinde **depolama hesabı oluştur** iletişim kutusunda seçin veya aşağıdaki bilgileri girin:

   * Depolama hesabını eklemek istediğiniz Azure aboneliği.
   * Yeni depolama hesabı için kullanmak istediğiniz adı.
   * Bölge veya benzeşim grubunda (örneğin, Batı ABD veya Doğu Asya).
   * Bir tür çoğaltma gibi depolama hesabı için kullanmak istediğiniz yerel olarak yedekli.

   ![Bir Azure depolama hesabı oluşturma](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC744166.png)

1. Seçin **oluşturma**.

Yeni depolama hesabı görünür **depolama** Çözüm Gezgini'nde listesi.

### <a name="to-attach-an-existing-storage-account-by-using-server-explorer"></a>Sunucu Gezgini kullanarak mevcut bir depolama hesabını eklemek için

1. Sunucu Gezgini'nde, Azure için kısayol menüsünü açın **depolama** düğümüne tıklayın ve ardından **dış depolama Ekle**.

    ![Mevcut bir depolama hesabı ekleme](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC766039.png)
1. İçinde **depolama hesabı oluştur** iletişim kutusunda seçin veya aşağıdaki bilgileri girin:

   * Eklemek istediğiniz mevcut bir depolama hesabı adı.
   * Seçili depolama hesabı anahtarı. Bir depolama hesabı seçtiğinizde bu değer genellikle sizin için sağlanır. Visual Studio içinde depolama hesabı anahtarını anımsa istiyorsanız belirleyin **hesap anahtarını anımsa** onay kutusu.
   * HTTP, HTTPS veya özel bir uç noktası gibi bir depolama hesabına bağlanmak için kullanılacak protokolü. Özel uç noktaları hakkında daha fazla bilgi için bkz. [bağlantı dizelerini yapılandırma nasıl](https://msdn.microsoft.com/library/azure/ee758697.aspx).

### <a name="to-view-the-secondary-endpoints"></a>İkincil uç noktaları görüntülemek için

Kullanarak bir depolama hesabı oluşturduysanız **okuma erişimli coğrafi olarak yedekli** çoğaltma seçeneği, kendi ikincil uç hesap adı için kısayol menüsünü açarak görüntüleyebilir ve ardından **özellikleri**.

![Depolama ikincil uç noktaları](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC766040.png)

### <a name="to-remove-a-storage-account-from-server-explorer"></a>Sunucu Gezgini'nden bir depolama hesabını kaldırmak için

Sunucu Gezgini'nde, hesap adı için kısayol menüsünü açın ve ardından **Sil**. 

Bir depolama hesabı silerseniz, bu hesap için kaydedilen tüm anahtar bilgilerini de kaldırılır.

Sunucu Gezgini'nden bir depolama hesabı silerseniz, depolama hesabınıza veya içerdiği herhangi bir veri etkilemez. Yalnızca Sunucu Gezgini'nden başvuruyu kaldırır. Bir depolama hesabı kalıcı olarak silmek için kullanın [Azure portalında](https://portal.azure.com/).

## <a name="next-steps"></a>Sonraki adımlar

Azure Depolama hizmetlerinin nasıl kullanılacağı hakkında daha fazla bilgi için bkz: [Azure depolama hizmetlerine erişilmesi](https://msdn.microsoft.com/library/azure/ee405490.aspx).
