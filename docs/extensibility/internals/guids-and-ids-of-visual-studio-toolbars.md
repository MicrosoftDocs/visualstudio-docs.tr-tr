---
title: GUID'leri ve kimlikleri Visual Studio araç çubuklarının | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- visual studio groups
- toolbars
- visual studio toolbar
- id
- toolgar group
- tool window toolbar
- guid
ms.assetid: c9cacd57-9225-450f-a9ac-cbf3168ea844
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 6982835b9d3b6259a47439dbe7b1b9252edc3dbe
ms.sourcegitcommit: 1c2ed640512ba613b3bbbc9ce348e28be6ca3e45
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/03/2018
ms.locfileid: "39499012"
---
# <a name="guids-and-ids-of-visual-studio-toolbars"></a>GUID'leri ve kimlikleri, Visual Studio araç çubukları
Bu konu Visual Studio tümleşik geliştirme ortamında (IDE) dahil edilen araç çubuklarını GUID ve ID değerlerini numaralandırır ve gruplarını içerir. Bu değerleri tanımlanan *.vsct* Visual Studio SDK'ın bir parçası olarak yüklenen dosyalar. Daha fazla bilgi için [IDE tanımlı komutlar, menüler ve gruplar](../../extensibility/internals/ide-defined-commands-menus-and-groups.md).  
  
> [!NOTE]
>  Birçok Visual Studio için kullanılabilir araç çubukları Visual Studio ve GUID tanımlanmaz ve kimlik değerleri ortak değildir. Bu konu Visual Studio SDK'da tanımlanan araç çubukları listeler *.vsct* dosyaları.  
  
 Tanımlanan IDE nesneler ile çalışma hakkında daha fazla bilgi için *.vsct* dosyaları görmek [genişletmek menüler ve komutlar](../../extensibility/extending-menus-and-commands.md).  
  
 Visual Studio IDE tarafından sağlanan varsayılan araç çubukları GUID'yi kullanın `guidSHLMainMenu`, aksi takdirde kullanılarak belirtilen belirtilmediği `GUID:ID` söz dizimi.  
  
## <a name="ide-toolbars"></a>IDE araç çubukları  
 Aşağıdaki araç çubuklarını, Visual Studio IDE tarafından sağlanır. Üzerinde seçerek araç çubukları görüntülenebilir **araç çubukları** alt **Araçları** menüsü. Bu bölümdeki araç pencerelerini, araç çubukları dahil edilmez.  
  
 Yalnızca grupların doğrudan araç düzen. Bir grup eklemek için üst GUID ve araç Kimliğini ayarlayın. Bir araç çubuğuna bir düğme eklemek için üst araç çubuğunda bir gruba ayarlayın.  
  
|Araç Çubuğu|Kimlik|  
|-------------|--------|  
|Standart|IDM_VS_TOOL_STANDARD|  
|Derleme|IDM_VS_TOOL_BUILD|  
|Metin Düzenleyici|IDM_VS_TOOL_TEXTEDITOR|  
|Hata ayıklama|guidVSDebugGroup:IDM_DEBUG_TOOLBAR|  
|Hata ayıklama konumu|guidVSDebugGroup:IDM_DEBUG_CONTEXT_TOOLBAR|  
  
### <a name="special-toolbars"></a>Özel araç çubukları  
 Bu araç çubukları Visual Studio IDE tarafından tanımlandı, ancak özel işlevler sunmak ve komut gruplarını barındırmamalıdır.  
  
|Araç Çubuğu|Kimlik|  
|-------------|--------|  
|Add komutu|IDM_VS_TOOL_ADDCOMMAND|  
|Tanımsız|IDM_VS_TOOL_UNDEFINED|  
|XML Şeması|IDM_VS_TOOL_SCHEMA|  
|XML verileri|IDM_VS_TOOL_DATA|  
  
## <a name="groups-on-the-ide-toolbars"></a>IDE çubuklarına grupları  
 Bir standart araç çubuğuna bir düğme eklemek için aşağıdaki gruplardan birine kendi üst öğesi olarak ayarlayın. Gruplar, üst araç tarafından sıralanır.  
  
### <a name="standard-toolbar-groups"></a>Standart araç çubuğu grupları  
  
|Ad|Kimlik|  
|----------|--------|  
|Kaydetme/Aç|IDG_VS_TOOLSB_SAVEOPEN|  
|Kes/Kopyala|IDG_VS_TOOLSB_CUTCOPY|  
|Geri Al/Yinele|IDG_VS_TOOLSB_UNDOREDO|  
|Çalıştır/derleme|IDG_VS_TOOLSB_RUNBUILD|  
|Ara|IDG_VS_TOOLSB_SEARCH|  
|Windows|IDG_VS_TOOLSB_WINDOWS|  
|Yeni Pencere|IDG_VS_TOOLSB_NEWWINDOWS|  
|Yükleme/kaydetme|IDG_VS_WINDOWUI_LOADSAVE|  
|Ölçer|IDG_VS_TOOLSB_GAUGE|  
  
### <a name="build-toolbar-groups"></a>Araç çubuğu grupları oluşturun  
  
|Ad|Kimlik|  
|----------|--------|  
|Derleme çubuğu|IDG_VS_BUILDBAR|  
|İptal|IDG_VS_BUILD_CANCEL|  
  
### <a name="text-editor-toolbar-groups"></a>Metin Düzenleyicisi araç çubuğu grupları  
  
|Ad|Kimlik|  
|----------|--------|  
|Tamamlama|IDM_VS_TOOL_TEXTEDITOR|  
|Girintile|IDG_VS_EDITTOOLBAR_INDENT|  
|Yorum|IDG_VS_EDITTOOLBAR_COMMENT|  
|Yer işaretleri|IDG_VS_EDITTOOLBAR_TEMPBOOKMARKS|  
  
### <a name="debug-toolbar-groups"></a>Hata ayıklama araç çubuğu grupları  
  
|Ad|Kimlik|  
|----------|--------|  
|Yürütme|IDM_DEBUG_TOOLBAR|  
|Adımlama|IDG_DEBUG_TOOLBAR_STEPPING|  
|İzleme|IDG_DEBUG_TOOLBAR_WATCH|  
|Windows|IDG_DEBUG_TOOLBAR_WINDOWS|  
  
### <a name="debug-location-toolbar-groups"></a>Hata ayıklama konumu araç çubuğu grupları  
  
|Ad|Kimlik|  
|----------|--------|  
|Hata ayıklama konumu|IDG_DEBUG_CONTEXT_TOOLBAR|  
  
## <a name="tool-window-toolbars"></a>Araç penceresi araç çubukları  
 Araç çubukları görüntülenebilir doğrudan IDE'de veya araç pencereleri gibi **Çözüm Gezgini**. Araç pencereleri içinde tanımlı değil çünkü *.vsct* dosyaları, araç penceresi araç çubukları sahip tanımlanmamış üst öğeleri. Bunun yerine, bunlar kodu yerleştirilir. Aşağıdaki tabloda, araç pencerelerini IDE içinde görünen araç çubuklarını ve içerdikleri komut gruplarını gösterir.  
  
> [!NOTE]
>  Araç çubukları ve grupları kullanma GUID `guidSHLMainMenu`, GUID:ID sözdizimi kullanılarak aksi belirtilmedikçe burada hariç. Araç için bir GUID belirtilmedikçe, bu araç çubuğundan Düzen grupları için de geçerlidir.  
  
|Araç penceresi|Araç Çubuğu|Gruplar|  
|-----------------|-------------|------------|  
|Çözüm Gezgini|IDM_VS_TOOL_PROJWIN|IDG_VS_PROJ_TOOLBAR1... 5|  
|Server Explorer|guid_SE_MenuGroup:IDM_SE_TOOLBAR_SERVEREXPLORER|IDG_SE_TOOLBAR_REFRESH|  
|Özellikler|IDM_VS_TOOL_PROPERTIES|IDG_VS_PROPERTIES_SORT<br /><br /> IDG_VS_PROPERTIES_PAGES|  
|Sınıf Görünümü|IDM_VS_TOOL_CLASSVIEW|IDG_VS_CLASSVIEW_FOLDERS<br /><br /> IDG_VS_CLASSVIEW_SEARCH<br /><br /> IDG_VS_CLASSVIEW_SETTINGS|  
|Sınıf Görünümü|IDM_VS_TOOL_CLASSVIEW_GO|IDG_VS_CLASSVIEW_SEARCH2|  
|Nesne Tarayıcısı|IDM_VS_TOOL_OBJBROWSER|IDG_VS_OBJBROWSER_SUBSETS<br /><br /> IDG_VS_OBJBROWSER_SEARCH<br /><br /> IDG_VS_OBJBROWSER_ADDREFERENCE<br /><br /> IDG_VS_OBJBROWSER_BROWSERSETTINGS|  
|Nesne Tarayıcısı|IDM_VS_TOOL_OBJECT_BROWSER_GO|IDG_VS_OBJBROWSER_SEARCH2|  
|Çıkış|IDM_VS_TOOL_OUTPUTWINDOW|IDG_VS_OUTPUTWINDOW_SELECT<br /><br /> IDG_VS_OUTPUTWINDOW_GOTO<br /><br /> IDG_VS_OUTPUTWINDOW_NEXTPREV<br /><br /> IDG_VS_OUTPUTWINDOW_CLEAR<br /><br /> IDG_VS_OUTPUTWINDOW_WORDWRAP|  
|Bulma ve Değiştirme|IDM_VS_TOOL_UNIFIEDFIND|IDG_VS_FINDTAB<br /><br /> IDG_VS_REPLACETAB|  
|Sonuçları Bul 1|IDM_VS_TOOL_FINDRESULTS1|IDG_VS_FINDRESULTS1_GOTO<br /><br /> IDG_VS_FINDRESULTS1_NEXTPREV<br /><br /> IDG_VS_FINDRESULTS1_CLEAR<br /><br /> IDG_VS_FINDRESULTS1_STOPFIND|  
|Sonuçları Bul 2|IDM_VS_TOOL_FINDRESULTS2|IDG_VS_FINDRESULTS2_GOTO<br /><br /> IDG_VS_FINDRESULTS2_NEXTPREV<br /><br /> IDG_VS_FINDRESULTS2_CLEAR<br /><br /> IDG_VS_FINDRESULTS2_STOPFIND|  
|Kod parçacığı|IDM_VS_TOOL_SNIPPETMENUS|IDG_VS_SNIPPET_REPL<br /><br /> IDG_VS_SNIPPET_REF<br /><br /> IDG_VS_SNIPPET_PROP|  
|Yer işaretleri|IDM_VS_TOOL_BOOKMARKWIND|IDG_VS_BWNEWFOLDER<br /><br /> IDG_VS_BWNEXTBM<br /><br /> IDG_VS_BWNEXTBMF<br /><br /> IDG_VS_BWENABLE<br /><br /> IDG_VS_BWDELETE|  
|Görev Listesi|IDM_VS_TOOL_TASKLIST|IDG_VS_TASKLIST_PROVIDERLIST|  
|Kullanıcı görevleri|IDM_VS_TOOL_USERTASKS|IDG_VS_TASKLIST_PROVIDERLIST<br /><br /> IDG_VS_USERTASKS_EDIT|  
|Hata Listesi|IDM_VS_TOOL_ERRORLIST|IDG_VS_ERRORLIST_ERRORGROUP<br /><br /> IDG_VS_ERRORLIST_WARNINGGROUP<br /><br /> IDG_VS_ERRORLIST_MESSAGEGROUP|  
|Çağrı tarayıcısı|IDM_VS_TOOL_CALLBROWSER1... 16|IDG_VS_TOOLBAR_CALLBROWSER1_ACTIONS<br /><br /> IDG_VS_TOOLBAR_CALLBROWSER1_TYPE<br /><br /> IDG_VS_TOOLBAR_CALLBROWSER1_CBSETTINGS|  
|Kesme noktaları|guidVSDebugGroup:IDM_BREAKPOINTS_WINDOW_TOOLBAR|IDG_BREAKPOINTS_WINDOW_NEW<br /><br /> IDG_BREAKPOINTS_WINDOW_DELETE<br /><br /> IDG_BREAKPOINTS_WINDOW_ALL<br /><br /> IDG_BREAKPOINTS_WINDOW_VIEW<br /><br /> IDG_BREAKPOINTS_WINDOW_EDIT<br /><br /> IDG_BREAKPOINTS_WINDOW_COLUMNS|  
|Ayrıştırılmış kodu|guidVSDebugGroup:IDM_DISASM_WINDOW_TOOLBAR|IDG_DISASM_WINDOW_TOOLBAR|  
|Bellek 1-4|guidVSDebugGroup:IDM_MEMORY_WINDOW_TOOLBAR1... 4|IDG_MEMORY_EXPRESSION1... 4<br /><br /> IDG_MEMORY_COLUMNS1... 4|  
|İşlemler|guidVSDebugGroup:IDM_ATTACHED_PROCS_TOOLBAR|IDG_ATTACHED_PROCS_EXECCNTRL IDG_ATTACHED_PROCS_STEPPING<br /><br /> IDG_ATTACHED_PROCS_EXECCNTRL2<br /><br /> IDG_ATTACHED_PROCS_ATTACH<br /><br /> IDG_ATTACHED_PROCS_COLUMNS|  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Araç çubuğuna menü denetleyicisi ekleme](../../extensibility/adding-a-menu-controller-to-a-toolbar.md)   
 [Araç penceresine araç çubuğu ekleme](../../extensibility/adding-a-toolbar-to-a-tool-window.md)   
 [GUID'leri ve kimlikleri, Visual Studio menü](../../extensibility/internals/guids-and-ids-of-visual-studio-menus.md)