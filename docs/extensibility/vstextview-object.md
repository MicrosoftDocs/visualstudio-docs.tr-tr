---
title: VSTextView nesnesi | Microsoft Docs
description: VSTextView nesnesi, kullanıcıların metin arabelleğinin Unicode metnini görüntülemesine ve düzenlemesine izin veren bir penceredir.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- VSTextView
helpviewer_keywords:
- VSTextView object, reference
- views [Visual Studio SDK], reference
ms.assetid: 78272ddc-9718-4c65-a94e-a44a2e8d54f4
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 90fad54be26c11db31d649d0ae6b25c108a6b361
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112905169"
---
# <a name="vstextview-object"></a>VSTextView nesnesi

Metin görünümü, kullanıcıların metin arabelleğinin Unicode metnini görüntülemesine ve düzenlemesine izin veren bir penceredir. Esas olarak görünüm, çoğu kullanıcının düzenleyici olarak başvurduğu şeydir. Görünüm, çeşitli metin katmanları (sözcük kaydırması, anahat metni vb.) tarafından arabelleğinden ayrıldığından, bu görünümün arabellekteki metnin tam bir gösterimi olması garanti edilmez. Metin görünümü hakkında daha fazla bilgi için, bkz. [eskı API kullanarak metin görünümüne erişme](/previous-versions/visualstudio/visual-studio-2015/extensibility/accessing-thetext-view-by-using-the-legacy-api?preserve-view=true&view=vs-2015).

Aşağıdaki tabloda, nesnesindeki arabirimler gösterilmektedir <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView> .

|Arabirim|Açıklama|
|---------------|-----------------|
|[IDropSource](/windows/desktop/api/oleidl/nn-oleidl-idropsource)|Standart OLE arabirimi.|
|<xref:Microsoft.VisualStudio.OLE.Interop.IDropTarget>|Standart OLE arabirimi.|
|<xref:Microsoft.VisualStudio.OLE.Interop.IObjectWithSite>|Standart OLE arabirimi.|
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|Standart OLE arabirimi.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompoundAction>|Bileşik eylemlerin (yani, tek bir geri alma/yineleme biriminde gruplanmış eylemler) oluşturulmasına izin vermez.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>|, Görünümü yönetmek ve bunlara erişmek için temel yöntemleri sağlar. `IVsTextView` iş parçacıklı güvenli değildir.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane>|Bir pencere bölmesi oluşturur ve yönetir.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLayeredTextView>|Metin katmanlarla etkileşime girer.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsThreadSafeTextView>|Farklı bir iş parçacığından görünüm üzerinde işlemler gerçekleştirir.|

## <a name="see-also"></a>Ayrıca bkz.

- [Şekil düzenleme](https://www.microsoft.com/download/details.aspx?id=55984)
- [VSTextBuffer nesnesi](../extensibility/vstextbuffer-object.md)