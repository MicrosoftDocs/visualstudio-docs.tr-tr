---
title: SccEnumChangedFiles işlevi | Microsoft Docs
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
- SccEnumChangedFiles
helpviewer_keywords:
- SccEnumChangedFiles function
ms.assetid: 76cac510-107b-4c1a-ba60-9c39b6db2e71
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: c4254df883bf268f7f473c89d99cdcadf991a8a1
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51736051"
---
# <a name="sccenumchangedfiles-function"></a>SccEnumChangedFiles İşlevi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu işlev yerel dosyaların listesini göz önünde bulundurulduğunda, hangi dosyaların kaynak kod denetimi veritabanında karşılık gelen sürümlerinden farklı olduğunu belirler.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
SCCRTN SccEnumChangedFiles(  
   LPVOID  pContext,  
   HWND    hWnd,  
   LONG    cFiles,  
   LPCSTR* lpFileNames,  
   LONG*   plIsFileDifferent  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 pContext  
 [in] Kaynak Denetimi Eklentisi bağlam işaretçisi.  
  
 hWnd  
 [in] Kaynak Denetimi Eklentisi sağladığı herhangi bir iletişim kutusu için bir üst öğe olarak kullanabileceğiniz IDE penceresi için bir tanıtıcı.  
  
 cFiles  
 [in] Belirtilen dosya adları sayısını `lpFileNames` dizisi. Ayrıca boyutunu belirtir `plIsFileDifferent` dizisi.  
  
 lpFileNames  
 [in] Denetlenecek yerel dosya adları dizisi.  
  
 plIsFileDifferent  
 [out içinde] Her dosya farkı durumunu belirten değerleri dizisi (dizisi en az olmalıdır `cFiles` girişleri). NonZero dosyanın farklı olduğu anlamına gelir.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Kaynak Denetimi Eklentisi uygulanması bu işlev, aşağıdaki değerlerden birini döndürmesi beklenir:  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|SCC_OK|İşlem başarıyla tamamlandı.|  
|SCC_UNSPECIFIEDERROR|Genel hata.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Kaynak Denetimi Eklentisi API İşlevleri](../extensibility/source-control-plug-in-api-functions.md)

