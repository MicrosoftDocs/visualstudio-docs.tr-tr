---
title: 'Nasıl yapılır: bildirime dayalı bir kural koşulu oluşturma (eski) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
helpviewer_keywords:
- declarative rule conditions
- condition statements, declarative rule conditions
- Rule Condition Editor dialog box
ms.assetid: 804b6129-c433-408f-a424-46987967730c
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 0c23fed64d7f3a7681fce96663262f6d633299a9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75849329"
---
# <a name="how-to-create-a-declarative-rule-condition-legacy"></a>Nasıl Yapılır: Bildirime Dayanan Kural Koşulu Oluşturma (Eski)
Bu konu, veya öğesini hedefleyen bir kural koşulunun nasıl bildirilebileceğinizi açıklar [!INCLUDE[wfd1](../includes/wfd1-md.md)] [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)] .

 Condition deyiminin **değeri true** veya **false**olarak değerlendirilir. Bildirim temelli bir kural koşulu, [kural koşulu Düzenleyicisi Iletişim kutusu (eski)](../workflow-designer/rule-condition-editor-dialog-box-legacy.md) kullanılarak oluşturulan ve iş akışı ile XML olarak depolanan bir koşul deyimidir. Bu, birden çok koşul birleştiren iş akışı durumunu ve Boole ALKU 'ı karşılaştıran koşullar içerebilir.

 Bildirim temelli kural koşulları aşağıdaki Windows Workflow Foundation hazır etkinliklerinde kullanılır:

- [ConditionedActivityGroup](https://msdn2.microsoft.com/library/system.workflow.activities.conditionedactivitygroup.aspx)

- [IfElseBranchActivity](https://msdn2.microsoft.com/library/system.workflow.activities.ifelsebranchactivity.aspx)

- [ReplicatorActivity](https://msdn2.microsoft.com/library/system.workflow.activities.replicatoractivity.aspx)

- [WhileActivity](https://msdn2.microsoft.com/library/system.workflow.activities.whileactivity.aspx)

- [SequentialWorkflowActivity](https://msdn2.microsoft.com/library/system.workflow.activities.sequentialworkflowactivity.aspx)

- [StateMachineWorkflowActivity](https://msdn2.microsoft.com/library/system.workflow.activities.statemachineworkflowactivity.aspx)

### <a name="to-create-a-declarative-rule-condition-using-the-rule-condition-editor"></a>Kural koşulu düzenleyicisini kullanarak bildirim temelli bir kural koşulu oluşturmak için

1. Etkinliğin **Özellikler** penceresinde, etkinliğe bağlı olarak **koşul** özelliğine veya **UntilCondition** özelliğine tıklayın.

2. Özellik için listeden **bildirim temelli Kural koşulu** ' nı seçin.

3. **Condition** veya **UntilCondition** özelliğini genişletin.

4. **ConditionName** özelliğine tıklayın.

5. **Koşul Seç** iletişim kutusunu açmak için **ConditionName** üç nokta **[...]** düğmesine tıklayın.

6. **Kural koşulu Düzenleyicisi** iletişim kutusunu açmak Için **Yeni koşul** ' a tıklayın.

7. **Koşul metin kutusuna** koşul için ifadeyi yazın.

     Koşul ifadeleri oluşturma hakkında daha fazla bilgi için bkz. [kural koşulu Düzenleyicisi Iletişim kutusu (eski)](../workflow-designer/rule-condition-editor-dialog-box-legacy.md).

8. Koşul ifadesi oluşturmayı tamamladığınızda, iletişim kutusunu kapatmak için **Tamam** ' a tıklayın ve atanmış bir ada sahip kural koşulunu oluşturun.

     **Koşul Seç** iletişim kutusu açılır.

     **Koşul Seç** iletişim kutusunu kullanma hakkında daha fazla bilgi için bkz. [Koşul Seç Iletişim kutusu (eski)](../workflow-designer/select-condition-dialog-box-legacy.md).

## <a name="see-also"></a>Ayrıca Bkz.
 [While etkinlik](https://msdn2.microsoft.com/library/bb628552.aspx) [kuralı koşulu Düzenleyicisi Iletişim kutusu (eski)](../workflow-designer/rule-condition-editor-dialog-box-legacy.md) [iş akışlarındaki koşulları kullanarak](https://msdn2.microsoft.com/library/bb628447.aspx) bir süre sonra [Koşul Seç Iletişim kutusunu (eski)](../workflow-designer/select-condition-dialog-box-legacy.md) kullanan [IfElseBranchActivity etkinliğini](https://msdn2.microsoft.com/library/bb628465.aspx) [Using the Replicator Activity](https://msdn2.microsoft.com/library/bb628544.aspx) kullanan [eski iş akışı etkinlikleri](../workflow-designer/legacy-workflow-activities.md) [Using the ConditionedActivityGroup](https://msdn2.microsoft.com/library/bb675237.aspx)
