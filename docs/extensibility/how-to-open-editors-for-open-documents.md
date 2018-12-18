---
title: 'Nasıl yapılır: açık belgeler için düzenleyicileri açma | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], opening for open documents
ms.assetid: 1a0fa49c-efa4-4dcc-bdc0-299b7052acdc
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 05e91dd296958e44d0c06f2b77d410efdd71fb1c
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49823131"
---
# <a name="how-to-open-editors-for-open-documents"></a>Nasıl yapılır: açık belgeler için düzenleyicileri açma
Bir belge penceresi bir proje açmadan önce proje önce dosyanın zaten başka bir düzenleyici belge penceresinde açık olup olmadığını belirlemeniz gerekir. Dosya ya da açık bir projeye özgü düzenleyicisinde olabilir ya da standart düzenleyicileri birini kayıtlı [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
## <a name="open-a-project-specific-editor"></a>Bir projeye özgü Düzenleyicisi'ni açın  
 Zaten açık olan bir dosya için bir projeye özgü düzenleyicisini açmak için aşağıdaki yordamı kullanın.  
  
### <a name="to-open-a-project-specific-editor-for-an-open-file"></a>Açık bir dosya için bir projeye özgü düzenleyicisini açmak için  
  
1. Çağrı <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.IsDocumentOpen%2A> yöntemi.  
  
    Bu çağrı uygunsa belgenin hiyerarşi, hiyerarşi öğesini ve pencere çerçevesi için işaretçiler döndürür.  
  
2. Belge açıksa, projeyi yalnızca bir belge veri nesnesi var olup olmadığını veya belge görünümü nesnesi varsa emin olmanız gerekir.  
  
   - Belge Görünümü nesne var ve bu görünüm bir hiyerarşi öğesini veya farklı hiyerarşi için ise, proje var olan pencereyi resurface için Görünüm penceresi çerçeve işaretçisi kullanır.  
  
   - Temel alınan belge veri nesnesine ekleyebilirsiniz, bir belge görünümü nesne var ve bu görünüm aynı hiyerarşiye ve hiyerarşi öğesini için ise, ikinci bir görünüm projeyi açabilirsiniz. Aksi takdirde, proje var olan pencereyi resurface için Görünüm penceresi çerçeve işaretçisi kullanmanız gerekir.  
  
   - Yalnızca belge veri nesnesi varsa, projeyi, belge veri nesnesi, görünüm için kullanıp kullanamayacağını belirlemeniz gerekir. Belge veri nesnesi uyumlu ise, tam adımlar ele [açık bir projeye özgü düzenleyici](../extensibility/how-to-open-project-specific-editors.md).  
  
     Belge veri nesnesi uyumlu değilse, kullanıcıya dosyası şu anda kullanımda olduğunu belirten bir hata görüntülenmesi gerekir. Bir dosyayı aynı anda derlendiğinde kullanıcı dışındaki bir düzenleyiciyi kullanarak dosyayı açmaya çalışıyor gibi bu hata yalnızca geçici durumlarda, görüntülenmesi gereken [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] temel metin düzenleyicisi. Temel metin düzenleyici, derleyici ile belge veri nesnesi paylaşabilirsiniz.  
  
3. Belge veri nesnesi ya da belge görünümü nesnesi olduğundan belgeyi açık değilse, adımları tamamlamanız [açık bir projeye özgü düzenleyici](../extensibility/how-to-open-project-specific-editors.md).  
  
## <a name="open-a-standard-editor"></a>Açık bir standart Düzenleyici  
 Aç zaten bir dosya için standart bir düzenleyicisini açmak için aşağıdaki yordamı kullanın.  
  
### <a name="to-open-a-standard-editor-for-an-open-file"></a>Açık bir dosya için standart bir düzenleyicisini açmak için  
  
1.  Çağrı <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>.  
  
     Bu yöntem ilk belge zaten çağırarak açık olmadığını doğrular <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.IsDocumentOpen%2A>. Belge zaten açık değilse, düzenleyici penceresinde resurfaced.  
  
2.  Belgenin açık değilse, ardından bölümünde bulunan adımları tamamladığınızdan [nasıl yapılır: standart düzenleyicileri açma](../extensibility/how-to-open-standard-editors.md).  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Açın ve proje öğeleri Kaydet](../extensibility/internals/opening-and-saving-project-items.md)   
 [Nasıl yapılır: projeye özgü düzenleyicileri açma](../extensibility/how-to-open-project-specific-editors.md)   
 [Nasıl yapılır: standart düzenleyicileri açma](../extensibility/how-to-open-standard-editors.md)
