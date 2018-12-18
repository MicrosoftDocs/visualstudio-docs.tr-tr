---
title: 'Güvenlik Uyarısı: Güvenilmeyen bir kullanıcının sahip olduğu işleme ekleme tehlikeli olabilir. Aşağıdaki bilgiler kuşkulu görünüyorsa ya da emin değilseniz, bu işleme eklemeyin. | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.debug.attachsecuritywarning
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 52246c1e-a371-40a0-b756-a435cc51876f
caps.latest.revision: 17
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: dac3ad5d51e2934bd2cbdf5a8fe9ad30a4a90a8b
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51745583"
---
# <a name="security-warning-attaching-to-a-process-owned-by-an-untrusted-user-can-be-dangerous-if-the-following-information-looks-suspicious-or-you-are-unsure-do-not-attach-to-this-process"></a>Güvenlik Uyarısı: Güvenilmeyen bir kullanıcının sahip olduğu işleme ekleme tehlikeli olabilir. Aşağıdaki bilgiler kuşkulu görünüyorsa ya da emin değilseniz, bu işleme eklemeyin
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Kısmen güvenilen kodu içerir veya hemen bağlama gerçekleşmeden önce güvenilmeyen bir kullanıcının sahip olduğu bir işleme eklediğinizde, bu uyarı iletişim kutusu görüntülenir. Kötü amaçlı kod içeren bir güvenilmeyen işlemi hata ayıklamada bilgisayar zarar verme olasılığı vardır. İşlem güvenmeyecekleri nedeniniz sonra tıklatmanız gerekir **iptal** hata ayıklama önlemek için.  
  
 Yasal bir senaryo hata ayıklama sırasında bu uyarının gösterilmemesi için Visual Studio'yu kapatın ve bu kayıt defteri anahtarı değerini 1 olarak ayarlayın: `HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\<version>\Debugger\DisableAttachSecurityWarning`ve sonra Visual Studio'yu yeniden başlatın. Hata ayıklama senaryoyu tamamladıktan sonra değerini 0 olarak ayarlamak ve Visual Studio'yu yeniden başlatın.  
  
 "Kullanıcıların güvenilen" dahil kendiniz artı genellikle .NET Framework gibi yüklü olan bilgisayarlarda tanımlanan standart kullanıcı kümesini `aspnet`, `localsystem`, `networkservice`, ve `localservice`.  
  
## <a name="uielement-list"></a>UIElement Listesi  
 Ad  
 Hata ayıklamak için istenen derlemenin adı  
  
 Kullanıcı  
 Geçerli kullanıcı  
  
 İliştir  
 Ekleyerek hatalarını ayıklamaya devam etmek için basın  
  
 İliştirme  
 İşleme eklemeyin.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Çalıştırma işlemleri iliştirme](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)   
 [Hata Ayıklayıcısı Güvenliği](../debugger/debugger-security.md)



