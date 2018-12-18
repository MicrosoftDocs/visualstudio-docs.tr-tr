---
title: Otomasyon VSPackages için sağlama | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, automation [Visual Studio SDK]
- automation [Visual Studio SDK], VSPackages
ms.assetid: 104c4c55-78b8-42f4-b6b0-9a334101aaea
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: fb5f3393443e41c9bd99a8890b53bedae006d7a5
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31131586"
---
# <a name="providing-automation-for-vspackages"></a>Otomasyon VSPackages için sağlama
Otomasyon için VSPackages sağlamak için başlıca iki yolu vardır: VSPackage özgü nesneler uygulayarak ve standart Otomasyon nesneleri uygulayarak. Genellikle, bunlar birlikte ortamının otomasyon modeli genişletmek için kullanılır.  
  
## <a name="vspackage-specific-objects"></a>VSPackage özgü nesneler  
 Otomasyon modelindeki belirli yerlerde, VSPackage benzersiz Otomasyon nesneleri sağlamanızı gerektirir. Örneğin, yeni projeler yalnızca, VSPackage sağlar ayrı nesneler gerektirir. Bu nesne adlarını kayıt defterinde girilen ve ortam çağrıları aracılığıyla elde `DTE` nesnesi.  
  
 Bir Otomasyon tüketici standart bir nesne nesne özelliği üzerinden sağlanan nesne kullandığında VSPackage özgü nesneler de elde edilebilir. Örneğin, standart `Window` nesnesi bir `Object` özelliği, yaygın olarak bilinen `Windows.Object` özelliği. Tüketiciler çağırdığınızda `Window.Object` , VSPackage uygulanan bir pencere üzerinde geri kendi tasarımınızı belirli Otomasyon nesnesinin geçirdiğiniz.  
  
#### <a name="projects"></a>Projeler  
 VSPackages kendi VSPackage özgü nesneleri yoluyla yeni proje türleri için otomasyon modeli genişletebilirsiniz. VSPackage benzersiz projenizi ayırt etmek için yeni Otomasyon nesneleri sağlama birincil amacı nesneleri bir <xref:Microsoft.VisualStudio.VCProjectEngine.VCProject> veya <xref:VSLangProj80.VSProject2> nesnesi. Bu ayrım göründükleri yan yana tek veya diğer proje türleri dışında projenin türünüz yinelemek için bir yol sağlamak istediğinizde kullanışlıdır bir çözümde. Daha fazla bilgi için bkz: [gösterme projesi nesneleri](../../extensibility/internals/exposing-project-objects.md).  
  
#### <a name="events"></a>Olaylar  
 Ortamının olay mimarisi kendi VSPackage özgü nesneleri eklemek başka bir yer sağlar. Örneğin, kendi benzersiz olay nesneleri oluşturarak, projeler için ortam olay modeli genişletebilirsiniz. Kendi proje türü için yeni bir öğe eklendiğinde, kendi olaylarını sağlamak isteyebilirsiniz. Daha fazla bilgi için bkz: [gösterme olayları](../../extensibility/internals/exposing-events-in-the-visual-studio-sdk.md).  
  
#### <a name="window-objects"></a>Pencere Nesneleri  
 Windows geri çağrıldığında geri ortama VSPackage özel bir Otomasyon nesnesi geçirebilirsiniz. Türetilmiş bir nesne uygulamak <xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject>, <xref:EnvDTE.IExtensibleObject> veya `IDispatch` , aktarır geri özellikleri, onu tarihli pencere nesnesi genişletme. Örneğin, bir pencere çerçevesi tarihli bir denetim için Otomasyon sağlamak için bu yaklaşımı kullanın. Bu nesne ve genişletmek diğer nesneleri semantiği tasarlamak için size aittir. Daha fazla bilgi için bkz: [nasıl yapılır: Windows için Otomasyon sağlamak](../../extensibility/internals/how-to-provide-automation-for-windows.md).  
  
#### <a name="options-pages-on-the-tools-menu"></a>Araçlar menüsünden Seçenekler sayfaları  
 Araçlar, sayfalar uygulamak ve kendi seçeneklerinizi oluşturmak üzere kayıt defterini bilgileri ekleyerek aracılığıyla seçenekleri otomasyon modeli genişletmek için sayfaları oluşturabilirsiniz. Sayfalarınızın diğer seçenekleri sayfalar gibi ortam nesne modeli aracılığıyla sonra çağrılabilir. Ortamı VSPackages üzerinden ekleme özelliği tasarım seçenekleri sayfaları gerektiriyorsa, Otomasyon desteği de eklemeniz gerekir. Daha fazla bilgi için bkz: [seçenekleri sayfaları için Otomasyon desteği](../../extensibility/internals/automation-support-for-options-pages.md).  
  
## <a name="standard-automation-objects"></a>Standart Otomasyon nesneleri  
 Projeler için Otomasyon genişletmek için de standart Otomasyon nesneleri uygular (türetilmiş `IDispatch`) diğer proje nesneleri göze ve standart yöntemleri ve özellikleri uygular. Standart nesneleri örneklerindendir çözüm hiyerarşiye gibi eklenen project nesneleri `Projects`, `Project`, `ProjectItem`, ve `ProjectItems`. Her yeni proje türü, bu nesnelerin (ve muhtemelen semantiğini bağlı olarak diğer olanları projenizin) uygulamanız gerekir.  
  
 Bir anlamda bu nesneler VSPackage özgü projesi nesneleri ters avantajı sağlar. Standart Otomasyon nesneleri aynı nesneleri destekleyen başka bir projeye gibi genelleştirilmiş bir şekilde kullanılacak projenizi izin verin. Bu nedenle, bir genel karşı yazılmış eklenti `Project` ve `ProjectItem` nesneleri karşı herhangi bir türde projeleri işlev görebilir. Daha fazla bilgi için bkz: [modelleme projesi](../../extensibility/internals/project-modeling.md).