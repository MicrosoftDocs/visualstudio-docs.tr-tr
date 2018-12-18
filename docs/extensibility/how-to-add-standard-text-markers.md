---
title: 'Nasıl yapılır: standart metin işaretçileri ekleyin | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - standard text markers
ms.assetid: a39fca69-0014-474c-933f-51f0e9b9617e
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 4dd34b14b89c78d01f1d4acab57f33014860d7ba
ms.sourcegitcommit: 06db1892fff22572f0b0a11994dc547c2b7e2a48
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/08/2018
ms.locfileid: "39638827"
---
# <a name="how-to-add-standard-text-markers"></a>Nasıl yapılır: standart metin işaretçileri Ekle
İle sağlanan varsayılan metin işaretçisi türleri oluşturmak için aşağıdaki yordamı kullanın. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] çekirdek Düzenleyici.  
  
## <a name="to-create-a-text-marker"></a>Bir metin işaretçisi oluşturmak için  
  
1.  Bir tane veya two dimensional koordinat sistemini kullanarak bağlı olarak, çağrı <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.CreateLineMarker%2A> yöntemi veya <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream.CreateStreamMarker%2A> yöntemini yeni bir metin işaretçisi.  
  
     Bu yöntem çağrısında bir işaret türü bir işaretçi üzerinde oluşturmak için metin aralığı belirtin ve bir <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> arabirimi. Bu yöntem, ardından yeni oluşturulan metin işaretçisi için bir işaretçi döndürür. İşaretçi türleri verilerinden alınır <xref:Microsoft.VisualStudio.TextManager.Interop.MARKERTYPE> sabit listesi. Belirtin bir <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> işaret olayları hakkında bilgi sahibi olmak istiyorsanız, arabirim.  
  
    > [!NOTE]
    >  Ana kullanıcı Arabirimi iş parçacığı üzerinde yalnızca metin işaretçileri oluşturun. Çekirdek düzenleyici metin işaretçileri oluşturmak için metin arabelleği içeriğine kullanır ve metin arabelleğini iş parçacığı güvenli değildir.  
  
## <a name="add-a-custom-command"></a>Özel komut ekleme  
 Uygulama `IVsTextMarkerClient` arabirimi ve bir işaretçi kendisine işaretten itibaren sağlayarak işaret davranışını çeşitli şekillerde geliştirir. İlk olarak, bu, işaretçinizi için ipuçları sağlar ve komutları yürütmek için sağlar. Bu ayrıca, tek tek işaretçileri için olay bildirimleri alması ve özel bağlam menüsü işaret oluşturmak için sağlar. İşaret bağlam menüsüne bir özel komut eklemek için aşağıdaki yordamı kullanın.  
  
### <a name="to-add-a-custom-command-to-the-context-menu"></a>Bağlam menüsüne özel komut ekleme  
  
1.  Bağlam menüsü görüntülenmeden önce ortam çağırır <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient.GetMarkerCommandInfo%2A> yöntemi ve metin işaretçisi için bir işaretçi sorundan geçişleri ve bağlam menüsünden komut öğe sayısı.  
  
     Örneğin, kesme noktası özgü komutlar bağlam menüsünde yer **kesme noktasını Kaldır** aracılığıyla **yeni kesme noktası**, aşağıdaki ekran görüntüsünde gösterildiği.  
  
     ![İşaretli bağlam menüsü](../extensibility/media/vsmarkercontextmenu.gif "vsMarkercontextmenu")  
  
2.  Özel komut adını tanımlayan bir metin geri geçirin. Örneğin, **kesme noktasını Kaldır** bu ortamı zaten sağlamadı özel komut olabilir. Ayrıca geri geçirdiğiniz komutu desteklenen, kullanılabilir ve etkin olup ve/veya açık-kapalı Değiştir. Ortam, özel komut bağlam menüsü doğru şekilde görüntülemek için bu bilgileri kullanır.  
  
3.  Ortam çağrıları komutu yürütmek için <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient.ExecMarkerCommand%2A> yöntemi, metin işaretçisi ve bağlam menüsünden Seçili komut sayısı için bir işaretçi geçirme.  
  
     Metin işaretçisi hangi eylemleri belirler, özel bir komut yürütmek için bu çağrı bu bilgileri kullanın.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Metin işaretçileri eski API'si ile kullanma](../extensibility/using-text-markers-with-the-legacy-api.md)   
 [Nasıl yapılır: uygulama, hata işaretçileri](../extensibility/how-to-implement-error-markers.md)   
 [Nasıl yapılır: özel metin işaretçileri oluşturma](../extensibility/how-to-create-custom-text-markers.md)   
 [Nasıl yapılır: metin işaretçileri kullanma](../extensibility/how-to-use-text-markers.md)