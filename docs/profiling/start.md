---
title: Başlangıç | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: b85d0fe9-f67a-4b7c-8d48-7eecf3f2dfe9
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: dbecc61e5203495e33aa4417e954607d8cdf6be8
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "35677815"
---
# <a name="start"></a>Başlat
**Başlat** seçeneği bir *VSPerfCmd.exe* seçeneği belirtilen profil oluşturma metodu için profil oluşturucuyu başlatır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cmd  
VSPerfCmd.exe /Start:Method /Output:FileName [Options]  
```  
  
#### <a name="parameters"></a>Parametreler  
 `Method`  
 Aşağıdaki anahtar sözcükler biri olmalıdır:  
  
-   **İzleme** -izleme metodunu belirtir.  
  
-   **ÖRNEK** -örnekleme yöntemini belirtir.  
  
-   **KAPSAMI** -kod kapsamı belirtir.  
  
-   **EŞZAMANLILIK** -kaynak çekişmesi yöntemini belirtir.  
  
## <a name="required-options"></a>Gerekli seçenekleri  
 **Çıkış** seçeneği olmalıdır belirtilen **Başlat** komut satırında belirtilen.  
  
 **Çıkış:** `filename`  
 Çıkış dosyası adını belirtir.  
  
## <a name="exclusive-options"></a>Dışlayan seçenekleri  
 Aşağıdaki seçenekler ile yalnızca kullanılabilir **Başlat** bir komut satırı seçeneği.  
  
 **CrossSession**&#124;**CS**  
 Etkinleştirir çapraz profil oluşturma işlem. Seçenek adları **CrossSession** ve **CS** desteklenen olan iki.  
  
 **Kullanıcı:**[`domain\`]`username`  
 İstemci erişimi belirtilen hesaptan izleyiciye sağlar.  
  
 **WinCounter:** `Path` [**Automark**:`n`]  
 **WinCounter** bir profil oluşturma veri dosyasını işareti olarak eklemek için bir Windows performans sayacı belirtir. **Otomatik işaret zamanının** veri dosyasının koleksiyonları arasındaki milisaniye olarak zaman aralığını belirtir.  
  
## <a name="invalid-options"></a>Geçersiz Seçenekler  
 Aşağıdaki seçenekler kullanılamaz **Başlat** bir komut satırı seçeneği.  
  
 **Status**  
 **Durum** profillenen bu işlemleri için geçerlidir. Bu işlemler, iş parçacıkları ve onların geçerli profil durumlarının (açık/kapalı) listeler. Örneğin, bir işlem durursa, **durumu** raporda belirtmez. **Durum** işlem ya da veya profil oluşturulan olduğunu gösterir.  
  
 **Kapatma**[**:**`Timeout`]  
 Profil oluşturucuyu devre dışı bırakır.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek nasıl kullanılacağını gösterir *VSPerfCmd.exe* **Başlat** seçeneği profil oluşturucu başlatılamadı.  
  
```cmd  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
VSPerfCmd.exe /Launch:TestApp.exe  
```  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Bağımsız uygulamalar profili](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Profil ASP.NET web uygulamaları](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Profil hizmetler](../profiling/command-line-profiling-of-services.md)