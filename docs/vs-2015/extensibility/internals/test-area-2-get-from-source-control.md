---
title: 'Test alanı 2: Kaynak denetiminden almak | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- source control plug-ins, getting items from source control
- source control [Visual Studio SDK], getting items from
ms.assetid: cbd345c5-ca43-4630-b7a4-85564f4e2090
caps.latest.revision: 19
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 96b00cfc9965b6006fa51b3cd313566658d604bd
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51786164"
---
# <a name="test-area-2-get-from-source-control"></a>Test Alanı 2: Kaynak Denetiminden Alma
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Bu test alanı Get komutu aracılığıyla sürüm deposundan öğeleri almak için test çalışmaları kapsar. Bu test çalışmaları, yerel ve Web projeleri için uygulanabilir.  
  
## <a name="command-menu-access"></a>Komut menü erişimi  
 Aşağıdaki [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] tümleşik geliştirme ortamı menüsü yolları test durumlarında kullanılır.  
  
##### <a name="get-latest-version"></a>En son sürümü Al:  
  
-   **Dosya**, **kaynak denetimi**, **en son sürümü Al**.  
  
-   **Dosya**, **en son sürümü Al**.  
  
-   Kısayol menüsünde, **en son sürümü Al**.  
  
-   Get: **dosya**, **kaynak denetimi**, **alma**.  
  
## <a name="expected-behavior"></a>Beklenen davranış  
  
##### <a name="get-latest-version"></a>En son sürümü Al:  
 Bir öğenin en son sürümünü (kullanıcı Arabirimi) Sessiz alınmasını sürüm Mağazası'ndan gerçekleştirir.  
  
##### <a name="get"></a>Al:  
 Görüntüler **alma** iletişim kutusu ve kullanıcının değişiklik alınır yanı sıra dosyaların nasıl alınır etkileyen seçenekleri değiştirmek, dosya kümesine izin verir.  
  
## <a name="test-cases"></a>Test çalışmaları  
  
|Eylem|Test adımları|Beklenen sonuçları doğrulamak için|  
|------------|----------------|--------------------------------|  
|Yerel olarak mevcut olmayan bir dosyanın en son sürümü Al|1.  Bir proje oluşturun.<br />2.  Projeye bir öğe ekleyin.<br />3.  Projenin kaynak denetimi altına yerleştirin.<br />4.  Öğenin yerel kopyasını silin.<br />5.  Öğenin en son sürümü Al (kısayol menüsünde, **en son sürümü Al**).|Öğesi dosyasını yerel olarak alınır.|  
|Yerel olarak mevcut olmayan bir dosya alın|1.  Bir proje oluşturun.<br />2.  Projeye bir öğe ekleyin.<br />3.  Projenin kaynak denetimi altına yerleştirin.<br />4.  Öğenin yerel kopyasını silin.<br />5.  Öğe alma (**dosya**, **kaynak denetimi**, **alma** \<öğesi >).|Öğesi dosyasını yerel olarak alınır.|  
|Özel olarak kullanıma ve yerel olarak değiştiren bir dosya alın|1.  Bir proje oluşturun.<br />2.  Projeye bir öğe ekleyin.<br />3.  Projenin kaynak denetimi altına yerleştirin.<br />4.  Proje öğesi özel kontrol edin.<br />5.  Yerel kopya değiştirin.<br />6.  Öğenin en son sürümü Al (**dosya**, **en son sürümü Al** \<öğesi >). Bu adım başarılı olursa, sonraki adıma geçin.<br />7.  Tıklayın **değiştirin** uyarı iletişim kutusunda düğmesi.|**6. adımdan reResult** `:`<br /><br /> Uyarı iletişim kutusunda, bu dosya kullanıma gösterir.<br /><br /> **7. adımdan reResult:**<br /><br /> Değiştirilen yerel dosya sürümü Mağazası'ndan özgün sürümle değiştirilir.<br /><br /> Okuma/yazma dosyasıdır.|  
|Alma ve kullanıma, paylaşılan ve yerel olarak değiştirilen dosya değiştirin|1.  Yeni bir proje oluşturun.<br />2.  Projeye bir öğe ekleyin.<br />3.  Projenin kaynak denetimi altına yerleştirin.<br />4.  Proje öğesi paylaşılan olarak göz atın.<br />5.  Yerel kopya değiştirin.<br />6.  Öğenin en son sürümü Al (**dosya**, **en son sürümü Al** \<öğesi >). Bu adım başarılı olursa, sonraki adıma geçin.<br />7.  Tıklayın **değiştirin** uyarı iletişim kutusunda.|**6. adımdan sonuç:**<br /><br /> Uyarı iletişim kutusunda, bu dosya kullanıma gösterir.<br /><br /> **7. adımdan sonuç:**<br /><br /> Değiştirilen yerel dosya sürümü Mağazası'ndan özgün sürümle değiştirilir.<br /><br /> Okuma/yazma dosyasıdır.|  
|Yerel olarak mevcut bir dosyayı aynı sürüm deposuna en son sürümü Al|1.  Yeni bir proje oluşturun.<br />2.  Projeye bir öğe ekleyin.<br />3.  Projenin kaynak denetimi altına yerleştirin.<br />4.  Öğe alma (**dosya**, **kaynak denetimi**, **alma** \<öğesi >).|Yerel dosya değiştirilmez.|  
|Bir proje içeren bir çözümünü edinme|1.  Bir çözümü ile bir proje oluşturun.<br />2.  Çözüm kaynak denetimi altına yerleştirin.<br />3.  Tüm proje dosyaları yerel olarak sil.<br />4.  Çözümünü edinme (**dosya**, **kaynak denetimi**, **alma**).|Tüm silinen dosyaları yerel olarak geri yüklenir.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Kaynak Denetimi Eklentileri için Test Kılavuzu](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)

