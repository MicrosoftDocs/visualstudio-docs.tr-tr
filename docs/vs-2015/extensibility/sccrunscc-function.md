---
title: SccRunScc işlevi | Microsoft Docs
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
- SccRunScc
helpviewer_keywords:
- SccRunScc function
ms.assetid: bbe7c931-b17a-4779-9cf6-59e5f9f0c172
caps.latest.revision: 15
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 67d2ad2ee783d23e3bd8c960ad5a94eac3fbd908
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51733686"
---
# <a name="sccrunscc-function"></a>SccRunScc İşlevi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu işlev, kaynak denetimi Yönetim Aracı'nı başlatır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp#  
SCCRTN SccRunScc(  
   LPVOID  pvContext,  
   HWND    hWnd,  
   LONG    nFiles,  
   LPCSTR* lpFileNames  
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
 [in] Seçili dosya adları dizisi.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Kaynak Denetimi Eklentisi uygulanması bu işlev, aşağıdaki değerlerden birini döndürmesi beklenir:  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|SCC_OK|Kaynak denetimi Yönetim Aracı'nı başarıyla çağrıldı.|  
|SCC_I_OPERATIONCANCELED|İşlem iptal edildi.|  
|SCC_E_INITIALIZEFAILED|Kaynak denetim sistemi başlatılamadı.|  
|SCC_E_ACCESSFAILURE|Kaynak denetim sistemi, ağ veya çakışma sorunları nedeniyle muhtemelen erişilirken sorun oluştu.|  
|SCC_E_CONNECTIONFAILURE|Kaynak Denetim sistemine bağlanmak başarısız oldu.|  
|SCC_E_FILENOTCONTROLLED|Seçili dosya kaynak denetimi altında değil.|  
|SCC_E_NONSPECIFICERROR|Belirli olmayan hata oluştu.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu işlevi çağıran bir dış yönetim aracı ile çeşitli kaynak denetim sistemi özelliklerine erişmek izin verir. Kaynak denetim sistemi herhangi bir kullanıcı arabirimi varsa, kaynak denetimi eklentisi gerekli yönetim işlevleri gerçekleştirmek için bir arabirim uygulayabilir.  
  
 Bu işlev, bir sayı ve şu anda seçili dosya için dosya adları dizisi ile çağrılır. Yönetim Aracı'nı destekliyorsa, dosyaların listesini SCP'si yönetim arabirimi dosyaları için kullanılabilir; Aksi takdirde, listeye göz ardı edilebilir.  
  
 Bu işlevin genellikle kullanıcı seçtiğinde çağrılır **başlatma \<kaynak denetim sunucusuna >** gelen **dosya** -> **kaynak denetimi** menüsü. Bu **başlatma** menü seçeneği her zaman devre dışı veya hatta bir kayıt defteri girişi ayarlayarak gizli. Bkz: [nasıl yapılır: kaynak denetimi eklentisi yükleme](../extensibility/internals/how-to-install-a-source-control-plug-in.md) Ayrıntılar için. Bu işlev, yalnızca aşağıdaki durumlarda çağrılır [Sccınitialize](../extensibility/sccinitialize-function.md) döndürür `SCC_CAP_RUNSCC` yeteneği biti (bkz [özellik bayrakları](../extensibility/capability-flags.md) bu ve diğer özellik BITS hakkında ayrıntılı bilgi için).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Kaynak Denetimi Eklentisi API işlevleri](../extensibility/source-control-plug-in-api-functions.md)   
 [Nasıl yapılır: kaynak denetimi eklentisi yükleme](../extensibility/internals/how-to-install-a-source-control-plug-in.md)   
 [Özellik bayrakları](../extensibility/capability-flags.md)   
 [SccInitialize](../extensibility/sccinitialize-function.md)

