---
title: 'Hata: Microsoft Visual Studio Uzaktan Hata Ayıklama İzleyicisi (MSVSMON.EXE) uzak bilgisayar üzerinde çalışıyor görünmüyor.'
titleSuffix: ''
ms.custom: seodec18
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: troubleshooting
f1_keywords:
- vs.debug.error.server_machine_no_default
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b2047174106c552357de69a25b0b676c4ab6a2c3
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53066437"
---
# <a name="error-the-microsoft-visual-studio-remote-debugging-monitor-msvsmonexe-does-not-appear-to-be-running-on-the-remote-computer"></a>Hata: Microsoft Visual Studio Uzaktan Hata Ayıklama İzleyicisi (MSVSMON.EXE) uzak bilgisayar üzerinde çalışıyor görünmüyor.
Bu hata iletisi, Visual Studio uzak bilgisayardaki Visual Studio uzaktan hata ayıklama İzleyicisi doğru örneği bulunamadı anlamına gelir. Çalışmak için uzaktan hata ayıklama için Visual Studio uzaktan hata ayıklama İzleyicisi yüklenmesi gerekir. İndirme ve uzaktan hata ayıklayıcı ayarlama hakkında daha fazla bilgi için bkz: [uzaktan hata ayıklama](../debugger/remote-debugging.md).  
  
> [!IMPORTANT]
>  Bu ileti bir ürün hatası nedeniyle almış düşünürseniz, lütfen [bu sorunu bildirmek için Visual Studio](../ide/how-to-report-a-problem-with-visual-studio-2017.md). Daha fazla yardıma ihtiyacınız varsa bkz [konuşmak bize](../ide/talk-to-us.md) yollarını Microsoft ile iletişime geçin.  
  
## <a name="i-got-this-message-while-i-was-debugging-in-visual-studio-2010-or-earlier"></a>Hata ayıklama Visual Studio 2010 veya önceki sürümlerde sırada bu iletiyi aldım.  
 Visual Studio 2010 veya önceki bir sürümü kullandığınız Visual Studio'nun sürümü ise dosya ve Yazıcı Paylaşımı etkin değil, bu hatayı alabilirsiniz. Bu sorun hakkında daha fazla bilgi için lütfen bu belgeler Visual Studio 2010 sürümüne bakın: [hata: Microsoft Visual Studio uzaktan hata ayıklama İzleyicisi (MSVSMON. EXE) uzak bilgisayar üzerinde çalışıyor görünmüyor. -Visual Studio 2010](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms164726(v=vs.100))  
  
## <a name="i-got-this-message-while-i-was-debugging-locally"></a>Yerel olarak debugging sırada bu iletiyi aldım.  
 Yerel olarak hata ayıklarken bu iletiyi alıyorsanız, virüsten koruma yazılımınızı veya bir üçüncü taraf güvenlik duvarı için blame olabilir. Visual Studio 32 bitlik bir uygulama olduğundan, 64 bit uygulamalarda hata ayıklama için uzaktan hata ayıklayıcı 64-bit sürümünü kullanır. İki işlem, yerel bilgisayarın yerel ağda kullanarak iletişim kurar. Bilgisayar trafiği bırakır, ancak üçüncü taraf güvenlik yazılımları iletişimi engelleyebilir mümkündür.  
  
 Aşağıdaki bölümlerde, neden, bu iletiyi edindiğiniz ve sorunu düzeltmek için yapabilecekleriniz başka bir nedenle listelenmektedir.  
  
## <a name="the-remote-machine-is-not-reachable"></a>Uzak makineye ulaşılamıyor  
 Deneyin [ping](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/ee624059(v=ws.10)) uzak makine. Ping işlemine yanıt vermez, uzak Araçlar ya da bağlanmak mümkün olmayacaktır. Uzak makine yeniden başlatılıyor ve aksi takdirde ağ üzerinde doğru yapılandırıldığından emin deneyin.  
  
## <a name="the-version-of-the-remote-debugger-doesnt-match-the-version-of-visual-studio"></a>Uzaktan hata ayıklayıcı sürümü Visual Studio sürümü ile eşleşmiyor  
 Visual Studio'nun sürümü yerel olarak çalışan uzak makine üzerinde çalışan uzaktan hata ayıklama İzleyicisi sürümüyle eşleşmesi gerekir. Bu sorunu gidermek için indirin ve uzaktan hata ayıklama İzleyicisi'nın eşleşen sürümünün yükleyin. Git [İndirme Merkezi](http://www.microsoft.com/en-us/download) uzaktan hata ayıklayıcı doğru sürümü bulunamadı.  
  
## <a name="the-local-and-remote-machines-have-different-authentication-modes"></a>Yerel ve uzak makineler sahip farklı bir kimlik doğrulama modları  
 Yerel ve uzak makineler aynı kimlik doğrulama modunu kullanmanız gerekir. Bu sorunu gidermek için her iki makine aynı kimlik doğrulama modu kullandığınızdan emin olun. Kimlik doğrulama modları hakkında daha fazla bilgi için bkz. [Windows kimlik doğrulamasına genel bakış](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831472(v=ws.11)).  
  
## <a name="the-remote-debugger-is-running-under-a-different-user-account"></a>Uzaktan hata ayıklayıcı farklı bir kullanıcı hesabı altında çalışıyor  
 Bu aşağıdaki yollardan biriyle çözebilirsiniz:  
  
-   Uzaktan hata ayıklayıcıyı durdurun ve yerel bilgisayarda kullanmakta olduğunuz hesapla yeniden başlatın.  
  
-   Komut satırından uzaktan hata ayıklayıcıyı başlatabilirsiniz **/ allow \<kullanıcıadı >** parametresi: `msvsmon /allow <username@computer>`  
  
-   Uzaktan hata ayıklayıcının izinleri kullanıcı ekleyebilir (uzaktan hata ayıklayıcı penceresinde **Araçlar > izinleri**).  
  
-   Önceki adımlarda yöntemlerini kullanamıyorsanız, uzaktan hata ayıklama yapmak herhangi bir kullanıcı izin verebilirsiniz. Uzaktan hata ayıklayıcı penceresinde Git **Araçlar > Seçenekler** iletişim. Seçtiğinizde, **kimlik doğrulaması yok**, daha sonra kontrol edebilirsiniz **tüm kullanıcıların hata ayıklamasına izin**. Ancak, bu seçeneği yalnızca hiçbir seçenek varsa ya da özel bir ağda olması durumunda kullanmanız gerekir.  
  
## <a name="the-firewall-on-the-remote-machine-doesnt-allow-incoming-connections-to-the-remote-debugger"></a>Uzak makinedeki güvenlik duvarı uzaktan hata ayıklayıcı gelen bağlantılara izin vermiyor  
 Visual Studio makinede güvenlik duvarı ve güvenlik duvarı uzak makinede Visual Studio uzaktan hata ayıklayıcı arasındaki iletişime izin verecek şekilde yapılandırılması gerekir. Uzaktan hata ayıklayıcıyı kullanarak bağlantı noktaları hakkında daha fazla bilgi için bkz: [uzaktan hata ayıklayıcı bağlantı noktası atamaları](../debugger/remote-debugger-port-assignments.md). Windows Güvenlik duvarını yapılandırma hakkında daha fazla bilgi için bkz: [uzaktan hata ayıklama için Windows Güvenlik Duvarı Yapılandırma](../debugger/configure-the-windows-firewall-for-remote-debugging.md).  
  
## <a name="anti-virus-software-is-blocking-the-connections"></a>Virüsten koruma yazılımının bağlantıları engelliyor  
 Uzaktan hata ayıklayıcı bağlantıları Windows virüsten koruma yazılımının sağlar, ancak bazı üçüncü taraf virüsten koruma yazılımının engelliyor olabilir. Bu bağlantılara izin verecek şekilde nasıl öğrenmek, virüsten koruma yazılımınızın belgelerine bakın.  
  
## <a name="network-security-policy-is-blocking-communication-between-the-remote-machine-and-visual-studio"></a>Ağ güvenlik ilkesi uzak makinede Visual Studio arasındaki iletişimi engelliyor  
 İletişimi engellemediğinden emin olmak için ağ güvenliği gözden geçirin. Windows ağ güvenlik ilkesi hakkında daha fazla bilgi için bkz: [güvenliği ilke ayarları](/windows/device-security/security-policy-settings/security-policy-settings).  
  
## <a name="the-network-is-too-busy-to-support-remote-debugging"></a>Ağ uzaktan hata ayıklamayı desteklemek için çok meşgul  
 Farklı bir zamanda uzaktan hata ayıklama yapın veya farklı bir saat için ağ üzerinde işi yeniden zamanlayabilir gerekebilir.  
  
## <a name="more-help"></a>Daha fazla yardım  
 Komut satırı anahtarları dahil olmak üzere daha fazla uzaktan hata ayıklayıcı Yardım almak için tıklayın **Yardım > kullanım** uzaktan hata ayıklayıcı penceresinde. Açık yoksa, aşağıdaki satırı kopyalayarak web sayfasını görmek bir **dosya Gezgini** penceresi. (Değiştirmeniz gereken \<Visual Studio yükleme dizini > Visual Studio yüklemenizin konumuyla.)  
  
 res: / /*\<Visual Studio yükleme dizini >* \Common7\IDE\Remote%20Debugger\x64\msvsmon.exe/help.htm  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Uzaktan Hata Ayıklama Hataları ve Sorun Giderme](../debugger/remote-debugging-errors-and-troubleshooting.md)
