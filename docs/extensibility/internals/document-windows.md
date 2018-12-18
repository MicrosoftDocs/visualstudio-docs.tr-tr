---
title: Windows belge | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio SDK, document windows
ms.assetid: 50081d48-987f-43db-8bf9-51b7cf76e9c0
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: dcd2c47de8e1ad8b650da0819b5e8b0a46213e29
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49875989"
---
# <a name="document-windows"></a>Belge pencereleri
Visual Studio'da bir *belge penceresi* bir çok Belgeli Arabirim (MDI) penceresi ile ilişkili bir Çerçeveli alt penceredir. Belge pencereleri genellikle görüntüleme ve kaynak kodu veya metin değişikliği için kullanılır, ancak işlev diğer türleri de barındırabilir. Belge pencereleri:  
  
- Böylece birden çok dosyayı aynı anda görüntülenebilir, üst MDI ayrı yatay veya dikey sekme grupları içinde düzenlenebilir.  
  
- MDI üst herhangi bir sırada sabitlenebilir.  
  
- Özgürce kaydırıldı.  
  
- Diğer MDI pencereleri için sekmesinde sırayla bağlanır.  
  
  Komutları gruplandırma için yerleşen ve kayan bir belge penceresi sekme kısayol menüsünde bulunabilir.  
  
  Visual Studio'da pencere davranış hakkında daha fazla bilgi için bkz. [pencere düzenlerini özelleştirme](../../ide/customizing-window-layouts-in-visual-studio.md).  
  
## <a name="document-window-implementation"></a>Belge penceresi uygulama  
 Belge pencereleri, bir düzenleyici uygulayarak oluşturulur. <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> Arabirimi bir düzenleyici örnekleme bir parçası olarak belge pencerelerini oluşturur. Daha fazla bilgi için [eski arabirimleri Düzenleyicisi'nde](../../extensibility/legacy-interfaces-in-the-editor.md).  
  
> [!NOTE]
>  Geriye doğru sağlamak ve bir pencere gezinti noktaları iletmek üzere uygulama <xref:Microsoft.VisualStudio.Shell.Interop.IVsBackForwardNavigation> arabirimi. Metin Düzenleyicisi metin işaretçileri belgedeki Gezinti noktalarını tanımlamak için kullanır.  
  
## <a name="the-running-document-table"></a>Çalıştırılan Belge tablosu  
 IDE her belge penceresi durumunu izlemek için çalıştırılan Belge tablosu (RDT) kullanır. RDT hangi belge windows olaylarını gibi bir çözüm kapatıldığında veya bir dosya düzenlendiğinde, bildirilir mekanizmadır. Daha fazla bilgi için [çalıştırılan Belge tablosu](../../extensibility/internals/running-document-table.md).  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Gecikmeli belge yüklemesi](../../extensibility/internals/delayed-document-loading.md)