---
title: Dağıtılan ASP.NET uygulamalarında hata ayıklama | Microsoft Docs
ms.custom: ''
ms.date: 06/30/2017
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- ASP.NET Web applications
- Web services, debugging
- XML, debugging Web services
- debugging Web services
- ASP.NET, debugging Web applications
- XML Web services, debugging
ms.assetid: b938a91b-be96-416f-83bc-4177e7f3929a
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- aspnet
ms.openlocfilehash: b8c7c9ea2f280eaf60f4592f149ed2989d862b9b
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2018
ms.locfileid: "31472442"
---
# <a name="debugging-deployed-aspnet-applications"></a>Dağıtılan ASP.NET uygulamalarında hata ayıklama
Kullanılacak [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] dağıtılan bir uygulama hata ayıklama için ilişkilendirmeniz gerekir [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] çalışan işlem ve hata ayıklayıcı uygulama simgeleri için erişimi olduğundan emin olun. Ayrıca, bulun ve uygulama için kaynak dosyaları açın gerekir. Daha fazla bilgi için bkz: [belirtin simge (.pdb) ve kaynak dosyaları](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md), [nasıl yapılır: ASP.NET işleminin adını bulma](../debugger/how-to-find-the-name-of-the-aspnet-process.md), ve [sistem gereksinimleri](../debugger/aspnet-debugging-system-requirements.md).  

> [!WARNING]
> İçin eklerseniz [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] çalışan işlemi hata ayıklama ve bir kesme noktası isabet için tüm yönetilen kod içinde çalışan işlem durur. Çalışan işlemin tüm yönetilen kodda durdurma tüm kullanıcılar için bir iş kesinti sunucuda neden olabilir. Bir üretim sunucusunda hata ayıklama önce Üretim iş olası etkisini göz önünde bulundurun. 
  
Ekleme işlemi [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] çalışan işlemi aynıdır herhangi diğer uzak işlemine iliştirme. Doğru projeyi yoksa, bağlı olan, uygulama böldüğünde bir iletişim kutusu görüntülenir. Bu iletişim kutusunda uygulama için kaynak dosyalarının konumunu ister. İletişim kutusunda belirttiğiniz dosya adı, Web sunucusunda hata ayıklama simgeleri ın belirtilen dosya adı eşleşmelidir. Daha fazla bilgi için bkz: [eklemek için çalışan işlemler](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md). IIS üzerinde uzaktan hata ayıklama kurulumu için bkz: [Uzak IIS bilgisayarda uzaktan hata ayıklama ASP.NET](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md).
 
> [!NOTE]
>  Birçok [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Web uygulamaları iş mantığı ya da başka yararlı bir kod içeren DLL'leri başvuru. Uygulamanızı dağıttığınızda, böyle bir başvuru DLL yerel bilgisayarınızdan Web uygulamasının sanal dizin \bin klasörüne kopyalar. Hata ayıklama yaptığınız zaman, Web uygulamanızın bu dll Dosyasının kopyasını ve kopya değil, yerel bilgisayarınızda başvuran unutmayın. 
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ASP.NET uygulamalarında hata ayıklama](../debugger/how-to-enable-debugging-for-aspnet-applications.md)   
 [Nasıl yapılır: ASP.NET uygulamaları için hata ayıklamayı etkinleştir](../debugger/how-to-enable-debugging-for-aspnet-applications.md)   
 [Nasıl yapılır: ASP.NET işleminin adını bulma](../debugger/how-to-find-the-name-of-the-aspnet-process.md)   
 [Simge (.pdb) belirtin ve kaynak dosyaları](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)