---
title: R için Yardım penceresini
description: Yardımcı R etkileşimli pencerede Visual Studio aracılığıyla doğrudan tümleşik? komutu.
ms.date: 01/24/2018
ms.prod: visual-studio-dev15
ms.technology: vs-rtvs
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: douge
ms.workload:
- data-science
ms.openlocfilehash: 6576a701abe699bfe47666acfc21c848dde1f53a
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "35666689"
---
# <a name="help-in-r-tools-for-visual-studio"></a>Visual Studio için R Araçları'nda Yardım

Yardımcı R etkileşimli penceresi Visual Studio'da doğrudan tümleşik. Herhangi bir zamanda kullandığınız `?` komutu gibi `?mtcars`, Yardım R belgelerindeki bir Visual Studio penceresinde görüntülenir:

![Visual Studio'daki Yardım](media/help-window.png)

> [!Tip]
> Yardım penceresini Visual Studio'da, diğer tüm gibi düzenlenmiş ve istediğiniz gibi yerleşik. Bkz: [Visual Studio'da pencere düzenlerini özelleştirme](../ide/customizing-window-layouts-in-visual-studio.md).
>
> Yardım sonuçları bir tarayıcıda açmak için seçmeniz **R Araçları** > **seçenekleri** menü ve kümesi **R tarayıcı yardımcı** özelliğini `External`. Bkz: [seçenekleri](options-for-r-tools-in-visual-studio.md).

Yardım aramak için kullanın `??` komutuna tarafından arama terimi. Arama terimi boşluk içeriyorsa tırnak işareti kullanın:

```R
??"Motor Trend"
```

![Yardım arama sonuçları](media/help-search1.png)

Yardım penceresini de üzerinden, daha fazla dokumentace R aramalarda doğrudan oluşturabilecekler arama giriş alanı vardır:

![Giriş alanını kullanarak Yardım arama sonuçları](media/help-search2.png)

## <a name="integrated-help-lookup"></a>Tümleşik Yardım arama

Geliştiriciler genellikle dokumentace R işlev adları, veri kümeleri ve diğer öğeleri hakkında Yardım almak için arama yapın. R araçları için Visual Studio (RTVS) Yardım aramaları Düzenleyicisi ve etkileşimli pencere ile tümleştirerek sürecini kolaylaştırır.

- Tuşuna basarak **F1** otomatik tamamlama işlemi sırasında alt dizeyi eşleştirin Yardım sonuçların listesini oluşturur.
- Bir arama terimi (örneğin, bir işlev) sağ tıklayıp **Yardım** komut söz konusu işlev için Yardım açar. Kullanarak da çağırabilirsiniz **Yardım** herhangi bir seçim için.

    ![Sağ tıklayıp bağlam menüsü aracılığıyla çağrılıyor Yardım](media/help-right-click.png)

> [!Tip]
> Tümleşik Yardım bir tarayıcıda açmak için seçmeniz **R Araçları** > **seçenekleri** ayarlayıp **F1 Web tarayıcısı** için `External`. Bkz: [seçenekleri](options-for-r-tools-in-visual-studio.md).

## <a name="integrated-stackoverflow-search"></a>Tümleşik StackOverflow arama

R belgelerinde arama ek olarak, geliştiriciler genellikle StackOverflow kod yazarken arama yapın. Bu işlem de RTVS kolaylaştırır. Bir terimi ya da seçimi, seçim sağ **Hledat na webu** komut (**Ctrl**+**F1**), ve Visual Studio, arama sonuçlarının kapsamı olan bir pencere açar StackOverflow:

![Visual Studio'da Web arama sonuçları](media/help-web-search-results.png)

Eklenen kapsanan dize değiştirebilirsiniz `R site:stackoverflow`temellidir **R Araçları** > **seçenekleri** > **F1 Web arama dizesi** seçeneği:

![F1 Web arama dizesini değiştirme](media/options-dialog.png)

Sonuçları bir tarayıcıda görüntülemek isterseniz değiştirme **F1 Web tarayıcısı** seçeneğinin üzerinde açıklandığı [seçenekleri](options-for-r-tools-in-visual-studio.md).