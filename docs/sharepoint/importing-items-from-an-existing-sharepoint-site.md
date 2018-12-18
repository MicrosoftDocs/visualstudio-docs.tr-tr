---
title: Mevcut bir SharePoint sitesinden öğeleri içeri aktarma | Microsoft Docs
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.WSPImport.SelectionDependency
- VS.SharepointTools.WSPImport.SpecifyProjectSource
- VS.SharePointTools.WSPImport.SelectionItemsToImport
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, importing items
- SharePoint development in Visual Studio, importing .wsp files
- importing items [SharePoint development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 7435d6c7ad210554031994f4a366812f9799ffb2
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49832114"
---
# <a name="import-items-from-an-existing-sharepoint-site"></a>Mevcut bir SharePoint sitesinden öğeleri içeri aktarma
  SharePoint çözüm paketini İçeri Aktar proje şablonu sayesinde yeni bir içerik türleri ve alanlarını mevcut SharePoint siteleri gibi öğeleri yeniden [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] SharePoint çözüm. İçeri aktarılan çözümleri değişiklik yapılmadan en çalıştırabilirsiniz, ancak olup olmadığını belirli kısıtlamalar ve dikkate alınması gereken sorunları özellikle içeri aktardıktan sonra tüm öğeleri değiştirin.  
  
> [!NOTE]  
>  Yeniden kullanılabilir iş akışlarını içeri aktarmak için yeniden kullanılabilir iş akışını içe proje şablonu kullanın. [!INCLUDE[crdefault](../sharepoint/includes/crdefault-md.md)] [Yeniden kullanılabilir iş akışlarını içeri aktarma yönergeleri](../sharepoint/guidelines-for-importing-reusable-workflows.md).  
  
## <a name="supported-sharepoint-solutions"></a>Desteklenen SharePoint çözümleri
 [!INCLUDE[vs_dev11_long](../sharepoint/includes/vs-dev11-long-md.md)] tam olarak oluşturulmuş çözümler alma destekleyen [!INCLUDE[wss_14_short](../sharepoint/includes/wss-14-short-md.md)] ve [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)].  
  
 [!INCLUDE[vs_dev11_long](../sharepoint/includes/vs-dev11-long-md.md)] Aşağıdaki uygulamalarda oluşturulmuş çözümler almayı desteklemiyor:  
  
- [!INCLUDE[winshare3](../sharepoint/includes/winshare3-md.md)]  
  
- [!INCLUDE[offshare7](../sharepoint/includes/offshare7-md.md)]  
  
- [!INCLUDE[vs_orcas_long](../sharepoint/includes/vs-orcas-long-md.md)]  
  
- Microsoft SharePoint Designer 2007  
  
- [!INCLUDE[vs_dev10_long](../sharepoint/includes/vs-dev10-long-md.md)]  
  
  Bu uygulamaları tarafından oluşturulan çözümleri genellikle başarıyla içeri aktarabilirsiniz ancak bu işlevselliği test ve desteklenmiyor.  
  
## <a name="item-import-restrictions"></a>Öğe içeri aktarma kısıtlamaları
 Mevcut bir SharePoint öğelerin çoğu alınabilir ancak *.wsp* dosya, aşağıdaki öğeler desteklenmez ve düzgün çalışması için değişiklik gerektirebilir:  
  
- İVB varlıklar  
  
- İş akışı ilişkilendirmesi öğelerini kod  
  
- Kod iş akışları  
  
- Visual Web Bölümü (.ascx)  
  
- Web Hizmetleri (*.asmx*)  
  
- İçerik türü bağlamaları  
  
- Olay alıcıları  
  
- Liste tanımları (şablon)  
  
- Site tanımları  
  
  Bir çözümü dışarı aktardığınızda [!INCLUDE[wss_14_short](../sharepoint/includes/wss-14-short-md.md)] veya [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)], bu öğeler otomatik olarak verilerinden dışlanan *.wsp* dosya. Ancak, diğer *.wsp* desteklenmeyen Araçları'ndan oluşturulan dosyalar, bu öğeler içerebilir. (Bu konuda daha önce "Desteklenen SharePoint çözümleri" bakın.)  
  
## <a name="what-happens-when-you-import-a-solution"></a>Çözümü içeri aktarma ne olur
 SharePoint çözüm paketini içeri aktarma şablonu ile bir çözüm içeri aktardığınızda [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] tüm içeriğini kopyalar *.wsp* dosya ve mutabık ve çok ilişkileri ve başvuruları arasında korumak için çalışır öğeleri ve bunların dosyaları mümkün olduğunca.  
  
 Tüm içeri aktarılan öğeleri kopyala karşılık gelen klasörlerde **Çözüm Gezgini**. Örneğin, içerik türleri klasörün altında görünür **içerik türlerine** ve liste örneklerini altında görünen **liste örnekleri**. İçeri aktarılan bir öğeyle ilişkili dosyalar da öğenin klasörüne kopyalanır. Örneğin, bir içeri aktarılan liste örneği, modüller, formlar ve ASPX sayfaları içerir.  
  
### <a name="dependent-items"></a>Bağımlı öğeler
 SharePoint çözüm paketini İçeri Aktar Sihirbazı'nı, ancak onun bağımlı öğeleri bir öğe seçin, bir ileti kutusu bağımlı öğeler de içeri aktarmadan önce seçilmelidir olduğunu bildirir.  
  
### <a name="what-are-features"></a>Özellikler nelerdir?
 SharePoint Designer kullanıcı adlı beklenmeyen dosya karşılaşabilirsiniz *özellikleri*, içeri aktarılan çözümleri görünür **Çözüm Gezgini.** SharePoint Designer çözümündeki özellikleri olsa da, bunlar görünümünden gizlenmiş. Özellik görünür kullanıma [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
 Özellikler, SharePoint öğeleri için kapsayıcılardır. Her bir özellik gibi içerik türleri ve içerdiği liste tanımları her öğeye bir başvuru tutar. Çözümünüzü içeri aktardığınızda [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] alınan tüm öğeleri için özellikleri ayarlar ve özellik öğe ilişkileri dosyaları korumak çalışır. Herhangi bir dosya olan başvuruları çözümlenemedi put **diğer içeri aktarılan dosyaları** klasör.  
  
 Özellikler hakkında daha fazla bilgi için bkz. [geliştirme SharePoint çözümleri](../sharepoint/developing-sharepoint-solutions.md) ve [özelliklerle çalışma](http://go.microsoft.com/fwlink/?LinkID=147704).  
  
### <a name="handle-special-cases"></a>Özel durumları işleme
 Bazı durumlarda, Visual Studio ile bağımlı dosyalarından öğeyi uyumlu hale getirilemiyor. Tüm dosyalar [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] değil çözümlenemiyor klasörün altında görünür **diğer içeri aktarılan dosyaları**. Ayrıca, kendi **DeploymentType** özelliklerinin **NoDeployment** böylece çözümle birlikte dağıtılmaz.  
  
 Liste tanımı ExpenseForms içe aktarırsanız, örneğin, bu ada sahip bir liste tanımı altında görünür **liste tanımları** klasöründe **Çözüm Gezgini** ile birlikte kendi  *Elements.xml* ve *Schema.xml* dosyaları. Ancak, kendi ilişkili ASPX ve HTML formlarına adlı bir klasöre yerleştirilmiş olabilir **ExpenseForms** altında **diğer içeri aktarılan dosyaları** klasör. İçeri aktarma işlemini tamamlamak için bu dosyaları ExpenseForms listesi tanımında altında taşıma **Çözüm Gezgini** değiştirip **DeploymentType** özelliği için her bir dosyadan **NoDeployment** için **ElementFile**.  
  
 Olay alıcıları içeri aktarılırken *Elements.xml* dosyası doğru konuma kopyalanır, ancak çözümle birlikte dağıtır, çözüm paketinde derlemeyi el ile içermelidir. [!INCLUDE[crabout](../sharepoint/includes/crabout-md.md)] Bunu yapmak için bkz. nasıl [nasıl yapılır: ek derlemeler ekleyip](../sharepoint/how-to-add-and-remove-additional-assemblies.md).  
  
 İş akışlarını içeri aktarma, InfoPath formlarını kopyalanıp **diğer içeri aktarılan dosyaları** klasör. Varsa *.wsp* dosyasını içeren bir Web şablonu, başlangıç sayfası olarak ayarla **Çözüm Gezgini**.  
  
## <a name="import-fields-and-property-bags"></a>İçeri aktarma alanları ve özellik paketleri
 Birden fazla alana sahip bir çözüm içeri aktardığınızda, ayrı alan tanımları tümünün tek bir birleştirilmiş *Elements.xml* dosya bir düğümünde **Çözüm Gezgini** adlı **alanları** . Benzer şekilde, tüm özellik paketi girişleri birleştirilir bir *Elements.xml* dosya adında bir düğüm altında **PropertyBags**.  
  
 SharePoint alanlarına bir metin, Boole veya arama gibi belirtilen veri türünde sütunlar var. Daha fazla bilgi için [yapı taşı: sütunları ve alan türleri](http://go.microsoft.com/fwlink/?LinkId=182304). Özellik paketleri bir gruba bir SharePoint sitesindeki bir liste kadar her şeyi SharePoint nesnelere özellikler eklemenize imkan tanır. Özellik paketleri özellik adlarını ve değerlerini karma tablosu uygulanır. Daha fazla bilgi için [yönetme SharePoint Yapılandırması](http://go.microsoft.com/fwlink/?LinkId=182296) veya [SharePoint özellik paketi ayarları](http://go.microsoft.com/fwlink/?LinkId=182297).  
  
## <a name="delete-items-in-the-project"></a>Proje öğeleri sil
 SharePoint çözümleri içindeki öğelerin çoğu, bir veya daha fazla bağımlı öğeleri var. Örneğin, liste örnekleri içerik türlerine bağlıdır ve alanlarda içerik türlerine bağlıdır. Bir SharePoint çözümünü içeri aktardıktan sonra [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] çözüm dağıtmayı denemeden kadar çözüm içindeki bir öğeyi, ancak değil, bağımlı öğeleri silerseniz, tüm başvuru sorunları bilgilendirmez. Örneğin, bir içerik türüne bağlı bir liste örneği içeri aktarılan bir çözümü varsa, ve o içerik türünü Sil dağıtımda bir hata oluşabilir. Bağımlı öğenin SharePoint sunucusu üzerinde mevcut değilse, hata oluşur. Benzer şekilde, silinmiş bir öğeyi de ilgili özellik paketi yoksa, ardından özellik paketi girişler silme **PropertyBags** *Elements.xml* dosya. Bu nedenle, içeri aktarılan bir çözümden öğeleri silin ve dağıtım hataları alırsanız bağımlı öğeler de silinecek gerekip gerekmediğini denetleyin.  
  
## <a name="restore-missing-feature-attributes"></a>Eksik özellik öznitelikleri geri yükleme
 Çözümler içe aktarırken, bazı isteğe bağlı özellik öznitelikleri içeri aktarılan özellik bildiriminden göz ardı edilir. Yeni özellik dosyası içinde bu özniteliklerin geri yüklemek istiyorsanız, yeni özellik bildiriminde özgün özellik dosyasına karşılaştırarak eksik öznitelikler tanımlamak ve konusundaki yönergeleri izleyin [nasıl yapılır: bir SharePoint özelliğiniözelleştirme](../sharepoint/how-to-customize-a-sharepoint-feature.md).  
  
## <a name="deployment-conflict-detection-is-not-performed-on-built-in-list-instances"></a>Dağıtım çakışma algılaması yerleşik liste örnekleri üzerinde gerçekleştirilmez
 [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] Dağıtım çakışma algılaması yerleşik liste örnekleri (SharePoint ile gelen diğer bir deyişle, varsayılan liste örnekleri) gerçekleştirmez. Çakışma algılaması gerçekleştirme değil, SharePoint üzerinde yerleşik liste örnekleri üzerine yazılmasını önlemek için yapılır. Yerleşik liste hala örnekleridir dağıtılan veya güncelleştirildi, ancak hiçbir zaman silineceğini veya üzerine. [!INCLUDE[crdefault](../sharepoint/includes/crdefault-md.md)] [SharePoint paketleme ve dağıtım sorunlarını giderme](../sharepoint/troubleshooting-sharepoint-packaging-and-deployment.md).  
  
## <a name="import-sharepoint-server-2010-workflows"></a>SharePoint Server 2010 iş akışlarını içeri aktarma
 İçinde oluşturulan bir iş akışını içeri aktarırsanız [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)], dağıttıktan sonra düzgün çalışmaz. Belirli bütünleştirilmiş kodların eksik olduğundan iş akışının düzgün çalışmaz ve [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)] iş akışı içinde şu anda desteklenmeyen InfoPath formlarını içeren [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] iş akışı çözümleri. Ancak, içeri aktarılan [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)] başvurularını ekleme gibi bazı öğeler düzelttikten sonra düzgün çalışması için iş akışlarını yapılabilir [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)] derlemeler ve InfoPath formlarını yeniden bağlanıyor. [!INCLUDE[crdefault](../sharepoint/includes/crdefault-md.md)] [SharePoint Server 2010 iş akışlarını içeri aktarma](http://go.microsoft.com/fwlink/?LinkId=182226).  
  
## <a name="item-name-character-limit"></a>Öğe adı karakter sınırı
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Proje ve yol dahil, proje öğe adlarını 260 toplam karakterlik bir sınırı vardır. Bir öğe adı bu sınırı aşarsa, bir çözüm içeri aktarılırken hata iletisi:  
  
 **Belirtilen yol, dosya adı veya her ikisi çok uzun olabilir. Tam dosya adı 260 karakterden az olmalıdır ve dizin adı 248 karakterden kısa olmalıdır.**  
  
 Bu hatayı alırsınız, öğe oluşturulmaz. Bu sorun genellikle içeri aktarılan modüllerle oluşur. Bu sorunu önlemek için aşağıdakileri yapın:  
  
-   Onları girerken, projeniz için kısa adlar kullanın **Yeni Proje Ekle** iletişim kutusu.  
  
-   Kök klasör yolu kısaltmak için mümkün olduğunca yakın bir konuma projesi oluşturun.  
  
## <a name="the-sharepointproductversion-attribute"></a>SharePointProductVersion özniteliği
 Gibi SharePoint önceki bir sürümde oluşturulmuş bir çözümü içeri aktarırsanız [!INCLUDE[winshare3](../sharepoint/includes/winshare3-md.md)] veya [!INCLUDE[offshare7](../sharepoint/includes/offshare7-md.md)], 12.0 için paket bildirimi SharePointProductVersion öznitelik değeri değiştirin veya betik manager denetim tüm içeri aktarılan Web ekleme sayfalar ve bırakın SharePointProductVersion 14.0 için ayarlayın. Aksi takdirde, içeri aktarılan Web forms SharePoint'te görüntülenmez.  
  
### <a name="background"></a>Arka Plan  
 Çözümleri [!INCLUDE[wss_14_short](../sharepoint/includes/wss-14-short-md.md)] ve [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)] SharePointProductVersion adlı bir öznitelik ekleyin. Bu öznitelik, SharePoint çözüm için tasarlanmış SharePoint sürümünü belirlemek için paket Bildirimlerde kullanır. İki 12.0 ve geçerli 14.0 değerlerdir. Öğe için tasarlanmıştır 12.0 değeri gösterir [!INCLUDE[winshare3](../sharepoint/includes/winshare3-md.md)] veya [!INCLUDE[offshare7](../sharepoint/includes/offshare7-md.md)]; 14.0 değeri öğe için tasarlandığını gösterir [!INCLUDE[wss_14_short](../sharepoint/includes/wss-14-short-md.md)] veya [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)].  
  
 ASPX sayfaları işlenirken Gelişmiş Güvenlik [!INCLUDE[wss_14_short](../sharepoint/includes/wss-14-short-md.md)] ve [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)] tüm ASPX veya ana sayfalar içeren bir betik manager denetim gerektirir. Komut Yöneticisi hakkında daha fazla bilgi için bkz. [ScriptManager denetimine genel bakış](http://go.microsoft.com/fwlink/?LinkID=169399). Betik manager denetim kullanılabilir olmadığından [!INCLUDE[winshare3](../sharepoint/includes/winshare3-md.md)] ve [!INCLUDE[offshare7](../sharepoint/includes/offshare7-md.md)], bir eklenmelidir herhangi [!INCLUDE[winshare3](../sharepoint/includes/winshare3-md.md)] veya [!INCLUDE[offshare7](../sharepoint/includes/offshare7-md.md)] sürümüne yükseltilir sayfa [!INCLUDE[wss_14_short](../sharepoint/includes/wss-14-short-md.md)] veya [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)]. Bir standart ana sayfaya zaten eklendiğinden, standart bir ana sayfa kullanan ASPX sayfaları betik manager denetim gerektirmez. Ana sayfa kullanmayın veya özel bir ana sayfa kullanan ASPX sayfaları çalışmak için bir betik denetimi ancak eklemelisiniz [!INCLUDE[wss_14_short](../sharepoint/includes/wss-14-short-md.md)] veya [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)].  
  
 Bir betik manager denetim olmaması içeri aktarırken bir sorun olabilir bir [!INCLUDE[winshare3](../sharepoint/includes/winshare3-md.md)] veya [!INCLUDE[offshare7](../sharepoint/includes/offshare7-md.md)] içine proje [!INCLUDE[vs_dev10_long](../sharepoint/includes/vs-dev10-long-md.md)], tüm yeni projeler SharePointProductVersion öznitelik 14.0 için ayarlanır. Bir komut Yöneticisi olmadan Web formu olan yükseltilmiş projenin dağıtırsanız, formun SharePoint'te görüntülenmez.  
  
## <a name="see-also"></a>Ayrıca bkz.
 [İzlenecek yol: mevcut bir SharePoint sitesinden öğeleri içeri aktarma](../sharepoint/walkthrough-import-items-from-an-existing-sharepoint-site.md)   
 [Yeniden kullanılabilir iş akışlarını içeri aktarma yönergeleri](../sharepoint/guidelines-for-importing-reusable-workflows.md)   
 [İzlenecek yol: bir SharePoint Tasarımcısı yeniden kullanılabilir iş akışını Visual Studio'ya içeri aktarma](../sharepoint/walkthrough-import-a-sharepoint-designer-reusable-workflow-into-visual-studio.md)   
 [Nasıl yapılır: bir SharePoint projesine mevcut bir BDC modeli dosyası ekleme](../sharepoint/how-to-add-an-existing-bdc-model-file-to-a-sharepoint-project.md)  
