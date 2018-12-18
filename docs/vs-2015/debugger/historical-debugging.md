---
title: Geçmiş hata ayıklama | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7cc5ddf2-2f7c-4f83-b7ca-58e92e9bfdd2
caps.latest.revision: 9
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d43e48b67cdbfabcb38703469f8570f78336dcab
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51794601"
---
# <a name="historical-debugging"></a>Geçmiş Hata Ayıklama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Geçmiş hata ayıklama IntelliTrace tarafından toplanan bilgiler bağımlı hata ayıklama bir moddur. Geriye doğru gitme ve uygulamanızın yürütmesini iletmek ve durumunu incelemek sağlar.  
  
 IntelliTrace, Visual Studio Enterprise edition (ancak Professional veya Community sürümlerini değil) kullanabilirsiniz.  
  
## <a name="why-use-historical-debugging"></a>Geçmiş hata ayıklama neden kullanmalısınız?  
 Hataları bulmak için kesme noktaları ayarlamak yerine hit-or-miss affair olabilir. Kodunuzda yakın bir yerde olması için hata nerede şüphelendiğiniz bir kesme noktası ayarlayın ve ardından hata ayıklayıcı ve kesme noktasına isabet ve burada yürütmeyi keser yerde hatanın kaynağını ortaya koyabilir alır soluk uygulamayı çalıştırın. Aksi durumda, kod içinde başka bir yerde bir kesme noktası ayarlamayı deneyin ve sorun bulana kadar test adımlarınızı tekrar tekrar yürütme hata ayıklayıcıyı yeniden çalıştırmak sahip olacaksınız.  
  
 ![bir kesme noktası ayarlamak](../debugger/media/breakpointprocesa.png "BreakpointProcesa")  
  
 Geçici uygulamanızdaki dolaşan ve kesme noktaları ayarlayın, hata ayıklamayı yeniden başlatmak zorunda kalmadan (çağrı yığını ve yerel değişkenler) durumunu incelemek için IntelliTrace ve geçmiş hata ayıklama kullanın ve test adımları yineleyin. Bu, çok fazla kaydedebilirsiniz süresini, özellikle zaman hata bulunan yürütmek için uzun zaman alan derin bir testi senaryosunda.  
  
## <a name="how-do-i-start-using-historical-debugging"></a>Geçmiş hata ayıklama kullanmaya nasıl başlarım?  
 IntelliTrace varsayılan olarak açıktır. Tek yapmanız gereken olan hangi olayların ve işlev çağrılarının ilginizi çeken karar verin. Aramak istediğiniz tanımlama hakkında daha fazla bilgi için bkz. [IntelliTrace özellikleri](../debugger/intellitrace-features.md). Adım adım bir hesabı IntelliTrace ile hata ayıklama bilgi için bkz: [izlenecek yol: IntelliTrace'i kullanarak](../debugger/walkthrough-using-intellitrace.md).  
  
## <a name="navigating-your-code-with-historical-debugging"></a>Geçmiş hata ayıklama ile kodunuzda gezinme  
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
  
1. Araçlar / Seçenekler / IntelliTrace / genel olarak, IntelliTrace etkinleştirilmiş ve IntelliTrace olayları seçin ve çağrı bilgisi seçeneğini emin olun. Bu seçeneği belirlemezseniz, gezinti kanalını (aşağıda açıklandığı gibi) görmeniz mümkün olmayacaktır.  
  
2. Bir kesme noktası ayarlamak `Console.WriteLine(resultInt);` satır.  
  
3. Hata ayıklama başlatılamıyor. Kesme noktasına kodu yürütür. İçinde **Yereller** penceresinde gördüğünüz gibi değerini `resultInt` 44 olduğu.  
  
4. Açık **tanılama araçları** penceresi (**Göster / hata ayıklama tanılama araçları**). Kod penceresi şu şekilde görünmelidir:  
  
    ![Kod penceresinde kesme noktasında](../debugger/media/historicaldebuggingbreakpoint.png "HistoricalDebuggingBreakpoint")  
  
5. Bir çift ok kesme noktası hemen üzerinde sol kenar boşluğu yanındaki görmeniz gerekir. Bu alan gezinti cilt payını çağrılır ve geçmiş hata ayıklama için kullanılır. Oka tıklayın.  
  
    Kod penceresinde durumunda olduklarını görmüş olmalısınız önceki kod satırının (`int resultInt = AddIterative(testInt);`) pembe renklendirilmiştir. Pencerenin geçmiş hata ayıklama artık, bir ileti görmeniz gerekir.  
  
    Kod penceresi artık şöyle görünür:  
  
    ![Geçmiş hata ayıklama modunda kod penceresinde](../debugger/media/historicaldebuggingback.png "HistoricalDebuggingBack")  
  
6. İçine adımla artık `AddAll()` yöntemi (**F11**, veya **içine adımla** Gezinti cilt payını düğmesi. İleri adım atın (**F10**, veya **sonraki çağrı Git** Gezinti cilt payını. Pembe satır şu anda etkin `j = AddInt(j);` satır. **F10** bu durumda, sonraki kod satırına girmez. Bunun yerine, bir sonraki işlev çağrısı için adımlar. Geçmiş hata ayıklama çağrı çağrı gider ve bir işlev çağrısı içermez kod satırlarını atlar.  
  
7. Artık adımla `AddInt()` yöntemi. Bu kodda hata hemen görmeniz gerekir.  
  
   Bu yordam, yalnızca geçmiş hata ayıklama ile yapabilecekleriniz yüzey çizik. Farklı ayarlar ve gezinti cilt payını farklı düğmeler etkileri hakkında daha fazla bilgi için bkz: [IntelliTrace özellikleri](../debugger/intellitrace-features.md).





