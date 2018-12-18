---
title: Kodlanmış UI Testlerinde HTML5 Denetimleri Kullanma
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: conceptual
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: a603a662c9007ab3ee0e66df0b23959bfdce83fb
ms.sourcegitcommit: ae46be4a2b2b63da7e7049e9ed67cd80897c8102
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/05/2018
ms.locfileid: "52896203"
---
# <a name="using-html5-controls-in-coded-ui-tests"></a>Kodlanmış UI testlerinde HTML5 denetimleri kullanma

Kodlanmış UI testleri, Internet Explorer 9 ve Internet Explorer 10 HTML5 denetimleri bazıları için destek içerir.

[!INCLUDE [coded-ui-test-deprecation](includes/coded-ui-test-deprecation.md)]

 **Gereksinimler**

-   Visual Studio Enterprise

> [!WARNING]
> Internet Explorer 10 önceki sürümlerinde, kodlanmış UI testleri, Internet Explorer işlemi kıyasla daha yüksek bir ayrıcalık düzeyinde çalıştırmak mümkün oldu. Kodlanmış UI testleri, Internet Explorer 10'da çalıştırırken, kodlanmış UI testi hem de Internet Explorer işlemi aynı ayrıcalık düzeyinde olması gerekir. Internet Explorer 10 daha güvenli bir AppContainer özellikleri nedeniyle budur.

> [!WARNING]
> Internet Explorer 10'da kodlanmış UI testi oluşturursanız, Internet Explorer 9 veya Internet Explorer 8 kullanarak çalışmayabilir. Internet Explorer 10, ses, Video, ProgressBar ve kaydırıcı gibi HTML5 denetimlerini içermesidir budur. Bu HTML5 denetimleri, Internet Explorer 9 veya Internet Explorer 8 tarafından tanınmaz. Benzer şekilde, Internet Explorer 9 kullanarak kodlanmış UI testleri, Internet Explorer 8 tarafından tanınmayacak bazı HTML5 denetimleri de içerebilir.

## <a name="audio-control"></a>Ses denetimi

**Ses denetimi:** HTML5 sesi denetim eylemleri doğru şekilde kaydedilir ve kayıttan yürütülebilir.

![HTML5 sesi denetimi](../test/media/codedui_html5_audio.png)

|Eylem|Kaydetme|Oluşturulan kod|
|-|---------------|-|
|**Ses kaydını oynatın**<br /><br /> Doğrudan denetimi veya denetimleri bağlam menüsü.|Play \<adı > ses 00:00:00|HtmlAudio.Play(TimeSpan)|
|**Ses belirli bir sürede arama**|Arama \<adı > ses 00:01:48|HtmlAudio.Seek(TimeSpan)|
|**Duraklatma ses**<br /><br /> Doğrudan denetimi veya denetimleri bağlam menüsü.|Duraklatma \<adı > 00:01:53, ses|HtmlAudio.Pause(TimeSpan)|
|**Sesi kapa ses**<br /><br /> Doğrudan denetimi veya denetimleri bağlam menüsü.|Sesi kapa \<adı > ses|HtmlAudio.Mute()|
|**Ses sesi Aç**<br /><br /> Doğrudan denetimi veya denetimleri bağlam menüsü.|Sesi Aç \<adı > ses|HtmlAudio.Unmute()|
|**Ses birimi değiştirin**|Ayarlama hacmi \<adı > ses % 79 arasında değişiyor|HtmlAudio.SetVolume(float)|

Bkz: [HTMLAudioElement](https://developer.mozilla.org/docs/Web/API/HTMLAudioElement) onaylama üzerinde ekleyebileceğiniz özellikler listesi.

 **Arama özellikleri:** arama özelliklerini `HtmlAudio` olan `Id`, `Name` ve `Title`.

 **Filtre özellikleri:** filtre özelliklerini `HtmlAudio` olan `Src`, `Class`, `ControlDefinition` ve `TagInstance`.

> [!NOTE]
> Arama ve duraklatma süreyi önemli ölçüde fazla olabilir. Kayıttan yürütme sırasında kodlanmış UI testi belirtilen süre içinde kadar bekleyin `(TimeSpan)` ses duraklatmadan önce. Bazı özel durumda tarafından duraklatma komutunu ulaşmaktan önce belirtilen zaman geçtiyse, bir özel durum oluşturulur.


## <a name="video-control"></a>Video denetimi
 **Video denetimi:** HTML5 Video denetimi eylemlerini doğru şekilde kaydedilir ve kayıttan yürütülebilir.

 ![HTML5 Video denetimi](../test/media/codedui_html5_video.png)

|Eylem|Kaydetme|Oluşturulan kod|
|-|---------------|-|
|**Videoyu oynat**<br /><br /> Doğrudan denetimi veya denetimleri bağlam menüsü.|Play \<adı > Video 00:00:00|HtmlVideo.Play(TimeSpan)|
|**Belirli bir zaman video arama**|Arama \<adı > Video 00:01:48|HtmlVideo.Seek(TimeSpan)|
|**Videoyu Duraklat**<br /><br /> Doğrudan denetimi veya denetimleri bağlam menüsü.|Duraklatma \<adı > 00:01:53, Video|HtmlVideo.Pause(TimeSpan)|
|**Sesi kapa video**<br /><br /> Doğrudan denetimi veya denetimleri bağlam menüsü.|Sesi kapa \<adı > Video|HtmlVideo.Mute()|
|**Video Sesi Aç**<br /><br /> Doğrudan denetimi veya denetimleri bağlam menüsü.|Sesi Aç \<adı > Video|HtmlVideo.Unmute()|
|**Video toplu değiştirme**|Ayarlama hacmi \<adı > % 79 arasında değişiyor Video||

Bkz: [HTMLVideoElement](https://developer.mozilla.org/docs/Web/HTML/Element/video) onaylama üzerinde ekleyebileceğiniz özellikler listesi.

 **Arama özellikleri:** arama özelliklerini `HtmlVideo` olan `Id`, `Name` ve `Title`.

 **Filtre özellikleri:** filtre özelliklerini `HtmlVideo` olan `Src`, `Poster`, `Class`, `ControlDefinition` ve `TagInstance`.

> [!NOTE]
> Geri veya ileri sarma-30s veya +30s etiketleri kullanarak video, bu uygun zaman aramak için toplanacak.

## <a name="progressbar"></a>ProgressBar
 **ProgressBar denetimi:** ProgressBar olan interactable olmayan bir denetim. Onaylamalar ekleyebilirsiniz `Value` ve `Max` bu denetimin özelliklerini. Daha fazla bilgi için [HTMLProgressElement](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/progress).

 ![HTML5 ProgressBar denetimi](../test/media/codedui_html5_progressbar.png)

## <a name="see-also"></a>Ayrıca bkz.

- [HTML öğeleri](https://developer.mozilla.org/docs/Web/HTML/Element)
- [UI otomasyonunu kullanarak kodunuzu test etme](../test/use-ui-automation-to-test-your-code.md)
- [Kodlanmış UI testleri oluşturma](../test/use-ui-automation-to-test-your-code.md)
- [Kodlanmış UI testleri ve eylem kayıtları için desteklenen yapılandırmalar ve platformlar](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md)
