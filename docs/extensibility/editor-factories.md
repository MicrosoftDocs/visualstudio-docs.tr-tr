---
title: Düzenleyici fabrikaları | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - editor factories
ms.assetid: cf4e8164-3546-441d-b465-e8a836ae7216
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 9f4dc0eca2c74161abb9cc4afe3917a160a18422
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49933137"
---
# <a name="editor-factories"></a>Düzenleyici fabrikaları
Bir düzenleyici fabrikası Düzenleyicisi nesneleri oluşturur ve bunları fiziksel bir görünüm olarak bilinen bir pencere çerçevesi koyar. Belge verileri ve düzenleyiciler ve tasarımcılar oluşturmak için gerekli olan belge görünümü nesneleri oluşturur. Bir düzenleyici fabrikası, Visual Studio çekirdek Düzenleyicisi ve herhangi bir standart düzenleyici oluşturmak için gereklidir. Özel bir düzenleyici Ayrıca isteğe bağlı olarak bir düzenleyici fabrikası ile oluşturulabilir.  
  
 Uygulayarak bir düzenleyici fabrikası oluşturma <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> arabirimi. Aşağıdaki örnek nasıl uygulanacağını göstermektedir <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> Düzenleyici fabrikası oluşturmak için:  
  
 [!code-vb[VSSDKEditorFactories#1](../extensibility/codesnippet/VisualBasic/editor-factories_1.vb)]
 [!code-csharp[VSSDKEditorFactories#1](../extensibility/codesnippet/CSharp/editor-factories_1.cs)]  
  
 Bu düzenleyici tarafından işlenen bir dosya türünü açmayı ilk kez bir düzenleyici yüklenir. Belirli bir düzenleyici veya varsayılan Düzenleyicisi'ni açmak seçebilirsiniz. Varsayılan Düzenleyicisi'ni seçerseniz, tümleşik geliştirme ortamı (IDE) açmak için doğru Düzenleyicisi belirler ve ardından açılır. Daha fazla bilgi için [belirlemek hangi Düzenleyicisi, bir projede bir dosya açar](../extensibility/internals/determining-which-editor-opens-a-file-in-a-project.md).  
  
## <a name="register-editor-factories"></a>Düzenleyici üreteçlerini kaydedin  
 Oluşturduğunuz bir düzenleyici kullanabilmeniz için önce işleyebileceği dosya uzantılarını da dahil olmak üzere, bunlar hakkında bilgi kaydetmeniz gerekir.  
  
 VSPackage, yönetilen kodda yazılır, yönetilen paket Framework (MPF) yöntemi kullanabileceğiniz <xref:Microsoft.VisualStudio.Shell.Package.RegisterEditorFactory%2A> , VSPackage yüklendikten sonra Düzenleyici fabrikası kaydedilecek. Yönetilmeyen kodda yazılmış, VSPackage'ı sonra Düzenleyici fabrikası kullanarak kaydetmelisiniz <xref:Microsoft.VisualStudio.Shell.Interop.SVsRegisterEditors> hizmeti.  
  
### <a name="register-an-editor-factory-by-using-managed-code"></a>Yönetilen kod kullanarak bir düzenleyici üreteci kaydettirir.  
 VSPackage içinde 's, düzenleyici fabrikası kaydetmelisiniz `Initialize` yöntemi. İlk çağrı `base.Initialize`ve sonra çağrı <xref:Microsoft.VisualStudio.Shell.Package.RegisterEditorFactory%2A> her Düzenleyici fabrikası için  
  
 Yönetilen kodda bir düzenleyici fabrikası kaydını kaldırmak için gerek yoktur VSPackage'ı bu sizin için işleyecek olduğundan. Ayrıca, düzenleyici fabrikası uyguluyorsa <xref:System.IDisposable>, kaydı olduğunda otomatik olarak kapatılır.  
  
### <a name="register-an-editor-factory-by-using-unmanaged-code"></a>Yönetilmeyen kod kullanarak bir düzenleyici üreteci kaydettirir.  
 İçinde <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> Düzenleyicisi paketinizi kullanmak için uygulama `QueryService` çağrılacak yöntem `SVsRegisterEditors`. Bunun yapılması, bir işaretçi döndürür <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterEditors>. Çağrı <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterEditors.RegisterEditor%2A> uygulamanıza geçirerek yöntemi <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> arabirimi. Ygula gerekir <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> ayrı bir sınıf.  
  
## <a name="the-editor-factory-registration-process"></a>Düzenleyici fabrikası kayıt işlemi  
 Visual Studio Düzenleyicisi Fabrika kullanarak düzenleyiciniz yüklediğinde aşağıdaki süreç gerçekleşir:  
  
1. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Proje sistem çağrıları <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>.  
  
2. Bu yöntem, düzenleyici üreteci döndürür. Visual Studio gecikmeler ancak, düzenleyicinin paket proje Sistemi Düzenleyicisi gerçekten gereken kadar yükleniyor.  
  
3. Visual Studio Proje Sistemi Düzenleyicisi gerektiğinde, çağıran <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>, hem belge görünümü hem de belge veri nesneleri döndüren özel bir yöntem.  
  
4. Varsa, düzenleyici fabrikası kullanarak Visual Studio tarafından çağıran <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> hem bir belge veri nesnesi hem de bir belge görünümü nesnesi döndürür, Visual Studio sonra belge penceresi oluşturur, belge view nesnesinin yerleştirir ve çalışan belgeye bir giriş yapar Belge veri nesnesi için tablo (RDT).  
  
## <a name="see-also"></a>Ayrıca bkz.  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory>   
 [çalıştırılan Belge tablosu](../extensibility/internals/running-document-table.md)