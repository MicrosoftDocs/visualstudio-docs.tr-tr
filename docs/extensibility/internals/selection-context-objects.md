---
title: Seçim bağlamı nesneleri | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- selection, tracking
- selection, context objects
ms.assetid: 7308ea8f-a42c-47e5-954e-7dee933dce7a
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: f09bcb260f4edd09045f860ed08d951622e54a5d
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49913169"
---
# <a name="selection-context-objects"></a>Seçim Bağlamı Nesneleri
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Tümleşik geliştirme ortamı (IDE), IDE'de görüntülenmesi gerektiğini belirlemek için bir genel seçimi bağlam nesnesi kullanır. Her bir pencere IDE içindeki genel seçimi bağlamına gönderilen kendi seçimi bağlam nesnesi olabilir. Bu pencere odaklandığında IDE genel seçim bağlamını penceresinden değerlerini güncelleştirir. Daha fazla bilgi için [kullanıcıya geri bildirim](../../extensibility/internals/feedback-to-the-user.md).  
  
 Her bir pencere çerçevesi veya IDE içindeki site adı verilen bir hizmet olan <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection>. Pencere çerçevesinde tarihli, VSPackage'ı tarafından oluşturulan nesne çağırmalıdır `QueryService` işaretçisi almak için yöntemi <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection> arabirimi.  
  
 Çerçeve pencereleri başlatıldıklarında tablolarınızda genel seçimi bağlamına seçim bağlamı bilgilerine bölümlerini tutabilirsiniz. Bu özellik ile boş bir seçim Başlat gerekebilir araç pencereleri için kullanışlıdır.  
  
 VSPackage izleyebilirsiniz genel seçim bağlamı Tetikleyicileri olayı değiştirme. VSPackage uygulayarak aşağıdaki görevleri gerçekleştirebilirsiniz `IVsTrackSelectionEx` ve <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection> arabirimleri:  
  
- Bir hiyerarşide o anda etkin dosyasını güncelleştirin.  
  
- Öğelerin belirli türlerini değişiklikleri izleyin. Örneğin, bir özel, VSPackage'ı kullanıyorsa, **özellikleri** penceresinde etkin değişiklikleri izleyebilirsiniz **özellikleri** penceresi ve sizinki gerektiğinde yeniden başlatın.  
  
  İzleme seçimi normal çalıştıysa aşağıdaki sırayı gösterir.  
  
1.  IDE yeni açılan penceresinde seçim bağlamını alır ve genel seçimi bağlamda koyar. Seçim bağlamını HIERARCHY_DONTPROPAGATE veya SELCONTAINER_DONTPROPAGATE kullanıyorsa, bu bilgileri için genel bağlamda dağıtılmadı. Daha fazla bilgi için [kullanıcıya geri bildirim](../../extensibility/internals/feedback-to-the-user.md).  
  
2.  Bildirim olayları, bunlar istenen herhangi VSPackage yayınlanır.  
  
3.  VSPackage'ı bir aracı veya diğer benzer görevleri yeniden etkinleştirme bir hiyerarşi, güncelleştirme gibi etkinlikleri gerçekleştirerek aldığı olaylar üzerinde çalışır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection>   
 [Visual Studio'da hiyerarşiler](../../extensibility/internals/hierarchies-in-visual-studio.md)   
 [Seçim ve para birimi IDE](../../extensibility/internals/selection-and-currency-in-the-ide.md)   
 [Proje Türleri](../../extensibility/internals/project-types.md)