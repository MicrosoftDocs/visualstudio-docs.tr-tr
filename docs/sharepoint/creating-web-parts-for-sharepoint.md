---
title: SharePoint için Web bölümleri oluşturma | Microsoft Docs
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- Microsoft.SharePoint.WebControls.DateTimeControl
- Microsoft.SharePoint.WebControls.CssLink
- Microsoft.SharePoint.WebControls.RssLink
- Microsoft.SharePoint.WebControls.Theme
- Microsoft.SharePoint.WebControls.AspMenu
- Microsoft.SharePoint.WebControls.ListProperty
- Microsoft.SharePoint.WebControls.ProjectProperty
- Microsoft.SharePoint.WebControls.FormsDigest
- Microsoft.SharePoint.WebControls.ScriptLink
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, Web Parts
- Web Parts [SharePoint development in Visual Studio], designing
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 0cbc26a198cace58a957f3d3aaf25457cf457256
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49906051"
---
# <a name="create-web-parts-for-sharepoint"></a>SharePoint için Web bölümleri oluşturma
  Web Bölümleri'ni kullanarak, içeriğini, görünümünü ve davranışını bir SharePoint sitesi sayfalarının bir tarayıcı kullanarak değiştirebilirsiniz. Web Bölümleri olan bir web bölümü sayfasının içinde çalışan sunucu tarafı denetimleri: bir SharePoint sitesinde görünen sayfaların yapı taşları oldukları. Bkz: [yapı taşı: Web Bölümleri](http://go.microsoft.com/fwlink/?LinkID=182097).  
  
 Oluşturun ve Visual Studio şablonlarını kullanarak bir SharePoint sitesinde web bölümleri hata ayıklayın.  
  
## <a name="create-a-web-part-in-visual-studio"></a>Visual Studio'da bir web bölümü oluşturma
 Ekleyerek bir web bölümü oluşturma bir **Web Bölümü** herhangi bir SharePoint projesine öğesi. Kullanabileceğiniz bir **Web Bölümü** bir korumalı çözüm veya grup çözümünde öğe.  
  
 Görsel Tasarımcı kullanarak bir web bölümü tasarlamak istiyorsanız oluşturma bir **görsel Web Bölümü** ekleyin veya proje **görsel Web Bölümü** herhangi bir SharePoint projesine öğesi. Kullanabileceğiniz bir **görsel Web Bölümü** yalnızca Grup çözümünde öğesi.  
  
### <a name="web-part-item"></a>Web Bölümü öğesi
 A **Web Bölümü** öğesi, bir SharePoint sitesi için bir web bölümü tasarlamak için kullanabileceğiniz dosyaları sağlar. Eklediğinizde bir **Web Bölümü** öğesi, Visual Studio projenize bir klasör oluşturur ve ardından çeşitli dosyalar klasörüne ekler. Aşağıdaki tabloda her dosya açıklanmaktadır.  
  
|Dosya|Açıklama|  
|----------|-----------------|  
|*Elements.XML*|Projenizdeki Özellik tanım dosyasının web bölümünü dağıtmak için kullandığı bilgileri içerir.|  
|.WebPart dosyası|SharePoint web bölümü, bir web bölümü galerisinde görüntülemesi gereken bilgileri sağlar.|  
|Kod dosyası|Web bölümüne denetimler ekleyen ve web bölümü içinde özel içerik oluşturan yöntemleri içerir.|  
  
 Daha fazla bilgi için [nasıl yapılır: bir SharePoint web bölümü oluşturma](../sharepoint/how-to-create-a-sharepoint-web-part.md).  
  
### <a name="visual-web-part-item"></a>Visual web bölümü öğesi
 Bir görsel web bölümü, Visual Studio'da Visual Web Developer Tasarımcısını kullanarak oluşturduğunuz bir web bölümüdür. Bir görsel web bölümü herhangi bir web bölümü olarak aynı şekilde çalışır. Bir web bölümüne düğme ve metin kutuları gibi denetimler eklemek için bir XML dosyası için kodu ekleyin. Ancak, denetimleri bir görsel web bölümü için sürükleyerek ya da Visual Studio içindeki web parçalarına kopyalayarak eklediğiniz **araç kutusu**. Tasarımcı, sonra gerekli kodu XML dosyasında oluşturur. Bkz: [nasıl yapılır: Tasarımcı kullanarak oluşturma SharePoint web bölümü](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md).  
  
## <a name="sharepoint-controls"></a>SharePoint denetimleri
 Visual Studio, uygulama sayfaları gibi SharePoint sayfaları oluşturmak için bazı denetimler sunar. Bu denetimlerin görünür **araç kutusu** altında **SharePoint denetimleri**. Bu denetimlerin işlevleri türetildiği [Microsoft.SharePoint.WebControls](http://go.microsoft.com/fwlink/?LinkId=235315) SharePoint site ve liste sayfalarında kullanılan ASP.NET sunucu denetimlerini içeren ad alanı.  
  
|Denetim adı|Açıklama|  
|------------------|-----------------|  
|[AspMenu](http://go.microsoft.com/fwlink/?LinkId=235307)|ASP menüsü ekler. Daha fazla bilgi için [Menü denetimine genel bakış](http://go.microsoft.com/fwlink/?LinkId=235316).|  
|[CssLink](http://go.microsoft.com/fwlink/?LinkId=235308)|Ekler bir **bağlantı** öğesine *.aspx* tarafından tanımlanan bir veya daha fazla dış stil sayfasını uygular ve sayfa **CssRegistration**.|  
|[DateTimeControl](http://go.microsoft.com/fwlink/?LinkId=235306)|Bir DateTime denetimine ekler *.aspx* sayfası.|  
|[FormDigest](http://go.microsoft.com/fwlink/?LinkId=235309)|İçine bir güvenlik doğrulaması ekler *.aspx* sayfası|  
|[ListProperty](http://go.microsoft.com/fwlink/?LinkId=235310)|Belirtilen bir listenin bir özelliğini döndürür.|  
|[ProjectProperty](http://go.microsoft.com/fwlink/?LinkId=235311)|Geçerli Web sitesinin genel bir özelliğini döndürür.|  
|[RssLink](http://go.microsoft.com/fwlink/?LinkId=235312)|İçine bir RSS bağlantısını ekler *.aspx* sayfası.|  
|[ScriptLink](http://go.microsoft.com/fwlink/?LinkId=235313)|Özellikler ve sayfa işlendiğinde bunlar istenebilir bir sayfadaki komut dosyaları gibi kaynakları kaydetme için yöntemler sağlar.|  
|[Tema](http://go.microsoft.com/fwlink/?LinkId=235314)|Bir tema uygular *.aspx* sayfası.|  
  
## <a name="debug-a-web-part"></a>Bir web bölümü hata ayıklama
 Yalnızca, diğer Visual Studio projelerinde yaptığınız gibi bir web bölümü içeren bir SharePoint Proje hata ayıklama yapabilirsiniz. Visual Studio hata ayıklayıcısını başlattığınızda, Visual Studio SharePoint sitesi açılır.  
  
 Kodunuzda hata ayıklamayı başlatmak için web bölümünü bir SharePoint web bölümü sayfasına ekleyin.  
  
 SharePoint projelerinde hata ayıklama hakkında daha fazla bilgi için bkz: [sorun giderme SharePoint çözümleri](../sharepoint/troubleshooting-sharepoint-solutions.md).  
  
## <a name="visual-web-part-limitations"></a>Visual web bölümü sınırlamaları
 Visual Studio'da başlatarak, korumalı SharePoint çözümlerine ve Grup çözümlerine görsel web bölümleri ekleyebilirsiniz. Ancak görsel web parçaları şu sınırlamalara sahiptir:  
  
- Görsel web bölümleri değiştirilebilir parametreleri desteklemez. Daha fazla bilgi için [değiştirilebilir parametreler](../sharepoint/replaceable-parameters.md).  
  
- Kullanıcı denetimleri veya görsel web bölümlerine sürüklenip ve bırakılan veya olamaz görsel web bölümlerine kopyalanır. Bu eylem, bir derleme hatasına neden olur.  
  
- Görsel web bölümleri $SPUrl gibi SharePoint sunucu belirteçlerini doğrudan desteklemez. Daha fazla bilgi için "Belirteci kısıtlamaları içinde Sandboxed Visual Web Bölümleri" bölümüne bakın. [sorun giderme SharePoint çözümleri](../sharepoint/troubleshooting-sharepoint-solutions.md).  
  
- Bir korumalı çözüm içindeki görsel web bölümleri bazen alma hatası, "korumalı kod ana bilgisayar hizmeti isteği işleyemeyecek kadar meşgul olduğundan korumalı kod yürütme isteği reddedildi." Bu gönderide bu hata hakkında daha fazla bilgi için bkz. [SharePoint Developer Team Blog](http://go.microsoft.com/fwlink/?LinkId=225932).  
  
- Sunucu tarafı JavaScript hata ayıklama Visual Studio'da desteklenmez ancak istemci tarafı JavaScript hata ayıklama desteklenir.  
  
   Satır içi JavaScript'i sunucu taraflı bir biçimlendirme dosyasına ekleyebilirsiniz, ancak biçimlendirmeye eklenen kesme noktaları için hata ayıklama desteği sunulmaz. JavaScript hata ayıklama için başvurusu için biçimlendirme dosyasında harici bir JavaScript dosyasına ve ardından JavaScript dosyasında kesme noktaları ayarlayın.  
  
- Satır içi hata ayıklama [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] kod biçimlendirme dosyası yerine üretilen kod dosyasında yapılmalıdır.  
  
- Görsel web bölümleri kullanımını desteklemez `<@ Assembly Src=` yönergesi.  
  
- SharePoint web denetimleri ve bazı [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] denetimleri SharePoint korumalı ortamında desteklenmez. Hata, bir korumalı çözüm içindeki bir görsel web bölümü üzerinde desteklenmeyen denetimler kullanılıyorsa "'Theme' ad alanı 'Microsoft.SharePoint.WebControls' içinde yok. tür veya ad alanı adı" görünür.  
  
  Korumalı çözümler hakkında daha fazla bilgi için bkz. [korumalı arasındaki farklar ve Grup çözümleri](../sharepoint/differences-between-sandboxed-and-farm-solutions.md).  
  
## <a name="create-older-style-sharepoint-based-web-parts"></a>Eski stil SharePoint tabanlı web bölümleri oluşturma
 Özel oluşturmak için Visual Studio içindeki şablonları kullanabilirsiniz [!INCLUDE[vstecasplong](../sharepoint/includes/vstecasplong-md.md)] için SharePoint web bölümleri. [!INCLUDE[vstecasplong](../sharepoint/includes/vstecasplong-md.md)] Web bölümleri, üst kısmındaki yerleşiktir [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] web bölümü yapısı ve yeni projeler için önerilen türdür.  
  
 Çok az durumda, eski stilde SharePoint tabanlı web bölümü kullanarak bir web bölümü oluşturmanız gerekebilir. Bu türde web bölümleri oluşturmak için Visual Studio'yu kullanabilirsiniz, ancak Visual Studio özellikle bunları oluşturmanıza yardımcı olmak üzere tasarlanmış şablonlar içermez.  
  
 Ne zaman eski stilde SharePoint tabanlı web bölümü oluşturmak isteyebilirsiniz hakkında daha fazla bilgi için bkz. [Windows SharePoint Services Web Bölümü altyapısı](http://go.microsoft.com/fwlink/?LinkId=169290). Eski stilde SharePoint tabanlı web bölümü kullanarak bir web bölümü oluşturma hakkında daha fazla bilgi için bkz. [basit bir SharePoint Web Bölümü oluşturma için izlenecek yol](http://go.microsoft.com/fwlink/?LinkId=169288).  
  
## <a name="related-topics"></a>İlgili konular
  
|Başlık|Açıklama|  
|-----------|-----------------|  
|[Nasıl yapılır: bir SharePoint web bölümü oluşturma](../sharepoint/how-to-create-a-sharepoint-web-part.md)|SharePoint sayfaları için web bölümleri oluşturma işlemi gösterilmektedir.|  
|[Nasıl yapılır: Tasarımcı kullanarak bir SharePoint web bölümü oluşturma](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md)|Bir görsel tasarım yüzeyini kullanarak SharePoint için web bölümleri oluşturma işlemi gösterilmektedir.|  
|[Nasıl yapılır: bir SharePoint uygulama sayfası veya web bölümü için bir kullanıcı denetimi oluşturma](../sharepoint/how-to-create-a-user-control-for-a-sharepoint-application-page-or-web-part.md)|Uygulama sayfaları ve SharePoint'te çalışan web bölümleri tarafından kullanılabilen özel, yeniden kullanılabilir denetimler oluşturma işlemi gösterilmektedir.|  
|[İzlenecek yol: SharePoint için bir web bölümü oluşturma](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint.md)|SharePoint için bir web bölümü tasarlamak açıklar.|  
|[İzlenecek yol: Tasarımcı kullanarak bir web bölümü SharePoint için oluşturma](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint-by-using-a-designer.md)|Denetimleri bir görsel tasarım yüzeyine sürükleyerek, SharePoint için bir web bölümü tasarlamak açıklar.|  
|[İzlenecek yol: SharePoint için OData görüntüleyen bir Silverlight web bölümü oluşturma](../sharepoint/walkthrough-creating-a-silverlight-web-part-that-displays-odata-for-sharepoint.md)|Bir Silverlight uygulamasını barındıran ve SharePoint listelerinden veri görüntüleyen bir SharePoint için bir web bölümü tasarlamak açıklar.|  
  
