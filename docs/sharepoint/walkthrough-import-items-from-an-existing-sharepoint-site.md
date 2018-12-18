---
title: 'İzlenecek yol: Mevcut bir SharePoint sitesinden öğeleri içeri aktarma | Microsoft Docs'
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
- SharePoint development in Visual Studio, importing items
- importing items [SharePoint development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 86256cdecd878c78c34d7128a05eb7b795067701
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49909763"
---
# <a name="walkthrough-import-items-from-an-existing-sharepoint-site"></a>İzlenecek yol: mevcut bir SharePoint sitesinden öğeleri içeri aktarma
  Bu izlenecek yol bir SharePoint sitesinden öğeleri içeri aktarma gösterir bir [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] SharePoint Proje.  
  
 Bu izlenecek yol aşağıdaki görevleri gösterir:  
  
- Özel site sütunu ekleyerek bir SharePoint sitesi özelleştirme (olarak da bilinen bir *alan*.  
  
- Bir SharePoint sitesi .wsp dosyasına aktarılıyor.  
  
- .Wsp dosyası içine aktararak [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .wsp Import project kullanarak SharePoint.  
  
  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Önkoşullar  
 Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:  
  
-   Desteklenen sürümleri [!INCLUDE[TLA#tla_win](../sharepoint/includes/tlasharptla-win-md.md)] ve SharePoint.  
  
-   Visual Studio.  
  
## <a name="customize-a-sharepoint-site"></a>Bir SharePoint sitesi özelleştirme
 Bu örnekte, oluşturun ve yeni bir site sütunu ekleyerek ve daha sonra kullanmak için başka bir alt oluşturarak SharePoint alt site özelleştirin. Daha sonra ilk alt .wsp dosyaya ve sonra projeyi .wsp İçeri Aktar'ı kullanarak özel site sütunu ikinci alt siteye alın.  
  
#### <a name="to-create-and-customize-a-sharepoint-site"></a>Oluşturmak ve bir SharePoint sitesi özelleştirmek için  
  
1. Http:// gibi bir Web tarayıcısı kullanarak bir SharePoint sitesi açın<em>sistem adı</em>/SitePages/Home.aspx.  
  
2. Bir alt ana SharePoint sitesi oturumu açarak oluşturmak **Site eylemleri** menüsüne ve ardından **Yeni Site**.  
  
3. Sitenin **Oluştur** iletişim kutusunda **boş Site** türü.  
  
4. İçinde **başlık** kutusuna **Site sütunu Test 1**; **URL adı** kutusuna **columntest1**; diğer ayarları, varsayılan olarak bırakın. değerleri; ve ardından **Oluştur** düğmesi.  
  
5. Site oluşturulduktan sonra ana sitenin tarayıcıya geri gezinme http://<em>sistem adı</em>/SitePages/Home.aspx.  
  
6. Yeniden açarak ana SharePoint site dışına boş bir alt site oluşturma **Site eylemleri** menüsünde seçerek **Yeni Site**ve ardından **boş Site** türü.  
  
7. İçinde **başlık** kutusuna **Site sütunu Test 2**; **URL adı** kutusuna **columntest2**; diğer ayarları, varsayılan olarak bırakın. değerleri; ve ardından **Oluştur** düğmesi.  
  
8. İlk alt siteye geri gidin http://<em>SystemName</em>/columntest1/default.aspx.  
  
9. Üzerinde **Site eylemleri** menüsünde seçin **Site Ayarları** Site Ayarları sayfasında görüntülenecek.  
  
10. İçinde **galeriler** bölümünde, seçin **Site sütunları** bağlantı.  
  
11. Üst kısmındaki **Site sütunu galeri** sayfasında **Oluştur** düğmesi.  
  
12. İçinde **sütun adı** kutusuna **Test sütun**, diğer varsayılan değerleri koruyun ve ardından **Tamam** düğmesi.  
  
13. **Test sütun** sütunu görünür özel sütunları başlığı Site sütunu galeride.  
  
## <a name="exporting-the-sharepoint-site"></a>SharePoint sitesi dışarı aktarma
 Ardından, SharePoint öğelerini ve içeri aktarmak istediğiniz öğeleri içeren bir SharePoint kurulumu (.wsp) dosyası elde etmek, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] SharePoint Proje. .Wsp dosyası zaten yoksa, ardından, var olan bir SharePoint sitesinden oluşturmanız gerekir. Bu örnekte, varsayılan SharePoint sitesini .wsp dosyası olarak dışa aktarmak.  
  
> [!IMPORTANT]  
>  Aşağıdaki yordamı gerçekleştirmeden bir çalışma zamanı hatası alırsanız, SharePoint sitesine erişimi olan bir sisteme yordamı uygulamak zorunda.  
  
#### <a name="to-export-an-existing-sharepoint-site"></a>Mevcut bir SharePoint sitesi dışarı aktarmak için  
  
1.  SharePoint sitesi seçin **Site Ayarları** üzerinde **Site eylemleri** Site Ayarları sayfasını görüntülemek için sekmesinde.  
  
2.  İçinde **Site eylemleri** bölümü Site Ayarları sayfasında, seçin **şablon olarak Kaydet site** bağlantı.  
  
3.  İçinde **dosya adı** kutusuna **ExampleSite**hem de **şablon adı** kutusuna **örnek Site**.  
  
4.  Bu örnekte, bırakın **dahil içerik** onay kutusunun işaretini kaldırın.  
  
     Bu kutuyu seçtiğinizde [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] tüm listeleri ve belge kitaplıklarını ve bunların içeriğini .wsp dosyasına kaydeder. Bazı durumlarda kullanışlıdır ancak bu örnek için gerekli değildir.  
  
5.  İşlem başarıyla tamamlandığında seçin **çözüm Galerisi** .wsp dosyasını görüntülemek için bağlantı.  
  
     Daha sonra açık çözüm Galerisi sayfasını görüntülemek için **Site eylemleri** menüsünde seçin **Site Ayarları**, seçin **en üst düzey site ayarlarına gidin** bağlantısını  **Site Koleksiyonu Yönetimi** bölümüne ve ardından **çözümleri** bağlantısını **galeriler** bölümü.  
  
6.  Çözümler, Galerisi'nde **ExampleSite** bağlantı.  
  
7.  İçinde **dosya indirme** iletişim kutusunda **Kaydet** düğmesini yerel sisteminizde dosyanın varsayılan olarak, indirmeler klasörünüze kaydedin.  
  
## <a name="import-the-wsp-file"></a>.Wsp dosyasını içeri aktar
 Olduğuna göre bir *.wsp* (özel site sütunu Test sütun) yeniden, içeri aktarmak istediğiniz öğeyi içeren dosya *.wsp* erişmek için dosya.  
  
#### <a name="to-import-a-wsp-file"></a>.Wsp dosyasını içeri aktarmak için  
  
1. İçinde [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], menü çubuğunda, **dosya** > **yeni** > **proje** görüntülenecek **yeni proje**iletişim kutusu. IDE'nizi menü çubuğundaki Visual Basic geliştirme ayarlarını kullanmaya ayarlanmışsa seçin **dosya** > **yeni proje**.  
  
2. Genişletin **SharePoint** ya da düğümünde **Visual C#** veya **Visual Basic**ve ardından **2010** düğümü.  
  
3. Seçin **SharePoint 2010 çözüm paketini içeri aktar** şablonunda **şablonları** bölmesinde WspImportProject1 olarak projenin adı bırakın ve ardından **Tamam** düğmesi.  
  
    **SharePoint Özelleştirme Sihirbazı** görünür.  
  
4. Üzerinde **hata ayıklama için site ve güvenlik düzeyini belirtin** want [!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)] daha önce oluşturduğunuz ikinci SharePoint alt site için. Yeni özel ekleyeceksiniz http:// öğesi, alan<em>sistem adı</em>/columntest2, o alt sitede.  
  
5. İçinde **bu SharePoint çözümünün güven düzeyi nedir?** bölümünde, seçimi bırakın **bir korumalı çözüm olarak Dağıt**.  
  
6. İçinde **yeni proje kaynağını belirtin** sayfasında, sistem üzerindeki kaydettiğiniz konuma *.wsp* daha önce dosya ve ardından **sonraki** düğmesi.  
  
   > [!NOTE]  
   >  Seçerseniz **son** bu sayfadaki tüm kullanılabilir öğeleri düğmesine *.wsp* dosya içeri aktarılacak.  
  
7. İçinde **içeri aktarılacak öğeleri seçin** kutusunda, tüm dışında listesinde onay kutularını temizleyin **Test sütun**ve ardından **son** düğmesi.  
  
    Liste çok sayıda öğe içerdiğinden, seçebileceğiniz **Ctrl**+**A** anahtarları listesinde, tüm öğeleri seçmek için onay kutularının tümünü temizlemek için boşluk tuşuna basın ve ardından yalnızca onay kutusunu seçin kutusunun yanındaki **Test sütun** öğesi.  
  
    İçeri aktarma işlemi tamamlandığında sonra adlı yeni bir proje **WspImportProject1** oluşturulan adlı bir klasör içeren **alanları**. Özel site sütunu bu klasörde olduğu **Test sütun** ve kendi tanım dosyası *Elements.xml*.  
  
## <a name="deploy-the-project"></a>Projeyi dağıtın
 Son olarak, dağıtım **WspImportProject1** ikinci SharePoint alt site özel site sütunu görüntülemek için daha önce oluşturduğunuz.  
  
#### <a name="to-deploy-the-project"></a>Projeyi dağıtmak için  
  
1.  İçinde [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], seçin **F5** dağıtmak ve çalıştırmak için anahtar *.wsp* projeyi alın.  
  
2.  SharePoint sitesinde açın **Site eylemleri** menüsünü seçip **Site Ayarları** Site Ayarları sayfasında görüntülenecek.  
  
3.  İçinde **galeriler** bölümünde, seçin **Site sütunları** bağlantı.  
  
4.  Ekranı aşağı kaydırarak **özel sütunları** bölümü.  
  
     İlk SharePoint sitesinden içeri aktardığınız özel site sütunu listesinde göründüğüne dikkat edin.  
  
## <a name="see-also"></a>Ayrıca bkz.
 [Mevcut bir SharePoint sitesinden öğeleri içeri aktarma](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)   
 [SharePoint çözümleri geliştirme](../sharepoint/developing-sharepoint-solutions.md)   
 [Web bölümleri veya uygulama sayfaları için yeniden kullanılabilir denetimler oluşturma](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)  
  
