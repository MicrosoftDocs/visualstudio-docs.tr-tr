---
title: Kod stili tercihleri
ms.date: 03/10/2017
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.CSharp.Code_Style.General
- VS.ToolsOptionsPages.Text_Editor.Basic.Code_Style.General
ms.workload:
- multiple
ms.openlocfilehash: 718110b3339628052d8a4a2e3ebbcdd163707a97
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53065267"
---
# <a name="code-style-preferences"></a>Kod stili tercihleri

Kod stili tercihleri ayarlanabilir C# ve Visual Basic projeleri için açarak **seçenekleri** iletişim kutusundan **Araçları** menüsü. İçinde **seçenekleri** iletişim kutusunda **metin düzenleyici** > [**C#** veya **temel**] > **kod stili**  >  **Genel**. Bu pencerede seçenekleri, yalnızca yerel makine için geçerlidir.

Listedeki her bir öğe seçildiğinde tercih önizlemesini sunar:

![Kod stili seçenekleri](media/code-style-quick-actions-dialog.png)

> [!NOTE]
> Bu konu, Windows üzerinde Visual Studio için geçerlidir. Mac için Visual Studio için bkz: [Mac için Visual Studio'daki Düzenleyici davranışı](/visualstudio/mac/editor-behavior).

## <a name="preference-and-severity"></a>Tercihi ve önem derecesi

Her öğe için ayarladığınız **tercih** ve **önem derecesi** açılan listeler, her satırda kullanarak değerleri. Önem derecesi ayarlanabilir **hiçbiri**, **öneri**, **uyarı**, veya **hata**. Etkinleştirmek istiyorsanız [hızlı Eylemler](../ide/quick-actions.md) emin olmak için bir kod stili **önem derecesi** ayarı için bir şey dışında **hiçbiri**. **Hızlı Eylemler** ampul ![küçük ampul](media/vs2015_lightbulbsmall.png) tercih edilmeyen bir stili kullanılır ve bir seçenek seçebileceğiniz görüntülendiğinde **hızlı Eylemler** için listeleyin otomatik olarak tercih edilen stili kodu yeniden yazın.

## <a name="editorconfig-files"></a>EditorConfig dosyaları

.NET ile de yönetilebilir için kod stili ayarları bir [EditorConfig](../ide/editorconfig-code-style-settings-reference.md) dosya. EditorConfig dosyasındaki ayarları önceliklidir seçili Seçenekler **seçenekleri** iletişim kutusu. EditorConfig dosya zorlamak ve tüm depoyu veya proje için kodlama stili yapılandırmak için kullanabilirsiniz.

## <a name="format-document-command"></a>Biçim belgesi komutu

Visual Studio 2017 sürüm 15,8 ve daha sonra yapılandırdığınız **belgeyi Biçimlendir** komut (**Düzenle** > **Gelişmiş**  >  **Belgeyi Biçimlendir**) ek kod temizleme bir dosya üzerinde gerçekleştirilecek gibi kaldırın ve kullanımları sıralama veya kod stili tercihleri uygulayın. İstediğiniz hangi ayarların tanımlayabilirsiniz **belgeyi Biçimlendir** uygulamak için [biçimlendirme seçenekleri sayfasında](reference/options-text-editor-csharp-formatting.md#format-document-settings).

Kod temizleme uyar yapılandırılan ayarları bir *.editorconfig* dosya veya bu kuralı veya bu kümesindeki dosya eksik **Araçları** > **seçenekleri**  >  **Metin düzenleyici**  >  **C#** > [**kod stili** veya **biçimlendirme**].

Tetiklenen ilk kez **belgeyi Biçimlendir** komutu Visual Studio 2017'de bir sarı bir bilgi çubuğu kod temizleme ayarlarınızı yapılandırmak ister.

> [!TIP]
> Yapılandırılan kuralları **hiçbiri** içinde bir *.editorconfig* dosya kodu temizleme katılmak yoktur, ancak ayrı ayrı aracılığıyla uygulanabilir **hızlı Eylemler ve yeniden düzenlemeler** menüsü.

## <a name="see-also"></a>Ayrıca bkz.

- [Hızlı Eylemler](../ide/quick-actions.md)
- [Kodlama kuralı ayarlarına EditorConfig için .NET](../ide/editorconfig-code-style-settings-reference.md)
- [Düzenleyici davranışı (Mac için Visual Studio)](/visualstudio/mac/editor-behavior)