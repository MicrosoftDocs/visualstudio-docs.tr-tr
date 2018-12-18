---
title: Bilgi Hakları Yönetimine ve yönetilen kod uzantılarına genel bakış
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Information Rights Management [Office development in Visual Studio]
- workbooks [Office development in Visual Studio], restricted permissions
- IRM [Office development in Visual Studio]
- documents [Office development in Visual Studio], restricted permissions
- rights management [Office development in Visual Studio]
- Office documents [Office development in Visual Studio, restricted permissions
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 35a118774d50bcc697cd3ff5663fc26d8580ac88
ms.sourcegitcommit: 209c2c068ff0975994ed892b62aa9b834a7f6077
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/17/2018
ms.locfileid: "34263767"
---
# <a name="information-rights-management-and-managed-code-extensions-overview"></a>Bilgi Hakları Yönetimine ve yönetilen kod uzantılarına genel bakış
  Microsoft Office Word ve Microsoft Office Excel, yetkisiz kişilerin hassas bilgileri görmesini veya değiştirmesini önlemeye yardımcı olabilecek bir özellik olan Bilgi Hakları Yönetimi (IRM) sağlar. Bilgi Hakları Yönetimi nasıl çalıştığı hakkında daha fazla bilgi için belirli Office uygulamasında yardımına bakın.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
## <a name="run-code-behind-documents-with-restricted-permissions"></a>Kısıtlı izinle belgelerin arkasında kodu çalıştırma  
 Çözümünüzü bir belge veya varsayılan olarak, IRM kullanan çalışma kitabındaki içeriyorsa, Word ve Excel herhangi kodun çalışmasına izin vermez. Belgenin yazarını olan veya tam denetim erişimi varsa, böylece çözümünüzün çalışması varsayılan değiştirebilirsiniz. Daha fazla bilgi için bkz: [nasıl yapılır: kodun kısıtlı izinle belgelerin arkasında çalışmasına izin verme](../vsto/how-to-permit-code-to-run-behind-documents-with-restricted-permissions.md).  
  
 IRM kullanımını engeller <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.ServerDocument> belgede önbelleğe alınmış veriyi almak veya değiştirmek için.  
  
## <a name="end-users-to-restrict-permissions-to-documents-that-use-managed-code-extensions"></a>Son kullanıcıların yönetilen kod uzantıları kullanan belgeler için izinleri kısıtla  
 IRM çözümünüzde belge veya çalışma kitabına tam denetim erişimi olan herkes izinleri kısıtlamak için kullanabilirsiniz. Örneğin, muhasebe departmanındaki bir son kullanıcı veritabanından verilerle çalışma otomatik olarak dolduran bir çözüm kullanıyorsa, bu kullanıcı yalnızca kendi departmanında kişilere erişimi değiştir ve başkaları için okuma erişimi izin vermek isteyebilirsiniz. Kullanıcı kısıtlı izinleri eklediğinde, varsayılan olarak, çalışma sayfası arka plan kod çalıştırılamıyor ve çalışma ile verileri doldurulmaz.  
  
 Sorunu düzeltmek için belge veya çalışma kitabına tam denetim erişim biriyle nesne modeli programlı erişmesine izin vermek için varsayılan izin ayarlarını değiştirmeniz gerekir. Daha fazla bilgi için bkz: [nasıl yapılır: kodun kısıtlı izinle belgelerin arkasında çalışmasına izin verme](../vsto/how-to-permit-code-to-run-behind-documents-with-restricted-permissions.md).  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Belge düzeyi çözümlerde belge koruması](../vsto/document-protection-in-document-level-solutions.md)   
 [Office belgelerinde parola koruması](../vsto/password-protection-on-office-documents.md)   
 [Office çözümleri güvenli](../vsto/securing-office-solutions.md)   
 [Office çözümünü dağıtma](../vsto/deploying-an-office-solution.md)   
 [Tasarlama ve Office çözümleri oluşturma](../vsto/designing-and-creating-office-solutions.md)  
  
  