---
title: -Updateconfiguration (devenv.exe) | Microsoft Docs
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
- /updateconfiguration Devenv switch
- Devenv, /updateconfiguration switch
- updateconfiguration Devenv switch
ms.assetid: 9a1084cc-8b68-4ccc-aaea-f95939164338
caps.latest.revision: 7
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: ed69bf8c54d3b428907b4dbe0636f2966254de75
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49253642"
---
# <a name="updateconfiguration-devenvexe"></a>/ Updateconfiguration (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
Bildirir [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] birleştirilecek [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] sistem ve MEF paketleri önbelleğe herhangi bir değişiklik.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
devenv /updateconfiguration  
```  
  
## <a name="remarks"></a>Açıklamalar  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Bu komut, bir VSIX paketi yüklediğinizde otomatik olarak çalıştırır. Çalıştırmalısınız `devenv.exe /updateconfiguration` dosyalarınızı düzeltme eki uygulama sonra böylece [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] MEF önbelleği güncelleştirir. Bu, düzeltmenizi yeterli olup olmadığını değerlendirmek sağlar.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki komut satırı nedenleri [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] birleştirilecek [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] sistem ve MEF paketleri önbelleğe herhangi bir değişiklik.  
  
```  
Devenv.exe /updateconfiguration  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual Studio'da geliştirme ayarlarını özelleştirme](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3)   
 [Devenv Komut Satırı Anahtarları](../../ide/reference/devenv-command-line-switches.md)



