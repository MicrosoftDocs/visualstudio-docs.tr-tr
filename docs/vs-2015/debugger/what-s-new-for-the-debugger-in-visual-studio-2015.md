---
title: Hata Ayıklayıcı'Visual Studio 2015'teki yenilikler | Microsoft Docs
titleSuffix: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debugger, what's new
- what's new [debugger]
- debugging [Visual Studio], what's new
- what's new [Visual Studio], debugging
ms.assetid: 2aed9caa-2384-4e49-8595-82d8b06cf271
caps.latest.revision: 86
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 261b3f42cb5c1040567ef16c62d3c44c5d60e0b3
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53065390"
---
# <a name="whats-new-for-the-debugger-in-visual-studio-2015"></a>Visual Studio 2015 Hata Ayıklayıcısı’ndaki Yenilikler
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio 2015 güncelleştirme 1'hata ayıklama ve tanılama konusunda yeni olan her şey hakkında bilgi için [Visual Studio 2015 güncelleştirme 1 sürüm notları](https://www.visualstudio.com/news/vs2015-update1-vs#debug).

 Visual Studio 2015 RTM hata ayıklama ve tanılama konusunda yeni olan her şey hakkında bilgi için [Visual Studio 2015 sürüm notları](https://www.visualstudio.com/news/vs2015-vs#debug).

## <a name="visual-studio-2015-update-1-changes"></a>Visual Studio 2015 güncelleştirme 1 değişiklikleri
 C++ Düzenle ve devam et, daha fazla özellik destekler. Daha fazla bilgi için [Düzenle ve devam et (Visual C++)](../debugger/edit-and-continue-visual-cpp.md).

 Visual C++ erişim ihlali hata ayıklama için yeni bir özel durum iletişim kutusu, özel duruma neden işaretçi belirtir. Daha fazla bilgi için lütfen bkz [nasıl hata ayıklamayı erişim ihlali?](../debugger/how-can-i-debug-an-access-violation-q.md) ve [geliştirme için Visual Studio 2015 güncelleştirme 1'de C++ erişim ihlali hata ayıklama](http://blogs.msdn.com/b/visualstudioalm/archive/2015/10/29/improvement-to-debugging-c-access-violations-in-visual-studio-2015-update-1.aspx)

## <a name="visual-studio-2015-rtm-debugger-ui-and-hotkey-changes"></a>Visual Studio 2015 RTM hata ayıklayıcı kullanıcı Arabirimi ve kısayol tuşu değişiklikleri
 Özel durumlar ve kesme noktaları UI önemli kullanıcı Arabirimi değişiklikleri vardır.

### <a name="breakpoints"></a>Kesme noktaları
 Visual Studio 2015'te olan kesme noktaları, yapılandırmak için yeni bir yolu yoktur **kesme noktası ayarları** penceresi.

 Kısayol tuşlarını ve ana kesme noktaları windows bir özeti aşağıda verilmiştir:

|Özellik|Menü konumu|Kısayol tuşu|
|-------------|-------------------|------------|
|Yeni kesme noktası, iki durumlu kesme noktası|**Hata ayıklama / kesme noktasını Değiştir**<br /><br /> Düzenleyici bağlam menüsünde / **kesme noktası Ekle**<br /><br /> Sol kenar boşluğunda tıklayın|F9|
|Yeni işlev kesme noktası|**Hata ayıklama / yeni kesme noktası / işlev kesme noktası**|Visual Studio 2015 RTM'de (ile hiçbir güncelleştirme), ALT + F9'a, B kullanın<br /><br /> Visual Studio 2015 güncelleştirme 1 ve sonraki sürümlerinde, CTRL + B kullanın|
|**Kesme noktaları** penceresi|**Hata ayıklama / Windows / kesme noktaları**|CTRL + ALT + B|
|**Kesme noktası ayarları**, **koşulları**|kesme noktası bağlam menüsünde / **koşulları**|ALT + F9, C|
|**Kesme noktası ayarları**, **eylemleri**|kesme noktası bağlam menüsünde / **eylemleri**|Hiçbir kısayol tuşu|

 Daha fazla bilgi için aşağıdaki makalelere bakın:

1.  [Kesme Noktalarını Kullanma](../debugger/using-breakpoints.md)

2.  [Yeni kesme noktası yapılandırması deneyimi](http://blogs.msdn.com/b/visualstudioalm/archive/2014/10/06/new-breakpoint-configuration-experience.aspx)

3.  [Kesme noktası yapılandırması deneyimi](http://channel9.msdn.com/Events/Visual-Studio/Connect-event-2014/711)

### <a name="exception-settings"></a>Özel durum ayarları
 Yeni **özel durum ayarları** penceresi, özel durum işleme için tek özel durum istediğiniz türde ya da kategorilerdeki özel durumları belirtmenize olanak sağlar.

|Özellik|Menü konumu|Kısayol tuşu|
|-------------|-------------------|------------|
|**Özel durum ayarları** penceresi|**Hata ayıklama / Windows / özel durum ayarları**|CTRL + ALT + E|

 Daha fazla bilgi için aşağıdaki makalelere bakın:

1.  [Özel Durumları Hata Ayıklayıcısı ile Yönetme](../debugger/managing-exceptions-with-the-debugger.md)

2.  [Yeni özel durumlar penceresi](http://blogs.msdn.com/b/visualstudioalm/archive/2015/02/23/the-new-exception-settings-window-in-visual-studio-2015.aspx)

### <a name="edit-and-continue"></a>Düzenle ve Devam Et
 Visual Studio 2015'te, Düzenle ve devam et içinde ayarlayabilirsiniz **Araçlar / Seçenekler / hata ayıklama / genel** sayfası. Önceki sürümlerde, bu ayarları ayrı seçenekler kategorisinde yoktu.

### <a name="attach-to-process"></a>İşleme
 Visual Studio 2015 İşleme İliştir yalnızca hata ayıklama menüsünden komut kullanılabilir. Önceki sürümde kullanılabilir Araçlar menüsünden de eklenmiştir. CTRL + ALT + P kısayol tuşu, tüm sürümlerde çalışır.

## <a name="see-also"></a>Ayrıca Bkz.
 [Visual Studio’da hata ayıklama](../debugger/debugging-in-visual-studio.md)
