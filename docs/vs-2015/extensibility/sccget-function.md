---
title: SccGet işlevi | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- SccGet
helpviewer_keywords:
- SccGet function
ms.assetid: 09a18bd2-b788-411a-9da6-067d806e46f6
caps.latest.revision: 15
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 78c766e52278c8bae29e57cad6f1c0255de4ea43
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51761723"
---
# <a name="sccget-function"></a>SccGet İşlevi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu işlev, bir veya daha fazla dosyaları görüntülemek ve derleme ancak düzenleme için bir kopyasını alır. Çoğu sistemde, dosyaları salt okunur olarak etiketlenir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp#  
SCCRTN SccGet(  
   LPVOID    pvContext,  
   HWND      hWnd,  
   LONG      nFiles,  
   LPCSTR*   lpFileNames,  
   LONG      fOptions,  
   LPCMDOPTS pvOptions  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
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
  
## <a name="return-value"></a>Dönüş Değeri  
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
>  `SCC_GET_RECURSIVE` hiçbir zaman olmadan geçirilmelidir `SCC_GET_ALL`. Ayrıca, dizinleri C:\A ve C:\A\B üzerinde bir özyinelemeli geçirilen her ikisini de almak ise C:\A\B ve tüm alt dizinlerinde aslında iki kez alınır olduğunu unutmayın. IDE'nin sorumluluğundadır — ve kaynak denetim eklentinin — bunun gibi yinelenen dizinin dışında tutulduğundan emin olmak için.  
  
 Son olarak, bir kaynak denetim bile eklenti belirtilen `SCC_CAP_GET_NOUI` başlatma, Get komutu için bir kullanıcı arabirimi yok, bu işlev hala dosyaları almak için IDE tarafından çağrılan belirten bayrağı. Bayrağı yalnızca IDE Get menü öğesini görüntülemez ve herhangi bir UI sağlamak eklenti değil, beklenen anlamına gelir.  
  
## <a name="renaming-and-sccget"></a>Yeniden adlandırma ve SccGet  
 Durum: bir kullanıcı, örneğin.txt, bir dosyayı kullanıma ve değiştirdiği. .Txt iade edilmeden önce ikinci bir kullanıcı.txt, kaynak denetim veritabanındaki b.txt yeniden adlandırır, out b.txt denetler, dosya için bazı değişiklikler yapar ve dosyayı iade. İlk kullanıcı, ilk kullanıcı, kendi.txt dosyasının yerel sürümünü b.txt için yeniden adlandırır ve dosya çubuğunda bir get mu ikinci kullanıcı tarafından yapılan değişiklikleri istiyor. Bununla birlikte, sürüm numaraları ve yerel önbellek hala.txt ilk sürümü yerel olarak depolanır ve bu nedenle, kaynak denetimi farklar çözümlenemiyor düşünüyor.  
  
 Kaynak Denetimi sürümü, yerel önbellek burada kaynak denetimi veritabanı ile eşitlenmemiş hale gelir, bu sorunu çözmek için iki yolu vardır:  
  
1.  Kaynak denetim veritabanında şu anda kullanıma alınmış dosya yeniden adlandırılırken izin vermez.  
  
2.  "Eski Sil"tarafından yeni Ekle"ve ardından" denk yapın. Bunu yapmanın bir yolu algoritmasıdır.  
  
    1.  Çağrı [SccQueryChanges](../extensibility/sccquerychanges-function.md) işlevi için kaynak denetim veritabanındaki b.txt.txt, yeniden adlandırma hakkında bilgi edinmek için.  
  
    2.  Yerel.txt b.txt için yeniden adlandırın.  
  
    3.  Çağrı `SccGet` .txt hem b.txt işlevi.  
  
    4.  .Txt kaynak denetim veritabanında var olmadığından, yerel sürüm önbelleğini eksik.txt sürüm bilgilerini temizlenir.  
  
    5.  Kullanıma alınan b.txt dosyanın yerel b.txt dosyasının içeriğini ile birleştirilir.  
  
    6.  Güncelleştirilmiş b.txt dosya artık denetlenebilir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Kaynak Denetimi Eklentisi API işlevleri](../extensibility/source-control-plug-in-api-functions.md)   
 [Özel Komutlar Tarafından Kullanılan Bit Bayrakları](../extensibility/bitflags-used-by-specific-commands.md)

