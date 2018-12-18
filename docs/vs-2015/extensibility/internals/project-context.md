---
title: Proje bağlamı | Microsoft Docs
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
- projects [Visual Studio SDK], opening items
ms.assetid: d1803f4a-24eb-44b0-b5d2-cb40c15534be
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: c2d54d0e4e8f2a19f641b984d82a5f35d6390274
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51795199"
---
# <a name="project-context"></a>Proje Bağlamı
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Kullanıcı ekler veya projeleri ve proje öğeleri ile birlikte çalışır, IDE proje bağlam kavramı nasıl çeşitli işlemler gerçekleştirilmelidir belirlemek için kullanır.  
  
 Genellikle, dosyaları seçerek kullanıcı açıkça oluşturan standart proje nesnelerdir **yeni proje** komut veya seçerek kullanılabilir yapar **Proje Aç** komutunu  **Dosya** menüsü. Bu gibi durumlarda, dosyalar oluşturulur ve bir proje bağlamında açılır ve proje türü belge düzenleme bağlamı tanımlar.  
  
 Bazı projeler çok zengin bir bağlam sağlar. Örneğin, bir proje kapsamlı, programlı bir ad alanı veya proje kapsamlı veritabanı bağlantısı veri bağlama için proje yönetir. Kullanıcının sık dosyaları veya veritabanı bağlantıları görüntülenen Çözüm Gezgini'nde bir proje öğesi gibi bir özel Proje nesne kullanarak doğrudan açabilirsiniz.  
  
 Diğer zamanlarda ise, öğenin proje bağlamı açıkça belirtilmedi. Kullanıcı seçerek bir dosya açıldığında, örneğin, bir öğenin bağlam kullanılamıyor **mevcut Dosya Aç** komutunu **dosya** hata ayıklayıcıyı bir dosya veya kullanıcı tıkladığında çalıştığında menüsü **Dosyalarda Bul** komutunu **Bul ve Değiştir** iletişim kutusu. Bu durumlarda, IDE aramaları işlenecek <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument> bir belgeyi açmak için en iyi proje bulma işlemini yönetmek için.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Proje önceliği](../../extensibility/internals/project-priority.md)   
 [Proje ve Proje Öğesi Şablonları Ekleme](../../extensibility/internals/adding-project-and-project-item-templates.md)

