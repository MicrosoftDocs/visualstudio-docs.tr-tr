---
title: 'Hata: Çalışma grubu uzak oturum açma hatası | Microsoft Docs'
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
- vs.debug.error.workgroup_remote_logon_failure
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- VB
- CSharp
- C++
helpviewer_keywords:
- logon failure, remote debugging
- remote debugging, logon failure
ms.assetid: 7be2c5bb-40fe-48d6-8cfc-c231fbd3d64e
caps.latest.revision: 22
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b13531d3a9dd5249b0c96ddc4e8f736c20696303
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51723656"
---
# <a name="error-workgroup-remote-logon-failure"></a>Hata: Çalışma Grubu Uzak Oturum Açma Başarısız
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu hata görünür:  
  
 Oturum açma hatası: Bilinmeyen kullanıcı adı veya hatalı parola  
  
 **Nedeni**  
  
 Bir çalışma grubunda bir makineden hata ayıklama ve uzak makinesine bağlanmaya çalışırsanız, bu hata oluşabilir. Olası nedenler şunlardır:  
  
-   Uzak makinede eşleşen adı ve parola ile hesabı yoktur.  
  
-   Çalışma gruplarında, hem Visual Studio bilgisayarı ve uzak makine varsa, bu hata nedeniyle varsayılan oluşabilir **yerel güvenlik ilkesi** uzak makinede ayarlama. Varsayılan ayarı **yerel güvenlik ilkesi** ayardır **yalnızca konuk - yerel kullanıcı konuk olarak kimlik doğrulaması**. Bu kurulum üzerinde hata ayıklamak için uzak makineye ayarları değiştirme **Klasik - yerel kullanıcıların kendileri olarak kimliklerini**.  
  
> [!NOTE]
>  Aşağıdaki görevleri gerçekleştirmek için yönetici olmanız gerekir.  
  
### <a name="to-open-the-local-security-policy-window"></a>Yerel Güvenlik İlkesi penceresini açmak için  
  
1.  Başlangıç **secpol.msc** Microsoft Yönetim Konsolu ek bileşeni. Windows Search'te Windows Çalıştır kutusuna veya bir komut isteminde secpol.msc yazın.  
  
### <a name="to-add-user-rights-assignments"></a>Kullanıcı hakları ataması eklemek için  
  
1.  Yerel açın  
  
2.  Açık **yerel güvenlik ilkesi** penceresi.  
  
3.  Genişletin **yerel ilkeler** klasör.  
  
4.  Tıklayın **kullanıcı hakları ataması**.  
  
5.  İçinde **ilke** sütunu, çift tıklatın **programları için hata ayıklama** geçerli yerel Grup İlkesi atamalarını görüntülemek için **Yerel Güvenlik İlkesi ayarının** iletişim kutusu.  
  
     ![Yerel Güvenlik İlkesi kullanıcı hakları](../debugger/media/dbg-err-localsecuritypolicy-userrightsdebugprograms.png "DBG_ERR_LocalSecurityPolicy_UserRightsDebugPrograms")  
  
6.  Yeni kullanıcı eklemek için tıklatın **kullanıcı veya Grup Ekle** düğmesi.  
  
### <a name="to-change-the-sharing-and-security-model"></a>Paylaşım ve güvenlik modeli değiştirmek için  
  
1.  Açık **yerel güvenlik ilkesi** penceresi.  
  
2.  Genişletin **yerel ilkeler** klasör.  
  
3.  Tıklayın **güvenlik seçenekleri**.  
  
4.  İçinde **ilke** sütunu, çift **ağ erişimi: Yerel hesaplar için paylaşım ve güvenlik modeli**.  
  
5.  İçinde **ağ erişimi: Yerel hesaplar için paylaşım ve güvenlik modeli** iletişim kutusunda, bir değerle değiştirmek **Klasik - yerel kullanıcıların kendileri olarak kimliklerini** tıklatıp **Uygula**düğmesi.  
  
     ![Yerel Güvenlik İlkesi güvenlik seçenekleri](../debugger/media/dbg-err-localsecuritypolicy-securityoptions-networkaccess.png "DBG_ERR_LocalSecurityPolicy_SecurityOptions_NetworkAccess")  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Uzaktan hata ayıklama ve sorun giderme](../debugger/remote-debugging-errors-and-troubleshooting.md)   
 [Uzaktan Hata Ayıklama](../debugger/remote-debugging.md)



