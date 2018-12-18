---
title: ServerDocument sınıfını kullanarak bir sunucu üzerinde belgeleri yönetme
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], managing on server
- Office documents [Office development in Visual Studio, managing on server
- ServerDocument class, managing documents on server
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: e983f4cf1b90150113fcfa33702d85bb41a30924
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49939143"
---
# <a name="manage-documents-on-a-server-by-using-the-serverdocument-class"></a>ServerDocument sınıfını kullanarak bir sunucu üzerinde belgeleri yönetme
  Kullanabileceğiniz `ServerDocument` sınıfını [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] Microsoft Office Word ve Microsoft Office Excel yüklü değilse, belge düzeyinde özelleştirmeler, çeşitli yönlerini yönetmek için. Aşağıdaki görevleri gerçekleştirebilirsiniz:  
  
- Erişim ve bir belge veya çalışma kitabının veri önbelleğindeki verileri değiştirebilirsiniz. Daha fazla bilgi için [belgede önbelleğe alınan verilerle çalışmak](#CachedData).  
  
- Bir belge ile ilişkilendirilen özelleştirme bütünleştirilmiş kodu yönetin. Daha fazla bilgi için [belge özelleştirme yönetme](#CustomizationInfo).  
  
  [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
## <a name="understand-the-serverdocument-class"></a>ServerDocument Sınıfını Anlama  
 `ServerDocument` Sınıfı Office'in yüklü olmayan bilgisayarlarda kullanılmak üzere tasarlanmıştır. Bu nedenle, genellikle bu sınıf, Office ile konsol projeleri Windows Forms projeleri yerine veya gibi Office projeleri tümleştirmeyen uygulamalarda kullanılır. Kullanım <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> sınıfını *Microsoft.VisualStudio.Tools.Applications.ServerDocument.dll* derleme.  
  
 `ServerDocument` Sınıfı kullanılarak oluşturulmuş olan belge düzeyi özelleştirmeleri üzerinde çalışılacak kullanılabilir [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)].  
  
 Hakkında daha fazla bilgi için Visual Studio 2010 Araçları Office çalışma zamanı ve Office uzantıları için .NET Framework için bkz: [Office çalışma zamanına genel bakış için Visual Studio Araçları](../vsto/visual-studio-tools-for-office-runtime-overview.md).  
  
> [!NOTE]  
>  Kullanan eski bir uygulama varsa `ServerDocument` sınıfını `Visual Studio Tools for Office` sistem (sürüm 3.0 çalışma zamanı), `Visual Studio Tools for Office` sistem (sürüm 3.0 çalışma zamanı), uygulamayı çalıştıran bilgisayarlarda yüklü olması gerekir. `Visual Studio 2010 Tools for Office runtime` Bu uygulamaları çalıştıramazsınız.  
  
##  <a name="CachedData"></a> Belge önbelleğe alınan verilerle çalışın  
 `ServerDocument` Özelleştirilmiş belgeleri veri önbelleğindeki çalışmak için kullanabileceğiniz üyeleri sınıf sağlar. Önbelleğe alınan veriler hakkında daha fazla bilgi için bkz. [veriyi önbelleğe alma](../vsto/caching-data.md) ve [sunucudaki belgelerde verilere erişme](../vsto/accessing-data-in-documents-on-the-server.md).  
  
 Aşağıdaki tabloda, önbelleğe alınan verilerle çalışmak için kullanabileceğiniz üyeleri listeler.  
  
|Görev|Üye kullanmak için|  
|----------|-------------------|  
|Bir belge bir veri önbelleği olup olmadığını belirlemek için.|<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.IsCacheEnabled%2A> Yöntemi.|  
|Bir belgede önbelleğe alınan verilere erişmek için.<br /><br /> Daha fazla bilgi için [sunucudaki belgelerde verilere erişme](../vsto/accessing-data-in-documents-on-the-server.md).|<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.CachedData%2A> Özelliği.|  
  
##  <a name="CustomizationInfo"></a> Belge özelleştirme yönetme  
 Üyelerinin kullanabileceği `ServerDocument` bir belgeyle ilişkilidir özelleştirme bütünleştirilmiş kodu yönetmek için sınıf. Örneğin, böylece belge artık bir özelleştirme parçasıdır belgeden özelleştirme programlı olarak kaldırabilirsiniz.  
  
 Aşağıdaki tabloda özelleştirme bütünleştirilmiş kodu yönetmek için kullanabileceğiniz üyeleri listeler.  
  
|Görev|Üye kullanmak için|  
|----------|-------------------|  
|Bir belge olup olmadığını belirlemek için belge düzeyi özelleştirmesi parçasıdır.|<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.GetCustomizationVersion%2A> Yöntemi.|  
|Program aracılığıyla bir belgeye çalışma zamanında bir özelleştirme eklemek için.<br /><br /> Daha fazla bilgi için [nasıl yapılır: ekleme yönetilen kod uzantıları belgeleri](../vsto/how-to-attach-managed-code-extensions-to-documents.md)|Aşağıdakilerden birini <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.AddCustomization%2A> yöntemleri.|  
|Program aracılığıyla bir özelleştirme çalışma zamanında bir belgeden kaldırmak için.<br /><br /> Daha fazla bilgi için [nasıl yapılır: belgelerden kaldırma yönetilen kod uzantıları](../vsto/how-to-remove-managed-code-extensions-from-documents.md).|<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.RemoveCustomization%2A> Yöntemi.|  
|Belge ile ilişkilendirilen dağıtım bildirimi URL'sini almak için.|<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.DeploymentManifestUrl%2A> Özelliği.|  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Nasıl yapılır: ekleme yönetilen kod uzantıları belgeleri](../vsto/how-to-attach-managed-code-extensions-to-documents.md)   
 [Nasıl yapılır: belgelerden kaldırma yönetilen kod uzantıları](../vsto/how-to-remove-managed-code-extensions-from-documents.md)   
 [Office çalışma zamanına genel bakış için Visual Studio Araçları](../vsto/visual-studio-tools-for-office-runtime-overview.md)   
 [Verileri önbelleğe](../vsto/caching-data.md)  
  