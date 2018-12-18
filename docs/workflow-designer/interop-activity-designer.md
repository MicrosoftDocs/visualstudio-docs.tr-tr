---
title: İş Akışı Tasarımcısı - Interop etkinlik Tasarımcısı
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- System.Activities.Statements.Interop.UI
ms.assetid: 800a3403-ba86-41c4-8de1-c4fee9703eb1
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 7f3b5fd2674d63fad6398eeaee082862c4cf6476
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51809135"
---
# <a name="interop-activity-designer"></a>Interop Etkinlik Tasarımcısı

**Interop** etkinlik Tasarımcısı oluşturmak ve yapılandırmak için kullanılan bir <xref:System.Activities.Statements.Interop> etkinlik.

## <a name="the-interop-activity"></a>Birlikte çalışma etkinliği

<xref:System.Activities.Statements.Interop> Etkinlik öğesinden türetilen türler yürütülmesini yönetir <xref:System.Workflow.ComponentModel.Activity?displayProperty=fullName> bir iş akışındaki.

### <a name="use-the-interop-activity-designer"></a>Interop etkinlik Tasarımcısı kullanma

**Interop** etkinlik Tasarımcısı bulunabilir **geçiş** kategorisi **araç kutusu**, hangi erişilen tıklayarak **araç kutusu**sekmesi. Alternatif olarak, seçin **araç kutusu** gelen **görünümü** tuşuna basın veya menü **Ctrl**+**Alt** + **X**.

[Geçiş](../workflow-designer/migration-activity-designers.md) içeren kategori <xref:System.Activities.Statements.Interop> etkinliği yalnızca gösterilir **araç kutusu** projenizi tam .NET Framework 4 hedefliyse.

C# projeleri için projeye sağ tıklayarak tam .NET Framework 4 kullanmak için projeyi yeniden hedefleyebilirsiniz **Çözüm Gezgini** seçerek **özellikleri**. Üzerinde **uygulama** sekmesinde **NET Framework 4** seçeneğini **hedef Framework'ü**. Seçin **Evet** bu değişikliği onaylamak için.

Visual Basic projeleri için projeye sağ tıklayarak tam .NET Framework 4 kullanmak için projeyi yeniden hedefleyebilirsiniz **Çözüm Gezgini** seçerek **özellikleri**. Üzerinde **derleme** sekmesinde **Gelişmiş derleme seçenekleri** düğmesi. Seçin **.Net Framework 4** gelen **hedef çerçeve listesi**ve ardından **Tamam**. Seçin **Evet** bu değişikliği onaylamak için.

**Interop** etkinlik Tasarımcısı, gelen sürüklenebilir **araç kutusu** ve etkinlikleri genellikle yerleştirilen her yerde, gibi olarak içinde iş akışı Tasarımcısı yüzeyine bırakılan bir <xref:System.Activities.Statements.Sequence>. Bırakarak **Interop** etkinlik Tasarımcısı oluşturur bir <xref:System.Activities.Statements.Interop> etkinliği ile bir varsayılan **DisplayName** , birlikte çalışabilirlik. Düzenleyebileceğiniz <xref:System.Activities.Activity.DisplayName%2A> başlığını **Interop** etkinlik Tasarımcısı veya **DisplayName** özellik kılavuzunda kutusu.

Tıklayın **göz atmak için tıklatın** metinde **ActivityType** üzerinde kutusu **Interop** etkinlik Tasarımcısı veya açmak için özellik kılavuzunda **göz atın ve Bir .net seçin türü** iletişim kutusu. İş akışı 3.0 veya 3.5 iş akışı etkinlikleri için yalnızca türleri gösterilmektedir. Diğer bir deyişle, yalnızca öğesinden türetilmiş <xref:System.Workflow.ComponentModel.Activity> gösterilir. Bir tür belirtmek için bu kutuyu kullanma hakkında daha fazla bilgi için bkz. [göz atın ve bir .NET türünü seç iletişim kutusu](../workflow-designer/browse-and-select-a-dotnet-type-dialog-box.md).

### <a name="the-interop-properties"></a>Birlikte çalışma özellikleri

Aşağıdaki tabloda <xref:System.Activities.Statements.Interop> özellikleri Tasarımcısı'nda nasıl kullanıldığı açıklanmaktadır. Bu özellikler, özellik kılavuzu veya iş akışı Tasarımcısı yüzeyine düzenlenebilir.

|Özellik adı|Gerekli|Kullanım|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Kolay adı <xref:System.Activities.Statements.Interop> etkinlik. Varsayılan değer **Interop**. Görünen ad gerekli olmamasına karşın, bir sağlamak için önerilir.|
|<xref:System.Activities.Statements.Interop.ActivityType%2A>|Doğru|Tarafından bulunan bir etkinlik türünü belirten <xref:System.Activities.Statements.Interop> etkinlik. Bu tür belirtilen öğesinden türetilmelidir <xref:System.Workflow.ComponentModel.Activity>.|

## <a name="see-also"></a>Ayrıca bkz.

- [Geçiş](../workflow-designer/migration-activity-designers.md)