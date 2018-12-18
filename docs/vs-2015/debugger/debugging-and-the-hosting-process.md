---
title: Hata ayıklama ve barındırma işlemi | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], hosting process
- hosting process
ms.assetid: d0f0b9a6-2a6e-463d-b6ea-9518ee727933
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8932f3edd1b51ad61293bbce716aa76944e23274
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51762352"
---
# <a name="debugging-and-the-hosting-process"></a>Hata Ayıklama ve Barındırma İşlemi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio barındırma işlemini, hata ayıklayıcı performansı artırır ve kısmi güven hata ayıklama ve tasarım zamanı ifade değerlendirmesi gibi yeni hata ayıklayıcı özelliklerini etkinleştirir. Gerekirse, barındırma işlemini devre dışı bırakabilirsiniz. Daha fazla bilgi için [nasıl yapılır: barındırma sürecini devre dışı bırakma](../ide/how-to-disable-the-hosting-process.md). Aşağıdaki bölümlerde, barındırma işlemi olmadan ve hata ayıklama arasındaki bazı farklar açıklanmaktadır.  
  
## <a name="partial-trust-debugging-and-click-once-security"></a>Kısmi güven hata ayıklama ve tıklayın-bir kez güvenlik  
 Kısmi güven hata ayıklama barındırma işlemini gerektiriyor. Barındırma işlemini devre dışı bırakırsanız, kısmi güven güvenliği etkinleştirilmiş olsa dahi kısmi güven hata ayıklama çalışmaz **güvenlik** sayfasının **proje özellikleri**. Daha fazla bilgi için [nasıl yapılır: barındırma sürecini devre dışı bırakma](../ide/how-to-disable-the-hosting-process.md) ve [nasıl yapılır: bir kısmi güven uygulamasında hata ayıklama](../debugger/how-to-debug-a-partial-trust-application.md).  
  
## <a name="design-time-expression-evaluation"></a>Tasarım zamanı ifade değerlendirmesi  
 Tasarım zamanı ifade her zaman, barındırma işlemi kullanır. Barındırma devre dışı bırakma işlemi **proje özellikleri** sınıf kitaplığı projeleri için tasarım zamanı ifade değerlendirmesi devre dışı bırakır. Diğer proje türleri için tasarım zamanı ifade değerlendirmesi devre dışı değil. Bunun yerine, Visual Studio gerçek yürütülebilir başlar ve barındırma işlemi olmadan tasarım zamanı değerlendirmesi için kullanır. Bu fark, farklı sonuçlar üretebilir.  
  
## <a name="appdomaincurrentdomainfriendlyname-differences"></a>AppDomain.CurrentDomain.FriendlyName farkları  
 `AppDomain.CurrentDomain.FriendlyName` barındırma işlemi etkin olup olmadığını bağlı olarak farklı sonuçlar döndürür. Eğer `AppDomain.CurrentDomain.FriendlyName` barındırma işlemi etkin döndürür *app_name*`.vhost.exe`. Bunu devre dışı barındırma işlemini çağırdığınızda, döndürür *app_name*`.exe`.  
  
## <a name="assemblygetcallingassemblyfullname-differences"></a>Assembly.GetCallingAssembly(). FullName farkları  
 `Assembly.GetCallingAssembly().FullName` barındırma işlemi etkin olup olmadığını bağlı olarak farklı sonuçlar döndürür. Eğer `Assembly.GetCallingAssembly().FullName` barındırma işlemi etkin döndürür `mscorlib`. Eğer `Assembly.GetCallingAssembly().FullName` barındırma işlemini devre dışı uygulama adını döndürür.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Barındırma süreci (vshost.exe)](../ide/hosting-process-vshost-exe.md)   
 [Nasıl yapılır: kısmen güvenilen uygulamada hata ayıklama](../debugger/how-to-debug-a-partial-trust-application.md)   
 [Nasıl Yapılır: Barındırma Sürecini Devre Dışı Bırakma](../ide/how-to-disable-the-hosting-process.md)



