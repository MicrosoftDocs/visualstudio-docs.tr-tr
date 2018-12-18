---
title: 'Test alanı 2: Kaynak denetiminden alma | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, getting items from source control
- source control [Visual Studio SDK], getting items from
ms.assetid: cbd345c5-ca43-4630-b7a4-85564f4e2090
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 27f2a535b2e08d3632dfd46031823919477fca3e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31133251"
---
# <a name="test-area-2-get-from-source-control"></a>Test alanı 2: Kaynak denetiminden Al
Bu test alan Get komutu aracılığıyla sürüm deposundan öğeleri alınıyor için test durumları kapsar. Bu test çalışmalarını, hem yerel ve Web projeleri için uygulanabilir.  
  
## <a name="command-menu-access"></a>Komut menü erişimi  
 Aşağıdaki [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] tümleşik geliştirme ortamı menü yolları test çalışmaları kullanılır.  
  
##### <a name="get-latest-version"></a>En son sürümünü alın:  
  
-   **Dosya**, **kaynak denetimi**, **en son sürümü Al**.  
  
-   **Dosya**, **en son sürümü Al**.  
  
-   Kısayol menüsünde **en son sürümü Al**.  
  
-   Get: **dosya**, **kaynak denetimi**, **almak**.  
  
## <a name="expected-behavior"></a>Beklenen bir davranış  
  
##### <a name="get-latest-version"></a>En son sürümünü alın:  
 En son sürümü öğenin sessiz (kullanıcı Arabirimi) alma sürüm Mağazası'ndan gerçekleştirir.  
  
##### <a name="get"></a>Al:  
 Görüntüler **Al** iletişim kutusu ve değişiklik alınır yanı sıra dosyaların nasıl alınır etkileyen seçenekleri değiştirmek istediğiniz dosya kümesine izin verir.  
  
## <a name="test-cases"></a>Test çalışmaları  
  
|Eylem|Test adımları|Doğrulamak için beklenen sonuçları|  
|------------|----------------|--------------------------------|  
|Yerel olarak var olmayan bir dosyanın en son sürümünü alın|1.  Bir proje oluşturun.<br />2.  Bir öğe projeye ekleyin.<br />3.  Kaynak denetimi altında proje yerleştirin.<br />4.  Öğenin yerel kopyasını silin.<br />5.  Öğesinin son sürümünü alın (kısayol menüsünde **en son sürümü Al**).|Öğesi dosyasını yerel olarak alınır.|  
|Yerel olarak var olmayan bir dosya alın|1.  Bir proje oluşturun.<br />2.  Bir öğe projeye ekleyin.<br />3.  Kaynak denetimi altında proje yerleştirin.<br />4.  Öğenin yerel kopyasını silin.<br />5.  Öğe alma (**dosya**, **kaynak denetimi**, **almak** \<öğesi >).|Öğesi dosyasını yerel olarak alınır.|  
|Özel olarak kullanıma ve yerel olarak değiştirilen bir dosya alın|1.  Bir proje oluşturun.<br />2.  Bir öğe projeye ekleyin.<br />3.  Kaynak denetimi altında proje yerleştirin.<br />4.  Proje öğesi özel olarak denetleyin.<br />5.  Yerel kopyayı değiştirin.<br />6.  Öğesinin son sürümünü alın (**dosya**, **en son sürümünü almak** \<öğesi >). Bu adım başarılı olursa, sonraki adıma geçin.<br />7.  Tıklatın **Değiştir** uyarı iletişim kutusunda düğme.|**6. adımda reResult** `:`<br /><br /> Uyarı iletişim kutusunda, bu dosya kullanıma gösterir.<br /><br /> **Adım 7 ' reResult:**<br /><br /> Değiştirilmiş yerel dosya sürümü deposundan özgün sürümü ile değiştirilir.<br /><br /> Okuma/yazma dosyasıdır.|  
|Alın ve kullanıma, paylaşılan ve yerel olarak değiştirildi dosyayı değiştir|1.  Yeni bir proje oluşturun.<br />2.  Bir öğe projeye ekleyin.<br />3.  Kaynak denetimi altında proje yerleştirin.<br />4.  Proje öğesi paylaşılan olarak göz atın.<br />5.  Yerel kopyayı değiştirin.<br />6.  Öğesinin son sürümünü alın (**dosya**, **en son sürümünü almak** \<öğesi >). Bu adım başarılı olursa, sonraki adıma geçin.<br />7.  Tıklatın **Değiştir** uyarı iletişim kutusunda.|**6. adımda neden:**<br /><br /> Uyarı iletişim kutusunda, bu dosya kullanıma gösterir.<br /><br /> **Adım 7 neden:**<br /><br /> Değiştirilmiş yerel dosya sürümü deposundan özgün sürümü ile değiştirilir.<br /><br /> Okuma/yazma dosyasıdır.|  
|Yerel olarak mevcut bir dosya sürüm deposu en son sürümü ile aynı alın|1.  Yeni bir proje oluşturun.<br />2.  Bir öğe projeye ekleyin.<br />3.  Kaynak denetimi altında proje yerleştirin.<br />4.  Öğe alma (**dosya**, **kaynak denetimi**, **almak** \<öğesi >).|Yerel dosya değiştirilmez.|  
|Bir proje ile çözümünü edinme|1.  Bir çözümü ile bir proje oluşturun.<br />2.  Kaynak denetimi altında çözüm yerleştirin.<br />3.  Tüm proje dosyalarını yerel olarak silin.<br />4.  Çözümünü edinme (**dosya**, **kaynak denetimi**, **almak**).|Tüm silinen dosyaların yerel olarak geri yüklenir.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Kaynak Denetimi Eklentileri için Test Kılavuzu](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)