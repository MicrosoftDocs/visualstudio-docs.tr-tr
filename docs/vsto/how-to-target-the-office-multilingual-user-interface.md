---
title: 'Nasıl yapılır: Office Çok Dilde Kullanıcı arabirimini hedefleme'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- globalization [Office development in Visual Studio], user interface targeting
- MUI [Office development in Visual Studio]
- Office applications [Office development in Visual Studio], localization
- Multilingual User Interface [Office development in Visual Studio]
- localization [Office development in Visual Studio], user interface targeting
- Office applications [Office development in Visual Studio], globalization
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 1b917479598b73f71a0f3092c874276a700717d6
ms.sourcegitcommit: 209c2c068ff0975994ed892b62aa9b834a7f6077
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/17/2018
ms.locfileid: "34262039"
---
# <a name="how-to-target-the-office-multilingual-user-interface"></a>Nasıl yapılır: Office Çok Dilde Kullanıcı arabirimini hedefleme
  Çok Dilde Kullanıcı Arabirimi (MUI) son kullanıcı kullanıcı arabirimi (UI) dilini değiştirme olanağı sağlayan bir Microsoft Office özelliğidir. Örneğin, İngilizce bir kullanıcı Arabirimi ile çalışan bir son kullanıcı için İspanyolca dil UI değiştirebilirsiniz.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 Uygulamanız çok sayıda dillerde Office kullanan kişiler tarafından kullanılacaksa, otomatik olarak (kullanıcı yüklü doğru kaynakları varsa) kullanıcının bilgisayarında Office tarafından kullanılan dil ile eşleşen UI dizelerinizi dilini değiştirmek için kod ekleyebilirsiniz.  
  
## <a name="to-check-the-current-office-ui-setting"></a>Geçerli Office UI ayarını denetlemek için  
  
1.  Kullanım <xref:System.Threading.Thread.CurrentUICulture%2A> geçerli iş parçacığının özelliği. Şu anda kullanıcının bilgisayar üzerinde çalışan Office sürümü tarafından kullanılan dil ile eşleşen UI dizelerinizi dilinin ayarlayın.  
  
     [!code-vb[Trin_VstcoreCreatingExcel#10](../vsto/codesnippet/VisualBasic/Trin_VstcoreCreatingExcelVB/Sheet1.vb#10)]
     [!code-csharp[Trin_VstcoreCreatingExcel#10](../vsto/codesnippet/CSharp/Trin_VstcoreCreatingExcelCS/Sheet1.cs#10)]  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Nasıl yapılır: birincil birlikte çalışma derlemeleriyle hedef Office uygulamaları](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md)   
 [Office çözümlerinde geç bağlama](../vsto/late-binding-in-office-solutions.md)  
  
  