---
title: Sınıf tasarımcısında Visual C++ numaralandırmaları | Microsoft Docs
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
- Class Designer [Visual Studio], enumerations
ms.assetid: 11e90ba1-18cd-44f8-9e26-e3746a7a19d1
caps.latest.revision: 14
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: b9d88cb954e89cfd6401f674fbbbc901ac634982
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49236366"
---
# <a name="visual-c-enumerations-in-class-designer"></a>Sınıf Tasarımcısında Visual C++ Numaralandırmaları
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sınıf Tasarımcısı, C++ destekler `enum` ve kapsamlı `enum class` türleri. Bir örneği verilmiştir:  
  
```  
enum CardSuit {  
   Diamonds = 1,  
   Hearts = 2,  
   Clubs = 3,  
   Spades = 4  
};  
  
// or...  
enum class CardSuit {  
   Diamonds = 1,  
   Hearts = 2,  
   Clubs = 3,  
   Spades = 4  
};  
  
```  
  
 Sınıf diyagramında C++ numaralandırma şekli görünür ve etiketi dışında bir yapı şeklinde çalışır **Enum** veya **sabit listesi sınıfı**, mavi yerine pembe ve sol üst taraftaki renkli kenarlık vardır Kenar boşlukları. Numaralandırma şekilleri ve yapı şekilleri dörtgen köşelerine sahiptir.  
  
 Kullanma hakkında daha fazla bilgi için `enum` yazın, bkz: [numaralandırmalar](http://msdn.microsoft.com/library/081829db-5dca-411e-a53c-bffef315bcb3).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual C++ kodu (Sınıf Tasarımcısı) ile çalışma](../ide/working-with-visual-cpp-code-class-designer.md)   
 [Sabit Listeleri](http://msdn.microsoft.com/library/081829db-5dca-411e-a53c-bffef315bcb3)



