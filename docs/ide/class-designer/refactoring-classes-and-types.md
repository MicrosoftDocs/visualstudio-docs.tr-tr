---
title: Sınıfları ve türleri Sınıf Tasarımcısı'nda taşıyın ve yeniden adlandırma
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.ClassDesigner.OverrideMembersDialog
helpviewer_keywords:
- members, overriding
- overriding members
- classes [Visual Studio], refactoring
- type members, overriding
- refactoring, types
- types [Visual Studio], refactoring
- Class Designer [Visual Studio], refactoring classes
- refactoring, classes
ms.assetid: dcf07bb4-fa3b-4224-9dec-566fd924a8ce
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0d5683f28150089335f04e9cf2e5274ad3ff413c
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49922529"
---
# <a name="refactor-classes-and-types-in-class-designer"></a>Sınıfları ve Sınıf Tasarımcısı'nda türleri yeniden düzenleme

Kodunu yeniden düzenlediğinizde, daha kolay anlamanız, bakımını yapmak ve daha verimli iç yapısını ve nesnelerini şeklini değiştirerek tasarlanan, dış davranışı. Sınıf Tasarımcısı ve sınıf Ayrıntıları penceresinde yapmanız gereken iş miktarını azaltmaya yönelik düzenlediğinizde, hataları giriş olasılığını kullanın C#, Visual Basic veya C++, Visual Studio projenize kodu.

> [!NOTE]
> Proje kaynak kodu denetiminde olması ve seçeneği işaretlenmezse, başvurulan bir projedir ve kendi dosya diskte salt okunur olarak işaretlenmiş olduğundan proje dosyaları salt okunur olabilir. Bu durumlardan biriyle projesinde çalışırken, projenin durumuna bağlı olarak çalışmanızı kaydetmek için çeşitli yollar sunulur. Bu, kodu yeniden düzenleme ve doğrudan düzenleme gibi başka bir yolla değiştirin kod geçerlidir.

## <a name="common-tasks"></a>Ortak görevler

|Görev|Destekleyici İçerik|
|----------| - |
|**Sınıfları yeniden düzenleme:** sınıfı kısmi sınıflara bölme veya soyut temel sınıf uygulamak için yeniden düzenleme işlemleri kullanabilirsiniz.|-   [Nasıl yapılır: sınıfı kısmi sınıflara bölme](how-to-split-a-class-into-partial-classes.md)|
|**Arabirimleri ile çalışma:** Sınıf Tasarımcısı'nda, uygulayabilirsiniz bir arabirim sınıf diyagramı üzerinde arabirim yöntemleri için kod sağlayan bir sınıf bağlanarak.|-   [Nasıl yapılır: arabirimi uygulama](how-to-implement-an-interface.md)|
|**Türler, tür üyeleri ve parametreleri yeniden düzenleme:** Sınıf Tasarımcısı'nı kullanarak, türleri yeniden adlandırabilir, tür üyeleri geçersiz kılma veya bir türden diğerine taşıyabilirsiniz. Boş değer atanabilir türler de oluşturabilirsiniz.|-   [Yeniden adlandırma türler ve tür üyeleri](#rename-types-and-type-members)<br />-   [Tür üyeleri bir türden diğerine taşıma](#move-type-members-from-one-type-to-another)<br />-   [Nasıl yapılır: boş değer atanabilir tür oluşturma](how-to-create-a-nullable-type.md)|

## <a name="rename-types-and-type-members"></a>Yeniden adlandırma türler ve tür üyeleri

Sınıf Tasarımcısı'nda, bir tür veya üye türü sınıf diyagramında veya yeniden adlandırabilirsiniz **özellikleri** penceresi. İçinde **sınıf ayrıntıları** penceresinde üyesi ancak bir tür adını değiştirebilirsiniz. Bir tür veya tür üyesi yeniden adlandırılması, tüm windows ve eski adı burada görünen kod konumlarını yayar.

### <a name="rename-in-the-class-designer"></a>Sınıf Tasarımcısı'nda yeniden adlandır

1. Sınıf diyagramında türe veya üyeye seçin ve adını seçin.

     Üyenin adı düzenlenebilir hale gelir.

2. Türe veya üyeye türü için yeni adı yazın

### <a name="rename-in-the-class-details-window"></a>Sınıf Ayrıntıları penceresinde yeniden adlandır

1. Görüntülenecek **sınıf ayrıntıları** penceresinde tür veya tür üyesi sağ tıklayıp **sınıf ayrıntıları**.

     **Sınıf ayrıntıları** penceresi görüntülenir.

2. İçinde **adı** sütun türü üyesinin adını değiştirme

3. Hücreden odağı taşımak için basın **Enter** anahtar veya uzak bir hücreye tıklayın.

    > [!NOTE]
    > İçinde **sınıf ayrıntıları** penceresinde üyesi ancak bir tür adını değiştirebilirsiniz.

### <a name="rename-in-the-properties-window"></a>Özellikler penceresinde yeniden adlandır

1. Sınıf diyagramında veya **sınıf ayrıntıları** penceresinde, türe veya üyeye sağ tıklayın ve ardından **özellikleri**.

     **Özellikleri** penceresi görüntülenir ve türü veya tür üyesi için özellikleri görüntüler.

2. İçinde **adı** özelliği türü adını değiştirin veya üye türü.

     Tüm windows ve eski adı burada görünen kod konumlarını geçerli projede yeni adı yayar.

## <a name="move-type-members-from-one-type-to-another"></a>Tür üyeleri bir türden diğerine taşıma

Kullanarak **Sınıf Tasarımcısı**, başka bir tür için tür üyesi bir türden diğerine taşıyabilirsiniz. Her iki tür geçerli bir sınıf diyagramında görünür olmalıdır.

1. Tasarım yüzeyinde görünür olan bir tür, başka bir türe taşıyın ve ardından istediğiniz üyeye sağ tıklayarak **Kes**.

2. Hedef türüne sağ tıklayıp **Yapıştır**.

     Özellik kaynak türden kaldırılır ve hedef türünde görünür.

## <a name="see-also"></a>Ayrıca bkz.

- [Türleri ve İlişkileri Görüntüleme](viewing-types-and-relationships.md)
- [Sınıfları ve türleri tasarlama](designing-classes-and-types.md)