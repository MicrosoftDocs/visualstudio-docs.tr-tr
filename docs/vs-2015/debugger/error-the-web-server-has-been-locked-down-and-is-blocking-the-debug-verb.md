---
title: 'Hata: Web sunucusu kilitli ve DEBUG fiilini engelliyor | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.debug.error.webdbg_debug_verb_blocked
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debugger, Web application errors
ms.assetid: 9c8c4812-17db-484d-9c1b-ffd9e3bfef5a
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 60fffd146516bca57497bfdaaabe0f51407063b0
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51770243"
---
# <a name="error-the-web-server-has-been-locked-down-and-is-blocking-the-debug-verb"></a>Hata: Web Sunucusu Kilitli ve DEBUG Fiilini Engelliyor
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bir Web uygulaması veya XML Web hizmeti içine Adımlama, IIS Kilitleme aracını çalıştırın ve URLScan yüklü ve etkin olduğundan başarısız oldu. Bu durum, IIS DEBUG fiilini almasını engeller.  
  
 URLScan IIS Web sitesi yöneticilerinin gereksiz özelliklerini Kapat ve sunucu işleyecek HTTP istek türlerini kısıtlamak olanağı vermek için IIS Kilitleme Aracı ile birlikte çalışan bir güvenlik aracıdır. URLScan güvenlik aracı, belirli HTTP isteklerini engelleyerek, sunucuya ulaşmadan ve zarar görmesine neden zararlı olabilecek istekleri engeller.  
  
 Uygulamanızı IIS 6.0, Windows Server 2003 çalıştırıyorsa, çünkü IIS 6.0 aynı işlevselliği sağlar, IIS Kilitleme aracını çalıştırmamanız.  
  
### <a name="to-enable-debugging-on-a-web-server-with-urlscan-installed"></a>Bir Web sunucusunda yüklü URLScan ile hata ayıklamayı etkinleştirmek için  
  
1.  Urlscan.ini dosyasını bulun. Normalde, şuna benzer bir dizinde bulacaksınız:  
  
     C:\WINNT\System32\Inetsrv\urlscan  
  
2.  Dosyanın bir kopyasını oluşturun ve adlandırın **Urlscan.old**.  
  
3.  Özgün kopyasını Urlscan.ini dosyasını Not Defteri'nde veya tercih ettiğiniz metin düzenleyiciyi kullanarak açın.  
  
4.  URLScan.ini içinde [AllowVerbs] bölümünü bulun. Hata ayıklama [AllowVerbs] bölümüne ekleyin. Görürseniz; [AllowVerbs] bölümünde hata AYIKLAMAK için noktalı fiili açıklamasını kaldırın.  
  
5.  [DenyVerbs] bölümünü bulun. Hata ayıklama [DenyVerbs] bölümünde görünüyorsa, bunu kaldırın.  
  
6.  Dosyayı kaydedin.  
  
7.  Sunucuyu yeniden başlatın veya IIS'yi yeniden başlatın.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Web uygulamalarında hata ayıklama: Hatalar ve sorun giderme](../debugger/debugging-web-applications-errors-and-troubleshooting.md)   
 [Hata: Web Sunucusu İstenen Kaynağı Bulamadı](../debugger/error-the-web-server-could-not-find-the-requested-resource.md)



