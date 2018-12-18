---
title: Diğer diller için düzenleyici desteği ekleme | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- syntax colorization
- IntelliSense
- IDE, navigation
- documents [Visual Studio], navigation
- TextMate bundle
- TextMate language grammar
- language support
ms.assetid: d78c43ee-4ef2-42e5-984e-d137de4e7e92
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: fa622ddb6d840698d1134e0fec1540d99b44f5e2
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53049800"
---
# <a name="adding-visual-studio-editor-support-for-other-languages"></a>Diğer diller için Visual Studio Düzenleyicisi desteği ekleme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Okuma ve farklı bir bilgisayara dil arasında gezinme Visual Studio Düzenleyicisi'ni nasıl destekler ve diğer diller için Visual Studio Düzenleyicisi desteği nasıl ekleyebileceğinizi öğrenin.

## <a name="syntax-colorization-statement-completion-and-navigate-to-support"></a>Söz dizimi renklendirme ve deyim tamamlama gitmek için destek
 Visual Studio Düzenleyicisi söz dizimi renklendirme, ifade tamamlama ve gezinme gibi özellikler, daha kolay okumak, oluşturmak ve kodunuzu düzenleyin yardımcı olabilir. Aşağıdaki ekran görüntüsünde, Perl komut dosyasını Visual Studio'da düzenleme bir örnek gösterilmektedir. Söz dizimi, otomatik olarak renklendirilir. Örneğin, kod içindeki açıklamalar yeşil renktedir kodudur siyah yolları kırmızı ve deyimleri mavi. Visual Studio Düzenleyicisi söz dizimi renklendirme desteklediği herhangi bir dil için otomatik olarak uygular. Ayrıca, bilinen dil anahtar sözcüğü veya nesne girmeye başladığınızda, deyim tamamlama olası deyimleri ve nesnelerin bir listesini görüntüler. Deyim tamamlama, kod daha hızlı ve kolay bir şekilde oluşturmanıza yardımcı olabilir.

 ![Perl komut söz dizimi renklendirme](../ide/media/vside-perledit.png "VSIDE_PerlEdit")

 Visual Studio şu anda sağlar söz dizimi renklendirme ve temel deyim tamamlama desteği aşağıdaki dillerde kullanarak [TextMate dil bilgileri](https://manual.macromates.com/en/language_grammars). Favori dilinizi tabloda yoksa, ancak endişelenmeyin - ekleyebilirsiniz.

|||||||
|-|-|-|-|-|-|
|BAT|F#|Java|Markdown|Rust|Visual Basic|
|Clojure|Git|JavaDoc|Objective-C|ShaderLab|Visual C#|
|CMake|Groovy|JSON|Perl|ShellScript|Visual C++|
|CoffeeScript|HTML|DAHA AZ|Python|SQL|VBNet|
|CSS|INI|LUA|R|Swift|XML|
|Docker|Jade|Marka|Ruby|TypeScript|YAML|

 Söz dizimi renklendirme ve temel deyim tamamlama ek olarak, Visual Studio de denilen bir özelliği olan [gitmek için](https://blogs.msdn.microsoft.com/benwilli/2015/04/09/visual-studio-tip-3-use-navigate-to/). Bu özellik, hızla kod dosyaları, dosya yolları ve kod semboller aramanıza olanak sağlar. Visual Studio aşağıdaki dillerde gitmek için destek sağlar.

- Git

- Java

- JavaScript

- PHP

- TypeScript

- Visual Basic

- Visual C++

- Visual C#

  Bu dosya türlerini belirli bir dil henüz yüklenmemiştir desteği özellikleri açıklandığı gibi daha önce bile sahiptir. Bazı diller için özelleştirilmiş desteğini yükleme, IntelliSense gibi ek dil desteği veya ampuller gibi diğer Gelişmiş dil özellikleri sağlayabilir.

## <a name="adding-support-for-non-supported-languages"></a>Desteklenmeyen dilleri için destek ekleme
 Visual Studio 2015 güncelleştirme 1 ve sonraki sürümlerinde sağlamak Düzenleyicisi'nde dil desteği kullanılarak [TextMate dil bilgileri](https://manual.macromates.com/en/language_grammars). En sevdiğiniz programlama dili Visual Studio Düzenleyicisi'nde şu anda desteklenmemektedir, ilk olarak, Web'de arama - TextMate paketi dil için zaten var olabilir. Ancak, bir bulamazsanız, Visual Studio 2015 güncelleştirme 1 veya daha sonra dil dilbilgisi ve kod parçacıkları için TextMate paketi model oluşturma desteği, kendiniz ekleyebilirsiniz.

 Visual Studio aşağıdaki klasörde yeni TextMate dil bilgileri ekleyin:

 %userprofile%\\.vs\Extensions

 Bunlar kendi durumunuza uygularsanız, bu taban yolu altında aşağıdaki klasörleri ekleyin:

|Klasör adı|Açıklama|
|-----------------|-----------------|
|\\*\<dil adı >*|Dil klasörü. Değiştirin  *\<dil adı >* dil adı. Örneğin, **\Matlab**.|
|\Syntaxes|Dilbilgisi klasör. Dil dilbilgisi .json dosyaları gibi içeren **Matlab.json**.|
|\Snippets|Kod parçacıklarının klasör. Dili için kod parçacıkları içerir.|

 Windows % USERPROFILE % yolunu Çözümler: c:\Users\\*\<kullanıcı adı >*. Uzantılar klasörünün sisteminizde mevcut değilse, oluşturmanız gerekir. Klasör zaten varsa, gizlenir.

 TextMate dil bilgisi oluşturma hakkında daha fazla bilgi için bkz [TextMate – dil dilbilgisi giriş: HTML kaynak kod söz dizimi vurgulama ekleme katıştırılmış](https://developmentality.wordpress.com/2011/02/08/textmate-introduction-to-language-grammars/) ve [dil dilbilgisi ve özel oluşturma ile ilgili notlar Textmate paketi için tema](https://benparizek.com/notebook/notes-on-how-to-create-a-language-grammar-and-custom-theme-for-a-textmate-bundle).

## <a name="see-also"></a>Ayrıca Bkz.
 [Visual Studio 2013'ün Git geliştirmeleri](https://blogs.msdn.microsoft.com/mvpawardprogram/2013/10/22/visual-studio-2013-navigate-to-improvements/) [izlenecek yol: kod parçacığı oluşturma](../ide/walkthrough-creating-a-code-snippet.md) [izlenecek yol: deyim tamamlamayı görüntüleme](../extensibility/walkthrough-displaying-statement-completion.md)
