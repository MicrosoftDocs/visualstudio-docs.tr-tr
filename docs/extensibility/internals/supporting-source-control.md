---
title: Kaynak denetimi destekleyen | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], supporting
ms.assetid: 567acde3-354e-4f39-8d99-0ef86c103396
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 9ae3590a5d02c2b3f1d4b67f724d0177f671f7d2
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31130696"
---
# <a name="supporting-source-control"></a>Kaynak denetimi destekleme
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Dosya kullanıma, iadeler ve diğer kaynak denetimi işlemleri proje veya Düzenleyicisi'ni destekler. Kaynak Denetim istemcisi olarak [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] bir kaynak denetimi paketiyle gibi etkileşim kuracak şekilde tasarlanmıştır [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)], arşivleme, sürüm ve dosyaları dinamik olarak tanımlanan bir dizi denetim tesislerinde sağlar.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Kaynak Denetimi Paketleri için Model](../../extensibility/internals/model-for-source-control-packages.md)  
 Proje türü uygulanmalı arabirimleri açıklayan kaynak denetimi desteklemek için.  
  
 [Tasarım kararları](../../extensibility/internals/source-control-design-decisions.md)  
 Proje türüne nasıl uygulayacağınıza yanıtlarını değiştirmek sorular sağlar.  
  
 [Yapılandırma ayrıntıları](../../extensibility/internals/source-control-configuration-details.md)  
 Kaynak denetimi destekleyen bir proje türü uyarlamasını nasıl değiştiğini açıklar.  
  
 [Projeler ve editörler için ek yönergeler](../../extensibility/internals/additional-source-control-guidelines-for-projects-and-editors.md)  
 Proje türleri ve editörler için en iyi uygulamaları açıklar.  
  
 [Çalışma zamanı ayrıntıları](../../extensibility/internals/source-control-runtime-details.md)  
 Bir kullanıcı, bir kaynak denetimi sisteme eklediğinde proje kaydetmek açıklar.  
  
## <a name="reference"></a>Başvuru  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>  
 Ortam ya da bir dosyadır hakkında bellekte değiştirilemez veya kaydedilmiş için kaynak denetimi paketi belirtir.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>  
 Projeler ve kendilerini kaynak denetimiyle kaydetmek ve kaynak denetimi durumu hakkında bilgi edinmek için hiyerarşileri sağlar.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>  
 Proje dosyaları ve proje öğeleri için kaynak denetimi sağlamak için bir proje sistemindeki uygulanmadı.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>  
 Göre projeleri ekleyin, kaldırın veya bir dosya veya dizin bir çözümde yeniden adlandırma izni ortamını sorgulamak için kullanılır.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>  
 Proje dosyaları veya dizinleri için yapılan değişiklikler istemcilere bildirir.  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [Proje Türleri](../../extensibility/internals/project-types.md)  
 Temel yapı taşlarını olarak projeleri genel bir bakış sağlar [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] tümleşik geliştirme ortamı (IDE). Projeleri oluşturma ve kod derleme nasıl kontrol açıklayan ek konulara bağlantılar sağlanmaktadır.