---
title: 'Hata: Hedef bilgisayardaki Visual Studio Uzaktan Hata Ayıklayıcı hizmeti geriye bu bilgisayara bağlanamıyor'
titleSuffix: ''
ms.custom: seodec18
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: troubleshooting
f1_keywords:
- vs.debug.error.service_access_denied_oncallback
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
ms.openlocfilehash: 37caaea1f70771145f318d892025d566a99f4ea6
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53062628"
---
# <a name="error-the-visual-studio-remote-debugger-service-on-the-target-computer-cannot-connect-back-to-this-computer"></a>Hata: Hedef bilgisayardaki Visual Studio Uzaktan Hata Ayıklayıcı hizmeti geriye bu bilgisayara bağlanamıyor
Bu hata, Visual Studio uzaktan hata ayıklayıcı hizmeti hata ayıklaması yaptığınız bilgisayarda bağlanmayı denediğinde doğrulayamayan bir kullanıcı hesabı altında çalıştığından emin anlamına gelir.  
  
 Aşağıdaki tabloda neler hesapları erişeceği gösterilmektedir bilgisayar:  
  
|||||  
|-|-|-|-|  
||LocalSystem hesabı|Etki alanı hesabı|Her iki bilgisayarda aynı kullanıcı adı ve parola sahip yerel hesaplar|  
|Her iki bilgisayar aynı etki alanında|Evet|Evet|Evet|  
|Her iki bilgisayarda çift yönlü güven bulunan etki alanları|Hayır|Hayır|Evet|  
|Bir çalışma grubunda bir veya her iki bilgisayar|Hayır|Hayır|Evet|  
|Farklı etki alanlarında bilgisayarları|Hayır|Hayır|Evet|  
  
 Bunlara ek olarak:  
  
-   Herhangi bir işlem hata ayıklama Visual Studio uzaktan hata ayıklayıcı hizmetin altında çalışacağı hesabın uzak bilgisayarda bir yönetici olmalıdır.  
  
-   Hesabın ayrıca verilecek sahip `Log on as a service` kullanan uzak bilgisayardaki ayrıcalığını **yerel güvenlik ilkesi** yönetim aracı.  
  
-   Bir yerel hesap erişim bilgisayarı kullanıyorsanız, yerel bir hesap altında Visual Studio uzaktan hata ayıklayıcı hizmeti çalıştırmanız gerekir.  
  
### <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
1.  Visual Studio uzaktan hata ayıklayıcı hizmeti uzak bilgisayarda doğru ayarlandığından emin olun. Daha fazla bilgi için [uzaktan hata ayıklama](../debugger/remote-debugging.md).  
  
2.  Hata ayıklayıcısı ana bilgisayar erişimi olan bir hesabı altında uzaktan hata ayıklayıcı hizmeti, önceki tabloda gösterildiği gibi çalıştırın.  
  
### <a name="to-add-log-on-as-a-service-privilege"></a>"Hizmet olarak oturum aç" ayrıcalığı eklemek için  
  
1.  Üzerinde **Başlat** menüsünde seçin **Denetim Masası**.  
  
2.  Denetim Masası'ndaki seçin **Klasik Görünüm**, gerekirse.  
  
3.  **Yönetim Araçları**'na çift tıklayın.  
  
4.  Yönetimsel Araçlar penceresinde, **yerel güvenlik ilkesi**.  
  
5.  İçinde **yerel güvenlik ayarları** penceresini genişletin **yerel ilkeler** klasör.  
  
6.  Tıklayın **kullanıcı hakları ataması**.  
  
7.  İçinde **ilke** sütunu, çift tıklayın **hizmet olarak oturum açın** geçerli yerel Grup İlkesi atamalarını görüntülemek için **hizmet oturum açma** iletişim kutusu.  
  
8.  Yeni kullanıcı eklemek için tıklatın **kullanıcı veya Grup Ekle** düğmesi.  
  
9. Kullanıcı ekleme işlemini tamamladığınızda, tıklayın **Tamam**.  
  
### <a name="to-work-around-this-error"></a>Bu hatayı çözmek için  
  
-   Hizmet yerine bir uygulama olarak uzaktan hata ayıklama İzleyicisi'ni çalıştırın.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Uzaktan hata ayıklama ve sorun giderme](../debugger/remote-debugging-errors-and-troubleshooting.md)   
 [Uzaktan Hata Ayıklama](../debugger/remote-debugging.md)