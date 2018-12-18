---
title: Yazdır komutu | Microsoft Docs
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
- debug.print
helpviewer_keywords:
- Debug.Print command
- Print method
- Print command
ms.assetid: 0412d381-590a-483f-bab4-6e1cca095645
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: e742b1fa6a25525d33e7b8a6fcb321cfea86f693
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49232758"
---
# <a name="print-command"></a>Yazdır Komutu
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
Bir ifadeyi değerlendirir veya belirtilen metni görüntüler.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
Debug.Print text  
```  
  
## <a name="arguments"></a>Arguments  
 `text`  
 Gerekli. Değerlendirilecek ifade veya görüntülenecek metin.  
  
## <a name="remarks"></a>Açıklamalar  
 Bu komut için bir diğer ad olarak, soru işareti (?) kullanabilirsiniz. Bunu, örneğin, komut  
  
```  
>Debug.Print expA  
```  
  
 Ayrıca yazılabilir  
  
```  
>? expA  
```  
  
 Bu komutun her iki sürümü ifadenin geçerli değerini döndürecektir `expA`.  
  
## <a name="example"></a>Örnek  
  
```  
>Debug.Print varA  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Deyimi değerlendir komutu](../../ide/reference/evaluate-statement-command.md)   
 [Visual Studio komutları](../../ide/reference/visual-studio-commands.md)   
 [Komut penceresi](../../ide/reference/command-window.md)   
 [Bul/komut kutusu](../../ide/find-command-box.md)   
 [Visual Studio Komut Diğer Adları](../../ide/reference/visual-studio-command-aliases.md)



