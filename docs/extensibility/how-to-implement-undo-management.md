---
title: 'Nasıl yapılır: uygulamak yönetim geri alma | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - undo management
ms.assetid: 1942245d-7a1d-4a11-b5e7-a3fe29f11c0b
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 227a002b5bd1b333da177944056eef7aca2cc393
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49830021"
---
# <a name="how-to-implement-undo-management"></a>Nasıl yapılır: uygulama geri alma yönetimi
Geri alma yönetimi için kullanılan birincil arabirimidir <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager>, ortamı tarafından gerçekleştirilir. Geri alma yönetimini desteklemek için ayrı geri alma birimi uygulayın (diğer bir deyişle, <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoUnit>, birden çok tek tek adımları içerebilir.  
  
 Geri alma yönetim nasıl uygulayacağınıza düzenleyiciniz birden çok görünüm veya destekleyip desteklemediğini bağlı olarak değişir. Her uygulama için yordamlar aşağıdaki bölümlerde ayrıntılı şekilde verilmiştir.  
  
## <a name="cases-where-an-editor-supports-a-single-view"></a>Burada tek bir görünümde bir düzenleyici destekler durumları  
 Bu senaryoda, birden çok görünüm Düzenleyici desteklemez. Yalnızca bir düzenleyici ve tek bir belge yoktur ve bunlar geri alma desteği. Geri alma Yönetimi uygulamak için aşağıdaki yordamı kullanın.  
  
### <a name="to-support-undo-management-for-a-single-view-editor"></a>Geri alma yönetimini desteklemek için tek görünüm Düzenleyicisi için  
  
1.  Çağrı `QueryInterface` üzerinde `IServiceProvider` pencere çerçevesi için arabirimdeki `IOleUndoManager`, geri alma yöneticisi erişmek için belge görünümü nesnesinden (`IID_IOLEUndoManager`).  
  
2.  Bir görünümü bir pencere çerçevesine tarihli, onu çağırmak için kullanabileceğiniz bir site işaretçi alır. `QueryInterface` için `IServiceProvider`.  
  
## <a name="cases-where-an-editor-supports-multiple-views"></a>Burada bir düzenleyici birden çok görünüm destekler durumları  
 Belge ve görünüm ayrımı varsa, belge ile ilişkili normalde bir geri alma yöneticisi yok. Tüm geri alma birimi belge veri nesneyle ilişkili bir geri alma yöneticisi yerleştirilir.  
  
 Belge verilerini nesne görünümü var olduğu her görünüm için bir geri alma yöneticisi sorgulama yerine çağrıları <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2.CreateInstance%2A> geri alma yöneticisi örneklemek için bir sınıf tanımlayıcısı CLSID_OLEUndoManager belirtme. Sınıf tanımlayıcısı tanımlanan *OCUNDOID.h* dosya.  
  
 Kullanırken <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2.CreateInstance%2A> kendi geri alma yöneticisi örneği oluşturmak için geri alma Yöneticisi'ni kullanarak ortama bağlama için aşağıdaki yordamı kullanın.  
  
### <a name="to-hook-your-undo-manager-into-the-environment"></a>Geri alma Yöneticisi'ni kullanarak ortama yeteneklerinizi  
  
1. Çağrı `QueryInterface` yönteminden döndürülen nesne üzerinde <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2> için `IID_IOleUndoManager`. İşaretçi Store <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager>.  
  
2. Çağrı `QueryInterface` üzerinde `IOleUndoManager` için `IID_IOleCommandTarget`. İşaretçi Store <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>.  
  
3. Geçiş, <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> ve <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> saklı çağırıyor `IOleCommandTarget` arabirimi aşağıdaki StandardCommandSet97 komutlar için:  
  
   -   cmdidUndo  
  
   -   cmdidMultiLevelUndo  
  
   -   cmdidRedo  
  
   -   cmdidMultiLevelRedo  
  
   -   cmdidMultiLevelUndoList  
  
   -   cmdidMultiLevelRedoList  
  
4. Çağrı `QueryInterface` üzerinde `IOleUndoManager` için `IID_IVsChangeTrackingUndoManager`. İşaretçi Store <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager>.  
  
    İşaretçi kullanın <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager> çağrılacak <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager.MarkCleanState%2A>, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager.AdviseTrackingClient%2A>ve <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager.UnadviseTrackingClient%2A> yöntemleri.  
  
5. Çağrı `QueryInterface` üzerinde `IOleUndoManager` için `IID_IVsLinkCapableUndoManager`.  
  
6. Çağrı <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLinkCapableUndoManager.AdviseLinkedUndoClient%2A> belgenizi ile hangi de uygulamanız gerekir <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLinkedUndoClient> arabirimi. Belge kapatıldığında aramanızı `IVsLinkCapableUndoManager::UnadviseLinkedUndoClient`.  
  
7. Belge kapatıldığında aramanızı `QueryInterface` için geri alma yöneticinize üzerinde `IID_IVsLifetimeControlledObject`.  
  
8. Çağrı <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLifetimeControlledObject.SeverReferencesToOwner%2A>.  
  
9. Belgeye değişiklik yapıldığında çağrı <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager.Add%2A> yöneticisiyle üzerinde bir `OleUndoUnit` sınıfı. <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager.Add%2A> Yöntemi tutar nesnesine bir başvuru bu nedenle genellikle bu yayın sonrasında doğru <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager.Add%2A>.  
  
   `OleUndoManager` Sınıfı, bir tek geri alma yığını örneği temsil eder. Bu nedenle, veri varlığı geri alma veya yineleme için izlenen her bir geri alma Yöneticisi nesnesi yok.  
  
> [!NOTE]
>  Geri alma Yöneticisi nesnesi metin düzenleyici tarafından yaygın olarak kullanılır, ancak belirli hiçbir metin düzenleyicisi desteği olan bir genel bileşen var. Çok düzeyli geri alma veya yineleme desteklemek istiyorsanız, bunu yapmak için bu nesneyi kullanırsınız.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLifetimeControlledObject>   
 [Nasıl yapılır: geri alma yığını Temizle](../extensibility/how-to-clear-the-undo-stack.md)