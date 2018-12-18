---
title: 'İzlenecek yol: özel Site iş akışı faaliyeti oluşturma | Microsoft Docs'
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
- custom workflow activities [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, custom workflow activities
- site workflows [SharePoint development in Visual Studio]
- workflow activities [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, site workflows
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 2adb6dd8788027d89a743518adee4425e424ce60
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49894176"
---
# <a name="walkthrough-create-a-custom-site-workflow-activity"></a>İzlenecek yol: özel site iş akışı faaliyeti oluşturma
  Bu izlenecek yol kullanarak bir site düzeyinde iş akışı için özel bir etkinlik oluşturma işlemini gösterir [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. (Yalnızca bir site listesindeki tüm site için site düzeyinde iş akışları uygulayın.) Özel Etkinlik bir yedekleme Duyurular listesi oluşturur ve ardından Duyurular listesi içeriğini buna kopyalar.  
  
 Bu izlenecek yol aşağıdaki görevleri gösterir:  
  
- Site düzeyinde iş akışı oluşturma.  
  
- Bir özel iş akışı etkinliği oluşturma.  
  
- Oluşturma ve bir SharePoint listesi siliniyor.  
  
- Öğeleri bir listeden diğerine kopyalama.  
  
- Hızlı Başlat çubuğunda liste görüntüleniyor.  
  
  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Önkoşullar  
 Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:  
  
-   Desteklenen sürümleri [!INCLUDE[TLA#tla_win](../sharepoint/includes/tlasharptla-win-md.md)] ve SharePoint.
  
-   Visual Studio.  
  
## <a name="create-a-site-workflow-custom-activity-project"></a>Site iş akışı özel aktivite projesi oluşturma
 İlk olarak tutun ve test özel iş akışı etkinliği için bir proje oluşturun.  
  
#### <a name="to-create-a-site-workflow-custom-activity-project"></a>Site iş akışı özel aktivite projesi oluşturmak için  
  
1.  Menü çubuğunda, **dosya** > **yeni** > **proje** görüntülenecek **yeni proje** iletişim kutusu.  
  
2.  Genişletin **SharePoint** ya da düğümünde **Visual C#** veya **Visual Basic**ve ardından **2010** düğümü.  
  
3.  İçinde **şablonları** bölmesinde seçin **SharePoint 2010 projesi** şablonu.  
  
4.  İçinde **adı** kutusuna **AnnouncementBackup**ve ardından **Tamam** düğmesi.  
  
     **SharePoint Özelleştirme Sihirbazı** görünür.  
  
5.  Üzerinde **hata ayıklama için site ve güvenlik düzeyini belirtin** sayfasında **Grup çözümü olarak Dağıt** seçenek düğmesini ve ardından **son** kabul etmek için düğme güven düzeyi ve varsayılan site.  
  
     Bu adım çözümünün güven düzeyi Grup çözümü iş akışı projeleri için kullanılabilir tek seçenek olarak ayarlar.  
  
6.  İçinde **Çözüm Gezgini**, proje düğümünü seçin ve ardından, menü çubuğunda, **proje** > **Yeni Öğe Ekle**.  
  
7.  Ya da altında **Visual C#** veya **Visual Basic**, genişletme **SharePoint** düğümünü seçip **2010** düğümü.  
  
8.  İçinde **şablonları** bölmesinde seçin **sıralı iş akışı (yalnızca Grup çözümü)** şablonu seçip **Ekle** düğmesi.  
  
     **SharePoint Özelleştirme Sihirbazı** görünür.  
  
9. Üzerinde **hata ayıklama için iş akışı adını** sayfasında, varsayılan adı (AnnouncementBackup - Workflow1) kabul edin. İş akışı şablonu türe çeviremezsiniz **Site iş akışı**ve ardından **sonraki** düğmesi.  
  
10. Seçin **son** düğmesini kalan varsayılan ayarları kabul edin.  
  
## <a name="add-a-custom-workflow-activity-class"></a>Bir özel iş akışı etkinlik sınıf ekleyin
 Ardından, özel iş akışı etkinliği kodu içeren projeye bir sınıf ekleyin.  
  
#### <a name="to-add-a-custom-workflow-activity-class"></a>Bir özel iş akışı etkinlik sınıf eklemek için  
  
1.  Menü çubuğunda, **proje** > **Yeni Öğe Ekle** görüntülenecek **Yeni Öğe Ekle** iletişim kutusu.  
  
2.  İçinde **yüklü şablonlar** ağaç görünümü öğesini **kod** düğümünü ve ardından **sınıfı** Şablonu proje öğesi şablonları listesinde. Class1 varsayılan adı kullanın. Seçin **Ekle** düğmesi.  
  
3.  Tüm Class1 kod aşağıdakiyle değiştirin:  
  
     [!code-csharp[SP_AnnBackup#1](../sharepoint/codesnippet/CSharp/announcementbackup/class1.cs#1)]
     [!code-vb[SP_AnnBackup#1](../sharepoint/codesnippet/VisualBasic/announcementbackupvb/class1.vb#1)]  
  
4.  Projeyi kaydedin ve ardından, menü çubuğunda, **derleme** > **Çözümü Derle**.  
  
     Class1 görünür özel bir eylem olarak **araç kutusu** üzerinde **AnnouncementBackup bileşenleri** sekmesi.  
  
## <a name="add-the-custom-activity-to-the-site-workflow"></a>Site iş akışı özel aktivite ekleme
 Ardından, özel kod içeren iş akışına bir etkinlik ekleyin.  
  
#### <a name="to-add-a-custom-activity-to-the-site-workflow"></a>Site iş akışı için özel bir etkinlik eklemek için
  
1.  İş akışı tasarımcısında Tasarım görünümünde Workflow1 açın.  
  
2.  Class1'öğesinden sürükleyin **araç kutusu** altında görünmesi `onWorkflowActivated1` etkinlik veya kısayol menüsünü açın, Class1 seçin **kopyalama**, altındaki kısayol menüsünü açın `onWorkflowActivated1` etkinlik ve ardından **Yapıştır**.  
  
3.  Projeyi kaydedin.  
  
## <a name="test-the-site-workflow-custom-activity"></a>Site iş akışı özel aktivitesi test
 Ardından, projeyi çalıştırın ve site iş akışı başlatın. Özel Etkinlik, bir yedekleme Duyurular listesi oluşturur ve geçerli duyuruları listesinden buna içeriğini kopyalar. Kod ayrıca yedekleme listesini zaten bir oluşturmadan önce mevcut olup olmadığını denetler. Yedek liste zaten varsa, silinir. Kod, bir bağlantı da SharePoint sitesinin Hızlı Başlat çubuğunda yeni listesine ekler.  
  
#### <a name="to-test-the-site-workflow-custom-activity"></a>Site iş akışı özel aktivitesi test etmek için  
  
1.  Seçin **F5** projeyi çalıştırın ve SharePoint'e dağıtmak için anahtar.  
  
2.  Hızlı Başlat çubuğunda **listeler** tüm SharePoint sitesinin kullanılabilir listelerini görüntülemek için bağlantı. Yalnızca bir liste adlı duyuruları fark **duyuruları**.  
  
3.  SharePoint sayfasının en üstünde **Site iş akışları** bağlantı.  
  
4.  Başlangıç yeni iş akışı bölümü altında seçin **AnnouncementBackup - Workflow1** bağlantı. Bu site iş akışı başlar ve özel eylemin kodu çalıştırır.  
  
5.  Hızlı Başlat çubuğunda **duyuruları yedekleme** bağlantı. Dikkat bulunan duyuruların hepsini **duyuruları** listesi bu yeni listesine kopyalanmış.  
  
## <a name="see-also"></a>Ayrıca bkz.
 [Nasıl yapılır: olay alıcısı oluşturma](../sharepoint/how-to-create-an-event-receiver.md)   
 [SharePoint çözümleri geliştirme](../sharepoint/developing-sharepoint-solutions.md)  
  
