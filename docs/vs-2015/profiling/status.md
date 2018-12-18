---
title: Durum | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ba656fa4-ef9d-4d8c-a3b6-739c3b5d23ae
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: da53fa3ecb1b13837b13c3183cdb0b6590305449
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51765798"
---
# <a name="status"></a>Durum
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

VSPerfCmd.exe **durumu** seçeneği profil oluşturucuyu ve şu anda profillenen herhangi bir işlem durumuyla ilgili bilgileri görüntüler.  
  
 **Durumu** seçeneği, komut satırında belirtilen tek seçenek olması gerekir. Profil Oluşturucu ile VSPerfCmd.exe başlatılmalıdır **Başlat** herhangi bir durum görüntülenebilmesi seçeneği.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Bağımsız uygulamaların profilini oluşturma](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [ASP.NET Web uygulamalarında profil oluşturma](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Profil Oluşturma Hizmetleri](../profiling/command-line-profiling-of-services.md)



