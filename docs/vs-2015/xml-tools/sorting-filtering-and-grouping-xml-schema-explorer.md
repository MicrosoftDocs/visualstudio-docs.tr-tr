---
title: Sıralama, filtreleme ve gruplandırma (XML Şeması Gezgini) | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4a914de0-9ffc-4526-9603-92e460e52513
caps.latest.revision: 11
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 49bd65d0ca9be83665f5f364f5e1f2115279cf5c
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49229742"
---
# <a name="sorting-filtering-and-grouping-xml-schema-explorer"></a>Sıralama, filtreleme ve gruplandırma (XML Şeması Gezgini)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Bu konu başlığı üzerinden seçeneklerle **sıralama, filtreleme ve gruplandırma seçeneklerini** XML şema Gezgini araç çubuğundaki menü.  
  
## <a name="filter-options"></a>Filtre Seçenekleri  
 Aşağıdaki filtre seçenekleri kullanılabilir. Varsayılan olarak, **ad alanlarını göster** ve **şema dosyalarını Göster** seçenekleri seçilidir.  
  
-   **Ad alanlarını göster**.  
  
-   **Şema dosyalarını Göster**.  
  
-   **Oluşturucuları Göster (dizisi/seçim/tümü)**.  
  
## <a name="sorting-options"></a>Sıralama seçenekleri  
 Aşağıdaki sıralama seçenekleri kullanılabilir. Varsayılan değer **türe göre sırala**. Sıralama ölçütü seçenekleri dosyalar ve ad alanları için geçerli değildir.  
  
-   **Türe Göre Sırala**.  
  
-   **Ada göre sırala**.  
  
-   **Belge sırada**.  
  
### <a name="sort-by-type"></a>Türe göre sırala  
 Zaman **türe göre sırala** seçeneği seçildiğinde, genel düğümler, aşağıdaki düzende sıralanır. Düğüm, her grup alfabetik olarak sıralanır.  
  
1.  `import` düğümleri.  
  
2.  `include` düğümleri.  
  
3.  `redefine` düğümleri.  
  
4.  `attribute` düğümleri.  
  
5.  `attributeGroup` düğümleri.  
  
6.  `complexType` düğümleri.  
  
7.  `simpleType` düğümleri.  
  
8.  `element` düğümleri.  
  
9. `group` düğümleri.  
  
### <a name="sort-by-name"></a>Ada göre sırala  
 Zaman **ada göre sırala** seçeneği seçildiğinde, genel düğümler, aşağıdaki düzende sıralanır:  
  
1.  `import` düğümleri (alfabetik sırada ad alanları).  
  
2.  `include` düğümleri (alfabetik sırada `schemaLocation` öznitelikleri).  
  
3.  `redefine` düğümleri (alfabetik sırada `schemaLocation` öznitelikleri).  
  
4.  Genel diğer düğümlere alfabetik olarak sıralayın.  
  
### <a name="document-order"></a>Belge sırada  
 **Belge sırada** seçeneği kullanılabilir olduğunda **şema dosyalarını Göster** seçeneği belirlenir. Zaman **belge sırada** seçildiğinde genel düğümler, şema dosyasında göründükleri sırada görüntülenir.  
  
## <a name="persisting-sortfilter-options"></a>Kalıcı sıralama/filtre seçenekleri  
 Sıralama, filtreleme ve gruplandırma Seçenekleri ayarları değiştirildi ne olursa olsun, çözüm veya dosya açıktı her bir kullanıcı için kayıt defterine kaydedildi.





