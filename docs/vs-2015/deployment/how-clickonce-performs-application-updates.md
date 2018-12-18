---
title: ClickOnce uygulama güncelleştirmelerini nasıl gerçekleştirir | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-deployment
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- updates, ClickOnce
- ClickOnce deployment, updates
- deploying applications [ClickOnce], application updates
ms.assetid: d54313c2-cf0c-420d-b151-99953a95f0bb
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: 5c2e135a2b872ecd389149626ac09caf02734f40
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49298031"
---
# <a name="how-clickonce-performs-application-updates"></a>ClickOnce Uygulama Güncelleştirmelerini Nasıl Gerçekleştirir
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

ClickOnce, uygulama dosyalarını güncelleştirmek karar vermek için bir uygulamanın dağıtım bildiriminde belirtilen dosya sürümü bilgilerini kullanır. Bir güncelleştirme başladıktan sonra ClickOnce, adında bir teknik kullanır. *dosya düzeltme eki uygulama* yedekli uygulama dosyalarının yüklenmesini önlemek için.  
  
## <a name="file-patching"></a>Dosya düzeltme eki uygulama  
 Dosyaları değiştirmediğiniz sürece bir uygulamayı güncelleştirdiğinizde, ClickOnce tüm dosyalar için uygulamanın yeni sürümünü karşıdan yüklemez. Bunun yerine, yeni sürüm için bildirim imzaları geçerli uygulama için uygulama bildiriminde belirtilen dosyalar karma imzalarını karşılaştırır. Bir dosyanın imzaları farklı ise, ClickOnce yeni sürümü yükler. İmzalar eşleşirse, dosyanın bir sürümünden sonraki değiştirilmemiştir. Bu durumda, ClickOnce, var olan dosyayı kopyalar ve uygulamayı yeni sürümünde kullanır. Bu yaklaşım ClickOnce yalnızca bir veya iki dosyalar değiştirilmiş olsa bile tüm uygulamayı yeniden indirmek zorunda kalmasını önler.  
  
 Düzeltme eki dosyası da çalışır yüklenen derlemeler için kullanarak isteğe bağlı olarak <xref:System.Deployment.Application.ApplicationDeployment.DownloadFileGroup%2A> ve <xref:System.Deployment.Application.ApplicationDeployment.DownloadFileGroupAsync%2A> yöntemleri.  
  
 Uygulamanızı derlemek için Visual Studio kullanıyorsanız, tüm projeyi yeniden her tüm dosyalar için yeni karma imzaları oluşturur. Bu durumda, yalnızca birkaç derlemeleri değişmiş olabilir ancak tüm derlemeler istemciye indirilir.  
  
 Dosya düzeltme eki uygulama, verileri olarak işaretlenmiş ve veri dizininde depolanan dosyalar için çalışmaz. Bu, dosyanın karması imzasını bağımsız olarak daima yüklenir. Veri dizini hakkında daha fazla bilgi için bkz. [erişen yerel ve uzak veri ClickOnce uygulamalarında](../deployment/accessing-local-and-remote-data-in-clickonce-applications.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ClickOnce güncelleştirme stratejisini seçme](../deployment/choosing-a-clickonce-update-strategy.md)   
 [ClickOnce Dağıtım Stratejisini Seçme](../deployment/choosing-a-clickonce-deployment-strategy.md)



