---
title: Eşitlenmiş Ayarlar
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- VS.ToolsOptionsPages.Environment.RoamingSettings
ms.assetid: a3d2ea29-be5d-4012-9820-44b06adbb7dd
caps.latest.revision: 13
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 1b0ab4b0d006183f6be3c42626c022d45a2de4ce
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53067135"
---
# <a name="synchronized-settings-in-visual-studio"></a>Visual Studio'da Eşitlenmiş Ayarlar
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio için birden çok bilgisayarda oturum açmak için aynı kişiselleştirme hesabı kullandığınızda, varsayılan olarak ayarlarınız tüm bilgisayarlarda eşitlenir.

## <a name="synchronized-settings"></a>Eşitlenmiş ayarlar
 Varsayılan olarak, şu ayarlar eşitlenir.

-   Geliştirme Ayarları (bir ayar kümesi seçmeniz gerekir. ilk kez Visual Studio'yu çalıştırın, ancak zaman seçimi değiştirebilirsiniz. Daha fazla bilgi için [Visual Studio'da geliştirme ayarlarını özelleştirme](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).)

-   Aşağıdaki seçenekleri **Araçları &#124; seçenekleri** sayfalar:

    -   **Tema** ve menü çubuğu üzerinde ayarları, büyük/küçük harfleri **ortam**, **genel** Seçenekleri sayfası

    -   Tüm ayarlar **ortam**, **yazı tipleri ve renkler** Seçenekleri sayfası

    -   Tüm klavye kısayolları **ortam**, **klavye** Seçenekleri sayfası

    -   Tüm ayarlar **ortamı, sekmeler ve Windows** Seçenekleri sayfası

    -   Tüm ayarlar **ortam**, **başlangıç** Seçenekleri sayfası

    -   Tüm ayarlar **metin düzenleyici** seçenekler sayfaları

-   XAML Tasarımcısı'ndaki tüm ayarlar seçenekler sayfaları

-   Kullanıcı tanımlı komut diğer adları. Komut diğer adlarını tanımlama hakkında daha fazla bilgi için bkz. [Visual Studio komut diğer adları](../ide/reference/visual-studio-command-aliases.md).

-   Kullanıcı tanımlı pencere düzenleri **penceresi &#124; pencere düzenlerini Yönet** sayfası

## <a name="turning-synchronized-settings-off-for-a-particular-computer"></a>Belirli bir bilgisayar için açma eşitlenmiş ayarları devre dışı
 Eşitlenmiş ayarlar Visual Studio için varsayılan olarak açık olabilir. Eşitlenmiş ayarlar bir bilgisayara giderek kapatabilirsiniz **Araçları &#124; seçenekleri &#124; ortam &#124; eşitlenmiş ayarlar** sayfası ve onay kutusunun seçilirliği kaldırıldığında.  Örneğin, bir bilgisayarda Visual Studio'nun ayarlarını eşitlemek karar verirseniz, herhangi bir ayarı değişiklik yapılan bilgisayarda Bilgisayar B görünmüyor do veya bilgisayar c bilgisayar B ve C birbiriyle, ancak bilgisayar A'ya eşitlenecek sürdürür

## <a name="synchronizing-settings-across-visual-studio-family-products-and-editions"></a>Visual Studio ailesi ürünler ve sürümleri ayarları eşitleme
 Visual Studio 2015 Express ve topluluk sürümleri dahil olmak üzere, herhangi bir sürümünü ayarları eşitlenebilir. Ayarları ayrıca Blend gibi Visual Studio ailesi ürünler arasında eşitlenir. Ancak, her biri bu ailesi ürünler Visual Studio ile paylaşılmayan kendi ayarlarına sahip olabilir. Bilgisayar b Blend ile ancak bilgisayar A veya b Visual Studio ile değil bilgisayarındaki Blend için özel ayarları gibi paylaşılır

> [!WARNING]
>  Ayarlar, Visual Studio 2015 ve Visual Studio 2013 arasında eşitlenmez. Visual Studio 2015'te, ilk açtığınızda, ayarlarınızı Visual Studio 2013'ten geçirilir, ancak Visual Studio 2013 için geri bundan sonra geçirilemezler.

## <a name="see-also"></a>Ayrıca Bkz.
 [IDE’yi Kişiselleştirme](../ide/personalizing-the-visual-studio-ide.md)
