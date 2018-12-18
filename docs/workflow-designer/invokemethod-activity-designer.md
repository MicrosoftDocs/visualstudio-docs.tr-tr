---
title: İş Akışı Tasarımcısı - InvokeMethod etkinlik Tasarımcısı
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- System.Activities.Statements.InvokeMethod.UI
ms.assetid: 15e6efdc-52ca-46d8-9c5e-063f7c8265a6
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 7ac82e36d3abc942e0c5492cc4d7acf347eba36c
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49839576"
---
# <a name="invokemethod-activity-designer"></a>InvokeMethod Etkinlik Tasarımcısı

**InvokeMethod** Tasarımcısı oluşturmak ve yapılandırmak için kullanılan bir <xref:System.Activities.Statements.InvokeMethod> etkinlik.

## <a name="the-invokemethod-activity"></a>InvokeMethod etkinliği

<xref:System.Activities.Statements.InvokeMethod> Belirtilen nesnenin veya türün genel bir yöntemi çağırır.

### <a name="use-the-invokemethod-activity-designer"></a>InvokeMethod etkinlik Tasarımcısı kullanma

Erişim **InvokeMethod** etkinlik Tasarımcısı'nda **Temelleri** kategorisi **araç kutusu**. **InvokeMethod** etkinlik Tasarımcısı, gelen sürüklenebilir **araç kutusu** ve etkinlikleri genellikle yerleştirilir burada ever, örneğin olarak içinde iş akışı Tasarımcısı yüzeyine açın bırakılan bir <xref:System.Activities.Statements.Sequence>. Etkinlik Tasarımcısı bırakarak oluşturur bir <xref:System.Activities.Statements.InvokeMethod> etkinliği ile bir varsayılan <xref:System.Activities.Activity.DisplayName%2A> InvokeMethod biri. <xref:System.Activities.Activity.DisplayName%2A> Üst bilgisinde düzenlenebilir **InvokeMethod** etkinlik Tasarımcısı veya **DisplayName** özellik kılavuzunda kutusu.

### <a name="the-invokemethod-properties"></a>InvokeMethod özellikleri

Aşağıdaki tabloda <xref:System.Activities.Statements.InvokeMethod> özelliklerini ve bunların Tasarımcısı'nda nasıl kullanıldığı açıklanmaktadır. Bu özellikler, özellik kılavuzunda düzenlenebilir ve bazı iş akışı Tasarımcısı yüzeyine düzenlenebilir.

|Özellik adı|Gerekli|Kullanım|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Kolay adı <xref:System.Activities.Statements.InvokeMethod> etkinlik. InvokeMethod varsayılan değerdir.<br /><br /> Ancak <xref:System.Activities.Activity.DisplayName%2A> kati şekilde gerekli değil kullanmak en iyisidir.|
|<xref:System.Activities.Statements.InvokeMethod.MethodName%2A>|Doğru|Etkinlik yürütüldüğünde çağrılacak yöntemin adı. Çağrılan yöntem olarak bildirilmelidir **genel**. Bu özellik, Tasarımcı yüzeyinde düzenlenebilir ve zorunludur.|
|<xref:System.Activities.Statements.InvokeMethod.Parameters%2A>|False|Çağrılan yöntem parametre koleksiyonu. Parametreler koleksiyonu Yöntem imzasında göründükleri sırayla eklenmesi gerekir. Görüntülenecek **parametreleri** iletişim ayarlayabilirsiniz bu özellik üç nokta düğmesini tıklatın **parametreleri** özellik kılavuzunda alanı. Tıklayın **bağımsız değişken oluşturma** düğmesini parametreleri ekleyin.|
|<xref:System.Activities.Statements.InvokeMethod.Result%2A>|False|Yöntem çağrısının dönüş değeri.|
|<xref:System.Activities.Statements.InvokeMethod.RunAsynchronously%2A>|Doğru|Zaman uyumsuz olarak çağrılan yöntemi olup olmadığını belirtir. Varsayılan değer **False**.|
|<xref:System.Activities.Statements.InvokeMethod.TargetObject%2A>|False|Çağrılacak yöntem içeren nesne. Bu özellik, Tasarımcı yüzeyinde düzenlenebilir.<br /><br /> Ya da <xref:System.Activities.Statements.InvokeMethod.TargetObject%2A> veya <xref:System.Activities.Statements.InvokeMethod.TargetType%2A> ayarlanması için gereklidir.|
|<xref:System.Activities.Statements.InvokeMethod.TargetType%2A>|False|Türünü <xref:System.Activities.Statements.InvokeMethod.TargetObject%2A>. Bu özellik, Tasarımcı yüzeyinde düzenlenebilir. Çağrılan yöntemi statik ise bu özellik yalnızca ayarlamanız gerekir.|

Parametre olarak geçirmeniz bir C# **kullanıma** parametresi (örneğin, `Method1(out myParam))`, kullanın **OutArgument** yerine **InOutArgument**

Adlı bağımsız değişkenleri olan yöntemleri **TargetObject** veya **sonucu** kullanılarak çağrılamaz <xref:System.Activities.Statements.InvokeMethod> etkinlik. Bunun nedeni olan <xref:System.Activities.Statements.InvokeMethod> etkinlik kayıtlarını <xref:System.Activities.Statements.InvokeMethod.GenericTypeArguments%2A>, <xref:System.Activities.Statements.InvokeMethod.TargetObject%2A> ve <xref:System.Activities.Statements.InvokeMethod.Result%2A> içinde <xref:System.Activities.Activity.CacheMetadata%2A>.

Parametreleri kaydetmek için algoritma <xref:System.Activities.Activity.CacheMetadata%2A> aşağıda gösterilmiştir:

1.  Kayıt <xref:System.Activities.Statements.InvokeMethod.TargetObject%2A> bağımsız değişken.

2.  Kayıt <xref:System.Activities.Statements.InvokeMethod.Result%2A> bağımsız değişken.

3.  Yinelemek <xref:System.Activities.Statements.InvokeMethod.Parameters%2A> koleksiyonu ve her bağımsız değişken kaydedin.

Sonuçta elde edilen özel durum türüdür <xref:System.Activities.InvalidWorkflowException> şu iletiyle: 'InvokeMethod': 'TargetObject' adıyla bir değişken RuntimeArgument veya zaten bir DelegateArgument bulunmaktadır. Adları bir ortam kapsamı içinde benzersiz olmalıdır.

Bu kısıtlama geçerli değildir <xref:System.Activities.Statements.InvokeMethod.TargetType%2A> ve <xref:System.Activities.Statements.InvokeMethod.RunAsynchronously%2A>. İş akışı bağımsız değişkenleri olmadığınız ve bu nedenle kayıtlı olmayan <xref:System.Activities.Statements.InvokeMethod.GenericTypeArguments%2A> koleksiyonunu <xref:System.Activities.Statements.InvokeMethod> etkinliğinde <xref:System.Activities.Activity.CacheMetadata%2A> yöntemi.

## <a name="see-also"></a>Ayrıca bkz.

- [Temel Türler](../workflow-designer/primitives-activity-designers.md)
- [Assign](../workflow-designer/assign-activity-designer.md)
- [Delay](../workflow-designer/delay-activity-designer.md)
- [WriteLine](../workflow-designer/writeline-activity-designer.md)