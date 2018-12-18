---
title: Kaldırma ve yeniden yüklemeyi konuları iç içe projeleri | Microsoft Docs
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
- nested projects, unloading and reloading
- projects [Visual Studio SDK], unloading and reloading nested
ms.assetid: 06c3427e-c874-45b1-b9af-f68610ed016c
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 28c5ba7dffecd73556a5f963c471910bb190f1db
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51756963"
---
# <a name="considerations-for-unloading-and-reloading-nested-projects"></a>İç İçe Projeleri Kaldırma ve Yeniden Yükleme Konusunda Dikkat Edilmesi Gerekenler
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

İç içe proje türleri uyguladığınızda, kaldırma ve projeleri yeniden ek adımları gerçekleştirmeniz gerekir. Doğru dinleyicileri çözüm olayları bildirmek için doğru şekilde yükseltmeniz gerekir `OnBeforeUnloadProject` ve `OnAfterLoadProject` olayları.  
  
 Bir neden bu olaylar bu şekilde yükseltmeniz gerekir: kaynak kodu denetimi öğeleri sunucudan silin ve varsa bunları tekrar yeni bir şey ekleyin (SCC) istemediğiniz bir `Get` SCC işlemi. Bu durumda, yeni bir dosya SCC dışında yüklenir ve kaldırma ve bunlar farklı olması durumunda tüm dosyaları yeniden yüklemek zorunda. SCC çağrıları `ReloadItem`. Projeyi silin ve yeniden uygulayarak yeniden oluşturmak için uygulamanız bu çağrının olan `IVsFireSolutionEvents` çağrılacak `OnBeforeUnloadProject` ve `OnAfterLoadProject`. Bu uygulama gerçekleştirdiğinizde, SCC proje geçici olarak silindi ve tekrar eklenmelidir, bilgisi verilir. Bu nedenle, SCC proje gerçekten sunucudan silinir ve yeniden eklenmesi gibi proje üzerinde çalışmaz.  
  
## <a name="reloading-projects"></a>Projeler yeniden yükleniyor  
 İç içe projeler yeniden yükleniyor desteklemek için uygulamanız <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.ReloadItem%2A> yöntemi. Uygulamanızda `ReloadItem`, iç içe projeler kapatın ve sonra yeniden oluşturun.  
  
 Genellikle bir proje yeniden yüklendiğinde, IDE başlatır <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnBeforeUnloadProject%2A> ve `M:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterLoadProject(Microsoft.VisualStudio.Shell.Interop.IVsHierarchy,Microsoft.VisualStudio.Shell.Interop.IVsHierarchy)` olayları. Ancak, silinmesi ve yeniden iç içe projeler için ana proje işlemi, IDE başlatır. Ana proje çözüm olayları oluşturmaz ve IDE başlatma işleminin hakkında bir bilgi bulunmaz çünkü olaylar oluşmaz.  
  
 Bu işlem, ana proje aramaları işlenecek `QueryInterface` üzerinde <xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents> kapalı arabirim <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution> arabirimi. `IVsFireSolutionEvents` yükseltmek için IDE bildiren bir işleve sahiptir `OnBeforeUnloadProject` iç içe geçmiş projeyi kaldırmak ve ardından yükseltmek için olay `OnAfterLoadProject` olayı aynı projeyi yeniden yükleyin.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3>   
 [Projeleri İç İçe Geçirme](../../extensibility/internals/nesting-projects.md)

