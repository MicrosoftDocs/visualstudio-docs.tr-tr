---
title: SharePoint projesi ve proje öğesi şablonları | Microsoft Docs
ms.custom: ''
ms.date: 02/22/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.SPE.FirstWizardPage
- VS.SharePointTools.SPE.ListInstance
- VS.SharePointTools.SPE.ListDefinition
- VS.SharePointTools.SPE.ListDefFromContentType
- VS.SharePointTools.SPE.ContentType
- SPE.Wizard
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, project and project item templates
- SharePoint development in Visual Studio, templates
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 6e38a3e709a8d49d29d598e7eabd55e7be154836
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49896451"
---
# <a name="sharepoint-project-and-project-item-templates"></a>SharePoint projesi ve proje öğesi şablonları
  Aşağıdaki bölümlerde kullanılabilir SharePoint Proje açıklamak ve proje öğesi şablonları ve bunların nasıl kullanıldığı. 
  
## <a name="project-and-project-item-templates-overview"></a>Proje ve proje öğesi şablonları genel bakış
 Visual Studio'da yeni bir SharePoint projesi oluşturduğunuzda, bir SharePoint projesi çözüme tüm proje türü tarafından gerekli proje öğelerinin birlikte eklenir. Örneğin, bir Silverlight Web Bölümü projesi oluşturursanız, Visual Studio bir görsel Web Bölümü proje öğesi ve bu proje öğeleri tarafından gerekli olan tüm dosyaların yanı sıra bir Silverlight uygulaması proje öğesi içeren bir çözüm oluşturur. Proje öğesi şablonları, bir olay alıcısı, site sütunu veya liste ekleme gibi bir var olan SharePoint projesi, proje öğeleri eklemek için kullanılır.  
  
 SharePoint ile ilgili temel bilgiler hakkında daha fazla bilgi için bkz. [SharePoint Foundation yapı taşlarını](http://go.microsoft.com/fwlink/?LinkId=179404). İleri düzey kullanıcılar özel Proje ve proje öğesi şablonları oluşturabilirsiniz. Daha fazla bilgi için [SharePoint Proje sistemini genişletmek](../sharepoint/extending-the-sharepoint-project-system.md).  
  
## <a name="project-templates"></a>Proje şablonları
 SharePoint proje şablonları listesi aşağıdadır. Visual Studio'da SharePoint proje şablonları görüntülemek için **yeni proje** iletişim kutusunda **SharePoint** ya da düğümünde **Visual C#**  veya  **Visual Basic**ve ardından **2010**.  
  
### <a name="sharepoint-2010-project"></a>SharePoint 2010 projesi
 İçeriği bir *SharePoint 2010 projesi* her SharePoint projesi şablonu içine dahil edilir. SharePoint 2010 projesi içerir:  
  
-   Bir proje dosyası.  
  
-   Proje özellikleri sayfasında.  
  
-   A **başvuruları** tüm derleme başvurularını projedeki listeleyen bir klasör.  
  
-   A **özellikleri** içeren klasörü bir *.feature* özellik SharePoint sunucusuna dağıtmak için kullanılan yapılandırma dosyası.  
  
-   A **paket** içeren klasörü bir *Package.package* SharePoint'e çözümü dağıtmak için kullanılan dosya,.  
  
-   Gelişmiş güvenlik için derlemeyi bir katı adla imzalamak için kullanılan bir key.snk (tanımlayıcı ad anahtarı) dosyası.  
  
### <a name="sharepoint-2010-silverlight-web-part"></a>SharePoint 2010 Silverlight web bölümü
 *SharePoint 2010 Silverlight Web Bölümü* projeleri olanak oluştur web bölümleri için Silverlight uygulamaları görüntülemek için SharePoint. Bu proje oluşturduğunuzda, ona yeni bir Silverlight uygulaması eklemek veya mevcut bir başvuru belirtebilirsiniz. Daha fazla bilgi için [için SharePoint web bölümleri oluşturma](../sharepoint/creating-web-parts-for-sharepoint.md) ve [izlenecek yol: SharePoint için OData görüntüleyen bir Silverlight web bölümü oluşturma](../sharepoint/walkthrough-creating-a-silverlight-web-part-that-displays-odata-for-sharepoint.md).  
  
### <a name="sharepoint-2010-visual-web-part"></a>SharePoint 2010 görsel web bölümü
 A *SharePoint 2010 Visual Web Bölümü* proje içeren bir *Elements.xml* tanım dosyasını bir **Web Bölümü** öğesi ve bir **kullanıcı denetimi** öğesi . Görsel web bölümü görünümünü sürükleyerek ya da kullanıcı denetiminin yüzeyine Visual Studio araç kutusundan denetimleri kopyalama tasarlayabilirsiniz. Daha fazla bilgi için [nasıl yapılır: Tasarımcı kullanarak bir SharePoint web bölümü oluşturma](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md) ve [yapı taşı: Web Bölümleri](http://go.microsoft.com/fwlink/?LinkId=179438).  
  
### <a name="import-sharepoint-2010-solution-package"></a>SharePoint 2010 çözüm paketini İçeri Aktar
 *SharePoint 2010 çözüm paketini içeri aktarma* projeleri, mevcut bir SharePoint 2010 site, bir SharePoint çözüm dışarı aktarılan bir kısmını veya tamamını içeri aktarmanıza olanak tanır (*.wsp*) dosyasına Visual Studio. Visual Studio'ya içeri sonra öğelerinden özelleştirebilir ve bunları yeniden dağıtın. Daha fazla bilgi için [mevcut bir SharePoint sitesinden öğeleri içeri aktarma](../sharepoint/importing-items-from-an-existing-sharepoint-site.md).  
  
### <a name="import-reusable-sharepoint-2010-workflow"></a>Yeniden kullanılabilir SharePoint 2010 iş akışını içeri aktarma
 *Yeniden kullanılabilir SharePoint 2010 iş akışını içe* projeleri Visual Studio'da SharePoint Designer 2010'da oluşturulan yeniden kullanılabilir, bildirim temelli bir iş akışını içeri aktarmanıza olanak tanır. İş akışı SharePoint sitesinden dışarı aktarılan bir *.wsp* dosya. Visual Studio'ya içeri sonra özelleştirebilir, kodu ekleyin ve ardından bir SharePoint sitesine dağıtma. Daha fazla bilgi için [izlenecek yol: bir SharePoint Tasarımcısı yeniden kullanılabilir iş akışını Visual Studio'ya içeri aktarma](../sharepoint/walkthrough-import-a-sharepoint-designer-reusable-workflow-into-visual-studio.md).  
  
## <a name="project-item-templates"></a>Proje öğesi şablonları
 SharePoint proje öğesi şablonları listesi aşağıdadır. Proje öğesi şablonları için site sütunları, listeler ve içerik türleri gibi SharePoint işlevleri desteklemek için SharePoint çözüm dosyaları ekleyin. Örneğin, çözümünüz için bir site sütunu ekleme içeren bir site sütunu proje ekler bir *Elements.xml* tanım dosyası. Bir görsel web bölümü ekleme, bir görsel web bölümü projesi içeren çözümünüze ekler bir *Elements.xml* dosya, bir kullanıcı denetimi öğesi ve bir görsel web bölümü öğesi.  
  
 SharePoint proje öğesi şablonları görüntülemek için **Çözüm Gezgini**, bir SharePoint projesi için kısayol menüsünü açın ve ardından **Ekle**, **yeni öğe**. Genişletin **SharePoint** ya da düğümünde **Visual C#**  veya **Visual Basic**ve ardından **2010**.  
  
### <a name="application-page-farm-solution-only"></a>Uygulama sayfası (yalnızca Grup çözümü)
 Bir **uygulama sayfası (yalnızca Grup çözümü)** öğesi tasarlamanızı sağlar bir [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] bir SharePoint sitesi için web sayfası. Uygulama sayfaları yalnızca Grup çözümlerinde kullanılabilir. Bu proje öğesi sadece grup çözümlerini ekleyebilirsiniz. Daha fazla bilgi için [nasıl yapılır: uygulama sayfası oluşturma](../sharepoint/how-to-create-an-application-page.md) ve [Application _layouts sayfa türü](http://go.microsoft.com/fwlink/?LinkId=179434).  
  
### <a name="business-data-connectivity-model-farm-solution-only"></a>İş Verileri Bağlantı Modeli (yalnızca Grup çözümü)
 A **iş verileri bağlantı modeli (yalnızca Grup çözümü)** öğesi sağlar için tümleştirme iş verilerini SharePoint ile. İş verileri yeniden ziyaret edebilir, arka uç sunucu uygulamalarından gibi [!INCLUDE[ssNoVersion](../sharepoint/includes/ssnoversion-md.md)], Siebel ve hizmet reklam Protokolü (SAP). İş Verileri Bağlantısı modelleri sadece grup çözümlerini kullanılabilir. Bu proje öğesi sadece grup çözümlerini ekleyebilirsiniz. Daha fazla bilgi için bkz. [nasıl yapılır: BDC modeli oluşturma](../sharepoint/how-to-create-a-bdc-model.md), [nasıl yapılır: yerelleştirilmiş adlar belirtin, özellikler ve izinleri için kaynak dosyası kullanma](../sharepoint/how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions.md), ve [yenilikler: iş bağlantısı Hizmetleri](http://go.microsoft.com/fwlink/?LinkId=179411).  
  
### <a name="content-type"></a>İçerik türü
 *İçerik türü* öğeleri, bir belge, duyuru veya bir görev gibi mevcut (Temel) içerik türüne göre özel içerik türleri oluşturmanıza olanak sağlar. Özel bir içerik türü tanımlarsınız sitesi sütunlar (alanlar) ile birlikte temel içerik türü olarak aynı öznitelikleri ve alanlar sağlar. Örneğin, SharePoint'te gelen temel kişi içerik türü temel alan özel bir içerik kişi türü oluşturabilirsiniz. İçerik türü var olan site sütunlarını değiştirme ya da daha fazla site sütunları temel içerik türü zaten bulunan ekleyerek özelleştirebilirsiniz.  
  
> [!NOTE]  
>  Bir SharePoint sınırlama nedeniyle, bir korumalı çözüm içerik türüne göre grup çözümü içerik türü oluşturulamıyor.  
  
 Daha fazla bilgi için [izlenecek yol: SharePoint için site sütunu, içerik türü ve liste oluşturma](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md) ve [yapı taşı: Content Type](http://go.microsoft.com/fwlink/?LinkId=179413).  
  
### <a name="empty-element"></a>Boş öğe
 *Boş öğeler* çoğunlukla bir proje veya proje öğesi şablonu Visual Studio'da sahip SharePoint Proje öğeleri tanımlamak için kullanılır. Projenize boş bir öğe eklediğinizde, bir düğüm adlı EmptyElement [x](where [x] is a unique number\) is created. [X] EmptyElement içeren tek dosya başka bir deyişle adlandırılmış *Elements.xml.* Kullanım [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] istenen öğeleri tanımlamak için deyimleri *Elements.xml*.  
  
### <a name="event-receiver"></a>Olay alıcısı
 *Olay alıcıları* bir listesine bir öğe eklendiğinde, bir web öğesi silindiğinde veya bir iş akışı başladığında gibi SharePoint sitesindeki öğeleri için olayları işleme. Olay alıcısı proje öğesi şablon işlemenize olanak tanır.  
  
- Liste etkinlikleri  
  
- Liste öğesi etkinlikleri  
  
- Liste e-posta etkinlikleri  
  
- Web olayları  
  
- Liste iş akışı etkinlikleri  
  
  Olay alıcısı proje öğesi oluşturur bir **olay alıcısı** projeyi oluştururken belirttiğiniz tüm olayları için olay işleyicileri içeren tek bir sınıf dosyası klasörü **SharePoint özelleştirme Sihirbaz**. Olay alıcısı sınıfına dosyaları, alanlar, öğeleri, listeler, ekleri, web bölümleri ve iş akışları gibi öğeleri eklendiğinde, güncelleştirilmiş, silindi, kaldırıldı veya SharePoint sitesinde meydana gelen olayları işleyebilir. Daha fazla bilgi için [nasıl yapılır: olay alıcısı oluşturma](../sharepoint/how-to-create-an-event-receiver.md) ve [yapı taşı: olay işleme](http://go.microsoft.com/fwlink/?LinkId=179416).  
  
### <a name="list"></a>List  
 Bir liste, bir yeniden kullanılabilir temel SharePoint liste tanımı, bir takvim veya görev listesi'gibi bir örneğidir. Çözümünüze bir liste eklendikten sonra liste Tasarımcı site sütunları listesine ekleyin ve özel listesi sütunları oluşturmanıza olanak sağlar. Bu içerik türünden site sütunları içerir. Belirtebileceğiniz *görünümü* listesi için listede görünür sütunlar belirler. Daha fazla bilgi için [izlenecek yol: SharePoint için site sütunu, içerik türü ve liste oluşturma](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md) ve [yapı taşı: listelerin ve belge kitaplıklarını](http://go.microsoft.com/fwlink/?LinkId=179421).  
  
### <a name="module"></a>Modül  
 *Modüller* (ile karıştırılmamalıdır [!include[vbprvb](../sharepoint/includes/vbprvb-md.md)] modülleri) görüntü veya notları gibi SharePoint sunucusuna dağıtmak istediğiniz tüm dosyaları içerir. Modül proje öğesi içeren bir **Modülü** düğümü. İki proje öğesi şablonları modülü düğüm içerir: modül için bir bildirim görür, bir XML tanım dosyası ve bir *örnek.txt* dosya, bir yer tutucu dosyası. Daha fazla bilgi için [Çözümdeki dosyalar dahil kullanım modüllerine](../sharepoint/using-modules-to-include-files-in-the-solution.md) ve [modülleri](http://go.microsoft.com/fwlink/?LinkId=179425).  
  
### <a name="sequential-workflow-farm-solution-only"></a>Sıralı iş akışı (yalnızca Grup çözümü)
 A *sıralı iş akışı* iş mantığı adımlar, son adım tamamlanana kadar sırayla gerçekleştirilen bir dizi. Sıralı iş akışı içeren SharePoint öğeleri listeler ve belgeler gibi işlemleri yönetmek için kullanılır. Site düzeyinde (Genel) iş akışları ya da liste düzeyini (yerel) iş akışları oluşturabilir ve bir iş akışı otomatik olarak veya el ile başlayıp başlamadığı seçebilirsiniz. Bu proje öğesi, yalnızca Grup çözümlerinde kullanılabilir. Bu proje öğesi sadece grup çözümlerini ekleyebilirsiniz. Daha fazla bilgi için [oluşturma SharePoint iş akışı çözümleri](../sharepoint/creating-sharepoint-workflow-solutions.md), [SharePoint Server 2010 iş akışlarında](http://go.microsoft.com/fwlink/?LinkId=260555), ve [yenilikler: iş akışı iyileştirmeleri](http://go.microsoft.com/fwlink/?LinkId=179418).  
  
### <a name="silverlight-web-part"></a>Silverlight web bölümü
 *Silverlight web bölümü* proje öğeleri olanak oluştur web bölümleri için Silverlight uygulamaları görüntülemek için SharePoint. Bu proje öğesi çözümünüze eklediğiniz zaman, yeni bir Silverlight uygulamasını eklemek veya mevcut bir daha sonra başvurmak seçebilirsiniz. Daha fazla bilgi için [için SharePoint web bölümleri oluşturma](../sharepoint/creating-web-parts-for-sharepoint.md) ve [izlenecek yol: SharePoint için OData görüntüleyen bir Silverlight web bölümü oluşturma](../sharepoint/walkthrough-creating-a-silverlight-web-part-that-displays-odata-for-sharepoint.md).  
  
### <a name="site-column"></a>Site sütunu
 A *site sütunu*olarak da bilinen bir *alan*, bir SharePoint projesine ekleyebilirsiniz en temel öğeleri biridir. Bir site sütunu, bir telefon numarası, metin açıklama ya da bir kişi listesini kişi şehir adı gibi bir veri türünü temsil eder. Daha fazla bilgi için [SharePoint için site sütunları, içerik türleri ve listeler oluşturma](../sharepoint/creating-site-columns-content-types-and-lists-for-sharepoint.md) ve [sütunları](http://go.microsoft.com/fwlink/?LinkId=226840).  
  
### <a name="site-definition-farm-solution-only"></a>Site tanımı (yalnızca Grup çözümü)
 *Site tanımı* proje öğeleri içeren aşağıdaki dosyaları içeren bir site tanımı klasörü:  
  
- Site için varsayılan web sayfası olarak kullanılan bir varsayılan .aspx sayfası.  
  
- Bir *onet.xml* site bileşenlerini tanımlayan dosya.  
  
- Görünen site tanımı yapılandırmaları belirten bir webtemp xml dosyası **Şablon Seçimi** bölümünü **yeni SharePoint sitesi** sayfası.  
  
  Bir site tanımı ekledikten sonra kod ve işlevleri tanıtmak için dosyaları ekleyin. Bu proje öğesi, yalnızca Grup çözümlerinde kullanılabilir. Bu proje öğesi sadece grup çözümlerini ekleyebilirsiniz. Daha fazla bilgi için [SharePoint için site tanımları oluşturma](../sharepoint/creating-site-definitions-for-sharepoint.md) ve [Site tanımları ve yapılandırmaları](http://go.microsoft.com/fwlink/?LinkId=260554).  
  
### <a name="state-machine-workflow-farm-solution-only"></a>Durum makinesi iş akışı (yalnızca Grup çözümü)
 A *Durum makinesi iş akışı* iş mantığı durumları, geçişleri ve eylemleri kümesidir. Bir Durum makinesi iş akışı adımları sırayla gerçekleştirilmez; Bunun yerine, Eylemler ve durumlar tarafından tetiklenir. Sıralı iş akışı gibi durum makine iş akışları listeler ve belgeler gibi SharePoint öğeleri ile ilişkilidir. Bir kez daha, site düzeyinde (Genel) iş akışları veya liste düzeyini (yerel) iş akışları oluşturabilirsiniz. Bir iş akışı otomatik olarak veya el ile başlayıp başlamadığı de seçebilirsiniz. Bu proje öğesi, yalnızca Grup çözümlerinde kullanılabilir. Bu proje öğesi sadece grup çözümlerini ekleyebilirsiniz. Daha fazla bilgi için [oluşturma SharePoint iş akışı çözümleri](../sharepoint/creating-sharepoint-workflow-solutions.md), [SharePoint Server 2010 iş akışlarında](http://go.microsoft.com/fwlink/?LinkId=260555), ve [yenilikler: iş akışı iyileştirmeleri](http://go.microsoft.com/fwlink/?LinkId=179418).  
  
### <a name="user-control-farm-solution-only"></a>Kullanıcı denetimi (yalnızca Grup çözümü)
 A *kullanıcı denetimi* olduğu ekleyebileceğiniz diğer ASP.NET denetimleri ve SharePoint denetimleri yeniden kullanılabilir, özel bir denetim. Kullanıcı denetimi uygulama sayfaları ve SharePoint'te çalışan web bölümleri eklenebilir. Bu proje öğesi, yalnızca Grup çözümlerinde kullanılabilir. Bu proje öğesi sadece grup çözümlerini ekleyebilirsiniz. Daha fazla bilgi için [Web Bölümleri veya uygulama sayfaları için yeniden kullanılabilir denetimler oluşturma](http://go.microsoft.com/fwlink/?LinkId=226841).  
  
### <a name="visual-web-part"></a>Görsel web bölümü
 Bir *görsel web bölümü* proje öğesi içeren bir *Elements.xml* tanım dosyası bir **Web Bölümü** öğesi ve bir **kullanıcı denetimi** öğesi. Görsel web bölümü görünümünü sürükleyerek ya da kullanıcı denetiminin yüzeyine Visual Studio araç kutusundan denetimleri kopyalama tasarlayabilirsiniz. Daha fazla bilgi için [nasıl yapılır: Tasarımcı kullanarak bir SharePoint web bölümü oluşturma](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md) ve [yapı taşı: Web Bölümleri](http://go.microsoft.com/fwlink/?LinkId=179438).  
  
### <a name="web-part"></a>Web kısmı
 A *web bölümü* sayfa bir Web Bölümü sayfası olarak adlandırılan özel bir tür içinde çalışan bir sunucu tarafı denetimidir. Bunlar bir SharePoint sitesinde görünen sayfaların yapı taşlarıdır. Web bölümü öğesi, bir SharePoint sitesi için bir web bölümü tasarlamak etkinleştirdiğiniz dosyaları sağlar. Daha fazla bilgi için [nasıl yapılır: bir SharePoint web bölümü oluşturma](../sharepoint/how-to-create-a-sharepoint-web-part.md) ve [yapı taşı: Web Bölümleri](http://go.microsoft.com/fwlink/?LinkId=179438).  
  
## <a name="see-also"></a>Ayrıca bkz.
 [SharePoint çözümleri geliştirme](../sharepoint/developing-sharepoint-solutions.md)   
 [SharePoint Ürünleri ve teknolojileri](http://go.microsoft.com/fwlink/?LinkId=178818)  
  
  
