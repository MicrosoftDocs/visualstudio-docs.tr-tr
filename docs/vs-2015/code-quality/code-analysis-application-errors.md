---
title: Kod çözümleme uygulama hataları | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- errors [Visual Studio ALM], code analysis
- code analysis, errors
- managed code, code analysis errors
- code analysis, policy errors
ms.assetid: d8fd9475-ac9b-4085-b5a3-b0c807922cac
caps.latest.revision: 25
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 66d611903c71cc526c01c1062c85ceef2e7975f5
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49225023"
---
# <a name="code-analysis-application-errors"></a>Kod Çözümleme Uygulama Hataları
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]
Bu bölüm, yönetilen kod analizi aracı tarafından oluşturulan hata iletileri bir başvurudur. Belirli hata iletileri için Yardım almak için hata numarası yazın **Ara** dizinde kutusu.

## <a name="in-this-section"></a>Bu Bölümde

|||
|-|-|
|[CA0001](ca0001.md)|Beklenen hata koşulu göstermez yönetilen kod çözümleme aracı içinde bir özel durum oluştu.|
|[CA0051](ca0051.md)|Hiçbir kural seçilmedi.|
|[CA0052](ca0052.md)|Analiz etmek için hiçbir hedef seçilmedi.|
|[CA0053](ca0053.md)|Kural derlemesi yüklenemedi.|
|[CA0054](ca0054.md)|Bir özel kural derlemesi geçersiz XML kaynaklara sahip.|
|[CA0055](ca0055.md)|Dosya yüklenemedi:\<yolu >|
|[CA0056](ca0056.md)|Bir proje dosyası, analiz aracı yanlış bir sürümü vardır.|
|[CA0057](ca0057.md)|Hedefleri ve kuralları geçerli kümesine ihlalleri eşlenemez.|
|[CA0058](ca0058.md)|Başvurulan derlemeler yüklenemiyor.|
|[CA0059](ca0059.md)|Komut satırı anahtarı hatası.|
|[CA0060](ca0060.md)|Dolaylı olarak başvurulan derlemeler yüklenemiyor.|
|[CA0061](ca0061.md)|Kural '*RuleId*' bulunamadı.|
|[CA0062](ca0062.md)|Kural '*RuleId*'Kural kümesinde başvurulan'*RuleSetName*' bulunamadı.|
|[CA0063](ca0063.md)|Kural kümesi dosyası veya bağlantılı kural kümesi dosyalarından biri yüklenemedi.|
|[CA0064](ca0064.md)|Belirtilen kural kümesi herhangi FxCop kuralı içermiyor olduğundan, hiçbir analiz gerçekleştirilmedi.|
|[CA0065](ca0065.md)|Desteklenmeyen Meta veri yapısı: türü '*TypeName*'hem bir özellik hem de aynı ada sahip bir alan içeriyor'*PropertyFieldName*'|
|[CA0066](ca0066.md)|Değer '*VersionID*' için sağlanan **/targetframeworkversion** tanınan bir sürüm değil.|
|[CA0067](ca0067.md)|Dizin bulunamadı.|
|[CA0068](ca0068.md)|Hata ayıklama bilgileri hedef derleme için bulunamadı *'AssemblyName'*.|
|[CA0069](ca0069.md)|Diğer platformlar kullanıyor. *FrameworkVersion1* bulunamadı. Kullanarak *FrameworkVersion2* yerine. İçin en iyi analiz sonuçları doğru .NET Framework yüklü emin olun.|
|[CA0070](ca0070.md)|Derleme veya tür güvenlik izinleri nedeniyle yüklenemiyor.|
|[CA0501](ca0501.md)|Çıkış raporu okunamıyor.|
|[CA0502](ca0502.md)|Desteklenmeyen dil.|
|[CA0503](ca0503.md))|Deprectated özelliğidir. Superceding özelliğini kullanın|
|[CA0504](ca0504.md)|Kural dizini yok sayıldı|
|[CA0505](ca0505.md)|Deprectated özelliğidir. Superceding özelliğini kullanın|
|[FxCopCmd Hataları](fxcopcmd-errors.md)|Yönetilen kod çözümleme hataları.|
|[Kod Çözümleme İlkesi Hataları](../code-quality/code-analysis-policy-errors.md)|Kod Analizi iade etme İlkesi hataları.|

## <a name="related-sections"></a>İlgili Bölümler

- [Güvenli kod yazma yönergeleri](http://msdn.microsoft.com/en-us/9892fd19-45cd-44b6-9fa8-10f1b5cb6ea4)
- [Yönetilen Kod Kalitesini Analiz Etme](../code-quality/analyzing-managed-code-quality-by-using-code-analysis.md)
- [Uygulama yaşam döngüsü Yönetim Araçları hatalarında sorun giderme için kaynaklar](http://msdn.microsoft.com/library/76ca8f76-1e2d-4b55-89e2-bd59e4abe74c)