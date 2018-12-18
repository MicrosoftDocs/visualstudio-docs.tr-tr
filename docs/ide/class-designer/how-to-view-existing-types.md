---
title: 'Nasıl Yapılır: Varolan Türleri Görüntüleme (Sınıf Tasarımcısı)'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.classdesigner.CannotShowBaseType
helpviewer_keywords:
- types [Visual Studio], visualizing
- types [Visual Studio], class diagrams
- class diagrams, types
ms.assetid: de110a4e-5b51-4a40-9dee-615df4d8f999
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6f477f64188c9592db65d0a82c8a1b8b3ec5b776
ms.sourcegitcommit: 4c0db930d9d5d8b857d3baf2530ae89823799612
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/10/2018
ms.locfileid: "33956659"
---
# <a name="how-to-view-existing-types-in-class-designer"></a>Nasıl yapılır: Sınıf Tasarımcısı'nda varolan türleri görüntüleme

Mevcut bir türle ve üyelerini görmek için bir sınıf diyagramı şeklini ekleyin.

Yerel ve başvurulan türleri görebilirsiniz. Yerel bir tür o anda açık olan projede mevcuttur ve okunur/yazılır. Başvurulan tür başka bir projede ya da başvurulan bir derlemede bulunur ve salt okunur özelliktedir.

Sınıf diyagramları yeni türlerinde tasarlamak için bkz: [nasıl yapılır: Sınıf Tasarımcısı kullanarak türleri oluşturma](how-to-create-types.md).

## <a name="to-see-types-in-a-project-on-a-class-diagram"></a>Projedeki türleri bir sınıf diyagramı üzerinde görmek için

1.  Bir projeye ait **Çözüm Gezgini**, mevcut bir sınıf diyagramı (.cd) dosyasını açın. Ya da hiçbir sınıf diyagramı yoksa, projeye yeni bir sınıf diyagramı ekleyin. Bkz: [nasıl yapılır: projelere sınıf diyagramları ekleme](how-to-add-class-diagrams-to-projects.md).

2.  Projesi ile **Çözüm Gezgini**, kaynak kodu dosyasının sınıf diyagramına sürükleyin.

    > [!NOTE]
    > Çözümünüzün birden çok uygulama arasında kod paylaşan proje varsa, bir sınıf diyagramı dosyaları veya kod yalnızca bu kaynaklardan sürükleyebilirsiniz:
    >
    > - Diyagramı içeren uygulama projesi
    > - Uygulama projesi tarafından alınan paylaşılan bir proje
    > - Başvurulan bir proje
    > - Bir derleme

    Kaynak kodu dosyasında tanımlı türleri temsil eden şekiller, diyagram üzerinde dosyayı sürüklediğiniz konumda görünür.

Proje düğümünde bir veya daha fazla türleri sürükleyerek projede türlerini görüntüleyebilirsiniz **sınıf görünümü** sınıf diyagramı için.

> [!TIP]
> Varsa **sınıf görünümü** açık, açık değil **sınıf görünümü** gelen **Görünüm** menüsü.

Varsayılan konumlara diyagramda türlerini görüntülemek için bir veya daha fazla türlerinde seçin **sınıf görünümü**, seçili türleri sağ tıklatın ve seçin **görünüm sınıfı diyagramı**.

> [!NOTE]
> Türü içeren bir kapalı sınıf diyagramı projede zaten varsa, sınıf diyagramı açılarak tür şeklini görüntüler. Ancak, hiçbir sınıf diyagramı içeren türü projesinde varsa **Sınıf Tasarımcısı** projede yeni bir sınıf diyagramı oluşturur ve türü görüntülenecek açar.

Bir türü diyagram üzerinde ilk kez görüntülediğinizde, bu türe ait şekil varsayılan olarak daraltılmış görünür. Şekli genişleterek içeriğini görüntüleyebilirsiniz.

### <a name="to-display-the-contents-of-a-project-in-a-class-diagram"></a>Sınıf diyagramında proje içeriğini görüntülemek için

İçinde **Çözüm Gezgini** veya **sınıf görünümü**, projeye sağ tıklayın ve seçin **Görünüm**, ardından **görünüm sınıfı diyagramı**. Otomatik olarak doldurulan bir Sınıf Diyagramı oluşturulur.

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: türler arasında devralmayı görüntüleme](how-to-view-inheritance-between-types.md)
- [Nasıl yapılır: sınıf diyagramlarını özelleştirme](how-to-customize-class-diagrams.md)
- [Türleri ve İlişkileri Görüntüleme](viewing-types-and-relationships.md)