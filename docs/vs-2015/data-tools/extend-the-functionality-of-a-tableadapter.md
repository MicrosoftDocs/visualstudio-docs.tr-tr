---
title: Bir TableAdapter işlevini genişletme | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- data [Visual Studio], TableAdapters
- data [Visual Studio], extending TableAdapters
- TableAdapters, adding functionality
ms.assetid: 418249c8-c7f3-47ef-a94c-744cb6fe6aaf
caps.latest.revision: 14
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 58f92f082ec4e7934e8eb7597832a6a58d23a1ca
ms.sourcegitcommit: d462dd10746624ad139f1db04edd501e7737d51e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/29/2018
ms.locfileid: "50219750"
---
# <a name="extend-the-functionality-of-a-tableadapter"></a>Bir TableAdapter’ın işlevselliğini genişletme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
TableAdapter bağdaştırıcısının kısmi sınıf dosyası için kod ekleyerek bir TableAdapter işlevselliğini genişletebilirsiniz.  
  
 Düzenleyici içindeki TableAdapter herhangi bir değişiklik yapıldığında bir TableAdapter tanımlayan kod yeniden oluşturulursa **veri kümesi Tasarımcısı**, veya ne zaman bir sihirbaz bir TableAdapter yapılandırmasını değiştirir. Kodunuzu bir TableAdapter oluşturma işlemi sırasında silinmesini önlemek için TableAdapter bağdaştırıcısının kısmi sınıf dosyası için kodu ekleyin.  
  
 Kısmi sınıflar arasında birden çok fiziksel dosyaları Bölünecek belirli bir sınıf için kod sağlar. Daha fazla bilgi için [kısmi](http://msdn.microsoft.com/library/7adaef80-f435-46e1-970a-269fff63b448) veya [partial (tür)](http://msdn.microsoft.com/library/27320743-a22e-4c7b-b0b3-53afe3607334).  
  
## <a name="locate-tableadapters-in-code"></a>TableAdapters kod içinde bulun  
 TableAdapter'ları ile tasarlandığında **veri kümesi Tasarımcısı**, oluşturulan TableAdapter sınıfları, iç içe sınıfları olmayan <xref:System.Data.DataSet>. TableAdapter'ları, TableAdapter bağdaştırıcısının ilişkili veri kümesinin adına dayalı bir ad alanında bulunur. Örneğin, uygulamanız adlı bir veri içeriyorsa `HRDataSet`, TableAdapter'ları bulunması `HRDataSetTableAdapters` ad alanı. (Bu deseni adlandırma kuralını izler: *DatasetName* + `TableAdapters`).  
  
 Aşağıdaki örnekte adlı bir TableAdapter varsayılır `CustomersTableAdapter`içeren bir proje içinde `NorthwindDataSet`.  
  
#### <a name="to-create-a-partial-class-for-a-tableadapter"></a>Kısmi bir sınıf için bir TableAdapter oluşturmak için  
  
1.  Yeni bir sınıf giderek projenize ekleyin. **proje** menü ve seçerek**sınıfı Ekle**.  
  
2.  Sınıf adını `CustomersTableAdapterExtended`.  
  
3.  Seçin **ekleme**.  
  
4.  Kod aşağıdaki gibi doğru ad alanını ve projeniz için kısmi sınıf adı ile değiştirin:  
  
     [!code-csharp[VbRaddataTableAdapters#2](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataTableAdapters/CS/CustomersTableAdapterExtended.cs#2)]
     [!code-vb[VbRaddataTableAdapters#2](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataTableAdapters/VB/CustomersTableAdapterExtended.vb#2)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [TableAdapter'ları kullanarak veri kümelerini doldurma](../data-tools/fill-datasets-by-using-tableadapters.md)

