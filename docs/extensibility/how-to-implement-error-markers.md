---
title: 'Nasıl yapılır: uygulama, hata işaretçileri | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - error markers
ms.assetid: e8e78514-5720-4fc2-aa43-00b6af482e38
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: eb6e511fa899680338831f3bc8e2a411f2126006
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49861169"
---
# <a name="how-to-implement-error-markers"></a>Nasıl yapılır: uygulama, hata işaretçileri
Hata işaretçileri (veya kırmızı dalgalı alt çizgiler) uygulamak için metin düzenleyici özelleştirmeleri en zor olan. Ancak, VSPackage kullanıcılara verdikleri kadar bunları sağlamanın maliyeti basıyor. Hata işaretçileri, dil ayrıştırıcı dalgalı veya dalgalı kırmızı bir çizgi ile yanlış olarak gördüğü metin farenizin işaretleyin. Bu gösterge programcılar hatalı kod görsel olarak görüntüleyerek yardımcı olur.  
  
 Kırmızı dalgalı alt çizgiler uygulamak için metin işaretçileri kullanın. Bir kural olarak, dil Hizmetleri kırmızı dalgalı alt çizgiler metin arabelleği için bir arka plan geçişi boşta kalma süresi veya bir arka plan iş parçacığında ekleyin.  
  
## <a name="to-implement-the-red-wavy-underline-feature"></a>Kırmızı dalgalı çizgi özelliği uygulamak için  
  
1. Kırmızı dalgalı çizgi yerleştirmek istediğiniz metni seçin.  
  
2. Bir işaretçi türünün oluşturma `MARKER_CODESENSE_ERROR`. Daha fazla bilgi için [nasıl yapılır: standart metin işaretçileri ekleme](../extensibility/how-to-add-standard-text-markers.md).  
  
3. Geçirin, sonra bir <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> arabirim işaretçisi.  
  
   Bu işlem ipucu metnini veya özel bağlam menüsü belirli bir işaret oluşturmanıza olanak sağlar. Daha fazla bilgi için [nasıl yapılır: standart metin işaretçileri ekleme](../extensibility/how-to-add-standard-text-markers.md).  
  
   Aşağıdaki nesneler, hata işaretçileri görüntülenebilmesi gereklidir.  
  
- Bir Ayrıştırıcı.  
  
- Bir görev sağlayıcısı (diğer bir deyişle, uygulaması <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskProvider2>), tutar satır bilgileri değişiklikleri kaydını yeniden ayrıştırılmış olmasını satırları tanımlamak için.  
  
- Giriş işaretini yakalayan bir metin Görünümü Filtresi değişiklik olayları kullanarak Görünüm <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEvents.OnChangeCaretLine%2A>) yöntemi.  
  
  Ayrıştırıcı, görev sağlayıcı ve filtre hata işaretçileri mümkün hale getirmek gerekli olan altyapıyı sağlar. Aşağıdaki adımlar, hata işaretçileri görüntülemek için işlem sağlar.  
  
1.  Filtre uygulanan bir görünümde, filtre bu görünümün verilerle ilişkili görev sağlayıcı için bir işaretçi alır.  
  
    > [!NOTE]
    >  Aynı komut filtre yöntemi ipuçları, deyim tamamlama, hata işaretçileri ve benzeri için kullanabilirsiniz.  
  
2.  Filtrenin başka bir satıra taşınır gösteren bir olay aldığında, hataları denetlemek için bir görev oluşturulur.  
  
3.  Görev işleyicisi satır olumsuz olup olmadığını denetler. Bu durumda, hatalar için satır ayrıştırır.  
  
4.  Görev sağlayıcısı, hata bulunursa, bir görev öğesi örneği oluşturur. Bu örnek, bir metin görünümünde hata işaretçisi olarak ortamı kullanır metin işaretçisi oluşturur.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Metin işaretçileri eski API'si ile kullanma](../extensibility/using-text-markers-with-the-legacy-api.md)   
 [Nasıl yapılır: standart metin işaretçileri Ekle](../extensibility/how-to-add-standard-text-markers.md)   
 [Nasıl yapılır: özel metin işaretçileri oluşturma](../extensibility/how-to-create-custom-text-markers.md)   
 [Nasıl yapılır: metin işaretçileri kullanma](../extensibility/how-to-use-text-markers.md)
