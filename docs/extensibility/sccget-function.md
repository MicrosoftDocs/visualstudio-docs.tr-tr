---
title: SccGet işlevi | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- SccGet
helpviewer_keywords:
- SccGet function
ms.assetid: 09a18bd2-b788-411a-9da6-067d806e46f6
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 3955905252b2293d3c200640ea33d5c23c8fd208
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49844464"
---
# <a name="sccget-function"></a>SccGet işlevi
Bu işlev, bir veya daha fazla dosyaları görüntülemek ve derleme ancak düzenleme için bir kopyasını alır. Çoğu sistemde, dosyaları salt okunur olarak etiketlenir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
SCCRTN SccGet(  
   LPVOID    pvContext,  
   HWND      hWnd,  
   LONG      nFiles,  
   LPCSTR*   lpFileNames,  
   LONG      fOptions,  
   LPCMDOPTS pvOptions  
);  
```  
  
### <a name="parameters"></a>Parametreler  
 pvContext  
 [in] Kaynak Denetimi Eklentisi bağlam yapısı.  
  
 hWnd  
 [in] Kaynak Denetimi Eklentisi sağladığı herhangi bir iletişim kutusu için bir üst öğe olarak kullanabileceğiniz IDE penceresi için bir tanıtıcı.  
  
 nFiles  
 [in] Belirtilen dosya sayısı `lpFileNames` dizisi.  
  
 lpFileNames  
 [in] Alınacak dosyaların tam adları dizisi.  
  
 fOptions  
 [in] Komut bayrakları (`SCC_GET_ALL`, `SCC_GET_RECURSIVE`).  
  
 pvOptions  
 [in] Kaynak denetimi fişi özel seçenekleri.  
  
## <a name="return-value"></a>Dönüş değeri  
 Kaynak Denetimi Eklentisi uygulanması bu işlev, aşağıdaki değerlerden birini döndürmesi beklenir:  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|SCC_OK|Alma işlemi başarılı.|  
|SCC_E_FILENOTCONTROLLED|Dosya kaynak denetimi altında değil.|  
|SCC_E_OPNOTSUPPORTED|Kaynak denetim sistemi bu işlemi desteklemiyor.|  
|SCC_E_FILEISCHECKEDOUT|Kullanıcı şu anda kullanıma alınmış dosyası alınamıyor.|  
|SCC_E_ACCESSFAILURE|Kaynak denetim sistemi, ağ veya çakışma sorunları nedeniyle muhtemelen erişilirken sorun oluştu. Bir yeniden deneme önerilir.|  
|SCC_E_NOSPECIFIEDVERSION|Belirtilen bir sürümü geçersiz veya tarih/saat.|  
|SCC_E_NONSPECIFICERROR|Belirli olmayan hata; Dosya eşitlenmedi.|  
|SCC_I_OPERATIONCANCELED|İşlem tamamlanmadan önce iptal edildi.|  
|SCC_E_NOTAUTHORIZED|Kullanıcı bu işlemi gerçekleştirmek için yetkili değil.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu işlev, bir sayı ve bir dizi Alınacak dosya adları ile çağrılır. IDE bayrağı geçerse `SCC_GET_ALL`, öğeler buna `lpFileNames` dosyaları ancak dizin olmayan ve alınacak belirli dizinlerdeki kaynak denetimi altındaki tüm dosyaları olan.  
  
 `SCC_GET_ALL` Bayrağı ile birleştirilebilir `SCC_GET_RECURSIVE` belirli dizinlerdeki tüm dosyaları ve tüm alt dizinler de almak için bayrak.  
  
> [!NOTE]
>  `SCC_GET_RECURSIVE` hiçbir zaman olmadan geçirilmelidir `SCC_GET_ALL`. Ayrıca unutmayın dizinleri *C:\A* ve *C:\A\B* özyinelemeli get, geçirilen *C:\A\B* ve tüm alt dizinlerinde aslında iki kez alınır. IDE'nin sorumluluğundadır — ve kaynak denetim eklentinin — bunun gibi yinelenen dizinin dışında tutulduğundan emin olmak için.  
  
 Son olarak, bir kaynak denetim bile eklenti belirtilen `SCC_CAP_GET_NOUI` başlatma, Get komutu için bir kullanıcı arabirimi yok, bu işlev hala dosyaları almak için IDE tarafından çağrılan belirten bayrağı. Bayrağı yalnızca IDE Get menü öğesini görüntülemez ve herhangi bir UI sağlamak eklenti değil, beklenen anlamına gelir.  
  
## <a name="rename-files-and-sccget"></a>Dosyaları ve SccGet yeniden adlandır  
 . Durum: Örneğin, bir dosyayı kullanıma bir kullanıcı denetimleri *.txt*ve onu değiştirir. Önce *.txt* iade edilmelidir, ikinci bir kullanıcı olarak yeniden adlandırır *.txt* için *b.txt* kaynak denetim veritabanında kullanıma *b.txt*, yapar bazı değişiklikler dosyanın ve dosyanın olup olmadığını denetler. İlk kullanıcı ilk kullanıcı kendi yerel sürümü ile yeniden adlandırır. Bu nedenle, ikinci kullanıcı tarafından yapılan değişiklikleri istediği *.txt* dosyasını *b.txt* ve dosya çubuğunda bir get yapar. Bununla birlikte, sürüm numaraları ve yerel önbellek ilk sürümü hala gördüğü *.txt* yerel olarak depolanır ve kaynak denetimi farklar çözümlenemiyor.  
  
 Kaynak Denetimi sürümü, yerel önbellek burada kaynak denetimi veritabanı ile eşitlenmemiş hale gelir, bu sorunu çözmek için iki yolu vardır:  
  
1.  Kaynak denetim veritabanında şu anda kullanıma alınmış dosya yeniden adlandırılırken izin vermez.  
  
2.  "Eski Sil"tarafından yeni Ekle"ve ardından" denk yapın. Bunu yapmanın bir yolu algoritmasıdır.  
  
    1.  Çağrı [SccQueryChanges](../extensibility/sccquerychanges-function.md) işlevi, yeniden adlandırma hakkında bilgi edinmek için *.txt* için *b.txt* kaynak denetim veritabanındaki.  
  
    2.  Yerel Yeniden Adlandır *.txt* için *b.txt*.  
  
    3.  Çağrı `SccGet` işlevi hem *.txt* ve *b.txt*.  
  
    4.  Çünkü *.txt* yok kaynak denetim veritabanında eksik olan yerel sürüm önbellek temizlenir *.txt* sürüm bilgisi.  
  
    5.  *B.txt* kullanıma alınan dosya içeriğini yerel ile birleştirilmiş *b.txt* dosya.  
  
    6.  Güncelleştirilmiş *b.txt* dosya artık iade edilmelidir.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Kaynak Denetimi Eklentisi API işlevleri](../extensibility/source-control-plug-in-api-functions.md)   
 [Özel komutlar tarafından kullanılan bit bayrakları](../extensibility/bitflags-used-by-specific-commands.md)
