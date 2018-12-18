---
title: Varsayılan komut, Grup ve araç çubuğu yerleşimi | Microsoft Docs
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
- commands [Visual Studio], default groups
- toolbars [Visual Studio], default
- commands [Visual Studio], default editor
- command groups
- commands [Visual Studio], default IDE
- commands [Visual Studio], default product
ms.assetid: 35342110-d639-4577-8367-00b21dcc6f07
caps.latest.revision: 31
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e91d535697d0e5b9402a7b7eb3bbd4559821c68a
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51773645"
---
# <a name="default-command-group-and-toolbar-placement"></a>Varsayılan Komut, Grup ve Araç Çubuğu Yerleşimi
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Ürün gerekmemesi ve tutarlılık için kullanıcı Arabirimi varsayılan olarak, bazı komut gruplarını görüntüler ve [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] komutları ve komut gruplar için tanımları sağlar. VSPackage de standart komut ve komut gruplarını kullanabilirsiniz.  
  
 Varsayılan komut gruplarını üç kategoriye ayrılır: IDE komutları, ürün komutları ve düzenleyici komutları.  
  
## <a name="default-ide-commands"></a>Varsayılan IDE komutları  
 Varsayılan IDE araç çubuğunda yer alan tüm ürünleri tarafından paylaşılan komutları içermektedir [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]. Bunlar gibi genel proje işlemleriyle ilgili komutları **Kaydet** komut ve **Öğe Ekle** komutu. VSPackage'ları ekleyin veya gerekir bu araç, bir özel durum ile Çıkart: yeni bir araç penceresi ürün veya VSPackage ekler ardından pencerenin üzerinde kullanılabilir araç pencereleri listesine eklenmesi gereken **görünümü** menü. Kendi araç, yeni ürünler veya VSPackages ekleyebilirsiniz.  
  
## <a name="default-product-commands"></a>Varsayılan ürün komutları  
 Her ürün IDE ile önemli içeren ve sık kullanılan komutlar kendi varsayılan araç çubuğu sağlar. Ancak, var olan menüleri ve araç çubuklarını mümkün olduğunca kullanın ve bunları gerektiği gibi diğer görev özel araç çubuklarıyla desteklemek için en iyisidir.  
  
 Satır yerleşimi için bir araç çubuğu Öncelik alanını belirler. Araç çubuğu menü çubuğu altındaki üçüncü satıra (Satır 3) sıfır öncelik yerleştirir (1 satır) ve **standart** araç çubuğu (satır 2). Bu nedenle, diğer araç çubukları satırında görünür (öncelik + 3). Oda ise aynı satırda sonraki araç çubukları yerleştirilir; Aksi takdirde, bunlar otomatik olarak sonraki satıra taşınır.  
  
## <a name="default-editor-commands"></a>Varsayılan Düzenleyicisi komutları  
 Özel bir düzenleyici sağlayan bir VSPackage'ı en önemli içeren ve sık kullanılan komutlar, düzenleyicide varsayılan araç sağlamanız gerekir. Düzenleyici etkinse ve Düzenleyici etkin değilken gizlenmelidir Düzenleyici araç çubuğu görüntülenmelidir. Bu görünürlük denetlenir `VisibilityConstraints Element` .vsct dosyası.  
  
 IDE ve ürün araç çubukları Düzenleyicisi araç çubukları yerleştirilmelidir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IDE tanımlı komutlar, menüler ve gruplar](../../extensibility/internals/ide-defined-commands-menus-and-groups.md)   
 [VSPackage’ların Kullanıcı Arabirimi Öğeleri Eklemesi](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)

