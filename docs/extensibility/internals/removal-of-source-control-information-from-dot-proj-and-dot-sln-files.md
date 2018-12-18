---
title: Kaynak Denetim bilgileri kaldırma. Proj ve. Sln dosyaları | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, .sln and .proj files
ms.assetid: 7b06883f-35de-41e2-9a9e-d3edba236f17
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 695a4ccfc5da20bda25c78929488625c244959a8
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31128993"
---
# <a name="removal-of-source-control-information-from-proj-and-sln-files"></a>Kaynak Denetim bilgileri kaldırma. Proj ve. Sln dosyaları
Sürüm kaynak denetim eklentisi API SCC 1.2 bilgiler MSSCCPRJ içinde depolanır. SCC dosyası. MSSCCPRJ yararlanabilir. SCC SCC bilgilerin olduğu değil kaynak - .proj ve .sln dosyalarında olduğu gibi denetlenen bir dosyadır.  
  
## <a name="version-12-changes"></a>Sürüm 1.2 değişiklikleri  
 Kaynak denetimi kaynak denetim eklentisi API'ye sürüm 1.1 bağlı eklentiler içinde kaynak denetimi hakkındaki bilgiler (.proj) proje ve çözüm (.sln) dosyalarında depolanır. Kaynak Denetim bilgileri veritabanı konumunu AuxPath tarafından belirtilir ve veritabanı içinde belirli konum ProjName tarafından belirtilir. ProjName genellikle bu işlemlerin hiçbirini sonra geçersiz olacağından bu davranış dal, çatalı veya kopyalama işlemleri sonra sorunlara neden olabilir.  
  
 Kaynak Denetim eklentisi API kullanılan sürüm 1.1, IDE içinde ~ bir eklenti MSSCCPRJ destekleyip desteklemediğini belirlemek için SAK dosyaları. Kaynak Denetim bilgilerini depolamak SCC yöntemi. Kaynak Denetim eklentisi API sürüm 1.2 MSSCCPRJ desteği saptamak için yeni bir özellik sağlar. SCC dosya kullanmadan bir ~ SAK dosya. Daha fazla bilgi için bkz: [ortadan kaldırılması ~ SAK dosyaları](../../extensibility/internals/elimination-of-tilde-sak-files.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Kaynak Denetimi Eklentisi API Sürümü 1.2’deki Yenilikler](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)