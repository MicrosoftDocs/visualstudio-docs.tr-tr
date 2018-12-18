---
title: Paketleme ve dağıtım bilgileri proje öğelerinde sağlama | Microsoft Docs
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.Project.SafeControlEntries
- VS.SharePointTools.Project.ProjectOutputReference
- VS.SharePointTools.Project.FeatureProperties
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, safe controls
- project output references [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, feature properties
- SharePoint development in Visual Studio, project output references
- SharePoint development in Visual Studio, advanced packaging tools
- feature properties [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, feature receiver
- feature receiver [SharePoint development in Visual Studio]
- safe controls [SharePoint development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: e4ce9f864307ffaee4bce51a565e9ad1726d043d
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49893305"
---
# <a name="provide-packaging-and-deployment-information-in-project-items"></a>Proje öğelerinde paketleme ve dağıtım bilgileri sağlayın
  Tüm SharePoint Proje öğeleri [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] için SharePoint projesi dağıtıldığında ek veri sağlamak için kullanabileceğiniz özelliklere sahiptir. Bu özellikler aşağıdaki gibidir:  
  
- Özellik özellikleri  
  
- Özellik alıcıları  
  
- Proje çıktısı başvuruları  
  
- Güvenli denetim girdileri  
  
  Bu özellikler görünür **özellikleri** penceresi.  
  
## <a name="feature-properties"></a>Özellik özellikleri
 Kullanım **özellik özellikleri** özelliğini kullanan verilerini belirtmek için özellik. Özellik özellikleri veri SharePoint'te dağıtıldığında bir özellikle birlikte eklenen değer, (anahtar/değer çifti olarak saklanır) değerler kümesidir. Özellik dağıtıldıktan sonra kodunuzdaki özellik değerlerine erişebilirsiniz.  
  
 Proje öğesinin özelliğini özellik değer eklediğinizde, değeri öğenin özellik bildirimindeki bir öğe olarak eklenir. Bir iş verileri bağlantısı (BDC) modeli projesi ModelFileName özellik olarak gibi görünür:  
  
```xml  
<Property Key="ModelFileName" Value="BdcModel1\BdcModel1.bdcm" />   
```  
  
 Bir özellik değeri ayarladıktan sonra bir projenin FeatureProperty öğesi olarak eklenir *.spdata* dosya. SharePoint özelliklerine erişme hakkında daha fazla bilgi için bkz: [SPFeaturePropertyCollection sınıfı](http://go.microsoft.com/fwlink/?LinkId=177391).  
  
 Tüm proje öğeleri aynı özellik özellik değerleri özellik bildiriminde birlikte birleştirilir. Ancak, iki farklı proje öğeleri eşleşmeyen değerlerle aynı özellik özellik anahtarı belirtirseniz, bir doğrulama hatası oluşur.  
  
 Özellik özellikleri doğrudan özellik dosyasına eklemek için (*.feature*), çağrı [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] SharePoint nesne modeli yöntemi <xref:Microsoft.VisualStudio.SharePoint.Features.IPropertyCollection.Add%2A>. Bu yöntemi kullanırsanız, aynı özellik özellik değerlerini özellik özelliklerinde ekleme hakkında daha fazla aynı kuralın de doğrudan özellik dosyasına eklenen özelliklerin uygulandığını unutmayın.  
  
## <a name="feature-receiver"></a>Özellik alıcısı
 Özellik alıcıları özelliği içeren bir proje öğesine belirli olaylar meydana geldiğinde yürütülen kodu var. Örneğin, özellik yüklü, etkinleştirilmiş veya yükseltilmiş yürütülen özellik alıcıları tanımlayabilirsiniz. Özellik alıcısı açıklandığı bir özelliği eklemek için eklemek için tek yönlü [izlenecek yol: özellik Olay alıcıları ekleme](../sharepoint/walkthrough-add-feature-event-receivers.md). Özellik alıcısının sınıf adı ve derlemeye başvurmak için başka bir yoludur **özellik alıcısı** özelliği.  
  
### <a name="direct-method"></a>Doğrudan yöntem
 Bir özellik ile doğrudan bir özellik alıcısı eklediğinizde bir kod dosyası altına yerleştirilir **özellik** Çözüm Gezgininde. SharePoint çözümünüzü oluşturduğunuzda, kod bir derleme içine derler ve SharePoint'e dağıtır. Varsayılan olarak, özellik özellikleri **alıcısı bütünleştirilmiş kodu** ve **alıcı sınıfı** derleme ve sınıf adını başvuru.  
  
### <a name="reference-method"></a>Reference yöntemi
 Özellik alıcısı eklemek için başka bir yolu kullanmaktır **özellik alıcısı** özellik alıcısı bütünleştirilmiş kodu başvurmak için bir proje öğesinin özellik. İki alt özellik alıcısı özellik değerine sahiptir: **derleme** ve **sınıf adı**. Derleme, tam olarak nitelenmiş kullanmalıdır, "tanımlayıcı" ada ve sınıf adı tam tür adı olmalıdır. Daha fazla bilgi için [Strong-Named derlemeleri](http://go.microsoft.com/fwlink/?LinkID=169573). SharePoint çözümü dağıtıldıktan sonra özellik başvurulan özellik alıcısı özellik olaylarını işlemek için kullanır.  
  
 Çözümü derleme zamanı, özellik alıcısı özellik değerlerini özelliği ve projeleri SharePoint çözümünün özellik bildiriminde özellik öğesi ReceiverAssembly ve ReceiverClass özniteliklerini ayarlanacak birleştirmek (*.wsp* ) dosyası. Derleme ve sınıf adını özellik değerlerini bir proje öğesi bir özelliği ve her ikisi de belirtilirse, bu nedenle, proje öğesi ve özellik özelliği değerlerin eşleşmesi gerekir. Değerler eşleşmiyorsa, bir doğrulama hatası alırsınız. Bir proje öğesi istiyorsanız dışındaki bir özellik alıcısı bütünleştirilmiş kodu başvurmak için kendi özellik kullanır, başka bir özelliğe taşıyın.  
  
 Sunucuda olmayan bir özellik alıcısı bütünleştirilmiş kodu başvuruda bulunursanız, derleme dosyası pakette de içermelidir; [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] eklemez, sizin için. Özellik dağıttığınızda, derleme dosyası ya da sistemin için kopyalanan [!INCLUDE[TLA#tla_gac](../sharepoint/includes/tlasharptla-gac-md.md)] veya SharePoint fiziksel dizini depo klasörü. Daha fazla bilgi için bkz: nasıl yapılır: [nasıl yapılır: ek derlemeler ekleyip](../sharepoint/how-to-add-and-remove-additional-assemblies.md).  
  
 Özellik alıcıları hakkında daha fazla bilgi için bkz: [özellik olayı alıcısını](http://go.microsoft.com/fwlink/?LinkID=169574) ve [özellik olayları](http://go.microsoft.com/fwlink/?LinkID=169575).  
  
## <a name="project-output-references"></a>Proje çıktısı başvuruları
 Proje çıktı başvuruları özelliği gibi proje öğenizin çalıştırması gereken bir derleme, bir bağımlılık belirtir. Örneğin, çözümünüze bir BDC projesi ve bir sınıf projesi olduğunu varsayalım. BDC projesi tarafından sınıfı proje çıkış bütünleştirilmiş kod üzerinde bir bağımlılık varsa, İVB projenin proje çıktı başvuruları özelliğini derlemeye başvurabilir. BDC projesi paketlendiğinde bağımlı derleme paketine dahildir.  
  
 Proje çıktı başvuruları genellikle derlemeleri, ancak bazı durumlarda (örneğin, Silverlight projeleri) diğer dosya türleri olabilir.  
  
 Daha fazla bilgi için [nasıl yapılır: proje çıktı başvurusu ekleme](../sharepoint/how-to-add-a-project-output-reference.md).  
  
## <a name="safe-control-entries"></a>Güvenli denetim girdileri
 SharePoint için belirli denetimler güvenilmeyen kullanıcıların erişimini sınırlamak için güvenli denetim girişleri olarak adlandırılan bir güvenlik mekanizması sağlar. Tasarım gereği, SharePoint, SharePoint sunucusunda ASPX sayfaları oluşturma ve karşıya yükleme güvenilmeyen kullanıcıların sağlar. Bu kullanıcılar ASPX sayfaları için güvenli olmayan kod eklemesini engellemek için SharePoint, erişimi sınırlar *güvenli denetimler*. Güvenli denetimler ASPX denetimleri ve Web Bölümleri güvenli olarak belirlenmiş ve sitenizde herhangi bir kullanıcı tarafından kullanılabilir. Daha fazla bilgi için [4. adım: Web Bölümünüzün güvenli denetimler listeye eklemek](http://go.microsoft.com/fwlink/?LinkID=171014).  
  
 Her bir SharePoint Proje öğe [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] adlı bir özelliğe sahiptir **güvenli denetim girdileri** iki Boolean alt olan: **güvenli** ve **karşı güvenli betik**. Güvenli özellik güvenilmeyen kullanıcıların bir denetim erişip erişemeyeceğini belirtir. Güvenilmeyen kullanıcıların görüntüleyebilir ve bir denetimin özelliklerini değiştirmek isteyip karşı güvenli betik alan özelliği belirtir.  
  
 Güvenli denetim girdileri, bir derleme olarak başvurulur. Proje öğesinin girerek projenin derleme için güvenli denetim girdileri eklemek **güvenli denetim girdileri** özelliği. Ancak, aynı zamanda güvenli denetim girdileri bir projenin derleme ekleyebileceğiniz **Gelişmiş** sekmesinde **paket Tasarımcısı** eklediğinizde bir ek bütünleştirilmiş kod paketi. Daha fazla bilgi için [nasıl yapılır: denetimleri güvenli denetim olarak işaretleme](../sharepoint/how-to-mark-controls-as-safe-controls.md) veya [güvenli denetim olarak bir Web Bölümü derlemeyi Kaydettirdikten](http://go.microsoft.com/fwlink/?LinkID=171013).  
  
### <a name="xml-entries-for-safe-controls"></a>Güvenli denetimler için XML girdileri
 Bir proje öğesi veya proje derlemesi için bir güvenli denetim girişi eklediğinizde, paket bildirimi aşağıdaki biçimde bir başvuru yazılır:  
  
```xml  
<Assemblies>  
    <Assembly Location="<assembly name>.dll"     
      DeploymentTarget="<'GlobalAssemblyCache' or 'WebApplication'">>  
        <SafeControls>  
            <SafeControl Assembly="<assembly name>.dll" Namespace=  
              "<SharePoint project name>" Safe="<true/false>"     
                TypeName="<control name>"   
                SafeAgainstScript="<true/false>" />  
        </SafeControls>  
    </Assembly>  
</Assemblies>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.
 [Paket ve SharePoint çözümlerini dağıtma](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)   
 [Çözüme dosyaları dahil etmek için modül kullanma](../sharepoint/using-modules-to-include-files-in-the-solution.md)   
 [SharePoint paketleme ve dağıtımını genişletme](../sharepoint/extending-sharepoint-packaging-and-deployment.md)  
