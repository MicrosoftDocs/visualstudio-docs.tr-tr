---
title: Windows Installer Ile VSPackage kaldırılıyor | Microsoft Docs
description: Windows Installer, yükleme işlemini tersine çevirerek VSPackage 'ı kaldırabilir. Windows Installer paketinizdeki özel eylemlerle nasıl başa çıkılacağınızı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- packages, uninstalling
- VSPackages, uninstalling
- uninstalling VSPackages
ms.assetid: c4575ac7-82da-4af8-a375-ea756a101fbf
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: bb5d0fe0e4812d66f6981ea58dfb51f19336d98b
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105090726"
---
# <a name="uninstalling-a-vspackage-with-windows-installer"></a>Windows Installer ile VSPackage Kaldırma
Çoğu bölüm için Windows Installer VSPackage 'ı yalnızca "geri alma" ile VSPackage 'ı yükleme işlemini kaldırabilir. [Yükleme işleminden sonra çalıştırılması gereken komutlarda](../../extensibility/internals/commands-that-must-be-run-after-installation.md) açıklanan özel eylemler, bir kaldırma işleminden sonra çalıştırılmalıdır. devenv.exe çağrıları hem yükleme hem de kaldırma için InstallFinalize standart eyleminden hemen önce gerçekleştiğinden, CustomAction ve InstallExecuteSequence tablo girdileri her iki durumda da sunar.

> [!NOTE]
> `devenv /setup`BIR MSI paketini kaldırdıktan sonra çalıştırın.

 Genel bir kural olarak, bir Windows Installer paketine özel eylemler eklerseniz, bu işlemleri kaldırma ve geri alma sırasında işlemeniz gerekir. VSPackage 'a kendi kendine kaydolabilmeniz için özel eylemler eklerseniz, örneğin kaydını silmek için özel eylemler eklemeniz gerekir.

> [!NOTE]
> Bir kullanıcının VSPackage 'ı yüklemesi ve ardından tümleşik olduğu sürümlerini kaldırması mümkündür [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . Bağımlılıkları olan kodu çalıştıran özel eylemleri ortadan kaldırarak VSPackage 'ın kaldırma işleminin bu senaryoda çalıştığından emin olabilirsiniz [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .

## <a name="handling-launch-conditions-at-uninstall-time"></a>Kaldırma sırasında başlatma koşullarını işleme
 LaunchConditions standart eylemi, koşullar karşılanmazsa hata iletilerini göstermek için LaunchCondition tablosunun satırlarını okur. Başlatma koşulları genellikle sistem gereksinimlerinin karşılandığından emin olmak için kullanıldığında, kaldırma işlemi sırasında başlatma koşullarını `NOT Installed` LaunchCondition tablosunun LaunchConditions satırına ekleyerek genellikle atlayabilirsiniz.

 Diğer bir seçenek de `OR Installed` kaldırma sırasında önemli olmayan başlatma koşullarına eklemektir. Bu, kaldırma işlemi sırasında koşulun her zaman doğru olmasını sağlar ve bu nedenle başlatma koşulu hata iletisini görüntülemez.

> [!NOTE]
> `Installed` özelliği, VSPackage 'ın sistemde zaten yüklü olduğunu algıladığında ayarlar Windows Installer.

## <a name="see-also"></a>Ayrıca bkz.
- [Windows Installer](/previous-versions/ee231230(v=vs.100))
- [Sistem Gereksinimlerini Algılama](../../extensibility/internals/detecting-system-requirements.md)