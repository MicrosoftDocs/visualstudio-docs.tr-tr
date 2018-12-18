---
title: Birden çok proje bağlantısında ayarların uygulanması | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- source control plug-ins, application of settings
ms.assetid: 2116d3d0-c46c-4d0a-b482-08a178584f46
caps.latest.revision: 16
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 16b7a139a3f1061516f779cb9b384bfb69eda7d3
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51740946"
---
# <a name="application-of-settings-across-multiple-project-connections"></a>Birden Çok Proje Bağlantısında Ayarların Uygulanması
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Kaynak Denetimi Eklentisi Kaynak Denetimi Eklentisi API 1.2 kullanılarak oluşturulan bir toplu işlem birden fazla proje veya birden çok bağlantı bağlamları arasında aynı kaynak denetimi işlemi yürütmek için kullanabilirsiniz. Toplu kullanılabilir yedekli ortadan kaldırmak için proje başına kullanıcı deneyiminden iletişim kutuları.  
  
 Bir kullanıcı birden fazla bağlantı kaynak denetimi eklentisi API 1.1 (örneğin, iki Web projeleri farklı bir dosya paylaşımı makinelerde) kullanılarak oluşturulan bir kaynak denetimi eklentisi içinde ait birden çok öğe seçilir ve bunları denetler, kullanıcı aynı iletişim kutusu görür. sürekli olarak. Kullanıcı tıkladığında bile böyle **tümüne uygula** IDE her bağlantı bağlamı için durumuna sıfırlar çünkü iletişim kutusunda, kutuyu işaretleyin.  
  
## <a name="new-capability-flag"></a>Yeni özellik bayrağı  
 `SccBeginBatch` İşlev kümeleri `SCC_CAP_BATCH` toplu işlem sürmekte olduğunu belirten bayrak  
  
## <a name="new-functions"></a>Yeni işlevleri  
 Toplu işlem aşağıdaki yeni işlevleri destekler:  
  
- [SccBeginBatch](../../extensibility/sccbeginbatch-function.md)  
  
- [SccEndBatch](../../extensibility/sccendbatch-function.md)  
  
  `SCCBeginBatch` İşlevi, bir grup kaynak denetimi işlemleri başlatır. `SccEndBatch` Grup kapatır. Grupları bulunmayabilir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Kaynak Denetimi Eklentisi API Sürümü 1.2’deki Yenilikler](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)

