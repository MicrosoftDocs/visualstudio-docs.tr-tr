---
title: Verilere Windows Forms denetimleri bağlama
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- data [Windows Forms], data sources
- Windows Forms, data binding
- Windows Forms, displaying data
- displaying data on forms
- forms, displaying data
- data sources, displaying data
- displaying data, Windows Forms
- data [Windows Forms], displaying
ms.assetid: 243338ef-41af-4cc5-aff7-1e830236f0ec
caps.latest.revision: 40
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 5fff4a06ab49caea8ad307ba24d88a46eae87692
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53053308"
---
# <a name="bind-windows-forms-controls-to-data-in-visual-studio"></a>Visual Studio'da verilere Windows Forms denetimleri bağlama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]


Windows Forms veri bağlama ile uygulamanızın kullanıcılarına verileri görüntüleyebilirsiniz. Bu verilere bağlı denetimler oluşturmak için öğeleri sürükleyebilirsiniz **veri kaynakları** penceresinden Windows Form Tasarımcısı'nda Visual Studio. Bu konuda en yaygın görevleri, araçları ve veri bağlantılı Windows Forms uygulamaları oluşturmak için gerekli sınıfların bazılarını açıklar.

 ![Veri kaynağı işlemi sürükleyin](../data-tools/media/raddata-data-source-drag-operation.png "raddata veri kaynağı işlemi sürükleyin")

 Visual Studio'da verilere bağlı denetimler oluşturma hakkında genel bilgi için bkz. [Visual Studio'da verilere denetimler bağlama](../data-tools/bind-controls-to-data-in-visual-studio.md). Windows Forms veri bağlama hakkında daha fazla bilgi için bkz: [Windows Forms veri bağlama](http://msdn.microsoft.com/library/c3826d8e-ea25-4ad4-a669-45bfb19192aa).

## <a name="in-this-section"></a>Bu bölümde

-   [Verilere Windows Forms denetimleri bağlama](../data-tools/bind-windows-forms-controls-to-data.md)

-   [Verileri kaydetmeden önce verilere bağlı denetimler üzerinde işlem içi düzenlemeler yürütme](../data-tools/commit-in-process-edits-on-data-bound-controls-before-saving-data.md)

-   [Windows Forms uygulamalarında arama tabloları oluşturma](../data-tools/create-lookup-tables-in-windows-forms-applications.md)

-   [Veri aramak için Windows Form oluşturma](../data-tools/create-a-windows-form-to-search-data.md)

-   [Basit veri bağlama modelini destekleyen bir Windows Forms kullanıcı denetimi oluşturma](../data-tools/create-a-windows-forms-user-control-that-supports-simple-data-binding.md)

-   [Karmaşık veri bağlama modelini destekleyen bir Windows Forms kullanıcı denetimi oluşturma](../data-tools/create-a-windows-forms-user-control-that-supports-complex-data-binding.md)

-   [Arama veri bağlama modelini destekleyen bir Windows Forms kullanıcı denetimi oluşturma](../data-tools/create-a-windows-forms-user-control-that-supports-lookup-data-binding.md)

-   [Formlar arasında veri geçirme](../data-tools/pass-data-between-forms.md)

## <a name="bindingsource-component"></a>BindingSource bileşeni
 <xref:System.Windows.Forms.BindingSource> Bileşen iki amaca hizmet eder. İlk olarak, form üzerindeki denetimleri için veri bağlama sırasında bir soyutlama katmanı sağlar. Form üzerinde denetimleri için ilişkili <xref:System.Windows.Forms.BindingSource> bileşen (yerine doğrudan bir veri kaynağına bağlanan).

 İkinci olarak, bu nesnelerin bir koleksiyonunu yönetebilirsiniz. Bir türe eklemek <xref:System.Windows.Forms.BindingSource> o türün bir liste oluşturur.

 Hakkında daha fazla bilgi için <xref:System.Windows.Forms.BindingSource> bileşeni için bkz:

-   [BindingSource Bileşeni](http://msdn.microsoft.com/library/3e2faf4c-f5b8-4fa6-9fbc-f59c37ec2fb9)

-   [BindingSource Bileşenine Genel Bakış](http://msdn.microsoft.com/library/be838caf-fcb0-4b68-827f-58b2c04b747f)

-   [BindingSource Bileşeni Mimarisi](http://msdn.microsoft.com/library/7bc69c90-8a11-48b1-9336-3adab5b41591)

## <a name="bindingnavigator-control"></a>BindingNavigator denetimi
 Bu bileşen, bir Windows uygulaması tarafından görüntülenen veriler aracılığıyla gezinmek için bir kullanıcı arabirimi sağlar. Daha fazla bilgi için [BindingNavigator denetimine](http://msdn.microsoft.com/library/18c1e2a5-9834-40d3-9b2e-2b545e4e769e).

## <a name="datagridview-control"></a>DataGridView denetimi
 Birçok farklı türde veri kaynaklarını gelen tablosal verileri görüntülemek ve düzenlemek için kullanın <xref:System.Windows.Forms.DataGridView> denetimi. Verilere bağlayabilirsiniz bir <xref:System.Windows.Forms.DataGridView> kullanarak <xref:System.Windows.Forms.DataGridView.DataSource%2A> özelliği. Daha fazla bilgi için [DataGridView denetimine genel bakış](http://msdn.microsoft.com/library/0a45c661-89dc-4390-9cc6-c47eee501488).

## <a name="see-also"></a>Ayrıca Bkz.
 [Visual Studio'da verilere denetimler bağlama](../data-tools/bind-controls-to-data-in-visual-studio.md)
