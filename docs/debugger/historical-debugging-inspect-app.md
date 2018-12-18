---
title: Geçmiş hata ayıklama ile uygulamanızı denetleyin | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 629b5d93-39b2-430a-b8ba-d2a47fdf2584
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 2309a3213344607fa0f5b2f626fc67af2eff8f79
ms.sourcegitcommit: a749c287ec7d54148505978e8ca55ccd406b71ee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/21/2018
ms.locfileid: "46542344"
---
# <a name="inspect-your-app-with-intellitrace-historical-debugging-in-visual-studio"></a>Visual Studio'da hata ayıklama geçmiş IntelliTrace ile uygulamanızı denetleyin
Kullanabileceğiniz [geçmiş hata ayıklama](../debugger/historical-debugging.md) geriye doğru gitme, uygulamanızın yürütmesini iletmek ve durumunu inceleyin.  
  
IntelliTrace, Visual Studio Enterprise sürümünde, ancak değil Professional veya Community sürümlerini kullanabilirsiniz.  
  
## <a name="navigate-your-code-with-historical-debugging"></a>Geçmiş hata ayıklama ile kodunuzda gezinin  
 Bir hata için basit bir program başlayalım. Bir C# konsol uygulamasında, aşağıdaki kodu ekleyin:  
  
```csharp  
static void Main(string[] args)  
{  
    int testInt = 0;  
    int resultInt = AddAll(testInt);  
    Console.WriteLine(resultInt);  
}  
private static int AddAll(int j)  
{  
    for (int i = 0; i < 20; i++)  
    {  
        j = AddInt(j);  
    }  
    return j;  
}  
  
private static int AddInt(int add)  
{  
    if (add == 10)  
    {  
        return add += 25;  
    }  
    return ++add;  
}  
```  
  
 Biz varsayacağız beklenen değeri `resultInt` arama sonra `AddAll()` 20'dir (artan sonucunu `testInt` 20 kez). (Şu hatayı göremez varsayacağız `AddInt()`). Ancak, gerçekte 44 sonucudur. Nasıl biz bulabilir hatayı aracılığıyla atlamadan `AddAll()` 10 kez? Geçmiş hata ayıklama hatayı daha hızlı ve daha kolay bulmak için kullanabiliriz. İşte nasıl:  
  
1.  İçinde **Araçlar > Seçenekler > IntelliTrace > Genel**, IntelliTrace etkin olduğundan emin olun ve seçin **IntelliTrace olayları ve çağrı bilgileri**. Bu seçeneği belirlemezseniz, gezinti kanalını (aşağıda açıklandığı gibi) görmeniz mümkün olmayacaktır.  
  
2.  Bir kesme noktası ayarlamak `Console.WriteLine(resultInt);` satır.  
  
3.  Hata ayıklama başlatılamıyor. Kesme noktasına kodu yürütür. İçinde **Yereller** penceresinde gördüğünüz gibi değerini `resultInt` 44 olduğu.  
  
4.  Açık **tanılama araçları** penceresi (**hata ayıklama > tanılama araçlarını Göster**). Kod penceresi şu şekilde görünmelidir:  
  
     ![Kod penceresinde kesme noktasında](../debugger/media/historicaldebuggingbreakpoint.png "HistoricalDebuggingBreakpoint")  
  
5.  Bir çift ok kesme noktası hemen üzerinde sol kenar boşluğu yanındaki görmeniz gerekir. Bu alan gezinti cilt payını çağrılır ve geçmiş hata ayıklama için kullanılır. Oka tıklayın.  
  
     Kod penceresinde durumunda olduklarını görmüş olmalısınız önceki kod satırının (`int resultInt = AddIterative(testInt);`) pembe renklendirilmiştir. Pencerenin geçmiş hata ayıklama artık, bir ileti görmeniz gerekir.  
  
     Kod penceresi artık şöyle görünür:  
  
     ![Geçmiş hata ayıklama modunda kod penceresinde](../debugger/media/historicaldebuggingback.png "HistoricalDebuggingBack")  
  
6.  İçine adımla artık `AddAll()` yöntemi (**F11**, veya **içine adımla** Gezinti cilt payını düğmesi. İleri adım atın (**F10**, veya **sonraki çağrı Git** Gezinti cilt payını. Pembe satır şu anda etkin `j = AddInt(j);` satır. **F10** bu durumda, sonraki kod satırına girmez. Bunun yerine, bir sonraki işlev çağrısı için adımlar. Geçmiş hata ayıklama çağrı çağrı gider ve bir işlev çağrısı içermez kod satırlarını atlar.  
  
7.  Artık adımla `AddInt()` yöntemi. Bu kodda hata hemen görmeniz gerekir.  

## <a name="next-steps"></a>Sonraki adımlar

Bu yordam, yalnızca geçmiş hata ayıklama ile yapabilecekleriniz yüzey çizik.

- Anlık görüntü hata ayıklama sırasında görüntülemek için bkz [IntelliTrace kullanarak önceki uygulama durumlarını incelemek](../debugger/view-historical-application-state.md).
- Farklı ayarlar ve gezinti cilt payını farklı düğmeler etkileri hakkında daha fazla bilgi için bkz: [IntelliTrace özellikleri](../debugger/intellitrace-features.md).