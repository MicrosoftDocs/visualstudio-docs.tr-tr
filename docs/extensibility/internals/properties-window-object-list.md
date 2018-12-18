---
title: Özellikler penceresi nesne listesi | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Properties window, object list
ms.assetid: 6c159c9d-345d-4b23-8ddd-9839d338b62f
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b6b7d238f7ce64122ac18a52dab59afb063ce47e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31130142"
---
# <a name="properties-window-object-list"></a>Özellikler penceresi nesne listesi
Nesne listesinde **özellikleri** penceredir açılan listesini diğer nesnelere bir veya daha fazla seçili Windows'a kullanılabilir seçimi değiştirmenize izin verir. Bu liste içinde farklı bir nesne seçerek tetikleyen bir çağrı <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.SelectObjects%2A> ortamında yeni bir nesne seçili olduğunu bildirmek için. Görüntülenen bilgileri **özellikleri** penceresi yeni seçilen nesnesiyle ilişkili özellikleri göstermek için sonra değiştirilir.  
  
## <a name="the-object-list"></a>Nesne listesi  
 Nesne listesi iki alandan oluşur: nesne adı (kalın olarak gösterilir) ve nesne türü.  
  
 Kalın yazı tipiyle nesne türünün solunda görüntülenen nesne adı nesnesinden alınır kullanarak `Name` özelliği tarafından sağlanan <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo> arabirimi. <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo.GetClassInfo%2A>, yalnızca yönteme <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo>, döndürür <xref:Microsoft.VisualStudio.OLE.Interop.ITypeInfo> bu arabirimin coclass'ı için. **Özellikleri** penceresi kullanır <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo> aşağı açılan listesinde nesne adı olarak gösterilen coclass adını almak için.  
  
 Nesne yoksa bir `Name` özelliği, bir ad nesne listesine ad alanında görüntülenmez. Nesne listesinde görüntülenen ad istiyorsanız, Name özelliği nesnesine ekleyebilirsiniz.  
  
 COM nesnesi uygulamazsa <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo>, **özellikleri** penceresi, listenin sol tarafında nesne adı yerine arabirimi adı görüntüler.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Özellikleri Genişletme](../../extensibility/internals/extending-properties.md)