---
title: İleti sınıfı için. ofs dosyasında geçersiz özellikler "
description: . Ofs dosyasındaki bir veya daha fazla özellik seçilen ileti sınıfı için geçerli olmadığında oluşan bir hatayı düzeltme hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VSTO.NewFormRegionWizard.OFSPropertyError
dev_langs:
- VB
- CSharp
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: b22870cdb038adee84adc0fd7a56c269cb048626
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99841931"
---
# <a name="invalid-properties-in-the-ofs-file-for-the-message-class"></a>İleti sınıfı için. ofs dosyasında geçersiz özellikler

  ". Ofs dosyasındaki bir veya daha fazla özellik seçilen ileti sınıfı için geçerli değil" hatası, Outlook 'ta tasarlanan bir form bölgesini içeri aktardığınızda görüntülenir, ancak form bölgesindeki bir veya daha fazla alan **Yeni form bölgesi** sihirbazının son sayfasında seçtiğiniz ileti sınıflarıyla uyumlu değildir.

Örneğin, **görev (IPM) öğesini seçebilirsiniz. Görev)** **Yeni form bölgesi** sihirbazının son sayfasında. Form bölgesinin bir **Iş adresi** alanı varsa, bir görevin iş adresi olmadığı için bu hatayı alırsınız. Bu nedenle, **Iş adresi** alanı `IPM.Task` ileti sınıfıyla uyumlu değildir.

 **Görev (IPM) seçeneğini belirleyebilirsiniz. Görev)** **Yeni form bölgesi** sihirbazının son sayfasında. Form bölgesinin bir **Iş adresi** alanı varsa, bir görevin iş adresi olmadığı için bu hatayı alırsınız. Bu nedenle, **Iş adresi** alanı `IPM.Task` ileti sınıfıyla uyumlu değildir.

## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için

- **Yeni form bölgesi** Sihirbazı ' nın son sayfasında, form bölgesindeki alanlarla uyumlu bir ileti sınıfı seçin.

- Outlook 'taki form tasarımcısında, ileti sınıflarıyla uyumlu olmayan alanları kaldırın. **Yeni form bölgesi** sihirbazının son sayfasında seçimi planladığınız alanları kaldırın.

## <a name="see-also"></a>Ayrıca bkz.
- [İzlenecek yol: Outlook 'ta tasarlanan form bölgesini Içeri aktarma](../vsto/walkthrough-importing-a-form-region-that-is-designed-in-outlook.md)
