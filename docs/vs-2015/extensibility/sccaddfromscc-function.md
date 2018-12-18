---
title: SccAddFromScc işlevi | Microsoft Docs
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
- SccAddFromScc
helpviewer_keywords:
- SccAddFromScc function
ms.assetid: 902e764d-200e-46e1-8c42-4da7b037f9a0
caps.latest.revision: 18
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b366c6c80dc52436743da0f69266105cc0ba5db8
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51771017"
---
# <a name="sccaddfromscc-function"></a>SccAddFromScc İşlevi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu işlev, göz atmak için kaynak denetim sistemi olan dosyaları verir ve daha sonra bu geçerli proje dosyaları parçası olun. Örneğin, bu işlev dosya kopyalama olmadan ortak bir üstbilgi dosyası geçerli projenin içine alabilirsiniz. Dosyaları iade dizisi `lplpFileNames`, IDE projeye eklemek için kullanıcının istediği dosyaların listesini içerir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp#  
SCCRTN SccAddFromScc (  
   LPVOID   pvContext,  
   HWND     hWnd,  
   LPLONG   lpnFiles,  
   LPCSTR** lplpFileNames  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 pvContext  
 [in] Kaynak Denetimi Eklentisi bağlam yapısı.  
  
 hWnd  
 [in] Kaynak Denetimi Eklentisi sağladığı herhangi bir iletişim kutusu için bir üst öğe olarak kullanabileceğiniz IDE penceresi için bir tanıtıcı.  
  
 lpnFiles  
 [out içinde] Bir arabellek olarak eklenen dosya sayısı. (Bu `NULL` bellek işaret ettiği varsa `lplpFileNames` serbest bırakılacağı. Açıklamalar Ayrıntılar için bkz.)  
  
 lplpFileNames  
 [out içinde] Dizin yolları olmadan tüm dosya adları için işaretçiler dizisi. Bu dizi ayrılan ve kaynak denetimi eklentisi tarafından serbest. Varsa `lpnFiles` = 1 ve `lplpFileNames` değil `NULL`, dizideki ilk adı tarafından işaret edilen `lplpFileNames` hedef klasör içeriyor.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Kaynak Denetimi Eklentisi uygulanması bu işlev, aşağıdaki değerlerden birini döndürmesi beklenir:  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|SCC_OK|Dosyalar başarıyla bulunan ve projeye eklendi.|  
|SCC_I_OPERATIONCANCELED|İşlem, herhangi bir etkisi ile iptal edildi.|  
|SCC_I_RELOADFILE|Bir dosya veya projenin yeniden yüklenmesi gerekiyor.|  
  
## <a name="remarks"></a>Açıklamalar  
 IDE, bu işlevi çağırır. Kaynak Denetimi Eklentisi, bir yerel hedef klasör belirterek destekliyorsa, IDE geçirir `lpnFiles` = 1 ve yerel klasör adını geçirir `lplpFileNames`.  
  
 Zaman çağrısı `SccAddFromScc` işlevi döndürür, eklenti atanan değerleri `lpnFiles` ve `lplpFileNames`, gerektiğinde dosya adı dizisi için bellek ayırma (Bu ayırma işaretçinin yerini Not `lplpFileNames`). Kaynak Denetimi Eklentisi, kullanıcının dizine veya belirtilen ataması klasördeki tüm dosyaları yerleştirmek için sorumludur. IDE, sonra IDE projeye dosyaları ekler.  
  
 Son olarak, IDE öğesinde geçen ikinci kez, bu işlevi çağıran `NULL` için `lpnFiles`. Bu kaynak denetimi dosya adı dizideki için ayrılan belleği serbest eklentisi tarafından özel bir sinyal yorumlanır `lplpFileNames``.`  
  
 `lplpFileNames` olan bir `char ***` işaretçi. Kaynak Denetimi Eklentisi, bir dosya adları, böylece liste bu API için standart bir biçimde geçirme için işaretçiler dizisi için bir işaretçi yerleştirir.  
  
> [!NOTE]
>  İlk VSSCI API sürümlerini hedef projeye eklenen dosyaları göstermek için bir yol sağlamadı. Bu semantiği uyum sağlayacak şekilde `lplpFIleNames` parametresi geliştirilmiş bir ın/out parametresi bir output parametresi yerine yapma. Yalnızca tek bir dosya belirtilir, diğer bir deyişle, değer tarafından işaret edilen `lpnFiles` 1 ve ardından ilk öğesi = `lplpFileNames` hedef klasör içerir. Bu yeni semantiği, IDE çağrıları kullanılacak `SccSetOption` işleviyle `nOption`parametresini `SCC_OPT_SHARESUBPROJ`. Kaynak Denetimi Eklentisi semantiği desteklemiyor varsa, döndürür `SCC_E_OPTNOTSUPPORTED`. Bunu devre dışı bırakır kullanımını yapılması **kaynak denetiminden Ekle** özelliği. Bir eklentiyi destekler, **kaynak denetiminden Ekle** özelliği (`SCC_CAP_ADDFROMSCC`), yeni semantiği desteği gerekir ve dönüş `SCC_I_SHARESUBPROJOK`.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Kaynak Denetimi Eklentisi API işlevleri](../extensibility/source-control-plug-in-api-functions.md)   
 [SccSetOption](../extensibility/sccsetoption-function.md)

