---
title: IDE-Defined komutlar, menüler ve gruplar | Microsoft Docs
description: Visual Studio tümleşik geliştirme ortamında (IDE) tanımlanan menüler, komutlar ve komut grupları hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- commands, environment-defined
- .vsct files, environment-defined constants
- command groups, environment-defined
ms.assetid: 86b3af13-7163-48c6-986b-7beeedbc26cc
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 5b88bbab9c92cdd8627521eaa58284fd33964b7e
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105085955"
---
# <a name="ide-defined-commands-menus-and-groups"></a>IDE Tanımlı Komutlar, Menüler ve Gruplar
Birçok menü, komut ve komut grubu, IDE tarafından kullanılmak üzere zaten tanımlanmış [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . Bu komutlar, uzatdığınızda kullanım için de kullanılabilir [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .

## <a name="finding-environment-defined-commands"></a>Environment-Defined komutlarını bulma
 Ortam komutları bir dizi dört. vsct dosyasında tanımlanır:

- SharedCmdDef. vsct

- SharedCmdPlace. vsct

- ShellCmdDef. vsct

- ShellCmdPlace. vsct

  Bu dosyalar \VisualStudioIntegration\Common\Inc konumunda bulunur *\<Visual Studio SDK installation path>* \\ . Bu dosyalar, VSPackage 'ın komut tablosu yapılandırma (. vsct) dosyasında kendi menü, Grup ve komutlarınız için kapsayıcı olarak kullanabileceğiniz menü ve grupların tanımlarını ve GUID 'Lerini sağlar.

## <a name="in-this-section"></a>Bu Bölümde
- [Visual Studio Menülerinin GUID’leri ve Kimlikleri](../../extensibility/internals/guids-and-ids-of-visual-studio-menus.md)

 Visual Studio menü çubuğunda ve içerdikleri gruplardan menülerin GUID ve ID değerlerini verir.

- [Visual Studio Araç Çubuklarının GUID’leri ve Kimlikleri](../../extensibility/internals/guids-and-ids-of-visual-studio-toolbars.md)

 Visual Studio IDE 'deki araç çubuklarının GUID ve KIMLIK değerlerini ve içerdikleri grupları verir.

- [Visual Studio Komutlarının GUID’leri ve Kimlikleri](../../extensibility/internals/guids-and-ids-of-visual-studio-commands.md)

 Visual Studio IDE tarafından tanımlanan komutların GUID ve ID değerlerini verir.

## <a name="see-also"></a>Ayrıca bkz.
- [Visual Studio Komut Tablosu (.Vsct) Dosyaları](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
- [Proje Sistemlerini Genişletmeye Yönelik IDE Tanımlı Komutlar](../../extensibility/internals/ide-defined-commands-for-extending-project-systems.md)
- [VSPackage’ların Kullanıcı Arabirimi Öğeleri Eklemesi](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
