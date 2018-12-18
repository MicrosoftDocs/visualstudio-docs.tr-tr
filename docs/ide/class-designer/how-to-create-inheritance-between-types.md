---
title: 'Nasıl yapılır: devralma türleri (Sınıf Tasarımcısı) arasındaki oluştur'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.classdesigner.inheritanceline
helpviewer_keywords:
- inheritance, relationship defining
- relationships, defining inheritance
ms.assetid: 3786a21c-8022-4bf5-9d13-740fd354e93c
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e8151020294f4fd5574a1de886509c5b11f0a326
ms.sourcegitcommit: 4c0db930d9d5d8b857d3baf2530ae89823799612
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/10/2018
ms.locfileid: "33956685"
---
# <a name="how-to-create-inheritance-between-types-in-class-designer"></a>Nasıl yapılır: Sınıf Tasarımcısı'nda türler arasında devralmayı oluşturma

Sınıf diyagramı kullanarak iki tür arasında bir devralma ilişkisi oluşturmak için **Sınıf Tasarımcısı**, kendi türetilmiş türü veya türleri ile temel türü bağlanın. İki sınıf arasında bir sınıf ve bir arabirim arasında veya iki arabirimler arasında bir devralma ilişkisi olabilir.

## <a name="to-create-an-inheritance-between-types"></a>Türler arasında devralmayı oluşturmak için

1.  İçinde projenizden **Çözüm Gezgini**, bir sınıf diyagramı (.cd) dosyasını açın.

     Sınıf diyagramında yoksa, oluşturun. Bkz: [nasıl yapılır: projelere sınıf diyagramları ekleme](how-to-add-class-diagrams-to-projects.md).

2.  İçinde **araç**altında **Sınıf Tasarımcısı**, tıklatın **devralma**.

3.  Sınıf diyagramında başlayarak istediğiniz türler arasında bir devralma çizgi çizme:

    -   Türetilmiş bir sınıf için temel sınıfı

    -   Uygulayan bir sınıfa uygulanan arabirimi

    -   Genişletme arabirime genişletilmiş arabirimi

4.  İsteğe bağlı olarak, genel bir türden türetilmiş bir tür olduğunda Devralma Satırı'ı tıklatın. İçinde **özellikleri** penceresindeki ayarlayın **tür bağımsız değişkenleri** genel türü için istediğiniz türüyle eşleşecek şekilde özelliği.

    > [!NOTE]
    > Bir üst soyut sınıf soyut en az bir üye içeriyorsa, tüm soyut üyelerini Özet olmayan türetilen sınıflar uygulanır.
    >
    >  Mevcut genel türleri görselleştirebilirsiniz rağmen yeni genel türler oluşturulamıyor. Ayrıca, varolan genel türleri için tür parametreleri değiştiremezsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [Devralma](/dotnet/csharp/programming-guide/classes-and-structs/inheritance)
- [Devralma Temelleri](/dotnet/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics)
- [Nasıl yapılır: türler arasında devralmayı görüntüleme](how-to-view-inheritance-between-types.md)
- [Sınıf Tasarımcısında Visual C++ Sınıfları](visual-cpp-classes.md)