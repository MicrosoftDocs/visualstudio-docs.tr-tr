---
title: Etki Alanı Yolu Sözdizimi
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, domain path
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 984b27b65b251a1e87c72962e488fd0d4036a4d0
ms.sourcegitcommit: 58052c29fc61c9a1ca55a64a63a7fdcde34668a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34749550"
---
# <a name="domain-path-syntax"></a>Etki Alanı Yolu Sözdizimi
DSL tanımları XPath benzeri bir sözdizimi bir modelde belirli öğeleri bulmak için kullanın.

 Normalde bu sözdizimi ile doğrudan çalışmak zorunda değildir. DSL ayrıntıları veya özellikleri penceresinde göründüğü aşağı oka tıklayın ve yolu Düzenleyicisi'ni kullanın. Ancak, düzenleyici kullandıktan sonra yol bu alanın formda görüntülenir.

 Bir etki alanı yolu aşağıdaki biçimdedir:

 *RelationshipName.PropertyName/! Rolü*

 ![CommentReferencesSubjects başvuru ilişkisi](../modeling/media/dsl_reference.png)

 Sözdizimi ağacı modelinin erişir. Örneğin, etki alanı ilişkisinin **CommentReferencesSubjects** Yukarıdaki çizimde sahip bir **konuları** rol. Yol kesimi **/! Subjectt** yolu üzerinden erişilen öğelerde tamamlandığını belirtir **konuları** rol.

 Her segmentinde bir etki alanı ilişkisinin adıyla başlar. Geçişi arasında bir ilişki öğeden ise, yol kesimi olarak görünür *Relationship.PropertyName*. Atlama bir öğeye bir bağlantıdan ise, yol kesimi olarak görünür *ilişki /! RoleName*.

 Eğik bir yolu sözdizimi ayırın. Her yol kesimi ya da bir atlama bir bağlantı (bir ilişki örneği) için bir öğe veya öğenin bağlantısını ' dir. Yol kesimleri sık çiftler halinde görüntülenir. Bir yol kesimi bir atlama bir öğeyi bağlantısını temsil eder ve sonraki kesimini bir atlama bağlantıdan diğer uçtaki öğesine temsil eder. (Herhangi bir bağlantıyı de kaynak veya hedef bir ilişkinin olabilir).

 Öğe bağlantı atlaması için kullandığınız adı rolün değeri `Property Name`. Link öğesi atlaması için kullandığınız adı hedef rol adı değil.

## <a name="see-also"></a>Ayrıca Bkz.

- [Modelleri, Sınıfları ve İlişkileri Anlama](../modeling/understanding-models-classes-and-relationships.md)