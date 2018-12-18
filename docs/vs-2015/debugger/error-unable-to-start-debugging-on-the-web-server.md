---
title: 'Hata: Web sunucusunda hata ayıklama başlatılamıyor. | Microsoft Docs'
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
- vs.debug.error.http
- vwd.nonadmin.error.
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- IIS, debugging DLLs
- debugger, Web application errors
- unable to start debugging error
- security [debugger], Web applications
- debugging [Visual Studio], errors
- HTTP servers, debugging error
- security settings, checking for default Web sites
- errors [debugger], unable to start debugging
- debugging ASP.NET Web applications, unable to start debugging error
- remote debugging, errors
ms.assetid: f62e378a-3a99-4f78-9d97-8bb63a4da181
caps.latest.revision: 40
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 168aaff6e7165c0566b198dab22174b14dad9949
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51779300"
---
# <a name="error-unable-to-start-debugging-on-the-web-server"></a>Hata: Web Sunucusunda Hata Ayıklama Başlatılamıyor
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bir Web sunucusunda çalışan bir ASP.NET uygulamasında hata ayıklama kaydetmeye çalıştığında bu hata iletisini alabilirsiniz: Web sunucusunda hata ayıklama başlatılamıyor.
  
IIS düzgün yapılandırılmadığından, çoğu durumda, bu hata oluşur.

##  <a name="vxtbshttpservererrorsthingstocheck"></a> IIS yapılandırmanızı denetleyin

Burada ve hata ayıklamak yeniden denemeden önce ayrıntılı bir sorunu gidermek için adımları uyguladıktan sonra Ayrıca IIS sıfırlamanız gerekebilir. Bir yönetici komut istemi'ni açıp yazarak bunu yapabilirsiniz `iisreset`, veya IIS Yöneticisi'nde bunu yapabilirsiniz. 

* Durdur ve, uygulama havuzlarını yeniden başlatın ve sonra yeniden deneyin.

    Uygulama havuzu durdurulmuş veya yaptığınız başka bir yapılandırma değişikliği durdurun ve, uygulama havuzunu yeniden başlatmak gerekebilir.
    
    > [!NOTE]
    > Uygulama havuzu durduruluyor tutar, Denetim Masası'ndan URL yeniden yazma modülünü kaldırıp Web Platformu Yükleyicisi (WPI) kullanarak yeniden yüklemeniz gerekebilir. Bu, önemli sistem yükseltmeden sonra bir sorun olabilir.

* Uygulama havuzu yapılandırmanızı denetleyin, gerekiyorsa düzeltin ve sonra yeniden deneyin.

    Parola kimlik bilgileri değiştiyse, kendi uygulama havuzunda güncelleştirmeniz gerekebilir. Ayrıca, ASP.NET yakın zamanda yüklediyseniz uygulama havuzu yanlış ASP.NET sürümü için yapılandırılabilir. Bu sorunu düzeltmek ve uygulama havuzu yeniden başlatın.
    
* Web uygulama klasörünüzdeki doğru izinlere sahip olduğunu denetleyin.

    IIS_IUSRS size veya IUSR (veya uygulama havuzuyla ilişkili kullanıcıyı) okuma ve yürütme hakları Web uygulaması klasörü için emin olun. Sorunu düzeltip, uygulama havuzu yeniden başlatın.

* İle yerel adresler HOSTS dosyası kullanıyorsanız, makinenin IP adresi yerine geri döngü adresi kullanarak deneyin.

* Localhost sayfasını tarayıcıda getirin.

     IIS doğru yüklü değilse, yazarken hatalar almalısınız `http://localhost` bir tarayıcıda.
     
     IIS'ye dağıtma hakkında daha fazla bilgi için bkz: [uzak bir IIS bilgisayarda uzaktan hata ayıklama ASP.NET](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md) veya ASP.NET Core [IIS yayımlama](https://docs.asp.net/en/latest/publishing/iis.html)).

* IIS üzerinde ASP.NET doğru sürümünün yüklü olduğundan emin olun.  Bkz: [bir ASP.NET uygulaması dağıtma](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md#BKMK_deploy_asp_net) veya ASP.NET Core [IIS yayımlama](https://docs.asp.net/en/latest/publishing/iis.html)).

* Sunucuda temel bir ASP.NET uygulaması oluşturun.

     Hata ayıklayıcısı ile çalışmak için uygulamanızı alınamıyor, temel bir ASP.NET uygulaması sunucu üzerinde yerel olarak oluşturmayı deneyin ve temel uygulama hatalarını ayıklamayı deneyin. Temel bir uygulama hatalarını ayıklayabilir, bu iki yapılandırma arasında farklıdır belirlemenize yardımcı olabilir.
  
* Yalnızca IP adresi kullanıyorsanız, kimlik doğrulama hatalarını çözümleme

     Varsayılan olarak, IP adreslerinin İnternet'e bir parçası olarak kabul edilir ve NTLM kimlik doğrulaması Internet üzerinden yapılmaz. Web sitenizi IIS kimlik doğrulaması gerektirecek şekilde yapılandırıldıysa, bu kimlik doğrulaması başarısız olur. Bu sorunu düzeltmek için IP adresi yerine uzak bilgisayarın adını belirtebilirsiniz.
     
## <a name="other-causes"></a>Yol açabilecek diğer nedenler

Visual Studio'nun daha eski bir sürümü kullanıyorsanız:

- Yükseltilmiş ayrıcalıklara sahip Visual Studio'yu yeniden başlatın ve yeniden deneyin.

    (Daha sonra sabit) daha eski sürümleri bir hata bazı ASP.NET hata ayıklama senaryoları yükseltilmiş ayrıcalıkları gerekli.
    
- Visual Studio'nun birden çok örneğini çalıştırıyorsanız, projenizi Visual Studio'nun bir örneğinde yeniden açın ve yeniden deneyin.
   
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Web Uygulamalarında Hata Ayıklama: Hatalar ve Sorun Giderme](../debugger/debugging-web-applications-errors-and-troubleshooting.md)



