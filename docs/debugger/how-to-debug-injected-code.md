---
title: 'Nasıl yapılır: Püskürtülen kodda hata ayıklama | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.injected
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- assembly language, viewing
- debugging [C++], viewing assembly code
- debugging [C++], injected code
- debugging [C++], enabling source annotation
- injected code
- Show Source Code command [debugger]
- debugging [C++], using attributes
- disassembly code, debugging
ms.assetid: a1b4104d-d49e-451f-a91e-e39ceaf35875
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 8efcc5780b27967644330e55dc540333a19105a2
ms.sourcegitcommit: dd839de3aa24ed7cd69f676293648c6c59c6560a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/27/2018
ms.locfileid: "52389344"
---
# <a name="how-to-debug-injected-code"></a>Nasıl Yapılır: Püskürtülen Kodda Hata Ayıklama

> [!NOTE]
> Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir. Ayarlarınızı değiştirmek için Araçlar menüsünden içeri ve dışarı aktarma ayarları seçin. Daha fazla bilgi için [ayarlarına](../ide/environment-settings.md#reset-settings).

Öznitelikleri kullanılarak C++ programlama büyük ölçüde basitleştirebilir. Daha fazla bilgi için [kavramları](/cpp/windows/attributed-programming-concepts). Bazı öznitelikler, derleyiciye tarafından yorumlanır. Diğer öznitelikleri kod derleyici ardından derler program kaynak yerleştirir. Eklenen bu kod, daha kolay yazmanız gereken kod miktarını azaltarak programlama yapar. Bazı durumlarda, ancak bir hata uygulamanızın eklenen kod yürütülürken başarısız olmasına neden olabilir. Bu durumda, eklenen koda göz atmak isteyeceksiniz. Visual Studio eklenen kodu görmek iki yol sağlar:

- Eklenen kodun görüntüleyebileceğiniz **ayrıştırılmış kodu** penceresi.

- Kullanarak [/Fx](/cpp/build/reference/fx-merge-injected-code), özgün ve eklenen kod içeren bir birleştirilmiş kaynak dosyası oluşturabilirsiniz.

**Ayrıştırılmış kodu** penceresi, kaynak kodu ve öznitelikleri tarafından eklenen kod karşılık gelen derleme dili talimatlarını gösterir. Ayrıca, **ayrıştırılmış kodu** penceresi, kaynak kodu ek açıklama gösterebilir.

## <a name="to-turn-on-source-annotation"></a>Kaynak ek açıklama üzerinde etkinleştirmek için

-   Sağ **ayrıştırılmış kodu** penceresinde ve **kaynak kodunu Göster** kısayol menüsünden.

     Bir kaynak penceresinde bir öznitelik konumunu biliyorsanız, eklenen kodun bulmak için kısayol menüsünü kullanabilirsiniz **ayrıştırılmış kodu** penceresi.

## <a name="to-view-injected-code"></a>Eklenen kodu görüntülemek için

1.  Hata ayıklayıcının kesme modunda olması gerekir.

2.  Bir kaynak kod penceresinde, imleci eklenen kodu görüntülemek istediğiniz öznitelik önüne koyun.

3.  Sağ tıklatın ve seçin **Ayrıştırılımış** kısayol menüsünden.

     Öznitelik konumu geçerli yürütme noktasını ise, seçebileceğiniz **ayrıştırılmış kodu** penceresinden **hata ayıklama** menüsü.

## <a name="to-view-the-disassembly-code-at-the-current-execution-point"></a>Geçerli yürütme noktasına ilişkin ayrıştırma kodunu görüntülemek için

1.  Hata ayıklayıcının kesme modunda olması gerekir.

2.  Gelen **hata ayıklama** menüsünde seçin **Windows**, tıklatıp **ayrıştırılmış kodu**.

## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklayıcısı Güvenliği](../debugger/debugger-security.md)
- [Yerel Kodda Hata Ayıklama](../debugger/debugging-native-code.md)