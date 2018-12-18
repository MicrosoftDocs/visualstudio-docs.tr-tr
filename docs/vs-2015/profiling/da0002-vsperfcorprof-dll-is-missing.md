---
title: 'DA0002: VSPerfCorProf.dll eksik | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.performance.DA0002
- vs.performance.2
- vs.performance.rules.DAVsPerfCorProfMissing
- vs.performance.rules.DA0002
ms.assetid: 76e614b3-ad7e-4b92-b7be-88dc1329be1d
caps.latest.revision: 19
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bb1359b525b286dbc88cbd3d8eecaef27060ab23
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51809473"
---
# <a name="da0002-vsperfcorprofdll-is-missing"></a>DA0002: VSPerfCorProf.dll eksik
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Kural Kimliği | DA0002 |  
| Kategori | Profil oluşturma araçları kullanım |  
| Profil oluşturma yöntemlerini | VSPerfCmd ve VSPerfASPNETCmd komut satırı araçlarını kullanarak profil oluşturma |  
| İleti | Dosya ortam değişkenleri VSPerfCLREnv.cmd ile düzgün şekilde ayarlamadan toplanmış görünür. Yönetilen ikililerin sembolleri olmayan çözebilir. |  
| Kural türü | Bilgi |  
  
## <a name="cause"></a>Sebep  
 Profil Oluşturucu, profil oluşturma çalışması süresince VSPerfCorProf.dll bulunamadı. Profil Oluşturucu veri koleksiyonu için komut satırı araçları gerekli ortam değişkenlerini başlatmak için VSPerfCLREnv.cmd Aracı'nı kullanarak olmadan kullanıldığında, bu uyarı oluşur. Başka bir profil oluşturucu profil oluşturma araçları başlattığınızda çalışıyorsa uyarı da tetikleyebilir.  
  
## <a name="rule-description"></a>Kural Tanımı  
 .NET Framework ikili dosyaları sembolleri çözümlemek profil oluşturucu için profil oluşturma yürütmesine önce belirli ortam değişkenlerini ayarlamanız gerekir. Bu uyarı, profil oluşturma verilerinin toplandığı önce VSPerfCLREnv.cmd aracı çalıştırılmadı önerir. Yönetilen ikililerin sembolleri çözebilir değil. Komut satırından profil oluşturma araçlarını kullanma hakkında daha fazla bilgi için bkz. [komut satırından profil oluşturma](../profiling/using-the-profiling-tools-from-the-command-line.md)  
  
## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?  
 Zaman profil yönetilen uygulamaların komut satırı araçları kullanarak [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] profil oluşturma, çalıştırma Araçları [VSPerfCLREnv](../profiling/vsperfclrenv.md) veri toplama başlamadan önce komut satırı aracı.



