---
title: Proje bağlam | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], opening items
ms.assetid: d1803f4a-24eb-44b0-b5d2-cb40c15534be
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d2f52260d63088d7673322f3c42d43d00184a9af
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31134701"
---
# <a name="project-context"></a>Proje bağlamı
Kullanıcı ekler veya projeleri ve proje öğeleri ile çalışır, IDE proje bağlamı kavramı nasıl çeşitli işlemleri yapılması gerektiğini belirlemek için kullanır.  
  
 Genellikle, dosyaları seçerek kullanıcı açıkça oluşturan standart proje nesneleridir **yeni proje** komut veya seçerek kullanılabilir hale getirir **Proje Aç** komutunu  **Dosya** menüsü. Bu durumda, dosyaları oluşturulur ve bir proje bağlamında açılır ve proje türüne belge düzenlenmek bağlamı tanımlar.  
  
 Bazı projeler çok zengin bir bağlam sağlar. Örneğin, bir proje kapsamı, programlı ad alanı veya veri bağlama için Proje kapsamlı veritabanı bağlantısı proje yönetir. Kullanıcının sık dosyaları veya veritabanı bağlantılarını doğrudan Çözüm Gezgini'nde görüntülenen bir proje öğesi gibi bir projedeki nesnesi kullanarak açabilirsiniz.  
  
 Diğer saatlerde öğeyi proje bağlamında açıkça belirtilmedi. Seçerek kullanıcı bir dosyayı açtığında, örneğin, bir öğenin bağlam kullanılamıyor **açık varolan dosyayı** komutunu **dosya** hata ayıklayıcı bir dosyada veya kullanıcı tıklattığında çalıştığında menüsünde. **Dosyaları bulmak** komutunu **bulma ve değiştirme** iletişim kutusu. Bu durumlarda, IDE çağrıları işlemek için <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument> bir belgeyi açmak için en iyi proje bulma işlemini yönetmek için.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Proje önceliği](../../extensibility/internals/project-priority.md)   
 [Proje ve Proje Öğesi Şablonları Ekleme](../../extensibility/internals/adding-project-and-project-item-templates.md)