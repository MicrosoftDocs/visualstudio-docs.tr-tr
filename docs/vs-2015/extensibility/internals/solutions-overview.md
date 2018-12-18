---
title: Çözümlere genel bakış | Microsoft Docs
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
- solutions, about solutions
ms.assetid: 3b21e3a1-170a-4485-941e-6b04b7b27886
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 7d9eb36da433575710ae7f24da85e4a1a0970b79
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51781068"
---
# <a name="solutions-overview"></a>Çözümlere Genel Bakış
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Bir çözümü, bir uygulama oluşturmak için birlikte çalışan bir veya daha fazla proje gruplandırmasıdır. Çözüme ilişkin proje ve durum bilgilerini iki farklı çözümü dosyalarında depolanır. Çözüm (.sln) dosyasını metin tabanlı kaynak kodu denetimi altında yerleştirilmiş ve kullanıcılar arasında paylaşılan. Çözüm kullanıcı seçeneği (.suo) ikili dosyadır. Sonuç olarak, .suo dosya kaynak kodu denetimi altında yerleştirilmiş ve kullanıcıya özgü bilgileri içerir.  
  
 Her iki çözüm dosya türünün herhangi bir VSPackage yazabilirsiniz. Dosya yapısı nedeniyle, kendisine yazmak için uygulanan iki farklı arabirimi vardır. <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps> Arabirimi .sln dosyasına metin bilgi yazar ve <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts> arabirimi ikili akışlar .suo dosyasına yazar.  
  
> [!NOTE]
>  Bir proje açıkça bir giriş kendisi için çözüm dosyasına yazmak zorunda değildir; ortam, proje için işler. Bu nedenle, ek içeriği özellikle çözüm dosyasına eklemek istediğiniz sürece, bu şekilde, VSPackage kaydetme gerekmez.  
  
 Çözüm Kalıcılık destekleyen her bir VSPackage üç arabirimi kullanan <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence> ortamı tarafından uygulanan ve VSPackage'ı tarafından çağrılır, arabirimi ve `IVsPersistSolutionProps` ve `IVsPersistSolutionOpts`, uygulanan hem de bir işlem olan VSPackage'ı. `IVsPersistSolutionOpts` Arabirimi yalnızca gereken gizli bilgileri tarafından VSPackage .suo dosyasına yazılması ise uygulanacak.  
  
 Bir çözümü açtığınızda, aşağıdaki süreç gerçekleşir.  
  
1. Ortam çözümü okur.  
  
2. Ortam bulursa bir `CLSID`, karşılık gelen VSPackage'ı yükler.  
  
3. VSPackage yüklendiği varsa, ortam çağrıları `QueryInterface` için <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage> VSPackage gerektiren arabirimi için bir arabirim.  
  
   1.  Bir .sln dosyasından okurken, ortam çağırır `QueryInterface` için `IVsPersistSolutionProps`.  
  
   2.  Bir .suo dosyasından okurken, ortam çağırır `QueryInterface` için `IVsPersistSolutionOpts`.  
  
   Bu dosyaların kullanımıyla ilgili belirli bilgileri bulunabilir [çözüm (. Sln) dosya](../../extensibility/internals/solution-dot-sln-file.md) ve [çözüm kullanıcı seçenekleri (. Suo) dosyası](../../extensibility/internals/solution-user-options-dot-suo-file.md).  
  
> [!NOTE]
>  İki proje yapılandırmalarını oluşan ve üçüncü bir derlemeden hariç olmak üzere yeni bir çözüm yapılandırması oluşturmak istiyorsanız, otomasyon ve özellik sayfaları kullanıcı arabirimini kullanmanız gerekir. Çözüm yapı yöneticisi yapılandırmaları ve özellikleri doğrudan değiştiremezsiniz, ancak çözüm derleme Yöneticisi kullanarak işleyebileceğiniz `SolutionBuild` DTE sınıfında otomasyon modeli. Çözümleri yapılandırma hakkında daha fazla bilgi için bkz. [çözüm yapılandırması](../../extensibility/internals/solution-configuration.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence>

