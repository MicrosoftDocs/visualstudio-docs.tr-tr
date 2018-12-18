---
title: Hata ayıklayıcıda çağrı yığınını görüntüleme | Microsoft Docs
ms.custom: seodec18
ms.date: 10/29/2018
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.callstack
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
- SQL
- aspx
helpviewer_keywords:
- threading [Visual Studio], displaying calls to or from
- functions [debugger], viewing code on call stack
- disassembly code
- breakpoints, Call Stack window
- debugging [Visual Studio], switching to another stack frame
- debugging [Visual Studio], Call Stack window
- Call Stack window, viewing source code for functions on the call stack
- stack, switching stack frames
- Call Stack window, viewing disassembly code for functions on the call stack
ms.assetid: 5154a2a1-4729-4dbb-b675-db611a72a731
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: fe3b266ee44b326749ed555df77dee66b8e82aae
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53062357"
---
# <a name="view-the-call-stack-and-use-the-call-stack-window-in-the-debugger"></a>Çağrı yığınını görüntüleme ve hata ayıklayıcı çağrı yığını penceresini kullanma

Kullanarak **çağrı yığını** penceresinde yığında olan işlev veya yordam çağrılarını görüntüleyebilirsiniz. **Çağrı yığını** penceresi, yöntemleri ve işlevleri çağrılır sırasını gösterir. Çağrı yığınını inceleyebilir ve bir uygulamanın yürütme akışını anlamanıza için iyi bir yoludur.

Zaman [hata ayıklama simgeleri](#bkmk_symbols) bir çağrı yığının bir bölümü için kullanılabilir değil **çağrı yığını** penceresi yükleyemeyebilir yerine görüntüleme çağrı yığını o kısmı için doğru bilgileri görüntülemek:

`[Frames below may be incorrect and/or missing, no symbols loaded for name.dll]`

> [!NOTE]
> **Çağrı yığını** penceresi benzer hata ayıklama perspektifi için Eclipse gibi bazı IDE içinde.

> [!NOTE]
> İletişim kutuları ve menü komutları gördüğünüz, etkin ayarlarınıza ve sürüm bağlı olarak burada açıklananlar farklılık gösterebilir. Ayarlarınızı değiştirmek için seçin **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü.  Bkz: [ayarlarına](../ide/environment-settings.md#reset-settings).

## <a name="view-the-call-stack-while-in-the-debugger"></a>Hata ayıklayıcı sırasında çağrı yığınını görüntüleme

- Hata ayıklarken, buna **hata ayıklama** menüsünde **Windows > çağrı yığını**.

  ![Çağrı yığını penceresi](../debugger/media/dbg_basics_callstack_window.png "CallStackWindow")

Sarı bir ok, yürütme işaretçisinin şu anda bulunduğu yığın çerçevesini tanımlar. Varsayılan olarak, kaynak, bu yığın çerçeve bilgi görünür **Yereller**, **Otolar**, **Watch**, ve **ayrıştırılmış kodu** windows. Yığındaki çerçeveye hata ayıklayıcı bağlamı değiştirmek için [başka bir yığın çerçevesine geçiş](#bkmk_switch).

## <a name="display-non-user-code-in-the-call-stack-window"></a>Kullanıcı olmayan kod çağrı yığını penceresinde görüntüleme

-   Sağ **çağrı yığını** penceresi ve select **harici kodu Göster**.

Kullanıcı olmayan kod olduğu zaman gösterilmez herhangi bir kod [yalnızca kendi kodum](../debugger/just-my-code.md) etkinleştirilir. Yönetilen kodda kullanıcı olmayan kod çerçevelerini varsayılan olarak gizlidir. Aşağıdaki gösterim, kullanıcı olmayan kod çerçevelerini yerine görüntülenir:

`[<External Code>]`

## <a name="bkmk_switch"></a> (Hata ayıklayıcı bağlamını değiştirme) başka bir yığın çerçevesine geçiş

1.  İçinde **çağrı yığını** penceresinde, yığın çerçeve kodunu ve görüntülemek istediğiniz veri sağ tıklatın.

    Veya çerçevede çift tıkladığınızda **çağrı yığını** penceresinde bu çerçeveye geçiş yap.

2.  Seçin **çerçeveye geçiş yap**.

     Kıvrık kuyruklu yeşil bir ok, seçtiğiniz yığın çerçevenin yanında görünür. Yürütme işaretçisi halen sarı ok ile işaretlenmiş olan özgün çerçevede kalır. Seçerseniz **adım** veya **devam** gelen **hata ayıklama** menüsünde, yürütme devam eder özgün çerçevede, seçtiğiniz çerçevenin.

## <a name="view-the-source-code-for-a-function-on-the-call-stack"></a>Çağrı yığınındaki bir işlevi için kaynak kodu görüntüleme

-   İçinde **çağrı yığını** penceresinde, istediğiniz kaynak kodunu işlevi görmek ve seçmek için sağ tıklama **kaynak koda Git**.

## <a name="run-to-a-specific-function-from-the-call-stack-window"></a>Çağrı yığını penceresinden belirli bir işleve çalıştırın

-  İçinde **çağrı yığını** penceresinde işlevi seçin, sağ tıklayın ve ardından **imlece kadar Çalıştır**.

## <a name="set-a-breakpoint-on-the-exit-point-of-a-function-call"></a>Bir işlev çağrısının çıkış noktası üzerinde bir kesme noktası ayarlayın

-   Bkz: [bir çağrı yığını işlevi bir kesme noktası ayarlamak](../debugger/using-breakpoints.md#BKMK_Set_a_breakpoint_in_the_call_stack_window).

## <a name="display-calls-to-or-from-another-thread"></a>İçin veya başka bir iş parçacığından çağrıları görüntüleme

-   Sağ **çağrı yığını** penceresi ve select **dahil çağrıları öğesine/öğesinden diğer iş parçacıkları**.

## <a name="visually-trace-the-call-stack"></a>Çağrı yığınını görsel olarak izleme

Visual Studio Enterprise'da (yalnızca), hata ayıklama sırasında çağrı yığınını için kod haritaları görüntüleyebilir.

- İçinde **çağrı yığını** penceresinde, kısayol menüsünü açın. Seçin **kod haritasında çağrı yığınını Göster** (**Ctrl** + **Shift** + **`**).

    Daha fazla bilgi için [hata ayıklarken çağrı yığınında yöntemler harita](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md).

![Kod haritasında çağrı yığınını Göster](../debugger/media/dbg_basics_show_call_stack_on_code_map.gif "ShowCallStackOnCodeMap")

## <a name="view-the-disassembly-code-for-a-function-on-the-call-stack-c-c-visual-basic-f"></a>Çağrı yığınındaki bir işleve ilişkin ayrıştırma kodunu görüntülemek (C#, C++, Visual Basic F#)

-   İçinde **çağrı yığını** penceresinde, sökme kodunu istediğiniz işlevi görebilir ve sağ **Ayrıştırılımış**.

## <a name="change-the-optional-information-displayed"></a>Görüntülenen isteğe bağlı bilgileri değiştirmek

-   Sağ **çağrı yığını** penceresi ve kümesi ya da temizleyin **Göster \<**  _istediğiniz bilgilerin_ **>**.

## <a name="bkmk_symbols"></a> Bir modüle ilişkin simgeleri yüklemek (C#, C++, Visual Basic F#)

İçinde **çağrı yığını** penceresi, hata ayıklama simgelerinin şu anda yüklü olmayan kod için semboller yükleyebilirsiniz. Bu simgeler, .NET Framework veya Microsoft ortak simge sunucularından yüklenen sistem simgeleri veya hata ayıklaması yaptığınız bilgisayarda simge yolunu sembolleri olabilir.

Bkz: [belirtin, sembol (.pdb) ve kaynak dosyaları](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).

### <a name="to-load-symbols"></a>Simgeleri yüklemek için

1.  İçinde **çağrı yığını** penceresinde, simgelerin yığın çerçevesi yüklenmedi sağ tıklatın. Çerçeve soluk görünecektir.

2.  İşaret **sembolleri Yükle** seçip **Microsoft sembol sunucuları** (varsa), ya da sembol yoluna göz atın.

### <a name="to-set-the-symbol-path"></a>Sembol yolunu ayarlamak için

1.  İçinde **çağrı yığını** penceresinde seçin **sembol ayarları** kısayol menüsünden.

     **Seçenekleri** iletişim kutusu açılır ve **sembolleri** sayfası görüntülenir.

2.  Seçin **sembol ayarları**.

3.  İçinde **seçenekleri** iletişim kutusunda, klasör simgesine tıklayın.

     İçinde **sembol dosyası (.pdb) konumlar** kutusunda, bir imleç görüntülenir.

4.  Bir dizin yol adı, hata ayıklaması yaptığınız bilgisayarda simge konumuna girin. Yerel ve uzak hata ayıklama için yerel bilgisayarınızda bir yolu budur.

5.  Seçin **Tamam** kapatmak için **seçenekleri** iletişim kutusu.

## <a name="see-also"></a>Ayrıca bkz.

- [Çağrı Yığını penceresinde karışık kod ve eksik bilgiler](../debugger/mixed-code-and-missing-information-in-the-call-stack-window.md)
- [Hata ayıklayıcıda verileri görüntüleme](../debugger/viewing-data-in-the-debugger.md)
- [Sembol (.pdb) ve kaynak dosyaları belirtme](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)
- [Kesme noktaları kullanma](../debugger/using-breakpoints.md)