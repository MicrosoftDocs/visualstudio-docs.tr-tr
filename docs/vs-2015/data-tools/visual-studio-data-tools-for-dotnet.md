---
title: .NET için Visual Studio veri araçları | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c3175080-1dfb-4ab8-a460-92dadbb844b4
caps.latest.revision: 22
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 841311af90ddf4bedfb9d055e5764068cdc71632
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49859713"
---
# <a name="visual-studio-data-tools-for-net"></a>.NET için Visual Studio veri araçları
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio ve .NET Framework birlikte kapsamlı API ve araç veritabanlarına bağlanma, bellekte veri modelleme ve veri kullanıcı arabiriminde görüntülemek için desteği sağlar.  Veri erişimi işlevleri sağlayan .NET Framework sınıfları olarak bilinen [ADO.NET](https://msdn.microsoft.com/library/e80y5yhx\(v=vs.110\).aspx). Visual Studio'da araçları verileriyle birlikte bir ADO.NET, başlangıçta öncelikli olarak ilişkisel veritabanı ve XML desteklemek için tasarlanmıştır. Bugünlerde çoğu NoSQL veritabanı satıcıların veya üçüncü taraflar, ADO.NET sağlayıcılar sunar.  
  
 Visual Studio 2015 güncelleştirme 2, en son güncelleştirmeleri içeren [SQL Server veri Araçları](https://msdn.microsoft.com/library/hh272686\(v=vs.103\).aspx), azure'daki en son özelliklere yönelik desteği etkinleştiren [SQL veritabanı](https://azure.microsoft.com/en-us/services/sql-database/) ve [SQL Server 2016](https://www.microsoft.com/en-us/server-cloud/products/sql-server-2016/). [.NET core](https://www.dotnetfoundation.org/netcore) ADO.NET veri kümeleri ve ilgili türler hariç destekler. .NET Core'u hedefleyen ve bir nesne ilişkisel eşleme (ORM) katmanı gerektirir, kullanmanız [Entity Framework Core](https://msdn.microsoft.com/data/ef.aspx).  
  
 Aşağıdaki diyagram, temel mimarisinin basitleştirilmiş bir görünümünü gösterir:  
  
 ![ADO.NET mimarisini](../data-tools/media/raddata-ado-net-architecture-diagram.png "raddata ADO.NET mimarisi diyagramı")  
  
 Tipik iş akışı şudur:  
  
1. Geliştirme veya test veritabanı yerel makinenize yükleyin. Bkz: [veritabanı sistemleri, araçları ve örnek yükleme](../data-tools/installing-database-systems-tools-and-samples.md). Bir Azure veri hizmeti kullanıyorsanız, bu adım gerekli değildir.  
  
2. Veritabanı (veya hizmet veya yerel dosya) bağlantı, Visual Studio'da test edin. Bkz: [yeni bağlantı ekleme](../data-tools/add-new-connections.md).  
  
3. (İsteğe bağlı) Oluştur ve yeni bir modeli yapılandırmak için araçları kullanın. Entity Framework tabanlı yeni uygulamalar için varsayılan öneriyi modelleridir. Modelin hangi birini kullanın, uygulama ile etkileşime giren veri kaynağıdır. Modeli, veritabanı veya hizmet ve uygulama arasında mantıksal olarak bulunur.  Bkz: [yeni veri kaynağı ekleme](../data-tools/add-new-data-sources.md).  
  
4. Veri kaynağından sürükleyin **veri kaynakları** verilerin belirttiğiniz şekilde kullanıcıya görüntülenecek veri bağlama kodunu oluşturmak için bir Windows Forms, ASP.NET veya Windows Presentation Foundation tasarım yüzeyine penceresi. Bkz: [Visual Studio'da verilere denetimler bağlama](../data-tools/bind-controls-to-data-in-visual-studio.md).  
  
5. Temel alınan veritabanına gösteren özel işlevsellikten yararlanmak için veya iş kuralları, arama ve veri doğrulama gibi şeyler için özel kod ekleyin.  
  
   3. adımına geçin ve sorunu komutları doğrudan bir model kullanmak yerine bir veritabanı için bir .NET uygulaması programı. Bu durumda, ilgili belgeleri burada bulabilirsiniz: [ADO.NET](https://msdn.microsoft.com/library/e80y5yhx\(v=vs.110\).aspx). Tasarımcılar ve veri kaynağı Yapılandırma Sihirbazı, bellek ve bu nesnelere veri bağlama UI denetimleri kendi nesnelerinizi doldurmanız veri bağlama kodunu oluşturmasını kullanmaya devam edebilirsiniz olduğunu unutmayın.  
  
## <a name="in-this-section"></a>Bu bölümde  
  
-   [ADO.NET kullanarak basit veri uygulaması oluşturma](../data-tools/create-a-simple-data-application-by-using-adonet.md)  
  
-   [Yeni bağlantı ekleme](../data-tools/add-new-connections.md)  
  
-   [Yeni veri kaynağı ekleme](../data-tools/add-new-data-sources.md)  
  
-   [Visual Studio'daki Varlık Veri Modeli Araçları](../data-tools/entity-data-model-tools-in-visual-studio.md)  
  
-   [Visual Studio'daki veri kümesi araçları](../data-tools/dataset-tools-in-visual-studio.md)  
  
-   [Visual Studio'daki LINQ to SQL Araçları](../data-tools/linq-to-sql-tools-in-visual-studio2.md)  
  
-   [Visual Studio'da verilere denetimler bağlama](../data-tools/bind-controls-to-data-in-visual-studio.md)  
  
-   [Veri erişimi hatalarında sorun giderme için ek kaynaklar](../data-tools/additional-resources-for-troubleshooting-data-access-errors.md)  
  
-   [Visual Studio'da Windows Communication Foundation Hizmetleri ve WCF Veri Hizmetleri](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)  
  
-   [Visual Studio'da veritabanları ve veri katmanı uygulamaları oluşturma ve yönetme](../data-tools/creating-and-managing-databases-and-data-tier-applications-in-visual-studio.md)  
  
-   [Veri erişimi hatalarında sorun giderme için ek kaynaklar](../data-tools/additional-resources-for-troubleshooting-data-access-errors.md)  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual Studio'da verilere erişime](../data-tools/accessing-data-in-visual-studio.md)







