---
title: N Katmanlı Veri Uygulamalarına Genel Bakış
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- presentation tier
- middle tier
- data tier
- n-tier applications, about n-tier applications
ms.assetid: 1020581d-eaaa-41a2-aca4-bf4c212895f6
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 3f9cf8c6a75e5f2a517931bf0fd858ea8f8f860c
ms.sourcegitcommit: c9a01c599ce19a5845605b3b28c0229fd0abb93f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2018
ms.locfileid: "52281751"
---
# <a name="n-tier-data-applications-overview"></a>N katmanlı veri uygulamalarına genel bakış
*N katmanlı* veri uygulamalardır içinde birden çok ayrılmış veri uygulamaları *katmanları*. "Dağıtılmış uygulamalar" ve "çok katmanlı uygulamalar" olarak da bilinir, n katmanlı uygulamalar, istemci ve sunucu arasında dağıtılan farklı katmanlara bir işlem ayırın. Verilere erişen uygulamalar geliştirirken, uygulamayı oluşturan çeşitli katmanları arasında NET bir ayrım olmalıdır.

Tipik bir n katmanlı uygulamanın sunu katmanı, bir orta katman ve bir veri katmanı içerir. N katmanlı uygulamada çeşitli Katmanları ayırmak için en kolay yolu, uygulamanıza dahil etmek istediğiniz her bir katman için ayrı projeler oluşturmaktır. Örneğin, sunu katmanı Orta katmanda bulunan bir sınıf kitaplığı veri erişim mantığına olabilir ancak bir Windows Forms uygulaması olabilir. Buna ek olarak, sunu katmanı Orta katmanda bir hizmet gibi bir hizmet aracılığıyla veri erişim mantığına iletişim. Uygulama bileşenleri ayrı katmanlara ayırmak Bakım ve uygulama'nın ölçeklenebilirliğini artırır. Bunu, tüm çözümü yeniden tasarlamanıza gereksinimi olmadan tek bir katmana uygulanabilen yeni teknolojilerin daha kolay benimsenmesini sağlayarak yapar. Ayrıca, n katmanlı uygulamalar genellikle hassas bilgileri Orta sunu katmanı yalıtımdan barındıran katman depolayın.

Visual Studio, geliştiricilerin n katmanlı uygulamalar oluşturmasına yardımcı olmak için çeşitli özellikler içerir:

-   Veri kümesi sağlayan bir **DataSet projesi** dataset (veri varlık katmanı) ve TableAdapters öğelerini ayrı olanak tanıyan özellik (veri erişim katmanı) farklı projelere.

-   [LINQ to SQL araçları Visual Studio'da](../data-tools/linq-to-sql-tools-in-visual-studio2.md) ayrı ad alanında DataContext ve veri sınıfları oluşturmak için ayarları sağlar. Bu mantıksal ayrılığı veri varlık katmanı ve veri erişimi sağlar.

-   [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index) sağlar <xref:System.Data.Linq.Table%601.Attach%2A> yönteminin bir uygulamada farklı katmanlarından gelen DataContext bir araya getirmenize olanak tanıyan. Daha fazla bilgi için [N katmanı ve uzak uygulamalarla LINQ-SQL](/dotnet/framework/data/adonet/sql/linq/n-tier-and-remote-applications-with-linq-to-sql).

## <a name="presentation-tier"></a>Sunu katmanı
*Sunu katmanı* kullanıcıların uygulamayla etkileşim katmanı gösterir. Ek uygulama mantığı genellikle de içerir. Tipik bir sunu katmanı bileşenleri şunları içerir:

-   Veri bileşenleri gibi bağlama <xref:System.Windows.Forms.BindingSource> ve <xref:System.Windows.Forms.BindingNavigator>.

-   Verilerin temsillerini gibi nesne [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index) sunu katmanı kullanmak için varlık sınıfları.

Genellikle sunu katmanına bir hizmet başvurusu kullanarak orta katman erişir (örneğin, bir [Windows Communication Foundation Hizmetleri ve Visual Studio'da WCF Veri Hizmetleri](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md) uygulama). Sunu katmanı veri katmanı doğrudan erişimi yoktur. Sunu katmanı, orta katman veri erişim bileşeni yoluyla veri katmanı ile iletişim kurar.

## <a name="middle-tier"></a>Orta katman
*Orta katman* sunu katmanı ve veri katmanı katman kullanın birbirleri ile iletişim kurmak için. Tipik bir orta katman bileşenleri şunları içerir:

-   İş kuralları ve veri doğrulama gibi iş mantığı.

-   Bileşenleri ve aşağıdaki gibi bir mantıksal veri erişim:

    -   [TableAdapter bağdaştırıcıları](create-and-configure-tableadapters.md) ve [DataAdapters ve DataReaders](/dotnet/framework/data/adonet/dataadapters-and-datareaders).

    -   Verilerin temsillerini gibi nesne [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index) varlık sınıfları.

    -   Kimlik doğrulama, yetkilendirme ve kişiselleştirme gibi ortak uygulama hizmetleri.

Özellikleri ve teknolojileri Visual Studio'da bulunan ve burada, n katmanlı bir uygulama orta katman için uygun olmayabilir aşağıdaki çizimde gösterilmektedir.

![Orta katman bileşenleri](../data-tools/media/ntiermid.png) orta katman

Orta katman veri katmanına genellikle bir veri bağlantısı kullanarak bağlanır. Bu veri bağlantısının veri erişim bileşeni genellikle depolanır.

## <a name="data-tier"></a>Veri katmanı
*Veri katmanı* temelde (örneğin, SQL Server çalıştıran bir sunucu) bir uygulamanın verilerini depolayan sunucusudur.

Aşağıda, özellikler ve Visual Studio içinde kullanılabilir ve bunlar n katmanlı bir uygulama için veri katmanı nerelerde teknolojiler gösterilmektedir.

![Veri katmanı bileşenlerini](../data-tools/media/ntierdatatier.png) veri katmanı

Veri katmanı, sunu katmanı istemcide doğrudan erişilemez. Bunun yerine, orta katman veri erişim bileşeni, sunu ve veri katmanları arasındaki iletişim için kullanılır.

## <a name="help-for-n-tier-development"></a>N katmanlı geliştirme için Yardım
Aşağıdaki konular, n katmanlı uygulamalar ile çalışma hakkında bilgi sağlar:

[Veri kümeleri ile TableAdapter’ları farklı projelere ayırma](../data-tools/separate-datasets-and-tableadapters-into-different-projects.md)

[İzlenecek yol: bir n katmanlı veri uygulaması oluşturma](../data-tools/walkthrough-creating-an-n-tier-data-application.md)

[N katmanı ve uzak uygulamalarla LINQ-SQL](/dotnet/framework/data/adonet/sql/linq/n-tier-and-remote-applications-with-linq-to-sql)

## <a name="see-also"></a>Ayrıca bkz.

- [İzlenecek yol: bir n katmanlı veri uygulaması oluşturma](../data-tools/walkthrough-creating-an-n-tier-data-application.md)
- [Hiyerarşik güncelleştirme](../data-tools/hierarchical-update.md)
- [Visual Studio'daki veri kümesi araçları](../data-tools/dataset-tools-in-visual-studio.md)
- [Visual Studio'da verilere erişime](../data-tools/accessing-data-in-visual-studio.md)