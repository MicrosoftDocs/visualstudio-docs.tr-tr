---
title: Kaynak denetim paketleri için model | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], model
ms.assetid: 6164b2d3-a622-4de8-bef3-a6de985e9ebd
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: fa0dcdd930412e4e53c59509848f0b7c1503c47b
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31129449"
---
# <a name="model-for-source-control-packages"></a>Kaynak denetim paketleri için modeli
Aşağıdaki modeli kaynak denetim uygulaması örneği temsil eder. Modeldeki uygulamanız gereken arabirimleri ve çağırmalısınız Ortam Hizmetleri bakın. Tüm hizmetler gibi gerçekten hizmeti aracılığıyla elde belirli bir arabirim yöntemleri çağırın. Sınıf adları, kaynak denetimi nasıl gerçekleştirildiği görmeyi kolaylaştırmak için tanımlanır.  
  
 ![SCC&#95;TUP örnekler](../../extensibility/internals/media/scc_tup.gif "SCC_TUP")  
Örnek kaynak denetimi projesi  
  
## <a name="interfaces"></a>Arabirimler  
 Aşağıdaki tabloda gösterilen arabirimleri listesini kullanarak Visual Studio'da yeni proje türlerinizi için kaynak denetimi uygulayabilirsiniz.  
  
|Arabirim|Bir yönetim grubuna bağlanmak veya bağlı bir yönetim grubunun özelliklerini düzenlemek için Yönetim çalışma alanında|  
|---------------|---------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>|Projeler ve bunlar kaydedin veya değiştirme (olumsuz) dosyaları önce düzenleyiciler tarafından çağrılır. Bu arabirim kullanılarak erişilir <xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave> hizmet.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>|Projeleri ekleyin, kaldırın veya bir dosya veya dizin yeniden adlandırma izni istemek için tarafından çağrılır. Bu arabirim, onaylanmış bir Ekle kaldırdığınızda veya eylem yeniden adlandırmak ortamı tamamlandıktan bildirmek için göre projeleri olarak da adlandırılır. Kullanılarak erişilir <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments> hizmet.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>|Projeleri eklediğinizde bildirilmesi kaydeder herhangi bir varlık tarafından uygulanan, yeniden adlandırın veya bir dosya veya dizin kaldırın. Olay bildirimi için kaydolmaya çağrısı <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2.AdviseTrackProjectDocumentsEvents%2A>.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>|Kaynak denetimi paketiyle kaydetmek ve kaynak denetimi durumu hakkında bilgi edinmek için projeler tarafından çağrılır. Bu arabirim kullanılarak erişilir <xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager> hizmet.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>|Proje dosyaları hakkında bilgi için kaynak denetimi isteklere yanıt verecek şekilde ve kaynak proje dosyası için gerekli denetim ayarlarını almak için tarafından uygulanır.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2.AdviseTrackProjectDocumentsEvents%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>   
 [Kaynak Denetimini Destekleme](../../extensibility/internals/supporting-source-control.md)