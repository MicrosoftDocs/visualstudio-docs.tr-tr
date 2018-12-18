---
title: 'Nasıl yapılır: grafik tanılama kayıttan yürütme makinesini değiştirme | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1b9aa3ea-29a0-4e21-bc57-936f33537b5c
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a2d5d56d37bbed4180d1231cac54da6beff3418d
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51737603"
---
# <a name="how-to-change-the-graphics-diagnostics-playback-machine"></a>Nasıl Yapılır: Grafik Tanılama Kayıttan Yürütme Makinesini Değiştirme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Yerel makinenizi kullanarak veya bir uzak makine ya da aygıt kullanarak grafik bilgilerini kayıttan yürütme.  
  
## <a name="choosing-a-playback-machine"></a>Kayıttan yürütme makinesi seçme  
 Kayıttan yürütme makinesi, bir makine ya da bir grafik günlüğünden grafik olaylarını kayıttan yürütmek için kullanılan cihaz ' dir. Genellikle yerel makine en kullanışlı seçenektir, ancak oluşturma sorununun nerede yakalanan farklı donanım veya sürücü sürümlerine makine sahip bir makinede oluşturma değil; Bu durumda, sorunu daha iyi yakalandığı bir uzak kayıttan yürütme makinesi seçebilir ve tanılamak için geliştirme makinenizi kullanmaya devam edebilirsiniz.  
  
#### <a name="to-use-the-local-machine-to-play-back-graphics-information"></a>Grafik bilgilerini kayıttan çalıştırmak üzere yerel makine kullanmak için  
  
1.  Grafik günlüğü belge penceresinde seçin **kayıttan yürütme makinesi** bağlantı. **Uzaktan hata ayıklayıcı bağlantıları** iletişim kutusu görüntülenir.  
  
2.  Altında **el ile yapılandırma**, **adresi** özelliği girin `localhost`.  
  
3.  Ayarlama **kimlik doğrulama modu** özelliğini **hiçbiri**.  
  
4.  Seçin **seçin** düğmesi.  
  
#### <a name="to-use-a-remote-machine-to-play-back-graphics-information"></a>Grafik bilgilerini kayıttan çalıştırmak üzere uzak bir makineyi kullanmak için  
  
1.  Grafik günlüğü belge penceresinde seçin **kayıttan yürütme makinesi** bağlantı. **Uzaktan hata ayıklayıcı bağlantıları** iletişim kutusu görüntülenir.  
  
2.  Altında **el ile yapılandırma**, **adresi** özelliği, Windows etki alanı adı veya makine ya da grafik bilgilerini kayıttan çalıştırmak üzere kullanmak istediğiniz cihazın IP adresini girin.  
  
3.  Yürütme makinesine bağlantıyı güvenli hale getirmek için kullanmak istediğiniz yetkilendirme türünü belirtin.  
  
    -   Windows kimlik doğrulaması için ayarlanmış **kimlik doğrulama modu** özelliğini **Windows**.  
  
    -   Kimlik doğrulaması için ayarlanmış **kimlik doğrulama modu** özelliğini **hiçbiri**.  
  
4.  Seçin **seçin** düğmesi.  
  
> [!NOTE]
>  **Uzaktan hata ayıklayıcı bağlantıları** iletişim kutusu, geliştirme makinenize doğrudan bağlı olan veya aynı alt ağda olan uzaktan hata ayıklama hedefleri de görüntüleyebilir. Bu uzaktan hata ayıklama hedeflerinden birini grafik tanılama kayıttan yürütme makinesi el ile yapılandırma olmadan kullanabilirsiniz. İçinde **uzaktan hata ayıklayıcı bağlantıları** iletişim kutusunda, istediğiniz ve ardından hedef seçin **seçin** düğmesi.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Grafik Günlük Belgesi](../debugger/graphics-log-document.md)



