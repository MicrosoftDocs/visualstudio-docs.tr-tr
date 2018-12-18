---
title: 'DA0007: denetim akışı için özel durumlar kullanmaktan kaçının. | Microsoft Docs'
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
- vs.performance.rules.DAExceptionsThrown
- vs.performance.7
- vs.performance.rules.DA0007
- vs.performance.DA0007
ms.assetid: ee8ba8b5-2313-46c9-b129-3f3a2a232898
caps.latest.revision: 18
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a86c36c55d11f91daff8e876e852daed2f222307
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51737094"
---
# <a name="da0007-avoid-using-exceptions-for-control-flow"></a>DA0007: Denetim akışı için özel durumlar kullanmaktan kaçının
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Kural Kimliği | DA0007 |  
| Kategori |. NET Framework kullanım |  
| Profil oluşturma yöntemlerini | Tüm |  
| İleti | Çok sayıda özel durumları tutarlı bir şekilde oluşturuldu. Program mantığında özel durumların kullanımını azaltmayı deneyin. |  
| İleti türü | Uyarı |  
  
 Örnekleme, .NET bellek ve kaynak çekişmesi yöntemleri kullanılarak profili, bu kural tetiklemek için en az 25 örnekleri toplamanız gerekir.  
  
## <a name="cause"></a>Sebep  
 Yüksek oranda .NET Framework özel durum işleyicileri profil oluşturma verileri adı veriliyordu. Oluşan özel durumların sayısını azaltmak için başka bir denetim akışı mantığı kullanmayı düşünün.  
  
## <a name="rule-description"></a>Kural Tanımı  
 Hataları ve program yürütme kesintiye diğer olayları yakalamak için özel durum işleyicileri kullanımını iyi olsa da, normal program yürütme mantığının parçası olarak özel durum işleyicisi kullanımını pahalı olabilir ve kaçınılmalıdır. Çoğu durumda, özel durum nadiren oluşur ve değil beklendiği durumlar için kullanılması gereken... Özel durumlar programın normal akışının bir parçası değer döndürmek için kullanılmamalıdır. Çoğu durumda, değerler doğrulanıyor ve soruna neden deyimleri yürütülmesini durdurmak için koşullu mantığı kullanarak özel durumlarını oluşturma önleyebilirsiniz.  
  
 Daha fazla bilgi için bkz [özel durum yönetimi](http://go.microsoft.com/fwlink/?LinkID=177825) bölümünü **bölüm 5: yönetilen kod performansını iyileştirme** içinde **geliştirme .NET uygulama performansı ve ölçeklenebilirlik** hacmi **Microsoft Patterns and Practices** MSDN Kitaplığı.  
  
## <a name="how-to-investigate-a-warning"></a>Bir uyarı araştırma  
 İleti Hata Listesi penceresindeki işaretleri görünümüne gitmek için çift tıklayın. İçeren bir sütun Bul **.NET CLR özel durumları (@ProcessInstance)\\atılan / sn** ölçümleri. Varsa belirli aşamaları program yürütmenin özel durum işleme diğerlerinden daha sık olduğu belirleyin. Throw deyimleri tanımlamak ve try/catch blokları sık karşılaşılan özel durumların üreten bir örnekleme profili kullanarak deneyin. Gerekirse, catch blokları hangi özel durumları en sık işlenen anlamanıza yardımcı olması için mantık ekleyin. Mümkünse, sık yürütülen Değiştir throw deyimleri ya da basit bir akış ile catch blokları mantığı veya doğrulama kodunu denetleyin.  
  
 Örneğin, uygulamanızı Bul çıkacaksa sıfır değerleri olan kesirler denetlemek için program mantığını uygulamanın performansını artıracak ekleme sık DivideByZeroException özel durumları, işleme oluştu.



