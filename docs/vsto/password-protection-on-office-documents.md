---
title: Office belgelerinde parola koruması
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- permissions [Office development in Visual Studio]
- workbooks [Office development in Visual Studio], restricted permissions
- passwords [Office development in Visual Studio], document protections
- documents [Office development in Visual Studio], restricted permissions
- Office documents [Office development in Visual Studio, restricted permissions
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 02deaccdd615bae0c948d50abdd41758dc701704
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "35676677"
---
# <a name="password-protection-on-office-documents"></a>Office belgelerinde parola koruması
  Böylece bunlar parola bilmeyen kişi tarafından açılamıyor, Microsoft Office Word belgelerini ve Microsoft Office Excel çalışma kitaplarını parola ayarlamak mümkündür. Bu seçenek olarak adlandırılan **açık parola**.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 Mevcut belgeler ve sahip çalışma kitaplarını kullanarak belge düzeyinde projeler oluşturabilir **açık parola** etkin. Visual Studio'da olan Word ve Excel belgeleri için farklı bir davranıştır **açık parola** etkin.  
  
 Etkinleştirme hakkında bilgi için **açık parola**, Word veya Excel'deki yardımına bakın.  
  
## <a name="behavior-of-excel-and-word"></a>Excel ve Word davranışı  
 Visual Studio'da olan her bir Excel çalışma kitabını açtığınızda **açık parola** etkin Excel parolasını ister. Çözümünüzü oluşturduğunuzda belge derleme sırasında açık olduğundan, parolasını yeniden istenir.  
  
 İlk kez açtığınızda bir Word belgesi Visual Studio'da sahip **açık parola** etkin, Word için parolayı ister. Parolanızı başarıyla girdikten sonra **açık parola** belgeden kaldırılır ve belgeyi açmayı parola artık gerekir. Çözümünüzde belgenin istiyorsanız, önce bir parola gerektirecek şekilde açılabilir, etkinleştirmelisiniz **açık parola** , son derlemeden sonra ve çözümü dağıtmadan önce.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Belge düzeyi çözümlerde belge koruması](../vsto/document-protection-in-document-level-solutions.md)   
 [Bilgi Hakları Yönetimine ve yönetilen kod uzantılarına genel bakış](../vsto/information-rights-management-and-managed-code-extensions-overview.md)   
 [Nasıl yapılır: kodun kısıtlı izinle belgelerin arkasında çalıştırmak için izin verme](../vsto/how-to-permit-code-to-run-behind-documents-with-restricted-permissions.md)   
 [Office çözümleri oluşturma ve tasarlama](../vsto/designing-and-creating-office-solutions.md)  
  
  