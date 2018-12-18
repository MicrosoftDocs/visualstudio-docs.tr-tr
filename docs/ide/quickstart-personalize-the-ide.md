---
title: Kümesi renk teması ve yazı tipleri
ms.date: 11/20/2017
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: quickstart
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 511c9d44e9aac49c0150be5a13651e5368e10eaf
ms.sourcegitcommit: 0cdd8e8a53fb4fd5e869f07c35204419fa12783d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53159418"
---
# <a name="quickstart-personalize-the-visual-studio-ide-and-editor"></a>Hızlı Başlangıç: Düzenleyici ve Visual Studio IDE'yi kişiselleştirme

5-10 dakika Bu hızlı başlangıçta, size Visual Studio renk teması koyu tema seçerek özelleştireceksiniz. Biz de iki farklı türde metin düzenleyicisinde metin renklerini özelleştireceksiniz.

Visual Studio henüz yüklemediyseniz, Git [Visual Studio indirmeleri](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) ücretsiz yüklemek için sayfa.

## <a name="set-the-color-theme"></a>Renk teması ayarlayabilir

Visual Studio 2017'in kullanıcı arabirimi için varsayılan renk teması adlı **mavi**. Kendisine değiştirelim **koyu**.

1. Menü çubuğunda, olan menüleri satırının gibi **dosya** ve **Düzenle**, seçin **Araçları** > **seçenekleri**.

1. Üzerinde **ortam** > **genel** seçenekler sayfası, değişiklik **renk teması** seçimi **koyu**seçin **Tamam**.

   Tüm Visual Studio geliştirme ortamı (IDE) için renk temasını değiştirme hedefi **koyu**.

   ![VS'de koyu tema](media/quickstart-personalize-dark-theme.png)

> [!TIP]
> Yükleyerek ek önceden tanımlı Temalar yükleyebilirsiniz **Visual Studio Color Theme Editor** gelen [Visual Studio Market](https://marketplace.visualstudio.com/items?itemName=VisualStudioPlatformTeam.VisualStudio2017ColorThemeEditor). Bu aracı yükledikten sonra ek renk temaları görünür **renk teması** aşağı açılan listesi.

## <a name="change-text-color"></a>Metin rengini değiştirme

Şimdi biz düzenleyici için bazı metin renklerini özelleştireceksiniz. İlk olarak, varsayılan renkleri görmek için yeni bir XML dosyası oluşturalım.

1. Menü çubuğundan seçin **dosya** > **yeni** > **dosya**.

1. İçinde **yeni dosya** iletişim kutusunun **genel** kategorisi seçin **XML dosyası**ve ardından **açık**.

1. Aşağıdaki XML içeren satırın altına yapıştırın `<?xml version="1.0" encoding="utf-8"?>`.

   ```xml
   <Catalog>
     <Book id="bk101">
     <Author>Garghentini, Davide</Author>
     <Title>XML Developer's Guide</Title>
     <Genre>Computer</Genre>
     <Price>44.95</Price>
     <PublishDate>2000-10-01</PublishDate>
     <Description>
       An in-depth look at creating applications with XML.
     </Description>
   </Book>
   <Book id="bk102">
     <Author>Garcia, Debra</Author>
     <Title>Midnight Rain</Title>
     <Genre>Fantasy</Genre>
     <Price>5.95</Price>
     <PublishDate>2000-12-16</PublishDate>
     <Description>
       A former architect battles corporate zombies, an evil
       sorceress, and her own childhood to become queen of the world.
     </Description>
   </Book>
   </Catalog>
   ```

   Satır numaralarını Turkuaz-mavi renk ve XML özniteliklerini olduğuna dikkat edin (gibi `id="bk101"`) bir açık mavi renk kodludur. Bu öğeler için metin rengini değiştirmek için ekleyeceğiz.

   ![XML dosyası yazı tipi renkleri](media/quickstart-personalize-xml-file.png)

1. Açmak için **seçenekleri** iletişim kutusunda **Araçları** > **seçenekleri** menü çubuğundan.

1. Altında **ortam**, seçin **yazı tipleri ve renkler** kategorisi.

   Dikkat altındaki metin **ayarlarını göster** diyor **metin düzenleyici**&mdash;istediğimiz budur. Yalnızca yerleri burada yazı tipleri ve metin rengini özelleştirebilirsiniz kapsamlı bir listesini görmek için açılan listeyi genişletin.

1. Satır numaraları metnin rengini değiştirmek için **görüntü öğeleri** listesinde **satır numarası**. İçinde **öğe ön plan** kutusunda **Zeytin**.

   ![Seçenekler iletişim kutusu, yazı tipleri ve renkler kategorisi](media/quickstart-personalize-line-number-color.png)

   Bazı diller, kendi özel yazı tipleri ve renkler ayarları vardır. C++ geliştiricisisiniz ve işlevleri için kullanılan rengi değiştirmek istediğinizde, örneğin, arayabileceğiniz **C++ işlevlerini** içinde **görüntü öğeleri** listesi.

1. Biz iletişim kutusu dışına çıkmadan önce de XML öznitelikleri rengini değiştirelim. İçinde **görüntü öğeleri** listesinde, aşağı kaydırarak **XML özniteliği** ve bu seçeneği belirleyin. İçinde **öğe ön plan** kutusunda **Küf**. Seçin **Tamam** bizim seçimlerini kaydetmek ve iletişim kutusunu kapatın.

   Satır numaraları artık Zeytin bir renk ve XML öznitelikleri, parlak Küf Yeşili. Bir C++ ya da C# kod dosyası gibi başka bir dosya türünü açarsanız, satır numaralarını Zeytin renkte göründüğünü göreceksiniz.

   ![Yeni yazı tipi renkleri olan XML dosyası](media/quickstart-personalize-xml-file-new-colors.png)

Biz, Visual Studio'daki renkler özelleştirme yalnızca birkaç yolu incelediniz. Diğer özelleştirme seçeneklerinin hakkında bilgi edineceksiniz umuyoruz **seçenekleri** iletişim kutusu, gerçek anlamda Visual Studio kendi yapma.

## <a name="see-also"></a>Ayrıca bkz.

- [Düzenleyiciyi özelleştirme](../ide/customizing-the-editor.md)
- [Visual Studio IDE’ye Genel Bakış](../get-started/visual-studio-ide.md)