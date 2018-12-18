---
title: 'Nasıl yapılır: iyileştirilmiş kodda hata ayıklama | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- breakpoints, in optimized code
- debugging [C++], optimized code
- optimization, debug builds
- debug builds, optimizing
- optimized code, debugging
ms.assetid: fc8eeeb8-6629-4c9b-99f7-2016aee81dff
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c6e212129c17ec7b4fe6cb9a6808c91cb302deb3
ms.sourcegitcommit: dd839de3aa24ed7cd69f676293648c6c59c6560a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/27/2018
ms.locfileid: "52387869"
---
# <a name="how-to-debug-optimized-code"></a>Nasıl Yapılır: İyileştirilmiş Kodda Hata Ayıklama

> [!NOTE]
> Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir. Ayarlarınızı değiştirmek için Araçlar menüsünden içeri ve dışarı aktarma ayarları seçin. Daha fazla bilgi için [ayarlarına](../ide/environment-settings.md#reset-settings).

> [!NOTE]
> [/Zo (geliştirmek için iyileştirilmiş hata ayıklama)](/cpp/build/reference/zo-enhance-optimized-debugging)derleyici seçeneği (Visual Studio güncelleştirme 3'te sunulmuştur) en iyi duruma getirilmiş kodu için daha zengin hata ayıklama bilgileri oluşturur (ile oluşturulmamış projeleri **/Od** derleyici seçeneği. Bkz: [/O seçenekler (kodu İyileştir)](/cpp/build/reference/o-options-optimize-code)). Bu yerel değişkenleri ve satır içine alınmış işlevlerin hata ayıklama için gelişmiş destek içerir.
>
> [Düzenle ve devam et](../debugger/edit-and-continue-visual-csharp.md) ne zaman devre dışı **/Zo** ocompiler seçeneği kullanılır.

 Kod derleyici en iyi duruma getirir, yeniden konumlandırır ve yönergeleri yeniden düzenler. Bu, daha verimli derlenmiş kodda sonuçlanır. Bu yeniden nedeniyle hata ayıklayıcı her zaman yönergeleri için karşılık gelen kaynak kodunu tanımlanamıyor.

 En iyi duruma getirme etkileyebilir:

- İyileştirici tarafından kaldırılmış veya hata ayıklayıcı anlamadığı konumlara taşınmış yerel değişkenler.

- İyileştirici kod bloklarını birleştirir, değiştirilen konumları bir işlev içinde.

- İyileştirici iki işlev birleştirir, yanlış olabilir çağrı yığınında çerçeve için işlev adlarını.

  Çağrı yığınındaki gördüğünüz çerçeveleri neredeyse her zaman Bununla birlikte, semboller için tüm çerçeveleri olduğunu varsayarsak doğrudur. Çağrı yığınında çerçeve derleme dilinde yazılı işlev varsa yığın bozulması varsa veya işletim sistemi çerçeve çağrı yığınında eşleştirme sembolleri olmayan ise yanlış olur.

  Genel ve statik değişkenleri her zaman doğru bir şekilde gösterilir. Bu nedenle yapısı düzendir. Bir yapıya bir işaretçi olması ve işaretçi değerini doğru ise, her üye değişkeni yapısının doğru değeri gösterilir.

  Bu sınırlamalar nedeniyle bu tamamen Mümkünse, programınızın iyileştirilmemiş bir sürümünü kullanarak hata ayıklama. Varsayılan olarak, en iyi duruma getirme Visual C++ programı hata ayıklama yapılandırmasında devre dışı bırakılmış ve yayın yapılandırmasında açık.

  Ancak, bir hatayı yalnızca bir programın en iyi duruma getirilmiş bir sürümünü görünebilir. Bu durumda, siz en iyi duruma getirilmiş kodda hata ayıklama gerekir.

## <a name="to-turn-on-optimization-in-a-debug-build-configuration"></a>Bir hata ayıklama iyileştirme etkinleştirmek için yapılandırma derleme

1. Yeni bir proje oluşturduğunuzda, `Win32 Debug` hedef. Kullanım `Win32``Debug` programınızı tam hata ayıklama ve derlemek için hazır kadar hedef bir `Win32 Release` hedef. Derleyicinin `Win32 Debug` hedef.

2. Çözüm Gezgini'nde projeyi seçin.

3. Üzerinde **görünümü** menüsünü tıklatın **özellik sayfaları**.

4. İçinde **özellik sayfaları** iletişim kutusunda, emin `Debug` seçili **yapılandırma** açılır listede.

5. Klasör Görünümü'nde sol taraftaki seçin **C/C++** klasör.

6. Altında **C++** klasörüne `Optimization`.

7. Sağ taraftaki özellikler listesinde, bulma `Optimization`. Bir ayarın yanındaki, büyük olasılıkla diyor `Disabled (` [/Od](/cpp/build/reference/od-disable-debug)`)`. Diğer seçeneklerden birini seçin (`Minimum Size``(`[/O1](/cpp/build/reference/o1-o2-minimize-size-maximize-speed)`)`, `Maximum Speed``(` [/O2](/cpp/build/reference/o1-o2-minimize-size-maximize-speed)`)`, `Full Optimization``(` [/Ox](/cpp/build/reference/ox-full-optimization) `)`, veya `Custom`).

8. Seçerseniz, `Custom` seçeneğini `Optimization`, artık gösterilen özellikler listesinde bulunan diğer özelliklerden herhangi biri için seçenekleri ayarlayabilirsiniz.

9. Yapılandırma özellikleri, C/C++, proje özellikleri sayfasında, komut satırı düğümünü seçin ve Ekle `(` [/Zo](/cpp/build/reference/zo-enhance-optimized-debugging) `)` için **ek seçenekler** metin kutusu.

    > [!WARNING]
    >  `/Zo` Visual Studio 2013 güncelleştirme 3 veya sonraki bir sürümü gerektirir.
    >
    >  Ekleme `/Zo` devre dışı bırakacak [Düzenle ve devam et](../debugger/edit-and-continue-visual-csharp.md).

   En iyi duruma getirilmiş kod hata ayıklaması yaparken kullanın **ayrıştırılmış kodu** penceresini hangi yönergeleri gerçekten oluşturulduğunu ve yürütüldü. Kesme noktası ayarlarsanız, kesme noktası ile birlikte bir yönerge taşınmasını gerektirecek bilmeniz gerekir. Örneğin, aşağıdaki kodu düşünün:

```cpp
for (x=0; x<10; x++)
```

 Bu satırında bir kesme noktası ayarlamak varsayalım. Kesme noktası 10 kez ulaşılmasına beklediğiniz ancak kodun en iyilenmesi, yalnızca bir kez kesme noktasına erişildiğinde. İlk yönerge değerini ayarlar çünkü `x` 0. Derleyici, bu yalnızca bir kez gerçekleştirilmesi gerekir ve döngü dışında hareket olduğunu algılar. Kesme noktası ile taşır. Karşılaştırın ve Artır yönergeleri `x` döngünün içinde kalır. Görüntülediğinizde **ayrıştırılmış kodu** penceresinde [adım birim](/previous-versions/visualstudio/visual-studio-2010/ek13f001(v=vs.100)) yönerge için en iyi duruma getirilmiş kodda adım adım bağlandığınızda yararlıdır daha fazla denetim için otomatik olarak ayarlanır.

## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklayıcısı Güvenliği](../debugger/debugger-security.md)
- [Yerel Kodda Hata Ayıklama](../debugger/debugging-native-code.md)