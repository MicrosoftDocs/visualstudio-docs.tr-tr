---
title: 'Nasıl yapılır: O R tasarımcısı tarafından oluşturulan kodu genişletme | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d6d1122e-2f55-4607-8d8b-48c3c22600fb
caps.latest.revision: 7
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 14fd1f950d50f2cb71e56fc8b1e75ff60f3da0ce
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49227932"
---
# <a name="how-to-extend-code-generated-by-the-or-designer"></a>Nasıl yapılır: bir O/R tasarımcısı tarafından oluşturulan kodu genişletme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Tarafından oluşturulan kodu [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] varlık sınıfları ve diğer nesneler üzerinde Tasarımcı yüzeyine değişiklik yapıldığında yeniden oluşturulur. Tasarımcı, kod yeniden oluşturur, bu kod oluşturma işlemi nedeniyle, oluşturulan kod için eklediğiniz herhangi bir kod genellikle üzerine yazılır. [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] Yazılmaz kod içine ekleyebileceğiniz kısmi sınıf dosyaları oluşturmak olanağı sağlar. Bir örneği tarafından oluşturulan kodu kendi kodunuzu ekleme [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] veri doğrulama (varlık) SQL sınıflarına LINQ to eklemektir. Bilgi için [nasıl yapılır: Varlık sınıflarına doğrulama ekleme](../data-tools/how-to-add-validation-to-entity-classes.md).  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
## <a name="adding-code-to-an-entity-class"></a>Bir varlık sınıfı için kod ekleme  
  
#### <a name="to-create-a-partial-class-and-add-code-to-an-entity-class"></a>Kısmi bir sınıf oluşturun ve bir varlık sınıfı için kod ekleyin  
  
1.  Yeni bir LINQ to SQL sınıfları dosyası oluşturun veya açın (**.dbml** dosya) içinde [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]. (Çift **.dbml** dosyası **Çözüm Gezgini**/**veritabanı Gezgini**.)  
  
2.  İçinde [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)], doğrulama ekleyin ve ardından istediğiniz sınıfı sağ **kodu görüntüle**.  
  
     Seçilen varlık sınıfı için bir parçalı sınıf Kod Düzenleyicisi açılır.  
  
3.  Kısmi sınıf bildiriminde varlık sınıfı için kodunuzu ekleyin.  
  
## <a name="adding-code-to-a-datacontext"></a>Bir DataContext için kod ekleme  
  
#### <a name="to-create-a-partial-class-and-add-code-to-a-datacontext"></a>Kısmi bir sınıf oluşturun ve bir DataContext için kod ekleyin  
  
1.  Yeni bir LINQ to SQL sınıfları dosyası oluşturun veya açın (**.dbml** dosya) içinde [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]. (Çift **.dbml** dosyası **Çözüm Gezgini**/**veritabanı Gezgini**.)  
  
2.  İçinde [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)], Tasarımcı üzerinde boş bir alana sağ tıklayın ve ardından **kodu görüntüle**.  
  
     Kod Düzenleyicisi ile kısmi bir sınıf için DataContext açılır.  
  
3.  Kısmi sınıf bildiriminde DataContext için kodunuzu ekleyin.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [LINQ to SQL araçlarını Visual Studio'da](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [İzlenecek yol: LINQ to SQL sınıfları (O R Designer) oluşturma](http://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233)   
 [LINQ to SQL](http://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655)   
 [İzlenecek yol: Varlık sınıflarına doğrulama ekleme](http://msdn.microsoft.com/library/85b06a02-b2e3-4534-95b8-d077c8d4c1d7)

