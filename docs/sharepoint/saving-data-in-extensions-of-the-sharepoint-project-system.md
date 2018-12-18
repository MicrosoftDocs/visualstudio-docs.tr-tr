---
title: SharePoint Proje sisteminin uzantılarında veri kaydetme | Microsoft Docs
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
helpviewer_keywords:
- SharePoint project items, saving string data
- project items [SharePoint development in Visual Studio], saving string data
- projects [SharePoint development in Visual Studio], saving string data
- SharePoint projects, saving string data
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 74228b5259b733c91397eb1b40a2485daea8b79e
ms.sourcegitcommit: d9e4ea95d0ea70827de281754067309a517205a1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/29/2018
ms.locfileid: "37120455"
---
# <a name="save-data-in-extensions-of-the-sharepoint-project-system"></a>SharePoint Proje sisteminin uzantılarında veri kaydetme
  SharePoint Proje sisteminin genişlettiğinizde, bir SharePoint Proje kapatıldıktan sonra devam ederse dize verilerini kaydedebilirsiniz. Verileri genellikle proje veya belirli bir proje öğesi ile ilişkilidir.  
  
 Kalıcı gerekmez veri varsa, herhangi bir nesneye uygulayan SharePoint araçları nesne modelinde veri ekleyebilirsiniz <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject> arabirimi. Daha fazla bilgi için bkz: [SharePoint ile özel verileri ilişkilendirme uzantıları Araçları](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md).  
  
## <a name="save-data-that-is-associated-with-a-project-item"></a>Bir proje öğesi ile ilişkili verileri kaydetme
 Bir proje öğesi eklediğiniz bir özelliğin değerini gibi belirli bir SharePoint proje öğesi ile ilişkili verileri varsa verileri kaydedebilirsiniz *.spdata* dosyası için proje öğesi. Bunu yapmak için kullanın <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A> özelliği bir <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem> nesnesi. Bu özelliğe eklemek veri kaydedildi **ExtensionData** öğesinde *.spdata* dosyası için proje öğesi. Daha fazla bilgi için bkz: [ExtensionData öğesi](../sharepoint/extensiondata-element.md).  
  
 Aşağıdaki kod örneğinde nasıl kullanılacağı ortaya <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A> özel bir SharePoint Proje öğe türüne tanımlanan bir dize özelliği değeri kaydetmek için özellik. Daha büyük bir örneğin bağlamında bu örnek için bkz [nasıl yapılır: özel bir SharePoint Proje öğe türüne özellik ekleme](../sharepoint/how-to-add-a-property-to-a-custom-sharepoint-project-item-type.md).  
  
 [!code-vb[SPExtensibility.ProjectItemExtension.MenuAndProperty#14](../sharepoint/codesnippet/VisualBasic/projectitemmenuandproperty/extension/projectitemtypeproperty.vb#14)]
 [!code-csharp[SPExtensibility.ProjectItemExtension.MenuAndProperty#14](../sharepoint/codesnippet/CSharp/projectitemmenuandproperty/extension/projectitemtypeproperty.cs#14)]  
  
## <a name="save-data-that-is-associated-with-a-project"></a>Bir proje ile ilişkili verileri kaydetme
 SharePoint projelerine ekleme bir özellik değeri gibi proje düzeyi veri varsa, veri proje dosyasına kaydedebilirsiniz ( *.csproj* dosya veya *.vbproj* dosya) veya proje kullanıcı seçeneği dosya ( *. csproj.user* dosya veya *. vbproj.user* dosyası). Verileri kaydetmek üzere seçim yapın dosya kullanılacak verilerini nasıl istediğinizi bağlıdır:  
  
-   Veriler SharePoint Proje Aç tüm geliştiriciler için kullanılabilir olmasını istiyorsanız, veri proje dosyasına kaydedin. Bu dosyadaki veri Projeyi kullanıma diğer geliştiriciler için kullanılabilir olması için bu dosyayı her zaman kaynak denetimi veritabanları için teslim edilir.  
  
-   Visual Studio'da açın SharePoint Proje sahip geçerli Geliştirici kullanılabilir olması için veri istiyorsanız, veri proje kullanıcı seçeneği dosyasına kaydedin. Bu dosyadaki veri Projeyi kullanıma diğer geliştiriciler için kullanılabilir değildir. Bu dosya genellikle kaynak denetimi veritabanları için iade değil.  
  
### <a name="save-data-to-the-project-file"></a>Proje dosyasına veri kaydetme
 Proje dosyasına verileri kaydetmek için dönüştürme bir <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject> nesnesine bir <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage> nesnesini genişletin ve ardından <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.SetPropertyValue%2A> yöntemi. Aşağıdaki kod örneği, bir proje özelliğinin değeri proje dosyasına kaydetmek için bu yöntemi kullanmak gösterilmiştir. Bu örneği bağlamında daha büyük bir örnek görmek için bkz: [nasıl yapılır: SharePoint projelerine özellik ekleme](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md).  
  
 [!code-vb[SpExt_SPCustomPrjProperty#3](../sharepoint/codesnippet/VisualBasic/customspproperty/customproperty.vb#3)]
 [!code-csharp[SpExt_SPCustomPrjProperty#3](../sharepoint/codesnippet/CSharp/customspproperty/customproperty.cs#3)]  
  
 Dönüştürme hakkında daha fazla bilgi için <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject> nesneler Visual Studio Otomasyon nesne modeli veya tümleştirme nesne modeli, diğer türleri için bkz: [SharePoint Proje sistem türleri ve diğer Visual Studio Proje türleriarasındadönüştürme](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md).  
  
### <a name="save-data-to-the-project-user-option-file"></a>Veri proje kullanıcı seçeneği dosyaya kaydet
 Verileri proje kullanıcı seçeneği dosyasına kaydetmek için kullanın <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject.ProjectUserFileData%2A> özelliği bir <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject> nesnesi. Aşağıdaki kod örneği, bir proje özelliğinin değeri proje kullanıcı seçeneği dosyasına kaydetmek için bu özelliği kullanmak gösterilmiştir. Bu örneği bağlamında daha büyük bir örnek görmek için bkz: [nasıl yapılır: SharePoint projelerine özellik ekleme](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md).  
  
 [!code-vb[SpExt_SPCustomPrjProperty#2](../sharepoint/codesnippet/VisualBasic/customspproperty/customproperty.vb#2)]
 [!code-csharp[SpExt_SPCustomPrjProperty#2](../sharepoint/codesnippet/CSharp/customspproperty/customproperty.cs#2)]  
  
## <a name="see-also"></a>Ayrıca bkz.
 [SharePoint Proje sistemini genişletme](../sharepoint/extending-the-sharepoint-project-system.md)   
 [SharePoint araç uzantıları ile özel verileri ilişkilendirme](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md)   
 [SharePoint Proje sistem türleri ve diğer Visual Studio Proje türleri arasında dönüştürme](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md)  
  
