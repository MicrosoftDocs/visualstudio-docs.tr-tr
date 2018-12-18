---
title: Yükleme sonrasında çalıştırılması gereken komutları | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- post-install commands
ms.assetid: c9601f2e-2c6e-4da9-9a6e-e707319b39e2
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 08e1bcf064a8e94af306230e705f686d2d8037c1
ms.sourcegitcommit: 206e738fc45ff8ec4ddac2dd484e5be37192cfbd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/03/2018
ms.locfileid: "39510712"
---
# <a name="commands-that-must-be-run-after-installation"></a>Yükleme sonrasında çalıştırılması gereken komutları
Uzantınızı aracılığıyla dağıtırsanız bir *.msi* dosyasını çalıştırmalısınız **devenv/Setup** sırayla uzantılarınızı bulmak Visual Studio yüklemenizin bir parçası olarak.  
  
> [!NOTE]
>  Bulma için bu konudaki bilgiler, geçerli *devenv.exe* Visual Studio 2008 ve önceki sürümleri. Bulma hakkında daha fazla bilgi için *devenv.exe* daha sonra Visual Studio sürümleriyle bkz [sistem gereksinimlerini algılama](../../extensibility/internals/detecting-system-requirements.md).  
  
## <a name="find-devenvexe"></a>Devenv.exe Bul  
 Her sürümün bulabilirsiniz *devenv.exe* , kayıt defterinden değerleri [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] yükleyicileri yazma, kayıt defteri değerlerini özellikleri olarak depolamak için RegLocator tablosu ve AppSearch tabloları kullanarak. Daha fazla bilgi için [sistem gereksinimlerini algılama](../../extensibility/internals/detecting-system-requirements.md).  
  
### <a name="reglocator-table-rows-to-locate-devenvexe-from-different-versions-of-visual-studio"></a>Visual Studio'nun farklı sürümlerine ait Devenv.exe bulunacak RegLocator tablo satırları  
  
|İmza|Kök|Anahtar|Ad|Tür|  
|-----------------|----------|---------|----------|----------|  
|RL_DevenvExe_2002|2|SOFTWARE\Microsoft\VisualStudio\7.0\Setup\VS|EnvironmentPath|2|  
|RL_DevenvExe_2003|2|SOFTWARE\Microsoft\VisualStudio\7.1\Setup\VS|EnvironmentPath|2|  
|RL_DevenvExe_2005|2|SOFTWARE\Microsoft\VisualStudio\8.0\Setup\VS|EnvironmentPath|2|  
|RL_DevenvExe_2008|2|SOFTWARE\Microsoft\VisualStudio\9.0\Setup\VS|EnvironmentPath|2|  
  
### <a name="appsearch-table-rows-for-corresponding-reglocator-table-rows"></a>Karşılık gelen RegLocator tablo satırları için AppSearch tablo satırları  
  
|Özellik|İmza|  
|--------------|-----------------|  
|DEVENV_EXE_2002|RL_DevenvExe_2002|  
|DEVENV_EXE_2003|RL_DevenvExe_2003|  
|DEVENV_EXE_2005|RL_DevenvExe_2005|  
|DEVENV_EXE_2008|RL_DevenvExe_2008|  
  
 Örneğin, Visual Studio yükleyicisi kayıt defteri değeri Yazar **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\9.0\Setup\VS\EnvironmentPath** olarak *C:\VS2008\Common7\IDE\devenv.exe*, bir yükleyiciyi çalıştırmanız gerekir yürütülebilirin tam yolu.  
  
> [!NOTE]
> 2 RegLocator tablonun türü sütun olduğu için imza tabloda ek sürüm bilgilerini belirtmek gerekli değildir.  
  
## <a name="run-devenvexe"></a>Devenv.exe çalıştırın  
 Standart eylemin çalıştırdığı yükleyicide AppSearch sonra işaret eden bir değer AppSearch tablodaki her bir özellik olan *devenv.exe* karşılık gelen Visual Studio sürümü için dosya. Herhangi bir belirtilen kayıt defteri değeri mevcut olup olmadığını — Visual Studio'nun bu sürümü yüklü olmadığından — belirtilen özelliği null.  
  
 Windows Installer destekler işaret ettiği bir özelliği bir yürütülebilir özel eylemi çalıştıran 50 yazın. Özel eylem bulunan komut dosyası yürütme seçenekleri içermelidir `msidbCustomActionTypeInScript` (1024) ve `msidbCustomActionTypeCommit` (VSPackage'ı başarıyla içine tümleştirme önce yüklü olduğundan emin olmak için 512), [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Daha fazla bilgi için [özel tablo](https://docs.microsoft.com/windows/desktop/msi/customaction-table) ve [özel eylem bulunan komut dosyası yürütme seçenekleri](https://docs.microsoft.com/windows/desktop/msi/custom-action-in-script-execution-options).  
  
 50 türündeki özel eylemler kaynak sütunu ve komut satırı bağımsız değişkenleri, hedef sütun değeri olarak yürütülebilir dosya içeren özelliği belirtin.  
  
### <a name="customaction-table-rows-to-run-devenvexe"></a>Devenv.exe çalıştırılacak özel tablo satırları  
  
|Eylem|Tür|Kaynak|Hedef|  
|------------|----------|------------|------------|  
|CA_RunDevenv2002|1586|DEVENV_EXE_2002|/ Setup|  
|CA_RunDevenv2003|1586|DEVENV_EXE_2003|/ Setup|  
|CA_RunDevenv2005|1586|DEVENV_EXE_2005|/ Setup|  
|CA_RunDevenv2008|1586|DEVENV_EXE_2008|/ Setup|  
  
 Özel Eylemler, bunları yüklenmesi sırasında yürütülmek üzere zamanlamak için InstallExecuteSequence tabloya yazılması gerekir. Özel eylemin durumunda çalıştırılmasını engellemek için karşılık gelen özelliği koşul sütununda her bir satırdaki kullanın sürümünü [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] sistemde yüklü değil.  
  
> [!NOTE]
>  Null değerli özellikleri değerlendirmek için `False` koşullarında kullanıldığında.  
  
 Her özel eylemiyle ilgili dizisini sütununun değeri, Windows Installer paketi diğer sırası değerleri bağlıdır. Sıralı değerleri olmalıdır şekilde *devenv.exe* InstallFinalize standart eylem hemen önce mümkün olduğunca Çalıştır özel eylemler kapatın.  
  
### <a name="installexecutesequence-table-to-schedule-the-devenvexe-custom-actions"></a>Devenv.exe özel eylemler zamanlamak için InstallExecuteSequence tablo  
  
|Eylem|Koşul|Dizisi|  
|------------|---------------|--------------|  
|CA_RunDevenv2002|DEVENV_EXE_2002|6602|  
|CA_RunDevenv2003|DEVENV_EXE_2003|6603|  
|CA_RunDevenv2005|DEVENV_EXE_2005|6605|  
|CA_RunDevenv2008|DEVENV_EXE_2008|6608|  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Windows Installer ile VSPackage yükleme](../../extensibility/internals/installing-vspackages-with-windows-installer.md)