---
title: CD yüklemeleri için AutoStart 'ı etkinleştirme | Microsoft Docs
description: Bir ClickOnce uygulamasını, CD-ROM veya DVD-ROM gibi çıkarılabilir medya aracılığıyla dağıttığınızda otomatik başlatmayı nasıl etkinleştirebileceğinizi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, AutoStart
- ClickOnce deployment, installation on CD or DVD
- deploying applications [ClickOnce], installation on CD or DVD
ms.assetid: caaec619-900c-4790-90e3-8c91f5347635
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: b157df8666223e72a1e36d58505a5c087b0351bf
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99900678"
---
# <a name="how-to-enable-autostart-for-cd-installations"></a>Nasıl yapılır: CD yüklemeleri için AutoStart 'ı etkinleştirme
[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]Uygulama, CD-ROM veya DVD-ROM gibi çıkarılabilir medya aracılığıyla dağıtıldığında, `AutoStart` [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] medya takıldığında uygulamanın otomatik olarak başlatılmasını sağlayabilirsiniz.

 `AutoStart`, **Proje Tasarımcısı**' nın **Yayımla** sayfasında etkinleştirilebilir.

### <a name="to-enable-autostart"></a>AutoStart 'ı etkinleştirmek için

1. **Çözüm Gezgini**' de bir proje seçiliyken, **Proje** menüsünde **Özellikler**' e tıklayın.

2. **Yayımla** sekmesine tıklayın.

3. **Seçenekler** düğmesine tıklayın.

     **Yayımlama seçenekleri** iletişim kutusu görüntülenir.

4. **Dağıtım**' ye tıklayın.

5. CD **takıldığında kurulumu otomatik olarak Başlat** onay kutusunu seçin.

     Uygulama yayımlandığında bir *Autorun. inf* dosyası yayımlama konumuna kopyalanır.

## <a name="see-also"></a>Ayrıca bkz.
- [ClickOnce uygulamalarını yayımlama](../deployment/publishing-clickonce-applications.md)
- [Nasıl yapılır: yayımlama sihirbazını kullanarak ClickOnce uygulaması yayımlama](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)