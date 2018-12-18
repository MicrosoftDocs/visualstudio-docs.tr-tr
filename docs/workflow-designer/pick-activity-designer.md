---
title: İş Akışı Tasarımcısı - Pick etkinlik Tasarımcısı
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- System.Activities.Statements.Pick.UI
ms.assetid: 642c0a47-1b47-45de-a19a-ca0606cedd7a
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 5bd37c78567ea11d53899bcbaefb2e3809a00057
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49826017"
---
# <a name="pick-activity-designer"></a>Pick Etkinlik Tasarımcısı

<xref:System.Activities.Statements.Pick> Olay tabanlı denetim akış etkinliği sağlar. Etkinlik birden fazla dalları birini bir tetikleyici olaya yanıt olarak yürütür.

## <a name="the-pick-activity"></a>Pick etkinliği

A <xref:System.Activities.Statements.Pick> etkinliği içeren bir koleksiyonu <xref:System.Activities.Statements.PickBranch> nesneler, biri <xref:System.Activities.Statements.Pick> etkinlik, bir tetikleyici olarak hizmet veren bazı gelen bir olay nedeniyle yürütebilir. Bu şekilde, iş akışı Tasarımcısı olay tabanlı denetim akış modelleme sağlar. Her <xref:System.Activities.Statements.PickBranch> içeren bir <xref:System.Activities.Statements.PickBranch.Trigger%2A> ve <xref:System.Activities.Statements.PickBranch.Action%2A>. Başında bir <xref:System.Activities.Statements.Pick> etkinliğin yürütme, tüm tetikleyici etkinliklerini <xref:System.Activities.Statements.PickBranch> öğeleri zamanlanır. İlk etkinlik tamamlandıktan sonra karşılık gelen eylem etkinliği zamanlandı ve diğer tetikleyici etkinlikleri iptal edilir.

### <a name="how-to-use-the-pick-activity-designer"></a>Çekme Etkinlik Tasarımcısı kullanma

Erişim **çekme** etkinlik Tasarımcısı'nda **akış denetimi** kategorisi **araç kutusu**. **Çekme** etkinlik Tasarımcısı, gelen sürüklenebilir **araç kutusu** ve etkinlik tasarımcıları normalde, örneğin içine yerleştirilen her yerde iş akışı Tasarımcısı yüzeyine açın bırakılan bir  **Dizisi** etkinlik Tasarımcısı. İş Akışı Tasarımcısı'na bırakarak sonra oluşturduğu bir <xref:System.Activities.Statements.Pick> içeren varsayılan olarak iki boş etkinlik <xref:System.Activities.Statements.PickBranch> etkinlikleri öğelerle olarak görünen adlar Branch1 ve Branch2. Bu ilgili <xref:System.Activities.Statements.PickBranch.DisplayName%2A> özellik değerlerini düzenlenebilir **PickBranch** etkinlik Tasarımcısı üst bilgi veya içinde **özellikleri** her dal için penceresi.

Eklemek için iki yolu vardır <xref:System.Activities.Statements.PickBranch> etkinlikleri koleksiyonuna bir <xref:System.Activities.Statements.Pick> nesne: sürükleme ve bırakma **PickBranch** nden Tasarımcı **araç kutusu** veya bağlam menüsünden kullanarak içinde **çekme** tasarım yüzeyi. Ayrıntılar için bkz [PickBranch](../workflow-designer/pickbranch-activity-designer.md) konu. Yalnızca öğesini dikkat edin, içine yerleştirilebilir bir **çekme** etkinlik Tasarımcısı bir **PickBranch** etkinlik Tasarımcısı.

### <a name="pick-activity-properties-in-the-workflow-designer"></a>İş akışı tasarımcısında etkinlik özellikleri seçin

Aşağıdaki tabloda <xref:System.Activities.Statements.Pick> özellikleri Tasarımcısı'nda nasıl kullanıldığı açıklanmaktadır. Bu özellikler, özellik kılavuzu veya tasarımcı yüzeyine düzenlenebilir.

|Özellik adı|Gerekli|Kullanım|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Kolay adı belirtir <xref:System.Activities.Statements.Pick> üst bilgisindeki etkinlik Tasarımcısı. Seçim varsayılan değerdir. Değer özellik kılavuzunda veya etkinlik Tasarımcısı başlığındaki doğrudan düzenleyebilirsiniz.<br /><br /> Ancak <xref:System.Activities.Activity.DisplayName%2A> kati şekilde gerekli değil kullanmak için en iyi bir uygulamadır.|

## <a name="see-also"></a>Ayrıca bkz.

- [Denetim Akışı](../workflow-designer/control-flow-activity-designers.md)
- [Pick Etkinliği](/dotnet/framework/windows-workflow-foundation/pick-activity)
- [Pick Etkinliği Kullanma](/dotnet/framework/windows-workflow-foundation/samples/using-the-pick-activity)