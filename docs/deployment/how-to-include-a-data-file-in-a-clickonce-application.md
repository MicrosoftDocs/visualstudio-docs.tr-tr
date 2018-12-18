---
title: 'Nasıl yapılır: ClickOnce uygulamasına bir veri dosyası dahil | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, data
- deploying applications [ClickOnce], data files
- data access, ClickOnce applications
ms.assetid: 89ee46ef-bc8c-4ab0-a2ac-1220f9da06fc
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: cfba7612ec0e019b8c8dfa7c7406435b6e43e6cc
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49917927"
---
# <a name="how-to-include-a-data-file-in-a-clickonce-application"></a>Nasıl yapılır: ClickOnce uygulamasına bir veri dosyası Ekle
Her [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] yüklediğiniz bir uygulama, bir veri dizini hedef bilgisayarın yerel diskte, burada uygulama yönetebilir, kendi veri atanır. Veri dosyaları, tüm dosya türlerini içerebilir: metin dosyalarını, XML dosyaları veya hatta bir Microsoft Access veritabanına (*.mdb*) dosyaları. Aşağıdaki yordamlar bir veri dosyası herhangi bir tür ekleme gösterir, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] uygulama.  
  
### <a name="to-include-a-data-file-by-using-mageexe"></a>Mage.exe kullanarak bir veri dosyası eklemek için  
  
1. Uygulamanızın dosyaların geri kalanı ile birlikte uygulama dizininize veri dosyası ekleyin.  
  
    Genellikle, uygulama dizininize dağıtımın geçerli sürümüyle etiketli bir dizin olacaktır — Örneğin, v1.0.0.0.  
  
2. Uygulama bildiriminizi listesine veri dosyasını güncelleştirin.  
  
    `mage -u v1.0.0.0\Application.manifest -FromDirectory v1.0.0.0`  
  
    Bu görevi gerçekleştirme uygulama bildiriminizi dosyaların listesini yeniden oluşturur ve karma imzaları da otomatik olarak oluşturur.  
  
3. Uygulama bildirimi, tercih edilen bir metin veya XML düzenleyicisinde açın ve bulun `file` son eklenen dosya için öğesi.  
  
    Adlı bir XML dosyası eklediyseniz `Data.xml`, dosyanın aşağıdaki kod örneği için benzer olacaktır.  
  
   `<file name="Data.xml" hash="23454C18A2DC1D23E5B391FEE299B1F235067C59" hashalg="SHA1" asmv2:size="39500" />`  
  
4. Öznitelik Ekle `type` bu öğeye ve değerli tedarik `data`.  
  
   `<file name="Data.xml" writeableType="applicationData" hash="23454C18A2DC1D23E5B391FEE299B1F235067C59" hashalg="SHA1" asmv2:size="39500" />`  
  
5. Uygulama bildiriminizi anahtar çifti veya sertifikayı kullanarak yeniden imzalayın ve ardından, dağıtım bildirimini yeniden imzalamanız.  
  
    Uygulama bildiriminin, karma değiştiğinden, dağıtım bildirimini yeniden imzalamanız gerekir.  
  
    `mage -s app manifest -cf cert_file -pwd password`
  
    `mage -u deployment manifest -appm app manifest`
  
    `mage -s deployment manifest -cf certfile -pwd password`
  
### <a name="to-include-a-data-file-by-using-mageuiexe"></a>MageUI.exe kullanarak bir veri dosyası eklemek için  
  
1.  Uygulamanızın dosyaların geri kalanı ile birlikte uygulama dizininize veri dosyası ekleyin.  
  
2.  Genellikle, uygulama dizininize dağıtımın geçerli sürümüyle etiketli bir dizin olacaktır — Örneğin, v1.0.0.0.  
  
3.  Üzerinde **dosya** menüsünde tıklayın **açın** uygulama bildiriminizi açın.  
  
4.  Seçin **dosyaları** sekmesi.  
  
5.  Uygulamanızın dosyaları içeren dizine sekmenin üstünde metin kutusuna girin ve ardından **Doldur**.  
  
     Veri dosyası kılavuzunda görünür.  
  
6.  Ayarlama **dosya türü** veri dosyasına değerini **veri**.  
  
7.  Uygulama bildirimini kaydedin ve sonra dosyayı yeniden imzalayın.  
  
     *MageUI.exe* dosyayı yeniden imzalamanızı ister.  
  
8.  Dağıtım bildirimini yeniden imzalamanız  
  
     Uygulama bildiriminin, karma değiştiğinden, dağıtım bildirimini yeniden imzalamanız gerekir.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [ClickOnce uygulamalarında yerel ve uzak veri erişimi](../deployment/accessing-local-and-remote-data-in-clickonce-applications.md)