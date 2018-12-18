---
title: Korumalı çözümle ilgili konular | Microsoft Docs
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.Project.SandboxedSolutions
- VS.SharePointTools.Security.SandboxedSolutions
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, sandboxed solutions
- sandboxed solutions [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, farm solutions
- farm solutions [SharePoint development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 2f9a5d0c439d619864cc6e9559608e3c3891fc7e
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49890042"
---
# <a name="sandboxed-solution-considerations"></a>Korumalı çözümle ilgili konular
  *Korumalı çözümler* kendi özel kod çözümlerini karşıya yüklemek site koleksiyonu kullanıcıları sağlayan Microsoft SharePoint 2010'daki bir özelliktir. Genel korumalı bir çözüm, kendi Web Bölümleri yükleme kullanıcı sayısıdır.  
  
 Korumalı bir SharePoint uygulama Web grubunda sınırlı bir kısmını erişimi olan bir güvenli ve izlenen bir işlemde çalıştırır. Microsoft SharePoint 2010, korumalı alana alınan çözümler etkinleştirmek için özellikler, çözüm galerileri, izleme çözümü ve doğrulama çerçevesinin bir birleşimini kullanır.  
  
## <a name="specify-project-trust-level"></a>Proje güven düzeyi belirtin
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] bir Boolean projesi özelliği aracılığıyla korumalı alana alınan çözümler adlı destekler *Korumalı çözüm*. Bu özelliği, projedeki herhangi bir zamanda ayarlanabilir veya projeyi oluşturduğunuzda belirtilebilir **SharePoint Özelleştirme Sihirbazı**.  
  
> [!NOTE]  
>  Değiştirme *Korumalı çözüm* oluşturulduktan sonra bir projenin özellik doğrulama hatalarına neden olabilir.  
  
 Çözüm Grup kapsamlı bir çözüm kabul edildiği *Korumalı çözüm* özelliği **false** veya seçtiğiniz **Grup çözümü olarak Dağıt** seçeneği. Ancak, çözümü farklı bir grup çözümünden anlamına gelir *Korumalı çözüm* özelliği **true** veya seçtiğiniz **bir korumalı çözüm olarak Dağıt** Sihirbazı'nda seçeneği.  
  
## <a name="sharepoint-site-hierarchy"></a>SharePoint site hiyerarşisi
 Nasıl korumalı alana alınan çözümler anlamak için iş, yardımcı olan SharePoint siteleri kapsamda hiyerarşik olduğunu öğrenmek için. Üst öğe Web grubu adı verilir ve diğer öğeleri kendisine bağımlı olan:  
  
 Web grubu  
  
 Bir Web uygulaması  
  
 Site koleksiyonu A1  
  
 Site A1a  
  
 Web uygulaması B  
  
 Site koleksiyonu B1  
  
 Site B1a  
  
 Site B1b  
  
 Site koleksiyonu B2  
  
 Site B2a  
  
 Gördüğünüz gibi Web grupları sırayla alt sahip ve benzeri bir veya daha fazla site koleksiyonları içerebilir, bir veya daha fazla Web uygulamaları içerebilir. Yalnızca bu koleksiyon sitede bir site koleksiyonu etkileyen için yapılan ve başka hiçbir değiştirir. Ancak, Web grubu düzeyinde yapılan değişiklikler, gruptaki tüm site koleksiyonlarında etkiler.  
  
 Windows SharePoint Services (WSS) 3.0, yalnızca grup düzeyine çözümlerini dağıtmanıza olanak sağlar ancak [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] grup düzeyinde (Grup çözümü) veya site koleksiyonu düzeyinde (Korumalı çözüm) için dağıtmanıza olanak tanır.  
  
## <a name="why-sandboxed-solutions"></a>Neden korumalı alana alınan çözümler?
 WSS 3.0 sürümünde, yalnızca grup düzeyi çözümleri dağıtılabilir. Bu, olası zararlı veya kararsız hale getiren çözümleri, etkilenen tüm Web grubunda ve tüm diğer site koleksiyonları ve bunun altında çalışan uygulamalar dağıtılmasını geliyordu. Ancak, korumalı alana alınan çözümler kullanarak, çözümlerinizi bir alt grup, belirli bir site koleksiyonu, bu alan için dağıtabilirsiniz. Ek koruma sağlamak için çözümün derleme ana yüklenmediğinden [!INCLUDE[TLA2#tla_iis5](../sharepoint/includes/tla2sharptla-iis5-md.md)] işlem (*w3wp.exe*). Bunun yerine, ayrı bir işleme yüklenmesini (*SPUCWorkerProcess.exe*). Bu işlem, izlenen ve kotalar ve CPU döngülerini kullanma sıkı döngüler çalıştırma gibi zararlı etkinlikleri gerçekleştirmesine korumalı çözümlerinden grubunu korumak için azaltma uygular.  
  
## <a name="site-collection-solution-gallery"></a>Site koleksiyonu çözüm Galerisi
 [!INCLUDE[sharepointShort](../sharepoint/includes/sharepointshort-md.md)] 2010 "site koleksiyonu çözüm Galerisi." bilinen bir özellik vardır. SharePoint 2010 merkezi yönetim sayfasından veya açarak bu özelliğe erişmek **Site eylemleri** menüsünde seçerek **Site Ayarları**ve ardından **çözümleri** altında bağlantı **galeriler** SharePoint sitesi. Çözüm galeriler site koleksiyonu yöneticileri, kendi site koleksiyonlarında bulunan çözümlerimi sağlayan çözümler depolarının ' dir.  
  
 Çözüm Galerisi, Web SharePoint sitesinin kök dizininde depolanmış bir belge kitaplıktır. Çözüm Galerisi site şablonu değiştirir ve çözüm paketleri destekler. Bir SharePoint çözüm paketini olduğunda (*.wsp*) dosyası, bir korumalı çözüm işlenir.  
  
## <a name="sandboxed-solution-limitations"></a>Korumalı çözüm sınırlamaları
 Bir korumalı çözüm dağıtılırken, SharePoint işlevselliği için kullanılabilir bir dizi yakınlarında herhangi bir güvenlik açığını azaltmak için sınırlıdır. Bu sınırlamaların bazıları şunlardır:  
  
- Korumalı çözümler dağıtılabilir çözüm öğeleri kullanabilecekleri sınırlı bir alt kümesine sahip. Site tanımları ve iş akışları gibi savunmasız SharePoint proje şablonları kullanılabilir değil.  
  
- SharePoint Korumalı çözüm kod bir işlemde çalıştırır (*SPUCWorkerProcess.exe*) ana ayrı [!INCLUDE[TLA2#tla_iis5](../sharepoint/includes/tla2sharptla-iis5-md.md)] uygulama havuzu (*w3wp.exe*) işlem.  
  
- Eşlenen klasörler projeye eklenemez.  
  
- Türlerini [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] derleme Microsoft.Office.Server korumalı çözümlerde kullanılamaz. Ayrıca, yalnızca türlerini [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] derleme Microsoft.SharePoint korumalı çözümlerde kullanılabilir.  
  
  Korumalı bir çözüm, SharePoint sunucusunda herhangi bir etkisi yoktur, bir SharePoint çözümünü belirten gibi dikkat edin önemlidir; yalnızca SharePoint Proje SharePoint'ten nasıl dağıtıldığını belirler [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] ve hangi derlemelerin, bağlanır. Oluşturulan etkilemez *.wsp* dosyasını ve *.wsp* dosyasının olduğundan doğrudan için karşılık gelen veri *Korumalı çözüm* özelliği.  
  
## <a name="capabilities-and-elements-in-sandboxed-solutions"></a>Özellikler ve öğeler korumalı alana alınan çözümler
 Korumalı çözümler, aşağıdaki özellikleri ve öğeleri destekler:  
  
- İçerik türleri/alanları  
  
- Özel Eylemler  
  
- Bildirim temelli iş akışları  
  
- Olay alıcıları  
  
- Özelliğini belirtme  
  
- Liste tanımları  
  
- Liste Örnekleri  
  
- Modül/dosyalar  
  
- Gezinti  
  
- *Onet.XML*  
  
- SPItemEventReceiver  
  
- SPListEventReceiver  
  
- SPWebEventReceiver  
  
- Öğesinden türetilen tüm Web bölümleri için destek `System.Web.UI.WebControls.WebParts.WebPart`  
  
- Web Bölümleri  
  
- LCID'sine özellik öğeleri (yerine *Webtemp.xml*)  
  
- Görsel Web Bölümleri  
  
  Korumalı çözümler, aşağıdaki özellikleri ve öğeleri desteklemez:  
  
- Uygulama sayfaları  
  
- Özel eylem grubu  
  
- Grup kapsamı özellikleri  
  
- `HideCustomAction` öğesi  
  
- Web uygulama kapsamlı özellikleri  
  
- Kod ile iş akışları  
  
## <a name="see-also"></a>Ayrıca bkz.
 [Korumalı arasındaki farklar ve Grup çözümleri](../sharepoint/differences-between-sandboxed-and-farm-solutions.md)   
 [SharePoint Çözümleri Geliştirme](../sharepoint/developing-sharepoint-solutions.md)  
  