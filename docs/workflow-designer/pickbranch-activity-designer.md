---
title: İş Akışı Tasarımcısı - PickBranch etkinlik Tasarımcısı
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- System.Activities.Statements.PickBranch.UI
ms.assetid: f523ad47-bbc0-4cda-a35c-41e67c4ba081
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e45c8ec2d7af5f1bfde5e145607728d3ff0bc85d
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49831789"
---
# <a name="pickbranch-activity-designer"></a>PickBranch Etkinlik Tasarımcısı

<xref:System.Activities.Statements.PickBranch> Yürütme içinde olay-tabanlı bir yolunu sağlayan bir <xref:System.Activities.Statements.Pick> , gelen bir olay tarafından tetiklenebilecek bir etkinlik.

## <a name="pickbranch"></a>PickBranch

<xref:System.Activities.Statements.PickBranch> içinde kapsanan nesneleri <xref:System.Activities.Statements.Pick.Branches%2A> koleksiyonunu bir <xref:System.Activities.Statements.Pick> etkinlik. Her <xref:System.Activities.Statements.PickBranch> bir dalda bulunan <xref:System.Activities.Statements.Pick> etkinliği ve bir tetikleyici olarak hizmet veren bazı gelen bir olay nedeniyle yürütülür. Bu şekilde, iş akışı Tasarımcısı olay tabanlı denetim akış modelleme sağlar. Her <xref:System.Activities.Statements.PickBranch> içeren bir <xref:System.Activities.Statements.PickBranch.Trigger%2A> ve <xref:System.Activities.Statements.PickBranch.Action%2A>.

### <a name="how-to-use-the-pick-activity-designer"></a>Çekme Etkinlik Tasarımcısı kullanma

Erişim **PickBranch** Tasarımcı içinde **akış denetimi** kategorisi **araç kutusu**.

İki boş <xref:System.Activities.Statements.PickBranch> nesneleriyle adlarını görüntülemek **Branch1** ve **Branch2** öğeleri olarak varsayılan olarak oluşturulan bir <xref:System.Activities.Statements.Pick> etkinlik zaman **çekme** Etkinlik Tasarımcısı, başlangıçta iş akışı tasarımcısını açın bırakılır. Bu ilgili <xref:System.Activities.Statements.PickBranch.DisplayName%2A> özellik değerlerini düzenlenebilir **PickBranch** Tasarımcı üst bilgi veya içinde **özellikleri** her dal için penceresi.

Eklemek için iki yolu vardır <xref:System.Activities.Statements.PickBranch> nesneler koleksiyonuna bir <xref:System.Activities.Statements.Pick> nesne: sürükleme ve bırakma **PickBranch** nden Tasarımcı **araç kutusu**, bağlam menüsünden kullanarak veya içinde **çekme** tasarım yüzeyine:

- **PickBranch** Tasarımcısı oluşturur bir <xref:System.Activities.Statements.PickBranch> zaman bunu sürüklediğiniz gelen **araç kutusu** ve dalları birine bırakılan bir **çekme** üzerinde etkinlik Tasarımcısı İş Akışı Tasarımcısı yüzeyine. Yeni <xref:System.Activities.Statements.PickBranch> nesneleri, içine yerleştirilebilir <xref:System.Activities.Statements.Pick> sola veya sağa var olan herhangi biri Tasarımcı <xref:System.Activities.Statements.PickBranch> zaten koleksiyonda yer alan öğeleri. Sürüklendiğinde bir **PickBranch** üzerine Tasarımcı **çekme** fareyle, tasarımcı **çekme** Tasarımcısı yeri belirtmek üzere bir dikey gri mavi bandı kullanır <xref:System.Activities.Statements.PickBranch> verilen fare yerleştirme için eklenir.

- Sağ **çekme** etkinlik Tasarımcısı (ancak değil iç **PickBranch** Tasarımcısı) seçin ve bağlam menüsü elde etmek için **dal oluşturma** yeni bir <xref:System.Activities.Statements.PickBranch>. Dikkat yeni <xref:System.Activities.Statements.PickBranch> varolan sağa eklenen <xref:System.Activities.Statements.PickBranch> nesneler **çekme** Tasarımcısı.

**PickBranch** Tasarımcısı açığa çıkarmak için Genişletilebilir **tetikleyici** ve **eylem** kutuları veya kendi üst sağ tarafında çift düzeltme işaretleri tıklayarak daraltılmış. Düzenleme <xref:System.Activities.Statements.PickBranch.Trigger%2A> ve <xref:System.Activities.Statements.PickBranch.Action%2A> her <xref:System.Activities.Statements.PickBranch> etkinliklerine bırakarak tarafından **tetikleyici** ve **eylem** kutularını kendi tasarımcıları.

<xref:System.Activities.Statements.PickBranch> Nesneler <xref:System.Activities.Statements.Pick.Branches%2A> koleksiyonunu bir <xref:System.Activities.Statements.Pick> nesne, bunları içinde yeni bir konuma sürükleyip bırakarak sıralanabilir **çekme** Tasarımcısı. **Çekme** Tasarımcısı yeri belirtmek üzere bir dikey gri mavi bandı kullanır <xref:System.Activities.Statements.PickBranch> verilen fare yerleştirme için eklenir.

Silmek için iki yolla bir <xref:System.Activities.Statements.PickBranch>:

- Seçin **PickBranch** Tasarımcısı ve silin.
- Seçin **PickBranch** seçin ve bağlam menüsünü elde etmek için tasarımcı, sağ tıklama **Sil**.

Seçtiğinizden emin olun **PickBranch** Tasarımcı içinde etkinliklerden birini seçerek olarak kendi **tetikleyici** veya **eylem** kutuları yanlışlıkla siler Bu etkinliklerden birini değil <xref:System.Activities.Statements.PickBranch> nesne.

### <a name="pickbranch-properties-in-the-workflow-designer"></a>İş akışı tasarımcısında PickBranch özellikleri

Aşağıdaki tabloda en kullanışlı gösterilmektedir <xref:System.Activities.Statements.PickBranch> özellikler ve iş akışı Tasarımcısı'nda kullanmayı açıklar.

|Özellik adı|Gerekli|Kullanım|
|-|--------------|-|
|<xref:System.Activities.Statements.PickBranch.DisplayName%2A>|False|Başlığında görüntülenen kolay ad **PickBranch** Tasarımcısı. Varsayılan değer daldır.<br /><br /> Ancak <xref:System.Activities.Activity.DisplayName%2A> kati şekilde gerekli değil kullanmak için en iyi bir uygulamadır.|
|<xref:System.Activities.Statements.PickBranch.Trigger%2A>|Doğru|Her <xref:System.Activities.Statements.PickBranch> içeren bir <xref:System.Activities.Statements.PickBranch.Trigger%2A> çağırabilirsiniz eylem <xref:System.Activities.Statements.PickBranch.Action%2A>.|
|<xref:System.Activities.Statements.PickBranch.Action%2A>|False|Her <xref:System.Activities.Statements.PickBranch> içeren bir <xref:System.Activities.Statements.PickBranch.Action%2A> tetiklenen ise yürütülür.|

## <a name="see-also"></a>Ayrıca bkz.

- [Denetim Akışı](../workflow-designer/control-flow-activity-designers.md)
- [Pick Etkinliği](/dotnet/framework/windows-workflow-foundation/pick-activity)
- [Pick Etkinliği Kullanma](/dotnet/framework/windows-workflow-foundation/samples/using-the-pick-activity)