---
title: Bağlam parametreleri | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- wizards, context parameters
- context parameters
ms.assetid: 1a062dcb-8a8f-40dd-bea9-3d10f9448966
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d595bcc99cbacabd55c8e85775e1d691e917a41c
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49875846"
---
# <a name="context-parameters"></a>Bağlam parametreleri
İçinde [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] tümleşik geliştirme ortamı (IDE), sihirbazlar ekleyebilirsiniz **yeni proje**, **Yeni Öğe Ekle**, veya **alt proje Ekle** iletişim kutuları. Eklenen sihirbazlar mevcuttur **dosya** menüsü veya bir projeye sağ tıklayarak **Çözüm Gezgini**. IDE bağlam parametreleri Sihirbazı uygulamaya geçirir. IDE Sihirbazı çağırdığında proje durumunu bağlam parametreleri tanımlayın.  
  
 Ayarlayarak sihirbazları IDE başlatıldığında <xref:Microsoft.VisualStudio.Shell.Interop.VSADDITEMOPERATION> IDE'nin çağrıda bayrağı <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.AddItem%2A> proje için yöntemi. Ayarlandığında, proje neden `IVsExtensibility::RunWizardFile` kayıtlı sihirbaz adı veya GUID ve IDE arabimini diğer bağlam parametreleri kullanarak yürütülecek yöntemi.  
  
## <a name="context-parameters-for-new-project"></a>Yeni proje için bağlam parametreleri  
  
| Parametre | Açıklama |
|-------------------------| - |
| `WizardType` | Sihirbaz türü kayıtlı (<xref:EnvDTE.Constants.vsWizardNewProject>) veya sihirbaz türünü gösteren GUID. İçinde [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] , sihirbaz GUID uygulamasıdır {0F90E1D0-4999-11D1-B6D1-00A0C90F2744}. |
| `ProjectName` | Benzersiz bir dize [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] proje adı. |
| `LocalDirectory` | Yerel bir konum, proje dosyaları çalışma. |
| `InstallationDirectory` | Dizin yolunu [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] yüklemedir. |
| `FExclusive` | Proje bir açık çözümü kapatmanız gösteren Boole bayrağı. |
| `SolutionName` | Dizin bölümü olmadan çözüm dosyasının adını veya *.sln* uzantısı. *.Suo* dosya adı, kullanarak da oluşturulur `SolutionName`. Bu bağımsız değişken boş bir dize olmadığı durumlarda, sihirbaz kullanan <xref:EnvDTE._Solution.Create%2A> ile projeyi eklemeden önce <xref:EnvDTE._Solution.AddFromTemplate%2A>. Bu adı boş bir dize ise, kullanın <xref:EnvDTE._Solution.AddFromTemplate%2A> çağırmadan <xref:EnvDTE._Solution.Create%2A>. |
| `Silent` | Sihirbaz sessiz bir şekilde çalıştırılması gerekip gerekmediğini belirten bir Boolean olarak **son** tıklanan (`TRUE`). |
  
## <a name="context-parameters-for-add-new-item"></a>Bağlam parametreleri için Yeni Öğe Ekle  
  
| Parametre | Açıklama |
|-------------------------| - |
| `WizardType` | Sihirbaz türü kayıtlı (<xref:EnvDTE.Constants.vsWizardAddItem>) veya sihirbaz türünü gösteren GUID. İçinde [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] , sihirbaz GUID uygulamasıdır {0F90E1D1-4999-11D1-B6D1-00A0C90F2744}. |
| `ProjectName` | Benzersiz bir dize [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] proje adı. |
| `ProjectItems` | Çalışan proje dosyalarını içeren yerel bir konum. |
| `ItemName` | Eklenecek öğenin adı. Bu ad, varsayılan dosya adı ya da gelen kullanıcı türleri dosya adı değil **öğeleri Ekle** iletişim kutusu. Ad, ayarlanan bayrakları temel *.vsdir* dosya. Ad null değeri olabilir. |
| `InstallationDirectory` | Dizin yolunu [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] yüklemedir. |
| `Silent` | Sihirbaz sessiz bir şekilde çalıştırılması gerekip gerekmediğini belirten bir Boolean olarak **son** tıklanan (`TRUE`). |
  
## <a name="context-parameters-for-add-sub-project"></a>Bağlam parametreleri için alt proje Ekle  
  
| Parametre | Açıklama |
|-------------------------| - |
| `WizardType` | Sihirbaz türü kayıtlı (<xref:EnvDTE.Constants.vsWizardAddSubProject>) veya sihirbaz türünü gösteren GUID. İçinde [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] , sihirbaz GUID uygulamasıdır {0F90E1D2-4999-11D1-B6D1-00A0C90F2744}. |
| `ProjectName` | Benzersiz bir dize [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] proje adı. |
| `ProjectItems` | İşaretçi `ProjectItems` Sihirbazı çalıştığı koleksiyonu. Bu işaretçinin proje hiyerarşisi seçimi temel alınarak sihirbaza geçirilir. Bir kullanıcı, genellikle bir klasör öğesi yerleştirileceği seçer ve ardından projenin çağırır **Öğe Ekle** iletişim kutusu. |
| `LocalDirectory` | Yerel bir konum, proje dosyaları çalışma. |
| `ItemName` | Eklenecek öğenin adı. Bu ad, varsayılan dosya adı ya da gelen kullanıcı türleri dosya adı değil **öğeleri Ekle** iletişim kutusu. Ad, ayarlanan bayrakları temel *.vsdir* dosya. Ad null değeri olabilir. |
| `InstallationDirectory` | Dizin yolunu [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] yükleme. |
| `Silent` | Sihirbaz sessiz bir şekilde çalıştırılması gerekip gerekmediğini belirten bir Boolean olarak **son** tıklanan (`TRUE`). |
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject2>   
 [Özel Parametreler](../../extensibility/internals/custom-parameters.md)   
 [Sihirbazlar](../../extensibility/internals/wizards.md)   
 [Sihirbaz (.vsz) dosyası](../../extensibility/internals/wizard-dot-vsz-file.md)   
 [Sihirbazları başlatmak için bağlam parametreleri](https://msdn.microsoft.com/Library/051a10f4-9e45-4604-b344-123044f33a24)