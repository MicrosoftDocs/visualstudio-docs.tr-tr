---
title: 'Test alanı 4: İade | Microsoft Docs'
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
- source control [Visual Studio SDK], checking items in
- source control plug-ins, checking items in
ms.assetid: d0329fa8-7a8d-4d30-b67b-6f2a97b75a30
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 97a610325a5165a1de2cc50fede5bbabf182ef5e
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51783312"
---
# <a name="test-area-4-check-in"></a>Test Alanı 4: İade Etme
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Bu kaynak denetimi eklentisi test alanını kapsayan güncelleştirilmiş öğeleri sürüm deposu gönderme **iade** komutu.  
  
## <a name="command-menu-access"></a>Komut menü erişimi  
 Aşağıdaki [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] tümleşik geliştirme ortamı menüsü yolları test durumlarında kullanılır.  
  
##### <a name="check-in"></a>Teslim etme:  
 **Dosya**, **kaynak denetimi**, **iade**.  
  
 **Dosya**, **iade**.  
  
 Kısayol menüsünde, **iade**.  
  
## <a name="common-expected-behavior"></a>Ortak beklenen davranışı  
  
-   Projeleri ve dosyaları bir çözüm veya proje kaynak denetimi altında eklenen görünür **iade** iletişim kutusu ve **Bekleyen İadeler** penceresi.  
  
-   Sonra iade eklenen öğeler kaynak denetiminde görünür.  
  
-   İade etme sonra güncelleştirilmiş öğeleri deposunda düzgün bir şekilde tutulur.  
  
## <a name="test-cases"></a>Test çalışmaları  
 Belirli test çalışmaları için iade etme test alanı aşağıda verilmiştir.  
  
### <a name="case-4a-modified-items"></a>Case 4a: öğeleri değiştirdiği  
 Onay değiştirildi kaynak denetimi altındaki bir dosyayı güncelleştirmek için eylemde kullanmayı açıklar.  
  
|Eylem|Test adımları|Beklenen sonuçları doğrulamak için|  
|------------|----------------|--------------------------------|  
|Kullanıma alınmış bir metin dosyasını değiştirme, dosyayı iade edin (**iade** iletişim kutusu)|1.  Yeni bir proje içeren bir metin dosyası oluşturun.<br />2.  Çözüm kaynak denetimine ekleyin.<br />3.  Kullanıma alma ve metin dosyasını değiştirin.<br />4.  İade Et iletişim kutusu kontrol edin (**dosya**, **kaynak denetimi**, **iade**).|Ortak beklenen bir davranış.|  
|Kullanıma alınmış bir metin dosyasını değiştirme, dosyayı iade edin (**Bekleyen İadeler** pencere)|1.  Yeni bir proje içeren bir metin dosyası oluşturun.<br />2.  Çözüm kaynak denetimine ekleyin.<br />3.  Kullanıma alma ve metin dosyasını değiştirin.<br />4.  Aracılığıyla iade **Bekleyen İadeler** penceresi.|Ortak beklenen bir davranış.|  
  
### <a name="case-4b-adding-files"></a>Case 4b: dosya ekleme  
 Bir dosya bir proje ya da bir çözüme bir öğe eklerken, proje veya çözümü de değiştirmeniz gerekir. Bu nedenle üst dosya ayrıca kullanıma ve ayrıca tamamlamak için iade edilmesi gerekir.  
  
|Eylem|Test adımları|Beklenen sonuçları doğrulamak için|  
|------------|----------------|--------------------------------|  
|Bir metin dosyası ekleyin ve her şeyi denetleyin (**iade** iletişim kutusu)|1.  Yeni bir proje oluşturun.<br />2.  Çözüm kaynak denetimine ekleyin.<br />3.  Bir metin dosyası projeye ekleyin.<br />4.  Projenin kullanıma istenirse kabul edin.<br />5.  Çözümde seçin **Çözüm Gezgini**.<br />6.  İade etme **iade** iletişim kutusu.|Ortak beklenen bir davranış.|  
|Bir metin dosyası ekleyin ve her şeyi denetleyin (**Bekleyen İadeler** pencere)|1.  Yeni bir proje oluşturun.<br />2.  Çözüm kaynak denetimine ekleyin.<br />3.  Bir metin dosyası projeye ekleyin.<br />4.  Projenin kullanıma istenirse kabul edin.<br />5.  Çözümden iade **Bekleyen İadeler** penceresi.|Ortak beklenen davranışı|  
  
### <a name="case-4c-adding-projects"></a>Case 4 c: Proje ekleme  
 Bir çözüme bir proje eklediğinizde, çözüm de değiştirmeniz gerekir. Bu nedenle çözüm dosyasını da kullanıma ve ayrıca tamamlamak için iade edilmesi gerekir.  
  
|Eylem|Test adımları|Beklenen sonuçları doğrulamak için|  
|------------|----------------|--------------------------------|  
|Kaynak denetimi altında boş bir çözüme proje ekleme (**iade** iletişim kutusu)|1.  Boş bir çözüm oluşturun.<br />2.  Çözüm kaynak denetimine ekleyin.<br />3.  Yeni bir proje ekleyin.<br />4.  Çözüm kullanıma istenirse kabul edin.<br />5.  İade etme **iade** iletişim kutusu.|Ortak beklenen bir davranış.|  
|Kaynak denetimi altında boş bir çözüme proje ekleme (**Bekleyen İadeler** pencere)|1.  Boş bir çözüm oluşturun.<br />2.  Çözüm kaynak denetimine ekleyin.<br />3.  Yeni bir proje ekleyin.<br />4.  Çözüm kullanıma istenirse kabul edin.<br />5.  Çözümden iade **Bekleyen İadeler** penceresi.|Ortak beklenen bir davranış.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Kaynak Denetimi Eklentileri için Test Kılavuzu](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)

