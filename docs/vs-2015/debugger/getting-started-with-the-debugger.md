---
title: Hata ayıklayıcısını kullanmaya başlama | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: c763d706-3213-494f-b4d2-990b6e1ec456
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 755c4a0b66c91aa37f96d3d6f06972878ee856b8
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51771615"
---
# <a name="getting-started-with-the-debugger"></a>Hata Ayıklayıcısını Kullanmaya Başlama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio hata ayıklayıcısını kolayca herhangi bir dilde kullanılabilir. Burada basit bir C# programı hata ayıklama göstereceğiz, ancak C++ ve JavaScript gibi diğer dillerde kod için aynı adımları uygulayabilirsiniz.  
  
##  <a name="BKMK_Start_debugging_a_VS_project"></a> Temel C# projesinde hata ayıklama  
 Bir basit C# konsol uygulaması ile başlayalım (**dosya / yeni / Project**, ardından **Visual C#** seçip **konsol uygulaması**). Hiçbir zaman önce Visual Studio çalıştıysanız bkz [izlenecek yol: basit bir uygulama oluşturma](../ide/walkthrough-create-a-simple-application-with-visual-csharp-or-visual-basic.md). **Ana** yöntemi yalnızca 1, 10 kez bir tamsayı değişkenine ekler ve sonucu konsola yazdırır:  
  
```csharp  
static void Main(string[] args)  
{  
    int testInt = 0;  
    for (int i = 1; i <= 10; i++)  
    {  
        testInt += 1;  
    }  
    Console.WriteLine(testInt);  
}  
```  
  
 Bu kod yapısı'nda **hata ayıklama** yapılandırma. Bu yapılandırma varsayılan olarak ayarlanır. Yapılandırmaları hakkında daha fazla bilgi için bkz. [derleme yapılandırmalarını anlama](../ide/understanding-build-configurations.md).  
  
 Bu kod hata ayıklayıcıda tıklayarak çalıştırın **hata ayıklama / hata ayıklamayı Başlat** (veya **Başlat** araç çubuğunda veya **F5**). Uygulamayı gerçekten her şeyi konsol penceresinde olup olmadığını yazdırıldığı bildiremez şekilde neredeyse anında çıkılması gerekiyor.  
  
 Konsol penceresinde bir kesme noktası ayarlamak ve önceden Adımlama görmek için yürütme yeterince durdurabilirsiniz. Bir kesme noktası ayarlamak için imlecinizi koymak `Console.WriteLine` satır ve tıklayın **hata ayıklama / yeni kesme noktası / işlev kesme noktası**, ya da aynı satırda sol kenar boşluğunda tıklamanız yeterlidir. Kesme noktasına şu şekilde görünmelidir:  
  
 ![Bir kesme noktası ayarlamak](../debugger/media/getstartedbreakpoint.png "GetStartedBreakpoint")  
  
 Kesme noktaları hakkında daha fazla bilgi için bkz: [kullanılarak kesme noktaları](../debugger/using-breakpoints.md).  
  
##  <a name="BKMK_Inspect_Variables"></a> Değişkenleri İnceleme  
 Genellikle hata ayıklama, belirli bir noktada beklediğiniz değer içermeyen değişkenleri bulma içerir. Değişkenleri inceleyebilirsiniz yollardan bazılarını göstereceğiz.  
  
 Hata ayıklamayı yeniden başlatın. Yürütmeyi durdurur önce `Console.WriteLine` kodu yürütür. Önceden ilerlemeye tarafından yürütülecek neden olabilir (tıklayın **hata ayıklama / adım üzerinden** veya **F10**). Bu durumda, seçtiğiniz **içine adımla** (**F11**) ve aynı sonucu; edinmiş fark daha sonra açıklayacağız. Yöntemin son küme ayracı ile satır açık sarı. Konsol penceresine bakın. Görmelisiniz **10**.  
  
 Üzerine gelerek **testInt** değişkenin geçerli değeri bir veri ipucunda görüntülemek için.  
  
 ![DBG&#95;Temelleri&#95;veri&#95;ipuçları](../debugger/media/dbg-basics-data-tips.png "DBG_Basics_Data_Tips")  
  
 Yalnızca kod penceresi görmeniz gerekir **Otolar**, **Yereller**, ve **Watch** windows. Bu windows zaman yürütme değişkenlerin geçerli değerleri gösterir. Her iki **Otolar** ve **Yereller** windows show **testInt** değeriyle **10**.  
  
 ![Hata ayıklama sırasında otomatik değişkenler penceresi](../debugger/media/getstartedwindows.png "GetStartedWindows")  
  
 Bu windows hakkında daha fazla bilgi için bkz: [Otolar ve yerel öğeler Windows](../debugger/autos-and-locals-windows.md).  
  
 Değişken değeri programı aracılığıyla inceleyeceğiz olarak nasıl değiştiğini görelim. Bir kesme noktası ayarlamak `testInt += 1;` satır ve hata ayıklamayı yeniden başlatın. Durumunda olduklarını görmüş olmalısınız **testInt** içinde **Yereller** ve **Otolar** Windows **0**, ve **miyim** olan**1**. Devam hata ayıklama (**hata ayıklama / Continue**, veya **devam** araç çubuğunda veya **F5**), gördüğünüz gibi değerini **testInt** değişikliklerini **1**, ardından **2**ve benzeri. Bu değişiklikler arama yorgun aldığınızda kesme noktasını Kaldır (**hata ayıklama / geçiş kesme noktası**, veya kenar boşluğunda tıklayın) ve hata ayıklamaya devam et. Tüm kesme noktalarını kaldırmak istiyorsanız, tıklayın **hata ayıklama / tüm kesme noktalarını Sil**, veya **CTRL + SHIFT + F9**, tıklatıp **Evet** soran iletişim kutusunda **bunu Tüm kesme noktalarını kaldırmak istiyor?** .  
  
## <a name="stepping-into-and-over-function-calls"></a>İçine ve işlev çağrıları üzerinden Adımlama  
 Hata ayıklayıcı deyimi-tarafından-deyiminde kod yürütebilir (**içine adımla**) veya hata ayıklayıcı işlevleri atlar sırasında kod yürütebilir (**Step Over**) kod içinde (daha fazla ilgi için hızlı bir şekilde almak için işlev kodunu hala yürütülür). Her iki yöntemde de aynı hata ayıklama oturumu arasında geçiş yapabilirsiniz.  
  
 Arasındaki farkı görmek için **içine adımla** ve **Step Over**, başka bir yöntem tarafından çağrılan bir yöntem eklemek ihtiyacımız. C# uygulaması için bir yöntem ekleyin ve ana yöntemi çağırın. Kod aşağıdaki gibi görünmelidir:  
  
```csharp  
static void Main(string[] args)  
{  
    Method1();  
    Console.WriteLine("end");  
}  
  
private static void Method1()  
{  
    Console.WriteLine("in Method1");  
}  
```  
  
 Bir kesme noktası ayarlamak `Method1();` Main yöntemine çağrı ve hata ayıklamaya başlayın. Yürütmeyi keserse tıklayın **hata ayıklama / adımla** (veya **içine adımla** araç çubuğunda veya **F11**). Yürütme sonlarında yeniden ilk küme ayracı Method1() içinde:  
  
 ![Kodun içine Adımlama](../debugger/media/getstartedstepinto.png "GetStartedStepInto")  
  
 Hata ayıklamayı durdurmak ve yeniden başlatın ve yürütme kesme noktasında kesildiğinde **hata ayıklama / adım üzerinden** (veya **Step Over** araç çubuğunda veya **F10**). Yürütmeyi keser yeniden adresindeki `Console.WriteLine("end");`.  
  
 Hata ayıklayıcısı ile kod gezinme hakkında daha fazla bilgi edinmek istiyorsanız bkz [hata ayıklayıcısı ile kodlarda gezinme](../debugger/navigating-through-code-with-the-debugger.md).





