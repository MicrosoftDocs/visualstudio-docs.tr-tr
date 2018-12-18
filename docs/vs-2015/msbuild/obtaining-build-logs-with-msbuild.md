---
title: Günlükleri MSBuild ile derleme alma | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- MSBuild, logging
- logging [MSBuild]
ms.assetid: 6ba9a754-9cc0-4fed-9fc8-4dcd3926a031
caps.latest.revision: 30
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6eb4a1822d0be86d19f25bfaa46e296abc7a73a0
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49811756"
---
# <a name="obtaining-build-logs-with-msbuild"></a>MSBuild ile Derleme Günlükleri Alma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
MSBuild ile anahtarlarını kullanarak, gözden geçirme ve yapı verileri bir veya daha fazla dosyaları kaydetmek isteyip istemediğinizi istediğiniz derleme veri miktarını belirtebilirsiniz. Yapılandırma verilerini toplamak için özel bir Günlükçü de belirtebilirsiniz. Bu konuda ele alınmamıştır MSBuild komut satırı anahtarları hakkında daha fazla bilgi için bkz. [komut satırı başvurusu](../msbuild/msbuild-command-line-reference.md).  
  
> [!NOTE]
>  Visual Studio IDE kullanarak projeleri derlemek, o yapılar Derleme günlüklerini gözden geçirerek giderebilirsiniz. Daha fazla bilgi için bkz. [nasıl yapılır: görünümü, kaydetme ve yapılandırma derleme günlük dosyalarını](../ide/how-to-view-save-and-configure-build-log-files.md).  
  
## <a name="setting-the-level-of-detail"></a>Ayrıntı düzeyini ayarlama  
 MSBuild ayrıntı düzeyini belirtmeden kullanarak bir proje oluşturduğunuzda çıkış günlüğünde aşağıdaki bilgiler görüntülenir:  
  
- Hataları, uyarıları ve iletileri son derece önemli olarak sınıflandırılmış.  
  
- Bazı durumu olayları.  
  
- Derleme özeti.  
  
  Kullanarak **/verbosity** (**/v**) geçiş, ne kadar veri çıkış günlüğünde görünür denetleyebilirsiniz. Sorun giderme için bir ayrıntı düzeyini ya da kullanmak `detailed` (`d`) veya `diagnostic` (`diag`), en çok bilgi sağlar.  
  
  Ayarladığınızda yapı işleminin daha yavaş olabilir **/verbosity** için `detailed` ve ayarladığınızda bile yavaş **/verbosity** için `diagnostic`.  
  
```  
msbuild MyProject.proj /t:go /v:diag  
```  
  
## <a name="saving-the-build-log-to-a-file"></a>Derleme günlüğünü bir dosyaya kaydetme  
 Kullanabileceğiniz **/fileLogger** (**fl**) yapılandırma verilerini bir dosyaya kaydetmek için anahtar. Aşağıdaki örnekte, yapılandırma verilerini adlı bir dosyaya kaydeder. `msbuild.log`.  
  
```  
msbuild MyProject.proj /t:go /fileLogger  
```  
  
 Aşağıdaki örnekte adlı günlük dosyası `MyProjectOutput.log`, ve ayrıntı düzeyini günlük çıktısını kümesine `diagnostic`. Bu iki ayar kullanarak belirttiğiniz **/filelogparameters** (`flp`) geçin.  
  
```  
msbuild MyProject.proj /t:go /fl /flp:logfile=MyProjectOutput.log;verbosity=diagnostic  
```  
  
 Daha fazla bilgi için [komut satırı başvurusu](../msbuild/msbuild-command-line-reference.md).  
  
## <a name="saving-the-log-output-to-multiple-files"></a>Günlük çıktısını birden çok dosyaya kaydetme  
 Aşağıdaki örnek tüm günlüğüne kaydeder `msbuild1.log`, hataları için `JustErrors.log`ve Uyarılar için yalnızca `JustWarnings.log`. Örnek dosya numaraları üç dosyaların her biri için kullanır. Dosya numaraları hemen sonrasına belirtilen **/fl** ve **/flp** anahtarları (örneğin, `/fl1` ve `/flp1`).  
  
 **/Filelogparameters** (`flp`) için her dosya adı gerekenler ve hangi her dosyasına eklenecek dosyaları 2 ve 3 belirtin geçer. Adsız şekilde 1 ' dosyası için belirtilen varsayılan adını `msbuild1.log` kullanılır.  
  
```  
msbuild MyProject.proj /t:go /fl1 /fl2 /fl3 /flp2:logfile=JustErrors.log;errorsonly /flp3:logfile=JustWarnings.log;warningsonly  
  
```  
  
 Daha fazla bilgi için [komut satırı başvurusu](../msbuild/msbuild-command-line-reference.md).  
  
## <a name="using-a-custom-logger"></a>Özel bir günlükçü kullanma  
 Uygulayan yönetilen bir tür geliştirerek kendi Günlükçü yazabilirsiniz <xref:Microsoft.Build.Framework.ILogger> arabirimi. Derleme hataları e-posta ile gönderin, bunları bir veritabanında oturum veya bir XML dosyasına günlüğüne için özel bir Günlükçü örneği için kullanabilirsiniz. Daha fazla bilgi için [Günlükçüleri derleme](../msbuild/build-loggers.md).  
  
 MSBuild komut satırında, özel bir Günlükçü kullanarak belirttiğiniz **/logger** geçin. Ayrıca **/noconsolelogger** varsayılan konsol günlüğe devre dışı bırakma.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:Microsoft.Build.Framework.LoggerVerbosity>   
 [Günlükçüleri derleme](../msbuild/build-loggers.md)   
 [Birden çok işlemcili ortamda oturum açma](../msbuild/logging-in-a-multi-processor-environment.md)   
 [İletme Günlükçüleri oluşturma](../msbuild/creating-forwarding-loggers.md)   
 [MSBuild Kavramları](../msbuild/msbuild-concepts.md)



