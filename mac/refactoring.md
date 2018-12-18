---
title: Kodu yeniden düzenleme
description: Mac için Visual Studio'da kod düzenleme, yeniden kaynak analizini kullanarak basit yapılır.
author: conceptdev
ms.author: crdun
ms.date: 05/06/2018
ms.assetid: C7782BF3-016F-4B41-8A81-85FC540A1A8F
ms.openlocfilehash: 672c7547da9360ae3e278f783b160ffdaed05e03
ms.sourcegitcommit: 0a8ac5f2a685270d9ca79bb39d26fd90099bfa29
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/09/2018
ms.locfileid: "51296469"
---
# <a name="refactoring"></a>Yeniden Düzenle

Kodu yeniden düzenleme, yeniden düzenleme, yeniden yapılandırmayı ve kodu Genel davranışını değişmeyen sağlarken mevcut kodu açıklamak için bir yoldur.

Yeniden düzenleme, veya herhangi başka bir geliştirici ya koda başvurabilir kullanıcı için fazla kullanım, okunabilir ve sürdürülebilir yaparak daha iyi bir kod tabanına üretir.

Roslyn, Microsoft'un açık kaynak .NET derleyici platformu ile tümleştirme Mac için Visual Studio için daha fazla yeniden düzenleme işlemleri sağlar.

## <a name="renaming"></a>Yeniden adlandırma

*Yeniden Adlandır* komutu yeniden düzenleme tüm kod tanımlayıcısı (örneğin, bir sınıf adı, özellik adı vb.) tüm tanımlayıcı örneklerini bulun ve bunları değiştirmek için kullanılabilir. Bir sembol yeniden adlandırmak için sağ tıklayın ve seçin **yeniden düzenleyin > Yeniden Adlandır**, veya **Cmd + R** anahtar bağlama:

![Menü öğesini yeniden adlandırma](media/refactoring-renaming1.png)

Bu, simge ve tüm başvuruları vurgular. Yeni bir ad yazarak başlattığınızda kodunuzdaki tüm başvurularını otomatik olarak değiştirir ve yeniden adlandırma, tamamlama tuşlarına basarak sinyal verebilirsiniz **Enter**:

![Yeniden adlandırma ve tanımlayıcı](media/refactoring-renaming2.png)

## <a name="context-actions"></a>Bağlam eylemleri

Bağlam Eylemler, herhangi bir C# kod İnceleme olanak sağlar ve tüm olası yeniden düzenleme seçeneklerini görmek.

**Çözmek** ve **yeniden düzenleme** bağlam öğeleri tek bir birleştirilmiş *hızlı düzeltme...*  kullanılabilir tüm bağlam Eylemler ile sağlayacak öğesi:

![İçerik öğeleri görüntüle](media/refactoring-context-action.png)

Herhangi bir bağlam eylemleri üzerine geldiğinizde, bir önizleme ne eklenecek veya kodunuz içinden kaldırıldı sağlar.

Alternatif olarak, basabilirsiniz **seçeneği + Enter** kodunuzdaki herhangi bir yeri:

![Seçeneği girin içerik öğeleri](media/refactoring-image2a.png)

Bu seçenekleri etkinleştirmek için seçmelisiniz *açık dosyaların kaynak analizini etkinleştir* seçeneklerinde **Mac için Visual Studio > Tercihler > Metin Düzenleyicisi > kaynak çözümleme**:

![Kaynak analizi etkinleştirme](media/refactoring-options.png)

Etkin veya devre dışı göz atarak önerilebilir, 100'den fazla olası eylemler vardır **Mac için Visual Studio > Tercihler > kaynak çözümleme > C# > kod eylemleri** seçerek veya yanındaki kutuyu seçimini Eylem:

![C# kaynak çözümleme eylemleri](media/refactoring-image3a.png)

### <a name="common-context-actions"></a>Genel bağlam eylemleri

En sık kullanılan bağlam eylemlerin bazıları aşağıda açıklanmıştır.

#### <a name="extract-method"></a>Ayıklama metodu

Ayıklama yöntemi yeniden düzenleme işlemi, varolan bir üye kodda seçim çekip çıkararak yeni bir yöntem oluşturmanıza olanak sağlar. Bu eylem, iki şey yapar:

* Seçilen kod içeren yeni bir yöntem oluşturur
* Seçilen kod olduğu yerde yeni yöntemi çağırır.

##### <a name="example"></a>Örnek

1. Aşağıdaki kodu ekleyin:

```csharp
    class MainClass
    {

        double CalculatePyramidVolume(double baseArea, double height)
        {

            double volume = (baseArea * height) / 3;

            return volume;
        }
    }
```

2. Satırı Vurgula `double volume = (baseArea * height) / 3;`, sağ tıklayın ve seçin **yeniden düzenleyin > yöntemi ayıklama**.

3. Yeni yöntemi kodunuzu nereye yerleştirileceğini seçmek için ok tuşlarını kullanın.

#### <a name="encapsulate-field"></a>Alanı kapsülleme

Alan yalıtma işlemi, mevcut bir alandan bir özellik oluşturmanıza olanak sağlar ve yeni oluşturulan özellik başvurmak için kodunuzu güncelleştirir. Alan kapsülleyen bir özellik oluşturarak, doğrudan erişim, ortak alan için diğer nesneler üzerinde değişiklik yapamazsınız, yani engelleyerek.

Bu eylem aşağıdakileri yapın:

* Özel erişim değiştiricisi değiştirir.
* (Bu durumda yalnızca bir alıcı oluşturun salt okunur alan olmadığı sürece), alıcı ve Ayarlayıcıyı alanın oluşturur.

## <a name="source-analysis"></a>Kaynak analizi

Kaynak analizi, kodunuzun çalışma sırasında altı çizili olası hataları ve stili ihlalleri tarafından analiz ederek bağlam eylem olarak otomatik sağlama giderir.

Metin Düzenleyicisi sağ tarafında kaydırma çubuğu görüntüleyerek herhangi bir zamanda tüm herhangi bir dosya için kaynak analiz sonuçlarını görüntüleyebilirsiniz:

![Kaynak analizi kenar çubuğu](media/refactoring-image4a.png)

Üst daireye tıklayarak, her öneri yüksek öneme sahip sorunlar ilk gösteren yineleyebilirsiniz. Bir tek tek sonuç veya satır geldiğinizde bağlam eylemleri sabit sorunu görüntüler:

![Kaynak analizi öğesi](media/refactoring-image5.png)

## <a name="see-also"></a>Ayrıca bkz.

- [Hızlı Eylemler (Windows için Visual Studio)](/visualstudio/ide/quick-actions)
- [(Windows için Visual Studio) kodu yeniden düzenleyin](/visualstudio/ide/refactoring-in-visual-studio)