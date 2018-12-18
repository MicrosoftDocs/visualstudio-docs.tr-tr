---
title: Kaynak denetimi paketleri için model | Microsoft Docs
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
- source control [Visual Studio SDK], model
ms.assetid: 6164b2d3-a622-4de8-bef3-a6de985e9ebd
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 27bac56b862d4a3dfd0495420ee20920801faaae
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51734128"
---
# <a name="model-for-source-control-packages"></a>Kaynak Denetimi Paketleri için Model
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Şu model, bir kaynak denetim uygulaması örneğini temsil eder. Modelde, uygulamanız gereken arabirimleri ve çağırmalısınız Ortam Hizmetleri bakın. Tüm hizmetleri gibi aslında hizmeti yoluyla elde belirli bir arabirim yöntemlerini çağırın. Sınıfların adlarını, kaynak denetimi nasıl gerçekleştirildiği görmeyi kolaylaştırmak için tanımlanır.  
  
 ![SCC&#95;Kurulum örnekler](../../extensibility/internals/media/scc-tup.gif "SCC_TUP")  
Örnek kaynak denetimi projesi  
  
## <a name="interfaces"></a>Arabirimler  
 Aşağıdaki tabloda gösterilen arabirimlerin listesini kullanarak Visual Studio'da, yeni proje türleri için kaynak denetimi uygulayabilirsiniz.  
  
|Arabirim|Bir yönetim grubuna bağlanmak veya bağlı bir yönetim grubunun özelliklerini düzenlemek için Yönetim çalışma alanında|  
|---------------|---------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>|Projeler ve düzenleyiciler önce bunlar kaydetme ya da değişiklik (değişiklik içeriyor) dosyaları tarafından çağrılır. Bu arabirim kullanılarak erişilen <xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave> hizmeti.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>|Ekleme, kaldırma veya bir dosya veya dizin yeniden adlandırma izni istemek için projeleri tarafından çağrılır. Bu arabirim, onaylanmış bir ekleme kaldırdığınızda veya yeniden adlandırma eylemi ortam tamamlandıktan bildirmek için projeleri tarafından olarak da adlandırılır. Kullanılarak erişilen <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments> hizmeti.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>|Projeleri eklediğinizde, bildirim almak için kaydeden herhangi bir varlık tarafından gerçekleştirilen, yeniden adlandırmak veya bir dosya veya dizin kaldırın. Olay bildirimi için kaydolmak için çağrı <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2.AdviseTrackProjectDocumentsEvents%2A>.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>|Projeler kaynak denetimi paketi kaydetmek için ve kaynak denetimi durumu hakkında bilgi edinmek için tarafından çağrılır. Bu arabirim kullanılarak erişilen <xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager> hizmeti.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>|Dosyalar hakkında bilgi için kaynak denetimi isteklerine yanıt ve kaynak denetim ayarları için proje dosyasını gerekli edinmek için proje tarafından uygulanır.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2.AdviseTrackProjectDocumentsEvents%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>   
 [Kaynak Denetimini Destekleme](../../extensibility/internals/supporting-source-control.md)

