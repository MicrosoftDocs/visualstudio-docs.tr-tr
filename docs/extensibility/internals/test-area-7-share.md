---
title: 'Test alanı 7: Paylaşma | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], sharing items
- source control plug-ins, sharing items
ms.assetid: 6ec4780a-bda4-4327-bb3e-c6c9e7eabf35
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: fa74d6ff2291288a1ca0e7f17a2edb1e126f222b
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31142474"
---
# <a name="test-area-7-share"></a>Test alanı 7: paylaşımı
Bu test alanını paylaşım öğeleri konumları arasında kapsayan **paylaşımı** komutu.  
  
 Dosya ve klasör öğesi bir kaynak denetimi dosya hiyerarşisi içinde iki veya daha fazla konumlar arasında görünen çoğaltılmasını hhare işlemdir. Çoğaltma sunucusunda gerçekten oluşmaz, ancak kullanıcı aynı dosya iki veya daha fazla belirli konumlara bakın. Herhangi bir paylaşılan öğeleri için yapılan bir değişiklik olduğunda, bu değişiklikler diğer paylaşılan tüm konumlarda görünür.  
  
 Kaynak denetiminde altında en az bir dosya ile bir klasör seçin klasörler halinde paylaşımı çalışır. Share komutunu aşağıdaki koşullarda devre dışı bırakılır:  
  
-   Seçilen klasör boş bir klasör ise.  
  
-   Gerçek bir klasör yoktur, ancak hiçbir kaynak denetim dosyalarını içeren durumunda.  
  
-   Sanal bir klasör ise, kaynak denetimindeki dosyalarla içinde veya olup.  
  
-   Bir uzak Site Web projesi ise.  
  
## <a name="command-menu-access"></a>Komut menü erişimi  
 Aşağıdaki [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] tümleşik geliştirme ortamı menü yolları test çalışmaları kullanılır.  
  
 Paylaşım: **dosya**->**kaynak denetimi**->**paylaşımı**.  
  
## <a name="expected-behavior"></a>Beklenen bir davranış  
  
-   Paylaşılan dosya paylaşılan konumda görüntülenir.  
  
-   Dosyaların paylaşıldığı kaynak denetimi sürüm deposu geçmişini gösterir görüntüleme.  
  
-   Paylaşılan dosya düzenleme dosyası konumlarının her ikisinde de düzenler.  
  
## <a name="test-cases"></a>Test çalışmaları  
 Belirli test çalışmaları paylaşımı test alanı için verilmiştir.  
  
|Eylem|Test adımları|Doğrulamak için beklenen sonuçları|  
|------------|----------------|--------------------------------|  
|Kaynak denetimi altında bir yüklenen proje dosyasından yüklenen başka bir projeye paylaşma|1.  Yeni bir proje oluşturun.<br />2.  İkinci bir proje çözüme ekleyin.<br />3.  İkinci projesinde ilk projesinde değil bir ada sahip bir dosya oluşturun.<br />4.  Çözümü kaynak denetimine ekleyin.<br />5.  İlk projesini seçin.<br />6.  Açık **paylaşımı** iletişim kutusu (**dosya** -> **kaynak denetimi** -> **paylaşımı**).<br />7.  İkinci projeden ilk proje için dosya paylaşımı.<br />8.  Kabul **kullanıma** istenirse.|Ortak beklenen davranıştır.|  
|Bir projeye ait başka bir dosya paylaşımı|1.  Yeni bir proje oluşturun.<br />2.  Kaynak denetimine ekleyin.<br />3.  Çözümü kapatın.<br />4.  (Yeni çözüm.) ikinci bir proje oluşturun<br />5.  Çözümü kaynak denetimine ekleyin.<br />6.  Projeyi seçin.<br />7.  Açık **paylaşımı** iletişim kutusu (**dosya** -> **kaynak denetimi** -> **paylaşımı**).<br />8.  Daha önce eklenen proje dosyasından açık projeye paylaşır.<br />9. Kabul **kullanıma** istenirse.|Ortak beklenen davranıştır.|  
|Şu anda yüklenen projeye proje kaynak denetiminden parçası olmayan dosya paylaşımı|1.  Yeni bir proje oluşturun.<br />2.  Çözümü kaynak denetimine ekleyin.<br />3.  Proje ve çözüm parçası olmayan kaynak denetimi için bir dosya ekleyin.<br />4.  Projeyi seçip açın **paylaşımı** iletişim kutusu (**dosya** -> **kaynak denetimi** -> **paylaşımı**).<br />5.  İçinde bir dosya seçin **paylaşmak** geçerli proje ya da çözüm içinde mevcut ve paylaşın iletişim kutusu.<br />6.  Kabul **kullanıma** istenirse.|Böylece dosyayı şimdi projesinin yerel konumda kaynak denetim deposunu bir Get gerçekleştirdi.|  
|Farklı bir klasöre aynı projedeki dosyaları paylaşma|1.  Seçin **otomatik olarak kullanıma** içinde **Araçları** -> **seçenekleri** -> **kaynak denetimi**.<br />2.  Yeni bir proje oluşturun ve kaynak denetimine ekleyin.<br />3.  Bir klasörü projeye ekleyin.<br />4.  Bir dosya klasörüne ekleyip klasörü denetleyin.<br />5.  Klasörü seçin.<br />6.  Açık **paylaşımı** iletişim kutusu (**dosya** -> **kaynak denetimi** -> **paylaşımı**).<br />7.  Seçilen klasör için dosya paylaşımı.|Ortak beklenen davranıştır.<br /><br /> Paylaşım için kullanılabilmesi için önce bir dosyada oturum klasör denetlenmesi gerekir.|  
|Bir klasörü yüklenen projeye paylaşmak — özyinelemeli|1.  Yeni bir proje oluşturun.<br />2.  Çözümü kaynak denetimine ekleyin.<br />3.  Projeyi seçin.<br />4.  Açık **paylaşımı** iletişim kutusu (**dosya** -> **kaynak denetimi** -> **paylaşımı**).<br />5.  Bir klasör seçin.<br />6.  Klasör yinelemeli olarak projeye paylaşır.|Ortak beklenen davranıştır.|  
|Bir projeye ait birden fazla dosya başka bir paylaşma|1.  Birkaç dosyalarında ile yeni bir proje oluşturun.<br />2.  Çözümü kaynak denetimine ekleyin.<br />3.  Çözümü kapatın.<br />4.  Yeni bir çözüme yeni bir proje oluşturun.<br />5.  Çözümü kaynak denetimine ekleyin.<br />6.  Projeyi seçin.<br />7.  Açık **paylaşımı** iletişim kutusu (**dosya** -> **kaynak denetimi** -> **paylaşımı**).<br />8.  Önceden oluşturulmuş projeye ait birden fazla dosya açık projeye paylaşır.|Ortak beklenen davranıştır.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Kaynak Denetimi Eklentileri için Test Kılavuzu](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)