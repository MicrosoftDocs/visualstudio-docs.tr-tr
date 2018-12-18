---
title: Katman modeli uzantısı dağıtma
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- dependency diagrams, deploying extensions
- layer models, deploying extensions
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 98697642135627173c5a6f31e90bf1dd1d0caeaf
ms.sourcegitcommit: 8cdc6e2ad2341f34bd6b02859a7c975daa0c9320
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/12/2018
ms.locfileid: "53307758"
---
# <a name="deploy-a-layer-model-extension"></a>Katman modeli uzantısı dağıtma

Visual Studio'nun diğer kullanıcıların katman modelleme uzantıları Visual Studio kullanarak oluşturduğunuz yükleyebilirsiniz.

## <a name="install-your-extension"></a>Uzantınızı yükleyin

Uzantınız, diğer bilgisayarlara yükleyebileceğiniz bir VSIX dosyasına derlenir. Uzantı Visual Studio ana örneğinde kullanılabilir hale getirmek için geliştirme bilgisayarınızdaki de yükleyebilirsiniz.

### <a name="to-install-the-extension"></a>Uzantıyı yüklemek için

1. İçeren projede **source.vsix.manifest**açın *bin* dosya Gezgini'nde dizin.

2. Kopyalama  **\*.vsix** uzantıyı yüklemek istediğiniz bilgisayarın dosyasına.

3. Hedef bilgisayarda, Windows Gezgini'nde *.vsix dosyasını çift tıklatın.

    VSIX yükleyici açılır.

### <a name="to-uninstall-the-extension"></a>Uzantıyı kaldırmak için

1.  Visual Studio'da üzerinde **Araçları** menüsünü tıklatın **Uzantılar ve güncelleştirmeler**.

2.  Uzantının adını tıklatın ve ardından **kaldırma**.

## <a name="install-an-extension-on-team-foundation-server"></a>Team Foundation Server'da bir uzantı yükleyin

Team Foundation Server sunucuları normalde Visual Studio yüklü olmayan ve çift tıklayarak VSIX kadar yükleyemez. Uzantıyı el ile yüklemeniz gerekir.

### <a name="to-install-your-layer-extension-on-a-team-foundation-server-server"></a>Katman uzantınızı bir Team Foundation Server sunucuya yüklemek için

1.  Kopyalama. *VSIX* dosyalarını Geliştirme bilgisayarınızdan Team Foundation Server (TFS) bilgisayarda.

     VSIX dosyasını şu konumlardan birinde yerleştirin:

    -   Tüm kullanıcılar ve hizmetler için yüklemek için:

         %ProgramFiles%\Microsoft visual Studio [sürüm] \Common7\IDE\Extensions\Microsoft

    -   Yapı çalıştıran ağ hizmeti için yüklemek için:

         %WinDir%\ServiceProfiles\NetworkService\AppData\Local\Microsoft\VisualStudio\\[version]\Extensions\Microsoft

    -   Belirli bir kullanıcı olarak etkileşimli modda çalıştırmak için yapıyı yapılandırdıysanız yalnızca bu kullanıcı için yükleyebilirsiniz:

         %LocalAppData%\Microsoft\VisualStudio\\[sürüm] \Extensions\Microsoft

2.  Her VSIX dosyasını aynı konumdaki bir klasöre genişletin:

    1.  Dosya adı uzantısını değiştirmek **.vsix** için **.zip**.

    2.  Bir klasöre .zip dosyasının içeriğini ayıklayın.

    3.  .Zip dosyasını sil

3.  TFS yeniden başlatın.
