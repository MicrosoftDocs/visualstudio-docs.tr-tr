---
title: Çift yönlü dillerde uygulamalar oluşturma | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Hebrew character display, creating applications
- bi-directional language support, about bi-directional language support
- Arabic language, creating applications
ms.assetid: b56f9795-ed8d-4452-9d49-8ca0b0145d86
caps.latest.revision: 11
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 32acd2a58c2482de6fdd7ed10c99a023d41a8cb4
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49248501"
---
# <a name="creating-applications-in-bi-directional-languages"></a>Çift Yönlü Dillerde Uygulamalar Oluşturma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sağ-Arapça ve İbranice gibi sola doğru dillerde yazılan metin görüntüleyen uygulamalar oluşturmak için Visual Studio kullanabilirsiniz. Bazı özellikler için özellikleri ayarlayabilirsiniz. Diğer durumlarda, kod özellikleri uygulamalıdır.  
  
> [!NOTE]
>  Girin ve çift yönlü diller görüntülemek için uygun dili ile yapılandırılmış bir Windows sürümü ile çalışmalısınız. Bu bir İngilizce sürümüyle ilgili dil paketi yüklü olan Windows veya Windows uygun şekilde yerelleştirilmiş sürümünü olabilir.  
  
## <a name="types-of-application-that-support-bi-directional-languages"></a>Uygulama bu destek çift yönlü diller türleri  
  
1.  Windows uygulamaları. İki yönlü metin, sağdan sola okuma düzeni ve yansıtma (windows, menüler, iletişim kutuları ve benzeri düzenini ters) için destek içeren tam çift yönlü uygulamalar oluşturabilirsiniz. Yansıtma dışında bu özellikler varsayılan olarak veya özellik ayarları olarak kullanılabilir. Yansıtma ileti kutuları gibi bazı özellikler için doğal olarak desteklenir. Ancak, diğer durumlarda kod yansıtma uygulamalıdır. Daha fazla bilgi için [Windows Forms uygulamaları için iki yönlü destek](http://msdn.microsoft.com/library/7b622fa4-f390-4e4d-b624-83a1917cccf2).  
  
2.  Web uygulamaları. Web Hizmetleri için destek ve alma UTF-8 ve Unicode metin gönderme, çift yönlü diller içeren uygulamalar için uygun hale getirir. Bir Web uygulaması yönlü destek derecesini bağımlı kullanıcının tarayıcı yönlü özelliklere ne kadar iyi destekler, bu nedenle web istemcisi uygulamalarını tarayıcılar için kendi kullanıcı arabirimini kullanır. Visual Studio'da, Arapça veya İbranice metin, sağdan sola okuma düzeni, dosya kodlamasını ve yerel kültür ayarları için desteğe sahip uygulamalar oluşturabilirsiniz. Daha fazla bilgi için [ASP.NET Web uygulamaları için çift yönlü destek](http://msdn.microsoft.com/library/5576f9b1-9b86-41ef-8354-092d366bcd03).  
  
3.  Konsol uygulamaları. Konsol uygulamaları, metin çift yönlü dil desteği içermez. Windows konsol uygulamaları ile nasıl çalıştığına ilişkin bir sonucu budur.  
  
## <a name="visual-studio-features-that-are-fully-supported"></a>Tam olarak desteklenen visual Studio özellikleri  
 Visual Studio'da tasarım zamanında çift yönlü diller aşağıdaki şekillerde kullanabilirsiniz:  
  
-   **Metin girişi** Visual Studio Unicode'u destekler, dolayısıyla sisteminizi ayarlanmış uygun yerel ve giriş dili, Arapça veya İbranice metin girebilirsiniz. (Keşide ve aksan Arapça desteği içerir.)  
  
-   **Nesne adları** çift yönlü diller çözümleri, projeleri, dosyaları, klasörleri ve benzeri için ad atamak için kullanabilirsiniz. Kodu, değişkenleri, sınıflar, nesne, öznitelikler, meta verileri ve diğer öğeleri adları için çift yönlü diller kullanabilirsiniz.  
  
-   **Dosya kodlama** kaydedebilir ve dosyaları bir dile özgü veya Unicode kodlaması ile açın. Daha fazla bilgi için [nasıl yapılır: kodlama ile açık dosyaları kaydetme ve](../ide/how-to-save-and-open-files-with-encoding.md).  
  
## <a name="features-with-limited-or-no-support"></a>Sınırlı veya destek özellikleri  
 Çift yönlü dil uygulamaları için ortak diğer özellikler tamamen Visual Studio'da veya bazı durumlarda, hiç desteklenmez. Bu güncelleştirmeler şunlardır:  
  
-   **Sağdan sola okuma düzeni** varsayılan olarak, Visual Studio'da kullandığınız metin girişi denetimleri sağdan sola okuma düzeni kullanır. Çoğu durumda, standart Windows hareketleri okuma sırasını değiştirmek için kullanabilirsiniz. Örneğin, özellik değerleri için sağdan sola okuma düzeni desteklemek için Özellikler penceresinde geçiş yapmak için Ctrl + sağ Shift tuşuna basabilirsiniz.  
  
     Ancak, sağdan sola okuma düzeni, Visual Studio'da her yerde desteklenmiyor. Özel durumlar şunlardır:  
  
    -   Her zaman onay kutuları, açılan listeler ve diğer Visual Studio iletişim kutularındaki denetimler sağdan sola okuma düzeni kullanın.  
  
    -   Kod Düzenleyicisi'ni (ve metin düzenleyici) sağdan sola okuma düzeni desteklemez. Bir çift yönlü dil metin girebilirsiniz, ancak okuma düzeni, her zaman sol ve sağ.  
  
## <a name="naming-things-using-arabic-or-hebrew-text"></a>Arapça kullanarak nesneleri adlandırma veya İbranice metin  
 Arapça veya İbranice metin, klasörleri, değişkenleri veya diğer nesnelerin adları atamak için kullanabilirsiniz. Arapça ile çalışırken Keşide ve aksan işaretleri dahil olmak üzere herhangi bir Arapça karakter kullanabilirsiniz.  
  
 Aşağıdaki öğeleri, Arapça veya İbranice kullanarak adlı ve Visual Studio doğru şekilde ele alınacaktır:  
  
-   Çözüm, proje ve proje yola dahil tüm klasörleri dahil olmak üzere, dosya adları. Çözüm Gezgini'nde çözüm ve öğe adları doğru görüntüler.  
  
-   Dosya içerikleri. Açabilir veya dosyaları Unicode kodlama veya seçili bir kod sayfası ile kaydedin.  
  
    > [!NOTE]
    >  Kod Düzenleyicisi, bir özel durumdur. Ayrıntılar için aşağıya bakın.  
  
-   Veri öğeleri. **Sunucu Gezgini** bu öğeleri doğru görüntüler ve bunları düzenlemenize izin.  
  
-   Öğeleri Windows panoya kopyalandı.  
  
-   Öznitelikler ve meta verileri.  
  
-   Özellik değeri. Özellikler penceresinde, Arapça veya İbranice metin kullanabilirsiniz. Pencere, standart Windows tuş vuruşları (CTRL + RightShift için sağdan sola ve CTRL + LeftShift için soldan sağa) kullanarak sağdan sola ve sağa sola okuma düzeni arasında geçiş yapmanızı sağlar.  
  
-   Kod ve metin. (Aynı zamanda olan metin düzenleyiciyi) Kod düzenleyicisinde, Arapça veya İbranice adı sınıfları, İşlevler, değişkenler, özellikler, dize değişmez değerleri, öznitelikleri ve benzeri kullanabilirsiniz. Ancak, düzenleyici sağdan sola okuma düzeni desteklemez; metin her zaman sol kenar boşluğunda başlatır.  
  
    > [!TIP]
    >  Bunları, programlarına kodlamak yerine kaynak dosyalarında dize değişmez değerleri koyun önerilir. Daha fazla bilgi için [izlenecek yol: Windows formlarını yerelleştirme](http://msdn.microsoft.com/en-us/9a96220d-a19b-4de0-9f48-01e5d82679e5).  
  
    > [!NOTE]
    >  Nasıl, bu dillerde adlı nesnelere başvurmak için tutarlı olması gerekir. Örneğin, Arapça bir değişkeni adlandırmada Kaşida kullanırsanız, bu değişkene söz konusu olduğunda her zaman Kaşida kullanmalısınız veya hatalara neden olabilecek.  
  
-   Kod açıklamaları. Açıklamalar, Arapça veya İbranice oluşturabilirsiniz. Açıklama Oluşturucu aracında bu diller de kullanabilirsiniz.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Forms uygulamalarında iki yönlü destek Windows](http://msdn.microsoft.com/library/7b622fa4-f390-4e4d-b624-83a1917cccf2)   
 [ASP.NET Web uygulamaları için çift yönlü destek](http://msdn.microsoft.com/library/5576f9b1-9b86-41ef-8354-092d366bcd03)   
 [Uygulamaları Genelleştirme](../ide/globalizing-applications.md)   
 [Uygulamaları Yerelleştirme](../ide/localizing-applications.md)

