---
title: 'F # için Düzenle ve devam et desteklenmiyor | Microsoft Docs'
description: 'F # hata ayıklaması için Düzenle ve devam et desteklenmez. Hata ayıklama sırasında koda yapılan düzenlemeler kaynağa uygulanmaz, bu nedenle, hataları Ayıklanacak kod kaynakla eşleşmez.'
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Edit and Continue [F#]
- Debugging [F#], Edit and Continue
ms.assetid: 40ec77bb-07e3-4b58-9254-ae015009441c
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: a686cf91a515d2b7b59d87d7b3ca8e92d4e54c59
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99871994"
---
# <a name="edit-and-continue-not-supported-for-f"></a>Düzenle ve Devam Et F#'de Desteklenmez #
F # kodunda hata ayıklarken Düzenle ve devam et desteklenmez. F # kodundaki düzenlemeler hata ayıklama oturumu sırasında mümkündür ancak kaçınılması gerekir. Kod değişiklikleri hata ayıklama oturumu sırasında uygulanmaz. Bu nedenle, hata ayıklama sırasında F # kodunda yapılan tüm düzenlemeler, hata ayıklamakta olan kodla eşleşmeyen kaynak koda neden olur.
