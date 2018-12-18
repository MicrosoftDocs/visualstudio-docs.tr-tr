---
title: 'İzlenecek yol: Proje Görev listesi tanımını dağıtma | Microsoft Docs'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, deploying
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 0e0a0338f14ecdea36c5a5678a42a76ae234bb6d
ms.sourcegitcommit: 1ab675a872848c81a44d6b4bd3a49958fe673c56
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2018
ms.locfileid: "44280369"
---
# <a name="walkthrough-deploy-a-project-task-list-definition"></a>İzlenecek yol: Proje Görev listesi tanımını dağıtma

Bu izlenecek yol size nasıl kullanılacağını gösterir [!INCLUDE[vs_dev11_long](../sharepoint/includes/vs-dev11-long-md.md)] oluşturmak için özelleştirme, hata ayıklama ve proje görevlerini izlemek için bir SharePoint listesi dağıtın.

[!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Önkoşullar

- Microsoft Windows ve SharePoint sürümleri desteklenir.

- Visual Studio 2017 veya Azure DevOps Hizmetleri.

## <a name="create-a-sharepoint-list"></a>Bir SharePoint listesi oluşturun

Bir SharePoint listesi projesi oluşturun ve liste tanımı görevleri ile ilişkilendirin.

1. Açık **yeni proje** iletişim kutusunda **SharePoint** düğümünü seçip **2010** düğümü.

2. İçinde **şablonları** bölmesinde seçin **SharePoint 2010 projesi** şablon, proje adı **ProjectTaskList**ve ardından **Tamam**düğmesi.

     **SharePoint Özelleştirme Sihirbazı** görünür.

3. Hata ayıklama için kullandığınız Yerel SharePoint sitesini belirtmek seçin **Grup çözümü olarak Dağıt** seçenek düğmesini ve ardından **son** düğmesi.

4. Proje için kısayol menüsünü açın ve ardından **Ekle** > **yeni öğe**.

5. İçinde **şablonları** bölmesinde seçin **listesi** şablonu seçip **Ekle** düğmesi.

     **SharePoint Özelleştirme Sihirbazı** görünür.

6. İçinde **hangi adı görüntülemek için listenizi istiyor musunuz?** kutusuna **proje görev listesi**.

7. Seçin **bir varolan liste türüne göre özelleştirilemeyen bir liste oluşturmak** seçenek düğmesini ve ardından, kendi listesinde **görevleri**ve ardından **son** düğmesi.

     Liste, özellik ve paket görünür **Çözüm Gezgini**.

## <a name="add-an-event-receiver"></a>Bir olay alıcısı Ekle

Görev listesinde vadesi otomatik olarak ayarlayan bir olay alıcısı ekleyebilirsiniz tarih ve görev açıklaması. Aşağıdaki yordamda, bir olay alıcısı liste örneği için bir basit olay işleyici ekler.

1. Proje düğümü için kısayol menüsünü açın, **Ekle**ve ardından **yeni öğe**.

2. SharePoint şablonları listesinde seçin **olay alıcısı** şablonu ve ardından ad **ProjectTaskListEventReceiver**.

     **SharePoint Özelleştirme Sihirbazı** görünür.

3. Üzerinde **olay alıcısı ayarlarını seçin** sayfasında **liste öğesi etkinlikleri** olay alıcı türü olarak **ne tür bir olay alıcısı istiyorsunuz** listesi.

4. İçinde **olay kaynağı hangi öğe olmalıdır** listesinde **görevleri**.

5. Olayları işlemek için listesinde yanındaki onay kutusunu işaretleyin **bir öğe eklendikten sonra**ve ardından **son** düğmesi.

     Yeni bir olay alıcısı düğüm adlı bir kod dosyası projeye eklenen **ProjectTaskListEventReceiver**.

6. Kodu `ItemAdded` yönteminde **ProjectTaskListEventReceiver** kod dosyası. Her seferinde yeni bir görev eklendiğinde, görevin varsayılan bir son tarih ve açıklama eklenir. Varsayılan son tarih olan 1 Temmuz 2009.

     [!code-vb[SPProjectTaskList#1](../sharepoint/codesnippet/VisualBasic/projecttasklist1/projecttasklisteventreceiver/projecttasklisteventreceiver.vb#1)]
     [!code-csharp[SPProjectTaskList#1](../sharepoint/codesnippet/CSharp/projecttasklist/projecttasklisteventreceiver/projecttasklisteventreceiver.cs#1)]

## <a name="customize-the-project-task-list-feature"></a>Proje Görev listesi özelliğini özelleştirme

Bir SharePoint çözüm oluşturduğunuzda, Visual Studio Proje öğeleri için varsayılan özellikler otomatik olarak oluşturur. Özellik Tasarımcısı'nı kullanarak, SharePoint sitesi için proje görev listesi ayarları özelleştirebilirsiniz.

1. İçinde **Çözüm Gezgini**, genişletme **özellikleri**.

2. Kısayol menüsünü açın **özellik1**ve ardından **Görünüm Tasarımcısı**.

3. İçinde **başlık** kutusuna **proje görev listesi özelliğini**.

4. İçinde **kapsam** listesinde **Web**.

5. İçinde **özellikleri** penceresinde girin **1.0.0.0** değeri olarak **sürüm** özelliği.

## <a name="customize-the-project-task-list-package"></a>Proje Görev listesi paketini özelleştirme

Bir SharePoint projesi oluşturduğunuzda, Visual Studio paketine varsayılan proje öğeleri içeren özellikler otomatik olarak ekler. Paket Tasarımcısını kullanarak, SharePoint sitesi için proje görev listesi ayarları özelleştirebilirsiniz.

1. İçinde **SolutionExplorer**, kısayol menüsünü açın **paket**ve ardından **Görünüm Tasarımcısı**.

2. İçinde **adı** kutusuna **ProjectTaskListPackage**.

3. Seçin **Web sunucusunu sıfırlama** onay kutusu.

## <a name="build-and-test-the-project-task-list"></a>Derleme ve test proje görev listesi

Projeyi çalıştırdığınızda, SharePoint sitesi açılır. Ancak, görev listesinin konumuna el ile gitmeniz gerekir.

1. Seçin **F5** anahtarını oluşturup dağıtmayı, proje görev listesi.

     SharePoint sitesi açılır.

2. Seçin **giriş** sekmesi.

3. Sol Kenar çubuğunda seçin **proje görev listesi** bağlantı.

     Proje Görev listesi sayfası görüntülenir.

4. İçinde **liste Araçları** sekmesini, **öğeleri** sekmesi.

5. İçinde **öğeleri** Grup öğesini **yeni öğe** düğmesi.

6. İçinde **başlık** metin kutusuna **Task1**.

7. Seçin **Kaydet** düğmesi.

     Site yenilendikten sonra **Task1** görev son tarihi 1/7/2009 görünür.

8. Seçin **Task1**.

     Görev öğesinin ayrıntılı görünümünü görünür ve "Kritik görev budur." açıklamayı gösterir

## <a name="deploy-the-project-task-list"></a>Proje Görev listesi dağıtma

Derleme ve test proje görev listesi sonra ona dağıtabilirsiniz *yerel sistem* veya *uzak sistem*. Farklı bir bilgisayara bir uzak sistem bilgileriyse yerel çözüm geliştirilen aynı bilgisayar sistemidir.

### <a name="to-deploy-the-project-task-list-to-the-local-system"></a>Proje Görev listesi için yerel sistemi dağıtmak için

Visual Studio menü çubuğunda **derleme** > **çözüm dağıtma**.

Visual Studio IIS uygulama havuzunu geri dönüştüren, çözümün var olan tüm sürümlerini geri çeker, çözüm paketine kopyalar (*.wsp*) dosyası için SharePoint ve ardından özelliklerini etkinleştirir. Artık, SharePoint'te bir çözüm kullanabilirsiniz. Dağıtım yapılandırma adımları hakkında daha fazla bilgi için bkz: [nasıl yapılır: SharePoint dağıtım yapılandırmasını düzenleme](../sharepoint/how-to-edit-a-sharepoint-deployment-configuration.md).

### <a name="to-deploy-the-project-task-list-to-a-remote-system"></a>Uzak bir sisteme proje görev listesi dağıtmak için

1. Visual Studio menü çubuğunda **derleme** > **Yayımla**.

2. İçinde **Yayımla** iletişim kutusunda **dosya sistemi Yayımla** seçenek düğmesini.

     Hedef konumda değiştirebilirsiniz **Yayımla** iletişim kutusunda üç nokta düğmesini seçerek ![üç nokta simgesine](../sharepoint/media/ellipsisicon.gif "üç nokta simgesine") ve ardından başka bir konuma gidin.

3. Seçin **Yayımla** düğmesi.

     A *.wsp* çözüm dosyası oluşturulur.

4. Kopyalama *.wsp* SharePoint uzak sistem için dosya.

5. PowerShell'i `Add-SPUserSolution` uzak SharePoint yükleme paketini yüklemek için komutu. (Küme çözümleri için kullanmak `Add-SPSolution` komutu.)

     Örneğin, `Add-SPUserSolution C:\MyProjects\ProjectTaskList\ProjectTaskList\bin\Debug\ProjectTaskList.wsp`.

6. PowerShell'i `Install-SPUserSolution` çözümü dağıtmak için komutu. (Küme çözümleri için kullanmak `Install-SPSolution` komutu.)

     Örneğin, `Install-SPUserSolution -Identity ProjectTaskList.wsp -Site http://NewSiteName`.

     Uzaktan dağıtım hakkında daha fazla bilgi için bkz. [kullanarak çözüm](http://go.microsoft.com/fwlink/?LinkId=217680) ve [ekleme ve SharePoint 2010'daki PowerShell ile çözümleri dağıtma](http://go.microsoft.com/fwlink/?LinkId=217682).

## <a name="next-steps"></a>Sonraki adımlar

Aşağıdaki konular SharePoint çözümlerini dağıtma ve özelleştirme hakkında daha fazla bilgi edinebilirsiniz:

- [İzlenecek yol: SharePoint için site sütunu, içerik türü ve liste oluşturma](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md)

- [Nasıl yapılır: olay alıcısı oluşturma](../sharepoint/how-to-create-an-event-receiver.md)

- [SharePoint Server 2010 için Windows PowerShell](http://go.microsoft.com/fwlink/?LinkId=217684)

## <a name="see-also"></a>Ayrıca bkz.
[Paketleme ve SharePoint çözümlerini dağıtma](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
