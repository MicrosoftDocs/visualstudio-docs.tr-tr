---
title: Tam zamanında hata ayıklayıcı devre dışı bırakma | Microsoft Docs
ms.custom: ''
ms.date: 05/23/18
ms.technology: vs-ide-debug
ms.topic: troubleshooting
helpviewer_keywords:
- debugging [Visual Studio], Just-In-Time
- Just-In-Time debugging
ms.assetid: 14972d5f-69bc-479b-9529-03b8787b118f
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 147e16bab14a6a038622804cf9c57e5fdc92bf02
ms.sourcegitcommit: c5e72875206b8c5737c29d5b1ec7b86eec747303
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/17/2018
ms.locfileid: "49382785"
---
# <a name="disable-the-just-in-time-debugger"></a>Tam zamanında hata ayıklayıcı devre dışı bırak 

Tam zamanında hata ayıklayıcı iletişim kutusu içinde çalışan bir uygulamanın hata oluştuğunda açın ve uygulama devam etmesini engelleyebilir. 

Tam zamanında hata ayıklayıcı, hata ayıklama için Visual Studio'yu başlatmak için seçeneği sunar. Olmalıdır [Visual Studio](http://visualstudio.microsoft.com) veya başka bir seçilen hata ayıklayıcı hata hakkında ayrıntılı bilgi görüntülemek veya hata ayıklarken için yüklü. 

Visual Studio sürümünü kullanıyorsanız ve hata ayıklama için bkz. denemek istiyorsanız [tam zamanında hata ayıklayıcı ile hata ayıklama](../debugger/debug-using-the-just-in-time-debugger.md). Hatayı düzeltin veya tam zamanında hata ayıklayıcı açmasının tutmak istediğiniz olamaz varsa [Visual Studio'dan devre dışı bırakma, Just-ın-Time hata ayıklama](debug-using-the-just-in-time-debugger.md#BKMK_Enabling). 

Visual Studio yüklü, ancak artık iş olsaydı gerekebilir [Windows kayıt defterinden devre dışı bırakma, Just-ın-Time hata ayıklama](debug-using-the-just-in-time-debugger.md#disable-just-in-time-debugging-from-the-windows-registry). 

Visual Studio yüklü yoksa, tam zamanında hata ayıklamayı veya sunucu tarafı hata ayıklamasını devre dışı bırakarak hata ayıklamayı engelleyebilir. 

- Bir web uygulamasını çalıştırmak çalışıyorsanız, komut dosyası hata ayıklaması devre dışı bırakın:
  
  Windows içinde **Denetim Masası** > **ağ ve Internet** > **Internet Seçenekleri**seçin **betik hata ayıklama (devre dışı bırak Internet Explorer)** ve **devre dışı bırak (diğer) ayıklamasını**. Uygulanacak adımlar ve ayarlarını Windows ve tarayıcınızı sürümünüze bağlıdır.
  
  ![JIT Internet Seçenekleri](../debugger/media/jitinternetoptions.png "JIT Internet Seçenekleri")
  
- IIS'de ASP.NET web uygulaması barındırıyorsanız, sunucu tarafı hata ayıklamasını devre dışı bırakın:

  1. IIS Yöneticisi'nde **özellikler görünümü**altında **ASP.NET** bölümünde, çift **.NET derleme**, veya seçin ve ardından **açık özellik**içinde **eylemleri** bölmesi. 
  1. Altında **davranışı** > **hata ayıklama**seçin **False**. IIS eski sürümlerinde adımlar farklıdır.

Tam zamanında hata ayıklama devre dışı bıraktıktan sonra uygulamaya normal olarak çalışır ve hatayı işlemek mümkün olabilir. 

Uygulamanın yine işlenmemiş bir hata varsa bir hata iletisini görebilirsiniz veya uygulama kilitlenme veya askıda olabilir. Uygulamayı, normalde hata düzeltilene kadar çalışmayacaktır. Uygulama sahibine başvurun ve sorunu gidermek için isteyin deneyebilirsiniz.

