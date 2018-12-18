---
title: Microsoft Visual Studio uzaktan hata ayıklama İzleyicisi'ne bağlanılamıyor. | Microsoft Docs
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
- vs.debug.error.remote_debug
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: a1d959fc-3817-491c-831b-e6b768a3877a
caps.latest.revision: 17
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 139c650ac61b9312b069cc2e19fa66d3673ca30f
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51733013"
---
# <a name="unable-to-connect-to-the-microsoft-visual-studio-remote-debugging-monitor"></a>Microsoft Visual Studio Uzaktan Hata Ayıklama İzleyicisi'ne Bağlanılamıyor.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Geçersiz bir Visual Studio uzaktan hata ayıklama İzleyicisi ad girdiğinizde bu hata iletisi görüntülenir. **iliştirme** iletişim kutusu. Uzaktan hata ayıklama İzleyicisi adı genellikle, uzaktan hata ayıklama için bağlanmaya çalıştığınız makine ile aynıdır. Bu ileti, uzak makine ağ üzerinde mevcut değil, uzaktan hata ayıklama İzleyicisi düzgün uzak makinede kurulu değil veya uzak makineye ağ sorunlarının veya güvenlik duvarı varlığını nedeniyle erişilemez durumda nedeniyle oluşabilir.  
  
> [!IMPORTANT]
>  Bir ürün hatası nedeniyle bu iletiyi almış olduğunu düşünüyorsanız, Visual Studio için lütfen bu sorunu bildirin [gülümseme Gönder](http://msdn.microsoft.com/library/5cc9b67a-54d0-41b0-aa8f-80dff4475a6b). Daha fazla yardıma ihtiyacınız varsa bkz [konuşmak bize](../ide/talk-to-us.md) yollarını Microsoft ile iletişime geçin.  
  
## <a name="i-got-this-message-while-i-was-debugging-locally"></a>Yerel olarak debugging sırada bu iletiyi aldım.  
 Yerel olarak hata ayıklarken bu iletiyi alıyorsanız, virüsten koruma yazılımınızı veya bir üçüncü taraf güvenlik duvarı için blame olabilir. Visual Studio 32 bitlik bir uygulama olduğundan, 64 bit uygulamalarda hata ayıklama için uzaktan hata ayıklayıcı 64-bit sürümünü kullanır. İki işlem, yerel bilgisayarın yerel ağda kullanarak iletişim kurar. Bilgisayar hiçbir ağ trafiği bırakır, ancak üçüncü taraf güvenlik yazılımları iletişimi engelleyebilir mümkündür.  
  
 Aşağıdaki bölümlerde, neden, bu iletiyi edindiğiniz ve sorunu düzeltmek için yapabilecekleriniz başka bir nedenle listelenmektedir.  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
-   Visual Studio uzaktan hata ayıklama İzleyicisi yüklü ve uzak makinede çalışıyor olduğundan emin olun. Uzaktan hata ayıklayıcı ve nasıl yükleneceği hakkında daha fazla bilgi için bkz. [uzaktan hata ayıklama](../debugger/remote-debugging.md).  
  
-   Visual Studio'da proje özelliklerine bakmak (**proje / özellikleri / hata ayıklama**). Emin **uzak sunucu adı** doğrudur.  
  
-   Uzak makinenin ağda erişilebilir olduğunu doğrulayın.  
  
## <a name="the-remote-machine-is-not-reachable"></a>Uzak makineye ulaşılamıyor  
 Deneyin [ping](https://technet.microsoft.com/library/ee624059\(v=ws.10\).aspx) uzak makine. Ping işlemine yanıt vermez, uzak Araçlar ya da bağlanmak mümkün olmayacaktır. Uzak makine yeniden başlatılıyor ve aksi takdirde ağ üzerinde doğru yapılandırıldığından emin deneyin.  
  
## <a name="the-version-of-the-remote-debugger-doesnt-match-the-version-of-visual-studio"></a>Uzaktan hata ayıklayıcı sürümü Visual Studio sürümü ile eşleşmiyor  
 Visual Studio'nun sürümü yerel olarak çalışan uzak makine üzerinde çalışan uzaktan hata ayıklama İzleyicisi sürümüyle eşleşmesi gerekir. Bu sorunu gidermek için indirin ve uzaktan hata ayıklama İzleyicisi'nın eşleşen sürümünün yükleyin. Git [İndirme Merkezi](http://www.microsoft.com/download) uzaktan hata ayıklayıcı doğru sürümü bulunamadı.  
  
## <a name="the-local-and-remote-machines-have-different-authentication-modes"></a>Yerel ve uzak makineler sahip farklı bir kimlik doğrulama modları  
 Yerel ve uzak makineler aynı kimlik doğrulama modunu kullanmanız gerekir. Bu sorunu gidermek için her iki makine aynı kimlik doğrulama modu kullandığınızdan emin olun. Kimlik doğrulama modu uzaktan hata ayıklayıcı değiştirebilirsiniz **Araçlar / Seçenekler** iletişim.  
  
 Kimlik doğrulama modları hakkında daha fazla bilgi için bkz. [Windows kimlik doğrulamasına genel bakış](https://technet.microsoft.com/library/hh831472.aspx).  
  
## <a name="the-remote-debugger-is-running-under-a-different-user-account"></a>Uzaktan hata ayıklayıcı farklı bir kullanıcı hesabı altında çalışıyor  
 Bu aşağıdaki yollardan biriyle çözebilirsiniz:  
  
-   Uzaktan hata ayıklayıcıyı durdurun ve yerel bilgisayarda kullanmakta olduğunuz hesapla yeniden başlatın.  
  
-   Komut satırından uzaktan hata ayıklayıcıyı başlatabilirsiniz **/ allow \<kullanıcıadı >** parametresi: `msvsmon /allow <username@computer>`  
  
-   Uzaktan hata ayıklayıcının izinleri kullanıcı ekleyebilir (uzaktan hata ayıklayıcı penceresinde **araçları / izinleri**).  
  
-   Önceki adımlarda yöntemlerini kullanamıyorsanız, uzaktan hata ayıklama yapmak herhangi bir kullanıcı izin verebilirsiniz. Uzaktan hata ayıklayıcı penceresinde Git **araçları/Options** iletişim. Seçtiğinizde, **kimlik doğrulaması yok**, daha sonra kontrol edebilirsiniz **tüm kullanıcıların hata ayıklamasına izin**. Ancak, bu seçeneği yalnızca hiçbir seçenek varsa ya da özel bir ağda olması durumunda kullanmanız gerekir.  
  
## <a name="the-firewall-on-the-remote-machine-doesnt-allow-incoming-connections-to-the-remote-debugger"></a>Uzak makinedeki güvenlik duvarı uzaktan hata ayıklayıcı gelen bağlantılara izin vermiyor  
 Visual Studio makinede güvenlik duvarı ve güvenlik duvarı uzak makinede Visual Studio uzaktan hata ayıklayıcı arasındaki iletişime izin verecek şekilde yapılandırılması gerekir. Uzaktan hata ayıklayıcıyı kullanarak bağlantı noktaları hakkında daha fazla bilgi için bkz: [uzaktan hata ayıklayıcı bağlantı noktası atamaları](../debugger/remote-debugger-port-assignments.md). Windows Güvenlik duvarını yapılandırma hakkında daha fazla bilgi için bkz: [uzaktan hata ayıklama için Windows Güvenlik Duvarı Yapılandırma](../debugger/configure-the-windows-firewall-for-remote-debugging.md).  
  
## <a name="anti-virus-software-is-blocking-the-connections"></a>Virüsten koruma yazılımının bağlantıları engelliyor  
 Uzaktan hata ayıklayıcı bağlantıları Windows virüsten koruma yazılımının sağlar, ancak bazı üçüncü taraf virüsten koruma yazılımının engelliyor olabilir. Bu bağlantılara izin verecek şekilde nasıl öğrenmek, virüsten koruma yazılımınızın belgelerine bakın.  
  
## <a name="network-security-policy-is-blocking-communication-between-the-remote-machine-and-visual-studio"></a>Ağ güvenlik ilkesi uzak makinede Visual Studio arasındaki iletişimi engelliyor  
 İletişimi engellemediğinden emin olmak için ağ güvenliği gözden geçirin. Windows ağ güvenlik ilkesi hakkında daha fazla bilgi için bkz: [güvenlik yönetimi](https://msdn.microsoft.com/library/windows/desktop/ms721855\(v=vs.85\).aspx).  
  
## <a name="the-network-is-too-busy-to-support-remote-debugging"></a>Ağ uzaktan hata ayıklamayı desteklemek için çok meşgul  
 Farklı bir zamanda uzaktan hata ayıklama yapın veya farklı bir saat için ağ üzerinde işi yeniden zamanlayabilir gerekebilir.  
  
## <a name="more-help"></a>Daha fazla yardım  
 Komut satırı anahtarları dahil olmak üzere daha fazla uzaktan hata ayıklayıcı Yardım almak için aşağıdaki bir tarayıcıda açın:  
  
 **res://C:\Program%20Files\Microsoft%20Visual%20Studio%2014.0\Common7\IDE\Remote%20Debugger\x64\msvsmon.exe/help.htm**  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Uzaktan Hata Ayıklama](../debugger/remote-debugging.md)



