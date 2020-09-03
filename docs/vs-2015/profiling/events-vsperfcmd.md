---
title: Olaylar (VSPerfCmd) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: eb139327-4783-4f2a-874c-efad377a7be4
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 0d24fc7a01a8eebe356f37704c1a821332f5dca1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75850759"
---
# <a name="events-vsperfcmd"></a>Olaylar (VSPerfCmd)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

VSPerfCmd.exe **Events** seçeneği, Windows Için olay Izleme (ETW) günlüğünü denetler. ETW verileri, profil oluşturucu veri dosyasından ayrı bir. etl dosyasına kaydedilir. Veriler [VSPerfReport](../profiling/vsperfreport.md) /Summary: ETW komutu kullanılarak bir raporda görüntülenebilir.  
  
 Profil oluşturma işlemini durdurmak için VSPerfCmd **kapatmadan** önce herhangi bir zamanda **Olaylar** seçeneği çağrılabilir.  
  
## <a name="syntax"></a>Söz dizimi  
  
```  
VSPerfCmd.exe /events {On|Off} {Guid|ProviderName} [,Flags[,Level]  
```  
  
#### <a name="parameters"></a>Parametreler  
 **&#124;** **kapalı**  
 Olay verilerini toplamayı başlatır veya sonlandırır.  
  
 `Guid`  
 Sağlayıcı denetiminin GUID 'SI.  
  
 `ProviderName`  
 Windows Yönetim Araçları (WMI) ile kaydedilen sağlayıcının adı.  
  
 `Flags`  
 Olay sağlayıcısı tarafından tanımlanan bir "0x"-önekli onaltılık bayraklar değeri.  
  
 `Level`  
 Toplanan veri miktarını belirtir. `Level` Olay sağlayıcısı tarafından tanımlanır.  
  
 **Olaylar** seçeneği, aşağıdaki çekirdek anahtar sözcüklerini sağlayıcı adları olarak anlamıştır:  
  
 **İşleme**  
 Olay işleme  
  
 **Zincirinin**  
 İş parçacığı olayları  
  
 **Görüntü**  
 Görüntü yükleme ve kaldırma olayları  
  
 **Disk**  
 Disk g/ç olayları  
  
 **Dosya**  
 Dosya g/ç olayları  
  
 **Hardfault**  
 Sabit sayfa hataları  
  
 **Pagefault**  
 Geçici sayfa hataları  
  
 **Ağ**  
 Ağ olayları  
  
 **Kapsayıcı Kayıt Defteri**  
 Kayıt defteri erişim olayları  
  
 Çekirdek sağlayıcının yalnızca etkinleştiğine de emin olun. İzleyici kapanana kadar devre dışı bırakılamaz veya bayrakları değiştirilemez.  
  
## <a name="remarks"></a>Açıklamalar  
  
> [!NOTE]
> CLR ETW olayları etkinleştirildiğinde, Izleme görünümü raporunda ek başlangıç verileri de toplanır. Raporda görünen başlangıç olaylarını dışlamak için aşağıdaki komutu kullanın:  
  
```  
C:\<path>VSPerfCmd -events on, \".NET Common Language Runtime\", 0x7fffffff, 5  
```  
  
> [!IMPORTANT]
> Başlangıç olaylarını dışlayamazsınız, bu olaylar Yönetilen Nesne Biçimi (MOF) dosyasında listelenmediğinden raporda GUID olarak görünürler. Daha fazla bilgi için Microsoft Web sitesindeki şu sayfaya bakın: [örnek yönetilen nesne biçimi (MOF) dosyası](https://msdn.microsoft.com/library/default.aspx).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Tek başına uygulamaların profilini oluşturma](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [ASP.NET Web uygulamalarının profilini oluşturma](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Profil Oluşturma Hizmetleri](../profiling/command-line-profiling-of-services.md)
