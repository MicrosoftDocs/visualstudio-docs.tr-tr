---
title: Sorgu düzenleme sorgu (kaynak denetimi VSPackage) kaydetme | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- QEQS events
- Query Edit Query Save events
- source control packages, Query Edit Query Save events
ms.assetid: c360d2ad-fe42-4d65-899d-d1588cc8a322
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: bf4fd74544e0646a84e4fdc37f35ba84b301f693
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31131523"
---
# <a name="query-edit-query-save-source-control-vspackage"></a>Sorgu düzenleme sorgusu (kaynak denetimi VSPackage) Kaydet
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Düzenleyiciler Sorgu Düzenle sorgu kaydedin (QEQS) olayları yayınlayabilirsiniz. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Alıcı QEQS olayların olmasını kaynak denetimi saplama QEQS hizmeti uygular. Bu olaylar sonra şu anda etkin kaynak denetimine VSPackage verilmiş. VSPackage uygulayan etkin kaynak denetimi <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2> ve onun yöntemleri. Yöntemlerinin `IVsQueryEditQuerySave2` arabirimi genellikle ilk kez ve hemen bir belge kaydedilmeden önce bir belge düzenlenmiş hemen önce çağrılır.  
  
## <a name="queryeditquerysave-events"></a>QueryEditQuerySave olayları  
 Kaynak denetimi VSPackage uygulayarak QEQS olayları işlemelidir `IVsQueryEditQuerySave2` arabirimi ve gerekli yöntemleri. Aşağıda VSPackage en azından uygulamalıdır iki yöntem kısa bir açıklaması verilmiştir. Gerçek uygulamayı kaynak denetimi modeli mantığı uygun olmalıdır.  
  
### <a name="queryeditfiles-method"></a>QueryEditFiles yöntemi  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> Bir dosyayı değiştirmek herhangi bir proje veya Düzenleyicisi istediği zaman çağrılır. İdeal olarak, bu yöntem çağrılır *önce* dosya değiştirilmiş ve bir dosya kaydedildiğinde. Çağrıldığında, `IVsQueryEditQuerySave2::QueryEditFiles` yöntemi denetler belirli dosyaları kaynak denetimi altında olup, bunlar kullanıma alınması gerekip gerekmediğini ve olup bunların yeniden. Koşullar dosyalar düzenlenebilir engelleyen varsa `IVsQueryEditQuerySave2::QueryEditFiles` yöntemi düzenlemeyi iptal etmek için çağıran program söyler. Ayrıca, çağıran çağırma modu belirtmek de mümkündür. Yalnızca onu görünen herhangi bir UI neden olmazsa, "sessiz" modunda bu yöntem eylem alır. UI kaçınılmaz ise, sorun belirten bir bayrak iade edilmesi gerekir.  
  
 Yöntemi bir işlem şekilde davranır; diğer bir deyişle, Düzen tek bir dosyayı iptal edilirse, düzenleme için tüm dosyaları iptal edildi. Düzenlemeye izin, buna karşılık, onu tüm dosyalara izin verilir. Bu yöntem, belirli bir dosya kümesi için bir kez düzenleme izin veriyorsa, bu her zaman aynı dosyaları kümesi için sonraki çağrılar düzenleme izin vermeniz gerekir. Dosyaları kapalı, kaydedilmiş ve yeniden kadar izin ver-düzenleme döngü devam eder; öznitelikleriyle (Özellikler) değiştirene kadar; veya kaynak denetimi paketi değiştirilene kadar. Uygulama dikkate alınması gereken durumlarda `IVsQueryEditQuerySave2::QueryEditFiles` yöntemi birden çok dosyaları, özel dosyaları içerir, kullanıcı ve bellek içi düzenlemeler iptal edin.  
  
### <a name="querysavefiles-method"></a>QuerySaveFiles yöntemi  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFiles%2A> Dosyaları kümesini kaydetmek herhangi bir proje veya Düzenleyicisi gerektiğinde çağrılır. Çağrıldığında, `IVsQueryEditQuerySave2::QuerySaveFiles` yöntemi verilen dosyalar salt okunur olduğunda ve kaynak denetimi altında olduğunu denetler. Dosyaları kullanıma alınması gerekiyorsa, çağrı için kaynak denetimi paketi temsilci. Koşullar kaydedilmesini engeller dosyaları engelliyorsa `IVsQueryEditQuerySave2::QuerySaveFiles` Yöntemi Düzenleyicisi'ni kaydetme işlemini iptal etmek için söyleyin gerekir. İle `IVsQueryEditQuerySave2::QueryEditFiles` yöntemi, onu mümkündür çağıran çağırma modu belirtmek. Yalnızca onu görünen herhangi bir UI neden olmazsa, "sessiz" modunda bu yöntem eylem alır. UI kaçınılmaz ise, sorun belirten bir bayrak iade edilmesi gerekir.  
  
 Bu yöntem, bir işlemsel davranışlar sergiliyor gerekir; diğer bir deyişle, tek bir dosyayı Kaydet iptal edilirse, kaydetme tüm dosyalar için iptal edildi. Kaydetme izin veriliyorsa, buna karşılık, onu tüm dosyalara izin verilmelidir. İle `IVsQueryEditQuerySave2::QueryEditFiles` yöntemi, uygulamada dikkate alınması gereken durumlarda `IVsQueryEditQuerySave2::QuerySaveFiles` yöntemi birden çok dosyaları, özel dosyaları içerir, kullanıcı ve bellek içi düzenlemeler iptal edin.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>