---
title: -LCID (devenv.exe) | Microsoft Docs
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
- language default
- locale IDs, setting for IDE
- Devenv, /LCID switch
- locale IDs
- /l Devenv switch
- LCID devenv switch
- /lcid Devenv switch
ms.assetid: 3a3f4e70-ea66-4351-9d62-acb1dec30e8e
caps.latest.revision: 15
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 242e0055e59312cba616859e08a2a61a45064e66
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49301918"
---
# <a name="lcid-devenvexe"></a>/LCID (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
Metin, para birimi ve diğer değerleri tümleşik geliştirme ortamında (IDE) için kullanılan varsayılan dili ayarlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
devenv {/LCID|/l} LocaleID  
```  
  
## <a name="arguments"></a>Arguments  
 `LocaleID`  
 Gerekli. Dilin LCID (yerel ayar kimliği) belirtirsiniz.  
  
## <a name="remarks"></a>Açıklamalar  
 IDE yükler ve ortam için varsayılan doğal dili ayarlar. Bu değişiklik oturumları arasında kalıcı ve yansıtılan **uluslararası ayarlar** bölmesinde **ortam** seçeneklerini **seçenekleri** iletişim kutusu IDE'de.  
  
 Belirtilen dil kullanıcının sisteminde kullanılabilir durumda değilse, / LCID anahtarı yok sayıldı.  
  
 Aşağıdaki tabloda LCID'ler tarafından desteklenen dilleri listeler [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
|Dil|LCID|  
|--------------|----------|  
|ve|2052|  
|seçenekleri yerine|1028|  
|İngilizce|1033|  
|Fransızca|1036|  
|Almanca|1031|  
|İtalyanca|1040|  
|Japonca|1041|  
|Korece|1042|  
|İspanyolca|3082|  
  
## <a name="example"></a>Örnek  
 Bu örnekte, İngilizce kaynak dizelerini IDE'ye yükler.  
  
```  
devenv /LCID 1033  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Devenv komut satırı anahtarları](../../ide/reference/devenv-command-line-switches.md)   
 [Uluslararası ayarlar, ortam, Seçenekler iletişim kutusu](../../ide/reference/international-settings-environment-options-dialog-box.md)   
 [Pencere düzenlerini özelleştirme](../../ide/customizing-window-layouts-in-visual-studio.md)



