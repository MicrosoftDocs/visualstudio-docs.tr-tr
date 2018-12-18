---
title: 'Nasıl yapılır: ayarlama IDE erişilebilirlik seçeneklerini'
description: Visual Studio'da tümleşik geliştirme ortamı (IDE) kullanmak herkes için daha kolay hale getirecek erişilebilirlik seçeneklerini ayarlama görme zorluğu olan kişiler ve zorluğu yazılacak olan kişiler de dahil olmak üzere bilgi edinin.
ms.date: 08/22/2017
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- accessibility [Visual Studio]
ms.assetid: ddc96c4c-0600-46c1-8267-7dce4c44ad24
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: df94a57358edd9619b43bbcddb26d4e3485a1ab1
ms.sourcegitcommit: dd839de3aa24ed7cd69f676293648c6c59c6560a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/27/2018
ms.locfileid: "52388432"
---
# <a name="how-to-set-ide-accessibility-options"></a>Nasıl yapılır: ayarlama IDE erişilebilirlik seçeneklerini

> [!TIP]
> Son erişilebilirlik güncelleştirmeleri hakkında daha fazla bilgi için bkz: [erişilebilirlik geliştirmeleri Visual Studio 2017 sürüm 15.3](https://blogs.msdn.microsoft.com/visualstudio/2017/08/14/accessibility-improvements-in-visual-studio-2017-version-15-3/) blog gönderisi.

[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] görme zorluğu olan kişiler ve zorluğu yazılacak olan kişiler için kolaylaştıran özellikler içerir. Bu özellikler, boyut ve dizileri düğmeleri araç çubukları ve yöntem ve parametreler için otomatik tamamlama ve metin boyutunu değiştirme düzenleyiciler, metin rengi değiştirme içerir.

Ayrıca, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] desteklediği en sık olun Dvorak klavye düzenleri, yazılan karakter daha erişilebilir. Kullanılabilir olan varsayılan kısayol tuşlarını da özelleştirebilirsiniz [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Daha fazla bilgi için [tanımlama ve özelleştirme klavye kısayolları](../../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md).

> [!NOTE]
> Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir. Ayarlarınızı değiştirmek için seçin **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü. Daha fazla bilgi için [ayarlarına](../environment-settings.md#reset-settings).

## <a name="editors-dialogs-and-tool-windows"></a>Düzenleyicilerde, iletişim kutuları ve araç pencereleri

 Varsayılan olarak, iletişim kutuları ve araç pencerelerinde tarafından [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] renkleri ve yazı tipi boyutu aynı işletim sistemi olarak kullanın. İletişim kutuları, araç çubukları ve araç pencerelerini IDE, çerçeve için renk ayarlarını dayalı bir renk şeması: açık veya koyu. Geçerli renk teması olarak değiştirebileceğiniz [genel, ortam, Seçenekler iletişim kutusu](../../ide/reference/general-environment-options-dialog-box.md).

 Bu gibi durumlarda, açılır pencereleri de Düzenleyicisi kod görünümünde görüntüleyebilirsiniz. Bu windows bir işlev veya ifade tamamlamak için kullanılabilir üyeler geçerli nesne ve parametreleri isteyebilir. Bu windows zorlanıyorsanız varsa yararlı olabilir. Ancak, bazı kullanıcılar için sorunlu Kod düzenleyicisinde odaklanılan müdahale. Bu windows oturumunu Seçenekleri iletişim kutusu açılıyor ve temizleyerek kapatabilirsiniz **otomatik üyeleri Listele** ve **parametre bilgileri** içinde **metin düzenleyici**, **tüm Diller**, **genel** sayfasını **seçenekleri** iletişim kutusu.

 Windows tümleşik geliştirme ortamı (IDE) çalışma biçiminizi en uygun şekilde düzenleyebilirsiniz. Yerleştirme, float, gizleme veya her araç penceresi otomatik olarak gizle.

 Pencere düzenlerini değiştirme hakkında daha fazla bilgi için bkz. [pencere düzenlerini özelleştirme](../../ide/customizing-window-layouts-in-visual-studio.md).

### <a name="changing-the-size-of-text"></a>Metin boyutunu değiştirme

 Metin tabanlı windows ayarlarını aşağıdaki gibi değiştirebilirsiniz **komut** penceresinde **hemen** penceresinde ve **çıkış** penceresi, **yazı tipleri ve Renkleri** bölmesinde **ortam** seçeneklerini **Araçları** iletişim kutusu. Zaman **[tüm metin aracı Windows]** seçili **ayarlarını göster** aşağı açılan listesinde, varsayılan ayar olarak listelendiğini **varsayılan** içinde **öğe ön planı**  ve **öğesi arka plan** açılan listeler. Ayrıca, Metin Düzenleyici'de nasıl görüntüleneceğini için ayarları değiştirebilirsiniz.

#### <a name="to-change-the-size-of-text-in-text-based-tool-windows-and-editors"></a>Metin tabanlı araç pencereleri ve düzenleyicileri metin boyutunu değiştirmek için

1.  Gelen **Araçları** menüsünde seçin **seçenekleri**.

2.  Seçin **yazı tipleri ve renkler** üzerinde **ortam** klasör.

3.  Üzerinde bir seçenek belirleyin **ayarlarını göster** açılan menüsü.

     Düzenleyicide metni için yazı tipi boyutunu değiştirmek için seçin **metin düzenleyici**.

     Metin tabanlı pencerelerdeki metin yazı tipi boyutunu değiştirmek için seçin **[tüm metin aracı Windows]**.

     Bir düzenleyici araç ipucu metni yazı tipi boyutunu değiştirmek için seçin **Düzenleyici araç ipucu**.

     Deyim tamamlama açılır pencereleri metin yazı tipi boyutunu değiştirmek için seçin **deyim tamamlama**.

4.  Gelen **görüntü öğeleri**seçin **düz metin**.

5.  İçinde **yazı tipi**, yeni bir yazı tipi seçin.

6.  İçinde **boyutu**, yeni bir yazı tipi boyutu seçin.

    > [!NOTE]
    > Metin tabanlı araç pencereleri ve düzenleyiciler için metin boyutu Sıfırla tercih **Varsayılanlar kullan**.

7.  Seçin **Tamam**.

### <a name="change-the-colors-that-are-used-in-the-ide"></a>IDE içinde kullanılan renkleri değiştirebilir

 Metin, kenar boşluğu göstergeleri, boşluk ve düzenleyicide kod öğeleri için varsayılan renkleri değiştirmek seçebilirsiniz.

> [!NOTE]
> Tüm uygulama windows işletim sisteminizdeki yüksek karşıtlık renklerini kullanmak için sol basın <strong>ALT +</strong>sol **SHIFT + PRINT SCREEN**. Varsa [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] açık, kapatın ve yeniden [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] tam yüksek karşıtlık renklerini uygulamak için.

#### <a name="to-change-the-color-of-items-in-the-editor"></a>Düzenleyicide öğelerinin rengini değiştirmek için

1.  Gelen **Araçları** menüsünde seçin **seçenekleri**.

2.  İçinde **ortam** klasörü seçin **yazı tipleri ve renkler**.

3.  İçinde **ayarlarını göster**, seçin **metin düzenleyici**.

4.  Gelen **görüntü öğeleri**, görüntü gibi değiştirmek istediğiniz öğeyi seçin **düz metin**, **gösterge kenar boşluğunu**, **görünür boşluk**, **HTML öznitelik adı**, veya **XML özniteliği**.

5.  Görüntü ayarlarını aşağıdaki seçeneklerden birini seçin: **öğe ön plan**, **öğesi arka plan**, ve **kalın**.

6.  Seçin **Tamam**.

## <a name="toolbars"></a>Araç Çubukları

 Araç çubuklarının kullanılabilirliğini ve erişilebilirliğini geliştirmek için araç çubuğu düğmeleri için metin ekleyebilirsiniz.

### <a name="to-assign-text-to-toolbar-buttons"></a>Araç çubuğu düğmeleri için metin atamak için

1.  Gelen **Araçları** menüsünde seçin **Özelleştir**.

2.  İçinde **Özelleştir** iletişim kutusunda **komutları** sekmesi.

3.  Seçin **araç** metnini görüntülemek için istediğinize düğmesini içeren bir araç çubuğu adı seçin.

4.  Listede, değiştirmek istediğiniz komutu seçin.

5.  Seçin **seçimi değiştirme**.

6.  Seçin **resim ve metin**.

### <a name="to-modify-the-displayed-text-in-a-button"></a>Bir düğme olarak görüntülenen metni değiştirmek için

1.  Yeniden seçin **seçimi değiştirme**.

2.  Bitişik içinde **adı**, Ekle, seçili düğme için yeni bir resim yazısı sağlayın.

## <a name="see-also"></a>Ayrıca bkz.

* [Visual Studio'nun erişilebilirlik özellikleri](../../ide/reference/accessibility-features-of-visual-studio.md)
* [Erişilebilir uygulamalar tasarlama için kaynaklar](../../ide/reference/resources-for-designing-accessible-applications.md)