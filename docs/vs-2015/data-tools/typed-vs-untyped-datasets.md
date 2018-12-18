---
title: Yazılmayan veri kümelerinin karşılaştırması yazılan | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c83ba0bb-5425-4d47-8891-6b4dbf937701
caps.latest.revision: 8
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 71761826611c490a3fb43413acaa29eb6520138f
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49283796"
---
# <a name="typed-vs-untyped-datasets"></a>Yazılan ve yazılmayan veri kümelerinin karşılaştırması
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Yazılan veri kümesi temel ilk türetilmiş bir veri kümesidir <xref:System.Data.DataSet> sınıfı ve ardından bilgilerinden **veri kümesi Tasarımcısı**, depolandığı .xsd dosyasına yeni, oluşturmak için bir veri kümesi sınıfı türü kesin belirlenmiş. (Tablolar, sütunlar ve benzeri) şema bilgileri oluşturulur ve bu yeni veri kümesi sınıfına birinci sınıf nesneleri ve özellikleri kümesi olarak derlenir. Yazılan veri kümesi temel devraldığından <xref:System.Data.DataSet> sınıfı, belirlenmiş bir sınıf tüm işlevlerini varsayar <xref:System.Data.DataSet> sınıfı ve bir örneği ele yöntemleriyle kullanılabilir bir <xref:System.Data.DataSet> bir parametre olarak sınıf.  
  
 Yazılmamış bir veri kümesi, buna karşılık, karşılık gelen hiçbir yerleşik şeması vardır. Türü belirtilmiş veri kümesi olduğu gibi tabloları, sütunları ve benzeri yazılmamış bir veri kümesi içerir; ancak bunlar yalnızca koleksiyon olarak sunulur. (El ile tabloları ve diğer veri öğelerini yazılmamış bir veri kümesini oluşturduktan sonra ancak, veri kümesinin yapısı bir şema dataset kullanarak dışa aktarabilirsiniz <xref:System.Data.DataSet.WriteXmlSchema%2A> yöntemi.)  
  
## <a name="contrasting-data-access-in-typed-and-untyped-datasets"></a>Yazılan ve yazılmayan veri kümeleri karşıt veri erişimi  
 Yazılan veri kümesi için sınıfın özelliklerini tabloları ve sütunları gerçek adları almakta nesne modeli vardır. Örneğin, bir türü belirtilmiş veri kümesi ile çalışıyorsanız, aşağıdaki gibi bir kod kullanarak bir sütun başvurabilirsiniz:  
  
 [!code-csharp[VbRaddataDatasets#4](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataDatasets/CS/Form1.cs#4)]
 [!code-vb[VbRaddataDatasets#4](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataDatasets/VB/Form1.vb#4)]  
  
 Buna karşılık, yazılmamış bir veri kümesi ile çalışıyorsanız, eşdeğer kod şöyledir:  
  
 [!code-csharp[VbRaddataDatasets#5](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataDatasets/CS/Form1.cs#5)]
 [!code-vb[VbRaddataDatasets#5](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataDatasets/VB/Form1.vb#5)]  
  
 Türü belirlenmiş erişim değil yalnızca daha kolay okunmasını, ancak aynı zamanda tam destekli IntelliSense içinde [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] **Kod Düzenleyicisi**. Yazılmış veri kümesi için söz dizimi ile çalışmak daha kolay olmasının yanı sıra veri kümesi üyeleri için değerler atama hataları olasılığını önemli ölçüde azaltan derleme zamanında tür sağlar. Bir sütunun adını değiştirirseniz, <xref:System.Data.DataSet> sınıfı ve ardından uygulamanızı derleyin, bir derleme hatası alırsınız. Derleme hataya çift tıklayarak **görev listesi**, doğrudan satır veya eski sütun adı başvuru kod satırlarını gidebilirsiniz. Erişim tablolar ve sütunlar bir türü belirtilmiş veri kümesi olduğundan da çalışma zamanında biraz daha hızlı erişim zamanında koleksiyonlar üzerinden değil, derleme zamanında belirlenir.  
  
 Türü belirtilmiş datasets birçok avantaj olsa bile yazılmamış bir veri kümesi çeşitli durumlarda yararlı olur. Şema veri kümesi için kullanılabilir olduğunda en belirgin senaryodur. Uygulamanız bir veri kümesi döndüren bir bileşeni ile etkileşim kurma Bu, örneğin, meydana gelebilir ancak önceden yapısını ne olduğunu bildiğiniz değil. Benzer şekilde, ne zaman bir statik, öngörülebilir yapısına sahip değil verilerle çalışma zamanları vardır. Türü belirtilmiş veri kümesi sınıfı her değişikliği veri yapısı ile yeniden oluşturmanız gerekirdi bu durumda, türü belirlenmiş bir veri kümesini kullanmak için pratik olmasıdır.  
  
 Daha genel olarak kullanılabilir bir şema zorunda kalmadan bir veri kümesini dinamik olarak oluşturabilir, birden çok kez vardır. Bu durumda, verileri ilişkisel bir biçimde temsil edilebilir olduğu sürece veri kümesi yalnızca bilgileri saklamak uygun bir yapı ' dir. Aynı anda bilgileri başka bir işleme geçirmek veya bir XML dosyasına yazmak için seri hale getirme olanağı gibi veri kümesinin özelliklerinden yararlanabilirsiniz.

