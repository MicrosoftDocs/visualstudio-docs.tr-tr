---
title: ClickOnce önbelleğine genel bakış | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- Windows applications, ClickOnce deployemtn
- ClickOnce applications, cache
- ClickOnce deployment, cache
ms.assetid: e379921e-9ef1-4326-bbf3-53ba67925526
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d846ec60f6cf1722584c4ea93c56c29bc7007b89
ms.sourcegitcommit: 8ee7efb70a1bfebcb6dd9855b926a4ff043ecf35
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/17/2018
ms.locfileid: "39077626"
---
# <a name="clickonce-cache-overview"></a>ClickOnce önbelleğine genel bakış
Tüm [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] uygulamaları, yerel olarak yüklü veya çevrimiçi barındırılan depolanır istemci bilgisayarda bir [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]uygulama *önbellek*. A [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Documents and Settings klasörü geçerli kullanıcının yerel ayarlarını dizininin altında gizli dizinler ailesinin bir önbellektir. Bu önbellek, derlemeleri, yapılandırma dosyaları, uygulama ve kullanıcı ayarlarını ve veri dizini gibi uygulamanın tüm dosyaları içerir. Önbellek, uygulamanın veri dizini en son sürüme geçirmek için sorumludur. Veri geçişi hakkında daha fazla bilgi için bkz. [erişen yerel ve uzak veri ClickOnce uygulamalarında](../deployment/accessing-local-and-remote-data-in-clickonce-applications.md).  
  
 Uygulama depolaması için tek bir konum sağlayarak [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] kullanıcıdan uygulamanın fiziksel yükleme yönetme görevini kazanır. Önbelleğe derlemeler ve veri dosyaları için tüm uygulamaları otomatik olarak kilitlenmesini sağlayarak uygulamalarını yalıtmak da yardımcı olur ve farklı sürümlerine birbirinden ayırın. Örneğin, yükseltme yaptığınızda bir [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] uygulama sürümü ve veri kaynaklarıyla önbelleğinde kendi dizinlerle sağlanır.  
  
## <a name="cache-storage-quota"></a>Önbellek depolama kotası  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Çevrimiçi barındırılan uygulamalar olunabilecek boşluk boyutunu sınırlayan bir kota tarafından kısıtlı [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] önbellek. Önbellek boyutu, kullanıcının tüm çevrimiçi uygulamalar için geçerlidir; tek bir kısmen güvenilen, çevrimiçi uygulama yarısı kota alanı kaplayan sınırlıdır. Yüklü uygulamalar, önbellek boyutuyla sınırlı değildir ve önbellek sınırınızı sayılmaz. Tüm [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] uygulamalar, önbelleğe yalnızca geçerli sürümü ve daha önce yüklü olan sürümü korur.  
  
 Çevrimiçi 250 MB depolama alanı için varsayılan olarak, istemci bilgisayarlara sahip [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] uygulamalar. Veri dosyaları, bu sınır içinde sayılmaz. Bir Sistem Yöneticisi büyütebilir veya kayıt defteri anahtarını değiştirerek belirli bir istemci bilgisayar üzerinde bu kotayı azaltmak **HKEY_CURRENT_USER\Software\Classes\Software\Microsoft\Windows\CurrentVersion\Deployment\OnlineAppQuotaInKB**, önbellek boyutu kilobayt cinsinden ifade bir DWORD değeri olduğu. Örneğin, 50 MB önbellek boyutunu azaltmak amacıyla, bu değer 51200 yapmanız gerekir.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [ClickOnce uygulamalarında yerel ve uzak veri erişimi](../deployment/accessing-local-and-remote-data-in-clickonce-applications.md)