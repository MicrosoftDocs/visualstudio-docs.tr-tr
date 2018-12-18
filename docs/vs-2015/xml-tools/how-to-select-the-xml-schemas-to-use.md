---
title: 'Nasıl yapılır: XML şemalarını seçme | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d6fda3ef-d465-4788-8514-2f2d528d658c
caps.latest.revision: 8
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 93f573412524619292b1966e87abeda11cc0813a
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49863730"
---
# <a name="how-to-select-the-xml-schemas-to-use"></a>Nasıl yapılır: XML şemalarını seçme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
XML Düzenleyicisi'ni %InstallDir%\Xml\Schemas dizininde bulunan bir şema önbelleği sağlar. Şema önbelleği, IntelliSense ve XML belgesi doğrulama için kullanılan XML şemaları iyi bilinen içerir.  
  
 **Şemaları** belge özelliği kullanmak için bir veya daha fazla XML Şeması Tanım Dili (XSD) şeması/şemaları seçmek için kullanılır. Şemalar şema önbelleğinden seçin ya da önbelleğinde bulunmayan bir şema belirtmenizi sağlar.  
  
 Belirttiğiniz şemaları yanı sıra tüm diğer XML belge özellikleri gizli bir çözüm kullanıcı seçenekleri dosyasında (.suo) kaydedilir. Sonuç olarak, bu değerleri çözüm bir sonraki açışınızda yeniden girmeniz gerekmez.  
  
> [!NOTE]
>  Düzenleyicide bir satır içi şema veya şema tarafından başvurulan kullanarak doğrulayabilirsiniz `xsd:schemaLocation` özniteliği. Daha fazla bilgi için [XML belgesi doğrulama](../xml-tools/xml-document-validation.md).  
  
### <a name="to-select-an-xml-schema-from-the-schema-cache"></a>Bir XML Şeması, şema önbelleğinden seçmek için  
  
1. Bir dosyasını XML düzenleyicisinde açın.  
  
2. Düğmesine tıklayarak belge Özellikler penceresinde **şemaları** alan.  
  
    **XML şemaları** iletişim kutusu görüntülenir. Tüm şemalar şema önbelleğinde (catalog.xml dosyasında başvurulan şemaları dahil) bir .xsd uzantısı ile iletişim kutusu listeler ve geçerli çözümde herhangi bir şema açmak için ayrıca Visual Studio, başvurulan bir `xsd:schemaLocation` özniteliği ya da başvuru **şemaları** özelliği.  
  
3. Aşağıdakilerden birini yaparak doğrulama için kullanılacak şemaları seçin:  
  
   - Listelenen bir şema seçin **XML şemaları** iletişim kutusunda, tıklayın **kullanım** sütun tıklayın ve ardından **Bu şemayı kullan**.  
  
     veya  
  
   - Birden çok şema listelenen seçin **XML şemaları** iletişim, sütuna sağ tıklayıp **Bu şemayı kullan**.  
  
4. **Tamam**'ı tıklatın.  
  
    Seçili şemaları listesini geri kopyalanır **şemaları** belge özelliği.  
  
### <a name="to-add-an-xml-schema-to-the-schema-cache"></a>Bir XML Şeması, şema önbelleğine eklemek için  
  
1.  Düğmesine tıklayarak belge Özellikler penceresinde **şemaları** alan.  
  
2.  **Ekle**'yi tıklatın.  
  
     Bu açılır **açık XSD şeması** iletişim.  
  
3.  Gözat ve şemaları şema önbelleğine eklemek için seçin.  
  
4.  Tıklayın **açık**.  
  
     Eklenir şemaları önbelleğe alma ve ise **kullanım** sütun değeri ayarı **Bu şemayı kullan**.  
  
### <a name="to-delete-an-xml-schema-from-the-schema-cache"></a>Bir XML Şeması, şema önbelleğinden silmek için  
  
1.  Düğmesine tıklayarak belge Özellikler penceresinde **şemaları** alan.  
  
2.  Kaldırın ve ardından şemayı seçin **Kaldır**.  
  
     Şema bellek içi şema önbelleğinden kaldırılıyor ancak dosya sisteminden kaldırılmaz.  
  
    > [!NOTE]
    >  Yine de şemanın başvuru varsa bir `schemaLocation` özniteliği veya eşleşen bir `targetNamespace` ardından **Kaldır** otomatik ilişkisi nedeniyle, bu durumda işe yaramaz. Bu durumda, şema olarak işaretlemek önerilir **seçili şemaları kullanma** içinde **kullanın** sütun.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Şema önbelleği](../xml-tools/schema-cache.md)   
 [XML şemaları iletişim kutusu](../xml-tools/xml-schemas-dialog-box.md)   
 [XML Düzenleyicisi](../xml-tools/xml-editor.md)



