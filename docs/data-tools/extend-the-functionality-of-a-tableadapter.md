---
title: Bir TableAdapter’ın işlevselliğini genişletme
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data [Visual Studio], TableAdapters
- data [Visual Studio], extending TableAdapters
- TableAdapters, adding functionality
ms.assetid: 418249c8-c7f3-47ef-a94c-744cb6fe6aaf
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: a5b34bcb9c1532190f730e26c691289d489a2f3c
ms.sourcegitcommit: 1df0ae74af03bcf0244129a29fd6bd605efc9f61
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/01/2018
ms.locfileid: "50751082"
---
# <a name="extend-the-functionality-of-a-tableadapter"></a>Bir TableAdapter’ın işlevselliğini genişletme

TableAdapter bağdaştırıcısının kısmi sınıf dosyası için kod ekleyerek bir TableAdapter işlevselliğini genişletebilirsiniz.

Düzenleyici içindeki TableAdapter herhangi bir değişiklik yapıldığında bir TableAdapter tanımlayan kod yeniden oluşturulursa **veri kümesi Tasarımcısı**, veya ne zaman bir sihirbaz bir TableAdapter yapılandırmasını değiştirir. Kodunuzu bir TableAdapter oluşturma işlemi sırasında silinmesini önlemek için TableAdapter bağdaştırıcısının kısmi sınıf dosyası için kodu ekleyin.

Kısmi sınıflar arasında birden çok fiziksel dosyaları Bölünecek belirli bir sınıf için kod sağlar. Daha fazla bilgi için [kısmi](/dotnet/visual-basic/language-reference/modifiers/partial) veya [partial (tür)](/dotnet/csharp/language-reference/keywords/partial-type).

## <a name="locate-tableadapters-in-code"></a>TableAdapters kod içinde bulun

TableAdapter'ları ile tasarlandığında **veri kümesi Tasarımcısı**, oluşturulan TableAdapter sınıfları, iç içe sınıfları olmayan <xref:System.Data.DataSet>. TableAdapter'ları, TableAdapter bağdaştırıcısının ilişkili veri kümesinin adına dayalı bir ad alanında bulunur. Örneğin, uygulamanız adlı bir veri içeriyorsa `HRDataSet`, TableAdapter'ları bulunması `HRDataSetTableAdapters` ad alanı. (Bu deseni adlandırma kuralını izler: *DatasetName* + `TableAdapters`).

Aşağıdaki örnekte adlı bir TableAdapter varsayılır `CustomersTableAdapter`içeren bir proje içinde `NorthwindDataSet`.

### <a name="to-create-a-partial-class-for-a-tableadapter"></a>Kısmi bir sınıf için bir TableAdapter oluşturmak için

1.  Yeni bir sınıf giderek projenize ekleyin. **proje** menü ve seçerek **sınıfı Ekle**.

2.  Sınıf adını `CustomersTableAdapterExtended`.

3.  Seçin **ekleme**.

4.  Kod aşağıdaki gibi doğru ad alanını ve projeniz için kısmi sınıf adı ile değiştirin:

     [!code-csharp[VbRaddataTableAdapters#2](../data-tools/codesnippet/CSharp/extend-the-functionality-of-a-tableadapter_1.cs)]
     [!code-vb[VbRaddataTableAdapters#2](../data-tools/codesnippet/VisualBasic/extend-the-functionality-of-a-tableadapter_1.vb)]

## <a name="see-also"></a>Ayrıca bkz.

- [TableAdapter'ları kullanarak veri kümelerini doldurma](../data-tools/fill-datasets-by-using-tableadapters.md)