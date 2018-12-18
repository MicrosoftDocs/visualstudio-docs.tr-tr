---
title: Kaynak denetimi bilgilerinin kaldırılması. Proj ve. Sln dosyaları | Microsoft Docs
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
- source control plug-ins, .sln and .proj files
ms.assetid: 7b06883f-35de-41e2-9a9e-d3edba236f17
caps.latest.revision: 15
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 850f2278480b27eb302fe9cc87c608c0cd522e38
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51761533"
---
# <a name="removal-of-source-control-information-from-proj-and-sln-files"></a>.Proj ve .Sln Dosyalarından Kaynak Denetimi Bilgilerinin Kaldırılması
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Kaynak Denetimi Eklentisi API SCC 1.2 sürümüne bilgiler bir MSSCCPRJ içinde depolanır. SCC dosyası. MSSCCPRJ yararlanın. SCC SCC bilgilerin olduğu değil kaynak - denetimli .proj ve .sln dosyalarında olduğu gibi dosyasıdır.  
  
## <a name="version-12-changes"></a>Sürüm 1.2  
 Kaynak denetimi kaynak denetimi eklentisi API sürüm 1.1 üzerinde alan eklentileri, kaynak denetimi ile ilgili bilgi (.proj) proje ve çözüm (.sln) dosyalarında depolanır. Kaynak denetimi bilgilerinin veritabanı konumu AuxPath tarafından belirlenir ve veritabanı içinde belirli bir konuma ProjName tarafından belirtilir. ProjName genellikle tüm bu işlemleri sonra geçersiz olacağından bu davranışı dal, çatal veya kopyalama işlemleri sonrasında sorunlara neden olabilir.  
  
 Kaynak Denetimi Eklentisi API kullanılan sürüm 1.1, IDE içinde ~ SAK dosyalarının bir eklenti MSSCCPRJ destekleyip desteklemediğini belirlemek için. Kaynak denetimi bilgilerinin depolanması SCC yöntemi. Kaynak Denetimi Eklentisi API sürümü 1.2 MSSCCPRJ desteği saptamak için yeni bir özellik sağlar. SCC dosyası kullanmadan bir ~ SAK dosya. Daha fazla bilgi için [Saydamlığından ~ SAK dosyalarının](../../extensibility/internals/elimination-of-tilde-sak-files.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Kaynak Denetimi Eklentisi API Sürümü 1.2’deki Yenilikler](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)

