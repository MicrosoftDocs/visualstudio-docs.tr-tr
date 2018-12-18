---
title: Proje yapılandırma nesnesi | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- project configurations, object
- objects, project configuration
ms.assetid: 877756c9-4261-43d9-9f32-51bf06b4219f
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 7385a5f7768a57fd1a3d9688df152fd60a1ea130
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31136035"
---
# <a name="project-configuration-object"></a>Proje yapılandırma nesnesi
Proje yapılandırma nesnesi kullanıcı Arabirimi için yapılandırma bilgilerini görüntüleme yönetir.  
  
 ![Visual Studio Proje yapılandırması](../../extensibility/internals/media/vsprojectcfg.gif "vsProjectCfg")  
Proje yapılandırması özellik sayfaları  
  
 Proje yapılandırma sağlayıcısı proje yapılandırmaları yönetir. Ortam ve ve bir projenin yapılandırmaları hakkında bilgi almak için proje yapılandırma sağlayıcısı nesneye iliştirilmiş arabirimleri çağrı erişim kazanmak için diğer paketler.  
  
> [!NOTE]
>  Oluşturamaz veya çözüm yapılandırma dosyalarını program aracılığıyla düzenleyin. Kullanmalısınız `DTE.SolutionBuilder`. Bkz: [çözüm yapılandırması](../../extensibility/internals/solution-configuration.md) daha fazla bilgi için.  
  
 UI yapılandırmasında kullanılması için bir görünen ad yayımlamak için projenize uygulamalıdır <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg.get_DisplayName%2A>. Ortam çağrıları <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgs%2A>, listesini döndürür `IVsCfg` işaretçileri ortamı kullanıcı Arabiriminde listelenmesi yapılandırma ve Platform bilgilerini için görünen adları almak için kullanabilirsiniz. Etkin yapılandırma ve platform etkin çözüm yapılandırmasında depolanmış projenin yapılandırmaya göre belirlenir. <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionBuildManager.FindActiveProjectCfg%2A> Yöntemi, etkin proje yapılandırmayı almak için kullanılabilir.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfgProvider> Nesne isteğe bağlı olarak uygulanabilir üzerinde <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2> nesnesi ile <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProviderEventsHelper> almaya izin vermek için nesne bir `IVsProjectCfg2` nesne tabanlı kurallı proje yapılandırma adı.  
  
 Ortamı ve diğer projeler proje yapılandırmaları erişim sağlamak için başka bir uygulama sağlayın projelerde yoludur `IVsCfgProvider2::GetCfgs` yöntemi bir veya daha fazla yapılandırma nesnesi döndürür. Projeleri de uygulayabilir <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2>, devralan `IVsProjectCfg` ve böylece `IVsCfg`, özel yapılandırma bilgilerini sağlamak için. <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2> platformlar ve işlevsellik ekleme, silme ve yeniden adlandırma proje yapılandırmaları destekler.  
  
> [!NOTE]
>  Visual Studio için iki yapılandırma türleri sınırlı artık, yapılandırmaları işleyen kodu değil yazılması gerektiğini varsayımlar ile yapılandırmaları sayısı hakkında ya da varsayımıyla yazılmalıdır olduğundan, yalnızca bir tane var olan bir projeyi mutlaka hata ayıklama veya perakende yapılandırmadır. Bu kullanımını kılar <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg.get_IsReleaseOnly%2A> ve <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg.get_IsDebugOnly%2A> artık kullanılmıyor.  
  
 Çağırma `QueryInterface` döndürülen nesne üzerinde`IVsGetCfgProvider::GetCfgProvider` alır `IVsCfgProvider2`. Varsa `IVsGetCfgProvider` çağırarak bulunamadı `QueryInterface` üzerinde `IVsProject3` proje nesnesi, çağırarak yapılandırma sağlayıcısı nesnesi erişebilir `QueryInterface` için döndürülen nesne için hiyerarşi kök tarayıcı nesnesindeki `IVsHierarchy::GetProperty(VSITEM_ROOT, VSHPROPID_BrowseObject)`, aracılığıyla veya için yapılandırma sağlayıcısı için bir işaretçi `IVsHierarchy::GetProperty(VSITEM_ROOT, VSHPROPID_ConfigurationProvider)`.  
  
 `IVsProjectCfg2` öncelikle erişimi yapı, hata ayıklama ve dağıtım yönetim nesneleri sağlar ve grup çıkışları serbestçe projeleri sağlar. Yöntemlerinin `IVsProjectCfg` ve `IVsProjectCfg2` uygulamak için kullanılan <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg> derleme işlemini yönetmek için ve <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputGroup> yapılandırmasının çıktı grupları işaretçileri.  
  
 Proje grupları yapılandırma yapılandırması bir grup içinde bulunan çıkışları sayısı değişebilir olsa bile, onu destekleyen her yapılandırması için aynı sayıda döndürmesi gerekir. Gruplar da aynı tanımlayıcı bilgileri (kurallı ad, görünen ad ve grup bilgileri) yapılandırma yapılandırması bir projede olmalıdır. Daha fazla bilgi için bkz: [çıktı için proje yapılandırması](../../extensibility/internals/project-configuration-for-output.md).  
  
 Hata ayıklamayı etkinleştirmek için yapılandırmalarınızı uygulamalıdır <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg>. `IVsDebuggableProjectCfg` bir yapılandırma başlatmak hata ayıklayıcı izin vermek için projeleri tarafından uygulanan isteğe bağlı bir arabirim olduğundan ve yapılandırma nesnesi üzerinde uygulanan `IVsCfg` ve `IVsProjectCfg`. Ortam kullanıcı F5 tuşuna basarak hata ayıklayıcısını başlatmak üzere seçtiğinde çağırır.  
  
 `ISpecifyPropertyPages` ve `IDispatch` özellik sayfaları ile birlikte almak ve kullanıcıya yapılandırma bağımlı bilgileri görüntülemek için kullanılır. Daha fazla bilgi için bkz: [özellik sayfaları](../../extensibility/internals/property-pages.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Yapılandırma seçenekleri yönetme](../../extensibility/internals/managing-configuration-options.md)   
 [Proje yapılandırması oluşturmak için](../../extensibility/internals/project-configuration-for-building.md)   
 [Çıktı için proje yapılandırması](../../extensibility/internals/project-configuration-for-output.md)   
 [Özellik sayfaları](../../extensibility/internals/property-pages.md)   
 [Çözüm Yapılandırması](../../extensibility/internals/solution-configuration.md)