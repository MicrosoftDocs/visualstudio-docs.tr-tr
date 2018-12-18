---
title: Etki alanı yolu sözdizimi | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Domain-Specific Language, domain path
ms.assetid: 945994f9-72b9-42e0-81b2-e5fb3d0e282d
caps.latest.revision: 27
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: d4e98715bae8869619e8d9f2852c810153984777
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49254780"
---
# <a name="domain-path-syntax"></a>Etki Alanı Yolu Sözdizimi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

DSL tanımlarına XPath benzeri bir sözdizimi bir modelde belirli öğeleri bulmak için kullanın.  
  
 Normalde bu sözdizimi ile doğrudan çalışmak zorunda değildir. DSL ayrıntıları veya Özellikler penceresinde göründüğü aşağı oka tıklayın ve yolu Düzenleyicisi'ni kullanın. Ancak, düzenleyici kullandıktan sonra yol bu alanı formda görüntülenir.  
  
 Bir etki alanı yolu aşağıdaki biçimi alır:  
  
 *RelationshipName.PropertyName/! Rol*  
  
 ![Başvuru ilişkisi CommentReferencesSubjects](../modeling/media/dsl-reference.png "dsl_reference")  
  
 Sözdizimi ağacı modelinin erişir. Örneğin, etki alanı ilişkisi **CommentReferencesSubjects** Yukarıdaki örnekteki sahip bir **konuları** rol. Yol kesimi **/! Subjectt** yolu üzerinden erişilen öğeleri tamamlandığını belirtir **konuları** rol.  
  
 Her segmentinde bir etki alanı ilişkisi adı ile başlar. Geçişi öğeden bir ilişki, yol kesimi olarak görünür *Relationship.PropertyName*. Atlama bağlantı için bir öğe, yol kesimi olarak görünür *ilişki /! RoleName*.  
  
 Eğik bir yolu sözdizimi ayırın. Her yol kesimi ya da bir atlama bir öğeye bir bağlantı (bir ilişkinin örneğini) veya bir öğe için bir bağlantı var. Yol kesimleri sık çiftler halinde görünür. Bir yol kesimini bir atlama öğeden bağlantısını temsil eder ve sonraki kesimini bir atlama bağlantıdan diğer uçtaki öğeyi temsil eder. (Tüm bağlantı de kaynak veya hedef bir ilişkinin olabilir).  
  
 Öğe bağlantısı atlama için kullandığınız adı rolün değeri `Property Name`. Link öğesi atlama için kullandığınız ad hedef rol adı değil.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Modelleri, Sınıfları ve İlişkileri Anlama](../modeling/understanding-models-classes-and-relationships.md)



