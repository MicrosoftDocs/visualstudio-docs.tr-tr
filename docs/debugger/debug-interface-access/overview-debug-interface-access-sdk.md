---
title: Genel Bakış (hata ayıklama arabirimi erişim SDK 'Sı) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- user-defined types
- .dbg files
- modules
- interfaces [DIA SDK]
- DBG files
- procedures [DIA SDK]
- executable files
- COM objects, in DIA SDK
- compilands
- executable images
ms.assetid: 720b4479-a8bc-4fec-860e-80c1a0780405
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7a403a8d3ddec82ce7e051e545687511c2421fa9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85461170"
---
# <a name="overview-debug-interface-access-sdk"></a>Genel Bakış (Arabirim Erişimi SDK'sında Hata Ayıklama)
Microsoft hata ayıklama bilgilerine erişmek için DIA SDK kullanın. DIA SDK, Microsoft hata ayıklama bilgilerinin biçimini her değiştirdiğinde kodunuzu yeniden yazma gereksinimini ortadan kaldıran COM tabanlı bir API kümesi sağlar. DIA SDK Ayrıca, [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] 5,0 ve üzeri sürümler tarafından oluşturulan. pdb ve. dbg dosyalarında bulunan önceki hata ayıklama bilgileri grubundan bir seçim kümesinden okumanızı sağlar.

 DIA SDK her arabirim, aksi belirtilmedikçe farklı bir COM nesnesini temsil eder. Ek arabirimler ve bu nedenle ek nesneler, var olan arabirim işaretçilerine çağrı yapmak yerine [IDiaDataSource:: openSession](../../debugger/debug-interface-access/idiadatasource-opensession.md) veya [IDiaSession:: findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)gibi açık sorgular aracılığıyla oluşturulur `QueryInterface` .

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaDataSource::openSession](../../debugger/debug-interface-access/idiadatasource-opensession.md)
- [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)