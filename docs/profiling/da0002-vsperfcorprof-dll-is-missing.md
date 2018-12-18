---
title: 'DA0002: VSPerfCorProf.dll eksik | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.DA0002
- vs.performance.2
- vs.performance.rules.DAVsPerfCorProfMissing
- vs.performance.rules.DA0002
ms.assetid: 76e614b3-ad7e-4b92-b7be-88dc1329be1d
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 79d2352891f040f0824719d7a8f0f0b6164e2a69
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49919214"
---
# <a name="da0002-vsperfcorprofdll-is-missing"></a>DA0002: VSPerfCorProf.dll eksik

|||  
|-|-|  
|Kural Kimliği|DA0002|  
|Kategori|Profil oluşturma araçları kullanım|  
|Profil oluşturma yöntemleri|VSPerfCmd ve VSPerfASPNETCmd komut satırı araçlarını kullanarak profil oluşturma|  
|İleti|Dosya ortam değişkenlerini doğru ayarlamadan toplanmış görünüyor *VSPerfCLREnv.cmd*. Yönetilen ikililerin sembolleri çözülemiyor olabilir.|  
|Kural türü|Bilgiler|  

## <a name="cause"></a>Sebep  
 Profil oluşturucu bulunamadı *VSPerfCorProf.dll* profil oluşturma çalışması sırasında. Profil Oluşturucu veri koleksiyonu için komut satırı araçlarını kullanarak olmadan kullanıldığında, bu uyarı oluşur *VSPerfCLREnv.cmd* gerekli ortam değişkenlerini başlatmak üzere. Başka bir profil oluşturucu profil oluşturma araçları başlattığınızda çalışıyorsa uyarı da tetikleyebilir.  

## <a name="rule-description"></a>Kural açıklaması  
 .NET Framework ikili dosyaları sembolleri çözümlemek profil oluşturucu için profil oluşturma yürütmesine önce belirli ortam değişkenlerini ayarlamanız gerekir. Bu uyarı öneren *VSPerfCLREnv.cmd* aracı profil oluşturma verilerinin toplandığı önce değil çalıştırıldı. Yönetilen ikililerin sembolleri çözebilir değil. Komut satırından profil oluşturma araçlarını kullanma hakkında daha fazla bilgi için bkz. [komut satırından profil oluşturma](../profiling/using-the-profiling-tools-from-the-command-line.md)  

## <a name="how-to-fix-violations"></a>İhlaller nasıl düzeltilir?  
 Zaman profil yönetilen uygulamaların komut satırı araçları kullanarak [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] profil oluşturma, çalıştırma Araçları [VSPerfCLREnv](../profiling/vsperfclrenv.md) veri toplama başlamadan önce komut satırı aracı.