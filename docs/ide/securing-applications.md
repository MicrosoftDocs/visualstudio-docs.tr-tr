---
title: Güvenlik
ms.date: 06/01/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- security [Visual Studio], applications
- application design, securability
ms.assetid: 7d32c4cf-8bec-4307-a2a8-42f0ceddf3eb
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 87e9cb7e9400253713caab17da04c44eb11f5ed1
ms.sourcegitcommit: ce154aee5b403d5c1c41da42302b896ad3cf8d82
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/07/2018
ms.locfileid: "34843916"
---
# <a name="secure-applications"></a>Uygulamaları güvenli hale getirme

Uygulama geliştirme sürecinizde, tasarımdan geliştirmeye kadar her yönüyle güvenliği göz önünde bulundurmalısınız. Visual Studio mümkün olduğunca güvenli bir şekilde çalıştırarak başlayın. Bkz: [kullanıcı izinleri](../ide/user-permissions-and-visual-studio.md).

Etkin bir şekilde güvenli uygulamalar geliştirmenize yardımcı olması için, geliştirmekte olduğunuz platformların güvenlik kavramları ve güvenlik özellikleri hakkında temel bilgiye sahip olmanız gerekir. Güvenli kodlama tekniklerini de anlamanız gerekir.

## <a name="code-for-security"></a>Kod güvenliği

Güvenlik açıklarına neden çoğu kodlama hataları kullanıcı girişi ile çalışırken, geliştiricilerin yanlış varsayımlar olun çünkü ya da, bunlar geliştirirken platform tam olarak anlamadığınız nedeniyle oluşur.

- [Güvenli kodlama yönergeleri](/dotnet/standard/security/secure-coding-guidelines) .NET kodu güvenlik sistemi ile çalışmak için tasarlanmış farklı yolları açıklanmaktadır.
- [C++ için en iyi yöntemler](/cpp/top/security-best-practices-for-cpp) C++ geliştiricileri için güvenlik araçları ve yöntemleri hakkında bilgi içerir.

## <a name="build-for-security"></a>Güvenlik için derleme

Güvenlik de önemli bir yapı işlemine konudur. Bazı ek adımlar, dağıtılmış bir uygulamayı güvenliğini artırmak ve yetkisiz ters mühendislik, yanıltma veya diğer saldırılara önlemeye yardımcı olur:

- [Dotfuscator](dotfuscator/index.md) ücretsizdir ve .NET derlemelerini yetkisiz hata ayıklama gibi ters mühendislik ve yetkisiz kullanıma karşı korunmasına yardımcı olur.
- [Tanımlayıcı ad imzası](managing-assembly-and-manifest-signing.md) benzersiz olarak yazılım bileşenlerini belirlemek ve adına kimlik sahtekarlığı önlemek için kullanılabilir.

## <a name="see-also"></a>Ayrıca bkz.

- [.NET Framework güvenliği](/dotnet/standard/security/index)
- [Azure güvenlik](/azure/security/)
- [Windows 10 Mobile Güvenlik Kılavuzu](/windows/security/threat-protection/windows-10-mobile-security-guide)
- [Apache Cordova platform güvenlik özellikleri](/visualstudio/cross-platform/tools-for-cordova/security/best-practices?view=toolsforcordova-2017)
- [ASP.NET Core güvenlik](/aspnet/core/security/?view=aspnetcore-2.1)
- [Windows Forms güvenliği](/dotnet/framework/winforms/windows-forms-security)