---
title: 'Güvenlik Uyarısı: Hata ayıklayıcı güvenilmeyen komut yürütmeli | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.sourceserver.securityalert
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: e5c004b3-b364-4098-ac98-770076ca9981
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3e99c56efc5338feeded20621c7467bbf8274bc9
ms.sourcegitcommit: 206e738fc45ff8ec4ddac2dd484e5be37192cfbd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/03/2018
ms.locfileid: "39510930"
---
# <a name="security-warning-debugger-must-execute-untrusted-command"></a>Güvenlik Uyarısı: Hata Ayıklayıcı Güvenilmeyen Komut Yürütmeli
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
 [Kaynak sunucu](/windows/desktop/Debug/source-server-and-source-indexing)