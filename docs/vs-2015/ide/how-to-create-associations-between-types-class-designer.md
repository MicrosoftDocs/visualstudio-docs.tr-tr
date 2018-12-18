---
title: 'Nasıl yapılır: türler (Sınıf Tasarımcısı) arasında ilişkilendirme oluşturma | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.classdesigner.associationline
helpviewer_keywords:
- types [Visual Studio], associations
- association lines, defining (Class Designer)
- defining association lines (Class Designer)
- associations, types
- association lines
ms.assetid: adccb9c8-2f8a-4086-9fa9-f70f99fb6e00
caps.latest.revision: 24
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 33b1a45d1c5dc3275ebbde8124986705bcac51ef
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49856801"
---
# <a name="how-to-create-associations-between-types-class-designer"></a>Nasıl yapılır: türler (Sınıf Tasarımcısı) arasında ilişkilendirme oluşturma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sınıf Tasarımcısı'nda ilişkilendirme çizgileri, bir diyagramdaki sınıfların nasıl ilişkili olduğunu gösterir. İlişkilendirme çizgisi, projenizdeki başka bir sınıfın özellik veya alan türü olan bir sınıfı temsil eder. İlişkilendirme çizgileri genellikle, projenizdeki sınıflar arasında en önemli ilişkileri göstermek için kullanılır.  
  
 Tüm alanları ve özellikleri ilişkilendirmeler halinde görüntüleyebilirsiniz; bununla birlikte diyagramda vurgulamak istediğiniz unsura bağlı olarak yalnızca önemli üyeleri ilişkilendirme olarak göstermek daha anlamlı olur. (Daha az önemli üyeleri normal üye olarak gösterebilir veya bütünüyle gizleyebilirsiniz.)  
  
> [!NOTE]
>  Sınıf Tasarımcısı yalnızca tek yönlü ilişkilendirmeleri destekler.  
  
### <a name="to-define-an-association-line-in-the-class-diagram"></a>Sınıf Diyagramı'nda bir ilişkilendirme çizgisi tanımlamak için  
  
1.  Araç Kutusu'nda, Sınıf Tasarımcısı'nın altında seçin **ilişkilendirme**.  
  
2.  İlişkilendirme ile bağlamak istediğiniz iki şekil arasına bir çizgi çizin.  
  
     İlk sınıfta yeni bir özellik oluşturulur. Bu özellik varsayılan ada sahip bir ilişkilendirme çizgisi görüntüler (şekildeki bir bölme içinde özellik olarak değil). Türü ise, ilişkilendirme çizgisinin işaret ettiği şekildir.  
  
### <a name="to-change-the-name-of-an-association"></a>İlişkilendirmenin adını değiştirmek için  
  
- Diyagram yüzeyinde ilişkilendirme çizgisinin etiketine tıklayın ve etiketi düzenleyin.  
  
  \- veya -  
  
1.  İlişkilendirme olarak gösterilen özelliği içeren şekle tıklayın.  
  
     Şekil odağı alır ve üyeleri Sınıf Ayrıntıları penceresinde ve Özellikler penceresinde görüntülenir.  
  
2.  Sınıf Ayrıntıları penceresinde ya da Özellikler penceresinde bu özelliğe ilişkin ad alanını düzenleyin ve Enter tuşuna basın.  
  
     Adı güncelleştirilmiştir **sınıf ayrıntıları** penceresinde, ilişkilendirme çizgisi, Özellikler penceresinde ve kod.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Nasıl Yapılır: Üye Gösterimi ile İlişkilendirme Gösterimi Arasında Geçiş (Sınıf Tasarımcısı)](../ide/how-to-change-between-member-notation-and-association-notation-class-designer.md)



