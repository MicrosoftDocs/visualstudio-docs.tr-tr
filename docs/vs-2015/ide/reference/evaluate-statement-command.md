---
title: Deyimi değerlendir komutu | Microsoft Docs
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
- debug.evaluatestatement
helpviewer_keywords:
- Debug.EvaluateStatement command
- Evaluate Statement command
ms.assetid: 032039bc-9477-4f93-9b9d-66d4be0e90f4
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: d3e50b519b162201d741f2460a8e9dbbe675c16e
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49230327"
---
# <a name="evaluate-statement-command"></a>Deyimi Değerlendir Komutu
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
Değerlendirir ve verilen deyimi görüntüler.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
Debug.EvaluateStatement text   
```  
  
## <a name="arguments"></a>Arguments  
 `text`  
 Gerekli. Değerlendirilecek ifade.  
  
## <a name="remarks"></a>Açıklamalar  
 Girmek için kullanılan pencere **EvaluateStatement** komut belirleyen bir eşittir işareti (=) karşılaştırma işleci veya bir atama işleci olarak yorumlanır.  
  
 İçinde **komut** penceresinde, eşittir işareti (=) karşılaştırma işleci yorumlanır. Örneğin, bu nedenle, değişkenlerin değerleri `a` ve `b` farklı, sonra komutu  
  
```  
>Debug.EvaluateStatement(a=b)  
```  
  
 bir değeri döndürür `false`.  
  
 İçinde **hemen** penceresinde, aksine, eşittir işareti (=) bir atama işleci yorumlanır. Bunu, örneğin, komut  
  
```  
>Debug.EvaluateStatement(a=b)  
```  
  
 atar `a` değişkenin değerini `b`.  
  
## <a name="example"></a>Örnek  
  
```  
>Debug.EvaluateStatement(a+b)  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Yazdır komutu](../../ide/reference/print-command.md)   
 [Visual Studio komutları](../../ide/reference/visual-studio-commands.md)   
 [Komut penceresi](../../ide/reference/command-window.md)   
 [Bul/komut kutusu](../../ide/find-command-box.md)   
 [Visual Studio Komut Diğer Adları](../../ide/reference/visual-studio-command-aliases.md)



