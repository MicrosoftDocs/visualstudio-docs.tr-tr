---
title: Kaynak denetimi paketleri için model | Microsoft Docs
description: Bu model bir kaynak denetim uygulamasını temsil eder. Makale, kaynak denetiminin nasıl yapıldığını görmeyi kolaylaştırmak için sınıfların adlarını gösterir.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], model
ms.assetid: 6164b2d3-a622-4de8-bef3-a6de985e9ebd
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: e4e437afdfa0d3de03da6814e221840cbd0763fd
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105063207"
---
# <a name="model-for-source-control-packages"></a>Kaynak Denetimi Paketleri için Model
Aşağıdaki model, kaynak denetimi uygulamasına bir örnek temsil eder. Modelinde, uygulamanız gereken arabirimleri ve çağırmanız gereken ortam hizmetlerini görürsünüz. Tüm hizmetler gibi, aslında hizmet yoluyla elde ettiğiniz belirli bir arabirimin yöntemlerini çağırabilirsiniz. Sınıfların adları, kaynak denetiminin nasıl yapıldığını görmeyi kolaylaştırmak için tanımlanır.

 ![SCC&#95;örneği örnekleri](../../extensibility/internals/media/scc_tup.gif "SCC_TUP") Örnek kaynak denetimi projesi

## <a name="interfaces"></a>Arabirimler
 Aşağıdaki tabloda gösterilen arabirimlerin listesini kullanarak Visual Studio 'da yeni proje türleriniz için kaynak denetimi uygulayabilirsiniz.

|Arabirim|Kullanın|
|---------------|---------|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>|Dosyalar kaydedilmeden veya değiştirmeden önce projeler ve düzenleyicilerle çağırılır. Bu arabirime hizmet kullanılarak erişilir <xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave> .|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>|Bir dosya veya dizin ekleme, kaldırma veya yeniden adlandırma izni istemek için projeler tarafından çağırılır. Bu arabirim, bir onaylanan ekleme, kaldırma veya yeniden adlandırma eylemi tamamlandığında ortamı bilgilendirmek için projeler tarafından da çağrılır. Hizmet kullanılarak erişilir <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments> .|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>|Projeler bir dosya veya dizin ekler, yeniden adlandırdığınızda veya kaldırırken bildirim almak üzere kaydeden herhangi bir varlık tarafından uygulanır. Olay bildirimine kaydolmak için çağrısı yapın <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2.AdviseTrackProjectDocumentsEvents%2A> .|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>|Kaynak denetim paketiyle kaydolmak ve kaynak denetimi durumu hakkında bilgi almak için projeler tarafından çağırılır. Bu arabirime hizmet kullanılarak erişilir <xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager> .|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>|Dosyalar hakkında bilgi edinmek ve proje dosyası için gereken kaynak denetimi ayarlarını almak için proje tarafından uygulanır.|

## <a name="see-also"></a>Ayrıca bkz.
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2.AdviseTrackProjectDocumentsEvents%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>
- [Kaynak Denetimini Destekleme](../../extensibility/internals/supporting-source-control.md)
