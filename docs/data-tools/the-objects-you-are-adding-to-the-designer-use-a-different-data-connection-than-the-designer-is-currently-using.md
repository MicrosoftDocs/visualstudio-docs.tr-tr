---
title: Nesneler farklı bağlantı kullanıyor
description: Tasarımcıya eklemekte olduğunuz nesneler tasarımcıdan farklı bir veri bağlantısı kullanır. Bu Visual Studio O/R Designer iletisi hakkındaki bilgileri görüntüleyin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: error-reference
ms.assetid: 332ed2f3-3377-4d51-8e3b-fdb98231978e
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: 22f982449ceb1d0ec5a6d960380d76dc11f66b09
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99858364"
---
# <a name="the-objects-you-are-adding-to-the-designer-use-a-different-data-connection-than-the-designer"></a>Tasarımcıya eklemekte olduğunuz nesneler tasarımcıdan farklı bir veri bağlantısı kullanır

Tasarımcıya eklemekte olduğunuz nesneler, tasarımcının kullanmakta olduğundan farklı bir veri bağlantısı kullanır. Tasarımcı tarafından kullanılan bağlantıyı değiştirmek istiyor musunuz?

Öğeleri **nesne ilişkisel Tasarımcısı** eklediğinizde (**O/R Designer**), tüm öğeler paylaşılan bir veri bağlantısı kullanır. (Tasarım yüzeyi, <xref:System.Data.Linq.DataContext> yüzeyde tüm nesneler için tek bir bağlantı kullanan öğesini temsil eder.) Tasarımcıya, tasarımcı tarafından kullanılmakta olan veri bağlantısından farklı bir veri bağlantısı kullanan bir nesne eklerseniz, bu ileti görünür. Bu hatayı çözmek için var olan bağlantıyı korumayı seçebilirsiniz. Bu seçimi yaparsanız, seçilen nesne eklenmez. Alternatif olarak, nesneyi eklemeyi ve <xref:System.Data.Linq.DataContext> Yeni bağlantıyla bağlantıyı sıfırlamayı seçebilirsiniz.

## <a name="connection-options"></a>Bağlantı seçenekleri

- Mevcut bağlantıyı seçilen nesne tarafından kullanılan bağlantıyla değiştirmek için **Evet**' e tıklayın.

   Seçilen nesne **O/R tasarımcısına** eklenir ve *DataContext. Connection* yeni bağlantı olarak ayarlanır.

   > [!NOTE]
   > **Evet**' e tıklarsanız, **O/R tasarımcısında** tüm varlık sınıfları yeni bağlantıyla eşleştirilir.

- Mevcut bağlantıyı kullanmaya devam etmek ve seçili nesneyi eklemeyi iptal etmek için **Hayır**'a tıklayın.

   Eylem iptal edildi. *DataContext. Connection* mevcut bağlantı olarak ayarlanmış durumda kalır.

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio 'da LINQ to SQL araçları](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
