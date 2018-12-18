---
title: -Güvenli modda (devenv.exe) | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- /SafeMode Devenv switch
- Devenv, /SafeMode switch
- SafeMode switch
ms.assetid: b191f6a5-8f12-47ec-bcc7-b68149a22aa8
caps.latest.revision: 9
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: b785a3e43726522f6e6cc6ce99dec4bf3815c81d
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49230086"
---
# <a name="safemode-devenvexe"></a>/SafeMode (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
Başlar [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] güvenli modda, yalnızca varsayılan ortama ve Hizmetleri Yükleniyor.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
devenv /SafeMode   
```  
  
## <a name="remarks"></a>Açıklamalar  
 Bu anahtar, ne zaman yüklenmesini tüm üçüncü taraf VSPackages engeller [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] böylece kararlı yürütme sağlamaya başlar.  
  
## <a name="description"></a>Açıklama  
 Aşağıdaki örnek başlatır [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] güvenli modda.  
  
## <a name="code"></a>Kod  
  
```  
Devenv.exe /SafeMode  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Devenv Komut Satırı Anahtarları](../../ide/reference/devenv-command-line-switches.md)



