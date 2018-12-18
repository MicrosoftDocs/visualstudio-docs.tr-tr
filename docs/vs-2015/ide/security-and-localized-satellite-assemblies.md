---
title: Güvenlik ve yerelleştirilmiş yardımcı derlemeler | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
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
caps.latest.revision: 9
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: d817569a5f6709794b452fb5efe38d584669033f
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49218653"
---
# <a name="security-and-localized-satellite-assemblies"></a>Güvenlik ve Yerleştirilmiş Yardımcı Derlemeler
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ana derlemenizin güçlü adlandırma kullanıyorsa, uydu derlemeleri ana derleme olarak aynı özel anahtarla oturum açmanız gerekir. Ortak/özel anahtar çifti eşleşmiyor ana ve yardımcı derlemeler, kaynaklarınız arasında yüklü değil ise. Derlemeleri imzalama hakkında daha fazla bilgi için bkz. [nasıl yapılır: bir derlemeyi tanımlayıcı bir adla imzalamak](http://msdn.microsoft.com/library/2c30799a-a826-46b4-a25d-c584027a6c67).  
  
 Genel olarak, kuruluşunuzun imzalama grubu veya özel anahtarla oturum dış imzalama kuruluş olması gerekebilir. Özel anahtarı hassas niteliği nedeniyle budur: erişimi kısıtlıdır genellikle birkaç kişi için. Geliştirme sırasında Gecikmeli imzalama kullanabilirsiniz. Daha fazla bilgi için [derlemeyi imzalamayı geciktirme](http://msdn.microsoft.com/library/9d300e17-5bf1-4360-97da-2aa55efd9070).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Derleme güvenliği konuları](http://msdn.microsoft.com/library/1b5439c1-f3d5-4529-bd69-01814703d067)   
 [Temel güvenlik kavramları](http://msdn.microsoft.com/library/3cfced4f-ea02-4e66-ae98-d69286363e98)   
 [.NET Framework tabanlı Uluslararası uygulamalara giriş](../ide/introduction-to-international-applications-based-on-the-dotnet-framework.md)   
 [Uygulamaları yerelleştirme](../ide/localizing-applications.md)   
 [Uygulamaları Genelleştirme ve Yerelleştirme](../ide/globalizing-and-localizing-applications.md)

