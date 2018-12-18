---
title: İşleme iliştirilemiyor | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.debug.remote.unable2attach
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
ms.openlocfilehash: 7036210f47e99ca11edbdb86fdf1f44e40829237
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2018
ms.locfileid: "31476721"
---
# <a name="unable-to-attach-to-the-process"></a>İşleme İliştirilemiyor
İşleme eklenemiyor. Hata ayıklayıcı bileşen sunucuda bu makineye bağlanırken erişim aldı.  
  
 Bu hataya neden iki yaygın senaryolar şunlardır:  
  
 **Senaryo 1:** makine bir Windows XP çalıştıran. Makine B, Windows Server 2003 çalışıyor. Kayıt defteri makine B üzerinde aşağıdaki DWORD değerini içerir:  
  
 `HKLM\Software\Microsoft\MachineDebugManager\AllowLaunchAsOtherUser=1`  
  
 Kullanıcı 1 B makinede Terminal sunucusu oturumu (oturumu 1) başlatır ve yönetilen bir uygulamanın bu oturumu başlatır.  
  
 Her iki makinede yönetici olan, kullanıcı 2, makine A. günlüğe kaydedilir Buradan, makine b 1 oturumunda çalışan bir uygulama eklemek çözemiyorsa çalışır  
  
 **Senaryo 2:** bir kullanıcı oturum makinelere iki, A ve B, aynı çalışma grubundaki her iki makinelerde aynı parola kullanarak. Hata ayıklayıcı bir makinede çalışıyor ve makine B. makine A'da çalıştıran yönetilen uygulamayı ekleme çalışılırken sahip **ağ erişimi: Yerel hesaplar için paylaşım ve güvenlik modeli** kümesine **Konuk**.  
  
### <a name="to-solve-scenario-1"></a>Senaryo 1 çözmek için  
  
-   Hata ayıklayıcı ve aynı kullanıcı hesabı adı ve parola altında yönetilen uygulamayı çalıştırın.  
  
### <a name="to-solve-scenario-2"></a>Senaryo 2 çözmek için  
  
1.  Gelen **Başlat** menüsünde seçin **Denetim Masası**.  
  
2.  Denetim Masası'nda çift **Yönetimsel Araçlar**.  
  
3.  Yönetimsel Araçlar penceresinde çift **yerel güvenlik ilkesi**.  
  
4.  Yerel Güvenlik İlkesi penceresinde seçin **yerel ilkeler**.  
  
5.  İçinde **ilkeleri** sütun, çift **ağ erişimi: Yerel hesaplar için paylaşım ve güvenlik modeli**.  
  
6.  İçinde **ağ erişimi: Yerel hesaplar için paylaşım ve güvenlik modeli** iletişim kutusunda, yerel güvenlik ayarını **Klasik**, tıklatıp **Tamam**.  
  
    > [!CAUTION]
    >  Güvenlik modeli Klasik olarak değiştirme paylaşılan dosyalara ve DCOM bileşenleri için beklenmeyen erişimle sonuçlanabilir. Bu değişiklik yaparsanız, uzak bir kullanıcı, yerel kullanıcı hesabı yerine ile Konuk doğrulayabilir. Uzak bir kullanıcı, kullanıcı adınızı ve parolanızı eşleşiyorsa, bu kullanıcının herhangi bir klasör veya DCOM nesnesi çıkışı paylaştığınız erişebilir olacaktır. Bu güvenlik modelini kullanırsanız, makinedeki tüm kullanıcı hesaplarının güçlü parolalar sahip veya hata ayıklama için bir yalıtılmış ağ Adası ayarlama ve yetkisiz erişimi önlemek için makineler hata ayıklaması emin olun.  
  
7.  Tüm pencereleri kapatın.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Hata ayıklayıcı ayarları ve hazırlığı](../debugger/debugger-settings-and-preparation.md)