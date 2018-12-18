---
title: SharePoint çözümlerinde hata ayıklama | Microsoft Docs
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.Project.WebConfigModificationDialog
- VS.SharePointTools.Project.DebuggingNotEnabled
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, debugging
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 6f53ca7f1a5e449d47a30a32967072f7220c159a
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49903159"
---
# <a name="debug-sharepoint-solutions"></a>SharePoint çözümlerinde hata ayıklama
  SharePoint çözümlerini kullanarak ayıklayabilirsiniz [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] hata ayıklayıcı. Hata ayıklamayı başlattığınızda [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] proje dosyaları SharePoint sunucusuna dağıtır ve ardından Web tarayıcısında SharePoint sitesine bir örneğini açar. Aşağıdaki bölümlerde, SharePoint uygulamalarında hata ayıklama işlemleri açıklanmaktadır [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
-   [Hata ayıklamayı etkinleştirme](#EnableDebug)  
  
-   [F5 hata ayıklama ve dağıtım işlemi](#Deployment)  
  
-   [SharePoint Proje Özellikleri](#Features)  
  
-   [İş Akışlarında Hata Ayıklama](#Workflow)  
  
-   [Hata ayıklama özellik Olay alıcıları](#FeatureEvents)  
  
-   [Gelişmiş hata ayıklama bilgileri etkinleştirme](#EnhancedDebug)  
  
## <a name="enable-debugging"></a>Hata ayıklamayı etkinleştir
 İlk hata ayıklaması yaptığınızda, bir SharePoint çözümünü [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], bir iletişim kutusu web.config dosyasında hata ayıklamayı etkinleştirmek için yapılandırılmamış sizi uyarır. (SharePoint server'ı yüklerken web.config dosyası oluşturulur. Daha fazla bilgi için [Web.config dosyaları ile çalışma](http://go.microsoft.com/fwlink/?LinkID=149266).) İletişim kutusu, hata ayıklamayı etkinleştirmek için ya da proje hata ayıklama veya web.config dosyasında değişiklik olmadan çalışan seçeneği sunar. İlk seçeneği belirlerseniz, proje normal olarak çalıştırır. İkinci seçeneği belirlerseniz, web.config dosyasında yapılandırılır:  
  
- Çağrı yığınındaki Aç (`CallStack="true"`)  
  
- Özel hatalar'ı devre dışı [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] (`<customErrors mode="Off" />`)  
  
- Derleme hata ayıklamayı etkinleştir (`<compilation debug="true">`)  
  
  Sonuçta elde edilen web.config dosyasına aşağıdaki gibidir:  
  
```xml  
<?xml version="1.0" encoding="UTF-8" standalone="yes"?>  
    <configuration>  
        ...  
        <SharePoint>  
            <SafeMode MaxControls="200"  
                CallStack="true"  
                DirectFileDependencies="10"  
                TotalFileDependencies="50"  
                AllowPageLevelTrace="false">  
                ...  
            </SafeMode>  
        ...  
        </SharePoint>  
        <system.web>  
            ...  
            <customErrors mode="Off" />  
            ...  
            <compilation debug="true">  
            ...  
            </compilation>  
            ...  
        </system.web>  
        ...  
    </configuration>  
```  
  
 Değişiklikleri geri almak ve hata ayıklama devre dışı bırakmak için aşağıdaki değiştirme [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] web.config dosyasında:  
  
-   Çağrı yığınını Aç (`CallStack="false"`)  
  
-   Özel hatalar etkinleştirme [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] (`<customErrors mode="On" />`)  
  
-   Derleme hata ayıklama devre dışı bırak (`<compilation debug="false">`)  
  
## <a name="f5-debug-and-deployment-process"></a>F5 hata ayıklama ve dağıtım işlemi
 SharePoint projenizi hata ayıklama modunda çalıştırdığınızda, SharePoint dağıtım işlemi aşağıdaki görevleri gerçekleştirir:  
  
1. Özelleştirilebilir dağıtım öncesi komutlarını çalıştırır.  
  
2. Kullanarak bir Web çözüm paketi (.wsp) dosyası oluşturur [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)] komutları. .Wsp dosyasını tüm özellikleri ve gerekli dosyaları içerir. Daha fazla bilgi için [çözümlerine genel bakış](http://go.microsoft.com/fwlink/?LinkID=128154).  
  
3. SharePoint çözümü Grup çözümü ise geri dönüştüren [!INCLUDE[TLA2#tla_iis5](../sharepoint/includes/tla2sharptla-iis5-md.md)] belirtilen site için uygulama havuzu [!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)]. Bu adım tarafından kilitlenmiş dosyaların sürümleri [!INCLUDE[TLA2#tla_iis5](../sharepoint/includes/tla2sharptla-iis5-md.md)] çalışan işlemi.  
  
4. Paketin önceki bir sürümü zaten varsa, özellikler ve .wsp dosyasını dosyalarında önceki sürümünü geri çeker. Bu adım, özellikleri devre dışı bırakır, çözüm paketine kaldırır ve ardından SharePoint sunucusundaki çözüm paketine siler.  
  
5. .Wsp dosyasında dosyaları ve özellikleri geçerli sürümünü yükler. Bu adım ekler ve çözümün SharePoint sunucusuna yükler.  
  
6. İş akışları, iş akışı derleme yükler. Kullanarak konumunu değiştirebilirsiniz *bütünleştirilmiş kod konumu* özelliği.  
  
7. Site veya Web kapsamındaysa, SharePoint Proje özelliğini etkinleştirir. Grup ve WebApplication kapsamlarda özellikleri etkinleştirilmedi.  
  
8. SharePoint kitaplığı, liste veya seçtiğiniz site iş akışları, iş akışı ilişkilendirir **SharePoint Özelleştirme Sihirbazı**.  
  
   > [!NOTE]  
   >  Yalnızca seçtiyseniz, bu ilişkiyi gerçekleşir **otomatik olarak ilişkilendirme iş akışı** Sihirbazı'nda.  
  
9. Özelleştirilebilir dağıtım sonrası komutları çalıştırır.  
  
10. Ekler [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] için hata ayıklayıcı [!INCLUDE[sharepointShort](../sharepoint/includes/sharepointshort-md.md)] işlem (*w3wp.exe*). Proje türü değiştirmenize izin veriyorsa *Korumalı çözüm* özelliği ve değerini ayarlandığında **true**, hata ayıklayıcı farklı bir işleme iliştirir sonra (*SPUCWorkerProcess.exe*). Daha fazla bilgi için [korumalı çözümle ilgili konular](../sharepoint/sandboxed-solution-considerations.md).  
  
11. SharePoint çözümü ise Grup çözümü, JavaScript hata ayıklayıcıyı başlatır.  
  
12. Web tarayıcısında, uygun bir kitaplık, liste veya site sayfası görüntüler.  
  
    [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Her görev tamamlandıktan sonra çıktı penceresinde bir durum iletisi görüntüler. Bir görev tamamlanamıyor, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Hata Listesi penceresindeki hata iletisi görüntüler.  
  
## <a name="sharepoint-project-features"></a>SharePoint Proje Özellikleri
 Bir özellik, site tanımları'ı kullanarak site değişikliği basitleştirir işlevlerin taşınabilir ve modüler bir birimdir. Ayrıca, bir paket olup [!INCLUDE[sharepointShort](../sharepoint/includes/sharepointshort-md.md)] (WSS) öğeleri, etkinleştirilmesi için belirli bir kapsamda ve kullanıcıları belirli hedef ya da görev gerçekleştirmek yardımcı olur. Şablonları özellikleri dağıtılır.  
  
 Bir proje hata ayıklama modunda çalıştırdığınızda, bir klasörde dağıtım işlemi oluşturur *özellik* dizin konumunda *%COMMONPROGRAMFILES%\Microsoft Shared\web server extensions\14\TEMPLATE\FEATURES*. Özellik adları *proje adı*ö_zellik*x*, TestProject_Feature1 gibi.  
  
 Özellik dizinde çözümün klasörünü içeren bir *özellik tanımı* dosyası ve bir *iş akışı tanımı* dosya. Özellik tanımı dosyası (gt;Feature.xml) dosyaları projenin kurulmasını proje tanım dosyasında açıklar (*Elements.xml*) proje şablonu açıklar. *Elements.xml* bulunabilir **Çözüm Gezgini**, ancak çözüm paketi oluşturulduğunda gt;Feature.XML oluşturulur. Bu dosyalar hakkında daha fazla bilgi için bkz. [SharePoint projesi ve proje öğesi şablonları](../sharepoint/sharepoint-project-and-project-item-templates.md).  
  
## <a name="debug-workflows"></a>İş akışları hata ayıklama
 İş akışı projeleri, hata ayıklaması yaparken [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] (bağlı olarak, türü) iş akışı şablonu bir kitaplığı veya bir listesine ekler. Ardından, el ile eklemek veya bir öğe güncelleştirme iş akışı şablonu başlayabilirsiniz. Ardından [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] iş akışı hata ayıklama.  
  
> [!NOTE]
>  Diğer derlemelere başvurular ekleyin, bu derlemeler genel derleme önbelleğinde yüklü olduğundan emin olun ( [!INCLUDE[TLA2#tla_gac](../sharepoint/includes/tla2sharptla-gac-md.md)]). Aksi takdirde, iş akışı çözümü başarısız olur. Derlemeleri yükleme hakkında daha fazla bilgi için bkz: [el ile bir iş akışını bir belge veya öğeyi Başlat](https://support.office.com/article/Manually-start-a-workflow-on-a-document-or-item-5C106E0E-6FF2-4A75-AF99-F01653BC7963).  
  
 Ancak, dağıtım işlemi, iş akışı başlamıyor. İş akışı SharePoint Web sitesinden başlatmanız gerekir. Ayrıca, Microsoft Office Word 2010 gibi bir istemci uygulaması kullanarak veya ayrı bir sunucu tarafı kod kullanarak iş akışı başlatabilirsiniz. Belirtilen yaklaşımlardan birini kullanın **SharePoint Özelleştirme Sihirbazı**.  
  
 Örneğin, iş akışı el ile başlatılabilir belirtilmişse, iş akışı doğrudan kitaplık veya liste öğesinden başlatın. Bir iş akışı el ile başlatma hakkında daha fazla bilgi için bkz. [el ile bir belge öğe üzerinde bir iş akışı başlatın](https://support.office.com/article/Manually-start-a-workflow-on-a-document-or-item-5C106E0E-6FF2-4A75-AF99-F01653BC7963).  
  
## <a name="debug-feature-event-receivers"></a>Hata ayıklama özellik Olay alıcıları
 Varsayılan olarak çalıştırdığınızda bir [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] SharePoint uygulamasının özelliklerini otomatik olarak sizin için SharePoint sunucusunda etkinleştirilir. Özellik Olay alıcıları hata ayıklaması yaparken bir özellik tarafından etkinleştirildiğinde çünkü Bununla birlikte, bu sorunlara neden [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], hata ayıklayıcı farklı bir işlemde çalıştırır. Başka bir deyişle, kesme noktaları gibi bazı hata ayıklama işlevselliğini düzgün çalışmaz.  
  
 SharePoint özelliğinin otomatik etkinleştirmeyi devre dışı bırakın ve uygun özellik Olay alıcıları hata ayıklamaya izin verecek şekilde projenin değerini **etkin Dağıtım Yapılandırması** özelliğini **Hayıretkinleştirme** hata ayıklama önce. Daha sonra SharePoint uygulamanızda hata ayıklamak başlattıktan sonra [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], el ile SharePoint özelliği etkinleştirin. Özelliğini etkinleştirmek için açık **Site eylemleri** SharePoint menüsünde **Site Ayarları**, seçin **Site özellikleri Yönet** bağlamak ve ardından **Etkinleştirme** normal hata ayıklamaya devam etmek için özelliğin yanındaki düğmesi.  
  
## <a name="enable-enhanced-debug-information"></a>Gelişmiş hata ayıklama bilgilerini etkinleştir
 Bazen karmaşık arasındaki etkileşimleri nedeniyle [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] işlem (devenv.exe) [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] SharePoint ana bilgisayar işlemi (*vssphost4.exe*), SharePoint ve ortaya çıkan hataları tanılama WCF katmanı sırada geliştirmeyi, dağıtmayı ve benzeri bir mücadele haline gelebilir. Bu tür hatalar çözmenize yardımcı olması için Gelişmiş hata ayıklama bilgileri etkinleştirebilirsiniz. Bunu yapmak için Windows kayıt defterinde aşağıdaki kayıt defteri anahtarına gidin:  
  
 **HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\11.0\SharePointTools**  
  
 Varsa "EnableDiagnostics" **REG_DWORD** değer zaten var, el ile oluşturun. "EnableDiagnostics" değerini "1" olarak ayarlayın  
  
 Bu anahtarı değeri 1 nedenleri yığınına ayarı izleme bilgilerini görünmesini **çıkış** çalışırken proje sistemi hataları meydana geldiğinde penceresi [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Gelişmiş hata ayıklama bilgileri devre dışı bırakmak için EnableDiagnostics 0 olarak ayarlayın veya değeri silin.  
  
 Diğer SharePoint kayıt defteri anahtarları hakkında daha fazla bilgi için bkz. [uzantıları Visual Studio'da SharePoint araçları için hata ayıklama](../sharepoint/debugging-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## <a name="see-also"></a>Ayrıca bkz.
 [SharePoint çözümlerinde sorun giderme](../sharepoint/troubleshooting-sharepoint-solutions.md)  
  
