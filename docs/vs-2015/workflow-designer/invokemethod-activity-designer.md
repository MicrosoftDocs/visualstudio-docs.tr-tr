---
title: InvokeMethod etkinlik Tasarımcısı | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- System.Activities.Statements.InvokeMethod.UI
ms.assetid: 15e6efdc-52ca-46d8-9c5e-063f7c8265a6
caps.latest.revision: 6
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: a3fa1c07bbb32bc1da963a0d2f0a91ae6c193a30
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49863691"
---
# <a name="invokemethod-activity-designer"></a>InvokeMethod Etkinlik Tasarımcısı
**InvokeMethod** Tasarımcısı oluşturmak ve yapılandırmak için kullanılan bir <xref:System.Activities.Statements.InvokeMethod> etkinlik.  
  
## <a name="the-invokemethod-activity"></a>InvokeMethod etkinliği  
 <xref:System.Activities.Statements.InvokeMethod> Belirtilen nesnenin veya türün genel bir yöntemi çağırır.  
  
### <a name="using-the-invokemethod-activity-designer"></a>InvokeMethod etkinlik Tasarımcısı kullanma  
 **InvokeMethod** etkinlik Tasarımcısı bulunabilir **Temelleri** kategorisi **araç kutusu**, hangi erişilen tıklayarak **araçkutusu** sekmesini [!INCLUDE[wfd2](../includes/wfd2-md.md)] (Alternatif olarak, seçin **araç** gelen **görünümü** menü veya CRTL + ALT + X.)  
  
 **InvokeMethod** etkinlik Tasarımcısı, gelen sürüklenebilir **araç kutusu** ve oturum bırakılan [!INCLUDE[wfd2](../includes/wfd2-md.md)] yüzey nerede hiç etkinlikleri genellikle yerleştirilir, gibi olarak içinde bir <xref:System.Activities.Statements.Sequence>. Bu, oluşturur bir <xref:System.Activities.Statements.InvokeMethod> etkinliği ile bir varsayılan <xref:System.Activities.Activity.DisplayName%2A> InvokeMethod biri. <xref:System.Activities.Activity.DisplayName%2A> Üst bilgisinde düzenlenebilir **InvokeMethod** etkinlik Tasarımcısı veya **DisplayName** özellik kılavuzunda kutusu.  
  
### <a name="the-invokemethod-properties"></a>InvokeMethod özellikleri  
 Aşağıdaki tabloda <xref:System.Activities.Statements.InvokeMethod> özellikleri Tasarımcısı'nda nasıl kullanıldığı açıklanmaktadır. Bu özellikler, özellik kılavuzunda düzenlenebilir ve bazı şirket düzenlenebilir [!INCLUDE[wfd2](../includes/wfd2-md.md)]Tasarımcı yüzeyine bırakın.  
  
|Özellik adı|Gerekli|Kullanım|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Kolay adı <xref:System.Activities.Statements.InvokeMethod> etkinlik. InvokeMethod varsayılan değerdir.<br /><br /> Ancak <xref:System.Activities.Activity.DisplayName%2A> kati şekilde gerekli değil kullanmak için en iyi bir uygulamadır.|  
|<xref:System.Activities.Statements.InvokeMethod.MethodName%2A>|Doğru|Etkinlik yürütüldüğünde çağrılacak yöntemin adı. Çağrılan yöntem olarak bildirilmelidir **genel**. Bu özellik, Tasarımcı yüzeyinde düzenlenebilir. Bu zorunlu bir özelliğidir.|  
|<xref:System.Activities.Statements.InvokeMethod.Parameters%2A>|False|Çağrılan yöntem parametre koleksiyonu. Parametreler koleksiyonu Yöntem imzasında göründükleri sırayla eklenmesi gerekir. Özellik kılavuzunda, üç nokta düğmesini **parametreleri** alanını görüntüler **parametreleri** iletişim, bu özelliği ayarlayabilirsiniz. Tıklayın **bağımsız değişken oluşturma** düğmesini parametreleri ekleyin.|  
|<xref:System.Activities.Statements.InvokeMethod.Result%2A>|False|Yöntem çağrısının dönüş değeri.|  
|<xref:System.Activities.Statements.InvokeMethod.RunAsynchronously%2A>|Doğru|Zaman uyumsuz olarak çağrılan yöntemi olup olmadığını belirtir. Varsayılan değer **False**.|  
|<xref:System.Activities.Statements.InvokeMethod.TargetObject%2A>|False|Çağrılacak yöntem içeren nesne. Bu özellik, Tasarımcı yüzeyinde düzenlenebilir.<br /><br /> Ya da <xref:System.Activities.Statements.InvokeMethod.TargetObject%2A> veya <xref:System.Activities.Statements.InvokeMethod.TargetType%2A> ayarlanması için gereklidir.|  
|<xref:System.Activities.Statements.InvokeMethod.TargetType%2A>|False|Türünü <xref:System.Activities.Statements.InvokeMethod.TargetObject%2A>. Bu özellik, Tasarımcı yüzeyinde düzenlenebilir. Çağrılan yöntemi statik ise bu özellik yalnızca ayarlamanız gerekir.|  
  
 Parametreleri bir C# geçirmek için **kullanıma** parametresi (örneğin, `Method1(out myParam)),` kullanmalısınız **OutArgument** yerine **InOutArgument**  
  
 Adlı bağımsız değişkenleri olan yöntemleri **TargetObject** veya **sonucu** kullanılarak çağrılamaz <xref:System.Activities.Statements.InvokeMethod> etkinlik. Bunun nedeni olan <xref:System.Activities.Statements.InvokeMethod> etkinlik kayıtlarını <xref:System.Activities.Statements.InvokeMethod.GenericTypeArguments%2A>, <xref:System.Activities.Statements.InvokeMethod.TargetObject%2A> ve <xref:System.Activities.Statements.InvokeMethod.Result%2A> içinde <xref:System.Activities.Activity.CacheMetadata%2A>.  
  
 Parametreleri kaydetmek için algoritma <xref:System.Activities.Activity.CacheMetadata%2A> aşağıda gösterilmiştir:  
  
1. Kayıt <xref:System.Activities.Statements.InvokeMethod.TargetObject%2A> bağımsız değişken.  
  
2. Kayıt <xref:System.Activities.Statements.InvokeMethod.Result%2A> bağımsız değişken.  
  
3. Yinelemek <xref:System.Activities.Statements.InvokeMethod.Parameters%2A> koleksiyonu ve her bağımsız değişken kaydedin.  
  
   Sonuçta elde edilen özel durum türüdür <xref:System.Activities.InvalidWorkflowException> şu iletiyle: 'InvokeMethod': 'TargetObject' adıyla bir değişken RuntimeArgument veya zaten bir DelegateArgument bulunmaktadır. Adları bir ortam kapsamı içinde benzersiz olmalıdır.  
  
   Bu kısıtlama geçerli değildir <xref:System.Activities.Statements.InvokeMethod.TargetType%2A> ve <xref:System.Activities.Statements.InvokeMethod.RunAsynchronously%2A> çünkü bunlar iş akışı bağımsız değişken değildir ve bu nedenle, kayıtlı olmayan <xref:System.Activities.Statements.InvokeMethod.GenericTypeArguments%2A> koleksiyonunu <xref:System.Activities.Statements.InvokeMethod> etkinliğinde <xref:System.Activities.Activity.CacheMetadata%2A> yöntemi.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Temel öğeler](../workflow-designer/primitives-activity-designers.md)   
 [Ata](../workflow-designer/assign-activity-designer.md)   
 [gecikme](../workflow-designer/delay-activity-designer.md)   
 [WriteLine](../workflow-designer/writeline-activity-designer.md)