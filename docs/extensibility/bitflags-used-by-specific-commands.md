---
title: Özel komutlar tarafından kullanılan bit bayrakları | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, bitflags used by specific commands
ms.assetid: 37969977-6f7d-45c9-ba03-1306ae71f5d1
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 39451e8d404e586d77de31b97db6b8dd81bdc18b
ms.sourcegitcommit: 0e5289414d90a314ca0d560c0c3fe9c88cb2217c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/19/2018
ms.locfileid: "39152120"
---
# <a name="bitflags-used-by-specific-commands"></a>Özel komutlar tarafından kullanılan bit bayrakları
Kaynak Denetimi Eklentisi API işlevleri bir dizi davranışını bir veya daha fazla BITS tek bir değer olarak ayarlayarak değiştirilebilir. Bu değerleri bit bayrakları bilinir. Kaynak Denetimi Eklentisi API tarafından kullanılan çeşitli bit bayrakları, bunları kullanan bir işlev tarafından gruplandırılmış burada açıklanmıştır.  
  
## <a name="checked-out-flag"></a>Bayrağı işaretli  
 Bu bayrak için ayarlanabilir [SccAdd](../extensibility/sccadd-function.md) veya [SccCheckin](../extensibility/scccheckin-function.md).  
  
|Bayrağı|Değer|Açıklama|  
|----------|-----------|-----------------|  
|`SCC_KEEP_CHECKEDOUT`|0x1000|Dosyayı kullanıma tutun.|  
  
## <a name="add-flags"></a>Bayrak Ekle  
 Bu bayraklar tarafından kullanılan [SccAdd](../extensibility/sccadd-function.md).  
  
|Bayrağı|Değer|Açıklama|  
|----------|-----------|-----------------|  
|`SCC_FILETYPE_AUTO`|0x00|Kaynak Denetimi Eklentisi otomatik olarak metin veya ikili dosyanın olup olmadığını algılamak için bekleniyor.|  
|`SCC_FILETYPE_TEXT`|0x01|Dosya türü metindir.|  
|`SCC_FILETYPE_BINARY`|0x04|İkili dosya türü. **Not:** `SCC_FILETYPE_TEXT` ve `SCC_FILETYPE_BINARY` bayrakları karşılıklı olarak birbirini dışlar.   Tam olarak bir ya da hiçbiri olarak ayarlayın.|  
|`SCC_ADD_STORELATEST`|0x02|Yalnızca en son sürümü (deltaları yok) Store.|  
  
## <a name="diff-flags"></a>Fark bayrakları  
 [SccDiff](../extensibility/sccdiff-function.md) Bu bayraklar fark oluşturma işlemiyle kapsamını tanımlamak için kullanır. `SCC_DIFF_QD_xxx` Bayrakları karşılıklı olarak birbirini dışlar. Herhangi biri belirtilirse, hiçbir görsel geri bildirim verilecek olan. "Hızlı fark" olarak (QD) eklentisi nasıl dosya yalnızca farklı olması durumunda farklı olduğunu belirlemez. Hiçbiri bu bayraklar "görsel fark" Bitti belirtilir; ayrıntılı dosya farklılıklarını hesaplanan ve görüntülenir. İstenen QD desteklenmiyorsa, eklenti için bir sonraki en iyi taşır. Örneği için bir sağlama toplamı IDE ister ve eklenti desteklemediği eklenti yoksa tam içeriği (yine de çok daha hızlı bir görüntü) kontrol edin.  
  
|Bayrağı|Değer|Açıklama|  
|----------|-----------|-----------------|  
|`SCC_DIFF_IGNORECASE`|0x0002|Büyük/küçük harf farklılıkları yoksayın.|  
|`SCC_DIFF_IGNORESPACE`|0x0004|Boşluk farklılıkları yoksayın. **Not:** `SCC_DIFF_IGNORECASE` ve `SCC_DIFF_IGNORESPACE` bayraklar isteğe bağlı bit bayrakları.|  
|`SCC_DIFF_QD_CONTENTS`|0x0010|Tüm dosya içeriğini karşılaştırarak QD.|  
|`SCC_DIFF_QD_CHECKSUM`|0x0020|QD tarafından sağlama toplamı.|  
|`SCC_DIFF_QD_TIME`|0x0040|QD dosya tarih/saat damgasının tarafından.|  
|`SCC_DIFF_QUICK_DIFF`|0x0070|Bu, tüm QD bit bayrakları kontrol etmek için kullanılan bir maskesidir. Bir işleve geçirilmemelidir; üç QD bit bayrakları karşılıklı olarak birbirini dışlar. QD her zaman kullanıcı arabiriminin bir görüntü yok anlamına gelir.|  
  
## <a name="populatelist-flag"></a>PopulateList bayrağı  
 Bu bayrağı tarafından kullanılan [SccPopulateList](../extensibility/sccpopulatelist-function.md) içinde `fOptions` parametresi.  
  
|Bayrağı|Değer|Açıklama|  
|----------|-----------|-----------------|  
|`SCC_PL_DIR`|0x00000001L|IDE, dizinleri, dosyaları değil geçiyor.|  
  
## <a name="populatedirlist-flags"></a>PopulateDirList bayrakları  
 Bu bayraklar tarafından kullanılan [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md) içinde `fOptions` parametresi.  
  
|Seçenek değeri|Değer|Açıklama|  
|------------------|-----------|-----------------|  
|SCC_PDL_ONELEVEL|0x0000|Tek düzey dizinleri (varsayılan değer budur) dizinler için inceleyin.|  
|SCC_PDL_RECURSIVE|0x0001|Yinelemeli olarak verilen her dizin altındaki tüm dizinleri inceleyin.|  
|SCC_PDL_INCLUDEFILES|0x0002|Dosya adları İnceleme işleminde içerir.|  
  
## <a name="openproject-flags"></a>OpenProject bayrakları  
 Bu bayraklar tarafından kullanılan [SccOpenProject](../extensibility/sccopenproject-function.md) içinde `dwFlags` parametresi.  
  
|Seçenek değeri|Değer|Açıklama|  
|------------------|-----------|-----------------|  
|SCC_OP_CREATEIFNEW|0x00000001L|Proje kaynak denetiminde yoksa, oluşturun. Bu bayrak ayarlanmazsa oluşturmak için proje kullanıcıdan (sürece `SCC_OP_SILENTOPEN` bayrağı belirtildi).|  
|SCC_OP_SILENTOPEN|0x00000002L|Bir proje oluşturmak için kullanıcıya sorma; sadece dönüş `SCC_E_UNKNOWNPROJECT`.|  
  
## <a name="get-flags"></a>Bayrakları Al  
 Bu bayraklar tarafından kullanılan [SccGet](../extensibility/sccget-function.md) ve [SccCheckout](../extensibility/scccheckout-function.md).  
  
|Bayrağı|Değer|Açıklama|  
|----------|-----------|-----------------|  
|`SCC_GET_ALL`|0x00000001L|IDE dizinleri geçirme, olmayan dosyalar: Bu dizinlerdeki tüm dosyaları alın.|  
|`SCC_GET_RECURSIVE`|0x00000002L|IDE dizinleri geçiyor: Bu dizinler ve bunların tüm alt dizinleri.|  
  
## <a name="noption-values"></a>nOption değerleri  
 Bu bayraklar tarafından kullanılan [SccSetOption](../extensibility/sccsetoption-function.md) içinde `nOption` parametresi.  
  
|Bayrağı|Değer|Açıklama|  
|----------|-----------|-----------------|  
|`SCC_OPT_EVENTQUEUE`|0x00000001L|Olay sırasındaki durumunu ayarlayın.|  
|`SCC_OPT_USERDATA`|0x00000002L|Kullanıcı verilerini belirtin `SCC_OPT_NAMECHANGEPFN`.|  
|`SCC_OPT_HASCANCELMODE`|0x00000003L|IDE iptal başa çıkabilir.|  
|`SCC_OPT_NAMECHANGEPFN`|0x00000004L|Ad değişiklikleri için bir geri çağırma ayarlayın.|  
|`SCC_OPT_SCCCHECKOUTONLY`|0x00000005L|Kaynak Denetimi Eklentisi kullanıcı Arabirimi kullanıma alma devre dışı bırakın ve çalışma dizinini ayarlamayın.|  
|`SCC_OPT_SHARESUBPROJ`|0x00000006L|Bir çalışma dizini belirtmek için kaynak denetim sisteminden ekleyin. Doğrudan alt öğesi ise ilişkili projeye paylaşmayı deneyin.|  
  
## <a name="dwval-bitflags"></a>dwVal bit bayrakları  
 Bu bayraklar tarafından kullanılan [SccSetOption](../extensibility/sccsetoption-function.md) içinde `dwVal` parametresi.  
  
|Bayrağı|Değer|Açıklama|Tarafından kullanılan `nOption` değeri|  
|----------|-----------|-----------------|-----------------------------|  
|`SCC_OPT_EQ_DISABLE`|0x00L|Olay sırası etkinlik askıya alır.|`SCC_OPT_EVENTQUEUE`|  
|`SCC_OPT_EQ_ENABLE`|0x01L|Olay sırası günlük kaydını etkinleştirir.|`SCC_OPT_EVENTQUEUE`|  
|`SCC_OPT_HCM_NO`|0 M|(Varsayılan) İptal modu yok; sahip. Eklenti isterseniz sağlamalısınız.|`SCC_OPT_HASCANCELMODE`|  
|`SCC_OPT_HCM_YES`|1 M|IDE iptal işler.|`SCC_OPT_HASCANCELMODE`|  
|`SCC_OPT_SCO_NO`|0 M|(Varsayılan) Eklenti kullanıcı Arabiriminden kullanıma için Tamam'ı tıklatın; Çalışma dizini ayarlanır.|`SCC_OPT_SCCCHECKOUTONLY`|  
|`SCC_OPT_SCO_YES`|1 M|Hiçbir eklenti kullanıcı Arabirimi kullanıma alma, çalışma dizini yok.|`SCC_OPT_SCCCHECKOUTONLY`|  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Kaynak denetimi eklentileri](../extensibility/source-control-plug-ins.md)