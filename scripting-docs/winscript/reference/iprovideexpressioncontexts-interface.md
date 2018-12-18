---
title: Iprovideexpressioncontexts arabirimi | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IProvideExpressionContexts interface
ms.assetid: e4c70f2c-7d86-4fdc-a1cb-f5a0bb8ed037
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 402b439da6f1fa369accacb27f987ac77119e343
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24794585"
---
# <a name="iprovideexpressioncontexts-interface"></a>IProvideExpressionContexts Arabirimi
Belirli bir bileşen tarafından bilinen ifade bağlamları numaralandırmak için bir yol sağlar. Komut dosyası motorları, genellikle bu arabirimi uygular.  
  
 İşlem Hata Ayıklama Yöneticisi'ni, belirli bir iş parçacığı ile ilişkili tüm genel ifade bağlamları bulmak için bu arabirimi kullanır.  
  
> [!NOTE]
>  Bu arabirime ilgilendiğiniz iş parçacığı içinde çağrılır. Geçerli iş parçacığının tanımlamak ve uygun bir numaralandırıcı dönmek için uygulayan kadar olur.  
  
## <a name="methods"></a>Yöntemler  
 Kaynağından devralındı yöntemleri yanı sıra `IUnknown`, `IProvideExpressionContexts` arabirimi aşağıdaki yöntemleri sunar.  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[IProvideExpressionContexts::EnumExpressionContexts](../../winscript/reference/iprovideexpressioncontexts-enumexpressioncontexts.md)|Bu bileşen tarafından bilinen ifade bağlamlarının bir numaralandırıcı döndürür.|