---
title: Iç Içe projeler için AddItem Iletişim kutusunu filtreleme | Microsoft Docs
description: Üst projenin IVsFilterAddProjectItemDlg arabirimini uygulayarak, Visual Studio 'da iç içe geçmiş bir proje için AddItem iletişim kutusunu nasıl filtreleyeceğinizi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- filtering, nested projects
- nested projects, AddItem dialog box filtering
ms.assetid: 5b3e352e-7f18-4f66-be16-b0ad55637ce5
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 59ae3c229ba359af0349ad93edc75e53c2cc3557
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105069588"
---
# <a name="filter-the-additem-dialog-box-for-nested-projects"></a>İç içe projeler için AddItem iletişim kutusunu filtrele
İç içe geçmiş bir proje için bir **ek iletişim kutusu** görüntülediğinizde, ana proje iletişim kutusunda hangi öğelerin görüntülendiğini denetleyebilir.

 Arabirim, ek <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2> bir iletişim kutusunda olacak düğümleri filtrelemenizi sağlar.  Alt proje **AddItem** iletişim kutusunu görüntülediğinde, üst öğe `IVsFilterAddProjectItemDlg` arabirimi uygulayabilir ve aksi takdirde alt öğe projesinde görüntülenecek öğeleri filtreleyebilirsiniz.

 Projeler belirli üst projeler altında işleve göre gruplandırılırken, `IVsFilterAddProjectItemDlg` kullanıcının iç içe geçmiş bir projedeki kısayol menüsünde **Proje öğesi Ekle** ' yi seçtiği zaman uygulayabilirsiniz. `IvsFilterAddProjectItemDlg displays`Yalnızca proje öğeleri veya bu gruba özgü dosyalar uygulama. Diğer gruplar için proje öğeleri, aynı dizinde depolansalar bile iletişim kutusunda filtrelenirler.

 Bir kullanıcı alt öğe için **AddItem** iletişim kutusunu açtığında, ana projenin `IVsFilterAddProjectItemDlg` arabirim uygulanması çağrılır.

 `IVsFilterAddProjectItemDlg`Arabirim filtreleme kategorisine göre de uygulanabilir. Daha fazla bilgi için bkz. [Yeni öğe Ekle iletişim kutusuna öğe ekleme](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md) ve [Proje ve öğe şablonlarını kaydetme](../../extensibility/internals/registering-project-and-item-templates.md).

## <a name="see-also"></a>Ayrıca bkz.
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>
- [Yeni öğe Ekle iletişim kutusuna öğe ekleme](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)
- [Proje ve öğe şablonlarını Kaydet](../../extensibility/internals/registering-project-and-item-templates.md)
- [İç içe projeler](../../extensibility/internals/nesting-projects.md)
