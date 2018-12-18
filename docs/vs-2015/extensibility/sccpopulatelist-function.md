---
title: SccPopulateList işlevi | Microsoft Docs
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
- SccPopulateList
helpviewer_keywords:
- SccPopulateList function
ms.assetid: 7416e781-c571-4a7f-8af3-a089ce8be662
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: fccf5ba354a99eaef6968c5d5027e8540762af75
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51798904"
---
# <a name="sccpopulatelist-function"></a>SccPopulateList İşlevi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu işlev, belirli bir kaynak denetim komut için dosyaları listesini güncelleştirir ve tüm belirli dosyalar kaynak denetimi durumunu sağlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp#  
SCCRTN SccPopulateList (  
   LPVOID          pvContext,  
   enum SCCCOMMAND nCommand,  
   LONG            nFiles,  
   LPCSTR*         lpFileNames,  
   POPLISTFUNC     pfnPopulate,  
   LPVOID          pvCallerData,  
   LPLONG          lpStatus,  
   LONG            fOptions  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 pvContext  
 [in] Kaynak Denetimi Eklentisi bağlam yapısı.  
  
 nyürütülen komut  
 [in] Tüm dosyalara uygulanacak Kaynak Denetimi'ne `lpFileNames` dizi (bkz [komut kodu](../extensibility/command-code-enumerator.md) olası komutların listesini görmek için).  
  
 nFiles  
 [in] Dosya sayısı `lpFileNames` dizisi.  
  
 lpFileNames  
 [in] IDE'ye bilinen dosya adları dizisi.  
  
 pfnPopulate  
 [in] Ekleme ve kaldırma dosyaları aramak için IDE geri çağırma işlevi (bkz [POPLISTFUNC](../extensibility/poplistfunc.md) Ayrıntılar için).  
  
 pvCallerData  
 [in] Geri çağırma işlevine geçirilecek değer değişmedi.  
  
 lpStatus  
 [out içinde] Kaynak denetimi durumu bayrakları her dosya için döndürülecek eklentisi için bir dizi.  
  
 fOptions  
 [in] Komut bayrakları ("PopulateList bayrağı" bölümüne bakın [kullanılan bit bayrakları tarafından belirli komutları](../extensibility/bitflags-used-by-specific-commands.md) Ayrıntılar için).  
  
## <a name="return-value"></a>Dönüş Değeri  
 Kaynak Denetimi Eklentisi uygulanması bu işlev, aşağıdaki değerlerden birini döndürmesi beklenir:  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|SCC_OK|Başarılı.|  
|SCC_E_NONSPECIFICERROR|Belirli olmayan hata oluştu.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu işlev, geçerli durumu için dosyaların listesini inceler. Kullandığı `pfnPopulate` bir dosya için ölçüt eşleşmediğinde çağrıyı yapana bunu bildirmesi için geri çağırma işlevi `nCommand`. Örneğin, komut ise `SCC_COMMAND_CHECKIN` ve listedeki bir dosyayı kullanıma alınmamış sonra geri çağıran bildirmek için kullanılır. Bazen, kaynak denetimi eklentisi komutunun bir parçası olması ve eklemediğiniz diğer dosyaları bulabilirsiniz. Bu, örneğin, bir Visual Basic kullanıcının kendi projesi tarafından kullanılır, ancak Visual Basic proje dosyasında görünmez .bmp dosyayı kullanıma izin verir. Kullanıcının **alma** IDE'de komutu. IDE kullanıcı alabilirsiniz gördüğü tüm dosyaların listesini görüntüler, ancak liste gösterilmeden önce `SccPopulateList` işlevi listenin görüntülenecek güncel olduğundan emin olmak için çağrılır.  
  
## <a name="example"></a>Örnek  
 IDE kullanıcı alabilirsiniz gördüğü dosyaların bir listesini oluşturur. Bu liste görüntülemeden önce çağrı `SccPopulateList` işlev, kaynak denetimi eklentisi için fırsatı veren ekleyin ve dosyaları listeden silin. Eklenti Listesi belirli bir geri çağırma işlevini çağırarak değiştirir (bkz [POPLISTFUNC](../extensibility/poplistfunc.md) daha fazla ayrıntı için).  
  
 Çağırmak eklenti devam `pfnPopulate` ekler ve tamamlandı ve ardından döndürür kadar dosyaları, siler, işlev `SccPopulateList` işlevi. IDE, daha sonra kendi listesini görüntüleyebilirsiniz. `lpStatus` Dizi IDE tarafından geçirilen orijinal listesindeki tüm dosyaları temsil eder. Tüm bu dosya ayrıca için yapma durumunu eklenti doldurur, geri çağırma işlevini kullanın.  
  
> [!NOTE]
>  Kaynak Denetimi Eklentisi, yalnızca hemen listesi olduğu gibi bırakarak bu işlevden döndürülecek seçeneği her zaman vardır. Bir eklenti bu işlevi uyguluyorsa, bu ayarlayarak gösterebilir `SCC_CAP_POPULATELIST` özelliği bit bayrak yapılan ilk çağrıda [Sccınitialize](../extensibility/sccinitialize-function.md). Varsayılan olarak, eklentinin her zaman geçirilen tüm öğeleri dosyalarıdır varsaymanız gerekir. Ancak, IDE ayarlarsa `SCC_PL_DIR` bayrağını `fOptions` parametresi, geçirilen tüm öğeleri olan dizin olarak kabul edilmesi için. Eklenti ait tüm dosyaların dizinlerinde eklemelisiniz. IDE karışımını dosyalar ve dizinler hiçbir zaman geçer.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Kaynak Denetimi Eklentisi API işlevleri](../extensibility/source-control-plug-in-api-functions.md)   
 [Sccınitialize](../extensibility/sccinitialize-function.md)   
 [POPLISTFUNC](../extensibility/poplistfunc.md)   
 [Özel komutlar tarafından kullanılan bit bayrakları](../extensibility/bitflags-used-by-specific-commands.md)   
 [Komut Kodu](../extensibility/command-code-enumerator.md)

