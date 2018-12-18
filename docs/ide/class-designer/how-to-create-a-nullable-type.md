---
title: 'Nasıl Yapılır: Boş Değer Atanabilir Tür Oluşturma (Sınıf Tasarımcısı)'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- nullable types, Class Designer
- Class Designer [Visual Studio], nullable types
ms.assetid: 84673a89-3f6d-4668-919e-1c0f56182fe5
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 5ef167e83bc8f27a53405ef6ab7a3f9271863b4d
ms.sourcegitcommit: c57ae28181ffe14a30731736661bf59c3eff1211
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/11/2018
ms.locfileid: "38785843"
---
# <a name="how-to-create-a-nullable-type-in-class-designer"></a>Nasıl yapılır: Sınıf Tasarımcısı'nda bir boş değer atanabilir tür oluşturma

Belirli değer türleri her zaman sahip (tanımlı bir değer veya gerekir). Burada bazı alanlar herhangi bir değer atanamaz veritabanlarında yaygın yöntem budur. Örneğin, bir null değer, henüz bir değer atanmadı olduğunu belirtmek için bir veritabanı alanı atayabilirsiniz.

A *boş değer atanabilir tür* türü ve ayrıca bir null değer için tipik değerleri aralığı alır, böylece genişleten bir değer türüdür. Örneğin, bir boş değer atanabilir, `Int32`, null olarak da başlar\<Int32 > herhangi bir değer -2147483648 2147483647 için atanabilir veya bir null değer atanabilir. Bir boş değer\<bool > değerler atanabilir `True`, `False`, ya da null (hiç değer).

Boş değer atanabilir türler örnekleridir <xref:System.Nullable%601> yapısı. Boş değer atanabilir bir tür örneği her iki genel salt okunur özelliklere sahip `HasValue` ve `Value`:

-   `HasValue` tür `bool` ve değişken tanımlı bir değer içerip içermediğini belirtir. `True` değişkeni boş olmayan bir değer içeren anlamına gelir. İçin tanımlı bir değer gibi bir deyim kullanarak test edebilirsiniz `if (x.HasValue)` veya `if (y != null)`.

-   `Value` temel alınan aynı türde değil. Varsa `HasValue` olduğu `True`, `Value` anlamlı bir değer içeriyor. Varsa `HasValue` olduğu `False`, erişim `Value` bir geçersiz işlem özel durum oluşturur.

Varsayılan, boş değer atanabilir bir tür olarak bir değişken bildirdiğinizde tanımlı değer yok sahiptir (`HasValue` olan `False`), kendi temel değer türünün varsayılan değeri diğer.

Sınıf Tasarımcısı, temelindeki türe görüntüler yalnızca boş değer atanabilir bir tür görüntüler.

C# dilinde boş değer atanabilir türler hakkında daha fazla bilgi için bkz: [boş değer atanabilir türler](/dotnet/csharp/programming-guide/nullable-types/index). Visual Basic'te boş değer atanabilir türler hakkında daha fazla bilgi için bkz: [boş değer atanabilir değer türleri](/dotnet/visual-basic/programming-guide/language-features/data-types/nullable-value-types).

[!INCLUDE[note_settings_general](../../data-tools/includes/note_settings_general_md.md)]

## <a name="to-add-a-nullable-type-by-using-the-class-designer"></a>Sınıf Tasarımcısı kullanarak boş değer atanabilir bir tür eklemek için

1.  Sınıf diyagramında varolan bir sınıfı genişletebilir veya yeni bir sınıf oluşturun.

2.  Projeye bir sınıf eklemek için **sınıf diyagramı** menüsünde tıklatın **Ekle** > **sınıfı Ekle**.

3.  Sınıf şeklinin genişletme için **sınıf diyagramı** menüsünde tıklatın **genişletme**.

4.  Sınıf şekli seçin. Üzerinde **sınıf diyagramı** menüsünü tıklatın **Ekle** > **alan**. Varsayılan ada sahip yeni bir alan **alan** sınıf şeklinin ve ayrıca görünür **sınıf ayrıntıları** penceresi.

5.  İçinde **adı** sütununun **sınıf ayrıntıları** penceresi (veya kendi sınıfında Şekil), yeni alan adı geçerli ve anlamlı bir adla değiştirin.

6.  İçinde **türü** sütununun **sınıf ayrıntıları** penceresinde, aşağıdaki belirterek türü boş değer atanabilir bir tür bildirin:

    - `int?` (Visual C#)
    - `Nullable(Of Integer)` (Visual Basic)

## <a name="to-add-a-nullable-type-by-using-the-code-editor"></a>Kod Düzenleyicisi'ni kullanarak boş değer atanabilir bir tür eklemek için

1.  Projeye bir sınıf ekleyin. İçinde proje düğümünü seçin **Çözüm Gezgini**ve **proje** menüsünde tıklatın **sınıfı Ekle**.

2.  Yeni bir sınıf .cs veya .vb dosyasında yeni bir sınıf içinde bir veya daha fazla boş değer atanabilir türler için sınıf bildirimi ekleyin.

    ```csharp
    // Declare a nullable type in Visual C#:
    class Test
    {
       int? building_number = 5;
    }
    ```

    ```vb
    ' Declare a nullable type in Visual Basic:
    Class Test
       Dim buildingNumber As Nullable(Of Integer) = 5
    End Class
    ```

3.  Sınıf Görünümü'ndeki yeni sınıf simgesi Sınıf Tasarımcısı tasarım yüzeyine sürükleyin. Sınıf diyagramında sınıf şekline görünür.

4.  Sınıf şeklinin ayrıntılarını genişletin ve sınıf üyeleri fare işaretçisini taşıyın. Araç İpucu her üyesi bildirimi görüntüler.

5.  Sınıf şeklinin sağ tıklatıp **sınıf ayrıntıları**. Görüntüleyebilir veya yeni türün özelliklerinde değişiklik **sınıf ayrıntıları** penceresi.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Nullable%601>
- [Boş Değer Atanabilir Tipler](/dotnet/csharp/programming-guide/nullable-types/index)
- [Boş Değer Atanabilir Tipleri Kullanma](/dotnet/csharp/programming-guide/nullable-types/using-nullable-types)
- [Nasıl yapılır: Boş Değer Atanabilir Tipi Tanımlama](/dotnet/csharp/programming-guide/nullable-types/how-to-identify-a-nullable-type)
- [Boş Değer Atanabilen Değer Türleri](/dotnet/visual-basic/programming-guide/language-features/data-types/nullable-value-types)
