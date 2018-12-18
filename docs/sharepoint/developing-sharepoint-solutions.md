---
title: SharePoint çözümleri geliştirme | Microsoft Docs
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.Project.ProjectProperties
- VS.SharePointTools.Project.ProjectItemProperties
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, overview
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 25a7402a8d0464152e9b1bdd9d2edcdc66824914
ms.sourcegitcommit: 0a8ac5f2a685270d9ca79bb39d26fd90099bfa29
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/09/2018
ms.locfileid: "51295910"
---
# <a name="develop-sharepoint-solutions"></a>SharePoint çözümleri geliştirme
  Bazı SharePoint proje türü şablonları kullanılabilir [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] SharePoint siteleri ve site öğeleri oluşturmak için. Kullanılabilir proje türlerinin bir listesi için bkz. [SharePoint projesi ve proje öğesi şablonları](../sharepoint/sharepoint-project-and-project-item-templates.md). Öğeleri bir açıklamasını ve özelliklerini bir SharePoint projesine aşağıda verilmiştir.  
  
 SharePoint 2013 ve SharePoint eklentileri hakkında daha fazla bilgi için bkz: [SharePoint 2013](https://msdn.microsoft.com/library/jj162979.aspx) ve [derleme SharePoint eklentileri](/sharepoint/dev/sp-add-ins/sharepoint-add-ins).  
  
## <a name="elements-of-a-sharepoint-project"></a>Bir SharePoint Proje öğeleri
 Bir SharePoint projesi altındaki düğümler olarak da bilinir *SharePoint öğeleri*. SharePoint öğeleri de denir, bir veya daha fazla alt içerebilir *SharePoint öğe dosyaları*, gibi [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] yapılandırma dosyaları, .aspx formları ve daha fazlası.  
  
 Kullanabileceğiniz proje öğesi dosyalarına eklenmiş olan proje şablonlarını kullanarak projeleri oluşturmak yerine, **boş proje** şablon boş bir SharePoint projesi oluşturun ve proje öğelerini el ile ekleyin. SharePoint projeleri isteğe bağlı olarak ayrıca bir veya daha fazla özellik dosyalarını (SharePoint'te etkinleştirme) ve hangi projenin dağıtılacağı paket dosyasını içerebilir.  
  
### <a name="special-nodes"></a>Özel düğümler
 Her SharePoint projesi, yeniden adlandırılmış, silinmiş, Kes, kopyalanamaz veya projeden sürüklenemeyen iki düğüm içerir. Bu düğümler aşağıdaki gibidir:  
  
- Özellikler    
- Paket  
  
  Proje için hiçbir özellik veya paket tanımlanmamış olsa bile her iki düğüm her zaman tüm SharePoint projelerinde görünür.  
  
#### <a name="features-node"></a>Özellikler düğümü
 **Özellikleri** düğümü bir veya daha fazla SharePoint proje özelliği içerir. Bir özellik, SharePoint uzantılarını bir kapsayıcıdır. Bir özellik SharePoint sunucusuna dağıtıldıktan sonra site tanımlamalarına dahil edilebilir veya SharePoint siteleri sitesindeki SharePoint Yöneticisi tarafından ayrı ayrı etkinleştirildi. Daha fazla bilgi için [özelliklerle çalışma](http://go.microsoft.com/fwlink/?LinkID=147704).  
  
 Bir SharePoint projesine içerik türü veya bir liste örneği gibi bir öğe eklediğinizde, bir özelliğe eklenir **özellikleri** düğümü. Öğenin kapsamı, yeni veya mevcut bir özelliğe eklenir olup olmadığını belirler. Yeni öğe mevcut özellikle aynı kapsama sahipse bu özelliğe eklenir. Aksi halde öğe yeni bir özelliğe eklenir.  
  
 El ile özellik eklemek için yürütme **Özellik Ekle** özellik düğümünün kısayol menüsünde komutu. Görüntüleyebilir veya özellik Tasarımcısı'nı kullanarak bir özelliğin içeriğini değiştirebilirsiniz. Daha fazla bilgi için [nasıl yapılır: bir SharePoint özelliğini özelleştirme](../sharepoint/how-to-customize-a-sharepoint-feature.md).  
  
 Bir özellik bir SharePoint projesine eklendiğinde görünür **Çözüm Gezgini** düğüm varsayılan olarak özellik adını*x*.feature, burada *x* benzersiz bir sayıdır. Bir özellik SharePoint sunucusuna dağıtıldıktan sonra SharePoint Yöneticisi, SharePoint sitesi kullanıcıları için kullanılabilir hale etkinleştirebilirsiniz.  
  
#### <a name="package-node"></a>Paket düğümü
 **Paket** düğümü SharePoint projesi için dağıtım mekanizması olarak görev yapar tek bir dosya içerir. Olarak bilinen bu dosya bir *çözüm paketi*, olan. CAB tabanlı bir. WSP uzantısı. Çözüm paketi özellikleri, site tanımları ve derlemeleri, SharePoint sitelerine Uygula ve Etkinleştir ya da tek tek devre dışı bir dizi içeren dağıtılabilir, yeniden kullanılabilir bir dosyadır. **Paket** düğümü de her zaman Package.wspdef olarak adlandırılan dosyayı içeren bir [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] paket tanımı dosyası. SharePoint'i çalıştıran sunucuya bir paket dağıtıldıktan sonra SharePoint Yöneticisi bunu yükleyebilir ve özelliklerini etkinleştirebilir.  
  
 Görüntüleyebilir veya paket içeriğini paket Tasarımcısı içinde paket düğümünü çift tıklayarak veya kısayol menüsünü açarak ve ardından değiştirmek **açık**. Daha fazla bilgi için [oluşturma SharePoint çözüm paketleri](../sharepoint/creating-sharepoint-solution-packages.md).  
  
## <a name="sharepoint-project-and-project-item-properties"></a>SharePoint projesi ve proje öğesi özellikleri
 SharePoint projeleri, olduğu gibi diğer [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] projeleri, Özellikler penceresinde ve Özellikler sayfasını özelliklerini görüntüleme. Görüntülenen özellikler seçilen düğüme bağlıdır.  
  
 Bir SharePoint projesi, proje öğesi veya proje öğesi dosya düğümü seçildiğinde **Çözüm Gezgini**, Özellikler penceresinde veya özellikler sayfasında aşağıdaki özellikler görünür:  
  
### <a name="project-properties"></a>Proje Özellikleri
  
|Özellik adı|Açıklama|  
|-------------------|-----------------|  
|Etkin dağıtım yapılandırması|Dağıtım sırasında gerçekleştirilen adım serisini belirtir. Daha fazla bilgi için [nasıl yapılır: SharePoint dağıtım yapılandırmasını düzenleme](../sharepoint/how-to-edit-a-sharepoint-deployment-configuration.md).|  
|Bütünleştirilmiş kod dağıtım hedefi|Nereye belirler *SharePoint uygulama derlemeleri* bulunur. Geçerli derleme konumu değerleri *GlobalAssemblyCache* (varsayılan) veya *WebApplication*.<br /><br /> Varsa *Korumalı çözüm* özelliği **true**, bu özelliği devre dışı bırakılır.|  
|Hata ayıklama sonrasında otomatik Ayıkla|Dağıtılan çözümün otomatik olarak SharePoint'ten uygulama hata ayıklama modunda çalıştırdıktan sonra veri çekip çekmeyeceğini belirtir [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Bu onay kutusu seçildiğinde, IDE geri hata ayıklama sonrasında Tasarım görünümüne döndüğünde çözüm geri çeker. Temizlendiğinde çözüm geri çekilmez. Daha fazla bilgi için [çözümü geri çekme](http://go.microsoft.com/fwlink/?LinkId=183819).|  
|Yapılandırmaları Düzenle|Proje için kullanılacak dağıtım yapılandırmasını belirtir. Daha fazla bilgi için [nasıl yapılır: SharePoint dağıtım yapılandırmasını düzenleme](../sharepoint/how-to-edit-a-sharepoint-deployment-configuration.md) ve [dağıtma, yayımlama ve yükseltme SharePoint çözüm paketleri](../sharepoint/deploying-publishing-and-upgrading-sharepoint-solution-packages.md).|  
|Silverlight hata ayıklamasını etkinleştir (betik hata ayıklaması yerine)|Seçildiğinde Silverlight hata ayıklayıcı hata ayıklama işlemine ekler. Temizlendiğinde komut hata ayıklayıcı hata ayıklama işlemine ekler. Daha fazla bilgi için [Silverlight hata ayıklamaya genel bakış](http://go.microsoft.com/fwlink/?LinkId=179826).|  
|Derlemeyi pakete dahil et|Veya proje derlemesinin oluşturma zamanında paketlenmiş olup olmadığını belirtir.|  
|Dağıtım sonrası komut satırı|SharePoint çözümü dağıtıldıktan sonra çalıştırılacak komutları belirtir. Bu satır, çözümleme ve MSBuild değişkenlerinin yanı sıra, toplu iş komutlarını destekler. Daha fazla bilgi için [nasıl yapılır: SharePoint dağıtım komutlarını ayarlama](../sharepoint/how-to-set-sharepoint-deployment-commands.md).|  
|Dağıtım öncesi komut satırı|SharePoint çözümü dağıtılmadan önce çalıştırılacak komutları belirtir. Bu satır, çözümleme ve MSBuild değişkenlerinin yanı sıra, toplu iş komutlarını destekler. Daha fazla bilgi için [nasıl yapılır: SharePoint dağıtım komutlarını ayarlama](../sharepoint/how-to-set-sharepoint-deployment-commands.md).|  
|Proje Dosyası|Oluşturma, yapılandırma ve proje hakkında diğer bilgileri içeren dosyanın adı.|  
|Proje klasörü|Proje dosyasının sistemdeki konumu. (Salt okunur.)|  
|Korumalı çözüm|Proje olarak dağıtılmasının gerekip gerekmediğini belirten bir *Korumalı çözüm*olarak da bilinen bir *kullanıcı tarafından oluşturulan çözüm*. Korumalı alan çözümleri mutlaka güvenilir değildir. Değerini **true** projenin Korumalı çözüm, bir değeri dağıtıldığını anlamına gelir **false** Grup çözümü olarak dağıtılan proje anlamına gelir. Daha fazla bilgi için [korumalı çözümle ilgili konular](../sharepoint/sandboxed-solution-considerations.md) ve [korumalı arasındaki farklar ve Grup çözümlerine](../sharepoint/differences-between-sandboxed-and-farm-solutions.md).|  
|Site URL'si|Belirtir [!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)] bu proje için hedef sitenin.|  
|Başlangıç öğesi|Çalıştırılacak projedeki ilk öğeyi belirtir.|  
  
 Bir SharePoint öğesi dosyasını (örneğin, bir iş akışı veya özellikler düğümünde bir özellik) seçtiğinizde, aşağıdaki özellikleri Özellikler penceresinde görüntülenir:  
  
### <a name="project-item-properties"></a>Proje öğesi özellikleri
  
|Özellik adı|Açıklama|  
|-------------------|-----------------|  
|Dağıtıma Çakışma Çözümlemesi|Özellikleri sunucudaki bir öğeninkilerle aynı olan bir proje öğesi dağıtılırken gerçekleştirilecek eylemi belirtir. Daha fazla bilgi için [sorun giderme SharePoint paketleme ve dağıtım](../sharepoint/troubleshooting-sharepoint-packaging-and-deployment.md).|  
|Özellik özellikleri|SharePoint'te dağıtıldığında bir özellikle birlikte eklenen değer kümesi (anahtar/değer çifti saklanır) belirtir. Özellik dağıtıldıktan sonra kodunuzdaki özellik değerlerine erişebilirsiniz. Daha fazla bilgi için [sağlama paketleme ve dağıtım bilgileri proje öğelerinde](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md).|  
|Özellik alıcısı|Özellik içeren bir proje öğesine belirli olaylar meydana geldiğinde yürütülen kodu sağlar. Daha fazla bilgi için [sağlama paketleme ve dağıtım bilgileri proje öğelerinde](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md).|  
|Klasör adı|SharePoint proje öğesi klasörünün adı.|  
|Proje çıktısı başvuruları|Gibi proje öğenizin çalıştırması gereken bir derleme, bir bağımlılık belirtir. Daha fazla bilgi için [sağlama paketleme ve dağıtım bilgileri proje öğelerinde](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md).|  
|Güvenli denetim girdileri|Düzenlemek güvenilir olmayan kullanıcıların düzenleyebileceği denetimleri belirtir. Daha fazla bilgi için [sağlama paketleme ve dağıtım bilgileri proje öğelerinde](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md).|  
  
### <a name="project-item-file-properties"></a>Proje öğesi dosyası özellikleri
  
|Özellik adı|Açıklama|  
|-------------------|-----------------|  
|Derleme eylemi|Dosyanın nasıl derleme ve dağıtım işlemleriyle olan ilişkisi belirtir. Daha fazla bilgi için [dosya özelliklerini](/previous-versions/visualstudio/visual-studio-2010/0c6xyb66\(v\=vs.100\)).|  
|Çıkış Dizinine Kopyala|Kaynak dosyalar çıkış dizinine mi kopyalanacağını belirtir. Aşağıdaki değerlerden biri olabilir:<br /><br /> -   *Kopyalamayın*<br />-   *Her zaman Kopyala*<br />-   *Yeniyse Kopyala*<br /><br /> Daha fazla bilgi için [dosya özelliklerini](/previous-versions/visualstudio/visual-studio-2010/0c6xyb66\(v\=vs.100\)).|  
|Özel araç|Varsa, tasarım zamanında dosyayı dönüştüren ve dönüştürme çıktısını başka bir dosyaya koyar, bir aracın adını belirtir. Örneğin, bir veri kümesi (.[!INCLUDE[TLA2#tla_xsd](../sharepoint/includes/tla2sharptla-xsd-md.md)]) dosyası varsayılan bir özel araca sahiptir. Daha fazla bilgi için [dosya özelliklerini](/previous-versions/visualstudio/visual-studio-2010/0c6xyb66\(v\=vs.100\)).|  
|Özel araç Namespace|İçinde özel aracın çıktısının kopyalanacağı ad alanı. Daha fazla bilgi için [dosya özelliklerini](/previous-versions/visualstudio/visual-studio-2010/0c6xyb66\(v\=vs.100\)).|  
|Dağıtım Konumu|Dosyanın SharePoint sunucusundaki tam yolu. Bu yol, dağıtım kökü ve dağıtım yolu alt özelliklerinden oluşur.|  
|Dağıtım yolu|Dosyanın Workflow1 gibi SharePoint Server dosyasındaki göreli yol\\. Dosyanın tam yolunu birleştirilerek oluşturulur *dağıtım yolu* sonuna değeri *dağıtım kökü* değeri.<br /><br /> Bir değeri seçerek *RootFile* için *dağıtım türü* özellik değişiklikleri *dağıtım kökü* özelliğini \<SharePointRoot >\\, tam olarak nitelenmiş yolu imzalanmayarak \<SharePointRoot > \Workflow1\\. Daha fazla bilgi için [paketleme ve dağıtma SharePoint çözümleri](../sharepoint/packaging-and-deploying-sharepoint-solutions.md).|  
|Dağıtım kökü|dize. Dosyanın SharePoint sunucusunda dağıtıldığı kök klasörü. Örneğin, \<SharePointRoot > \Template\Features\\\<FeatureName >\\.<br /><br /> Değerini *dağıtım kökü* özelliği tarafından belirlenir *dağıtım türü* ayarı.|  
|Dağıtım türü|Belirleyen dosya dağıtım türü kendi *dağıtım kökü* değeri. Aşağıdaki değerlerden biri olabilir:<br /><br /> NoDeployment:  *\<değer yok >*<br /><br /> Elementmanifest öğesini:  *\<SharePointRoot > \Template\Features\\\<FeatureName >*\\<br /><br /> ElementFile:  *\<SharePointRoot > \Template\Features\\\<FeatureName >\\*<br /><br /> TemplateFile:  *\<SharePointRoot > \Template\\*<br /><br /> RootFile:  *\<SharePointRoot >\\*<br /><br /> GlobalResource:  *\<SharePointRoot > \Resources\\*<br /><br /> ClassResource:  *\<ClassResourcePath >\\*<br /><br /> Daha fazla bilgi için bkz. <xref:Microsoft.VisualStudio.SharePoint.DeploymentType>.|  
|Dosya Adı|Öğe dosyası için dosya veya klasörün adı.|  
|Tam yolu|Öğe dosyasının konumu. (Salt okunur.)|  
  
## <a name="related-topics"></a>İlgili konular
  
|Başlık|Açıklama|  
|-----------|-----------------|  
|[SharePoint Projesi ve Proje Öğesi Şablonları](../sharepoint/sharepoint-project-and-project-item-templates.md)|SharePoint projesi ve proje öğesi şablonları de kullanılabilir açıklar [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].|  
|[Nasıl yapılır: Bir SharePoint Projesine Öğeler Ekleme](../sharepoint/how-to-add-items-to-a-sharepoint-project.md)|Yeni veya varolan öğeler ekleneceğini açıklar bir [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] SharePoint Proje.|  
|[İzlenecek yol: SharePoint için site sütunu, içerik türü ve liste oluşturma](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md)|Adım adım bir müşteri alanı, içerik türü, liste tanımı ve liste örneği oluşturmada size yol gösterir.|  
|[Nasıl yapılır: olay alıcısı oluşturma](../sharepoint/how-to-create-an-event-receiver.md)|Oluşturduğunuz proje için bir olay alıcısı ekleneceğini açıklar [izlenecek yol: SharePoint için site sütunu, içerik türü ve liste oluşturma](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md).|  
|[SharePoint iş akışı çözümleri oluşturma](../sharepoint/creating-sharepoint-workflow-solutions.md)|İş akışı ilişkilendirme formları ve iş akışı başlatma formlarını içeren iş akışı projelerinin nasıl oluşturulduğunu açıklar.|  
|[SharePoint için sayfa oluşturma](../sharepoint/creating-pages-for-sharepoint.md)|SharePoint için uygulama sayfaları, site sayfaları, ana sayfalar ve sayfa düzenleri gibi sayfaları nasıl oluşturacağınızı açıklar.|  
|[SharePoint için Web bölümleri oluşturma](../sharepoint/creating-web-parts-for-sharepoint.md)|Kullanıcıların içeriğini, görünümünü ve davranışını SharePoint sitesi sayfalarının bir tarayıcı kullanarak doğrudan değiştirmesine olanak tanıyan denetimler eklemeyi açıklar.|  
|[Web bölümleri veya uygulama sayfaları için yeniden kullanılabilir denetimler oluşturma](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)|Uygulama sayfaları ve SharePoint'te çalışan Web bölümleri tarafından kullanılabilen kullanıcı denetimlerinin nasıl yaratılacağını açıklar.|  
|[İş verilerini SharePoint ile tümleştirme](../sharepoint/integrating-business-data-into-sharepoint.md)|Veri Web Hizmetleri ve arka uç sunucu uygulamalarından SharePoint uygulamasına tümleştirmek açıklar.|  
|[SharePoint için site tanımları oluşturma](../sharepoint/creating-site-definitions-for-sharepoint.md)|Nasıl site tanımları oluşturulacağını açıklar: SharePoint siteleri oluşturmak için kullanılan şablonları.|  
|[Mevcut bir SharePoint Sitesinden Öğeleri İçeri Aktarma](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)|Bir SharePoint sitesinden içerik türleri veya modüller gibi öğeleri içe aktarmayı açıklar bir [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] SharePoint Proje.|  
|[Çözüme Dosyaları Dahil Etmek için Modül Kullanma](../sharepoint/using-modules-to-include-files-in-the-solution.md)|Dosyaları dağıtmak için modülleri kullanmayı açıklar, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] proje SharePoint sitesi.|  
|[Sunucu Gezgini kullanarak SharePoint bağlantılarına göz atın](../sharepoint/browsing-sharepoint-connections-using-server-explorer.md)|Sunucu Gezgini kullanarak yerel SharePoint sitelerine göz atmak açıklar.|  
|[Proje öğelerinde paketleme ve dağıtım bilgileri sağlayın](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)|Güvenli denetim girişleri, proje çıktı başvuruları ve özellikler gibi projeler için paketleme ve dağıtım bilgileri sağlamak için proje öğesi özelliklerini kullanmayı açıklar.|  
|[Nasıl yapılır: eşlenmiş klasörler ekleme ve kaldırma](../sharepoint/how-to-add-and-remove-mapped-folders.md)|Nasıl eşlenen klasörler açıklar SharePoint kaynaklarına daha kolay erişim sağlamak için projenize eklendi.|  
|[Korumalı çözümle ilgili konular](../sharepoint/sandboxed-solution-considerations.md)|Korumalı çözümlerle ilgili sorunları açıklar.|  
|[SharePoint Çözümleri için Güvenlik](../sharepoint/security-for-sharepoint-solutions.md)|SharePoint çözümleri geliştirmek için güvenlik konuları açıklanmaktadır [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].|  
|[URL Seçici iletişim kutusu &#40;Visual Studio'da SharePoint geliştirme&#41;](../sharepoint/url-picker-dialog-box-sharepoint-development-in-visual-studio.md)|Projenizdeki veya yerel SharePoint sunucusundaki kaynaklara yol başvuruları eklemek için kullanabileceğiniz bir iletişim kutusu tanımlar.|  
  
## <a name="see-also"></a>Ayrıca bkz.
 [Başlama &#40;Visual Studio'da SharePoint geliştirme&#41;](../sharepoint/getting-started-sharepoint-development-in-visual-studio.md)   
 [Sunucu Gezgini kullanarak SharePoint bağlantılarına göz atın](../sharepoint/browsing-sharepoint-connections-using-server-explorer.md)   
 [Derleme ve SharePoint çözümlerinde hata ayıklama](../sharepoint/building-and-debugging-sharepoint-solutions.md)   
 [Paketleme ve SharePoint çözümlerini dağıtma](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
  
  
