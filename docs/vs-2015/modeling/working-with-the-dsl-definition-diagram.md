---
title: DSL tanım diyagramı ile çalışma | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.dsltools.dsldesigner.diagram
- vs.dsltools.dsldesigner.dsldiagram
helpviewer_keywords:
- Domain-Specific Language Tools, diagram
- Domain-Specific Language Tools, Split Tree
- Domain-Specific Language Tools, Show Map Lines
- Domain-Specific Language Tools, Show As Class
- Domain-Specific Language Tools, Bring Tree Here
ms.assetid: 1a4c7a58-e134-438e-848e-efd98f92bf10
caps.latest.revision: 23
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 1fc0dbc007dcb3e15891a4176fc5bdb96babbfa8
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49208591"
---
# <a name="working-with-the-dsl-definition-diagram"></a>DSL Tanım Diyagramı ile Çalışma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Diyagramı bir [!INCLUDE[dsl](../includes/dsl-md.md)] tanımı etki alanına özgü dil tanımlamak için önemli bir araçtır. Etki alanınıza öğeleri modelini ve diyagramda ilişkileri tanımlamak ve daha okunabilir yapmak için diyagramın düzenini değiştirebilirsiniz ekleyebilirsiniz.  
  
## <a name="the-layout-of-the-diagram"></a>Diyagram Düzeni  
 [!INCLUDE[dsl](../includes/dsl-md.md)] Tanım diyagramı sahip iki bölüm **sınıflar ve ilişkiler** bölüm ve **diyagram öğelerine** bölüm. **Sınıflar ve ilişkiler** bölüm alan sınıfları, etki alanı ilişkileri ve devralma görüntüler. **Diyagram öğelerine** bölüm şekil sınıfları, bağlayıcı sınıfları, Kulvar sınıfları ve oluşturulan Tasarımcısı Diyagramı görüntüler.  
  
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
 [Etki alanına özgü dil araçları sözlüğü](http://msdn.microsoft.com/en-us/ca5e84cb-a315-465c-be24-76aa3df276aa)



