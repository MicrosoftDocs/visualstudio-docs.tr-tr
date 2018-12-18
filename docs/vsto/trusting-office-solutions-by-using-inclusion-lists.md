---
title: Ekleme listelerini kullanarak Office çözümlerine güven
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- permissions [Office development in Visual Studio]
- inclusion lists [Office development in Visual Studio], about inclusion lists
- security [Office development in Visual Studio], inclusion lists
- inclusion lists [Office development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 9e2fea115b941af4b119b59dade16114cab3383d
ms.sourcegitcommit: c57ae28181ffe14a30731736661bf59c3eff1211
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/11/2018
ms.locfileid: "38783707"
---
# <a name="trust-office-solutions-by-using-inclusion-lists"></a>Ekleme listelerini kullanarak Office çözümlerine güven
  Ekleme listeleri yayımcıyı tanımlayan bir sertifika ile imzalanmış Office çözümlerine güven verme olanağı verir. Ekleme listeleri kullanıcıya özeldir ve belge düzeyi özelleştirmeleri ve VSTO eklentileri için kullanılabilir.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 Bir kullanıcı bu kullanıcı için güven verilmemiş bir Office çözümünü başlattığında, Microsoft Office çözümünün gitmesini ile bir güvenlik kararı ister bir [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] güven istemi. Kullanıcı çözümü güven karar verirse, özelleştirme çalışır ve kullanıcı olmayan istenir sonraki.  
  
## <a name="inclusion-list-and-windows-installer"></a>Ekleme listesi ve Windows Installer  
 Office çözümleriyle yükleme *Program dosyaları* Windows Installer kullanarak dizini, yönetici hakları gerektirir. Office çözümleri için *Program dosyaları* dizin, Office çalışma zamanı için Visual Studio Araçları Office çözümlerini FullTrust izin zaten verilmiş olduğundan ekleme listesi artık denetler.  
  
## <a name="clickonce-trust-prompt"></a>ClickOnce güven istemi  
 Kullanarak [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] yöneticileri Office çözümleri için uygulama isteyen izin vermek üzere istemi devre dışı bırakma istemi güven düzeyini yapılandırın veya güvenilen bir sertifika gerektirir. Bu yapılandırma erişimi denetleyen kayıt defteri anahtarını kullanarak yapılır ekleme listesi.  
  
 İstem devre dışıysa, güvenilir ve bilinen bir sertifikası olan çözümleri yüklenebilir. İstem düzeyi gerekli Authenticode ayarlarsanız, çözümü, bilinen yetkilisinden bir sertifika ile imzalanmalıdır, ancak bir sertifika (güvenilen bir sertifika) güvenilir kök yetkilisi zincirlenen gerektirmez. İsteyen izin verilirse, bilinmeyen kimliğe sahip bir sertifika çözümü imzalanabileceği. Bu senaryoda, güven kararı, son kullanıcıya ertelenmiş ve geçici bir sertifika çözümü yüklemek yeterli olacaktır.  
  
 Daha fazla bilgi için [nasıl yapılır: ekleme listesi güvenliğini yapılandırma](../vsto/how-to-configure-inclusion-list-security.md) ve Tablo 2 ' nin isteyen düzeyi kayıt defteri anahtarı değeri başlatma etkileri başlıklı [yapılandırma ClickOnce Güvenilen Yayımcılar](http://go.microsoft.com/fwlink/?LinkId=94774).  
  
## <a name="structure-of-the-inclusion-list"></a>Ekleme listelerini yapısı  
 Geçerli ekleme listesi girişi iki bölümden oluşur: dağıtım bildiriminin yanı sıra, çözümü imzalamak için kullanılan ortak anahtar için bir yol. Bir çözüm listesine eklendikten sonra kabul edilir güvenilir. Office çözümünün çalıştığında, Office uygulamasının ekleme listesindeki ortak anahtar imzalama anahtarı şu anda çalışıyor çözüm özgün güvenilir sürümüyle aynı olduğunu doğrulamak için dağıtım bildirimi içinde ile karşılaştırır.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Office çözümlerine güven verme](../vsto/granting-trust-to-office-solutions.md)   
 [Office çözümleri güvenliğini sağlama](../vsto/securing-office-solutions.md)  
  
  