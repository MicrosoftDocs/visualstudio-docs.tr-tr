---
title: Kodlanmış UI testleri HTML5 denetimleri kullanma | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2000b214-ae92-4334-b549-aa0eb4f45fe1
caps.latest.revision: 19
ms.author: gewarren
manager: douge
ms.openlocfilehash: 92ee95d4840ab9a833adc1b0060117f0d6b94fbd
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49254468"
---
# <a name="using-html5-controls-in-coded-ui-tests"></a>Kodlanmış UI Testlerinde HTML5 Denetimleri Kullanma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Kodlanmış UI testleri, Internet Explorer 9 ve Internet Explorer 10 HTML5 denetimleri bazıları için destek içerir.  
  
 **Gereksinimler**  
  
-   Visual Studio Enterprise  
  
> [!WARNING]
>  Internet Explorer 10 önceki sürümlerinde, kodlanmış UI testleri, Internet Explorer işlemi kıyasla daha yüksek bir ayrıcalık düzeyinde çalıştırmak mümkün oldu. Kodlanmış UI testleri, Internet Explorer 10'da çalıştırırken, kodlanmış UI testi hem de Internet Explorer işlemi aynı ayrıcalık düzeyinde olması gerekir. Internet Explorer 10 daha güvenli bir AppContainer özellikleri nedeniyle budur.  
  
> [!WARNING]
>  Internet Explorer 10'da kodlanmış UI testi oluşturursanız, Internet Explorer 9 veya Internet Explorer 8 kullanarak çalışmayabilir. Internet Explorer 10, ses, Video, ProgressBar ve kaydırıcı gibi HTML5 denetimlerini içermesidir budur. Bu HTML5 denetimleri, Internet Explorer 9 veya Internet Explorer 8 tarafından tanınmaz. Benzer şekilde, Internet Explorer 9 kullanarak kodlanmış UI testleri, Internet Explorer 8 tarafından tanınmayacak bazı HTML5 denetimleri de içerebilir.  
  
## <a name="supported-html5-controls"></a>Desteklenen HTML5 denetimleri  
 Kodlanmış UI testleri, kayıt, kayıttan yürütme ve doğrulamayı aşağıdaki HTML5 denetimleri için destek içerir:  
  
-   [Ses denetimi](#UsingHTML5ControlsCodedUITestsAudio)  
  
-   [Video denetimi](#UsingHTML5ControlsCodedUITestsVideo)  
  
-   [Kaydırıcı](#UsingHTML5ControlsCodedUITestsSlider)  
  
-   [ProgressBar](#UsingHTML5ControlsCodedUITestsProgressBar)  
  
###  <a name="UsingHTML5ControlsCodedUITestsAudio"></a> Ses denetimi  
 **Ses denetimi:** HTML5 sesi denetim eylemleri doğru şekilde kaydedilir ve kayıttan yürütülebilir.  
  
 ![HTML5 sesi denetim](../test/media/codedui-html5-audio.png "CodedUI_HTML5_Audio")  
  
|Eylem|Kaydetme|Oluşturulan kod|  
|------------|---------------|--------------------|  
|**Ses kaydını oynatın**<br /><br /> Doğrudan denetimi veya denetimleri bağlam menüsü.|Play \<adı > ses 00:00:00|HtmlAudio.Play(TimeSpan)|  
|**Ses belirli bir sürede arama**|Arama \<adı > ses 00:01:48|HtmlAudio.Seek(TimeSpan)|  
|**Duraklatma ses**<br /><br /> Doğrudan denetimi veya denetimleri bağlam menüsü.|Duraklatma \<adı > 00:01:53, ses|HtmlAudio.Pause(TimeSpan)|  
|**Sesi kapa ses**<br /><br /> Doğrudan denetimi veya denetimleri bağlam menüsü.|Sesi kapa \<adı > ses|HtmlAudio.Mute()|  
|**Ses sesi Aç**<br /><br /> Doğrudan denetimi veya denetimleri bağlam menüsü.|Sesi Aç \<adı > ses|HtmlAudio.Unmute()|  
|**Ses birimi değiştirin**|Ayarlama hacmi \<adı > ses % 79 arasında değişiyor|HtmlAudio.SetVolume(float)|  
  
 Aşağıdaki özellikler HtmlAudio için kullanılabilir ve hepsinde onaylama ekleyebilirsiniz:  
  
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
  
 **Arama özellikleri:** arama özelliklerini `HtmlAudio` olan `Id`, `Name` ve `Title`.  
  
 **Filtre özellikleri:** filtre özelliklerini `HtmlAudio` olan `Src`, `Class`, `ControlDefinition` ve `TagInstance`.  
  
> [!NOTE]
>  Arama ve duraklatma süreyi önemli ölçüde fazla olabilir. Kayıttan yürütme sırasında kodlanmış UI testi belirtilen süre içinde kadar bekleyin `(TimeSpan)` ses duraklatmadan önce. Bazı özel durumda tarafından duraklatma komutunu ulaşmaktan önce belirtilen zaman geçtiyse, bir özel durum oluşturulur.  
  
###  <a name="UsingHTML5ControlsCodedUITestsVideo"></a> Video denetimi  
 **Video denetimi:** HTML5 Video denetimi eylemlerini doğru şekilde kaydedilir ve kayıttan yürütülebilir.  
  
 ![HTML5 Video denetimi](../test/media/codedui-html5-video.png "CodedUI_HTML5_Video")  
  
|Eylem|Kaydetme|Oluşturulan kod|  
|------------|---------------|--------------------|  
|**Videoyu oynat**<br /><br /> Doğrudan denetimi veya denetimleri bağlam menüsü.|Play \<adı > Video 00:00:00|HtmlVideo.Play(TimeSpan)|  
|**Belirli bir zaman video arama**|Arama \<adı > Video 00:01:48|HtmlVideo.Seek(TimeSpan)|  
|**Videoyu Duraklat**<br /><br /> Doğrudan denetimi veya denetimleri bağlam menüsü.|Duraklatma \<adı > 00:01:53, Video|HtmlVideo.Pause(TimeSpan)|  
|**Sesi kapa video**<br /><br /> Doğrudan denetimi veya denetimleri bağlam menüsü.|Sesi kapa \<adı > Video|HtmlVideo.Mute()|  
|**Video Sesi Aç**<br /><br /> Doğrudan denetimi veya denetimleri bağlam menüsü.|Sesi Aç \<adı > Video|HtmlVideo.Unmute()|  
|**Video toplu değiştirme**|Ayarlama hacmi \<adı > % 79 arasında değişiyor Video||  
  
 Tüm özelliklerini HtmlAudio HtmlVideo için kullanılabilir. Ayrıca, şu üç özellik de kullanılabilir. Onaylama işlemi hepsinde eklenebilir.  
  
```  
string Poster  
string VideoHeight  
string VideoWidth  
  
```  
  
 **Arama özellikleri:** arama özelliklerini `HtmlVideo` olan `Id`, `Name` ve `Title`.  
  
 **Filtre özellikleri:** filtre özelliklerini `HtmlVideo` olan `Src`, `Poster`, `Class`, `ControlDefinition` ve `TagInstance`.  
  
> [!NOTE]
>  Geri veya ileri sarma-30s veya +30s etiketleri kullanarak video, bu uygun zaman aramak için toplanacak.  
  
###  <a name="UsingHTML5ControlsCodedUITestsSlider"></a> Kaydırıcı  
 **Kaydırıcı denetimi:** HTML5 kaydırıcı denetimi eylemlerini doğru şekilde kaydedilir ve kayıttan yürütülebilir.  
  
 ![HTML5 kaydırıcı denetimi](../test/media/codedui-html5-slider.png "CodedUI_HTML5_Slider")  
  
|Eylem|Kaydetme|Oluşturulan kod|  
|------------|---------------|--------------------|  
|**Kaydırıcı konumda ayarlayın**|Kümesine konumu \<x > içinde \<adı > kaydırıcı|HtmlSlider.ValueAsNumber=\<x >|  
  
 Aşağıdaki özellikler HtmlSlider için kullanılabilir ve onaylama hepsinde eklenebilir:  
  
```  
string Disabled  
string Max  
string Min  
string Required  
string Step  
string ValueAsNumber  
```  
  
###  <a name="UsingHTML5ControlsCodedUITestsProgressbar"></a> ProgressBar  
 **ProgreesBar denetimi:** ProgressBar olan interactable olmayan bir denetim. Onaylamalar ekleyebilirsiniz `Value` ve `Max` bu denetimin özelliklerini.  
  
 ![HTML5 ProgressBar denetimi](../test/media/codedui-html5-progressbar.png "CodedUI_HTML5_ProgressBar")  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [HTML öğeleri](http://go.microsoft.com/fwlink/?LinkID=232441)   
 [Kodunuzu test etmek için UI otomasyonunu kullanma](../test/use-ui-automation-to-test-your-code.md)   
 [Kodlanmış UI testleri oluşturma](../test/use-ui-automation-to-test-your-code.md#VerifyingCodeUsingCUITCreate)   
 [Kodlanmış UI testleri özelleştirme](../test/use-ui-automation-to-test-your-code.md#VerifyingCodeCUITModify)   
 [Kodlanmış UI Testleri ve Eylem Kayıtları için Desteklenen Yapılandırmalar ve Platformlar](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md)



