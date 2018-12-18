---
title: Bellek komut listesi | Microsoft Docs
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
- debug.listmemory
helpviewer_keywords:
- Debug.ListMemory command
- ListMemory command
- list memory command
ms.assetid: a84de361-a6a6-4f6d-96aa-a0d4a424371e
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 25be71041f0ab127037a25a03cff1d6ffe42ac97
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49224503"
---
# <a name="list-memory-command"></a>Belleği Listele Komutu
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
Belirtilen bellek aralığının içeriklerini görüntüler.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
Debug.ListMemory [/ANSI|Unicode] [/Count:number] [/Format:formattype]  
[/Hex|Signed|Unsigned] [expression]  
```  
  
## <a name="arguments"></a>Arguments  
 `expression`  
 İsteğe bağlı. Bellek görüntüleme başlayacağı bellek adresi.  
  
## <a name="switches"></a>Anahtarlar  
 / ANSI&#124;Unicode  
 İsteğe bağlı. Bellek, bellek, ANSI veya Unicode bayt için karşılık gelen karakter olarak görüntüler.  
  
 / Sayısı:`number`  
 İsteğe bağlı. Başlangıç belleği görüntülemek için kaç bayt belirler `expression`.  
  
 / Biçimi:`formattype`  
 İsteğe bağlı. Biçim türü bellek bilgileri görüntülemek için **bellek** penceresi; Mayıs OneByte, TwoBytes, FourBytes, EightBytes olabilir, Float (32-bit) veya çift (64-bit). OneByte kullanılıyorsa `/Unicode` kullanılamıyor.  
  
 / Onaltılık&#124;imzalı&#124;işaretsiz  
 İsteğe bağlı. Numaraları görüntüleme biçimini belirtir: olarak işaretli, imzasız veya onaltılık.  
  
## <a name="remarks"></a>Açıklamalar  
 Eksiksiz bir yazmak yerine **Debug.ListMemory** komut tüm anahtarların ile önceden tanımlanmış diğer adlar için belirtilen değerler önceden belirli anahtarları komutu çağırır. Örneğin, girmek yerine:  
  
```  
>Debug.ListMemory /Format:float /Count:30 /Unicode  
```  
  
 şunu yazabilirsiniz:  
  
```  
>df /Count:30 /Unicode  
```  
  
 İşte bir listesi için kullanılabilir diğer adlar, **Debug.ListMemory** komutu:  
  
|Alias|Komut ve anahtarlar|  
|-----------|--------------------------|  
|**d**|Debug.ListMemory|  
|**da**|Debug.ListMemory /Ansi|  
|**DB**|Debug.ListMemory /Format:OneByte|  
|**DC**|Debug.ListMemory /Format:FourBytes /Ansi|  
|**dd**|Debug.ListMemory /Format:FourBytes|  
|**SD**|Debug.ListMemory /Format:Float|  
|**dq**|Debug.ListMemory /Format:EightBytes|  
|**DU**|Debug.ListMemory / Unicode|  
  
## <a name="example"></a>Örnek  
  
```  
>Debug.ListMemory /Format:float /Count:30 /Unicode  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Çağrı yığınını Listele komutu](../../ide/reference/list-call-stack-command.md)   
 [İş parçacıklarını Listele komutu](../../ide/reference/list-threads-command.md)   
 [Visual Studio komutları](../../ide/reference/visual-studio-commands.md)   
 [Komut penceresi](../../ide/reference/command-window.md)   
 [Bul/komut kutusu](../../ide/find-command-box.md)   
 [Visual Studio Komut Diğer Adları](../../ide/reference/visual-studio-command-aliases.md)




