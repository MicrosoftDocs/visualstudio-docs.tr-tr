---
title: SDI sunucu uygulamaları | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- SDI server applications
- SDI server applications, debugging
ms.assetid: 09713718-1376-4753-b119-26f36639693e
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9047c9b39bad5f4f790327b5ee65b4de688db9d8
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2018
ms.locfileid: "31475668"
---
# <a name="sdi-server-applications"></a>SDI Sunucu Uygulamaları
SDI sunucu uygulaması ayıkladığınız varsa, belirtmeniz gerekir `/Embedding` veya `/Automation` içinde **komut satırı bağımsız değişkenleri** özelliğinde *proje* özellik sayfaları iletişim kutusu için C/C++, C# veya Visual Basic projeleri.  
  
 Bu komut satırı bağımsız değişkenleri ile başlatılan gibi sorgulamanıza kapsayıcıdan hata ayıklayıcı sunucu uygulaması başlatabilirsiniz. Kapsayıcı Program Yöneticisi'ni ya da Dosya Yöneticisi başlatma hata ayıklayıcısı'ndaki başlatılan sunucu örneğini kullanması kapsayıcı neden olur.  
  
## <a name="finding-the-command-line-arguments-property"></a>Komut satırı bağımsız değişkenleri özelliğini bulma  
 Erişim için *proje* özellik sayfaları iletişim kutusu, Çözüm Gezgini'nde projenize sağ tıklayın ve ardından kısayol menüsünden Özellikler'i seçin. Komut satırı bağımsız değişkenleri özelliğini bulmak için yapılandırma özellikleri kategorisini genişletin ve hata ayıklama Sayfası'ı tıklatın.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [COM ve ActiveX hata ayıklaması](../debugger/com-and-activex-debugging.md)   
 [Nasıl yapılır: COM sunucularında hata ayıklama](../debugger/how-to-debug-com-servers.md)