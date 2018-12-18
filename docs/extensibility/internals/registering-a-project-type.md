---
title: Proje türü kaydetme | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], new project registry entries
- registry, new project types
- registration, new project types
ms.assetid: dfc0e231-6b4e-447d-9d64-0e66dea3394a
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 1839ed51b3bd8b26bd67583054fa142f5853a2de
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49939691"
---
# <a name="registering-a-project-type"></a>Proje Türü Kaydetme
Yeni bir proje türü oluşturduğunuzda, sağlayan kayıt defteri girdileri oluşturmanız gerekir [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] tanınması ve proje türünüz ile çalışır. Genellikle bir kayıt defteri (.rgs) komut dosyası kullanarak bu kayıt defteri girdilerini oluşturun.  
  
 Aşağıdaki örnekte, kayıt defterinden deyimleri varsayılan yollarını sağlar ve veri uygunsa girişlerinden for each deyimi kayıt betiği içeren bir tablo ardından. Tabloları, komut dosyası girişleri ve deyimler hakkında ek bilgiler sağlar.  
  
> [!NOTE]
>  Aşağıdaki kayıt defteri bilgileri, örnek türü ve girişleri, proje türünü kaydetmek için yazacaksınız kayıt defteri betiklerdeki amaçları olması amaçlanmıştır. Gerçek girişlerinizi ve kullanımları proje türünüz belirli gereksinimlerine bağlı olarak değişebilir. Geliştirdiğiniz projenin türünü çok benzeyen bir bulmak kullanılabilir örneklerin gözden geçirin ve sonra bu örnek için kayıt betiği gözden geçirin.  
  
 HKEY_CLASSES_ROOT verilebilir.  
  
## <a name="example"></a>Örnek  
  
```  
\.figp  
   @="FigPrjFile"  
   "Content Type"="text/plain"  
\.figp\ShellNew  
   "NullFile"=""  
\FigPrjFile  
   @="Figure Project File"  
\DefaultIcon  
   @="<Visual Studio SDK installation path>\\9.0VSIntegration\\SomeFolder\\FigPkgs\\FigPrj\\Debug\\FigPrj.dll,-206"  
\shell\open  
   @="&Open in Visual Studio"  
\shell\open\command  
   @="devenv.exe \"%1\""  
```  
  
|Ad|Tür|Veri|Açıklama|  
|----------|----------|----------|-----------------|  
|`@`|REG_SZ|`FigPrjFile`|Ad ve açıklama projenin uzantısı .figp sahip dosyaları yazın.|  
|`Content Type`|REG_SZ|`Text/plain`|Proje dosyaları için içerik türü.|  
|`NullFile`|REG_SZ|`Null`||  
|`@`|REG_SZ|`%MODULE%,-206`|Bu tür bir proje için kullanılan varsayılan simge. % MODULE % deyimi, DLL proje türünün varsayılan konumu için kayıt defterindeki tamamlanır.|  
|`@`|REG_SZ|`&Open in Visual Studio`|Varsayılan uygulama, bu proje türü açılır.|  
|`@`|REG_SZ|`devenv.exe "%1"`|Bu tür bir proje açıldığında çalıştırılacak varsayılan komutu.|  
  
 Aşağıdaki örnek HKEY_LOCAL_MACHINE ' ve kayıt defteri anahtarı [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\99.0Exp\Packages] altında yer alır.  
  
## <a name="example"></a>Örnek  
  
```  
\{ACEF4EB2-57CF-11D2-96F4-000000000000} (The CLSID for the VSPackage)  
   @="FigPrj Project Package"  
   "InprocServer32"="9.0<Visual Studio SDK installation path>\\VSIntegration\\Archive\\FigPkgs\\FigPrj\\                      Debug\\FigPrj.dll"  
   "CompanyName"="Microsoft"  
   "ProductName"="Figure Project Sample"  
   "ProductVersion"="9.0"  
   "MinEdition"="professional"  
   "ID"=dword:00000001  
\{ACEF4EB2-57CF-11D2-96F4-000000000000}\SatelliteDLL  
   "DllName"="FigPrjUI.dll"  
   "Path"="9.0<Visual Studio SDK installation path>\\VSIntegration\\Archive\\FigPkgs\\FigPrj\\Debug\\"  
\{ACEF4EB2-57CF-11D2-96F4-000000000000}\Automation  
   "FigProjects"=""  
\{ACEF4EB2-57CF-11D2-96F4-000000000000}\AutomationEvents  
   "FigProjectsEvents"="Returns the FigProjectsEvents Object"  
   "FigProjectItemsEvents"="Returns the FigProjectItemsEvents Object"  
```  
  
|Ad|Tür|Veri|Açıklama|  
|----------|----------|----------|-----------------|  
|`@` (Varsayılan)|REG_SZ|`FigPrj Project VSPackage`|Bu yerelleştirilebilir adıdır VSPackage'ı (proje türü) kayıtlı.|  
|`InprocServer32`|REG_SZ|`%MODULE%`|Proje türü DLL yolu. IDE bu DLL'yi yükler ve VSPackage CLSID değerine geçirir `DllGetClassObject` almak için <xref:Microsoft.VisualStudio.OLE.Interop.IClassFactory> oluşturulacağını <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage> nesne.|  
|`CompanyName`|REG_SZ|`Microsoft`|Proje türü geliştirilen şirketin adı.|  
|`ProductName`|REG_SZ|`Figure Project Sample`|Proje türünün adı.|  
|`ProductVersion`|REG_SZ|`9.0`|Proje türü sürüm numarasını bırakın.|  
|`MinEdition`|REG_SZ|`professional`|Kaydedilmekte VSPackage sürümü.|  
|`ID`|REG_DWORD|`%IDS_PACKAGE_LOAD_KEY%`|Paket anahtar ' % s'projesi VSPackage'ı yükleyin. Anahtar, ortam başlatıldıktan sonra bir proje yüklendiğinde doğrulanır.|  
|`DllName`|REG_SZ|`%RESOURCE_DLL%`|Uydu proje türü için yerelleştirilmiş kaynaklar içeren DLL dosya adı.|  
|`Path`|REG_SZ|`%RESOURCE_PATH%`|Uydu DLL yolu.|  
|`FigProjectsEvents`|REG_SZ|Değerin açıklamasına bakın.|Bu Otomasyon olay için döndürülen metin dizesini belirler.|  
|`FigProjectItemsEvents`|REG_SZ|Değerin açıklamasına bakın.|Bu Otomasyon olay için döndürülen metin dizesini belirler.|  
  
 Aşağıdaki örnekler kayıt defteri anahtarı [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\9.0Exp\Projects] altında yer alır.  
  
## <a name="example"></a>Örnek  
  
```  
\{C061DB26-5833-11D2-96F5-000000000000} (The CLSID for projects of this type)  
   @="FigPrj Project"  
   "DisplayName"="#2"  
   "Package"="{ACEF4EB2-57CF-11D2-96F4-000000000000}"  
   "ProjectTemplatesDir"="C:\\Program Files\\VSIP 9.0\\EnvSDK\\FigPkgs\\                           FigPrj\\FigPrjProjects"  
   "ItemTemplatesDir"="<Visual Studio SDK installation path>\\VSIntegration\\Archive9.0\\FigPkgs\\FigPrj\\                           FigPrjProjectItems"  
   "DisplayProjectFileExtensions"="#3"  
   "PossibleProjectExtensions"="figp"  
   "DefaultProjectExtension"=".figp"  
\{C061DB26-5833-11D2-96F5-000000000000}\Filters\1       (Folder 1 contains settings for Open Files filters.)  
   @="#4"  
   "CommonOpenFilesFilter"=dword:00000000  
   "CommonFindFilesFilter"=dword:00000000  
   "NotAddExistingItemFilter"=dword:00000000  
   "FindInFilesFilter"=dword:00000000  
   "NotOpenFileFilter"=dword:00000000  
   "SortPriority"=dword:000003e8  
\{C061DB26-5833-11D2-96F5-000000000000}\Filters\2  
      (Folder 2 contains settings for Find in Files filters.)  
   @="#5"  
   "CommonOpenFilesFilter"=dword:00000000  
   "CommonFindFilesFilter"=dword:00000000  
   "NotAddExistingItemFilter"=dword:00000001  
   "FindInFilesFilter"=dword:00000001  
   "NotOpenFileFilter"=dword:00000000  
   "SortPriority"=dword:000003e8  
\{C061DB26-5833-11D2-96F5-000000000000}\AddItemTemplates\TemplateDirs\ {ACEF4EB2-57CF-11D2-96F4-000000000000}\1 (Second GUID indicates the registered project type for the Add Items templates.)  
   @="#6"  
   "TemplatesDir"="<Visual Studio SDK installation path>\\VSIntegration\\Archive9.0\\FigPkgs\\FigPrj\\                    FigPrjProjectItems"  
   "SortPriority"=dword:00000064  
```  
  
|Ad|Tür|Veri|Açıklama|  
|----------|----------|----------|-----------------|  
|`@`|REG_SZ|`FigPrj Project`|Bu tür projeler varsayılan adı.|  
|`DisplayName`|REG_SZ|`#%IDS_PROJECT_TYPE%`|Uydu DLL alınacak adı kaynak Kimliğini paketleri altında kayıtlı.|  
|`Package`|REG_SZ|`%CLSID_Package%`|VSPackage'ı sınıfı kimliği paketleri altında kayıtlı.|  
|`ProjectTemplatesDir`|REG_SZ|`%TEMPLATE_PATH%\FigPrjProjects`|Proje şablonu dosyaları varsayılan yolu. Bu, yeni bir proje şablonu tarafından gösterilen dosyalarıdır.|  
|`ItemTemplatesDir`|REG_SZ|`%TEMPLATE_PATH% \FigPrjProjectItems`|Proje öğesi şablon dosyaları varsayılan yolu. Yeni Öğe Ekle şablon tarafından görüntülenen dosyalar şunlardır.|  
|`DisplayProjectFileExtensions`|REG_SZ|`#%IDS_DISPLAY_PROJ_FILE_EXT%`|Uygulamak IDE sağlayan **açık** iletişim kutusu.|  
|`PossibleProjectExtensions`|REG_SZ|`figp`|IDE tarafından açılması projenin bu proje türü (Proje fabrikası) işlenip işlenmediğini belirlemek için kullanılır. Birden fazla giriş biçimini noktalı virgülle ayrılmış listesidir. Örneğin "vdproj; vdp".|  
|`DefaultProjectExtension`|REG_SZ|`.figp`|IDE tarafından Kaydet işlemi için varsayılan dosya adı uzantısı olarak kullanılır.|  
|`Filter Settings`|REG_DWORD|Çeşitli, ifadeler ve tablodan sonraki açıklamaları bakın.|Bu ayarlar, kullanıcı Arabirimi iletişim kutularında dosyaları görüntülemek için çeşitli filtreleri ayarlamak için kullanılır.|  
|`@`|REG_SZ|`#%IDS_ADDITEM_TEMPLATES_ENTRY%`|Öğe Ekle şablonları için kaynak kimliği.|  
|`TemplatesDir`|REG_SZ|`%TEMPLATE_PATH%\FigPrjProjectItems`|Yolu için iletişim kutusunda görüntülenen proje öğelerinin **Yeni Öğe Ekle** şablonu.|  
|`SortPriority`|REG_DWORD|`100 (vcprx64)`|Ağaç düğümünde görüntülenen dosyaların sıralama düzeni belirler **Yeni Öğe Ekle** iletişim kutusu.|  
  
 Aşağıdaki tablo, önceki kod kesimi içinde filtre seçenekleri gösterir.  
  
|Filtre seçeneği|Açıklama|  
|-------------------|-----------------|  
|`CommonFindFilesFilter`|Filtre ortak filtrelere biri olduğunu gösterir **dosyalarda Bul** iletişim kutusu. Ortak Filtrelere genel'olarak işaretlenmemiş filtreleri önce Filtre listesinde listelenir.|  
|`CommonOpenFilesFilter`|Filtre ortak filtrelere biri olduğunu gösterir **açık dosya** iletişim kutusu. Ortak Filtrelere genel'olarak işaretlenmemiş filtreleri önce Filtre listesinde listelenir.|  
|`FindInFilesFilter`|Filtre filtrelerden biri olacağını belirtir **dosyalarda Bul** iletişim kutusunu ve sonra ortak filtrelere listelenir.|  
|`NotOpenFileFilter`|Filtre kullanılacak değil olduğunu gösteren **açık dosya** iletişim kutusu.|  
|`NotAddExistingItemFilter`|Filtre Ekle kullanılmayacak gösterir **var olan öğe** iletişim kutusu.|  
  
 Varsayılan olarak, bir filtre yok ya da daha fazlası bayrakları kümesini filtre kullanılır **varolan öğeyi Ekle** iletişim kutusu ve **açık dosya** ortak filtreler listelenmiştir sonra iletişim kutusu. Filtre kullanılmaz **dosyalarda Bul** iletişim kutusu.  
  
 Aşağıdaki örnekler kayıt defteri anahtarı [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\9.0Exp\Projects] altında yer alır.  
  
## <a name="example"></a>Örnek  
  
```  
{FE3BBBB6-72D5-11d2-9ACE-00C04F79A2A4} (The CLSID for Enterprise Projects)  
\{FE3BBBB6-72D5-11d2-9ACE-00C04F79A2A4}\AddItemTemplates\TemplateDirs\ {ACEF4EB2-57CF-11D2-96F4-000000000000}\1 (CLSID for projects of this type)  
   @="#7"  
   "TemplatesDir"="<Visual Studio SDK installation path>\\VSIntegration\\Archive9.0\\FigPrj\\FigPrjProjects"  
   "SortPriority"=dword:00000029  
   "NewProjectDialogOnly"=dword:00000000  
```  
  
|Ad|Tür|Veri|Açıklama|  
|----------|----------|----------|-----------------|  
|`@`|REG_SZ|`#%IDS_NEWPROJ_ TEMPLATES_ENTRY%`|Yeni proje şablonları kaynak kimliği.|  
|`TemplatesDir`|REG_SZ|`%TEMPLATE_PATH%\FigPrjProjects`|Varsayılan yolu kayıtlı proje türü projeler için.|  
|`SortPriority`|REG_DWORD|`41 (x29)`|Sıralama projelerinin yeni projeler Sihirbazı iletişim kutusunda görüntülenen ayarlar.|  
|`NewProjectDialogOnly`|REG_DWORD|`0`|0, bu tür projeleri yalnızca yeni proje iletişim kutusunda görüntülendiğini gösterir.|  
  
 Aşağıdaki örnekler kayıt defteri anahtarı [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\9.0Exp\Projects] altında yer alır.  
  
## <a name="example"></a>Örnek  
  
```  
\{A2FE74E1-B743-11d0-AE1A-00A0C90FFFC3} (CLSID for Miscellaneous Files projects)  
   @="Miscellaneous Files Project"  
\AddItemTemplates\TemplateDirs\{ACEF4EB2-57CF-11D2-96F4-000000000000}\1  
                                 (CLSID for Figures Project projects)  
   @="#6"  
   "TemplatesDir"="<Visual Studio SDK installation path>\\VSIntegration\\Archive9.0\\FigPkgs\\FigPrj\\                    FigPrjProjectItems"  
   "SortPriority"=dword:00000064  
```  
  
|Ad|Tür|Veri|Açıklama|  
|----------|----------|----------|-----------------|  
|`@`|REG_SZ|Yok.|Çeşitli dosyalar projeleri girişleri aşağıdaki girişleri gösterir varsayılan değeri.|  
|`@`|REG_SZ|`#%IDS_ADDITEM_TEMPLATES_ENTRY%`|Yeni öğe ekleme şablon dosyaları için kaynak kimliği değeri.|  
|`TemplatesDir`|REG_SZ|`%TEMPLATE_PATH%\FigPrjProjectItems`|Varsayılan yol olarak görüntülenen öğelerin **Yeni Öğe Ekle** iletişim kutusu.|  
|`SortPriority`|REG_DWORD|`100 (vcprx64)`|Ağaç düğümünde görüntülemek için sıralama düzeni oluşturur **Yeni Öğe Ekle** iletişim kutusu.|  
  
 Aşağıdaki örnek, kayıt defteri anahtarı [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\9.0Exp\Menus] altında bulunur.  
  
## <a name="example"></a>Örnek  
  
```  
"{ACEF4EB2-57CF-11D2-96F4-000000000000}"=",1000,1"  
```  
  
 IDE menüsü girişi menü bilgilerini almak için kullanılan kaynağına işaret eder. Bu veriler menü veritabanına birleştirilmiştir, aynı anahtarı kayıt defteri MenusMerged bölümünde eklenir. VSPackage'ı MenusMerged bölümünde herhangi bir şey doğrudan değiştirmeniz gerekir. Aşağıdaki tabloda veri alanında üç virgülle ayrılmış-alanları vardır. İlk alanı menüsü kaynak dosyasının tam yol tanımlar:  
  
- İlk alan atlanırsa, menü kaynağı uydu DLL VSPackage GUID ile tanımlanan'ndan yüklenir.  
  
  İkinci alan CTMENU türünde bir menü kaynak kimliği tanımlar:  
  
- Kaynak Kimliği belirtilmiş ve dosya yolu ilk parametre tarafından sağlanan, menü kaynağı tam dosya yolundan yüklenir.  
  
- Kaynak Kimliği sağlanırsa ancak dosya yolu değil, menü kaynağı uydu DLL yüklenir.  
  
- Tam dosya yolunu sağlanır ve kaynak kimliği atlanırsa, yüklenecek dosyanın CTO dosyası olması beklenir.  
  
  Son alan CTMENU kaynak için sürüm numarasını belirtir. Sürüm numarası değiştirerek menüsünün yeniden birleştirebilirsiniz.  
  
|Ad|Tür|Veri|Açıklama|  
|----------|----------|----------|-----------------|  
|CLSID_Package %|REG_SZ|`,1000,1`|Menü bilgilerini almak için kaynak.|  
  
 Aşağıdaki örnekler kayıt defteri anahtarı [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\9.0Exp\NewProjectTemplates] altında yer alır.  
  
```  
\TemplateDirs\{ACEF4EB2-57CF-11D2-96F4-000000000000}\1                (CLSID for Figures Project projects)  
   @="#7"  
   "TemplatesDir"="<Visual Studio SDK installation path>\\VSIntegration\\Archive9.0\\FigPkgs\\FigPrj\\FigPrjProjects"  
   "SortPriority"=dword:00000029  
   "NewProjectDialogOnly"=dword:00000000  
```  
  
|Ad|Tür|Veri|Açıklama|  
|----------|----------|----------|-----------------|  
|`@`|REG_SZ|`#%IDS_NEWPROJ_TEMPLATES_ENTRY%`|Kaynak Kimliği değeri rakamları proje yeni proje şablonları.|  
|`TemplatesDir`|REG_SZ|`%TEMPLATE_PATH%\FigPrjProjects`|Yeni Proje dizini varsayılan yolu. Bu dizinin öğeleri içinde görüntülenecektir **yeni proje sihirbazını** iletişim kutusu.|  
|`SortPriority`|REG_DWORD|`41 (x29)`|Hangi projelerin görüntülenir ağaç düğümünde sırayla kurar **yeni proje** iletişim kutusu.|  
|`NewProjectDialogOnly`|REG_DWORD|`0`|0, bu tür projeleri yalnızca görüntülendiğini gösterir **yeni proje** iletişim kutusu.|  
  
 Aşağıdaki örnek, kayıt defteri anahtarı [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\9.0Exp\InstalledProducts] altında bulunur.  
  
```  
\FiguresProductSample  
   "Package"="{ACEF4EB2-57CF-11D2-96F4-000000000000}"  
   "UseInterface"=dword:00000001  
```  
  
|Ad|Tür|Veri|Açıklama|  
|----------|----------|----------|-----------------|  
|`Package`|REG_SZ|`%CLSID_Package%`|Kayıtlı VSPackage sınıfı kimliği.|  
|`UseInterface`|REG_DWORD|`1`|1 kullanıcı Arabirimi bu proje ile etkileşim kurmak için kullanılacağını gösterir. 0, herhangi bir kullanıcı Arabirimi arabirim olduğunu gösterir.|  
  
 Yeni proje türleri sık denetleyen The.vsz dosyaları relatıve_path giriş içerir. Bu yol, aşağıdaki kurulum anahtarı proje türünde \ProductDir girdisini altında belirtilen yolun göreli şöyledir:  
  
 HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\7.0Exp\Setup  
  
 Örneğin, Kurumsal çerçeve proje şablonları, aşağıdaki kayıt defteri girdilerini ekleyin:  
  
 HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\7.0Exp\Setup\EF\ProductDir C:\Program Files\Microsoft Visual Studio\EnterpriseFrameworks\ =  
  
 Yani bir PROJECT_TYPE içerip içermediğini = EF girişi .vsz dosyasında, .vsz dosyaları daha önce belirtilen ProductDir dizinde ortam bulur.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Denetim listesi: Yeni proje türleri oluşturma](../../extensibility/internals/checklist-creating-new-project-types.md)   
 [Proje modeli öğeleri](../../extensibility/internals/elements-of-a-project-model.md)   
 [Proje Üreteçlerini Kullanarak Proje Örnekleri Oluşturma](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)