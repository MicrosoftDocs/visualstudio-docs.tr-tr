---
title: Kullanıcıya geri bildirim | Microsoft Docs
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
- user model feedback
- environment, context
- IDE, context
- IDE, user feedback
ms.assetid: 2d472a24-3813-4f5f-9783-b491ad8a71ad
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 509dffa0d2a474059277dbb3df2ba984fa35fe42
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51751166"
---
# <a name="feedback-to-the-user"></a>Kullanıcıya Geri Bildirim
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

İçinde [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] tümleşik geliştirme ortamı (IDE), kullanıcının geçerli seçimi ve genel seçim bağlamını ilgili kullanılabilir işlevler temel görsel geri bildirim. Aşağıdaki tabloda farklı seçim bağlamlarında kullanılabilir olan işlevleri listeler.  
  
|Seçim bağlamı|Kullanılabilir işlevleri|  
|-----------------------|-----------------------------|  
|IDE|Global|  
|Geçerli ürün kümesi|Belirli bir ürün|  
|Etkin olan hiyerarşi|Hiyerarşi türü özel|  
|Etkin olan hiyerarşi öğesi|Hiyerarşi öğesi türü özel|  
|Etkin belge|Belge türü özel|  
|En üstteki Çok Belgeli Arabirim (MDI) penceresi|Pencere türü özel|  
|Geçerli seçim bağlamı|Seçim bağlamını belirli|  
  
 Yalnızca kullanıcılar gereken ve sürekli olarak tutarlı seçimi ve ortam bağlamı geri bildirim sağlamak işlevselliğini yüzey, IDE karmaşıklığını azaltın. Her bir pencere IDE içinde açıldığında aşağıdaki kurallar geçerlidir:  
  
- Pencerenin alt seçim bağlamını değişirse, seçim geri bildirimi penceresinde açıkça belirtilir ve dinamik Yardım penceresi, geçerli bağlam yansıtacak şekilde güncelleştirilir yoksa.  
  
- Pencerenin genel seçim bağlamını değişirse, tüm özel bağlam menüleri, etkin olan hiyerarşi pencere ve uygulama başlık çubuğunun geçerli bağlam yansıtacak şekilde güncelleştirilir.  
  
- Pencerenin geçerli seçimde özelliklerini yüzey **özellikleri** penceresi ve isteğe bağlı olarak gösteriliyorsa, **özellik sayfaları** iletişim kutusu.  
  
- Pencere özellikleri surface etmez veya genel seçim bağlamını değiştirme, artık IDE'de etkin pencere olduğunda seçim geri bildirimi penceresinde kalmalıdır değil.  
  
- Tüm belge özel araç pencereleri, sürekli olarak etkin belgeyi yansıtmalıdır.  
  
- Menüleri ve araç çubukları uygulama başlık çubuğunda en üstteki Çok Belgeli Arabirim (MDI) istemci penceresi yansıtmalıdır.  
  
  Örneğin, zaman içinde bir Visual Basic Web uygulaması projesini Web formu HTML görünümü açılır ve kullanıcının seçtiği bir `<td>` etiketi, geri bildirim aşağıdaki şekilde sağlanır:  
  
- Seçimi etkin pencerede gösterilir ve yansıtılan **özellikleri** penceresi.  
  
- Belgeye özgü **araç kutusu** etkin belgeyi yansıtacak şekilde güncelleştirilir.  
  
- **Düzenleyicisi** araç ve **tablo** menüsü görüntülenir ve Web formu pencerenin yansıtmak için başlık çubuğunda güncelleştirir.  
  
- Genellikle etkin olan hiyerarşi penceresinde **Çözüm Gezgini**ve geçerli bağlamı ve bağlama duyarlı yansıtmak için başlık çubuğunda güncelleştirme **proje** menü komutları, etkin Web şimdi Uygula Uygulama projesi.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Seçim ve para birimi IDE](../../extensibility/internals/selection-and-currency-in-the-ide.md)   
 [Seçim bağlamı nesneleri](../../extensibility/internals/selection-context-objects.md)   
 [Hiyerarşiler ve Seçim](../../extensibility/internals/hierarchies-and-selection.md)

