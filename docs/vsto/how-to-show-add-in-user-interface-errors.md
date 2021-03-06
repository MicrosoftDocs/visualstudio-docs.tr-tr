---
title: 'Nasıl yapılır: eklenti Kullanıcı arayüzü hatalarını gösterme'
description: Visual Studio 'Yu kullanarak Microsoft Office uygulamalarında, Add-User Interface User Interface hatalarını programlı bir şekılde gösterme hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- add-ins [Office development in Visual Studio], user interface errors
- errors [Office development in Visual Studio], user interface errors
- user interfaces [Office development in Visual Studio], errors
- application-level add-ins [Office development in Visual Studio], user interface errors
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 29e07e49d901b44b534d9d274e5535be663e97ef
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99927685"
---
# <a name="how-to-show-add-in-user-interface-errors"></a>Nasıl yapılır: eklenti Kullanıcı arayüzü hatalarını gösterme
  Varsayılan olarak, bir VSTO eklentisi Microsoft Office Kullanıcı arabirimini (UI) işlemeyi denerse ve başarısız olursa, hata iletisi gösterilmez. Ancak, Kullanıcı arabirimiyle ilgili hatalara yönelik iletileri göstermek için Microsoft Office uygulamaları yapılandırabilirsiniz. Bu iletileri, özel bir şeridin neden görünmediğini veya bir şeridin neden göründüğünü, ancak hiçbir denetimin görünmediğini belirlemede yardımcı olması için kullanabilirsiniz.

 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]

## <a name="to-show-vsto-add-in-user-interface-errors"></a>VSTO eklentisi Kullanıcı arabirimi hatalarını göstermek için

1. Uygulamayı başlatın.

2. **Dosya** sekmesine tıklayın.

3. **Seçenekler**’e tıklayın.

4. Kategoriler bölmesinde **Gelişmiş**' e tıklayın.

5. Ayrıntılar bölmesinde, **VSTO eklentisi Kullanıcı arabirimi hatalarını göster**' i seçin ve ardından **Tamam**' a tıklayın.

    > [!NOTE]
    > Outlook için, **VSTO eklentisi Kullanıcı arabirimi hatalarını göster** onay kutusu, ayrıntılar bölmesinin **Geliştirici** bölümünde bulunur. Diğer uygulamalar için, onay kutusu Ayrıntılar bölmesinin **genel** bölümünde bulunur.

## <a name="see-also"></a>Ayrıca bkz.
- [Office UI özelleştirmesi](../vsto/office-ui-customization.md)
- [Outlook form bölgeleri oluşturma](../vsto/creating-outlook-form-regions.md)
- [Şerite genel bakış](../vsto/ribbon-overview.md)
- [Eylemler bölmesine genel bakış](../vsto/actions-pane-overview.md)
