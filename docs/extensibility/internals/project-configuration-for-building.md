---
title: Proje derleme için yapılandırma | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], configuration for building
- project configurations, building
ms.assetid: 2c83615d-fa4d-4b9f-b315-7a69b3000da0
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 4d78ac1cabc356db162639d3eb19d0bff71e295e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31133318"
---
# <a name="project-configuration-for-building"></a>Proje yapılandırması oluşturmak için
Belirli bir çözüm için çözüm yapılandırmaları listesi çözüm yapılandırmaları iletişim kutusu tarafından yönetilir.  
  
 Bir kullanıcı her kendi benzersiz bir ad ile ek çözüm yapılandırmaları oluşturabilirsiniz. Kullanıcı yeni bir çözüm yapılandırması oluşturduğunda, karşılık gelen ad varsa IDE projeleri ya da hata ayıklama ilgili yapılandırma adı varsayılan olarak ayarlanır. Kullanıcı Seçimi gerekirse belirli gereksinimleri karşılayacak şekilde değiştirebilirsiniz. Proje yeni çözüm yapılandırması adıyla eşleşen bir yapılandırma desteklediğinde Bu davranış için tek özel durumdur. Örneğin, bir çözüm Project1 ve Project2 içeren varsayın. Proje yapılandırmaları hata ayıklama, perakende ve MyConfig1 Project1 sahiptir. Proje yapılandırmaları hata ayıklama, perakende ve MyConfig2 Project2 sahiptir.  
  
 Kullanıcı MyConfig2 adlı yeni bir çözüm yapılandırması oluşturursa, Project1 çözüm yapılandırması hata ayıklama yapılandırmasını varsayılan olarak bağlar. Project2 de MyConfig2 yapılandırmasıyla çözüm yapılandırması için varsayılan olarak bağlar.  
  
> [!NOTE]
>  Bağlama büyük/küçük harf duyarlıdır.  
  
 Kullanıcı seçtiğinde **çoklu seçim** öğesi yapılandırma aşağı açılan listesinde ortamı kullanılabilir yapılandırmaların listesi sunan bir iletişim kutusu görüntüler.  
  
 ![Birden çok yapılandırmayı](../../extensibility/internals/media/vsmultiplecfgs.gif "vsMultipleCfgs")  
Birden fazla yapılandırma  
  
 Bu iletişim kutusunda, kullanıcı bir veya birden çok yapılandırmaları seçebilirsiniz. Özellik sayfaları iletişim kutusunda görüntülenen özellik değerlerini seçildikten sonra seçili yapılandırmaları değerlerinin kesişimini yansıtır.  
  
 Bkz: [çözüm yapılandırması](../../extensibility/internals/solution-configuration.md) ekleme ve yapılandırmalarını çözümler ve projeler için yeniden adlandırma ile ilgili bilgi için.  
  
 Proje bağımlılıkları ve derleme sırası olan çözüm yapılandırması bağımsız: başka bir deyişle, yalnızca bir bağımlılık ağacı tüm Çözümdeki projeler için ayarlayabilirsiniz. Çözüme ya da projeye sağ tıklayıp ya da seçerek **proje bağımlılıkları** veya **proje derleme siparişi** seçeneği açılır **proje bağımlılıkları** iletişim kutusu. Bu da açılabilir **proje** menüsü.  
  
 ![Proje bağımlılıkları](../../extensibility/internals/media/vsprojdependencies.gif "vsProjDependencies")  
Proje bağımlılıkları  
  
 Proje bağımlılıkları, projeler derleme sırasını belirler. Derleme sırası sekmesini iletişim kutusunda, bir çözüm içindeki projelerin yapı ve yapı sırasını değiştirmek için bağımlılıkları sekmesini kullanın tam sırayı görüntülemek için kullanın.  
  
> [!NOTE]
>  Seçili onay kutularını ancak soluk görünür Projeler listesinde tarafından belirtilen belirli bağımlılıkları nedeniyle ortamı tarafından eklenmiştir <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildDependency> veya <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployDependency> arabirimleri ve değiştirilemez. Örneğin, bir proje başvuru ekleme bir [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] başka bir projeye projesine başvuru silerek yalnızca kaldırılabilir bir derleme bağımlılığına otomatik olarak ekler. Bunun yapılması bir bağımlılık döngüsünün oluşturabileceğinden, onay kutularını temizleyin ve soluk görünür projeleri seçilemez (örneğin, Project1 Project2 bağımlı olacaktır ve Project2 Project1 bağımlı olur), hangi derleme kabin.  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Yapı işlemleri tipik derleme ve tek bir derleme komutla çağrılan bağlantı işlemlerini içerir. Diğer iki yapı işlemler de desteklenebilir: önceki yapıdan ve çıktı öğeyi yapılandırmasında değişip değişmediğini belirlemek için güncel bir onay tüm çıktı öğeleri silmek için temizleme işlemi.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2> nesneler döndürmeye karşılık gelen <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg> (döndürülen <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2.get_CfgType%2A>) derleme süreçlerinin yönetmek için. Yapılandırmalar, gerçekleştirildiği sırada bir yapı işlemin durumunu bildirmek için çağrı yapmak <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildStatusCallback>, arayüz ortamı tarafından uygulanan ve herhangi bir nesnenin yapı durum olayları ilgileniyor.  
  
 Bir kez oluşturulduktan sonra yapılandırma ayarlarını hata ayıklayıcı denetiminde çalıştırılabilir olup olmadığını belirlemek için kullanılabilir. Yapılandırmalar uygulamanız <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg> hata ayıklamayı desteklemek için.  
  
 Proje bağımlılıkları kullanıldıktan sonra otomasyon modeli aracılığıyla bağımlılıklar program aracılığıyla yönetebilirsiniz. Çağırmanız <xref:EnvDTE.SolutionBuild.BuildDependencies%2A> otomasyon modeli. Çözüm derleme Yöneticisi yapılandırmaları ve bunların özelliklerini doğrudan işleme izin yok kullanılabilir VSIP API düzeyi arabirimi vardır.  
  
 Ayrıca, proje bağımlılıklarını penceresinde bir kılavuz sağlar. Daha fazla bilgi için bkz: [özellikler görünen kılavuz](../../extensibility/internals/properties-display-grid.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Yapılandırma seçenekleri yönetme](../../extensibility/internals/managing-configuration-options.md)   
 [Dağıtım yönetmek için proje yapılandırması](../../extensibility/internals/project-configuration-for-managing-deployment.md)   
 [Çıkış için Proje Yapılandırması](../../extensibility/internals/project-configuration-for-output.md)