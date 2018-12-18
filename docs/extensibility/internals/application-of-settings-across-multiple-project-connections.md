---
title: Birden çok proje bağlantısında ayarların uygulanması | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, application of settings
ms.assetid: 2116d3d0-c46c-4d0a-b482-08a178584f46
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 6d8b8d7d6dc1e596686a2fad7b53363b2387a47b
ms.sourcegitcommit: 1c2ed640512ba613b3bbbc9ce348e28be6ca3e45
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/03/2018
ms.locfileid: "39500049"
---
# <a name="application-of-settings-across-multiple-project-connections"></a>Birden çok proje bağlantısında ayarların uygulanması
Kaynak Denetimi Eklentisi Kaynak Denetimi Eklentisi API sürümü 1.2 kullanılarak oluşturulan bir toplu işlem birden fazla proje veya birden çok bağlantı bağlamları arasında aynı kaynak denetimi işlemi yürütmek için kullanabilirsiniz. Toplu kullanılabilir yedekli ortadan kaldırmak için proje başına kullanıcı deneyiminden iletişim kutuları.  
  
 Bir kullanıcı birden fazla bağlantı kaynak denetimi eklentisi API sürüm 1.1 (örneğin, iki web projeleri farklı bir dosya paylaşımı makinelerde) kullanılarak oluşturulan bir kaynak denetimi eklentisi içinde ait birden çok öğe seçilir ve bunları denetler, kullanıcı aynı görür iletişim kutusunu tekrar tekrar. Kullanıcı olsa bile, bu senaryo ortaya **tümüne uygula** IDE her bağlantı bağlamı için durumuna sıfırlar çünkü iletişim kutusunda, kutuyu işaretleyin.  
  
## <a name="new-capability-flag"></a>Yeni özellik bayrağı  
 `SccBeginBatch` İşlev kümeleri `SCC_CAP_BATCH` toplu işlem sürmekte olduğunu belirten bayrak.  
  
## <a name="new-functions"></a>Yeni işlevleri  
Toplu işlem aşağıdaki yeni işlevleri destekler:  
  
-   [SccBeginBatch](../../extensibility/sccbeginbatch-function.md)  
  
-   [SccEndBatch](../../extensibility/sccendbatch-function.md)  

  
`SCCBeginBatch` İşlevi, bir grup kaynak denetimi işlemleri başlatır. `SccEndBatch` İşlev grubu kapatır. Grupları bulunmayabilir.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Kaynak Denetimi Eklentisi API sürümü 1.2 yenilikler nelerdir?](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)