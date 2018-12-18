---
title: 'Nasıl yapılır: ASP.NET özel durumlarında hata ayıklama | Microsoft Docs'
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
- debugging [Visual Studio], ASP.NET exceptions
- ASP.NET, exceptions
- exceptions, ASP.NET
ms.assetid: 1810096e-de8c-435e-be3d-f365d0cd0a6a
caps.latest.revision: 26
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3d505e67018c24f659e88401b565011a4c7bea96
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51789219"
---
# <a name="how-to-debug-aspnet-exceptions"></a>Nasıl Yapılır: ASP.NET Özel Durumlarında Hata Ayıklama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Özel durumların hatalarının ayıklanması, güçlü bir geliştirme önemli bir parçası olduğu [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] uygulama. Özel durumları hata ayıklama hakkında genel bilgilerine [yönetme özel durumları hata ayıklayıcısı ile](../debugger/managing-exceptions-with-the-debugger.md).  
  
 Hata ayıklamak için işlenmemiş [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] özel durumları, hata ayıklayıcının onlar için durduğundan emin olmalısınız. [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] Çalışma zamanı bir üst düzey özel durum işleyicisine sahiptir. Bu nedenle, hata ayıklayıcı varsayılan olarak hiçbir zaman işlenmeyen özel durumları keser. Bir özel durum oluştuğunda hata ayıklayıcıyı durdurmak için seçmelisiniz **bir özel durum olduğunda Kes: oluşan** o özel duruma ayarını **özel durumları** iletişim kutusu.  
  
 Yalnızca kendi Kodum'u etkinleştirdiyseniz **bir özel durum olduğunda Kes: oluşan** hata ayıklayıcının .NET Framework yöntemi veya başka bir sistem kodunda özel durum oluşturulursa hemen kesilmesine neden olmaz. Sistem dışı kod hata ayıklayıcı sayısına ulaşana kadar bu keser sonra bunun yerine, yürütme devam eder. Sonuç olarak, yüklü bir özel durum oluştuğunda sistem kodu boyunca adım adım.  
  
 Yalnızca kendi kodum daha yararlı olabilecek başka bir seçenek sağlar: **bir özel durum olduğunda Kes: kullanıcı işlenmemiş**. Bir özel durum için bu ayarı seçerseniz, hata ayıklayıcı, ancak özel durum yakalanıp işlenmezse kullanıcı kodu tarafından işlenen, yalnızca kullanıcı kodunda yürütmeyi keser. Bu ayar etkisini en üst düzey verilerek [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] özel durum işleyicisi, o işleyicisi kullanıcı dışındaki kodda olduğundan.  
  
### <a name="to-enable-debugging-of-aspnet-exceptions-with-just-my-code"></a>ASP.NET özel durumlarında yalnızca kendi kodum ile hata ayıklamayı etkinleştirmek için  
  
1.  Üzerinde **hata ayıklama** menüsünde tıklatın **özel durumları**.  
  
     **Özel durumları** iletişim kutusu görüntülenir.  
  
2.  Üzerinde **ortak dil çalışma zamanı özel durumları** satır, select **sayıcı** veya **kullanıcı-işlenmemiş**.  
  
     Kullanılacak **kullanıcı-işlenmemiş** ayarını **yalnızca kendi kodum** etkinleştirilmesi gerekir...  
  
### <a name="to-use-best-practices-for-aspnet-exception-handling"></a>ASP.NET özel durum işleme için en iyi uygulamaları kullanmak için  
  
-   Bir yerde `try … catch` geçici özel durumlar atabilen kod blokları, tahmin ve nasıl işleyeceğini bilen. Bir XML Web hizmetine veya doğrudan bir SQL Server uygulama çağrıları yapıyor, örneğin, kod içinde olmalıdır **try... catch** oluşabilecek çok sayıda özel durum olduğundan engeller.



