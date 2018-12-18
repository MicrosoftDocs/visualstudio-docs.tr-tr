---
title: 'Nasıl yapılır: grafik tanılama kayıttan yürütme makinesini değiştirme | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 1b9aa3ea-29a0-4e21-bc57-936f33537b5c
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 143ae65b8d7db584546c250bf5d032450bf220aa
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2018
ms.locfileid: "31473877"
---
# <a name="how-to-change-the-graphics-diagnostics-playback-machine"></a>Nasıl Yapılır: Grafik Tanılama Kayıttan Yürütme Makinesini Değiştirme
Grafik bilgilerini yerel makinenize veya bir uzak makine ya da cihaz kullanarak geri yürütebilirsiniz.  
  
## <a name="choosing-a-playback-machine"></a>Kayıttan yürütme makinesini seçme  
 Kayıttan yürütme makinesini makine ya da bir grafik günlüğündeki grafik olaylar çalmak için kullanılan aygıt ' dir. Genellikle, yerel makine en uygun seçenektir ancak bir işleme sorun nerede yakalanan farklı bir donanım veya sürücü sürümlerini sayısından olduğu bir makineye oluşturmak değildir; Bu durumda, sorunu daha iyi oluşmazsa bir uzak kayıttan yürütme makinesini seçin ve hala bu tanılamak için geliştirme makinenizde kullanın.  
  
#### <a name="to-use-the-local-machine-to-play-back-graphics-information"></a>Grafik bilgilerini çalmak için yerel makine kullanmak için  
  
1.  Grafik günlük belgesi penceresinde, seçin **kayıttan yürütme makinesini** bağlantı. **Uzaktan hata ayıklayıcı bağlantıları** iletişim kutusu görüntülenir.  
  
2.  Altında **el ile yapılandırma**, **adresi** özelliği girin `localhost`.  
  
3.  Ayarlama **kimlik doğrulama modu** özelliğine **hiçbiri**.  
  
4.  Seçin **seçin** düğmesi.  
  
#### <a name="to-use-a-remote-machine-to-play-back-graphics-information"></a>Grafik bilgilerini çalmak için bir uzak makine kullanmak için  
  
1.  Grafik günlük belgesi penceresinde, seçin **kayıttan yürütme makinesini** bağlantı. **Uzaktan hata ayıklayıcı bağlantıları** iletişim kutusu görüntülenir.  
  
2.  Altında **el ile yapılandırma**, **adresi** özelliği, Windows etki alanı adı veya IP adresini Makine ya da grafik bilgilerini çalmak için kullanmak istediğiniz aygıt girin.  
  
3.  Kayıttan yürütme makinesini bağlantısı güvenliğini sağlamak için kullanmak istediğiniz yetkilendirme türünü belirtin.  
  
    -   Windows kimlik doğrulaması için ayarlanmış **kimlik doğrulama modu** özelliğine **Windows**.  
  
    -   Hiçbir kimlik doğrulamasını ayarlamak **kimlik doğrulama modu** özelliğine **hiçbiri**.  
  
4.  Seçin **seçin** düğmesi.  
  
> [!NOTE]
>  **Uzaktan hata ayıklayıcı bağlantıları** iletişim kutusu, aynı alt ağda geliştirme makinenizde doğrudan bağlı ya da uzaktan hata ayıklama hedeflerini de görüntülenebilir. Bu uzaktan hata ayıklama hedeflerini birini el ile yapılandırma olmadan grafik tanılama kayıttan yürütme makinesini kullanabilirsiniz. İçinde **uzaktan hata ayıklayıcı bağlantıları** iletişim kutusunda, istediğiniz ve ardından hedef seçin **seçin** düğmesi.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Grafik Günlük Belgesi](graphics-log-document.md)