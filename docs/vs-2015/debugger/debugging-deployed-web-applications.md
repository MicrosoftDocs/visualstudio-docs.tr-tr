---
title: Dağıtılmış Web uygulamalarında hata ayıklama | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- ASP.NET Web applications
- Web services, debugging
- XML, debugging Web services
- debugging Web services
- ASP.NET, debugging Web applications
- XML Web services, debugging
ms.assetid: b938a91b-be96-416f-83bc-4177e7f3929a
caps.latest.revision: 34
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 923a8e104f03a4014f269f587d5cb3a1da5266b7
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51807574"
---
# <a name="debugging-deployed-web-applications"></a>Dağıtılmış Web Uygulamalarında Hata Ayıklama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bir üretim sunucusunda çalışan bir Web uygulamasında hata ayıklamak ihtiyacınız varsa, bu dikkatle yapılmalıdır. İçin eklerseniz [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] çalışan işleme hata ayıklama için ve bir kesme noktası isabet, örneğin, tüm yönetilen kod içinde çalışan işlemi durur. Çalışan işlemi tüm yönetilen kodda durdurma iş kesinti tüm kullanıcılar için sunucu üzerinde neden olabilir. Bir üretim sunucusunda hata ayıklama önce Üretim iş olası etkisini göz önünde bulundurun.  
  
 Kullanılacak [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] dağıtılan bir uygulamada hata ayıklamak için iliştirmeniz gerekir [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] çalışan işlem ve hata ayıklayıcı semboller için uygulama erişimi olduğundan emin olun. Ayrıca, uygulama için kaynak dosyalarını bulun ve gerekir. Daha fazla bilgi için [belirtin sembol (.pdb) ve kaynak dosyaları](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md), [nasıl yapılır: ASP.NET işleminin adını bulma](../debugger/how-to-find-the-name-of-the-aspnet-process.md), ve [sistem gereksinimleri](../debugger/aspnet-debugging-system-requirements.md).  
  
> [!NOTE]
>  Birçok [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] Web uygulamaları, iş mantığı ya da diğer kullanışlı bir kod içeren dll başvurusu. Böyle bir başvuruyu DLL Web uygulamasının sanal dizin \bin klasörüne kullanarak yerel bilgisayarınızdan otomatik olarak kopyalar. Hata ayıklama, Web uygulamanıza dll, kopyalama ve kopya değil, yerel bilgisayarınızda başvuran unutmayın.  
  
 Ekleme işlemi [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] çalışan işlemi olan tüm diğer uzak işlemine iliştirme ile aynı. Doğru Proje Aç yoksa, bağlı olduğunuz, uygulama kesildiğinde bir iletişim kutusu görüntülenir. Bu iletişim kutusunu uygulama için kaynak dosyalarının konumunu ister. İletişim kutusunda belirttiğiniz dosya adı, Web sunucusunda hata ayıklama sembolleri içinde belirtilen dosya adı eşleşmelidir. Daha fazla bilgi için [çalışan işlemlere ekleme](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ASP.NET ve AJAX uygulamalarında hata ayıklama](../debugger/debugging-aspnet-and-ajax-applications.md)   
 [Web uygulamalarında ve betikte hata ayıklama](../debugger/debugging-web-applications-and-script.md)   
 [Nasıl yapılır: ASP.NET uygulamaları için hata ayıklamayı etkinleştirme](../debugger/how-to-enable-debugging-for-aspnet-applications.md)   
 [Nasıl yapılır: ASP.NET işleminin adını bulma](../debugger/how-to-find-the-name-of-the-aspnet-process.md)   
 [Simge (.pdb) ve Kaynak Dosyaları Belirtme](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)



