---
title: Seçenekler Sayfası, Ortam Düğümü Özellikleri
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- automation [Visual Studio], controlling Tools Options
- Tools Options settings, Environment node properties
ms.assetid: 26dca41f-91fc-4ca7-9103-3da402baa1d5
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e22b24889a14d49afddd3c30858814ddec663e6a
ms.sourcegitcommit: be938c7ecd756a11c9de3e6019a490d0e52b4190
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50672736"
---
# <a name="options-page-environment-node-properties"></a>Seçenekler Sayfası, Ortam Düğümü Özellikleri
Bu belgede, sayfa (veya özellik koleksiyonları) açıklanmaktadır ile ilişkili **ortam** kategori `DTE.Properties("Environment", <Property Page>)`, biri **seçenekleri** iletişim kutusu. Her bir alt bölümünün başlığı özellikler koleksiyonuna erişmek için kullanılan çağrıdır ve her bir alt bölümdeki tabloda koleksiyondaki özellikler listelenmektedir.

## <a name="general"></a>Genel
 `DTE.Properties("Environment", "General")`

|Özellik Öğesi Adı|Değer|Açıklama|
| - |-----------|-----------------|
|ShowStatusBar|Get/Set (Boole)|Durum çubuğunun görünür olup olmadığını belirler.|
|WindowMenuContainsNItems|Get/Set (kısa)|Belge pencereleri Windows menüsünün alt kısmında bulunan nasıl belirler.|
|MRUListContainsNItems|Get/Set (kısa)|"En son kullanılan" alt menüde kaç dosyaları görüntülemek belirler.|
|Animasyonlar|Get/Set (Boole)|Tümleşik geliştirme ortamı (IDE) durum çubuğunda animasyon kullanıp kullanmadığını belirler.|
|AnimationSpeed|Get/Set (kısa)||
|AutoAdjustExperience|Get/Set (Boole)|İstemci performansına bağlı olarak görsel deneyimi otomatik olarak ayarlar.|
|RichClientExperienceOptions|Get/Set (Enum)|Zengin istemci görsel deneyimini değerleriyle sağlayan <xref:EnvDTE100.vsRichClientExperienceOptions>.|
|CloseButtonActiveTabOnly|Get/Set (Boole)|Belirler olmadığını **Kapat** düğme, yalnızca etkin sekmesinde gösterilir.|
|AutohidePinActiveTabOnly|Get/Set (Boole)|Belirler olmadığını **Otomatik Gizle** düğmesi sadece etkin sekmede etkiler.|

## <a name="add-inmacros-security"></a>Ekle/makro güvenliği
 `DTE.Properties("Environment", "AddinMacrosSecurity")`

|Özellik Öğesi Adı|Değer|Açıklama|
| - |-----------|-----------------|
|MacrosEnabled|Get/Set (Boole)|Makroların çalıştırılmasına olanak tanır.|
|AddinsEnabled|Get/Set (Boole)|Yüklenecek eklentileri sağlar.|
|LoadAddinsFromTheWeb|Get/Set (Boole)|Web üzerinde bir URL'den yüklenecek eklentiler sağlar.|

## <a name="documents"></a>Belgeler
 `DTE.Properties("Environment", "Documents")`

|Özellik Öğesi Adı|Değer|Açıklama|
| - |-----------|-----------------|
|ReuseSavedActiveDocWindow|Get/Set (Boole)|Geçerli belge kaydedilirse, yeni bir dosya açmak mevcut belge penceresini yeniden olup olmadığını belirler. `false` her zaman açık her belge için yeni bir belge penceresi Aç anlamına gelir.|
|DetectFileChangesOutsideIDE|Get/Set (Boole)|Ortam, işletim sistemi dosyaları diskte değiştirilmiş IDE bildirdiğinde IDE içinde açılan dosyaları otomatik olarak yükler olup olmadığını belirler.|
|AutoloadExternalChanges|Get/Set (Boole)|Açık belge değil değiştirilirse değiştirilen dosya otomatik olarak açmak için dış değişiklikler yeniden tespit edip etmediğini belirler. Açık belge değiştirilir ve bu özellik `true`, bu özellik'ymiş gibi IDE ister `false`.|
|InitializeOpenFileFromCurrentDocument|Get/Set (Boole)|Belirler olmadığını <xref:EnvDTE.DTEClass.OpenFile%2A> komut çekirdeğini son etkin belgeden dizin ve dosya adı veya son bir yerden bir dosya açılır.|
|MiscFilesProjectSavesLastNItems|Get/Set (kısa)|Çeşitli dosyalar projesi kayıtları kaç dosyaları belirler. Sonuç olarak, hangi en son açmış diskte çeşitli dosya olarak IDE sonraki kullandığınızda görebilirsiniz.|
|ShowMiscFilesProject|Get/Set (Boole)|Çeşitli dosyalar projeleri gösterilip gösterilmeyeceğini belirler.|
|CheckForConsisentLineEndings|Get/Set (Boole)|Dosya tutarlı satır sonlarını denetler.|
|SaveDocsAsUnicodeWhenDataLoss|Get/Set (Boole)|Veri kod sayfasına kaydedilemiyor, belgeleri Unicode olarak kaydeder.|
|DontShowGlobalUndoChangeLossDialog|Get/Set (Boole)|Genel Geri Al diğer düzenlediğiniz dosyaların değiştirecek bir uyarı görüntüler.|
|AllowEditingReadOnlyFiles|Get/Set (Boole)|Salt okunur dosyaları, ancak bir uyarı verme bunları kaydetme girişimi olduğunda düzenlenmesini sağlar.|
|DocumentDockPreference|Get/Set (Enum)|<xref:EnvDTE100.vsDocumentDockPreferenceOptions>. İyi, açılan belge eklemek sekmesinde konumu.|

## <a name="extension-manager"></a>Uzantı Yöneticisi
 `DTE.Properties("Environment", "ExtensionManager")`

|Özellik Öğesi Adı|Değer|Açıklama|
| - |-----------|-----------------|
|EnableAdminExtensions|Get/Set (Boole)|Visual Studio yönetici kimlik bilgileri altında çalıştırdığınızda, kullanıcı başına uzantılar yükler. Bu değeri değiştirildikten sonra visual Studio'nun yeniden başlatılması gerekiyor.|
|EnableOnline|Get/Set (Boole)|Visual Studio Market uzantıları erişim sağlar.|
|AutomaticallyCheckForUpdates|Get/Set (Boole)|Güncelleştirmeleri yüklü uzantılar için otomatik olarak denetler.|

## <a name="find-and-replace"></a>Bulma ve Değiştirme
 `DTE.Properties("Environment", "FindAndReplace")`

|Özellik Öğesi Adı|Değer|Açıklama|
| - |-----------|-----------------|
|ShowWarningMessages|Get/Set (Boole)|Uyarı iletilerini görüntüler.|
|InitializeFromEditor|Get/Set (Boole)|Otomatik olarak doldurur **Aranan** düzenleyicisinden metin kutusu.|
|ShowMessageBoxes|Get/Set (Boole)|Bilgilendirici iletileri görüntüler.|
|HideWindowsAfterMatchFromQuickFindReplace|Get/Set (Boole)|Gizler **Bul ve Değiştir** kullanarak bir eşleşme arkalarına penceresi **Hızlı Bul** veya **hızlı Değiştir**.|

## <a name="import-and-export-settings"></a>İçeri ve dışarı aktarma ayarları
 `DTE.Properties("Environment", "Import and Export Settings")`

|Özellik Öğesi Adı|Değer|Açıklama|
| - |-----------|-----------------|
|TrackTeamSettings|Get/Set (Boole)|TeamSettingsFile tarafından belirtilen dosyada ayarları kullanır.|
|TeamSettingsFile|Get/Set (dize)|Takım ayarları içeren dosyanın adı.|
|AutoSaveFile|Get/Set (dize)|Kullanıcı ayarları otomatik olarak kaydedildiği dosyanın adı.|

## <a name="international-settings"></a>Uluslararası ayarlar
 `DTE.Properties("Environment", "International")`

|Özellik Öğesi Adı|Değer|Açıklama|
| - |-----------|-----------------|
|Dil|Get/Set (dize)|Visual Studio için geçerli dili için LCID değer.|

## <a name="keyboard"></a>Klavye
 `DTE.Properties("Environment", "Keyboard")`

|Özellik Öğesi Adı|Değer|Açıklama|
| - |-----------|-----------------|
|Düzen|Get/Set (dize)|Yerleşik bir düzeni içeren bir dize, yüklenen .vsk dosyasının tam yolu içeren bir dize veya "(hiçbir .vsk dosyasının yüklü ise varsayılan)" döndürür.|

## <a name="projects-and-solution"></a>Proje ve çözüm
 `DTE.Properties("Environment", "ProjectsAndSolution")`

|Özellik Öğesi Adı|Değer|Açıklama|
| - |-----------|-----------------|
|OnRunOrPreview|Get/Set (dize)|IDE her şeyi Önizleme veya yerleşik bir proje çalıştırmadan önce kaydetmeyeceğini belirler.|
|ProjectsLocation|Get/Set (dize)|Varsayılan dizin belirler burada **Proje Ekle** yeni proje iletişim kutusu kaydeder.|
|ShowOutputWindowBeforeBuild|Get/Set (Boole)|Bir derleme görüntüler başlangıç olup olmadığını belirleyen **çıkış** penceresi.|
|ShowTaskListAfterBuild|Get/Set (Boole)|Başarısız bir derleme işlemi görüntülenip görüntülenmeyeceğini belirler **görev listesi** derleme bittiğinde.|
|TrackFileSelectionInExplorer|Get/Set (Boole)|Geçerli öğe içinde izleniyor olup olmadığını belirler **Çözüm Gezgini**.|
|AlwaysShowSolutionNode|Get/Set (Boole)|Çözüm düğümüne görüntülenip görüntülenmeyeceğini belirler.|
|OnlySaveStartupProjectsAndDependencies|Get/Set (Boole)|Kaydetme işlemleri başlangıç projelerini ve bunların bağımlı dosyaları için sınırlı olup olmadığını belirler.|
|ShowAdvancedBuildConfigurations|Get/Set (Boole)|Gelişmiş derleme yapılandırmalarını görüntülenip görüntülenmeyeceğini belirler.|
|ConcurrentBuilds|Get/Set (dize)|Oluşabilecek paralel proje yapılandırma sayısını belirler.|
|SaveNewProjects|Get/Set (Boole)|Yeni projeler otomatik olarak oluşturulduktan sonra kaydedilip kaydedilmeyeceğini belirler.|
|PromptForRenameSymbol|Get/Set (Boole)|Dosyaları yeniden adlandırıldıklarında sembolik yeniden adlandırmayı sorulup sorulmayacağını belirtir.|
|OnRunWhenErrors|Get/Set (Enum)|Bir derleme hatalarla tamamlandı çalıştırmaya davranışını belirtir.|
|OnRunWhenOutOfDate|Get/Set (Enum)|Bir proje güncel olduğunda çalıştırma davranışını belirtir.|
|ProjectTemplatesLocation|Get/Set (dize)|Kullanıcı proje şablonları içeren dizin.|
|ProjectItemTemplatesLocation|Get/Set (dize)|Kullanıcı öğe şablonları içeren dizin.|
|DefaultBehaviorForStartupProjects|Get/Set (dize)||
|MSBuildOutputVerbosity|Get/Set (dize)|Derleme çıkışı için ayrıntı düzeyini belirtir.|

## <a name="startup"></a>Başlangıç
 `DTE.Properties("Environment", "Startup")`

|Özellik Öğesi Adı|Değer|Açıklama|
| - |-----------|-----------------|
|OnStartUp|Get/Set (Enum)|Öğesinden başlatma sırasında gerçekleştirilecek eylem <xref:EnvDTE.vsStartUp>, 0 ile 5 değerleriyle:<br /><br /> -0: giriş sayfasını açın<br />-1: yük en son yüklenen çözümü<br />-2: Göster **açık proje** iletişim kutusu<br />-3: Göster **yeni proje** iletişim kutusu<br />-4: boş ortamı Göster<br />-5: başlangıç sayfasını göster|
|StartPageRSSUrl|Get/Set (dize)|RSS, akış URL'sini başlatma sırasında kullanılır.|
|StartPageRefreshDownloadedContent|Get/Set (Boole)|Başlangıç sayfası StartPageRefreshInterval içinde belirtilen aralık her ilgi çekici sonra yeniler.|
|StartPageRefreshInterval|Get/Set (kısa)|Aralığının başlangıç sayfası yenilemek için dakika cinsinden değeri.|

## <a name="tasklist"></a>Görev listesi
 `DTE.Properties("Environment", "TaskList")`

|Özellik Öğesi Adı|Değer|Açıklama|
| - |-----------|-----------------|
|ConfirmTaskDeletion|Get/Set (Boole)|Bir onay kutusu görevlerden silerken görüntülenip görüntülenmeyeceğini belirtir **görev listesi**.|
|WarnOnAddingHiddenItem|Get/Set (Boole)|Bir kullanıcı eklerken uyarı olup olmadığını belirtir gösterilmeyecek bir görevi.|
|DontShowFilePaths|Get/Set (Boole)|Görev listesinde tam dosya yollarını gösterilip gösterilmeyeceğini belirtir.|
|CommentTokens|SAFEARRAY'i|SafeArray yorum belirteci değerlerini döndürür. Her alan yok `Name` (dize) ve `Priority` (<xref:EnvDTE.vsTaskPriority>, yüksek, Orta veya düşük).|

## <a name="web-browser"></a>Web tarayıcısı
 `DTE.Properties("Environment", "WebBrowser")`

|Özellik Öğesi Adı|Değer|Açıklama|
| - |-----------|-----------------|
|Giriş sayfası|Get/Set (dize)|Giriş sayfası URL'si temsil eder.|
|SearchPage|Get/Set (dize)|Arama sayfası URL'si temsil eder.|
|ViewSourceIn|Get/Set (Enum)|<xref:EnvDTE.vsBrowserViewSource> (Kaynak, tasarım, dış).|
|ViewSourceExternalProgram|Get/Set (dize)|Dış kaynak Görüntüleyicisi yolu.|

## <a name="see-also"></a>Ayrıca Bkz.

- [Seçenek ayarlarını denetleme](https://msdn.microsoft.com/Library/a09ed242-7494-4cde-bbd1-7a8ec617965d)
- [Seçenekler sayfasında özellik öğelerinin adlarını belirleme](https://msdn.microsoft.com/Library/d450422d-47c7-4eeb-9f9f-3286264bc5aa)
- [Seçenekler Sayfası, Yazı Tipleri ve Renkler Düğümü Özellikleri](../../ide/reference/options-page-fonts-and-colors-node-properties.md)
- [Seçenekler Sayfası, Metin Düzenleyici Düğümü Özellikleri](../../ide/reference/options-page-text-editor-node-properties.md)
- [Ortam Seçenekleri İletişim Kutusu](../../ide/reference/environment-options-dialog-box.md)