---
title: İşleme iliştirilemiyor. | Microsoft Docs
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
- vs.debug.remote.unable2attach
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 0468de6c-3ff1-4979-a8c6-8afb53f37547
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f0075050b6d24b63ed8380644ad9ec50dd4aa8ec
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51737662"
---
# <a name="unable-to-attach-to-the-process"></a>İşleme İliştirilemiyor
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

İşleme iliştirilemiyor. Hata ayıklayıcı bileşeni sunucuda bu makineye bağlanırken erişim aldı.  
  
 Bu hataya neden iki yaygın senaryo vardır:  
  
 **Senaryo 1:** makine bir Windows XP çalıştıran. Windows Server 2003 çalıştıran makine B. Makine B üzerinde kayıt defterini, aşağıdaki DWORD değerini içerir:  
  
 `HKLM\Software\Microsoft\MachineDebugManager\AllowLaunchAsOtherUser=1`  
  
 1 kullanıcı Terminal Server oturumunu (oturumu 1) makinede B ve yönetilen bir uygulama bu oturumdan başlayan.  
  
 Her iki makinede yönetici de olan, kullanıcı 2, makine A. kaydediliyor Burada, makine b 1 oturumda çalışan bir uygulamaya eklemek izinli çalışır  
  
 **Senaryo 2:** bir kullanıcı oturum açmışken makinelere iki, A ve B, aynı çalışma grubunda iki makinelerde aynı parola kullanarak. Hata ayıklayıcı bir makine üzerinde çalışan ve makine b makine A üzerinde çalışan yönetilen bir uygulamaya iliştirmeye **ağ erişimi: Yerel hesaplar için paylaşım ve güvenlik modeli** kümesine **Konuk**.  
  
### <a name="to-solve-scenario-1"></a>Senaryo 1 çözmek için  
  
-   Hata ayıklayıcı ve yönetilen uygulama aynı kullanıcı hesabı adı ve parola altında çalıştırın.  
  
### <a name="to-solve-scenario-2"></a>Senaryo 2 çözmek için  
  
1.  Gelen **Başlat** menüsünde seçin **Denetim Masası**.  
  
2.  Denetim Masası'ndaki çift **Yönetimsel Araçlar**.  
  
3.  Yönetimsel Araçlar penceresinde, **yerel güvenlik ilkesi**.  
  
4.  Yerel Güvenlik İlkesi penceresinde **yerel ilkeler**.  
  
5.  İçinde **ilkeleri** sütunu, çift **ağ erişimi: Yerel hesaplar için paylaşım ve güvenlik modeli**.  
  
6.  İçinde **ağ erişimi: Yerel hesaplar için paylaşım ve güvenlik modeli** iletişim kutusunda, yerel güvenlik ayarını **Klasik**, tıklatıp **Tamam**.  
  
    > [!CAUTION]
    >  Güvenlik modeli Klasik olarak değiştirilmesi beklenmeyen Access'te paylaşılan dosyaları ve DCOM bileşenleri için neden olabilir. Bu değişiklik yaparsanız, uzak bir kullanıcı, yerel kullanıcı hesabı yerine ile Konuk kimlik doğrulaması yapabilir. Uzak bir kullanıcı, kullanıcı adınızı ve parolanızı eşleşiyorsa, bu kullanıcı herhangi bir klasör veya DCOM nesne dışarı paylaştığı erişebilir olacaktır. Bu güvenlik modeli kullandığınız makinedeki tüm kullanıcı hesaplarını güçlü parolalar veya hata ayıklama için bir yalıtılmış ağ Adası ayarlama ve yetkisiz erişimi önlemek için makineleri hata ayıklaması emin olun.  
  
7.  Tüm pencereleri kapatın.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Hata Ayıklayıcısı Ayarları ve Hazırlığı](../debugger/debugger-settings-and-preparation.md)



