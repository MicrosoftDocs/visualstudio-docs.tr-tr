---
title: Linux üzerinde App Service yayımlayın
description: Sürekli ve tek seferlik seçenekler dahil olmak üzere kapsayıcıları kullanarak Linux Azure App Service ASP.NET Core Uygulamaları yayımlama yöntemleri hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 01/29/2019
ms.topic: quickstart
helpviewer_keywords:
- deployment, website
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- azure
ms.openlocfilehash: 0371a4186d51598a79818f79719b58e122a311f2
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99927463"
---
# <a name="publish-an-aspnet-core-app-to-app-service-on-linux-using-visual-studio"></a>Visual Studio kullanarak Linux 'ta App Service için ASP.NET Core uygulaması yayımlama

Visual Studio 2017 sürüm 15,7 ' den başlayarak, aşağıdaki yöntemlerden birini kullanarak Linux Azure App Service Linux (kapsayıcılar kullanarak) ASP.NET Core uygulamalar yayımlayabilirsiniz.

* Uygulamaların sürekli (veya otomatik) dağıtımı için [Azure Pipelines](/azure/devops/pipelines/get-started-yaml?view=azdevops&preserve-view=true)Ile Azure DevOps kullanın.

* Uygulamaların tek seferlik (veya el ile) dağıtımı için, Visual Studio 'daki **Yayımla** aracını kullanarak Linux için App Service ASP.NET Core uygulamalar yayımlayın (kapsayıcılar kullanarak).

Bu makalede, tek seferlik dağıtım için **Yayımla** aracının nasıl kullanılacağı açıklanır.

[!INCLUDE [quickstart-prereqs-azure-linux](includes/quickstart-prereqs-azure-linux.md)]

## <a name="publish-to-azure-app-service-on-linux"></a>Linux üzerinde Azure App Service yayımlayın

1. Çözüm Gezgini, projeye sağ tıklayın ve **Yayımla** ' yı seçin (veya **Yapı**  >  **Yayımla** menü öğesini kullanın).

    ![Çözüm Gezgini içindeki proje bağlam menüsündeki Yayımla komutu](../deployment/media/quickstart-publish.png "Yayımla ' yı seçin")

1. Daha önce herhangi bir yayımlama profili yapılandırdıysanız, **Yayımla** penceresi görüntülenir. **Yeni**'yi seçin.

1. **Yayımla** penceresinde **Azure**' ı seçin.

    ![Yayımlama hedefini seçin](../deployment/media/quickstart-publish-azure-new.png)

1. **Azure App Service (Linux)** ve **İleri ' yi** seçin.

    ![Linux üzerinde Azure App Service seçin](../deployment/media/quickstart-publish-linux-select-azure-service.png)

1. Gerekirse Azure hesabınızla oturum açın. **Yeni Azure App Service oluştur ' u seçin...**

    ![Azure App Service yeni bir örneğini oluşturmak için bağlantı](../deployment/media/quickstart-publish-linux-create-new-link.png)

1. **Azure App Service oluştur (Linux)** iletişim kutusunda, **uygulama adı**, **kaynak grubu** ve **App Service planı** giriş alanları doldurulur. Bu adları koruyabilir veya değiştirebilirsiniz. Hazırlanıyor, **Oluştur**' u seçin.

    ![Ad, abonelik, kaynak grubu ve barındırma planı alanları doldurulmuş Azure App Service oluştur (Linux) iletişim kutusunun ekran görüntüsü.](../deployment/media/quickstart-publish-linux-create-new-dialog.png)

1. **Yayımla** iletişim kutusunda yeni oluşturulan örnek otomatik olarak seçilmiştir. Hazırlık sırasında **son**' a tıklayın.

    ![Yayımlama için App Service olarak yeni oluşturulan MyASpCoreWebAppOnAzure hizmeti ile Yayımla iletişim kutusunun ekran görüntüsü.](../deployment/media/quickstart-publish-linux-select-instance.png)

1. **Yayımla**’yı seçin. Visual Studio uygulamayı Azure App Service dağıtır ve Web uygulaması tarayıcınıza yüklenir. Proje özellikleri **Yayımlama** bölmesi, site URL 'sini ve diğer ayrıntıları gösterir.

    ![Profil özetini gösteren özellik bölmesini Yayımla](../deployment/media/quickstart-publish-linux-summary-page.png)

## <a name="clean-up-resources"></a>Kaynakları temizleme

Önceki adımlarda, bir kaynak grubunda Azure kaynakları oluşturdunuz. İleride bu kaynaklara ihtiyaç duymayacağınızı düşünüyorsanız kaynakları silmek için kaynak grubunu silebilirsiniz.
Azure portalında sol taraftaki menüden **Kaynak grupları**'nı seçin ve ardından **myResourceGroup** seçeneğini belirleyin.
Kaynak grubu sayfasındaki listede yer alan kaynakların silmek istediğiniz kaynaklar olduğundan emin olun.
**Sil**'i seçin, metin kutusuna **myResourceGroup** yazın ve ardından **Sil**'e tıklayın.

## <a name="next-steps"></a>Sonraki adımlar

Bu hızlı başlangıçta, Linux üzerinde App Service dağıtım için bir yayımlama profili oluşturmak üzere Visual Studio 'Yu nasıl kullanacağınızı öğrendiniz. Azure kullanarak Linux 'a yayımlama hakkında daha fazla bilgi isteyebilirsiniz.

> [!div class="nextstepaction"]
> [Linux App Service](/azure/app-service/containers/app-service-linux-intro)