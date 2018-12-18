---
title: Sorgu düzenleme sorgu kaydetme (kaynak denetimi VSPackage'ı) | Microsoft Docs
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
- QEQS events
- Query Edit Query Save events
- source control packages, Query Edit Query Save events
ms.assetid: c360d2ad-fe42-4d65-899d-d1588cc8a322
caps.latest.revision: 18
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 170056db4269b8dd69f241093c467243b75131b7
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51763251"
---
# <a name="query-edit-query-save-source-control-vspackage"></a>Sorgu Düzenleme Sorgu Kaydetme (Kaynak Denetimi VSPackage’ı)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Sorgu düzenleme sorgu kaydetme (QEQS) olayları düzenleyicileri yayınlayabilirsiniz. [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Alıcı QEQS olayların olmasını kaynak denetimi saplama QEQS hizmet uygular. Bu olaylar, ardından şu anda etkin kaynak denetimi VSPackage'ı verilmiş. Etkin kaynak denetimi VSPackage'ı uygulayan <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2> ve yöntemleri. Yöntemlerinin `IVsQueryEditQuerySave2` arabirimi genellikle ilk kez ve hemen bir belge kaydedilmeden önce bir belge düzenlenemez hemen önce çağrılır.  
  
## <a name="queryeditquerysave-events"></a>QueryEditQuerySave olayları  
 Kaynak denetimi VSPackage'ı uygulayarak QEQS olayları işlemelidir `IVsQueryEditQuerySave2` arabirimi ve gerekli yöntemleri. VSPackage'ı en azından uygulamalıdır iki yöntem kısa bir açıklaması aşağıdadır. Gerçek uygulamalar kaynak denetimi modeli mantığına uygun olarak olmalıdır.  
  
### <a name="queryeditfiles-method"></a>QueryEditFiles yöntemi  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> Bir dosyayı değiştirmek herhangi bir proje veya Düzenleyicisi istediğinde çağrılır. İdeal olarak, bu yöntem çağrılır *önce* dosyasını değiştirdikten ve bir dosya kaydedildiğinde. Çağrıldığında `IVsQueryEditQuerySave2::QueryEditFiles` yöntemi, belirli dosyalar kaynak denetimi altında olup kullanıma alınması için ihtiyaçları ve yoksa bunlar yeniden yüklenebilir denetler. Koşullar dosyalar düzenlenebilir olmasını engellemek, `IVsQueryEditQuerySave2::QueryEditFiles` yöntemi düzenlemeyi iptal etmek için çağırma program söyler. Ayrıca, arayanın çağırma modu belirtmek de mümkündür. Yalnızca, herhangi bir UI görünmesine neden olmazsa, "sessiz" modunda, bu yöntem eylem alır. UI kaçınılmaz ise bir bayrak sorun belirtmek için iade edilmesi gerekir.  
  
 Yöntemi, işlemsel bir şekilde davranır; diğer bir deyişle, tek bir dosya düzenlemeyi iptal edilirse, düzenleme için tüm dosyaları iptal edildi. Buna karşılık, Düzen izin verilirse, tüm dosyaları için kullanılabilir. Bu yöntem bir kez belirli bir dosya kümesi için düzenleme izin veriyorsa, arka arkaya çağrı aynı dosya kümesi için düzenleme her zaman izin gerekir. Dosyaları kapalı, kaydedilen ve yeniden kadar izin ver-düzenleme döngü devam eder; öznitelikleri (Özellikler) değiştirene kadar; veya kaynak denetim paketi değiştirilene kadar. Uygulama dikkate alınması gereken durumlarda `IVsQueryEditQuerySave2::QueryEditFiles` yöntemi birden çok dosyaları, özel dosyaları içerir, kullanıcı ve bellek içi düzenlemeler iptal edin.  
  
### <a name="querysavefiles-method"></a>QuerySaveFiles yöntemi  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFiles%2A> Dosyaları kaydetmek herhangi bir proje veya Düzenleyicisi gerektiğinde çağırılır. Çağrıldığında `IVsQueryEditQuerySave2::QuerySaveFiles` yöntemi, belirli dosyalar salt okunursa ve bunların kaynak denetimi altında olup olmadığını denetler. Dosyaları kullanıma alınması gerekiyorsa, arama için kaynak denetim paketi temsilci. Koşullar kaydedilmiş dosyaları engelliyorsa `IVsQueryEditQuerySave2::QuerySaveFiles` yöntemi kaydetme işlemini iptal etmek için Düzenleyicisi söylemeniz gerekir. Olduğu gibi `IVsQueryEditQuerySave2::QueryEditFiles` yöntemi mümkündür arayan bir çağırma modu belirtmek. Yalnızca, herhangi bir UI görünmesine neden olmazsa, "sessiz" modunda, bu yöntem eylem alır. UI kaçınılmaz ise bir bayrak sorun belirtmek için iade edilmesi gerekir.  
  
 Bu yöntem, işlemsel bir şekilde davranmalıdır; diğer bir deyişle, tek bir dosya kaydetme iptal edilirse, kaydetme tüm dosyalar için iptal edildi. Kaydetme izin verilirse, buna karşılık, onu tüm dosyalara izin verilmesi gerekir. Olduğu gibi `IVsQueryEditQuerySave2::QueryEditFiles` yöntemi, uygulamada dikkate alınması gereken durumlarda `IVsQueryEditQuerySave2::QuerySaveFiles` yöntemi birden çok dosyaları, özel dosyaları içerir, kullanıcı ve bellek içi düzenlemeler iptal edin.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>

