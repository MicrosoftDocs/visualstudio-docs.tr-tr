---
title: IDE tanımlı komutlar, menüler ve gruplar | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- commands, environment-defined
- .vsct files, environment-defined constants
- command groups, environment-defined
ms.assetid: 86b3af13-7163-48c6-986b-7beeedbc26cc
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 34c41608a90b15538e190be093ed2791a90824f9
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49857282"
---
# <a name="ide-defined-commands-menus-and-groups"></a>IDE Tanımlı Komutlar, Menüler ve Gruplar
Birçok menüler, komutları ve komut grupları zaten tarafından tanımlanan [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE. Bu komutlar da genişlettiğinizde, kullanımınıza sunulan. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
## <a name="finding-environment-defined-commands"></a>Ortam tanımlı komutları bulma  
 Ortam komutları dört .vsct dosyaları kümesi içinde tanımlanır:  
  
- SharedCmdDef.vsct  
  
- SharedCmdPlace.vsct  
  
- ShellCmdDef.vsct  
  
- ShellCmdPlace.vsct  
  
  Bu dosyalar bulunur  *\<Visual Studio SDK'sını yükleme yolu >* \VisualStudioIntegration\Common\Inc\\. Bu dosyalar, menüler ve kendi menüler, gruplar ve komutlar için kapsayıcı olarak, VSPackage'ı komut tablosu (.vsct) yapılandırma dosyasında kullanabileceğiniz grupların GUID'leri ve tanımları sağlar.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Visual Studio Menülerinin GUID’leri ve Kimlikleri](../../extensibility/internals/guids-and-ids-of-visual-studio-menus.md)  
 Visual Studio menü çubuğundaki menüleri ve içerdikleri tüm grupların GUID ve ID değerleri sağlar.  
  
 [Visual Studio Araç Çubuklarının GUID’leri ve Kimlikleri](../../extensibility/internals/guids-and-ids-of-visual-studio-toolbars.md)  
 Visual Studio IDE'de araç çubukları ve içerdikleri tüm grupların GUID ve ID değerleri sağlar.  
  
 [Visual Studio Komutlarının GUID’leri ve Kimlikleri](../../extensibility/internals/guids-and-ids-of-visual-studio-commands.md)  
 Tarafından Visual Studio IDE tanımlı komutlar GUID ve ID değerini verir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual Studio komut tablosu (. Vsct) dosyaları](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)   
 [Proje sistemlerini genişletmeye yönelik IDE tanımlı komutlar](../../extensibility/internals/ide-defined-commands-for-extending-project-systems.md)   
 [VSPackage’ların Kullanıcı Arabirimi Öğeleri Eklemesi](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)