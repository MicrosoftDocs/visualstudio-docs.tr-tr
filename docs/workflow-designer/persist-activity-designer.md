---
title: İş Akışı Tasarımcısı-kalıcı etkinlik Tasarımcısı
description: Kalıcı etkinlik ve kalıcı etkinlik tasarımcısının kalıcı etkinlik oluşturmak ve yapılandırmak için nasıl kullanılacağı hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Persist.UI
ms.assetid: be8648dd-3eb9-4a50-8ec1-57a8be804692
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 988c080b7b6c89baa4151858fcaf4e3320582e09
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99968729"
---
# <a name="persist-activity-designer"></a>Persist Etkinlik Tasarımcısı

**Kalıcı** etkinlik Tasarımcısı, etkinlik oluşturmak ve yapılandırmak için kullanılır <xref:System.Activities.Statements.Persist> .

## <a name="the-persist-activity"></a>Kalıcı etkinlik

<xref:System.Activities.Statements.Persist>Etkinlik, mümkünse bir iş akışını diske kaydeder. <xref:System.Activities.Statements.Persist>Etkinlik, örneğin bir etkinlik içinde, kalıcılık olmayan bir bölgede yürütülemez <xref:System.Activities.Statements.TransactionScope> . <xref:System.Activities.Statements.Persist>Kalıcı olmayan bir kapsamda etkinlik kullanıyorsanız, çalışma zamanında bir özel durum oluşturulur.

### <a name="using-the-persist-activity-designer"></a>Kalıcı etkinlik tasarımcısını kullanma

**Kalıcı** etkinlik **Tasarımcısı araç kutusu sekmesine** tıklanarak erişilen (alternatif olarak, **Görünüm** menüsünden **araç kutusu** ' nu veya Ctrl + Alt + X ' i seçerek **),** **çalışma alanının çalışma zamanı** kategorisinde bulunabilir.

**Kalıcı** etkinlik Tasarımcısı **araç kutusundan** sürüklenip, örneğin içinde olduğu gibi etkinliklerin genellikle yerleştirildiği iş akışı Tasarımcısı yüzeyine bırakılabilir <xref:System.Activities.Statements.Sequence> . Bu <xref:System.Activities.Statements.Persist> , varsayılan olarak **görünmeyen** bir etkinlik oluşturur. , <xref:System.Activities.Activity.DisplayName%2A> **Kalıcı** etkinlik tasarımcısının üst bilgisinde veya özellik kılavuzunun **DisplayName** kutusunda düzenlenebilir.

### <a name="the-persist-properties"></a>Devam eden özellikler

Aşağıdaki tabloda <xref:System.Activities.Statements.Persist> Özellikler gösterilmektedir ve bunların tasarımcıda nasıl kullanıldığı açıklanmaktadır. Bu özellikler özellik kılavuzunda düzenlenebilir ve bazıları İş Akışı Tasarımcısı yüzeyinde düzenlenebilirler.

|Özellik Adı|Gerekli|Kullanım|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Yanlış|Etkinliğin kolay adı <xref:System.Activities.Statements.Persist> . Varsayılan değer korunur. Görünen ad kesinlikle gerekli olmasa da, bir görünen ad kullanmak en iyi uygulamadır.|

## <a name="see-also"></a>Ayrıca bkz.

- [Çalışma Zamanı](../workflow-designer/runtime-activity-designers.md)
- [TerminateWorkflow](../workflow-designer/terminateworkflow-activity-designer.md)
