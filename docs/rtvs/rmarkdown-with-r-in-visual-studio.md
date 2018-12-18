---
title: R Markdown
description: Yüksek kaliteli raporları, sunuları ve panoları oluşturmak için Visual Studio'da R Markdown belgeleri oluşturma
ms.date: 11/16/2017
ms.prod: visual-studio-dev15
ms.technology: vs-rtvs
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: douge
ms.workload:
- data-science
ms.openlocfilehash: 1bb6779e0e8174dd10f209d9825ffb861d00455d
ms.sourcegitcommit: f685fa5e2df9dc307bf1230dd9dc3288aaa408b5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36238382"
---
# <a name="create-r-markdown-documents"></a>R Markdown belgeleri oluşturma

[R Markdown](https://rmarkdown.rstudio.com/) yüksek kaliteli belgeleri, raporları, sunuları ve panolar analiz R etkinleştiren bir belge biçimidir.

R araçları için Visual Studio (RTVS) bir R Markdown öğesi şablonu sağlar, Düzenleyici (IntelliSense de dahil olmak üzere R kodu Düzenleyicisi içinde), dosya oluşturma yeteneklerini desteklemek ve Canlı Önizleme.

## <a name="using-r-markdown"></a>R Markdown kullanma

1. Visual Studio’yu kapatın.
1. (Yalnızca bir kez) Yükleme `pandoc` gelen [pandoc.org](http://pandoc.org/installing.html).
1. Pandoc yüklemesini seçmeniz gerekir Visual Studio'yu yeniden başlatın.
1. Yükleme `knitr` ve `rmarkdown` yapmak için paketler [etkileşimli pencere](interactive-repl-for-r-in-visual-studio.md):

    ```R
    install.packages("knitr")
    install.packages("rmarkdown")

    ```
1. Yeni bir R Markdown dosyası kullanarak oluşturmak **dosya** > **yeni** > **dosya** menü komutu ve seçerek **R**  >  **R Markdown** listeden. Bir proje bağlamında, Çözüm Gezgini'nde projeye sağ tıklayın ve seçin **eklemek R Markdown** (veya **Ekle** > **yeni öğe** ve seçerek**R Markdown** listeden).

1. Yeni dosya varsayılan içeriğini aşağıdaki gibidir:

    ~~~markdown
    ---
    title: "Untitled"
    output: html_document
    ---

    This is an R Markdown document. Markdown is a simple formatting syntax for authoring HTML, PDF, and Microsoft Word documents. For more details on using R Markdown see <http://rmarkdown.rstudio.com>.

    When you click the **R Tools | Publish | Preview** button a document will be generated that includes both content as well as the output of any embedded R code chunks within the document. You can embed an R code chunk like this:

    ```{r}
    summary(cars)
    ```

    You can also embed plots, for example:

    ```{r, echo=FALSE}
    plot(cars)
    ```

    Note that the `echo = FALSE` parameter was added to the code chunk to prevent printing of the R code that generated the plot.

    ~~~

## <a name="previews"></a>Önizlemeler

Visual Studio 2017 15,5 ve sonraki sürümleri, Canlı Önizleme R Markdown için otomatik olarak sağlayın. Düzenleyici ve önizleme arasında otomatik eşitlemeyi etkinleştirmek için seçin **R Araçları** > **Markdown** > **otomatik eşitleme** ( **CTRL**+**Shift**+**Y**). Otomatik eşitleme kullanmıyorsanız, Önizleme kullanarak yenileyebilirsiniz **R Araçları** > **Markdown** > **yeniden R Markdown önizlemesini**.

Microsoft Word biçimleri Düzenleyicisi'nde sağ tıklayıp aşağıdakilerden birini seçerek ve HTML, PDF, dosyasında da önizleyebilirsiniz **Önizleme** komutları. Aynı komutları da kullanılabilir **R Araçları** > **Markdown** menüsü. (Visual Studio'nun önceki sürümleri, bu komutları üzerinde bulunan **R Araçları** > **Yayımla** menü.)

![RMarkdown Canlı Önizleme ve diğer Önizleme menü komutları](media/rmarkdown-live-preview.png)
