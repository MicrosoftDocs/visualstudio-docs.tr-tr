---
title: 'Nasıl yapılır: SharePoint projelerine özellik ekleme | Microsoft Docs'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- projects [SharePoint development in Visual Studio], extending
- SharePoint development in Visual Studio, extending projects
- SharePoint projects, extending
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: c956da1df5507d2efecb3ff72f034d54fb377eb5
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49898421"
---
# <a name="how-to-add-a-property-to-sharepoint-projects"></a>Nasıl yapılır: SharePoint projelerine özellik ekleme
  Bir özellik için herhangi bir SharePoint projesine eklemek için bir proje uzantısı'nı kullanabilirsiniz. Özellik görünür **özellikleri** proje seçildiğinde penceresi **Çözüm Gezgini**.  
  
 Aşağıdaki adımlar, bir proje uzantısı zaten oluşturduğunuzu varsayalım. Daha fazla bilgi için [nasıl yapılır: bir SharePoint proje uzantısı oluşturma](../sharepoint/how-to-create-a-sharepoint-project-extension.md).  
  
### <a name="to-add-a-property-to-a-sharepoint-project"></a>Bir SharePoint projesine bir özellik eklemek için  
  
1.  Eklediğiniz SharePoint projelerine özellik temsil eden genel özelliğine sahip bir sınıfı tanımlar. Birden çok özellik eklemek istiyorsanız, tüm özelliklerin aynı sınıftaki veya farklı sınıflardaki tanımlayabilirsiniz.  
  
2.  İçinde <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension.Initialize%2A> yöntemi, <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> uygulama, tanıtıcısını <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectPropertiesRequested> olayı *projectService* parametresi.  
  
3.  İçin olay işleyicisinde <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectPropertiesRequested> olay özellikleri sınıfı bir örneğini ekleme <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectPropertiesRequestedEventArgs.PropertySources%2A> olay bağımsız değişkenleri parametre koleksiyonu.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği, iki özellik SharePoint projelerine ekleme gösterilmiştir. Bir özellik devam ederse, proje kullanıcı seçeneği dosya verilerini ( *. csproj.user* dosya veya *. vbproj.user* dosyası). Proje dosyasındaki verilerini diğer özellik devam ederse (*.csproj* dosya veya *.vbproj* dosyası).  
  
 [!code-vb[SpExt_SPCustomPrjProperty#1](../sharepoint/codesnippet/VisualBasic/customspproperty/customproperty.vb#1)]
 [!code-csharp[SpExt_SPCustomPrjProperty#1](../sharepoint/codesnippet/CSharp/customspproperty/customproperty.cs#1)]  
  
### <a name="understand-the-code"></a>Kodu anlama  
 ' In aynı örneğine emin olmak için `CustomProjectProperties` sınıfı, her zaman kullanılır <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectPropertiesRequested> bir olay oluşursa, kod örneği için özellikleri nesnesi ekler <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> bu olay gerçekleştiğinde ilk proje özelliği. Bu olay tekrar oluştuğunda bu nesne kodu alır. Kullanma hakkında daha fazla bilgi için <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> veri projeleri ile ilişkilendirilecek özelliğine bakın [SharePoint ile özel verileri ilişkilendirme araçları uzantıları](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md).  
  
 Özellik değerleri, değişiklikleri kalıcı hale getirmek için **ayarlamak** erişimci özellikleri için aşağıdaki API'leri kullanın:  
  
- `CustomUserFileProperty` kullanan <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject.ProjectUserFileData%2A> özellik değerini proje kullanıcı seçeneği dosyasına kaydetmek için.  
  
- `CustomProjectFileProperty` kullanan <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.SetPropertyValue%2A> , değer proje dosyasına kaydetmek için yöntemi.  
  
  Bu dosyalardaki kalıcı veriler hakkında daha fazla bilgi için bkz. [SharePoint Proje sisteminin uzantılarında veri kaydetme](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md).  
  
### <a name="specify-the-behavior-of-custom-properties"></a>Özel özellikler davranışını belirtin  
 Özel bir özellik görünür ve davranır nasıl tanımlayabileceğiniz **özellikleri** öznitelikleri uygulayarak penceresi <xref:System.ComponentModel> özellik tanımı için ad alanı. Aşağıdaki öznitelikler pek çok senaryoda kullanışlıdır:  
  
-   <xref:System.ComponentModel.DisplayNameAttribute>: Özelliğin görünen adını belirtir **özellikleri** penceresi.  
  
-   <xref:System.ComponentModel.DescriptionAttribute>: Belirtir görünen açıklama dizesi tabanında **özellikleri** özelliği seçildiğinde penceresi.  
  
-   <xref:System.ComponentModel.DefaultValueAttribute>: Bir özelliğin varsayılan değerini belirtir.  
  
-   <xref:System.ComponentModel.TypeConverterAttribute>: Görüntülenen dizeyi arasında özel bir dönüştürme belirtir **özellikleri** penceresi ve dize olmayan özellik değeri.  
  
-   <xref:System.ComponentModel.EditorAttribute>: Bir özelliği değiştirmek için özel bir düzenleyici belirtir.  
  
## <a name="compile-the-code"></a>Kod derleme  
 Bu örnek aşağıdaki derlemelere başvurular gerektirir:  
  
-   Microsoft.VisualStudio.SharePoint
-    
-   Microsoft.VisualStudio.Shell
-     
-   Microsoft.VisualStudio.Shell.Interop
-     
-   Microsoft.VisualStudio.Shell.Interop.8.0
-     
-   System.ComponentModel.Composition  
  
## <a name="deploy-the-extension"></a>Uzantıyı dağıtmak  
 Uzantıyı dağıtmak için oluşturun bir [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] uzantısı (VSIX) paketini derleme ve uzantısıyla dağıtmak istediğiniz diğer tüm dosyalar için. Daha fazla bilgi için [Visual Studio'da SharePoint araçları için uzantıları dağıtma](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## <a name="see-also"></a>Ayrıca bkz.
 [SharePoint projeleri genişletme](../sharepoint/extending-sharepoint-projects.md)   
 [Nasıl yapılır: bir SharePoint proje uzantısı oluşturma](../sharepoint/how-to-create-a-sharepoint-project-extension.md)   
 [Nasıl yapılır: bir kısayol menü öğesini SharePoint projelerine ekleme](../sharepoint/how-to-add-a-shortcut-menu-item-to-sharepoint-projects.md)   
 [SharePoint Proje sistemini genişletme](../sharepoint/extending-the-sharepoint-project-system.md)  
  
  
