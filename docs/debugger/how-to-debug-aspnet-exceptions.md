---
title: 'Nasıl yapılır: ASP.NET özel durumlarında hata ayıklama | Microsoft Docs'
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
- debugging [Visual Studio], ASP.NET exceptions
- ASP.NET, exceptions
- exceptions, ASP.NET
ms.assetid: 1810096e-de8c-435e-be3d-f365d0cd0a6a
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- aspnet
ms.openlocfilehash: 5923818e93170ded1f857ac20d42cd6134aed5d3
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2018
ms.locfileid: "31476162"
---
# <a name="how-to-debug-aspnet-exceptions"></a>Nasıl Yapılır: ASP.NET Özel Durumlarında Hata Ayıklama
Özel durumlar hata ayıklama, sağlam bir geliştirme önemli bir bölümü değildir [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] uygulama. Özel durumlar hata ayıklama hakkında genel bilgi olduğuna [yönetme özel durumları hata ayıklayıcısı ile](../debugger/managing-exceptions-with-the-debugger.md).  
  
 Hata ayıklama için işlenmemiş [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] özel durumlar, hata ayıklayıcı bunları durdurur emin olmalısınız. [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Çalışma zamanı sahip bir üst düzey özel durum işleyicisi. Bu nedenle, hata ayıklayıcı varsayılan olarak hiçbir zaman işlenmeyen özel durumları keser. Bir özel durum oluştuğunda hata ayıklayıcısında araya girmektir için seçmelisiniz **bölün bir özel durum olduğunda: durum** , bir özel durum ayarını **özel durumları** iletişim kutusu.  
  
 Sadece kendi kodumu etkinleştirilirse **bölün bir özel durum olduğunda: durum** .NET Framework yöntemi veya başka bir sistem kod bir özel durum, hemen ayırmak hata ayıklayıcı neden olmaz. Sistem dışı kodu, hata ayıklayıcı isabetler kadar bu keser sonra bunun yerine, yürütme devam eder. Sonuç olarak, yüklü bir özel durum oluştuğunda sistem kodlarda adıma.  
  
 Sadece kendi kodumu daha yararlı olabilecek başka bir seçenek sağlar: **bir özel durum olduğunda Kes: kullanıcının işlemediği**. Bir özel durum için bu ayarı seçerseniz, hata ayıklayıcı ancak özel durum yakalandı değil ve kullanıcı kodu tarafından işlenen kullanıcı kodu yürütme kesintiye uğrar. Bu ayar üzerindeki etkisini, üst düzey geçersiz kılar [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] özel durum işleyicisi, bu işleyici kullanıcı olmayan kodda olduğundan.  
  
### <a name="to-enable-debugging-of-aspnet-exceptions-with-just-my-code"></a>ASP.NET özel durumlarının sadece kendi kodumu ile hata ayıklamayı etkinleştirmek için  
  
1.  Üzerinde **hata ayıklama** menüsünde tıklatın **özel durumları**.  
  
     **Özel durumları** iletişim kutusu görüntülenir.  
  
2.  Üzerinde **ortak dil çalışma zamanı özel durumları** satır, select **sayıcı** veya **kullanıcı işlenmemiş**.  
  
     Kullanılacak **kullanıcı işlenmemiş** ayarı **sadece kendi kodumu** etkinleştirilmelidir...  
  
### <a name="to-use-best-practices-for-aspnet-exception-handling"></a>ASP.NET özel durum işleme için en iyi uygulamaları kullanmak için  
  
-   Yer `try ... catch` geçici özel durumlar oluşturan kod blokları düşündüğünüz ve nasıl ele alınacağını bildikleri. Uygulama çağrıları XML Web hizmeti veya doğrudan bir SQL Server değiştirirken, örneğin, bu kodu bulunmalıdır **try... catch** oluşabilecek çeşitli özel durumlar olduğundan engeller.

## <a name="see-also"></a>Ayrıca Bkz.
[ASP.NET uygulamalarında hata ayıklama](../debugger/how-to-enable-debugging-for-aspnet-applications.md)