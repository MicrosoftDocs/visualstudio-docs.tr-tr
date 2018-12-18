---
title: LINQ to XML genel bakış ile WPF verilerini bağlama | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3bf80845-891b-41de-a71b-4080b5bd3ea6
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 457a097d46f9af409580d3784bb577090db0c535
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49852420"
---
# <a name="wpf-data-binding-with-linq-to-xml-overview"></a>LINQ to XML genel bakış ile WPF verilerini bağlama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu konu, dinamik veri bağlama özellikleri tanıtır <xref:System.Xml.Linq> ad alanı. Bu özellikler, kullanıcı arabirimi (UI) öğeleri Windows Presentation Foundation (WPF) için bir veri kaynağı olarak kullanılabilir.  
  
## <a name="xaml-and-linq-to-xml"></a>XAML ve LINQ to XML  
 .NET Framework 3.0 teknolojilerini desteklemek için Microsoft tarafından oluşturulan bir XML diyalekti Extensible Application Markup Language (XAML) olur. WPF içinde kullanıcı arabirimi öğeleri ve olayları ve veri bağlama gibi ilgili özellikleri göstermek için kullanılır. Program yapısı, program denetimi gibi göstermek için kullanılan Windows Workflow Foundation'da XAML (*iş akışları*). XAML bildirim temelli bir programın daha bireyselleştirilmiş davranışını tanımlayan ilgili yordam kodundan ayrı bir teknoloji yönlerini sağlar.  
  
 XAML ve LINQ to XML etkileşim kurabilir, geniş iki yolu vardır:  
  
- XAML dosyaları doğru biçimlendirilmiş olduğundan, XML, sorgulanabilen ve LINQ to XML gibi XML teknolojileri aracılığıyla yönetilebilir.  
  
- LINQ to XML sorgularında temsil ettiği için bir veri kaynağı, bu sorgular için veri bağlama WPF kullanıcı Arabirimi öğeleri için bir veri kaynağı olarak kullanılabilir.  
  
  Bu belgede, ikinci senaryo açıklanmaktadır.  
  
## <a name="data-binding-in-the-windows-presentation-foundation"></a>Veri Windows Presentation Foundation'da bağlama  
 WPF verilerini bağlama özelliklerinden birine bir veri kaynağı ile ilişkilendirmek bir kullanıcı Arabirimi öğesi sağlar. Bu basit örnekte bir <xref:System.Windows.Controls.Label> metni bir genel özelliğinin değeri bir kullanıcı tanımlı nesne sunar. WPF verilerini bağlama hakkında aşağıdaki bileşenleri kullanır:  
  
|Bileşen|Açıklama|  
|---------------|-----------------|  
|Bağlama hedefi|Veri kaynağı ile ilişkilendirilecek Kullanıcı Arabirimi öğesi. Görsel öğeler ' WPF'de türetilir <xref:System.Windows.UIElement> sınıfı.|  
|Hedef özelliği|*Bağımlılık özelliği* bağlama hedefinin bağlama veri kaynağı değerini yansıtır. Bağımlılık özellikleri tarafından doğrudan desteklenir <xref:System.Windows.DependencyObject> sınıfı, hangi <xref:System.Windows.UIElement> türetir.|  
|Bağlama kaynağı|Sunu için kullanıcı Arabirimi öğesi için sağlanan bir veya daha fazla değerler için kaynak nesne. WPF otomatik olarak kaynakları bağlama olarak şu türleri destekliyor: CLR nesneleri, ADO.NET veri nesneleri, XML verilerinin (XPath veya LINQ to XML sorgularında) veya başka bir <xref:System.Windows.DependencyObject>.|  
|Kaynak yolu|Değeri veya değerleri kümesi bağlanacağını çözümler bağlama kaynağı özelliği.|  
  
 Bağımlılık özelliği bir belirli bir kullanıcı Arabirimi öğesinin dinamik olarak hesaplanan bir özellik temsil eden WPF kavramıdır. Örneğin, varsayılan değerleri veya bir üst öğe tarafından sağlanan değerleri bağımlılık özellikleri genellikle sahiptir. Bu özel özellikleri örnekleri tarafından desteklenen <xref:System.Windows.DependencyProperty> sınıfı (ve değil olarak alanları standart özellikleri ile). Daha fazla bilgi için [bağımlılık özelliklerine genel bakış](http://msdn.microsoft.com/library/d119d00c-3afb-48d6-87a0-c4da4f83dee5).  
  
### <a name="dynamic-data-binding-in-wpf"></a>Dinamik veri bağlama ' WPF'de  
 Varsayılan olarak, veri bağlama, yalnızca hedef UI öğesi başlatıldığında gerçekleşir. Bu adlandırılır *tek seferlik* bağlama. Birçok amaç için yetersiz budur; genellikle bir veri bağlama çözüm değişiklikleri aşağıdakilerden birini kullanarak çalışma zamanında dinamik olarak dağıtılmasını gerektirir:  
  
- *Tek yönlü* bağlama otomatik olarak dağıtılmasını bir tarafı değişiklikleri neden olur. En yaygın olarak, hedef kaynak değişiklikler yansıtılır, ancak tersi bazı durumlarda yararlı olabilir.  
  
- İçinde *iki yönlü* bağlamayı kaynağında yapılan değişiklikler hedefte otomatik olarak yayılır ve hedefte yapılan değişiklikler kaynağı için otomatik olarak yayılır.  
  
  Tek veya çift yönlü gerçekleşmesi için bağlama için kaynak değişikliği bildirim mekanizması, örneğin uygulayarak uygulamalıdır <xref:System.ComponentModel.INotifyPropertyChanged> kullanarak veya arabirim bir *PropertyNameChanged* desteklenen her bir özellik için bir desen.  
  
  WPF veri bağlama hakkında daha fazla bilgi için bkz: [veri bağlama (WPF)](http://msdn.microsoft.com/library/90f79b97-17e7-40d1-abf0-3ba600ad1d7e).  
  
## <a name="dynamic-properties-in-linq-to-xml-classes"></a>LINQ to XML sınıfları dinamik özellikleri  
 Çoğu LINQ to XML sınıfları uygun WPF dinamik veri kaynağı olarak uygun değil: bazı faydalı bilgiler, yalnızca yöntemler (ve özellikleri) kullanılabilir ve bu sınıflar özelliklerinde değişiklik bildirimleri uygulamayın. LINQ to XML WPF verilerini bağlama desteklemek için bir dizi kullanıma sunan *Dinamik Özellikler*.  
  
 Varolan bir yöntem işlevselliği yinelenen özel çalışma zamanı özelliklerini ve özellikler bu dinamik özellikler olur <xref:System.Xml.Linq.XAttribute> ve <xref:System.Xml.Linq.XElement> sınıfları. Bunlar yalnızca bunları WPF için dinamik veri kaynağı olarak davranacak şekilde etkinleştirmek için bu sınıfların eklendi. Bu gereksinimi karşılamak için değişiklik bildirimleri bu dinamik özellikler uygular. Sonraki bölümde, bu dinamik özelliklerin ayrıntılı bir başvuru sağlanmıştır [LINQ to XML dinamik özellikleri](../designers/linq-to-xml-dynamic-properties.md).  
  
> [!NOTE]
>  Standart genel özelliklerin çoğu bulunan çeşitli sınıflarda <xref:System.Xml.Linq> ad alanı, tek seferlik veri bağlama için kullanılabilir. Bununla birlikte, kaynak ya da hedef dinamik olarak altında bu düzeni güncelleştirileceğini unutmayın.  
  
### <a name="accessing-dynamic-properties"></a>Dinamik özelliklerine erişme  
 Dinamik Özellikler <xref:System.Xml.Linq.XAttribute> ve <xref:System.Xml.Linq.XElement> sınıflar gibi standart özelliklere erişilemez. Örneğin, C# gibi CLR uyumlu dilde bunlar olamaz:  
  
- Doğrudan derleme zamanında erişilir. Dinamik özellikler, derleyici ve Visual Studio IntelliSense için görünmez.  
  
- .NET yansıma kullanarak bulunan veya erişilen, çalışma zamanı. Bile çalışma zamanında, temel CLR algılama özellikleri değiller.  
  
  C# içinde dinamik özellikler yalnızca çalışma zamanında tarafından sağlanan özellikleri aracılığıyla erişilebilir <xref:System.ComponentModel> ad alanı.  
  
  Buna karşılık, ancak bir XML kaynağı dinamik özellikleri basit bir gösterim aşağıdaki biçimde aracılığıyla erişilebilir:  
  
```  
<object>.<dynamic-property>  
```  
  
 Bu iki sınıf ya da doğrudan kullanılabilen bir değer ya da sonuç değeri veya değerler koleksiyonu almak için dizin ile sağlanan bir dizin oluşturucu çözümlemek için dinamik özellikler. İkinci sözdizimi formu alır:  
  
```  
<object>.<dynamic-property>[<index-value>]  
```  
  
 Daha fazla bilgi için [LINQ to XML dinamik özellikleri](../designers/linq-to-xml-dynamic-properties.md).  
  
 Dinamik bağlama WPF uygulamak için dinamik özellikler tarafından sağlanan özellikleri ile kullanılacak <xref:System.Windows.Data> ad alanı, özellikle <xref:System.Windows.Data.Binding> sınıfı.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [LINQ to XML ile WPF verilerini bağlama](../designers/wpf-data-binding-with-linq-to-xml.md)   
 [LINQ to XML dinamik özellikleri](../designers/linq-to-xml-dynamic-properties.md)   
 [WPF'de XAML](http://msdn.microsoft.com/library/5d858575-a83b-42df-ad3f-047ed2d6e3c8)   
 [Veri bağlama (WPF)](http://msdn.microsoft.com/library/90f79b97-17e7-40d1-abf0-3ba600ad1d7e)   
 [İş akışı biçimlendirmesi kullanma](http://go.microsoft.com/fwlink/?LinkId=98685)



