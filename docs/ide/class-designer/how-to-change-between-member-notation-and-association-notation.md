---
title: 'Nasıl Yapılır: Üye Gösterimi ile İlişkilendirme Gösterimi Arasında Geçiş (Sınıf Tasarımcısı)'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- notation, member
- association notation
- member notation
- notation, association
ms.assetid: 65881c5a-d251-4a36-ad0d-73d088436092
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: bdb4f28fc367b309a015a3faa8f749e2512db879
ms.sourcegitcommit: 4c0db930d9d5d8b857d3baf2530ae89823799612
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/10/2018
ms.locfileid: "33957807"
---
# <a name="how-to-change-between-member-notation-and-association-notation-in-class-designer"></a>Nasıl yapılır: üye gösterimi ile ilişkilendirme gösterimi sınıf tasarımcısında değiştirme

İçinde **Sınıf Tasarımcısı**, sınıf diyagramı temsil eden iki türden üye gösterimi ilişkilendirme gösterimi ve tersi yönde arasında bir ilişki ilişki şekilde değiştirebilirsiniz. İlişkilendirme satırları genellikle görüntülenen üyeleri türleri nasıl ilişkilendirildiğini yararlı görsel öğe sağlar.

> [!NOTE]
> İlişkilendirme ilişkileri bir üye özelliği veya alanı gösterilebilir. Üye gösterimi ilişkilendirme gösterimi değiştirmek için bir tür başka bir türünün bir üyesi olması gerekir. Üye gösterimi ilişkilendirme gösterimi değiştirmek için iki tür bir ilişki satır ile bağlanmalıdır. Daha fazla bilgi için bkz: [nasıl yapılır: bBetween türleri ilişkilendirmeleri oluşturma](how-to-create-associations-between-types.md). Projeniz birden çok sınıf diyagramları içeriyorsa, bir diyagram ilişkilendirme ilişkileri görüntüler şekilde yaptığınız değişiklikler yalnızca o diyagramı etkiler. Başka bir diyagrama ilişkilendirme ilişkileri görüntülenme şeklini değiştirmek için açın veya diyagramlarda görüntülemek ve aşağıdaki adımları gerçekleştirin.

## <a name="to-change-member-notation-to-association-notation"></a>Üye gösterimi ilişkilendirme gösterimi değiştirmek için

1.  Çözüm Gezgini'nde proje düğümden sınıf diyagramı (.cd) dosyasını açın.

2.  Üye özellik veya alan ilişkiyi temsil eden sınıf diyagramında türü şeklinde sağ tıklatın ve seçin **Göster ilişkilendirmesi olarak**.

    > [!TIP]
    > Hiçbir özellikler veya alanlar türü şeklinde görünür durumdaysa şeklinde bölmeler daraltılmış olabilir. Türü şekli genişletmek için bölme adına çift tıklayın veya türü şekli sağ tıklatın ve seçin **genişletme**.

    Üye türü şeklinde bölme kaybolur ve iki tür bağlanmak için bir ilişki çizgi görünür. İlişkilendirme çizgisi özelliği veya alanı adıyla etiketlenir.

## <a name="to-change-association-notation-to-member-notation"></a>Üye gösterimi ilişkilendirme gösterimi değiştirmek için

Sınıf diyagramında ilişkilendirme satırın sağ tıklatın ve seçin **Göster özelliği olarak** veya **Göster alanı olarak** uygun şekilde. İlişkilendirme çizgisi kaybolur, ve özellik türü şeklini diyagramda içinde uygun bölme görüntüler.

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: türler arasında devralmayı oluşturma](how-to-create-inheritance-between-types.md)
- [Nasıl yapılır: türler arasında devralmayı görüntüleme](how-to-view-inheritance-between-types.md)
- [Türleri ve İlişkileri Görüntüleme](viewing-types-and-relationships.md)
- [Nasıl yapılır: Koleksiyon ilişkilendirmesini Görselleştirme](how-to-visualize-a-collection-association.md)