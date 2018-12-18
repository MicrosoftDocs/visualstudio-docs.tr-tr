---
title: İç içe projeler için sihirbaz desteği | Microsoft Docs
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
- Add Item wizard
- nested projects, wizard support
- New Project wizard
ms.assetid: 1b496acc-b326-4cdb-bb48-e3b5c6f12e05
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: fe3bb7b5a97fc0e840a425231765f3d33fb98764
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51785904"
---
# <a name="wizard-support-for-nested-projects"></a>İç içe Projeler için Sihirbaz Desteği
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

IDE ana proje iç içe projeler için uygulayabileceğiniz iki sihirbazları çalıştırır: **yeni proje** Sihirbazı ve **Öğe Ekle** Sihirbazı.  
  
 Bir kullanıcı başlarsa **yeni proje** seçerek Sihirbazı **Proje Ekle** tıklayıp **yeni proje** Dosya menüsünden veya seçerek **Ekle** sağ **yeni proje** IDE Çözüm Gezgini'nde çalışan **AddProject** komut ve üst projenin uygulaması **AddProject**komut ya da bir şablon proje dosyası veya bir dizi bağlam parametreleri içeren bir sihirbaz (.vsz) dosyası döndürür.  
  
 Benzer şekilde, bir üst projenin uygulaması **addItem** sihirbazları farklı bir bağlam parametreleri kümesini içeren bir .vsz dosyası döndürür.  
  
 Sihirbazları hakkında daha fazla bilgi için bkz: [Sihirbazı (. Vsz) dosya](../../extensibility/internals/wizard-dot-vsz-file.md), [bağlam parametreleri](../../extensibility/internals/context-parameters.md) ve [proje ve öğe şablonlarını kaydetme](../../extensibility/internals/registering-project-and-item-templates.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>   
 [Projeleri İç İçe Geçirme](../../extensibility/internals/nesting-projects.md)

