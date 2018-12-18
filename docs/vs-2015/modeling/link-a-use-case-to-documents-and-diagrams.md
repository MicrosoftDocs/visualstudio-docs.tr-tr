---
title: Kullanım örneğini belgelere ve diyagramlara bağlama | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.teamarch.usecasediagram.artifact.properties.artifactlink
- vs.teamarch.usecasediagram.artifact
helpviewer_keywords:
- use case diagrams
ms.assetid: 4c9ed205-9197-4ed5-b39d-ddfa24a0a421
caps.latest.revision: 12
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: a5b4ef580825115a1d44c3abb39404332a4277ea
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51787919"
---
# <a name="link-a-use-case-to-documents-and-diagrams"></a>Kullanım örneğini belgelere ve diyagramlara bağlama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bir kullanım örneği bir kullanım durumu diyagramı, başka bir diyagrama veya belge bağlayabilirsiniz. Örneğin, aşağıdaki diyagramları ve belgeler için kullanım örneği bağlayabilirsiniz:  
  
- Kullanıcılar ve sistem veya ana bileşenleri arasındaki etkileşimler tarafından kullanım örneğinin hedeflerini nasıl gerçekleştirildiğini gösteren bir sıralı diyagram.  
  
- Kullanım örneği gerçekleştirdikleri sırada ayrıntılı eylemler veya kullanıcıları ve sistemin ana bileşenlerini gösteren bir etkinlik diyagramı.  
  
- Bir OneNote sayfası veya ayrıntılı kullanım örneğini açıklanacak paragraf.  
  
- Bir Word belgesi veya ayrıntılı kullanım örneğini açıklanacak PowerPoint sunusu. Bu tür belgeleri çözümü veya bir konumda bir SharePoint sitesi gibi ekip için erişilebilir kalmasını sağlayabilirsiniz.  
  
  Kullanım örneği, belgeye bağlamak için kullanım durumu diyagramında bir yapı oluşturmak ve yapıya kullanım örneğine bağlanın. Yapı'nın Özellikleri'nde bir diyagram veya belge dosya yolunu ayarlayın. Yapıt, diğer diyagram veya belge çift tıkladığınızda açılır.  
  
  İstediğiniz kadar çok sayıda yapıtları her kullanım örneği bağlanabilirsiniz. Öğe bir kullanım durumu diyagramı üzerindeki diğer türlerdeki yapıtları bağlayabilirsiniz.  
  
### <a name="to-open-a-document-associated-with-an-artifact"></a>Bir yapı ile ilişkilendirilmiş bir belgeyi açmak için  
  
-   Kullanım durumu diyagramında yapıt şekle çift tıklayın.  
  
     İlişkili belge açılır.  
  
### <a name="to-link-a-use-case-to-a-diagram-or-file-in-the-same-solution"></a>Bir kullanım durumu diyagramı veya aynı çözüm içindeki dosya bağlamak için  
  
1.  Bir sıralı diyagram veya kullanım örneğinin bir senaryoyu göstermek üzere etkinlik diyagramı gibi bir diyagramı.  
  
2.  Kullanım durumu diyagramı geri dönün.  
  
3.  Çözüm Gezgini'nden boş bir kısmına kullanım durumu diyagramı diyagram veya dosya sürükleyin.  
  
4.  Yapıdan kullanım örneği bağlanırken bir **bağımlılık**.  
  
### <a name="to-link-to-a-solution-file-such-as-a-word-document-or-powerpoint-presentation"></a>Bir çözüm dosyası gibi bir Word belgesi veya PowerPoint sunumu bağlamak için  
  
1.  Belge ekleyin.  
  
    1.  Word belgesi çözümü olarak aynı Windows klasöre taşıyın.  
  
    2.  Çözüm Gezgini'nde çözüme sağ tıklayın, fareyle **Ekle**ve ardından **var olan öğe**.  
  
    3.  Word belgesine gelin ve tıklayın **Ekle**.  
  
         Word belgesi bir çözüm klasörü Çözüm Gezgini'nde görünür.  
  
2.  Çözüm Gezgini'nden kullanım durumu diyagramı boş bir kısmına Word belgesi sürükleyin.  
  
     Yeni Yapıt görünür.  
  
3.  Yapıdan kullanım örneği bağlanırken bir **bağımlılık**.  
  
### <a name="to-link-to-a-shared-document-onenote-element-or-web-page"></a>Paylaşılan belge, OneNote öğesi veya web sayfası bağlamak için  
  
1.  Paylaşılan öğe URL'sini alın. Bu, örneğin, bir ağ dosya yolu başlangıç olabilir '\\\\', veya bir web sayfası veya Sharepoint URL'si başına 'http://' veya bir OneNote bölümüne bir bağlantı sayfa, paragraf başına ' onenote:'.  
  
2.  Araç kutusunda tıklayın **Yapıt** ve kullanım örneği diyagramı'ye tıklayın.  
  
3.  Yeni yapıt seçili yazın veya URL'sini yapıştırın **köprü** özelliği.  
  
    > [!NOTE]
    >  Bir dosya yolu sağlamak istiyorsanız, bir dosya ya da ortak bir çalışma alanı seçmek en iyi (başlayarak '\\\\'), veya Visual Studio çözümündeki bir dosya. Bu dosya yolu başka bir takım üyesinin bilgisayarda geçerli olarak kalmasını sağlar veya çözüm taşınır. Bir Word belgesi gibi bir belge çözümünüze eklemek için Çözüm Gezgini'nde çözüme sağ tıklatın, **Ekle** ve ardından **var olan öğe**.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [UML Kullanım durumu diyagramları: başvuru](../modeling/uml-use-case-diagrams-reference.md)   
 [UML Kullanım durumu diyagramları: yönergeler](../modeling/uml-use-case-diagrams-guidelines.md)   
 [UML modellerini ve diyagramları düzenleme](../modeling/edit-uml-models-and-diagrams.md)   
 [Uygulamanız için model oluşturma](../modeling/create-models-for-your-app.md)



