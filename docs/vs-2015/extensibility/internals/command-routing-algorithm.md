---
title: Komut yönlendirme algoritması | Microsoft Docs
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
- commands, routing
- command routing
ms.assetid: 998b616b-bd08-45cb-845f-808efb8c33bc
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 44fc431f008c59a7d4ceff2d9b9ec14d85091daf
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51727997"
---
# <a name="command-routing-algorithm"></a>Komut Yönlendirme Algoritması
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Visual Studio'da komutlar çeşitli farklı bileşenler tarafından işlenir. Komutlar, en dıştaki (genel olarak da bilinir) bağlamına geçerli seçime göre en içteki bağlamından yönlendirilir. Daha fazla bilgi için [kullanılabilirlik](../../extensibility/internals/command-availability.md).  
  
## <a name="order-of-command-resolution"></a>Komut çözüm sırası  
 Komutları komut içeriğini aşağıdaki düzeylerde geçirilir:  
  
1.  Add-Ins: Ortam mevcut olan eklentileri komutu ilk sunar.  
  
2.  Öncelik komutları: şu komutları kullanarak kaydedilen <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterPriorityCommandTarget>. Bunlar, Visual Studio'da her komut için çağrılır ve kayıtlı olan sırayla çağrılır.  
  
3.  Bağlam menüsü komutları: tipik yönlendirme için bağlam menüsünü ve sonra sağlanan komut hedefi için bir bağlam menüsünde bulunan bir komut ilk sunulur.  
  
4.  Araç çubuğu komut hedefleri ayarlayın: Bu komut hedefleri çağırdığınızda kayıtlı <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell4.SetupToolbar2%2A>. `pCmdTarget` Parametresi `null`. Değilse `null`, bu komut hedefi ayarladığınız araç çubuğunda bulunan herhangi bir komut güncelleştirmek için kullanılır. Shell araç ayarlıyor sonra pencere çerçevesi olarak geçirir `pCmdTarget` böylece komutları araç akışınız pencere çerçevesi aracılığıyla yapılan tüm güncelleştirmeler bile olmadığı odakta.  
  
5.  Araç penceresi: Genellikle uygulayan bir windows aracı <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> arabirimi, aynı zamanda uygulamalıdır <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> araç penceresi etkin pencere olduğunda, Visual Studio komut hedefi alabilmesi arabirim. Ancak, araç penceresi, odak ise **proje** penceresini, sonra komutu yönlendirileceğini <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> seçilen öğelerin ortak üst arabirimi. Bu seçim birden çok projeleri yayılmış durumdaysa komutu yönlendirilir <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution> hiyerarşisi. <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> Arabirimi içeren <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A> ve <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.ExecCommand%2A> ilgili komutları için benzer yöntemler <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> arabirimi.  
  
6.  Belge penceresi: komut RouteToDocs bayrağı, .vsct dosyası içinde olarak varsa, Visual Studio bir komut hedefi üzerinde ya da belge view nesnesinin bir örneğini arar bir <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> arabirimi ya da bir belge nesnesi örneğini (genellikle bir <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines>arabirimi veya <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> arabirimi). Belge view nesnesinin komutu desteklemiyorsa, Visual Studio komutu yönlendiren <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> döndürülen arabirimi. (İsteğe bağlı bir arabirim belge veri nesneleri için budur.)  
  
7.  Geçerli hiyerarşi: geçerli hiyerarşi etkin belge penceresini veya Seçili hiyerarşiyi sahibi olan projenin olabilir **Çözüm Gezgini**. Visual Studio arar <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> geçerli ya da etkin hiyerarşisini uygulanan arabirimi. Hiyerarşi, proje öğesinin bir belge penceresi odağa sahip olsa bile hiyerarşi etkin olduğunda, geçerli olan komutlar desteklemelidir. Ancak, yalnızca geçerli komutları **Çözüm Gezgini** sahip odak kullanarak desteklenmelidir <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> arabirimi ve kendi <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A> ve <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.ExecCommand%2A>yöntemleri.  
  
     **Kes**, **kopyalama**, **Yapıştır**, **Sil**, **Yeniden Adlandır**, **girin**ve **DoubleClick** komutları özel işleme gerektirir. Nasıl yönetileceği hakkında bilgi için **Sil** ve **Kaldır** hiyerarşileri komutlarında bkz <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyDeleteHandler> arabirimi.  
  
8.  Genel: bir komut tarafından daha önce bahsedilen bağlamları işlenen değil, Visual Studio uygulayan bir komut sahibi VSPackage yönlendirmek çalışır <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> arabirimi. VSPackage'ı zaten yüklü değil, Visual Studio çağırdığında yüklenmez <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> yöntemi. VSPackage'ı yalnızca yüklenen <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> yöntemi çağrılır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Komut Tasarımı](../../extensibility/internals/command-design.md)

