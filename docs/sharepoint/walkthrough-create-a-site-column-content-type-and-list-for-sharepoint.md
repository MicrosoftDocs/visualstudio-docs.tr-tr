---
title: 'İzlenecek yol: bir Site sütunu, içerik türü ve SharePoint için liste oluşturma | Microsoft Docs'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.ListDesigner.GeneralMessageHelp
- Microsoft.VisualStudio.SharePoint.Designers.ListDesigner.ViewModels.ListViewModel.SortingAndGrouping
- VS.SharePointTools.ListDesigner.SortingGrouping
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, list definitions
- SharePoint development in Visual Studio, list instances
- SharePoint development in Visual Studio, fields
- SharePoint development in Visual Studio, content types
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 2fb78f5c40a04bb69d2f95d7f872b05e3d501113
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49900130"
---
# <a name="walkthrough-create-a-site-column-content-type-and-list-for-sharepoint"></a>İzlenecek yol: SharePoint için site sütunu, içerik türü ve liste oluşturma
  Aşağıdaki yordamlar özel SharePoint sitesi sütunlar oluşturma işlemini göstermektedir: veya *alanları*— site sütunlarını kullanan bir içerik türü yanı sıra. Ayrıca, yeni içerik türü kullanan bir liste oluşturma işlemini gösterir.  
  
 Bu izlenecek yol aşağıdaki görevleri içerir:  
  
- [Özel Site sütun oluşturma](#BKMK_CreatingCustSiteCols).  
  
- [Özel bir içerik türünü oluşturma](#BKMK_CreateCustContType).  
  
- [Liste oluşturma](#BKMK_CreateList).  
  
- [Liste oluşturma](#BKMK_CreateList).  
  
- [Uygulamayı test etme](#BKMK_TestApp).  
  
  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Önkoşullar  
 Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:  
  
-   Windows ve SharePoint sürümleri desteklenir.
  
-   Visual Studio.  
  
## <a name="create-custom-site-columns"></a>Özel site sütunları oluşturma
 Bu örnek, bir hastane hastalar yönetmek için bir liste oluşturur. İlk olarak, bir SharePoint projesinde oluşturmalısınız [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] ve aşağıda belirtildiği gibi site sütunlarını ekleyin.  
  
#### <a name="to-create-the-project"></a>Proje oluşturmak için  
  
1.  Üzerinde [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] **dosya** menüsünde seçin **yeni** > **proje**.  
  
2.  İçinde **yeni proje** iletişim kutusunda, ya da altında **Visual C#** veya **Visual Basic**, genişletme **SharePoint** düğümünü seçin**2010**.  
  
3.  İçinde **şablonları** bölmesinde seçin **SharePoint 2010 projesi**, proje adını değiştirmek **Clinic**ve ardından **Tamam** düğmesi.  
  
     Bu örnekte, site sütunlarını ve daha sonra eklenen diğer proje öğeleri kapsamak için kullanılmış boş bir proje SharePoint 2010 proje şablonudur.  
  
4.  Üzerinde **hata ayıklama için site ve güvenlik düzeyini belirtin** sayfasında, yeni özel alan öğesi eklemek istediğiniz yerel SharePoint sitesinin URL'sini girin veya varsayılan konumu kullanın (`http://<`*SystemName* `>/)`.  
  
5.  İçinde **bu SharePoint çözümünün güven düzeyi nedir?** bölümünde, varsayılan değeri kullanın **bir korumalı çözüm olarak Dağıt**.  
  
     Korumalı hakkında daha fazla bilgi ve Grup çözümleri için bkz [korumalı çözümle ilgili konular](../sharepoint/sandboxed-solution-considerations.md).  
  
6.  Seçin **son** düğmesi. Proje içinde artık listelenmelidir **Çözüm Gezgini**.  
  
#### <a name="to-add-site-columns"></a>Site sütunları eklemek için  
  
1.  Yeni bir site sütunu ekleyin. Bunu yapmak için **Çözüm Gezgini**, kısayol menüsünü açın **Clinic**ve ardından **Ekle** > **yeni öğe**.  
  
2.  İçinde **Yeni Öğe Ekle** iletişim kutusunda **Site sütunu**, adla değiştirin **hasta adı**ve ardından **Ekle** düğmesi.  
  
3.  Site sütunun içinde *Elements.xml* bırakın, dosya **türü** olarak ayarlama **metin**, değiştirip **grubu** ayarını  **Clinic Site sütunları**. Tamamlandığında, site sütunun *Elements.xml* dosya, aşağıdaki örnekteki gibi görünmelidir.  
  
    ```xml  
    <Field  
         ID="{f9ba60d1-5631-41fb-b016-a38cf48eef63}"  
         Name="Clinic - Patient Name"  
         DisplayName="Patient Name"  
         Type="Text"  
         Required="FALSE"  
         Group="Clinic Site Columns">  
    </Field>  
    ```  
  
4.  Aynı yordamı kullanarak, iki daha fazla site sütunları projeye ekleyin: **hasta kimliği** (tür = "Tamsayı") ve **Doktor adı** (tür = "Text"). Grup değerlerine ayarlayın **Clinic Site sütunları**.  
  
## <a name="create-a-custom-content-type"></a>Özel bir içerik türü oluştur
 Ardından, içerik türü oluşturun — kişiler içerik türe göre — önceki yordamda oluşturduğunuz site sütunları içerir. Mevcut bir içerik türünde bir içerik türü almasını sağlayarak, temel içerik türü kullanılmak üzere yeni içerik türü birden fazla site sütunları sağladığından zamandan tasarruf edebilirsiniz.  
  
#### <a name="to-create-a-custom-content-type"></a>Özel bir içerik türü oluşturmak için  
  
1.  Bir içerik türü, projeye ekleyin. Bunu yapmak için **Çözüm Gezgini**, proje düğümünü seçin  
  
2.  Menü çubuğunda, **proje** > **Yeni Öğe Ekle**.  
  
3.  Ya da altında **Visual C#** veya **Visual Basic**, genişletme **SharePoint** düğümünü seçip **2010** düğümü.  
  
4.  İçinde **şablonları** bölmesinde seçin **içerik türü** şablon adla değiştirin **hasta bilgileri**ve ardından **Ekle** düğmesi.  
  
     **SharePoint Özelleştirme Sihirbazı** açılır.  
  
5.  İçinde **bu içerik türü hangi temel içerik türü devralınan** listesinde **kişi** hakkında yeni içerik türü temel ve ardından istediğiniz içerik türü olarak **Son**düğmesi.  
  
     Bunun yapılması, daha önce tanımladığınız site sütunlarını yanı sıra kişi içerik türü diğer faydalı olabilecek site sütunlara erişmenizi sağlar.  
  
6.  Sonra içerik türü Tasarımcısı görünen **sütunları** sekmesinde, üç site daha önce tanımlanan sütunları ekleyin: **hasta adı**, **hasta kimliği**ve **Doktor adı**. Bu sütunlar eklemek için site sütunları listesinde ilk liste kutusunu seçin. **görünen ad**, her bir site sütunu aynı anda listeden birini seçin.  
  
    > [!TIP]  
    >  Daha hızlı bir şekilde site sütunları seçmek için sütunun adını ilk birkaç harfini girerek listeyi filtreleyin.  
  
7.  Üç özel site sütunu ek olarak, ekleme **açıklamaları** site sütunları listeden site sütunu.  
  
8.  Seçin **gerekli** onay kutusunu **hasta adı** ve **hasta kimliği** bunları yapmak için site sütunları alanları gereklidir.  
  
9. Üzerinde **içerik türü** sekme, içerik türü adı olduğundan emin olun **hasta bilgileri**ve sonra açıklamayı değiştirin **hasta bilgi kartını**.  
  
10. Değişiklik **grup adı** için **Clinic içerik türleri**ve diğer ayarları varsayılan değerlerinde bırakın.  
  
11. Menü çubuğunda, **dosya** > **Tümünü Kaydet**ve ardından içerik türü Tasarımcısı'nı kapatın.  
  
## <a name="create-a-list"></a>Bir liste oluşturun
 Şimdi yeni içerik türü ve site sütunlarını kullanan bir liste oluşturun.  
  
#### <a name="to-create-a-list"></a>Bir liste oluşturmak için  
  
1.  Bir liste projeye ekleyin. Bunu yapmak için **Çözüm Gezgini**, proje düğümünü seçin.  
  
2.  Menü çubuğunda, **proje** > **Yeni Öğe Ekle**.  
  
3.  Ya da altında **Visual C#** veya **Visual Basic**, genişletme **SharePoint** düğümünü seçip **2010** düğümü.  
  
4.  İçinde **şablonları** bölmesinde seçin **listesi** şablon adla değiştirin **Hastalara**ve ardından **Ekle** düğmesi.  
  
5.  Bırakın **dayanan liste özelleştirme** olarak ayarlama **varsayılan (boş)** ve ardından **son** düğmesi.  
  
6.  Liste Tasarımcısı'nda **içerik türleri** görüntülemek için düğmeyi **içerik türü ayarlarını** iletişim kutusu.  
  
7.  Yeni satır seçin, **hasta bilgileri** içerik türü listesinde içerik türleri ve ardından **Tamam** düğmesi.  
  
     Bunun yapılması, ekler tüm site sütunlarını **hasta bilgileri** içerik listeye türü.  
  
8.  Tüm site sütunlar listesinde aşağıdaki istisnalar dışında silin:  
  
    -   Hasta kimliği  
  
    -   Hasta adı  
  
    -   Ev Telefonu  
  
    -   E-posta  
  
    -   Hastanede adı  
  
    -   Açıklamalar  
  
9. Altında **sütun görünen adı**, boş bir satırı seçin, bir özel liste sütun ekleyin ve adlandırın **hastane**. Kendi veri türü bırakın **tek satır metin**.  
  
     Özel liste sütun bu listede yalnızca geçerlidir. Özel liste sütunu bir listesine eklediğinizde, listeye eklenen tüm sütunları içeren yeni bir liste içerik türü, oluşturulur ve varsayılan liste olarak ayarlayın.  
  
    > [!TIP]  
    >  Site sütunlar listesinden bir sütun seçerseniz, varolan bir site sütunu kullanılır. Hiçbir sütun listesinde seçerek olmadan bir sütun adı değerini girerseniz, aynı ada sahip bir sütun zaten listede mevcut olsa bile ancak bir özel liste sütunu oluşturulur.  
  
     İsteğe bağlı olarak, özel liste sütunu için veri türünü ayarlamak yerine **tek satır metin**, arama için bunun yerine bu sütunun veri türünü ayarlayabilirsiniz ve değerlerinin bir tablo ya da başka bir listeye alınması. Arama sütunları hakkında daha fazla bilgi için bkz. [listesi ilişkileri SharePoint 2010'daki](http://go.microsoft.com/fwlink/?LinkId=224994) ve [aramalar ve liste ilişkileri](http://go.microsoft.com/fwlink/?LinkID=224995).  
  
10. Yanındaki **hasta kimliği** ve **hasta adı** kutularında seçme **gerekli** onay kutusu.  
  
11. Üzerinde **görünümleri** sekmesinde, bir görünüm oluşturmak için boş bir satırı seçin. Girin **Hastaların ayrıntılarını**.  
  
     Üzerinde **görünümleri** sekmesinde, SharePoint listesinde görünmesini istediğiniz sütunları belirtebilirsiniz.  
  
12. Yeni seçin **hasta ayrıntıları** satır ve ardından **varsayılan olarak ayarla** düğmesi.  
  
     Yeni görünüm listesi için varsayılan görünümü sunulmuştur.  
  
13. Aşağıdaki sütunları ekleyin **seçili sütun** aşağıdaki sırayla listesi:  
  
    -   Hasta kimliği  
  
    -   Hasta adı  
  
    -   Ev Telefonu  
  
    -   E-posta  
  
    -   Hastanede adı  
  
    -   Hastane  
  
    -   Açıklamalar  
  
14. İçinde **özellikleri** listesinde **sıralamasını ve gruplandırmasını** özelliği ve ardından üç nokta düğmesini ![üç nokta simgesine](../sharepoint/media/ellipsisicon.gif "üç nokta simgesine")görüntülenecek **sıralamasını ve gruplandırmasını** iletişim kutusu.  
  
15. İçinde **sütun adı** listesinde **hasta adı**, emin **sıralama** sütun ayarlanmış **artan**, seçin **Tamam** düğmesi.  
  
## <a name="test-the-application"></a>Uygulamayı test etme
 Özel site sütunları, içerik türü ve liste hazır olduğuna göre bunları SharePoint'e dağıtmak ve test etmek için uygulamayı çalıştırın.  
  
#### <a name="to-test-the-application"></a>Uygulamayı test etmek için  
  
1.  Menü çubuğunda, **dosya** > **Tümünü Kaydet**.  
  
2.  Seçin **F5** uygulamayı çalıştırmak için anahtar.  
  
     Uygulama derlendiğinde ve ardından özelliklerini SharePoint'e dağıtılan ve etkinleştirilen.  
  
3.  Hızlı bir gezinti çubuğunda, **Hastalara** görüntülemek için bağlantıyı **Hastalara** listesi.  
  
     Sütun adları listesi, girdiğiniz eşleşmelidir **görünümleri** sekmesinde [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
4.  Seçin **Yeni Öğe Ekle** hasta bilgi kartını oluşturmak için bağlantı.  
  
5.  Alanlara bilgileri girin ve ardından **Kaydet** düğmesi.  
  
     Yeni kayıt listesinde görünür.  
  
## <a name="see-also"></a>Ayrıca bkz.
 [SharePoint için site sütunları, içerik türleri ve listeler oluşturma](../sharepoint/creating-site-columns-content-types-and-lists-for-sharepoint.md)   
 [SharePoint çözümleri geliştirme](../sharepoint/developing-sharepoint-solutions.md)   
 [Nasıl yapılır: özel alan türü oluşturma](http://go.microsoft.com/fwlink/?LinkId=192079)   
 [İçerik türleri](http://go.microsoft.com/fwlink/?LinkId=192080)   
 [Sütunları](http://go.microsoft.com/fwlink/?LinkId=192081)  
  
