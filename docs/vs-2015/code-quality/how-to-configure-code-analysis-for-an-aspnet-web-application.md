---
title: 'Nasıl yapılır: bir ASP.NET Web uygulaması için kod çözümlemesini yapılandırma | Microsoft Docs'
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
- vs.codeanalysis.propertypages.asp
ms.assetid: b3000b31-fd9d-489e-81a2-a4bee49453ba
caps.latest.revision: 15
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: bf7450341dd166977d67639f4f3762fae6ef89c8
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49283913"
---
# <a name="how-to-configure-code-analysis-for-an-aspnet-web-application"></a>Nasıl yapılır: Bir ASP.NET Web Uygulaması İçin Kod Çözümlemesini Yapılandırma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

İçinde [!INCLUDE[vsPreShort](../includes/vspreshort-md.md)] ve [!INCLUDE[vsUltShort](../includes/vsultshort-md.md)] Kod Analizi listesinden seçtiğiniz *kural kümeleri* uygulamak için [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] Web uygulaması. Varsayılan kuralı Microsoft Mininimum önerilen kurallar kümesidir. Başka bir kural Web sitesine uygulamak için kümesini seçebilirsiniz.  
  
### <a name="to-configure-a-rule-set-for-an-aspnet-page-framework-project"></a>Bir ASP.NET sayfası Framework projesi için bir kural yapılandırmak için  
  
1.  Web sitesinde seçin **Çözüm Gezgini**.  
  
2.  Üzerinde **Çözümle** menüsünde tıklatın **Web sitesi için Kod Analizi yapılandırma**.  
  
3.  Seçtiğiniz çözüm ve birden çok proje çözümü varsa, yapı, yapılandırma ve hedef işletim sisteminden seçin **yapılandırma** ve **Platform** listeler.  
  
4.  Çözümde her proje için tıklatın **kural kümesi** sütun ve ardından çalıştırmak için kuralın adını ayarlayın.  
  
5.  Varsayılan olarak, Çözümdeki tüm projeleri üzerinde kod analizini Çalıştır. Belirli bir projenin kod analizini etkinleştir veya devre dışı bırakmak için aşağıdaki adımları izleyin:  
  
    1.  Proje adına sağ tıklayın ve ardından Özellikler seçeneğine tıklayın.  
  
    2.  İşaretleyin veya temizleyin **kod çözümlemeyi etkinleştir** onay kutusu. Ayrıca kod analizini el ile seçerek çalıştırabilirsiniz **Web sitesinde kod analizini Çalıştır** gelen **Çözümle** menüsü.  
  
6.  İçinde **bu kural kümesini Çalıştır** aşağı açılan listesinde, aşağıdaki adımları izleyin:  
  
    -   Kullanmak istediğiniz bir kural kümesi seçin.  
  
    -   Seçin  **\<Gözat >** var olan bir özel kural kümesini belirlemek için listesinde değil.  
  
    -   Bir özel kural kümesi tanımlar. Daha fazla bilgi için [özel kural kümeleri oluşturma](../code-quality/creating-custom-code-analysis-rule-sets.md).



