---
title: Sözleşmeler birlikte çalışma bütünleştirilmiş kodlarında komut | Microsoft Docs
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
- command handling with interop assemblies, command contracts
- interop assemblies, command contracts
ms.assetid: 57245708-f539-42dc-8963-2754a48f0189
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 8089314293c92a24396a90f4be4dd4120c03bbcd
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51725090"
---
# <a name="command-contracts-in-interop-assemblies"></a>Birlikte Çalışma Bütünleştirilmiş Kodlarında Komut Sözleşmeleri
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Komutları işlemeye yönelik temel sözleşmesi <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> arabirimidir ortam çağırır <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> komutu desteklenip desteklenmediğini ve bu desteklenip desteklenmediğini belirlemek için metin ve durumu belirlemek için yöntemi. Sonra ortamı çağrıları <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> komutu yürütmek için yöntemi.  
  
 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> Yöntemi tüm komutlar için aynı şekilde işlenir. Daha fazla iletişim (örneğin, açılan listeler ile), gerekirse yönetilir çağırarak <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> uygun parametrelerle yöntemi. Bu parametre yorumu belirtilen komut bağlıdır.  
  
 Komut hedefi çıkış parametresi değerleri döndürürse, çağıran her zaman ayrılmış tüm kaynakları serbest bırakma için sorumludur. Bu parametre bir değişken olduğundan, değişken temizleme kaynakları serbest bırakır.  
  
 Burada komutları gerekir çalışan bir hiyerarşi penceresinde durumlarda <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> arabirimi kullanılmalıdır. <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> Benzer yöntemler ile benzer bir sözleşme arabirimi vardır: <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A> ve <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.ExecCommand%2A>.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [VSPackage kullanıcı arabirimi öğelerini nasıl eklenir](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [Vspackage'larda komut yönlendirme](../../extensibility/internals/command-routing-in-vspackages.md)   
 [Uygulama](../../extensibility/internals/command-implementation.md)

