---
title: İş Akışı Tasarımcısı - CompensableActivity etkinlik Tasarımcısı
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- System.Activities.Statements.CompensableActivity.UI
ms.assetid: e0340d89-d39e-4a52-8557-13e27040d7b5
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 7257e7cc31e0503c7e466bbf4f8c9dd02e5fe15a
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49836143"
---
# <a name="compensableactivity-activity-designer"></a>CompensableActivity Etkinlik Tasarımcısı

**CompensableActivity** etkinlik Tasarımcısı oluşturmak ve yapılandırmak için kullanılan bir <xref:System.Activities.Statements.CompensableActivity> etkinlik.

## <a name="the-compensableactivity-activity"></a>CompensableActivity etkinlik
 <xref:System.Activities.Statements.CompensableActivity> Onaylanabilir veya işlemin başarıyla tamamlanmasından sonra dengelenebilecek iş birimi tanımlar.

### <a name="using-the-compensableactivity-activity-designer"></a>CompensableActivity etkinlik Tasarımcısı kullanma
 **CompensableActivity** etkinlik Tasarımcısı bulunabilir **işlem** kategorisi **araç kutusu**. Açmak için **araç kutusu**seçin **araç kutusu** iş akışı Tasarımcısı'nın sol tarafındaki sekmesi. Alternatif olarak, seçin **araç kutusu** gelen **görünümü** tuşuna basın veya menü **Ctrl**+**Alt** + **X**.

 **CompensableActivity** etkinlik Tasarımcısı, gelen sürüklenebilir **araç kutusu** ve iş akışı Tasarımcısı yüzeyine açın. Etkinlik Tasarımcısı içinde açılan bir <xref:System.Activities.Statements.Sequence>. Etkinlik Tasarımcısı bırakarak oluşturur bir <xref:System.Activities.Statements.CompensableActivity> etkinliği ile bir varsayılan <xref:System.Activities.Activity.DisplayName%2A> CompensableActivity biri. Düzen <xref:System.Activities.Activity.DisplayName%2A> üstbilgisinin değerini **CompensableActivity** etkinlik Tasarımcısı. İçinde de düzenlenebilir **DisplayName** özellik kılavuzunda kutusu.

### <a name="the-compensableactivity-properties"></a>CompensableActivity özellikleri
 Aşağıdaki tabloda <xref:System.Activities.Statements.CompensableActivity> özellikleri Tasarımcısı'nda nasıl kullanıldığı açıklanmaktadır. <xref:System.Activities.Activity.DisplayName%2A> Ve <xref:System.Activities.Activity%601.Result%2A> özelliği özellik kılavuzunda düzenlenebilir ancak iş akışı Tasarımcısı yüzeyine diğer özellikleri düzenlenmesi gerekir.

|Özellik adı|Gerekli|Kullanım|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|İsteğe bağlı kolay adı <xref:System.Activities.Statements.CompensableActivity> etkinlik. CompensableActivity varsayılandır.|
|<xref:System.Activities.Activity%601.Result%2A>|False|Dönüş değerini belirtir <xref:System.Activities.Statements.CompensableActivity>. Bu özellik, özellik kılavuzunda düzenlenmelidir.|
|<xref:System.Activities.Statements.CompensableActivity.Body%2A>|Doğru|Sağlanan maaş, iptal ve Doğrulama mantığı için etkinlik belirtir. Eklemek için <xref:System.Activities.Statements.CompensableActivity.Body%2A> etkinlik, açılan bir etkinlikten **araç kutusu** içine **gövdesi** kutusuna **CompensableActivity** etkinlik Tasarımcısı. "Buraya Bırak etkinlik" İpucu metnini ekleyin.|
|<xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A>|False|İptal durumunda olduğunda çalıştırılan etkinlik belirtir. Etkinlik eklemek için kendi Tasarımcısından bırak **araç kutusu** içine **CancellationHandler** kutusuna **CompensableActivity** etkinlik Tasarımcısı. İpucu metni "Etkinliği buraya bırakın" ekleyin.|
|<xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A>|False|Etkinlik için telafi bırakıldığında yürütülecek belirtir <xref:System.Activities.Statements.CompensableActivity.Body%2A> etkinlik. Bu işleyici açıkça çağrılabilir <xref:System.Activities.Statements.Compensate> etkinlik.<br /><br /> Etkinlik eklemek için etkinlik Tasarımcısı'ndan doğrudan **araç kutusu** içine **CompensationHandler** kutusuna **CompensableActivity** etkinlik Tasarımcısı. İpucu metni "Etkinliği buraya bırakın" ekleyin.|
|<xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A>|False|Onaylama yürütülecek etkinliği <xref:System.Activities.Statements.CompensableActivity.Body%2A> etkinlik. Bu işleyici açıkça çağrılabilir <xref:System.Activities.Statements.Confirm> etkinlik.<br /><br /> Etkinlik eklemek için etkinlik Tasarımcısı'ndan doğrudan **araç kutusu** içine **ConfirmationHandler** kutusuna **CompensableActivity** etkinlik Tasarımcısı. İpucu metni "Etkinliği buraya bırakın" ekleyin.|

## <a name="see-also"></a>Ayrıca bkz.

- [İşlem](../workflow-designer/transaction-activity-designers.md)
- [CancellationScope](../workflow-designer/cancellationscope-activity-designer.md)
- [Compensate](../workflow-designer/compensate-activity-designer.md)
- [Confirm](../workflow-designer/confirm-activity-designer.md)
- [TransactionScope](../workflow-designer/transactionscope-activity-designer.md)