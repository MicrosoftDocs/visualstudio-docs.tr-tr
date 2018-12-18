---
title: 'Hata: Web sunucusu kilitli ve DEBUG fiilini engelliyor | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: troubleshooting
f1_keywords:
- vs.debug.error.webdbg_debug_verb_blocked
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugger, Web application errors
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c2537868da6c72df9a68c492b650c72d8a980fcb
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2018
ms.locfileid: "31474004"
---
# <a name="error-the-web-server-has-been-locked-down-and-is-blocking-the-debug-verb"></a>Hata: Web Sunucusu Kilitli ve DEBUG Fiilini Engelliyor
Bir Web uygulaması veya XML Web hizmeti içine Adımlama, IIS Kilitleme aracını çalıştırın ve URLScan yüklü ve etkinleştirilmiş olduğundan başarısız oldu. Bu durum IIS DEBUG fiilini almasını engeller.  
  
 URLScan IIS Web sitesi yöneticileri gereksiz özelliklerini kapatmak ve, sunucunun işlediği HTTP isteği türü kısıtlama olanağı vermek için IIS Kilitleme Aracı ile birlikte çalışan bir güvenlik aracıdır. Belirli HTTP isteklerini engelleyerek URLScan güvenlik aracı sunucudan ve zarar görmesine neden zararlı olabilecek istekleri engeller.  
  
 Uygulamanız IIS 6.0, Windows Server 2003 çalıştırıyorsa, çünkü IIS 6.0 aynı işlevselliği sağlar, IIS Kilitleme Aracı çalıştırmamanız.  
  
### <a name="to-enable-debugging-on-a-web-server-with-urlscan-installed"></a>Bir Web sunucusunda yüklü URLScan ile hata ayıklamayı etkinleştirmek için  
  
1.  Urlscan.ini dosyasını bulun. Normalde, aşağıdakine benzer bir dizinde bulacaksınız:  
  
     C:\WINNT\System32\Inetsrv\urlscan  
  
2.  Dosyanın bir kopyasını oluşturun ve adlandırın **Urlscan.old**.  
  
3.  Not Defteri veya metin düzenleyiciyi kullanarak Urlscan.ini dosyasını özgün kopyasını açın.  
  
4.  URLScan.ini içinde [AllowVerbs] bölümünü bulun. Hata ayıklama [AllowVerbs] bölümüne ekleyin. Görürseniz; [AllowVerbs] bölümünde hata ayıklama, fiili açıklamadan çıkarın için noktalı virgül kaldırın.  
  
5.  [DenyVerbs] bölümünü bulun. Hata ayıklama [DenyVerbs] bölümünde görüntülenirse, kaldırın.  
  
6.  Dosyayı kaydedin.  
  
7.  Sunucuyu yeniden başlatmanız veya IIS yeniden başlatın.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Web uygulamalarında hata ayıklama: Hatalar ve sorun giderme](../debugger/debugging-web-applications-errors-and-troubleshooting.md)   
 [Hata: Web sunucusu istenen kaynak bulunamadı.](../debugger/error-the-web-server-could-not-find-the-requested-resource.md)