---
title: 'Nasıl Yapılır: Menüleri ve Araç Çubuklarını Özelleştirme'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
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
caps.latest.revision: 31
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 3196aac35a05d915f1f4c3b58547e0787e9a1afc
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53066710"
---
# <a name="how-to-customize-menus-and-toolbars-in-visual-studio"></a>Nasıl Yapılır: Visual Studio'da Menüleri ve Araç Çubuklarını Özelleştirme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Araç çubuklarını ve menü çubuğundaki menüleri ekleyip kaldırmanın yanı sıra herhangi bir araç çubuğundaki veya menüdeki komutları ekleyip kaldırmak suretiyle de Visual Studio'yu özelleştirebilirsiniz.

> [!WARNING]
>  Bir araç çubuğunu veya menüyü özelleştirdikten sonra ilgili onay kutusunun seçili kaldığından emin olun **Özelleştir** iletişim kutusu. Aksi takdirde, Visual Studio'yu kapatıp yeniden açtıktan sonra değişiklikleriniz kalıcı olmaz.

 **Bu konuda:**

-   [Ekleme, kaldırma veya menü çubuğunda taşıma](../ide/how-to-customize-menus-and-toolbars-in-visual-studio.md#bkmk_addmenu)

-   [Ekleme, kaldırma veya taşıma araç çubuğu](../ide/how-to-customize-menus-and-toolbars-in-visual-studio.md#bkmk_addtoolbar)

-   [Bir menü veya araç çubuğunu özelleştirme](../ide/how-to-customize-menus-and-toolbars-in-visual-studio.md#bkmk_customize)

-   [Bir menü veya araç çubuğunu sıfırlama](../ide/how-to-customize-menus-and-toolbars-in-visual-studio.md#bkmk_reset)

##  <a name="bkmk_addmenu"></a> Ekleme, kaldırma veya menü çubuğunda taşıma

1.  Menü çubuğunda, **Araçları**, **Özelleştir**.

     **Özelleştir** iletişim kutusu açılır.

2.  Üzerinde **komutları** sekmesinde **menü çubuğu** bırakın, seçenek düğmesini seçili **menü çubuğu** bu seçeneğin yanındaki listede seçili bırakmanızı ve ardından aşağıdaki adımlardan birini gerçekleştirin adımlar:

    -   Menü eklemek için **yeni menü Ekle** düğmesini öğesini **Seçimi Değiştir** düğmesini ve sonra eklemek istediğiniz menünün adını.

         ![Özelleştir iletişim kutusu bir menü ekleme gösteren](../ide/media/addmenu.png "MenüEkle")

    -   Bir menüyü kaldırmak için projeyi seçin **denetimleri** listeleyin ve ardından **Sil** düğmesi.

    -   Menü çubuğu dahilinde bir menüyü taşımak için menüden seçin **denetimleri** listeleyin ve ardından **Yukarı Taşı** veya **Aşağı Taşı** düğmesi.

##  <a name="bkmk_addtoolbar"></a> Ekleme, kaldırma veya taşıma araç çubuğu

1.  Menü çubuğunda, **Araçları**, **Özelleştir**.

     **Özelleştir** iletişim kutusu açılır.

2.  Üzerinde **araç** sekmesinde, aşağıdaki adımlardan birini gerçekleştirin:

    -   Araç çubuğu eklemek için **yeni** ekleyin ve ardından istediğiniz araç için bir ad belirtin, düğme **Tamam** düğmesi.

         ![Özelleştir iletişim kutusu araç çubuğu ekleme gösteren](../ide/media/addtoolbar.png "AddToolbar")

    -   Özel bir araç çubuğunu kaldırmak için onu seçin **araç çubukları** listeleyin ve ardından **Sil** düğmesi.

        > [!IMPORTANT]
        >  Kendi oluşturduğunuz araç çubuklarını silebilir, ancak varsayılan araç çubuklarını silemezsiniz.

    -   Bir araç çubuğunu farklı bir yerleştirme konumuna taşımak için projeyi seçin **araç çubukları** listesinde **Seçimi Değiştir** düğmesini ve ardından görüntülenen listede bir konum seçin.

         Ayrıca, bir araç çubuğunu, ana yerleştirme alanında herhangi bir konuma taşımak için sol kenarından sürükleyebilirsiniz.

        > [!NOTE]
        >  Kullanılabilirliğini ve erişilebilirliğini araç çubuklarının geliştirme konusunda daha fazla bilgi için bkz. [nasıl yapılır: IDE erişilebilirlik seçeneklerini ayarlama](../ide/reference/how-to-set-ide-accessibility-options.md).

##  <a name="bkmk_customize"></a> Bir menü veya araç çubuğunu özelleştirme

1.  Menü çubuğunda, **Araçları**, **Özelleştir**.

     **Özelleştir** iletişim kutusu açılır.

2.  Üzerinde **komutları** sekmesinde, özelleştirmek istediğiniz öğe türüne ilişkin seçenek düğmesini seçin.

3.  Bu öğe türüne ilişkin listede, özelleştirmek istediğiniz menü veya araç çubuğunu seçin ve sonra aşağıdaki adım gruplarından birini gerçekleştirin:

    -   Bir komut eklemek için **Add Command** düğmesi.

         İçinde **Add Command** iletişim kutusunda, bir öğeyi **kategorileri** listesinde, bir öğe seçin **komutları** listeleyin ve ardından **Tamam**düğmesi.

         ![Visual Studio'da Ekle komutu iletişim kutusu](../ide/media/addcommand.png "AddCommand")

    -   Bir komutu silmek için onu seçin **denetimleri** listeleyin ve ardından **Sil** düğmesi.

    -   Komutları yeniden düzenlemek için bir komut seçin **denetimleri** listeleyin ve ardından **Yukarı Taşı** veya **Aşağı Taşı** düğmesi.

    -   Komutları gruplar halinde ayırmak için bir komut seçin **denetimleri** listesinde **Seçimi Değiştir** düğmesine ve ardından **bir Grup Başlat** menüde görünür.

##  <a name="bkmk_reset"></a> Bir menü veya araç çubuğunu sıfırlama

1.  Menü çubuğunda, **Araçları**, **Özelleştir**.

     **Özelleştir** iletişim kutusu açılır.

2.  Üzerinde **komutları** sekmesinde, sıfırlamak istediğiniz öğe türüne ilişkin seçenek düğmesini seçin.

3.  Bu öğe türüne ilişkin listede, sıfırlamak istediğiniz menü veya araç çubuğunu seçin.

4.  Seçin **Seçimi Değiştir** düğmesine ve ardından **sıfırlama** menüde görünür.

     Seçerek tüm menüleri ve araç çubuklarını da sıfırlayabilirsiniz **Tümünü Sıfırla** düğmesi.
