---
title: Durum | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: ba656fa4-ef9d-4d8c-a3b6-739c3b5d23ae
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 5cd721dc6682057519821ee155ac8a5d803769dc
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "35677138"
---
# <a name="status"></a>Durum
*VSPerfCmd.exe* **durumu** seçeneği profil oluşturucuyu ve şu anda profillenen herhangi bir işlem durumuyla ilgili bilgileri görüntüler.  
  
 **Durumu** seçeneği, komut satırında belirtilen tek seçenek olması gerekir. Profil Oluşturucu ile başlatılmalıdır *VSPerfCmd.exe* **Başlat** herhangi bir durum görüntülenebilmesi seçeneği.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cmd  
VSPerfCmd.exe /Status  
```  
  
#### <a name="parameters"></a>Parametreler  
 Yok.  
  
## <a name="remarks"></a>Açıklamalar  
 **Durumu** seçeneği profil oluşturucu için aşağıdaki durum bilgileri görüntülenir.  
  
 **Çıkış dosyası adı**  
 Geçerli profil oluşturucu veri dosyasının yolu ve dosya adı.  
  
 **Koleksiyon modu**  
 Örnek veya izleme  
  
 **En fazla işlem**  
 Tek seferde profili işlemlerin sayısı ve şu anda etkin işlem sayısı.  
  
 **En fazla iş parçacığı**  
 Tek seferde profili iş parçacığı sayısı.  
  
 **Arabellek sayısı**  
 Profil oluşturma veri yazmada ayrılmış bellek arabellek sayısı.  
  
 **Arabellek boyutu**  
 Bir bellek arabelleğin bayt cinsinden boyutu.  
  
 **Durumu** seçeneği şu anda profili oluşturulan her işlem için aşağıdaki durum bilgileri görüntüler.  
  
 **İşlem**  
 Profilli işlemin adı.  
  
 **İşlem kimliği**  
 İşlem sistem tanımlayıcısı.  
  
 **İş parçacığı sayısı**  
 Şu anda çalışan iş parçacıklarının sayısı.  
  
 **Başlat/Durdur sayısı**  
 Bu işlem için veri toplamayı denetlemek için birincil iç Profil Oluşturucu sayısı. Sayısı, veri toplamak için birine eşit olmalıdır. Başlat/Durdur sayısını gösterilen VSPerfCmd seçenek ve profil oluşturucu API'ler ile yönetilebilir **GlobalOn**, **GlobalOff**, **ProcessOn**, **ProcessOff**, **ThreadOn**, ve **ThreadOff**.  
  
 **Askıya alma/sürdürme sayısı**  
 Bu işlem için veri toplamayı denetlemek için ikincil iç Profil Oluşturucu sayısı. Sayısı, veri toplamak için sıfıra eşit veya daha az olmalıdır. **Askıya alma/sürdürme** sayısı yalnızca profil oluşturucu tarafından API'leri yönetilebilir.  
  
 **İzleyiciye erişim hakkına sahip kullanıcılar**  
 Profil Oluşturucu için erişime sahip kullanıcılar adlarını listeler. Ek kullanıcılar verilebilir erişim VSPerfCmd.exe kullanarak **yönetici** seçeneği  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Bağımsız uygulamalar profili](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Profil ASP.NET web uygulamaları](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Profil hizmetler](../profiling/command-line-profiling-of-services.md)