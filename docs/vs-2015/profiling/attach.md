---
title: Ekleme | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 79614283-6733-4592-a53a-d428052271ad
caps.latest.revision: 17
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 136ee79c8fc7a3c6d627d186cb2f0dd0266b7a42
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51727329"
---
# <a name="attach"></a>İliştir
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

VSPerfCmd.exe **iliştirme** seçeneği, çalışan işlemin işlem kimliği (PID) tarafından belirtilen örnek profil oluşturma başlar.  
  
 Kullanılacak **iliştirme** seçeneğini belirtmelisiniz **örnek** başlangıç seçeneği yöntemi.  
  
> [!NOTE]
>  Varsa **Başlat** seçeneği ile belirtilen **Crosssession** seçeneğini çağrıları **VSPerfCmd /Attach** veya **VSPerfCmd/detach** gerekir Ayrıca belirtin **Crosssession**.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
VSPerfCmd.exe /Attach:ProcessID [Options]  
```  
  
#### <a name="parameters"></a>Parametreler  
 `ProcessID`  
 İşlem kimliği (PID) çalışan işleminin. Windows Görev Yöneticisi'nin İşlemler sekmesinde bir çalışan işleminin PID listeleniyor.  
  
## <a name="valid-options"></a>Geçerli seçenekler şunlardır:  
 Aşağıdaki **VSPerfCmd** seçenekleri ile birleştirilebilir **iliştirme** tek bir komut satırı seçeneği.  
  
 **Crosssession**  
 Oturumlarında oturum dışındaki uygulamaların profilini oluşturma etkinleştirir. Gerekli if **Başlat** seçeneği ile belirtilen **Crosssession** seçeneği.  
  
 **Başlat:** `Method`  
 Komut satırı Profil Oluşturucu oturumu başlatır ve belirtilen profil oluşturma yöntemini ayarlar.  
  
 **TargetCLR**  
 Profil oluşturma oturumu içinde birden fazla sürümü yüklendiğinde, .NET Framework ortak dil çalışma zamanı (CLR) profil sürümü belirtir. Varsayılan olarak, ilk yüklenen sürümü profil oluşturulan.  
  
 **GlobalOn ve GlobalOff**  
 Sürdürür (**GlobalOn**) veya duraklatır (**GlobalOff**) profil oluşturma, ancak profil oluşturma oturumu sona ermez.  
  
 **ProcessOn:** `PID` **ProcessOff:** `PID`  
 Sürdürür (**ProcessOn**) veya duraklatır (**ProcessOff**) belirtilen işlem için profil oluşturma.  
  
## <a name="interval-options"></a>Aralık Seçenekleri  
 Örnekleme aralığı şunlardan birini Ekle komut satırında belirtilebilir. Varsayılan örnekleme aralığı 10.000.000 işlemci saat döngülerini ' dir.  
  
 **Zamanlayıcı**[**:**`Cycles`]**PF**[**:**`Events`]**Sys**[<strong>:</strong> Olayları]**sayacı**[**:**`Name`,`Reload`,`FriendlyName`]  
 Sayısı ve örnekleme aralığı türünü belirtir.  
  
-   **Zamanlayıcı** -örnekleri her `Cycles` işlemci saat döngüsü. Varsa `Cycles` belirtilmezse, 10.000.000 döngüleri kullanılır.  
  
-   **PF** -örnekleri her `Events` sayfa hataları. Varsa `Events` belirtilmezse, 10 sayfa hataları kullanılır.  
  
-   **Sys** -örnekleri her `Events` işletim sistem çağrıları. Varsa `Events` belirtilmezse, 10 sistem çağrıları kullanılır.  
  
-   **Sayaç** -örnekleri her `Reload` CPU performans sayaç tarafından belirtilen sayıda `Name`. İsteğe bağlı olarak, `FriendlyName` profil oluşturucusu raporu sütun başlığına olarak kullanılacak bir dize belirtebilirsiniz.  
  
## <a name="example"></a>Örnek  
 Bu örnek uygulamanın çalışan bir örneği 12345 işlem kimliği eklemek nasıl gösterir.  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
VSPerfCmd.exe /Attach:12345  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Bağımsız uygulamaların profilini oluşturma](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [ASP.NET Web uygulamalarında profil oluşturma](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Profil Oluşturma Hizmetleri](../profiling/command-line-profiling-of-services.md)



