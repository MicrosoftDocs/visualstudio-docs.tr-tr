---
title: .ofs dosyasındaki bir veya daha fazla özellik seçilen ileti sınıfı için geçerli değil
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- VSTO.NewFormRegionWizard.OFSPropertyError
dev_langs:
- VB
- CSharp
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: cfae8533337bbe18c89dbb670fb58a0c89c6c54c
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34692505"
---
# <a name="one-or-more-properties-in-the-ofs-file-are-not-valid-for-the-message-class-selected"></a>.ofs dosyasındaki bir veya daha fazla özellik seçilen ileti sınıfı için geçerli değil
  Outlook'ta tasarlanan form bölgesini içeri aktardığınızda, bu hata görünür, ancak bir veya daha fazla alan form bölgesi üzerindeki son sayfasında, seçtiğiniz ileti sınıfları ile uyumlu olmayan **Yeni Form bölgesi** Sihirbazı.  

Örneğin, seçebilirsiniz **görev (IPM. Görev)** son sayfasında **Yeni Form bölgesi** Sihirbazı. Form bölgesini varsa bir **iş adresi** alan, bir görev iş adresi sahip olmadığından bu hatayı alırsınız. Bu nedenle, **iş adresi** alanı ile uyumlu değildir `IPM.Task` ileti sınıfı.  
  
 Seçtiğiniz **görev (IPM. Görev)** son sayfasında **Yeni Form bölgesi** Sihirbazı. Form bölgesini varsa bir **iş adresi** alan, bir görev iş adresi sahip olmadığından bu hatayı alırsınız. Bu nedenle, **iş adresi** alanı ile uyumlu değildir `IPM.Task` ileti sınıfı.  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
-   Sihirbazın son sayfasında **Yeni Form bölgesi** Sihirbazı, form bölgesini alanları ile uyumlu bir ileti sınıfı seçin.  
  
-   Outlook Form tasarımcısında ileti sınıflarıyla uyumlu olmayan alanlarını kaldırın. Son sayfasında, seçmek için planlama alanları kaldırmak **Yeni Form bölgesi** Sihirbazı.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [İzlenecek yol: Outlook'ta tasarlanan form bölgesini içeri aktarma](../vsto/walkthrough-importing-a-form-region-that-is-designed-in-outlook.md)  
  
  