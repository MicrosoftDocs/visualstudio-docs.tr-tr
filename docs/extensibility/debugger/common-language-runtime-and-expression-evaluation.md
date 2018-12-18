---
title: Ortak dil çalışma zamanı ve ifade değerlendirme | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation, and common language runtime
ms.assetid: b36c1eb5-1aaf-48a6-b287-ee7a273d2b1c
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 7db25e563e2728d30ade9f4c7f2dc6faf659721b
ms.sourcegitcommit: 36835f1b3ec004829d6aedf01938494465587436
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/23/2018
ms.locfileid: "39204381"
---
# <a name="common-language-runtime-and-expression-evaluation"></a>Ortak dil çalışma zamanı ve ifade değerlendirme
> [!IMPORTANT]
>  Visual Studio 2015'te, bu şekilde ifade değerlendiricisi uygulama kullanım dışı bırakılmıştır. CLR ifade değerlendiricisi uygulama hakkında daha fazla bilgi için lütfen bkz [CLR ifade değerlendiricilerini](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) ve [yönetilen ifade değerlendiricisi örnek](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Derleyiciler, Visual Basic ve C (C-sharp olarak okunur) ortak dil çalışma zamanı (CLR) hedefleyen, #, Microsoft Ara dil (sonraki olan MSIL) oluşturmak gibi yerel koda derlenmiş. CLR hata ayıklama altyapısı elde edilen kodda hata ayıklamak için (DE) sağlar. Visual Studio IDE'ye özel programlama diliniz tümleştirme planlıyorsanız, MSIL olarak derlemek seçebilirsiniz ve bu nedenle kendi DE yazmanız gerekmez. Ancak, programlama diliniz bağlam içinde ifadelerin değerlendirilmesi özelliğine sahip olan bir ifade değerlendiricisi (EE) yazma gerekecektir.  
  
## <a name="discussion"></a>Tartışma  
 Bilgisayar dili ifadeleri, genellikle bir dizi veri nesneleri ve bunları yönetmek için kullanılan işleçleri kümesini üretmek için ayrıştırılır. Örneğin, "A"'i ve "büyük olasılıkla başka bir veri nesnesi içinde elde edilen B" ifadesi "A + B" Toplama işleci (+) uygulamak için veri ayrıştırılması nesneleri. Toplam veri nesneleri, işleçler ve ilişkilerini çoğunlukla temsil edilen bir programda ağacı düğümlerde işleçler ve veri nesnelerini dallar, bir ağaç olarak. Bir ifade ağacı forma bozuk genellikle ayrıştırılmış bir ağaç olarak adlandırılır.  
  
 Bir ifade ayrıştırılmış bir kez sembol sağlayıcısı (SP) her veri nesnesi değerlendirmek için çağrılır. Örneğin, "A" tanımlanmışsa, hem de birden fazla metot, soru "A?" Bir değeri saptanabilen önce yanıtlanması gerekir. SP tarafından döndürülen yanıt "Beşinci yığın çerçevesinde üçüncü öğe" gibi bir şeydir veya "Bu yönteme 50 bayt statik bellek başlangıcı dışında bir ayrıldı."  
  
 Program için MSIL üretmenin yanı sıra, CLR derleyicileri de bir Program veritabanına yazılan çok açıklayıcı hata ayıklama bilgilerini oluşturabilir (*.pdb*) dosyası. Bir özel dil derleyicisi CLR derleyicileri olarak aynı biçimde hata ayıklama bilgisi üretir sürece, CLR'nin SP dil veri nesneleri adlı tanımlamak kullanabilirsiniz. Adlandırılmış veri nesnesi belirlendikten sonra EE bağlayıcı nesnesi ilişkilendirmek (veya bağlamak için) veri nesnesi, nesnenin değeri tutan bellek alanı kullanır. DE alın veya veri nesnesi için yeni bir değer ayarlayın.  
  
 Özel bir derleyici çağırarak hata ayıklama bilgileri CLR sağlayabilir `ISymbolWriter` arabirimi (.NET Framework ad alanında tanımlanan `System.Diagnostics.SymbolStore`). MSIL olarak derleme ve bu arabirimler üzerinden hata ayıklama bilgileri yazılırken, özel bir derleyici SP'yi ve CLR DE kullanabilirsiniz Bu, büyük ölçüde özel bir dil Visual Studio IDE'ye tümleştirme kolaylaştırır.  
  
 CLR DE bir ifadeyi değerlendirmek için özel EE çağırdığında bir SP ve bağlayıcı nesnesi arabirimleri ile EE DE sağlar. Bu nedenle, CLR tabanlı hata ayıklama altyapısı anlamına gelir yazma yalnızca uygun bir ifade değerlendiricisi arabirimleri uygulamak gerekli olan; CLR bağlama ve sizin için işleme sembol üstlenir.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Bir CLR ifade değerlendiricisi yazma](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)