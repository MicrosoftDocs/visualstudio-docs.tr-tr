---
title: 'Nasıl yapılır: içerik haritası gezintisini kullanma | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 4a688056-37dc-406a-9071-be2141e192fe
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: 19f9add69f8746962e6ed0ef9e4beea0f7ba37ec
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49259044"
---
# <a name="how-to-use-breadcrumb-navigation"></a>Nasıl yapılır: içerik haritası gezintisini kullanma
Görüntülenen etkinlikler kümesini değiştirmek için üç ana yolu vardır [!INCLUDE[wfd1](../includes/wfd1-md.md)]:  
  
1.  Bir alt etkinlik ayrıntılarına girmek çift tıklayın.  
  
2.  Bir üst etkinliğe gitmek için içerik haritası çubuğundaki bir düğmeye tıklayın.  
  
3.  Genişletme veya daraltma yerinde etkinlikler.  
  
### <a name="using-breadcrumb-navigation"></a>İçerik haritası gezintisini kullanma  
  
1.  Bir etkinliğin çift [!INCLUDE[wfd2](../includes/wfd2-md.md)] Kök etkinlik tıklandı etkinlik için değiştirilecek. Tıklandı etkinlik sonra tam olarak-kök dizininde genişletilir ve alt öğelerinden içerik haritası çubuğunda gösterilir. Bu durum bazen içinde veya dışında bir etkinlik ayrıntılara denir.  
  
2.  Geçerli Kök etkinlik öğesinin üst öğesi için gitmek için içerik haritası çubuğundaki etkinliği tıklatın.  
  
### <a name="expanding-or-collapsing-an-activity-in-place"></a>Genişletme veya daraltma yerinde bir etkinlik  
  
1.  Bir etkinlik köşeli çift tıklayarak genişletir veya daraltır. etkinliği yerinde.  
  
2.  Düğmeye tıklayarak durumu genişletme durumu değiştirildiğinde, yeni genişletme durumunu XAML içinde kaydedilir.  
  
    > [!WARNING]
    >  Tüm etkinlikleri yerinde genişletilebilir. İki durum vardır etkinlik yerinde genişletildiğinde: ya da etkinliğin üst alt yerinde genişletilecek izin vermez, (örneğin, bir akış etkinlikleri yerinde genişletilemez), veya etkinlik Tasarımcısı kendisine izin vermiyor yerinde genişletilebilir. Dahil etkinlik tasarımcıları hiçbiri rağmen [!INCLUDE[wfd2](../includes/wfd2-md.md)] ikinci davranışa sahip, bazı özel etkinlikleri bu davranışı sergiler.  
  
### <a name="expanding-all-or-collapsing-all-activities"></a>Tüm genişletme veya daraltma tüm etkinlikler  
  
1.  Kullanım **Tümünü Genişlet** ve **Daralt tüm** genişletmek veya geçerli içerik haritası kökü altındaki etkinliklerin tümünü daraltmak için kullanıcı arabiriminde düğmeleri. Tümünü Genişlet ve Tümünü Daralt Not genel durumlarını aynıdır. Bu'ye kadar zaman içerik haritalı gezinme, Tümünü Genişlet kullanarak Kök etkinlik değiştirmek veya tüm durum Daralt kalıcı olduğu anlamına gelir **geri**.  
  
2.  Tüm genişletme uyguladığınız veya tüm durum Daralt sonra tıklayabilirsiniz **geri** her etkinliğe daha önce uyguladığınız durumu bakarak için geri dönmek için görüntülenen düğme.  
  
    > [!WARNING]
    >  Bir etkinlik ise gibi <xref:System.Activities.Statements.Flowchart>, ettikten dışında bir yerde genişletin, işlevselliği ile ilişkili **Tümünü Genişlet** ve **Tümünü Daralt** düğmeleri devre **akış çizelgesi**  Tasarımcısı. [!INCLUDE[crabout](../includes/crabout-md.md)] **akış** Tasarımcı, bkz: [akış](../workflow-designer/flowchart-activity-designer.md) konu.  
  
    > [!WARNING]
    >  Tümünü Genişlet de sahip bir özel efekt **anahtar** ve **TryCatch** etkinlik tasarımcıları. Tıkladığınızda **Tümünü Genişlet**, tüm anahtar durumlarında ve try/catch/finally bloğu görüntülenir. Tıklayarak **geri** veya **Tümünü Daralt** bu tasarımcıları içinden tıklayabilirsiniz varsayılan durumlarına, bir tek çalışması/içeriğini görüntülemek için bloğu döndüren.