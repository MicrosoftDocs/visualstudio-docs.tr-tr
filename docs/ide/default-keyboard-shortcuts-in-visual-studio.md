---
title: Varsayılan klavye kısayolları
description: çeşitli komutlara ve windows 'a erişmenize olanak tanıyan Visual Studio varsayılan klavye kısayolları hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 06/21/2021
ms.topic: reference
helpviewer_keywords:
- shortcut keys [Visual Studio], keyboard binding schemes
- keyboard binding schemes [Visual Studio]
- Help [Visual Studio], shortcut keys
- keyboard shortcuts [Visual Studio], keyboard binding schemes
- keyboard shortcuts
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: dec9f76f2b21e11cc79bc55efc4a2de6fb7dedc3
ms.sourcegitcommit: 15821c790d6498210f30b3268402ffad6bb70c7c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/14/2021
ms.locfileid: "113725527"
---
# <a name="default-keyboard-shortcuts-in-visual-studio"></a>Visual Studio varsayılan klavye kısayolları

uygun klavye kısayolunu seçerek Visual Studio içindeki çeşitli [komutlara](reference/visual-studio-commands.md) ve pencereler için erişebilirsiniz. Bu sayfa, Visual Studio yüklediğinizde seçmiş olabileceğiniz **genel** profil için varsayılan komut kısayollarını listeler. Seçtiğiniz profil ne olduğuna bakılmaksızın, **Seçenekler** iletişim kutusunu açıp **ortam** düğümünü genişleterek ve ardından **klavye**' yi seçerek bir komutun [kısayolunu belirleyebilirsiniz](identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md) . Ayrıca, verilen komutlardan herhangi birine farklı bir kısayol atayarak kısayollarınızı özelleştirebilirsiniz.

Yaygın klavye kısayollarının ve diğer üretkenlik bilgilerinin bir listesi için bkz.:

- [Klavye ipuçları](../ide/productivity-shortcuts.md)
- [Üretkenlik ipuçları](../ide/productivity-features.md).

Visual Studio erişilebilirlik hakkında daha fazla bilgi için bkz. [erişilebilirlik ipuçları ve püf noktaları](../ide/reference/accessibility-tips-and-tricks.md) ve [nasıl yapılır: klavyeyi özel olarak kullanma](../ide/reference/how-to-use-the-keyboard-exclusively.md).

<a name="popular"></a>
## <a name="popular-keyboard-shortcuts-for-visual-studio"></a>Visual Studio için popüler klavye kısayolları

Aksi belirtilmedikçe, bu bölümdeki tüm kısayollar Global olarak uygulanır. *Genel* bağlam, kısayolun Visual Studio tüm araç pencereleri için geçerli olduğu anlamına gelir.

> [!NOTE]
> **Seçenekler** iletişim kutusunu açıp **ortam** düğümünü genişleterek ve ardından **klavye**' yi seçerek herhangi bir komutun [kısayolunu arayabilirsiniz](identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md) .


#### <a name="build-popular-shortcuts"></a>Oluşturma: popüler kısayollar

|Komutlar|Klavye kısayolları |Komut KIMLIĞI|
|-|-|-|
|Çözüm oluştur|**Ctrl+Shift+B** | Build.BuildSolution |
|İptal|**Ctrl+Break tuşu** | Build.Cancel |
|Se|**Ctrl+F7** | Build.Compile |
|Çözümde Kod analizini Çalıştır|**Alt+F11**| Build.RunCodeAnalysisonSolution |

#### <a name="debug-popular-shortcuts"></a>Hata Ayıkla: popüler kısayollar

|Komutlar|Klavye kısayolları [özel bağlamlar]|Komut KIMLIĞI|
|-|-|-|
|İşlevde kes|**Ctrl+B**| Debug.BreakatFunction |
|Tümünü kes|**Ctrl+Alt+Break tuşu**| Debug.BreakAll |
|Tüm kesme noktalarını Sil|**CTRL + SHIFT + F9**| Debug.DeleteAllBreakpoints |
|Özel durumlar|**Ctrl+Alt+E**| Debug.Exceptions |
|Hızlı Bakış|**Ctrl+Alt+Q**<br /><br />veya **SHIFT + F9**| Debug.QuickWatch |
|Yeniden başlat|**Ctrl+Shift+F5**| Debug.Restart |
|İmlece kadar Çalıştır|**Ctrl+F10**| Debug.RunToCursor |
|Sonraki ifadeyi ayarla|**Ctrl+Shift+F10**| Debug.SetNextStatement |
|Başlangıç|**F5**| Debug.Start |
|Hata ayıklama olmadan Başlat|**Ctrl+F5**| Debug.StartWithoutDebugging |
|Adımla|**F11**| Debug.StepInto |
|Dışarı adımla|**Shift+F11**| Debug.StepOut |
|Adımla|**F10**| Debug.StepOver |
|Hata ayıklamayı Durdur|**Shift+F5**| Debug.StopDebugging |
|Kesme noktasını aç|**F9**| Debug.ToggleBreakpoint |

#### <a name="edit-popular-shortcuts"></a>Düzenle: popüler kısayollar

|Komutlar|Klavye kısayolları [özel bağlamlar]|Komut KIMLIĞI|
|-|-|-|
|Çizgiyi Böl|**Enter** [metin düzenleyicisi, Rapor Tasarımcısı, Windows Form Tasarımcısı]<br /><br />veya **SHIFT + enter** [metin düzenleyici]| Edit.BreakLine |
|Tanımlara Daralt|**CTRL + M**, **CTRL + O** [metin düzenleyici]| Düzenle. CollapseToDefinitions |
|Açıklama seçimi|**CTRL + K**, **CTRL + C** [metin düzenleyici]| Edit.CommentSelection |
|Sözcüğü Tamam|**Alt + sağ ok** [metin düzenleyici, iş akışı Tasarımcısı]<br /><br />veya **CTRL + Ara çubuğu** [metin düzenleyici, iş akışı Tasarımcısı]<br /><br />ya da **CTRL + K**, **W** [iş akışı Tasarımcısı]<br /><br />ya da **CTRL + K, CTRL + W** [iş akışı Tasarımcısı]| Edit.CompleteWord |
|Kopyala|**Ctrl+C**<br /><br />veya **Ctrl+Insert tuşlarına basın**| Edit.Copy |
|Kes|**Ctrl+X**<br /><br />veya **Shift+Delete**| Edit.Cut |
|Sil|**Sil** [Takım Gezgini]<br /><br />veya **Shift+Delete** [Sıra Diyagramı, UML Etkinlik Diyagramı, Katman Diyagramı]<br /><br />veya **Ctrl+Delete** [Sınıf Diyagramı]| Edit.Delete |
|Bul|**Ctrl+F**| Edit.Find |
|Tüm başvuruları bulma|**Shift+F12**| Edit.FindAllReferences |
|Dosyalarda bulma|**Ctrl+Shift+F**| Edit.FindinFiles |
|Sonrakini bul|**F3**| Edit.FindNext |
|Sonraki seçileni bul|**Ctrl+F3**| Edit.FindNextSelected |
|Belgeyi biçimlendir|**Ctrl+K, Ctrl+D** [Metin Düzenleyici]| Edit.FormatDocument |
|Biçim seçimi|**Ctrl+K, Ctrl+F** [Metin Düzenleyici]| Edit.FormatSelection |
|Git|**Ctrl+G**| Edit.GoTo |
|Bildirime git|**Ctrl+F12**| Edit.GoToDeclaration |
|Tanıma git|**F12**| Edit.GoToDefinition |
|Birleşik giriş bulmak için gidin|**Ctrl+D**| Edit.GoToFindCombo |
|Sonraki konuma gidin|**F8**| Edit.GoToNextLocation |
|Kod parçacığı ekleme|**Ctrl+K**, **Ctrl+X**| Edit.InsertSnippet |
|Ekle sekmesi|**Sekme** [Rapor Tasarımcısı, Windows Forms Tasarımcısı, Metin Düzenleyici]| Edit.InsertTab |
|Satır kesme|**Ctrl+L** [Metin Düzenleyici]| Edit.LineCut |
|Satır aşağı genişletme sütunu|**Shift+Alt+Aşağı Ok** [Metin Düzenleyici]| Edit.LineDownExtendColumn |
|Yukarıda açık satır|**Ctrl+Enter** [Metin Düzenleyici]| Edit.LineOpenAbove |
|Üyeleri listele|**Ctrl+J** [Metin Düzenleyici, İş Akışı Tasarımcısı]<br /><br />veya **Ctrl+K, Ctrl+L** [İş Akışı Tasarımcısı]<br /><br />veya **Ctrl+K, L** [İş Akışı Tasarımcısı]| Edit.ListMembers |
| sayfasına gidin|**Ctrl+,**| Edit.NavigateTo |
|Dosya aç|**Ctrl+Shift+G**| Edit.OpenFile |
|Overtype modu|**Ekle** [Metin Düzenleyici]| Edit.OvertypeMode |
|Parametre bilgileri|**Ctrl+Shift+Ara Çubuğu** [Metin Düzenleyici, İş Akışı Tasarımcısı]<br /><br />veya **Ctrl+K, Ctrl+P** [İş Akışı Tasarımcısı]<br /><br />veya **Ctrl+K, P** [İş Akışı Tasarımcısı]| Edit.ParameterInfo |
|Yapıştır|**Ctrl+V**<br /><br />veya **Shift+Insert**| Edit.Paste |
|Tanıma göz atma|**Alt+F12** [Metin Düzenleyici]| Edit.PeekDefinition |
|Yinele|**Ctrl+Y**<br /><br />veya **Shift+Alt+Geri Al**<br /><br />veya **Ctrl+Shift+Z**| Edit.Redo |
|Değiştir|**Ctrl+H**| Edit.Replace |
|Tümünü seç|**Ctrl+A**| Edit.SelectAll |
|Geçerli sözcüğü seçme|**Ctrl+W** [Metin Düzenleyici]| Edit.SelectCurrentWord |
|Seçim iptali|**Esc** [Metin Düzenleyici, Rapor Tasarımcısı, Ayarlar Tasarımcısı, Windows Forms Tasarımcısı, Yönetilen Kaynaklar Düzenleyicisi]| Edit.SelectionCancel |
|Çevrele|**Ctrl+K, Ctrl+S**| Edit.SurroundWith |
|Sekme sol|**Shift+Sekme** [Metin Düzenleyici, Rapor Tasarımcısı, Windows Forms Düzenleyicisi]| Edit.TabLeft |
|Tüm altı çizili düğmeyi değiştir|**Ctrl+M, Ctrl+L** [Metin Düzenleyici]| Edit.ToggleAllOutlining |
|Yer işaretini değiştir|**Ctrl+K, Ctrl+K** [Metin Düzenleyici]| Edit.ToggleBookmark |
|Tamamlama modunu değiştir|**Ctrl+Alt+Ara Çubuğu** [Metin Düzenleyici]| Edit.ToggleCompletionMode |
|Altı çizili genişletmeyi değiştir|**Ctrl+M, Ctrl+M** [Metin Düzenleyici]| Edit.ToggleOutliningExpansion |
|Uncomment selection|**Ctrl+K, Ctrl+U** [Metin Düzenleyici]| Edit.UncommentSelection |
|Geri Al|**Ctrl+Z**<br /><br />veya **Alt+Geri Al**| Edit.Undo |
|Sona kadar sözcük silme|**Ctrl+Delete** [Metin Düzenleyici]| Edit.WordDeleteToEnd |
|Başlamak için sözcük silme|**Ctrl+Geri Al** [Metin Düzenleyici]| Edit.WordDeleteToStart |

#### <a name="file-popular-shortcuts"></a>Dosya: popüler kısayollar

|Komutlar|Klavye kısayolları [Özel bağlamlar]|Komut Kimliği|
|-|-|-|
|Çıkış|**Alt+F4**| File.Exit |
|Yeni dosya|**Ctrl+N**| File.NewFile |
|Yeni proje|**Ctrl+Shift+N**| File.NewProject |
|Yeni web sitesi|**Shift+Alt+N**| File.NewWebSite |
|Dosya aç|**Ctrl+O**| File.OpenFile |
|Projeyi açma|**Ctrl+Shift+O**| File.OpenProject |
|Web sitesini açma|**Shift+Alt+O**| File.OpenWebSite |
|Rename|**F2** [Takım Gezgini]| File.Rename |
|Hepsini kaydet|**Ctrl+Shift+S**| File.SaveAll |
|Seçilen öğeleri kaydetme|**Ctrl+S**| File.SaveSelectedItems |
|Tarayıcıda görüntüleme|**Ctrl+Shift+W**| File.ViewinBrowser |

#### <a name="project-popular-shortcuts"></a>Project: popüler kısayollar

|Komutlar|Klavye kısayolları [Özel bağlamlar]|Komut Kimliği|
|-|-|-|
|Mevcut öğeyi ekleme|**Shift+Alt+A**| Project.AddExistingItem |
|Yeni öğe ekleme|**Ctrl+Shift+A**| Project.AddNewItem |

#### <a name="refactor-popular-shortcuts"></a>Yeniden düzenleme: popüler kısayollar

|Komut|Klavye kısayolu [Özel bağlamlar]|Komut Kimliği|
|-|-|-|
|Ayıklama metodu|**Ctrl+R, Ctrl+M**| Refactor.ExtractMethod |

#### <a name="tools-popular-shortcuts"></a>Araçlar: popüler kısayollar

|Komut|Klavye kısayolu [Özel bağlamlar]|Komut Kimliği|
|-|-|-|
|İşleme ekle|**Ctrl+Alt+P**| Tools.AttachtoProcess |

#### <a name="view-popular-shortcuts"></a>Görünüm: popüler kısayollar

|Komutlar|Klavye kısayolları [özel bağlamlar]|Komut KIMLIĞI|
|-|-|-|
|Sınıf Görünümü|**Ctrl+Shift+C**| View.ClassView |
|Etiketi Düzenle|**F2**| View.EditLabel |
|Hata listesi|**CTRL + \\ , CTRL + E**<br /><br />ya da **CTRL + \\ , E**| View.ErrorList |
|Geriye git|**CTRL +-**| View.NavigateBackward |
|İleri git|**CTRL + SHIFT +-**| View.NavigateForward |
|Nesne tarayıcısı|**Ctrl+Alt+J**| View.ObjectBrowser |
|Çıktı|**Ctrl+Alt+O**| View.Output |
|Özellik penceresi|**F4**| View.PropertiesWindow |
|Yenile|**F5** [Takım Gezgini]| View.Refresh |
|Sunucu Gezgini|**Ctrl+Alt+S**| View.ServerExplorer |
|Akıllı etiketi göster|**CTRL +.**<br /><br />veya **SHIFT + alt + F10** [HTML Düzenleyicisi tasarım görünümü]| View.ShowSmartTag |
|Çözüm gezgini|**Ctrl+Alt+L**| View.SolutionExplorer |
|TFS Takım Gezgini|**CTRL + \\ , CTRL + ı**| View.TfsTeamExplorer |
|Araç Kutusu|**Ctrl+Alt+X**| View.Toolbox |
|Kodu görüntüle|**ENTER** [sınıf diyagramı]<br /><br />or **F7** [Ayarlar tasarımcısı]| View.ViewCode |
|Görünüm tasarımcısı|**SHIFT + F7** [HTML düzenleyici kaynak görünümü]| View.ViewDesigner |

#### <a name="window-popular-shortcuts"></a>Pencere: popüler kısayollar

|Komutlar|Klavye kısayolları [özel bağlamlar]|Komut KIMLIĞI|
|-|-|-|
|Belge penceresini etkinleştir|**Esc**| Window.ActivateDocumentWindow |
|Belge penceresini kapat|**Ctrl+F4**| Window.CloseDocumentWindow |
|Sonraki belge penceresi|**Ctrl+F6**| Window.NextDocumentWindow |
|Sonraki belge penceresine git|**Ctrl+Sekme**| Window.NextDocumentWindowNav |
|Sonraki bölme bölmesi|**F6**| Window.NextSplitPane |


## <a name="global-shortcuts"></a>Genel kısayollar

bu klavye kısayolları *geneldir*, bu da Visual Studio bir pencere odağa sahip olduğunda bunları kullanabileceğiniz anlamına gelir.

- [Analiz](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_analyze)
- [Düzenle](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_edit)
- [Project](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_project)
- [Test](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_test)
- [Mimari](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_architecture)
- [Düzenleyici bağlam menüleri](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_editorContext)
- [Project ve çözüm bağlam menüleri](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_projectContext)
- [Test Gezgini](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_testexplorerGLOBAL)
- [Derleme](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_build)
- [Dosya](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_file)
- [Yeniden düzenleme](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_refactor)
- [Araçlar](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_tools)
- [Bağlam menülerini Sınıf Görünümü](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_classview)
- [Yardım](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_help)
- [Çözüm Gezgini](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_solutionexplorerGLOBAL)
- [Görünüm](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_view)
- [Hata Ayıklama](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_debug)
- [Yük testi](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_loadtest)
- [Team](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_team) (Takım)
- [Pencere](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_window)
- [Hata ayıklayıcı bağlam menüleri](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_debugger)
- [Diğer bağlam menüleri](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_otherContext)
- [Team Foundation bağlam menüleri](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_TFcontext)
- [Azure](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_windowsazure)
- [Tanılama hub’ı](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_diagnostics)

### <a name="analyze"></a><a name="bkmk_analyze"></a> Analiz

|Komutlar|Klavye kısayolları|Komut Kimliği|
|-|-|-|
|Geriye doğru gidin|**Shift+Alt+3**| Analyze.NavigateBackward |
|İleriye gidin|**Shift+Alt+4**| Analyze.NavigateForward |

### <a name="architecture"></a><a name="bkmk_architecture"></a> Mimari

|Komutlar|Klavye kısayolları|Komut Kimliği|
|-|-|-|
|Yeni diyagram|**Ctrl+ \\ , Ctrl+N**| Architecture.NewDiagram |

### <a name="build"></a><a name="bkmk_build"></a> Oluşturmak

|Komutlar|Klavye kısayolları|Komut Kimliği|
|-|-|-|
|Derleme seçimi|**Ctrl+B** (Visual Studio 2019)| Build.BuildSelection |
|Çözüm oluşturma|**Ctrl+Shift+B**| Build.BuildSolution |
|İptal|**Ctrl+Break tuşu**| Build.Cancel |
|Derlemek|**Ctrl+F7**| Build.Compile |
|Çözümde kod analizi çalıştırma|**Alt+F11**| Build.RunCodeAnalysisonSolution |

### <a name="class-view-context-menus"></a><a name="bkmk_classview"></a> Sınıf Görünümü menüleri

|Komutlar|Klavye kısayolları|Komut Kimliği|
|-|-|-|
|Özellikler|**Alt+Enter**| ClassViewContextMenus.ClassViewMultiselectProjectreferencesItems.Properties |

### <a name="debug"></a><a name="bkmk_debug"></a> Hata ayıklama

|Komutlar|Klavye kısayolları|Komut Kimliği|
|-|-|-|
|Kod değişikliklerini uygulama|**Alt+F10**| Debug.ApplyCodeChanges |
|İşleme ekleme|**Ctrl+Alt+P**| Debug.AttachtoProcess |
|Otomobil|**Ctrl+Alt+V, A**| Debug.Autos |
|Hepsini kesme|**Ctrl+Alt+Break tuşu**| Debug.BreakAll |
|Kesme noktaları|**Ctrl+Alt+B**| Debug.Breakpoints |
|Çağrı yığını|**Ctrl+Alt+C**| Debug.CallStack |
|Tüm kesme noktaları silin|**Ctrl+Shift+F9**| Debug.DeleteAllBreakpoints |
|Başlat|**Alt+F2**| Debug.DiagnosticsHub.Launch |
|Demontaj|**Ctrl+Alt+D**| Debug.Disassembly |
|Dom gezgini|**Ctrl+Alt+V, D**| Debug.DOMExplorer |
|Kesme noktası etkinleştirme|**Ctrl+F9**| Debug.EnableBreakpoint |
|Özel durumlar|**Ctrl+Alt+E**| Debug.Exceptions |
|İşlev kesme noktası|**Ctrl+K, B** (Visual Studio 2019)<br />**Ctrl tuşunu basılı tutarak** + **B** (Visual Studio 2017)| Debug.FunctionBreakpoint |
|Önceki çağrıya veya IntelliTrace olayına gidin|**Ctrl+Shift+F11**| Debug.GoToPreviousCallorIntelliTraceEvent |
|Tanılamayı başlatma|**Alt+F5**| Debug.Graphics.StartDiagnostics |
|Hemen|**Ctrl+Alt+I**| Debug.Immediate |
|IntelliTrace çağrıları|**Ctrl+Alt+Y, T**| Debug.IntelliTraceCalls |
|IntelliTrace olayları|**Ctrl+Alt+Y, F**| Debug.IntelliTraceEvents |
|JavaScript Konsolu|**Ctrl+Alt+V, C**| Debug.JavaScriptConsole |
|Ayarlanmalıdır|**Ctrl+Alt+V, L**| Debug.Locals |
|İşlem açılan kutusu|**Ctrl+5**| Debug.LocationToolbar.ProcessCombo |
|Yığın çerçevesi açılan kutusu|**Ctrl+7**| Debug.LocationToolbar.StackFrameCombo |
|İş parçacığı açılan kutusu|**Ctrl+6**| Debug.LocationToolbar.ThreadCombo |
|Geçerli iş parçacığının bayrak durumuna geç|**Ctrl+8**| Debug.LocationToolbar.ToggleCurrentThreadFlaggedState |
|Bayraklı iş parçacıklarını değiştirme|**Ctrl+9**| Debug.LocationToolbar.ToggleFlaggedThreads |
|Bellek 1|**Ctrl+Alt+M, 1**| Debug.Memory1 |
|Bellek 2|**Ctrl + alt + a, 2**| Debug.Memory2 |
|Bellek 3|**Ctrl + alt + a, 3**| Debug.Memory3 |
|Bellek 4|**Ctrl + alt + a, 4**| Debug.Memory4 |
|Modül|**Ctrl+Alt+U**| Debug.Modules |
|Paralel Yığınlar|**Ctrl+Shift+D, S**| Debug.ParallelStacks |
|Paralel izleme 1|**Ctrl+Shift+D, 1**| Debug.ParallelWatch1 |
|Paralel izleme 2|**CTRL + SHIFT + D, 2**| Debug.ParallelWatch2 |
|Paralel izleme 3|**CTRL + SHIFT + D, 3**| Debug.ParallelWatch3 |
|Paralel izleme 4|**CTRL + SHIFT + D, 4**| Debug.ParallelWatch4 |
|İşlemler|**Ctrl+Alt+Z**| Debug.Processes |
|Hızlı Bakış|**SHIFT + F9** ya da **Ctrl + Alt + Q**| Debug.QuickWatch |
|İşleme yeniden iliştir|**Shift+Alt+P**| Hata Ayıkla. yeniden Iliştirchtoprocess |
|WindowsApp 'yi Yenile|**Ctrl+Shift+R**| Debug.RefreshWindowsapp |
|Kayıtların|**Ctrl+Alt+G**| Debug.Registers |
|Yeniden başlat|**Ctrl+Shift+F5**| Debug.Restart |
|İmlece kadar Çalıştır|**Ctrl+F10**| Debug.RunToCursor |
|Sonraki ifadeyi ayarla|**Ctrl+Shift+F10**| Debug.SetNextStatement |
|Kod haritasında çağrı yığınını göster|**CTRL + SHIFT + '**| Debug.ShowCallStackonCodeMap |
|Sonraki ifadeyi göster|**Alt + NUM** *| Debug.ShowNextStatement |
|Başlangıç|**F5**| Debug.Start |
|Windows Phone uygulama analizini Başlat|**Alt+F1**| Debug.StartWindowsPhoneApplicationAnalysis |
|Hata ayıklama olmadan Başlat|**Ctrl+F5**| Debug.StartWithoutDebugging |
|Adımla|**F11**| Debug.StepInto |
|Geçerli işleme adımla|**Ctrl+Alt+F11**| Debug.StepIntoCurrentProcess |
|Belirli bir adımla|**Shift+Alt+F11**| Debug.StepIntoSpecific |
|Dışarı adımla|**Shift+F11**| Debug.StepOut |
|Geçerli işlemi adımla|**Ctrl+Shift+Alt+F11**| Debug.StepOutCurrentProcess |
|Adımla|**F10** (hata ayıklama sırasında: eylem üzerinde bir adım gerçekleştirir)| Debug.StepOver |
|Adımla|**F10** (hata ayıklama olmadığında: Kullanıcı kodunun ilk satırında hata ayıklamaya başlar ve duraklar)| Debug.StepOver |
|Geçerli işlemin üzerinde adımla|**Ctrl+Alt+F10**| Debug.StepOverCurrentProcess |
|Hata ayıklamayı Durdur|**Shift+F5**| Debug.StopDebugging |
|Performans analizini durdur|**Shift+Alt+F2**| Debug.StopPerformanceAnalysis |
|Görevler|**Ctrl+Shift+D, K**| Debug.Tasks |
|İş Parçacıkları|**Ctrl+Alt+H**| Debug.Threads |
|Kesme noktasını aç|**F9**| Debug.ToggleBreakpoint |
|Ayrıştırılmış derlemeyi değiştirme|**Ctrl+F11**| Debug.ToggleDisassembly |
|1 izleyin|**Ctrl+Alt+W, 1**| Debug.Watch1 |
|2. gözcü|**CTRL + ALT + W, 2**| Debug.Watch2 |
|3. gözcü|**CTRL + ALT + W, 3**| Debug.Watch3 |
|4 izleyin|**CTRL + ALT + W, 4**| Debug.Watch4 |

### <a name="debugger-context-menus"></a><a name="bkmk_debugger"></a> Hata ayıklayıcı bağlam menüleri

|Komutlar|Klavye kısayolları|Komut KIMLIĞI|
|-|-|-|
|Sil|**Alt+F9, D**| DebuggerContextMenus.BreakpointsWindow.Delete |
|Ayrıştırılmış koda git|**Alt+F9, A**| DebuggerContextMenus.BreakpointsWindow.GoToDisassembly |
|Kaynak koduna git|**Alt+F9, S**| DebuggerContextMenus.BreakpointsWindow.GoToSourceCode |

### <a name="diagnostics-hub"></a><a name="bkmk_diagnostics"></a> Tanılama Merkezi

|Komut|Klavye kısayolu|Komut KIMLIĞI|
|-|-|-|
|Toplamayı durdur|**Ctrl+Alt+F2**| DiagnosticsHub.StopCollection |

### <a name="edit"></a><a name="bkmk_edit"></a> Düzenle

|Komutlar|Klavye kısayolları|Komut KIMLIĞI|
|-|-|-|
|Kopyala|**Ctrl+C**<br /><br /> veya<br /><br /> **Ctrl+Ins**| Edit.Copy |
|Kes|**Ctrl+X**<br /><br /> veya<br /><br /> **Shift+Delete**| Edit.Cut |
|Geçiş panosu halkası|**Ctrl+Shift+V**<br /><br /> veya<br /><br /> **Ctrl+Shift+Ins**| Edit.CycleClipboardRing |
|Sil|**Silme**| Edit.Delete |
|Yinele|**Ctrl+D**| Düzenle. Yinele |
|Bul|**Ctrl+F**| Edit.Find |
|Tüm başvuruları bul|**Shift+F12**| Edit.FindAllReferences |
|Dosyalarda bul|**Ctrl+Shift+F**| Edit.FindinFiles |
|Sonrakini bul|**F3**| Edit.FindNext |
|Sonraki seçileni bul|**Ctrl+F3**| Edit.FindNextSelected |
|Öncekini bul|**Shift+F3**| Edit.FindPrevious |
|Önceki seçileni bul|**Ctrl+Shift+F3**| Edit.FindPreviousSelected |
|Metot oluşturma|**Ctrl+K, Ctrl+M**| Edit.GenerateMethod |
|Git|**Ctrl+G**| Edit.GoTo |
|Tamam'a gidin|**Ctrl+veya** **Ctrl+T**| Edit.GoToAll |
|Bildirime git|**Ctrl+F12**| Edit.GoToDeclaration |
|Tanıma git|**F12**| Edit.GoToDefinition |
|Üyeye git|**Ctrl+1, Ctrl+M** veya **Ctrl+1, M** veya **Alt+ \\**| Edit.GoToMember |
|Sonraki konuma gidin|**F8** (Hata Listesi veya Çıkış penceresinde sonraki hata)| Edit.GoToNextLocation |
|Ön konuma gidin|**Shift+F8** (Hata Listesi veya Çıkış penceresinde önceki hata)| Edit.GoToPrevLocation |
|Kod parçacığı ekleme|**Ctrl+K, Ctrl+X**| Edit.InsertSnippet |
|Denetimi aşağı taşıma|**Ctrl+Aşağı Ok**| Edit.MoveControlDown |
|Denetimi aşağı kılavuza taşıma|**Aşağı Ok**| Edit.MoveControlDownGrid |
|Denetimi sola taşıma|**Ctrl+Sol Ok**| Edit.MoveControlLeft |
|Denetimi sol kılavuza taşıma|**Sol Ok**| Edit.MoveControlLeftGrid |
|Denetimi sağa taşıma|**Ctrl+Sağ Ok**| Edit.MoveControlRight |
|Denetimi sağ kılavuza taşıma|**Sağ Ok**| Edit.MoveControlRightGrid |
|Denetimi yukarı taşıma|**Ctrl+Yukarı Ok**| Edit.MoveControlUp |
|Denetimi yukarı kılavuza taşıma|**Yukarı Ok**| Edit.MoveControlUpGrid |
|Sonraki yer işareti|**Ctrl+K, Ctrl+N**| Edit.NextBookmark |
|Klasördeki sonraki yer işareti|**Ctrl+Shift+K, Ctrl+Shift+N**| Edit.NextBookmarkInFolder |
|Dosyayı açma|**Ctrl+Shift+G** (İmleç altında dosya adını açar)| Edit.OpenFile |
|Yapıştır|**Ctrl+V**<br /><br /> veya<br /><br /> **Shift+Ins**| Edit.Paste |
|Önceki yer işareti|**Ctrl+K, Ctrl+P**| Edit.PreviousBookmark |
|Klasördeki önceki yer işareti|**Ctrl+Shift+K, Ctrl+Shift+P**| Edit.PreviousBookmarkInFolder |
|Hızlı bul simgesi|**Shift+Alt+F12**| Edit.QuickFindSymbol |
|Yinele|**Ctrl+Y**<br /><br /> veya<br /><br /> **Ctrl+Shift+Z**<br /><br /> veya<br /><br /> **Shift+Alt+Geri Al tuşu**| Edit.Redo |
|Uzak başvuruları yenileme|**Ctrl+Shift+J**| Edit.RefreshRemoteReferences |
|Değiştir|**Ctrl+H**| Edit.Replace |
|Dosyalarda değiştirme|**Ctrl+Shift+H**| Edit.ReplaceinFiles |
|Tümünü seç|**Ctrl+A**| Edit.SelectAll |
|Sonraki denetimi seçin|**Sekme**| Edit.SelectNextControl |
|Önceki denetimi seçme|**Shift+Sekme Tuşu**| Edit.SelectPreviousControl |
|Kutucuk kılavuzu gösterme|**Enter**| Edit.ShowTileGrid |
|Boyut denetimi aşağı|**Ctrl+Shift+Aşağı Ok**| Edit.SizeControlDown |
|Boyut denetimi aşağı kılavuz|**Shift+Aşağı Ok**| Edit.SizeControlDownGrid |
|Boyut denetimi sola|**Ctrl+Shift+Sol Ok**| Edit.SizeControlLeft |
|Boyut denetimi sol kılavuz|**Shift+Sol Ok**| Edit.SizeControlLeftGrid |
|Boyut denetimi hakkı|**Ctrl+Shift+Sağ Ok**| Edit.SizeControlRight |
|Boyut denetimi sağ kılavuzu|**Shift+Sağ Ok**| Edit.SizeControlRightGrid |
|Boyut denetimi|**Ctrl+Shift+Yukarı Ok**| Edit.SizeControlUp |
|Kılavuzda boyut denetimi|**Shift+Yukarı Ok**| Edit.SizeControlUpGrid |
|Arama durdurma|**Alt+F3, S**| Edit.StopSearch |
|Çevrele|**Ctrl+K, Ctrl+S**| Edit.SurroundWith |
|Geri Al|**Ctrl+Z**<br /><br /> veya<br /><br /> **Alt+Geri Al tuşu**| Edit.Undo |

### <a name="editor-context-menus"></a><a name="bkmk_editorContext"></a> Düzenleyici bağlam menüleri

|Komutlar|Klavye kısayolları|Komut Kimliği|
|-|-|-|
|Kesme noktası koşulları|**Alt+F9, C**| EditorContextMenus.CodeWindow.Breakpoint.BreakpointConditions |
|Kesme noktası etiketleri düzenleme|**Alt+F9, L**| EditorContextMenus.CodeWindow.Breakpoint.BreakpointEditlabels |
|Öğeyi göster|**Ctrl+'**| EditorContextMenus.CodeWindow.CodeMap.ShowItem |
|Yürütme|**Ctrl+Alt+F5**| EditorContextMenus.CodeWindow.Execute |
|Görünüme git|**Ctrl+M, Ctrl+G**| EditorContextMenus.CodeWindow.GoToView |
|Üst bilgi kod dosyasını aç/kapat|**Ctrl+K, Ctrl+O** ('O' harfi)| EditorContextMenus.CodeWindow.ToggleHeaderCodeFile |
|Çağrı hiyerarşisini görüntüleme|**Ctrl+K, Ctrl+T**<br /><br /> veya<br /><br /> **Ctrl+K, T**| EditorContextMenus.CodeWindow.ViewCallHierarchy |

### <a name="file"></a><a name="bkmk_file"></a> Dosya

|Komutlar|Klavye kısayolları|Komut Kimliği|
|-|-|-|
|Çıkış|**Alt+F4**| File.Exit |
|Yeni dosya|**Ctrl+N**| File.NewFile |
|Yeni proje|**Ctrl+Shift+N**| File.NewProject |
|Yeni web sitesi|**Shift+Alt+N**| File.NewWebSite |
|Dosyayı açma|**Ctrl+O** ('O' harfi)| File.OpenFile |
|Projeyi açma|**Ctrl+Shift+O** ('O' harfi)| File.OpenProject |
|Web sitesini açma|**Shift+Alt+O** ('O' harfi)| File.OpenWebSite |
|Yazdır|**Ctrl+P**| File.Print |
|Hepsini kaydet|**Ctrl+Shift+S**| File.SaveAll |
|Seçili öğeleri kaydetme|**Ctrl+S**| File.SaveSelectedItems |
|Tarayıcıda görüntüleme|**Ctrl+Shift+W**| File.ViewinBrowser |

### <a name="help"></a><a name="bkmk_help"></a> Yardım

|Komutlar|Klavye kısayolları|Komut Kimliği|
|-|-|-|
|Yardım içeriği ekleme ve kaldırma|**Ctrl+Alt+F1**| Help.AddandRemoveHelpContent |
|F1 yardımı|**F1**| Help.F1Help |
|Yardımı görüntüleme|**Ctrl+F1**| Help.ViewHelp |
|Pencere yardımı|**Shift+F1**| Help.WindowHelp |

### <a name="load-test"></a><a name="bkmk_loadtest"></a> Yük testi

|Komut|Klavye kısayolu|Komut Kimliği|
|-|-|-|
|Sayaç bölmesine atla|**Ctrl+R, Q**| LoadTest.JumpToCounterPane |

### <a name="other-context-menus"></a><a name="bkmk_otherContext"></a> Diğer bağlam menüleri

|Komut|Klavye kısayolu|Komut Kimliği|
|-|-|-|
|Yeni diyagram ekleme|**Ekle**| OtherContextMenus.MicrosoftDataEntityDesignContext.AddNewDiagram |

### <a name="project"></a><a name="bkmk_project"></a> Proje

|Komutlar|Klavye kısayolları|Komut Kimliği|
|-|-|-|
|Mevcut öğeyi ekleme|**Shift+Alt+A**| Project.AddExistingItem |
|Yeni öğe ekleme|**Ctrl+Shift+A**| Project.AddNewItem |
|Sınıf sihirbazı|**Ctrl+Shift+X**| Project.ClassWizard |
|Geçersiz kıl|**Ctrl+Alt+Ins**| Project.Override |
|Değişiklikleri önizleme|**Alt+;** ardından **Alt+C**| Project.Previewchanges |
|Seçilen dosyaları yayımlama|**Alt+;** ardından **Alt+P**| Project.Publishselectedfiles |
|Sunucudan seçilen dosyaları değiştirme|**Alt+;** ardından **Alt+R**| Project.Replaceselectedfilesfromserver |

### <a name="project-and-solution-context-menus"></a><a name="bkmk_projectContext"></a>Project ve çözüm bağlam menüleri

|Komutlar|Klavye kısayolları|Komut Kimliği|
|-|-|-|
|Aşağı taşı|**Alt+Aşağı Ok**| ProjectandSolutionContextMenus.Item.MoveDown |
|Yukarı taşı|**Alt+Yukarı Ok**| ProjectandSolutionContextMenus.Item.MoveUp |

### <a name="refactor"></a><a name="bkmk_refactor"></a> Yeniden düzenleme

|Komutlar|Klavye kısayolları|Komut Kimliği|
|-|-|-|
|Alanı kapsülleme|**Ctrl+R, Ctrl+E**| Refactor.EncapsulateField |
|Ayıklama arabirimi|**Ctrl+R, Ctrl+I**| Refactor.ExtractInterface |
|Ayıklama metodu|**Ctrl+R, Ctrl+M**| Refactor.ExtractMethod |
|Parametreleri kaldırma|**Ctrl+R, Ctrl+V**| Refactor.RemoveParameters |
|Rename|**Ctrl+R, Ctrl+R**| Refactor.Rename |
|Parametreleri yeniden sıralama|**Ctrl+R, Ctrl+O** ('O' harfi)| Refactor.ReorderParameters |

### <a name="solution-explorer"></a><a name="bkmk_solutionexplorerGLOBAL"></a> Çözüm Gezgini

|Komutlar|Klavye kısayolları|Komut KIMLIĞI|
|-|-|-|
|Açık dosyalar filtresi|**CTRL + [**, **O** (harf ' O ')<br /><br /> veya<br /><br /> **CTRL + [**, **CTRL + O** (harf ' O ')| SolutionExplorer.OpenFilesFilter |
|Bekleyen değişiklikler filtresi|**CTRL + [**, **P**<br /><br /> veya<br /><br /> **CTRL + [**, **CTRL + P**| SolutionExplorer.PendingChangesFilter |
|Etkin belge ile Eşitle|**CTRL + [**, **S**<br /><br /> veya<br /><br /> **CTRL + [**, **CTRL + S**| SolutionExplorer.SyncWithActiveDocument |

### <a name="team"></a><a name="bkmk_team"></a> Takım

|Komutlar|Klavye kısayolları|Komut KIMLIĞI|
|-|-|-|
|Git dallarına git|**CTRL + 0** (sıfır), **CTRL + N**<br /><br /> veya<br /><br /> **Ctrl+0, N**| Team.Git.GoToGitBranches |
|Git değişikliklerine git|**CTRL + 0** (sıfır), **CTRL + G**<br /><br /> veya<br /><br /> **Ctrl+0, G**| Team.Git.GoToGitChanges |
|Git yürütmelerine git|**CTRL + 0** (sıfır), **CTRL + O** (harf ' O ')<br /><br /> veya<br /><br /> **Ctrl+0, O**| Team.Git.GoToGitCommits |
|Takım Gezgini araması|**CTRL + '**| Team.TeamExplorerSearch |

### <a name="team-foundation-context-menus"></a><a name="bkmk_TFcontext"></a> Team Foundation bağlam menüleri

|Komutlar|Klavye kısayolları|Komut KIMLIĞI|
|-|-|-|
|Derlemeler 'e git|**CTRL + 0** (sıfır), **CTRL + B**<br /><br /> veya<br /><br /> **Ctrl+0, B**| TeamFoundationContextMenus.Commands.GoToBuilds |
|Bağlan 'a git|**CTRL + 0** (sıfır), **CTRL + C**<br /><br /> veya<br /><br /> **Ctrl+0, C**| TeamFoundationContextMenus.Commands.GoToConnect |
|Belgelere git|**CTRL + 0** (sıfır), **CTRL + D**<br /><br /> veya<br /><br /> **Ctrl+0, D**| TeamFoundationContextMenus.Commands.GoToDocuments |
|Girişe git|**CTRL + 0** (sıfır), **CTRL + H**<br /><br /> veya<br /><br /> **Ctrl+0, H**| TeamFoundationContextMenus.Commands.GoToHome |
|Çalışmam 'a git|**CTRL + 0** (sıfır), **CTRL + ı**<br /><br /> veya<br /><br /> **Ctrl+0, M**| TeamFoundationContextMenus.Commands.GoToMyWork |
|Bekleyen değişikliklere git|**CTRL + 0** (sıfır), **CTRL + P**<br /><br /> veya<br /><br /> **Ctrl+0, P**| TeamFoundationContextMenus.Commands.GoToPendingChanges |
|Raporlara git|**CTRL + 0** (sıfır), **CTRL + R**<br /><br /> veya<br /><br /> **Ctrl+0, R**| TeamFoundationContextMenus.Commands.GoToReports |
|Ayarlar 'a git|**CTRL + 0** (sıfır), **CTRL + S**<br /><br /> veya<br /><br /> **Ctrl+0, S**| TeamFoundationContextMenus.Commands.GoToSettings |
|Web erişimi 'ne git|**CTRL + 0** (sıfır), **CTRL + A**<br /><br /> veya<br /><br /> **Ctrl+0, A**| TeamFoundationContextMenus.Commands.GoToWebAccess |
|İş öğelerine git|**CTRL + 0** (sıfır), **CTRL + W**<br /><br /> veya<br /><br /> **Ctrl+0, W**| TeamFoundationContextMenus.Commands.GoToWorkItems |

### <a name="test"></a><a name="bkmk_test"></a> Sınamanız

|Komutlar|Klavye kısayolları|Komut KIMLIĞI|
|-|-|-|
|Kodlanmış UI Test Oluşturucusu kullan|**CTRL + \\ , CTRL + C**| Test.UseCodedUITestBuilder |
|Var olan eylem kaydını kullan|**CTRL + \\ , CTRL + A**| Test.UseExistingActionRecording |

### <a name="test-explorer"></a><a name="bkmk_testexplorerGLOBAL"></a> Test Gezgini

|Komutlar|Klavye kısayolları|Komut KIMLIĞI|
|-|-|-|
|Tüm testlerde hata ayıkla|**Ctrl+R, Ctrl+A**| TestExplorer.DebugAllTests |
|Bağlamdaki tüm testlerde hata ayıkla|**Ctrl+R, Ctrl+T**| TestExplorer.DebugAllTestsInContext |
|Son çalıştırmada hata ayıkla|**CTRL + R, D**| TestExplorer. DebugLastRun |
|Son çalıştırmayı Yinele|**Ctrl+R, L**| TestExplorer.RepeatLastRun |
|Tüm Testleri Çalıştır|**Ctrl+R, A**| TestExplorer.RunAllTests |
|Tüm testleri bağlamda Çalıştır|**Ctrl+R, T**| TestExplorer.RunAllTestsInContext |
|Test Gezginini göster|**CTRL + E, T**| TestExplorer. ShowTestExplorer |
|Sekmeyi aç|**CTRL + E, L**| LiveUnitTesting. OpenTab |
|Kod kapsamı sonuçları|**Ctrl+E, C**| Test. CodeCoverageResults |

### <a name="tools"></a><a name="bkmk_tools"></a> Aracı

|Komutlar|Klavye kısayolları|Komut KIMLIĞI|
|-|-|-|
|İşleme ekle|**Ctrl+Alt+P**| Tools.AttachtoProcess |
|Kod parçacıkları Yöneticisi|**Ctrl+K, Ctrl+B**| Tools.CodeSnippetsManager |
|GC 'yi zorla|**Ctrl+Shift+Alt+F12, Ctrl+Shift+Alt+F12**| Tools.ForceGC |

### <a name="view"></a><a name="bkmk_view"></a> Görünümü

|Komutlar|Klavye kısayolları|Komut KIMLIĞI|
|-|-|-|
|Tüm pencereler|**Shift+Alt+M**| View.AllWindows |
|Mimari Gezgini|**CTRL + \\ , CTRL + R**| View.ArchitectureExplorer |
|Geri|**Alt + sol ok** (metin düzenleyicisinde View. navigategeri geriye doğru işlevler)| View.Backward |
|Yer işareti penceresi|**Ctrl+K, Ctrl+W**| View.BookmarkWindow |
|Sonrakine Git|**Ctrl+Shift+1**| View.BrowseNext |
|Öncekine gözatamıyorum|**Ctrl+Shift+2**| View.BrowsePrevious |
|Çağrı hiyerarşisi|**Ctrl+Alt+K**| View.CallHierarchy |
|Sınıf Görünümü|**Ctrl+Shift+C**| View.ClassView |
|Sınıf görünümü arama Birleşik giriş kutusuna git|**Ctrl+K, Ctrl+V**| View.ClassViewGoToSearchCombo |
|Kod tanımı penceresi|**CTRL + \\ , D**<br /><br /> veya<br /><br /> **CTRL + \\ , CTRL + D**| View.CodeDefinitionWindow |
|Komut penceresi|**Ctrl+Alt+A**| View.CommandWindow |
|Veri kaynakları|**Shift+Alt+D**| View.DataSources |
|Belge ana hattı|**Ctrl+Alt+T**| View.DocumentOutline |
|Etiketi Düzenle|**F2**| View.EditLabel |
|Hata listesi|**CTRL + \\ , E**<br /><br /> veya<br /><br /> **Ctrl+ \\ , Ctrl+E**| View.ErrorList |
|F# etkileşimli|**Ctrl+Alt+F**| View.F#Interactive |
|Sembol sonuçlarını bulma|**Ctrl+Alt+F12**| View.FindSymbolResults |
|İleri|**Alt+Sağ Ok**  (Metin Düzenleyicisi'nde View.NavigateForward'tan farklı işlevler)| View.Forward |
|İleri göz atma bağlamı|**Ctrl+Shift+7**| View.ForwardBrowseContext |
|Tam ekran|**Shift+Alt+Enter**| View.FullScreen |
|Geriye doğru gidin|**Ctrl+-**| View.NavigateBackward |
|İleriye gidin|**Ctrl+Shift+-**| View.NavigateForward |
|Sonraki hata|**Ctrl+Shift+F12**| View.NextError |
|Bildirimler|**Ctrl+W, N**<br /><br /> veya<br /><br /> **Ctrl+W, Ctrl+N**| View.Notifications |
|Nesne tarayıcısı|**Ctrl+Alt+J**| View.ObjectBrowser |
|Nesne tarayıcısı arama birleşik giriş|**Ctrl+K, Ctrl+R**| View.ObjectBrowserGoToSearchCombo |
|Çıktı|**Ctrl+Alt+O** ('O' harfi)| View.Output |
|Açılır göz atma bağlamı|**Ctrl+Shift+8** (yalnızca C++)| View.PopBrowseContext |
|Özellik penceresi|**F4**| View.PropertiesWindow |
|Özellik sayfaları|**Shift+F4**| View.PropertyPages |
|Kaynak görünümü|**Ctrl+Shift+E**| View.ResourceView |
|Sunucu gezgini|**Ctrl+Alt+S**| View.ServerExplorer |
|Akıllı etiketi göster|**Shift+Alt+F10**<br /><br /> veya<br /><br /> **Ctrl+.**| View.ShowSmartTag |
|Çözüm gezgini|**Ctrl+Alt+L**| View.SolutionExplorer |
|SQL sunucusu nesne gezgini|**Ctrl+ \\ , Ctrl+S**| View.SQLServerObjectExplorer |
|Görev listesi|**Ctrl+ \\ , T**<br /><br /> veya<br /><br /> **Ctrl+ \\ , Ctrl+T**| View.TaskList |
|TFS takım gezgini|**Ctrl+ \\ , Ctrl+M**| View.TfsTeamExplorer |
|Araç Kutusu|**Ctrl+Alt+X**| View.Toolbox |
|UML model gezgini|**Ctrl+ \\ , Ctrl+U**| View.UMLModelExplorer |
|Kodu görüntüleme|**F7**| View.ViewCode |
|Görünüm tasarımcısı|**Shift+F7**| View.ViewDesigner |
|Web tarayıcısı|**Ctrl+Alt+R**| View.WebBrowser |
|Yakınlaştır|**Ctrl+Shift+.**| View.ZoomIn |
|Uzaklaştır|**Ctrl+Shift+,**| View.ZoomOut |
|Test Gezginini Göster|**Ctrl+E, T**| TestExplorer.ShowTestExplorer |

### <a name="window"></a><a name="bkmk_window"></a> Pencere

|Komutlar|Klavye kısayolları|Komut KIMLIĞI|
|-|-|-|
|Belge penceresini etkinleştir|**Esc**| Window.ActivateDocumentWindow |
|Seçime sekme ekle|**Ctrl+Shift+Alt+Ara Çubuğu**| Window.AddTabtoSelection |
|Belge penceresini kapat|**Ctrl+F4**| Window.CloseDocumentWindow |
|Araç penceresini kapat|**Shift+Esc**| Window.CloseToolWindow |
|Sekmeyi açık tut|**Ctrl+Alt+Home**| Window.KeepTabOpen |
|Gezinti çubuğuna taşı|**Ctrl+F2**| Window.MovetoNavigationBar |
|Sonraki belge penceresi|**Ctrl+F6**| Window.NextDocumentWindow |
|Sonraki belge penceresine git|**Ctrl+Sekme**| Window.NextDocumentWindowNav |
|Sonraki bölme|**Alt+F6**| Window.NextPane |
|Sonraki bölme bölmesi|**F6**| Window.NextSplitPane |
|Sonraki sekme|**Ctrl+Alt+PgDn**<br /><br /> veya<br /><br /> **Ctrl+PgDn**| Window.NextTab |
|Sonraki sekme ve Seçime Ekle|**Ctrl+Shift+Alt+PgDn**| Window.NextTabandAddtoSelection |
|Sonraki araç penceresine git|**Alt+F7**| Window.NextToolWindowNav |
|Önceki belge penceresi|**Ctrl+Shift+F6**| Window.PreviousDocumentWindow |
|Önceki belge penceresine git|**Ctrl+Shift+Sekme**| Window.PreviousDocumentWindowNav |
|Önceki bölme|**Shift+Alt+F6**| Window.PreviousPane |
|Önceki bölme bölmesi|**Shift+F6**| Window.PreviousSplitPane |
|Önceki sekme|**Ctrl+Alt+PgUp**<br /><br /> veya<br /><br /> **Ctrl+PgUp**| Window.PreviousTab |
|Önceki sekme ve Seçime Ekle|**Ctrl+Shift+Alt+PgUp**| Window.PreviousTabandAddtoSelection |
|Önceki araç penceresi gezintisi|**Shift+Alt+F7**| Window.PreviousToolWindowNav |
|Hızlı Başlat|**Ctrl+Q**| Window.QuickLaunch |
|Önceki kategoriyi Hızlı Başlat|**Ctrl+Shift+Q**| Window.QuickLaunchPreviousCategory |
|Dock menüsünü göster|**Alt +-**| Window.ShowDockMenu |
|EX MDI dosya listesini göster|**Ctrl+Alt+Aşağı Ok**| Window.ShowEzMDIFileList |
|Çözüm Gezgini araması|**CTRL +;**| Window.SolutionExplorerSearch |
|Pencere arama|**Alt + '**| Window.WindowSearch |

### <a name="azure"></a><a name="bkmk_windowsazure"></a> Mavisi

|Komutlar|Klavye kısayolları|Komut KIMLIĞI|
|-|-|-|
|Mobil Hizmet betiği işlemini yeniden dene|**CTRL + NUM \* , CTRL + R**| WindowsAzure.RetryMobileServiceScriptOperation |
|Mobil Hizmet betiği hata ayrıntılarını göster|**CTRL + NUM \* , CTRL + D**| WindowsAzure.ShowMobileServiceScriptErrorDetails |

## <a name="context-specific-shortcuts"></a>Bağlama özgü kısayollar


### <a name="adonet-entity-data-model-designer"></a>ADO.NET Varlık Veri Modeli Tasarımcısı

Bu içeriğe özgü kısayollar şunlardır:

|Komutlar|Klavye kısayolları|Komut KIMLIĞI|
|-|-|-|
|Aşağı|**Alt+Aşağı Ok**| OtherContextMenus.MicrosoftDataEntityDesignContext.MoveProperties.Down |
|Aşağı 5|**Alt+PgDn**| OtherContextMenus.MicrosoftDataEntityDesignContext.MoveProperties.Down5 |
|Alta|**Alt+End**| OtherContextMenus.MicrosoftDataEntityDesignContext.MoveProperties.ToBottom |
|Üste|**Alt+Home**| OtherContextMenus.MicrosoftDataEntityDesignContext.MoveProperties.ToTop |
|Yukarı|**Alt+Yukarı Ok**| OtherContextMenus.MicrosoftDataEntityDesignContext.MoveProperties.Up |
|En fazla 5|**Alt+PgUp**| OtherContextMenus.MicrosoftDataEntityDesignContext.MoveProperties.Up5 |
|Rename|**Ctrl+R, R**| OtherContextMenus.MicrosoftDataEntityDesignContext.Refactor.Rename |
|Diyagramdan kaldır|**Shift+Del**| OtherContextMenus.MicrosoftDataEntityDesignContext.RemovefromDiagram |
|Varlık veri modeli tarayıcısı|**CTRL + 1**| View.EntityDataModelBrowser |
|Varlık veri modeli eşleme ayrıntıları|**Ctrl+2**| View.EntityDataModelMappingDetails |

### <a name="class-diagram"></a>Sınıf diyagramı

Bu içeriğe özgü kısayollar şunlardır:


|Komutlar|Klavye kısayolları|Komut KIMLIĞI|
|-|-|-|
|Daralt|**Num -**| ClassDiagram.Collapse |
|Genişlet|**NUM +**| ClassDiagram.Expand |
|Sil|**Ctrl+Del**| Edit.Delete |
|Expand temel tür listesini Daralt|**Shift+Alt+B**| Edit.ExpandCollapseBaseTypeList |
|Lolipop 'a git|**Shift+Alt+L**| Edit.NavigateToLollipop |
|Diyagramdan kaldır|**Silme**| Edit.RemovefromDiagram |
|Kodu görüntüle|**Enter**| View.ViewCode |

### <a name="coded-ui-test-editor"></a>Kodlanmış UI Test Düzenleyicisi

Bu içeriğe özgü kısayollar şunlardır:


|Komutlar|Klavye kısayolları|Komut KIMLIĞI|
|-|-|-|
|Başvuruyu panoya kopyala|**Ctrl+C**| OtherContextMenus.UITestEditorContextMenu.CopyReferencetoClipboard |
|Öncesine gecikme Ekle|**Ctrl+Alt+D**| OtherContextMenus.UITestEditorContextMenu.InsertDelayBefore |
|Tümünü Bul|**Shift+Alt+L**| OtherContextMenus.UITestEditorContextMenu.LocateAll |
|UI denetimini bulma|**Ctrl+Shift+L**| OtherContextMenus.UITestEditorContextMenu.LocatetheUIControl |
|Kodu taşı|**Ctrl+Alt+C**| OtherContextMenus.UITestEditorContextMenu.Movecode |
|Yeni bir yönteme Böl|**Ctrl+Shift+T**| OtherContextMenus.UITestEditorContextMenu.Splitintoanewmethod |

### <a name="dataset-editor"></a>Veri Kümesi Düzenleyicisi

Bu içeriğe özgü kısayollar şunlardır:


|Komutlar|Klavye kısayolları|Komut KIMLIĞI|
|-|-|-|
|Sütun Ekle|**Ekle**| OtherContextMenus.ColumnContext.InsertColumn |
|Sütun|**Ctrl+L**| OtherContextMenus.DbTableContext.Add.Column |

### <a name="difference-viewer"></a>Fark Görüntüleyicisi

Bu içeriğe özgü kısayollar şunlardır:


|Komutlar|Klavye kısayolları|Komut KIMLIĞI|
|-|-|-|
|Kırpma boşluğunu yoksay|**CTRL + \\ , CTRL + Ara çubuğu**| Diff.IgnoreTrimWhitespace |
|Satır içi görünüm|**Ctrl+ \\ , Ctrl+1**| Diff.InlineView |
|Yalnızca sol görünüm|**Ctrl+ \\ , Ctrl+3**| Diff.LeftOnlyView |
|Sonraki fark|**F8**| Diff.NextDifference |
|Önceki fark|**Shift+F8**| Diff.PreviousDifference |
|Yalnızca sağ görünüm|**Ctrl+ \\ , Ctrl+4**| Diff.RightOnlyView |
|Yan yana görünüm|**Ctrl+ \\ , Ctrl+2**| Diff.SideBySideView |
|Sol ve sağ arasında geçiş|**Ctrl+ \\ , Ctrl+Sekme**| Diff.SwitchBetweenLeftAndRight |
|Görünümü eşitle iki durumlu düğme|**Ctrl+ \\ , Ctrl+Aşağı Ok**| Diff.SynchronizeViewToggle |
|Açıklama ekleme|**Ctrl+Shift+K**| EditorContextMenus.CodeWindow.AddComment |
|Yerel dosyayı düzenleme|**Ctrl+Shift+P**| EditorContextMenus.CodeWindow.EditLocalFile |

### <a name="dom-explorer"></a>DOM Gezgini

Bu bağlama özgü kısayollar:


|Komutlar|Klavye kısayolları|Komut Kimliği|
|-|-|-|
|Yenile|**F5**| DOMExplorer.Refresh |
|Öğe seçme|**Ctrl+B**| DOMExplorer.SelectElement |
|Düzeni göster|**Ctrl+Shift+I**| DOMExplorer.ShowLayout |

### <a name="f-interactive"></a>F# etkileşimli

Bu bağlama özgü kısayollar:


|Komut|Klavye kısayolu|Komut Kimliği|
|-|-|-|
|Etkileşimli değerlendirmeyi iptal etme|**Ctrl+Break tuşu**| OtherContextMenus.FSIConsoleContext.CancelInteractiveEvaluation |

### <a name="graph-document-editor"></a>Grafik Belgesi Düzenleyicisi

Bu bağlama özgü kısayollar:


|Komutlar|Klavye kısayolları|Komut Kimliği|
|-|-|-|
|Düğüm ekleme|**Ekle**| ArchitectureContextMenus.DirectedGraphContextMenu.Advanced.Add.AddNode |
|Her iki bağımlılık da|**B**| ArchitectureContextMenus.DirectedGraphContextMenu.Advanced.Select.BothDependencies |
|Gelen bağımlılıklar|**ı**| ArchitectureContextMenus.DirectedGraphContextMenu.Advanced.Select.IncomingDependencies |
|Giden bağımlılıklar|**O**| ArchitectureContextMenus.DirectedGraphContextMenu.Advanced.Select.OutgoingDependencies |
|Yeni açıklama|**Ctrl+Shift+K**<br /><br /> veya<br /><br /> **Ctrl+E, C**| ArchitectureContextMenus.DirectedGraphContextMenu.NewComment |
|Kaldır|**Silme**| ArchitectureContextMenus.DirectedGraphContextMenu.Remove |
|Rename|**F2**| ArchitectureContextMenus.DirectedGraphContextMenu.Rename |

### <a name="graphics-diagnostics"></a>Grafik tanılaması

Bu bağlama özgü kısayollar:


|Komutlar|Klavye kısayolları|Komut Kimliği|
|-|-|-|
|Yakalama çerçevesi|Hiçbiri| Debug.Graphics.CaptureFrame |
|Piksel seçimini aşağı taşı|**Shift+Alt+Aşağı Ok**| Graphics.MovePixelSelectionDown |
|Piksel seçimini sola taşı|**Shift+Alt+Sol Ok**| Graphics.MovePixelSelectionLeft |
|Piksel seçimini sağa taşıma|**Shift+Alt+Sağ Ok**| Graphics.MovePixelSelectionRight |
|Piksel seçimini yukarı taşı|**Shift+Alt+Yukarı Ok**| Graphics.MovePixelSelectionUp |
|Gerçek boyuta yakınlaştırma|**Shift+Alt+0** (sıfır)| Graphics.ZoomToActualSize |
|Pencereye sığdırmak için yakınlaştır|**Shift+Alt+9**| Graphics.ZoomToFitInWindow |
|Yakınlaştır|**Shift+Alt+=**| Graphics.ZoomIn |
|Uzaklaştır|**Shift+Alt+-**| Graphics.ZoomOut |

### <a name="html-editor"></a>HTML Düzenleyicisi

Bu bağlama özgü kısayollar:


|Komut|Klavye kısayolu|Komut Kimliği|
|-|-|-|
|Denetleyiciye gidin|**Ctrl+M, Ctrl+G**| OtherContextMenus.HTMLContext.GoToController |

### <a name="html-editor-design-view"></a>HTML Düzenleyicisi Tasarım Görünümü

Bu bağlama özgü kısayollar:


|Komutlar|Klavye kısayolları|Komut Kimliği|
|-|-|-|
|Denetimi aşağı taşıma|**Ctrl+Aşağı Ok**| Edit.MoveControlDown |
|Denetimi yukarı taşıma|**Ctrl+Yukarı Ok**| Edit.MoveControlUp |
|Kalın|**Ctrl+B**| Format.Bold |
|Köprüye dönüştürme|**Ctrl+L**| Format.ConverttoHyperlink |
|Yer işareti ekleme|**Ctrl+Shift+L**| Format.InsertBookmark |
|İtalik|**Ctrl+I**| Format.Italic |
|Altı çizili|**Ctrl+U**| Format.Underline |
|İçerik ekle sayfası|**Ctrl+M, Ctrl+C**| Project.AddContentPage |
|Sol tarafta sütun|**Ctrl+Alt+Sol Ok**| Table.ColumntotheLeft |
|Sağ sütun|**Ctrl+Alt+Sağ Ok**| Table.ColumntotheRight |
|Yukarıdaki satır|**Ctrl+Alt+Yukarı Ok**| Table.RowAbove |
|Aşağıdaki satır|**Ctrl+Alt+Aşağı Ok**| Table.RowBelow |
|Görsel olmayan net denetimler|**Ctrl+Shift+N**| View.ASP.NETNonvisualControls |
|Ana sayfayı düzenleme|**Ctrl+M, Ctrl+M**| View.EditMaster |
|Sonraki görünüm|**Ctrl+PgDn**| View.NextView |
|Akıllı etiketi göster|**Shift+Alt+F10**| View.ShowSmartTag |
|Biçimlendirmeyi görüntüleme|**Shift+F7**| View.ViewMarkup |
|Önceki sekme|**Ctrl+PgUp**| Window.PreviousTab |

### <a name="html-editor-source-view"></a>HTML Düzenleyicisi Kaynak Görünümü

Bu bağlama özgü kısayollar:


|Komutlar|Klavye kısayolları|Komut Kimliği|
|-|-|-|
|Denetleyiciye gidin|**Ctrl+M, Ctrl+G**| OtherContextMenus.HTMLContext.GoToController |
|Sonraki görünüm|**Ctrl+PgDn**| View.NextView |
|Görünümleri eşitleme|**Ctrl+Shift+Y**| View.SynchronizeViews |
|Görünüm tasarımcısı|**Shift+F7**| View.ViewDesigner |
|Önceki sekme|**Ctrl+PgUp**| Window.PreviousTab |

### <a name="layer-diagram"></a>Katman diyagramı

Bu bağlama özgü kısayollar:


|Komut|Klavye kısayolu|Komut Kimliği|
|-|-|-|
|Sil|**Shift+Delete**| Edit.Delete |

### <a name="managed-resources-editor"></a>Yönetilen Kaynaklar Düzenleyicisi

Bu bağlama özgü kısayollar:


|Komutlar|Klavye kısayolları|Komut Kimliği|
|-|-|-|
|Hücreyi düzenle|**F2**| Edit.EditCell |
|Kaldır|**Silme**| Edit.Remove |
|Satırı kaldırma|**Ctrl+Delete**| Edit.RemoveRow |
|Seçim iptali|**Esc**| Edit.SelectionCancel |
|Ses|**Ctrl+4**| Resources.Audio |
|Dosyalar|**Ctrl+5**| Resources.Files |
|Simgeler|**Ctrl+3**| Resources.Icons |
|Görüntüler|**Ctrl+2**| Resources.Images |
|Diğer|**Ctrl+6**| Resources.Other |
|Dizeler|**Ctrl+1**| Resources.Strings |

### <a name="merge-editor-window"></a>Düzenleyiciyi Birleştir penceresi

Bu bağlama özgü kısayollar:


|Komutlar|Klavye kısayolları|Komut Kimliği|
|-|-|-|
|Sol pencereye odağı ayarlama|**Alt+1**| TeamFoundationContextMenus.MergeContextMenu.SetFocusonLeftWindow |
|Sonuç penceresine odağı ayarlama|**Alt+2**| TeamFoundationContextMenus.MergeContextMenu.SetFocusonResultWindow |
|Sağ pencereye odağı ayarlama|**Alt+3**| TeamFoundationContextMenus.MergeContextMenu.SetFocusonRightWindow |

### <a name="microsoft-sql-server-data-tools-schema-compare"></a>Microsoft SQL Server Veri Araçları, Şema Karşılaştırma

Bu bağlama özgü kısayollar:


|Komutlar|Klavye kısayolları|Komut Kimliği|
|-|-|-|
|SSDT şeması karşılaştırması|**Shift+Alt+C**| SQL.SSDTSchemaCompareCompare |
|SSDT şeması karşılaştırma betiği oluşturma|**Shift+Alt+G**| SQL.SSDTSchemaCompareGenerateScript |
|SSDT şeması bir sonraki değişikliği karşılaştırma|**Shift+Alt+.**| SQL.SSDTSchemaCompareNextChange |
|SSDT şeması önceki değişikliği karşılaştırma|**Shift+Alt+,**| SQL.SSDTSchemaComparePreviousChange |
|SSDT şeması karşılaştırma durdurma|**Alt+Break**| SQL.SSDTSchemaCompareStop |
|SSDT şeması yazma güncelleştirmelerini karşılaştırma|**Shift+Alt+U**| SQL.SSDTSchemaCompareWriteUpdates |

### <a name="microsoft-sql-server-data-tools-table-designer"></a>Microsoft SQL Server Veri Araçları, Tablo Tasarımcısı

Bu bağlama özgü kısayollar:


|Komutlar|Klavye kısayolları|Komut Kimliği|
|-|-|-|
|CommitAllEdits|**Shift+Alt+U**|
|Joker karakterleri genişletme|**Ctrl+R, E**<br /><br /> veya<br /><br /> **Ctrl+R, Ctrl+E**| SQL.ExpandWildcards |
|Adları tam olarak nitelendirin|**Ctrl+R, Q**<br /><br /> veya<br /><br /> **Ctrl+R, Ctrl+Q**| SQL.FullyqualifyNames |
|Şemaya taşıma|**Ctrl+R, M**<br /><br /> veya<br /><br /> **Ctrl+R, Ctrl+M**| SQL.MovetoSchema |
|Rename|**F2**<br /><br /> veya<br /><br /> **Ctrl+R, R**<br /><br /> veya<br /><br /> **Ctrl+R, Ctrl+R**| SQL.Rename |
|ViewFileInScriptPanel|**Shift+Alt+PgDn**| |

### <a name="microsoft-sql-server-data-tools-t-sql-editor"></a>Microsoft SQL Server Veri Araçları, T-SQL Düzenleyicisi

Bu içeriğe özgü kısayollar şunlardır:


|Komutlar|Klavye kısayolları|Komut KIMLIĞI|
|-|-|-|
|CommitAllEdits|**Shift+Alt+U**|
|Hata ayıklayıcı ile Yürüt|**Alt+F5**| SQL.ExecuteWithDebugger |
|Joker karakterleri Genişlet|**Ctrl+R, E**<br /><br /> veya<br /><br /> **Ctrl+R, Ctrl+E**| SQL.ExpandWildcards |
|Adları tam olarak nitelendir|**Ctrl+R, Q**<br /><br /> veya<br /><br /> **Ctrl+R, Ctrl+Q**| SQL.FullyqualifyNames |
|Şemaya taşı|**Ctrl+R, M**<br /><br /> veya<br /><br /> **Ctrl+R, Ctrl+M**| SQL.MovetoSchema |
|Rename|**F2**<br /><br /> veya<br /><br /> **Ctrl+R, R**<br /><br /> veya<br /><br /> **Ctrl+R, Ctrl+R**| SQL.Rename |
|T SQL düzenleyicisi sorguyu iptal et|**Alt+Break**| SQL.TSqlEditorCancelQuery |
|T SQL düzenleyicisi sorgu yürütme|**Ctrl+Shift+E**| SQL.TSqlEditorExecuteQuery |
|dosya olarak SQL düzenleyici sonuçları|**Ctrl+D, F**| SQL.TSqlEditorResultsAsFile |
|düzenleyici sonuçlarını kılavuz olarak SQL|**Ctrl+D, G**| SQL.TSqlEditorResultsAsGrid |
|SQL düzenleyici sonuçları metin olarak|**Ctrl+D, T**| SQL.TSqlEditorResultsAsText |
|T SQL düzenleyicisi tahmini planı göster|**Ctrl+D, E**| SQL.TSqlEditorShowEstimatedPlan |
|T SQL düzenleyicisi yürütme planını değiştirme|**Ctrl+D, A**| SQL.TSqlEditorToggleExecutionPlan |
|T SQL düzenleyicisi geçiş sonuçları bölmesi|**Ctrl+D, R**| SQL.TSqlEditorToggleResultsPane |
|T SQL düzenleyicisi kopya sorgusu|**Ctrl+Alt+N**|SQL. Tsqtaditorclonequery |
|T SQL düzenleyicisi veritabanı birleşik kutusu|**Shift+Alt+PgDn**|SQL. Tsqtaditordatabasecombo |

### <a name="microsoft-sql-server-data-tools-t-sql-pdw-editor"></a>Microsoft SQL Server Veri Araçları, T-SQL PDW Düzenleyicisi

Bu içeriğe özgü kısayollar şunlardır:


|Komutlar|Klavye kısayolları|Komut KIMLIĞI|
|-|-|-|
|T SQL düzenleyicisi sorguyu iptal et|**Alt+Break**| SQL.TSqlEditorCancelQuery |
|T SQL düzenleyicisi sorgu yürütme|**Ctrl+Shift+E**| SQL.TSqlEditorExecuteQuery |
|dosya olarak SQL düzenleyici sonuçları|**Ctrl+D, F**| SQL.TSqlEditorResultsAsFile |
|düzenleyici sonuçlarını kılavuz olarak SQL|**Ctrl+D, G**| SQL.TSqlEditorResultsAsGrid |
|SQL düzenleyici sonuçları metin olarak|**Ctrl+D, T**| SQL.TSqlEditorResultsAsText |
|T SQL düzenleyicisi tahmini planı göster|**Ctrl+D, E**| SQL.TSqlEditorShowEstimatedPlan |
|T SQL düzenleyicisi yürütme planını değiştirme|**Ctrl+D, A**| SQL.TSqlEditorToggleExecutionPlan |
|T SQL düzenleyicisi geçiş sonuçları bölmesi|**Ctrl+D, R**| SQL.TSqlEditorToggleResultsPane |
|T SQL düzenleyicisi kopyalama sorgusu|**Ctrl+Alt+N**|SQL. TSqlEditorCloneQuery |
|T SQL düzenleyicisi kopyalama sorgusu|**Shift+Alt+PgDn**|SQL. TSqlEditorCloneQuery |

### <a name="page-inspector"></a>Sayfa Denetçisi

Bu bağlama özgü kısayollar:


|Komut|Klavye kısayolu|Komut Kimliği|
|-|-|-|
|Simge durumuna küçült|**F12**| PageInspector.Minimize |

### <a name="query-designer"></a>Sorgu Tasarımcısı

Bu bağlama özgü kısayollar:


|Komutlar|Klavye kısayolları|Komut Kimliği|
|-|-|-|
|Veri alma işlemini iptal etme|**Ctrl+T**| QueryDesigner.CancelRetrievingData |
|Ölçütler|**Ctrl+2**| QueryDesigner.Criteria |
|Diyagram|**Ctrl+1**| QueryDesigner.Diagram |
|Yürütme SQL|**Ctrl+R**| QueryDesigner.ExecuteSQL |
|Satıra var|**Ctrl+G**| QueryDesigner.GotoRow |
|Birleştirme modu|**Ctrl+Shift+J**| QueryDesigner.JoinMode |
|Sonuçlar|**Ctrl+4**| QueryDesigner.Results |
|Sql|**Ctrl+3**| QueryDesigner.SQL |

### <a name="query-results"></a>Sorgu sonuçları

Bu bağlama özgü kısayollar:


|Komutlar|Klavye kısayolları|Komut Kimliği|
|-|-|-|
|Sorgu sonuçları yeni satırı|**Alt+End**| SQL.QueryResultsNewRow |
|Sorgu sonuçlarını yenileme|**Shift+Alt+R**| SQL.QueryResultsRefresh |
|Sorgu sonuçları durdurma|**Alt+Break**| SQL.QueryResultsStop |

### <a name="report-designer"></a>Rapor Tasarımcısı

Bu bağlama özgü kısayollar:


|Komutlar|Klavye kısayolları|Komut Kimliği|
|-|-|-|
|Kesme çizgisi|**Enter**| Edit.BreakLine |
|Char sol|**Sol Ok**| Edit.CharLeft |
|Char sol genişletme|**Shift+Sol Ok**| Edit.CharLeftExtend |
|Char right|**Sağ Ok**| Edit.CharRight |
|Karakter sağ genişletme|**Shift+Sağ Ok**| Edit.CharRightExtend |
|Ekle sekmesi|**Sekme**| Edit.InsertTab |
|Satır aşağı|**Aşağı Ok**| Edit.LineDown |
|Çizgi aşağı genişletme|**Shift+Aşağı Ok**| Edit.LineDownExtend |
|Sırala|**Yukarı Ok**| Edit.LineUp |
|Genişletmeyi yukarı doğru sırala|**Shift+Yukarı Ok**| Edit.LineUpExtend |
|Denetimi aşağı taşıma|**Ctrl+Aşağı Ok**| Edit.MoveControlDown |
|Denetimi sola taşıma|**Ctrl+Sol Ok**| Edit.MoveControlLeft |
|Denetimi sağa taşıma|**Ctrl+Sağ Ok**| Edit.MoveControlRight |
|Denetimi yukarı taşı|**Ctrl+Yukarı Ok**| Edit.MoveControlUp |
|Seçimi iptal et|**Esc**| Edit.SelectionCancel |
|Denetimi aşağı doğru Boyutlandır|**Ctrl+Shift+Aşağı Ok**| Edit.SizeControlDown |
|Denetimi sola Boyutlandır|**Ctrl+Shift+Sol Ok**| Edit.SizeControlLeft |
|Denetimi sağa Boyutlandır|**Ctrl+Shift+Sağ Ok**| Edit.SizeControlRight |
|Denetimin boyutunu ayarla|**Ctrl+Shift+Yukarı Ok**| Edit.SizeControlUp |
|Sekme sola|**Shift+Sekme Tuşu**| Edit.TabLeft |
| Rapor verileri|**Ctrl+Alt+D**| View.ReportData |

### <a name="sequence-diagram"></a>Sıralı diyagram

Bu içeriğe özgü kısayollar şunlardır:


|Komutlar|Klavye kısayolları|Komut KIMLIĞI|
|-|-|-|
|Koda git|**F12**| ArchitectureDesigner.Sequence.NavigateToCode |
|Sil|**Shift+Del**| Edit.Delete |

### <a name="settings-designer"></a>Ayarlar Tasarımcısı

Bu içeriğe özgü kısayollar şunlardır:


|Komutlar|Klavye kısayolları|Komut KIMLIĞI|
|-|-|-|
|Hücreyi Düzenle|**F2**| Edit.EditCell |
|Satırı Kaldır|**Ctrl+Delete**| Edit.RemoveRow |
|Seçimi iptal et|**Esc**| Edit.SelectionCancel |
|Kodu görüntüle|**F7**| View.ViewCode |

### <a name="solution-explorer"></a>Çözüm Gezgini

Bu içeriğe özgü kısayollar şunlardır:


|Komut|Klavye kısayolu|Komut KIMLIĞI|
|-|-|-|
|Sayfa denetçisinde görüntüle|**Ctrl+K, Ctrl+G**| ClassViewContextMenus.ClassViewProject.View.ViewinPageInspector |

### <a name="team-explorer"></a>Ekip Gezgini

Bu içeriğe özgü kısayollar şunlardır:


|Komut|Klavye Kısayolu|Komut KIMLIĞI|
|-|-|-|
|Sil|**Silme**| Edit.Delete |
|Rename|**F2**| File.Rename |
|Takım Gezgini gezintisine git|**Alt+Home**| TeamFoundationContextMenus.Commands.GoToTeamExplorerNavigation |
|Takım Gezgini sonraki bölüm içeriğine git|**Alt+Aşağı Ok**| TeamFoundationContextMenus.Commands.GoToTeamExplorerNextSectionContent |
|Takım Gezgini sayfa içeriğine git|**Alt + 0** (sıfır)| TeamFoundationContextMenus.Commands.GoToTeamExplorerPageContent |
|Takım Gezgini önceki bölüm içeriğine git|**Alt+Yukarı Ok**| TeamFoundationContextMenus.Commands.GoToTeamExplorerPreviousSectionContent |
|Takım Gezgini Bölüm 1 içeriğine git|**Alt+1**| TeamFoundationContextMenus.Commands.GoToTeamExplorerSection1Content |
|Takım Gezgini Bölüm 2 içeriğine git|**Alt+2**| TeamFoundationContextMenus.Commands.GoToTeamExplorerSection2Content |
|Takım Gezgini Bölüm 3 içeriğine git|**Alt+3**| TeamFoundationContextMenus.Commands.GoToTeamExplorerSection3Content |
|Takım Gezgini Bölüm 4 içeriğine git|**Alt+4**| TeamFoundationContextMenus.Commands.GoToTeamExplorerSection4Content |
|Takım Gezgini Bölüm 5 içeriğine git|**Alt+5**| TeamFoundationContextMenus.Commands.GoToTeamExplorerSection5Content |
|Takım Gezgini Bölüm 6 içeriğine git|**Alt+6**| TeamFoundationContextMenus.Commands.GoToTeamExplorerSection6Content |
|Takım gezgini bölüm 7 içeriğine gidin|**Alt+7**| TeamFoundationContextMenus.Commands.GoToTeamExplorerSection7Content |
|Takım gezgini bölüm 8 içeriğine gidin|**Alt+8**| TeamFoundationContextMenus.Commands.GoToTeamExplorerSection8Content |
|Takım gezgini bölüm 9 içeriğine gidin|**Alt+9**| TeamFoundationContextMenus.Commands.GoToTeamExplorerSection9Content |
|Takım gezgini geriye doğru gidin|**Alt+Sol Ok**| TeamFoundationContextMenus.Commands.TeamExplorerNavigateBackward |
|Takım gezgini ileri gidin|**Alt+Sağ Ok**| TeamFoundationContextMenus.Commands.TeamExplorerNavigateForward |
|TFS bağlamı çalışma sayfam create copy wi|**Shift+Alt+C**| TeamFoundationContextMenus.MyWorkPageInProgress.TfsContextMyWorkPageCreateCopyWI |
|TFS bağlamı çalışma sayfam yeni bağlı wi|**Shift+Alt+L**| TeamFoundationContextMenus.MyWorkPageInProgress.TfsContextMyWorkPageNewLinkedWI |
|Yenile|**F5**| View.Refresh |

### <a name="test-explorer"></a>Test Gezgini

Bu bağlama özgü kısayollar:


|Komut|Klavye kısayolu|Komut Kimliği|
|-|-|-|
|Testi açma|**F12**| TestExplorer.OpenTest |

### <a name="text-editor"></a>Metin Düzenleyici

Bu bağlama özgü kısayollar:


| Komutlar | Klavye kısayolları |Komut Kimliği|
|-|-|-|
|Kesme çizgisi| **Enter**<br /><br /> veya<br /><br /> **Shift+Enter** | Edit.BreakLine |
|Char sol| **Sol Ok** | Edit.CharLeft |
|Char sol genişletme| **Shift+Sol Ok** | Edit.CharLeftExtend |
|Char left extend column| **Shift+Alt+Sol Ok** | Edit.CharLeftExtendColumn |
|Char right| **Sağ Ok** | Edit.CharRight |
|Karakter sağ genişletme| **Shift+Sağ Ok** | Edit.CharRightExtend |
|Char right extend column| **Shift+Alt+Sağ Ok** | Edit.CharRightExtendColumn |
|Yer işaretlerini temizleme| **Ctrl+K, Ctrl+L** | Edit.ClearBookmarks |
|Tüm outlining'i daralt| **Ctrl+M, Ctrl+A** | Edit.CollapseAllOutlining |
|Geçerli bölgeyi daralt| **Ctrl+M, Ctrl+S** | Edit.CollapseCurrentRegion |
|Etiketi daralt| **Ctrl+M, Ctrl+T** | Edit.CollapseTag |
|Tanımları daralt| **Ctrl+M, Ctrl+O** ('O' harfi) | Edit.CollapseToDefinitions |
|Sözleşme seçimi| **Shift+Alt+-** | Edit.ContractSelection |
|Açıklama seçimi| **Ctrl+K, Ctrl+C** | Edit.CommentSelection |
|Tam sözcük| **Ctrl+Ara Çubuğu**<br /><br /> veya<br /><br /> **Alt+Sağ Ok** | Edit.CompleteWord |
|Parametre ipucu kopyalama| **Ctrl+Shift+Alt+C** | Edit.CopyParameterTip |
|Filtre düzeyini azaltma| **Alt+,** | Edit.DecreaseFilterLevel |
|Geriye doğru silme| **Geri Al tuşu**<br /><br /> veya<br /><br /> **Shift+Geri Al tuşu** | Edit.DeleteBackwards |
|Yatay boşluğu silme| **CTRL + K, CTRL +\\** | Edit.DeleteHorizontalWhiteSpace |
|Belge sonu| **Ctrl+End** | Edit.DocumentEnd |
|Belge bitişi uzat| **Ctrl+Shift+End** | Edit.DocumentEndExtend |
|Belge başlangıcı| **Ctrl+Home** | Edit.DocumentStart |
|Belge başlangıcını uzat| **Ctrl+Shift+Home** | Edit.DocumentStartExtend |
|Tüm anahat oluşturmayı Genişlet| **Ctrl+M, Ctrl+X** | Edit.ExpandAllOutlining |
|Geçerli bölgeyi Genişlet| **Ctrl+M, Ctrl+E** | Edit.ExpandCurrentRegion |
|Seçimi genişlet| **SHIFT + alt + =** | . ExpandSelection öğesini Düzenle |
|Seçimi kapsayan bloğa Genişlet| **SHIFT + alt +]** | . ExpandSelectiontoContainingBlock öğesini Düzenle |
|Belgeyi biçimlendir| **Ctrl+K, Ctrl+D** | Edit.FormatDocument |
|Biçim seçimi| **Ctrl+K, Ctrl+F** | Edit.FormatSelection |
|Tümüne git| **CTRL + T**<br /><br /> veya<br /><br /> **CTRL +,** | . Sayfayall Düzenle |
|Ayraç git| **CTRL +]** | Edit.GotoBrace |
|Goto ayraç Genişlet| **CTRL + SHIFT +]** | Edit.GotoBraceExtend |
|Son git| **CTRL + T, R** | Düzenle. Sayfayson |
|Dosyadaki bir sonraki soruna git| **Alt+PgDn** | Düzenle. GotoNextIssueinFile |
|Dosyadaki önceki soruna git| **Alt+PgUp** | Düzenle. GotoPreviousIssueinFile |
|Seçimi Gizle| **Ctrl+M, Ctrl+H** | Edit.HideSelection |
|Filtre düzeyini artır| **Alt +.** | Edit.IncreaseFilterLevel |
|Artımlı arama| **Ctrl+I** | Edit.IncrementalSearch |
|Her eşleşen giriş Ekle| **SHIFT + alt +;** | Edit. ınsertcaretsatalleþleþen |
|Sonraki eşleşen giriş işaretini Ekle| **SHIFT + alt +.** | Edit. ınsertnextmatchingşapka |
|Ekle sekmesi| **Sekme** | Edit.InsertTab |
|Kesme satırı| **Ctrl+L** | Edit.LineCut |
|Satır silme| **Ctrl+Shift+L** | Edit.LineDelete |
|Aşağı satır| **Aşağı Ok** | Edit.LineDown |
|Satır aşağı genişlet| **Shift+Aşağı Ok** | Edit.LineDownExtend |
|Satır aşağı genişlet sütunu| **Shift+Alt+Aşağı Ok** | Edit.LineDownExtendColumn |
|Satır sonu| **End** | Edit.LineEnd |
|Çizgi bitişi uzat| **Shift+End** | Edit.LineEndExtend |
|Satır sonu genişletme sütunu| **Shift+Alt+End** | Edit.LineEndExtendColumn |
|Üstteki satır aç| **Ctrl+Enter** | Edit.LineOpenAbove |
|Aşağıda satır aç| **Ctrl+Shift+Enter** | Edit.LineOpenBelow |
|Satır başlangıcı| **Giriş Ekranı** | Edit.LineStart |
|Satır başlangıcını uzat| **Shift+Home** | Edit.LineStartExtend |
|Satır başı Genişlet sütunu| **Shift+Alt+Home** | Edit.LineStartExtendColumn |
|Satır sırasını değiştir| **Shift+Alt+T** | Edit.LineTranspose |
|Satır yukarı| **Yukarı Ok** | Edit.LineUp |
|Çizgi uzat| **Shift+Yukarı Ok** | Edit.LineUpExtend |
|Çizgiyi Genişlet sütunu Genişlet| **Shift+Alt+Yukarı Ok** | Edit.LineUpExtendColumn |
|Üyeleri Listele| **Ctrl+J** | Edit.ListMembers |
|Küçük harf yap| **Ctrl+U** | Edit.MakeLowercase |
|Büyük harf yap| **Ctrl+Shift+U** | Edit.MakeUppercase |
|Seçili satırları aşağı taşı| **Alt+Aşağı Ok** | Edit.MoveSelectedLinesDown |
|Seçili satırları yukarı taşı| **Alt+Yukarı Ok** | Edit.MoveSelectedLinesUp |
|Sonraki vurgulanan başvuru| **Ctrl+Shift+Aşağı Ok** | Edit.NextHighlightedReference |
|Üzerine yazma modu| **Ekle** | Edit.OvertypeMode |
|Sayfa aşağı| **PgDn** | Edit.PageDown |
|Sayfa aşağı genişlet| **Shift+PgDn** | Edit.PageDownExtend |
|Sayfa yukarı| **PgUp** | Edit.PageUp |
|Sayfa yukarı Genişlet| **Shift+PgUp** | Edit.PageUpExtend |
|Parametre bilgisi| **Ctrl+Shift+Ara Çubuğu** | Edit.ParameterInfo |
|Parametre ipucunu Yapıştır| **Ctrl+Shift+Alt+P** | Edit.PasteParameterTip |
|Geriye göz at| **Ctrl+Alt+-** | Edit.PeekBackward |
|Açıklama Özeti| **Alt+F12** | Edit.PeekDefinition |
|İleriye göz at| **Ctrl + alt + =** | Edit.PeekForward |
|Önceki vurgulanan başvuru| **Ctrl+Shift+Yukarı Ok** | Edit.PreviousHighlightedReference |
|Hızlı bilgi| **Ctrl+K, Ctrl+I** | Edit.QuickInfo |
|Ters Artımlı arama| **Ctrl+Shift+I** | Edit.ReverseIncrementalSearch |
|Satırı aşağı kaydır| **Ctrl+Aşağı Ok** | Edit.ScrollLineDown |
|Bir satır yukarı kaydır| **Ctrl+Yukarı Ok** | Edit.ScrollLineUp |
|Geçerli sözcüğü seç| **Ctrl+W** | Edit.SelectCurrentWord |
|Seçimi iptal et| **Esc** | Edit.SelectionCancel |
|En son geri dönmek için seçin| **CTRL + =** | Edit.SelectToLastGoBack |
|Kod lens menüsünü göster| **CTRL + K, CTRL +\`** | Edit.ShowCodeLensMenu |
|Git menüsünü göster| **Alt +\`** | Edit. ShowNavigateMenu |
|Geçerli gizlemeyi durdur| **Ctrl+M, Ctrl+U** | Edit.StopHidingCurrent |
|Açıklamayı durdurma| **Ctrl+M, Ctrl+P** | Edit.StopOutlining |
|Yer değiştirme| **Ctrl+K, Ctrl+A** | Edit.SwapAnchor |
|Sekme sol| **Shift+Sekme Tuşu** | Edit.TabLeft |
|Tüm altı çizili düğmeyi değiştir| **Ctrl+M, Ctrl+L** | Edit.ToggleAllOutlining |
|Yer işaretini değiştir| **Ctrl+K, Ctrl+K** | Edit.ToggleBookmark |
|Tamamlama modunu değiştir| **Ctrl+Alt+Ara Çubuğu** | Edit.ToggleCompletionMode |
|Altı çizili genişletmeyi değiştir| **Ctrl+M, Ctrl+M** | Edit.ToggleOutliningExpansion |
|Görev listesi kısayolunu değiştir| **Ctrl+K, Ctrl+H** | Edit.ToggleTaskListShortcut |
|Sözcük kaydırmayı açıp kaydırma| **Ctrl+E, Ctrl+W** | Edit.ToggleWordWrap |
|Uncomment selection| **Ctrl+K, Ctrl+U** | Edit.UncommentSelection |
|Alttaki görünümü| **Ctrl+PgDn** | Edit.ViewBottom |
|Alttaki genişletmeyi görüntüleme| **Ctrl+Shift+PgDn** | Edit.ViewBottomExtend |
|Üst görünümü| **Ctrl+PgUp** | Edit.ViewTop |
|Üst genişletmeyi görüntüle| **Ctrl+Shift+PgUp** | Edit.ViewTopExtend |
|Boşluğu görüntüleme| **Ctrl+R, Ctrl+W** | Edit.ViewWhiteSpace |
|Sona kadar sözcük silme| **Ctrl+Delete** | Edit.WordDeleteToEnd |
|Başlamak için sözcük silme| **Ctrl+Geri Al tuşu** | Edit.WordDeleteToStart |
|Sonraki sözcük| **Ctrl+Sağ Ok** | Edit.WordNext |
|Word next extend| **Ctrl+Shift+Sağ Ok** | Edit.WordNextExtend |
|Word next extend column| **Ctrl+Shift+Alt+Sağ Ok** | Edit.WordNextExtendColumn |
|Önceki sözcük| **Ctrl+Sol Ok** | Edit.WordPrevious |
|Word önceki genişletme| **Ctrl+Shift+Sol Ok** | Edit.WordPreviousExtend |
|Word önceki genişletme sütunu| **Ctrl+Shift+Alt+Sol Ok** | Edit.WordPreviousExtendColumn |
|Sözcük dönüşüm| **Ctrl+Shift+T** | Edit.WordTranspose |
|Etkileşimli olarak yürütme| **Alt+Enter** | EditorContextMenus.CodeWindow.ExecuteInInteractive |
|Satırı etkileşimli olarak yürütme| **Alt+'** | EditorContextMenus.CodeWindow.ExecuteLineInInteractive |
|Sayfa denetçisinde görüntüle| **Ctrl+K, Ctrl+G** | OtherContextMenus.HTMLContext.ViewinPageInspector |
|TFS sonraki bölgeye taşıma ek açıklama ekleme| **Alt+PgDn** | TeamFoundationContextMenus.Annotate.TfsAnnotateMoveNextRegion |
|TFS önceki bölgeyi taşımaya açıklama ekleme| **Alt+PgUp** | TeamFoundationContextMenus.Annotate.TfsAnnotateMovePreviousRegion |

### <a name="uml-activity-diagram"></a>UML etkinlik diyagramı

Bu bağlama özgü kısayollar:


|Komut|Klavye kısayolu|Komut Kimliği|
|-|-|-|
|Sil|**Shift+Del**| Edit.Delete |

### <a name="uml-class-diagram"></a>UML sınıf diyagramı

Bu bağlama özgü kısayollar:


|Komut|Klavye kısayolu|Komut Kimliği|
|-|-|-|
|Modelden sil|**Shift+Del**| Edit.DeleteFromModel |

### <a name="uml-component-diagram"></a>UML bileşen diyagramı

Bu bağlama özgü kısayollar:


|Komut|Klavye kısayolu|Komut Kimliği|
|-|-|-|
|Modelden sil|**Shift+Del**| Edit.DeleteFromModel |

### <a name="uml-use-case-diagram"></a>UML kullanım durumu diyagramı

Bu bağlama özgü kısayollar:


|Komut|Klavye kısayolu|Komut Kimliği|
|-|-|-|
|Modelden sil|**Shift+Del**| Edit.DeleteFromModel |

### <a name="vc-accelerator-editor"></a>VC Hızlandırıcı Düzenleyicisi

Bu bağlama özgü kısayollar:


|Komutlar|Klavye kısayolları|Komut Kimliği|
|-|-|-|
|Yeni hızlandırıcı|**Ekle**| Edit.NewAccelerator |
|Sonraki anahtar türü|**Ctrl+W**| Edit.NextKeyTyped |

### <a name="vc-dialog-editor"></a>VC İletişim Kutusu Düzenleyicisi

Bu bağlama özgü kısayollar:


|Komutlar|Klavye kısayolları|Komut Kimliği|
|-|-|-|
|Denetimi aşağı taşıma|**Aşağı Ok**| Edit.MoveControlDown |
|Denetimi sola taşıma|**Sol Ok**| Edit.MoveControlLeft |
|Denetimi sağa taşıma|**Sağ Ok**| Edit.MoveControlRight |
|Denetimi yukarı taşıma|**Yukarı Ok**| Edit.MoveControlUp |
|Sütunu sola kaydırma|**Ctrl+Sol Ok**| Edit.ScrollColumnLeft |
|Sütunu sağa kaydırma|**Ctrl+Sağ Ok**| Edit.ScrollColumnRight |
|Satırı aşağı kaydırma|**Ctrl+Aşağı Ok**| Edit.ScrollLineDown |
|Yukarı doğru kaydırma|**Ctrl+Yukarı Ok**| Edit.ScrollLineUp |
|Boyut denetimi aşağı|**Shift+Aşağı Ok**| Edit.SizeControlDown |
|Boyut denetimi sola|**Shift+Sol Ok**| Edit.SizeControlLeft |
|Boyut denetimi hakkı|**Shift+Sağ Ok**| Edit.SizeControlRight |
|Boyut denetimi|**Shift+Yukarı Ok**| Edit.SizeControlUp |
|Altları hizala|**Ctrl+Shift+Aşağı Ok**| Format.AlignBottoms |
|Merkezleri hizalama|**Shift+F9**| Format.AlignCenters |
|Sola hizala|**Ctrl+Shift+Sol Ok**| Format.AlignLefts |
|Ortaları hizala|**F9**| Format.AlignMiddles |
|Hakları hizalama|**Ctrl+Shift+Sağ Ok**| Format.AlignRights |
|Üstleri hizala|**Ctrl+Shift+Yukarı Ok**| Format.AlignTops |
|Alttaki düğme|**Ctrl+B**| Format.ButtonBottom |
|Sağ düğme|**Ctrl+R**| Format.ButtonRight |
|Orta yatay|**Ctrl+Shift+F9**| Format.CenterHorizontal |
|Orta dikey|**Ctrl+F9**| Format.CenterVertical |
|Mnemonics'i denetleme|**Ctrl+M**| Format.CheckMnemonics |
|İçerik boyutu|**Shift+F7**| Format.SizetoContent |
|Boşluk genelinde|**Alt+Sağ Ok**<br /><br /> veya<br /><br /> **Alt+Sol Ok**| Format.SpaceAcross |
|Boşluk bırak|**Alt+Yukarı Ok**<br /><br /> veya<br /><br /> **Alt+Aşağı Ok**| Format.SpaceDown |
|Sekme sırası|**Ctrl+D**| Format.TabOrder |
|Test iletişim kutusu|**Ctrl+T**| Format.TestDialog |
|Geçiş kılavuzları|**Ctrl+G**| Format.ToggleGuides |

### <a name="vc-image-editor"></a>VC Görüntü Düzenleyicisi

Bu bağlama özgü kısayollar:


|Komutlar|Klavye kısayolları|Komut Kimliği|
|-|-|-|
|Airbrush aracı|**Ctrl+A**| Image.AirbrushTool |
|Fırça aracı|**Ctrl+B**| Image.BrushTool |
|Kopyalama ve ana hat seçimi|**Ctrl+Shift+U**| Image.CopyandOutlineSelection |
|Opak çizme|**Ctrl+J**| Image.DrawOpaque |
|Üç nokta aracı|**Alt+P**| Image.EllipseTool |
|Silme aracı|**Ctrl+Shift+I**| Image.EraseTool |
|Doldurulmuş üç nokta aracı|**Ctrl+Shift+Alt+P**| Image.FilledEllipseTool |
|Doldurulmuş dikdörtgen aracı|**Ctrl+Shift+Alt+R**| Image.FilledRectangleTool |
|Doldurulmuş yuvarlanmış dikdörtgen araç|**Ctrl+Shift+Alt+W**| Image.FilledRoundedRectangleTool |
|Dolgu aracı|**Ctrl+F**| Image.FillTool |
|Yatay çevirme|**Ctrl+H**| Image.FlipHorizontal |
|Dikey çevirme|**Shift+Alt+H**| Image.FlipVertical |
|Daha büyük fırça|**Ctrl+=**| Image.LargerBrush |
|Çizgi aracı|**Ctrl+L**| Image.LineTool |
|Büyütme aracı|**Ctrl+M**| Image.MagnificationTool |
|Büyütmek|**Ctrl+Shift+M**| Image.Magnify |
|Yeni görüntü türü|**Ekle**| Image.NewImageType |
|Sonraki renk|**Ctrl+]**<br /><br /> veya<br /><br /> **Ctrl+Sağ Ok**| Image.NextColor |
|Sağ sonraki renk|**Ctrl+Shift+]**<br /><br /> veya<br /><br /> **Ctrl+Shift+Sağ Ok**| Image.NextRightColor |
|Özetlenen üç nokta aracı|**Shift+Alt+P**| Image.OutlinedEllipseTool |
|Özetlenen dikdörtgen aracı|**Shift+Alt+R**| Image.OutlinedRectangleTool |
|Özetlenen yuvarlanmış dikdörtgen araç|**Shift+Alt+W**| Image.OutlinedRoundedRectangleTool |
|Kalem aracı|**Ctrl+I**| Image.PencilTool |
|Önceki renk|**Ctrl+[**<br /><br /> veya<br /><br /> **Ctrl+Sol Ok**| Image.PreviousColor |
|Önceki sağ renk|**Ctrl+Shift+[**<br /><br /> veya<br /><br /> **Ctrl+Shift+Sol Ok**| Image.PreviousRightColor |
|Dikdörtgen seçim aracı|**Shift+Alt+S**| Image.RectangleSelectionTool |
|Dikdörtgen araç|**Alt+R**| Image.RectangleTool |
|90 Derece Döndür derece|**Ctrl+Shift+H**| Image.Rotate90Degrees |
|Yuvarlanmış dikdörtgen araç|**Alt+W**| Image.RoundedRectangleTool |
|Kılavuzu göster|**Ctrl+Alt+S**| Image.ShowGrid |
|Kutucuk kılavuzu gösterme|**Ctrl+Shift+Alt+S**| Image.ShowTileGrid |
|Küçük fırça|**Ctrl+.**| Image.SmallBrush |
|Daha küçük fırça|**Ctrl+-**| Image.SmallerBrush |
|Metin aracı|**Ctrl+T**| Image.TextTool |
|Seçimi fırça olarak kullanma|**Ctrl+U**| Image.UseSelectionasBrush |
|Yakınlaştır|**Ctrl+Shift+.**<br /><br /> veya<br /><br /> **Ctrl+Yukarı Ok**| Image.ZoomIn |
|Uzaklaştır|**Ctrl+Shift+,**<br /><br /> veya<br /><br /> **Ctrl+Aşağı Ok**| Image.ZoomOut |

### <a name="vc-string-editor"></a>VC Dize Düzenleyicisi

Bu bağlama özgü kısayollar:


|Komut|Klavye kısayolu|Komut Kimliği|
|-|-|-|
|Yeni dize|**Ekle**| Edit.NewString |

### <a name="view-designer"></a>Görünüm Tasarımcısı

Bu bağlama özgü kısayollar:


|Komutlar|Klavye kısayolları|Komut Kimliği|
|-|-|-|
|Veri alma işlemini iptal etme|**Ctrl+T**| QueryDesigner.CancelRetrievingData |
|Ölçütler|**Ctrl+2**| QueryDesigner.Criteria |
|Diyagram|**Ctrl+1**| QueryDesigner.Diagram |
|Yürütme SQL|**Ctrl+R**| QueryDesigner.ExecuteSQL |
|Satıra var|**Ctrl+G**| QueryDesigner.GotoRow |
|Birleştirme modu|**Ctrl+Shift+J**| QueryDesigner.JoinMode |
|Sonuçlar|**Ctrl+4**| QueryDesigner.Results |
|Sql|**Ctrl+3**| QueryDesigner.SQL |

### <a name="visual-studio"></a>Visual Studio

Bu bağlama özgü kısayollar:


|Komut|Klavye kısayolu|Komut Kimliği|
|-|-|-|
|Yöntemleri gizle bölmesi|**Ctrl+1**| OtherContextMenus.ORDesignerContext.HideMethodsPane |

### <a name="windows-forms-designer"></a>Windows Form Tasarımcısı

Bu içeriğe özgü kısayollar şunlardır:


|Komutlar|Klavye kısayolları|Komut KIMLIĞI|
|-|-|-|
|Çizgiyi Böl|**Enter**| Edit.BreakLine |
|Sol karakter|**Sol Ok**| Edit.CharLeft |
|Karakter sola Genişlet|**Shift+Sol Ok**| Edit.CharLeftExtend |
|Sağ karakter|**Sağ Ok**| Edit.CharRight |
|Sağ karakter Genişlet|**Shift+Sağ Ok**| Edit.CharRightExtend |
|Belge sonu|**End**| Edit.DocumentEnd |
|Belge bitişi uzat|**Shift+End**| Edit.DocumentEndExtend |
|Belge başlangıcı|**Giriş Ekranı**| Edit.DocumentStart |
|Belge başlangıcını uzat|**Shift+Home**| Edit.DocumentStartExtend |
|Ekle sekmesi|**Sekme**| Edit.InsertTab |
|Aşağı satır|**Aşağı Ok**| Edit.LineDown |
|Satır aşağı genişlet|**Shift+Yukarı Ok**| Edit.LineDownExtend |
|Satır yukarı|**Yukarı Ok**| Edit.LineUp |
|Çizgi uzat|**Shift+Aşağı Ok**| Edit.LineUpExtend |
|Denetimi aşağı taşı|**Ctrl+Aşağı Ok**| Edit.MoveControlDown |
|Denetimi sola taşı|**Ctrl+Sol Ok**| Edit.MoveControlLeft |
|Denetimi sağa taşı|**Ctrl+Sağ Ok**| Edit.MoveControlRight |
|Denetimi yukarı taşı|**Ctrl+Yukarı Ok**| Edit.MoveControlUp |
|Seçimi iptal et|**Esc**| Edit.SelectionCancel |
|Denetimi aşağı doğru Boyutlandır|**Ctrl+Shift+Aşağı Ok**| Edit.SizeControlDown |
|Denetimi sola Boyutlandır|**Ctrl+Shift+Sol Ok**| Edit.SizeControlLeft |
|Denetimi sağa Boyutlandır|**Ctrl+Shift+Sağ Ok**| Edit.SizeControlRight |
|Denetimin boyutunu ayarla|**Ctrl+Shift+Yukarı Ok**| Edit.SizeControlUp |
|Sekme sola|**Shift+Sekme Tuşu**| Edit.TabLeft |

### <a name="work-item-editor"></a>Çalışma Öğesi Düzenleyicisi

Bu içeriğe özgü kısayollar şunlardır:


|Komutlar|Klavye kısayolları|Komut KIMLIĞI|
|-|-|-|
|İş öğesinin kopyasını oluştur|**Shift+Alt+C**| Edit.CreateCopyofWorkItem |
|İş öğesini Yenile|**F5**| Edit.RefreshWorkItem |
|Yeni bağlantılı iş öğesi|**Shift+Alt+L**| Team.NewLinkedWorkItem |

### <a name="work-item-query-view"></a>Çalışma Öğesi Sorgu Görünümü

Bu içeriğe özgü kısayollar şunlardır:


|Komutlar|Klavye kısayolları|Komut KIMLIĞI|
|-|-|-|
|İş öğesinin kopyasını oluştur|**Shift+Alt+C**| Edit.CreateCopyofWorkItem |
|Leyebilirsiniz|**Shift+Alt+Sağ Ok**| Edit.Indent |
|Girintiyi|**Shift+Alt+Sol Ok**| Edit.Outdent |
|Yeni bağlantılı iş öğesi|**Shift+Alt+L**| Team.NewLinkedWorkItem |
|Yenile|**F5**| Team.Refresh |
|İki Durumlu Düğme|**Shift+Alt+V**| Window.Toggle |

### <a name="work-item-results-view"></a>Çalışma Öğesi Sonuçlar Görünümü

Bu içeriğe özgü kısayollar şunlardır:


|Komutlar|Klavye kısayolları|Komut KIMLIĞI|
|-|-|-|
|İş öğesinin kopyasını oluştur|**Shift+Alt+C**| Edit.CreateCopyofWorkItem |
|Leyebilirsiniz|**Shift+Alt+Sağ Ok**| Edit.Indent |
|Girintiyi|**Shift+Alt+Sol Ok**| Edit.Outdent |
|Sonraki iş öğesine git|**Shift+Alt+N**| Team.GotoNextWorkItem |
|Önceki iş öğesine git|**Shift+Alt+P**| Team.GotoPreviousWorkItem |
|Yeni bağlantılı iş öğesi|**Shift+Alt+L**| Team.NewLinkedWorkItem |
|Yenile|**F5**| Team.Refresh |
|İki Durumlu Düğme|**Shift+Alt+V**| Window.Toggle |

### <a name="workflow-designer"></a>İş Akışı Tasarımcısı

Bu içeriğe özgü kısayollar şunlardır:


|Komutlar|Klavye kısayolları|Komut KIMLIĞI|
|-|-|-|
|Sözcüğü Tamam|**Ctrl+K, W**<br /><br /> veya<br /><br /> **Ctrl+K, Ctrl+W**<br /><br /> veya<br /><br /> **Ctrl+Ara Çubuğu**<br /><br /> veya<br /><br /> **Alt+Sağ Ok**| Edit.CompleteWord |
|Filtre düzeyini azalt|**Alt+,**| Edit.DecreaseFilterLevel |
|Filtre düzeyini artır|**Alt +.**| Edit.IncreaseFilterLevel |
|Üyeleri Listele|**Ctrl+K, L**<br /><br /> veya<br /><br /> **Ctrl+K, Ctrl+L**<br /><br /> veya<br /><br /> **Ctrl+J**| Edit.ListMembers |
|Parametre bilgisi|**Ctrl+K, P**<br /><br /> veya<br /><br /> **Ctrl+K, Ctrl+P**<br /><br /> veya<br /><br /> **Ctrl+Shift+Ara Çubuğu**| Edit.ParameterInfo |
|Hızlı bilgi|**Ctrl+K, I**<br /><br /> veya<br /><br /> **Ctrl+K, Ctrl+I**| Edit.QuickInfo |
|Daralt|**Ctrl+E, Ctrl+C**<br /><br /> veya<br /><br /> **Ctrl+E, C**| WorkflowDesigner.Collapse |
|Tümünü daralt|veya| WorkflowDesigner.CollapseAll |
|Bağlan düğümleri|**Ctrl+E, Ctrl+F**<br /><br /> veya<br /><br /> **Ctrl+E, F**| WorkflowDesigner.ConnectNodes |
|Değişken Oluştur|**Ctrl+E, Ctrl+N**<br /><br /> veya<br /><br /> **Ctrl+E, N**| WorkflowDesigner.CreateVariable |
|Tümünü genişlet|**Ctrl+E, Ctrl+X**<br /><br /> veya<br /><br /> **Ctrl+E, X**| WorkflowDesigner.ExpandAll |
|Yerinde Genişlet|**Ctrl+E, Ctrl+E**<br /><br /> veya<br /><br /> **Ctrl+E, E**| WorkflowDesigner.ExpandInPlace |
|Üst öğeye git|**Ctrl+E, Ctrl+P**<br /><br /> veya<br /><br /> **Ctrl+E, P**| WorkflowDesigner.GoToParent |
|Odağı taşı|**Ctrl+E, Ctrl+M**<br /><br /> veya<br /><br /> **Ctrl+E, M**| WorkflowDesigner.MoveFocus |
|Tasarımcı üzerinden gezinme|**Ctrl+Alt+F6**| WorkflowDesigner.NavigateThroughDesigner |
|Geri Yükleme|**Ctrl+E, Ctrl+R**<br /><br /> veya<br /><br /> **Ctrl+E, R**| WorkflowDesigner.Restore |
|Bağımsız değişken tasarımcısını gizleme göster|**Ctrl+E, Ctrl+A**<br /><br /> veya<br /><br /> **Ctrl+E, A**| WorkflowDesigner.ShowHideArgumentDesigner |
|İçeri aktarmaları tasarımcısını göster|**Ctrl+E, Ctrl+I**<br /><br /> veya<br /><br /> **Ctrl+E, I**| WorkflowDesigner.ShowHideImportsDesigner |
|Genel bakış haritasını göster|**CTRL + E, CTRL + O** (harf ' O ')<br /><br /> veya<br /><br /> **Ctrl+E, O**| WorkflowDesigner.ShowHideOverviewMap |
|Değişken tasarımcısını gizleme 'yi göster|**Ctrl+E, Ctrl+V**<br /><br /> veya<br /><br /> **Ctrl+E, V**| WorkflowDesigner.ShowHideVariableDesigner |
|Seçimi değiştirme|**Ctrl+E, Ctrl+S**<br /><br /> veya<br /><br /> **Ctrl+E, S**| WorkflowDesigner.ToggleSelection |
|Yakınlaştır|**CTRL + NUM +**| WorkflowDesigner.ZoomIn |
|Uzaklaştır|**Ctrl+Num -**| WorkflowDesigner.ZoomOut |

### <a name="xaml-ui-designer"></a>XAML Tasarımcısı

Bu içeriğe özgü kısayollar şunlardır:


|Komutlar|Klavye kısayolları|Komut KIMLIĞI|
|-|-|-|
|Tümünü Sığdır|**CTRL + 0** (sıfır)| Design.FitAll |
|Tutamaçları göster|**F9**| Design.ShowHandles |
|Yakınlaştır|**Ctrl + alt + =**| Design.ZoomIn |
|Uzaklaştır|**Ctrl+Alt+-**| Design.ZoomOut |
|Tasarımcı seçenekleri|**CTRL + SHIFT +;**|
|Metin düzenleme|**F2**| Format.EditText |
|Tümü|**Ctrl+Shift+R**| Format.ResetLayout.All |
|Proje kodunu Çalıştır|**Ctrl+F9**|
|Gizle (yalnızca Blend)|**Ctrl+H**| Zaman çizelgesi. gizle (yalnızca Blend) |
|Kilitle (yalnızca Blend)|**Ctrl+L**| Timeline. Lock (yalnızca Blend) |
|Göster (yalnızca Blend)|**Ctrl+Shift+H**| Timeline. Show (yalnızca Blend) |
|Kilit açma (yalnızca Blend)|**Ctrl+Shift+L**| Timeline. Unlock (yalnızca Blend) |
|Sol kenar sola taşı|**Ctrl+Shift+,**| View.EdgeLeftMoveLeft |
|Kenar sol hareket sağ|**Ctrl+Shift+.**| View.EdgeLeftMoveRight |
|Kenar sağ hareket sola|**Ctrl+Shift+Alt+,**| View.EdgeRightMoveLeft |
|Kenar sağ taşı|**Ctrl+Shift+Alt+.**| View.EdgeRightMoveRight |
|Özellik işaretçisini göster menüsü|**Ctrl+Ara Çubuğu**| View.ShowPropertyMarkerMenu |

### <a name="xml-text-editor"></a>XML (Metin) Düzenleyicisi

Bu bağlama özgü kısayollar:


|Komutlar|Klavye kısayolları|Komut Kimliği|
|-|-|-|
|XSLT hata ayıklamayı başlatma|**Alt+F5**| XML.StartXSLTDebugging |
|Hata ayıklama olmadan XSLT'i başlatma|**Ctrl+Alt+F5**| XML.StartXSLTWithoutDebugging |

### <a name="xml-schema-designer"></a>XML Şema Tasarımcısı

Bu bağlama özgü kısayollar:


|Komutlar|Klavye kısayolları|Komut Kimliği|
|-|-|-|
|Aşağıdan yukarıya|**Alt+Yukarı Ok**| GraphView.BottomtoTop |
|Soldan sağa|**Alt+Sağ Ok**| GraphView.LefttoRight |
|Sağdan sola|**Alt+Sol Ok**| GraphView.RighttoLeft |
|Üstten aşağıya|**Alt+Aşağı Ok**| GraphView.ToptoBottom |
|Çalışma alanından kaldırma|**Silme**| OtherContextMenus.GraphView.RemovefromWorkspace |
|İçerik modeli görünümünü gösterme|**Ctrl+2**| XsdDesigner.ShowContentModelView |
|Grafik görünümünü gösterme|**Ctrl+3**| XsdDesigner.ShowGraphView |
|Başlangıç görünümünü göster|**Ctrl+1**| XsdDesigner.ShowStartView |

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio komutları](reference/visual-studio-commands.md)
