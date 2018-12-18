---
title: İç içe projeler için addItem iletişim kutusunu filtreleme | Microsoft Docs
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
- filtering, nested projects
- nested projects, AddItem dialog box filtering
ms.assetid: 5b3e352e-7f18-4f66-be16-b0ad55637ce5
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 363ba8e38ae2de445bd18bb9378d48aa4d824298
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51769770"
---
# <a name="filtering-the-additem-dialog-box-for-nested-projects"></a>İç içe Projeler için AddItem İletişim Kutusunu Filtreleme
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Görüntülerken bir **addItem** ana proje iç içe geçmiş proje için iletişim kutusu, hangi öğeleri iletişim kutusunda görüntülenen denetleyebilirsiniz.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2> Arabirimi sayesinde filtre olacak düğümleri bir **addItem** iletişim kutusu. Alt projenin görüntülendiğinde **addItem** iletişim kutusu, üst uygulayabilirsiniz `IVsFilterAddProjectItemDlg` çocuğun projesinde gösterilecek arabirimi ve filtre öğeleri.  
  
 Projeleri, belirli bir üst projeleri altında işlevi tarafından gruplandırıldığında, uygulayabileceğiniz `IVsFilterAddProjectItemDlg` kullanıcı seçtiğinde **proje Öğe Ekle** iç içe geçmiş bir projedeki kısayol menüsünde. Uygulama `IvsFilterAddProjectItemDlg displays` yalnızca proje öğelerini ya da bu gruba belirli dosyaları. Aynı dizinde depolanan bile diğer gruplar için proje öğeleri iletişim kutusu dışı filtrelenir.  
  
 Kullanıcı açtığında **addItem** alt, üst projenin uygulaması için iletişim kutusu `IVsFilterAddProjectItemDlg` arabirimi çağrılır.  
  
 `IVsFilterAddProjectItemDlg` Arabirimi, kategoriye göre filtreleme de uygulayabilirsiniz. Daha fazla bilgi için [ekleme yeni öğe iletişim kutularına öğe eklemeyi](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md) ve [kaydetme proje ve öğe şablonları](../../extensibility/internals/registering-project-and-item-templates.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>   
 [Öğeler ekleme yeni öğe Ekle iletişim kutuları](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)   
 [Proje ve öğe şablonlarını kaydetme](../../extensibility/internals/registering-project-and-item-templates.md)   
 [Projeleri İç İçe Geçirme](../../extensibility/internals/nesting-projects.md)

