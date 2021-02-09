---
title: .NET için veri araçları
description: Veritabanlarına bağlanmak, bellekteki verileri modellemek ve Kullanıcı arabirimindeki verileri göstermek için API ve araç desteği sağlayan .NET için Visual Studio veri Araçları ' nı gözden geçirin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: overview
ms.assetid: c3175080-1dfb-4ab8-a460-92dadbb844b4
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- data-storage
- dotnet
ms.openlocfilehash: f0a9609a578deb0c7c1b39a43f45b796b66a55ce
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99858221"
---
# <a name="visual-studio-data-tools-for-net"></a>.NET için Visual Studio veri araçları

Visual Studio ve .NET birlikte, veritabanlarına bağlanmak, bellekteki verileri modellemesi ve Kullanıcı arabirimindeki verileri görüntülemek için kapsamlı API ve araç desteği sağlar. Veri erişim işlevselliği sağlayan .NET sınıfları [ADO.net](/dotnet/framework/data/adonet/index)olarak bilinir. Visual Studio 'daki veri araçlarının yanı sıra ADO.NET, birincil olarak ilişkisel veritabanlarını ve XML 'yi desteklemek için tasarlanmıştır. Bu günler, birçok NoSQL veritabanı satıcısı veya üçüncü taraf, ADO.NET sağlayıcıları sunmaktadır.

[.NET Core](/dotnet/core/) , veri kümeleri ve bunlarla ilgili türler hariç ADO.net destekler. .NET Core 'u hedefliyorsanız ve nesne ilişkisel eşleme (ORM) katmanı gerektiriyorsa, [Entity Framework Core](/ef/core/)kullanın.

Aşağıdaki diyagramda temel mimarinin basitleştirilmiş bir görünümü gösterilmektedir:

![ADO.NET Mimarisi](../data-tools/media/raddata-ado-net-architecture-diagram.png)

## <a name="typical-workflow"></a>Tipik iş akışı

Tipik iş akışı budur:

1. Yerel makinenize bir geliştirme veya test veritabanı yükler. Bkz. [veritabanı sistemlerini, araçları ve örnekleri yükleme](../data-tools/installing-database-systems-tools-and-samples.md). Azure Data Service kullanıyorsanız, bu adım gerekli değildir.

2. Visual Studio 'da veritabanına (veya hizmet ya da yerel dosya) bağlantıyı test edin. Bkz. [yeni bağlantılar ekleme](../data-tools/add-new-connections.md).

3. Seçim Yeni bir model oluşturmak ve yapılandırmak için araçları kullanın. Entity Framework göre modeller, yeni uygulamalar için varsayılan önersahiptir. Kullandığınız bir model, uygulamanın etkileşime girdiği veri kaynağıdır. Model, veritabanı veya hizmet ile uygulama arasında mantıksal olarak bulunur. Bkz. [Yeni veri kaynakları ekleme](../data-tools/add-new-data-sources.md).

4. Verileri belirttiğiniz şekilde kullanıcıya görüntüleyecek veri bağlama kodunu oluşturmak için veri **kaynakları** penceresinden Windows Forms, ASP.NET veya Windows Presentation Foundation tasarım yüzeyine veri kaynağını sürükleyin. Bkz. [Visual Studio 'daki verilere denetimleri bağlama](../data-tools/bind-controls-to-data-in-visual-studio.md).

5. İş kuralları, arama ve veri doğrulama gibi şeyler için veya temeldeki veritabanının sunduğu özel işlevlerden faydalanmak için özel kod ekleyin.

Bir model kullanmak yerine, komutları doğrudan bir veritabanına vermek için adım 3 ' ü ve bir .NET uygulamasını programlayabilirsiniz. Bu durumda ilgili belgeleri burada bulabilirsiniz: [ADO.net](/dotnet/framework/data/adonet/index). Veri **kaynağı Yapılandırma Sihirbazı 'nı** ve tasarımcılarını bellekte kendi nesnelerinizi doldurduktan sonra veri bağlama kodu oluşturmak için de kullanabileceğinizi ve bu nesnelere veri bağlamayı unutmayın.

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio'da verilere erişime](../data-tools/accessing-data-in-visual-studio.md)
