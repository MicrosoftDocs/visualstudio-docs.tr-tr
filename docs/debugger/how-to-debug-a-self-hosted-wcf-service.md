---
title: Self-Hosted WCF hizmetinde hata ayıklama | Microsoft Docs
description: Şirket içinde barındırılan bir WCF hizmetinde hata ayıklamayı öğrenin. En kolay yol (ancak her zaman mümkün değildir), Visual Studio 'Yu hem istemci hem de sunucu başlatılacak şekilde yapılandırmaktır.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging, WCF
- WCF, self-hosted service
- WCF, debugging
ms.assetid: 288922be-ba3f-411e-af50-bba39c9529cc
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 3cd11966347cd90576eb78a59f6c7eb96cc697ef
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102155087"
---
# <a name="how-to-debug-a-self-hosted-wcf-service"></a>Nasıl Yapılır: Kendini Barındıran WCF Hizmetinde Hata Ayıklama
*Şirket içinde barındırılan bir hizmet* , IIS 'de, WCF hizmeti ana bilgisayarında veya geliştirme sunucusunda ÇALıŞTıRMAYAN bir WCF hizmetidir [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] . Şirket içinde barındırılan bir WCF 'yi hata ayıklamanın en kolay yolu, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] **hata** ayıklama menüsünde **hata ayıklamayı Başlat** ' ı seçtiğinizde hem istemciyi hem de sunucuyu başlatacak şekilde yapılandırmaktır.

 WCF hizmeti içinde kendiliğinden barındırılsa veya NT hizmeti gibi bu şekilde başlatılabilen bir işlem ise, bu yöntemi kullanamazsınız. Bunun yerine, aşağıdakilerden birini yapabilirsiniz:

- Hata ayıklayıcıyı barındırma işlemine el ile ekleyin. Daha fazla bilgi için bkz. [çalışan Işlemlere iliştirme](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).

     veya

- İstemcide hata ayıklamayı başlatın ve ardından hizmete bir çağrı yapın. Bu, app.config dosyasında hata ayıklamayı etkinleştirmenizi gerektirir. Daha fazla bilgi için [WCF hata ayıklama sınırlamaları](../debugger/limitations-on-wcf-debugging.md).

### <a name="to-start-both-client-and-host-from-visual-studio"></a>Hem istemciyi hem de Konağı Visual Studio 'dan başlatmak için

1. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]Hem istemci hem de sunucu projelerini içeren bir çözüm oluşturun.

2. **Hata ayıklama** menüsünde **Başlat** ' ı seçtiğinizde, çözümü hem istemci hem de sunucu işlemlerini başlatacak şekilde yapılandırın.

   1. **Çözüm Gezgini**, çözüm adına sağ tıklayın.

   2. **Başlangıç projelerini ayarla**' ya tıklayın.

   3. **Çözüm \<name> özellikleri** Iletişim kutusunda **birden çok başlangıç projesi**' ni seçin.

   4. **Birden çok başlangıç projesi** kılavuzunda, sunucu projesine karşılık gelen satırda **eylem** ' e tıklayın ve **Başlat**' ı seçin.

   5. İstemci projesine karşılık gelen satırda **eylem** ' e tıklayın ve **Başlat**' ı seçin.

   6. **Tamam**'a tıklayın.

## <a name="see-also"></a>Ayrıca bkz.
- [WCF Hizmetlerinde Hata Ayıklama](../debugger/debugging-wcf-services.md)
- [WCF hata ayıklama sınırlamaları](../debugger/limitations-on-wcf-debugging.md)
- [Nasıl yapılır: WCF hizmetlerine adımla](../debugger/how-to-step-into-wcf-services.md)
