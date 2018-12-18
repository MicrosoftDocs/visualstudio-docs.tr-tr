---
title: 'Hata: Hata ayıklama birincile&#39;olası bir çekirdek hata ayıklayıcısı sistemde etkin olduğundan t | Microsoft Docs'
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
- vs.debug.error.kernel_dbg_enabled
dev_langs:
- FSharp
- VB
- CSharp
- C++
- VB
- CSharp
- C++
helpviewer_keywords:
- kernel debugger
ms.assetid: 630a7abd-3303-4aaa-888a-6de3de14bc01
caps.latest.revision: 26
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: eea2e7d8277bc67df75be3d05d907a8bd13c29c5
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51725284"
---
# <a name="error-debugging-isn39t-possible-because-a-kernel-debugger-is-enabled-on-the-system"></a>Hata: Hata ayıklama birincile&#39;olası bir çekirdek hata ayıklayıcısı sistemde etkin olduğundan t
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Yönetilen kod hata ayıklaması yaparken, aşağıdaki hata iletisini alabilirsiniz:  
  
```  
Debugging isn't possible because a kernel debugger is enabled on the system  
```  
  
 Yönetilen kod hata ayıklamayı denediğinizde bu ileti oluşur:  
  
-   üzerinde bir [!INCLUDE[win7](../includes/win7-md.md)] veya [!INCLUDE[wiprlhext](../includes/wiprlhext-md.md)]hata ayıklama modunda çalışmaya sistem.  
  
-   Uygulama, CLR 2.0, 3.0 veya 3.5 CLR sürümünü kullanır.  
  
## <a name="solution"></a>Çözüm  
  
#### <a name="to-fix-this-problem"></a>Bu sorunu gidermek için  
  
-   CLR 4.0 veya 4.5 sürümü kullanmak için uygulamanızı yükseltme  
  
     —veya—  
  
-   Çekirdek hata ayıklamasını devre dışı bırak ve hata ayıklayın [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
     —veya—  
  
-   Çekirdek hata ayıklayıcı yerine kullanarak hata ayıklama [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
     —veya—  
  
-   Çekirdek hata ayıklayıcısı kullanıcı modu özel durumlarını devre dışı bırakın.  
  
#### <a name="to-disable-kernel-debugging-in-the-current-session"></a>Geçerli oturumda çekirdek hata ayıklamasını devre dışı bırakmak için  
  
-   Komut isteminde, şunları yazın:  
  
    ```  
    Kdbgctrl.exe -d  
    ```  
  
#### <a name="to-disable-kernel-debugging-for-all-sessions-windows-vista-and-windows-7"></a>Tüm oturumlardaki (Windows Vista ve Windows 7) çekirdek hata ayıklamasını devre dışı bırakmak için  
  
1.  Komut isteminde, şunları yazın:  
  
    ```  
    bcdedit /debug off   
    ```  
  
2.  Bilgisayarı yeniden başlatın.  
  
#### <a name="to-disable-kernel-debugging-for-all-sessions-other-windows-operating-systems"></a>Tüm oturumlardaki (diğer Windows işletim sistemleri) çekirdek hata ayıklamasını devre dışı bırakmak için  
  
1.  Sistem sürücünüzde Boot.ini bulun (genellikle C:\\). Boot.ini dosyası, gizli ve salt okunur olabilir. Bu nedenle, görmek için aşağıdaki komutu kullanmanız gerekir:  
  
    ```  
    dir /ASH  
    ```  
  
2.  Not Defteri'ni kullanarak boot.ini açın ve aşağıdaki seçenekleri kaldırın:  
  
    ```  
    /debug  
    /debugport  
    /baudrate  
    ```  
  
3.  Bilgisayarı yeniden başlatın.  
  
#### <a name="to-debug-with-the-kernel-debugger"></a>Çekirdek hata ayıklayıcısı ile hata ayıklamak için  
  
1.  Çekirdek hata ayıklayıcısı ölçekledikçe, hatalarını ayıklamaya devam etmek isteyip istemediğinizi soran bir ileti görürsünüz. Devam etmek için düğmeye tıklayın.  
  
2.  Alma bir `User break exception(Int 3).` bu meydana gelirse, hatalarını ayıklamaya devam etmek için aşağıdaki çekirdek hata ayıklayıcısı komutu yazın:  
  
     `gn`  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Hata ayıklayıcısı güvenliği](../debugger/debugger-security.md)   
 [Yönetilen Kodda Hata Ayıklama](../debugger/debugging-managed-code.md)



