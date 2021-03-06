---
title: 'Nasıl yapılır: Backstage görünümüne denetimler ekleme '
description: Dosya sekmesine tıkladığınızda açılan menüye denetim eklemek için şerit tasarımcısını nasıl kullanabileceğinizi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- customizing the Ribbon, menus
- controls, Ribbon
- menus, customizing
- Microsoft Office Button
- custom Ribbon, menus
- Ribbon, customizing
- Office button
- Ribbon, menus
- Microsoft Office Menu
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 830ecea036ee972321d98994ab36924e0c61a09b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99954273"
---
# <a name="how-to-add-controls-to-the-backstage-view"></a>Nasıl yapılır: Backstage görünümüne denetimler ekleme
  **Dosya** sekmesine tıkladığınızda açılan menüye denetim eklemek Için şerit tasarımcısını kullanabilirsiniz. Uygulamayı çalıştırdığınızda, **Dosya** sekmesine eklediğiniz denetimler, **Eklentiler** adlı bir grup görünür.

 Visual Studio 'daki şerit tasarımcısını kullanarak yerleşik denetimlerden önce veya sonra Denetim konumlandırabilirsiniz. Yerleşik denetim, Backstage görünümünde zaten görüntülenen bir denetimdir. Denetimleri yerleşik denetimlerden önce veya sonra konumlandırmak istiyorsanız, Şerit XML kullanmanız gerekir. **Şerit (XML)** hakkında daha fazla bilgi için bkz. [Ribbon XML](../vsto/ribbon-xml.md). Backstage görünümünü özelleştirme hakkında daha fazla bilgi için bkz. [geliştiriciler Için office 2010 Backstage görünümüne giriş](/previous-versions/office/developer/office-2010/ee691833(v=office.14)) ve [geliştiriciler Için Office 2010 Backstage görünümünü özelleştirme](/previous-versions/office/developer/office-2010/ee815851(v=office.14)).

 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]

### <a name="to-add-controls-to-backstage-view"></a>Backstage görünümüne denetimler eklemek için

1. Tasarım görünümü içindeki şerit öğesini açın.

     Projenize **Şerit (görsel Tasarımcı)** öğesi ekleme hakkında daha fazla bilgi için bkz. [nasıl yapılır: Şeriti özelleştirmeye başlama](../vsto/how-to-get-started-customizing-the-ribbon.md).

2. Şerit tasarımcısında **Dosya** sekmesine tıklayın.

     Bir menü Tasarımcısı görüntülenir. Bu tasarım yüzeyi herhangi bir denetim içermiyor.

3. **Araç kutusunun** **Office Şerit denetimleri** sekmesinden, aşağıdaki denetimlerden herhangi birini menü tasarımcısına sürükleyin:

    - Düğme

    - CheckBox

    - Galeri

    - Menü

    - Ayırıcı

    - SplitButton

    - ToggleButton

4. Denetimleri menüdeki yeni konumlara taşımak için sürükleyin.

## <a name="see-also"></a>Ayrıca bkz.
- [Şerite genel bakış](../vsto/ribbon-overview.md)
- [Şerit Tasarımcısı](../vsto/ribbon-designer.md)
- [Şerit XML](../vsto/ribbon-xml.md)
- [Nasıl yapılır: Şeriti özelleştirmeye başlama](../vsto/how-to-get-started-customizing-the-ribbon.md)
- [İzlenecek yol: Şerit Tasarımcısını kullanarak özel sekme oluşturma](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)
