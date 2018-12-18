---
title: Yükleme sonrasında çalıştırılması gereken komutları | Microsoft Docs
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
- post-install commands
ms.assetid: c9601f2e-2c6e-4da9-9a6e-e707319b39e2
caps.latest.revision: 23
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 90ce272270ffd511ee3b0efe8a711730ccdb92b5
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51724200"
---
# <a name="commands-that-must-be-run-after-installation"></a>Yükleme Sonrasında çalıştırılması Gereken Komutlar
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Uzantınızı bir .msi dosyası aracılığıyla dağıtırsanız, çalıştırmalısınız `devenv /setup` sırayla uzantılarınızı bulmak Visual Studio yüklemenizin bir parçası olarak.  
  
> [!NOTE]
>  Bu konu başlığı altındaki bilgiler, bulma DevEnv Visual Studio 2008 ve önceki sürümleri için geçerlidir. Visual Studio'nun daha yeni sürümleriyle DevEnv bulma hakkında daha fazla bilgi için bkz: [sistem gereksinimlerini algılama](../../extensibility/internals/detecting-system-requirements.md).  
  
## <a name="finding-devenvexe"></a>Devenv.exe bulma  
 Her sürümün bulabilirsiniz devenv.exe kayıt defterinden değerleri [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] yükleyicileri yazma, kayıt defteri değerlerini özellikleri olarak depolamak için RegLocator tablosunu ve AppSearch tablosunu kullanarak. Daha fazla bilgi için [sistem gereksinimlerini algılama](../../extensibility/internals/detecting-system-requirements.md).  
  
### <a name="reglocator-table-rows-to-locate-devenvexe-from-different-versions-of-visual-studio"></a>Visual Studio'nun farklı sürümlerine ait Devenv.exe bulunacak RegLocator tablo satırları  
  
|Signature_|Kök|Anahtar|Ad|Tür|  
|-----------------|----------|---------|----------|----------|  
|RL_DevenvExe_2002|2|SOFTWARE\Microsoft\VisualStudio\7.0\Setup\VS|EnvironmentPath|2|  
|RL_DevenvExe_2003|2|SOFTWARE\Microsoft\VisualStudio\7.1\Setup\VS|EnvironmentPath|2|  
|RL_DevenvExe_2005|2|SOFTWARE\Microsoft\VisualStudio\8.0\Setup\VS|EnvironmentPath|2|  
|RL_DevenvExe_2008|2|SOFTWARE\Microsoft\VisualStudio\9.0\Setup\VS|EnvironmentPath|2|  
  
### <a name="appsearch-table-rows-for-corresponding-reglocator-table-rows"></a>Karşılık gelen RegLocator tablo satırları için AppSearch tablo satırları  
  
|Özellik|Signature_|  
|--------------|-----------------|  
|DEVENV_EXE_2002|RL_DevenvExe_2002|  
|DEVENV_EXE_2003|RL_DevenvExe_2003|  
|DEVENV_EXE_2005|RL_DevenvExe_2005|  
|DEVENV_EXE_2008|RL_DevenvExe_2008|  
  
 Örneğin, Visual Studio yükleyicisi kayıt defteri değeri Yazar **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\9.0\Setup\VS\EnvironmentPath** olarak **C:\VS2008\Common7\IDE\devenv.exe**, bir yükleyiciyi çalıştırmanız gerekir yürütülebilirin tam yolu.  
  
 **Not** 2 RegLocator türü sütun olduğu için imza tabloda ek sürüm bilgilerini belirtmek ise gerekli değildir.  
  
## <a name="running-devenvexe"></a>Devenv.exe çalıştırma  
 Yükleyicide standart eylemin çalıştırdığı AppSearch sonra ilgili Visual Studio sürümü için devenv.exe dosyasını işaret eden bir değer AppSearch tablodaki her bir özellik vardır. Herhangi bir belirtilen kayıt defteri değeri mevcut olup olmadığını — Visual Studio'nun bu sürümü yüklü olmadığından — belirtilen özelliği null.  
  
 Windows Installer destekler işaret ettiği bir özelliği bir yürütülebilir özel eylemi çalıştıran 50 yazın. Özel eylem bulunan komut dosyası yürütme seçenekleri, msidbCustomActionTypeInScript (1024) ve msidbCustomActionTypeCommit (512) VSPackage'ı başarıyla içine tümleştirme önce yüklü olduğundan emin olmak için içermelidir [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]. Daha fazla bilgi için özel eylem bulunan komut dosyası yürütme seçenekleri ve özel tabloya bakın.  
  
 50 türündeki özel eylemler kaynak sütunu ve komut satırı bağımsız değişkenleri, hedef sütun değeri olarak yürütülebilir dosya içeren özelliği belirtin.  
  
### <a name="customaction-table-rows-to-run-devenvexe"></a>Devenv.exe çalıştırılacak özel tablo satırları  
  
|Eylem|Tür|Kaynak|Hedef|  
|------------|----------|------------|------------|  
|CA_RunDevenv2002|1586|DEVENV_EXE_2002|/ Setup|  
|CA_RunDevenv2003|1586|DEVENV_EXE_2003|/ Setup|  
|CA_RunDevenv2005|1586|DEVENV_EXE_2005|/ Setup|  
|CA_RunDevenv2008|1586|DEVENV_EXE_2008|/ Setup|  
  
 Özel Eylemler, bunları yüklenmesi sırasında yürütülmek üzere zamanlamak için InstallExecuteSequence tabloya yazılması gerekir. Özel eylemin durumunda çalıştırılmasını engellemek için karşılık gelen özelliği koşul sütununda her bir satırdaki kullanın sürümünü [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] sistemde yüklü değil.  
  
> [!NOTE]
>  `Null` özellikleri değerlendirmek için `False` koşullarında kullanıldığında.  
  
 Her özel eylemiyle ilgili dizisini sütununun değeri, Windows Installer paketi diğer sırası değerleri bağlıdır. Farklı Çalıştır devenv.exe özel eylemler InstallFinalize standart eylem hemen önce mümkün olduğunca kapatın, sıralı değerleri olmalıdır.  
  
### <a name="installexecutesequence-table-to-schedule-the-devenvexe-custom-actions"></a>Devenv.exe özel eylemler zamanlamak için InstallExecuteSequence tablo  
  
|Eylem|Koşul|Dizisi|  
|------------|---------------|--------------|  
|CA_RunDevenv2002|DEVENV_EXE_2002|6602|  
|CA_RunDevenv2003|DEVENV_EXE_2003|6603|  
|CA_RunDevenv2005|DEVENV_EXE_2005|6605|  
|CA_RunDevenv2008|DEVENV_EXE_2008|6608|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Windows Installer ile VSPackage Yükleme](../../extensibility/internals/installing-vspackages-with-windows-installer.md)

