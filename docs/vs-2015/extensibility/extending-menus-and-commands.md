---
title: Menüler ve komutlar genişletme | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- menus, common tasks
- VSPackages, menu tasks
- .vsct files, common menu tasks
ms.assetid: 7b2be4b9-e3fe-4412-874f-ae72ebc84c4b
caps.latest.revision: 50
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 36dcc3742b745f8933f340b8df966b1f621d6998
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51793158"
---
# <a name="extending-menus-and-commands"></a>Menüleri ve Komutları Genişletme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Komutları için Visual Studio eylem ve işlemleri ekleme yoludur. Çoğu durumda, menü veya araç çubukları komutları görüntülenir. VSPackage proje şablonu, çok basit bir komut uygulamak gösterilmektedir. Görmek için biraz daha uzun ancak yine de temel bir uygulama, [bir menü komutuyla uzantı oluşturma](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
 Visual Studio komutlar, menüler ve araç çubukları hakkında daha fazla bilgi için bkz: [komutlar, menüler ve araç çubukları](../extensibility/internals/commands-menus-and-toolbars.md).  
  
 Komutlar, menüler ve araç çubukları VSPackage projelerin bir parçası olan .vsct dosyası içinde tanımlanır. Visual Studio IDE ve içinde .vsct dosyası hakkında bilgi bulabilirsiniz [nasıl VSPackages Ekle kullanıcı arabirimi öğeleri](../extensibility/internals/how-vspackages-add-user-interface-elements.md).  
  
 Aşağıdaki konular, farklı türde komutlar, menüler ve araç çubuklarını ekleme işlemleri açıklanmaktadır.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Visual Studio Menü Çubuğuna Menü Ekleme](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md)  
 En üste Visual Studio menü çubuğunda bir menü ekleme işlemi açıklanmaktadır.  
  
 [Menü Öğelerine Klavye Kısayolları Bağlama](../extensibility/binding-keyboard-shortcuts-to-menu-items.md)  
 Bir menü öğesi için bir kısayol tuşu (örneğin, CTRL + 3) ekleme açıklanmaktadır.  
  
 [Bir Menüye Alt Menü Ekleme](../extensibility/adding-a-submenu-to-a-menu.md)  
 Üst menüye alt menü ekleme işlemi açıklanmaktadır.  
  
 [Bir Alt Menüye Son Kullanılanlar Listesi Ekleme](../extensibility/adding-a-most-recently-used-list-to-a-submenu.md)  
 En son kullanılan liste ekleme açıklanmaktadır.  
  
 [Yeniden Kullanılabilir Düğme Grupları Oluşturma](../extensibility/creating-reusable-groups-of-buttons.md)  
 Birden çok menülerde eklenebilir böylece komut öğeleri gruplandırmak açıklar.  
  
 [Menü Komutlarına Simge Ekleme](../extensibility/adding-icons-to-menu-commands.md)  
 Hem araç hem de bir menü komutu için bir simge eklemeyi açıklar.  
  
 [Bir Menü Komutunun Metnini Değiştirme](../extensibility/changing-the-text-of-a-menu-command.md)  
 Kullanımını açıklar `TextChanges` dinamik olarak değiştirilmesi bir menü öğesini etkinleştirmek için bayrak.  
  
 [Bir Komutun Görünümünü Değiştirme](../extensibility/changing-the-appearance-of-a-command.md)  
 Dinamik olarak etkinleştirme veya devre dışı bir komut açıklar.  
  
 [Kullanıcı Arabirimini Güncelleştirme](../extensibility/updating-the-user-interface.md)  
 Son değişiklikleri yansıtmak için kullanıcı arabiriminin bir güncelleştirmeyi zorlamak açıklar.  
  
 [Menü Komutlarını Yerelleştirme](../extensibility/localizing-menu-commands.md)  
 Menü komutlarını yerelleştirme açıklanmaktadır.  
  
## <a name="related-sections"></a>İlgili Bölümler

