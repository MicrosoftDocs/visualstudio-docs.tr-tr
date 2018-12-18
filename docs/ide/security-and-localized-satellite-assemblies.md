---
title: Güvenlik ve Yerleştirilmiş Yardımcı Derlemeler
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- key pairs for strong-named assemblies
- strong-named assemblies, security considerations
- satellite assemblies, localized
- code signing, assemblies
- security [Visual Studio], assemblies
- strong-named assemblies, localized
- assemblies [Visual Studio], security
- localization, satellite assemblies
ms.assetid: 6d953840-b301-47d5-8d34-30c1b29b5071
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b7eb391f01bc5a709aeaf0002ac647c358355e5f
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/26/2018
ms.locfileid: "31943754"
---
# <a name="security-and-localized-satellite-assemblies"></a>Güvenlik ve Yerleştirilmiş Yardımcı Derlemeler

Ana derleme güçlü adlandırma kullanıyorsa, uydu derlemeleri ana derlemeyle aynı özel anahtar ile imzalanmalıdır. Ortak/özel anahtar çifti eşleşmiyor ana ve uydu derlemelerini, kaynaklarınız arasında yüklü değil İmzalama derlemeler hakkında daha fazla bilgi için bkz: [nasıl yapılır: bir derlemeyi tanımlayıcı adla oturum](/dotnet/framework/app-domains/how-to-sign-an-assembly-with-a-strong-name).

 Genel olarak, kuruluşunuzun imzalama grubu veya özel anahtar ile oturum açma dış imzalama kuruluş olması gerekebilir. Özel anahtarı hassas yapısı nedeniyle budur: erişim kısıtlıdır genellikle birkaç kişi. Geliştirme sırasında Gecikmeli imzalama kullanabilirsiniz. Daha fazla bilgi için bkz: [Gecikmeli bir derleme imzalama](/dotnet/framework/app-domains/delay-sign-assembly).

## <a name="see-also"></a>Ayrıca bkz.

- [Derleme güvenliği konuları](/dotnet/framework/app-domains/assembly-security-considerations)  - [anahtar güvenlik kavramları](/dotnet/standard/security/key-security-concepts)
- [.NET Framework Tabanlı Uluslararası Uygulamalara Giriş](../ide/introduction-to-international-applications-based-on-the-dotnet-framework.md)
- [Uygulamaları Yerelleştirme](../ide/localizing-applications.md)
- [Uygulamaları Genelleştirme ve Yerelleştirme](../ide/globalizing-and-localizing-applications.md)