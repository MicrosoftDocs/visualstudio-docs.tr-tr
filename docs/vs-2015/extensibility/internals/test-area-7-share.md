---
title: 'Test alanı 7: Paylaşma | Microsoft Docs'
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
- source control [Visual Studio SDK], sharing items
- source control plug-ins, sharing items
ms.assetid: 6ec4780a-bda4-4327-bb3e-c6c9e7eabf35
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e9389d03da7c4e4b763e979a721a22639ecb9fbe
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51796928"
---
# <a name="test-area-7-share"></a>Test Alanı 7: Paylaşma
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Bu test alanı konumlar arasında paylaşım öğelerini kapsar **paylaşımı** komutu.  
  
 Dosya ve klasör öğeleri kaynak denetim dosyası hiyerarşi içinde en az iki konum arasında belirgin çoğaltma hhare işlemdir. Çoğaltma sunucusunda gerçekten oluşmaz, ancak kullanıcının aynı dosyanın iki veya daha fazla belirtilen konumlarda bakın. Herhangi bir paylaşılan öğeyi değişiklik yapıldığında, bu değişiklikleri diğer paylaşılan tüm konumlardaki görünür.  
  
 En az bir dosya içindeki kaynak denetimi altında bir klasör seçerseniz klasörler halinde paylaşımı çalışır. Paylaş komutunu aşağıdaki koşullarda devre dışı bırakılır:  
  
-   Seçili klasörü boş bir klasör ise.  
  
-   Gerçek bir klasör bulunur, ancak hiçbir kaynak denetim dosyaları içerir.  
  
-   Sanal bir klasör varsa, kaynak denetimi altında dosyaların içinde veya olup.  
  
-   Bir uzak Site Web projesi varsa.  
  
## <a name="command-menu-access"></a>Komut menü erişimi  
 Aşağıdaki [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] tümleşik geliştirme ortamı menüsü yolları test durumlarında kullanılır.  
  
 Paylaşımı: **dosya**->**kaynak denetimi**->**paylaşımı**.  
  
## <a name="expected-behavior"></a>Beklenen davranış  
  
-   Paylaşılan dosya, paylaşılan bir konumda görüntülenir.  
  
-   Dosyaları paylaşılır kaynak denetim sürüm deposu geçmişini gösterir görüntüleme.  
  
-   Paylaşılan bir dosya düzenleme dosyası konumlarının her ikisinde de düzenler.  
  
## <a name="test-cases"></a>Test çalışmaları  
 Belirli test çalışmaları için paylaşımı test alanı aşağıda verilmiştir.  
  
|Eylem|Test adımları|Beklenen sonuçları doğrulamak için|  
|------------|----------------|--------------------------------|  
|Yüklü başka bir proje için kaynak denetimi altında yüklü bir projeden bir dosya paylaşımı|1.  Yeni bir proje oluşturun.<br />2.  İkinci bir proje ekleyin.<br />3.  İkinci projedeki ilk projede yer almayan bir ada sahip bir dosya oluşturun.<br />4.  Çözüm kaynak denetimine ekleyin.<br />5.  İlk projenizi seçin.<br />6.  Açık **paylaşımı** iletişim kutusu (**dosya** -> **kaynak denetimi** -> **paylaşımı**).<br />7.  İlk proje dosyasına ikinci projeden paylaşın.<br />8.  Kabul **kullanıma** istenirse.|Ortak beklenen bir davranış.|  
|Diğer bir projeden bir dosya paylaşımı|1.  Yeni bir proje oluşturun.<br />2.  Kaynak denetimine ekleyin.<br />3.  Çözümü kapatın.<br />4.  İkinci (yeni çözüm). proje oluşturma<br />5.  Çözüm kaynak denetimine ekleyin.<br />6.  Projeyi seçin.<br />7.  Açık **paylaşımı** iletişim kutusu (**dosya** -> **kaynak denetimi** -> **paylaşımı**).<br />8.  Açık projeye önceden eklenen projeden bir dosya paylaşımı.<br />9. Kabul **kullanıma** istenirse.|Ortak beklenen bir davranış.|  
|Yüklü projeye projeyi kaynak denetiminden parçası olmayan bir dosya paylaşımı|1.  Yeni bir proje oluşturun.<br />2.  Çözüm kaynak denetimine ekleyin.<br />3.  Bir dosya proje veya çözümün bir parçası değil. kaynak denetimine ekleyin.<br />4.  Projeyi seçip açın **paylaşımı** iletişim kutusu (**dosya** -> **kaynak denetimi** -> **paylaşımı**).<br />5.  İçinde bir dosya seçin **paylaşmak** iletişim kutusu geçerli proje veya çözüm içinde mevcut değil, dosya paylaşın.<br />6.  Kabul **kullanıma** istenirse.|Dosya artık yerel proje konumunda, bu nedenle, kaynak denetim deposunda bir Get gerçekleştirdi.|  
|Aynı projeye farklı bir klasör içinde dosya paylaşma|1.  Seçin **otomatik olarak kullanıma** içinde **Araçları** -> **seçenekleri** -> **kaynak denetimi**.<br />2.  Yeni bir proje oluşturun ve kaynak denetimine ekleyin.<br />3.  Bir klasörü projeye ekleyin.<br />4.  Klasörüne bir dosya ekleyin ve klasörde denetleyin.<br />5.  Klasörü seçin.<br />6.  Açık **paylaşımı** iletişim kutusu (**dosya** -> **kaynak denetimi** -> **paylaşımı**).<br />7.  Seçilen klasöre dosya paylaşımı.|Ortak beklenen bir davranış.<br /><br /> Paylaşım için kullanılmadan önce bir dosyada oturum klasör denetlenmesi gerekir.|  
|Yüklenen projeye bir klasör paylaşma-özyinelemeli|1.  Yeni bir proje oluşturun.<br />2.  Çözüm kaynak denetimine ekleyin.<br />3.  Projeyi seçin.<br />4.  Açık **paylaşımı** iletişim kutusu (**dosya** -> **kaynak denetimi** -> **paylaşımı**).<br />5.  Bir klasör seçin.<br />6.  Klasör yinelemeli olarak projeye paylaşın.|Ortak beklenen bir davranış.|  
|Bir projeden diğerine çeşitli dosyaları paylaşma|1.  Çeşitli dosyaları ile yeni bir proje oluşturun.<br />2.  Çözüm kaynak denetimine ekleyin.<br />3.  Çözümü kapatın.<br />4.  Yeni bir proje içinde yeni bir çözüm oluşturun.<br />5.  Çözüm kaynak denetimine ekleyin.<br />6.  Projeyi seçin.<br />7.  Açık **paylaşımı** iletişim kutusu (**dosya** -> **kaynak denetimi** -> **paylaşımı**).<br />8.  Açık olan proje için önceden oluşturulmuş projeden birkaç dosyalarını paylaşın.|Ortak beklenen bir davranış.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Kaynak Denetimi Eklentileri için Test Kılavuzu](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)

