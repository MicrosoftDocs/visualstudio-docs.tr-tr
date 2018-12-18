---
title: 'Nasıl yapılır: çağrı yığını penceresini kullanma | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.debug.callstack
dev_langs:
- FSharp
- VB
- CSharp
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
caps.latest.revision: 45
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c45f0a645945e68b7b3d21eefe2f981b9b4b352f
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51751019"
---
# <a name="how-to-use-the-call-stack-window"></a>Nasıl Yapılır: Çağrı Yığını Penceresini Kullanma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Kullanarak **çağrı yığını** penceresinde yığında olan işlev veya yordam çağrılarını görüntüleyebilirsiniz.  
  
 **Çağrı yığını** penceresi, her işlevin adını ve yazılmış olduğu programlama dilini görüntüler. İşlev veya yordam adına modül adı, satır numarası ve parametre adları, türleri ve değerleri gibi isteğe bağlı bilgiler eşlik edebilir. Bu isteğe bağlı bilgilerin görüntülenmesini açılıp kapatılabilir.  
  
 Sarı bir ok, yürütme işaretçisinin şu anda bulunduğu yığın çerçevesini tanımlar. Varsayılan olarak, bu bilgilerini kaynakta görünen çerçevesidir **ayrıştırılmış kodu**, **Yereller**, **Watch**, ve **Otolar** windows. Yığındaki çerçeveye bağlamı değiştirmek istiyorsanız, bunu yapabilirsiniz **çağrı yığını** penceresi.  
  
 Hata ayıklama simgeleri bir çağrı yığının bir bölümü için mevcut olmadığı durumlarda **çağrı yığını** penceresi çağrı yığının o kısmı için doğru bilgileri görüntüleme olanağınız olabilir. Aşağıdaki gösterim görüntülenir:  
  
 [Aşağıdaki çerçeveler hatalı ve/veya eksik name.dll için Sembol yüklenmedi]  
  
 Yönetilen kodda varsayılan olarak. **çağrı yığını** penceresi bilgileri kullanıcı dışındaki kodu gizler. Aşağıdaki gösterim gizli bilgilerin yerine görüntülenir:  
  
 **[\<Dış kod >]**  
  
 "Benim kodumu kısayol menüsünü kullanarak kullanıcı dışı kod için çağrı yığını bilgilerini görüntülemeyi seçebilirsiniz. değil herhangi bir kod kullanıcı dışındaki kodu.  
  
 Kısayol menüsünü kullanarak iş parçacıkları arasındaki çağrıları görmek isteyip istemediğinizi seçebilirsiniz.  
  
> [!NOTE]
>  İletişim kutuları ve menü komutları gördüğünüz açıklanana Yardım'da, etkin ayarlarınıza ve sürüm bağlı olarak farklı olabilir. Ayarlarınızı değiştirmek için seçin **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü. Daha fazla bilgi için [Visual Studio'da geliştirme ayarlarını özelleştirme](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-display-the-call-stack-window-in-break-mode-or-in-run-mode"></a>Çağrı yığını penceresini kesme modunda veya çalıştırma modunda görüntülemek için  
  
-   Üzerinde **hata ayıklama** menüsünde **Windows** ve ardından **çağrı yığını**.  
  
### <a name="to-change-the-optional-information-displayed"></a>Görüntülenen isteğe bağlı bilgileri değiştirmek için  
  
-   Sağ **çağrı yığını** penceresi ve kümesi ya da temizleyin **Göster \<**  _istediğiniz bilgilerin_ **>**.  
  
### <a name="to-display-non-user-code-frames-in-the-call-stack-window"></a>Kullanıcı olmayan kod çerçevelerini çağrı yığını penceresinde görüntülemek için  
  
-   Sağ **çağrı yığını** penceresi ve select **harici kodu Göster**.  
  
### <a name="to-switch-to-another-stack-frame"></a>Başka bir yığın çerçevesine geçiş yapmak için  
  
1.  İçinde **çağrı yığını** penceresinde Çerçeveyi sağ kodunu ve görüntülemek istediğiniz veri.  
  
2.  Seçin **çerçeveye geçiş yap**.  
  
     Kıvrık kuyruklu yeşil bir ok, seçtiğiniz çerçevenin yanında görünür. Yürütme işaretçisi halen sarı ok ile işaretlenmiş olan özgün çerçevede kalır. Seçerseniz **adım** veya **devam** gelen **hata ayıklama** menüsünde, yürütme devam eder özgün çerçevede, seçtiğiniz çerçevenin.  
  
### <a name="to-display-calls-to-or-from-another-thread"></a>İçin veya başka bir iş parçacığından çağrıları görüntülemek için  
  
-   Sağ **çağrı yığını** penceresi ve select **dahil çağrıları öğesine/öğesinden diğer iş parçacıkları**.  
  
### <a name="to-view-the-source-code-for-a-function-on-the-call-stack"></a>Çağrı yığınındaki bir işleve kaynak kodunu görüntülemek için  
  
-   İçinde **çağrı yığını** penceresinde, istediğiniz kaynak kodunu işlevi görmek ve seçmek için sağ tıklama **kaynak koda Git**.  
  
### <a name="to-visually-trace-the-call-stack"></a>Çağrı yığınını görsel olarak izlemek için  
  
1.  İçinde **çağrı yığını** penceresinde, kısayol menüsünü açın. Seçin **kod haritasında çağrı yığınını Göster**. (Klavye: **CTRL** + **SHIFT** + **`**)  
  
     Bkz: [hata ayıklarken çağrı yığınında yöntemler harita](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md).  
  
### <a name="to-view-the-disassembly-code-for-a-function-on-the-call-stack"></a>Çağrı yığınındaki bir işleve ilişkin ayrıştırma kodunu görüntülemek için  
  
-   İçinde **çağrı yığını** penceresinde, sökme kodunu istediğiniz işlevi görebilir ve sağ **Ayrıştırılımış**.  
  
### <a name="to-run-to-a-specific-function-from-the-call-stack-window"></a>Çağrı yığını penceresinden belirli bir işlevi çalıştırmak için  
  
-  İçinde **çağrı yığını** penceresinde işlevi seçin, sağ tıklatın ve seçin **imlece kadar Çalıştır**.  
  
### <a name="to-set-a-breakpoint-on-the-exit-point-of-a-function-call"></a>Bir işlev çağrısının çıkış noktası üzerinde bir kesme noktası ayarlamak için  
  
-   Bkz: [bir çağrı yığını işlevi bir kesme noktası ayarlamak](../debugger/using-breakpoints.md#BKMK_Set_a_breakpoint_in_the_call_stack_window).  
  
### <a name="to-load-symbols-for-a-module"></a>Bir modüle ilişkin simgeleri yüklemek için  
  
-   İçinde **çağrı yığını** penceresinde, simgelerinin modülü gösteren Çerçeveyi sağ tıklatın, yeniden yükleyin ve istediğiniz **sembolleri Yükle**.  
  
## <a name="loading-symbols"></a>Semboller yükleniyor  
 İçinde **çağrı yığını** penceresi, hata ayıklama simgelerinin şu anda yüklü olmayan kod için semboller yükleyebilirsiniz. Bu simgeler, .NET Framework veya Microsoft ortak simge sunucularından yüklenen sistem simgeleri veya hata ayıklaması yaptığınız bilgisayarda simge yolunu sembolleri olabilir.  
  
 Bkz: [sembol (.pdb) belirtin ve kaynak dosyaları](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)  
  
#### <a name="to-load-symbols"></a>Simgeleri yüklemek için  
  
1.  İçinde **çağrı yığını** penceresinde, simgelerin çerçevesi yüklenmedi sağ tıklatın. Çerçeve soluk görünecektir.  
  
2.  İşaret **sembolleri şuradan Yükle** ve ardından **Microsoft sembol sunucuları** veya **sembol yolu**.  
  
#### <a name="to-set-the-symbol-path"></a>Sembol yolunu ayarlamak için  
  
1.  İçinde **çağrı yığını** penceresinde seçin **sembol ayarları** kısayol menüsünden.  
  
     **Seçenekleri** iletişim kutusu açılır ve **sembolleri** sayfası görüntülenir.  
  
2.  Tıklayın **sembol ayarları**.  
  
3.  İçinde **seçenekleri** iletişim kutusunda, klasör simgesine tıklayın.  
  
     İçinde **sembol dosyası (.pdb) konumlar** kutusunda, bir imleç görüntülenir.  
  
4.  Hata ayıklaması yaptığınız bilgisayarda simge konumuna bir dizin yol adı yazın. Yerel hata ayıklama için yerel bilgisayarınıza budur. Uzaktan hata ayıklama için Uzak bilgisayardır.  
  
5.  Tıklayın **Tamam** kapatmak için **seçenekleri** iletişim kutusu.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Karışık kod ve eksik bilgiler çağrı yığını penceresi](../debugger/mixed-code-and-missing-information-in-the-call-stack-window.md)   
 [Nasıl yapılır: hata ayıklayıcı Windows sayısal biçimini değiştirme](http://msdn.microsoft.com/library/cd593847-a625-411d-a430-b798346ef18f)   
 [Hata ayıklayıcıda verileri görüntüleme](../debugger/viewing-data-in-the-debugger.md)   
 [Sembol (.pdb) belirtin ve kaynak dosyaları](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)   
 [Kesme Noktalarını Kullanma](../debugger/using-breakpoints.md)





