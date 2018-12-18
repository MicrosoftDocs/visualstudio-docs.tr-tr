---
title: Yerel klasöre dağıtma
ms.custom: ''
ms.date: 06/22/2018
ms.technology: vs-ide-deployment
ms.topic: quickstart
helpviewer_keywords:
- deployment, local folder
ms.assetid: adb461c4-812a-4b8c-b2ab-96002379f6a9
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 517698aa2e042d74138579dae3633930b338cd61
ms.sourcegitcommit: c57ae28181ffe14a30731736661bf59c3eff1211
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/11/2018
ms.locfileid: "38781919"
---
# <a name="deploy-an-app-to-a-local-folder-using-visual-studio"></a>Visual Studio kullanarak yerel bir klasöre uygulama dağıtma

Kullanabileceğiniz **Yayımla** ASP.NET, ASP.NET Core, .NET Core ve Python uygulamaları yerel bir klasöre Visual Studio'dan yayımlamak için aracı. Node.js için adımları desteklenir ancak kullanıcı arabirimi farklıdır.

[!INCLUDE [quickstart-prereqs](includes/quickstart-prereqs.md)]

## <a name="deploy-to-a-local-folder"></a>Yerel klasöre dağıtma

1. Çözüm Gezgini'nde projeye sağ tıklayıp seçin **Yayımla** (veya **derleme** > **Yayımla** menü öğesi).

    ![Çözüm Gezgini'nde proje bağlam menüsünde Yayımla komutunu](../deployment/media/quickstart-publish.png "seçin yayımlama")

1. Tüm yayımlama profilleri, daha önce yapılandırdıysanız **Yayımla** bölmesi görünür. Seçin **yeni profil oluşturma**.

1. İçinde **yayımlama hedefi seçin** iletişim kutusunda **klasör**.

    ![Yayımlama seçilmeli olarak yerel klasörü seç](../deployment/media/quickstart-publish-folder.png "Klasör Seç")

1. Bir yol girin veya seçin **Gözat** yerel klasörü belirtin.

1. Seçin **yayımlama**. Visual Studio projeyi oluşturur ve belirtilen klasöre yayımlar. Proje özelliklerini **Yayımla** bir profili bölmesi görünür, Özet gösteriliyor.

    ![Yayımlama profili Özet gösteren özellik bölmesi](../deployment/media/quickstart-publish-folder-summary.png)

1. Dağıtım ayarları yapılandırmak için seçin **yapılandırma** Özet ve select profilinde **ayarları** sekmesi.

    ![Profil ayarları](../deployment/media/quickstart-profile-settings.png "profil ayarları")

1. Bir hata ayıklama veya sürüm yapılandırmasına dağıtın ve ardından gibi seçenekleri **Kaydet**.

1. Yeniden yayımlamak için seçin **Yayımla**.

Yayımlanan dosyaları istediğiniz herhangi bir şekilde dağıtın. Örneğin, bunları paketleyebilirsiniz bir *.zip* dosya, bir basit kopyası komutunu kullanın veya bunları seçtiğiniz herhangi bir yükleme paketi ile birlikte dağıtabilirsiniz.

## <a name="next-steps"></a>Sonraki adımlar

- [Yayımla aracı ile .NET Core Uygulaması dağıtma](/dotnet/core/deploying/deploy-with-vs?toc=/visualstudio/deployment/toc.json&bc=/visualstudio/deployment/_breadcrumb/toc.json)
- [Bir masaüstü uygulamasını Microsoft Store için paketleme (Masaüstü Köprüsü)](/windows/uwp/porting/desktop-to-uwp-packaging-dot-net?toc=/visualstudio/deployment/toc.json&bc=/visualstudio/deployment/_breadcrumb/toc.json)
- (.NET) [.NET Framework ve uygulamaları dağıtma](/dotnet/framework/deployment/)
