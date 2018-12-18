---
title: Güvenlik
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
- code access security, coding errors
- security [.NET Framework], about security
ms.assetid: 318c34ce-f643-468c-83a1-843196f5d845
caps.latest.revision: 24
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: ae5db15fda1914d52be192a516d70704d2ad3cf6
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53061752"
---
# <a name="security-in-visual-studio"></a>Visual Studio'da Güvenlik
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Uygulama geliştirme sürecinizde, tasarımdan geliştirmeye kadar her yönüyle güvenliği göz önünde bulundurmalısınız. Visual Studio mümkün olduğunca güvenli bir şekilde çalıştırarak başlayın. Bkz: [kullanıcı izinleri](../ide/user-permissions-and-visual-studio.md).

 Etkin bir şekilde güvenli uygulamalar geliştirmenize yardımcı olması için, geliştirmekte olduğunuz platformların güvenlik kavramları ve güvenlik özellikleri hakkında temel bilgiye sahip olmanız gerekir. Güvenli kodlama tekniklerini de anlamanız gerekir.

## <a name="understanding-security"></a>Güvenliği Anlama
 [Güvenlik](http://msdn.microsoft.com/library/9a9621d7-8883-4a4f-a874-65e8e09e20a6) açıklar .NET Framework kod erişim güvenliği, rol tabanlı güvenlik, güvenlik ilkesi ve güvenlik araçları.

 [İlk on güvenlik ipuçları her geliştirici bilmeniz gerekir ile kodunuzu koruyun](http://go.microsoft.com/fwlink/?LinkId=72877) için düşmemesi ve böylece, verileriniz veya sisteminizin güvenliğinin tehlikeye sorunları açıklar.

## <a name="coding-for-security"></a>Güvenlik İçin Kodlama
 Güvenlik açıklarına neden olan çoğu kodlama hatası, geliştiricilerin kullanıcı girdisiyle çalışırken yanlış varsayımlarda bulunmaları veya uygulama geliştirdikleri platformu tam olarak anlamamaları yüzünden meydana gelir.

 [Güvenli kodlama yönergeleri](http://msdn.microsoft.com/library/4f882d94-262b-4494-b0a6-ba9ba1f5f177) güvenlik sorunlarını gidermek için bileşenlerinizin sınıflandırılmasına için yönergeler sağlar.

 [En iyi güvenlik uygulamaları](http://msdn.microsoft.com/library/86acaccf-cdb4-4517-bd58-553618e3ec42) /GS derleme zamanı bayrağı tarafından sağlanan özellik Discusses arabellek taşmalarını ve Microsoft Visual C++ güvenlik eksiksiz bir görünümünü denetler.
