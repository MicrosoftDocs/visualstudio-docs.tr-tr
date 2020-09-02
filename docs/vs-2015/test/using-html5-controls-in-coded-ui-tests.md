---
title: Kodlanmış UI testlerinde HTML5 denetimleri kullanma | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
ms.assetid: 2000b214-ae92-4334-b549-aa0eb4f45fe1
caps.latest.revision: 19
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 029b547102863f4798ad261deb678c4d98596916
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72657198"
---
# <a name="using-html5-controls-in-coded-ui-tests"></a>Kodlanmış UI Testlerinde HTML5 Denetimleri Kullanma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Kodlanmış UI testleri, Internet Explorer 9 ve Internet Explorer 10 ' da bulunan HTML5 denetimlerinin bazılarına yönelik destek içerir.

 **Gereksinimler**

- Visual Studio Enterprise

> [!WARNING]
> Internet Explorer 10 ' dan önceki sürümlerde, kodlanmış UI testlerini Internet Explorer süreciyle karşılaştırıldığında daha yüksek bir ayrıcalık düzeyinde çalıştırmak mümkün oldu. Internet Explorer 10 ' da kodlanmış UI testleri çalıştırılırken, hem kodlanmış UI testi hem de Internet Explorer işlemi aynı ayrıcalık düzeyinde olmalıdır. Bunun nedeni, Internet Explorer 10 ' da daha güvenli AppContainer özellikleri.

> [!WARNING]
> Internet Explorer 10 ' da kodlanmış UI testi oluşturursanız, Internet Explorer 9 veya Internet Explorer 8 kullanılarak çalışmayabilir. Bunun nedeni, Internet Explorer 10 ' un ses, video, ProgressBar ve kaydırıcı gibi HTML5 denetimlerini içermektir. Bu HTML5 denetimleri, Internet Explorer 9 veya Internet Explorer 8 tarafından tanınmaz. Benzer şekilde, Internet Explorer 9 kullanarak kodlanmış UI testleri, Internet Explorer 8 tarafından tanınmayacak bazı HTML5 denetimleri de içerebilir.

## <a name="supported-html5-controls"></a>Desteklenen HTML5 denetimleri
 Kodlanmış UI testleri, aşağıdaki HTML5 denetimlerinin kaydı, yürütülmesi ve doğrulanması için destek içerir:

- [Ses denetimi](#audio-control)

- [Video denetimi](#video-control)

- [Slider](#slider)

- [ProgressBar](#progressbar)

### <a name="audio-control"></a>Ses denetimi
 **Ses denetimi:** HTML5 ses denetimindeki eylemler doğru şekilde kaydedilir ve kayıttan yürütülür.

 ![HTML5 ses denetimi](../test/media/codedui-html5-audio.png)

|Eylem|Kayıt|Oluşturulan kod|
|------------|---------------|--------------------|
|**Ses çal**<br /><br /> Doğrudan denetimden veya denetimler bağlam menüsünden.|\<name>00:00:00 'den ses çal|Htmdefdio. Play (TimeSpan)|
|**Ses içinde belirli bir zamana arama**|\<name>Sesi 00:01:48 'e ara|Htmdefdio. Seek (TimeSpan)|
|**Sesi Duraklat**<br /><br /> Doğrudan denetimden veya denetimler bağlam menüsünden.|\<name>Sesi 00:01:53 ' de Duraklat|Htmdefdio. Pause (TimeSpan)|
|**Sesi sustur**<br /><br /> Doğrudan denetimden veya denetimler bağlam menüsünden.|Sesi sustur \<name>|Htmdefdio. Mute ()|
|**Sesi aç**<br /><br /> Doğrudan denetimden veya denetimler bağlam menüsünden.|\<name>Sesi aç|Htmdefdio. aç ()|
|**Ses düzeyini Değiştir**|\<name>Ses hacmini %79 olarak ayarla|Htmdefdio. SetVolume (float)|

 Aşağıdaki özellikler Htmdefdio için kullanılabilir ve bunların tümüne bir onaylama işlemi ekleyebilirsiniz:

```
string AutoPlay
string Controls
string CurrentSrc
string CurrentTime
string CurrentTimeAsString
string Duration
string DurationAsString
string Ended
string Loop
string Muted
string Paused
string PlaybackRate
string ReadyState
string Seeking
string Src
string Volume
```

 **Arama özellikleri:** İçin arama özellikleri `HtmlAudio` `Id` ve ' dir `Name` `Title` .

 **Filtre özellikleri:** İçin filtre özellikleri `HtmlAudio` `Src` , ve ' `Class` dir `ControlDefinition` `TagInstance` .

> [!NOTE]
> Arama ve duraklatma için zaman miktarı önemli olabilir. Kayıttan yürütme sırasında, kodlanmış UI testi sesi duraklatmadan önce içinde belirtilen zamana kadar bekler `(TimeSpan)` . Bazı özel durumlar tarafından, belirtilen süre duraklatma komutuna vurmadan önce geçmişse, bir özel durum oluşturulur.

### <a name="video-control"></a>Video denetimi
 **Video denetimi:** HTML5 video denetimindeki eylemler doğru şekilde kaydedilir ve kayıttan yürütülür.

 ![HTML5 video denetimi](../test/media/codedui-html5-video.png)

|Eylem|Kayıt|Oluşturulan kod|
|------------|---------------|--------------------|
|**Videoyu oynat**<br /><br /> Doğrudan denetimden veya denetimler bağlam menüsünden.|\<name>Videoyu 00:00:00 'den oynat|HtmlVideo. Play (TimeSpan)|
|**Videoda belirli bir zamana arama**|\<name>Videoyu 00:01:48 ile ara|HtmlVideo. Seek (TimeSpan)|
|**Videoyu Duraklat**<br /><br /> Doğrudan denetimden veya denetimler bağlam menüsünden.|\<name>Videoyu 00:01:53 adresinden Duraklat|HtmlVideo. Pause (TimeSpan)|
|**Videoyu sustur**<br /><br /> Doğrudan denetimden veya denetimler bağlam menüsünden.|Videoyu sustur \<name>|HtmlVideo. Mute ()|
|**Videoyu aç**<br /><br /> Doğrudan denetimden veya denetimler bağlam menüsünden.|\<name>Videoyu aç|HtmlVideo. aç ()|
|**Video hacmini değiştirme**|\<name>Video hacmini %79 olarak ayarlayın||

 Htmdefdio 'ın tüm özellikleri HtmlVideo için kullanılabilir. Ayrıca, aşağıdaki üç özellik de kullanılabilir. Onaylama, tümüne eklenebilir.

```
string Poster
string VideoHeight
string VideoWidth

```

 **Arama özellikleri:** İçin arama özellikleri `HtmlVideo` `Id` ve ' dir `Name` `Title` .

 **Filtre özellikleri:** İçin filtre özellikleri `HtmlVideo` ,, `Src` ve ' dir `Poster` `Class` `ControlDefinition` `TagInstance` .

> [!NOTE]
> -30s veya + 30s etiketlerini kullanarak videoyu geri sarın veya ileri sardıysanız, bu, uygun zamana göre arama yapmak için toplanır.

### <a name="slider"></a>Slider
 **Kaydırıcı denetimi:** HTML5 kaydırıcı denetimindeki eylemler doğru şekilde kaydedilir ve kayıttan yürütülür.

 ![HTML5 kaydırıcı denetimi](../test/media/codedui-html5-slider.png)

|Eylem|Kayıt|Oluşturulan kod|
|------------|---------------|--------------------|
|**Kaydırıcıda bir konum ayarlayın**|Konumu kaydırıcı olarak \<x> Ayarla \<name>|HtmlSlider. ValueAsNumber =\<x>|

 Aşağıdaki özellikler HtmlSlider için kullanılabilir ve bunların tümüne onay eklenebilir:

```
string Disabled
string Max
string Min
string Required
string Step
string ValueAsNumber
```

### <a name="progressbar"></a>ProgressBar
 **ProgressBar denetimi:** ProgressBar, ınteractable olmayan bir denetimdir. `Value` `Max` Bu denetimin ve özelliklerine onay ekleyebilirsiniz.

 ![HTML5 ProgressBar denetimi](../test/media/codedui-html5-progressbar.png)

## <a name="see-also"></a>Ayrıca bkz.

- [HTML öğeleri](https://www.w3schools.com/HTML/html_elements.asp)
- [Kodunuzu Test Etmek için UI Otomasyonunu Kullanma](../test/use-ui-automation-to-test-your-code.md)
- [Kodlanmış UI testleri oluşturma](../test/use-ui-automation-to-test-your-code.md#VerifyingCodeUsingCUITCreate)
- [Kodlanmış UI testinizi özelleştirme](../test/use-ui-automation-to-test-your-code.md#VerifyingCodeCUITModify)
- [Kodlanmış UI Testleri ve Eylem Kayıtları için Desteklenen Yapılandırmalar ve Platformlar](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md)
