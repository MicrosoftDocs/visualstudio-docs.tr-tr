---
title: Komutlar ve menüler birlikte çalışma bütünleştirilmiş kodlarını kullanan | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- menus, using interop assemblies
- interop assemblies, using in commands and menus
- commands, handling using interop assemblies
- command handling with interop assemblies
ms.assetid: 8f4af525-39e5-4e69-92c8-d3efabe80bb2
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 2212d9eb38487bf824fd8df3c497d9f256379c10
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49907813"
---
# <a name="commands-and-menus-that-use-interop-assemblies"></a>Komutlar ve menüler birlikte çalışma bütünleştirilmiş kodları kullanın
Birlikte çalışma derlemelerini kullanarak menü ve araç çubuğu komutlarını uygulayan bir VSPackage'ı gerekir:  
  
- Bildirmek [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] tümleşik geliştirme ortamı (IDE), desteklediği komutlar ve bunlar şu anda etkinleştirilip etkinleştirilmediği.  
  
- Komutları işlemek için kuralları (sözleşme) izliyor.  
  
- Açıkça komut işleme kullanarak uygulama <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> veya <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> arabirimi.  
  
  Aşağıdaki bölümde bu görevlerin nasıl yapılacağını açıklar.  
  
## <a name="in-this-section"></a>Bu bölümde  
 [Birlikte çalışma bütünleştirilmiş kodları kullanarak komut durumunu belirleme](../../extensibility/internals/determining-command-status-by-using-interop-assemblies.md)  
 VSPackage IDE nasıl bildirir açıklar, hangi komutları destekler ve bunlar şu anda etkinleştirilip etkinleştirilmediği.  
  
 [Birlikte çalışma bütünleştirilmiş kodlarında komut sözleşmeleri](../../extensibility/internals/command-contracts-in-interop-assemblies.md)  
 Tüm VSPackages birlikte çalışma bütünleştirilmiş kodları kullanan komutlar uygulama tarafından kullanılan temel komut sözleşmesi tanımını sağlar.
  
 [Komut uygulama](../../extensibility/internals/command-implementation.md)  
 VSPackage bir komutu nasıl uyguladığını genel bir bakış sağlar.  
  
 [Birlikte çalışma bütünleştirilmiş kodu komut işleyicilerini kaydetme](../../extensibility/internals/registering-interop-assembly-command-handlers.md)  
 VSPackage'nın bir komut işleyici sunar IDE'nin bildirmek için gerekli kayıt defteri girdilerini açıklar.  
  
## <a name="related-sections"></a>İlgili bölümler  
 [Komut kullanılabilirliği](../../extensibility/internals/command-availability.md)  
 IDE tarafından hangi VSPackage komutları kullanılabilir ve bunların hangi nesne işleme belirlemek için kullanılan ölçütleri açıklanmaktadır.  
  
 [VSPackage kullanıcı arabirimi öğelerini nasıl eklenir](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)  
 Kullanan kullanıcı Arabirimi oluşturma hakkında ayrıntılar sağlar [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] komut desteği.  
  
 [Vspackage'larda komut yönlendirme](../../extensibility/internals/command-routing-in-vspackages.md)  
 Bir nesne doğru komutu istekle ilişkilendirmek için kullanılan işlemine bir genel bakış.