---
title: MSBuild ile derleme günlükleri alma | Microsoft Docs
description: Ne kadar derleme verisi inceleyeceğinizi ve derleme verilerinin bir veya daha fazla dosyaya kaydedilip edilmeyeceğini belirtmek için MSBuild ile anahtarları kullanmayı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, logging
- logging [MSBuild]
ms.assetid: 6ba9a754-9cc0-4fed-9fc8-4dcd3926a031
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 7ecfa11122b76bcfef3473ff5d06083c64157a2c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99905447"
---
# <a name="obtain-build-logs-with-msbuild"></a>MSBuild ile derleme günlükleri alma

MSBuild ile anahtarları kullanarak, ne kadar yapı verisi gözden geçirmek istediğinizi ve derleme verilerini bir veya daha fazla dosyaya kaydetmek isteyip istemediğinizi belirtebilirsiniz. Ayrıca, derleme verilerini toplamak için özel bir günlükçü belirtebilirsiniz. Bu konunun kapsamayan MSBuild komut satırı anahtarları hakkında daha fazla bilgi için bkz. [komut satırı başvurusu](../msbuild/msbuild-command-line-reference.md).

> [!NOTE]
> Visual Studio IDE kullanarak projeler oluşturuyorsanız, Derleme günlüklerini inceleyerek bu derlemeler için sorun giderebilirsiniz. Daha fazla bilgi için bkz. [nasıl yapılır: yapı günlüğü dosyalarını görüntüleme, kaydetme ve yapılandırma](../ide/how-to-view-save-and-configure-build-log-files.md).

## <a name="set-the-level-of-detail"></a>Ayrıntı düzeyini ayarlama

 Bir ayrıntı düzeyi belirtmeden MSBuild kullanarak bir proje oluşturduğunuzda, çıkış günlüğünde aşağıdaki bilgiler görüntülenir:

- Yüksek oranda önemli olarak sınıflandırılan hatalar, uyarılar ve mesajlar.

- Bazı durum olayları.

- Yapı Özeti.

**-Ayrıntı** (**-v**) anahtarını kullanarak, çıktı günlüğünde ne kadar veri göründüğünü kontrol edebilirsiniz. Sorun giderme için, `detailed` `d` `diagnostic` `diag` en fazla bilgiyi sağlayan () veya () ayrıntı düzeyini kullanın.

-Ayrıntı düzeyini ' a ayarladığınızda, **-ayrıntı düzeyini** `detailed` ve hatta daha yavaş ayarlarsanız yapı işlemi daha yavaş olabilir  `diagnostic` .

```cmd
msbuild MyProject.proj -t:go -v:diag
```

### <a name="verbosity-settings"></a>Ayrıntı ayarları

Aşağıdaki tabloda, günlük ayrıntı düzeyi (sütun değerleri) hangi ileti türlerinin (satır değerleri) günlüğe kaydedileceğini nasıl etkilediğini gösterir.

| İleti türü/ayrıntı düzeyi              | Quiet | En az | Normal | Ayrıntılı | Tanılama |
|---------------------------------------|:-----:|:-------:|:------:|:--------:|:----------:|
| Hatalar                                |   ✅   |    ✅    |    ✅   |     ✅    |      ✅     |
| Uyarılar                              |   ✅   |    ✅    |    ✅   |     ✅    |      ✅     |
| Yüksek öneme sahip Iletiler              |       |    ✅    |    ✅   |     ✅    |      ✅     |
| Normal-önemli mesajlar           |       |         |    ✅   |     ✅    |      ✅     |
| Düşük öneme sahip Iletiler              |       |         |        |     ✅    |      ✅     |
| Ek MSBuild-Engine bilgileri |       |         |        |          |      ✅     |

## <a name="save-the-build-log-to-a-file"></a>Derleme günlüğünü bir dosyaya kaydetme

Derleme verilerini bir dosyaya kaydetmek için **-filegünlükçü** (**fl**) anahtarını kullanabilirsiniz. Aşağıdaki örnek, yapı verilerini *MSBuild. log* adlı bir dosyaya kaydeder.

```cmd
msbuild MyProject.proj -t:go -fileLogger
```

 Aşağıdaki örnekte, günlük dosyası *Myprojectoutput. log* olarak adlandırılır ve günlük çıkışının ayrıntı düzeyi olarak ayarlanır `diagnostic` . Bu iki ayarı **-FileLoggerParameters** ( `flp` ) anahtarını kullanarak belirtirsiniz.

```cmd
msbuild MyProject.proj -t:go -fl -flp:logfile=MyProjectOutput.log;verbosity=diagnostic
```

 Daha fazla bilgi için bkz. [komut satırı başvurusu](../msbuild/msbuild-command-line-reference.md).

## <a name="save-the-log-output-to-multiple-files"></a>Günlük çıktısını birden çok dosyaya kaydetme

 Aşağıdaki örnek, tüm günlüğü *msbuild1. log* dosyasına kaydeder, yalnızca bir hata oluştu *. log* ve yalnızca *JustWarnings. log* için uyarılar. Örnek, her üç dosyanın dosya numarasını kullanır. Dosya numaraları **-fl** ve **-FLP** anahtarlarından hemen sonra belirtilir (örneğin, `-fl1` ve `-flp1` ).

 Dosyalar 2 ve 3 için **-FileLoggerParameters** ( `flp` ) anahtarları her bir dosyanın ne şekilde ekleneceğini ve her dosyaya nelerin ekleneceğini belirtir. Dosya 1 için ad belirtilmedi, bu nedenle varsayılan *msbuild1. log* adı kullanılır.

```cmd
msbuild MyProject.proj -t:go -fl1 -fl2 -fl3 -flp2:logfile=JustErrors.log;errorsonly -flp3:logfile=JustWarnings.log;warningsonly
```

 Daha fazla bilgi için bkz. [komut satırı başvurusu](../msbuild/msbuild-command-line-reference.md).

## <a name="save-a-binary-log"></a>İkili günlük kaydetme

**-Binarygünlükçü** (**BL**) anahtarını kullanarak günlüğü sıkıştırılmış, ikili biçimde kaydedebilirsiniz. Bu günlük, derleme işleminin ayrıntılı açıklamasını içerir ve belirli günlük analizi araçları tarafından okunabilir.

Aşağıdaki örnekte, *binarylogfilename* adlı bir ikili günlük dosyası oluşturulur.

```cmd
-bl:binarylogfilename.binlog
```

Daha fazla bilgi için bkz. [komut satırı başvurusu](../msbuild/msbuild-command-line-reference.md).

## <a name="use-a-custom-logger"></a>Özel bir günlükçü kullanma

 Arabirimini uygulayan bir yönetilen tür yazarak kendi günlüklerinizi yazabilirsiniz <xref:Microsoft.Build.Framework.ILogger> . Özel bir günlükçü, örneğin, e-postada derleme hataları göndermek, bunları bir veritabanına kaydetmek veya bir XML dosyasına kaydetmek için kullanabilirsiniz. Daha fazla bilgi için bkz. [oluşturma Günlükçüler](../msbuild/build-loggers.md).

 MSBuild komut satırında, **-günlükçü** anahtarını kullanarak özel günlükçü belirtirsiniz. Varsayılan Konsol günlükçü 'yi devre dışı bırakmak için **-noconsolegünlükçü** anahtarını da kullanabilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.Build.Framework.LoggerVerbosity>
- [Günlükçüleri derleme](../msbuild/build-loggers.md)
- [Birden çok işlemcili ortamda oturum açma](../msbuild/logging-in-a-multi-processor-environment.md)
- [İletme günlükçüleri oluşturma](../msbuild/creating-forwarding-loggers.md)
- [MSBuild kavramları](../msbuild/msbuild-concepts.md)
