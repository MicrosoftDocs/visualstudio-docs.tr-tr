---
title: 'Nasıl yapılır: eski dil hizmetinde gizli metin desteği | Microsoft Docs'
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
- hidden text, supporting
- editors [Visual Studio SDK], hidden text
- language services, implementing hidden text regions
ms.assetid: 1c1dce9f-bbe2-4fc3-a736-5f78a237f4cc
caps.latest.revision: 22
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 5d5451576115dcada98f6b8f7daaf1cca5a86f95
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51727227"
---
# <a name="how-to-provide-hidden-text-support-in-a-legacy-language-service"></a>Nasıl yapılır: eski dil hizmetinde gizli metin desteği
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Anahat bölgelerin yanı sıra gizli metin bölgeler oluşturabilirsiniz. İstemci tarafından denetlenen veya Düzenleyicisi tarafından denetlenen gizli metin bölgeleri olabilir ve metnin bir bölge tamamen gizlemek için kullanılır. Düzenleyici gizli bölge yatay çizgiler olarak görüntüler. Bu HTML Düzenleyici görünümünde yalnızca betik örneğidir.  
  
## <a name="procedure"></a>Yordam  
  
#### <a name="to-implement-a-hidden-text-region"></a>Bir gizli metin bölgeye uygulamak için  
  
1.  Çağrı `QueryService` için <xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager>.  
  
     Bu bir işaretçi döndürür <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager>.  
  
2.  Çağrı <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.GetHiddenTextSession%2A>, verilen metin arabelleği için bir işaretçi olarak geçen. Bu, gizli metin oturumu zaten için arabellek var olup olmadığını belirler.  
  
3.  Zaten bir tane sonra biri ve var olan bir işaretçi oluşturun gerekmez <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> nesne döndürülür. Bu işaretçinin, listeleme ve gizli metin bölgeler oluşturmak için kullanın. Aksi takdirde, çağrı <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.CreateHiddenTextSession%2A> arabellek için gizli metin oturum oluşturmak için.  
  
     Bir işaretçi <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> nesne döndürülür.  
  
    > [!NOTE]
    >  Çağırdığınızda `CreateHiddenTextSession`, gizli metin istemci belirtebilirsiniz (diğer bir deyişle, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextClient>). Gizli metin istemci gizli metni veya anahat oluşturma genişletilmiş veya daraltılmış kullanıcı tarafından size bildirir.  
  
4.  Çağrı <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession.AddHiddenRegions%2A> ekleyin ya da daha yeni aşağıdakileri belirten bölgeleri teker teker anahat `reHidReg` (<xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion>) parametre:  
  
    1.  Bir değer belirleyebilirsiniz `hrtConcealed` içinde `iType` üyesi <xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion> yapısı bir anahat bölgesi yerine gizli bir bölge oluşturduğunuzu belirtmek için.  
  
        > [!NOTE]
        >  Bölgeleri altına gizlenmiş gizlendiğinde Düzenleyicisi satırları kendi varlığını göstermek için gizli bölgeler etrafında otomatik olarak görüntüler.  
  
    2.  Bölge istemci tarafından denetlenen veya Düzenleyicisi tarafından denetlenen içinde olup olmadığını belirtin `dwBehavior` üyeleri <xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion> yapısı. Akıllı ana hat oluşturma uygulamanız Düzenleyicisi ve istemci denetlenen anahat ve gizli metin bölgeleri bir karışımını içerebilir.

