---
title: Yazmaçlar penceresi hakkında | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- Registers window, about Registers window
- debugging [Visual Studio], Registers window
ms.assetid: ab354047-053e-4f94-8ac1-26e761442b6f
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0219418b754c93b8e5e50997ede73e0611ed496a
ms.sourcegitcommit: a7de99f36e9ead7ea9e9bac23c88d05ddfc38b00
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/20/2018
ms.locfileid: "52257062"
---
# <a name="about-the-registers-window-in-visual-studio-c-c-visual-basic-f"></a>Visual Studio'da yazmaçlar penceresi hakkında (C#, C++, Visual Basic F#)

**Kaydeder** pencere, yalnızca adres seviyesinde hata ayıklamayı etkin değilse kullanılabilir **seçenekleri** iletişim kutusu, **hata ayıklama** düğümü.  
  
 Yazmaçları küçük parçaları işlemci etkin olarak üzerinde çalıştığı veri depolamak için kullanılan özel bir işlemci (CPU) konumlardır. Derleme veya kaynak kodu yorumlama gerektiğinde verileri bellekten kayıtları ve yeniden yeniden taşıma yönergeleri oluşturur. Yazmaçları veri erişimi sağlayan bir kayıttaki verileri korumak ve sürekli olarak erişmek için işlemci kodu daha hızlı işlemci sürekli olarak yüklemek ve kayıtları kaldırmak için gerektiren kod yürütmesine eğilimi gösterir. Bu nedenle, bellek, veri erişimi için karşılaştırıldığında çok hızlıdır. Kayıtlara verileri korumak ve diğer iyileştirmeler gerçekleştirmek derleyicinin kolaylaştırmak için genel değişkenleri kullanmaktan kaçının ve yerel değişkenlerini mümkün olduğunca gerekir. Bu şekilde yazılmış kod iyi yerleşim yeri başvurunun olması bildirilir. C/C++ gibi bazı dillerde Programcı değişkeni her zaman bir kayıttaki tutmak için en iyi şekilde denemek için varsaymasını söyleyen bir kayıt değişken bildirebilirsiniz. Daha fazla bilgi için [kaydetme anahtar sözcüğü](https://msdn.microsoft.com/library/5b66905a-2f7f-4918-bb55-5e66d4bc50f9).  
  
 İki tür olarak kayıtları ayrılabilir: genel amaçlı ve özel amaçlı. Genel amaçlı kayıtları iki sayıyı toplayan veya başvuran bir dizideki bir öğe gibi genel işlemler için veri tutun. Özel amaçlı kayıtları belirli amaçlar ve özel bir anlamı vardır. Programın çağrı yığını izlemek için işlemci kullanır, yığın işaretçisi Kaydet, iyi bir örnektir. Bir programcısı, yığın işaretçisi doğrudan düzenlemezsiniz olmayabilir. Ancak, yığın işaretçisi bir işlev çağrısı sonunda geri dönmek nereye işlemci bilmez olduğundan düzgün programınızın çalışması için gereklidir.  
  
 Çoğu genel amaçlı kayıtları yalnızca bir tek veri öğesi tutun. Örneğin, bir tek bir tamsayı, kayan noktalı sayı veya bir dizideki öğe. Bazı yeni işlemci, daha büyük kayıtlar, küçük bir dizi veri tutabilen vektör kayıt adı yok. Çok fazla veri tuttukları olduğundan, vektör kayıt işlemleri çok hızlı bir şekilde gerçekleştirilmesi gereken dizileri içeren izin verir. Vektör kayıt pahalı, yüksek performanslı Süper bilgisayarlar üzerinde ilk kez kullanıldı, ancak artık yoğun grafik işlemlerde avantajı için burada kullanılan mikro kullanılabilir hale gelmektedir.  
  
 Bir işlemci, genellikle iki kayan nokta işlemleri diğeri tamsayı işlemleri için en iyi duruma getirilmiş bir genel amaçlı kayıtları sahiptir. Edilebileceği bu kayan nokta adı verilir ve tamsayı kaydeder.  
  
 Çalışma zamanında fiziksel kasalar mikro erişen yerel kod için yönetilen kod derlenir. **Kaydeder** penceresi, ortak dil çalışma zamanı veya yerel kod için fiziksel bu kayıtları görüntüler. **Kaydeder** penceresi yazmaçların kavramı desteklemeyen diller olduğundan komut dosyası ve SQL komut dosyası veya SQL uygulama için kayıt bilgileri görüntülemez.  
  
 Görüntüleme hakkında daha fazla bilgi için **kaydeder** penceresinde görmek [kayıtları penceresini kullanarak](../debugger/how-to-use-the-registers-window.md).  
  
 Baktığınızda **kaydeder** penceresinde gibi girişler görürsünüz `EAX = 003110D8`.  
  
 Sol tarafındaki simge `=` işaretidir, kayıt adı `EAX`, bu durumda. Sayı sağındaki `=` oturum kayıt içeriğini temsil eder.  
  
 **Kaydeder** penceresi bir kaydın içeriğini görünümü daha fazlasını yapmanıza olanak sağlar. Yerel kodda kesme modunda olduğunda, bir kayıt içeriğine tıklayın ve değerini düzenleyin. Bu, rastgele yapmanız gereken bir şey değildir. Düzenlemekte olduğunuz kayıt ve içerdiği verilere anlamadan dikkatsiz düzenleme sonucunu programın kilitlendiğini ya da diğer bir istenmeyen sonuç olması olasıdır. Ne yazık ki, ayrıntılı bir açıklama çeşitli Intel ve Intel uyumlu işlemci kayıt kümelerinin kadar bu kısa giriş kapsamı dışındadır gider.  
  
## <a name="register-groups"></a>YAZMAÇ grupları  
 Dağınıklığı, azaltmak için **kaydeder** penceresi kayıtları gruplar halinde düzenler. Üzerinde sağ tıkladığınızda **kaydeder** penceresinde görüntülemek veya gördüğünüz şekilde Gizle gruplarının bir listesini içeren bir kısayol menüsü göreceksiniz.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Nasıl yapılır: yazmaçlar penceresini kullanma](../debugger/how-to-use-the-registers-window.md)   
 [Hata Ayıklayıcısı Temel Bilgileri](../debugger/getting-started-with-the-debugger.md)