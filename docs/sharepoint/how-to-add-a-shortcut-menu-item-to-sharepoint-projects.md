---
title: 'Nasıl yapılır: SharePoint projelerine kısayol menü öğesi ekleme | Microsoft Docs'
titleSuffix: ''
description: Visual Studio 'da bir SharePoint projesine kısayol menü öğesi ekleyin. Çözüm Gezgini içindeki bir proje düğümüne sağ tıkladığınızda menü öğesi görünür.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- projects [SharePoint development in Visual Studio], extending
- SharePoint development in Visual Studio, extending projects
- SharePoint projects, extending
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 54ac53ad317f500e787baebfdfeb4a86dc917e06
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2021
ms.locfileid: "106216819"
---
# <a name="how-to-add-a-shortcut-menu-item-to-sharepoint-projects"></a>Nasıl yapılır: SharePoint projelerine kısayol menü öğesi ekleme
  Herhangi bir SharePoint projesine kısayol menü öğesi ekleyebilirsiniz. Kullanıcı **Çözüm Gezgini** bir proje düğümüne sağ tıkladığında, menü öğesi görünür.

 Aşağıdaki adımlarda zaten bir proje uzantısı oluşturmuş olduğunuz varsayılır. Daha fazla bilgi için bkz. [nasıl yapılır: SharePoint Proje uzantısı oluşturma](../sharepoint/how-to-create-a-sharepoint-project-extension.md).

### <a name="to-add-a-shortcut-menu-item-to-sharepoint-projects"></a>SharePoint projelerine kısayol menü öğesi eklemek için

1. <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension.Initialize%2A> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> Uygulamanızın yönteminde, <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectMenuItemsRequested> *ProjectService* parametresinin olayını işleyin.

2. Olaya yönelik olay işleyicinizde <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectMenuItemsRequested> , <xref:Microsoft.VisualStudio.SharePoint.IMenuItem> <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectMenuItemsRequestedEventArgs.ActionMenuItems%2A> <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectMenuItemsRequestedEventArgs.AddMenuItems%2A> olay bağımsız değişkenleri parametresinin veya koleksiyonuna yeni bir nesne ekleyin.

3. <xref:Microsoft.VisualStudio.SharePoint.IMenuItem.Click>Yeni nesne için olay işleyicisinde <xref:Microsoft.VisualStudio.SharePoint.IMenuItem> , Kullanıcı kısayol menü öğesine tıkladığında yürütmek istediğiniz görevleri gerçekleştirin.

## <a name="example"></a>Örnek
 Aşağıdaki kod örneği, **Çözüm Gezgini** bir kısayol menü öğesinin SharePoint proje düğümlerine nasıl ekleneceğini gösterir. Kullanıcı bir proje düğümüne sağ tıkladıktan sonra **Çıkış penceresi Için Ileti yaz** menü öğesine tıkladığında, Visual Studio **çıktı** penceresinde bir ileti görüntüler. Bu örnek, iletiyi göstermek için SharePoint proje hizmetini kullanır. Daha fazla bilgi için bkz. [SharePoint proje hizmetini kullanma](../sharepoint/using-the-sharepoint-project-service.md).

 :::code language="csharp" source="../sharepoint/codesnippet/CSharp/projectmenu/extension/projectitemextensionmenu.cs" id="Snippet1":::
 :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/projectmenu/extension/projectitemextensionmenu.vb" id="Snippet1":::

## <a name="compile-the-code"></a>Kodu derle
 Bu örnek, aşağıdaki derlemelere başvurular içeren bir sınıf kitaplığı projesi gerektirir:

- Microsoft. VisualStudio. SharePoint

- System. ComponentModel. Composition

## <a name="deploy-the-extension"></a>Uzantıyı dağıtma
 Uzantıyı dağıtmak için, [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] derleme için bir uzantı (VSIX) paketi ve uzantıyla dağıtmak istediğiniz diğer dosyalar oluşturun. Daha fazla bilgi için bkz. [Visual Studio 'Da SharePoint araçları için uzantıları dağıtma](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).

## <a name="see-also"></a>Ayrıca bkz.
- [SharePoint projelerini genişletme](../sharepoint/extending-sharepoint-projects.md)
- [Nasıl yapılır: SharePoint Proje uzantısı oluşturma](../sharepoint/how-to-create-a-sharepoint-project-extension.md)
- [Nasıl yapılır: SharePoint projelerine özellik ekleme](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md)
