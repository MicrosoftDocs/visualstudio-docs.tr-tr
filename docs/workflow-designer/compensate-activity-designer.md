---
title: İş Akışı Tasarımcısı-telafi etkinlik Tasarımcısı
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Compensate.UI
ms.assetid: 7347c947-bfff-4bad-becd-5cd23e7b24cd
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5332b6d9ec087f4e1b127d93563dc0f2fe5fdd15
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "86876157"
---
# <a name="compensate-activity-designer"></a>Compensate Etkinlik Tasarımcısı

**Telafi** etkinliği Tasarımcısı, etkinlik oluşturmak ve yapılandırmak için kullanılır <xref:System.Activities.Statements.Compensate> .

## <a name="the-compensate-activity"></a>Telafi etkinliği

<xref:System.Activities.Statements.Compensate>Etkinlik, <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A> içinde bulunan bir etkinlik için açıkça öğesini çağırır <xref:System.Activities.Statements.CompensableActivity> . Etkinlik, <xref:System.Activities.Statements.Compensate> veya bir içinde kullanılmıyorsa, <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A> <xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A> <xref:System.Activities.Statements.CompensableActivity> özelliğini belirtmeniz gerekir <xref:System.Activities.Statements.Compensate.Target%2A> .

<xref:System.Activities.Statements.CompensationToken>Tarafından belirtilen, <xref:System.Activities.Statements.Compensate.Target%2A> başarıyla tamamlandıktan sonra açıkça onaylamak veya telafi etmek için bir yol sağlar <xref:System.Activities.Statements.CompensableActivity> <xref:System.Activities.Statements.CompensableActivity.Body%2A> <xref:System.Activities.Statements.CompensableActivity> .

### <a name="using-the-compensate-activity-designer"></a>Telafi etkinliği tasarımcısını kullanma

**Telafi** etkinliği Tasarımcısı **araç kutusunun** **işlem** kategorisinde bulunabilir. **Araç kutusunu**açmak için iş akışı Tasarımcısı sol tarafında bulunan **araç kutusu** sekmesini seçin. Alternatif olarak, **Görünüm** menüsünden **araç kutusu** ' nu seçin veya **CTRL** + **alt** + **X**tuşlarına basın.

**Telafi** etkinliği Tasarımcısı **araç kutusundan** sürüklenip, içindeki gibi etkinliklerin yerleştirildiği iş akışı Tasarımcısı yüzeyine bırakılabilir <xref:System.Activities.Statements.Sequence> . Etkinlik Tasarımcısı ' nın atılması, <xref:System.Activities.Statements.Compensate> varsayılan telafi olan bir etkinlik oluşturur <xref:System.Activities.Activity.DisplayName%2A> . <xref:System.Activities.Activity.DisplayName%2A>Değer, **telafi** etkinlik tasarımcısının üst bilgisinde veya özellik kılavuzunun **DisplayName** kutusunda düzenlenebilir.

### <a name="the-compensate-properties"></a>Telafi özellikleri

Aşağıdaki tabloda <xref:System.Activities.Statements.CancellationScope> Özellikler gösterilmektedir ve bunların tasarımcıda nasıl kullanıldığı açıklanmaktadır. <xref:System.Activities.Activity.DisplayName%2A>Özellik, özellik kılavuzunda veya iş akışı Tasarımcısı yüzeyinde düzenlenebilir. Özellik <xref:System.Activities.Statements.Compensate.Target%2A> kılavuzunda özelliğini düzenleyin.

|Özellik Adı|Gerekli|Kullanım|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Yanlış|Etkinliğin isteğe bağlı kolay adını belirtir <xref:System.Activities.Statements.Compensate> . Varsayılan olarak telafi 'dir.|
|<xref:System.Activities.Statements.Compensate.Target%2A>|Doğru|<xref:System.Activities.InArgument%601> <xref:System.Activities.Statements.CompensationToken> Bu etkinlik için öğesini içeren öğesini belirtir <xref:System.Activities.Statements.Compensate> .|

## <a name="see-also"></a>Ayrıca bkz.

- [İşlem](../workflow-designer/transaction-activity-designers.md)
- [CompensableActivity](../workflow-designer/compensableactivity-activity-designer.md)
- [Compensate Etkinlik Tasarımcısı](../workflow-designer/compensate-activity-designer.md)
- [Confirm](../workflow-designer/confirm-activity-designer.md)
- [TransactionScope](../workflow-designer/transactionscope-activity-designer.md)