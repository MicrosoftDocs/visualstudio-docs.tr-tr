---
title: İç içe geçmiş projeleri için sihirbaz desteği | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Add Item wizard
- nested projects, wizard support
- New Project wizard
ms.assetid: 1b496acc-b326-4cdb-bb48-e3b5c6f12e05
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 14e8a32db2542ae1729a7fdc87cc2ab32845f8ca
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31137501"
---
# <a name="wizard-support-for-nested-projects"></a>İç içe geçmiş projeleri için sihirbaz desteği
İç içe geçmiş projeleri için ana proje uygulayabilirsiniz iki sihirbaz IDE çalıştırır: **yeni proje** Sihirbazı'nı ve **Öğe Ekle** Sihirbazı.  
  
 Bir kullanıcı başlıyorsa **yeni proje** seçerek Sihirbazı **Proje Ekle** tıklatıp **yeni proje** Dosya menüsünden veya seçerek **Ekle** ve sağ **yeni proje** IDE Çözüm Gezgini'nde çalıştıran **AddProject** komut ve üst projenin uyarlamasını **AddProject**komut ya da bir şablon proje dosyası ya da bir bağlam parametreleri kümesini içeren bir Sihirbazı'nı (.vsz) dosyası döndürür.  
  
 Benzer şekilde, bir üst projenin uyarlamasını **addItem** sihirbazları farklı bir bağlam parametreleri kümesini içeren bir .vsz dosyası döndürür.  
  
 Sihirbazları hakkında daha fazla bilgi için bkz: [Sihirbazı'nı (. Vsz) dosya](../../extensibility/internals/wizard-dot-vsz-file.md), [bağlam parametreleri](../../extensibility/internals/context-parameters.md) ve [proje ve öğe şablonlarını kaydetme](../../extensibility/internals/registering-project-and-item-templates.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>   
 [Projeleri İç İçe Geçirme](../../extensibility/internals/nesting-projects.md)