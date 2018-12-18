---
title: Dize Görselleştirici içinde dizelerini görüntüle | Microsoft Docs
ms.custom: ''
ms.date: 10/10/2018
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.debug.stringviewer
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
- SQL
helpviewer_keywords:
- string visualizer
- visualizers, string
ms.assetid: 080fd8f1-72b0-461f-8451-3c84d5dc51df
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: eb447a29ea669dbea3a68312884760f8984cc2de
ms.sourcegitcommit: dd839de3aa24ed7cd69f676293648c6c59c6560a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/27/2018
ms.locfileid: "52388562"
---
# <a name="view-strings-in-a-string-visualizer-in-visual-studio"></a>Visual Studio'da dize görselleştiricide dizelerini görüntüle

Visual Studio'da hata ayıklarken, dizeleri ile yerleşik dize Görselleştirici görüntüleyebilirsiniz. Dize Görselleştirici veri ipucu veya hata ayıklayıcı penceresi için çok uzun dizeler gösterir. Da hatalı biçimlendirilmiş dizeler belirlemenize yardımcı olabilir.

Düz metin, XML, HTML ve JSON yerleşik dize Görselleştirici içerir seçenekleri. Ayrıca WPF nesneleri gibi birkaç diğer türleri, görselleştiriciler açabileceğiniz **Otolar** ya da diğer hata ayıklayıcı pencereleri.

## <a name="open-a-string-visualizer"></a>Dize Görselleştirici açın

Dize Görselleştirici'ni açmak için hata ayıklama sırasında duraklatılmış gerekir. Düz metin, XML, HTML veya dize değeri ve Büyüteç simgesini seçerek JSON sahip bir değişken üzerine geldiğinizde ![VisualizerIcon](../debugger/media/dbg-tips-visualizer-icon.png "Görselleştirici simgesi").

![Dize Görselleştirici açın](../debugger/media/dbg-tips-string-visualizers.png "açık dize Görselleştirici")

## <a name="view-string-visualizer-data"></a>Dize Görselleştirici verileri görüntüle

Dize Görselleştirici penceresinde **ifade** alan değişkenin veya ifadenin, üzerine geldiğinizde gösterir ve **değer** alan dize değerini gösterir.

Boş bir **değer** seçilen görselleştiricisi dize tanıyamaz anlamına gelir. Örneğin, **XML Görselleştirici** boş gösterir **değer** bir metin dizesiyle XML etiket yok veya bir JSON dizesi.

Seçilen görselleştiricisi tanıyamaz dizeler görüntülemek için seçin **metin görselleştiricisi**. **Metin görselleştiricisi** düz metin gösterir.

### <a name="view-json-string-data"></a>JSON dizesi veri görünümü

İyi biçimlendirilmiş bir JSON dizesi aşağıdaki çizimde JSON Görselleştirici şunun gibi görünür. Hatalı biçimlendirilmiş JSON, bir hata simgesi (veya tanınmayan ise boş) görüntüleyebilir. JSON hatası tanımlamak için kopyalayın ve dize gibi bir JSON linting aracına yapıştırın [JSLint](https://www.jslint.com/).

![JSON dizesi Görselleştirici](../debugger/media/dbg-tips-string-visualizer-json.png "JSON dize Görselleştirici")

### <a name="view-xml-string-data"></a>XML dizesi veri görünümü

İyi biçimlendirilmiş bir XML dizesi aşağıdaki çizimde XML Görselleştirici şunun gibi görünür. Hatalı biçimlendirilmiş XML XML etiket veya boş tanınmayan varsa görüntülenebilir.

![XML dizesi Görselleştirici](../debugger/media/dbg-string-visualizers-xml.png "XML dize Görselleştirici")

### <a name="view-html-string-data"></a>Dize verileri HTML'yi görüntüle

İyi biçimlendirilmiş bir HTML dizesi görünür alacağı bir tarayıcıda aşağıdaki çizimde gösterildiği gibi çizilir. Hatalı biçimlendirilmiş HTML düz metin olarak görüntülenebilir.

![HTML dize Görselleştirici](../debugger/media/dbg-string-visualizers-html.png "HTML dize Görselleştirici")

## <a name="see-also"></a>Ayrıca bkz.

- [Özel görselleştiriciler (C#, Visual Basic) oluşturma](../debugger/create-custom-visualizers-of-data.md)
- [Mac için Visual Studio'da veri görselleştirmeleri](/visualstudio/mac/data-visualizations)