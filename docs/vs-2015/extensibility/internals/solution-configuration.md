---
title: Çözüm Yapılandırması | Microsoft Docs
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
- solution configurations
ms.assetid: f22cfc75-3e31-4e0d-88a9-3ca99539203b
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 53d8e3d33a81e20d553e6a5c97eb6e6f33339079
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51801615"
---
# <a name="solution-configuration"></a>Çözüm Yapılandırması
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Çözüm yapılandırmalarını çözüm düzeyi özellikleri depolar. Bunlar davranışını doğrudan **Başlat** (F5) anahtarı ve **derleme** komutları. Varsayılan olarak, bu komutlar, derleme ve hata ayıklama Yapılandırması'nı başlatın. Bir çözüm yapılandırması bağlamında her iki komutu yürütün. Bu, başlangıç ve derleme Ayarları'nda yapılandırılmış herhangi bir etkin çözüm için kullanıcı F5 bekleyebileceğiniz anlamına gelir. Ortam oluşturmak ve çalıştırmak için söz konusu olduğunda projeleri yerine çözümleri için en iyi duruma getirmek için tasarlanmıştır.  
  
 Standart Visual Studio araç Başlat düğmesi ve aşağı açılan Başlat düğmesinin sağında bir çözüm yapılandırması içerir. Bu liste, F5 tuşuna basıldığında başlatılması için yapılandırmayı seçin, kendi çözüm yapılandırmaları oluşturmak veya mevcut bir yapılandırmayı düzenlemek kullanıcıların sağlar.  
  
> [!NOTE]
>  Oluşturma veya düzenleme çözüm yapılandırmaları hiçbir genişletilebilirlik arabirimleri vardır. Kullanmalısınız `DTE.SolutionBuilder`. Ancak, çözüm derlemesi yönetmek için genişletilebilirlik API'leri vardır. Daha fazla bilgi için bkz. <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionBuildManager2>.  
  
 Proje türü tarafından desteklenen çözüm yapılandırmaları nasıl uygulayacağınıza dair aşağıda verilmiştir:  
  
- Proje  
  
   Geçerli çözümde bulunan projelerinin adlarını görüntüler.  
  
- Yapılandırma  
  
   Proje türü tarafından desteklenen yapılandırmaların listesi sağlamak ve özellik sayfaları'nda görüntülenen uygulamak için <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2>.  
  
   Yapılandırma sütunu, bu çözüm yapılandırmasındaki, derlemek için proje yapılandırması adını görüntüler ve ok düğmesine tıkladığınızda, tüm proje yapılandırmalarını listeler. Ortam çağrıları <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgNames%2A> bu listeyi doldurmak için yöntemi. Varsa <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgProviderProperty%2A> proje yapılandırmasını düzenleme, yeni destekler veya düzenleme seçimleri ayrıca yapılandırma başlığı altında görüntülenen yöntemi gösterir. Bu seçimleri her yöntemlerini çağıran iletişim kutularını başlatma `IVsCfgProvider2` proje yapılandırmalarını Düzenle için arabirim.  
  
   Bir proje yapılandırmaları desteklemez, yapılandırma sütunu hiçbiri görüntüler ve devre dışı bırakıldı.  
  
- Platform  
  
   Seçilen proje yapılandırması için derlemeler ve ok düğmesine tıkladığınızda, tüm proje için kullanılabilir platformları listeler platform görüntüler. Ortam çağrıları <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetPlatformNames%2A> bu listeyi doldurmak için yöntemi. Varsa <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgProviderProperty%2A> proje platformu düzenleme, yeni destekler veya düzenleme seçimleri ayrıca Platform başlığı altında görüntülenen yöntemi gösterir. Bu seçimleri her çağrı iletişim kutularını başlatma `IVsCfgProvider2` projenin kullanılabilir platformlar düzenlemek için yöntemleri.  
  
   Proje platformlarını desteklemiyor, bu proje için platform sütun yok görüntüler ve devre dışı bırakıldı.  
  
- Derleme  
  
   Projenin geçerli çözüm yapılandırması tarafından oluşturulmuş olup olmadığını belirtir. Çözüm düzeyinde derleme komutları içerdikleri proje bağımlılıkları rağmen çağrıldığında seçili olmayan projeler oluşturulmadı. Oluşturulacak seçili olmayan projeler, hata ayıklama, çalışan, paketleme ve çözümün dağıtımı yine de eklenir.  
  
- Dağıt  
  
   Proje başlangıç veya dağıtma komutları seçili çözüm yapı yapılandırması ile birlikte kullanıldığında dağıtılacak olup olmadığını belirtir. Bu alan için onay kutusunu proje uygulayarak dağıtma destekliyorsa kullanılabilir <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg> üzerinde arabirim kendi <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2> nesne.  
  
  Yeni bir çözüm yapılandırması eklendikten sonra kullanıcı oluşturun ve/veya söz konusu yapılandırmayı başlatmak için standart araç çözüm yapılandırması aşağı açılan liste kutusundan seçebilirsiniz.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Yapılandırma seçeneklerini yönetme](../../extensibility/internals/managing-configuration-options.md)   
 [Derleme için proje yapılandırması](../../extensibility/internals/project-configuration-for-building.md)   
 [Proje Yapılandırması Nesnesi](../../extensibility/internals/project-configuration-object.md)

