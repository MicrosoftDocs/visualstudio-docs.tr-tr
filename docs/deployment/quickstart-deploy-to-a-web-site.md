---
title: Bir Web sitesine yayımlama
ms.date: 01/29/2019
ms.topic: quickstart
helpviewer_keywords:
- deployment, website
ms.assetid: fc82b1f1-d342-4b82-9a44-590479f0a895
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7ec5ea0b52c5d0708630a30b7d2b80be2275f3a9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "84173713"
---
# <a name="publish-a-web-app-to-a-web-site-using-visual-studio"></a>Web uygulamasını Visual Studio kullanarak Web sitesinde yayımlama

**Yayımla** aracını, ASP.NET, ASP.NET Core, .NET Core ve Python uygulamalarını Visual Studio 'daki bir Web sitesine yayımlamak için kullanabilirsiniz. Node.js, adımlar desteklenir, ancak kullanıcı arabirimi farklıdır.

[!INCLUDE [quickstart-prereqs](includes/quickstart-prereqs.md)]

> [!NOTE]
> Bir Windows masaüstü uygulamasını bir ağ dosya paylaşımında yayımlamanız gerekiyorsa bkz. [ClickOnce kullanarak masaüstü uygulaması dağıtma](how-to-publish-a-clickonce-application-using-the-publish-wizard.md) (C# veya Visual Basic). C++/CLR için bkz. [ClickOnce kullanarak yerel uygulama dağıtma](/cpp/windows/clickonce-deployment-for-visual-cpp-applications) veya C/C++ için bkz. [Kurulum projesi kullanarak yerel uygulama dağıtma](/cpp/windows/walkthrough-deploying-a-visual-cpp-application-by-using-a-setup-project).

## <a name="publish-to-a-web-site"></a>Web sitesinde yayımlama

1. Çözüm Gezgini, projeye sağ tıklayın ve **Yayımla** ' yı seçin (veya **Yapı**  >  **Yayımla** menü öğesini kullanın).

    ![Çözüm Gezgini içindeki proje bağlam menüsündeki Yayımla komutu](../deployment/media/quickstart-publish.png "Yayımla ' yı seçin")

1. Daha önce herhangi bir yayımlama profili yapılandırdıysanız, **Yayımla** bölmesi görüntülenir. **Yeni Profil oluştur**' u seçin.

1. **Yayımla** Iletişim kutusunda **Web sunucusu (IIS)** öğesini seçin.

    ![Yayımlama hedefini seçin](../deployment/media/quickstart-publish-iis.png "IIS, FTP, vb. seçin.")

1. Dağıtım yöntemi olarak **Web dağıtımı** seçin. Web Dağıtımı, Web uygulamalarının ve Web sitelerinin IIS sunucularına dağıtımını basitleştirir ve sunucuda bir uygulama olarak yüklenmelidir. Yüklemek için [Web Platformu Yükleyicisi](https://www.microsoft.com/web/downloads/platform.aspx) 'ni kullanın.

    ![Dağıtım yöntemini seçin](../deployment/media/quickstart-publish-iis-web-deploy.png "IIS, FTP, vb. seçin.")

1. Yayımla yöntemi için gerekli ayarları yapılandırın ve **son**' u seçin. 

    ![Web Dağıtımı bağlantı ayrıntıları](../deployment/media/quickstart-publish-iis-web-deploy-connection-details.png)

1. Yayımlamak için Özet sayfasında **Yayımla** ' yı seçin. Çıkış penceresinde dağıtım ilerleme durumu ve sonuçları gösterilir.

## <a name="next-steps"></a>Sonraki adımlar

Bu hızlı başlangıçta, bir yayımlama profili oluşturmak için Visual Studio 'Yu nasıl kullanacağınızı öğrendiniz. Yayımlama ayarlarını içeri aktararak de bir yayımlama profili yapılandırabilirsiniz.

> [!div class="nextstepaction"]
> [Yayımlama ayarlarını içeri aktarma ve IIS’ye dağıtma](tutorial-import-publish-settings-iis.md)
