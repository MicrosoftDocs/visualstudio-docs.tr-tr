---
title: Bağlam parametreleri | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- wizards, context parameters
- context parameters
ms.assetid: 1a062dcb-8a8f-40dd-bea9-3d10f9448966
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f9d9c1d6c78bb026fe0e26c99bbf712d4412ebd5
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51773216"
---
# <a name="context-parameters"></a>Bağlam Parametreleri
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

İçinde [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] tümleşik geliştirme ortamı (IDE), sihirbazlar ekleyebilirsiniz **yeni proje**, **Yeni Öğe Ekle**, veya **alt proje Ekle** iletişim kutuları. Eklenen sihirbazlar mevcuttur **dosya** menüsü veya bir projeye sağ tıklayarak **Çözüm Gezgini**. IDE bağlam parametreleri Sihirbazı uygulamaya geçirir. IDE Sihirbazı çağırdığında proje durumunu bağlam parametreleri tanımlayın.  
  
 Ayarlayarak sihirbazları IDE başlatıldığında <xref:Microsoft.VisualStudio.Shell.Interop.VSADDITEMOPERATION> IDE'nin çağrıda bayrağı <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.AddItem%2A> proje için yöntemi. Ayarlandığında, proje neden `IVsExtensibility::RunWizardFile` kayıtlı sihirbaz adı veya GUID ve IDE arabimini diğer bağlam parametreleri kullanarak yürütülecek yöntemi.  
  
## <a name="context-parameters-for-new-project"></a>Yeni proje için bağlam parametreleri  
  
|Parametre|Açıklama|  
|---------------|-----------------|  
|`WizardType`|Sihirbaz türü kayıtlı (<xref:EnvDTE.Constants.vsWizardNewProject>) veya sihirbaz türünü gösteren GUID. İçinde [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)] , sihirbaz GUID uygulamasıdır {0F90E1D0-4999-11D1-B6D1-00A0C90F2744}.|  
|`ProjectName`|Benzersiz bir dize [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] proje adı.|  
|`LocalDirectory`|Yerel bir konum, proje dosyaları çalışma.|  
|`InstallationDirectory`|Dizin yolunu [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] yüklemedir.|  
|`FExclusive`|Proje bir açık çözümü kapatmanız gösteren Boole bayrağı.|  
|`SolutionName`|Dizin bölümü veya .sln uzantısı olmadan çözüm dosyasının adı. .Suo dosya adı da kullanılarak oluşturulan `SolutionName`. Bu bağımsız değişken boş bir dize olmadığı durumlarda, sihirbaz kullanan <xref:EnvDTE._Solution.Create%2A> ile projeyi eklemeden önce <xref:EnvDTE._Solution.AddFromTemplate%2A>. Bu adı boş bir dize ise, kullanın <xref:EnvDTE._Solution.AddFromTemplate%2A> çağırmadan <xref:EnvDTE._Solution.Create%2A>.|  
|`Silent`|Sihirbaz sessiz bir şekilde çalıştırılması gerekip gerekmediğini belirten bir Boolean olarak **son** tıklanan (`TRUE`).|  
  
## <a name="context-parameters-for-add-new-item"></a>Yeni öğe için bağlam parametreleri ekleme  
  
|Parametre|Açıklama|  
|---------------|-----------------|  
|`WizardType`|Sihirbaz türü kayıtlı (<xref:EnvDTE.Constants.vsWizardAddItem>) veya sihirbaz türünü gösteren GUID. İçinde [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)] , sihirbaz GUID uygulamasıdır {0F90E1D1-4999-11D1-B6D1-00A0C90F2744}.|  
|`ProjectName`|Benzersiz bir dize [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] proje adı.|  
|`ProjectItems`|Çalışan proje dosyalarını içeren yerel bir konum.|  
|`ItemName`|Eklenecek öğenin adı. Bu ad, varsayılan dosya adı ya da gelen kullanıcı türleri dosya adı değil **öğeleri Ekle** iletişim kutusu. Ad .vsdir dosyasında ayarlanan bayrakları temel alır. Ad null değeri olabilir.|  
|`InstallationDirectory`|Dizin yolunu [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] yüklemedir.|  
|`Silent`|Sihirbaz sessiz bir şekilde çalıştırılması gerekip gerekmediğini belirten bir Boolean olarak **son** tıklanan (`TRUE`).|  
  
## <a name="context-parameters-for-add-sub-project"></a>Bağlam parametreleri ekleme alt proje için  
  
|Parametre|Açıklama|  
|---------------|-----------------|  
|`WizardType`|Sihirbaz türü kayıtlı (<xref:EnvDTE.Constants.vsWizardAddSubProject>) veya sihirbaz türünü gösteren GUID. İçinde [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)] , sihirbaz GUID uygulamasıdır {0F90E1D2-4999-11D1-B6D1-00A0C90F2744}.|  
|`ProjectName`|Benzersiz bir dize [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] proje adı.|  
|`ProjectItems`|İşaretçi `ProjectItems` Sihirbazı çalıştığı koleksiyonu. Bu işaretçinin proje hiyerarşisi seçimi temel alınarak sihirbaza geçirilir. Bir kullanıcı, genellikle bir klasör öğesi yerleştirileceği seçer ve ardından projenin çağırır **Öğe Ekle** iletişim kutusu.|  
|`LocalDirectory`|Yerel bir konum, proje dosyaları çalışma.|  
|`ItemName`|Eklenecek öğenin adı. Bu ad, varsayılan dosya adı ya da gelen kullanıcı türleri dosya adı değil **öğeleri Ekle** iletişim kutusu. Ad .vsdir dosyasında ayarlanan bayrakları temel alır. Ad null değeri olabilir.|  
|`InstallationDirectory`|Dizin yolunu [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] yüklemedir.|  
|`Silent`|Sihirbaz sessiz bir şekilde çalıştırılması gerekip gerekmediğini belirten bir Boolean olarak **son** tıklanan (`TRUE`).|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject2>   
 [Özel Parametreler](../../extensibility/internals/custom-parameters.md)   
 [Sihirbazlar](../../extensibility/internals/wizards.md)   
 [Sihirbazı (. Vsz) dosyası](../../extensibility/internals/wizard-dot-vsz-file.md)   
 [Sihirbazları başlatmak için bağlam parametreleri](http://msdn.microsoft.com/library/051a10f4-9e45-4604-b344-123044f33a24)

