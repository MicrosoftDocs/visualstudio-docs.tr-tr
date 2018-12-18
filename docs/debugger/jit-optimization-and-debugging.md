---
title: JIT iyileştirmesi ve hata ayıklama | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], optimized code
- optimized code, debugging
ms.assetid: 19bfabf3-1a2e-49dc-8819-a813982e86fd
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9a9b18ab38c7c19fa5208d34439bd3133099e8bc
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2018
ms.locfileid: "31477361"
---
# <a name="jit-optimization-and-debugging"></a>JIT İyileştirmesi ve Hata Ayıklaması
**En iyi duruma getirme .NET içinde nasıl çalışır?:** kodda hata ayıklama çalışıyorsanız, bu zaman kodu daha kolay olmasıdır **değil** en iyi duruma getirilmiş. İyileştirilmiş kodda, böylece daha hızlı çalışır, ancak daha az doğrudan bir eşleme özgün kaynak koduna sahip derleyici ve çalışma zamanı verilmiş CPU kodda değişiklik olmasıdır. Bunun anlamı hata ayıklayıcıları yerel değişkenlerin değerini söyleyin ve kod atlama sık sorunu yaşıyor ve kesme noktaları beklendiği gibi çalışmayabilir.

Normalde yayın yapı yapılandırma en iyi duruma getirilmiş kod oluşturur ve hata ayıklama derleme yapılandırmasını desteklemez. `Optimize` MSBuild özelliği, derleyici kodu en iyi duruma getirme söylediyse olup olmadığını denetler.

.NET ekosistemi, iki adımlı bir işlem CPU yönergeleri için kaynak kodu çevrilir: ilk olarak, C# Derleyici yazdığınız metin MSIL adlı bir ara ikili biçime dönüştürür ve bu .dll dosyaları için yazar. Daha sonra .NET çalışma zamanı bu MSIL CPU yönergeleri dönüştürür. Her iki adımın dereceye için en iyi duruma getirebilirsiniz, ancak daha önemli iyileştirmeler .NET çalışma zamanı tarafından gerçekleştirilen ikinci adımı gerçekleştirir.

**'Modülü Yükü (sadece yönetilen) bastırmak JIT iyileştirmesi' seçeneği:** hata ayıklayıcı iyileştirmeler etkinleştirilerek derlenmiş DLL hedef işlem içinde yüklediğinde olanlar denetleyen bir seçenek sunar. Bu seçenek işaretli değilse (varsayılan durumu), sonra da .NET çalışma zamanı CPU koda MSIL kod derlediğinde iyileştirmeler bırakır. Seçenek işaretlenirse, hata ayıklayıcı iyileştirmeleri devre dışı bırakılmasını ister.

**Bastırmak JIT iyileştirmesi modülü Yükü (sadece yönetilen)** seçeneği bulunabilir **genel** altında sayfa **hata ayıklama** düğümünde **seçenekleri** iletişim kutusu.

**Ne zaman, kontrol etmelidir bu seçenek:** nuget paketi gibi başka bir kaynaktan DLL'leri indirilir ve bu DLL kodda hata ayıklama istediğinizde bu seçeneği işaretleyin. Bunun çalışması sırayla simge (.pdb) dosyası için bu DLL bulmalıdır.

Yalnızca hata ayıklama yerel olarak oluşturmakta olduğunuz kodu ilgileniyorsanız, bazı durumlarda, bu seçeneğin etkinleştirilmesi önemli ölçüde hata ayıklama aşağı yavaşlatır gibi bu seçeneği işaretlemeyin en iyisidir. Yavaşlamasına iki nedeni vardır:

* En iyi duruma getirilmiş kodu daha hızlı çalışır. Çok sayıda kod iyileştirmeler kapatılması, performans etkisi ekleyebilirsiniz.
* Etkin sadece kendi kodumu varsa, hata ayıklayıcı bile deneyin ve en iyi duruma getirilir DLL'ler için simgeler yükleyin. Simgeler bulma uzun sürebilir.

**Bu seçenek sınırlamaları:** burada bu seçenek olacak iki durum vardır **değil** çalışır:

1. Burada zaten çalışan bir işlemi hata ayıklayıcı ekleme durumlarda, bu seçenek zaten hata ayıklayıcısı ekli anda yüklenen modülleri üzerinde hiçbir etkisi gerekir.
2. Bu seçenek silinmiş DLL'leri üzerinde hiçbir etkisi yoktur (a.k.a Ngen) önceden yerel koda derlenmiş. Ancak, önceden derlenmiş kod kullanımını değişken 'COMPlus_ZapDisable', '1' olarak ayarlanan ortamıyla işlemi başlatarak devre dışı bırakabilirsiniz.

## <a name="see-also"></a>Ayrıca Bkz.  
 [Yönetilen kodda hata ayıklama](../debugger/debugging-managed-code.md)   
 [Hata ayıklayıcısı ile kodlarda gezinme](../debugger/navigating-through-code-with-the-debugger.md)   
 [Çalıştırma işlemine iliştirme](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)   
 [Yönetilen Yürütme İşlemi](/dotnet/standard/managed-execution-process)
