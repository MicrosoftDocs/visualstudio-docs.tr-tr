---
title: Diğer diller için düzenleyici desteği eklendi
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- syntax colorization
- IntelliSense
- IDE, navigation
- documents [Visual Studio], navigation
- TextMate bundle
- TextMate language grammar
- language support
ms.assetid: d78c43ee-4ef2-42e5-984e-d137de4e7e92
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: f0ac463161d42e0d9ddf6b845b752916675ba4fe
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53062101"
---
# <a name="add-visual-studio-editor-support-for-other-languages"></a>Diğer diller için Visual Studio Düzenleyicisi desteği Ekle

Okuma ve farklı bir bilgisayara dil arasında gezinme Visual Studio Düzenleyicisi'ni nasıl destekler ve diğer diller için Visual Studio Düzenleyicisi desteği nasıl ekleyebileceğinizi öğrenin.

## <a name="syntax-colorization-statement-completion-and-navigate-to-support"></a>Söz dizimi renklendirme ve deyim tamamlama gitmek için destek

Visual Studio Düzenleyicisi söz dizimi renklendirme, deyim tamamlama (IntelliSense olarak da bilinir) gibi özellikleri ve _gitmek için_ daha kolayca yazma, okuma ve kodunuzu düzenleyin yardımcı olabilir. Aşağıdaki ekran görüntüsünde, Perl komut dosyasını Visual Studio'da düzenleme bir örnek gösterilmektedir. Söz dizimi, otomatik olarak renklendirilir. Örneğin, kod içindeki açıklamalar yeşil renktedir kodudur siyah yolları kırmızı ve deyimleri mavi. Visual Studio Düzenleyicisi söz dizimi renklendirme desteklediği herhangi bir dil için otomatik olarak uygular. Ayrıca, bilinen dil anahtar sözcüğü veya nesne girmeye başladığınızda, deyim tamamlama olası deyimleri ve nesnelerin bir listesini görüntüler. Deyim tamamlama daha hızlı ve kolay bir şekilde kod yazmanıza yardımcı olabilir.

![Perl komut söz dizimi renklendirme](../ide/media/vside_perledit.png)

Visual Studio şu anda sağlar söz dizimi renklendirme ve temel deyim tamamlama desteği aşağıdaki dillerde kullanarak [TextMate dil bilgileri](https://manual.macromates.com/en/language_grammars). Favori dilinizi tabloda yoksa, ancak endişelenmeyin - ekleyebilirsiniz.

|||||||
|-|-|-|-|-|-|
|BAT|F#|Java|Markdown|Rust|Visual Basic|
|Clojure|Git|JavaDoc|Objective-C|ShaderLab|C#|
|CMake|Groovy|JSON|Perl|ShellScript|Visual C++|
|CoffeeScript|HTML|DAHA AZ|Python|SQL|VBNet|
|CSS|INI|LUA|R|Swift|XML|
|Docker|Jade|Marka|Ruby|TypeScript|YAML|

Söz dizimi renklendirme ve temel deyim tamamlama ek olarak, Visual Studio de denilen bir özelliği olan [gitmek için](https://blogs.msdn.microsoft.com/benwilli/2015/04/09/visual-studio-tip-3-use-navigate-to/). Bu özellik, hızla kod dosyaları, dosya yolları ve kod semboller aramanıza olanak sağlar. Visual Studio aşağıdaki dillerde gitmek için destek sağlar.

-   Git

-   Java

-   JavaScript

-   PHP

-   TypeScript

-   Visual Basic

-   Visual C++

-   C#

Bu dosya türlerini belirli bir dil henüz yüklenmemiştir desteği özellikleri açıklandığı gibi daha önce bile sahiptir. Bazı diller için özelleştirilmiş desteğini yükleme, IntelliSense gibi ek dil desteği veya ampuller gibi diğer Gelişmiş dil özellikleri sağlayabilir.

## <a name="add-support-for-non-supported-languages"></a>Desteklenmeyen dilleri desteği ekleme

Visual Studio 2015 güncelleştirme 1 ve sonraki sürümlerinde sağlamak Düzenleyicisi'nde dil desteği kullanılarak [TextMate dil bilgileri](https://manual.macromates.com/en/language_grammars). En sevdiğiniz programlama dili Visual Studio Düzenleyicisi'nde şu anda desteklenmemektedir, ilk olarak, Web'de arama - TextMate paketi dil için zaten var olabilir. Ancak, bir bulamazsanız, Visual Studio 2015 güncelleştirme 1 veya daha sonra dil dilbilgisi ve kod parçacıkları için TextMate paketi model oluşturma desteği, kendiniz ekleyebilirsiniz.

Visual Studio aşağıdaki klasörde yeni TextMate dil bilgileri ekleyin:

*%userprofile%\\.vs\Extensions*

Bunlar kendi durumunuza uygularsanız, bu taban yolu altında aşağıdaki klasörleri ekleyin:

|Klasör adı|Açıklama|
|-----------------|-----------------|
|\\*\<dil adı >*|Dil klasörü. Değiştirin  *\<dil adı >* dil adı. Örneğin, *\Matlab*.|
|*\Syntaxes*|Dilbilgisi klasör. Dil bilgisi içeren *.json* dil için gibi dosyaları *Matlab.json*.|
|*\Snippets*|Kod parçacıklarının klasör. Dili için kod parçacıkları içerir.|

Windows içinde *% USERPROFILE %* yolunu Çözümler: *c:\Users\\\<kullanıcı adı >*. Uzantılar klasörünün sisteminizde mevcut değilse, oluşturmanız gerekir. Klasör zaten varsa, gizlenir.

TextMate dil bilgisi oluşturma hakkında daha fazla bilgi için bkz [TextMate - dil dilbilgisi giriş: HTML kaynak kod söz dizimi vurgulama ekleme katıştırılmış](https://developmentality.wordpress.com/2011/02/08/textmate-introduction-to-language-grammars/) ve [dil dilbilgisi ve özel oluşturma ile ilgili notlar Textmate paketi için tema](https://benparizek.com/notebook/notes-on-how-to-create-a-language-grammar-and-custom-theme-for-a-textmate-bundle).

## <a name="see-also"></a>Ayrıca bkz.

- [İzlenecek Yol: Kod parçacığı oluşturma](../ide/walkthrough-creating-a-code-snippet.md)
- [İzlenecek yol: Görüntü deyim tamamlama](../extensibility/walkthrough-displaying-statement-completion.md)
