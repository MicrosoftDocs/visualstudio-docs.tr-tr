---
title: Yazılan ve yazılmayan veri kümelerinin karşılaştırması
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
ms.assetid: c83ba0bb-5425-4d47-8891-6b4dbf937701
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: d817938a7611d7390e400cfbf69c6836b9256f3b
ms.sourcegitcommit: d9e4ea95d0ea70827de281754067309a517205a1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/29/2018
ms.locfileid: "37117231"
---
# <a name="typed-vs-untyped-datasets"></a>Yazılan ve yazılmayan veri kümelerinin karşılaştırması
Taban ilk türetilmiş bir veri kümesi türü belirtilmiş veri kümesi olan <xref:System.Data.DataSet> sınıfı ve dosyasındaki bilgileri kullanır **veri kümesi Tasarımcısı**, kesin türü belirtilmiş veri kümesi sınıfı, yeni, oluşturmak için bir .xsd dosyasında depolanır. (Tablolar, sütunlar ve benzeri) şema bilgileri oluşturulur ve bu yeni veri kümesi sınıfına birinci sınıf nesneler ve özelliklerinin bir küme olarak derlenmiş. Türü belirtilmiş veri kümesi temelden devralan çünkü <xref:System.Data.DataSet> sınıfı, belirlenmiş sınıf varsayar tüm işlevselliğini <xref:System.Data.DataSet> sınıfı ve bir örneği ele yöntemleriyle kullanılabilir bir <xref:System.Data.DataSet> sınıfı bir parametre olarak.

 Türü belirsiz bir veri kümesini buna karşılık, karşılık gelen hiçbir yerleşik şeması vardır. Türü belirtilmiş veri kümesi olduğu gibi tablolar, sütunlar ve benzeri türü belirsiz bir veri kümesini içerir; ancak bu yalnızca koleksiyonu sunulur. (El ile tabloları ve diğer veri öğeleri türü belirsiz bir veri kümesini oluşturduktan sonra ancak, veri kümesi'nin yapısı bir şema veri kümesi'nin kullanarak dışa aktarabilirsiniz <xref:System.Data.DataSet.WriteXmlSchema%2A> yöntemi.)

## <a name="contrast-data-access-in-typed-and-untyped-datasets"></a>Yazılan ve yazılmayan veri kümeleri Karşıtlık veri erişimi
 Türü belirtilmiş veri kümesi için sınıf özelliklerini gerçek adlarını tablolar ve sütunlar üzerinde almakta nesne modeli vardır. Örneğin, bir türü belirtilmiş veri kümesi ile çalışıyorsanız, aşağıdaki gibi kod kullanarak bir sütun başvurusu yapabilir:

 [!code-csharp[VbRaddataDatasets#4](../data-tools/codesnippet/CSharp/typed-vs-untyped-datasets_1.cs)]
 [!code-vb[VbRaddataDatasets#4](../data-tools/codesnippet/VisualBasic/typed-vs-untyped-datasets_1.vb)]

 Buna karşılık, türü belirsiz bir veri kümesi ile çalışıyorsanız, eşdeğer kodu verilmiştir:

 [!code-csharp[VbRaddataDatasets#5](../data-tools/codesnippet/CSharp/typed-vs-untyped-datasets_2.cs)]
 [!code-vb[VbRaddataDatasets#5](../data-tools/codesnippet/VisualBasic/typed-vs-untyped-datasets_2.vb)]

 Yazılı erişim değil yalnızca okunmasını, ancak aynı zamanda tam olarak desteklenen Visual Studio'da IntelliSense tarafından **Kod düzenleyicisinde**. Çalışmak daha kolay olmanın yanı sıra türü belirtilmiş veri kümesi için söz dizimi derleme zamanında denetimi türü veri kümesi üyeleri için değerler atama hataları olasılığını önemli ölçüde azaltan sağlar. Bir sütun adını değiştirirseniz, <xref:System.Data.DataSet> sınıfı ve uygulamanızı derleyin, bir derleme hatası alıyorsunuz. Derleme hata çift tıklatarak **görev listesi**, doğrudan satırı veya eski sütun adı başvuru kod satırlarını gidebilirsiniz. Erişim için tabloları ve sütunları yazılmış bir veri kümesi olduğundan ayrıca çalışma zamanında biraz daha hızlı erişim çalışma zamanında koleksiyonlar üzerinden değil derleme zamanında belirlenir.

 Yazılan veri kümeleri birçok avantaj olsa da, çeşitli koşullar türü belirsiz bir veri kümesini yararlıdır. Hiçbir şema veri kümesi için kullanılabilir olduğunda en bariz senaryodur. Uygulamanızı bir veri kümesini döndüren bir bileşen ile etkileşim Bu, örneğin, meydana gelebilir ancak önceden yapısını nedir bildiğiniz değil. Benzer şekilde, ne zaman statik, tahmin edilebilir yapısına sahip değil verilerle çalışma saatleri vardır. Bu durumda, veri yapısı her değişiklik türü belirtilmiş veri kümesi sınıfıyla yeniden oluşturmak zorunda olduğu için yazılmış bir veri kümesini kullanmak için pratik.

 Daha fazla genel olarak, kullanılabilir bir şema gerek kalmadan bir veri kümesini dinamik olarak oluşturabilir, birçok kez vardır. Bu durumda, verileri ilişkisel bir biçimde temsil edilebilir olduğu sürece veri kümesi yalnızca bilgileri saklamak uygun bir yapı ' dir. Aynı anda bilgilerini başka bir işleme geçirmek için veya bir XML dosyasına yazmak için serileştirme yeteneği gibi veri kümesi'nin özelliklerinden yararlanabilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [Veri kümesi araçları](../data-tools/dataset-tools-in-visual-studio.md)