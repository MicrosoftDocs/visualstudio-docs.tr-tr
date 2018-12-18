---
title: SharePoint Çözümlerini Yerelleştirme | Microsoft Docs
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.Project.GlobalAndFeatureResource
- VS.SharePoint.Project.AddResourceDialog
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- globalizing [SharePoint development in Visual Studio]
- localizing [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, localizing
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: ba02d8811fc6633a55e06ae63c9399c70f59634f
ms.sourcegitcommit: d9e4ea95d0ea70827de281754067309a517205a1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/29/2018
ms.locfileid: "37120585"
---
# <a name="localize-sharepoint-solutions"></a>SharePoint Çözümlerini Yerelleştirme

  Böylece tüm dünyada kullanılabilir uygulamalarınız Hazırlama işlemi yerelleştirme bilinir. Yerelleştirme, belirli bir kültür kaynaklara çevirme. Daha fazla bilgi için bkz: [Globalizing ve yerelleştirme uygulamaları](/visualstudio/ide/globalizing-and-localizing-applications). Bu konu, bir SharePoint çözüm yerelleştirme hakkında genel bir bakış sağlar.  
  
 Bir çözüm yerelleştirme için sabit kodlanmış dizeleri koddan kaldırın ve kaynak dosyalarıyla soyut. Bir kaynak dosya bir [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)]-ile dosya tabanlı bir *.resx* uzantısı. Kaynak dosyanın çözümünüz içinde kullanılan dizeleri çevrilen sürümlerini içerir. Daha fazla bilgi için bkz: [uygulamalarında kaynakları](http://go.microsoft.com/fwlink/?LinkID=155844).  
  
> [!NOTE]  
>  Yalnızca dize kaynaklarını SharePoint çözüm kaynak dosyalarını ekleyin. Dize olmayan kaynakları eklemek kaynak düzenleyicisini sağlar, ancak dize olmayan kaynakları SharePoint'e dağıtmayın.  
  
## <a name="resource-files"></a>Kaynak dosyaları
 Kaynak dosyaları üç tür vardır: varsayılan ve dilden dile özgü.  
  
|Kaynak dosya türü|Açıklama|  
|------------------------|-----------------|  
|Varsayılan|Olarak da bilinen bir geri dönüş kaynak İngilizce gibi varsayılan kültür için yerelleştirilmiş dizeleri varsayılan kaynak dosyaları içerir. Belirtilen dil için yerelleştirilmiş kaynak dosyası bulunamazsa, bunlar kullanılır. Varsayılan kaynaklar ayrı dosyalar sahip değilse, ana uygulama bütünleştirilmiş kodunda depolanır.|  
|Dilden|Bir dil, ancak belirli bir kültür için yerelleştirilmiş dizeleri içeren bir kaynak dosyası. Örneğin, Fransızca için "fr".|  
|Dile özgü|Bir dil ve kültür için yerelleştirilmiş dizeleri içeren bir kaynak dosyası. Örneğin, "fr-CA" Fransızca Kanada için.|  
  
 Daha fazla bilgi için bkz: [yerelleştirme, hiyerarşik kuruluş kaynakları](http://go.microsoft.com/fwlink/?LinkId=178360).  
  
 İçinde geliştirmek SharePoint projelerine varsayılan kaynak dosyaları belirtmek için [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], seçin **sabit dil (sabit ülke)** kültür listesinde **kaynak ekleme** iletişim kutusunda, bir kaynak dosyası ekleyin.  
  
## <a name="localize-visual-studio-sharepoint-solutions"></a>Visual Studio SharePoint Çözümlerini Yerelleştirme
 Bir çözüm yerelleştirme sırasında tüm kullanıcılara çözümünüzü görüntüler metinsel bilgileri düşünmelisiniz. Bilgilendirici iletileri, hata iletileri ve [!INCLUDE[TLA2#tla_ui](../sharepoint/includes/tla2sharptla-ui-md.md)] dizeleri çevrilen ve bu çevirileri kaynak dosyalarında yerleştirilir.  
  
 Her dizeye kaynak dosyasında benzersiz bir tanımlayıcı sahiptir. Her kaynak dosyasında çevrilmiş dizesi için aynı tanımlayıcısı kullanın. Örneğin, "Dize1" varsayılan kaynak dosyasında ilk dizesi için tanımlayıcı ise, aynı tanımlayıcısı dile özgü kaynak dosyalarında ilk dize için kullanın.  
  
 Genellikle yerelleştirme üç alan vardır [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] SharePoint uygulamaları: özellikler, ASPX sayfası biçimlendirme ve kod. Gösterim amacıyla aşağıdaki bölümlerde, Almanca ve Japonca yerelleştirme istediğiniz bir SharePoint çözüm sahip olduğunuzu varsayar. İngilizce varsayılan dildir.  
  
### <a name="localize-features"></a>Özellikler yerelleştirme
 Bir özelliği yerelleştirme için çevrilmiş başlık ve dize yerelleştirilmiş kaynaklar dosyasında başvuran bir ifade sabit kodlanmış başlığı ve açıklamayı özelliğinin yerine gerekir. Bu değişikliği yaptıktan **özelliği Designer** içinde [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Daha fazla bilgi için bkz: [nasıl yapılır: bir özelliği yerelleştirme](../sharepoint/how-to-localize-a-feature.md).  
  
 Almanca ve Japonca halinde, İngilizce özelliği yerelleştirme için üç kaynak dosyası proje öğeleri projenize eklemeniz: İngilizce, Almanca için diğeri Japonca için. Özellik kaynak dosyalarını ASPX işaretleme veya kod yerelleştirme için kullanılamaz; ayrı kaynak dosyaları için gereklidir.  
  
 Kaynak dosyaları özellik oluşturduktan sonra çevrilen dizeleri bunlara ekleyin. Yerelleştirilmiş dizeleri aşağıdaki biçimde bir ifade ile erişim:  
  
```aspx-csharp  
$Resources:String ID  
```  
  
 Özellik kaynaklarında [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] her zaman kaynaklar olarak da adlandırılır. Sabit dil, ardından bir kültür dışında bir dil seçerseniz [!INCLUDE[TLA2#tla_id](../sharepoint/includes/tla2sharptla-id-md.md)] kaynak dosya adına eklenir. Örneğin, bir sabit dil (varsayılan) özelliğini kaynak dosyası eklerseniz, çağrılır *Resources.resx*. Dile özgü özellik kaynak Japonca (Japonya) kültürünü seçerek eklerseniz, dosya adında *Resources.ja JP.resx*. Özellik kaynak dosya adlarını otomatik olarak atanır ve değiştirilemez.  
  
 İçin eklenen özellik için özellik kaynakları kapsamını yereldir. Çözüm herhangi bir özellik veya öğesi dosyada tarafından kullanılan kaynakları oluşturmak için Ekle bir **Genel kaynaklar dosyası** özellik kaynak dosya yerine proje öğesi. **Genel kaynaklar dosyası** proje öğesi bulunduğu **2010** klasörü altında **SharePoint** içinde **Yeni Öğe Ekle** iletişim kutusu. Genel kaynaklar dosyaları SharePoint kök klasörü \Resources klasörüne dağıtabilirsiniz.  
  
### <a name="localize-aspx-page-markup"></a>ASPX Sayfası biçimlendirmesini yerelleştirme
 Yerelleştirme için [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] sayfaları, üç kaynak dosyası proje öğeleri projenize ekleyin: İngilizce, Almanca için diğeri Japonca için. İşaretleme ek kod yerelleştirme yoksa, bunun yerine genel kaynaklar dosyaları ekleyebilirsiniz.  
  
 Varsayılan dil kaynak dosyasına için bir ad sağlayın. Yerelleştirilmiş kaynak dosyaları ile dile özgü kültür eklenmiş aynı adı vermek [!INCLUDE[TLA2#tla_id](../sharepoint/includes/tla2sharptla-id-md.md)]. Örneğin, *MyAppResources.de DE.resx* Almanca için ve *MyAppResources.ja JP.resx* Japonca için.  
  
 Ayarlama **dağıtım türü** için her kaynak dosyasının özelliği **AppGlobalResource**. Bu, tüm ASPX sayfaları ve denetimleri çözümde kullanılabilir olduğu App_GlobalResources klasöre dağıtmak kaynak dosyaları neden olur. İçinde C:\inetpub\wwwroot\wss\VirtualDirectories App_GlobalResources klasöründe\\< bağlantı noktası numarası\>\App_GlobalResources.  
  
> [!NOTE]  
>  Genel olmayan kaynak dosyaları kullanırsanız, bunları dağıtım türü özelliği ve diğer SharePoint özgü özelliklerini etkinleştirmek için proje öğesi klasörüne taşıyın.  
  
 ASPX biçimlendirmesini kaynak dosyaları, kod yerelleştirme için de kullanılabilir. Kod yanı sıra ASPX biçimlendirmesini yerelleştirme için kaynakların kullanıyorsanız, uydu derlemeye derlemek için yapı eylemi özellik ayarı her dosyanın katıştırılmış kaynağın neden için kaynak olarak bırakın. Ancak, yalnızca biçimlendirmesini yerelleştirme için kaynak dosyaları kullanıyorsanız, yapı eylemi ana uygulama derlemeye derlenmiş dosya önlemek için içerik için isteğe bağlı olarak değiştirebilirsiniz.  
  
 Tüm sabit kodlanmış özellik dizelerini ASPX sayfalar ve denetimler biçimlendirme, aşağıdaki biçimde bir ifade ile değiştirin:  
  
```aspx-csharp  
<asp:<class> runat="server" Text="<%$Resources:<Resource File Name>, <String ID>%>" />  
```  
  
 Örneğin:  
  
```aspx-csharp  
<asp:Button ID="btn1" runat="server" onclick="btn1_Click" Text="<%$Resources:Resource1,String7%>"></asp:Button>  
```  
  
 Metin olarak ASPX için bir ifade aşağıdaki biçimi kullanın:  
  
```aspx-csharp  
<asp:literal ID="<ID>" runat="server" Text="<%$Resources:<Resource File Name>, <String ID>%>" />  
```  
  
 Örneğin:  
  
```aspx-csharp  
<asp:literal ID="Literal1" runat="server" Text="<%$Resources:Resource1, String9%>" />  
```  
  
 Daha fazla bilgi için bkz: [nasıl yapılır: yerelleştirmeye ASPX biçimlendirmesini](../sharepoint/how-to-localize-aspx-markup.md).  
  
### <a name="localize-code"></a>Kod yerelleştirme
 Özellik dizeleri yerelleştirme yanı sıra ve [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] biçimlendirme da sahip ileti dizeleri ve çözüm kodunuzda görünen hata dizeleri yerelleştirme. Bilgilendirme yerelleştirilmiş ve hata iletileri uydu derlemeleri bulunur. Uydu derlemeleri içermesi gibi kullanıcılar tarafından görülebilir dizeleri [!INCLUDE[TLA2#tla_ui](../sharepoint/includes/tla2sharptla-ui-md.md)] metin ve çıktı iletileri özel durumlar ister.  
  
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Standart .NET Framework hub ve bağlı bileşen modeli kullanır. Hub veya ana program derleme, varsayılan dil kaynakları içerir. Dile özgü kaynaklar bağlı bileşen ya da uydu derlemelerini içerir. Daha fazla bilgi için bkz: [paketleme ve dağıtma kaynakları](http://go.microsoft.com/fwlink/?LinkId=179280). Uydu derlemeleri kaynaktan derlenmiş (*.resx*) dosyaları. Dile özgü kaynak dosyaları, proje ve çözüm paketi eklediğinizde [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] adlı uydu derlemelerini kaynak dosyalarını derler *{proje adı}.resources.dll*.  
  
 Projeniz için ayrı kaynak dosyası proje öğeleri ekleyerek ASPX biçimlendirmesini ile SharePoint uygulama kod yerelleştirme gibi; bir varsayılan dil ve her bir dil yerelleştirilmiş. Ancak, ASPX biçimlendirmesini yerelleştirme için kaynak dosyaları zaten varsa, daha önce belirtildiği gibi bunları kod yerelleştirme için yeniden kullanabilirsiniz. Kaynak dosyaları oluşturmanız gerekiyorsa, varsayılan dil kaynak dosyasına eklenen tercih ettiğiniz bir ad verin bir *.resx* uzantısı. Yerelleştirilmiş kaynak dosyaları, dile özgü kültür ile eklenen aynı adı [!INCLUDE[TLA2#tla_id](../sharepoint/includes/tla2sharptla-id-md.md)]. Her kaynak dosyasının yapı eylemi özelliği uydu kaynak derlemelerini oluşturulmasını sağlamak üzere katıştırılmış kaynak olarak ayarlayın.  
  
 Uydu derlemeleri oluşturma için projeyi oluşturun ve ek derlemeleri olarak dosyaları ekleyin **Gelişmiş** sekmesinde **paket tasarımcısını**. Derlemeleri eklerken bir kültür başına [!INCLUDE[TLA2#tla_id](../sharepoint/includes/tla2sharptla-id-md.md)] konumu yolu, klasör gibi *de-DE\\{proje öğesi adı}.resources.dll*. Bu, aynı ada sahip dosyaları içeren paket sağlar.  
  
 Kodunuzda çağrıları sabit kodlanmış dizeler yerine <xref:System.Web.HttpContext.GetGlobalResourceObject%2A> yöntemi aşağıdaki sözdizimini kullanarak:  
  
```aspx-csharp  
HttpContext.GetGlobalResourceObject("<Resource File Name>", "<String ID>")  
```  
  
 Daha fazla bilgi için bkz: [nasıl yapılır: kod yerelleştirme](../sharepoint/how-to-localize-code.md).  
  
#### <a name="web-part-code-localization"></a>Web Bölümü kod yerelleştirme
 Web Bölümleri özelliklerin, kategori ve WebDescription gibi sabit kodlanmış dizeleri kullanmak kod öznitelikleri içeren bir özel özellik Düzenleyici özelliği içerir. Bu öznitelikler dize değerlerini değiştirmek için özniteliğin sınıfından türetilen ayrı bir sınıf oluşturun. Bu sınıfların, özniteliğin özelliğini ayarlayın. Öznitelik özelliği temel sınıfını bağlıdır. Örneğin, DisplayNameValue özelliklerin özniteliği özelliktir ve DescriptionValue WebDescription özniteliği özelliğidir.  
  
 Türetilen sınıfta kaynak dosyasını ve dize kimliği için yerelleştirilmiş değeri ResourceManager nesnesi dize kimliği başvurusu Bu değer için özellik Düzenleyicisi özniteliği döndürür.  
  
## <a name="see-also"></a>Ayrıca bkz.
 [Nasıl yapılır: bir özelliği yerelleştirme](../sharepoint/how-to-localize-a-feature.md)   
 [Nasıl yapılır: ASPX biçimlendirmesini yerelleştirme](../sharepoint/how-to-localize-aspx-markup.md)   
 [Nasıl yapılır: kod yerelleştirme](../sharepoint/how-to-localize-code.md)   
 [Nasıl yapılır: kaynak dosyası ekleme](../sharepoint/how-to-add-a-resource-file.md)   
 [Nasıl yapılır: yerelleştirilmiş adlar, özellikler ve izinleri belirtmek için kaynak dosyası kullanın](../sharepoint/how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions.md)  
  
