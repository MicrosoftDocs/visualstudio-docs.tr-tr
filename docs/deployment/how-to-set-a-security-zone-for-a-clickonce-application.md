---
title: 'Nasıl yapılır: ClickOnce uygulaması için bir güvenlik bölgesi ayarlama | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, security settings
- code access security, ClickOnce applications
- security zones, ClickOnce applications
ms.assetid: d3dac454-518a-44d7-a76e-ccb7b9c3a150
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1b2155cb36a2538bd93c48ccda1f2c93b0876b95
ms.sourcegitcommit: 8ee7efb70a1bfebcb6dd9855b926a4ff043ecf35
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/17/2018
ms.locfileid: "39077733"
---
# <a name="how-to-set-a-security-zone-for-a-clickonce-application"></a>Nasıl yapılır: ClickOnce uygulaması için bir güvenlik bölgesi ayarlama
Temel bir izin kümesi ile başlatmak gereken kod erişim güvenlik izinlerini ClickOnce uygulaması için ayarladığınızda, **güvenlik** sayfasının **Proje Tasarımcısı**.  
  
 Çoğu durumda, ayrıca seçebilirsiniz **Internet** sınırlı bir izin kümesi içeren bir bölge veya **yerel Intranet** büyük bir izin kümesi içeren bir bölge. Uygulamanız özel izinleri gerektiriyorsa, bunu seçerek yapabilirsiniz **özel** güvenlik bölgesi. Özel izinleri ayarlama hakkında daha fazla bilgi için bkz: [nasıl yapılır: ClickOnce uygulaması için özel izinleri ayarlama](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md).  
  
### <a name="to-set-a-security-zone"></a>Bir güvenlik bölgesi ayarlama  
  
1.  Seçili bir projeyle **Çözüm Gezgini**, **proje** menüsünü tıklatın **özellikleri**.  
  
2.  Tıklayın **güvenlik** sekmesi.  
  
3.  Seçin **ClickOnce güvenlik ayarlarını etkinleştirme** onay kutusu.  
  
4.  Seçin **kısmi güven uygulamasıdır** seçenek düğmesini.  
  
     Denetimlerde **ClickOnce güvenlik izinleri** bölüm etkinleştirilir.  
  
5.  İçinde **uygulamanızı yükleneceği kaynak bölge** aşağı açılan listesinde, bir güvenlik bölgesi seçin.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Nasıl yapılır: ClickOnce uygulaması için özel izinleri ayarlama](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md)   
 [ClickOnce uygulamalarının güvenliğini sağlama](../deployment/securing-clickonce-applications.md)   
 [ClickOnce uygulamaları için kod erişimi güvenliği](../deployment/code-access-security-for-clickonce-applications.md)   
