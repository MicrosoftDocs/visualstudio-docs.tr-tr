---
title: 'Nasıl yapılır: Püskürtülen kodda hata ayıklama | Microsoft Docs'
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
- vs.debug.injected
dev_langs:
- FSharp
- VB
- CSharp
- C++
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
caps.latest.revision: 20
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7ff81b082c877098acec78e56ef9ef211cae8854
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51778156"
---
# <a name="how-to-debug-injected-code"></a>Nasıl Yapılır: Püskürtülen Kodda Hata Ayıklama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[NOT]
>  Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir. Ayarlarınızı değiştirmek için Araçlar menüsünden içeri ve dışarı aktarma ayarları seçin. Daha fazla bilgi için [Visual Studio'da geliştirme ayarlarını özelleştirme](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
 Öznitelikleri kullanılarak C++ programlama büyük ölçüde basitleştirebilir. Daha fazla bilgi için [kavramları](http://msdn.microsoft.com/library/563e7e7c-65e1-44f4-b0b2-da04a6c1bc9e). Bazı öznitelikler, derleyiciye tarafından yorumlanır. Diğer öznitelikleri kod derleyici ardından derler program kaynak yerleştirir. Eklenen bu kod, daha kolay yazmanız gereken kod miktarını azaltarak programlama yapar. Bazı durumlarda, ancak bir hata uygulamanızın eklenen kod yürütülürken başarısız olmasına neden olabilir. Bu durumda, eklenen koda göz atmak isteyeceksiniz. Visual Studio eklenen kodu görmek iki yol sağlar:  
  
- Eklenen kodun görüntüleyebileceğiniz **ayrıştırılmış kodu** penceresi.  
  
- Kullanarak [/Fx](http://msdn.microsoft.com/library/14f0e301-3bab-45a3-bbdf-e7ce66f20560), özgün ve eklenen kod içeren bir birleştirilmiş kaynak dosyası oluşturabilirsiniz.  
  
  **Ayrıştırılmış kodu** penceresi, kaynak kodu ve öznitelikleri tarafından eklenen kod karşılık gelen derleme dili talimatlarını gösterir. Ayrıca, **ayrıştırılmış kodu** penceresi, kaynak kodu ek açıklama gösterebilir.  
  
### <a name="to-turn-on-source-annotation"></a>Kaynak ek açıklama üzerinde etkinleştirmek için  
  
-   Sağ **ayrıştırılmış kodu** penceresinde ve **kaynak kodunu Göster** kısayol menüsünden.  
  
     Bir kaynak penceresinde bir öznitelik konumunu biliyorsanız, eklenen kodun bulmak için kısayol menüsünü kullanabilirsiniz **ayrıştırılmış kodu** penceresi.  
  
### <a name="to-view-injected-code"></a>Eklenen kodu görüntülemek için  
  
1.  Hata ayıklayıcının kesme modunda olması gerekir.  
  
2.  Bir kaynak kod penceresinde, imleci eklenen kodu görüntülemek istediğiniz öznitelik önüne koyun.  
  
3.  Sağ tıklatın ve seçin **Ayrıştırılımış** kısayol menüsünden.  
  
     Öznitelik konumu geçerli yürütme noktasını ise, seçebileceğiniz **ayrıştırılmış kodu** penceresinden **hata ayıklama** menüsü.  
  
### <a name="to-view-the-disassembly-code-at-the-current-execution-point"></a>Geçerli yürütme noktasına ilişkin ayrıştırma kodunu görüntülemek için  
  
1.  Hata ayıklayıcının kesme modunda olması gerekir.  
  
2.  Gelen **hata ayıklama** menüsünde seçin **Windows**, tıklatıp **ayrıştırılmış kodu**.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Hata ayıklayıcısı güvenliği](../debugger/debugger-security.md)   
 [Yerel Kodda Hata Ayıklama](../debugger/debugging-native-code.md)



