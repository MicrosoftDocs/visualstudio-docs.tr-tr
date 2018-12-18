---
title: Özellikler penceresi nesne listesi | Microsoft Docs
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
- Properties window, object list
ms.assetid: 6c159c9d-345d-4b23-8ddd-9839d338b62f
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: bbb9153a216b2d2fcc7cdeba0399aa60fc73881e
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51768903"
---
# <a name="properties-window-object-list"></a>Özellikler Penceresi Nesne Listesi
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Nesne listesinde **özellikleri** bir veya daha fazla seçili pencereleri içinde kullanılabilir olan diğer nesnelerin seçimini değiştirmek izin veren bir açılır listede bir penceredir. Bu listede farklı bir nesne seçmek için bir çağrı tetikler <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.SelectObjects%2A> yeni bir nesne seçili ortam bildirmek için. Görüntülenen bilgileri **özellikleri** penceresi yeni seçilen bir nesneyle ilişkili özellikleri görüntülemek için sonra değiştirilir.  
  
## <a name="the-object-list"></a>Nesne listesi  
 Nesne listesine iki alandan oluşur: nesne adı (kalın olarak gösterilir) ve nesne türü.  
  
 Soldaki kalın nesne türü için görüntülenen nesne adı nesnesinden alınır kullanarak `Name` özelliği tarafından sağlanan <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo> arabirimi. <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo.GetClassInfo%2A>, yalnızca metottaki <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo>, döndürür <xref:Microsoft.VisualStudio.OLE.Interop.ITypeInfo> o arabirimin coclass'ı için. **Özellikleri** penceresi kullanan <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo> aşağı açılan listesinde nesne adı olarak gösterilen coclass adı.  
  
 Nesne yoksa bir `Name` özelliği, bir ad nesne listesinin adı alanında görüntülenmez. Nesne listesinde görüntülenen adını isterseniz nesnesine Name özelliği ekleyebilirsiniz.  
  
 COM nesnesi uygulamazsa <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo>, **özellikleri** penceresinde, listenin sol tarafında arabirim adını nesne adının yerine görüntülenir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Özellikleri Genişletme](../../extensibility/internals/extending-properties.md)

