---
title: SharePoint çözümlerinde sorun giderme | Microsoft Docs
ms.custom: ''
ms.date: 02/22/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- Microsoft.VisualStudio.Tools.SharePoint.Errors.Debugging
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, troubleshooting
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: f68f6e50be569df6130f7e6c6f3aa4bc7c107214
ms.sourcegitcommit: 0a8ac5f2a685270d9ca79bb39d26fd90099bfa29
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/09/2018
ms.locfileid: "51296053"
---
# <a name="troubleshoot-sharepoint-solutions"></a>SharePoint çözümlerinde sorun giderme
  SharePoint çözümlerini kullanarak hata ayıklaması yaparken aşağıdaki sorunları veya uyarılar ortaya çıkabilir [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] hata ayıklayıcı. Daha fazla bilgi için [hata ayıklama SharePoint 2007 iş akışı çözümleri](https://msdn.microsoft.com/3a5392f3-66f3-48be-956e-02de23fa6247).
  
## <a name="token-restrictions-in-sandboxed-visual-web-parts"></a>Korumalı bir görsel web bölümleri içindeki belirteç kısıtlamaları
 Korumalı çözümler ortamdaki görsel web bölümleri SharePoint çalışma zamanını destekleyen $SPUrl gibi standart belirteçleri işleyemiyor. Sonuç olarak, URL çözülmüş değildir ve sizin için bir betik öğesinde doğrudan gibi aşağıdaki örnekte başvuruyorsa visual web bölümü tasarımcısında Tasarım görünümünde içeriği önizlemesi görüntülenemiyor:  
  
```xml  
<script src="<% $SPUrl:~site/SiteAssets/ListOperations.js %>"></script>  
```  
  
 Bu sınırlamaya geçici bir çözüm ve belirteci çözülemedi, değişmez değerlerini kullanarak başvurmak için:  
  
```xml  
<asp:literal ID="Literal1" runat="server" Text="<script src='" />  
<asp:literal ID="Literal2" runat="server" Text="<% $SPUrl:~site/SiteAssets/ListOperations.js %>" />  
<asp:literal ID="Literal3" runat="server" Text="' type='text/javascript' ></script>" />  
```  
  
## <a name="character-restrictions-in-names-of-projects-and-project-items"></a>Proje ve proje öğelerinin adlarındaki karakter kısıtlamaları
 Proje ve proje öğeleri adları, yalnızca SharePoint 2010'daki bir dağıtım yolda geçersiz karakterler içerebilir. Diğer bir karakterlere izin verilir.  
  
### <a name="error-message"></a>hata iletisi
 "Geçersiz karakterler" hata iletisi.  
  
### <a name="resolution"></a>Çözüm  
 SharePoint projeleri ve proje öğeleri adları için yalnızca şu karakterleri kullanın:  
  
- Alfasayısal ASCII karakterler  
  
- Alan  
  
- Nokta (.)  
  
- Virgül (,)  
  
- Alt çizgi (_)  
  
- Tire (-)  
  
- Ters eğik çizgi (\\)  
  
  Bir proje paketlediğinizde, bir doğrulama kuralı dağıtmakta her dosya için dağıtım yolu özelliği yalnızca bu geçerli karakterleri içerdiğini doğrular.  
  
## <a name="errors-when-creating-custom-fields"></a>Özel alanlar oluştururken hatalar oluşuyor
 İçinde [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], özel alanlar, XML dosyasında tanımlanır. Bir alanı tanımlı değil veya belirli bir biçimi kullanılarak başvurulan hatalar oluşabilir.  
  
### <a name="error-message"></a>hata iletisi
 Paketleme zaman "Geçersiz karakterler" hata iletisi.  
  
### <a name="resolution"></a>Çözüm  
 Bir alan tanımı kimliği tarafından aşağıdaki örnekte gösterildiği gibi küme ayraçları içine alınmış bir GUID olması gerekir:  
  
```xml  
<Field ID="{5744d18c-305e-4632-8bd1-09d134f4830d}"   
    Type="Note"   
    Name="PatientName"   
    DisplayName="Patient Name"   
    Group="A Custom Group">  
</Field>.  
```  
  
 Aşağıdaki örnekte gösterildiği gibi bir içerik türü alan başvuru boş öğe biçimini kullanarak tanımlanmalıdır (\<FieldRef / >), başlangıç/bitiş öğeleri kullanarak değil (\<FieldRef >\</FieldRef >):  
  
```xml  
<FieldRef ID="{5744d18c-305e-4632-8bd1-09d134f4830d}"   
    Name="PatientName"   
    DisplayName="Patient Name"   
    Required="TRUE"/>  
```  
  
 Alan için kaynak XML hatalı biçimlendirilmiş, geçerli bir XML dosyası değil veya başka bir sorunun yaşandığı hata "dosyasını ayrıştıramıyor" gerçekleşir.  
  
## <a name="new-non-english-site-definitions-do-not-appear-in-site-creation-page-after-deployment"></a>Dağıtımdan sonra yeni İngilizce olmayan site tanımları site oluşturma sayfasında görünmez
 İngilizce olmayan bir sürümünü kullanarak bir site tanımı oluşturup sonra [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] (diğer bir deyişle, bir yerel ayar sürümüyle [!INCLUDE[TLA2#tla_id](../sharepoint/includes/tla2sharptla-id-md.md)] 1033 dışında), **SharePoint özelleştirmeleri** içinde sekmesigörünmüyorsa**Şablon Seçimi** kutusu ve yeni site şablonu içinde görünmüyorsa **yeni SharePoint sitesi** sayfası.  
  
### <a name="error-message"></a>hata iletisi
 Yok.  
  
### <a name="resolution"></a>Çözüm  
 Bu sorun nedeniyle yanlış bir değere **yolu** gibi webtemp site tanımı yapılandırması için özellik dosyası *webtemp_SiteDefinitionProject1.xml*. İçinde **yolu** özelliği altında bulunan webtemp dosyası için **dağıtım konumu**, 1033 uygun yerel ayarı değiştirme [!INCLUDE[TLA2#tla_id](../sharepoint/includes/tla2sharptla-id-md.md)]. Örneğin, kullanılacak bir Japonca yerel ayarında değerini değiştirin için 1041. Daha fazla bilgi için [Microsoft tarafından atanan yerel kimlikler](http://go.microsoft.com/fwlink/?LinkID=165561).  
  
## <a name="error-appears-when-a-workflow-project-is-deployed-on-a-clean-system"></a>Temiz bir sistemde bir iş akışı projesi dağıtıldığında hata görüntülenir.
 Bir iş akışı projesinde dağıtırsanız, bu sorun oluşur [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] temiz bir sistemde. Yeni yüklemesini olduğu bir bilgisayarda temiz bir sistemdir [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] ve SharePoint, ancak dağıtılmış iş akışı projesi yok.  
  
### <a name="error-message"></a>hata iletisi
 SharePoint listesi bulunamıyor: İş Akışı Geçmişi.  
  
### <a name="resolution"></a>Çözüm  
 Bu hata, eksik bir iş akışı geçmiş listesinin nedeniyle oluşur. Geliştirme ortamınızı temiz bir sistemi olduğundan, hiçbir iş akışları dağıtılır ve iş akışı geçmiş listesinin henüz mevcut değil. Bu sorunu çözmek için iş akışı geçmiş listesinin oluşturulması neden olan iş akışı Sihirbazı ' nı yeniden açın.  
  
##### <a name="to-reenter-the-workflow-wizard"></a>İş akışı Sihirbazı'nı yeniden girmek için  
  
1.  İçinde **Çözüm Gezgini**, iş akışı düğümünü seçin.  
  
2.  İçinde **özellikleri** penceresinde üç noktalı düğme bulunan herhangi bir özellikte nokta (...) düğmesini seçin.  
  
## <a name="user-must-refresh-application-page-in-browser-while-debugging-to-view-updated-image"></a>Kullanıcı uygulama sayfasını tarayıcıda güncelleştirilmiş resmi görmek için hata ayıklama sırasında yenilemeniz gerekir
 Gibi bir resim görüntüleyen bir denetimi ile bir uygulama sayfasını içeren bir SharePoint çözüm hata ayıklama, bir [!INCLUDE[TLA2#tla_html](../sharepoint/includes/tla2sharptla-html-md.md)] görüntü denetimi görüntüye yapılan değişiklikleri görüntülemek için tarayıcı içinde sayfayı yenileyin gerekir.  
  
## <a name="error-the-site-location-is-not-valid"></a>Hata: Site konumu geçerli değil
 Bu sorun ortaya çıkabilir [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)] yüklü değil. Belirtilen SharePoint Web sitesine yönetici erişimi yoksa da oluşabilir **SharePoint Özelleştirme Sihirbazı**.  
  
### <a name="error-message"></a>hata iletisi
  
-   SharePoint site konumu geçerli değil.  
  
### <a name="resolution"></a>Çözüm  
  
-   [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)]yükleyin.  
  
-   SharePoint Web sitesine yönetici erişimi olduğundan emin olun. Daha fazla bilgi için [!INCLUDE[TLA2#tla_office](../sharepoint/includes/tla2sharptla-office-md.md)] çevrimiçi makalede [atama veya SharePoint Server yöneticileri, hizmet uygulaması kaldırma](https://docs.microsoft.com/sharepoint/administration/assign-or-remove-administrators-of-service-applications).  
  
## <a name="site-deletion-web-event-does-not-occur-in-event-receiver-project"></a>Site silme web olayı olay alıcısı projesinde gerçekleşmez
 Bir olay alıcısı projesi oluşturun ve "bir site silinirken gibi" belirli Web olayları seçin, olayı hiçbir zaman oluşur.  
  
### <a name="error-message"></a>hata iletisi
 Yok.  
  
### <a name="resolution"></a>Çözüm  
 Özellik kapsamına site düzeyinde olayları işlemek için "Site" olmalı, ancak "Web" olay alıcısı projeleri için varsayılan özellik kapsamı olduğundan bu sorun oluşur. Etkilenen Web olaylar şunlardır:  
  
- Bir site oluşturuluyor (WebDeleting) silindi  
  
- Bir site silindikten sonra (WebDeleted)  
  
- Bir site oluşturuluyor (WebMoving) taşındı  
  
- Bir site taşındıktan sonra (WebMoved)  
  
  Sorunu gidermek için olay alıcısının özellik kapsamına aşağıdaki gibi değiştirin.  
  
##### <a name="to-change-the-feature-scope-of-the-event-receiver"></a>Özellik kapsamına ait olay alıcısının değiştirmek için  
  
1.  İçinde **Çözüm Gezgini**, olay alıcının açın *.feature* dosyası **özellik Tasarımcısı** dosyasına çift veya onun kısayol menüsünü açın ve ardından seçme **açık**.  
  
2.  Yanındaki oku seçin **kapsam**ve ardından **Site** listesinde görünür.  
  
## <a name="deployment-error-appears-after-the-name-of-an-identifier-in-a-business-data-connectivity-model-project-is-changed"></a>Bir iş verileri bağlantısı modeli proje bir tanımlayıcı adı değiştirildikten sonra dağıtım hatası görünür.
 Bir varlıkta bir iş verileri bağlantısı (BDC) modeli tanımlayıcı adını değiştirin ve sonra çözümü dağıtmak deneyin, bu sorun oluşur.  
  
### <a name="error-messages"></a>Hata iletileri
  
-   \<*model adı*> şu dış içerik türü etkinleştirme hatalar...  
  
-   Adla IMetadataObject '\<*model adı*>' 'yineleniyor alan adı ' bir değere sahip...  
  
### <a name="resolution"></a>Çözüm  
 Bu sorunu çözmek için model el ile silin ve ardından çözümü yeniden dağıtın.  Aşağıdaki araçlardan birini kullanarak model silebilirsiniz:  
  
-   SharePoint 2010 Merkezi Yönetim'ı seçin. Daha fazla bilgi için [İVB Model Yönetimi](http://go.microsoft.com/fwlink/?LinkID=181472) Microsoft TechNet Web sitesinde.  
  
-   Windows PowerShell. Komut isteminde aşağıdaki komutu yazarak model silebilirsiniz: **Remove-SPBusinessDataCatalogModel**. Daha fazla bilgi için [genel cmdlet'leri (SharePoint Server 2010)](http://go.microsoft.com/fwlink/?LinkID=182375) Microsoft TechNet Web sitesinde.  
  
## <a name="an-error-appears-when-you-try-to-view-a-visual-web-part-in-sharepoint"></a>SharePoint'te bir görsel web bölümü görüntülemeye çalıştığınızda bir hata görüntülenir.
 Bu sorun, **yolu** özelliği kullanıcı denetiminin dizesi ile başlayan değil "CONTROLTEMPLATES\\".  
  
### <a name="error-messages"></a>Hata iletileri
  
-   Dosya ' /_CONTROLTEMPLATES/*\<proje adı >*/*\<Web Bölümü adı >*/*\<kullanıcı denetimi adı >*.ascx' mevcut değil.  
  
-   '/' Uygulamasında sunucu hatası.  
  
### <a name="resolution"></a>Çözüm  
  
##### <a name="to-resolve-this-issue"></a>Bu sorunu çözmek için  
  
1.  İçinde **Çözüm Gezgini**, dosya adı uzantısı olan kullanıcı denetimi dosya *.ascx*.  
  
2.  Menü çubuğunda, **görünümü** > **Özellikler penceresi**.  
  
3.  İçinde **özellikleri** penceresini genişletin **dağıtım konumu** düğümü.  
  
4.  Değerini emin **yolu** özelliği dizesi ile başlar "CONTROLTEMPLATES\\".  
  
## <a name="error-appears-when-an-imported-reusable-workflow-that-contains-a-task-form-field-is-run"></a>Bir görev form alanı içeren bir içeri aktarılan yeniden kullanılabilir iş akışını çalıştırdığınızda hata görüntülenir.
 Bir alanı görev formuna içeren bir iş akışı alın ve ardından aktardığınız aynı sistemde yeni iş akışını çalıştırmak, bu sorun oluşur.  
  
### <a name="error-message"></a>hata iletisi
 Etkinleştir'Özellikler ' dağıtım adımda hata oluştu: alan kimliği [*GUID*] özelliği tanımlı [*GUID*] geçerli site koleksiyonunu veya bir alt sitede bulunamadı.  
  
### <a name="resolution"></a>Çözüm  
 Bu hata yeniden kullanılabilir iş akışını içeri aktar proje içinde olduğundan, alan kimliği çakışması sonucudur [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] görev form alanı kimlikleri değiştirmez. İçeri aktarılan bir iş akışı özgün iş akışı içeren aynı sunucuda dağıtırsanız, alan kimliği çakışması oluşur.  
  
 Bu sorunu çözmek için tüm içeri aktarılan iş akışı dosyalarını alan kimliği özniteliğinin değerini değiştirmek için Bul ve Değiştir özelliğini kullanın.  
  
## <a name="error-appears-when-a-renamed-imported-list-instance-is-run"></a>Yeniden adlandırılan bir içe aktarılırken hata liste örneği çalıştırmak görünür
 Alınan liste örneği yeniden adlandırın ve ardından çalışmasında Bu sorun oluşur [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
### <a name="error-message"></a>hata iletisi
 Derleme hatası: 'Özellikleri etkinleştir' dağıtım adımda hata oluştu: ' % s'dosyası Template\Features\\[*projesini içeri*<em>özellik</em>*adı*] \Files\Lists \\[*eski*<em>liste adı</em>] \Schema.xml mevcut değil.  
  
### <a name="resolution"></a>Çözüm  
 Bir liste örneği içeri aktardığınızda CustomSchema adlı bir öznitelik liste örneği için Elements.xml dosyası eklenir. Elements.XML liste örneği için özel bir schema.xml yolunu içerir. Liste örneği olarak adlandırın zaman [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]özel schema.xml dağıtım yolunu değiştirir ancak CustomSchema özniteliğinin yol değeri güncelleştirilmez. Sonuç olarak, liste örneği bulunamıyor *schema.xml* özelliği etkinleştirildiğinde CustomSchema özniteliği tarafından belirtilen yolda eski dosya.  
  
 Bu sorunu çözmek için dağıtım konumu yolu güncelleştirme *schema.xml* CustomSchema öznitelik dosyasında.  
  
## <a name="sharepoint-debugging-session-terminated-by-iis"></a>SharePoint hata ayıklama oturumu IIS tarafından sonlandırıldı
 Bir kesme noktası ayarlarsanız bu sorun bir [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] SharePoint çözümünü seçin **F5** çalıştırın ve ardından 90 saniyeden daha uzun bir kesme noktasında kalması için anahtar.  
  
### <a name="error-message"></a>hata iletisi
 Ayıklanan Web sunucusu işlemi Internet Information Services (IIS) tarafından sonlandırıldı. IIS uygulama havuzu ping ayarlarını yapılandırarak bu sorunu önleyebilirsiniz. Bkz. daha fazla ayrıntı için Yardım.  
  
### <a name="resolution"></a>Çözüm  
 Varsayılan olarak, IIS uygulama havuzu bir uygulamanın uygulama kapatılmadan önce yanıt 90 saniye bekler. Bu işlem, "uygulama ping olarak" adı verilir. Bu sorunu çözmek için bekleme süresini artırmak veya tamamen ping işlemi uygulamayı devre dışı bırakabilirsiniz.  
  
##### <a name="to-access-the-iis-app-pool-settings"></a>IIS uygulama havuzu ayarlarını erişmek için  
  
1.  IIS Yöneticisi'ni açın.  
  
2.  İçinde **bağlantıları** bölmesinde, SharePoint sunucu düğümünü genişletin ve ardından **uygulama havuzları** düğümü.  
  
3.  Üzerinde **uygulama havuzları** (genellikle "SharePoint - 80"), SharePoint uygulama havuzu seçin ve ardından **eylemleri** bölmesinde seçin **Gelişmiş ayarlar** bağlantı.  
  
4.  IIS zaman aşımından önce bekleme süresini artırmak için değerini değiştirmek **Ping en yüksek yanıt süresi (saniye)** 90 saniyeden büyük olan bir değer.  
  
5.  Ping IIS devre dışı bırakmak için ayarlanmış **Ping etkin** için **False**.  
  
## <a name="auto-retract-leaves-orphaned-list-instance-in-sharepoint"></a>SharePoint'te bırakır yalnız bırakılmış bir liste örneği otomatik geri çek
 Aşağıdaki adımlar bu sorun oluşur.  
  
1.  Bir liste örneği sahip bir liste tanımı oluşturma [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
2.  Seçin **F5** çözümü çalıştırmak için anahtar.  
  
3.  Hata ayıklamayı durdurmak veya SharePoint sitesi kapatın.  
  
4.  SharePoint sitesine yeniden açın ve liste örneği açın.  
  
### <a name="error-message"></a>hata iletisi
 '/' Uygulamasında sunucu hatası.  
  
### <a name="resolution"></a>Çözüm  
 Sonra bir SharePoint çözümünün bir hata ayıklama oturumu kapatmak için böyle otomatik geri çekme özelliği, çözümü geri çeker. Geri çekme SharePoint liste tanımını siler ancak liste örneğini silmez. Temel alınan liste tanımı tarafından liste örneği gereklidir.  
  
 Bu sorunu çözmek için menü çubuğundan seçme dağıtımınızdan **derleme** > **Dağıt**. (Çözüm seçerek hata ayıklama olmayan **F5** anahtarı.) Ardından, SharePoint'te bir liste örneği silin.  
  
## <a name="original-sharepoint-solution-is-replaced-by-an-exported-version"></a>Özgün SharePoint çözüm dışarı aktarılan bir sürüm ile değiştirilir
 Bir SharePoint çözümünü verdiğinizde, çözümün içine aktarın [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]ve ardından çözümü, dışarı aynı sitede yeniden dağıtmak, özgün SharePoint çözüm değiştirilir. Çözüm üzerinde etkin özgün çözümüne sahip bir sunucuya dağıtırsanız, bu sorun gerçekleşmez.  
  
### <a name="error-message"></a>hata iletisi
 Yok.  
  
### <a name="resolution"></a>Çözüm  
 İçinden, dışarı aktarılan sitesinde bir çözüm üzerine yazılmasını önlemek için SolutionID GUID'leri ve içeri aktarılan tüm özelliklerini özellik kimliklerini değiştirme [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] proje.  
  
## <a name="error-appears-when-debugging-starts"></a>Hata ayıklama başladığında hata görüntülenir.
 Bir SharePoint çözümünü Visual Studio'da hata ayıklamak başlattığınızda, belirli bir anahtarın sözlükte olmadığından Visual Studio Web.config dosyası yüklenemedi bir hata olduğunu gösterir.  
  
### <a name="error-message"></a>hata iletisi
 Web.config yapılandırma dosyası yüklenemedi. Dosya hatalı biçimlendirilmiş XML öğeleri için denetleyin ve yeniden deneyin. Şu hata oluştu: verilen anahtar sözlükte yoktu.  
  
### <a name="resolution"></a>Çözüm  
 Bu sorunu çözmek için Visual Studio'da SharePoint projenin Site URL'si özellik değeri için alternatif erişim eşlemeleri web uygulamasının varsayılan bölgeye atanan URL eşleştiğinden emin olun. Intranet gibi başka bir bölge için URL'yi kullanarak bir hata oluştu çözümlenemiyor. Site, projenin URL'sini ve varsayılan bölge URL'de eşleşmelidir. Alternatif erişim eşlemeleri erişmek için SharePoint 2010 Merkezi Yönetim yardımcı programı'nı açın, **Uygulama Yönetimi** bağlantısını ve sonra **Web uygulamaları**, seçin  **Alternatif erişim eşlemelerini yapılandırma** bağlantı. Daha fazla bilgi için [Web uygulamaları için bölge oluşturma](http://go.microsoft.com/fwlink/?LinkId=192274).  
  
## <a name="see-also"></a>Ayrıca bkz.
 [SharePoint paketleme ve dağıtım sorunlarını giderme](../sharepoint/troubleshooting-sharepoint-packaging-and-deployment.md)   
 [Derleme ve SharePoint çözümlerinde hata ayıklama](../sharepoint/building-and-debugging-sharepoint-solutions.md)   
 [Visual Studio’da hata ayıklama](/visualstudio/debugger/debugging-in-visual-studio)  
  
  
