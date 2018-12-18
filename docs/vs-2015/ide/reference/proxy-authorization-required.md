---
title: Proxy yetkilendirmesi gerekli | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c2d24ae1-9902-460e-b72a-0299eed9ee82
caps.latest.revision: 9
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 2650dadddefe3be18a4406eb4fd07c5599622212
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49259221"
---
# <a name="proxy-authorization-required"></a>Proxy kimlik doğrulaması gerekli
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
Bu hata genellikle kullanıcılar Visual Studio Online için bir proxy sunucu üzerinden bağlanır ve proxy sunucusu çağrıları engeller oluşur. Visual Studio Online IDE açan kullanıcı tutmak için kullanılır.  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
-   Visual Studio'yu yeniden başlatın. Bir ara sunucu kimlik doğrulaması iletişim kutusu görünür. İletişim kutusunda kimlik bilgilerinizi girin.  
  
-   Yukarıdaki adım sorunu çözmezse, proxy sunucusu için kimlik bilgileri istenmez Bunun nedeni olabilir http://go.microsoft.com yöneliktir ancak bunu yapar *. visualStudio.com adresleri. Bu sunucular için güvenilir listeye Visual Studio'da tüm oturum açma senaryoları engelini kaldırmak için aşağıdaki listeyi gerekir:  
  
    -   *.windows.net  
  
    -   *.microsoftonline.com  
  
    -   *.visualstudio.com  
  
    -   *.microsoft.com  
  
    -   *.live.com  
  
-   Aksi takdirde kaldırabilirsiniz http://go.microsoft.com adresi için hem de proxy kimlik doğrulaması iletişim kutusu gösterilir böylece bir beyaz liste http://go.microsoft.com adresi ve Visual Studio başlatıldığında sunucu uç noktaları.  
  
-   VEYA  
  
-   Ara sunucunuzda varsayılan kimlik bilgilerinizi kullanmak istiyorsanız, aşağıdakileri yapabilirsiniz:  
  
    1.  Devenv.exe.config (devenv.exe yapılandırma dosyası) bulun: **%ProgramFiles%\Microsoft Visual Studio 14.0\Common7\IDE** (veya **% ProgramFiles (x86) %\Microsoft Visual Studio 14.0\Common7\IDE**) .  
  
    2.  Yapılandırma dosyasında bulunamıyor `<system.net>` engelleyin ve bu kodu ekleyin:  
  
        ```xml  
        <defaultProxy enabled="true" useDefaultCredentials="true">  
            <proxy bypassonlocal="True" proxyaddress=" HYPERLINK "http://<yourproxy:port#" http://<yourproxy:port#>"/>  
        </defaultProxy>  
  
        ```  
  
         Doğru ara sunucu adresi için ağınızda eklemelisiniz `proxyaddress="<http://<yourproxy:port#>`.  
  
-   VEYA  
  
-   Yönergeleri de izleyebilirsiniz [yazıya](http://blogs.msdn.com/b/rido/archive/2010/05/06/how-to-connect-to-tfs-through-authenticated-web-proxy.aspx) Ara sunucusunu kullanacak şekilde sağlayacak kodu eklemek için.



