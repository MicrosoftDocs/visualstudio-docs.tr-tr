---
title: DSL Tanım Diyagramı ile Çalışma
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.dsltools.dsldesigner.diagram
- vs.dsltools.dsldesigner.dsldiagram
helpviewer_keywords:
- Domain-Specific Language Tools, diagram
- Domain-Specific Language Tools, Split Tree
- Domain-Specific Language Tools, Show Map Lines
- Domain-Specific Language Tools, Show As Class
- Domain-Specific Language Tools, Bring Tree Here
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: d7e052f64e931769b1fedde7e184bfeefa43a77d
ms.sourcegitcommit: 768d7877fe826737bafdac6c94c43ef70bf45076
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/02/2018
ms.locfileid: "50967408"
---
# <a name="working-with-the-dsl-definition-diagram"></a>DSL Tanım Diyagramı ile Çalışma
Diyagramı bir [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] tanımı etki alanına özgü dil tanımlamak için önemli bir araçtır. Etki alanınıza öğeleri modelini ve diyagramda ilişkileri tanımlamak ve daha okunabilir yapmak için diyagramın düzenini değiştirebilirsiniz ekleyebilirsiniz.

## <a name="the-layout-of-the-diagram"></a>Diyagram Düzeni
 [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] Tanım diyagramı sahip iki bölüm **sınıflar ve ilişkiler** bölüm ve **diyagram öğelerine** bölüm. **Sınıflar ve ilişkiler** bölüm alan sınıfları, etki alanı ilişkileri ve devralma görüntüler. **Diyagram öğelerine** bölüm şekil sınıfları, bağlayıcı sınıfları, Kulvar sınıfları ve oluşturulan Tasarımcısı Diyagramı görüntüler.

 Etki alanı sınıfları birden fazla konumda görünebilir **sınıflar ve ilişkiler** bölümler. Gömme veya başvuru ilişkileri kaynağını ise, diğer etki alanı sınıfları ve ilişkileri ağacı temel sınıfı olan bir etki alanı sınıf tanımının devralma ağacını görüntüler. Etki alanı sınıfı yer tutucuları gömme veya başvuru ilişkileri hedefleri görünür. Varsayılan olarak, yer tutucu öğeleri ile görüntülenen **etki alanı özellikleri** daraltılmış bölme. Bunlar, devralma veya gömme veya başvuru ilişkileri gösterme.

 Bir etki alanı sınıfı eklediğinizde, alt kısmında görünür **sınıflar ve ilişkiler** bölüm. Gömme ekleyin ya da ilişki başvuru altında ve kaynak etki alanı sınıfı sağındaki çizilir.

 Etki alanı sınıfları ve ilişkileri ekleme gibi belirli bir etki alanı sınıfı bulması zor hale gelebilir. Bir alan sınıfına sağ tıklayarak bulabilirsiniz **DSL Gezgini** tıklayıp **diyagramda Bul**.

 Aşağıdaki bölümlerde, okunmasını kolaylaştırmak için diyagram görünümünü nasıl değiştirebileceğiniz açıklanır.

## <a name="copying-elements"></a>Öğeleri kopyalama
 Kopyala, Kes ve DSL tanım diyagramı öğelere yapıştırın.

## <a name="zooming-in-or-out-on-the-diagram"></a>Diyagram üzerinde yakınlaştırma veya uzaklaştırma
 Kullanarak veya diyagram uzaklaştırmak yakınlaştırabilirsiniz **DSL Tasarımcısı** yakınlaştırma düzeyini ayarlamak için araç çubuğu.

## <a name="hiding-map-lines"></a>Eşleme satırlarını gizleme
 Eşleme satırlarını, bir etki alanı sınıfı veya etki alanı ilişkisi ve şekli arasında çizilmiş satırları veya eşlenmiş bağlayıcı olabilir. Eşleme satırlarını tıklayarak gizleyebilirsiniz **eşleme satırlarını göster** düğmesini **DSL Tasarımcısı** araç çubuğu. Satırları göstermek için düğmeye tıklayın.

## <a name="changing-the-diagram-layout"></a>Diyagram düzeni değiştirme
 Düzenini değiştirebilirsiniz **sınıflar ve ilişkiler** gibi bölümleme.

### <a name="expandcollapse"></a>Genişlet/Daralt
 Bir şekli alan sınıfıyla ya da sağ tıklatıp sonra temsil eden bir bölme şekli öğesi boyutunu azaltabilirsiniz **Daralt**. Bu gizler **etki alanı özellikleri** bölme şeklinin. Gösterilecek **etki alanı özellikleri** yeniden bölme, şekle sağ tıklayın ve ardından **genişletme**.

### <a name="move-updown"></a>Yukarı/Aşağı Taşı
 Öğeyi sağ tıklatıp ardından bölümünde bir etki alanı sınıfı veya diyagram öğesini yukarı veya aşağı taşıyabilirsiniz **Yukarı Taşı** veya **Aşağı Taşı**. İlişkinin bir gömme veya başvuru ilişkisi hedefi olarak görüntülenen bir yer tutucu öğesi taşırsanız, ile taşınır.

### <a name="expandcollapse-relationships-tree"></a>İlişki ağacını Genişlet/Daralt
 Bir etki alanı sınıfı gömme veya başvuru ilişkileri diğer alan sınıfları ile kaynak rol oynar, etki alanı sınıf tanımına sağ tıklatıp ardından ilişkileri gizleyebilir **Daralt ilişkileri ağaç**. İlişkileri göstermek için tanım öğesinin sağ tıklayın ve ardından **ilişkileri ağacı genişletin**.

### <a name="expandcollapse-inheritance-tree"></a>Devralma ağacını Genişlet/Daralt
 Bir etki alanı sınıfı, diğer etki alanı sınıflarının temel sınıf ise, etki alanı sınıf tanımına sağ tıklatıp ardından devralma ağacını gizleyebilirsiniz **devralma ağacını Daralt**. Devralma ağacını göstermek için tanım öğesinin sağ tıklayın ve ardından **devralma ağacını Genişlet**.

### <a name="bring-tree-here"></a>Buraya Ağacı Getir
 Bir yer tutucu etki alanı sınıfı sağ tıklayarak ve ardından diyagram birleştirebilir **ağacı buraya getirin**. Yer tutucu etki alanı sınıfı, bir tanım öğesi haline gelir ve devralma ve ilişkiler ağaçları görüntüler. Bir ilişki veya devralma ilişkisi alt hedefi ise önceki tanım öğesi bir yer tutucu öğesi olur; Aksi takdirde, kaybolur.

### <a name="split-tree"></a>Ağacı Böl
 Devralma ve ilişkiler ağaçları görüntüler etki alanı sınıf tanımı sağ tıklatıp ardından bozabilir **ağacı Böl**. Tanım öğesinin bir yer tutucu öğesi olur ve tanımı etki alanı sınıfı, devralma ve ilişkiler ağaçları birlikte artık bölümünün altında görüntülenir.

### <a name="show-as-class"></a>Sınıf Olarak Göster
 Bir etki alanı ilişkisi ilişkileri türetilmiş ya da diğer etki alanı ilişkileri gömme veya başvuru ilişkileri varsa, ilişkiyi sınıf olarak ilişkiye sağ tıklayın ve ardından görüntüleyebilirsiniz **sınıf olarak göster** . İlişki ile görüntülenen bir **etki alanı özellikleri** bölme ve devralma ve ilişkiler ağaçları gösterilir.

## <a name="see-also"></a>Ayrıca Bkz.

- [Etki alanına özgü dil araçları sözlüğü](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)