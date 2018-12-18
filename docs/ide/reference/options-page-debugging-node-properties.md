---
title: Seçenekler Sayfası, Hata Ayıklama Düğümü Özellikleri
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
ms.assetid: 564cc8b2-0084-420e-b560-200cc5621a7e
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 70a06548dd25ade1bf64bad6a99261e043f6ac65
ms.sourcegitcommit: be938c7ecd756a11c9de3e6019a490d0e52b4190
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50670842"
---
# <a name="options-page-debugging-node-properties"></a>Seçenekler Sayfası, Hata Ayıklama Düğümü Özellikleri
Aşağıdaki tablolarda sayfaları (veya özellik koleksiyonları) açıklanmaktadır ile ilişkili **hata ayıklama** kategori `DTE.Properties("Debugging", <Property Page>)` , **seçenekleri** iletişim kutusu.

## <a name="general"></a>Genel
 `DTE.Properties("Debugging", "General")`

|Özellik Öğesi Adı|Değer|Açıklama|
| - |-----------|-----------------|
|PromptOnBreakpointDelete|Get/Set (Boole)|Hata ayıklayıcı bir projedeki tüm kesme noktalarını silmeden önce izin ister olup olmadığını belirler.|
|BreakAllProcesses|Get/Set (Boole)|Tek bir işlem keser her durumda hata ayıklayıcı tüm işlemler keser olup olmadığını belirler.|
|BreakAtBoundaries|Get/Set (Boole)|Hata ayıklayıcı bir özel durum uygulama etki alanları arasında bir kenarlık geçtiğinde, yürütmeyi keser veya arasında yönetilen ve yerel kod belirler.|
|EnableAddressLevelDebugging|Get/Set (Boole)|Adres seviyesinde hata ayıklama özellikleri etkin olup olmadığını belirler.|
|ShowDisassemblyIfNoSource|Get/Set (Boole)|Hata ayıklayıcı kaynak kodu mevcut olmadığında ayrıştırılmış kodu görüntülenip görüntülenmeyeceğini belirler.|
|EnableBreakpointFilters|Get/Set (Boole)|Kesme noktası filtrelemesinin etkinleştirilip etkinleştirilmeyeceğini belirler.|
|EnableExceptionAssistant|Get/Set (Boole)|Özel durum Yardımcısı'nı yönetilen özel durumlar için kullanılıp kullanılmayacağını belirler.|
|UnwindCallstack|Get/Set (Boole)|Hata ayıklayıcı işlenmeyen bir özel durum için çağrı yığınını geriye doğru izler olup olmadığını belirler.|
|EnableJustMyCode|Get/Set (Boole)|C# ve Visual Basic kodu için yalnızca kendi kodum etkin olup olmadığını belirler.|
|ShowAllMembers|Get/Set (Boole)|Kullanıcı olmayan nesneler için hata ayıklayıcı değişken pencerelerinde tüm nesne üyeleri görüntülenip görüntülenmeyeceğini belirler. Yalnızca kendi kodum etkin değilse bu seçenek bir etkisi yoktur.|
|WarnIfNoUserCode|Get/Set (Boole)|Kullanıcı, kullanıcı kodu olmayan bir işleme iliştirmek çalıştığında hata ayıklayıcı bir uyarı verir olup olmadığını belirler. Yalnızca kendi kodum etkin değilse bu seçenek bir etkisi yoktur.|
|EnablePropertyEvaluation|Get/Set (Boole)|Hata ayıklayıcı özellikleri otomatik olarak değerlendirir ve yönetilen kodda örtük işlev çağrısı olup olmadığını belirler.|
|CallStringConversion|Get/Set (Boole)|Hata ayıklayıcı örtük olarak bir dize dönüştürme işlevini değişken pencerelerindeki nesnelerde çağırır olup olmadığını belirler.|
|EnableSourceServer|Get/Set (Boole)|Hata ayıklayıcı bir kaynak sunucudan erişim kodu için olup olmadığını belirler.|
|PrintSourceServerDiagnostics|Get/Set (Boole)|Kaynak sunucu ile ilgili tanılama iletilerini çıkış penceresine gösterip göstermediğini belirler. Kaynak sunucu erişimini etkinleştirilmediği sürece bu seçeneğin bir etkisi yoktur.|
|HighlightEntireLine|Get/Set (Boole)|Hata ayıklayıcı kesme noktaları ve geçerli deyim için satırın tamamını vurgular olup olmadığını belirler.|
|RequireSourceToMatch|Get/Set (Boole)|Hata ayıklayıcı kaynak dosyalarının hata ayıklama için dosyalar açıldığında özgün sürümle tam olarak eşleşmesi gerekli olup olmadığını belirler.|
|RedirectOutputToImmediate|Get/Set (Boole)|Çıkış penceresi çıkışını yürütme penceresine yeniden yönlendirilen olup olmadığını belirler.|
|ShowRawVariableStructure|Get/Set (Boole)|Değişken pencerelerindeki nesnelerde ham biçimde gösterilip gösterilmeyeceğini belirler.|
|SuppressJitOptimization|Get/Set (Boole)|Yönetilen kod için hata ayıklayıcı tarafından just-ın-time iyileştirme atlanıp atlanmadığını belirler.|
|WarnIfNoSymbols|Get/Set (Boole)|Hata ayıklayıcı işlemi başlatıldığında hiçbir hata ayıklama simgeleri kullanılabilir değilse bir uyarı görüntüler olup olmadığını belirler.|
|WarnIfScriptDisabled|Get/Set (Boole)|Hata ayıklayıcı işlemi başlatıldığında betik hata ayıklamasını etkin değilse bir uyarı görüntüler olup olmadığını belirler.|
|ShowMarkersForAllThreads|Get/Set (Boole)|Hata ayıklayıcı iş parçacığı işaretçileri görüntülenip görüntülenmeyeceğini belirler.|
|StepOverPropertiesAndOperators|Get/Set (Boole)|Yalnızca yönetilen kod içindeki özellikler ve işleçlerin üzerinden adımla belirtir.|

## <a name="edit-and-continue"></a>Düzenle ve Devam Et
 `DTE.Properties("Debugging", "EditAndContinue")`

|Özellik Öğesi Adı|Değer|Açıklama|
| - |-----------|-----------------|
|EnableEditAndContinue|Get/Set (Boole)|Düzenle ve devam et etkin olup olmadığını belirler. Bu seçenek, Düzenle ve devam et destekleyen tüm diller için geçerlidir.|
|InvokedByCommands|Get/Set (Boole)|Düzenle ve devam et otomatik olarak uygulanıp uygulanmayacağını kod değişiklikleri kullanıcı gibi hata ayıklama komutu seçtiğinde belirler **adım** veya **devam**. Bu seçenek, yalnızca yerel kod için geçerlidir.|
|InvokedByCommandsAskFirst|Get/Set (Boole)|Düzenle ve devam et kullanıcıya kullanıcı gibi hata ayıklama komutu seçtiğinde, kod değişiklikleri uygulamak izni uyarıp uyarmayacağını belirler **adım** veya **devam**. Bu seçenek, yalnızca yerel kod için geçerlidir.|
|WarnAboutStaleCode|Get/Set (Boole)|Düzenle ve devam et güncel olmayan veya eski, kod yürütülmesine neden olur, hata ayıklayıcı bir uyarı iletisi sorunları olup olmadığını belirler. Bu seçenek, yalnızca yerel kod için geçerlidir.|
|RelinkChangesOnStop|Get/Set (kısa)|Visual Studio uygulamanın yürütülmesini durdurur, Düzenle ve devam et tarafından uygulanan kod değişiklikleri i olup olmadığını belirler. Bu seçenek, yalnızca yerel kod için geçerlidir.|
|AllowPrecompiling|Get/Set (kısa)|Düzenle ve devam et izin verilip verilmediğini arka planda önceden derlenmiş üst bilgiler yükleneceğini belirler. Bu seçenek, yalnızca yerel kod için geçerlidir.|

## <a name="just-in-time"></a>Tam Zamanında
 `DTE.Properties("Debugging", "JustInTime")`

|Özellik Öğesi Adı|Değer|Açıklama|
| - |-----------|-----------------|
|JitManaged|Get/Set (Boole)|Yönetilen kod için tam zamanında hata ayıklama etkin olup olmadığını belirler.|
|JitNative|Get/Set (Boole)|Yerel kod için tam zamanında hata ayıklama etkin olup olmadığını belirler.|
|JitScript|Get/Set (Boole)|Betik kodu için tam zamanında hata ayıklama etkin olup olmadığını belirler.|

## <a name="native"></a>Yerel
 `DTE.Properties("Debugging", "Native")`

|Özellik Öğesi Adı|Değer|Açıklama|
| - |-----------|-----------------|
|LoadDllExports|Get/Set (Boole)|Hata ayıklayıcı DLL dışa aktarma tablolarını yükler olup olmadığını belirler.|
|EnableRPC|Get/Set (Boole)|Hata ayıklayıcı COM uzak yordam çağrılarını adım olup olmadığını belirler.|

## <a name="see-also"></a>Ayrıca Bkz.

- [Seçenek ayarlarını denetleme](https://msdn.microsoft.com/Library/a09ed242-7494-4cde-bbd1-7a8ec617965d)
- [Seçenekler sayfasında özellik öğelerinin adlarını belirleme](https://msdn.microsoft.com/Library/d450422d-47c7-4eeb-9f9f-3286264bc5aa)
- [Seçenekler Sayfası, Yazı Tipleri ve Renkler Düğümü Özellikleri](../../ide/reference/options-page-fonts-and-colors-node-properties.md)
- [Seçenekler Sayfası, Metin Düzenleyici Düğümü Özellikleri](../../ide/reference/options-page-text-editor-node-properties.md)
- [Genel, Hata Ayıklama, Seçenekler İletişim Kutusu](../../debugger/general-debugging-options-dialog-box.md)
- [Düzenle ve devam et, hata ayıklama, Seçenekler iletişim kutusu](/visualstudio/debugger/edit-and-continue?view=vs-2015)
- [Tam Zamanında, Hata Ayıklama, Seçenekler İletişim Kutusu](../../debugger/just-in-time-debugging-options-dialog-box.md)