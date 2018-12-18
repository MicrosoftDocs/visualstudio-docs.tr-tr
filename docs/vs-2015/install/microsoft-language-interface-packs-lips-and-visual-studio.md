---
title: Microsoft Dil Arabirim Paketleri (LIP'ler) | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-install
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- text [Visual Studio], multiple languages
- Multilingual User Interface [Visual Studio]
- language switching [Visual Studio]
- MUI [Visual Studio]
- multiple language support [Visual Studio SDK]
- Windows Multilingual User Interface
- UI text language [Visual Studio]
- languages, multiple language support
ms.assetid: dc86304b-65b7-47e6-9314-1dfd02ecfa65
caps.latest.revision: 28
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.openlocfilehash: 647935dce06d74b29271af130686a10fb8cfc1e9
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53065044"
---
# <a name="microsoft-language-interface-packs-lips-and-visual-studio"></a>Microsoft Dil Arabirim Paketleri (LIP'ler) ve Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bir Windows Dil Arabirim Paketi (LIP) kullanarak Windows dil sürümünü yükleyin ve ardından çeşitli kullanıcı arabirimi dil paketlerini yükleyin. Kullanıcı Arabirimi Dil paketleri, işletim sistemi için yerelleştirilmiş kullanıcı arabirimi (UI) sağlayın. Örneğin, Japonca Dil Arabirimi Paketi İngilizce sürümünü Windows üzerine yükleyin ve ardından Windows arabiriminde Japonca ve İngilizce arasında geçiş yapabilirsiniz. LIP'ler kullanarak tek bir bilgisayarda Windows birden çok dil sürümlerini olabilir.

 LIP'ler ve birden çok dil sürümleri Visual Studio'nun yüklü olan bilgisayarlarda Windows değiştirme görüntü dil ayarları ayarlar hem Windows hem de Visual Studio eşleşen dil paketleri yüklendiğinde.

## <a name="limitations-of-multi-language-installations"></a>Çok dilli yüklemeleri sınırlamaları
 Aynı bilgisayarda Visual Studio'nun farklı dil sürümlerini yükleme sırasında yalnızca diller eşleşen sürümler arasında geçiş yapabilirsiniz. Örneğin, İngilizce Express yüklü sürüm varsa, yüklü bir Almanca Express Edition ve Professional sürümü yüklü, diller yalnızca geçiş yapabilirsiniz Professional Edition için değil, Express sürümleri için.

 Visual Studio birleşik dil paketi kullanır. Bu ürünler birden fazla dil sürümünü yüklemek için tam dil ürününü yükleyin ve ardından bir veya daha fazla dil paketlerini yükleyin.

> [!NOTE]
>  Visual Studio tam dil ürün birden çok dil sürümünü aynı bilgisayara yükleme desteklemiyor. Bir tam dil ürünü yükledikten sonra dil paketlerini kullanarak dil sürümleri eklemeniz gerekir. Bu gibi durumlarda, Express sürümleri birden çok ürünlerin tam dil yine de aynı bilgisayara yükleyebilirsiniz.

### <a name="support-for-code-pages"></a>Kod sayfaları için destek
 Bazı Visual Studio Araçları metin geçerli kod sayfasında karakter içerdiğinde metin düzgün görüntülemez. Bunun yerine, soru işareti görünür veya metin bozuk olabilir. Aşağıdaki araçlar veya alanlar etkilenir:

-   FTP kullanarak dağıtılmış siteler.

-   ASCII olmayan bilgisayar adlarında bazı denetimler.

-   Visual Studio dışında çalışan komut satırı araçları.

-   Visual Basic Geçiş Sihirbazı.

-   ActiveX denetimi Test kapsayıcısı.

-   OLE/COM Nesne Görüntüleyici.

-   ISAPI Web hata ayıklama aracı.

-   HTML Yardımı içeriğe sahip MFC uygulaması projeleri.

-   Visual SourceSafe / SCCI UI gördükleri İngilizce'ye zaman uyumsuz kod sayfası.

-   Visual SourceSafe Unicode dosya adlarını desteklemez.

-   Son kullanıcı tarafından tanımlanan karakter (özel kullanım bölge), belirteç/tanımlayıcı olarak kullanılamaz.

-   Bazı Visual Studio araç pencerelerinin Windows kod sayfası, Doğu Asya dilleri için ayarlandığında Latin Genişletilmiş-B karakterleri görüntülenemiyor.

-   Birden çok dili betikleri karakterlerinden oluşan metin çalışır, bazı karakterler için varsayılan karakter görüntüleyebilir.

-   Kopyalama ve karmaşık kod dizeleri ortak denetimlere yapıştırma kaybolacak şekillendirme karakter neden olabilir. Bunun yerine, metin girişi için karşılık gelen dil klavyeyi kullanın.

##### <a name="to-correctly-display-characters-that-are-not-included-in-the-current-code-page"></a>Geçerli kod sayfasında bulunmayan karakterler düzgün görüntülemek için

1.  Tıklayın **Başlat**, tıklayın **Denetim Masası**ve ardından açın **bölge ve Dil Seçenekleri** (veya **bölge** içinde [!INCLUDE[win8](../includes/win8-md.md)]).

    > [!NOTE]
    >  Bu adımları izlemek için bilgisayarda yönetici olması gerekir.

2.  Tıklayın **Gelişmiş** sekmesi.

3.  İçinde **Unicode olmayan program kullanmak istediğiniz dil sürümüyle eşleşen bir dil seçin** listesinde, şu anda dil seçin.

4.  **Tamam**'ı tıklatın.

## <a name="changing-the-language-used-for-the-ui-text-in-visual-studio"></a>Visual Studio UI metinde kullanılan dili değiştirme
 Birden çok dil sürümünü yüklediğinizde [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] aynı bilgisayarda [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] UI varsayılanları **Microsoft Windows ile aynı**. Bu ayar [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] UI metni, işletim sistemi için görüntüleme dili olarak belirttiğiniz dilde görüntülenir.

> [!NOTE]
>  Visual Studio kullanmak üzere ayarlanmışsa **Microsoft Windows ile aynı**ve eşleşen Visual Studio dil paketi yüklü değil, Visual Studio, ilk Visual Studio yüklemesinin kullanacaktır.

#### <a name="to-set-the-language-that-is-used-for-the-ui-text-in-visual-studio"></a>Visual Studio UI metinde kullanılan dili ayarlamak için

1. Üzerinde **Araçları** menüsünü tıklatın **seçenekleri**.

2. İçinde **seçenekleri** iletişim kutusunda **ortam** ve ardından **uluslararası ayarlar**.

3. İçinde **dil** listesinde, geliştirme ortamında UI metni görüntüleneceği dili seçin.

    UI metni IDE içinde ayarlama işletim sistemi görüntüleme dilini eşleşmesi için seçin **Microsoft Windows ile aynı**.

   Devenv komut, kullanıcı Arabiriminde kullanılan dilini ayarlamak amacıyla da kullanabilirsiniz. Daha fazla bilgi için [/LCID (devenv.exe)](../ide/reference/lcid-devenv-exe.md).

## <a name="see-also"></a>Ayrıca Bkz.
 [Uluslararası Ayarlar, Ortam, Seçenekler İletişim Kutusu](../ide/reference/international-settings-environment-options-dialog-box.md)