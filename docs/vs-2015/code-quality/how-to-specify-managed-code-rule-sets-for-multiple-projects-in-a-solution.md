---
title: 'Nasıl yapılır: bir çözümde birden çok proje için yönetilen kod kural kümesi belirtme | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.codeanalysis.propertypages.solution
ms.assetid: 92dc3250-a010-4396-b515-f03a0b30cd2a
caps.latest.revision: 14
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: d2469491eeb5419c70e208bbf6e1ed7809657dbc
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49218705"
---
# <a name="how-to-specify-managed-code-rule-sets-for-multiple-projects-in-a-solution"></a>Nasıl Yapılır: Bir Çözümde Birden Çok Proje İçin Yönetilen Kod Kural Kümesi Belirtme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Varsayılan olarak, Microsoft en az önerilen kurallar Kod Analizi bir çözümün tüm yönetilen projelere atanır *kural kümesi*. Proje Özellikleri iletişim kutusunda çözüm için bir çözüm atanmış olan kural kümeleri değiştirebilirsiniz.  
  
> [!NOTE]
>  Varsayılan olarak, Kod Analizi projesi bir derleme adımı olarak çalıştırılmaz. Kod Analizi bir derleme adımı olarak etkinleştirmek için bkz: [nasıl yapılır: yönetilen kod projesi için Kod Analizi yapılandırma](../code-quality/how-to-configure-code-analysis-for-a-managed-code-project.md).  
  
### <a name="to-specify-a-rule-set-for-multiple-projects-in-a-managed-code--solution"></a>Yönetilen kod çözümde birden çok proje için bir kural belirtmek için  
  
1.  İçinde [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)]. [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], veya [!INCLUDE[vsPro](../includes/vspro-md.md)] çözümü açın.  
  
2.  Üzerinde **Çözümle** menüsünde tıklatın **çözüm için Kod Analizi yapılandırma**.  
  
3.  Gerekirse genişletin **ortak özellikler**ve ardından **Kod Analizi ayarları**.  
  
4.  Bir veya daha fazla proje için bir kural belirtebilirsiniz.  
  
    -   Bir kural kümesi için bir projeyi belirtmek için proje adına tıklayın.  
  
    -   Birden çok proje için bir kural belirtmek için CTRL tuşunu basılı tutun ve proje adları tıklayın.  
  
    -   Çözümdeki tüm projeleri belirtmek için SHIFT tuşunu basılı tutun ve Proje listesinde tıklayın.  
  
5.  Tıklayın **kural kümesi** alan bir proje ve kural adını ayarlayın uygulamak istediğiniz'a tıklayın.



