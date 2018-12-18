---
title: Kod çözümleme İlkesi hataları | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.codeanalysis.policyfailures
helpviewer_keywords:
- policy errors, code analysis
ms.assetid: d1f221cd-68c0-4277-9397-b76ad0dbae77
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 4582f19882cc283acd3712236cdbb081e2f8f3ae
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49859830"
---
# <a name="code-analysis-policy-errors"></a>Kod Çözümleme İlkesi Hataları
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Kod Analizi İlkesi iade aşamasında karşılanmıyor aşağıdaki hatalar oluşur:  
  
 **Bir veya daha fazla proje için Kod Analizi ayarları Kod Analizi ilkesiyle uyumlu değildir.**  
  
 Bir veya daha fazla kod projeleri için takım projesi kaynak denetimine iade Kod Analizi gereksinimleri karşılanmadı. Bu hata, bir veya daha fazla aşağıdaki koşullardan biri tarafından kaynaklanabilir:  
  
1. Tüm çözüm içindeki projeleri için derleme üzerinde kod analizi etkin değil.  
  
2. Visual Studio'da proje daha az kısıtlayıcı için ayarlanmış yerel kural **eylem** takım proje kural gibi ayarlamak için bir kural kümesi daha ayarlama **eylem**=**hata**  sunucusunda sahip kendi **eylem** kümesine **uyarı** veya **hiçbiri** kuralında Visual Studio'da çalıştırılmasını ayarlayın).  
  
3. Kural kümesi Visual Studio'da belirtilen tüm kurallar kural kümesi içinde takım projesi için Kod Analizi iade ilkesi belirtilen belirtilen içermiyor.  
  
   **Kod Analizi ilkesini başarısız oldu. Projede hata olmadığından {0} veya derleme güncel değil.**  
  
   Derleme hataları içeriyor veya hatalar ancak kod analizi, düzeltme gerçekleştirilmedi.  
  
   **İade etme başarısız oldu. Kod Analizi İlkesi Visual Studio aracılığıyla açık bir Çözümle iade olmasını gerektirir.**  
  
   Kod Analizi İlkesi, tüm dosyalar iade edilen içinde açık olan çözümü gerekir olmasını gerektirir. Bu hatayı düzeltmek için dosyanın iade edilmesini içeren çözümü açın.  
  
   **Tüm dosyalar bekleyen iade içinde açık olan çözümü sahiptir.**  
  
   Kod Analizi İlkesi, tüm dosyalar iade edilen içinde açık olan çözümü gerekir olmasını gerektirir. Açık bir çözüm yoktur, ancak bazı dosyalar "bekleyen iade etme" Görünümü'nde, şu anda açılan çözümü parçası değildir, bu hata ortaya çıkar. Bu hatayı düzeltmek için dosyanın iade edilmesini içeren çözümü açın.  
  
   **Sürümü '{0}' doğru değil. Tanımlayıcı-ilkesinde belirtilen ad '{1}'.**  
  
   Bu hata, .NET projelerine yöneliktir. Kod Analizi İlkesi tarafından gerekli bir kural .dll dosyasını yerel bilgisayarda var, ancak sürüm/genel anahtar eşleşmiyor. Bu hatayı düzeltmek için ilke Oluşturucusu .dll içinde güncelleştirme *C:\Program Files\Microsoft Visual Studio 8\Team Tools\Static analiz Tools\FxCop\Rules\\*  bilgisayarlarında dizin.  
  
   **'{0}' ilkesinde belirtilen derleme yok.**  
  
   Bu hata, .NET projelerine yöneliktir. Kod Analizi İlkesi tarafından gerekli bir kural, istemci bilgisayarda yüklü karşılık gelen dll yok. Bu hatayı düzeltmek için ilke Oluşturucu DLL'de güncelleştirmeniz gerekir *C:\Program Files\Microsoft Visual Studio 8\Team Tools\Static analiz Tools\FxCop\Rules\\*  bilgisayarlarında dizin.  
  
   **Proje {0} kural ayarları olmayan kod analizi İlkesi ile uyum içinde.**  
  
   Bu hata, .NET projelerine yöneliktir. Yönetilen kod kuralları ayarları İlkesi gerektirdiği katı değil. Bu hatayı düzeltmek için istemci ayarı aynı olmalıdır veya sunucu üzerindeki ilke gereksinimi öğesinden daha katıdır.  
  
   **Kod Analizi etkin yapılandırma üzerinde etkin değil. Geçiş için yapılandırma {0} ve proje {1} iade etmeden önce.**  
  
   İçinde [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]etkin yapılandırmayı Kod Analizi etkin olmayan, ancak en az bir kod analizi Etkin yoktur.  
  
   **Proje içinde yönetilen ikililer için kod analizini etkinleştir {0} özellikleri ve iade etmeden önce derleme.**  
  
   Bu hata uygulandığı [!INCLUDE[vcprvc](../includes/vcprvc-md.md)] .NET uygulamaları. Gerçekleştirilecek yönetilen kod analizi İlkesi gerektiriyor, ancak istemcide geçerli projede etkin değil.  
  
   **Projede kod analizini etkinleştir {0} özellikleri ve iade etmeden önce derleme.**  
  
   Bu hata için uygulanan [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] projeleri ve Web projeleri. Gerçekleştirilecek yönetilen kod analizi İlkesi gerektiriyor, ancak istemcide geçerli projede etkin değil.  
  
   **C/C++ Kod Analizi projede etkinleştirmelisiniz {0} özellikleri ve iade etmeden önce derleme.**  
  
   Bu hata, yönetilmeyen projeler için geçerlidir. Kod Analizi İlkesi C/C++ için Kod Analizi gerektirir, ancak istemcide geçerli projede etkin değil.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Kod Çözümleme Uygulama Hataları](../code-quality/code-analysis-application-errors.md)



