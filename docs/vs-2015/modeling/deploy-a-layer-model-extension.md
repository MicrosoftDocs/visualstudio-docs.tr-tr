---
title: Bir katman modeli uzantısı dağıtma | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- layer diagrams, deploying extensions
- layer models, deploying extensions
ms.assetid: 00a4675b-d20e-487e-8fd5-be2b1e0ba238
caps.latest.revision: 29
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: a31413f5332ddfec8dc6021da85e2135d691f930
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51735117"
---
# <a name="deploy-a-layer-model-extension"></a>Katman modeli uzantısı dağıtma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio'nun diğer kullanıcıların katman modelleme uzantıları Visual Studio kullanarak oluşturduğunuz yükleyebilirsiniz.  
  
## <a name="installing-your-extension"></a>Uzantınız yükleniyor  
 Uzantınız, diğer bilgisayarlara yükleyebileceğiniz bir VSIX dosyasına derlenir. Uzantı Visual Studio ana örneğinde kullanılabilir hale getirmek için geliştirme bilgisayarınızdaki de yükleyebilirsiniz.  
  
#### <a name="to-install-the-extension"></a>Uzantıyı yüklemek için  
  
1. İçeren projede **source.vsix.manifest**açın **bin\\\\*** dosya Gezgini'nde.  
  
2. Kopyalama  **\*.vsix** uzantıyı yüklemek istediğiniz bilgisayarın dosyasına.  
  
3. Hedef bilgisayarda, Windows Gezgini'nde *.vsix dosyasını çift tıklatın.  
  
    VSIX yükleyici açılır.  
  
#### <a name="to-uninstall-the-extension"></a>Uzantıyı kaldırmak için  
  
1.  Visual Studio'da üzerinde **Araçları** menüsünü tıklatın **Uzantılar ve güncelleştirmeler**.  
  
2.  Uzantının adını tıklatın ve ardından **kaldırma**.  
  
## <a name="installing-an-extension-on-a-team-foundation-build-server"></a>Bir Team Foundation Yapısı sunucusuna uzantı yükleme  
 [!INCLUDE[esprbuild](../includes/esprbuild-md.md)] sunucuları normalde Visual Studio yüklü olmayan ve çift tıklayarak VSIX kadar yükleyemez. Yüklenmesini [!INCLUDE[esprbuild](../includes/esprbuild-md.md)] bazı bileşenleri içermektedir bir VSIX uzantısının çalışmasına izin ver, ancak uzantıyı el ile yüklemeniz gerekir.  
  
#### <a name="to-install-your-layer-extension-on-a-includeesprbuildincludesesprbuild-mdmd-server"></a>Katman uzantınızı yüklemek için bir [!INCLUDE[esprbuild](../includes/esprbuild-md.md)] sunucusu  
  
1.  Kopyalama **.vsix** geliştirme bilgisayarınıza dosyalarından [!INCLUDE[esprbuild](../includes/esprbuild-md.md)] bilgisayar.  
  
     VSIX dosyasını şu konumlardan birinde yerleştirin:  
  
    -   Tüm kullanıcılar ve hizmetler için yüklemek için:  
  
         %ProgramFiles%\Microsoft visual Studio [sürüm] \Common7\IDE\Extensions\Microsoft  
  
    -   Çalışan ağ hizmeti için yüklemek için [!INCLUDE[esprbuild](../includes/esprbuild-md.md)]:  
  
         %WinDir%\ServiceProfiles\NetworkService\AppData\Local\Microsoft\VisualStudio\\[version]\Extensions\Microsoft  
  
    -   Yapılandırdıysanız [!INCLUDE[esprbuild](../includes/esprbuild-md.md)] belirli bir kullanıcı olarak etkileşimli modda çalıştırmak için yalnızca bu kullanıcı için yükleyebilirsiniz:  
  
         %LocalAppData%\Microsoft\VisualStudio\\[sürüm] \Extensions\Microsoft  
  
        > [!NOTE]
        >  % LocalAppData %, genellikle *DriveName*: kullanıcıların*kullanıcıadı*AppDataLocal.  
  
2.  Her VSIX dosyasını aynı konumdaki bir klasöre genişletin:  
  
    1.  Dosya adı uzantısını değiştirmek **.vsix** için **.zip**.  
  
    2.  Bir klasöre .zip dosyasının içeriğini ayıklayın.  
  
    3.  .Zip dosyasını sil  
  
3.  Yeniden [!INCLUDE[esprbuild](../includes/esprbuild-md.md)].



