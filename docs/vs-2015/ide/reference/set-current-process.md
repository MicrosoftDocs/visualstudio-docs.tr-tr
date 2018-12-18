---
title: Geçerli işlemi Ayarla | Microsoft Docs
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
- Debug.SetCurrentProcess command
- Set Current Process command
ms.assetid: 1e016ebd-aadd-411f-a606-03bf69d3f8aa
caps.latest.revision: 13
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 0baea39c341e8034ff222de32548d0518f115e82
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49246668"
---
# <a name="set-current-process"></a>Geçerli Süreci Ayarla
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
Belirtilen işlemi Hata ayıklayıcıdaki etkin işlem olarak ayarlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
Debug.SetCurrentProcess index  
```  
  
## <a name="arguments"></a>Arguments  
 `index`  
 Gerekli. İşlem dizini.  
  
## <a name="remarks"></a>Açıklamalar  
 Hata ayıklama, ancak yalnızca bir işlem dublajcı içerisinde belirli bir zamanda birden çok işleme iliştirebilirsiniz. Kullanabileceğiniz `SetCurrentProcess` etkin işlemi ayarlamak için komutu.  
  
## <a name="example"></a>Örnek  
  
```  
>Debug.SetCurrentProcess 1  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual Studio komutları](../../ide/reference/visual-studio-commands.md)   
 [Komut penceresi](../../ide/reference/command-window.md)   
 [Visual Studio Komut Diğer Adları](../../ide/reference/visual-studio-command-aliases.md)



