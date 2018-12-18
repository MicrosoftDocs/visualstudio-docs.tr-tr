---
title: Proje ve öğe şablonlarını kaydetme | Microsoft Docs
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
- projects [Visual Studio SDK], adding items
- registry, Add New Item dialog box
- Add New Item dialog box
- Add New Project dialog box
- registry, Add New Project dialog box
ms.assetid: 6b909f93-d7f5-4aec-81c6-ee9ff0f31638
caps.latest.revision: 28
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 06a9840680c76103373cde00ac37310bb6138095
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51764291"
---
# <a name="registering-project-and-item-templates"></a>Proje ve Öğe Şablonlarını Kaydetme
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Proje türleri, kendi proje ve proje öğesi şablonları bulunduğu yere dizinleri kaydetmeniz gerekir. [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] gösterilecek belirlemek için proje türleri ile ilişkili kayıt bilgileri kullanır **Yeni Proje Ekle** ve **Yeni Öğe Ekle** iletişim kutuları.  
  
 Şablonlar hakkında daha fazla bilgi için bkz. [ekleme proje ve proje öğesi şablonları](../../extensibility/internals/adding-project-and-project-item-templates.md).  
  
## <a name="registry-entries-for-projects"></a>Projeleri için kayıt defteri girişleri  
 Aşağıdaki örnekler hkey_local_machıne\software\microsoft\visualstudio altında kayıt defteri girdilerini\\<*sürüm*>. Eşlik eden tabloları örneklerde kullanılan öğeleri açıklamaktadır.  
  
```  
[Projects\{ProjectGUID}]  
@="MyProjectType"  
"DisplayName"="#2"  
"Package"="{VSPackageGUID}"  
"ProjectTemplatesDir"="C:\\MyProduct\\MyProjectTemplates"  
```  
  
|Ad|Tür|Açıklama|  
|----------|----------|-----------------|  
|@|REG_SZ|Bu tür projeler varsayılan adı.|  
|displayName|REG_SZ|Uydu DLL alınacak adı kaynak Kimliğini paketleri altında kayıtlı.|  
|Paket|REG_SZ|Sınıf kimliği paket paketleri altında kayıtlı.|  
|ProjectTemplatesDir|REG_SZ|Proje şablonu dosyaları varsayılan yolu. Proje şablonu dosyaları tarafından görüntülenen **yeni proje** şablonu.|  
  
### <a name="registering-item-templates"></a>Öğe şablonlarını kaydetme  
 Öğe şablonları depoladığınız directory kaydetmeniz gerekir.  
  
```  
[Projects\{ProjectGUID}\AddItemTemplates\TemplateDirs\{VSPackageGUID}\1]  
@="#7"  
"TemplatesDir"="C:\\MyProduct\\MyProjectItemTemplates "  
"TemplatesLocalizedSubDir"="#10"  
"SortPriority"=dword:00000064  
```  
  
|Ad|Tür|Açıklama|  
|----------|----------|-----------------|  
|@|REG_SZ|Öğe Ekle şablonları için kaynak kimliği.|  
|TemplatesDir|REG_SZ|Yolu için iletişim kutusunda görüntülenen proje öğelerinin **Yeni Öğe Ekle** Sihirbazı.|  
|TemplatesLocalizedSubDir|REG_SZ|Kaynak Kimliği TemplatesDir alt adlarıyla bir dize, yerelleştirilmiş şablonları tutar. Çünkü [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] yükleri dize kaynağını Uydu DLL'leri, varsa, her bir uydu DLL farklı yerelleştirilmiş alt adı içerebilir.|  
|SortPriority|REG_DWORD|Ayarlama, şablon içinde görüntülenme sırasını belirleyen SortPriority **Yeni Öğe Ekle** iletişim kutusu. Daha büyük SortPriority değerleri daha önce şablon listesinde görünür.|  
  
### <a name="registering-file-filters"></a>Dosya filtreleri kaydediliyor  
 İsteğe bağlı olarak, filtre kaydedebilirsiniz, [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] dosya adları için istediğinde kullanır. Örneğin, [!INCLUDE[csprcs](../../includes/csprcs-md.md)] filtre **açık dosya** iletişim kutusudur:  
  
 **Visual C# dosyaları (\*.cs,\*.resx,\*.settings,\*.xsd,\*.wsdl);\*. cs,\*.resx,\*.settings,\*.xsd,\*.wsdl)**  
  
 Birden çok filtre kaydını desteklemek için her bir filtrenin hkey_local_machıne\software\microsoft\visualstudio altında kendi alt kayıtlı\\<*sürüm*> \Projects\\{ \< *ProjectGUID*>} \Filters\\<*alt*>. Alt anahtar adı isteğe bağlıdır; [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] alt anahtarının adı yoksayar ve yalnızca değerlerini kullanır.  
  
 Bir filtre bayrakları, aşağıdaki tabloda gösterilen ayarlayarak kullanılır bağlamları denetleyebilirsiniz. Filtre Ayarla herhangi bir bayrağı yoksa, ortak filtrelere sonra listelenecektir **varolan öğeyi Ekle** iletişim kutusu ve **açık dosya** iletişim kutusu, ancak kullanılmaz **dosyalarda Bul**  iletişim kutusu.  
  
```  
[Projects\{ProjectGUID}\Filters\MyLanguageFilter]  
@="#3"  
"CommonOpenFilesFilter"=dword:00000000  
"CommonFindFilesFilter"=dword:00000000  
"FindInFilesFilter"=dword:00000000  
"NotOpenFileFilter"=dword:00000000  
"NotAddExistingItemFilter"=dword:00000000  
"SortPriority"=dword:00000064  
```  
  
|Ad|Tür|Açıklama|  
|----------|----------|-----------------|  
|CommonFindFilesFilter|REG_DWORD|Filtreye ortak filtrelerden birini yapar **dosyalarda Bul** iletişim kutusu. Ortak filtreler gibi yaygın olarak işaretlenmemiş filtreleri önce Filtre listesinde listelenir.|  
|CommonOpenFilesFilter|REG_DWORD|Filtreye ortak filtrelerden birini yapar **açık dosya** iletişim kutusu. Ortak filtreler gibi yaygın olarak işaretlenmemiş filtreleri önce Filtre listesinde listelenir.|  
|FindInFilesFilter|REG_DWORD|Ortak filtrelere sonra filtre listeleri **dosyalarda Bul** iletişim kutusu.|  
|NotOpenFileFilter|REG_DWORD|Filtre olarak kullanılmayacağını gösterir **açık dosya** iletişim kutusu.|  
|NotAddExistingItemFilter|REG_DWORD|Filtre olarak kullanılmayacağını gösterir **varolan öğeyi Ekle** iletişim kutusu.|  
|SortPriority|REG_DWORD|Filtreler görüntülenme sırasını belirleyen SortPriority ayarlayın. Daha büyük SortPriority değerleri daha önce Filtre listesinde görünür.|  
  
## <a name="directory-structure"></a>Dizin yapısı  
 Konum tümleşik geliştirme ortamı (IDE) üzerinden kayıtlı olduğu sürece VSPackages şablon dosyaları ve klasörleri herhangi bir yerel veya uzak bir diskte yerleştirebilirsiniz. Ancak, kuruluş kolaylığı için ürün uygulamasının yükleme yolu altında aşağıdaki dizin yapısını öneririz.  
  
 \Templates  
  
 \Projects (proje şablonları içerir)  
  
 \Applications  
  
 \Components  
  
 \ ...  
  
 \ProjectItems (proje öğeleri içerir)  
  
 \Class  
  
 \Form  
  
 \Web Sayfası  
  
 \HelperFiles (çok dosyalı proje öğelerinde kullanılan dosyaları içerir)  
  
 \WizardFiles  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Proje ve proje öğesi şablonları ekleme](../../extensibility/internals/adding-project-and-project-item-templates.md)   
 [Sihirbazlar](../../extensibility/internals/wizards.md)   
 [Uygulamaları yerelleştirme](../../ide/localizing-applications.md)   
 [Genişletme Projeleri için Genellikle Kullanılan Nesnelerin CATID’leri](../../extensibility/internals/catids-for-objects-that-are-typically-used-to-extend-projects.md)

