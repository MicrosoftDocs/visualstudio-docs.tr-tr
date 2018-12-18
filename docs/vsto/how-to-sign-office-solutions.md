---
title: 'Nasıl yapılır: Office çözümlerini imzalama'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- certificates [Office development in Visual Studio], Office solutions
- security [Office development in Visual Studio], signing Office solutions
- signing manifests [Office development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 161c175b6bb37ece93559f0378bbaf8e5e16d170
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43776139"
---
# <a name="how-to-sign-office-solutions"></a>Nasıl yapılır: Office çözümlerini imzalama
  Bir çözüm oturum açarsanız, kanıt olarak sertifika kullanarak çözüme güven verebilirsiniz. Birden çok çözüm için aynı sertifikayı kullanabilirsiniz ve tüm çözümleri hiçbir ek güvenlik ilkesi güncelleştirmeleriyle güvenilen olacaktır.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 Uygulamayı el ile düzenlemeniz ve dağıtım bildirimlerini bildirim oluşturma ve düzenleme aracı kullanarak (*mage.exe* ve *mageui.exe*), kullanabilmeniz için önce bildirimleri yeniden imzalamanız gerekir. Daha fazla bilgi için [nasıl yapılır: yeniden, uygulama ve dağıtım bildirimlerini imzalama](/visualstudio/deployment/how-to-re-sign-application-and-deployment-manifests).  
  
## <a name="sign-by-using-a-certificate"></a>Bir sertifika kullanarak oturum açın  
 Bir sertifika benzersiz bir anahtar ve çözüm yayıncısı kimliğini içeren bir dosyadır. Bir sertifika yetkilisinden sertifika satın alın veya kendi sertifikanızı oluşturun ve sahip bir sertifika yetkilisi imzalayın.  
  
 Visual Studio Office çözümleri hata ayıklamayı etkinleştirmek için geçici bir sertifika ile imzalar. Dağıtılan çözümleri durum kanıtı geçici bir sertifika kullanmamalıdır.  
  
### <a name="to-sign-an-office-solution-by-using-a-certificate"></a>Bir sertifika kullanarak Office çözümü imzalamak için  
  
1.  Üzerinde **proje** menüsünü tıklatın _SolutionName_**özellikleri**.  
  
2.  Tıklayın **imzalama** sekmesi.  
  
3.  Seçin **ClickOnce bildirimlerini imzala**.  
  
4.  Tıklayarak sertifikayı bulun **Store ' seçin** veya **dosyadan Seç** ve sertifikada gezinin.  
  
5.  Doğru sertifikayı kullanılmakta olduğunu doğrulamak için tıklayın **daha fazla ayrıntı** sertifika bilgileri görüntülemek için.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Office çözümleri güvenliğini sağlama](../vsto/securing-office-solutions.md)   
 [Office çözümlerine güven verme](../vsto/granting-trust-to-office-solutions.md)   
 [İmzalama Sayfası, Proje Tasarımcısı](/visualstudio/ide/reference/signing-page-project-designer)  
  
  