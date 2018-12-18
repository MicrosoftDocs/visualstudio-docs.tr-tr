---
title: N katmanlı veri uygulamalarına genel bakış | Microsoft Docs
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
- presentation tier
- middle tier
- data tier
- n-tier applications, about n-tier applications
ms.assetid: 1020581d-eaaa-41a2-aca4-bf4c212895f6
caps.latest.revision: 29
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 8a5f6c89f6b71ecd2902877757f7d852c0e51088
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49852927"
---
# <a name="n-tier-data-applications-overview"></a>N Katmanlı Veri Uygulamalarına Genel Bakış
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
N-katmanı * veri uygulamaları, birden çok ayrılmış veri uygulama *katmanları*. "Dağıtılmış uygulamalar" ve "çok katmanlı uygulamalar" olarak da bilinir, n katmanlı uygulamalar, istemci ve sunucu arasında dağıtılan farklı katmanlara bir işlem ayırın. Verilere erişen uygulamalar geliştirirken, uygulamayı oluşturan çeşitli katmanları arasında NET bir ayrım olmalıdır.  
  
 Tipik bir n katmanlı uygulamanın sunu katmanı, bir orta katman ve bir veri katmanı içerir. N katmanlı uygulamada çeşitli Katmanları ayırmak için en kolay yolu, uygulamanıza dahil etmek istediğiniz her bir katman için ayrı projeler oluşturmaktır. Örneğin, sunu katmanı Orta katmanda bulunan bir sınıf kitaplığı veri erişim mantığına olabilir ancak bir Windows Forms uygulaması olabilir. Buna ek olarak, sunu katmanı Orta katmanda bir hizmet gibi bir hizmet aracılığıyla veri erişim mantığına iletişim. Uygulama bileşenleri ayrı katmanlara ayırmak Bakım ve uygulama'nın ölçeklenebilirliğini artırır. Bunu, tüm çözümü yeniden tasarlamanıza gereksinimi olmadan tek bir katmana uygulanabilen yeni teknolojilerin daha kolay benimsenmesini sağlayarak yapar. Ayrıca, n katmanlı uygulamalar genellikle hassas bilgileri Orta sunu katmanı yalıtımdan barındıran katman depolayın.  
  
 Visual Studio, geliştiricilerin n katmanlı uygulamalar oluşturmasına yardımcı olmak için çeşitli özellikler içerir:  
  
-   [Oluşturma ve yazılan veri kümelerini düzenleme](../data-tools/creating-and-editing-typed-datasets.md) sağlayan bir **DataSet projesi** dataset (veri varlık katmanı) ayrı olanak tanıyan özellik ve `TableAdapter`s (veri erişim katmanı) ayrık içine projeleri.  
  
-   [LINQ to SQL araçlarını Visual Studio'da](../data-tools/linq-to-sql-tools-in-visual-studio2.md) ayrı ad alanında DataContext ve veri sınıfları oluşturmak için ayarları sağlar. Bu mantıksal ayrılığı veri varlık katmanı ve veri erişimi sağlar.  
  
-   [LINQ to SQL](http://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655) sağlar <xref:System.Data.Linq.Table%601.Attach%2A> yönteminin bir uygulamada farklı katmanlarından gelen DataContext bir araya getirmenize olanak tanıyan. Daha fazla bilgi için [N katmanı ve uzak uygulamalarla LINQ-SQL](http://msdn.microsoft.com/library/854a1cdd-53cb-45f5-83ca-63962a9b3598).  
  
## <a name="presentation-tier"></a>Sunu katmanı  
 *Sunu katmanı* kullanıcıların uygulamayla etkileşim katmanı gösterir. Ek uygulama mantığı genellikle de içerir. Tipik bir sunu katmanı bileşenleri şunları içerir:  
  
- Veri bileşenleri gibi bağlama <xref:System.Windows.Forms.BindingSource> ve <xref:System.Windows.Forms.BindingNavigator>.  
  
- Verilerin temsillerini gibi nesne [LINQ to SQL](http://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655) sunu katmanı kullanmak için varlık sınıfları.  
  
  Genellikle sunu katmanına bir hizmet başvurusu kullanarak orta katman erişir (örneğin, bir [Windows Communication Foundation Hizmetleri ve Visual Studio'da WCF Veri Hizmetleri](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md) uygulama). Sunu katmanı veri katmanı doğrudan erişimi yoktur. Sunu katmanı, orta katman veri erişim bileşeni yoluyla veri katmanı ile iletişim kurar.  
  
## <a name="middle-tier"></a>Orta katman  
 *Orta katman* sunu katmanı ve veri katmanı katman kullanın birbirleri ile iletişim kurmak için. Tipik bir orta katman bileşenleri şunları içerir:  
  
- İş kuralları ve veri doğrulama gibi iş mantığı.  
  
- Bileşenleri ve aşağıdaki gibi bir mantıksal veri erişim:  
  
  -   [TableAdapter bağdaştırıcıları](http://msdn.microsoft.com/library/09416de9-134c-4dc7-8262-6c8d81e3f364) ve [DataAdapters ve DataReaders](http://msdn.microsoft.com/library/cc952ca2-ec19-46ab-9189-15174b52cb74).  
  
  -   Verilerin temsillerini gibi nesne [LINQ to SQL](http://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655) varlık sınıfları.  
  
  -   Kimlik doğrulama, yetkilendirme ve kişiselleştirme gibi ortak uygulama hizmetleri.  
  
  Özellikleri ve teknolojileri Visual Studio'da bulunan ve burada, n katmanlı bir uygulama orta katman için uygun olmayabilir aşağıdaki çizimde gösterilmektedir.  
  
  ![Orta katman bileşenleri](../data-tools/media/ntiermid.png "NtierMid")  
  Orta katman  
  
  Orta katman veri katmanına genellikle bir veri bağlantısı kullanarak bağlanır. Bu veri bağlantısının veri erişim bileşeni genellikle depolanır.  
  
## <a name="data-tier"></a>Veri katmanı  
 *Veri katmanı* temel bir uygulamanın verilerini depolayan sunucudur (örneğin, çalıştıran bir sunucuya [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]).  
  
 Aşağıda, özellikler ve Visual Studio içinde kullanılabilir ve bunlar n katmanlı bir uygulama için veri katmanı nerelerde teknolojiler gösterilmektedir.  
  
 ![Veri katmanı bileşenlerini](../data-tools/media/ntierdatatier.png "ntierdatatier")  
Veri katmanı  
  
 Veri katmanı, sunu katmanı istemcide doğrudan erişilemez. Bunun yerine, orta katman veri erişim bileşeni, sunu ve veri katmanları arasındaki iletişim için kullanılır.  
  
## <a name="help-for-n-tier-development"></a>N katmanlı geliştirme için Yardım  
 Aşağıdaki konular, n katmanlı uygulamalar ile çalışma hakkında bilgi sağlar:  
  
 [Veri kümeleri ile TableAdapter’ları farklı projelere ayırma](../data-tools/separate-datasets-and-tableadapters-into-different-projects.md)  
  
 [İzlenecek Yol: N Katmanlı Bir Veri Uygulaması Oluşturma](../data-tools/walkthrough-creating-an-n-tier-data-application.md)  
  
 [İzlenecek yol: Bir N katmanlı bir veri uygulamasına doğrulama ekleme](http://msdn.microsoft.com/library/b35d072c-31f0-49ba-a225-69177592c265)  
  
 [LINQ to SQL ile N Katmanı ve Uzak Uygulamalar](http://msdn.microsoft.com/library/854a1cdd-53cb-45f5-83ca-63962a9b3598)  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Data.Linq.ITable.Attach%2A>   
 [İzlenecek yol: bir N katmanlı veri uygulaması oluşturma](../data-tools/walkthrough-creating-an-n-tier-data-application.md)   
 [Hiyerarşik güncelleştirme](../data-tools/hierarchical-update.md)   
 [Visual Studio'da veri kümesi araçları](../data-tools/dataset-tools-in-visual-studio.md)   
 [Visual Studio'da verilere erişime](../data-tools/accessing-data-in-visual-studio.md)

