---
title: Uzaktan hata ayıklayıcı yükleme
description: Uzaktan hata ayıklayıcı için karşıdan yükleme bağlantıları
services: ''
author: mikejo5000
ms.service: ''
ms.topic: include
ms.date: 05/23/2018
ms.author: mikejo
ms.custom: include file
ms.openlocfilehash: 6c429614a094ceefc4f9a1e358ebc8ee26c40773
ms.sourcegitcommit: 1df0ae74af03bcf0244129a29fd6bd605efc9f61
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/01/2018
ms.locfileid: "50915280"
---
Uzak cihaz üzerinde hata ayıklamak istediğiniz sunucu yerine veya Visual Studio makinesine, indirin ve aşağıdaki tabloda bağlantıları uzak araçların doğru sürümünü yükleyin.

- Visual Studio sürümünüz için en son uzak Araçlar'ı indirin. En son uzak Araçlar sürümü, önceki Visual Studio sürümleriyle uyumludur, ancak uzak Araçlar sürümlerde daha yeni Visual Studio sürümleriyle uyumlu değil. 
- Üzerinde yüklüyorsanız makine aynı mimarisine sahip uzak Araçları'nı indirin. Örneğin, bir 64-bit işletim sistemi çalıştıran bir uzak bilgisayarda bir 32-bit uygulamanın hatalarını ayıklamak istiyorsanız, 64-bit uzak Araçları'nı yükleme. 

|Sürüm|Bağlantı|Notlar|
|-|-|-|
|Visual Studio 2017 (en son sürüm)|[Uzak Araçlar](https://visualstudio.microsoft.com/downloads/?q=remote+tools#remote-tools-for-visual-studio-2017)|Tüm Visual Studio 2017 sürümleri ile uyumludur. Cihaz işletim sisteminiz (x 86, x64 veya ARM64) eşleşen sürümünü indirin. Windows Server'da bkz [dosya indirme engellemesini](../../debugger/remote-debugging-unblock-file-download.md) uzak araçları yükleme konusunda yardım almak için.|
|Visual Studio 2015|[Uzak Araçlar](https://my.visualstudio.com/Downloads?q=remote%20tools%20visual%20studio%202015)|Visual Studio 2015 için Uzak Araçlar, My.VisualStudio.com kullanılabilir. İstenirse, ücretsiz katılın [Visual Studio Dev Essentials](https://visualstudio.microsoft.com/dev-essentials/) program ya da Visual Studio abonelik kimliğinizle oturum açın. Windows Server'da bkz [dosya indirme engellemesini](../../debugger/remote-debugging-unblock-file-download.md) uzak araçları yükleme konusunda yardım almak için.|
|Visual Studio 2013|[Uzak Araçlar](/previous-versions/visualstudio/visual-studio-2013/bt727f1t(v=vs.120)#Installing_the_Remote_Tools)|Visual Studio 2013 belgeleri sayfasında indirin|
|Visual Studio 2012|[Uzak Araçlar](/previous-versions/visualstudio/visual-studio-2012/bt727f1t(v=vs.110)#BKMK_Installing_the_Remote_Tools)|Visual Studio 2012 belgeleri sayfasında indirin|

Uzaktan hata ayıklayıcı kopyalayarak çalıştırabileceğiniz *msvsmon.exe* uzak araçları yükleme yerine uzak bilgisayar. Ancak, uzaktan hata ayıklayıcı Yapılandırma Sihirbazı'nı (*rdbgwiz.exe*) yalnızca uzak araçları yüklediğinizde kullanılabilir. Uzaktan hata ayıklayıcıyı bir hizmet olarak çalıştırmak istiyorsanız sihirbazın yapılandırmasını kullanmanız gerekebilir. Daha fazla bilgi için [(isteğe bağlı) yapılandırma hizmet olarak uzaktan hata ayıklayıcı](../../debugger/remote-debugging.md#bkmk_configureService).

>[!NOTE]
>- Windows 10 uygulamaları ARM cihazları üzerinde hata ayıklamak için Uzak Araçlar'ın en son sürümüyle kullanılabilir olduğu, ARM64'nı kullanın.  
>- Windows 10 uygulamaları Windows RT cihazlarında hata ayıklamak için yalnızca Visual Studio uzak araçları indirmek 2015'te kullanılabilir olan ARM kullanın.

