---
title: GUID'leri ve kimlikleri Visual Studio menülerinin | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- visual studio menus
- visual studio groups
- id
- existing menus
- guid
- menus
ms.assetid: 84639d86-dd21-4b35-9988-6bb654162488
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 1b7c8af93604a7e8e33d7d21d26b85c59985b878
ms.sourcegitcommit: 1c2ed640512ba613b3bbbc9ce348e28be6ca3e45
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/03/2018
ms.locfileid: "39499945"
---
# <a name="guids-and-ids-of-visual-studio-menus"></a>GUID'leri ve kimlikleri, Visual Studio menü
Bu makalede, menüler ve gruplar Visual Studio menü çubuğunda GUID ve ID değerlerini numaralandırır. Bu değerleri tanımlanan *.vsct* Visual Studio SDK'ın bir parçası olarak yüklenen dosyalar. Daha fazla bilgi için [IDE tanımlı komutlar, menüler ve gruplar](../../extensibility/internals/ide-defined-commands-menus-and-groups.md).  
  
 Tümleşik geliştirme ortamı (IDE) tanımlanan bir nesneler ile çalışma hakkında daha fazla bilgi için *.vsct* dosyaları görmek [genişletmek menüler ve komutlar](../../extensibility/extending-menus-and-commands.md).  
  
 Menüler ve gruplar Visual Studio menü çubuğunda, GUID'yi kullanın `guidSHLMainMenu`. Menü çubuğundaki Kimliğine sahip `IDM_VS_TOOL_MAINMENU`.  
  
## <a name="groups-on-the-visual-studio-menu-bar"></a>Visual Studio menü çubuğunda grupları  
 Menü çubuğuna menü eklemek için bu gruplardan birini kendi üst öğesi olarak ayarlayın.  
  
|Grup|Kimlik|  
|-----------|--------|  
|Dosya/düzenleme/görüntüleme|IDG_VS_MM_FILEEDITVIEW|  
|Yeniden Düzenle|IDG_VS_MM_REFACTORING:|  
|Proje|IDG_VS_MM_PROJECT|  
|Derleme|IDG_VS_MM_BUILDDEBUGRUN|  
|Biçim/Tools|IDG_VS_MM_TOOLSADDINS|  
|Pencere ve Yardım/Community|IDG_VS_MM_WINDOWHELP|  
|Eklentileri|IDG_VS_MM_MACROS|  
|FullScreenBar|IDG_VS_MM_FULLSCREENBAR|  
  
## <a name="menus-on-the-visual-studio-menu-bar"></a>Visual Studio menü çubuğundaki menüleri  
 Varolan bir Visual Studio menüsüne bir grup eklemek için aşağıdaki menülerden birini kendi üst öğesi olarak ayarlayın. Alt menüler bu listede yer almaz.  
  
|Menü|Kimlik|  
|----------|--------|  
|Dosya|IDM_VS_MENU_FILE|  
|Düzenle|IDM_VS_MENU_EDIT|  
|Görüntüle|IDM_VS_MENU_VIEW|  
|Yeniden Düzenleme (Refactor)|IDM_VS_MENU_REFACTORING|  
|Proje|IDM_VS_MENU_PROJECT|  
|Derleme|IDM_VS_MENU_BUILD|  
|Biçimi|IDM_VS_MENU_FORMAT|  
|Araçlar|IDM_VS_MENU_TOOLS|  
|Pencere|IDM_VS_MENU_WINDOW|  
|Eklentileri|IDM_VS_MENU_ADDINS|  
|Topluluk|IDM_VS_MENU_COMMUNITY|  
|Yardım|IDM_VS_MENU_HELP|  
  
## <a name="groups-on-visual-studio-menus"></a>Visual Studio menü grupları  
 Aşağıdaki listelerde, Visual Studio menü çubuğundaki menüleri doğrudan Düzen grupları gösterilir. En hızlı yolu, Visual Studio menüsüne komut ekleme, bu grupların bir üst öğe olarak ayarlamaktır. Alt düzen gruplarını, bu bölümde görünmez.  
  
### <a name="file-menu-groups"></a>Dosya menü grupları  
  
|Grup|Kimlik|  
|-----------|--------|  
|Yeni/Aç|IDG_VS_FILE_FILE|  
|Ekle|IDG_VS_FILE_ADD|  
|Çözüm|IDG_VS_FILE_SOLUTION|  
|Çeşitli|IDG_VS_FILE_MISC|  
|Kaydet|IDG_VS_FILE_SAVE|  
|Rename|IDG_VS_FILE_RENAME|  
|Tarayıcı|IDG_VS_FILE_BROWSER|  
|Yazdırma|IDG_VS_FILE_PRINT|  
|En son kullanılan|IDG_VS_FILE_MRU|  
|Taşıma|IDG_VS_FILE_MOVE|  
|Çık|IDG_VS_FILE_EXIT|  
  
### <a name="edit-menu-groups"></a>Menü grupları Düzenle  
  
|Grup|Kimlik|  
|-----------|--------|  
|Geri Al/Yinele|IDG_VS_EDIT_UNDOREDO|  
|Kes/kopyala/yapıştır|IDG_VS_EDIT_CUTCOPY|  
|Seçim|IDG_VS_EDIT_SELECT|  
|Git|IDG_VS_EDIT_GOTO|  
|Bul|IDG_VS_EDIT_FIND|  
|Nesneler|IDG_VS_EDIT_OBJECTS|  
|OLE fiilleri|IDG_VS_EDIT_OLEVERBS|  
|Komut kutusu|IDG_VS_EDIT_COMMANDWELL|  
  
### <a name="refactor-menu-groups"></a>Menü grupları yeniden düzenleyin  
  
|Grup|Kimlik|  
|-----------|--------|  
|Ortak|IDG_REFACTORING_COMMON|  
|Gelişmiş|IDG_REFACTORING_ADVANCED|  
  
### <a name="view-menu-groups"></a>Menü grupları görüntüleyin  
  
|Grup|Kimlik|  
|-----------|--------|  
|Form kodu|IDG_VS_VIEW_FORMCODE|  
|Tarayıcı|IDG_VS_VIEW_BROWSER|  
|Görünüm tanımlama|IDG_VS_VIEW_DEFINEVIEWS|  
|Windows|IDG_VS_VIEW_WINDOWS|  
|Windows Mimar|IDG_VS_VIEW_ARCH_WINDOWS|  
|Kuruluş Windows|IDG_VS_VIEW_ORG_WINDOWS|  
|Kod tarayıcı|IDG_VS_VIEW_CODEBROWSENAV_WINDOWS|  
|Windows geliştirme|IDG_VS_VIEW_DEV_WINDOWS|  
|Araç Çubukları|IDG_VS_VIEW_TOOLBARS|  
|Simgeleri|IDG_VS_VIEW_SYMBOLNAVIGATE|  
|Gidin|IDG_VS_VIEW_NAVIGATE|  
|Küçük gidin|IDG_VS_VIEW_SMALLNAVIGATE|  
|Nesne Tarayıcısı|IDG_VS_VIEW_OBJBRWSR|  
|Komut kutusu|IDG_VS_VIEW_COMMANDWELL|  
|Özellik Sayfaları|IDG_VS_VIEW_PROPPAGES|  
|Yenile|IDG_VS_VIEW_REFRESH|  
  
### <a name="project-menu-groups"></a>Proje menü grupları  
  
|Grup|Kimlik|  
|-----------|--------|  
|Çeşitli Ekle|IDG_VS_PROJ_MISCADD|  
|Ekle|IDG_VS_PROJ_ADD|  
|Klasör|IDG_VS_PROJ_FOLDER|  
|Kaldırma/yeniden yükleme|IDG_VS_PROJ_UNLOADRELOAD|  
|Başvuru|IDG_VS_PROJ_REFERENCE|  
|Seçenekler|IDG_VS_PROJ_OPTIONS|  
|Ayarlar|IDG_VS_PROJ_SETTINGS|  
  
### <a name="build-menu-groups"></a>Menü grupları oluşturun  
  
|Grup|Kimlik|  
|-----------|--------|  
|Çözüm|IDG_VS_BUILD_SOLUTION|  
|Seçim|IDG_VS_BUILD_SELECTION|  
|Profil Temelli İyileştirme|IDG_VS_PGO_SELECTION|  
|Çeşitli|IDG_VS_BUILD_MISC|  
|İptal|IDG_VS_BUILD_CANCEL|  
  
### <a name="tools-menu-groups"></a>Araçlar menü grupları  
  
|Grup|Kimlik|  
|-----------|--------|  
|Komut satırı|IDG_VS_TOOLS_CMDLINE|  
|Kod parçacıkları|IDG_VS_TOOLS_SNIPPETS|  
|Nesne alt|IDG_VS_TOOLS_OBJSUBSET|  
|Seçenekler|IDG_VS_TOOLS_OPTIONS|  
|Diğer 2|IDG_VS_TOOLS_OTHER2|  
|Dış Araçlar|IDG_VS_TOOLS_EXT_TOOLS|  
|Dış özelleştirmeleri|IDG_VS_TOOLS_EXT_CUST|  
  
### <a name="window-menu-groups"></a>Pencere menü grupları  
  
|Grup|Kimlik|  
|-----------|--------|  
|Yeni|IDG_VS_WINDOW_NEW|  
|Dock/Kapat|IDG_VS_DOCKCLOSE|  
|Dock/Gizle|IDG_VS_DOCKHIDE|  
|Düzenleme|IDG_VS_WINDOW_ARRANGE|  
|Gezinti|IDG_VS_WINDOW_NAVIGATION|  
|List|IDG_VS_WINDOW_LIST|  
  
### <a name="help-menu-groups"></a>Yardım menü grupları  
  
|Grup|Kimlik|  
|-----------|--------|  
|Örnekler|IDG_VS_HELP_SAMPLES|  
|Destek|IDG_VS_HELP_SUPPORT|  
|Hakkında|IDG_VS_HELP_ABOUT|  
  
## <a name="submenus-of-visual-studio-menus"></a>Visual Studio menülerinin alt menüler  
 Aşağıdaki hiyerarşi, Visual Studio menü çubuğundaki menüleri ile ilişkili alt menüler gösterir. Yalnızca bir grubu kendi üst menü olabileceğinden, her alt gruptan menüde yerine doğrudan menüsünden Düzen gerekir. Menüleri, gruplar ve alt menülerini arasındaki ilişki hakkında daha fazla bilgi için bkz. [menüye alt menü ekleme](../../extensibility/adding-a-submenu-to-a-menu.md).  
  
> [!NOTE]
>  Bunlar IDE içindeki gruplar için adlandırma kuralı şu şekilde olayla çünkü Visual Studio menü çubuğundaki menüleri adlarını bu hiyerarşide ayrı olarak gösterilmez: *IDG_VS_\<menüsü adı\>_\< Grup adı\>*.  
  
|Üst grup|Alt menü|Alt gruplar|  
|------------------|-------------|------------------|  
|IDG_VS_FILE_FILE|IDM_VS_CSCD_NEW|IDG_VS_FILE_NEW_CASCADE|  
||IDM_VS_CSCD_OPEN|IDG_VS_FILE_OPENP_CASCADE|  
|||IDG_VS_FILE_OPENF_CASCADE|  
|IDG_VS_FILE_ADD|IDM_VS_CSCD_ADD|IDG_VS_FILE_ADD_PROJECT_NEW|  
|||IDG_VS_FILE_ADD_PROJECT_EXI|  
|IDG_VS_FILE_MRU|IDM_VS_CSCD_FILEMRU|IDG_VS_FILE_FMRU_CASCADE|  
||IDM_VS_CSCD_PROJMRU|IDG_VS_FILE_PMRU_CASCADE|  
|IDG_VS_FILE_MOVE|IDM_VS_CSCD_MOVETOPRJ|IDG_VS_FILE_MOVE_CASCADE|  
|||IDG_VS_FILE_MOVE_PICKER|  
|IDG_VS_VIEW_DEV_WINDOWS|IDM_VS_CSCD_FINDRESULTS|IDG_VS_WNDO_FINDRESULTS|  
||IDM_VS_CSCD_WINDOWS|IDG_VS_VIEW_CALLBROWSER|  
|||IDG_VS_WNDO_OTRWNDWS1... 6|  
|||IDG_VS_WNDO_WINDOWS2|  
|IDG_VS_VIEW_TOOLBARS|IDM_VS_CSCD_COMMANDBARS||  
|IDG_VS_EDIT_GOTO|IDM_VS_EDITOR_FIND_MENU||  
|IDG_VS_EDIT_OBJECTS|IDM_VS_CSCD_MNUDES|IDG_VS_MNUDES_INSERT|  
|||IDG_VS_MNUDES_EDITNAMES|  
||IDM_VS_CSCD_OLEVERBS|IDG_VS_EDIT_OLEVERBS|  
|IDG_VS_BUILD_SELECTION|IDM_VS_CSCD_BUILD|IDG_VS_BUILD_CASCADE|  
|||IDG_VS_BUILD_PROJPICKER|  
||IDM_VS_CSCD_REBUILD|IDG_VS_REBUILD_CASCADE|  
|||IDG_VS_REBUILD_PROJPICKER|  
||IDM_VS_CSCD_PROJONLY|IDG_VS_PROJONLY_CASCADE|  
||IDM_VS_CSCD_CLEAN|IDG_VS_CLEAN_CASCADE|  
|||IDG_VS_CLEAN_PROJPICKER|  
||IDM_VS_CSCD_DEPLOY|IDG_VS_DEPLOY_CASCADE|  
|||IDG_VS_DEPLOY_PROJPICKER|  
|IDG_VS_PGO_SELECTION|IDM_VS_CSCD_PGO_BUILD|IDG_VS_PGO_BUILD_CASCADE_BUILD|  
|||IDG_VS_PGO_BUILD_CASCADE_RUN|  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [GUID'leri ve kimlikleri, Visual Studio araç çubukları](../../extensibility/internals/guids-and-ids-of-visual-studio-toolbars.md)   
 [GUID'leri ve kimlikleri, Visual Studio komutları](../../extensibility/internals/guids-and-ids-of-visual-studio-commands.md)   
 [Visual Studio komut tablosu (.vsct) dosyaları](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)