---
title: Bir Windows Forms uygulamasındaki verileri filtreleme ve sıralama
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- row states, filtering
- data views, sorting
- row version, filtering
- row states
- data views, filtering
- sorting datasets, using data views
- dataset filtering, using data views
ms.assetid: f4f100f1-776d-46dc-b2fd-5b35b98d9561
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 1868d670458e204f6e503b132aaceab17f3da742
ms.sourcegitcommit: 1df0ae74af03bcf0244129a29fd6bd605efc9f61
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/01/2018
ms.locfileid: "50750929"
---
# <a name="filter-and-sort-data-in-a-windows-forms-application"></a>Bir Windows Forms uygulamasındaki verileri filtreleme ve sıralama

Ayarlayarak verileri filtreleme <xref:System.Windows.Forms.BindingSource.Filter%2A> özelliğini istenen kayıtlar döndüren bir dize ifadesi.

Ayarlayarak verileri sıralamak <xref:System.Windows.Forms.BindingSource.Sort%2A> özelliğini sütun adına göre sıralamak isteyebilirsiniz; ekleme `DESC` azalan düzende sıralamak veya ekleme için `ASC` artan düzende sıralamak için.

> [!NOTE]
> Uygulamanızı kullanmıyorsa <xref:System.Windows.Forms.BindingSource> bileşenleri filtreleyebilirsiniz ve kullanarak verileri sıralama <xref:System.Data.DataView> nesneleri. Daha fazla bilgi için [DataViews](/dotnet/framework/data/adonet/dataset-datatable-dataview/dataviews).

## <a name="to-filter-data-by-using-a-bindingsource-component"></a>BindingSource bileşenini kullanarak verilere filtre uygulamak için

-   Ayarlama <xref:System.Windows.Forms.BindingSource.Filter%2A> özelliğini döndürmek istediğiniz ifade. Örneğin, aşağıdaki kod ile müşteriler döndürür bir `CompanyName` "B" ile başlar:

     [!code-csharp[VbRaddataDisplaying#6](../data-tools/codesnippet/CSharp/filter-and-sort-data-in-a-windows-forms-application_1.cs)]
     [!code-vb[VbRaddataDisplaying#6](../data-tools/codesnippet/VisualBasic/filter-and-sort-data-in-a-windows-forms-application_1.vb)]

## <a name="to-sort-data-by-using-a-bindingsource-component"></a>BindingSource bileşenini kullanarak verileri sıralama

-   Ayarlama <xref:System.Windows.Forms.BindingSource.Sort%2A> özelliğini sıralamak istediğiniz sütunu. Örneğin, aşağıdaki kod üzerinde müşterileri sıralar `CompanyName` azalan düzende sütun:

     [!code-csharp[VbRaddataDisplaying#7](../data-tools/codesnippet/CSharp/filter-and-sort-data-in-a-windows-forms-application_2.cs)]
     [!code-vb[VbRaddataDisplaying#7](../data-tools/codesnippet/VisualBasic/filter-and-sort-data-in-a-windows-forms-application_2.vb)]

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio'da verilere denetimler bağlama](../data-tools/bind-controls-to-data-in-visual-studio.md)