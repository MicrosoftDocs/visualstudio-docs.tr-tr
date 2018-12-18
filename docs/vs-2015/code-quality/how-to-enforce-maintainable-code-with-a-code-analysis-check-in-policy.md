---
title: 'Nasıl yapılır: bir kod analizi iade ilkesi ile Bakımı yapılabilir kodu zorlama | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- code analysis, check-in policies
ms.assetid: d1b3b04f-4dd9-40e6-b2d4-b414d33fb647
caps.latest.revision: 10
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 3ef282bf1b19cb2d72075619539921cdb88d08f2
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49174857"
---
# <a name="how-to-enforce-maintainable-code-with-a-code-analysis-check-in-policy"></a>Nasıl yapılır: Bir Kod Çözümleme İade İlkesi ile Bakımı Yapılabilir Kodu Zorlama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Geliştiriciler, karmaşıklığı ve bakımı kodlarını ölçmek için kod ölçümleri araç kullanabilirsiniz, ancak iade ilkesinin parçası olarak kod ölçümleri çağrılamaz. Ancak, bir takım, kodun kod ölçümleri standartlarıyla uyumluluğu doğrulamak ve iade etme ilkeleri aracılığıyla kuralları zorunlu Kod Analizi kuralları etkinleştirebilirsiniz. Kod ölçümleri hakkında daha fazla bilgi için bkz: [kod ölçüm değerleri](../code-quality/code-metrics-values.md).  
  
 Geliştiriciler, derinliği, devralma, eşlenmesiyle sınıfı, bakım dizini ve karmaşıklık kurallarını Kod Analizi iade ilkeleri ile Bakımı yapılabilir kodu zorlama etkinleştirebilirsiniz. Dört bu kurallar, Kod Analizi İlkesi Düzenleyicisi'nde "Bakım kuralları" kategorisi altında bulunur.  
  
 Yöneticiler sürümü denetlemek için [!INCLUDE[esprfound](../includes/esprfound-md.md)] iade ilkesi gereksinimleri için Kod Analizi bakım kuralları ekleyebilirsiniz. Bu ilkeleri geliştiriciler kod iade başlatmadan önce bu kuralı değişikliklere dayalı analizi çalıştırmak gerekli iade.  
  
### <a name="to-open-the-code-analysis-policy-editor"></a>Kod Analizi İlkesi Düzenleyicisi'ni açmak için  
  
1.  İçinde **Takım Gezgini**, takım projesine sağ tıklayın, **takım projesi ayarları**ve ardından **kaynak denetimi**.  
  
     **Kaynak denetimi** iletişim kutusu görüntülenir.  
  
2.  Üzerinde **iade ilkesi** sekmesine ve tıklayın **Ekle**.  
  
     **İade İlkesi Ekle** iletişim kutusu görüntülenir.  
  
3.  İçinde **iade ilkesi** listesinden **Kod Analizi** onay kutusunu işaretleyin ve ardından **Tamam**.  
  
     **Kod Analizi İlke Düzenleyicisi** iletişim kutusu görüntülenir.  
  
### <a name="to-enable-code-analysis-maintainability-rules"></a>Kod Analizi bakım kuralları etkinleştirmek için  
  
1.  İçinde **Kod Analizi İlke Düzenleyicisi** iletişim kutusunun **kural ayarları**, genişletme **bakım kuralları** düğümü.  
  
2.  Aşağıdaki kurallar için onay kutularını seçin:  
  
    -   Devralma derinliği: **CA1501 AvoidExcessiveInheritance** -eşiği: fazla 5 düzey derinliğinde uyarı  
  
    -   Karmaşıklık: **CA1502 AvoidExcessiveComplexity** -eşiği: 25'den fazla uyarı  
  
    -   Bakım dizini: **CA1505 AvoidUnmaintainableCode** -eşiği: az 20 uyarı  
  
    -   Sınıf bağlantısı: **CA1506 AvoidExcessiveClassCoupling** -eşiği: bir sınıf için 80'den fazla ve 30 bir yöntem için birden fazla uyarı  
  
    -   Ayrıca, bir derleme önlemek için bir kuralı ihlali istiyorsanız seçin **uyarı bir hata olarak değerlendir** kural açıklaması yanındaki onay kutusunu.  
  
3.  **Tamam**'ı tıklatın. Yeni iade ilkesi artık, gelecekteki iade etme işlemleri için de geçerlidir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Kod ölçüm değerleri](../code-quality/code-metrics-values.md)   
 [Kod Çözümleme İade İlkeleri Oluşturma ve Kullanma](../code-quality/creating-and-using-code-analysis-check-in-policies.md)



