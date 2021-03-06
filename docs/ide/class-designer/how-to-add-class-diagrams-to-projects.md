---
title: Projelere sınıf diyagramları ekleme (Sınıf Tasarımcısı)
description: Sınıfları ve diğer türleri tasarlama, düzenleme ve yeniden düzenleme, C#, Visual Basic veya C++ projenize bir sınıf diyagramı ekleme hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 05/08/2018
ms.topic: how-to
helpviewer_keywords:
- class diagrams, creating
- Class Designer [Visual Studio], opening
ms.assetid: 0eac1b54-2711-4e4b-9654-a0c429c08c8f
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 0af2717efec7cab8594f193c06e8813bd556b01f
ms.sourcegitcommit: c3713f284c4fe10b10996d5eb67077ddd8641424
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112375792"
---
# <a name="how-to-add-class-diagrams-to-projects"></a>Nasıl yapılır: projelere sınıf diyagramları ekleme

Sınıfları ve diğer türleri tasarlamak, düzenlemek ve yeniden düzenlemek için C#, Visual Basic veya C++ projenize bir sınıf diyagramı ekleyin. Projedeki kodun farklı kısımlarını görselleştirmek için projeye birden çok sınıf diyagramı ekleyin.

Birden çok uygulama arasında kod paylaşan projelerden sınıf diyagramları oluşturamazsınız. UML sınıf diyagramları oluşturmak için bkz. [UML modelleme projeleri ve diyagramları oluşturma](https://devblogs.microsoft.com/devops/uml-designers-have-been-removed-layer-designer-now-supports-live-architectural-analysis/).

## <a name="install-the-class-designer-component"></a>Sınıf Tasarımcısı bileşenini yükler

**Sınıf Tasarımcısı** bileşenini yüklemediyseniz, yüklemek için aşağıdaki adımları izleyin.

1. Windows Başlat menüsünden **Visual Studio yükleyicisi** açın veya **Araçlar**' ı seçerek  >  Visual Studio 'daki menü çubuğundan Araçlar **ve Özellikler al** ' ı seçin.

   **Visual Studio yükleyicisi** açılır.

1. **Ayrı bileşenler** sekmesini seçin ve ardından **kod araçları** kategorisine gidin.

1. **Sınıf Tasarımcısı** seçin ve ardından **Değiştir**' i seçin.

   ![Sınıf Tasarımcısı bileşeni Visual Studio Yükleyicisi](media/class-designer-component.png)

   **Sınıf Tasarımcısı** bileşen yüklenmeye başlıyor.

## <a name="add-a-blank-class-diagram-to-a-project"></a>Projeye boş bir sınıf diyagramı ekleme

1. **Çözüm Gezgini**, proje düğümüne sağ tıklayın ve ardından   >  **Yeni öğe** Ekle ' yi seçin. Ya da **CTRL** + **SHIFT** + **A**'ya basın.

   **Yeni öğe Ekle** iletişim kutusu açılır.

2. Genel **öğeler**  >  **genel**' i genişletin ve ardından şablon listesinden **sınıf diyagramı** ' nı seçin. Visual C++ projeler için, **sınıf diyagramı** şablonunu bulmak Için **yardımcı program** kategorisine bakın.

   > [!NOTE]
   > **Sınıf diyagramı** şablonunu görmüyorsanız, Visual Studio için **Sınıf Tasarımcısı** bileşenini yüklemek için [adımları izleyin](#install-the-class-designer-component) .

   Sınıf diyagramı Sınıf Tasarımcısı açılır ve **Çözüm Gezgini** *. CD* uzantılı bir dosya olarak görünür. **Araç kutusu**' ndan şekilleri ve çizgileri diyagrama sürükleyebilirsiniz.

Birden fazla sınıf diyagramı eklemek için bu yordamdaki adımları yineleyin.

## <a name="add-a-class-diagram-based-on-existing-types"></a>Varolan türlere göre bir sınıf diyagramı ekleyin

**Çözüm Gezgini**, bir sınıf dosyasının bağlam menüsünü açın (sağ tıklayın) ve ardından **sınıf diyagramını görüntüle**' yi seçin.

-veya-

**Sınıf görünümü**, ad alanı veya tür bağlam menüsünü açın ve ardından **sınıf diyagramını görüntüle**' yi seçin.

> [!TIP]
> **Sınıf görünümü** açık değilse, **Görünüm** menüsünden **sınıf görünümü** açın.

## <a name="to-display-the-contents-of-a-complete-project-in-a-class-diagram"></a>Bir sınıf diyagramında tüm projenin içeriğini görüntüleme

**Çözüm Gezgini** veya sınıf görünümü ' de projeye sağ tıklayın ve **görüntüle**' yi seçin ve ardından **sınıf diyagramını görüntüle**' yi seçin.

Otomatik doldurulmuş bir sınıf diyagramı oluşturulur.

> [!NOTE]
> Sınıf Tasarımcısı .NET Core projelerinde kullanılamaz.

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: Sınıf Tasarımcısı kullanarak tür oluşturma](how-to-create-types.md)
- [Nasıl yapılır: varolan türleri görüntüleme](how-to-view-existing-types.md)
- [Sınıfları ve türleri tasarlama ve görüntüleme](designing-and-viewing-classes-and-types.md)
