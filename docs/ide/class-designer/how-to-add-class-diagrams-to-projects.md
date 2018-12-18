---
title: 'Nasıl Yapılır: Projelere Sınıf Diyagramları Ekleme (Sınıf Tasarımcısı)'
ms.date: 05/08/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- class diagrams, creating
- Class Designer [Visual Studio], opening
ms.assetid: 0eac1b54-2711-4e4b-9654-a0c429c08c8f
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 133f15f6c160e9ec48b1db4ab8713023e492cbae
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/24/2018
ms.locfileid: "42901304"
---
# <a name="how-to-add-class-diagrams-to-projects"></a>Nasıl yapılır: projelere sınıf diyagramları ekleme

Tasarlama, düzenleme ve sınıfları ve diğer türleri yeniden düzenleme için C#, Visual Basic veya C++ projenize bir sınıf diyagramı ekleyin. Kod projesinde farklı parçalarını görselleştirmek için birden fazla sınıf diyagramı projeye ekleyin.

Birden fazla uygulama arasında kod paylaşma projelerinden sınıf diyagramları oluşturamazsınız. UML sınıf diyagramları oluşturmak için bkz [oluşturma UML modelleme projeleri ve diyagramları](../../modeling/create-uml-modeling-projects-and-diagrams.md).

## <a name="install-the-class-designer-component"></a>Sınıf Tasarımcısı bileşeni

Visual Studio 2017 çalıştırıyorsanız ve yüklü olmayan **Sınıf Tasarımcısı** bileşeni yüklemek için aşağıdaki adımları izleyin.

1. Açık **Visual Studio yükleyicisi** Windows Başlat menüsünden veya seçerek **Araçları** > **araçları ve özellikleri Al** Visual Studio'da menü çubuğundan.

   **Visual Studio yükleyicisi** açılır.

1. Seçin **tek tek bileşenler** sekmesine ve ardından aşağı kaydırarak **kod Araçları** kategorisi.

1. Seçin **Sınıf Tasarımcısı** seçip **Değiştir**.

   ![Visual Studio Yükleyicisi'nde Tasarımcısı bileşen sınıfı](media/class-designer-component.png)

   **Sınıf Tasarımcısı** bileşeni yükleme başlar.

## <a name="add-a-blank-class-diagram-to-a-project"></a>Boş bir sınıf diyagramı projeye ekleme

1. İçinde **Çözüm Gezgini**, proje düğümüne sağ tıklayın ve ardından **Ekle** > **yeni öğe**. Veya basın **Ctrl**+**Shift**+**A**.

   **Yeni Öğe Ekle** iletişim kutusu açılır.

2. Genişletin **ortak öğeler** > **genel**ve ardından **sınıf diyagramı** şablon listesinden. Visual C++ projeleri için konum **yardımcı programı** bulmak için kategori **sınıf diyagramı** şablonu.

   > [!NOTE]
   > Görmüyorsanız **sınıf diyagramı** şablon [adımları](#install-the-class-designer-component) yüklemek için **Sınıf Tasarımcısı** Visual Studio için bileşen.

   Sınıf diyagramı Sınıf Tasarımcısı'nda açılır ve bir dosya görünür bir *.cd* uzantısında **Çözüm Gezgini**. Diyagramdan için şekilleri ve çizgileri sürükleyebilirsiniz **araç kutusu**.

Birden fazla sınıf diyagramı eklemek için bu yordamdaki adımları yineleyin.

## <a name="add-a-class-diagram-based-on-existing-types"></a>Varolan türlere dayalı bir sınıf diyagramı ekleyin

İçinde **Çözüm Gezgini**, bir sınıf dosyasının bağlam menüsü (sağ tıklama) açın ve ardından **sınıf diyagramını görüntüle**.

veya

İçinde **sınıf görünümü**, ad alanı veya tür bağlam menüsünü açın ve ardından **sınıf diyagramını görüntüle**.

> [!TIP]
> Varsa **sınıf görünümü** açık, açık olmayan **sınıf görünümü** gelen **görünümü** menüsü.

## <a name="to-display-the-contents-of-a-complete-project-in-a-class-diagram"></a>Bir sınıf diyagramında eksiksiz bir projenin içeriğini görüntülemek için

İçinde **Çözüm Gezgini** veya sınıf görünümü projeye sağ tıklayıp seçin, **görünümü**, ardından **sınıf diyagramını görüntüle**.

Bir otomatik olarak doldurulan bir sınıf diyagramı oluşturulur.

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: Sınıf Tasarımcısı kullanarak tür oluşturma](how-to-create-types.md)
- [Nasıl yapılır: Varolan türleri görüntüleme](how-to-view-existing-types.md)
- [Tasarım ve görünüm sınıfları ve türleri](designing-and-viewing-classes-and-types.md)
- [Görünüm türleri ve ilişkiler](viewing-types-and-relationships.md)
- [Sınıf diyagramları ile çalışma](working-with-class-diagrams.md)
