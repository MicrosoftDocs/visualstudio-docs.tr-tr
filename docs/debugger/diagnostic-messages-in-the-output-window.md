---
title: İletilerini çıkış penceresine Gönder. | Microsoft Docs
ms.custom: ''
ms.date: 11/08/2018
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- diagnostic messages [C#]
- System.Diagnostics.Debug class, Output window
- messages, diagnostic
- Debug.Print replacements
- diagnosis
- Output window, diagnostic messages
- System.Diagnostics.Trace class, Output window
- Trace class, diagnostic messages
- diagnostics
- debugger, Output window
- debugging [Visual Studio], diagnostic messages in Output window
- Debug class
ms.assetid: 386e9524-be17-4573-83fb-4f7c5cae0be0
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 02bdd2c6d83e13887a8051ab4101627ba14220fa
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51724474"
---
# <a name="send-messages-to-the-output-window"></a>İletilerini çıkış penceresine Gönder.

Çalışma zamanı iletileri yazabileceğiniz **çıkış** penceresini kullanarak <xref:System.Diagnostics.Debug> sınıfı veya <xref:System.Diagnostics.Trace> parçası olan bir sınıf, <xref:System.Diagnostics> sınıf kitaplığı. Kullanım <xref:System.Diagnostics.Debug> , yalnızca çıkış istiyorsanız sınıfı *hata ayıklama* programınızın sürümü. Kullanım <xref:System.Diagnostics.Trace> hem de çıkış isterseniz sınıfı *hata ayıklama* ve *yayın* sürümleri.  
  
## <a name="output-methods"></a>Çıkış yöntemleri  
 <xref:System.Diagnostics.Trace> Ve <xref:System.Diagnostics.Debug> sınıfları aşağıdaki çıktı yöntemlerini sağlar:  
  
- Çeşitli `Write` yürütme bozmadan bilgi çıkış yöntemleri. Bu yöntemler yerine `Debug.Print` Visual Basic'in önceki sürümlerinde kullanılan yöntem.  
  
- <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName> ve <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=fullName> belirtilen bir koşulu başarısız olursa, yürütme ve çıkış bilgileri sonu yöntemleri. Varsayılan olarak, `Assert` yöntemi bilgileri iletişim kutusu içinde görüntüler. Daha fazla bilgi için [yönetilen koddaki onaylar](../debugger/assertions-in-managed-code.md).  
  
- <xref:System.Diagnostics.Debug.Fail%2A?displayProperty=fullName> Ve <xref:System.Diagnostics.Trace.Fail%2A?displayProperty=fullName> yürütme ve çıkış bilgileri her zaman Kes yöntemleri. Varsayılan olarak, `Fail` yöntemleri bilgileri iletişim kutusu içinde görüntüler.  
  
**Çıkış** penceresi de görüntüleyebilir bilgi hakkında:  
  
- Modüller hata ayıklayıcı yüklü veya kaldırılmış.  
  
- Oluşan özel durumlar.  
  
- Çıkış işlemleri.  
  
- Çıkış iş parçacıkları.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Hata ayıklayıcısı güvenliği](../debugger/debugger-security.md)   
 [Çıkış penceresi](../ide/reference/output-window.md)   
 [İzleme ve izleme uygulamaları](/dotnet/framework/debug-trace-profile/tracing-and-instrumenting-applications)  
 [C#, F#ve Visual Basic proje türleri](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)   
 [Yönetilen kodda hata ayıklama](../debugger/debugging-managed-code.md)
