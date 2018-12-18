---
title: Kalıcılığı ve çalışmasını belge tablo | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- persistence, managing
- IVsPersistHierarchyItem interface, implementing
- architecture, persistence
- running document table (RDT), architecture
ms.assetid: 27117eae-6c58-4189-a61a-1397a43b5ecf
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 51f3d2cc41c9adaf97215701ad01da2e59d245a8
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31129741"
---
# <a name="persistence-and-the-running-document-table"></a>Kalıcılığı ve çalışan belge tablosu
İçinde [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE projeleri bunlar hizmet kullanarak gerçekleştirmek, kullanıcıların proje öğeleri kalıcılığı yönetmek için tamamen sorumlu <xref:Microsoft.VisualStudio.Shell.Interop.SVsRunningDocumentTable>. Visual Studio ortamında Kalıcılık temel birimidir belgelerdir. Proje açma, kaydetme ve çalışan belge tablosu (RDT), tüm açık belgeleri durumunu izleyen bir kaynak belgelerle adlandırılmasını koordine.  
  
## <a name="managing-persistence"></a>Kalıcılık yönetme  
 Projeleri uygulayarak ortamı Kalıcılık Hizmet Denetim <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem> arabirimi. Ortam hiçbir zaman doğrudan kendisini kalıcı hale getirmek için bir belge ister olsa da, sahibi olan proje (veya hiyerarşi) belgeyi kaydetmek için sorar. Proje öğesi verilerini yerel dosyaları, uzak dosyaları, bir veritabanı, bir havuz veya diğer Orta kaydetmek için projeyi olanaklı kılar.  
  
 Genel ortam RDT tutar. Tüm açık pencereleri girişlerinde ortamı tutar ve bunların kılar RDT belgelerde bir çözüm kapatıldığında gibi özel bildirimleri alma. Ayrıca, RDT, karşılık gelen düğümlerini izlemek ortamı için mümkün kılar **Çözüm Gezgini**. RDT açık, kalıcı nesne proje dosyalarını ve proje öğesi belgeleri de dahil olmak üzere, her bir kayıt tutar.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Çalışan belge tablosu](../../extensibility/internals/running-document-table.md)   
 [IDE’de Seçim ve Para Birimi](../../extensibility/internals/selection-and-currency-in-the-ide.md)