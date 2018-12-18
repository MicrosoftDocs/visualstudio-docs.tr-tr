---
title: Menüleri ve araç çubuklarını özelleştirme
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.renametoolbar
- vs.customize.toolbars
- vs.buttoneditor
- vs.customize.commands
- vs.newtoolbar
helpviewer_keywords:
- captions, customizing toolbar
- custom toolbars [Visual Studio]
- command buttons, customizing toolbar
- labels, customizing toolbar
- images [Visual Studio], toolbar buttons
- buttons [Visual Studio], custom toolbars
- toolbars [Visual Studio], creating in the IDE
- icons [Visual Studio], customizing toolbar
- commands [Visual Studio], customizing environment
- customizing toolbars
- toolbars [Visual Studio], customizing
- toolbars [Visual Studio], customizing in the IDE
ms.assetid: b570ae2f-5302-45dc-9cc9-8d4d1ad50603
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: bb58d0a20e8764e7cefe013458476ddcd41ac416
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53049698"
---
# <a name="how-to-customize-menus-and-toolbars-in-visual-studio"></a>Nasıl yapılır: menüleri ve Visual Studio araç çubuklarını özelleştirme

Visual Studio yalnızca ekleyerek ve araç çubuklarını ve menü çubuğundaki menüleri kaldırma, aynı zamanda ekleyerek ve herhangi bir araç veya menü komutları kaldırma özelleştirebilirsiniz.

> [!WARNING]
> Bir araç çubuğunu veya menüyü özelleştirdikten sonra ilgili onay kutusunun seçili kaldığından emin olun **Özelleştir** iletişim kutusu. Aksi takdirde, Visual Studio'yu kapatıp yeniden açtıktan sonra değişiklikleriniz kalıcı olmaz.

## <a name="add-remove-or-move-a-menu-on-the-menu-bar"></a>Eklemek, kaldırmak veya menü çubuğunda bir menü Taşı

1.  Menü çubuğunda, **Araçları** > **Özelleştir**.

     **Özelleştir** iletişim kutusu açılır.

2.  Üzerinde **komutları** sekmesinde **menü çubuğu** bırakın, seçenek düğmesini seçili **menü çubuğu** bu seçeneğin yanındaki listede seçili bırakmanızı ve ardından aşağıdaki adımlardan birini gerçekleştirin adımlar:

    -   Menü eklemek için **yeni menü Ekle** düğmesini öğesini **Seçimi Değiştir** düğmesini ve sonra eklemek istediğiniz menünün adını.

        ![Özelleştir iletişim kutusu gösteren bir menü ekleme](../ide/media/addmenu.png)

    -   Bir menüyü kaldırmak için projeyi seçin **denetimleri** listeleyin ve ardından **Sil** düğmesi.

    -   Menü çubuğu dahilinde bir menüyü taşımak için menüden seçin **denetimleri** listeleyin ve ardından **Yukarı Taşı** veya **Aşağı Taşı** düğmesi.

## <a name="add-remove-or-move-a-toolbar"></a>Eklemek, kaldırmak veya araç çubuğunu taşımak

1.  Menü çubuğunda, **Araçları** > **Özelleştir**.

     **Özelleştir** iletişim kutusu açılır.

2.  Üzerinde **araç** sekmesinde, aşağıdaki adımlardan birini gerçekleştirin:

    -   Araç çubuğu eklemek için **yeni** ekleyin ve ardından istediğiniz araç için bir ad belirtin, düğme **Tamam** düğmesi.

        ![Özelleştir iletişim kutusu araç çubuğu ekleme gösteriliyor](../ide/media/addtoolbar.png)

    -   Özel bir araç çubuğunu kaldırmak için onu seçin **araç çubukları** listeleyin ve ardından **Sil** düğmesi.

        > [!IMPORTANT]
        > Kendi oluşturduğunuz araç çubuklarını silebilir, ancak varsayılan araç çubuklarını silemezsiniz.

    -   Bir araç çubuğunu farklı bir yerleştirme konumuna taşımak için projeyi seçin **araç çubukları** listesinde **Seçimi Değiştir** düğmesini ve ardından görüntülenen listede bir konum seçin.

        Ayrıca, bir araç çubuğunu, ana yerleştirme alanında herhangi bir konuma taşımak için sol kenarından sürükleyebilirsiniz.

        > [!NOTE]
        > Kullanılabilirliğini ve erişilebilirliğini araç çubuklarının geliştirme konusunda daha fazla bilgi için bkz. [nasıl yapılır: ayarlama IDE erişilebilirlik seçeneklerini](../ide/reference/how-to-set-ide-accessibility-options.md).

## <a name="customizing_menu">Bir menü veya araç çubuğunu özelleştirme</a>

1.  Menü çubuğunda, **Araçları** > **Özelleştir**.

    **Özelleştir** iletişim kutusu açılır.

2.  Üzerinde **komutları** sekmesinde, özelleştirmek istediğiniz öğe türüne ilişkin seçenek düğmesini seçin.

3.  Bu öğe türüne ilişkin listede, özelleştirmek istediğiniz menü veya araç çubuğunu seçin ve sonra aşağıdaki adım gruplarından birini gerçekleştirin:

    -   Bir komut eklemek için **Add Command** düğmesi.

        İçinde **Add Command** iletişim kutusunda, bir öğeyi **kategorileri** listesinde, bir öğe seçin **komutları** listeleyin ve ardından **Tamam**düğmesi.

        ![Visual Studio'da Ekle komutu iletişim kutusu](../ide/media/addcommand.png)

    -   Bir komutu silmek için onu seçin **denetimleri** listeleyin ve ardından **Sil** düğmesi.

    -   Komutları yeniden düzenlemek için bir komut seçin **denetimleri** listeleyin ve ardından **Yukarı Taşı** veya **Aşağı Taşı** düğmesi.

    -   İlk komut seçin, yatay çizgi altındaki komutları grup **denetimleri** listesinde **Seçimi Değiştir** düğmesine ve ardından **bir Grup Başlat** içinde açılan menüsü.

## <a name="reset-a-menu-or-a-toolbar"></a>Bir menü veya araç çubuğunu sıfırlama

1.  Menü çubuğunda, **Araçları** > **Özelleştir**.

    **Özelleştir** iletişim kutusu açılır.

2.  Üzerinde **komutları** sekmesinde, sıfırlamak istediğiniz öğe türüne ilişkin seçenek düğmesini seçin.

3.  Bu öğe türüne ilişkin listede, sıfırlamak istediğiniz menü veya araç çubuğunu seçin.

4.  Seçin **Seçimi Değiştir** düğmesine ve ardından **sıfırlama** menüde görünür.

    Seçerek tüm menüleri ve araç çubuklarını da sıfırlayabilirsiniz **Tümünü Sıfırla** düğmesi.

## <a name="see-also"></a>Ayrıca bkz.

- [IDE'yi kişiselleştirme](../ide/personalizing-the-visual-studio-ide.md)
- [Düzenleyiciyi özelleştirme](../ide/customizing-the-editor.md)