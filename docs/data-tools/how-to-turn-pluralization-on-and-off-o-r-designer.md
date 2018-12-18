---
title: 'Nasıl yapılır: çoğullaştırma üzerinde ve devre dışı bırak (O R Tasarımcısı)'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 9b693bc3-303a-40a9-97ee-9cef5ca3ae81
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 0a2d2e44efc284c38cfc450833839776effb9936
ms.sourcegitcommit: e9d1018a01af62c3dc5aeb6b325faba7e20bd496
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/28/2018
ms.locfileid: "37089389"
---
# <a name="how-to-turn-pluralization-on-and-off-or-designer"></a>Nasıl yapılır: çoğullaştırma üzerinde ve devre dışı bırak (O/R Tasarımcısı)
S veya gelen zellikleri bitiş adlara sahip veritabanı nesnelerini sürüklediğinizde, varsayılan olarak, **Sunucu Gezgini** veya **Database Explorer** üzerine [LINQ-SQL Visual Studio Araçları](../data-tools/linq-to-sql-tools-in-visual-studio2.md), Oluşturulan varlık sınıflarının adlarını çoğul için tekil değiştirilir. Bu, tek bir veri kaydı için oluşturulmuş varlık sınıfı eşlemeleri olgu daha doğru bir şekilde temsil etmek için gerçekleştirilir. Örneğin, ekleme bir `Customers` tablosu **O/R Tasarımcısı** sonuçları adlı, varlık sınıfı `Customer` sınıfı için yalnızca tek bir müşteri verilerini tutacak olduğundan.

> [!NOTE]
>  Çoğullaştırma yalnızca Visual Studio'nun İngilizce sürümünde varsayılan olarak açıktır.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

### <a name="to-turn-pluralization-on-and-off"></a>Çoğullaştırma üzerinde ve devre dışı bırakma

1.  Üzerinde **Araçları** menüsünde tıklatın **seçenekleri**.

2.  İçinde **seçenekleri** iletişim kutusunda, genişletin **veritabanı araçları**.

    > [!NOTE]
    >  Seçin **tüm ayarları göster** varsa **veritabanı araçları** düğümü görünür değil.

3.  Tıklatın **O/R Tasarımcısı**.

4.  Ayarlama **adlarının Çoğullaştırma** için **etkin** = **False** ayarlamak için **O/R Tasarımcısı** böylece sınıf adları değiştirmez .

5.  Ayarlama **adlarının Çoğullaştırma** için **etkin** = **True** eklenen nesneleri sınıf adlarını çoğullaştırma kuralları uygulamak için **O/R Tasarımcı**.

## <a name="see-also"></a>Ayrıca bkz.

- [LINQ-SQL Visual Studio Araçları](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)
- [Visual Studio'da verilere erişime](../data-tools/accessing-data-in-visual-studio.md)