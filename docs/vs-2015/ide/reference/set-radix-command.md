---
title: Sayı tabanı komut kümesi | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- debug.setradix
helpviewer_keywords:
- Set Radix command
- Debug.SetRadix command
ms.assetid: 6ffd1554-7530-4da4-b5f5-e276a5034f3b
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: f0df00cf4c1d1264692be5ab5313eb9f03920b3c
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49296133"
---
# <a name="set-radix-command"></a>Sayı Tabanını Ayarla Komutu
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
Tamsayı değerleri görüntülemek için kullanılan sayısal taban döndürür veya ayarlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
Debug.SetRadix [10 | 16 | hex | dec]  
```  
  
## <a name="arguments"></a>Arguments  
 `10` veya `16` veya `hex` veya `dec`  
 İsteğe bağlı. Ondalık gösterir (10 veya Ara) ya da onaltılık (16 veya onaltılık). Ardından bir bağımsız değişken yoksayılırsa geçerli taban değeri döndürülür.  
  
## <a name="example"></a>Örnek  
 Bu örnek, tamsayı değerlerini onaltılık biçimde görüntülemek için ortamı ayarlar.  
  
```  
>Debug.SetRadix hex  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual Studio komutları](../../ide/reference/visual-studio-commands.md)   
 [Komut penceresi](../../ide/reference/command-window.md)   
 [Bul/komut kutusu](../../ide/find-command-box.md)   
 [Visual Studio Komut Diğer Adları](../../ide/reference/visual-studio-command-aliases.md)



