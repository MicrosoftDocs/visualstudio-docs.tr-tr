---
title: Günlükleri MSBuild ile derleme alma | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, logging
- logging [MSBuild]
ms.assetid: 6ba9a754-9cc0-4fed-9fc8-4dcd3926a031
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 83f4de3efc64d78dd561a44fabed1e16f673d736
ms.sourcegitcommit: 71218ffc33da325cc1b886f69ff2ca50d44f5f33
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/09/2018
ms.locfileid: "48879134"
---
# <a name="obtain-build-logs-with-msbuild"></a>MSBuild ile derleme günlükleri alın
MSBuild ile anahtarlarını kullanarak, gözden geçirme ve yapı verileri bir veya daha fazla dosyaları kaydetmek isteyip istemediğinizi istediğiniz derleme veri miktarını belirtebilirsiniz. Yapılandırma verilerini toplamak için özel bir Günlükçü de belirtebilirsiniz. Bu konuda ele alınmamıştır MSBuild komut satırı anahtarları hakkında daha fazla bilgi için bkz. [komut satırı başvurusu](../msbuild/msbuild-command-line-reference.md).  
  
> [!NOTE]
>  Visual Studio IDE kullanarak projeleri derlemek, o yapılar Derleme günlüklerini gözden geçirerek giderebilirsiniz. Daha fazla bilgi için bkz. [nasıl yapılır: görüntüleme, kaydetme ve yapılandırma derleme günlüğü dosyalarını](../ide/how-to-view-save-and-configure-build-log-files.md).  
  
## <a name="set-the-level-of-detail"></a>Ayrıntı düzeyini ayarlayın  
 MSBuild ayrıntı düzeyini belirtmeden kullanarak bir proje oluşturduğunuzda çıkış günlüğünde aşağıdaki bilgiler görüntülenir:  
  
-   Hataları, uyarıları ve iletileri son derece önemli olarak sınıflandırılmış.  
  
-   Bazı durumu olayları.  
  
-   Derleme özeti.  

Kullanarak **-ayrıntı** (**- v**) geçiş, ne kadar veri çıkış günlüğünde görünür denetleyebilirsiniz. Sorun giderme için bir ayrıntı düzeyini ya da kullanmak `detailed` (`d`) veya `diagnostic` (`diag`), en çok bilgi sağlar.  

Ayarladığınızda yapı işleminin daha yavaş olabilir **-ayrıntı** için `detailed` ve ayarladığınızda bile yavaş **-ayrıntı** için `diagnostic`.  
  
```cmd  
msbuild MyProject.proj -t:go -v:diag  
```  

## <a name="save-the-build-log-to-a-file"></a>Derleme günlüğünü bir dosyaya kaydet  
 Kullanabileceğiniz **- fileLogger** (**fl**) yapılandırma verilerini bir dosyaya kaydetmek için anahtar. Aşağıdaki örnekte, yapılandırma verilerini adlı bir dosyaya kaydeder. *msbuild.log*.  
  
```cmd  
msbuild MyProject.proj -t:go -fileLogger  
```  
  
 Aşağıdaki örnekte adlı günlük dosyası *MyProjectOutput.log*, ve ayrıntı düzeyini günlük çıktısını kümesine `diagnostic`. Bu iki ayar kullanarak belirttiğiniz **- filelogparameters** (`flp`) geçin.  
  
```cmd  
msbuild MyProject.proj -t:go -fl -flp:logfile=MyProjectOutput.log;verbosity=diagnostic  
```  
  
 Daha fazla bilgi için [komut satırı başvurusu](../msbuild/msbuild-command-line-reference.md).  
  
## <a name="save-the-log-output-to-multiple-files"></a>Günlük çıktısını birden çok dosyaya kaydet  
 Aşağıdaki örnek tüm günlüğüne kaydeder *msbuild1.log*, hataları için *JustErrors.log*ve Uyarılar için yalnızca *JustWarnings.log*. Örnek dosya numaraları üç dosyaların her biri için kullanır. Dosya numaraları hemen sonrasına belirtilen **-fl** ve **- flp** anahtarları (örneğin, `-fl1` ve `-flp1`).  
  
 **- Filelogparameters** (`flp`) için her dosya adı gerekenler ve hangi her dosyasına eklenecek dosyaları 2 ve 3 belirtin geçer. Adsız şekilde 1 ' dosyası için belirtilen varsayılan adını *msbuild1.log* kullanılır.  
  
```cmd  
msbuild MyProject.proj -t:go -fl1 -fl2 -fl3 -flp2:logfile=JustErrors.log;errorsonly -flp3:logfile=JustWarnings.log;warningsonly  
  
```  
  
 Daha fazla bilgi için [komut satırı başvurusu](../msbuild/msbuild-command-line-reference.md).  

## <a name="save-a-binary-log"></a>İkili günlük kaydetme

Sıkıştırılmış, ikili biçim kullanılarak günlüğe kaydedebilirsiniz **- binaryLogger** (**bl**) geçin. Bu günlük, derleme işleminin ayrıntılı açıklamasını içerir ve belirli günlük analizi araçları tarafından okunabilir.

Aşağıdaki örnekte, bir ikili günlük dosyası adıyla oluşturulur *binarylogfilename*.

```cmd  
/bl:binarylogfilename.binlog
``` 
 
Daha fazla bilgi için [komut satırı başvurusu](../msbuild/msbuild-command-line-reference.md).  

## <a name="use-a-custom-logger"></a>Özel bir Günlükçü kullanma  
 Uygulayan yönetilen bir tür geliştirerek kendi Günlükçü yazabilirsiniz <xref:Microsoft.Build.Framework.ILogger> arabirimi. Derleme hataları e-posta ile gönderin, bunları bir veritabanında oturum veya bir XML dosyasına günlüğüne için özel bir Günlükçü örneği için kullanabilirsiniz. Daha fazla bilgi için [günlükçüleri derleme](../msbuild/build-loggers.md).  
  
 MSBuild komut satırında, özel bir Günlükçü kullanarak belirttiğiniz **-Günlükçü** geçin. Ayrıca **- noconsolelogger** varsayılan konsol günlüğe devre dışı bırakma.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 <xref:Microsoft.Build.Framework.LoggerVerbosity>   
 [Günlükçüleri derleme](../msbuild/build-loggers.md)   
 [Birden çok işlemcili ortamda oturum açma](../msbuild/logging-in-a-multi-processor-environment.md)   
 [İletme günlükçüleri oluşturma](../msbuild/creating-forwarding-loggers.md)   
 [MSBuild kavramları](../msbuild/msbuild-concepts.md)