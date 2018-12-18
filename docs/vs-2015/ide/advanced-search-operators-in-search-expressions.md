---
title: Arama işleçlerini arama ifadelerindeki Gelişmiş | Microsoft Docs
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
- Help Viewer 2.0, searching for keywords
- Help Viewer 2.0, searching code
- Help Viewer 2.0, searching code by programming language
- Help Viewer 2.0, searching titles
- searching code [Help Viewer 2.0]
- searching titles [Help Viewer 2.0]
ms.assetid: 0cdc1746-8481-45ec-9c53-d0d89cdcbd5e
caps.latest.revision: 11
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 706d6d89d46a1e5db4f94c2e7d5e35ace73e1bac
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49178009"
---
# <a name="advanced-search-operators-in-search-expressions"></a>Arama İfadelerindeki Gelişmiş Arama İşleçleri
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Gelişmiş arama işleçleri kullanarak aramanızı içerik için daha basit olanlardan daha karmaşık arama ifadeler oluşturarak iyileştirebilirsiniz. Aşağıdaki tabloda gösterildiği gibi bu işleçler, bir sorgu çalıştığı bağlam kısıtlayın.  
  
> [!WARNING]
>  Son iki nokta üst üste ve arama motoru için iki noktadan önce boşluk olmaması Gelişmiş arama işleçleri tanıması için girmeniz gerekir.  
  
|Aramak için|Bir yönetim grubuna bağlanmak veya bağlı bir yönetim grubunun özelliklerini düzenlemek için Yönetim çalışma alanında|Örnek|Sonuç|  
|-------------------|---------|-------------|------------|  
|Bir konu başlığının terimi|Başlık:|Başlık: binaryreader|Kendi başlıklarında "binaryreader" içeren konulardır.|  
|Bir kod örneği bir terimi|Kod:|Kod: readdouble|Bir kod örneğinde "readdouble" içeren konulardır.|  
|Bir terimi belirli bir programlama dili örneği|Kod: vb:|Kod: vb:string|Visual Basic örneği "dize" içeren konulardır.|  
|Belirli bir dizin anahtar sözcüğüyle ilişkili konu|Anahtar:|anahtar sözcüğü: readbyte|"Readbyte" dizin anahtar sözcüğü ile ilgili konular.|  
  
 Kodu kullanabilirsiniz: işleç çeşitli programlama dilleri, ancak ilgili içeriği bulmak için belirli bir programlama dili ile işaretlenmiş içerik için sonuçları döndürür. Aşağıdaki tabloda bu işleci destekleyen programlama dilleri listeler:  
  
|Programlama dili|Bir yönetim grubuna bağlanmak veya bağlı bir yönetim grubunun özelliklerini düzenlemek için Yönetim çalışma alanında|  
|--------------------------|---------|  
|Visual Basic|Kod: vb<br /><br /> veya<br /><br /> Kod: visualbasic|  
|C#|Kod: c#<br /><br /> veya<br /><br /> Kod: csharp|  
|C++|Kod: cpp<br /><br /> veya<br /><br /> Kod: c ++<br /><br /> veya<br /><br /> Kod: cplusplus|  
|F#|Kod: f #<br /><br /> veya<br /><br /> Kod: fsharp|  
|JavaScript|Kod: javascript<br /><br /> veya<br /><br /> Kod: js|  
|XAML|Kod: xaml|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Arama ifadelerindeki mantıksal işleçler](../ide/logical-operators-in-search-expressions.md)   
 [Tam Metin Arama İpuçları](../ide/full-text-search-tips.md)



