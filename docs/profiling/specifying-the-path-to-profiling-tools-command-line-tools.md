---
title: Profil oluşturma yolunu belirtme Araçları komut satırı araçları | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 7047bf18-5779-4f6e-872c-66e2fc47c969
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1afb0b00a7e121c611dedbc235684a67cc9cec53
ms.sourcegitcommit: 1b9c1e333c2f096d35cfc77e846116f8e5054557
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2018
ms.locfileid: "34814501"
---
# <a name="specify-the-path-to-profiling-tools-command-line-tools"></a>Profil oluşturma araçları komut satırı araçları yolunu belirtin
Yolunu [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] profil oluşturma araçları komut satırı araçları PATH ortam değişkenine eklenmez. 32-bit bilgisayarlarda, tek bir dizin araçlardır. 32 bit ve 64-bit sürümü 64-bit bilgisayarlarda profil oluşturma araçları vardır.  
  
## <a name="32-bit-computers"></a>32-bit bilgisayarlar  
 32-bit bilgisayarlarda, varsayılan profil oluşturucu Araçlar dizinidir *önyükleme sürücüsü\Program Files\Microsoft Visual Studio 11.0\Team Araçlar\Performans Araçları*.  
  
## <a name="64-bit-computers"></a>64 bit bilgisayarlar  
 64-bit bilgisayarlarda, profili uygulamanın hedef platformu göre yolu belirtin.  
  
-   32-bit uygulamalar için varsayılan profil oluşturucu Araçlar dizindir:  
  
     *önyükleme sürücüsü\Program dosyaları (x86) \Microsoft Visual Studio 11.0\Team Araçlar\Performans araçları*  
  
-   64-bit uygulamalar için varsayılan profil oluşturucu Araçlar dizindir:  
  
     *önyükleme sürücüsü\Program dosyaları (x86) \Microsoft Visual Studio 11.0\Team Araçlar\Performans Tools\x64*