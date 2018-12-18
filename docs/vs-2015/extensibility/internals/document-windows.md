---
title: Windows belge | Microsoft Docs
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
- Visual Studio SDK, document windows
ms.assetid: 50081d48-987f-43db-8bf9-51b7cf76e9c0
caps.latest.revision: 18
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d669485eb13c8d9f089a54dcbfcf92fac710f474
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51784591"
---
# <a name="document-windows"></a>Belge Pencereleri
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Gecikmeli Belge Yüklemesi](../../extensibility/internals/delayed-document-loading.md)

