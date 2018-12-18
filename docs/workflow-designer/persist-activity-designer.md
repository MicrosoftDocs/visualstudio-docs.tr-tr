---
title: İş Akışı Tasarımcısı - Persist etkinlik Tasarımcısı
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- System.Activities.Statements.Persist.UI
ms.assetid: be8648dd-3eb9-4a50-8ec1-57a8be804692
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 51f74b5348c7e99824659ee713171bd71c5f522e
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49831348"
---
# <a name="persist-activity-designer"></a>Persist Etkinlik Tasarımcısı

**Kalan** etkinlik Tasarımcısı oluşturmak ve yapılandırmak için kullanılan bir <xref:System.Activities.Statements.Persist> etkinlik.

## <a name="the-persist-activity"></a>Persist etkinlik

<xref:System.Activities.Statements.Persist> Etkinliğini bir iş akışı mümkünse diske kaydeder. <xref:System.Activities.Statements.Persist> Etkinlik yürütülemiyor alanında bir Kalıcılık olmayan, örneğin, içinde bir <xref:System.Activities.Statements.TransactionScope> etkinlik. Kullanıyorsanız bir <xref:System.Activities.Statements.Persist> etkinlik kalıcı olmayan bir kapsam içinde bir özel durumu çalışma zamanında oluşturulur.

### <a name="using-the-persist-activity-designer"></a>Kullanarak Persist etkinlik Tasarımcısı

**Kalan** etkinlik Tasarımcısı bulunabilir **çalışma zamanı** kategorisi **araç kutusu**, hangi erişilen tıklayarak **araç kutusu** sekme (Alternatif olarak, seçin **araç kutusu** gelen **görünümü** menüsünden veya CTRL + ALT + X.)

**Kalan** etkinlik Tasarımcısı, gelen sürüklenebilir **araç kutusu** ve etkinlikleri genellikle yerleştirilen her yerde, gibi olarak içinde iş akışı Tasarımcısı yüzeyine açın bırakılan bir <xref:System.Activities.Statements.Sequence>. Bu, oluşturur bir <xref:System.Activities.Statements.Persist> etkinliği ile bir varsayılan **DisplayName** kalan. <xref:System.Activities.Activity.DisplayName%2A> Üst bilgisinde düzenlenebilir **kalan** etkinlik Tasarımcısı veya **DisplayName** özellik kılavuzunda kutusu.

### <a name="the-persist-properties"></a>Kalıcı özellikleri

Aşağıdaki tabloda <xref:System.Activities.Statements.Persist> özellikleri Tasarımcısı'nda nasıl kullanıldığı açıklanmaktadır. Bu özellikler, özellik kılavuzunda düzenlenebilir ve bunlardan bazıları iş akışı Tasarımcısı yüzeyine düzenlenebilir.

|Özellik adı|Gerekli|Kullanım|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Kolay adı <xref:System.Activities.Statements.Persist> etkinlik. Kalan varsayılandır. Görünen ad kesinlikle gerekli olmamakla birlikte, bir görünen ad kullanmak için en iyi bir uygulamadır.|

## <a name="see-also"></a>Ayrıca bkz.

- [Çalışma Zamanı](../workflow-designer/runtime-activity-designers.md)
- [TerminateWorkflow](../workflow-designer/terminateworkflow-activity-designer.md)