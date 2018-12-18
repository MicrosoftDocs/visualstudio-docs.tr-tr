---
title: İleti kodları | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- message codes
ms.assetid: 9f91f4e2-c1f1-4349-9f11-2fbbf59654be
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 25b2061d9f20da8e9c4d5b4f9794f400d638260c
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2018
ms.locfileid: "31474449"
---
# <a name="message-codes"></a>İleti Kodları
Gösterilen her ileti satırı [iletiler görünümü](../debugger/messages-view.md) 'P,' içeren kullanıcının,' ın,' veya 'R' kod. Bu kodları şu anlama gelir:  
  
|Kod|Açıklama|  
|----------|-------------|  
|P|İleti kuyruğa ile deftere **PostMessage** işlevi. İletinin ultimate değerlendirme ilgili hiçbir bilgi kullanılabilir.|  
|S|İleti ile gönderilmiş **SendMessage** işlevi. Başka bir deyişle, alıcı işler ve iletiyi döndürür kadar gönderen denetim gerekse değil. Alıcı bu nedenle, bir dönüş değeri gönderene geçirebilir.|  
|s|İleti gönderildi ancak güvenlik için dönüş değerini erişimi engeller.|  
|R|Her kullanıcının ' iletisi dönüş değeri listeler karşılık gelen bir 'R' (iade) satır bulunur. Bazen, bir ileti işleyicisi başka bir ileti gönderir başka bir deyişle, ileti çağrıları yerleştirilir.|