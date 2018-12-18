---
title: Microsoft Visual Studio uzaktan hata ayıklama İzleyicisi'ne bağlanılamıyor. | Microsoft Docs
ms.custom: ''
ms.date: 08/24/2017
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.debug.error.remote_debug
- vs.debug.error.firewall.remotemachine
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
ms.openlocfilehash: 1096188a6cf6be34d56c6330d588e56e0c306581
ms.sourcegitcommit: 50b19010b2e2b4736835350710e2edf93b980b56
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/10/2018
ms.locfileid: "49073941"
---
# <a name="unable-to-connect-to-the-microsoft-visual-studio-remote-debugging-monitor"></a>Microsoft Visual Studio Uzaktan Hata Ayıklama İzleyicisi'ne Bağlanılamıyor.
Bu ileti, uzaktan hata ayıklama İzleyicisi düzgün uzak makinede kurulu değil veya uzak makineye ağ sorunlarının veya güvenlik duvarı varlığını nedeniyle erişilemez olduğu için meydana gelebilir.
  
> [!IMPORTANT]
>  Bu ileti bir ürün hatası nedeniyle almış düşünürseniz, lütfen [bu sorunu bildirin](../ide/how-to-report-a-problem-with-visual-studio-2017.md) Visual Studio için. Daha fazla yardıma ihtiyacınız varsa bkz [konuşmak bize](../ide/talk-to-us.md) yollarını Microsoft ile iletişime geçin.

## <a name="specificerrors"></a>Ayrıntılı hata iletisini nedir?

`Unable to Connect to the Microsoft Visual Studio Remote Debugging Monitor` İleti geneldir. Genellikle, daha belirli bir ileti hata dizesi içinde bulunur ve sorun veya arama için daha kesin düzeltme nedenini belirlemenize yardımcı olabilir. Birkaç ana hata iletisi eklenir daha yaygın hata iletileri şunlardır:

- [Hata ayıklayıcı uzak bilgisayara bağlanamıyor. Hata ayıklayıcı belirtilen bilgisayar adını çözümleyemedi](#cannot_connect)
- [Bağlantı isteği uzaktan hata ayıklayıcı tarafından reddedildi](#rejected)
- [Geçersiz bellek konumuna erişim](#invalid_access)
- [Belirtilen ada uzak bilgisayar üzerinde çalışan sunucusu yok](#no_server)
- [İstenen ad geçerli, ancak istenen türde hiçbir veri bulunamadı](#valid_name)
- [Visual Studio uzaktan hata ayıklayıcı hedef bilgisayarda bu bilgisayara bağlanamıyor](#cant_connect_back)
- [Erişim reddedildi](#access_denied)
- [Güvenlik paketi belirli bir hata oluştu](#security_package)

## <a name="cannot_connect"></a> Hata ayıklayıcı uzak bilgisayara bağlanamıyor. Hata ayıklayıcı belirtilen bilgisayar adını çözümleyemedi

Aşağıdaki adımları deneyin:

1. Geçerli bir bilgisayar adı girin ve bağlantı noktası numarasını sağlayın **iliştirme** iletişim kutusu veya Proje Özellikleri'nde (özelliklerini ayarlamak için bkz: [adımları](#server_incorrect)). Bilgisayar adı şu biçimde olmalıdır:

    `computername:port`

    > [!NOTE]
    > Bağlantı noktası numarasını eşleşmelidir [bağlantı noktası numarasına uzaktan hata ayıklayıcı](../debugger/remote-debugger-port-assignments.md), hangi *çalıştırmalıdır* hedef makinede.

2. Bilgisayar adı çalışmazsa, IP adresi deneyin ve bunun yerine bağlantı noktası numarası.

3. Sürümü hedef makine üzerinde çalışan uzaktan hata ayıklayıcı, Visual Studio sürümünüze eşleştiğinden emin olun. Uzaktan hata ayıklayıcı doğru sürümünü almak için bkz: [uzaktan hata ayıklama](../debugger/remote-debugging.md).

    > [!TIP]
    > İşleme iliştirmekte olduğunuz ve başarıyla bağlanması, ancak istediğiniz işlemi görmüyorsanız, seçin **Göster tüm kullanıcıların bu onay kutusunu işlemlerden**. Bu, işlemleri farklı bir kullanıcı hesabı altında bağlı olmadığını gösterir.

4. Bu adımları bu hatayı çözmezse bkz [uzak makineye ulaşılamıyor](#dns).

## <a name="rejected"></a> Bağlantı isteği uzaktan hata ayıklayıcı tarafından reddedildi

İçinde **iliştirme** iletişim kutusunda veya proje özelliklerinde, uzak bilgisayar adını ve bağlantı noktası numarası uzaktan hata ayıklayıcı penceresinde gösterilen adını ve bağlantı noktası numarası eşleştiğinden emin olun. Yanlış ise, düzeltin ve yeniden deneyin.

Bu değerlerin doğru olduğundan ve ileti bahsetmeleri **Windows kimlik doğrulaması** modu, uzaktan hata ayıklayıcı doğru kimlik doğrulaması modunda olup olmadığını denetleyin (**Araçlar > Seçenekler**).

## <a name="invalid_access"></a> Geçersiz bellek konumuna erişim

Bir iç hata oluştu. Visual Studio'yu yeniden başlatın ve yeniden deneyin.

## <a name="no_server"></a> Belirtilen ada uzak bilgisayar üzerinde çalışan sunucusu yok

Visual Studio uzaktan hata ayıklayıcıyı bağlanamadı. Bu ileti, çeşitli nedenlerle oluşabilir:

- Uzaktan hata ayıklayıcı farklı bir kullanıcı hesabı altında çalışıyor olabilir. Bkz: [adımları](#user_accounts)

- Güvenlik duvarında bağlantı noktası engellenir. Güvenlik Duvarı olduğundan emin olun [isteğiniz engellemeyen](#firewall), özellikle bir üçüncü taraf güvenlik duvarı kullanıyorsanız.

- Visual Studio uzaktan hata ayıklayıcı sürümü eşleşmiyor. Uzaktan hata ayıklayıcı doğru sürümünü almak için bkz: [uzaktan hata ayıklama](../debugger/remote-debugging.md)


## <a name="valid_name"></a> İstenen ad geçerli, ancak istenen türde hiçbir veri bulunamadı

Uzak bilgisayarın var, ancak Visual Studio uzaktan hata ayıklayıcıyı bağlanamadı. Bu ileti, çeşitli nedenlerle oluşabilir:

- Bir DNS sorununun bağlantıyı engelliyor. Bkz: [adımları](#dns).

- Uzaktan hata ayıklayıcı farklı bir kullanıcı hesabı altında çalışıyor olabilir. İzleyin [adımları](#user_accounts).

- Güvenlik duvarında bağlantı noktası engellenir. Güvenlik Duvarı olduğundan emin olun [isteğiniz engellemeyen](#firewall), özellikle bir üçüncü taraf güvenlik duvarı kullanıyorsanız.

- Visual Studio uzaktan hata ayıklayıcı sürümü eşleşmiyor. Uzaktan hata ayıklayıcı doğru sürümünü almak için bkz: [uzaktan hata ayıklama](../debugger/remote-debugging.md).

## <a name="cant_connect_back"></a> Visual Studio uzaktan hata ayıklayıcı hedef bilgisayarda bu bilgisayara bağlanamıyor

Uzaktan hata ayıklayıcı farklı bir kullanıcı hesabı altında çalışıyor olabilir. Uzaktan hata ayıklayıcı açın **Araçlar > izinleri** kullanıcı uzaktan hata ayıklayıcının izinleri eklemek için. Daha fazla bilgi için [uzaktan hata ayıklayıcı farklı bir kullanıcı hesabı altında çalıştığından](#user_accounts).

Hata iletisi ayrıca bir güvenlik duvarı bahsetmeleri, güvenlik duvarı yerel makinede geri Visual Studio için Uzak bilgisayardan iletişimi engelliyor olabilir. Bkz: [adımları](#firewall).

## <a name="access_denied"></a> Erişim reddedildi

(Desteklenmiyor) bir 32-bit bilgisayarda 64-bit uzak bilgisayarda hata ayıklamaya çalıştığınızda bu hatayı görebilirsiniz.

## <a name="security_package"></a> Güvenlik paketi belirli bir hata oluştu

Bu, Windows XP ve Windows 7 için belirli bir bilinen sorun olabilir. Bkz. Bu [bilgi](https://stackoverflow.com/questions/4786016/unable-to-connect-to-the-microsoft-remote-debugging-monitor-a-security-package). 

## <a name="causes-and-recommendations"></a>Neden olur ve öneriler

### <a name="dns"></a> Uzak makineye ulaşılamıyor 

Uzak bilgisayar adını kullanarak bağlanamıyorsa, IP adresi kullanmayı deneyin. Kullanabileceğiniz `ipconfig` IPv4 adresini almak için uzak bilgisayarda bir komut satırında. HOSTS dosyası kullanıyorsanız, doğru şekilde yapılandırıldığını doğrulayın.

Bu başarısız olursa, uzak bilgisayarın ağda erişilebilir olduğunu doğrulayın ([ping](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/ee624059(v=ws.10)) uzak makine). Internet üzerinden uzaktan hata ayıklama desteklenmiyor, Microsoft Azure bazı senaryolarda hariç.
  
### <a name="server_incorrect"></a> Sunucu adı yanlış veya üçüncü taraf yazılım, uzaktan hata ayıklayıcı ile engelliyor

Visual Studio'da proje özelliklerine bakmak ve sunucu adının doğru olduğundan emin olun. Konular için bkz. [C# ve Visual Basic](../debugger/remote-debugging-csharp.md#remote_csharp) ve [C++](../debugger/remote-debugging-cpp.md#remote_cplusplus). ASP.NET için açık **özellikleri / Web / sunucuları** veya **özellikleri / Debug** proje türüne bağlı olarak.

> [!NOTE]
> İşleme bağlıyorsanız, proje özelliklerinde uzak ayarları kullanılmaz.

Sunucu adı doğruysa, virüsten koruma yazılımınızı veya bir üçüncü taraf güvenlik duvarı uzaktan hata ayıklayıcı engelliyor olabilir. Visual Studio uzaktan hata ayıklayıcı 64-bit sürümü 64-bit uygulamalarında hata ayıklamak için kullandığı için 32 bitlik bir uygulama olduğundan, yerel hata ayıklama sırasında bu durum oluşabilir. 32 bit ve 64-bit işlemler, yerel bilgisayarın yerel ağda kullanarak iletişim kurar. Bilgisayar hiçbir ağ trafiği bırakır, ancak üçüncü taraf güvenlik yazılımları iletişimi engelleyebilir mümkündür.

### <a name="user_accounts"></a> Uzaktan hata ayıklayıcı farklı bir kullanıcı hesabı altında çalışıyor 

Uzaktan hata ayıklayıcı varsayılan olarak, yalnızca Yöneticiler grubunun üyelerinin ve uzaktan hata ayıklayıcıyı başlatan kullanıcı bağlantılarını kabul eder. Ek kullanıcılar, açıkça izin verilmelidir. 
 
Bu aşağıdaki yollardan biriyle çözebilirsiniz:  

-   Visual Studio kullanıcı uzaktan hata ayıklayıcının izinleri ekleyin (uzaktan hata ayıklayıcı penceresinde **Araçlar > izinleri**).

-   Uzak bilgisayarda Visual Studio bilgisayarda kullandığınız parolanın ve aynı kullanıcı hesabı altında uzaktan hata ayıklayıcıyı yeniden başlatın.

    > [!NOTE]
    > Uzaktan hata ayıklayıcı uzak bir sunucuda çalışıyorsa, uzaktan hata ayıklayıcı uygulama sağ tıklatın ve seçin **yönetici olarak çalıştır** (veya, uzaktan hata ayıklayıcıyı bir hizmet olarak çalıştırmak). Uzak bir sunucuda, çalıştırmıyorsanız yalnızca başlatın normalde.
  
-   Komut satırından uzaktan hata ayıklayıcıyı başlatabilirsiniz **/ allow \<kullanıcıadı >** parametresi: `msvsmon /allow <username@computer>`. 
  
-   Alternatif olarak, uzaktan hata ayıklama yapmak herhangi bir kullanıcı izin verebilirsiniz. Uzaktan hata ayıklayıcı penceresinde Git **Araçlar > Seçenekler** iletişim. Seçtiğinizde, **kimlik doğrulaması yok**, daha sonra kontrol edebilirsiniz **tüm kullanıcıların hata ayıklamasına izin**. Ancak, bu seçenek yalnızca diğer seçenekleri başarısız olursa veya özel bir ağda olduğunda denemelisiniz.

### <a name="firewall"></a> Uzak makinedeki güvenlik duvarı uzaktan hata ayıklayıcı gelen bağlantılara izin vermiyor  
 Visual Studio makinede güvenlik duvarı ve güvenlik duvarı uzak makinede Visual Studio uzaktan hata ayıklayıcı arasındaki iletişime izin verecek şekilde yapılandırılması gerekir. Uzaktan hata ayıklayıcıyı kullanarak bağlantı noktaları hakkında daha fazla bilgi için bkz: [uzaktan hata ayıklayıcı bağlantı noktası atamaları](../debugger/remote-debugger-port-assignments.md). Windows Güvenlik duvarını yapılandırma hakkında daha fazla bilgi için bkz: [uzaktan hata ayıklama için Windows Güvenlik Duvarı Yapılandırma](../debugger/configure-the-windows-firewall-for-remote-debugging.md).
  
### <a name="the-version-of-the-remote-debugger-doesnt-match-the-version-of-visual-studio"></a>Uzaktan hata ayıklayıcı sürümü Visual Studio sürümü ile eşleşmiyor  
 Visual Studio'nun sürümü yerel olarak çalışan uzak makine üzerinde çalışan uzaktan hata ayıklama İzleyicisi sürümüyle eşleşmesi gerekir. Bu sorunu gidermek için indirin ve uzaktan hata ayıklama İzleyicisi'nın eşleşen sürümünün yükleyin. Uzaktan hata ayıklayıcı doğru sürümünü almak için bkz: [uzaktan hata ayıklama](../debugger/remote-debugging.md).
  
### <a name="the-local-and-remote-machines-have-different-authentication-modes"></a>Yerel ve uzak makineler sahip farklı bir kimlik doğrulama modları  
 Yerel ve uzak makineler aynı kimlik doğrulama modunu kullanmanız gerekir. Bu sorunu gidermek için her iki makine aynı kimlik doğrulama modu kullandığınızdan emin olun. Kimlik doğrulama modu değiştirebilirsiniz. Uzaktan hata ayıklayıcı penceresinde Git **Araçlar > Seçenekler** iletişim kutusu.
  
 Kimlik doğrulama modları hakkında daha fazla bilgi için bkz. [Windows kimlik doğrulamasına genel bakış](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831472(v=ws.11)).   
  
### <a name="anti-virus-software-is-blocking-the-connections"></a>Virüsten koruma yazılımının bağlantıları engelliyor  
 Uzaktan hata ayıklayıcı bağlantıları Windows virüsten koruma yazılımının sağlar, ancak bazı üçüncü taraf virüsten koruma yazılımının engelliyor olabilir. Bu bağlantılara izin verecek şekilde nasıl öğrenmek, virüsten koruma yazılımınızın belgelerine bakın.  
  
### <a name="network-security-policy-is-blocking-communication-between-the-remote-machine-and-visual-studio"></a>Ağ güvenlik ilkesi uzak makinede Visual Studio arasındaki iletişimi engelliyor  
 İletişimi engellemediğinden emin olmak için ağ güvenliği gözden geçirin. Windows ağ güvenlik ilkesi hakkında daha fazla bilgi için bkz: [güvenliği ilke ayarları](/windows/device-security/security-policy-settings/security-policy-settings).  
  
### <a name="the-network-is-too-busy-to-support-remote-debugging"></a>Ağ uzaktan hata ayıklamayı desteklemek için çok meşgul  
 Farklı bir zamanda uzaktan hata ayıklama yapın veya farklı bir saat için ağ üzerinde işi yeniden zamanlayabilir gerekebilir.  
  
## <a name="more-help"></a>Daha fazla yardım  
 Daha fazla uzaktan hata ayıklayıcı Yardım almak için uzaktan hata ayıklayıcının Yardım sayfasını açın (**Yardım > kullanım** uzaktan hata ayıklayıcı).
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Uzaktan Hata Ayıklama](../debugger/remote-debugging.md)
