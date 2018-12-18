---
title: İşareti | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 1d72cef3-bb09-4bbb-8864-6ea0ab623ff9
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 89a26a3a3729241cb4ec9180e6cb16f131194b86
ms.sourcegitcommit: ce154aee5b403d5c1c41da42302b896ad3cf8d82
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/07/2018
ms.locfileid: "34844800"
---
# <a name="mark"></a>İşaret
*VSPerfCmd.exe* **işareti** seçeneği belirtilen bilgileri profil oluşturma veri dosyasına ekler. Profil Oluşturucu UI işareti rapor görünümü veya ayrı bir VSPerfReport raporlarında işareti listelenebilir. **İşareti** başlangıç ve bitiş noktalarını rapor ve Görünüm filtreleri belirtmek için kullanılır.  
  
 **İşareti** seçeneği, komut satırında belirtilen tek seçenek olmalıdır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cmd  
VSPerfCmd.exe /Mark:MarkID,[MarkName]  
```  
  
#### <a name="parameters"></a>Parametreler  
 `MarkID`  
 Profil Oluşturucu görünümleri ve raporlarda işareti kimliği olarak listelenen bir kullanıcı tanımlı bir tamsayı. `MarkID` benzersiz olması gerekmez.  
  
 `MarkName`  
 (İsteğe bağlı) Profil Oluşturucu görünümler ve raporlar işareti adı olarak listelenen bir kullanıcı tarafından tanımlanan bir dize. Varsa `MarkName` belirtilmezse, işareti dökümün işareti adı alanı boş olur. Boşluk içeremez veya eğik tırnak işaretleri ("/") iletmek dizeleri alın.  
  
## <a name="example"></a>Örnek  
 Bu örnek 123 Kimliğine ve "TestMark" işareti adını işaretiyle ekler.  
  
```cmd  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
VSPerfCmd.exe /Launch:TestApp.exe  
VSPerfCmd.exe /Mark:123,TestMark  
```  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Bağımsız uygulamalar profili](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Profil ASP.NET web uygulamaları](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Profil Hizmetleri](../profiling/command-line-profiling-of-services.md)