---
title: 'Nasıl yapılır: menü öğesini kullanarak uyarıları bastırma | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- warnings, suppressing
- code analysis, suppressing warnings
ms.assetid: 36bd1850-dcde-4ed0-9bc3-0b83df434362
caps.latest.revision: 26
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 1c756a5ab6516d78f5370622555898c98658e8b3
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49211795"
---
# <a name="how-to-suppress-warnings-by-using-the-menu-item"></a>Nasıl yapılır: Menü Öğesini Kullanarak Uyarıları Bastırma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[NOT]
>  Kaynak gizleme web sitesi projeleri için desteklenmiyor.  
  
 Kod çözümleme uyarılarını bastırma için Kod Analizi penceresi kullanabilirsiniz. Uyarı gizleme devre dışı bırakmasını ile aynı değil. Bir uyarıyı bastırmak ihlalinin yalnızca belirli bir örneği için uygulanır. Aynı uyarı diğer ihlalleri yine de hata Listesi penceresinde bildirilir.  
  
 Kod Analizi çalıştırdıktan sonra bir veya daha fazla kod Analizi penceresi içinde görüntülenen kod çözümleme uyarıları, uygulamanız için geçerli olmadığını belirlemek. Örneğin, kodun doğru olduğunu belirlemek. Veya bazı ihlalleri düşük öncelikli ve mevcut geliştirme döngüsü içinde sabit olmayan bir durum olabilir. Bunun nedeni ne olursa olsun, uyarı kodunu gözden geçirildi ve bu uyarı bastırılabilir belirlendi takım üyelerinizin izin vermek için geçerli olduğunu belirtmek çoğunlukla yararlı olur. Bu, uyarının oluşturulduğu yakın bir gizleme yerleştirmenizi sağlar çünkü kaynakta gizleme yararlı olur.  
  
 Kaynak kodu veya küresel bir gizleme dosyasında gizleme görüntülenip görüntülenmeyeceğini seçebilirsiniz. Genel gizleme dosyasında bazı gizlemeleri yerleştirilmelidir. Bu durum söz konusuysa **içinde kaynak** seçeneği devre dışı bırakılacak.  
  
### <a name="to-suppress-a-warning-by-using-menu-item"></a>Menü öğesini kullanarak bir uyarıyı bastırmak için  
  
1.  Üzerinde **Çözümle** menüsünde seçin **Windows** seçip **Kod Analizi**.  
  
2.  İçinde **Kod Analizi** penceresinde, uyarı bastır seçin.  
  
3.  Eylem seçin ve ardından **iletileri gösterme**seçin **içinde kaynak** veya **proje gizleme dosyası**.  
  
     Özel uyarı bastırılır ve üzeri Kod Analizi penceresi bir uyarı görüntülenir.  
  
> [!NOTE]
>  Bir hedef olmayan gizlemeleri küresel bir gizleme dosyasında görünür.



