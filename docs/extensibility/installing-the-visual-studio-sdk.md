---
title: Visual Studio SDK yükleme | Microsoft Docs
ms.custom: ''
ms.date: 07/12/2018
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: c730edb6-5099-4c16-85a8-08def09f1455
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 8dceab38f543c58997092559bf9a840806e9b013
ms.sourcegitcommit: 1c2ed640512ba613b3bbbc9ce348e28be6ca3e45
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/03/2018
ms.locfileid: "39498593"
---
# <a name="install-the-visual-studio-sdk"></a>Visual Studio SDK’yı Yükleme

Visual Studio SDK (Yazılım Geliştirme Seti), Visual Studio kurulumunda isteğe bağlı bir özelliktir. VS SDK'yi daha sonra yükleyebilirsiniz.  
  
## <a name="install-the-visual-studio-sdk-as-part-of-a-visual-studio-installation"></a>Visual Studio yüklemesinin bir parçası Visual Studio SDK'sını yükleme

Visual Studio yüklemenizin VS SDK'sı dahil etmek için yükleme **Visual Studio uzantısı geliştirme** altında iş yükü **diğer araç takımları**. Bu iş yükünü Visual Studio SDK'sı ve gerekli önkoşulları yükleyecek. Daha fazla yükleme seçme veya seçimini bileşenlerini ayarlayabilirsiniz **özeti** görünümü.
  
## <a name="install-the-visual-studio-sdk-after-installing-visual-studio"></a>Visual Studio yüklendikten sonra Visual Studio SDK'sını yükleyin

Visual Studio yüklemenizin tamamladıktan sonra Visual Studio SDK'yı yüklemek için Visual Studio yükleyiciyi yeniden çalıştırın ve seçin **Visual Studio uzantısı geliştirme** iş yükü.  
  
## <a name="install-the-visual-studio-sdk-from-a-solution"></a>Bir çözümü Visual Studio SDK'sını yükleme

Bir çözüm, VS SDK'yı yüklemeden bir genişletilebilirlik projesi açarsanız tarafından istenir bir **eksik özellik yükleme** yüklemek için iletişim **Visual Studio uzantısı geliştirme** iş yükü:

![Uzantı geliştirme yükleme](../extensibility/media/install-extension-development.png "yükleme uzantısı geliştirme")  
  
## <a name="install-the-visual-studio-sdk-from-the-command-line"></a>Komut satırından Visual Studio SDK'yı yükleme

Tüm Visual Studio iş yükü veya bileşen ile de yükleyebilirsiniz gibi **Visual Studio uzantısı geliştirme** iş yükü (kimlik: Microsoft.VisualStudio.Workload.VisualStudioExtension) komut satırı. Bkz: [Visual Studio'yu yüklemek için komut satırı parametreleri kullanmak](../install/use-command-line-parameters-to-install-visual-studio.md) uygun komut satırı anahtarları ve iş yükü veya bileşen tanımlayıcıları belirleme hakkında genel yönergeler hakkında ayrıntılı bilgi için.
  
Yüklü Visual Studio sürümünüzle eşleşen Visual Studio yükleyicisi kullanmanız gerektiğini unutmayın. Örneğin, bilgisayarınızda yüklü Visual Studio Enterprise varsa, Visual Studio Enterprise yükleyiciyi çalıştırmanız gerekir (*vs_enterprise.exe*).