---
title: Menüler ve komutlar genişletme | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- menus, common tasks
- VSPackages, menu tasks
- .vsct files, common menu tasks
ms.assetid: 7b2be4b9-e3fe-4412-874f-ae72ebc84c4b
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: e6f5cd78709c9a4843588188494b4a70f7268742
ms.sourcegitcommit: 06db1892fff22572f0b0a11994dc547c2b7e2a48
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/08/2018
ms.locfileid: "39639756"
---
# <a name="extend-menus-and-commands"></a>Menüler ve komutlar genişletme
Komutları için Visual Studio eylem ve işlemleri ekleme yoludur. Çoğu durumda, menü veya araç çubukları komutları görüntülenir. VSPackage proje şablonu, çok basit bir komut uygulamak gösterilmektedir. Görmek için biraz daha uzun ancak yine de temel bir uygulama, [bir menü komutuyla uzantı oluşturma](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
 Visual Studio komutlar, menüler ve araç çubukları hakkında daha fazla bilgi için bkz: [komutlar, menüler ve araç çubukları](../extensibility/internals/commands-menus-and-toolbars.md).  
  
 Komutlar, menüler ve araç çubukları içinde tanımlanmıştır *.vsct* dosya VSPackage projelerin bir parçası. Visual Studio IDE hakkında bilgi bulabilirsiniz ve *.vsct* dosyası [nasıl VSPackages kullanıcı arabirimi öğeleri ekleyebilir](../extensibility/internals/how-vspackages-add-user-interface-elements.md).  
  
 Aşağıdaki konular, farklı türde komutlar, menüler ve araç çubuklarını ekleme işlemleri açıklanmaktadır.  
  
## <a name="in-this-section"></a>Bu bölümde  
 [Visual Studio menü çubuğuna menü ekleme](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md)  
 En üste Visual Studio menü çubuğunda bir menü ekleme işlemi açıklanmaktadır.  
  
 [Menü öğelerine klavye kısayolları bağlama](../extensibility/binding-keyboard-shortcuts-to-menu-items.md)  
 Bir menü öğesi için bir kısayol tuşu (örneğin, CTRL + 3) ekleme açıklanmaktadır.  
  
 [Bir menüye alt menü ekleme](../extensibility/adding-a-submenu-to-a-menu.md)  
 Üst menüye alt menü ekleme işlemi açıklanmaktadır.  
  
 [Bir en son kullanılan bir alt menüye listesi Ekle](../extensibility/adding-a-most-recently-used-list-to-a-submenu.md)  
 En son kullanılan liste ekleme açıklanmaktadır.  
  
 [Yeniden kullanılabilir düğme grupları oluşturma](../extensibility/creating-reusable-groups-of-buttons.md)  
 Birden çok menülerde eklenebilir böylece komut öğeleri gruplandırmak açıklar.  
  
 [Menü komutlarına simge ekleme](../extensibility/adding-icons-to-menu-commands.md)  
 Hem araç hem de bir menü komutu için bir simge eklemeyi açıklar.  
  
 [Menü komutunun metnini değiştirme](../extensibility/changing-the-text-of-a-menu-command.md)  
 Kullanımını açıklar `TextChanges` dinamik olarak değiştirilmesi bir menü öğesini etkinleştirmek için bayrak.  
  
 [Bir komutun görünümünü değiştirme](../extensibility/changing-the-appearance-of-a-command.md)  
 Dinamik olarak etkinleştirme veya devre dışı bir komut açıklar.  
  
 [Kullanıcı arabirimini güncelleştirme](../extensibility/updating-the-user-interface.md)  
 Son değişiklikleri yansıtmak için kullanıcı arabiriminin bir güncelleştirmeyi zorlamak açıklar.  
  
 [Menü komutlarını yerelleştirme](../extensibility/localizing-menu-commands.md)  
 Menü komutlarını yerelleştirme açıklanmaktadır.  