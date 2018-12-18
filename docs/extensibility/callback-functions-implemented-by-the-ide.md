---
title: IDE tarafından uygulanan geri çağırma işlevleri | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, callback functions
- callback functions, source control plug-ins
ms.assetid: 4a8833f0-6ac0-4ea7-9400-8275aa991468
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: c76a9ef3ab81cf764d5f82fdfb9c8d6a86f24bee
ms.sourcegitcommit: 25a62c2db771f938e3baa658df8b1ae54a960e4f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/24/2018
ms.locfileid: "39232487"
---
# <a name="callback-functions-implemented-by-the-ide"></a>IDE tarafından uygulanan geri çağırma işlevleri
Bir birleşik son kullanıcı deneyimi sağlar ve mümkün olduğunca sorunsuz olarak tümleşik geliştirme ortamı (IDE) ile tümleştirme yapmak için kaynak denetimi eklentisi IDE tarafından uygulanan geri çağırma işlevleri kullanabilirsiniz. Eklenti bu işlevler IDE bilgi geçirmek için bir kaynak denetimi işlemi sırasında uygun zamanlarda çağırabilirsiniz; IDE, katıştırılmış öğeler kendi yerel kullanıcı Arabirimi olarak bu bilgiler daha sonra görüntüleyebilirsiniz. Kullanıcı, bu senaryoda, eklenti kendi UI işe, daha az parçalanmış bir deneyimi vardır.  
  
 Gerekli bir üstbilgi dosyasıdır *scc.h*. Varsayılan konum *\Program Files\VSIP 8.0\EnvSDK\common\inc\\*. Ayrıca kaynak denetimi eklentisi örneğine sahip VSIP klasörde olduğu *\Program Files\VSIP 8.0\MSSCCI\\*.  
  
## <a name="in-this-section"></a>Bu bölümde  
 [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)  
 Tarafından kullanılan geri çağırma işlevi açıklar [SccOpenProject](../extensibility/sccopenproject-function.md) kaynak denetimi eklentisi IDE üzerinden alınan iletileri görüntülemek için.  
  
 [POPLISTFUNC](../extensibility/poplistfunc.md)  
 Tarafından kullanılan geri çağırma işlevi açıklar [SccPopulateList](../extensibility/sccpopulatelist-function.md) zaman IDE tam erişimi yok yalnızca kaynak denetimi eklentisi sürüm denetimi altında dosyaların tam bir listesini gibi kullanılabilir olan bilgiler.  
  
 [QUERYCHANGESFUNC](../extensibility/querychangesfunc.md)  
 Tarafından kullanılan geri çağırma işlevi açıklar [SccQueryChanges](../extensibility/sccquerychanges-function.md) işlemi.  
  
 [POPDIRLISTFUNC](../extensibility/popdirlistfunc.md)  
 Tarafından kullanılan geri çağırma işlevi açıklar [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md) işlemi.  
  
 [OPTNAMECHANGEPFN](../extensibility/optnamechangepfn.md)  
 Geri çağırma işlevine bir çağrı tarafından ayarlanan açıklar [SccSetOption](../extensibility/sccsetoption-function.md) kaynak denetimi Eklentisi adı değişiklikleri geri IDE'ye iletişim kurmasına olanak tanır.  
  
## <a name="related-sections"></a>İlgili bölümler  
 [SccOpenProject](../extensibility/sccopenproject-function.md)  
 Bir proje açılır.  
  
 [SccPopulateList](../extensibility/sccpopulatelist-function.md)  
 Bunların geçerli durum için dosyaların listesini inceler. Ayrıca, kullandığı `pfnPopulate` işlevi bir dosya için ölçüt eşleşmediğinde çağrıyı yapana bunu bildirmesi `nCommand`.  
  
 [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md)  
 Dizinleri ve dosyaları bir proje veya kaynak denetimi altında olan projeler listesini inceler. Bulunan her dizin ve dosya adı, bir geri çağırma işlevine geçirilir.  
  
 [SccQueryChanges](../extensibility/sccquerychanges-function.md)  
 Dosyaların listesini yapılan ad değişiklikleri inceler. Her dosya adının, değişiklik durumuyla birlikte bir geri çağırma işlevine geçirilir.  
  
 [SccSetOption](../extensibility/sccsetoption-function.md)  
 Çok çeşitli seçenekler ayarlar. Her seçeneği ile başlayan `SCC_OPT_xxx` ve kendi tanımlanan değerleri kümesi vardır.  
  
 [Kaynak Denetimi Eklentileri](../extensibility/source-control-plug-ins.md)  
 Kaynak Denetimi Eklentisi SDK başvuru bölümü içeriğini açıklar.