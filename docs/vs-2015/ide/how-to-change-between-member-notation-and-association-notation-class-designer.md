---
title: 'Nasıl yapılır: üye gösterimi ile ilişkilendirme gösterimi (Sınıf Tasarımcısı) arasında | Microsoft Docs'
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
- notation, member
- association notation
- member notation
- notation, association
ms.assetid: 65881c5a-d251-4a36-ad0d-73d088436092
caps.latest.revision: 25
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 1ed7ee328e65f0e76426a21db8f2481e590b0546
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49173614"
---
# <a name="how-to-change-between-member-notation-and-association-notation-class-designer"></a>Nasıl Yapılır: Üye Gösterimi ile İlişkilendirme Gösterimi Arasında Geçiş (Sınıf Tasarımcısı)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sınıf Tasarımcısı'nda, sınıf diyagramı temsil eden iki türden ilişkilendirme gösterimi ve bunun tersi de üye gösterimi arasında bir ilişkilendirme ilişkisi şeklini değiştirebilirsiniz. Üyeleri ilişkilendirme çizgileri genellikle görüntülenen türleri nasıl ilişkili olduğunu, kullanışlı bir görselleştirme sağlar.  
  
> [!NOTE]
>  İlişkilendirme ilişkileri bir üye özelliği veya alanı gösterilebilir. Üye gösterimi ilişkilendirme gösterimi değiştirmek için bir tür, başka bir tür üyesi olmalıdır. Üye gösterimi ilişkilendirme gösterimi değiştirmek için iki tür tarafından bir ilişkilendirme çizgisi bağlanması gerekir. Daha fazla bilgi için [nasıl yapılır: ilişkileri arasında türleri oluşturmak (Sınıf Tasarımcısı)](../ide/how-to-create-associations-between-types-class-designer.md). Projenizi içeren birden fazla sınıf diyagramı, diyagram ilişkilendirme ilişkileri görüntüler şekilde yaptığınız değişiklikler yalnızca o diyagramı etkiler. Başka bir diyagrama ilişkilendirme ilişkileri görüntüleme biçimini değiştirmek için açın veya bu diyagramı görüntüleyin ve aşağıdaki adımları gerçekleştirin.  
  
### <a name="to-change-member-notation-to-association-notation"></a>Üye gösterimi ilişkilendirme gösterimi değiştirmek için  
  
1.  Çözüm Gezgini'nde proje düğümü aracılığıyla, sınıf diyagramı (.cd) dosyası açın.  
  
2.  Üye özellik veya alan ilişkisini temsil eden içinde tür şeklini sınıf diyagramı'nda, sağ tıklatın ve seçin **ilişkilendirmesi olarak göster**.  
  
    > [!TIP]
    >  Hiçbir özelliklerle veya alanlarla türü şeklinde görünür durumdaysa, bölmeleri şeklinde daraltılmış olabilir. Tür şeklini genişletmek için bölme adına çift tıklayın veya türü şekle sağ tıklayın ve seçin **genişletme**.  
  
     Bölme türü şeklinde üyenin kaybolur ve iki tür bağlanmak için bir ilişkilendirme çizgisi görüntülenir. İlişkilendirme çizgisi, özelliği veya alanı adıyla etiketlenir.  
  
### <a name="to-change-association-notation-to-member-notation"></a>Üye gösterimi ilişkilendirme gösterimi değiştirmek için  
  
-   Sınıf diyagramı'nda ilişkilendirme çizgisi sağ tıklatın ve seçin **Göster özelliği olarak** veya **alan olarak göster** uygun şekilde.  
  
     İlişkilendirme çizgisi kaybolur, ve tür şeklini diyagramda içinde uygun bölme özelliği görüntülenir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Nasıl yapılır: (Sınıf Tasarımcısı) türler arasında devralma oluşturma](../ide/how-to-create-inheritance-between-types-class-designer.md)   
 [Nasıl yapılır: (Sınıf Tasarımcısı) türler arasında devralmayı görüntüleme](../ide/how-to-view-inheritance-between-types-class-designer.md)   
 [Türleri ve ilişkiler (Sınıf Tasarımcısı) görüntüleme](../ide/viewing-types-and-relationships-class-designer.md)   
 [Nasıl Yapılır: Koleksiyon İlişkilendirmesini Görselleştirme (Sınıf Tasarımcısı)](../ide/how-to-visualize-a-collection-association-class-designer.md)



