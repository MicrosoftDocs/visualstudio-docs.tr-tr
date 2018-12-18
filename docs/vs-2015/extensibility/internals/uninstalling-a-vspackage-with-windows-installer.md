---
title: Windows Installer ile VSPackage kaldırma | Microsoft Docs
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
- packages, uninstalling
- VSPackages, uninstalling
- uninstalling VSPackages
ms.assetid: c4575ac7-82da-4af8-a375-ea756a101fbf
caps.latest.revision: 15
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 0082e86389620881c3879fe6dc79936b540d557f
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51742734"
---
# <a name="uninstalling-a-vspackage-with-windows-installer"></a>Windows Installer ile VSPackage Kaldırma
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Çoğunlukla, Windows Installer, VSPackage'ı yalnızca göre kaldırabilirsiniz ", VSPackage'ı yüklemek için kişiselleştirmeden geri alma". Özel Eylemler ele [komutları, gerekir olması çalıştırma sonra yükleme](../../extensibility/internals/commands-that-must-be-run-after-installation.md) bir kaldırma işleminden sonra çalıştırılmalıdır. Devenv.exe çağrıları hem yüklenmesi veya kaldırılması için InstallFinalize standart eylem hemen önce gerçekleşmesi için özel ve InstallExecuteSequence tablo girişleri her iki durumda hizmet.  
  
> [!NOTE]
>  Çalıştırma `devenv /setup` bir MSI paketi kaldırdıktan sonra.  
  
 Özel Eylemler bir Windows Installer paketini eklerseniz, genel bir kural olarak, bu eylemlerin kaldırma ve geri alma sırasında işlemesi gerekir. Örneğin, VSPackage'ı kendi kendine kaydettirmek için özel eylemler eklerseniz, çok kaydını kaldırmak için özel eylemler eklemeniz gerekir.  
  
> [!NOTE]
>  Bir kullanıcı, VSPackage'ı yükleyin ve ardından sürümleri kaldırmak mümkündür [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] ile tümleşik olduğundan. Üzerinde çalışan kod bağımlılıkları olan özel eylemler ortadan kaldırarak, VSPackage'nın kaldırılması bu senaryoda çalıştığından emin olun yardımcı [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
## <a name="handling-launch-conditions-at-uninstall-time"></a>İşleme sırasında başlatma koşulları kaldırması  
 Hatayı göstermek için LaunchCondition tablonun satırlarını LaunchConditions standart işlemi okur koşullar karşılanmazsa iletileri. Başlatma koşulları emin olmak için sistem gereksinimleri karşılanmadığı, koşul ekleyerek başlatma koşulları kaldırma sırasında genellikle atlayabilirsiniz genellikle kullanıldığından `NOT Installed`, LaunchCondition tablonun LaunchConditions satır.  
  
 Alternatif eklemektir `OR Installed` kaldırma sırasında önemli olmayan Koşulları'nı başlatmak için. Koşul kaldırma sırasında her zaman true olur ve bu nedenle başlatma koşulu hata iletisini görüntülemez sağlar.  
  
> [!NOTE]
>  `Installed` Windows Installer, VSPackage'ı sistemde zaten yüklü olduğunu algıladığında ayarlar özelliğidir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Windows Installer](http://msdn.microsoft.com/en-us/187d8965-c79d-4ecb-8689-10930fa8b3b5)   
 [Sistem Gereksinimlerini Algılama](../../extensibility/internals/detecting-system-requirements.md)

