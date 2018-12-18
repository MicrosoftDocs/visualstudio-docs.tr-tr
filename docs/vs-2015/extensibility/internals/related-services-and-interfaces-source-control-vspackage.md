---
title: İlgili hizmetler ve arabirimler (kaynak denetimi VSPackage'ı) | Microsoft Docs
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
- source control packages, interfaces
- interfaces, source control packages
ms.assetid: 3e96e838-5675-46bb-99cf-40d420086038
caps.latest.revision: 27
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 8f308c0d8669bc8950578ffc615ebe64b91a4ea7
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51764323"
---
# <a name="related-services-and-interfaces-source-control-vspackage"></a>İlgili Hizmetler ve Arabirimler (Kaynak Denetimi VSPackage’ı)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Bu bölümde, tüm kaynak denetimi VSPackage'ı ile ilgili arabirimler listelenmiştir [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)]. Kaynak denetimi VSPackage'ı, bazı bu arabirimleri uygulayan ve diğer kaynak denetimi görevlerini gerçekleştirmek için kullanır.  
  
## <a name="interfaces-implemented-by-and-for-source-control-vspackages"></a>Kaynak denetimi VSPackage'larını ve tarafından uygulanan arabirimler  
 Aşağıdaki arabirimlerinden açıklanan [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)], ve bir alt kümesini istenen özellik kendine bağlı olarak kaynak denetimi VSPackage'ı uygular. Bazı arabirimler işaretli olarak gerekli ve her kaynak denetimi VSPackage'ı uygulanmalıdır.  
  
 Bir paketi uygulamayan, bu arabirimlerin [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] varsayılan uygulamasını sağlar. Varsayılan uygulama yok VSPackage kaydedildiğinde durum ve proje için tasarlanmıştır Not denetlenir. Bu arabirimler için varsayılan uygulama bırakmak yerine tüm gerekli arabirimleri doğru yazılmış kaynak denetimi VSPackage'ı uygular.  
  
 Kaynak denetimi VSPackage'ı bazılarını veya tümünü aşağıdaki arabirimlerinden kapsülleyen bir özel hizmet uygulamalıdır.  
  
 Arabirimleri şunlardır:  
  
-   Gerekli: Uygun varlık (Proje kaynak denetimi VSPackage'ı, kaynak denetimi saplama) arabirimini uygulaması gerekir.  
  
-   Önerilen: Varlık bu arabirimi uygulayan; Aksi takdirde, kaynak denetimi işlevlerini sınırlı olabilir.  
  
-   İsteğe bağlı: varlık daha zengin bir özellik kümesi sağlamak için bu arabirimi uygulayabilir.  
  
|Arabirim|Amaç|Uygulayan|Uygulansın mı?|  
|---------------|-------------|--------------------|----------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>|Düzenleyiciler, değiştirme veya bir dosyayı kaydetmeden önce bu arabirimi çağırın. Kaynak denetimi VSPackage'ı dosyayı kullanıma alın veya kullanıma alma başarısız olursa, işlem reddet.|Kaynak denetimi VSPackage'ı|Önerilen|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>|Bu arabirim, kaydetme ve projeler kaynak denetimi ile kaydı ve temel kaynak denetim karakterleri için destek sunarak gibi projeler için temel kaynak denetimi işlevlerini sağlar.|Kaynak denetimi VSPackage'ı|Gerekli|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>|Bu arabirim elde edilen <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> kullanarak <xref:System.Runtime.InteropServices.Marshal.QueryInterface%2A> işlevi veya yalnızca uygulama nesnesi atama `IVsHierarchy` için `IVsSccProject2`. Bir projedeki kaynak denetimi altında dosyaları alma veya proje konumu ve geçerli kaynak denetimi durumu bildiren için kullanılır.|Proje|Gerekli|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider>|Tümleştirme modülü, bu arabirimin geçerli etkin VSPackage'ı ayarlamak için kullanır.|Kaynak denetimi VSPackage'ı|Gerekli|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>|Bu arabirim, bir abonelik modeline dayalıdır. Herhangi bir VSPackage belge olaylarını almak ve Kabuk tarafından gerçekleşmek üzere olan olayları olun ister sinyal verebilirsiniz. Uygulanan ve tarafından işlenen [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)], sırayla Geçiren uygulama olayları `IVsTrackProjectDocumentsEvents2` VSPackage için.|Kaynak denetimi saptama|Gerekli|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments3>|Bu arabirim, toplu işlem, eşitlenmiş okuma/yazma işlemleri ve gelişmiş bir sağlar `OnQueryAddFiles` yöntemi.|Kaynak denetimi saptama|Gerekli|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>|**Çözüm Gezgini** ve projeleri çağrı bu arabirim projelere yeni dosya eklendiğinde veya dosya ve klasörleri yeniden adlandırılır veya projelerinden silindi. Kaynak denetimi VSPackage'ı, proje dosyasını kullanıma almanız veya işlemi iptal edin.|Kaynak denetimi VSPackage'ı|Önerilen|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents3>|**Çözüm Gezgini** ve projeleri bu arabirimi IVstrackProjectDocuments3 arabiriminin yöntemlere yapılan çağrılar için yanıt arayın. Kaynak denetimi VSPackage'ı eşitlenmiş toplu işlemleri izlemek okuma/yazma işlemleri ve bir daha gelişmiş iş `OnQueryAddFiles` yöntemi.|Kaynak denetimi VSPackage'ı|Önerilen|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccEnlistmentPathTranslation>|Bu arabirim, liste Yönetim Web projeleri için destek sağlar.|Kaynak denetimi VSPackage'ı|Önerilen|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManagerTooltip>|Bu arabirim, projelerde kaynak-denetimli dosyaları için araç ipuçları almak için kullanılır.|Kaynak denetimi VSPackage'ı|İsteğe Bağlı|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccOpenFromSourceControl>|Bu arabirim, ad alanı uzantısı desteği sağlar.|Kaynak denetimi VSPackage'ı|İsteğe Bağlı|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccControlNewSolution>|VSPackage'ı, bir ad alanı uzantısı'na tümleştirmek için bu arabirimi kullanır. **yeni**, **açık**, veya **Kaydet** iletişim kutuları. Sonuç olarak, projeleri otomatik olarak kaynak denetimine oluşturulurken eklenebilir, ya da kaynak denetimine kaydetme sırasında eklenen işlem etkindir.|Kaynak denetimi VSPackage'ı|İsteğe Bağlı|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccGlyphs>|VSPackage'ı ek karakterleri düğümler için kaynak denetim karakterleri olarak tanımlamak için bu arabirimi kullanan **Çözüm Gezgini**.|Kaynak denetimi VSPackage'ı|İsteğe Bağlı|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccAddWebProjectFromSourceControl>|**Ekle** Web projeleri için iletişim kutusunda, bu arabirim kullanır. Bu, bir kaynak denetimi konumunu ve kaynak denetim deposu bu konumdaki daha önce eklenen bir Web projesi açmak için gözatma için yöntemler sağlar.|Kaynak denetimi VSPackage'ı|Önerilen|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsAsynchOpenFromScc>|Bu arabirim, projelerin kaynak denetiminden zaman uyumsuz (arka plan) yüklenmesi için destek sağlar.|Kaynak denetimi VSPackage'ı|İsteğe Bağlı|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsAsynchOpenFromSccProjectEvents>|Bu arabirim tarafından başlatılan zaman uyumsuz yükleme ilerlemesini izlemek projeleri sağlar <xref:Microsoft.VisualStudio.Shell.Interop.IVsAsynchOpenFromScc>.|Proje|İsteğe Bağlı|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccToolsOptions>|Bu arabirim etkin kaynak denetimi VSPackage'ı sorgulamak IDE sağlar. Hiçbir etkin kaynak denetimi VSPackage'ı kayıtlı olduğunda bile anlama sahip bir kaynak denetim ayarları değerini IDE sorgular. Bu arabirim uygulanan ve tarafından işlenen [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].|Kaynak denetimi saptama|Gerekli|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterScciProvider>|Bu arabirim, kaynak denetimi VSPackage'ı kaydedilirken kullanılır.|Kaynak denetimi saptama|Gerekli|  
|<xref:EnvDTE.SourceControl>|Bu arabirim, Otomasyon kullanılır. Bu nedenle, herhangi bir UI görüntülemeden yürütülen işlevler sunar.|Kaynak denetimi VSPackage'ı|İsteğe Bağlı|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps>|Bu arabirim, kaynak denetim ayarları içinde çözüm (.sln) dosyasını kaydetmek için kullanılır. Kaynak Denetim durumu bayrakları ve kaynak denetimi konumunu ayarlar içerir.|Kaynak denetimi VSPackage'ı|Önerilen|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts>|Bu arabirim, çözüm seçenekleri (. suo) dosyayı kaynak denetimi ayarlarını kaydetmek için kullanılır. Bu, geçerli kullanıcının kayıt konumu gibi kullanıcıya özgü kaynak denetim ayarları içerebilir.|Kaynak denetimi VSPackage'ı|Önerilen|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3>|Bu arabirim, çözümleri kapatma ya da proje açarken yeni dosyalar kaynak denetiminden almak önce proje dosyalarının iade gibi işlemleri gerçekleştirmek için olayları izlemek için kullanılır.|Kaynak denetimi VSPackage'ı|Önerilen|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Tasarım Öğeleri](../../extensibility/internals/source-control-vspackage-design-elements.md)

