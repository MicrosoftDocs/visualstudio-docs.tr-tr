---
title: R Markdown
description: Yüksek kaliteli raporlar, sunular ve panolar oluşturmak için Visual Studio 'da R Markdown belgeleri oluşturma.
ms.date: 11/16/2017
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: jmartens
ms.workload:
- data-science
ms.openlocfilehash: 4e74966e71a7d440aed918e8aa609eeb8e68c355
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99851887"
---
# <a name="create-r-markdown-documents"></a>R Markdown belgeleri oluşturma

[R Markdown](https://rmarkdown.rstudio.com/) , R 'deki Analizi yüksek kaliteli belgeler, raporlar, sunular ve panolar halinde etkinleştiren bir belge biçimidir.

Visual Studio için R Araçları (RTVS), R Markdown bir öğe şablonu, düzenleyici desteği (düzenleyici içindeki R kodu için IntelliSense dahil), dosya oluşturma özellikleri ve Canlı önizleme sağlar.

## <a name="using-r-markdown"></a>R Markdown kullanma

1. Visual Studio’yu kapatın.
1. (Yalnızca bir kez) `pandoc` [Pandoc.org](https://pandoc.org/installing.html)adresinden yükler.
1. Visual Studio 'yu yeniden başlatarak pandoc yüklemesini seçin.
1. `knitr` `rmarkdown` [Etkileşimli pencereden](interactive-repl-for-r-in-visual-studio.md)yapabileceğiniz ve paketlerini yükleyebilirsiniz:

    ```R
    install.packages("knitr")
    install.packages("rmarkdown")

    ```

1. **Dosya** yeni dosya menü komutunu kullanarak yeni bir R Markdown dosyası oluşturun  >    >   ve listeden **R**  >  **R Markdown** öğesini seçin. Bir proje bağlamında Çözüm Gezgini projeye sağ tıklayın ve **R Markdown Ekle** ' yi seçin (veya   >  **Yeni öğe** ekleyin ve listeden **R Markdown** seçeneğini belirleyin).

1. Yeni dosyanın varsayılan içeriği aşağıdaki gibidir:

    <!-- markdownlint-disable MD048 -->
    ~~~markdown
    ---
    title: "Untitled"
    output: html_document
    ---

    This is an R Markdown document. Markdown is a simple formatting syntax for authoring HTML, PDF, and Microsoft Word documents. For more details on using R Markdown see <http://rmarkdown.rstudio.com>.

    When you select the **R Tools | Publish | Preview** button, a document will be generated that includes both content as well as the output of any embedded R code chunks within the document. You can embed an R code chunk like this:

    ```{r}
    summary(cars)
    ```

    You can also embed plots, for example:

    ```{r, echo=FALSE}
    plot(cars)
    ```

    Note that the `echo = FALSE` parameter was added to the code chunk to prevent printing of the R code that generated the plot.

    ~~~
    <!-- markdownlint-disable MD048 -->

## <a name="previews"></a>Önizlemeler

Visual Studio 2017 sürüm 15,5 ve üzeri otomatik olarak R Markdown için Canlı önizleme sağlar. Düzenleyici ve önizleme arasındaki otomatik eşitlemeyi etkinleştirmek için **R araçları**  >  **markaşağı**  >  **Otomatik eşitleme** (**CTRL** + **Shift** + **Y**) seçeneğini belirleyin. Otomatik eşitleme kullanmıyorsanız, **R araçları**  >  **markaşağı**  >  **yeniden yükleme R Markdown önizleme**'yi kullanarak önizlemeyi yenileyebilirsiniz.

Ayrıca, düzenleyicide sağ tıklayıp **Önizleme** komutlarından birini seçerek dosyayı HTML, PDF ve Microsoft Word biçimlerinde da önizleyebilirsiniz. Aynı komutlar **R araçları**  >  **markaşağı** menüsünde de bulunur. (Visual Studio 'nun önceki sürümlerinde bu komutlar **R araçları**  >  'nda bulunur **Yayımla** menüsü.)

![Rmarkaşağı canlı önizleme ve diğer önizleme menü komutları](media/rmarkdown-live-preview.png)
