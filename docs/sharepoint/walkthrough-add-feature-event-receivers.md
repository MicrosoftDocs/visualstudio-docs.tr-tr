---
title: 'İzlenecek yol: Özellik Olay alıcıları ekleme | Microsoft Docs'
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
- SharePoint development in Visual Studio, advanced packaging tools
- SharePoint development in Visual Studio, event receivers
- SharePoint development in Visual Studio, feature event receivers
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 4ab2eded41d9416f03592c9346a379f8a276366a
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49948788"
---
# <a name="walkthrough-add-feature-event-receivers"></a>İzlenecek yol: özellik Olay alıcıları ekleme
  Özellik Olay alıcıları SharePoint'te özelliği ile ilgili aşağıdaki olaylardan biri meydana geldiğinde yürütülen yöntemler şunlardır:

- Bir özelliği yüklenir.

- Bir özelliği etkinleştirilir.

- Bir özelliği devre dışı bırakılır.

- Bir özellik kaldırılır.

  Bu yönerge, SharePoint projesindeki bir özellik için bir olay alıcısı ekleneceğini gösterir. Bunu, aşağıdaki görevleri gösterir:

- Boş bir proje özellik olayı alıcısını oluşturuluyor.

- İşleme **FeatureDeactivating** yöntemi.

- Duyuru duyuruları listesine eklemek için SharePoint Proje nesne modelini kullanma.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Önkoşullar
 Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:

-   Microsoft Windows ve SharePoint sürümleri desteklenir.

-   Visual Studio.

## <a name="create-a-feature-event-receiver-project"></a>Bir özelliği olay alıcısı projesi oluşturma
 İlk olarak, özellik olayı alıcısını içeren bir proje oluşturun.

#### <a name="to-create-a-project-with-a-feature-event-receiver"></a>Özellik olayı alıcısını bir proje oluşturmak için

1.  Menü çubuğunda, **dosya** > **yeni** > **proje** görüntülenecek **yeni proje** iletişim kutusu.

2.  Genişletin **SharePoint** ya da düğümünde **Visual C#** veya **Visual Basic**ve ardından **2010** düğümü.

3.  İçinde **şablonları** bölmesinde seçin **SharePoint 2010 projesi** şablonu.

     Hiçbir proje şablonu sahip oldukları özellik Olay alıcıları için bu proje türünü kullanın.

4.  İçinde **adı** kutusuna **FeatureEvtTest**ve ardından **Tamam** görüntülemek için düğmeyi **SharePoint Özelleştirme Sihirbazı**.

5.  Üzerinde **hata ayıklama için site ve güvenlik düzeyini belirtin** sayfasında, yeni özel alan öğesi eklemek istediğiniz sunucu için SharePoint sitesi URL'sini girin veya varsayılan konumu kullanın (http://\<*sistem adı*> /).

6.  İçinde **bu SharePoint çözümünün güven düzeyi nedir?** bölümünde, seçin **Grup çözümü olarak Dağıt** seçenek düğmesini.

     Grup çözümlerini karşı korumalı çözümler hakkında daha fazla bilgi için bkz. [korumalı çözümle ilgili konular](../sharepoint/sandboxed-solution-considerations.md).

7.  Seçin **son** düğmesini ve ardından özellik1 adlı bir özellik altında göründüğüne dikkat edin **özellikleri** düğümü.

## <a name="add-an-event-receiver-to-the-feature"></a>Özelliği olay alıcısı Ekle
 Ardından, özelliği olay alıcısı Ekle ve özellik devre dışı durumunda yürütülen kodu ekleyin.

#### <a name="to-add-an-event-receiver-to-the-feature"></a>Bir olay alıcısı için bir özelliği eklemek için

1.  Özellikler düğümü için kısayol menüsünü açın ve ardından **ekleme özelliği** bir özellik oluşturmak için.

2.  Altında **özellikleri** düğümü için kısayol menüsünü açın **özellik1**ve ardından **olay alıcısı Ekle** özelliği olay alıcısı eklemek.

     Bu, özellik1 altında bir kod dosyası ekler. Ya da bu durumda, isimlendirilmiştir *Feature1.EventReceiver.cs* veya *Feature1.EventReceiver.vb*projenizin geliştirme dilini bağlı olarak.

3.  Projenizi yazılmışsa [!INCLUDE[csprcs](../sharepoint/includes/csprcs-md.md)], zaten yoksa, olay alıcısı üstüne aşağıdaki kodu ekleyin:

     [!code-csharp[SP_FeatureEvt#1](../sharepoint/codesnippet/CSharp/featureevttest2/features/feature1/feature1.eventreceiver.cs#1)]

4.  Olay alıcısı sınıfına olay gibi davranan birçok kılınan yöntemleri içerir. Değiştirin **FeatureDeactivating** aşağıdaki yöntemi:

     [!code-vb[SP_FeatureEvt#2](../sharepoint/codesnippet/VisualBasic/featureevt2vb/features/feature1/feature1.eventreceiver.vb#2)]
     [!code-csharp[SP_FeatureEvt#2](../sharepoint/codesnippet/CSharp/featureevttest2/features/feature1/feature1.eventreceiver.cs#2)]

## <a name="test-the-feature-event-receiver"></a>Test özelliği olay alıcısı
 Ardından, test etmek için özellik devre dışı olup olmadığını **FeatureDeactivating** yöntemi bir duyuruyu SharePoint Duyurular listesi verir.

#### <a name="to-test-the-feature-event-receiver"></a>Özellik olayı alıcısını test etmek için

1.  Projenin değerini **etkin Dağıtım Yapılandırması** özelliğini **Hayır etkinleştirme**.

     Bu özelliğin ayarlanması SharePoint'te etkinleştirmesini özellik engeller ve özellik Olay alıcıları hatalarını ayıklamanıza olanak tanır. Daha fazla bilgi için [hata ayıklama SharePoint çözümleri](../sharepoint/debugging-sharepoint-solutions.md).

2.  Seçin **F5** projeyi çalıştırın ve SharePoint'e dağıtmak için anahtar.

3.  SharePoint Web sayfasının en üstünde açın **Site eylemleri** menüsünü seçip **Site Ayarları**.

4.  Altında **Site eylemleri** bölümünü **Site Ayarları** sayfasında **site özelliklerini Yönet** bağlantı.

5.  Üzerinde **özellikleri** sayfasında **etkinleştirme** düğmesinin yanındaki **FeatureEvtTest özellik1** özelliği.

6.  Üzerinde **özellikleri** sayfasında **devre dışı bırak** düğmesinin yanındaki **FeatureEvtTest özellik1** özelliği ve ardından **bu özelliği devre dışı bırak**  özelliği devre dışı bırakmak için onay bağlantısı.

7.  Seçin **giriş** düğmesi.

     Bir duyurunun göründüğüne dikkat edin **duyuruları** özelliği devre dışı bırakıldıktan sonra listesi.

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: olay alıcısı oluşturma](../sharepoint/how-to-create-an-event-receiver.md)
- [SharePoint çözümleri geliştirme](../sharepoint/developing-sharepoint-solutions.md)