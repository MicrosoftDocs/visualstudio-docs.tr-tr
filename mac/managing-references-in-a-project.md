---
title: Bir projedeki başvuruları yönetme
description: Bu makalede, Mac için Visual Studio'da bir projedeki başvuruları yönetme işlemi açıklanır
author: conceptdev
ms.author: crdun
ms.date: 05/06/2018
ms.assetid: 4AD51385-B0A8-4BA7-B2D4-BF2BD167A142
ms.openlocfilehash: 54e07d3c170859405ef584b884547dad335788f3
ms.sourcegitcommit: 0a8ac5f2a685270d9ca79bb39d26fd90099bfa29
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/09/2018
ms.locfileid: "51295286"
---
# <a name="managing-references-in-a-project"></a>Bir projedeki başvuruları yönetme

Mac için Visual Studio projenize ek başvurular ekleme iki yöntem sunar:

![Proje başvuruları](media/projects-and-solutions-image10.png)

Bunlar:

* Referanslar
* Nuget'lar (eklenen Packages klasörünü aracılığıyla)

Ayrıca, Web başvuruları ve yerel başvurular da herhangi bir projesine eklenebilir.

## <a name="assembly-references"></a>Derleme başvuruları

Xamarin içindeki her bir çerçeve üzerinde bir düzine derlemeleri ile birlikte gelir. Bu derleme paketlerin hepsini projenizde varsayılan olarak başvurulur.

Projenizde başvurulan paketleri düzenlemek için kullanın **başvuruları Düzenle** başvuruları klasörü çift tıklayarak ya da seçerek görüntülenen iletişim kutusunda **başvuruları Düzenle** üzerinde bağlama Menü eylemlerinin:

![Bütünleştirilmiş kod başvuruları iletişim](media/projects-and-solutions-image11.png)

Her bir Xamarin çerçeve için kullanılabilir derlemeler hakkında daha fazla bilgi için bkz [kullanılabilir derlemeler](https://developer.xamarin.com/guides/cross-platform/advanced/available-assemblies/) Kılavuzu.

## <a name="nuget"></a>NuGet

NuGet, .NET geliştirme için en popüler paket yöneticisidir. NuGet desteği Mac için Visual Studio, projenize eklenecek paketleri aramak sağlar.

Bunu yapmak için sağ **paket** klasöründe çözüm bölmesi ve paketleri Ekle'i seçin.

Bir NuGet paketi kullanma hakkında daha fazla bilgi sağlanır [dahil olmak üzere bir NuGet paketini projenize](nuget-walkthrough.md) gözden geçirme.

## <a name="see-also"></a>Ayrıca bkz.

- [Başvuruları (Windows için Visual Studio) yönetme](/visualstudio/ide/managing-references-in-a-project)
- [Başvuru eklerken NuGet uzantı SDK'sı (Windows için Visual Studio) ile kullanma](/visualstudio/ide/adding-references-using-nuget-versus-an-extension-sdk)