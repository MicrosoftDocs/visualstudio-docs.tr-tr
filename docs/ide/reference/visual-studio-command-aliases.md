---
title: Komut diğer adları
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- aliases, Visual Studio commands
- Visual Studio, commands
- predefined command aliases
- commands, aliases
- Visual Studio commands
- pre-defined command aliases
- command aliases
ms.assetid: de8bb378-8c1c-4087-a9a5-537fa8314c19
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a74bc2bc38befe81ec3a26c5da4819dbe1c66148
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53056444"
---
# <a name="visual-studio-command-aliases"></a>Visual Studio Komut Diğer Adları

Komut diğer adları daha az karakter, bir komut çalıştırmak istediğinizde yazmanıza olanak sağlar. Diğer adlar içine girdiğiniz **Bul/komut** kutusu veya **komut** penceresi. Örneğin, girmek yerine `>File.OpenFile` görüntülemek için **Dosya Aç** iletişim kutusu, önceden tanımlanmış diğer kullanabilirsiniz `>of`.

Tür `alias` içinde **komut** geçerli diğer adlar ve tanımlarının listesini görüntülemek için pencere. Tür `>cls` içeriğini temizlemek için **komut** penceresi. Belirli bir komut için bir diğer ad görmek istiyorsanız, yazın `alias <command name>`.

Bir Visual Studio komutları için kendi bir diğer ad (ile veya bağımsız değişkenler olmadan) kolayca oluşturabilirsiniz. Örneğin, diğer ad kullanımı için söz dizimi `File.NewFile MyFile.txt` olduğu `alias MyAlias File.NewFile MyFile.txt`. Diğer adlar ile silebilirsiniz `alias <alias name> /delete`

Aşağıdaki tabloda, önceden tanımlanmış Visual Studio komut diğer adları listesini içerir. Bazı komut adları birden fazla önceden tanımlanmış diğer adı vardır. Komut adlarının doğru sözdizimi, bağımsız değişkenleri ve bu komutlara anahtarları açıklayan ayrıntılı konulara görüntülemek için aşağıdaki bağlantıları tıklatın.

|Komut adı|Alias|Tam adı|
|------------------|-----------|-------------------|
|[Yazdır Komutu](../../ide/reference/print-command.md)|?|Debug.Print|
|[Hızlı Bakış Komutu](../../ide/reference/quick-watch-command.md)|??|Debug.Quickwatch|
|Yeni Proje Ekle|AddProj|File.AddNewProject|
|[Diğer Ad Komutu](../../ide/reference/alias-command.md)|Alias|Tools.Alias|
|Otomatik değişkenler penceresi|İfade ve değişkenler|Debug.Autos|
|Kesme Noktaları penceresi|Bl|Debug.Breakpoints|
|İki durumlu kesme noktası|BP|Debug.ToggleBreakPoint|
|Çağrı Yığını penceresi|Çağrı yığını|Debug.CallStack|
|Yer işaretlerini Temizle|ClearBook|Edit.ClearBookmarks|
|Close|Close|File.Close|
|Tüm belgeleri kapatma|CloseAll|Window.CloseAllDocuments|
|Tümünü temizle|CLS|Edit.ClearAll|
|Komut modu|cmd|View.CommandWindow|
|Kodu Görüntüle|kod|View.ViewCode|
|[Belleği Listele Komutu](../../ide/reference/list-memory-command.md)|d|Debug.ListMemory|
|[Bellek komut listesi](../../ide/reference/list-memory-command.md) ANSI olarak|da|Debug.ListMemory /Ansi|
|[Bellek komut listesi](../../ide/reference/list-memory-command.md) tek baytlık biçimi|DB|Debug.ListMemory /Format:OneByte|
|[Bellek komut listesi](../../ide/reference/list-memory-command.md) ANSI ile dört bayt olarak Biçimlendir|DC|Debug.ListMemory /Format:FourBytes /Ansi|
|[Bellek komut listesi](../../ide/reference/list-memory-command.md) dört bayt biçimi|Ekle|Debug.ListMemory /Format:FourBytes|
|BOL'a kadar Sil|DelBOL|Edit.DeleteToBOL|
|EOL'ye kadar Sil|DelEOL|Edit.DeleteToEOL|
|Yatay boşluğu Sil|DelHSp|Edit.DeleteHorizontalWhitespace|
|Görünüm Tasarımcısı|tasarımcı|View.ViewDesigner|
|[Bellek komut listesi](../../ide/reference/list-memory-command.md) kayan noktalı sayı biçimi|SD|Debug.ListMemory/Format:Float|
|Ayrıştırma penceresi|dısasm|Debug.Disassembly|
|[Bellek komut listesi](../../ide/reference/list-memory-command.md) sekiz bayt biçimi|dq|Debug.ListMemory /Format:EightBytes|
|[Bellek komut listesi](../../ide/reference/list-memory-command.md) Unicode|DU|Debug.ListMemory / Unicode|
|[Deyimi Değerlendir Komutu](../../ide/reference/evaluate-statement-command.md)|Değerlendirme|Debug.EvaluateStatement|
|Çık|Çık|File.Exit|
|Seçimi Biçimlendir|biçim|Edit.FormatSelection|
|Tam ekran|Tam ekran|View.FullScreen|
|[Başlat Komutu](../../ide/reference/start-command.md)|G|Debug.Start|
|[Git Komutu](../../ide/reference/go-to-command.md)|GotoLn|Edit.GoTo|
|Küme ayracına Git|GotoBrace|Edit.GotoBrace|
|F1Help|Yardım|Help.F1Help|
|Anlık mod|immed|Tools.ImmediateMode|
|Dosyayı metin olarak Ekle|Insertfile|Edit.InsertFileAsText|
|[Çağrı Yığınını Listele Komutu](../../ide/reference/list-call-stack-command.md)|KB|Debug.ListCallStack|
|Küçük harfe çevir|LCase|Edit.MakeLowercase|
|Satırı Kes|LineCut|Edit.LineCut|
|Satırı Sil|LineDel|Edit.LineDelete|
|Üyeleri Listeleme|ListMembers|Edit.ListMembers|
|Yerel öğeler penceresi|Yerel öğeler|Debug.Locals|
|[Komut Penceresi Çıktısı Günlüğü Tut Komutu](../../ide/reference/log-command-window-output-command.md)|Günlük|Tools.LogCommandWindowOutput|
|Komut penceresinde işaret modu|işareti|Tools.CommandWindowMarkMode|
|Bellek penceresi|Bellek Memory1|Debug.Memory1|
|Bellek penceresi 2|Memory2|Debug.Memory2|
|Bellek penceresi 3|Memory3|Debug.Memory3|
|Bellek penceresi 4|Belleği4|Debug.Memory4|
|[Sayı Tabanını Ayarla Komutu](../../ide/reference/set-radix-command.md)|n|Debug.SetRadix|
|[ShowWebBrowser Komutu](../../ide/reference/showwebbrowser-command.md)|NAV gidin|View.ShowWebBrowser|
|Sonraki Yer İşareti|NextBook|Edit.NextBookmark|
|[Yeni Dosya Komutu](../../ide/reference/new-file-command.md)|nf|File.NewFile|
|Yeni Proje|NP NewProj|File.NewProject|
|[Dosya Aç Komutu](../../ide/reference/open-file-command.md)|Açma|File.OpenFile|
|[Proje Aç Komutu](../../ide/reference/open-project-command.md)|OP|File.OpenProject|
|Tanımları/durdurma anahat oluşturma için Daralt|OutlineDefs StopOutlining|Edit.CollapseToDefinitions|
|Üzerinden adımla|p|Debug.StepOver|
|Parametre bilgileri|Paramınfo|Edit.ParameterInfo|
|Dışına adımla|çekme isteği|Debug.StepOut|
|Önceki Yer İşareti|PrevBook|Edit.PreviousBookmark|
|Dosya Yazdır|Yazdırma|File.Print|
|Özellikler Penceresi|Özellikler|View.PropertiesWindow|
|Durdur|q|Debug.StopDebugging|
|Yinele|Yinele|Edit.Redo|
|Yazmaçlar penceresi|yazmaçlar|Debug.Registers|
|İmlece kadar Çalıştır|RTC|Debug.RunToCursor|
|Seçili öğeleri Kaydet|Kaydet|File.SaveSelectedItems|
|Tümünü Kaydet|SaveAll|File.SaveAll|
|Farklı Kaydet|Farklı Kaydet|File.SaveSelectedItemsAs|
|[Kabuk Komutu](../../ide/reference/shell-command.md)|kabuk|Tools.Shell|
|Dosyalar içinde aramayı Durdur|StopFind|Edit.findınfiles/stop|
|Yer işaretini değiştir|SwapAnchor|Edit.SwapAnchor|
|Adımla|t|Debug.StepInto|
|Seçimi sekmeye Dönüştür|sekmelere ayırma|Edit.TabifySelection|
|Görev Listesi penceresi|Görev listesi|View.TaskList|
|İş Parçacıkları penceresi|İş Parçacıkları|Debug.Threads|
|Yatay Döşe|TileH|Window.TileHorizontally|
|Dikey Döşe|TileV|Window.TileVertically|
|Yer İşaretini Değiştir|ToggleBook|Edit.ToggleBookmark|
|Araç penceresi|araç kutusu|View.Toolbox|
|[Ayrıştırılmış Kodu Listele Komutu](../../ide/reference/list-disassembly-command.md)|u|Debug.ListDisassembly|
|Büyük Harf Yap|UCase|Edit.MakeUppercase|
|Geri alma|Geri alma|Edit.Undo|
|Seçimin sekmesini Kaldır|Sekmeye dönüştürme|Edit.UntabifySelection|
|Gözcü penceresi|İzleme|Debug.WatchN|
|Sözcük kaydırmayı Aç/Kapat|WordWrap|Edit.ToggleWordWrap|
|Süreçleri Listele|&#124;|Debug.ListProcesses|
|[İş Parçacıklarını Listele Komutu](../../ide/reference/list-threads-command.md)|~ ~ * k ~\*kb|Debug.ListThreads Debug.ListTheads /AllThreads|

## <a name="see-also"></a>Ayrıca Bkz.

- [Visual Studio Komutları](../../ide/reference/visual-studio-commands.md)
- [Komut Penceresi](../../ide/reference/command-window.md)
- [Bul/Komut Kutusu](../../ide/find-command-box.md)