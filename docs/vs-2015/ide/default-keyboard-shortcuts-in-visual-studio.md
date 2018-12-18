---
title: Varsayılan Klavye Kısayolları
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- shortcut keys [Visual Studio], keyboard binding schemes
- keyboard binding schemes [Visual Studio]
- Help [Visual Studio], shortcut keys
- keyboard shortcuts [Visual Studio], keyboard binding schemes
- keyboard shortcuts
ms.assetid: c2c64648-00f8-4e48-a8a0-96c67cfd968c
caps.latest.revision: 59
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: a1ea4c51f617d6128018ba23cbf564996cccf1a3
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53057264"
---
# <a name="default-keyboard-shortcuts-in-visual-studio"></a>Visual Studio'daki Klavye Kısayolları
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio'da uygun klavye kısayolunu kullanarak çeşitli komutlara ve pencerelere daha kolay erişim sağlayabilirsiniz. Bu konuda, Visual Studio'yu yüklerken tercih etmiş olabileceğiniz Genel Geliştirme profiline ilişkin varsayılan kısayollar listelenmektedir. Seçtiğiniz profilden bağımsız olarak açarak bir komutun kısayolunu belirleyebilirsiniz **seçenekleri** genişletme iletişim kutusu, **ortam** düğümünü ve ardından **klavye**. Ayrıca, verilen komutlardan herhangi birine farklı bir kısayol atayarak kısayollarınızı özelleştirebilirsiniz.

 Ortak klavye kısayollarının ve diğer üretkenlik bilgilerinin bir listesi için bkz. [ipuçları ve püf noktaları](../ide/tips-and-tricks-for-visual-studio.md) ve [üretkenlik ipuçları](../ide/productivity-tips-for-visual-studio.md).

 Aşağıdaki tablonun bölümlerinde, Visual Studio'nun her yerinden klavye kısayollarını kullanarak erişim sağlayabilmeniz bakımından genel kabul edilen komutlar yer almaktadır:

|||||
|-|-|-|-|
|[Analiz edin](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_analyze)|[Düzenle](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_edit)|[Project](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_project)|[Test](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_test)|
|[Mimari](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_architecture)|[Düzenleyici bağlam menüleri](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_editorContext)|[Proje ve çözüm bağlam menüleri](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_projectContext)|[Test Gezgini](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_testexplorerGLOBAL)|
|[Derleme](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_build)|[Dosya](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_file)|[Yeniden düzenleme](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_refactor)|[Araçlar](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_tools)|
|[Sınıf Görünümü Bağlam menüleri](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_classview)|[Yardım](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_help)|[Çözüm Gezgini](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_solutionexplorerGLOBAL)|[Görünümü](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_view)|
|[Hata ayıklama](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_debug)|[Yük testi](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_loadtest)|[Takım](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_team)|[Pencere](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_window)|
|[Hata ayıklayıcı bağlam menüleri](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_debugger)|[Diğer bağlam menüleri](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_otherContext)|[Team Foundation bağlam menüleri](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_TFcontext)|[Azure](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_windowsazure)|
|[Tanılama Merkezi](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_diagnostics)||||

 Aşağıdaki tablodaki her bölüm, klavye kısayollarının adı verilen bölümün bağlamına özgü olduğu komutları içermektedir.

|||||
|-|-|-|-|
|[ADO.NET varlık veri modeli Tasarımcısı](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_ADONET)|[Katman diyagramı](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_layerDiagram)|[Ayarlar Tasarımcısı](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_SettingsDesigner)|[VC görüntü Düzenleyicisi](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_vcimageeditor)|
|[Sınıf diyagramı](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_classDiagram)|[Yönetilen kaynaklar Düzenleyicisi](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_managedResources)|[Çözüm Gezgini](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_SolutionExplorer)|[VC Dize Düzenleyicisi](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_vcstringeditor)|
|[Kodlanmış UI Test Düzenleyicisi](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_codedUItest)|[Birleştirme Düzenleyicisi penceresi](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_MergeEditor)|[Takım Gezgini](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_TeamExplorer)|[Görünüm Tasarımcısı](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_viewDesigner)|
|[Veri kümesi Düzenleyicisi](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_dataset)|[Microsoft SQL Server veri araçları, Şema karşılaştırma](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_SchemaCompare)|[Team Foundation Yapı ayrıntı Düzenleyicisi](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_TFBuild)|[Visual Studio](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_visualstudio)|
|[Fark Görüntüleyicisi](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_diff)|[Microsoft SQL Server veri araçları, Tablo Tasarımcısı](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_TableDesigner)|[Test Gezgini](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_TestExplorer)|[Windows Form Tasarımcısı](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_wfdesigner)|
|[DOM Gezgini](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_DOM)|[Microsoft SQL Server veri araçları, T-SQL Düzenleyicisi](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_TSQLeditor)|[Metin Düzenleyici](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_TextEditor)|[Çalışma öğesi Düzenleyicisi](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_workItemEditor)|
|[F# Interactive](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_FSharp)|[Microsoft SQL Server veri araçları, T-SQL PDW Düzenleyicisi](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_linkfix)|[UML etkinlik diyagramı](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_UMLactivityDiagram)|[Çalışma öğesi sorgu görünümü](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_WIqueryview)|
|[Graf belgesi Düzenleyicisi](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_graphDoc)|[Sayfa denetçisi](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_PageInspector)|[UML sınıf diyagramı](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_UMLclassDiagram)|[Çalışma öğesi Sonuçlar Görünümü](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_WIresultsview)|
|[Grafik tanılama](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_graphicsDebugger)|[Sorgu Tasarımcısı](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_QueryDesigner)|[UML bileşen diyagramı](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_UMLcomponentDiagram)|[İş Akışı Tasarımcısı](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_workflowdesigner)|
|[HTML düzenleyicisi](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_HTMLeditor)|[Sorgu Sonuçları](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_QueryResults)|[UML Kullanım durumu diyagramı](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_UMLusecaseDiagram)|[XAML Tasarımcısı](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_xamluidesigner)|
|[HTML düzenleyicisi Tasarım görünümü](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_HTMLeditorDesign)|[Rapor Tasarımcısı](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_ReportDesigner)|[VC Hızlandırıcı Düzenleyicisi](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_vcaccelerator)|[XML (metin) Düzenleyicisi](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_xmlTextEditor)|
|[HTML düzenleyicisi kaynak görünümü](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_HTMLeditorSource)|[Sıralı diyagram](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_SequenceDiagram)|[VC iletişim kutusu Düzenleyicisi](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_vcdialogeditor)|[XML Şema Tasarımcısı](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_xmlSchemaDesigner)|

##  <a name="bkmk_global"></a> Genel

###  <a name="bkmk_analyze"></a> Analiz edin

|Komutlar|Klavye Kısayolları|
|--------------|------------------------|
|Analyze.NavigateBackward|Shift+Alt+3|
|Analyze.NavigateForward|Shift+Alt+4|

###  <a name="bkmk_architecture"></a> Mimarisi

|Komutlar|Klavye Kısayolları|
|--------------|------------------------|
|Architecture.NewDiagram|CTRL +\\, Ctrl + N|

###  <a name="bkmk_build"></a> Derleme

|Komutlar|Klavye Kısayolları|
|--------------|------------------------|
|Build.BuildSolution|Ctrl+Shift+B|
|Build.Cancel|Ctrl+Break tuşu|
|Build.Compile|Ctrl+F7|
|Build.RunCodeAnalysisonSolution|Alt+F11|

###  <a name="bkmk_classview"></a> Sınıf Görünümü Bağlam menüleri

|Komutlar|Klavye Kısayolları|
|--------------|------------------------|
|ClassViewContextMenus.ClassViewMultiselectProjectreferencesItems.Properties|Alt+Enter|

###  <a name="bkmk_debug"></a> Hata ayıklama

|Komutlar|Klavye Kısayolları|
|--------------|------------------------|
|Debug.ApplyCodeChanges|Alt+F10|
|Debug.Autos|Ctrl+Alt+V, A|
|Debug.BreakAll|Ctrl+Alt+Break tuşu|
|Debug.BreakatFunction|Ctrl+B|
|Debug.Breakpoints|Ctrl+Alt+B|
|Debug.CallStack|Ctrl+Alt+C|
|Debug.DeleteAllBreakpoints|Ctrl+Shift+F9|
|Debug.DiagnosticsHub.Launch|Alt+F2|
|Debug.Disassembly|Ctrl+Alt+D|
|Debug.DOMExplorer|Ctrl+Alt+V, D|
|Debug.EnableBreakpoint|Ctrl+F9|
|Debug.Exceptions|Ctrl+Alt+E|
|Debug.GoToPreviousCallorIntelliTraceEvent|Ctrl+Shift+F11|
|Debug.Graphics.StartDiagnostics|Alt+F5|
|Debug.Immediate|Ctrl+Alt+I|
|Debug.IntelliTraceCalls|Ctrl+Alt+Y, T|
|Debug.IntelliTraceEvents|Ctrl+Alt+Y, F|
|Debug.JavaScriptConsole|Ctrl+Alt+V, C|
|Debug.Locals|Ctrl+Alt+V, L|
|Debug.LocationToolbar.ProcessCombo|Ctrl+5|
|Debug.LocationToolbar.StackFrameCombo|Ctrl+7|
|Debug.LocationToolbar.ThreadCombo|Ctrl+6|
|Debug.LocationToolbar.ToggleCurrentThreadFlaggedState|Ctrl+8|
|Debug.LocationToolbar.ToggleFlaggedThreads|Ctrl+9|
|Debug.Memory1|Ctrl+Alt+M, 1|
|Debug.Memory2|Ctrl + Alt + M, 2|
|Debug.Memory3|Ctrl + Alt + M, 3|
|Debug.Memory4|Ctrl + Alt + M, 4|
|Debug.Modules|Ctrl+Alt+U|
|Debug.ParallelStacks|Ctrl+Shift+D, S|
|Debug.ParallelWatch1|Ctrl+Shift+D, 1|
|Debug.ParallelWatch2|CTRL + SHIFT + D, 2|
|Debug.ParallelWatch3|CTRL + SHIFT + D, 3|
|Debug.ParallelWatch4|CTRL + SHIFT + D, 4|
|Debug.Processes|Ctrl+Alt+Z|
|Debug.QuickWatch|Shift+F9<br /><br /> veya<br /><br /> Ctrl+Alt+Q|
|Debug.RefreshWindowsapp|Ctrl+Shift+R|
|Debug.Registers|Ctrl+Alt+G|
|Debug.Restart|Ctrl+Shift+F5|
|Debug.RunToCursor|Ctrl+F10|
|Debug.SetNextStatement|Ctrl+Shift+F10|
|Debug.ShowCallStackonCodeMap|Ctrl+Shift+`|
|Debug.ShowNextStatement|Alt+Num *|
|Debug.Start|F5|
|Debug.StartWindowsPhoneApplicationAnalysis|Alt+F1|
|Debug.StartWithoutDebugging|Ctrl+F5|
|Debug.StepInto|F11|
|Debug.StepIntoCurrentProcess|Ctrl+Alt+F11|
|Debug.StepIntoSpecific|Shift+Alt+F11|
|Debug.StepOut|Shift+F11|
|Debug.StepOutCurrentProcess|Ctrl+Shift+Alt+F11|
|Debug.StepOver|F10|
|Debug.StepOverCurrentProcess|Ctrl+Alt+F10|
|Debug.StopDebugging|Shift+F5|
|Debug.StopPerformanceAnalysis|Shift+Alt+F2|
|Debug.Tasks|Ctrl+Shift+D, K|
|Debug.Threads|Ctrl+Alt+H|
|Debug.ToggleBreakpoint|F9|
|Debug.ToggleDisassembly|Ctrl+F11|
|Debug.Watch1|Ctrl+Alt+W, 1|
|Debug.Watch2|Ctrl + Alt + W, 2|
|Debug.Watch3|Ctrl + Alt + W, 3|
|Debug.Watch4|Ctrl + Alt + W, 4|

###  <a name="bkmk_debugger"></a> Hata ayıklayıcı bağlam menüleri

|Komutlar|Klavye Kısayolları|
|--------------|------------------------|
|DebuggerContextMenus.BreakpointsWindow.Delete|Alt+F9, D|
|DebuggerContextMenus.BreakpointsWindow.GoToDisassembly|Alt+F9, A|
|DebuggerContextMenus.BreakpointsWindow.GoToSourceCode|Alt+F9, S|

###  <a name="bkmk_diagnostics"></a> Tanılama Merkezi

|Komut|Klavye Kısayolu|
|-------------|-----------------------|
|DiagnosticsHub.StopCollection|Ctrl+Alt+F2|

###  <a name="bkmk_edit"></a> Düzenle

|Komutlar||
|--------------|-|
|Edit.Copy|Ctrl+C<br /><br /> veya<br /><br /> Ctrl+Ins|
|Edit.Cut|Ctrl+X<br /><br /> veya<br /><br /> Shift+Delete|
|Edit.CycleClipboardRing|Ctrl+Shift+V<br /><br /> veya<br /><br /> Ctrl+Shift+Ins|
|Edit.Delete|Sil|
|Edit.Find|Ctrl+F|
|Edit.FindAllReferences|Shift+F12|
|Edit.FindinFiles|Ctrl+Shift+F|
|Edit.FindNext|F3|
|Edit.FindNextSelected|Ctrl+F3|
|Edit.FindPrevious|Shift+F3|
|Edit.FindPreviousSelected|Ctrl+Shift+F3|
|Edit.GenerateMethod|Ctrl+K, Ctrl+M|
|Edit.GoTo|Ctrl+G|
|Edit.GoToDeclaration|Ctrl+F12|
|Edit.GoToDefinition|F12|
|Edit.GoToFindCombo|Ctrl+D|
|Edit.GoToNextLocation|F8|
|Edit.GoToPrevLocation|Shift+F8|
|Edit.InsertSnippet|Ctrl+K, Ctrl+X|
|Edit.MoveControlDown|Ctrl+Aşağı Ok|
|Edit.MoveControlDownGrid|Aşağı Ok|
|Edit.MoveControlLeft|Ctrl+Sol Ok|
|Edit.MoveControlLeftGrid|Sol Ok|
|Edit.MoveControlRight|Ctrl+Sağ Ok|
|Edit.MoveControlRightGrid|Sağ Ok|
|Edit.MoveControlUp|Ctrl+Yukarı Ok|
|Edit.MoveControlUpGrid|Yukarı Ok|
|Edit.NavigateTo|Ctrl+,|
|Edit.NextBookmark|Ctrl+K, Ctrl+N|
|Edit.NextBookmarkInFolder|Ctrl+Shift+K, Ctrl+Shift+N|
|Edit.OpenFile|Ctrl+Shift+G|
|Edit.Paste|Ctrl+V<br /><br /> veya<br /><br /> Shift+Ins|
|Edit.PreviousBookmark|Ctrl+K, Ctrl+P|
|Edit.PreviousBookmarkInFolder|Ctrl+Shift+K, Ctrl+Shift+P|
|Edit.QuickFindSymbol|Shift+Alt+F12|
|Edit.Redo|Ctrl+Y<br /><br /> veya<br /><br /> Ctrl+Shift+Z<br /><br /> veya<br /><br /> Shift+Alt+Geri Al tuşu|
|Edit.RefreshRemoteReferences|Ctrl+Shift+J|
|Edit.Replace|Ctrl+H|
|Edit.ReplaceinFiles|Ctrl+Shift+H|
|Edit.SelectAll|Ctrl+A|
|Edit.SelectNextControl|Tab|
|Edit.SelectPreviousControl|Shift+Sekme Tuşu|
|Edit.ShowTileGrid|Enter|
|Edit.SizeControlDown|Ctrl+Shift+Aşağı Ok|
|Edit.SizeControlDownGrid|Shift+Aşağı Ok|
|Edit.SizeControlLeft|Ctrl+Shift+Sol Ok|
|Edit.SizeControlLeftGrid|Shift+Sol Ok|
|Edit.SizeControlRight|Ctrl+Shift+Sağ Ok|
|Edit.SizeControlRightGrid|Shift+Sağ Ok|
|Edit.SizeControlUp|Ctrl+Shift+Yukarı Ok|
|Edit.SizeControlUpGrid|Shift+Yukarı Ok|
|Edit.StopSearch|Alt+F3, S|
|Edit.SurroundWith|Ctrl+K, Ctrl+S|
|Edit.Undo|Ctrl+Z<br /><br /> veya<br /><br /> Alt+Geri Al tuşu|

###  <a name="bkmk_editorContext"></a> Düzenleyici bağlam menüleri

|Komutlar|Klavye Kısayolları|
|--------------|------------------------|
|EditorContextMenus.CodeWindow.Breakpoint.BreakpointEditlabels|Alt+F9, L|
|EditorContextMenus.CodeWindow.CodeMap.ShowItem|Ctrl+`|
|EditorContextMenus.CodeWindow.Execute|Ctrl+Alt+F5|
|EditorContextMenus.CodeWindow.GoToView|Ctrl+M, Ctrl+G|
|EditorContextMenus.CodeWindow.ToggleHeaderCodeFile|Ctrl+K, Ctrl+O|
|EditorContextMenus.CodeWindow.ViewCallHierarchy|Ctrl+K, Ctrl+T<br /><br /> veya<br /><br /> Ctrl+K, T|

###  <a name="bkmk_file"></a> Dosya

|Komutlar|Klavye Kısayolları|
|--------------|------------------------|
|File.Exit|Alt+F4|
|File.NewFile|Ctrl+N|
|File.NewProject|Ctrl+Shift+N|
|File.NewWebSite|Shift+Alt+N|
|File.OpenFile|Ctrl+O|
|File.OpenProject|Ctrl+Shift+O|
|File.OpenWebSite|Shift+Alt+O|
|File.Print|Ctrl+P|
|File.SaveAll|Ctrl+Shift+S|
|File.SaveSelectedItems|Ctrl+S|
|File.ViewinBrowser|Ctrl+Shift+W|

###  <a name="bkmk_help"></a> Yardım

|Komutlar|Klavye Kısayolları|
|--------------|------------------------|
|Help.AddandRemoveHelpContent|Ctrl+Alt+F1|
|Help.F1Help|F1|
|Help.ViewHelp|Ctrl+F1|
|Help.WindowHelp|Shift+F1|

###  <a name="bkmk_loadtest"></a> Yük testi

|Komut|Klavye Kısayolu|
|-------------|-----------------------|
|LoadTest.JumpToCounterPane|Ctrl+R, Q|

###  <a name="bkmk_otherContext"></a> Diğer bağlam menüleri

|Komut|Klavye Kısayolu|
|-------------|-----------------------|
|OtherContextMenus.MicrosoftDataEntityDesignContext.AddNewDiagram|Ekleme|

###  <a name="bkmk_project"></a> Proje

|Komutlar|Klavye Kısayolları|
|--------------|------------------------|
|Project.AddExistingItem|Shift+Alt+A|
|Project.AddNewItem|Ctrl+Shift+A|
|Project.ClassWizard|Ctrl+Shift+X|
|Project.Override|Ctrl+Alt+Ins|
|Project.Previewchanges|Alt+;, Alt+C|
|Project.Publishselectedfiles|Alt+;, Alt+P|
|Project.Replaceselectedfilesfromserver|Alt+;, Alt+R|

###  <a name="bkmk_projectContext"></a> Proje ve çözüm bağlam menüleri

|Komutlar|Klavye Kısayolları|
|--------------|------------------------|
|ProjectandSolutionContextMenus.Item.MoveDown|Alt+Aşağı Ok|
|ProjectandSolutionContextMenus.Item.MoveUp|Alt+Yukarı Ok|

###  <a name="bkmk_refactor"></a> Yeniden düzenleme

|Komutlar|Klavye Kısayolları|
|--------------|------------------------|
|Refactor.EncapsulateField|Ctrl+R, Ctrl+E|
|Refactor.ExtractInterface|Ctrl+R, Ctrl+I|
|Refactor.ExtractMethod|Ctrl+R, Ctrl+M|
|Refactor.RemoveParameters|Ctrl+R, Ctrl+V|
|Refactor.Rename|Ctrl+R, Ctrl+R|
|Refactor.ReorderParameters|Ctrl+R, Ctrl+O|

###  <a name="bkmk_solutionexplorerGLOBAL"></a> Çözüm Gezgini

|Komutlar|Klavye Kısayolları|
|--------------|------------------------|
|SolutionExplorer.OpenFilesFilter|Ctrl+[, O<br /><br /> veya<br /><br /> Ctrl+[, Ctrl+O|
|SolutionExplorer.PendingChangesFilter|Ctrl+[, P<br /><br /> veya<br /><br /> Ctrl+[, Ctrl+P|
|SolutionExplorer.SyncWithActiveDocument|Ctrl+[, S<br /><br /> veya<br /><br /> Ctrl+[, Ctrl+S|

###  <a name="bkmk_team"></a> Takım

|Komutlar|Klavye Kısayolları|
|--------------|------------------------|
|Team.Git.GoToGitBranches|Ctrl+0, Ctrl+N<br /><br /> veya<br /><br /> Ctrl+0, N|
|Team.Git.GoToGitChanges|Ctrl+0, Ctrl+G<br /><br /> veya<br /><br /> Ctrl+0, G|
|Team.Git.GoToGitCommits|Ctrl+0, Ctrl+O<br /><br /> veya<br /><br /> Ctrl+0, O|
|Team.TeamExplorerSearch|Ctrl+'|

###  <a name="bkmk_TFcontext"></a> Team Foundation bağlam menüleri

|Komutlar|Klavye Kısayolları|
|--------------|------------------------|
|TeamFoundationContextMenus.Commands.GoToBuilds|Ctrl+0, Ctrl+B<br /><br /> veya<br /><br /> Ctrl+0, B|
|TeamFoundationContextMenus.Commands.GoToConnect|Ctrl+0, Ctrl+C<br /><br /> veya<br /><br /> Ctrl+0, C|
|TeamFoundationContextMenus.Commands.GoToDocuments|Ctrl+0, Ctrl+D<br /><br /> veya<br /><br /> Ctrl+0, D|
|TeamFoundationContextMenus.Commands.GoToHome|Ctrl+0, Ctrl+H<br /><br /> veya<br /><br /> Ctrl+0, H|
|TeamFoundationContextMenus.Commands.GoToMyWork|Ctrl+0, Ctrl+M<br /><br /> veya<br /><br /> Ctrl+0, M|
|TeamFoundationContextMenus.Commands.GoToPendingChanges|Ctrl+0, Ctrl+P<br /><br /> veya<br /><br /> Ctrl+0, P|
|TeamFoundationContextMenus.Commands.GoToReports|Ctrl+0, Ctrl+R<br /><br /> veya<br /><br /> Ctrl+0, R|
|TeamFoundationContextMenus.Commands.GoToSettings|Ctrl+0, Ctrl+S<br /><br /> veya<br /><br /> Ctrl+0, S|
|TeamFoundationContextMenus.Commands.GoToWebAccess|Ctrl+0, Ctrl+A<br /><br /> veya<br /><br /> Ctrl+0, A|
|TeamFoundationContextMenus.Commands.GoToWorkItems|Ctrl+0, Ctrl+W<br /><br /> veya<br /><br /> Ctrl+0, W|

###  <a name="bkmk_test"></a> Test

|Komutlar|Klavye Kısayolları|
|--------------|------------------------|
|Test.UseCodedUITestBuilder|Ctrl+\\, Ctrl+C|
|Test.UseExistingActionRecording|CTRL +\\, Ctrl + A|

###  <a name="bkmk_testexplorerGLOBAL"></a> Test Gezgini

|Komutlar|Klavye Kısayolları|
|--------------|------------------------|
|TestExplorer.DebugAllTests|Ctrl+R, Ctrl+A|
|TestExplorer.DebugAllTestsInContext|Ctrl+R, Ctrl+T|
|TestExplorer.RepeatLastRun|Ctrl+R, L|
|TestExplorer.RunAllTests|Ctrl+R, A|
|TestExplorer.RunAllTestsInContext|Ctrl+R, T|

###  <a name="bkmk_tools"></a> Araçları

|Komutlar|Klavye Kısayolları|
|--------------|------------------------|
|Tools.AttachtoProcess|Ctrl+Alt+P|
|Tools.CodeSnippetsManager|Ctrl+K, Ctrl+B|
|Tools.ForceGC|Ctrl+Shift+Alt+F12, Ctrl+Shift+Alt+F12|
|Tools.GoToCommandLine|Ctrl+/|

###  <a name="bkmk_view"></a> Görünümü

|Komutlar|Klavye Kısayolları|
|--------------|------------------------|
|View.AllWindows|Shift+Alt+M|
|View.ArchitectureExplorer|Ctrl+\\, Ctrl+R|
|View.Backward|Alt+Sol Ok|
|View.BookmarkWindow|Ctrl+K, Ctrl+W|
|View.BrowseNext|Ctrl+Shift+1|
|View.BrowsePrevious|Ctrl+Shift+2|
|View.CallHierarchy|Ctrl+Alt+K|
|View.ClassView|Ctrl+Shift+C|
|View.ClassViewGoToSearchCombo|Ctrl+K, Ctrl+V|
|View.CodeDefinitionWindow|CTRL +\\, D<br /><br /> veya<br /><br /> CTRL +\\, Ctrl + D|
|View.CommandWindow|Ctrl+Alt+A|
|View.DataSources|Shift+Alt+D|
|View.DocumentOutline|Ctrl+Alt+T|
|View.EditLabel|F2|
|View.ErrorList|CTRL +\\, E<br /><br /> veya<br /><br /> CTRL +\\, Ctrl + E|
|View.F#Interactive|Ctrl+Alt+F|
|View.FindSymbolResults|Ctrl+Alt+F12|
|View.Forward|Alt+Sağ Ok|
|View.ForwardBrowseContext|Ctrl+Shift+7|
|View.FullScreen|Shift+Alt+Enter|
|View.NavigateBackward|Ctrl+-|
|View.NavigateForward|Ctrl+Shift+-|
|View.NextError|Ctrl+Shift+F12|
|View.Notifications|Ctrl+W, N<br /><br /> veya<br /><br /> Ctrl+W, Ctrl+N|
|View.ObjectBrowser|Ctrl+Alt+J|
|View.ObjectBrowserGoToSearchCombo|Ctrl+K, Ctrl+R|
|View.Output|Ctrl+Alt+O|
|View.PopBrowseContex|Ctrl+Shift+8|
|View.PropertiesWindow|F4|
|View.PropertyPages|Shift+F4|
|View.ResourceView|Ctrl+Shift+E|
|View.ServerExplorer|Ctrl+Alt+S|
|View.ShowSmartTag|Shift+Alt+F10<br /><br /> veya<br /><br /> Ctrl+.|
|View.SolutionExplorer|Ctrl+Alt+L|
|View.SQLServerObjectExplorer|CTRL +\\, Ctrl + S|
|View.TaskList|CTRL +\\, T<br /><br /> veya<br /><br /> CTRL +\\, Ctrl + T|
|View.TfsTeamExplorer|CTRL +\\, Ctrl + M|
|View.Toolbox|Ctrl+Alt+X|
|View.UMLModelExplorer|CTRL +\\, Ctrl + U|
|View.ViewCode|F7|
|View.ViewDesigner|Shift+F7|
|View.WebBrowser|Ctrl+Alt+R|
|View.ZoomIn|Ctrl+Shift+.|
|View.ZoomOut|Ctrl+Shift+,|

###  <a name="bkmk_window"></a> Pencere

|Komutlar|Klavye Kısayolları|
|--------------|------------------------|
|Window.ActivateDocumentWindow|Esc|
|Window.AddTabtoSelection|Ctrl+Shift+Alt+Ara Çubuğu|
|Window.CloseDocumentWindow|Ctrl+F4|
|Window.CloseToolWindow|Shift+Esc|
|Window.KeepTabOpen|Ctrl+Alt+Home|
|Window.MovetoNavigationBar|Ctrl+F2|
|Window.NextDocumentWindow|Ctrl+F6|
|Window.NextDocumentWindowNav|Ctrl+Sekme|
|Window.NextPane|Alt+F6|
|Window.NextSplitPane|F6|
|Window.NextTab|Ctrl+Alt+PgDn<br /><br /> veya<br /><br /> Ctrl+PgDn|
|Window.NextTabandAddtoSelection|Ctrl+Shift+Alt+PgDn|
|Window.NextToolWindowNav|Alt+F7|
|Window.PreviousDocumentWindow|Ctrl+Shift+F6|
|Window.PreviousDocumentWindowNav|Ctrl+Shift+Sekme|
|Window.PreviousPane|Shift+Alt+F6|
|Window.PreviousSplitPane|Shift+F6|
|Window.PreviousTab|Ctrl+Alt+PgUp<br /><br /> veya<br /><br /> Ctrl+PgUp|
|Window.PreviousTabandAddtoSelection|Ctrl+Shift+Alt+PgUp|
|Window.PreviousToolWindowNav|Shift+Alt+F7|
|Window.QuickLaunch|Ctrl+Q|
|Window.QuickLaunchPreviousCategory|Ctrl+Shift+Q|
|Window.ShowDockMenu|Alt+-|
|Window.ShowEzMDIFileList|Ctrl+Alt+Aşağı Ok|
|Window.SolutionExplorerSearch|Ctrl+;|
|Window.WindowSearch|Alt+`|

###  <a name="bkmk_windowsazure"></a> Azure

|Komutlar|Klavye Kısayolları|
|--------------|------------------------|
|WindowsAzure.RetryMobileServiceScriptOperation|Ctrl+Num *, Ctrl+R|
|WindowsAzure.ShowMobileServiceScriptErrorDetails|Ctrl+Num *, Ctrl+D|

##  <a name="bkmk_ADONET"></a> ADO.NET varlık veri modeli Tasarımcısı

|Komutlar|Klavye Kısayolları|
|--------------|------------------------|
|OtherContextMenus.MicrosoftDataEntityDesignContext.MoveProperties.Down|Alt+Aşağı Ok|
|OtherContextMenus.MicrosoftDataEntityDesignContext.MoveProperties.Down5|Alt+PgDn|
|OtherContextMenus.MicrosoftDataEntityDesignContext.MoveProperties.ToBottom|Alt+End|
|OtherContextMenus.MicrosoftDataEntityDesignContext.MoveProperties.ToTop|Alt+Home|
|OtherContextMenus.MicrosoftDataEntityDesignContext.MoveProperties.Up|Alt+Yukarı Ok|
|OtherContextMenus.MicrosoftDataEntityDesignContext.MoveProperties.Up5|Alt+PgUp|
|OtherContextMenus.MicrosoftDataEntityDesignContext.Refactor.Rename|Ctrl+R, R|
|OtherContextMenus.MicrosoftDataEntityDesignContext.RemovefromDiagram|Shift+Del|
|View.EntityDataModelBrowser|Ctrl+1|
|View.EntityDataModelMappingDetails|Ctrl+2|

##  <a name="bkmk_classDiagram"></a> Sınıf diyagramı

|Komutlar|Klavye Kısayolları|
|--------------|------------------------|
|ClassDiagram.Collapse|Num -|
|ClassDiagram.Expand|Num +|
|Edit.Delete|Ctrl+Del|
|Edit.ExpandCollapseBaseTypeList|Shift+Alt+B|
|Edit.NavigateToLollipop|Shift+Alt+L|
|Edit.RemovefromDiagram|Sil|
|View.ViewCode|Enter|

##  <a name="bkmk_codedUItest"></a> Kodlanmış UI Test Düzenleyicisi

|Komutlar|Klavye Kısayolları|
|--------------|------------------------|
|OtherContextMenus.UITestEditorContextMenu.CopyReferencetoClipboard|Ctrl+C|
|OtherContextMenus.UITestEditorContextMenu.InsertDelayBefore|Ctrl+Alt+D|
|OtherContextMenus.UITestEditorContextMenu.LocateAll|Shift+Alt+L|
|OtherContextMenus.UITestEditorContextMenu.LocatetheUIControl|Ctrl+Shift+L|
|OtherContextMenus.UITestEditorContextMenu.Movecode|Ctrl+Alt+C|
|OtherContextMenus.UITestEditorContextMenu.Splitintoanewmethod|Ctrl+Shift+T|

##  <a name="bkmk_dataset"></a> Veri kümesi Düzenleyicisi

|Komutlar|Klavye Kısayolları|
|--------------|------------------------|
|OtherContextMenus.ColumnContext.InsertColumn|Ekleme|
|OtherContextMenus.DbTableContext.Add.Column|Ctrl+L|

##  <a name="bkmk_diff"></a> Fark Görüntüleyicisi

|||
|-|-|
|Komutlar|Klavye Kısayolları|
|Diff.IgnoreTrimWhitespace|CTRL +\\, Ctrl + Ara çubuğu|
|Diff.InlineView|Ctrl+\\, Ctrl+1|
|Diff.LeftOnlyView|Ctrl+\\, Ctrl+3|
|Diff.NextDifference|F8|
|Diff.PreviousDifference|Shift+F8|
|Diff.RightOnlyView|Ctrl+\\, Ctrl+4|
|Diff.SideBySideView|Ctrl+\\, Ctrl+2|
|Diff.SwitchBetweenLeftAndRight|CTRL +\\, Ctrl + sekme|
|Diff.SynchronizeViewToggle|CTRL +\\, Ctrl + aşağı ok|
|EditorContextMenus.CodeWindow.AddComment|Ctrl+Shift+K|
|EditorContextMenus.CodeWindow.EditLocalFile|Ctrl+Shift+P|

##  <a name="bkmk_DOM"></a> DOM Gezgini

|Komutlar|Klavye Kısayolları|
|--------------|------------------------|
|DOMExplorer.Refresh|F5|
|DOMExplorer.SelectElement|Ctrl+B|
|DOMExplorer.ShowLayout|Ctrl+Shift+I|

##  <a name="bkmk_FSharp"></a> F#Etkileşimli

|Komut|Klavye Kısayolu|
|-------------|-----------------------|
|OtherContextMenus.FSIConsoleContext.CancelInteractiveEvaluation|Ctrl+Break tuşu|

##  <a name="bkmk_graphDoc"></a> Graf belgesi Düzenleyicisi

|Komutlar|Klavye Kısayolları|
|--------------|------------------------|
|ArchitectureContextMenus.DirectedGraphContextMenu.Advanced.Add.AddNode|Ekleme|
|ArchitectureContextMenus.DirectedGraphContextMenu.Advanced.Select.BothDependencies|B|
|ArchitectureContextMenus.DirectedGraphContextMenu.Advanced.Select.IncomingDependencies|I|
|ArchitectureContextMenus.DirectedGraphContextMenu.Advanced.Select.OutgoingDependencies|O|
|ArchitectureContextMenus.DirectedGraphContextMenu.NewComment|Ctrl+Shift+K<br /><br /> veya<br /><br /> Ctrl+E, C|
|ArchitectureContextMenus.DirectedGraphContextMenu.Remove|Sil|
|ArchitectureContextMenus.DirectedGraphContextMenu.Rename|F2|

##  <a name="bkmk_graphicsDebugger"></a> Grafik tanılama

|Komutlar|Klavye Kısayolları|
|--------------|------------------------|
|Debug.Graphics.CaptureFrame|Yok.|
|Graphics.MovePixelSelectionDown|Shift+Alt+Aşağı Ok|
|Graphics.MovePixelSelectionLeft|Shift+Alt+Sol Ok|
|Graphics.MovePixelSelectionRight|Shift+Alt+Sağ Ok|
|Graphics.MovePixelSelectionUp|Shift+Alt+Yukarı Ok|
|Graphics.ZoomToActualSize|Shift+Alt+0|
|Graphics.ZoomToFitInWindow|Shift + Alt + 9|
|Graphics.ZoomIn|Shift+Alt+=|
|Graphics.ZoomOut|Shift+Alt+-|

##  <a name="bkmk_HTMLeditor"></a> HTML düzenleyicisi

|Komut|Klavye Kısayolu|
|-------------|-----------------------|
|OtherContextMenus.HTMLContext.GoToController|Ctrl+M, Ctrl+G|

##  <a name="bkmk_HTMLeditorDesign"></a> HTML düzenleyicisi Tasarım görünümü

|Komutlar|Klavye Kısayolları|
|--------------|------------------------|
|Edit.MoveControlDown|Ctrl+Aşağı Ok|
|Edit.MoveControlUp|Ctrl+Yukarı Ok|
|Format.Bold|Ctrl+B|
|Format.ConverttoHyperlink|Ctrl+L|
|Format.InsertBookmark|Ctrl+Shift+L|
|Format.Italic|Ctrl+I|
|Format.Underline|Ctrl+U|
|Project.AddContentPage|Ctrl+M, Ctrl+C|
|Table.ColumntotheLeft|Ctrl+Alt+Sol Ok|
|Table.ColumntotheRight|Ctrl+Alt+Sağ Ok|
|Table.RowAbove|Ctrl+Alt+Yukarı Ok|
|Table.RowBelow|Ctrl+Alt+Aşağı Ok|
|View.ASP.NETNonvisualControls|Ctrl+Shift+N|
|View.EditMaster|Ctrl+M, Ctrl+M|
|View.NextView|Ctrl+PgDn|
|View.ShowSmartTag|Shift+Alt+F10|
|View.ViewMarkup|Shift+F7|
|Window.PreviousTab|Ctrl+PgUp|

##  <a name="bkmk_HTMLeditorSource"></a> HTML düzenleyicisi kaynak görünümü

|Komutlar|Klavye Kısayolları|
|--------------|------------------------|
|OtherContextMenus.HTMLContext.GoToController|Ctrl+M, Ctrl+G|
|View.NextView|Ctrl+PgDn|
|View.SynchronizeViews|Ctrl+Shift+Y|
|View.ViewDesigner|Shift+F7|
|Window.PreviousTab|Ctrl+PgUp|

##  <a name="bkmk_layerDiagram"></a> Katman diyagramı

|Komut|Klavye Kısayolu|
|-------------|-----------------------|
|Edit.Delete|Shift+Delete|

##  <a name="bkmk_managedResources"></a> Yönetilen kaynaklar Düzenleyicisi

|Komutlar|Klavye Kısayolları|
|--------------|------------------------|
|Edit.EditCell|F2|
|Edit.Remove|Sil|
|Edit.RemoveRow|Ctrl+Delete|
|Edit.SelectionCancel|Esc|
|Resources.Audio|Ctrl+4|
|Resources.Files|Ctrl+5|
|Resources.Icons|Ctrl+3|
|Resources.Images|Ctrl+2|
|Resources.Other|Ctrl+6|
|Resources.Strings|Ctrl+1|

##  <a name="bkmk_MergeEditor"></a> Birleştirme Düzenleyicisi penceresi

|Komutlar|Klavye Kısayolları|
|--------------|------------------------|
|TeamFoundationContextMenus.MergeContextMenu.SetFocusonLeftWindow|Alt+1|
|TeamFoundationContextMenus.MergeContextMenu.SetFocusonResultWindow|Alt+2|
|TeamFoundationContextMenus.MergeContextMenu.SetFocusonRightWindow|Alt+3|

##  <a name="bkmk_SchemaCompare"></a> Microsoft SQL Server veri araçları, Şema karşılaştırma

|Komutlar|Klavye Kısayolları|
|--------------|------------------------|
|SQL.SSDTSchemaCompareCompare|Shift+Alt+C|
|SQL.SSDTSchemaCompareGenerateScript|Shift+Alt+G|
|SQL.SSDTSchemaCompareNextChange|Shift+Alt+.|
|SQL.SSDTSchemaComparePreviousChange|Shift+Alt+,|
|SQL.SSDTSchemaCompareStop|Alt+Break|
|SQL.SSDTSchemaCompareWriteUpdates|Shift+Alt+U|

##  <a name="bkmk_TableDesigner"></a> Microsoft SQL Server veri araçları, Tablo Tasarımcısı

|Komutlar|Klavye Kısayolları|
|--------------|------------------------|
|CommitAllEdits|Shift+Alt+U|
|SQL.ExpandWildcards|Ctrl+R, E<br /><br /> veya<br /><br /> Ctrl+R, Ctrl+E|
|SQL.FullyqualifyNames|Ctrl+R, Q<br /><br /> veya<br /><br /> Ctrl+R, Ctrl+Q|
|SQL.MovetoSchema|Ctrl+R, M<br /><br /> veya<br /><br /> Ctrl+R, Ctrl+M|
|SQL.Rename|F2<br /><br /> veya<br /><br /> Ctrl+R, R<br /><br /> veya<br /><br /> Ctrl+R, Ctrl+R|
|ViewFileInScriptPanel|Shift+Alt+PgDn|

##  <a name="bkmk_TSQLeditor"></a> Microsoft SQL Server veri araçları, T-SQL Düzenleyicisi

|Komutlar|Klavye Kısayolları|
|--------------|------------------------|
|CommitAllEdits|Shift+Alt+U|
|SQL.ExecuteWithDebugger|Alt+F5|
|SQL.ExpandWildcards|Ctrl+R, E<br /><br /> veya<br /><br /> Ctrl+R, Ctrl+E|
|SQL.FullyqualifyNames|Ctrl+R, Q<br /><br /> veya<br /><br /> Ctrl+R, Ctrl+Q|
|SQL.MovetoSchema|Ctrl+R, M<br /><br /> veya<br /><br /> Ctrl+R, Ctrl+M|
|SQL.Rename|F2<br /><br /> veya<br /><br /> Ctrl+R, R<br /><br /> veya<br /><br /> Ctrl+R, Ctrl+R|
|SQL.TSqlEditorCancelQuery|Alt+Break|
|SQL.TSqlEditorExecuteQuery|Ctrl+Shift+E|
|SQL.TSqlEditorResultsAsFile|Ctrl+D, F|
|SQL.TSqlEditorResultsAsGrid|Ctrl+D, G|
|SQL.TSqlEditorResultsAsText|Ctrl+D, T|
|SQL.TSqlEditorShowEstimatedPlan|Ctrl+D, E|
|SQL.TSqlEditorToggleExecutionPlan|Ctrl+D, A|
|SQL.TSqlEditorToggleResultsPane|Ctrl+D, R|
|TSqlEditorCloneQuery|Ctrl+Alt+N|
|TSqlEditorDatabaseCombo|Shift+Alt+PgDn|

##  <a name="bkmk_linkfix"></a> Microsoft SQL Server veri araçları, T-SQL PDW Düzenleyicisi

|Komutlar|Klavye Kısayolları|
|--------------|------------------------|
|SQL.TSqlEditorCancelQuery|Alt+Break|
|SQL.TSqlEditorExecuteQuery|Ctrl+Shift+E|
|SQL.TSqlEditorResultsAsFile|Ctrl+D, F|
|SQL.TSqlEditorResultsAsGrid|Ctrl+D, G|
|SQL.TSqlEditorResultsAsText|Ctrl+D, T|
|SQL.TSqlEditorShowEstimatedPlan|Ctrl+D, E|
|SQL.TSqlEditorToggleExecutionPlan|Ctrl+D, A|
|SQL.TSqlEditorToggleResultsPane|Ctrl+D, R|
|TSqlEditorCloneQuery|Ctrl+Alt+N|
|TSqlEditorDatabaseCombo|Shift+Alt+PgDn|

##  <a name="bkmk_PageInspector"></a> Sayfa denetçisi

|Komut|Klavye Kısayolu|
|-------------|-----------------------|
|PageInspector.Minimize|F12|

##  <a name="bkmk_QueryDesigner"></a> Sorgu Tasarımcısı

|Komutlar|Klavye Kısayolları|
|--------------|------------------------|
|QueryDesigner.CancelRetrievingData|Ctrl+T|
|QueryDesigner.Criteria|Ctrl+2|
|QueryDesigner.Diagram|Ctrl+1|
|QueryDesigner.ExecuteSQL|Ctrl+R|
|QueryDesigner.GotoRow|Ctrl+G|
|QueryDesigner.JoinMode|Ctrl+Shift+J|
|QueryDesigner.Results|Ctrl+4|
|QueryDesigner.SQL|Ctrl+3|

##  <a name="bkmk_QueryResults"></a> Sorgu sonuçları

|Komutlar|Klavye Kısayolları|
|--------------|------------------------|
|SQL.QueryResultsNewRow|Alt+End|
|SQL.QueryResultsRefresh|Shift+Alt+R|
|SQL.QueryResultsStop|Alt+Break|

##  <a name="bkmk_ReportDesigner"></a> Rapor Tasarımcısı

|Komutlar|Klavye Kısayolları|
|--------------|------------------------|
|Edit.BreakLine|Enter|
|Edit.CharLeft|Sol Ok|
|Edit.CharLeftExtend|Shift+Sol Ok|
|Edit.CharRight|Sağ Ok|
|Edit.CharRightExtend|Shift+Sağ Ok|
|Edit.InsertTab|Tab|
|Edit.LineDown|Aşağı Ok|
|Edit.LineDownExtend|Shift+Aşağı Ok|
|Edit.LineUp|Yukarı Ok|
|Edit.LineUpExtend|Shift+Yukarı Ok|
|Edit.MoveControlDown|Ctrl+Aşağı Ok|
|Edit.MoveControlLeft|Ctrl+Sol Ok|
|Edit.MoveControlRight|Ctrl+Sağ Ok|
|Edit.MoveControlUp|Ctrl+Yukarı Ok|
|Edit.SelectionCancel|Esc|
|Edit.SizeControlDown|Ctrl+Shift+Aşağı Ok|
|Edit.SizeControlLeft|Ctrl+Shift+Sol Ok|
|Edit.SizeControlRight|Ctrl+Shift+Sağ Ok|
|Edit.SizeControlUp|Ctrl+Shift+Yukarı Ok|
|Edit.TabLeft|Shift+Sekme Tuşu|
|View.ReportData|Ctrl+Alt+D|

##  <a name="bkmk_SequenceDiagram"></a> Sıralı diyagram

|Komutlar|Klavye Kısayolları|
|--------------|------------------------|
|ArchitectureDesigner.Sequence.NavigateToCode|F12|
|Edit.Delete|Shift+Del|

##  <a name="bkmk_SettingsDesigner"></a> Ayarlar Tasarımcısı

|Komutlar|Klavye Kısayolları|
|--------------|------------------------|
|Edit.EditCell|F2|
|Edit.RemoveRow|Ctrl+Delete|
|Edit.SelectionCancel|Esc|
|View.ViewCode|F7|

##  <a name="bkmk_SolutionExplorer"></a> Çözüm Gezgini

|Komut|Klavye Kısayolu|
|-------------|-----------------------|
|ClassViewContextMenus.ClassViewProject.View.ViewinPageInspector|Ctrl+K, Ctrl+G|

##  <a name="bkmk_TeamExplorer"></a> Takım Gezgini

|Komut|Klavye Kısayolu|
|-------------|-----------------------|
|Edit.Delete|Sil|
|File.Rename|F2|
|TeamFoundationContextMenus.Commands.GoToTeamExplorerNavigation|Alt+Home|
|TeamFoundationContextMenus.Commands.GoToTeamExplorerNextSectionContent|Alt+Aşağı Ok|
|TeamFoundationContextMenus.Commands.GoToTeamExplorerPageContent|Alt+0|
|TeamFoundationContextMenus.Commands.GoToTeamExplorerPreviousSectionContent|Alt+Yukarı Ok|
|TeamFoundationContextMenus.Commands.GoToTeamExplorerSection1Content|Alt+1|
|TeamFoundationContextMenus.Commands.GoToTeamExplorerSection2Content|Alt+2|
|TeamFoundationContextMenus.Commands.GoToTeamExplorerSection3Content|Alt+3|
|TeamFoundationContextMenus.Commands.GoToTeamExplorerSection4Content|Alt+4|
|TeamFoundationContextMenus.Commands.GoToTeamExplorerSection5Content|Alt+5|
|TeamFoundationContextMenus.Commands.GoToTeamExplorerSection6Content|Alt+6|
|TeamFoundationContextMenus.Commands.GoToTeamExplorerSection7Content|Alt+7|
|TeamFoundationContextMenus.Commands.GoToTeamExplorerSection8Content|Alt+8|
|TeamFoundationContextMenus.Commands.GoToTeamExplorerSection9Content|Alt+9|
|TeamFoundationContextMenus.Commands.TeamExplorerNavigateBackward|Alt+Sol Ok|
|TeamFoundationContextMenus.Commands.TeamExplorerNavigateForward|Alt+Sağ Ok|
|TeamFoundationContextMenus.MyWorkPageInProgress.TfsContextMyWorkPageCreateCopyWI|Shift+Alt+C|
|TeamFoundationContextMenus.MyWorkPageInProgress.TfsContextMyWorkPageNewLinkedWI|Shift+Alt+L|
|View.Refresh|F5|

##  <a name="bkmk_TFBuild"></a> Team Foundation Yapı ayrıntı Düzenleyicisi

|Komut|Klavye Kısayolu|
|-------------|-----------------------|
|View.Refresh|F5|

##  <a name="bkmk_TestExplorer"></a> Test Gezgini

|Komut|Klavye Kısayolu|
|-------------|-----------------------|
|TestExplorer.OpenTest|F12|

##  <a name="bkmk_TextEditor"></a> Metin Düzenleyici

|                             Komutlar                              |                  Klavye Kısayolları                   |
|-------------------------------------------------------------------|-------------------------------------------------------|
|                          Edit.BreakLine                           |     Enter<br /><br /> veya<br /><br /> Shift+Enter      |
|                           Edit.CharLeft                           |                      Sol Ok                       |
|                        Edit.CharLeftExtend                        |                   Shift+Sol Ok                    |
|                     Edit.CharLeftExtendColumn                     |                 Shift+Alt+Sol Ok                  |
|                          Edit.CharRight                           |                      Sağ Ok                      |
|                       Edit.CharRightExtend                        |                   Shift+Sağ Ok                   |
|                    Edit.CharRightExtendColumn                     |                 Shift+Alt+Sağ Ok                 |
|                        Edit.CharTranspose                         |                        Ctrl+T                         |
|                        Edit.ClearBookmarks                        |                    Ctrl+K, Ctrl+L                     |
|                     Edit.CollapseAllOutlining                     |                    Ctrl+M, Ctrl+A                     |
|                    Edit.CollapseCurrentRegion                     |                    Ctrl+M, Ctrl+S                     |
|                         Edit.CollapseTag                          |                    Ctrl+M, Ctrl+T                     |
|                    Edit.CollapsetoDefinitions                     |                    Ctrl+M, Ctrl+O                     |
|                       Edit.CommentSelection                       |                    Ctrl+K, Ctrl+C                     |
|                         Edit.CompleteWord                         | Ctrl+Ara Çubuğu<br /><br /> veya<br /><br /> Alt+Sağ Ok |
|                       Edit.CopyParameterTip                       |                   Ctrl+Shift+Alt+C                    |
|                     Edit.DecreaseFilterLevel                      |                         Alt+,                         |
|                       Edit.DeleteBackwards                        |   Geri Al tuşu<br /><br /> veya<br /><br /> Shift+Geri Al tuşu   |
|                  Edit.DeleteHorizontalWhiteSpace                  |                    Ctrl+K, Ctrl+\                     |
|                         Edit.DocumentEnd                          |                       Ctrl+End                        |
|                      Edit.DocumentEndExtend                       |                    Ctrl+Shift+End                     |
|                        Edit.DocumentStart                         |                       Ctrl+Home                       |
|                     Edit.DocumentStartExtend                      |                    Ctrl+Shift+Home                    |
|                      Edit.ExpandAllOutlining                      |                    Ctrl+M, Ctrl+X                     |
|                     Edit.ExpandCurrentRegion                      |                    Ctrl+M, Ctrl+E                     |
|                        Edit.FormatDocument                        |                    Ctrl+K, Ctrl+D                     |
|                       Edit.FormatSelection                        |                    Ctrl+K, Ctrl+F                     |
|                          Edit.GotoBrace                           |                        Ctrl+]                         |
|                       Edit.GotoBraceExtend                        |                     Ctrl+Shift+]                      |
|                        Edit.HideSelection                         |                    Ctrl+M, Ctrl+H                     |
|                     Edit.IncreaseFilterLevel                      |                         Alt+.                         |
|                      Edit.IncrementalSearch                       |                        Ctrl+I                         |
|                          Edit.InsertTab                           |                          Tab                          |
|                           Edit.LineCut                            |                        Ctrl+L                         |
|                          Edit.LineDelete                          |                     Ctrl+Shift+L                      |
|                           Edit.LineDown                           |                      Aşağı Ok                       |
|                        Edit.LineDownExtend                        |                   Shift+Aşağı Ok                    |
|                     Edit.LineDownExtendColumn                     |                 Shift+Alt+Aşağı Ok                  |
|                           Edit.LineEnd                            |                          End                          |
|                        Edit.LineEndExtend                         |                       Shift+End                       |
|                     Edit.LineEndExtendColumn                      |                     Shift+Alt+End                     |
|                        Edit.LineOpenAbove                         |                      Ctrl+Enter                       |
|                        Edit.LineOpenBelow                         |                   Ctrl+Shift+Enter                    |
|                          Edit.LineStart                           |                         Ana Sayfası                          |
|                       Edit.LineStartExtend                        |                      Shift+Home                       |
|                    Edit.LineStartExtendColumn                     |                    Shift+Alt+Home                     |
|                        Edit.LineTranspose                         |                      Shift+Alt+T                      |
|                            Edit.LineUp                            |                       Yukarı Ok                        |
|                         Edit.LineUpExtend                         |                    Shift+Yukarı Ok                     |
|                      Edit.LineUpExtendColumn                      |                  Shift+Alt+Yukarı Ok                   |
|                         Edit.ListMembers                          |                        Ctrl+J                         |
|                        Edit.MakeLowercase                         |                        Ctrl+U                         |
|                        Edit.MakeUppercase                         |                     Ctrl+Shift+U                      |
|                    Edit.MoveSelectedLinesDown                     |                    Alt+Aşağı Ok                     |
|                     Edit.MoveSelectedLinesUp                      |                     Alt+Yukarı Ok                      |
|                   Edit.NextHighlightedReference                   |                 Ctrl+Shift+Aşağı Ok                 |
|                         Edit.OvertypeMode                         |                        Ekleme                         |
|                           Edit.PageDown                           |                         PgDn                          |
|                        Edit.PageDownExtend                        |                      Shift+PgDn                       |
|                            Edit.PageUp                            |                         PgUp                          |
|                         Edit.PageUpExtend                         |                      Shift+PgUp                       |
|                        Edit.ParameterInfo                         |                  Ctrl+Shift+Ara Çubuğu                  |
|                      Edit.PasteParameterTip                       |                   Ctrl+Shift+Alt+P                    |
|                         Edit.PeekBackward                         |                      Ctrl+Alt+-                       |
|                        Edit.PeekDefinition                        |                        Alt+F12                        |
|                         Edit.PeekForward                          |                      Ctrl+Alt+=                       |
|                 Edit.PreviousHighlightedReference                 |                  Ctrl+Shift+Yukarı Ok                  |
|                          Edit.QuickInfo                           |                    Ctrl+K, Ctrl+I                     |
|                   Edit.ReverseIncrementalSearch                   |                     Ctrl+Shift+I                      |
|                        Edit.ScrollLineDown                        |                    Ctrl+Aşağı Ok                    |
|                         Edit.ScrollLineUp                         |                     Ctrl+Yukarı Ok                     |
|                      Edit.SelectCurrentWord                       |                        Ctrl+W                         |
|                       Edit.SelectionCancel                        |                        Esc                         |
|                      Edit.SelectToLastGoBack                      |                        Ctrl+=                         |
|                       Edit.ShowCodeLensMenu                       |                        Alt +\`                         |
|                      Edit.StopHidingCurrent                       |                    Ctrl+M, Ctrl+U                     |
|                        Edit.StopOutlining                         |                    Ctrl+M, Ctrl+P                     |
|                          Edit.SwapAnchor                          |                    Ctrl+K, Ctrl+A                     |
|                           Edit.TabLeft                            |                       Shift+Sekme Tuşu                       |
|                      Edit.ToggleAllOutlining                      |                    Ctrl+M, Ctrl+L                     |
|                        Edit.ToggleBookmark                        |                    Ctrl+K, Ctrl+K                     |
|                     Edit.ToggleCompletionMode                     |                    Ctrl+Alt+Ara Çubuğu                     |
|                   Edit.ToggleOutliningExpansion                   |                    Ctrl+M, Ctrl+M                     |
|                    Edit.ToggleTaskListShortcut                    |                    Ctrl+K, Ctrl+H                     |
|                        Edit.ToggleWordWrap                        |                    Ctrl+E, Ctrl+W                     |
|                      Edit.UncommentSelection                      |                    Ctrl+K, Ctrl+U                     |
|                          Edit.ViewBottom                          |                       Ctrl+PgDn                       |
|                       Edit.ViewBottomExtend                       |                    Ctrl+Shift+PgDn                    |
|                           Edit.ViewTop                            |                       Ctrl+PgUp                       |
|                        Edit.ViewTopExtend                         |                    Ctrl+Shift+PgUp                    |
|                        Edit.ViewWhiteSpace                        |                    Ctrl+R, Ctrl+W                     |
|                       Edit.WordDeleteToEnd                        |                      Ctrl+Delete                      |
|                      Edit.WordDeleteToStart                       |                    Ctrl+Geri Al tuşu                     |
|                           Edit.WordNext                           |                   Ctrl+Sağ Ok                    |
|                        Edit.WordNextExtend                        |                Ctrl+Shift+Sağ Ok                 |
|                     Edit.WordNextExtendColumn                     |              Ctrl+Shift+Alt+Sağ Ok               |
|                         Edit.WordPrevious                         |                    Ctrl+Sol Ok                    |
|                      Edit.WordPreviousExtend                      |                 Ctrl+Shift+Sol Ok                 |
|                   Edit.WordPreviousExtendColumn                   |               Ctrl+Shift+Alt+Sol Ok               |
|                        Edit.WordTranspose                         |                     Ctrl+Shift+T                      |
|        EditorContextMenus.CodeWindow.ExecuteInInteractive         |                       Alt+Enter                       |
|      EditorContextMenus.CodeWindow.ExecuteLineInInteractive       |                         Alt+'                         |
|         OtherContextMenus.HTMLContext.ViewinPageInspector         |                    Ctrl+K, Ctrl+G                     |
|   TeamFoundationContextMenus.Annotate.TfsAnnotateMoveNextRegion   |                       Alt+PgDn                        |
| TeamFoundationContextMenus.Annotate.TfsAnnotateMovePreviousRegion |                       Alt+PgUp                        |

##  <a name="bkmk_UMLactivityDiagram"></a> UML etkinlik diyagramı

|Komut|Klavye Kısayolu|
|-------------|-----------------------|
|Edit.Delete|Shift+Del|

##  <a name="bkmk_UMLclassDiagram"></a> UML sınıf diyagramı

|Komut|Klavye Kısayolu|
|-------------|-----------------------|
|Edit.DeleteFromModel|Shift+Del|

##  <a name="bkmk_UMLcomponentDiagram"></a> UML bileşen diyagramı

|Komut|Klavye Kısayolu|
|-------------|-----------------------|
|Edit.DeleteFromModel|Shift+Del|

##  <a name="bkmk_UMLusecaseDiagram"></a> UML Kullanım durumu diyagramı

|Komut|Klavye Kısayolu|
|-------------|-----------------------|
|Edit.DeleteFromModel|Shift+Del|

##  <a name="bkmk_vcaccelerator"></a> VC Hızlandırıcı Düzenleyicisi

|Komutlar|Klavye Kısayolları|
|--------------|------------------------|
|Edit.NewAccelerator|Ekleme|
|Edit.NextKeyTyped|Ctrl+W|

##  <a name="bkmk_vcdialogeditor"></a> VC iletişim kutusu Düzenleyicisi

|Komutlar|Klavye Kısayolları|
|--------------|------------------------|
|Edit.MoveControlDown|Aşağı Ok|
|Edit.MoveControlLeft|Sol Ok|
|Edit.MoveControlRight|Sağ Ok|
|Edit.MoveControlUp|Yukarı Ok|
|Edit.ScrollColumnLeft|Ctrl+Sol Ok|
|Edit.ScrollColumnRight|Ctrl+Sağ Ok|
|Edit.ScrollLineDown|Ctrl+Aşağı Ok|
|Edit.ScrollLineUp|Ctrl+Yukarı Ok|
|Edit.SizeControlDown|Shift+Aşağı Ok|
|Edit.SizeControlLeft|Shift+Sol Ok|
|Edit.SizeControlRight|Shift+Sağ Ok|
|Edit.SizeControlUp|Shift+Yukarı Ok|
|Format.AlignBottoms|Ctrl+Shift+Aşağı Ok|
|Format.AlignCenters|Shift+F9|
|Format.AlignLefts|Ctrl+Shift+Sol Ok|
|Format.AlignMiddles|F9|
|Format.AlignRights|Ctrl+Shift+Sağ Ok|
|Format.AlignTops|Ctrl+Shift+Yukarı Ok|
|Format.ButtonBottom|Ctrl+B|
|Format.ButtonRight|Ctrl+R|
|Format.CenterHorizontal|Ctrl+Shift+F9|
|Format.CenterVertical|Ctrl+F9|
|Format.CheckMnemonics|Ctrl+M|
|Format.SizetoContent|Shift+F7|
|Format.SpaceAcross|Alt+Sağ Ok<br /><br /> veya<br /><br /> Alt+Sol Ok|
|Format.SpaceDown|Alt+Yukarı Ok<br /><br /> veya<br /><br /> Alt+Aşağı Ok|
|Format.TabOrder|Ctrl+D|
|Format.TestDialog|Ctrl+T|
|Format.ToggleGuides|Ctrl+G|

##  <a name="bkmk_vcimageeditor"></a> VC görüntü Düzenleyicisi

|Komutlar|Klavye Kısayolları|
|--------------|------------------------|
|Image.AirbrushTool|Ctrl+A|
|Image.BrushTool|Ctrl+B|
|Image.CopyandOutlineSelection|Ctrl+Shift+U|
|Image.DrawOpaque|Ctrl+J|
|Image.EllipseTool|Alt+P|
|Image.EraseTool|Ctrl+Shift+I|
|Image.FilledEllipseTool|Ctrl+Shift+Alt+P|
|Image.FilledRectangleTool|Ctrl+Shift+Alt+R|
|Image.FilledRoundedRectangleTool|Ctrl+Shift+Alt+W|
|Image.FillTool|Ctrl+F|
|Image.FlipHorizontal|Ctrl+H|
|Image.FlipVertical|Shift+Alt+H|
|Image.LargerBrush|Ctrl+=|
|Image.LineTool|Ctrl+L|
|Image.MagnificationTool|Ctrl+M|
|Image.Magnify|Ctrl+Shift+M|
|Image.NewImageType|Ekleme|
|Image.NextColor|Ctrl+]<br /><br /> veya<br /><br /> Ctrl+Sağ Ok|
|Image.NextRightColor|Ctrl+Shift+]<br /><br /> veya<br /><br /> Ctrl+Shift+Sağ Ok|
|Image.OutlinedEllipseTool|Shift+Alt+P|
|Image.OutlinedRectangleTool|Shift+Alt+R|
|Image.OutlinedRoundedRectangleTool|Shift+Alt+W|
|Image.PencilTool|Ctrl+I|
|Image.PreviousColor|Ctrl+[<br /><br /> veya<br /><br /> Ctrl+Sol Ok|
|Image.PreviousRightColor|Ctrl+Shift+[<br /><br /> veya<br /><br /> Ctrl+Shift+Sol Ok|
|Image.RectangleSelectionTool|Shift+Alt+S|
|Image.RectangleTool|Alt+R|
|Image.Rotate90Degrees|Ctrl+Shift+H|
|Image.RoundedRectangleTool|Alt+W|
|Image.ShowGrid|Ctrl+Alt+S|
|Image.ShowTileGrid|Ctrl+Shift+Alt+S|
|Image.SmallBrush|Ctrl+.|
|Image.SmallerBrush|Ctrl+-|
|Image.TextTool|Ctrl+T|
|Image.UseSelectionasBrush|Ctrl+U|
|Image.ZoomIn|Ctrl+Shift+.<br /><br /> veya<br /><br /> Ctrl+Yukarı Ok|
|Image.ZoomOut|Ctrl+Shift+,<br /><br /> veya<br /><br /> Ctrl+Aşağı Ok|

##  <a name="bkmk_vcstringeditor"></a> VC Dize Düzenleyicisi

|Komut|Klavye Kısayolu|
|-------------|-----------------------|
|Edit.NewString|Ekleme|

##  <a name="bkmk_viewDesigner"></a> Görünüm Tasarımcısı

|Komutlar|Klavye Kısayolları|
|--------------|------------------------|
|QueryDesigner.CancelRetrievingData|Ctrl+T|
|QueryDesigner.Criteria|Ctrl+2|
|QueryDesigner.Diagram|Ctrl+1|
|QueryDesigner.ExecuteSQL|Ctrl+R|
|QueryDesigner.GotoRow|Ctrl+G|
|QueryDesigner.JoinMode|Ctrl+Shift+J|
|QueryDesigner.Results|Ctrl+4|
|QueryDesigner.SQL|Ctrl+3|

##  <a name="bkmk_visualstudio"></a> Visual Studio

|Komut|Klavye Kısayolu|
|-------------|-----------------------|
|OtherContextMenus.ORDesignerContext.HideMethodsPane|Ctrl+1|

##  <a name="bkmk_wfdesigner"></a> Windows Form Tasarımcısı

|Komutlar|Klavye Kısayolları|
|--------------|------------------------|
|Edit.BreakLine|Enter|
|Edit.CharLeft|Sol Ok|
|Edit.CharLeftExtend|Shift+Sol Ok|
|Edit.CharRight|Sağ Ok|
|Edit.CharRightExtend|Shift+Sağ Ok|
|Edit.DocumentEnd|End|
|Edit.DocumentEndExtend|Shift+End|
|Edit.DocumentStart|Ana Sayfası|
|Edit.DocumentStartExtend|Shift+Home|
|Edit.InsertTab|Tab|
|Edit.LineDown|Aşağı Ok|
|Edit.LineDownExtend|Shift+Yukarı Ok|
|Edit.LineUp|Yukarı Ok|
|Edit.LineUpExtend|Shift+Aşağı Ok|
|Edit.MoveControlDown|Ctrl+Aşağı Ok|
|Edit.MoveControlLeft|Ctrl+Sol Ok|
|Edit.MoveControlRight|Ctrl+Sağ Ok|
|Edit.MoveControlUp|Ctrl+Yukarı Ok|
|Edit.SelectionCancel|Esc|
|Edit.SizeControlDown|Ctrl+Shift+Aşağı Ok|
|Edit.SizeControlLeft|Ctrl+Shift+Sol Ok|
|Edit.SizeControlRight|Ctrl+Shift+Sağ Ok|
|Edit.SizeControlUp|Ctrl+Shift+Yukarı Ok|
|Edit.TabLeft|Shift+Sekme Tuşu|

##  <a name="bkmk_workItemEditor"></a> Çalışma öğesi Düzenleyicisi

|Komutlar|Klavye Kısayolları|
|--------------|------------------------|
|Edit.CreateCopyofWorkItem|Shift+Alt+C|
|Edit.RefreshWorkItem|F5|
|Team.NewLinkedWorkItem|Shift+Alt+L|

##  <a name="bkmk_WIqueryview"></a> Çalışma öğesi sorgu görünümü

|Komutlar|Klavye Kısayolları|
|--------------|------------------------|
|Edit.CreateCopyofWorkItem|Shift+Alt+C|
|Edit.Indent|Shift+Alt+Sağ Ok|
|Edit.Outdent|Shift+Alt+Sol Ok|
|Team.NewLinkedWorkItem|Shift+Alt+L|
|Team.Refresh|F5|
|Window.Toggle|Shift+Alt+V|

##  <a name="bkmk_WIresultsview"></a> Çalışma öğesi Sonuçlar Görünümü

|Komutlar|Klavye Kısayolları|
|--------------|------------------------|
|Edit.CreateCopyofWorkItem|Shift+Alt+C|
|Edit.Indent|Shift+Alt+Sağ Ok|
|Edit.Outdent|Shift+Alt+Sol Ok|
|Team.GotoNextWorkItem|Shift+Alt+N|
|Team.GotoPreviousWorkItem|Shift+Alt+P|
|Team.NewLinkedWorkItem|Shift+Alt+L|
|Team.Refresh|F5|
|Window.Toggle|Shift+Alt+V|

##  <a name="bkmk_workflowdesigner"></a> İş Akışı Tasarımcısı

|Komutlar|Klavye Kısayolları|
|--------------|------------------------|
|Edit.CompleteWord|Ctrl+K, W<br /><br /> veya<br /><br /> Ctrl+K, Ctrl+W<br /><br /> veya<br /><br /> Ctrl+Ara Çubuğu<br /><br /> veya<br /><br /> Alt+Sağ Ok|
|Edit.DecreaseFilterLevel|Alt+,|
|Edit.IncreaseFilterLevel|Alt+.|
|Edit.ListMembers|Ctrl+K, L<br /><br /> veya<br /><br /> Ctrl+K, Ctrl+L<br /><br /> veya<br /><br /> Ctrl+J|
|Edit.ParameterInfo|Ctrl+K, P<br /><br /> veya<br /><br /> Ctrl+K, Ctrl+P<br /><br /> veya<br /><br /> Ctrl+Shift+Ara Çubuğu|
|Edit.QuickInfo|Ctrl+K, I<br /><br /> veya<br /><br /> Ctrl+K, Ctrl+I|
|WorkflowDesigner.Collapse|Ctrl+E, Ctrl+C<br /><br /> veya<br /><br /> Ctrl+E, C|
|WorkflowDesigner.CollapseAll|veya|
|WorkflowDesigner.ConnectNodes|Ctrl+E, Ctrl+F<br /><br /> veya<br /><br /> Ctrl+E, F|
|WorkflowDesigner.CreateVariable|Ctrl+E, Ctrl+N<br /><br /> veya<br /><br /> Ctrl+E, N|
|WorkflowDesigner.ExpandAll|Ctrl+E, Ctrl+X<br /><br /> veya<br /><br /> Ctrl+E, X|
|WorkflowDesigner.ExpandInPlace|Ctrl+E, Ctrl+E<br /><br /> veya<br /><br /> Ctrl+E, E|
|WorkflowDesigner.GoToParent|Ctrl+E, Ctrl+P<br /><br /> veya<br /><br /> Ctrl+E, P|
|WorkflowDesigner.MoveFocus|Ctrl+E, Ctrl+M<br /><br /> veya<br /><br /> Ctrl+E, M|
|WorkflowDesigner.NavigateThroughDesigner|Ctrl+Alt+F6|
|WorkflowDesigner.Restore|Ctrl+E, Ctrl+R<br /><br /> veya<br /><br /> Ctrl+E, R|
|WorkflowDesigner.ShowHideArgumentDesigner|Ctrl+E, Ctrl+A<br /><br /> veya<br /><br /> Ctrl+E, A|
|WorkflowDesigner.ShowHideImportsDesigner|Ctrl+E, Ctrl+I<br /><br /> veya<br /><br /> Ctrl+E, I|
|WorkflowDesigner.ShowHideOverviewMap|Ctrl+E, Ctrl+O<br /><br /> veya<br /><br /> Ctrl+E, O|
|WorkflowDesigner.ShowHideVariableDesigner|Ctrl+E, Ctrl+V<br /><br /> veya<br /><br /> Ctrl+E, V|
|WorkflowDesigner.ToggleSelection|Ctrl+E, Ctrl+S<br /><br /> veya<br /><br /> Ctrl+E, S|
|WorkflowDesigner.ZoomIn|Ctrl+Num +|
|WorkflowDesigner.ZoomOut|Ctrl+Num -|

##  <a name="bkmk_xamluidesigner"></a> XAML Tasarımcısı

|Komutlar|Klavye Kısayolları|
|--------------|------------------------|
|Design.FitAll|Ctrl+0|
|Design.ShowHandles|F9|
|Design.ZoomIn|Ctrl+Alt+=|
|Design.ZoomOut|Ctrl+Alt+-|
|Format.EditText|F2|
|Format.ResetLayout.All|Ctrl+Shift+R|
|View.EdgeLeftMoveLeft|Ctrl+Shift+,|
|View.EdgeLeftMoveRight|Ctrl+Shift+.|
|View.EdgeRightMoveLeft|Ctrl+Shift+Alt+,|
|View.EdgeRightMoveRight|Ctrl+Shift+Alt+.|
|Proje kodunu Çalıştır|Ctrl+F9|

##  <a name="bkmk_xmlTextEditor"></a> XML (metin) Düzenleyicisi

|Komutlar|Klavye Kısayolları|
|--------------|------------------------|
|XML.StartXSLTDebugging|Alt+F5|
|XML.StartXSLTWithoutDebugging|Ctrl+Alt+F5|

##  <a name="bkmk_xmlSchemaDesigner"></a> XML şema Tasarımcısı

|Komutlar|Klavye Kısayolları|
|--------------|------------------------|
|GraphView.BottomtoTop|Alt+Yukarı Ok|
|GraphView.LefttoRight|Alt+Sağ Ok|
|GraphView.RighttoLeft|Alt+Sol Ok|
|GraphView.ToptoBottom|Alt+Aşağı Ok|
|OtherContextMenus.GraphView.RemovefromWorkspace|Sil|
|XsdDesigner.ShowContentModelView|Ctrl+2|
|XsdDesigner.ShowGraphView|Ctrl+3|
|XsdDesigner.ShowStartView|Ctrl+1|

## <a name="see-also"></a>Ayrıca Bkz.
 [Simgeler için görüntü Düzenleyicisi](http://msdn.microsoft.com/library/586d2b8b-0348-4883-a85d-1ff0ddbf14dd) [IntelliSense kullanma](../ide/using-intellisense.md)
