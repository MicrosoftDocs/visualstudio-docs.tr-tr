---
title: Projeleri yükseltme | Microsoft Docs
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
- upgrading VSPackages
- upgrading applications, strategies
- VSPackages, upgrade support
ms.assetid: e01cb44a-8105-4cf4-8223-dfae65f8597a
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: a3f045d947f968655923df16de8c02aafc12a34b
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51783772"
---
# <a name="upgrading-projects"></a>Projeleri Yükseltme
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Proje modeli için bir sürümünden değişiklikleri [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] sonraki sürüme üzerinde çalıştırabilmeniz için projeler ve çözümler yükseltilmesi özellikle gerektirebilir. [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)] Yükseltme desteği kendi projelerinde uygulamak için kullanılan arabirimleri sağlar.  
  
## <a name="upgrade-strategies"></a>Yükseltme stratejileri  
 Yükseltme desteklemek için proje sistemi uygulamanızı tanımlamak ve yükseltme bir strateji yürütmelidir. Stratejinizi belirlemede yan yana (SxS) yedekleme, kopya yedekleme veya her ikisini de desteklemek seçebilirsiniz.  
  
-   SxS yedekleme, bir proje bir yerde, uygun dosya adı sonek, örneğin, ekleme "eski" Yükseltme gereken dosyaları kopyalar anlamına gelir.  
  
-   Kopya yedekleme, bir projenin tüm proje öğeleri kullanıcı tarafından sağlanan bir yedek konumuna kopyalar anlamına gelir. Ardından, özgün proje konumda sürücülerinizdeki ilgili dosyaların yükseltilir.  
  
## <a name="how-upgrade-works"></a>Yükseltme nasıl çalışır?  
 Bir önceki sürümünde oluşturulmuş bir çözümü, [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] , çözüm dosya yükseltilmesi gerekip gerekmediğini belirlemek için IDE denetimleri gibi daha yeni bir sürümü açılır. Yükseltme gerekli ise **Yükseltme Sihirbazı** kullanıcı yükseltme sürecinde size yol için otomatik olarak başlatılır.  
  
 Bir çözüm yükseltme gerektiğinde, her proje fabrikası yükseltme stratejisinin için sorgular. Strateji, proje fabrikası kopya yedekleme veya SxS yedekleme destekleyip desteklemediğini belirler. Bilgiler gönderilir **Yükseltme Sihirbazı**, yedekleme için gerekli bilgileri toplar ve kullanıcıya uygun bir seçenek sunar.  
  
### <a name="multi-project-solutions"></a>Birden çok proje çözümü  
 Varsa bir çözüm birden fazla proje içeren ve yükseltme stratejiler farklı gibi yalnızca SxS yedekleme destekleyen bir C++ projesi ve yalnızca kopya yedeği destekleyen bir Web projesi, proje fabrikalarını yükseltme stratejisini anlaşmaları gerekir.  
  
 Her proje fabrikası için çözüm sorgular <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory>. Ardından <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject_CheckOnly%2A> genel proje dosyalarını yükseltme gerekip gerekmediğini ve desteklenen yükseltme stratejiler belirlemek için. **Yükseltme Sihirbazı** sonra çağrılır.  
  
 Kullanıcı, sihirbaz tamamlandıktan sonra <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> gerçek yükseltmeyi gerçekleştirmek için her proje fabrikası çağrılır. Yedekleme kolaylaştırmak için IVsProjectUpgradeViaFactory yöntemleri sağlayan <xref:Microsoft.VisualStudio.Shell.Interop.SVsUpgradeLogger> yükseltme işleminin ayrıntılarını oturum hizmeti. Bu hizmet önbelleğe alınamaz.  
  
 Tüm ilgili genel dosyaları güncelleştirdikten sonra her proje fabrikası, bir proje oluşturmak seçebilirsiniz. Proje uygulama desteklemelidir <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>. <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> Yöntemi tüm ilgili proje öğeleri yükseltmek sonra çağrılır.  
  
> [!NOTE]
>  <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> Yöntemi SVsUpgradeLogger hizmet sağlamaz. Bu hizmet, çağrılarak alınabilir <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A>.  
  
## <a name="best-practices"></a>En İyi Yöntemler  
 Kullanım <xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave> hizmetinin, bir dosya düzenlemeden önce düzenleyebilir ve kaydetmeden önce kaydedebilirsiniz olmadığını denetleyin. Bu yedekleme yardımcı olur ve yükseltme uygulamaları işlemek için kaynak denetimi altında proje dosyaları, dosyaları yetersiz izinler ve benzeri.  
  
 Kullanım <xref:Microsoft.VisualStudio.Shell.Interop.SVsUpgradeLogger> hizmet yedekleme tüm aşamalarında ve başarı veya başarısızlık yükseltme işleminin bilgi sağlamak için yükseltin.  
  
 Yedekleme ve projelerini yükseltme hakkında daha fazla bilgi için içinde vsshell2.idl IVsProjectUpgrade için yorumlara bakın.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Projeleri](../../extensibility/internals/projects.md)   
 [Özel projelerini yükseltme](../../misc/upgrading-custom-projects.md)   
 [Proje öğeleri yükseltme](../../misc/upgrading-project-items.md)

