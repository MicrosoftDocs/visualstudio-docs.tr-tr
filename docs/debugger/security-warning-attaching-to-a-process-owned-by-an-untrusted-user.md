---
title: 'Güvenlik Uyarısı: güvenilmeyen bir kullanıcıya ait bir işlem ekleme tehlikeli olabilir. Aşağıdaki bilgiler şüpheli görünüyorsa veya emin değilseniz, bu işlem için eklemeyin | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.attachsecuritywarning
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: 52246c1e-a371-40a0-b756-a435cc51876f
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 68d88e01dde07789467272db830cae45ca5d60c4
ms.sourcegitcommit: eefffa7ebe339d1297cdc12f51a813e7849d7e95
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/15/2018
ms.locfileid: "34178014"
---
# <a name="security-warning-attaching-to-a-process-owned-by-an-untrusted-user-can-be-dangerous-if-the-following-information-looks-suspicious-or-you-are-unsure-do-not-attach-to-this-process"></a>Güvenlik Uyarısı: güvenilmeyen bir kullanıcıya ait bir işlem ekleme tehlikeli olabilir. Aşağıdaki bilgiler şüpheli görünüyorsa veya emin değilseniz, bu işlem için eklemeyin
Kısmen güvenilen kod içeren veya hemen ekleme oluşmadan önce güvenilmeyen bir kullanıcıya ait olan bir işlem eklediğinizde bu uyarı iletişim kutusu görüntülenir. Kötü amaçlı kod içeren güvenilmeyen bir işlem hata ayıklama yapmadan bilgisayar zarar olasılığı vardır. İşlem güvenmeyecekleri nedeniniz sonra tıklamanız **iptal** hata ayıklama önlemek için.  
  
 Bu yasal bir senaryo hata ayıklama sırasında gizlemek için Visual Studio'yu kapatın ve bu kayıt defteri anahtarı değerini 1 olarak ayarlayın: `HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\<version>\Debugger\DisableAttachSecurityWarning`ve Visual Studio'yu yeniden başlatın. Senaryo hata ayıklama işlemini tamamladıktan sonra değerini 0 olarak ayarlamak ve Visual Studio'yu yeniden başlatın.  
  
 "Kullanıcıların güvenilen" dahil kendiniz artı .NET Framework'ün gibi yüklü olan bilgisayarlarda genellikle tanımlanan standart kullanıcılar bir dizi `aspnet`, `localsystem`, `networkservice`, ve `localservice`.  
  
## <a name="uielement-list"></a>UIElement Listesi  
 Ad  
 Hata ayıklama için istenen derlemenin adı  
  
 Kullanıcı  
 Geçerli kullanıcı  
  
 İliştir  
 Ekleyerek hata ayıklamak devam tuşuna basın  
  
 Attach yok  
 İşleme iliştirilemiyor değil  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Çalıştırma işlemine iliştirme](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)   
 [Hata ayıklama güvenliği](../debugger/debugger-security.md)