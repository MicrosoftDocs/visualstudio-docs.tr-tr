---
title: 'Güvenlik Uyarısı: Hata ayıklayıcı güvenilmeyen komut yürütmeli | Microsoft Docs'
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
- vs.debug.sourceserver.securityalert
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: e5c004b3-b364-4098-ac98-770076ca9981
caps.latest.revision: 16
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c4f37f629d12a94c65031543d196be92b3f259b6
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51744725"
---
# <a name="security-warning-debugger-must-execute-untrusted-command"></a>Güvenlik Uyarısı: Hata Ayıklayıcı Güvenilmeyen Komut Yürütmeli
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Kaynak Sunucusu'nu kullanırken, bu uyarı iletişim kutusu görüntülenir. Bu, hata ayıklayıcı kaynak kodunu edinmek için yürütmek için gereken komut kaynak sunucu srcsvr.ini dosyasının içerdiği için güvenilir komutları listesinde olmadığını gösterir. Bu geçerli bir komutsa, srcsvr.ini dosyasına bunu ekleyebilirsiniz. Aksi takdirde, bunu çalıştırmamanız gerekir. Daha fazla bilgi için [belirtin sembol (.pdb) ve kaynak dosyaları](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).  
  
## <a name="message-text"></a>İleti metni  
 **Hata ayıklayıcı kaynak kodunu kaynak sunucudan almak için aşağıdaki güvenilmeyen komutu yürütmelidir.**  
  
 **Hata ayıklama sembol dosyası varsa (\*.pdb) olduğunu değil bir bilinen ve güvenilir bir kaynaktan, bu komut geçersiz veya çalıştırılması tehlikeli olabilir.**  
  
 **Bu komutu çalıştırmak istiyor musunuz?**  
  
## <a name="uielement-list"></a>UIElement Listesi  
 Metin kutusu  
 Çalıştırılacak .pdb dosyasından komut.  
  
 Çalıştır  
 Çalıştırmak için komuta izin verin.  
  
 Çalıştırma  
 Komutun yürütülmesini ve kaynak sunucudan dosya indirme durdurun.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Sembol (.pdb) belirtin ve kaynak dosyaları](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)   
 [Hata ayıklayıcısı güvenliği](../debugger/debugger-security.md)   
 [Kaynak sunucu](http://msdn.microsoft.com/library/windows/desktop/ms680641\(v=vs.85\).aspx)



