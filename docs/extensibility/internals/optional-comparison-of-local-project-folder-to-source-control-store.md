---
title: Kaynak Denetim deposunu proje klasörüne karşılaştırma | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, comparing versions
- source control plug-ins, local project folders
ms.assetid: 65217e8b-15a6-4446-92b0-4cff1c6220f5
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 2e0f6f2185385ee7ec3942556a43f58d43e7a4da
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31130581"
---
# <a name="optional-comparison-of-local-project-folder-to-source-control-store"></a>Kaynak Denetim deposunu yerel proje klasörüne isteğe bağlı karşılaştırması
Eklenti API yerel proje klasörünü ve kaynak denetimi karşılaştırması işlevlerini kullanarak gerçekleştirilir 1.2 kaynağında kontrol [SccDirQueryInfo](../../extensibility/sccdirqueryinfo-function.md) ve [SccDirDiff](../../extensibility/sccdirdiff-function.md).  
  
 İçinde **Çözüm Gezgini**, tek bir dosyayı yerine bir klasör seçilirse, **karşılaştırmak sürümleri** kısayol menüsünü çağırır yeni [SccDirQueryInfo](../../extensibility/sccdirqueryinfo-function.md) ve [ SccDirDiff](../../extensibility/sccdirdiff-function.md) eklenti kaynak denetiminde.  
  
## <a name="new-capability-flags"></a>Yeni yetenek bayrakları  
 `SCC_CAP_DIRECTORYDIFF`  
  
 `SCC_CAP_DIRECTORYCHECKOUT`  
  
## <a name="new-functions"></a>Yeni işlevleri  
 [SccDirDiff](../../extensibility/sccdirdiff-function.md)  
  
 [SccDirQueryInfo](../../extensibility/sccdirqueryinfo-function.md)  
  
 `SccDirQueryInfo` İşlevi çağrılmadan önce `SccDirDiff` çalışma dizini kaynak denetimli olup olmadığını belirlemek için. `SccDirDiff` İşlevi geçerli yerel dizin ve karşılık gelen kaynak denetimi klasör arasındaki farkları görüntüler. Bu komut eklentisinin dizine değişikliklerin listesini görüntülemek için kaynak denetimi sorar. Kaynak Denetim eklentisi farkları görüntülemek için kendi kullanıcı Arabirimi sağlar.  
  
> [!NOTE]
>  Bu işlev olarak aynı komutu bayrakları kullanır [SccDiff](../../extensibility/sccdiff-function.md). Kaynak denetimi eklenti sağlayıcısı, dizinler için "hızlı fark" işlemi desteklemeyen tercih edebilirsiniz.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Kaynak Denetimi Eklentisi API Sürümü 1.2’deki Yenilikler](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)