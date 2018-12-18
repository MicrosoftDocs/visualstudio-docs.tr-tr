---
title: Erişilebilirlik
description: Bu makale, Mac ve bunların nasıl etkinleştirilebilir için Visual Studio'nun erişilebilirlik özellikleri tanıtır.
author: conceptdev
ms.author: crdun
ms.date: 08/15/2017
ms.assetid: 2C4AAC2E-3B4A-4496-8BE0-1F5A7F81D1CA
ms.openlocfilehash: f90f5fca9d68ed00162fd746ddf291343c8d51f7
ms.sourcegitcommit: 0a8ac5f2a685270d9ca79bb39d26fd90099bfa29
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/09/2018
ms.locfileid: "51296352"
---
# <a name="accessibility"></a>Erişilebilirlik

Özellikler ve macOS yardımcı programlara ek olarak, Mac için Visual Studio daha erişilebilir engelli kişiler için kolaylaştırır aşağıdaki özelliklere sahiptir:

- Çözüm ve Düzenleyicisi bölmeleri metin büyütme
- Metin düzenleyicilerde boyut seçenekleri
- Düzenleyicilerde özelleştirme rengi
- Klavye kısayolunu özelleştirme
- Yöntem ve parametreler için kod tamamlama

MacOS erişilebilirlik özellikleri hakkında daha fazla bilgi için bkz. [Apple'nın Web sitesi](https://www.apple.com/accessibility/mac/).

## <a name="using-accessibility-features-in-visual-studio-for-mac"></a>Mac için Visual Studio'da erişilebilirlik özelliklerini kullanma

Mac için Visual Studio'nun erişilebilirlik özellikleri varsayılan olarak kapalıdır. Bunları etkinleştirmek için aşağıdaki adımları uygulayın:

1. Git **Visual Studio > Tercihler > Diğer > Erişilebilirlik**.

2. Seçin **etkinleştirme erişilebilirlik** Aşağıdaki diyagramda gösterildiği gibi onay kutusunu:

    ![Erişilebilirlik onay kutusunu etkinleştir](media/accessibility-image1.png)

3. Tuşuna **Visual Studio'yu yeniden başlatın** erişilebilirlik özellikleri etkili şekilde düğmesi.

Alternatif olarak, erişilebilirlik özelliklerini etkinleştirmek için komut satırını kullanabilirsiniz. Bunu yapmak için terminalde aşağıdaki komutu girin:

```bash
defaults write com.microsoft.visual-studio com.monodevelop.AccessibilityEnabled 1
```

Erişilebilirliği açtıktan sonra Visual Studio'yu yeniden başlatmanız gerekir.

## <a name="how-to-use-keyboard-navigation"></a>Nasıl yapılır: klavye gezintisini kullanma

Klavye ile gezinme, tam klavye erişim seçeneğini ayarlayarak etkinleştirilebilir **sistem tercihleri > klavye > kısayolları** için **tüm denetimleri**:

![Macos sistemleri Tercihler panelinde](media/accessibility-image2.png)

Odak dikdörtgenini üzerinde tam klavye erişim ayarı kapatır. Denetimleri kullanarak daha sonra seçebilirsiniz:

- Denetim boyunca ileri gitmek için sekmesinde
- Shift-Sekme denetim boyunca geriye Git
- Oklar yönünü denetimlerin arasında gezinmek için ok tuşları'ni kullanın.

Boşluk çubuğuna basarak odaklı denetimin etkinleştirir.

## <a name="how-to-enable-and-use-voice-over"></a>Nasıl yapılır: etkinleştirme ve Voice Over kullanma

VoiceOver tuşuna açıp kapatması **Cmd + F5**

UI VoiceOver komutları gitmek için aşağıdaki komutları kullanın:

- VoiceOver imleci denetimler arasında taşıma: **Ctrl + Alt + Sol Ok tuşu / sağ ok tuşu**

   Denetimleri, bazı ayrıntılarını ve onunla yapabileceklerinizi adı voiceOver okur.

- Gruplar ve denetimler (örneğin, çözüm bölmesi, araç ve diğer doldurmalar) girin: **Ctrl + Alt + Shift + aşağı ok**

   Kullanabileceğiniz bir denetimi içinde bir kez **Ctrl + Alt + ok** içinde hareket etmek için.

MacOS VoiceOver kullanma hakkında genel bilgi için aşağıdaki kılavuzlara bakın:

- [VoiceOver ile çalışmaya başlama](https://help.apple.com/voiceover/info/guide/10.12/)
- [MacOS voiceOver komutları](http://lab.dotjay.com/notes/voiceover-commands/)

## <a name="see-also"></a>Ayrıca bkz.

- [(Windows üzerinde) Visual Studio'nun erişilebilirlik özellikleri](/visualstudio/ide/reference/accessibility-features-of-visual-studio)