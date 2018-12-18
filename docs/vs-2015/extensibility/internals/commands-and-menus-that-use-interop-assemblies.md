---
title: Komutlar ve menüler birlikte çalışma bütünleştirilmiş kodlarını kullanan | Microsoft Docs
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
- menus, using interop assemblies
- interop assemblies, using in commands and menus
- commands, handling using interop assemblies
- command handling with interop assemblies
ms.assetid: 8f4af525-39e5-4e69-92c8-d3efabe80bb2
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 1a1c7d0e3acde1ca412d7bfaba0cfa3606ee54a4
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51753679"
---
# <a name="commands-and-menus-that-use-interop-assemblies"></a>Birlikte Çalışma Bütünleştirilmiş Kodları Kullanan Komutlar ve Menüler
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Birlikte çalışma derlemelerini kullanarak menü ve araç çubuğu komutlarını uygulayan bir VSPackage'ı gerekir:  
  
- Bildirmek [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] tümleşik geliştirme ortamı (IDE), desteklediği komutlar ve bunlar şu anda etkinleştirilip etkinleştirilmediği.  
  
- Komutları işlemek için kuralları (sözleşme) izliyor.  
  
- Açıkça komut işleme kullanarak uygulama <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> veya <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> arabirimi.  
  
  Bu görevlerin nasıl yapılacağını açıklar.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Birlikte Çalışma Bütünleştirilmiş Kodları Kullanarak Komut Durumunu Belirleme](../../extensibility/internals/determining-command-status-by-using-interop-assemblies.md)  
 VSPackage IDE nasıl bildirir açıklar, hangi komutları destekler ve bunlar şu anda etkinleştirilip etkinleştirilmediği.  
  
 [Birlikte Çalışma Bütünleştirilmiş Kodlarında Komut Sözleşmeleri](../../extensibility/internals/command-contracts-in-interop-assemblies.md)  
 Tüm VSPackages birlikte çalışma bütünleştirilmiş kodları kullanan komutlar uygulama tarafından kullanılan temel komut sözleşme tanımı sağlar  
  
 [Uygulama](../../extensibility/internals/command-implementation.md)  
 VSPackage bir komutu nasıl uyguladığını genel bir bakış sağlar.  
  
 [Birlikte Çalışma Bütünleştirilmiş Kodu Komut İşleyicilerini Kaydetme](../../extensibility/internals/registering-interop-assembly-command-handlers.md)  
 VSPackage'nın bir komut işleyici sunar IDE'nin bildirmek için gerekli kayıt defteri girdilerini açıklar.  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [Kullanılabilirlik](../../extensibility/internals/command-availability.md)  
 IDE tarafından hangi VSPackage komutları kullanılabilir ve bunların hangi nesne işleme belirlemek için kullanılan ölçütleri açıklanmaktadır.  
  
 [VSPackage’ların Kullanıcı Arabirimi Öğeleri Eklemesi](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)  
 Kullanan kullanıcı Arabirimi oluşturma hakkında ayrıntılar sağlar [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] komut desteği.  
  
 [VSPackage’larda Komut Yönlendirme](../../extensibility/internals/command-routing-in-vspackages.md)  
 Bir nesne doğru komutu istekle ilişkilendirmek için kullanılan işlemine bir genel bakış.

