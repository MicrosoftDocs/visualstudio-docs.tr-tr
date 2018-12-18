---
title: Hata ayıklayıcıda ayrıştırılmış kodu görüntüleme | Microsoft Docs
ms.custom: seodec18
ms.date: 10/30/2018
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.disassembly
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- assembly language, debugging inline assembly code
- breakpoints, Disassembly window
- Disassembly window
- machine code
ms.assetid: eaf84dd0-c82d-481b-af51-690b74e7794c
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c35432bdd01b9b79c2afaa266d8078caf04bd62b
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53063842"
---
# <a name="view-disassembly-code-in-the-visual-studio-debugger-c-c-visual-basic-f"></a>Visual Studio hata ayıklayıcıda ayrıştırılmış kodu görüntüle (C#, C++, Visual Basic F#)

**Ayrıştırılmış kodu** penceresi için derleyici tarafından oluşturulan talimatlara karşılık gelen derleme kodlarını gösterir. Yönetilen kodda hata ayıklama, bu derleme yönergeleri, Visual Studio derleyici tarafından oluşturulan değil Microsoft Ara dilini (MSIL) Just-ın-Time (JIT) derleyici tarafından oluşturulan yerel koda karşılık gelir.

> [!NOTE]
> Tüm avantajlarından yararlanabilmek için **ayrıştırılmış kodu** penceresinde anlamak veya temel bilgileri öğrenmek [derleme dili programlama](https://wikipedia.org/wiki/Assembly_language).

Bu özellik yalnızca adres seviyesinde hata ayıklamayı etkin olduğunda kullanılabilir. Betik veya SQL hata ayıklama için kullanılabilir değildir.

Derleme yönergeleri yanı sıra **ayrıştırılmış kodu** penceresi, aşağıdaki isteğe bağlı bilgileri gösterebilir:

- Her yönerge bulunduğu bellek adresi. Yerel uygulamalar için bu gerçek bellek adresidir. Visual Basic veya C#, işlev başından uzaklık olduğu.

- Bütünleştirilmiş kodu türetildiği kaynak kodu.

- Bayt olarak diğer bir deyişle, bayt temsillerini MSIL yönergeleri ve gerçek makine kodu.

- Sembol adları için bellek adresleri.

- Kaynak koduna karşılık gelen satır numaraları.

Derleme dili talimatlarını oluşur *anımsatıcıları*, yönerge adları kısaltmaları olduğu ve *sembolleri* değişkenleri, kayıtlar ve sabitleri için. Her makine dil yönergesi, isteğe bağlı olarak bir veya daha fazla sembolleri tarafından izlenen bir çevirici dili anımsatıcı tarafından temsil edilir.

Bütünleştirilmiş kodu, yoğun işlemci kasalarda kullanır veya ortak dil çalışma zamanı yönetilen kod için kaydeder. Kullanabileceğiniz **ayrıştırılmış kodu** penceresi ile birlikte **kaydeder** kayıt içeriğini incelemek sağlayan bir pencere.

Assembly dili olarak değil, kendi işlenmemiş bir sayısal biçimde makine kodu yönergeleri görüntülemek için kullanın **bellek** penceresi ya da seçin **kodu bayt** kısayol menüsünden **ayrıştırılmış kodu**  penceresi.

## <a name="use-the-disassembly-window"></a>Ayrıştırılmış kod penceresini kullanma

Etkinleştirmek için **ayrıştırılmış kodu** penceresinin altında **Araçları** > **seçenekleri** (veya **Araçları**  >  **Seçenekleri**) > **hata ayıklama**seçin **adres seviyesinde hata ayıklamayı**.

Açmak için **ayrıştırılmış kodu** , hata ayıklama sırasında Seç penceresi **Windows** > **ayrıştırılmış kodu** veya basın **Alt** + **8**.

> [!NOTE]
> Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir. Ayarlarınızı değiştirmek için seçin **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü. Daha fazla bilgi için [ayarlarına](../ide/environment-settings.md#reset-settings).

İsteğe bağlı bilgiler açıp kapatmak için sağ **ayrıştırılmış kodu** penceresinde ayarlayın ve kısayol menüsünde istenen seçenekleri temizleyin.

Sol kenar boşluğundaki bir sarı ok geçerli yürütme noktasını işaretler. Yerel kod için CPU'nun program sayacı yürütme noktasını karşılık gelir. Bu konum, programınızda yürütülecek sonraki yönergeyi gösterir.

## <a name="see-also"></a>Ayrıca bkz.

* [Yukarı veya aşağı bellek disk belleği](../debugger/how-to-page-up-or-down-in-memory.md)
* [Hata ayıklayıcıda verileri görüntüleme](../debugger/viewing-data-in-the-debugger.md)
* [Nasıl yapılır: yazmaçlar penceresini kullanma](../debugger/how-to-use-the-registers-window.md)